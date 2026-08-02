# 28 — Stratégie globale de tests, validation, sécurité et performance de Mansa

## 1. Objet du document

Ce document définit la stratégie officielle de tests de Mansa.

Il couvre :

- les tests unitaires ;
- les tests d’intégration ;
- les tests End-to-End ;
- les tests de contrats ;
- les tests de base de données ;
- les tests Prisma ;
- les tests de migrations ;
- les tests de sécurité ;
- les tests de permissions ;
- les tests de fraude ;
- les tests de charge ;
- les tests de performance ;
- les tests de résilience ;
- les tests mobiles ;
- les tests web ;
- les tests TPE ;
- les tests partenaires ;
- les tests multi-pays ;
- les tests multi-devises ;
- les tests multi-environnements ;
- les tests d’accessibilité ;
- les tests de reprise ;
- les critères de qualité ;
- les rapports ;
- les validations avant production.

L’objectif est de garantir que chaque composant de Mansa soit :

- correct ;
- sécurisé ;
- compatible ;
- stable ;
- performant ;
- résilient ;
- traçable ;
- testable ;
- prêt à évoluer sans régression.

---

# 2. Principes fondamentaux

## 2.1 Les tests font partie du produit

Les tests ne doivent pas être ajoutés uniquement à la fin.

Chaque fonctionnalité doit définir dès sa conception :

- ses scénarios normaux ;
- ses erreurs ;
- ses limites ;
- ses permissions ;
- ses cas extrêmes ;
- ses risques ;
- ses critères d’acceptation.

## 2.2 Les parcours critiques ont la priorité

Les domaines prioritaires sont :

- authentification ;
- paiements ;
- transferts ;
- cartes ;
- ledger ;
- remboursements ;
- KYC/KYB ;
- fraude ;
- permissions ;
- TPE ;
- partenaires ;
- services publics ;
- migrations ;
- configuration critique.

## 2.3 Un test doit être reproductible

Un test doit produire le même résultat dans les mêmes conditions.

Il doit éviter :

- dépendance à des données aléatoires non contrôlées ;
- dépendance à une heure réelle non simulée ;
- dépendance à un partenaire de production ;
- ordre implicite ;
- état résiduel d’un test précédent ;
- accès réseau non maîtrisé.

## 2.4 Les environnements de test utilisent des données fictives

Les tests ne doivent pas utiliser librement :

- vraies identités ;
- vrais numéros de carte ;
- vrais documents ;
- vrais comptes ;
- vrais secrets ;
- vrais tokens ;
- données de production non anonymisées.

## 2.5 La qualité ne dépend pas uniquement de la couverture

La couverture indique quelles lignes sont exécutées, mais pas si les bons scénarios sont testés.

Mansa doit mesurer :

- couverture ;
- scénarios critiques ;
- cas d’erreur ;
- tests de permissions ;
- tests de concurrence ;
- tests de sécurité ;
- tests de reprise ;
- tests de performance ;
- stabilité des tests.

# 3. Pyramide de tests

Structure recommandée :

```text
                 E2E
             Contrats
          Intégration
        Tests unitaires
```

La majorité des tests doivent rester rapides et proches du code métier.

Les tests E2E sont moins nombreux mais couvrent les parcours critiques.

# 4. Tests unitaires

Les tests unitaires couvrent notamment :

- fonctions pures ;
- objets valeur ;
- services de domaine ;
- validations ;
- calculs ;
- frais ;
- commissions ;
- limites ;
- arrondis ;
- conversions ;
- règles d’éligibilité ;
- transitions de statut ;
- décisions de permissions.

# 5. Tests unitaires financiers

Ils doivent couvrir :

- montant zéro ;
- montant négatif interdit ;
- précision ;
- arrondi ;
- devise ;
- frais fixes ;
- frais variables ;
- remboursement partiel ;
- remboursement total ;
- plafond ;
- minimum ;
- maximum ;
- conversion ;
- taux expiré ;
- commission.

# 6. Tests de domaine

Chaque domaine doit vérifier ses invariants.

Exemples :

- une carte bloquée ne peut pas autoriser un paiement ;
- un remboursement ne dépasse pas le montant disponible ;
- une écriture ledger validée n’est pas modifiée ;
- un terminal suspendu ne peut pas prendre de paiement ;
- un KYC insuffisant limite certaines opérations ;
- un rôle expiré ne donne plus accès.

# 7. Tests d’intégration

Ils doivent vérifier les interactions entre :

- services ;
- base de données ;
- Prisma ;
- cache ;
- files ;
- stockage ;
- webhooks ;
- workers ;
- composants backend ;
- partenaires simulés.

# 8. Base de données de test

Les tests d’intégration doivent utiliser une base isolée.

Options possibles :

- conteneur temporaire ;
- base dédiée CI ;
- schéma par exécution ;
- instance éphémère.

Chaque exécution doit nettoyer son état.

# 9. Tests Prisma

Ils couvrent :

- relations ;
- contraintes ;
- enums ;
- transactions ;
- requêtes ;
- index critiques ;
- sélections ;
- pagination ;
- suppressions logiques ;
- concurrence optimiste.

# 10. Tests de migrations

Chaque migration doit être testée sur :

- base vide ;
- base avec données ;
- données invalides attendues ;
- volume réaliste ;
- ancienne version ;
- rollback ou stratégie de retour ;
- compatibilité avec le code précédent ;
- compatibilité avec le nouveau code.

# 11. Tests de contrats

Les contrats doivent être testés entre :

- applications mobiles et API ;
- sites web et API ;
- TPE et API ;
- services internes ;
- événements ;
- webhooks ;
- partenaires ;
- SDK.

# 12. Consumer-Driven Contracts

Chaque consommateur peut déclarer ce qu’il attend d’un fournisseur.

Exemples :

- Mansa Client attend certains champs de `/wallets` ;
- Mansa TPE attend certains statuts de paiement ;
- le partenaire attend une structure de webhook ;
- le service notification attend une version d’événement.

# 13. Tests OpenAPI

La CI doit pouvoir vérifier :

- schéma valide ;
- routes documentées ;
- réponses ;
- erreurs ;
- changements cassants ;
- paramètres ;
- authentification ;
- version.

# 14. Tests d’événements

Ils couvrent :

- schéma ;
- version ;
- producteur ;
- consommateur ;
- champs obligatoires ;
- compatibilité ;
- ordre ;
- doublon ;
- rejet de version inconnue ;
- Outbox ;
- Inbox.

# 15. Tests de webhooks

Ils couvrent :

- signature valide ;
- signature invalide ;
- secret expiré ;
- timestamp invalide ;
- événement dupliqué ;
- payload invalide ;
- endpoint indisponible ;
- retry ;
- dead-letter queue ;
- rejeu ;
- ordre ;
- timeout.

# 16. Tests End-to-End

Les tests E2E couvrent un parcours complet.

Exemples :

- inscription utilisateur ;
- connexion ;
- KYC ;
- création de wallet ;
- transfert ;
- paiement ;
- réception de notification ;
- consultation de reçu ;
- support.

# 17. Parcours E2E Client

Scénarios minimum :

- création de compte ;
- vérification de téléphone ;
- connexion ;
- récupération d’accès ;
- ajout bénéficiaire ;
- envoi d’argent ;
- paiement QR ;
- création de carte virtuelle ;
- gel de carte ;
- consultation d’historique ;
- téléchargement d’un reçu ;
- clôture de session.

# 18. Parcours E2E Commerce

Scénarios minimum :

- création commerce ;
- KYB ;
- ajout établissement ;
- ajout employé ;
- création produit ;
- gestion de stock ;
- vente ;
- remboursement ;
- facture ;
- règlement ;
- rapport.

# 19. Parcours E2E TPE

Scénarios minimum :

- activation terminal ;
- connexion employé ;
- paiement réussi ;
- paiement refusé ;
- timeout ;
- impression ;
- remboursement ;
- clôture ;
- perte réseau ;
- reprise ;
- synchronisation ;
- mise à jour.

# 20. Parcours E2E Admin

Scénarios minimum :

- connexion renforcée ;
- recherche utilisateur ;
- consultation limitée ;
- changement de configuration ;
- validation ;
- double approbation ;
- export ;
- journal d’audit ;
- révocation d’accès ;
- incident.

# 21. Tests de permissions

Chaque permission doit être testée au minimum sur :

- acteur autorisé ;
- acteur interdit ;
- rôle incomplet ;
- rôle expiré ;
- tenant différent ;
- pays différent ;
- environnement différent ;
- accès temporaire ;
- délégation ;
- accès d’urgence.

# 22. Tests RBAC et ABAC

Ils couvrent :

- héritage ;
- conflits ;
- portée ;
- montant ;
- pays ;
- organisation ;
- niveau KYC ;
- appareil ;
- horaire ;
- état de la ressource ;
- contexte de risque.

# 23. Tests de sécurité

Catégories :

- SAST ;
- DAST ;
- scan dépendances ;
- scan secrets ;
- scan images ;
- scan IaC ;
- tests d’injection ;
- tests d’autorisation ;
- tests d’authentification ;
- tests de session ;
- tests de chiffrement ;
- tests de certificats.

# 24. Tests d’injection

Ils doivent couvrir notamment :

- SQL Injection ;
- NoSQL Injection si applicable ;
- XSS ;
- CSRF ;
- SSRF ;
- Command Injection ;
- Path Traversal ;
- Template Injection ;
- Header Injection.

# 25. Tests d’authentification

Scénarios :

- mot de passe correct ;
- mot de passe incorrect ;
- compte bloqué ;
- OTP valide ;
- OTP expiré ;
- OTP déjà utilisé ;
- MFA requis ;
- appareil inconnu ;
- session révoquée ;
- token expiré ;
- refresh token réutilisé ;
- passkey invalide.

# 26. Tests de session

Ils couvrent :

- expiration ;
- renouvellement ;
- révocation ;
- déconnexion distante ;
- multi-appareils ;
- session inactive ;
- changement de mot de passe ;
- changement de téléphone ;
- session privilégiée ;
- accès d’urgence.

# 27. Tests de chiffrement

Ils doivent vérifier :

- chiffrement au repos ;
- chiffrement en transit ;
- rotation de clé ;
- données anciennes ;
- erreurs de déchiffrement ;
- accès non autorisé ;
- sauvegardes ;
- exports ;
- documents.

# 28. Tests de secrets

Ils couvrent :

- absence dans Git ;
- absence dans les logs ;
- rotation ;
- révocation ;
- secret expiré ;
- double secret pendant transition ;
- permissions ;
- environnement.

# 29. Tests de fraude

Scénarios :

- montant inhabituel ;
- nouvel appareil ;
- localisation inhabituelle ;
- fréquence élevée ;
- bénéficiaire risqué ;
- comportement automatisé ;
- tentative répétée ;
- carte compromise ;
- faux positif ;
- escalade manuelle.

# 30. Tests KYC/KYB

Ils couvrent :

- document valide ;
- document expiré ;
- document illisible ;
- document falsifié simulé ;
- selfie invalide ;
- preuve de vie échouée ;
- bénéficiaire effectif manquant ;
- sanctions ;
- PEP ;
- revue manuelle ;
- expiration du dossier.

# 31. Tests ledger

Ils doivent couvrir :

- double entrée ;
- équilibre ;
- débit ;
- crédit ;
- réservation ;
- libération ;
- contre-écriture ;
- remboursement ;
- ajustement ;
- devise ;
- clôture ;
- reconstruction de solde ;
- concurrence ;
- idempotence.

# 32. Tests de paiement

Scénarios :

- succès ;
- refus ;
- échec ;
- pending ;
- timeout ;
- statut inconnu ;
- webhook tardif ;
- confirmation API ;
- doublon ;
- retry ;
- remboursement ;
- remboursement partiel ;
- annulation ;
- rapprochement.

# 33. Tests Mobile Money

Scénarios :

- opérateur actif ;
- opérateur indisponible ;
- numéro invalide ;
- timeout ;
- confirmation tardive ;
- webhook dupliqué ;
- montant hors limite ;
- frais ;
- cash-in ;
- cash-out ;
- rapprochement.

# 34. Tests cartes

Ils couvrent :

- création ;
- activation ;
- gel ;
- dégel ;
- blocage ;
- remplacement ;
- PIN ;
- plafond ;
- autorisation ;
- refus ;
- capture ;
- remboursement ;
- tokenisation ;
- wallet provisioning ;
- carte virtuelle ;
- carte temporaire.

# 35. Tests multi-devise

Scénarios :

- devise identique ;
- conversion ;
- taux expiré ;
- taux absent ;
- arrondi ;
- devise sans décimale ;
- devise à deux décimales ;
- frais ;
- conversion inversée ;
- remboursement après variation de taux.

# 36. Tests multi-pays

Ils couvrent :

- pays actif ;
- pays non actif ;
- partenaire différent ;
- KYC différent ;
- limite différente ;
- langue ;
- fuseau ;
- devise ;
- données localisées ;
- fonctionnalité interdite ;
- version différente.

# 37. Tests multi-tenant

Scénarios :

- accès à son organisation ;
- accès à une autre organisation refusé ;
- export ;
- recherche ;
- partage de ressource ;
- rôle multi-organisation ;
- tenant suspendu ;
- suppression ;
- cache ;
- file ;
- événement.

# 38. Tests de configuration

Ils couvrent :

- valeur par défaut ;
- valeur pays ;
- valeur partenaire ;
- héritage ;
- priorité ;
- valeur invalide ;
- expiration ;
- planification ;
- rollback ;
- cache ;
- mode hors ligne ;
- double validation.

# 39. Tests de feature flags

Scénarios :

- activé ;
- désactivé ;
- ciblage ;
- pourcentage ;
- pays ;
- partenaire ;
- version ;
- cohorte ;
- kill switch ;
- expiration ;
- conflit ;
- rollback.

# 40. Tests de notifications

Ils couvrent :

- push ;
- SMS ;
- e-mail ;
- préférence ;
- consentement ;
- plage silencieuse ;
- retry ;
- fallback ;
- duplication ;
- template ;
- langue ;
- contenu sensible ;
- écran verrouillé.

# 41. Tests Jini

Ils doivent couvrir :

- permissions ;
- données accessibles ;
- données interdites ;
- outils autorisés ;
- escalade ;
- erreur ;
- hallucination contrôlée par validation métier ;
- action financière ;
- journalisation ;
- langue ;
- version ;
- coût ;
- timeout.

# 42. Tests mobiles

Les applications mobiles doivent être testées sur :

- plusieurs tailles d’écran ;
- plusieurs versions OS ;
- appareils peu puissants ;
- mémoire faible ;
- réseau lent ;
- réseau instable ;
- mode avion ;
- arrière-plan ;
- reprise ;
- biométrie ;
- caméra ;
- NFC ;
- notifications.

# 43. Tests iOS

Ils couvrent :

- versions minimales ;
- Face ID/Touch ID ;
- Keychain ;
- notifications ;
- deep links ;
- App Store build ;
- permissions ;
- mode sombre ;
- VoiceOver ;
- interruption ;
- restauration.

# 44. Tests Android

Ils couvrent :

- versions minimales ;
- constructeurs ;
- biométrie ;
- Keystore ;
- notifications ;
- deep links ;
- services Google ;
- appareil sans services Google si ciblé ;
- TalkBack ;
- gestion batterie ;
- reprise.

# 45. Tests SQLite local

Ils couvrent :

- création ;
- migration ;
- corruption simulée ;
- cache ;
- brouillons ;
- synchronisation ;
- conflits ;
- nettoyage ;
- chiffrement ;
- reprise ;
- suppression ;
- expiration.

# 46. Tests Web

Ils couvrent :

- navigateurs ;
- tailles ;
- responsive ;
- JavaScript désactivé lorsque pertinent ;
- cookies ;
- sessions ;
- CSP ;
- CSRF ;
- navigation clavier ;
- Core Web Vitals ;
- erreurs réseau ;
- preview.

# 47. Tests TPE matériels

Ils doivent être exécutés sur les modèles réels ciblés.

Ils couvrent :

- NFC ;
- puce ;
- sans contact ;
- imprimante ;
- scanner ;
- batterie ;
- réseau ;
- redémarrage ;
- mode kiosque ;
- mise à jour ;
- stockage ;
- certificat ;
- sécurité physique.

# 48. Tests partenaires

Chaque connecteur doit être testé avec :

- mocks ;
- sandbox ;
- préproduction ;
- réponses valides ;
- réponses invalides ;
- timeout ;
- 4xx ;
- 5xx ;
- 429 ;
- certificat expiré ;
- webhook absent ;
- doublon ;
- rapprochement.

# 49. Tests de charge

Ils doivent mesurer :

- requêtes par seconde ;
- utilisateurs simultanés ;
- paiements ;
- transferts ;
- lecture de solde ;
- notifications ;
- files ;
- exports ;
- recherche ;
- TPE ;
- webhooks.

# 50. Types de tests de performance

- load test ;
- stress test ;
- spike test ;
- endurance test ;
- soak test ;
- capacity test ;
- volume test.

# 51. Tests de latence

Mesurer :

- p50 ;
- p75 ;
- p90 ;
- p95 ;
- p99.

Les moyennes seules sont insuffisantes.

# 52. Tests de montée en charge

Scénarios :

- lancement national ;
- paiement de salaires ;
- bourses ;
- campagnes ;
- fin de mois ;
- grand événement ;
- panne d’un partenaire ;
- nombreux TPE simultanés ;
- import massif.

# 53. Tests de saturation

Ils doivent vérifier le comportement lorsque :

- CPU est saturé ;
- mémoire est faible ;
- pool base est plein ;
- file est longue ;
- stockage est lent ;
- partenaire limite ;
- cache est indisponible ;
- workers sont insuffisants.

# 54. Tests de résilience

Ils couvrent :

- panne service ;
- panne base ;
- panne cache ;
- panne file ;
- panne stockage ;
- panne partenaire ;
- timeout ;
- latence ;
- redémarrage ;
- perte réseau ;
- bascule ;
- rollback.

# 55. Chaos Testing

Des tests contrôlés peuvent simuler :

- arrêt d’instance ;
- perte réseau ;
- latence ;
- erreur DNS ;
- certificat invalide ;
- indisponibilité régionale ;
- saturation ;
- suppression d’un worker.

Ils doivent être exécutés de manière maîtrisée.

# 56. Tests de reprise

Ils couvrent :

- redémarrage application ;
- reprise de job ;
- reprise de saga ;
- rejeu ;
- restauration ;
- failover ;
- reprise TPE ;
- reprise mobile ;
- statut inconnu ;
- reconstruction de solde.

# 57. Tests de sauvegarde

Ils doivent vérifier :

- création ;
- chiffrement ;
- intégrité ;
- rétention ;
- disponibilité ;
- restauration ;
- point-in-time recovery ;
- données après restauration ;
- permissions.

# 58. Tests de restauration

Une restauration doit être validée par :

- démarrage service ;
- cohérence base ;
- intégrité ledger ;
- disponibilité documents ;
- reprise des files ;
- vérification utilisateurs ;
- test d’opérations ;
- audit.

# 59. Tests d’accessibilité

Ils couvrent :

- lecteur d’écran ;
- navigation clavier ;
- contraste ;
- tailles de texte ;
- zoom ;
- focus ;
- labels ;
- erreurs ;
- animations réduites ;
- touch targets ;
- daltonisme.

# 60. Tests visuels

Ils peuvent détecter :

- régression UI ;
- débordement ;
- mauvaise police ;
- composant cassé ;
- mode sombre ;
- responsive ;
- erreur de thème ;
- changement de token.

# 61. Snapshot Testing

Les snapshots peuvent être utilisés avec prudence.

Ils ne doivent pas remplacer la vérification fonctionnelle.

# 62. Tests de localisation

Ils couvrent :

- français ;
- anglais ;
- langues ciblées ;
- texte long ;
- pluriels ;
- dates ;
- montants ;
- devises ;
- sens de lecture si nécessaire ;
- caractères spéciaux ;
- troncature.

# 63. Tests d’erreurs

Chaque endpoint important doit être testé sur :

- validation ;
- authentification ;
- autorisation ;
- ressource absente ;
- conflit ;
- limite ;
- erreur partenaire ;
- timeout ;
- erreur interne ;
- statut inconnu.

# 64. Tests de corrélation

Vérifier que les identifiants traversent :

- API ;
- service ;
- file ;
- worker ;
- partenaire ;
- webhook ;
- ledger ;
- notification ;
- audit.

# 65. Tests d’observabilité

Ils doivent vérifier :

- métrique émise ;
- log structuré ;
- trace ;
- health check ;
- alerte ;
- masquage ;
- absence de secret ;
- version ;
- pays ;
- environnement.

# 66. Tests de logs sensibles

Le pipeline doit vérifier l’absence de :

- mot de passe ;
- OTP ;
- PIN ;
- CVV ;
- token complet ;
- numéro complet de carte ;
- secret ;
- document ;
- données privées non nécessaires.

# 67. Tests de concurrence

Ils couvrent :

- double clic ;
- double requête ;
- deux remboursements ;
- deux mises à jour ;
- deux paiements ;
- deux workers ;
- verrouillage ;
- version optimiste ;
- idempotence ;
- course condition.

# 68. Tests de temps

Simuler :

- expiration ;
- fuseau ;
- changement de jour ;
- fin de mois ;
- année ;
- heure d’été si concernée ;
- date future ;
- date passée ;
- certificat expiré ;
- session expirée ;
- tâche planifiée.

# 69. Données de test

Les données doivent être :

- déterministes ;
- fictives ;
- documentées ;
- isolées ;
- reproductibles ;
- faciles à nettoyer ;
- représentatives ;
- compatibles multi-pays.

# 70. Factories

Des factories peuvent générer :

- utilisateurs ;
- commerces ;
- wallets ;
- paiements ;
- cartes ;
- TPE ;
- dossiers KYC ;
- partenaires ;
- événements ;
- configurations.

# 71. Fixtures

Les fixtures doivent rester petites et ciblées.

Elles ne doivent pas devenir un jeu de données global impossible à maintenir.

# 72. Mocks

Les mocks doivent être utilisés pour isoler une dépendance.

Ils ne doivent pas masquer les problèmes réels d’intégration.

# 73. Simulateurs partenaires

Chaque partenaire critique doit disposer d’un simulateur capable de retourner :

- succès ;
- refus ;
- pending ;
- timeout ;
- erreur ;
- doublon ;
- webhook tardif ;
- réponse invalide ;
- limite ;
- certificat expiré.

# 74. Environnements de test

Séparation recommandée :

- tests unitaires locaux ;
- intégration CI ;
- E2E CI ;
- sandbox partenaires ;
- préproduction ;
- tests matériels ;
- tests de charge isolés.

# 75. Tests en production

Seuls des tests sûrs et contrôlés peuvent être exécutés en production.

Exemples :

- health checks ;
- requêtes synthétiques ;
- monitoring ;
- test de lecture ;
- transaction technique encadrée ;
- webhook de test autorisé.

# 76. Synthetic Monitoring

Des scénarios synthétiques peuvent vérifier régulièrement :

- connexion ;
- consultation ;
- API ;
- paiement simulé ;
- partenaire ;
- site public ;
- certificat ;
- TPE de test.

# 77. Critères d’entrée en test

Une fonctionnalité peut entrer en test lorsqu’elle possède :

- spécification ;
- critères d’acceptation ;
- code compilable ;
- dépendances disponibles ;
- environnement ;
- données ;
- instrumentation ;
- version.

# 78. Critères de sortie

Une fonctionnalité est validée lorsque :

- scénarios critiques réussis ;
- bugs bloquants corrigés ;
- permissions validées ;
- sécurité validée ;
- performance acceptable ;
- observabilité présente ;
- documentation mise à jour ;
- rollback prévu.

# 79. Gravité des défauts

## 79.1 Bloquant

- perte financière ;
- faille critique ;
- corruption ;
- impossibilité d’utiliser le service ;
- mauvais solde ;
- permission contournée.

## 79.2 Majeur

- fonctionnalité critique incorrecte ;
- partenaire principal bloqué ;
- parcours essentiel impossible ;
- données incohérentes.

## 79.3 Modéré

- fonctionnalité secondaire ;
- contournement disponible ;
- erreur non financière.

## 79.4 Mineur

- texte ;
- alignement ;
- défaut visuel ;
- comportement sans impact important.

# 80. Gestion des anomalies

Chaque anomalie doit contenir :

- titre ;
- description ;
- environnement ;
- version ;
- étapes ;
- résultat attendu ;
- résultat observé ;
- gravité ;
- preuves ;
- logs ;
- corrélation ;
- propriétaire ;
- statut.

# 81. Régression

Chaque bug corrigé doit recevoir un test de non-régression lorsque pertinent.

# 82. Flaky Tests

Un test instable doit être :

- identifié ;
- suivi ;
- corrigé ;
- temporairement isolé si nécessaire ;
- interdit comme excuse permanente.

# 83. Quarantaine

La quarantaine doit être limitée dans le temps.

Elle doit contenir :

- propriétaire ;
- raison ;
- date ;
- échéance ;
- ticket ;
- impact.

# 84. Rapports

Les rapports doivent inclure :

- tests exécutés ;
- réussites ;
- échecs ;
- ignorés ;
- durée ;
- couverture ;
- environnement ;
- version ;
- artefact ;
- anomalies ;
- tendances.

# 85. Dashboards de qualité

Ils peuvent afficher :

- taux de réussite ;
- temps de pipeline ;
- couverture ;
- flaky tests ;
- bugs ;
- régressions ;
- performance ;
- sécurité ;
- dette ;
- stabilité par application.

# 86. Tendances

Suivre :

- augmentation des erreurs ;
- baisse de couverture ;
- ralentissement ;
- hausse des bugs ;
- tests instables ;
- temps de correction ;
- défauts par domaine ;
- incidents après déploiement.

# 87. Quality Gates

Une fusion ou un déploiement peut être bloqué si :

- tests critiques échouent ;
- lint échoue ;
- typecheck échoue ;
- build échoue ;
- scan critique échoue ;
- migration invalide ;
- couverture critique baisse ;
- contrat cassé ;
- test de permission échoue.

# 88. Exceptions

Une exception doit être :

- rare ;
- justifiée ;
- approuvée ;
- limitée ;
- tracée ;
- assortie d’un plan de correction.

# 89. Validation manuelle

Certains domaines nécessitent une validation humaine :

- UX ;
- accessibilité ;
- TPE ;
- documents ;
- parcours KYC ;
- incidents ;
- communication ;
- intégrations institutionnelles.

# 90. Recette métier

La recette doit être effectuée par des personnes représentant :

- produit ;
- finance ;
- conformité ;
- support ;
- sécurité ;
- opérations ;
- pays ;
- partenaire.

# 91. Tests de conformité

Ils couvrent selon les règles applicables :

- KYC ;
- AML ;
- sanctions ;
- conservation ;
- consentement ;
- droits ;
- audit ;
- limites ;
- reporting ;
- services publics.

# 92. Tests de documents

Ils couvrent :

- reçus ;
- factures ;
- relevés ;
- contrats ;
- CGU ;
- documents KYC ;
- rapports ;
- PDF ;
- impression ;
- traduction ;
- version.

# 93. Tests de compatibilité ascendante

Vérifier que :

- ancienne application fonctionne avec nouveau backend ;
- nouveau backend accepte ancien contrat supporté ;
- nouvel événement ne casse pas les consommateurs ;
- nouvelle configuration conserve les valeurs par défaut ;
- migration reste compatible pendant le déploiement.

# 94. Tests de compatibilité descendante

Vérifier lorsque nécessaire que :

- rollback applicatif reste possible ;
- anciennes données restent lisibles ;
- ancienne version du service peut fonctionner temporairement ;
- nouvelle base ne bloque pas le code précédent.

# 95. Tests de version

Ils couvrent :

- version minimale ;
- version recommandée ;
- version obligatoire ;
- version bloquée ;
- mode dégradé ;
- appareil non compatible ;
- API dépréciée ;
- TPE obsolète.

# 96. Tests de déploiement

Ils couvrent :

- rolling ;
- blue/green ;
- canary ;
- migration ;
- smoke tests ;
- rollback ;
- feature flags ;
- monitoring ;
- trafic partiel.

# 97. Tests de rollback

Ils doivent vérifier :

- retour d’artefact ;
- retour de configuration ;
- désactivation de fonctionnalité ;
- compatibilité base ;
- reprise ;
- absence de perte ;
- audit ;
- métriques.

# 98. Tests de release mobile

Ils couvrent :

- signature ;
- version ;
- build ;
- installation ;
- mise à jour ;
- conservation des données ;
- migration SQLite ;
- store ;
- crash symbols ;
- notification.

# 99. Tests de mise à jour TPE

Ils couvrent :

- téléchargement ;
- signature ;
- batterie ;
- espace ;
- interruption ;
- reprise ;
- rollback ;
- matériel ;
- configuration ;
- certificat.

# 100. Responsabilités

Chaque domaine doit avoir des responsables de test.

Exemples :

- backend ;
- mobile ;
- web ;
- TPE ;
- sécurité ;
- infrastructure ;
- base ;
- produit ;
- conformité ;
- partenaires.

# 101. Permissions

Exemples :

```text
testing.read
testing.run
testing.result.read
testing.environment.manage
testing.data.manage
testing.performance.run
testing.security.run
testing.production.synthetic.run
testing.quality_gate.override
testing.audit.read
```

# 102. Actions critiques

Doivent être protégées :

- test de charge en production ;
- test destructif ;
- chaos test ;
- modification de données ;
- réinitialisation environnement ;
- override quality gate ;
- utilisation de secrets partenaires ;
- test financier réel.

# 103. Double validation

Peut être exigée pour :

- test production ;
- test de reprise ;
- chaos test ;
- test financier ;
- suppression de données ;
- override sécurité ;
- désactivation d’un quality gate.

# 104. API internes

Exemples :

```http
GET    /testing/runs
GET    /testing/runs/{id}
GET    /testing/reports
GET    /testing/quality-gates
GET    /testing/environments

POST   /testing/runs
POST   /testing/performance-runs
POST   /testing/security-runs
POST   /testing/quality-gates/{id}/override
```

# 105. Modèles

- TestPlan
- TestSuite
- TestCase
- TestExecution
- TestResult
- TestEnvironment
- TestDataSet
- TestArtifact
- TestDefect
- RegressionTest
- PerformanceTest
- SecurityTest
- ContractTest
- QualityGate
- QualityGateOverride
- TestReport
- TestAudit

# 106. Règles métier

1. Chaque fonctionnalité critique possède des tests.
2. Les tests sont reproductibles.
3. Les données de test sont fictives.
4. Les tests unitaires couvrent les règles métier.
5. Les tests d’intégration utilisent des dépendances contrôlées.
6. Les contrats sont testés.
7. Les permissions sont testées.
8. Le ledger possède une couverture renforcée.
9. Les paiements couvrent les statuts incertains.
10. Les partenaires sont simulables.
11. Les migrations sont testées.
12. Les applications mobiles sont testées sur appareils variés.
13. Les TPE sont testés sur matériel réel.
14. Les tests de charge utilisent des objectifs définis.
15. Les tests de résilience couvrent les pannes critiques.
16. Les sauvegardes sont restaurées régulièrement.
17. L’accessibilité est testée.
18. Les secrets ne figurent pas dans les résultats.
19. Les bugs corrigés reçoivent un test de non-régression.
20. Les flaky tests sont suivis.
21. Les quality gates bloquent les changements dangereux.
22. Les overrides sont audités.
23. Les tests production sont limités.
24. Les rapports sont conservés.
25. Les résultats sont reliés à une version et un artefact.

# 107. Analytics

Événements possibles :

```text
test_plan_created
test_execution_started
test_execution_completed
test_execution_failed
test_case_failed
test_regression_detected
test_flaky_detected
test_performance_threshold_exceeded
test_security_issue_detected
test_contract_breaking_change_detected
test_quality_gate_failed
test_quality_gate_overridden
test_restore_completed
test_chaos_experiment_started
test_production_synthetic_failed
```

# 108. Critères d’acceptation

La stratégie de tests est validée lorsque :

- les niveaux de tests sont définis ;
- les parcours critiques sont couverts ;
- les règles financières sont testées ;
- les permissions sont testées ;
- les contrats sont validés ;
- les migrations sont testées ;
- les partenaires sont simulables ;
- les tests mobiles couvrent plusieurs appareils ;
- les TPE sont testés sur matériel réel ;
- les tests de performance ont des seuils ;
- les tests de résilience existent ;
- les sauvegardes sont restaurées ;
- les tests d’accessibilité sont exécutés ;
- les flaky tests sont suivis ;
- les quality gates sont actifs ;
- les rapports sont liés aux versions ;
- les tests couvrent les principaux risques.
