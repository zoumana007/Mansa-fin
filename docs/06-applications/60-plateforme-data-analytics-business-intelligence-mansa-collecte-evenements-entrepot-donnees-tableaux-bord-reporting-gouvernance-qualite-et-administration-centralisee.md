# 60 — Plateforme Data, Analytics et Business Intelligence Mansa : collecte, événements, entrepôt de données, tableaux de bord, reporting, gouvernance, qualité et administration centralisée

## 1. Objet du document

Ce document définit l’architecture officielle de la **Plateforme Data, Analytics et Business Intelligence Mansa**.

Cette plateforme centralise les données analytiques produites par l’ensemble de l’écosystème Mansa afin de permettre :

- le pilotage de l’activité ;
- le suivi des utilisateurs ;
- l’analyse des transactions ;
- le suivi des revenus ;
- la mesure des coûts ;
- le suivi des commissions ;
- la surveillance des agents ;
- l’analyse des commerçants ;
- le pilotage des cartes ;
- le suivi des TPE ;
- le suivi des DAB ;
- le suivi du Cash Network ;
- le suivi des entreprises ;
- le suivi des établissements scolaires ;
- le suivi des institutions publiques ;
- le suivi des partenaires ;
- l’analyse du support ;
- l’analyse de la fraude ;
- l’analyse de la sécurité ;
- l’analyse financière ;
- le suivi de la qualité de service ;
- la création de rapports ;
- la création de tableaux de bord ;
- la prévision ;
- la segmentation ;
- la détection des anomalies ;
- la prise de décision.

La plateforme reçoit des données provenant de :

- l’application Client ;
- l’application Commerce ;
- l’application Agent ;
- l’application TPE ;
- l’application Admin Lite ;
- le Hub et Annuaire ;
- le site officiel ;
- le portail Admin Web ;
- le portail Développeurs ;
- le portail Institutions ;
- le portail Banques ;
- le portail Entreprises ;
- le portail Écoles et Universités ;
- le portail Support ;
- la console Sécurité et Fraude ;
- la console Finance ;
- le système de notifications ;
- les DAB ;
- les partenaires ;
- les banques ;
- les opérateurs Mobile Money ;
- les réseaux de cartes ;
- les systèmes KYC et KYB ;
- le ledger ;
- les infrastructures techniques ;
- les journaux d’audit ;
- les moteurs de risque ;
- les services backend.

L’objectif est de fournir une plateforme :

- centralisée ;
- sécurisée ;
- gouvernée ;
- multi-pays ;
- multi-devises ;
- multi-entités ;
- fiable ;
- traçable ;
- performante ;
- évolutive ;
- accessible selon les rôles ;
- capable de séparer les données opérationnelles des données analytiques ;
- capable de produire des indicateurs en temps réel et différé.

---

# 2. Principes fondamentaux

## 2.1 La plateforme analytique ne remplace pas les systèmes opérationnels

Les systèmes de référence restent :

- le ledger pour les écritures financières ;
- le backend transactionnel pour les opérations ;
- le KYC pour l’identité ;
- le système de cartes pour les cartes ;
- le portail Finance pour les données comptables ;
- les applications métier pour leurs données opérationnelles.

La plateforme Data copie, transforme et agrège les données à des fins d’analyse.

Elle ne doit jamais être utilisée pour modifier directement :

- un solde ;
- une transaction ;
- une écriture comptable ;
- un profil client ;
- une carte ;
- un règlement ;
- une permission ;
- un statut réglementaire.

---

## 2.2 Les données doivent avoir une source officielle

Chaque donnée doit posséder :

- une source ;
- un propriétaire ;
- une définition ;
- un format ;
- une date de création ;
- une fréquence de mise à jour ;
- un niveau de sensibilité ;
- une politique de conservation ;
- une règle de qualité ;
- une version.

---

## 2.3 Les indicateurs doivent être définis de manière unique

Un indicateur comme « utilisateur actif » ne doit pas avoir plusieurs définitions contradictoires.

Chaque KPI doit préciser :

- son nom ;
- sa formule ;
- son périmètre ;
- sa période ;
- ses exclusions ;
- sa source ;
- son propriétaire ;
- sa version ;
- sa date d’effet.

---

## 2.4 Les données sensibles doivent être minimisées

La plateforme analytique ne doit stocker que les données nécessaires.

Les données doivent être :

- masquées ;
- pseudonymisées ;
- agrégées ;
- chiffrées ;
- limitées par rôle ;
- soumises à une durée de conservation ;
- séparées selon leur sensibilité.

---

## 2.5 Toute consultation sensible doit être auditée

Le système doit enregistrer :

- utilisateur ;
- rôle ;
- équipe ;
- pays ;
- rapport ;
- jeu de données ;
- requête ;
- filtre ;
- export ;
- date ;
- heure ;
- appareil ;
- IP ;
- motif ;
- résultat.

---

# 3. Utilisateurs de la plateforme

Rôles possibles :

```text
CHIEF_DATA_OFFICER
DATA_PLATFORM_ADMIN
DATA_ENGINEER
ANALYTICS_ENGINEER
DATA_ANALYST
BUSINESS_INTELLIGENCE_ANALYST
FINANCE_DATA_ANALYST
FRAUD_DATA_ANALYST
RISK_DATA_ANALYST
PRODUCT_ANALYST
MARKETING_ANALYST
OPERATIONS_ANALYST
CUSTOMER_SUPPORT_ANALYST
DATA_SCIENTIST
MACHINE_LEARNING_ENGINEER
DATA_GOVERNANCE_MANAGER
DATA_QUALITY_MANAGER
DATA_STEWARD
INTERNAL_AUDITOR
VIEWER
```

---

# 4. Permissions

Exemples :

```text
data.dashboard.read
data.dataset.read
data.dataset.manage
data.pipeline.read
data.pipeline.manage
data.metric.read
data.metric.manage
data.report.read
data.report.create
data.report.publish
data.export.create
data.export.approve
data.quality.read
data.quality.manage
data.catalog.read
data.catalog.manage
data.model.read
data.model.manage
data.audit.read
```

---

# 5. Périmètres d’accès

Un utilisateur peut être limité à :

- un pays ;
- une région ;
- une entité juridique ;
- une filiale ;
- une devise ;
- un produit ;
- une application ;
- un partenaire ;
- une institution ;
- une entreprise ;
- un établissement ;
- un type de client ;
- une période ;
- un niveau d’agrégation ;
- un jeu de données ;
- un indicateur ;
- un environnement.

---

# 6. Authentification

Méthodes possibles :

- mot de passe fort ;
- MFA ;
- passkey ;
- clé de sécurité ;
- SSO ;
- certificat ;
- appareil géré ;
- IP autorisée ;
- réseau privé ;
- accès bastion.

---

# 7. MFA obligatoire

Le MFA doit être obligatoire pour :

- les administrateurs Data ;
- les accès production ;
- les exports ;
- les données sensibles ;
- les rapports réglementaires ;
- la modification d’un pipeline ;
- la publication d’un KPI ;
- la création d’un accès ;
- la modification d’une politique ;
- l’accès aux données pseudonymisées détaillées.

---

# 8. Architecture du projet

Structure recommandée :

```text
data-platform/
├── ingestion/
├── events/
├── streaming/
├── batch/
├── connectors/
├── raw-zone/
├── staging/
├── warehouse/
├── lakehouse/
├── marts/
├── transformations/
├── orchestration/
├── catalog/
├── lineage/
├── quality/
├── governance/
├── metrics/
├── semantic-layer/
├── dashboards/
├── reports/
├── exports/
├── notebooks/
├── machine-learning/
├── monitoring/
├── privacy/
├── security/
├── audit/
└── administration/
```

---

# 9. Couches de données

Architecture recommandée :

```text
Sources opérationnelles
→ Ingestion
→ Zone brute
→ Zone de préparation
→ Entrepôt central
→ Data marts
→ Couche sémantique
→ Tableaux de bord et rapports
```

---

# 10. Types d’ingestion

La plateforme doit gérer :

- ingestion temps réel ;
- micro-batch ;
- batch horaire ;
- batch quotidien ;
- fichiers ;
- API ;
- webhooks ;
- événements ;
- bases de données ;
- files de messages ;
- SFTP ;
- imports manuels contrôlés ;
- données partenaires.

---

# 11. Sources principales

Exemples :

- PostgreSQL ;
- Redis ;
- journaux applicatifs ;
- Event Bus ;
- Message Queue ;
- fichiers CSV ;
- fichiers JSON ;
- fichiers Parquet ;
- API partenaires ;
- fichiers bancaires ;
- fichiers Mobile Money ;
- fichiers cartes ;
- données TPE ;
- données DAB ;
- données agents ;
- données commerçants ;
- données institutions ;
- données de support ;
- données de sécurité.

---

# 12. Événements analytiques

Chaque événement doit contenir au minimum :

- event_id ;
- event_name ;
- event_version ;
- occurred_at ;
- received_at ;
- source ;
- environment ;
- country ;
- application ;
- user_id pseudonymisé si applicable ;
- session_id ;
- device_id pseudonymisé ;
- correlation_id ;
- propriétés autorisées.

---

# 13. Convention de nommage des événements

Format recommandé :

```text
domain.entity.action
```

Exemples :

```text
client.account.created
client.login.completed
payment.transaction.completed
payment.transaction.failed
card.virtual.created
merchant.settlement.completed
agent.deposit.completed
agent.withdrawal.completed
support.ticket.resolved
fraud.case.confirmed
finance.period.closed
```

---

# 14. Versionnement des événements

Chaque événement doit être versionné.

Exemples :

```text
payment.transaction.completed.v1
payment.transaction.completed.v2
```

Une nouvelle version doit être créée lorsqu’un changement casse la compatibilité.

---

# 15. Schémas d’événements

Chaque événement doit posséder :

- nom ;
- version ;
- description ;
- propriétaire ;
- propriétés ;
- types ;
- champs obligatoires ;
- champs facultatifs ;
- exemples ;
- niveau de sensibilité ;
- durée de conservation ;
- date d’effet ;
- statut.

---

# 16. Statuts d’un schéma

- DRAFT ;
- REVIEW ;
- APPROVED ;
- ACTIVE ;
- DEPRECATED ;
- RETIRED ;
- ARCHIVED.

---

# 17. Validation des événements

Le système doit vérifier :

- schéma connu ;
- version autorisée ;
- champs obligatoires ;
- types valides ;
- taille ;
- données interdites ;
- doublons ;
- date ;
- source ;
- signature éventuelle ;
- environnement.

---

# 18. Données interdites dans les événements analytiques

Ne doivent jamais être envoyés en clair :

- PIN ;
- OTP ;
- CVV ;
- mot de passe ;
- numéro complet de carte ;
- clé privée ;
- secret API ;
- token d’authentification ;
- document complet ;
- biométrie ;
- message privé complet ;
- numéro complet de compte non autorisé ;
- donnée médicale non nécessaire.

---

# 19. Idempotence

Chaque événement doit utiliser un identifiant unique.

Le système doit empêcher :

- double ingestion ;
- double comptage ;
- double agrégation ;
- double export ;
- double déclenchement analytique.

---

# 20. Zone brute

La zone brute conserve les données telles que reçues, dans les limites autorisées.

Elle doit être :

- chiffrée ;
- restreinte ;
- immuable ;
- horodatée ;
- partitionnée ;
- auditée ;
- soumise à rétention ;
- inaccessible aux utilisateurs ordinaires.

---

# 21. Zone de préparation

La zone de préparation permet :

- nettoyage ;
- normalisation ;
- déduplication ;
- validation ;
- enrichissement ;
- conversion ;
- contrôle qualité ;
- traitement des erreurs ;
- préparation au chargement.

---

# 22. Entrepôt de données

L’entrepôt doit contenir des données structurées pour :

- clients ;
- comptes ;
- transactions ;
- cartes ;
- commerçants ;
- agents ;
- entreprises ;
- écoles ;
- institutions ;
- partenaires ;
- support ;
- fraude ;
- finance ;
- notifications ;
- produits ;
- pays ;
- devises ;
- périodes.

---

# 23. Modèle dimensionnel

Dimensions possibles :

- DimDate ;
- DimTime ;
- DimCountry ;
- DimRegion ;
- DimCity ;
- DimCurrency ;
- DimProduct ;
- DimChannel ;
- DimCustomer ;
- DimMerchant ;
- DimAgent ;
- DimPartner ;
- DimInstitution ;
- DimCompany ;
- DimSchool ;
- DimDevice ;
- DimApplication ;
- DimTransactionStatus.

---

# 24. Tables de faits

Exemples :

- FactTransaction ;
- FactPayment ;
- FactTransfer ;
- FactDeposit ;
- FactWithdrawal ;
- FactCardTransaction ;
- FactMerchantSettlement ;
- FactAgentOperation ;
- FactSupportTicket ;
- FactFraudAlert ;
- FactSecurityIncident ;
- FactRevenue ;
- FactCommission ;
- FactNotification ;
- FactApplicationSession.

---

# 25. Historisation

Le système doit conserver les changements importants.

Exemples :

- changement de segment ;
- changement de pays ;
- changement de statut ;
- changement de type de compte ;
- changement de niveau KYC ;
- changement de partenaire ;
- changement d’organisation ;
- changement de tarif.

---

# 26. Data marts

Data marts recommandés :

- Client ;
- Paiements ;
- Transferts ;
- Cartes ;
- Commerçants ;
- Agents ;
- Cash Network ;
- Entreprises ;
- Éducation ;
- Institutions ;
- Support ;
- Fraude ;
- Sécurité ;
- Finance ;
- Marketing ;
- Produit ;
- Opérations ;
- Partenaires.

---

# 27. Couche sémantique

La couche sémantique doit centraliser :

- mesures ;
- dimensions ;
- filtres ;
- relations ;
- règles de calcul ;
- formats ;
- devises ;
- périodes ;
- définitions métier ;
- permissions.

---

# 28. Catalogue de données

Le catalogue doit permettre de rechercher :

- jeux de données ;
- tables ;
- colonnes ;
- événements ;
- indicateurs ;
- rapports ;
- tableaux de bord ;
- propriétaires ;
- classifications ;
- dépendances ;
- définitions.

---

# 29. Fiche d’un jeu de données

Elle doit contenir :

- nom ;
- description ;
- propriétaire ;
- domaine ;
- source ;
- fréquence ;
- fraîcheur ;
- sensibilité ;
- pays ;
- schéma ;
- qualité ;
- lineage ;
- utilisateurs ;
- statut ;
- date de création ;
- date de mise à jour.

---

# 30. Statuts d’un jeu de données

- DRAFT ;
- ACTIVE ;
- DEGRADED ;
- STALE ;
- SUSPENDED ;
- DEPRECATED ;
- ARCHIVED.

---

# 31. Classification des données

Niveaux possibles :

- PUBLIC ;
- INTERNAL ;
- CONFIDENTIAL ;
- SENSITIVE ;
- HIGHLY_SENSITIVE ;
- REGULATED.

---

# 32. Propriétaires des données

Chaque domaine doit posséder :

- Data Owner ;
- Data Steward ;
- équipe technique ;
- équipe métier ;
- responsable qualité ;
- responsable sécurité ;
- responsable conformité.

---

# 33. Lineage

Le système doit permettre de voir :

```text
Source
→ pipeline
→ transformation
→ table
→ métrique
→ rapport
→ utilisateur
```

---

# 34. Impact d’un changement

Avant modification d’une table, d’une métrique ou d’un pipeline, le système doit identifier :

- tableaux de bord concernés ;
- rapports concernés ;
- modèles concernés ;
- exports concernés ;
- équipes concernées ;
- partenaires concernés ;
- risques ;
- migrations nécessaires.

---

# 35. Qualité des données

Dimensions de qualité :

- exactitude ;
- complétude ;
- unicité ;
- cohérence ;
- validité ;
- fraîcheur ;
- intégrité ;
- disponibilité ;
- traçabilité.

---

# 36. Règles de qualité

Exemples :

- montant positif ;
- devise connue ;
- pays connu ;
- transaction unique ;
- statut valide ;
- date cohérente ;
- compte existant ;
- partenaire connu ;
- débit et crédit équilibrés ;
- événement non dupliqué ;
- champ obligatoire présent.

---

# 37. Score de qualité

Chaque jeu de données peut avoir un score selon :

- complétude ;
- validité ;
- fraîcheur ;
- anomalies ;
- incidents ;
- conformité ;
- couverture des tests.

---

# 38. Statuts de qualité

- HEALTHY ;
- WARNING ;
- DEGRADED ;
- CRITICAL ;
- UNKNOWN.

---

# 39. Incidents de données

Exemples :

- pipeline échoué ;
- table non mise à jour ;
- schéma modifié ;
- données manquantes ;
- doublons ;
- volume inhabituel ;
- valeur incohérente ;
- retard de fichier ;
- mauvaise devise ;
- mauvais pays ;
- fuite potentielle ;
- accès non autorisé.

---

# 40. Dossier d’incident Data

Il doit contenir :

- référence ;
- jeu de données ;
- source ;
- impact ;
- sévérité ;
- date ;
- propriétaire ;
- équipes ;
- cause ;
- actions ;
- résolution ;
- rapports affectés ;
- utilisateurs affectés ;
- post-mortem.

---

# 41. Sévérités

- DATA_SEV_4 ;
- DATA_SEV_3 ;
- DATA_SEV_2 ;
- DATA_SEV_1.

---

# 42. Monitoring des pipelines

Le système doit suivre :

- statut ;
- début ;
- fin ;
- durée ;
- volume ;
- erreurs ;
- retries ;
- retard ;
- coût ;
- source ;
- destination ;
- version ;
- propriétaire.

---

# 43. Statuts d’un pipeline

- DRAFT ;
- TESTING ;
- ACTIVE ;
- RUNNING ;
- SUCCESS ;
- PARTIAL_SUCCESS ;
- FAILED ;
- PAUSED ;
- DISABLED ;
- DEPRECATED.

---

# 44. Orchestration

L’orchestrateur doit permettre :

- dépendances ;
- planification ;
- retries ;
- timeout ;
- alertes ;
- reprise ;
- backfill ;
- paramètres ;
- environnements ;
- verrouillage ;
- journalisation.

---

# 45. Backfill

Un backfill doit préciser :

- période ;
- jeu de données ;
- pipeline ;
- motif ;
- impact ;
- volume ;
- coût estimé ;
- demandeur ;
- approbateur ;
- environnement ;
- audit.

---

# 46. Temps réel

Les indicateurs temps réel peuvent couvrir :

- transactions par seconde ;
- paiements réussis ;
- paiements échoués ;
- retraits ;
- dépôts ;
- activité TPE ;
- activité DAB ;
- alertes fraude ;
- incidents ;
- disponibilité ;
- files de notifications ;
- liquidité critique.

---

# 47. Données différées

Les traitements batch peuvent couvrir :

- revenus ;
- commissions ;
- cohortes ;
- rétention ;
- rentabilité ;
- clôtures ;
- rapports mensuels ;
- rapports réglementaires ;
- segmentation ;
- prévisions ;
- qualité.

---

# 48. Tableaux de bord exécutifs

Ils peuvent afficher :

- utilisateurs inscrits ;
- utilisateurs actifs ;
- volume de transactions ;
- valeur des transactions ;
- revenus ;
- coûts ;
- marge ;
- nombre de commerçants ;
- nombre d’agents ;
- nombre de cartes ;
- nombre de TPE ;
- nombre de DAB ;
- couverture géographique ;
- disponibilité ;
- fraude ;
- satisfaction ;
- croissance.

---

# 49. Indicateurs utilisateurs

Exemples :

- nouveaux utilisateurs ;
- utilisateurs actifs journaliers ;
- utilisateurs actifs mensuels ;
- taux d’activation ;
- taux de rétention ;
- taux d’abandon ;
- taux de vérification KYC ;
- fréquence d’utilisation ;
- valeur moyenne ;
- segmentation ;
- réactivation ;
- churn.

---

# 50. Définition d’un utilisateur actif

La définition doit être configurable et versionnée.

Exemple :

```text
Utilisateur ayant réalisé au moins une opération éligible
pendant la période sélectionnée.
```

Les opérations éligibles doivent être définies.

---

# 51. Indicateurs transactionnels

Exemples :

- nombre de transactions ;
- montant total ;
- montant moyen ;
- taux de succès ;
- taux d’échec ;
- taux d’annulation ;
- délai moyen ;
- canal ;
- produit ;
- pays ;
- devise ;
- partenaire.

---

# 52. Indicateurs Cash Network

Exemples :

- dépôts ;
- retraits ;
- float disponible ;
- cash déclaré ;
- agents actifs ;
- agents sans liquidité ;
- commissions ;
- écarts de caisse ;
- zones non couvertes ;
- temps d’attente ;
- incidents.

---

# 53. Indicateurs commerçants

Exemples :

- commerçants actifs ;
- volume ;
- revenu ;
- panier moyen ;
- remboursement ;
- chargeback ;
- taux d’acceptation ;
- règlement ;
- secteur ;
- localisation ;
- fidélité ;
- croissance.

---

# 54. Indicateurs cartes

Exemples :

- cartes émises ;
- cartes actives ;
- cartes virtuelles ;
- cartes physiques ;
- taux d’activation ;
- paiements ;
- retraits ;
- refus ;
- fraude ;
- carte perdue ;
- coût par carte ;
- revenu par carte.

---

# 55. Indicateurs TPE

Exemples :

- terminaux actifs ;
- terminaux hors ligne ;
- volume ;
- disponibilité ;
- taux d’acceptation ;
- erreurs ;
- version ;
- paiements hors ligne ;
- maintenance ;
- commerçants liés.

---

# 56. Indicateurs DAB

Exemples :

- DAB actifs ;
- disponibilité ;
- retraits ;
- dépôts ;
- billets disponibles ;
- incidents ;
- débit sans remise ;
- maintenance ;
- volume par emplacement ;
- rentabilité.

---

# 57. Indicateurs entreprises

Exemples :

- entreprises actives ;
- employés ;
- masse salariale ;
- cartes professionnelles ;
- dépenses ;
- notes de frais ;
- budgets ;
- fournisseurs ;
- revenus Mansa ;
- rétention entreprise.

---

# 58. Indicateurs scolaires

Exemples :

- établissements actifs ;
- étudiants ;
- inscriptions ;
- paiements ;
- impayés ;
- bourses ;
- cartes étudiantes ;
- logements ;
- transports ;
- revenus ;
- taux de paiement.

---

# 59. Indicateurs institutionnels

Exemples :

- institutions ;
- services actifs ;
- paiements ;
- recettes ;
- amendes ;
- taxes ;
- bourses ;
- aides ;
- références créées ;
- taux de paiement ;
- délais ;
- incidents.

---

# 60. Indicateurs support

Exemples :

- tickets ouverts ;
- tickets fermés ;
- délai de réponse ;
- délai de résolution ;
- SLA ;
- satisfaction ;
- réouvertures ;
- catégories ;
- canaux ;
- agents support ;
- charge ;
- qualité.

---

# 61. Indicateurs fraude

Exemples :

- alertes ;
- dossiers ;
- fraude confirmée ;
- faux positifs ;
- pertes ;
- pertes évitées ;
- comptes restreints ;
- cartes bloquées ;
- agents suspects ;
- commerçants suspects ;
- temps de traitement.

---

# 62. Indicateurs Finance

Exemples :

- revenus ;
- coûts ;
- marge ;
- commissions ;
- taxes ;
- liquidité ;
- cantonnement ;
- couverture ;
- règlements ;
- rapprochements ;
- suspenses ;
- clôtures ;
- écarts.

---

# 63. Segmentation

La plateforme doit permettre des segments selon :

- pays ;
- ville ;
- âge selon règles ;
- activité ;
- type de compte ;
- produit ;
- fréquence ;
- montant ;
- appareil ;
- canal ;
- niveau KYC ;
- comportement ;
- fidélité ;
- risque ;
- organisation.

---

# 64. Cohortes

Les cohortes peuvent être basées sur :

- date d’inscription ;
- première transaction ;
- première carte ;
- premier dépôt ;
- premier paiement ;
- pays ;
- campagne ;
- partenaire ;
- produit ;
- canal d’acquisition.

---

# 65. Funnels

Exemples :

```text
Installation
→ création de compte
→ vérification du téléphone
→ KYC
→ premier dépôt
→ première transaction
→ réutilisation
```

---

# 66. Analyse de rétention

Le système doit permettre :

- rétention J1 ;
- rétention J7 ;
- rétention J30 ;
- rétention mensuelle ;
- rétention par produit ;
- rétention par pays ;
- rétention par campagne ;
- rétention par canal ;
- rétention par segment.

---

# 67. Analyse des parcours

La plateforme peut analyser :

- écrans visités ;
- actions ;
- abandons ;
- erreurs ;
- temps ;
- reprises ;
- conversions ;
- parcours hors ligne ;
- assistance demandée ;
- points de friction.

Les données sensibles doivent rester exclues.

---

# 68. Attribution

Le système peut mesurer l’origine d’un utilisateur ou d’une conversion selon :

- campagne ;
- parrainage ;
- agent ;
- commerçant ;
- partenaire ;
- institution ;
- publicité ;
- lien ;
- QR ;
- événement ;
- canal organique.

---

# 69. Expérimentations

La plateforme peut prendre en charge :

- A/B tests ;
- tests multivariés ;
- groupes de contrôle ;
- feature flags ;
- objectifs ;
- résultats ;
- durée ;
- significativité ;
- segments ;
- arrêt anticipé.

---

# 70. Protection des expérimentations

Les expérimentations ne doivent pas :

- modifier les règles réglementaires ;
- masquer les frais ;
- réduire la sécurité ;
- contourner le KYC ;
- modifier le ledger ;
- exposer des données sensibles ;
- tester une action critique sans validation.

---

# 71. Rapports

Types de rapports :

- exécutif ;
- opérationnel ;
- financier ;
- réglementaire ;
- commercial ;
- produit ;
- fraude ;
- sécurité ;
- support ;
- partenaires ;
- agents ;
- commerçants ;
- institutions ;
- entreprises ;
- écoles.

---

# 72. Rapports programmés

Un rapport peut être envoyé :

- chaque heure ;
- quotidiennement ;
- chaque semaine ;
- chaque mois ;
- chaque trimestre ;
- après clôture ;
- après incident ;
- après campagne ;
- après règlement.

---

# 73. Formats d’export

- CSV ;
- XLSX ;
- PDF ;
- JSON ;
- Parquet ;
- API ;
- SFTP ;
- lien sécurisé.

---

# 74. Sécurité des exports

Les exports doivent être :

- autorisés ;
- limités ;
- masqués ;
- chiffrés ;
- temporaires ;
- traçables ;
- soumis à expiration ;
- soumis à approbation selon sensibilité ;
- protégés par watermark si nécessaire.

---

# 75. Exports massifs

Un export massif doit exiger :

- justification ;
- périmètre ;
- champs ;
- période ;
- destinataire ;
- durée ;
- demandeur ;
- approbateur ;
- chiffrement ;
- audit.

---

# 76. Tableaux de bord

Chaque tableau de bord doit contenir :

- nom ;
- description ;
- propriétaire ;
- indicateurs ;
- filtres ;
- pays ;
- langue ;
- fraîcheur ;
- accès ;
- version ;
- statut ;
- date de publication.

---

# 77. Statuts d’un tableau de bord

- DRAFT ;
- REVIEW ;
- APPROVED ;
- PUBLISHED ;
- DEGRADED ;
- DEPRECATED ;
- ARCHIVED.

---

# 78. Filtres

Filtres possibles :

- période ;
- pays ;
- région ;
- ville ;
- produit ;
- devise ;
- canal ;
- partenaire ;
- statut ;
- segment ;
- organisation ;
- application ;
- environnement.

---

# 79. Drill-down

Un utilisateur autorisé peut passer :

```text
Vue globale
→ pays
→ région
→ ville
→ organisation
→ produit
→ opération agrégée
```

L’accès au détail individuel doit rester limité.

---

# 80. Alertes analytiques

Le système peut alerter en cas de :

- chute du taux de succès ;
- hausse des échecs ;
- baisse des utilisateurs actifs ;
- hausse des retraits ;
- liquidité faible ;
- fraude élevée ;
- volume anormal ;
- revenu anormal ;
- pipeline en retard ;
- qualité faible ;
- données manquantes ;
- coût élevé.

---

# 81. Seuils dynamiques

Les alertes peuvent utiliser :

- seuil fixe ;
- pourcentage ;
- moyenne mobile ;
- tendance ;
- comparaison historique ;
- saisonnalité ;
- anomalie statistique ;
- règle métier ;
- modèle prédictif.

---

# 82. Prévisions

La plateforme peut produire des prévisions pour :

- utilisateurs ;
- transactions ;
- revenus ;
- liquidité ;
- commissions ;
- retraits ;
- dépôts ;
- fraude ;
- tickets support ;
- demande de cartes ;
- besoin en TPE ;
- besoin en DAB ;
- croissance géographique.

---

# 83. Modèles prédictifs

Exemples :

- risque de churn ;
- risque de fraude ;
- prévision de liquidité ;
- prévision de volume ;
- probabilité d’activation ;
- probabilité de remboursement ;
- prévision de tickets ;
- recommandation d’emplacement d’agent ;
- recommandation d’emplacement de DAB.

---

# 84. Cycle de vie des modèles

Chaque modèle doit passer par :

1. développement ;
2. test ;
3. validation ;
4. revue sécurité ;
5. revue conformité ;
6. déploiement ;
7. surveillance ;
8. réentraînement ;
9. retrait.

---

# 85. Fiche d’un modèle

Elle doit contenir :

- nom ;
- version ;
- objectif ;
- propriétaire ;
- données utilisées ;
- variables ;
- métriques ;
- biais connus ;
- limites ;
- date ;
- statut ;
- environnement ;
- approbations ;
- monitoring.

---

# 86. Statuts d’un modèle

- DRAFT ;
- TRAINING ;
- VALIDATION ;
- APPROVED ;
- SHADOW ;
- ACTIVE ;
- DEGRADED ;
- SUSPENDED ;
- RETIRED ;
- ARCHIVED.

---

# 87. Mode Shadow

Un modèle en mode Shadow :

- produit des résultats ;
- ne prend pas de décision ;
- ne modifie pas le parcours ;
- permet de comparer ;
- permet d’évaluer les biais ;
- permet de mesurer les performances.

---

# 88. Limites de l’intelligence artificielle

Un modèle analytique ne doit pas :

- modifier un solde ;
- bloquer seul définitivement un compte ;
- déclarer seul une fraude ;
- décider seul d’un remboursement ;
- supprimer une donnée ;
- modifier une permission ;
- contourner un workflow ;
- utiliser des données interdites ;
- remplacer une décision réglementaire obligatoire.

---

# 89. Notebooks

Les notebooks doivent être :

- isolés ;
- contrôlés ;
- versionnés ;
- limités par rôle ;
- dépourvus de secrets ;
- connectés à des données autorisées ;
- soumis à expiration ;
- audités.

---

# 90. Environnements

La plateforme doit distinguer :

- Développement ;
- Démo ;
- Recette ;
- Préproduction ;
- Production ;
- Sandbox analytique.

Les données de Production ne doivent pas être copiées librement dans les environnements inférieurs.

---

# 91. Données de test

Les environnements de test doivent utiliser :

- données fictives ;
- données synthétiques ;
- données anonymisées ;
- sous-ensembles contrôlés ;
- jeux de tests ;
- scénarios prédéfinis.

---

# 92. Vie privée

La plateforme doit permettre :

- pseudonymisation ;
- anonymisation ;
- minimisation ;
- masquage ;
- agrégation ;
- suppression contrôlée ;
- limitation des finalités ;
- gestion de la rétention ;
- traçabilité des accès.

---

# 93. Rétention

La durée de conservation peut dépendre :

- du pays ;
- du domaine ;
- du type de donnée ;
- de la sensibilité ;
- de l’usage ;
- du contrat ;
- des obligations ;
- de la finalité analytique.

---

# 94. Suppression

Une suppression doit être :

- autorisée ;
- documentée ;
- propagée ;
- auditée ;
- vérifiée ;
- compatible avec les obligations de conservation ;
- appliquée aux copies concernées.

---

# 95. Gouvernance des KPI

La création ou modification d’un KPI doit suivre :

1. proposition ;
2. définition ;
3. validation métier ;
4. validation Data ;
5. test ;
6. publication ;
7. versionnement ;
8. communication ;
9. suivi.

---

# 96. Fiche d’un KPI

Elle doit contenir :

- code ;
- nom ;
- description ;
- formule ;
- unité ;
- source ;
- propriétaire ;
- dimensions ;
- exclusions ;
- fréquence ;
- fraîcheur ;
- version ;
- statut ;
- date d’effet.

---

# 97. Statuts d’un KPI

- DRAFT ;
- REVIEW ;
- APPROVED ;
- ACTIVE ;
- DEPRECATED ;
- RETIRED.

---

# 98. Administration centrale

L’administration peut gérer :

- sources ;
- connecteurs ;
- pipelines ;
- schémas ;
- événements ;
- jeux de données ;
- tables ;
- métriques ;
- KPI ;
- rapports ;
- tableaux de bord ;
- accès ;
- rôles ;
- qualité ;
- incidents ;
- rétention ;
- classifications ;
- modèles ;
- exports ;
- coûts ;
- environnements ;
- feature flags.

---

# 99. Approbations

Peuvent nécessiter une approbation :

- nouveau connecteur ;
- accès à une donnée sensible ;
- nouveau KPI ;
- export massif ;
- nouvelle source externe ;
- modification d’un schéma actif ;
- suppression d’un jeu de données ;
- publication d’un rapport réglementaire ;
- activation d’un modèle ;
- backfill important ;
- changement de politique de rétention.

---

# 100. Double validation

Peut être exigée pour :

- export de données individuelles ;
- accès à des données hautement sensibles ;
- suppression massive ;
- publication réglementaire ;
- modification d’un KPI financier ;
- activation d’un modèle de risque ;
- import de données partenaires ;
- copie de données Production ;
- modification d’un pipeline critique.

---

# 101. Séparation des rôles

Exemple :

```text
Data Engineer prépare
→ Data Steward contrôle
→ Data Owner approuve
→ Plateforme publie
```

Le demandeur ne doit pas être son unique validateur pour les actions critiques.

---

# 102. API

Exemples :

```http
POST   /data/events
GET    /data/events/schemas
POST   /data/events/schemas

GET    /data/catalog/datasets
GET    /data/catalog/datasets/{id}
POST   /data/catalog/datasets

GET    /data/metrics
POST   /data/metrics
POST   /data/metrics/{id}/publish

GET    /data/dashboards
POST   /data/dashboards
POST   /data/dashboards/{id}/publish

GET    /data/reports
POST   /data/reports
POST   /data/reports/{id}/schedule

GET    /data/quality
GET    /data/pipelines
POST   /data/pipelines/{id}/run
POST   /data/pipelines/{id}/backfill

GET    /data/models
POST   /data/models/{id}/deploy

POST   /data/exports
GET    /data/audit
```

---

# 103. Webhooks internes

Événements possibles :

```text
data.event.rejected
data.schema.published
data.pipeline.started
data.pipeline.completed
data.pipeline.failed
data.dataset.updated
data.dataset.stale
data.quality.warning
data.quality.critical
data.metric.published
data.dashboard.published
data.report.generated
data.export.created
data.export.downloaded
data.model.deployed
data.model.degraded
data.security.alert
```

---

# 104. Intégrations

La plateforme peut se connecter à :

- backend Mansa ;
- PostgreSQL ;
- Redis ;
- Event Bus ;
- Message Queue ;
- ledger ;
- Finance ;
- Support ;
- Sécurité ;
- notifications ;
- stockage objet ;
- outils BI ;
- outils d’orchestration ;
- outils de qualité ;
- outils de catalogue ;
- outils de machine learning ;
- SFTP ;
- partenaires ;
- banques ;
- Mobile Money ;
- réseaux cartes.

Les technologies précises doivent rester remplaçables.

---

# 105. Multi-pays

Chaque pays peut avoir :

- sources ;
- schémas ;
- indicateurs ;
- devises ;
- calendriers ;
- entités ;
- règles de rétention ;
- politiques d’accès ;
- rapports ;
- obligations ;
- fournisseurs ;
- formats ;
- langues.

---

# 106. Multi-devises

La plateforme doit gérer :

- devise de transaction ;
- devise du compte ;
- devise fonctionnelle ;
- devise de reporting ;
- taux de conversion ;
- date du taux ;
- source du taux ;
- montants originaux ;
- montants convertis.

---

# 107. Fuseaux horaires

Les données doivent conserver :

- heure UTC ;
- heure locale ;
- fuseau ;
- pays ;
- date métier ;
- date comptable ;
- date de valeur.

---

# 108. Performance

La plateforme doit être conçue pour :

- grands volumes ;
- requêtes concurrentes ;
- agrégations ;
- partitions ;
- cache ;
- pré-calculs ;
- index ;
- compression ;
- traitement distribué ;
- archivage ;
- reprise après panne.

---

# 109. Gestion des coûts Data

Le système doit suivre :

- stockage ;
- calcul ;
- requêtes ;
- transferts ;
- pipelines ;
- rapports ;
- exports ;
- modèles ;
- environnement ;
- pays ;
- équipe ;
- produit.

---

# 110. Budgets Data

Un budget peut être défini par :

- équipe ;
- pays ;
- produit ;
- environnement ;
- pipeline ;
- projet ;
- modèle ;
- période ;
- utilisateur.

---

# 111. Alertes de coût

Le système doit alerter en cas de :

- requête trop coûteuse ;
- hausse du stockage ;
- pipeline anormal ;
- export volumineux ;
- boucle de traitement ;
- backfill excessif ;
- modèle trop coûteux ;
- dépassement de budget.

---

# 112. Sécurité

Mesures principales :

- MFA ;
- RBAC ;
- ABAC ;
- chiffrement ;
- pseudonymisation ;
- masquage dynamique ;
- accès par ligne ;
- accès par colonne ;
- réseau privé ;
- IP allowlist ;
- audit ;
- détection d’anomalie ;
- gestion des secrets ;
- rotation des clés ;
- révocation.

---

# 113. Protection contre les abus internes

Le système doit détecter :

- requêtes massives ;
- consultation inhabituelle ;
- export excessif ;
- accès hors horaire ;
- accès hors pays ;
- tentative d’accès à une colonne interdite ;
- copie vers un environnement non autorisé ;
- suppression inhabituelle ;
- utilisation d’un compte partagé ;
- téléchargement répété ;
- contournement des filtres.

---

# 114. Audit

Le journal doit contenir :

- utilisateur ;
- rôle ;
- équipe ;
- pays ;
- jeu de données ;
- table ;
- rapport ;
- métrique ;
- export ;
- requête ;
- action ;
- date ;
- heure ;
- appareil ;
- IP ;
- environnement ;
- motif ;
- approbateur ;
- résultat.

---

# 115. Immutabilité des audits

Les journaux d’audit ne doivent pas être :

- modifiés ;
- supprimés ;
- réécrits ;
- désactivés ;
- masqués sans trace ;
- exportés sans permission.

---

# 116. Modèles principaux

- DataSource
- DataConnector
- DataEventSchema
- DataEvent
- DataPipeline
- DataPipelineRun
- DataDataset
- DataTable
- DataColumn
- DataClassification
- DataCatalogEntry
- DataLineageNode
- DataLineageRelation
- DataQualityRule
- DataQualityResult
- DataIncident
- DataMetric
- DataMetricVersion
- DataDashboard
- DataDashboardWidget
- DataReport
- DataReportSchedule
- DataExport
- DataCohort
- DataSegment
- DataExperiment
- DataModel
- DataModelVersion
- DataModelDeployment
- DataRetentionPolicy
- DataApproval
- DataCost
- DataBudget
- DataAudit

---

# 117. Analytics de la plateforme Data

Événements possibles :

```text
data_login_completed
data_dataset_opened
data_dashboard_opened
data_report_generated
data_export_requested
data_export_approved
data_export_downloaded
data_pipeline_started
data_pipeline_failed
data_quality_issue_created
data_metric_created
data_metric_published
data_model_deployed
data_access_denied
data_security_alert_created
```

---

# 118. Données analytics interdites

La plateforme ne doit pas enregistrer dans ses propres analytics :

- contenu complet d’une requête sensible ;
- résultat complet d’un export ;
- données clients détaillées ;
- numéro complet de carte ;
- PIN ;
- OTP ;
- CVV ;
- secret ;
- clé privée ;
- mot de passe ;
- document complet ;
- donnée biométrique ;
- message privé.

---

# 119. Tests

- tests d’ingestion ;
- tests d’événements ;
- tests de schémas ;
- tests de versionnement ;
- tests d’idempotence ;
- tests de déduplication ;
- tests de zone brute ;
- tests de staging ;
- tests de transformations ;
- tests de warehouse ;
- tests de data marts ;
- tests de dimensions ;
- tests de faits ;
- tests d’historisation ;
- tests de lineage ;
- tests de catalogue ;
- tests de qualité ;
- tests de fraîcheur ;
- tests d’incident ;
- tests de pipelines ;
- tests de retries ;
- tests de backfill ;
- tests temps réel ;
- tests batch ;
- tests KPI ;
- tests de cohérence ;
- tests de tableaux de bord ;
- tests de rapports ;
- tests d’exports ;
- tests de segmentation ;
- tests de cohortes ;
- tests de funnels ;
- tests d’expérimentations ;
- tests de modèles ;
- tests Shadow ;
- tests de biais ;
- tests de confidentialité ;
- tests de rétention ;
- tests de suppression ;
- tests multi-pays ;
- tests multi-devises ;
- tests de fuseaux horaires ;
- tests de coûts ;
- tests de sécurité ;
- tests d’audit ;
- tests de performance ;
- tests de reprise.

---

# 120. Règles métier

1. Les systèmes opérationnels restent les sources officielles.
2. La plateforme Data ne modifie jamais directement les opérations.
3. Chaque événement possède un identifiant unique.
4. Chaque événement respecte un schéma versionné.
5. Les données interdites ne sont pas collectées.
6. Les données sensibles sont pseudonymisées.
7. Chaque jeu de données possède un propriétaire.
8. Chaque KPI possède une définition unique.
9. Les transformations sont versionnées.
10. Les pipelines sont surveillés.
11. Les erreurs de qualité créent des alertes.
12. Les données obsolètes sont signalées.
13. Le lineage est conservé.
14. Les exports sensibles sont contrôlés.
15. Les accès sont limités par rôle et périmètre.
16. Les données Production sont séparées des environnements de test.
17. Les modèles sont surveillés.
18. Les modèles peuvent être testés en mode Shadow.
19. L’IA ne prend pas seule de décision critique.
20. Les règles de rétention sont appliquées.
21. Les suppressions sont propagées selon les obligations.
22. Les coûts sont suivis.
23. Les rapports réglementaires utilisent un workflow.
24. Le demandeur ne valide pas seul une action critique.
25. Les audits sont immuables.

---

# 121. Critères d’acceptation

La Plateforme Data, Analytics et Business Intelligence Mansa est validée lorsque :

- toutes les sources autorisées peuvent être connectées ;
- les événements sont versionnés ;
- les événements sont validés ;
- les doublons sont empêchés ;
- les données sensibles sont filtrées ;
- la zone brute est sécurisée ;
- la zone de préparation fonctionne ;
- l’entrepôt est opérationnel ;
- les data marts sont disponibles ;
- la couche sémantique est centralisée ;
- le catalogue de données est disponible ;
- le lineage est visible ;
- les propriétaires sont définis ;
- les classifications sont appliquées ;
- les règles de qualité fonctionnent ;
- les scores de qualité sont disponibles ;
- les incidents Data sont suivis ;
- les pipelines sont orchestrés ;
- les retries fonctionnent ;
- les backfills sont contrôlés ;
- les indicateurs temps réel sont disponibles ;
- les traitements batch fonctionnent ;
- les KPI sont versionnés ;
- les tableaux de bord exécutifs sont disponibles ;
- les indicateurs Client sont disponibles ;
- les indicateurs Cash Network sont disponibles ;
- les indicateurs commerçants sont disponibles ;
- les indicateurs cartes sont disponibles ;
- les indicateurs TPE et DAB sont disponibles ;
- les indicateurs entreprises sont disponibles ;
- les indicateurs scolaires sont disponibles ;
- les indicateurs institutionnels sont disponibles ;
- les indicateurs support sont disponibles ;
- les indicateurs fraude sont disponibles ;
- les indicateurs Finance sont disponibles ;
- les segments sont administrables ;
- les cohortes sont calculables ;
- les funnels sont disponibles ;
- la rétention est mesurable ;
- les parcours peuvent être analysés ;
- les expérimentations sont encadrées ;
- les rapports programmés fonctionnent ;
- les exports sont sécurisés ;
- les tableaux de bord sont filtrables ;
- le drill-down respecte les permissions ;
- les alertes analytiques fonctionnent ;
- les prévisions sont disponibles ;
- les modèles sont versionnés ;
- le mode Shadow fonctionne ;
- la gouvernance Data est définie ;
- les politiques de rétention sont appliquées ;
- les données de test sont séparées ;
- le multi-pays fonctionne ;
- le multi-devises fonctionne ;
- les fuseaux horaires sont gérés ;
- les coûts Data sont mesurés ;
- les accès sensibles sont protégés ;
- les audits sont immuables ;
- les tests couvrent les parcours essentiels.
