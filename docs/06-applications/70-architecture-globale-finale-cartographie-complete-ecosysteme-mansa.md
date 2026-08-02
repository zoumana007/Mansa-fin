# 70 — Architecture globale finale et cartographie complète de l’écosystème Mansa

## 1. Objet du document

Ce document définit l’**architecture globale finale de Mansa** ainsi que la cartographie complète de ses applications, services, utilisateurs, partenaires, infrastructures, flux financiers, flux techniques et responsabilités administratives.

Il constitue la vue de référence permettant de comprendre comment tous les composants de Mansa fonctionnent ensemble.

Il couvre notamment :

- les applications mobiles ;
- les portails web ;
- les interfaces administratives ;
- les services backend ;
- le ledger ;
- les wallets ;
- les cartes ;
- les paiements ;
- les transferts ;
- les agents ;
- les commerçants ;
- les TPE ;
- les GAB et DAB ;
- le Mobile Money ;
- les banques partenaires ;
- les institutions publiques ;
- les écoles ;
- les entreprises ;
- les partenaires techniques ;
- la sécurité ;
- la fraude ;
- le KYC et le KYB ;
- la Finance ;
- la Data ;
- Jini ;
- les notifications ;
- la supervision ;
- la documentation ;
- les tests ;
- les versions ;
- le déploiement ;
- la continuité d’activité ;
- l’administration centrale.

L’objectif est de fournir une architecture :

- modulaire ;
- évolutive ;
- sécurisée ;
- multi-pays ;
- multi-devises ;
- multi-partenaire ;
- hautement disponible ;
- auditable ;
- administrable ;
- compatible avec une montée en charge nationale puis régionale.

---

# 2. Vision générale

Mansa doit être conçue comme une plateforme financière complète reliant :

```text
Clients
→ Commerçants
→ Agents
→ TPE
→ GAB/DAB
→ Banques
→ Mobile Money
→ Entreprises
→ Écoles
→ Institutions publiques
→ Partenaires
```

Tous les acteurs doivent utiliser une infrastructure commune tout en conservant des interfaces adaptées à leurs rôles.

---

# 3. Principes architecturaux

L’architecture repose sur les principes suivants :

- séparation claire des responsabilités ;
- services faiblement couplés ;
- sécurité par défaut ;
- configuration centralisée ;
- événements traçables ;
- aucune opération financière sans écriture ledger ;
- aucune action sensible sans autorisation ;
- aucune modification critique sans audit ;
- compatibilité multi-pays ;
- compatibilité avec les réseaux faibles ;
- reprise après incident ;
- observabilité complète ;
- automatisation des tests et déploiements ;
- possibilité de remplacer un fournisseur sans réécrire toute la plateforme.

---

# 4. Vue d’ensemble des couches

Architecture recommandée :

```text
Utilisateurs et appareils
→ Applications et portails
→ API Gateway
→ Services métier
→ Ledger et services financiers
→ Intégrations partenaires
→ Données et événements
→ Infrastructure et sécurité
→ Administration et supervision
```

---

# 5. Couche Utilisateurs

Les catégories principales sont :

- client particulier ;
- client premium ;
- commerçant ;
- employé commerçant ;
- agent ;
- superviseur agent ;
- technicien ;
- administrateur ;
- support ;
- analyste fraude ;
- analyste Finance ;
- analyste Data ;
- entreprise ;
- employé d’entreprise ;
- école ;
- étudiant ;
- institution ;
- agent public ;
- partenaire bancaire ;
- opérateur Mobile Money ;
- développeur partenaire ;
- auditeur.

---

# 6. Applications principales

L’écosystème Mansa comprend notamment :

1. Application Client.
2. Application Commerce.
3. Application Agent.
4. Application TPE.
5. Application Admin Lite.
6. Portail Admin Web.
7. Site vitrine Mansa.
8. Portail Développeurs.
9. Portail Entreprises.
10. Portail Éducation.
11. Portail Institutions.
12. Centre de Support.
13. Back-office Finance.
14. Back-office Fraude.
15. Back-office Data.
16. Console d’Observabilité.
17. Console de Conformité.
18. Logiciel GAB/DAB.
19. Outils de Maintenance.
20. Portail Partenaires.

---

# 7. Application Client

L’application Client permet notamment :

- création de compte ;
- authentification ;
- KYC ;
- consultation du solde ;
- historique ;
- transfert ;
- paiement ;
- recharge ;
- dépôt ;
- retrait ;
- cartes ;
- coffres ;
- budgets ;
- abonnements ;
- QR ;
- NFC ;
- factures ;
- fidélité ;
- support ;
- notifications ;
- Jini ;
- sécurité ;
- gestion des appareils.

---

# 8. Application Commerce

L’application Commerce permet :

- création du compte commerçant ;
- KYB ;
- gestion des points de vente ;
- encaissement ;
- QR ;
- liens de paiement ;
- factures ;
- remboursements ;
- catalogue ;
- employés ;
- caisses ;
- promotions ;
- fidélité ;
- règlement ;
- rapports ;
- support ;
- gestion des TPE.

---

# 9. Application Agent

L’application Agent permet :

- enrôlement ;
- connexion sécurisée ;
- ouverture de caisse ;
- dépôt ;
- retrait ;
- float ;
- commissions ;
- réapprovisionnement ;
- reçu ;
- historique ;
- incident ;
- fermeture de caisse ;
- demande de liquidité ;
- support ;
- gestion de l’appareil.

---

# 10. Application TPE

L’application TPE permet :

- paiement carte ;
- paiement sans contact ;
- paiement QR ;
- Mobile Money ;
- remboursement ;
- annulation ;
- reçu ;
- clôture ;
- offline contrôlé ;
- synchronisation ;
- reporting ;
- mise à jour distante ;
- supervision ;
- support.

---

# 11. Logiciel GAB/DAB

Le logiciel GAB/DAB permet selon le type de machine :

- retrait ;
- dépôt ;
- consultation du solde ;
- mini-relevé ;
- changement de PIN ;
- retrait sans carte ;
- recharge ;
- paiement de factures ;
- transfert ;
- assistance ;
- impression ;
- supervision ;
- gestion des cassettes ;
- gestion des billets ;
- maintenance ;
- sécurité physique et logicielle.

---

# 12. Admin Lite

Admin Lite permet les opérations urgentes et limitées :

- consultation d’alertes ;
- validation restreinte ;
- blocage urgent ;
- consultation d’incidents ;
- suspension ;
- notifications ;
- suivi opérationnel ;
- authentification forte.

---

# 13. Portail Admin Web

Le portail Admin Web centralise :

- utilisateurs ;
- agents ;
- commerçants ;
- cartes ;
- TPE ;
- GAB/DAB ;
- frais ;
- commissions ;
- plafonds ;
- KYC ;
- KYB ;
- fraude ;
- Finance ;
- partenaires ;
- pays ;
- produits ;
- notifications ;
- workflows ;
- rapports ;
- configurations ;
- rôles ;
- permissions ;
- audits.

---

# 14. Site vitrine Mansa

Le site vitrine présente :

- Mansa ;
- produits ;
- chiffres clés ;
- partenaires ;
- sécurité ;
- tarifs ;
- pays ;
- actualités ;
- carrières ;
- support ;
- développeurs ;
- institutions ;
- commerçants ;
- agents ;
- téléchargement des applications.

---

# 15. Portail Développeurs

Le portail Développeurs propose :

- documentation API ;
- SDK ;
- Sandbox ;
- clés de test ;
- webhooks ;
- exemples ;
- changelog ;
- statut des services ;
- support technique ;
- gestion des applications partenaires.

---

# 16. Portail Entreprises

Le portail Entreprises peut couvrir :

- comptes d’entreprise ;
- employés ;
- salaires ;
- dépenses ;
- cartes professionnelles ;
- validations ;
- factures ;
- paiements fournisseurs ;
- budgets ;
- rapports ;
- API ;
- intégration comptable.

---

# 17. Portail Éducation

Le portail Éducation peut couvrir :

- établissements ;
- étudiants ;
- cartes étudiantes ;
- inscriptions ;
- paiements scolaires ;
- bourses ;
- restauration ;
- bibliothèque ;
- transport ;
- présence ;
- justificatifs ;
- rapports.

---

# 18. Portail Institutions

Le portail Institutions peut couvrir :

- amendes ;
- taxes ;
- redevances ;
- bourses ;
- aides ;
- salaires ;
- paiements publics ;
- identités agents ;
- recouvrement ;
- rapprochement ;
- rapports ;
- traçabilité ;
- lutte contre la corruption.

---

# 19. Centre de Support

Le Centre de Support gère :

- tickets ;
- appels ;
- chat ;
- réclamations ;
- litiges ;
- fraude ;
- remboursements ;
- incidents ;
- SLA ;
- escalades ;
- satisfaction ;
- base de connaissances ;
- assistance multi-canal.

---

# 20. Back-office Finance

Le back-office Finance gère :

- ledger ;
- rapprochement ;
- suspenses ;
- règlements ;
- liquidité ;
- commissions ;
- frais ;
- revenus ;
- trésorerie ;
- cantonnement ;
- reporting ;
- clôtures ;
- audits financiers.

---

# 21. Back-office Fraude

Il gère :

- alertes ;
- règles ;
- scoring ;
- cas ;
- investigations ;
- comptes suspects ;
- appareils suspects ;
- transactions suspectes ;
- gel ;
- blocage ;
- escalade ;
- preuve ;
- reporting.

---

# 22. Back-office Data

Il permet :

- indicateurs ;
- tableaux de bord ;
- rapports ;
- segmentation ;
- analyse ;
- qualité des données ;
- export ;
- lineage ;
- modèle analytique ;
- gouvernance ;
- suivi des usages.

---

# 23. Console d’Observabilité

Elle centralise :

- logs ;
- métriques ;
- traces ;
- incidents ;
- alertes ;
- disponibilité ;
- latence ;
- erreurs ;
- files ;
- bases ;
- partenaires ;
- versions ;
- appareils ;
- coûts ;
- capacité.

---

# 24. Console de Conformité

Elle centralise :

- AML ;
- CFT ;
- sanctions ;
- PEP ;
- gel des avoirs ;
- KYC ;
- KYB ;
- alertes ;
- dossiers ;
- déclarations ;
- rapports ;
- politiques ;
- audits ;
- preuves.

---

# 25. API Gateway

L’API Gateway constitue le point d’entrée principal pour :

- applications mobiles ;
- portails web ;
- TPE ;
- GAB/DAB ;
- partenaires ;
- institutions ;
- banques ;
- Mobile Money ;
- développeurs.

Elle doit gérer :

- authentification ;
- autorisation ;
- routage ;
- quotas ;
- rate limiting ;
- versionnement ;
- journalisation ;
- sécurité ;
- transformation ;
- monitoring ;
- protection contre les abus.

---

# 26. Services d’identité

Ils gèrent :

- utilisateurs ;
- organisations ;
- rôles ;
- permissions ;
- sessions ;
- MFA ;
- appareils ;
- biométrie ;
- passkeys ;
- certificats ;
- récupération ;
- révocation.

---

# 27. Service Wallet

Le service Wallet gère :

- wallets clients ;
- wallets commerçants ;
- wallets agents ;
- wallets entreprises ;
- wallets institutions ;
- devises ;
- statuts ;
- soldes ;
- réservations ;
- limites ;
- relations avec le ledger.

---

# 28. Ledger central

Le ledger doit constituer la source de vérité financière.

Il gère :

- comptes ;
- sous-comptes ;
- écritures ;
- débit ;
- crédit ;
- références ;
- statuts ;
- dates ;
- devises ;
- frais ;
- commissions ;
- compensation ;
- annulation ;
- rapprochement ;
- audit.

---

# 29. Service Paiement

Il gère :

- paiement commerçant ;
- paiement QR ;
- paiement NFC ;
- paiement carte ;
- paiement Mobile Money ;
- paiement récurrent ;
- paiement public ;
- paiement scolaire ;
- split payment ;
- paiement fractionné ;
- paiement en masse.

---

# 30. Service Transfert

Il gère :

- transfert Mansa à Mansa ;
- transfert banque ;
- transfert Mobile Money ;
- transfert international ;
- bénéficiaires ;
- limites ;
- frais ;
- conformité ;
- statut ;
- reprise ;
- rapprochement.

---

# 31. Service Cartes

Il gère :

- cartes physiques ;
- cartes virtuelles ;
- cartes jetables ;
- cartes temporaires ;
- activation ;
- PIN ;
- blocage ;
- opposition ;
- tokenisation ;
- limites ;
- autorisation ;
- expiration ;
- remplacement ;
- réseaux cartes.

---

# 32. Service Cash Network

Il gère :

- agents ;
- points de vente ;
- float ;
- caisses ;
- dépôts ;
- retraits ;
- commissions ;
- liquidité ;
- réapprovisionnement ;
- supervision ;
- incidents ;
- zones ;
- performances.

---

# 33. Service GAB/DAB

Il gère :

- machines ;
- transactions ;
- cassettes ;
- billets ;
- dépôts ;
- retraits ;
- maintenance ;
- alarmes ;
- incidents ;
- versions ;
- configurations ;
- sécurité ;
- supervision ;
- rapports.

---

# 34. Service TPE

Il gère :

- terminaux ;
- commerçants ;
- points de vente ;
- transactions ;
- périphériques ;
- mises à jour ;
- configurations ;
- certificats ;
- offline ;
- synchronisation ;
- maintenance ;
- reporting.

---

# 35. Service KYC

Il gère :

- identité ;
- documents ;
- biométrie ;
- vérification ;
- niveau ;
- pays ;
- statut ;
- expiration ;
- revue ;
- recours ;
- fournisseur ;
- audit.

---

# 36. Service KYB

Il gère :

- entreprise ;
- registre ;
- représentant ;
- bénéficiaire effectif ;
- activité ;
- risque ;
- documents ;
- validation ;
- statut ;
- mise à jour ;
- audit.

---

# 37. Service Fraude

Il gère :

- règles ;
- scores ;
- signaux ;
- alertes ;
- modèles ;
- appareils ;
- comportements ;
- listes ;
- cas ;
- décisions ;
- blocages ;
- audits.

---

# 38. Service Notifications

Il gère :

- push ;
- SMS ;
- e-mail ;
- WhatsApp si activé ;
- modèles ;
- langues ;
- préférences ;
- priorités ;
- retries ;
- fournisseurs ;
- statuts ;
- coûts.

---

# 39. Service Facturation

Il gère :

- factures ;
- reçus ;
- avoirs ;
- remboursements ;
- taxes ;
- numérotation ;
- documents ;
- export ;
- conservation ;
- envoi.

---

# 40. Service Fidélité

Il gère :

- points ;
- cashback ;
- niveaux ;
- récompenses ;
- partenaires ;
- campagnes ;
- expiration ;
- utilisation ;
- rapports.

---

# 41. Service Coffres et Budgets

Il gère :

- coffres ;
- objectifs ;
- épargne ;
- règles automatiques ;
- budgets ;
- catégories ;
- alertes ;
- projections ;
- partage ;
- historique.

---

# 42. Service Support

Il gère :

- tickets ;
- conversations ;
- catégories ;
- priorités ;
- SLA ;
- escalades ;
- pièces jointes ;
- remboursements ;
- incidents ;
- satisfaction.

---

# 43. Service Jini

Jini peut intervenir sur :

- assistance client ;
- assistance agent ;
- assistance commerçant ;
- aide administrateur ;
- recherche documentaire ;
- analyse ;
- support ;
- recommandations ;
- automatisation limitée ;
- explication des opérations.

Il doit respecter strictement :

- permissions ;
- confidentialité ;
- limites d’action ;
- validation humaine ;
- traçabilité ;
- sécurité.

---

# 44. Service Configuration

Il centralise :

- pays ;
- devises ;
- modules ;
- frais ;
- commissions ;
- plafonds ;
- langues ;
- produits ;
- rôles ;
- workflows ;
- partenaires ;
- feature flags ;
- paramètres ;
- versions ;
- dates d’effet.

---

# 45. Event Bus

L’Event Bus transporte les événements entre services.

Exemples :

```text
payment.authorized
payment.completed
transfer.created
wallet.credited
wallet.debited
card.blocked
agent.cashout.completed
atm.cash.low
kyc.approved
fraud.alert.created
notification.sent
```

---

# 46. Files de messages

Les files doivent gérer :

- opérations asynchrones ;
- retries ;
- priorités ;
- événements ;
- notifications ;
- partenaires ;
- traitements lourds ;
- reprise ;
- Dead Letter Queue.

---

# 47. Idempotence

Chaque opération sensible doit posséder :

- clé d’idempotence ;
- référence unique ;
- état ;
- résultat ;
- délai ;
- historique ;
- contrôle de doublon.

---

# 48. Bases de données

Les bases principales peuvent inclure :

- PostgreSQL ;
- Redis ;
- stockage objet ;
- moteur de recherche ;
- data warehouse ;
- data lake ;
- base de logs ;
- base analytique ;
- cache ;
- registre de schémas.

---

# 49. PostgreSQL

PostgreSQL peut héberger :

- identité ;
- wallets ;
- ledger ;
- transactions ;
- agents ;
- commerçants ;
- cartes ;
- KYC ;
- KYB ;
- support ;
- configuration ;
- audit ;
- appareils ;
- documents.

---

# 50. Redis

Redis peut être utilisé pour :

- cache ;
- sessions ;
- rate limiting ;
- verrou distribué ;
- files temporaires ;
- feature flags ;
- compteurs ;
- données à expiration courte.

---

# 51. Stockage objet

Il peut contenir :

- documents ;
- justificatifs ;
- reçus ;
- exports ;
- rapports ;
- preuves ;
- sauvegardes ;
- médias ;
- journaux techniques.

---

# 52. Moteur de recherche

Il peut indexer :

- utilisateurs ;
- transactions ;
- documents ;
- tickets ;
- appareils ;
- agents ;
- commerçants ;
- logs ;
- base de connaissances.

---

# 53. Data Platform

La plateforme Data gère :

- ingestion ;
- transformation ;
- déduplication ;
- qualité ;
- stockage ;
- agrégation ;
- modèles ;
- reporting ;
- gouvernance ;
- anonymisation ;
- lineage ;
- sécurité.

---

# 54. Flux de paiement commerçant

Exemple :

```text
Client
→ Application ou carte
→ TPE / QR / Commerce
→ API Gateway
→ Authentification
→ Risk Engine
→ Service Paiement
→ Ledger
→ Wallet commerçant
→ Notification
→ Règlement
```

---

# 55. Flux de dépôt Agent

```text
Client remet les espèces
→ Agent ouvre Mansa Agent
→ Identification du client
→ Contrôle float et limites
→ Service Cash Network
→ Ledger
→ Crédit wallet client
→ Débit float agent
→ Commission
→ Reçu
→ Notification ou SMS
```

Le client ne valide pas le dépôt dans son application.

---

# 56. Flux de retrait Agent

```text
Client demande un retrait
→ Agent saisit le montant
→ Vérification solde et liquidité
→ Authentification du client
→ Ledger
→ Débit wallet client
→ Crédit float agent
→ Remise des espèces
→ Reçu
→ Commission
```

---

# 57. Flux de retrait GAB/DAB

```text
Client
→ Carte / QR / code
→ Authentification
→ GAB/DAB
→ API Gateway
→ Service GAB/DAB
→ Risk Engine
→ Ledger
→ Autorisation
→ Distribution des billets
→ Confirmation
→ Reçu
→ Notification
```

---

# 58. Flux de dépôt GAB

```text
Client
→ Identification
→ Insertion des billets
→ Validation des billets
→ Comptage
→ Contrôle fraude
→ Ledger
→ Crédit du wallet
→ Stockage ou recyclage des billets
→ Reçu
→ Notification
```

---

# 59. Flux Mobile Money

```text
Client
→ Mansa
→ Connecteur Mobile Money
→ Opérateur
→ Confirmation
→ Ledger Mansa
→ Notification
→ Rapprochement
```

---

# 60. Flux bancaire

```text
Mansa
→ Connecteur bancaire
→ Banque partenaire
→ Compte de cantonnement ou compte technique
→ Confirmation
→ Ledger
→ Rapprochement
→ Reporting
```

---

# 61. Flux réseau cartes

```text
Carte
→ TPE ou GAB
→ Acquéreur
→ Réseau cartes
→ Émetteur
→ Autorisation
→ Ledger
→ Compensation
→ Règlement
→ Rapprochement
```

---

# 62. Flux de commission

```text
Transaction
→ Calcul des frais
→ Calcul des commissions
→ Répartition
→ Écriture ledger
→ Comptes Mansa / Agent / Banque / Partenaire
→ Reporting
```

---

# 63. Flux de remboursement

```text
Demande
→ Vérification
→ Autorisation
→ Service Paiement
→ Ledger
→ Annulation ou écriture compensatoire
→ Notification
→ Rapprochement
```

---

# 64. Architecture partenaires

Chaque partenaire doit utiliser :

- identifiant ;
- contrat ;
- environnement ;
- API ;
- certificat ;
- authentification ;
- quotas ;
- webhooks ;
- SLA ;
- monitoring ;
- support ;
- audit.

---

# 65. Connecteurs partenaires

Connecteurs possibles :

- banque ;
- Mobile Money ;
- réseau cartes ;
- KYC ;
- SMS ;
- e-mail ;
- cloud ;
- géolocalisation ;
- assurance ;
- opérateur télécom ;
- institution ;
- école ;
- entreprise.

---

# 66. Abstraction des partenaires

Le code métier ne doit pas dépendre directement d’un fournisseur précis.

Exemple :

```text
NotificationService
→ SMSProviderInterface
→ Fournisseur A ou Fournisseur B
```

---

# 67. Circuit Breaker

Chaque connecteur critique doit gérer :

- timeout ;
- erreur ;
- retry ;
- circuit breaker ;
- fallback ;
- file d’attente ;
- statut ;
- alerte ;
- reprise.

---

# 68. Sécurité globale

La sécurité couvre :

- identité ;
- accès ;
- MFA ;
- appareils ;
- chiffrement ;
- clés ;
- certificats ;
- HSM ;
- réseau ;
- code ;
- données ;
- partenaires ;
- logs ;
- surveillance ;
- réponse à incident ;
- sauvegardes.

---

# 69. Zero Trust

Chaque requête doit être vérifiée selon :

- identité ;
- rôle ;
- permission ;
- appareil ;
- contexte ;
- risque ;
- localisation éventuelle ;
- environnement ;
- ressource ;
- sensibilité.

---

# 70. RBAC et ABAC

Mansa peut combiner :

- RBAC : droits selon le rôle ;
- ABAC : droits selon les attributs.

Exemples d’attributs :

- pays ;
- organisation ;
- niveau KYC ;
- risque ;
- appareil ;
- environnement ;
- heure ;
- localisation ;
- montant.

---

# 71. Chiffrement

Le chiffrement doit couvrir :

- données au repos ;
- données en transit ;
- bases ;
- sauvegardes ;
- stockage ;
- appareils ;
- fichiers ;
- communications partenaires ;
- clés ;
- secrets.

---

# 72. HSM

Le HSM peut protéger :

- clés de cartes ;
- clés PIN ;
- clés de signature ;
- certificats ;
- clés de chiffrement ;
- clés partenaires ;
- clés TPE ;
- clés GAB/DAB.

---

# 73. Gestion des secrets

Les secrets doivent être :

- centralisés ;
- chiffrés ;
- rotatifs ;
- limités ;
- versionnés ;
- audités ;
- séparés par environnement ;
- non stockés dans Git.

---

# 74. Zones réseau

L’infrastructure peut être segmentée en :

- zone publique ;
- zone API ;
- zone services ;
- zone données ;
- zone paiement ;
- zone administration ;
- zone sécurité ;
- zone partenaires ;
- zone TPE ;
- zone GAB/DAB ;
- zone sauvegarde.

---

# 75. Environnements

Environnements recommandés :

- LOCAL ;
- DEVELOPMENT ;
- TEST ;
- DEMO ;
- RECETTE ;
- SANDBOX ;
- PREPRODUCTION ;
- PRODUCTION ;
- PERFORMANCE ;
- SECURITY ;
- DISASTER_RECOVERY.

---

# 76. Séparation des environnements

Chaque environnement doit avoir :

- données séparées ;
- secrets séparés ;
- clés séparées ;
- certificats séparés ;
- accès séparés ;
- partenaires séparés ;
- logs séparés ;
- coûts séparés ;
- pipelines séparées.

---

# 77. Infrastructure as Code

L’infrastructure doit être décrite dans du code pour :

- reproductibilité ;
- revue ;
- versionnement ;
- déploiement ;
- restauration ;
- audit ;
- sécurité ;
- multi-région ;
- multi-pays.

---

# 78. Conteneurs

Les services peuvent être déployés sous forme de conteneurs avec :

- images signées ;
- scans ;
- versions ;
- limites ;
- health checks ;
- secrets ;
- monitoring ;
- rollback.

---

# 79. Orchestration

L’orchestrateur doit gérer :

- déploiement ;
- disponibilité ;
- autoscaling ;
- redémarrage ;
- réseau ;
- secrets ;
- configuration ;
- mise à jour progressive ;
- rollback ;
- monitoring.

---

# 80. Haute disponibilité

Les services critiques doivent fonctionner sur :

- plusieurs instances ;
- plusieurs zones ;
- réplication ;
- load balancing ;
- stockage redondé ;
- surveillance ;
- bascule ;
- capacité de reprise.

---

# 81. Multi-région

L’architecture doit prévoir :

- région principale ;
- région secondaire ;
- réplication ;
- sauvegardes ;
- DNS ;
- bascule ;
- failback ;
- sécurité ;
- tests.

---

# 82. Scalabilité

Le système doit pouvoir augmenter :

- nombre d’utilisateurs ;
- transactions ;
- agents ;
- commerçants ;
- TPE ;
- GAB/DAB ;
- partenaires ;
- pays ;
- données ;
- notifications.

---

# 83. Autoscaling

L’autoscaling peut dépendre :

- CPU ;
- mémoire ;
- nombre de requêtes ;
- taille de queue ;
- latence ;
- événements ;
- calendrier ;
- campagne ;
- activité pays.

---

# 84. Observabilité

Chaque service doit produire :

- logs ;
- métriques ;
- traces ;
- événements ;
- health checks ;
- alertes ;
- tableaux de bord ;
- SLA ;
- SLO.

---

# 85. Logs

Les logs doivent inclure :

- service ;
- environnement ;
- version ;
- requête ;
- référence ;
- statut ;
- erreur ;
- durée ;
- corrélation ;
- pays ;
- appareil si nécessaire.

Ils ne doivent pas contenir de secrets.

---

# 86. Traces distribuées

Une transaction doit pouvoir être suivie à travers :

```text
Application
→ Gateway
→ Service
→ Ledger
→ Partenaire
→ Notification
```

---

# 87. Identifiant de corrélation

Chaque requête importante doit posséder un identifiant de corrélation utilisé dans :

- logs ;
- traces ;
- incidents ;
- support ;
- audit ;
- partenaires ;
- reporting.

---

# 88. Alertes

Les alertes peuvent concerner :

- erreur ;
- indisponibilité ;
- fraude ;
- sécurité ;
- ledger ;
- paiement ;
- agent ;
- GAB/DAB ;
- TPE ;
- partenaire ;
- base ;
- sauvegarde ;
- certificat ;
- capacité ;
- performance.

---

# 89. Gestion des incidents

Le processus doit couvrir :

- détection ;
- qualification ;
- priorité ;
- affectation ;
- mitigation ;
- résolution ;
- communication ;
- preuve ;
- post-mortem ;
- action corrective.

---

# 90. Continuité d’activité

L’architecture doit intégrer :

- PCA ;
- PRA ;
- sauvegardes ;
- réplication ;
- bascule ;
- mode dégradé ;
- lecture seule ;
- files d’attente ;
- reprise ;
- réconciliation ;
- exercices.

---

# 91. Tests globaux

Les tests doivent couvrir :

- unité ;
- intégration ;
- contrat ;
- end-to-end ;
- sécurité ;
- performance ;
- charge ;
- résilience ;
- réseau faible ;
- hors ligne ;
- TPE ;
- GAB/DAB ;
- multi-pays ;
- reprise ;
- migrations ;
- compatibilité.

---

# 92. CI/CD

La chaîne CI/CD doit automatiser :

- lint ;
- build ;
- tests ;
- scans ;
- validation Prisma ;
- génération ;
- artefacts ;
- signature ;
- déploiement ;
- smoke tests ;
- rollback ;
- rapports.

---

# 93. Gestion des versions

Chaque composant doit avoir :

- version ;
- build ;
- commit ;
- artefact ;
- statut ;
- compatibilité ;
- changelog ;
- date ;
- propriétaire ;
- fin de support.

---

# 94. Feature flags

Les feature flags peuvent cibler :

- pays ;
- utilisateur ;
- organisation ;
- appareil ;
- version ;
- environnement ;
- partenaire ;
- pourcentage ;
- produit ;
- risque.

---

# 95. Administration centrale

L’administration centrale doit pouvoir configurer :

- pays ;
- devises ;
- langues ;
- produits ;
- modules ;
- utilisateurs ;
- partenaires ;
- frais ;
- commissions ;
- plafonds ;
- cartes ;
- agents ;
- commerçants ;
- TPE ;
- GAB/DAB ;
- notifications ;
- fraude ;
- Finance ;
- Data ;
- sécurité ;
- versions ;
- documents ;
- tests ;
- alertes ;
- workflows ;
- audits.

---

# 96. Hiérarchie administrative

Exemple :

```text
Super Admin Groupe
→ Admin Pays
→ Admin Domaine
→ Superviseur
→ Opérateur
→ Lecteur
```

---

# 97. Administration multi-pays

Un administrateur doit uniquement accéder aux pays autorisés.

Le Super Admin peut voir plusieurs pays selon ses droits.

---

# 98. Administration multi-organisation

Les organisations peuvent inclure :

- Mansa ;
- banque ;
- agent ;
- commerçant ;
- entreprise ;
- école ;
- institution ;
- prestataire ;
- partenaire.

---

# 99. Permissions administratives

Exemples :

```text
user.read
user.manage
wallet.read
wallet.freeze
payment.read
payment.refund
agent.manage
merchant.manage
atm.manage
terminal.manage
fee.manage
commission.manage
configuration.publish
audit.read
```

---

# 100. Approbations

Les actions pouvant nécessiter une approbation incluent :

- modification des frais ;
- modification des commissions ;
- blocage massif ;
- remboursement important ;
- restauration ;
- bascule ;
- mise à jour obligatoire ;
- publication Production ;
- suppression ;
- export sensible ;
- changement de clé.

---

# 101. Double validation

Peut être exigée pour :

- modification ledger ;
- restauration Production ;
- blocage national ;
- changement de frais nationaux ;
- rotation HSM ;
- suppression massive ;
- déploiement GAB/DAB ;
- retrait d’un partenaire ;
- changement de compte de cantonnement.

---

# 102. Audit global

Chaque action sensible doit enregistrer :

- utilisateur ;
- rôle ;
- organisation ;
- pays ;
- appareil ;
- action ;
- ressource ;
- ancienne valeur ;
- nouvelle valeur ;
- date ;
- heure ;
- motif ;
- approbateur ;
- résultat ;
- preuve.

---

# 103. Immutabilité des audits

Les audits doivent être protégés contre :

- modification ;
- suppression ;
- réécriture ;
- remplacement ;
- désactivation ;
- falsification ;
- export non autorisé.

---

# 104. Cartographie des données

Chaque donnée doit avoir :

- source ;
- propriétaire ;
- classification ;
- usage ;
- destination ;
- rétention ;
- chiffrement ;
- accès ;
- pays ;
- transfert éventuel ;
- base ;
- suppression.

---

# 105. Classification des données

Exemples :

- PUBLIC ;
- INTERNAL ;
- CONFIDENTIAL ;
- RESTRICTED ;
- FINANCIAL ;
- PERSONAL ;
- SENSITIVE ;
- HIGHLY_RESTRICTED.

---

# 106. Flux transfrontaliers

Les flux entre pays doivent être contrôlés selon :

- réglementation ;
- localisation des données ;
- contrats ;
- chiffrement ;
- partenaire ;
- consentement ;
- audit ;
- rétention.

---

# 107. Multi-devises

L’architecture doit gérer :

- devise du wallet ;
- devise de transaction ;
- devise de règlement ;
- taux ;
- arrondis ;
- frais ;
- conversion ;
- reporting ;
- risque de change.

---

# 108. Multi-langues

Chaque interface doit pouvoir charger :

- traductions ;
- formats ;
- messages ;
- contenus ;
- documents ;
- notifications ;
- aide ;
- terminologie.

---

# 109. Multi-pays

Chaque pays peut avoir :

- produits ;
- devises ;
- frais ;
- plafonds ;
- KYC ;
- KYB ;
- partenaires ;
- banques ;
- Mobile Money ;
- langues ;
- règles ;
- calendrier ;
- support ;
- infrastructure ;
- stockage ;
- reporting.

---

# 110. Stratégie de démarrage

Le lancement peut commencer avec :

- un seul pays ;
- une banque partenaire ;
- un opérateur Mobile Money ;
- un réseau limité d’agents ;
- quelques TPE ;
- un premier GAB ;
- fonctions essentielles ;
- administration centralisée ;
- environnement de démonstration ;
- pilote contrôlé.

---

# 111. Architecture minimale de lancement

Le socle initial peut inclure :

- Application Client ;
- Application Commerce ;
- Application Agent ;
- Application TPE ;
- Admin Web ;
- API Gateway ;
- Authentification ;
- Wallet ;
- Ledger ;
- Paiement ;
- Transfert ;
- KYC ;
- Notifications ;
- Configuration ;
- Support ;
- monitoring ;
- sauvegardes.

---

# 112. Architecture de croissance

À mesure que Mansa grandit, ajouter :

- GAB/DAB ;
- cartes ;
- entreprises ;
- institutions ;
- écoles ;
- Data avancée ;
- fraude avancée ;
- Jini ;
- multi-pays ;
- multi-région ;
- automatisation ;
- haute disponibilité renforcée ;
- partenaires multiples.

---

# 113. Architecture cible nationale

Elle doit pouvoir gérer :

- plusieurs millions d’utilisateurs ;
- milliers d’agents ;
- milliers de commerçants ;
- milliers de TPE ;
- réseau GAB/DAB ;
- partenaires bancaires ;
- Mobile Money ;
- institutions ;
- paiements de masse ;
- haute disponibilité ;
- support national.

---

# 114. Architecture cible régionale

Elle doit supporter :

- plusieurs pays ;
- plusieurs devises ;
- plusieurs réglementations ;
- plusieurs banques ;
- plusieurs opérateurs ;
- plusieurs régions cloud ;
- règlement transfrontalier ;
- reporting consolidé ;
- gouvernance groupe ;
- administration locale.

---

# 115. Cartographie fonctionnelle synthétique

```text
IDENTITÉ
├── Client
├── Agent
├── Commerçant
├── Entreprise
├── Institution
└── Administrateur

FINANCE
├── Wallet
├── Ledger
├── Paiement
├── Transfert
├── Cartes
├── Frais
├── Commissions
└── Règlement

RÉSEAU PHYSIQUE
├── Agents
├── TPE
├── GAB
├── DAB
├── Agences
└── Partenaires

CONTRÔLE
├── KYC
├── KYB
├── Fraude
├── Conformité
├── Audit
└── Sécurité

OPÉRATIONS
├── Support
├── Finance
├── Data
├── Observabilité
├── Maintenance
└── Continuité
```

---

# 116. Cartographie technique synthétique

```text
Applications
→ API Gateway
→ Microservices
→ Event Bus
→ Ledger
→ Bases
→ Partenaires
→ Data Platform
→ Administration
→ Observabilité
```

---

# 117. Cartographie de responsabilités

Exemple :

```text
Produit
→ définit le besoin

Développement
→ construit

QA
→ teste

Sécurité
→ contrôle

Conformité
→ valide les obligations

Finance
→ contrôle les écritures

Opérations
→ exploite

Support
→ assiste

Administration
→ configure

Audit
→ vérifie
```

---

# 118. Modèles principaux

- User
- Organization
- Role
- Permission
- Device
- Wallet
- LedgerAccount
- LedgerEntry
- Transaction
- Payment
- Transfer
- Card
- Merchant
- Agent
- CashDrawer
- FloatAccount
- Terminal
- ATM
- KYCProfile
- KYBProfile
- FraudAlert
- FeeRule
- CommissionRule
- Partner
- CountryConfiguration
- Notification
- SupportTicket
- ConfigurationVersion
- Release
- Incident
- AuditEvent

---

# 119. API principales

Exemples :

```http
POST   /auth/login
POST   /users
GET    /wallets/{id}
POST   /payments
POST   /transfers
POST   /cash/deposits
POST   /cash/withdrawals
POST   /cards
GET    /agents
GET    /merchants
GET    /terminals
GET    /atms
POST   /kyc
POST   /kyb
GET    /fraud/alerts
GET    /finance/reconciliation
GET    /configuration
GET    /audit
```

---

# 120. Webhooks principaux

Exemples :

```text
user.created
kyc.approved
wallet.created
payment.completed
payment.failed
transfer.completed
cash.deposit.completed
cash.withdrawal.completed
card.activated
agent.float.low
atm.cash.low
terminal.offline
fraud.alert.created
reconciliation.break.created
```

---

# 121. Reporting global

Les rapports peuvent couvrir :

- utilisateurs ;
- transactions ;
- revenus ;
- frais ;
- commissions ;
- agents ;
- commerçants ;
- TPE ;
- GAB/DAB ;
- cartes ;
- fraude ;
- KYC ;
- KYB ;
- support ;
- disponibilité ;
- performance ;
- pays ;
- partenaires.

---

# 122. Indicateurs globaux

Exemples :

- utilisateurs actifs ;
- volume de transactions ;
- valeur totale ;
- taux de succès ;
- revenu net ;
- commissions ;
- agents actifs ;
- commerçants actifs ;
- TPE actifs ;
- GAB/DAB actifs ;
- taux de fraude ;
- taux KYC ;
- disponibilité ;
- latence ;
- incidents ;
- satisfaction.

---

# 123. Risques architecturaux

Risques possibles :

- dépendance à un partenaire unique ;
- mauvaise isolation des pays ;
- dette technique ;
- surcharge du ledger ;
- mauvaise gestion des secrets ;
- erreurs de configuration ;
- absence de monitoring ;
- panne régionale ;
- perte de données ;
- fraude ;
- mauvaise compatibilité ;
- complexité excessive ;
- coûts cloud élevés.

---

# 124. Réduction des risques

Mesures :

- abstraction des partenaires ;
- multi-fournisseurs ;
- tests ;
- revue d’architecture ;
- observabilité ;
- PCA/PRA ;
- automatisation ;
- limites ;
- feature flags ;
- rollbacks ;
- gouvernance ;
- sécurité ;
- documentation ;
- audits.

---

# 125. Rôles architecturaux

Exemples :

```text
CHIEF_ARCHITECT
SOLUTION_ARCHITECT
SECURITY_ARCHITECT
DATA_ARCHITECT
PAYMENTS_ARCHITECT
INTEGRATION_ARCHITECT
CLOUD_ARCHITECT
MOBILE_ARCHITECT
TERMINAL_ARCHITECT
ATM_ARCHITECT
COUNTRY_ARCHITECT
AUDITOR
VIEWER
```

---

# 126. Permissions

Exemples :

```text
architecture.read
architecture.manage
architecture.approve
architecture.publish
architecture.diagram.manage
architecture.service.manage
architecture.dependency.manage
architecture.risk.manage
architecture.audit.read
```

---

# 127. Approbations

Peuvent nécessiter une approbation :

- nouveau service critique ;
- nouvelle base ;
- nouveau partenaire ;
- nouvelle région ;
- changement ledger ;
- changement sécurité ;
- changement réseau ;
- nouvelle technologie ;
- suppression de service ;
- modification d’un flux financier.

---

# 128. Double validation

Peut être exigée pour :

- modification d’architecture du ledger ;
- changement de région Production ;
- nouvelle intégration cartes ;
- changement de HSM ;
- migration de base ;
- remplacement d’API Gateway ;
- changement de flux de cantonnement ;
- modification nationale.

---

# 129. Tests de l’architecture

- tests de flux ;
- tests API ;
- tests ledger ;
- tests événements ;
- tests partenaires ;
- tests idempotence ;
- tests sécurité ;
- tests permissions ;
- tests multi-pays ;
- tests multi-devises ;
- tests réseau faible ;
- tests offline ;
- tests TPE ;
- tests GAB/DAB ;
- tests de charge ;
- tests de stress ;
- tests de résilience ;
- tests de bascule ;
- tests de restauration ;
- tests de montée en charge ;
- tests de compatibilité ;
- tests de monitoring ;
- tests d’audit.

---

# 130. Règles métier

1. Toute transaction financière passe par le ledger.
2. Tout service critique est supervisé.
3. Toute action sensible est autorisée.
4. Toute modification critique est auditée.
5. Les pays sont isolés logiquement.
6. Les partenaires sont abstraits.
7. Les opérations sont idempotentes.
8. Les erreurs partenaires sont gérées.
9. Les services critiques sont hautement disponibles.
10. Les sauvegardes sont testées.
11. Les données sensibles sont chiffrées.
12. Les secrets ne sont pas stockés dans Git.
13. Les appareils critiques sont enregistrés.
14. Les versions sont traçables.
15. Les configurations sont centralisées.
16. Les feature flags sont administrables.
17. Les flux sont documentés.
18. Les rôles sont séparés.
19. Les environnements sont isolés.
20. Les audits sont immuables.
21. Le GAB et le DAB sont gérés comme deux catégories distinctes.
22. Les agents disposent d’un float séparé.
23. Les dépôts Agent ne nécessitent pas de confirmation Client dans l’application.
24. Les retraits exigent une authentification du client.
25. Les frais et commissions sont entièrement configurables.

---

# 131. Critères d’acceptation

L’Architecture globale finale et la Cartographie complète de Mansa sont validées lorsque :

- toutes les applications sont cartographiées ;
- tous les portails sont identifiés ;
- les rôles utilisateurs sont définis ;
- l’API Gateway est positionnée ;
- les services d’identité sont définis ;
- le Wallet est défini ;
- le ledger est la source financière officielle ;
- le service Paiement est défini ;
- le service Transfert est défini ;
- le service Cartes est défini ;
- le Cash Network est intégré ;
- les GAB/DAB sont intégrés ;
- les TPE sont intégrés ;
- le KYC est intégré ;
- le KYB est intégré ;
- la fraude est intégrée ;
- les notifications sont intégrées ;
- la facturation est intégrée ;
- la fidélité est intégrée ;
- les coffres et budgets sont intégrés ;
- le support est intégré ;
- Jini est intégré ;
- le moteur de configuration est intégré ;
- l’Event Bus est défini ;
- les files de messages sont définies ;
- l’idempotence est imposée ;
- les bases sont cartographiées ;
- PostgreSQL est positionné ;
- Redis est positionné ;
- le stockage objet est positionné ;
- le moteur de recherche est positionné ;
- la Data Platform est intégrée ;
- les flux de paiement sont définis ;
- les flux de dépôt Agent sont définis ;
- les flux de retrait Agent sont définis ;
- les flux GAB/DAB sont définis ;
- les flux Mobile Money sont définis ;
- les flux bancaires sont définis ;
- les flux cartes sont définis ;
- les flux de commission sont définis ;
- les flux de remboursement sont définis ;
- les partenaires sont abstraits ;
- les circuit breakers sont prévus ;
- la sécurité globale est définie ;
- le Zero Trust est appliqué ;
- le RBAC et l’ABAC sont supportés ;
- le chiffrement est généralisé ;
- le HSM est intégré ;
- les secrets sont centralisés ;
- les zones réseau sont séparées ;
- les environnements sont isolés ;
- l’infrastructure as code est définie ;
- les conteneurs sont sécurisés ;
- l’orchestration est définie ;
- la haute disponibilité est prévue ;
- le multi-région est prévu ;
- la scalabilité est prévue ;
- l’autoscaling est prévu ;
- l’observabilité est intégrée ;
- les logs sont protégés ;
- les traces distribuées sont disponibles ;
- les alertes sont définies ;
- la gestion des incidents est intégrée ;
- le PCA et le PRA sont intégrés ;
- la stratégie de tests est intégrée ;
- la CI/CD est intégrée ;
- les versions sont traçables ;
- les feature flags sont intégrés ;
- l’administration centrale est définie ;
- la hiérarchie administrative est définie ;
- le multi-pays est administrable ;
- le multi-organisation est administrable ;
- les approbations critiques sont protégées ;
- les audits sont immuables ;
- les données sont cartographiées ;
- les flux transfrontaliers sont contrôlés ;
- le multi-devises est supporté ;
- le multi-langues est supporté ;
- l’architecture minimale de lancement est définie ;
- l’architecture de croissance est définie ;
- l’architecture nationale est définie ;
- l’architecture régionale est définie ;
- les responsabilités sont cartographiées ;
- les risques architecturaux sont identifiés ;
- les tests couvrent les parcours essentiels.
