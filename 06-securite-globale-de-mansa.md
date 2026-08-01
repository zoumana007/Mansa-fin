# 06 — Sécurité globale de Mansa

## 1. Objet du document

Ce document définit les exigences de sécurité applicables à l'ensemble de l'écosystème Mansa.

Il couvre :

- les utilisateurs ;
- les commerçants ;
- les administrateurs ;
- les partenaires ;
- les API ;
- les applications mobiles ;
- les applications web ;
- les terminaux TPE ;
- les services backend ;
- les bases de données ;
- les documents ;
- les communications ;
- les infrastructures.

La sécurité doit être intégrée dès la conception ("Security by Design") et non ajoutée après le développement.

---

# 2. Principes fondamentaux

## 2.1 Sécurité par défaut

Tout nouvel écran, API, service ou fonctionnalité est considéré comme non sécurisé tant que :

- les permissions ;
- les validations ;
- les contrôles d'accès ;
- les audits ;
- les protections contre les abus ;

ne sont pas définis.

## 2.2 Principe du moindre privilège

Chaque utilisateur, employé, commerçant ou administrateur ne dispose que des droits strictement nécessaires à sa fonction.

Les privilèges temporaires doivent expirer automatiquement.

## 2.3 Défense en profondeur

Chaque opération critique doit être protégée par plusieurs couches :

- authentification ;
- autorisation ;
- validation métier ;
- contrôle de fraude ;
- audit ;
- journalisation ;
- surveillance.

## 2.4 Zéro confiance

Aucune requête n'est considérée comme fiable uniquement parce qu'elle provient :

- d'une application Mansa ;
- d'un TPE ;
- d'un réseau interne ;
- d'un partenaire.

Chaque requête est validée.

---

# 3. Authentification

## 3.1 Méthodes autorisées

Mansa doit pouvoir prendre en charge :

- mot de passe ;
- PIN ;
- OTP SMS ;
- OTP e-mail ;
- biométrie ;
- Passkeys/WebAuthn ;
- authentification à deux facteurs (2FA).

Les méthodes disponibles peuvent varier selon le pays, le rôle ou le niveau de risque.

## 3.2 Politique de mot de passe

Les mots de passe doivent respecter une politique configurable :

- longueur minimale ;
- complexité ;
- historique ;
- expiration si imposée par une réglementation ;
- vérification contre les mots de passe compromis.

Ils ne doivent jamais être stockés en clair.

## 3.3 PIN

Le PIN est utilisé pour les opérations sensibles sur mobile.

Exigences :

- longueur configurable ;
- stockage sécurisé ;
- limitation des tentatives ;
- verrouillage après plusieurs échecs.

---

# 4. Gestion des sessions

Chaque session doit enregistrer :

- identifiant de session ;
- appareil ;
- système d'exploitation ;
- version de l'application ;
- adresse IP si autorisée ;
- pays ;
- date de création ;
- dernière activité ;
- niveau de confiance.

Les utilisateurs doivent pouvoir consulter et révoquer leurs sessions actives.

---

# 5. Gestion des appareils

Chaque appareil approuvé possède :

- un identifiant unique ;
- un niveau de confiance ;
- un statut (actif, révoqué, suspendu) ;
- une date d'approbation.

Un nouvel appareil peut nécessiter une vérification supplémentaire avant d'accéder aux opérations sensibles.

---

# 6. Contrôle d'accès

Les autorisations sont basées sur :

- le rôle (RBAC) ;
- les attributs (ABAC) ;
- le pays ;
- le niveau KYC/KYB ;
- le contexte (montant, appareil, risque).

Le backend reste l'autorité unique pour les décisions d'accès.

---

# 7. Protection des données

Les données sont classées en plusieurs niveaux :

- publiques ;
- internes ;
- confidentielles ;
- sensibles ;
- hautement sensibles.

Les données sensibles (PIN, secrets, clés, CVV, etc.) doivent être chiffrées et ne jamais être exposées dans les journaux.

---

# 8. Chiffrement

Le système doit utiliser :

- TLS pour les communications ;
- chiffrement des données sensibles au repos ;
- rotation des clés ;
- gestion sécurisée des secrets.

Les clés de chiffrement doivent être stockées dans un gestionnaire de secrets dédié.

---

# 9. Protection des API

Les API doivent intégrer :

- authentification ;
- autorisation ;
- limitation de débit (rate limiting) ;
- validation des entrées ;
- protection contre les attaques par rejeu ;
- journalisation.

Les opérations financières doivent utiliser une clé d'idempotence.

---

# 10. Protection contre la fraude

Le système doit analyser notamment :

- les connexions inhabituelles ;
- les nouveaux appareils ;
- les montants anormaux ;
- les destinations inhabituelles ;
- les tentatives répétées ;
- les comportements automatisés.

Selon le niveau de risque, une opération peut être :

- autorisée ;
- soumise à une vérification supplémentaire ;
- retardée ;
- refusée.

---

# 11. Journal d'audit

Toutes les actions critiques doivent être enregistrées :

- connexion ;
- déconnexion ;
- modification des permissions ;
- création ou suppression d'un compte ;
- paiements ;
- remboursements ;
- modifications administratives ;
- changements de configuration.

Les journaux doivent être horodatés, protégés contre la modification et conservés selon la politique de rétention.

---

# 12. Sécurité des applications mobiles

Les applications doivent intégrer :

- stockage sécurisé des secrets ;
- détection de root/jailbreak si jugée nécessaire ;
- protection contre le débogage abusif ;
- protection contre les captures d'écran pour certains écrans ;
- validation des certificats réseau lorsque approprié.

---

# 13. Sécurité du portail Admin

Le portail Admin exige :

- authentification forte ;
- 2FA obligatoire ;
- réauthentification pour les actions critiques ;
- journalisation complète ;
- gestion fine des permissions.

Les actions sensibles peuvent nécessiter une double approbation.

---

# 14. Sécurité des TPE

Les terminaux TPE doivent prévoir :

- authentification des employés ;
- identification du terminal ;
- certificats ;
- mises à jour sécurisées ;
- stockage local chiffré ;
- effacement sécurisé des données en cas de désactivation.

---

# 15. Continuité et réponse aux incidents

Une procédure de gestion des incidents doit définir :

- la détection ;
- la qualification ;
- la notification ;
- le confinement ;
- la résolution ;
- l'analyse post-incident.

Les incidents critiques doivent être documentés et audités.

---

# 16. Tests de sécurité

Le projet doit prévoir :

- analyses statiques ;
- analyses dynamiques ;
- revues de code ;
- tests d'intrusion ;
- vérification des dépendances ;
- tests de permissions ;
- tests d'élévation de privilèges.

---

# 17. Critères d'acceptation

La sécurité globale est considérée comme validée lorsque :

- toutes les opérations critiques sont protégées ;
- les permissions sont appliquées côté backend ;
- les données sensibles sont chiffrées ;
- les API sont sécurisées ;
- les sessions sont maîtrisées ;
- les appareils sont gérés ;
- les journaux d'audit sont complets ;
- les risques de fraude sont pris en compte ;
- les environnements sont isolés ;
- les procédures d'incident sont définies ;
- les tests de sécurité sont intégrés au cycle de développement.
