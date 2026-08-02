# 20 — Gestion de la sécurité globale de Mansa

## 1. Objet du document

Ce document définit l'architecture officielle de sécurité de Mansa.

Il couvre :

- la sécurité des utilisateurs ;
- la sécurité des employés ;
- la sécurité des administrateurs ;
- la sécurité des partenaires ;
- la sécurité des API ;
- la sécurité des applications mobiles ;
- la sécurité des sites web ;
- la sécurité des TPE ;
- la sécurité des données ;
- la sécurité des paiements ;
- la sécurité des cartes ;
- la sécurité du ledger ;
- la sécurité de l'infrastructure ;
- la gestion des secrets ;
- la cryptographie ;
- la détection de fraude ;
- les audits ;
- les réponses aux incidents ;
- les politiques de sécurité.

L'objectif est de garantir :

- la confidentialité ;
- l'intégrité ;
- la disponibilité ;
- la traçabilité ;
- la non-répudiation ;
- la conformité réglementaire.

---

# 2. Principes fondamentaux

## 2.1 Security by Design

La sécurité doit être intégrée dès la conception.

Aucune fonctionnalité ne doit être développée sans analyse des risques.

---

## 2.2 Défense en profondeur

La sécurité repose sur plusieurs couches indépendantes :

- authentification ;
- autorisation ;
- chiffrement ;
- journalisation ;
- surveillance ;
- limitation ;
- segmentation ;
- validation ;
- protection réseau.

Une seule protection ne doit jamais être considérée comme suffisante.

---

## 2.3 Zero Trust

Aucun utilisateur, appareil ou service n'est considéré comme fiable par défaut.

Chaque requête doit être :

- authentifiée ;
- autorisée ;
- vérifiée ;
- journalisée.

---

## 2.4 Principe du moindre privilège

Chaque acteur ne possède que les permissions nécessaires.

Les permissions inutiles sont interdites.

---

## 2.5 Séparation des responsabilités

Les actions critiques doivent être réparties.

Exemples :

- création d'une règle ;
- validation ;
- approbation ;
- publication.

---

# 3. Piliers de sécurité

Le système repose sur :

- IAM ;
- RBAC ;
- MFA ;
- chiffrement ;
- gestion des secrets ;
- audit ;
- monitoring ;
- détection d'anomalies ;
- réponse aux incidents ;
- sauvegardes.

---

# 4. Authentification

Méthodes possibles :

- mot de passe ;
- PIN ;
- biométrie ;
- OTP SMS ;
- OTP e-mail ;
- application d'authentification ;
- passkeys ;
- authentification forte.

---

# 5. Gestion des sessions

Chaque session doit posséder :

- identifiant ;
- utilisateur ;
- appareil ;
- pays ;
- adresse IP ;
- date ;
- expiration ;
- niveau d'authentification ;
- version d'application.

Le système doit permettre :

- révocation ;
- expiration ;
- déconnexion distante ;
- limitation du nombre de sessions.

---

# 6. Authentification multifacteur (MFA)

Le MFA doit être exigé pour :

- changement de mot de passe ;
- changement de téléphone ;
- ajout d'un appareil ;
- opérations financières sensibles ;
- administration ;
- accès support privilégié ;
- export de données ;
- modification de permissions.

---

# 7. Gestion des appareils

Chaque appareil enregistré doit contenir :

- identifiant ;
- modèle ;
- système ;
- version ;
- date d'enregistrement ;
- dernière activité ;
- niveau de confiance ;
- statut.

L'utilisateur peut :

- consulter ;
- renommer ;
- révoquer ;
- déclarer perdu.

---

# 8. Politique des mots de passe

Le système doit définir :

- longueur minimale ;
- complexité ;
- historique ;
- expiration si nécessaire ;
- vérification contre les mots de passe compromis ;
- limitation des tentatives.

Les mots de passe doivent être hachés avec un algorithme robuste (ex. Argon2id ou équivalent).

---

# 9. PIN

Le PIN doit :

- être chiffré ;
- ne jamais être journalisé ;
- être limité en tentatives ;
- déclencher un verrouillage temporaire ;
- nécessiter une réinitialisation sécurisée.

---

# 10. Biométrie

La biométrie doit :

- rester gérée par le système d'exploitation ;
- ne jamais être stockée par Mansa ;
- servir à déverrouiller une clé locale ;
- pouvoir être désactivée.

---

# 11. Chiffrement

Les données sensibles doivent être chiffrées :

- au repos ;
- en transit ;
- dans les sauvegardes.

Les algorithmes doivent être conformes aux bonnes pratiques de l'industrie.

---

# 12. Gestion des secrets

Les secrets incluent :

- clés API ;
- clés privées ;
- certificats ;
- secrets JWT ;
- tokens partenaires ;
- mots de passe techniques.

Ils doivent être stockés dans un gestionnaire de secrets sécurisé.

Ils ne doivent jamais être :

- codés en dur ;
- stockés dans Git ;
- affichés dans les logs.

---

# 13. Certificats

Le système doit gérer :

- certificats TLS ;
- certificats partenaires ;
- certificats TPE ;
- rotation ;
- expiration ;
- renouvellement ;
- révocation.

---

# 14. Sécurité réseau

Le réseau doit utiliser :

- TLS moderne ;
- segmentation ;
- pare-feu ;
- limitation IP ;
- protection DDoS ;
- filtrage ;
- VPN pour certains accès.

---

# 15. Sécurité des API

Les API doivent appliquer :

- authentification ;
- autorisation ;
- validation stricte ;
- limitation de débit ;
- idempotence ;
- journalisation ;
- protection contre les injections ;
- contrôle CORS lorsque nécessaire.

---

# 16. Validation des entrées

Toutes les entrées utilisateur doivent être validées.

Protéger contre notamment :

- SQL Injection ;
- XSS ;
- CSRF ;
- SSRF ;
- Command Injection ;
- Path Traversal ;
- fichiers malveillants.

---

# 17. Protection contre la fraude

Le moteur de fraude doit pouvoir analyser :

- appareil ;
- localisation ;
- fréquence ;
- montant ;
- comportement ;
- bénéficiaire ;
- historique ;
- partenaire.

Il peut :

- bloquer ;
- demander une vérification ;
- augmenter le niveau d'authentification ;
- créer un dossier fraude.

---

# 18. Journalisation de sécurité

Les événements suivants doivent être journalisés :

- connexion ;
- échec ;
- changement de mot de passe ;
- changement PIN ;
- MFA ;
- ajout appareil ;
- suppression appareil ;
- export ;
- changement de rôle ;
- accès d'urgence ;
- incident.

---

# 19. Sauvegardes

Les sauvegardes doivent être :

- chiffrées ;
- testées ;
- versionnées ;
- géographiquement redondantes ;
- surveillées.

---

# 20. Réponse aux incidents

Le système doit prévoir :

- détection ;
- confinement ;
- investigation ;
- correction ;
- communication ;
- restauration ;
- retour d'expérience.

---

# 21. Sécurité mobile

Les applications mobiles doivent :

- détecter le root/jailbreak lorsque pertinent ;
- protéger le stockage local ;
- utiliser le coffre-fort sécurisé du système ;
- empêcher les captures d'écran sur les écrans sensibles si nécessaire ;
- protéger contre le reverse engineering.

---

# 22. Sécurité Web

Les sites web doivent appliquer :

- CSP ;
- HSTS ;
- cookies sécurisés ;
- SameSite ;
- protection CSRF ;
- limitation des sessions ;
- validation stricte.

---

# 23. Sécurité TPE

Le TPE doit protéger :

- les clés ;
- les certificats ;
- les mises à jour ;
- le firmware ;
- les journaux ;
- les paiements hors ligne.

Toute tentative de compromission doit être détectée et signalée.

---

# 24. Sécurité des données

Les données doivent être classées :

- publiques ;
- internes ;
- confidentielles ;
- sensibles ;
- hautement sensibles.

Chaque niveau définit :

- chiffrement ;
- accès ;
- conservation ;
- export ;
- audit.

---

# 25. Conformité

Le système doit pouvoir satisfaire les exigences applicables (selon les pays et partenaires), notamment :

- protection des données personnelles ;
- sécurité des paiements ;
- conservation des journaux ;
- lutte contre le blanchiment ;
- auditabilité.

---

# 26. Administration

Le portail Admin doit permettre :

- consulter les événements de sécurité ;
- gérer les politiques ;
- consulter les appareils ;
- gérer les certificats ;
- consulter les alertes ;
- gérer les secrets de référence ;
- suivre les incidents ;
- lancer des audits.

---

# 27. Permissions

Exemples :

```text
security.read
security.policy.manage
security.audit.read
security.incident.manage
security.secret.reference
security.device.revoke
security.certificate.manage
security.export_sensitive
```

---

# 28. API

Exemples :

```http
GET    /security/events
GET    /security/policies
GET    /security/devices

POST   /security/incidents
POST   /security/device/revoke
POST   /security/mfa/reset

GET    /security/certificates
POST   /security/certificates/rotate
```

---

# 29. Modèles

- SecurityPolicy
- SecurityEvent
- SecurityIncident
- Device
- TrustedDevice
- AuthenticationMethod
- Session
- SecretReference
- Certificate
- FraudSignal
- FraudCase
- SecurityAudit

---

# 30. Règles métier

1. Toute requête est authentifiée.
2. Toute action est autorisée avant exécution.
3. Les secrets ne sont jamais stockés dans le code.
4. Les données sensibles sont chiffrées.
5. Les événements de sécurité sont audités.
6. Le MFA protège les opérations critiques.
7. Les appareils peuvent être révoqués.
8. Les sauvegardes sont chiffrées.
9. Les certificats sont surveillés.
10. Les protections réseau sont activées.
11. Les entrées sont validées.
12. Les attaques courantes sont bloquées.
13. Les incidents suivent une procédure officielle.
14. Les données sont classifiées.
15. Les permissions sont minimales.
16. Les accès d'urgence sont tracés.
17. Les partenaires sont authentifiés.
18. Les applications sont versionnées.
19. Les politiques sont administrables.
20. Les tests de sécurité sont obligatoires.

---

# 31. Analytics

Événements possibles :

```text
security_login_success
security_login_failed
security_mfa_required
security_device_registered
security_device_revoked
security_incident_created
security_secret_rotated
security_certificate_expiring
security_fraud_detected
security_policy_updated
```

---

# 32. Tests

- tests MFA ;
- tests RBAC ;
- tests de permissions ;
- tests d'injection ;
- tests XSS ;
- tests CSRF ;
- tests SSRF ;
- tests de chiffrement ;
- tests de rotation des secrets ;
- tests de certificats ;
- tests de fraude ;
- tests de sauvegardes ;
- tests de restauration ;
- tests d'audit ;
- tests d'incidents ;
- tests de charge sécurité.

---

# 33. Critères d'acceptation

La sécurité globale est validée lorsque :

- les utilisateurs sont correctement authentifiés ;
- les permissions sont contrôlées ;
- les secrets sont protégés ;
- les données sensibles sont chiffrées ;
- les appareils sont gérés ;
- les incidents sont tracés ;
- les alertes fonctionnent ;
- les sauvegardes sont sécurisées ;
- les API sont protégées ;
- les tests de sécurité sont validés.
