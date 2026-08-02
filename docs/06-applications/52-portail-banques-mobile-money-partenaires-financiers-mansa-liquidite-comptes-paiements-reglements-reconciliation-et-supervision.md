# 52 — Portail Banques, Mobile Money et Partenaires Financiers Mansa : liquidité, comptes, paiements, règlements, réconciliation et supervision

## 1. Objet du document

Ce document définit l’architecture officielle du **Portail Banques, Mobile Money et Partenaires Financiers Mansa**.

Ce portail est destiné aux partenaires financiers connectés à l’écosystème Mansa, notamment :

- banques partenaires ;
- établissements de monnaie électronique ;
- opérateurs Mobile Money ;
- réseaux de cartes ;
- processeurs de paiement ;
- acquéreurs ;
- émetteurs ;
- sociétés de transfert ;
- institutions de microfinance ;
- partenaires de règlement ;
- partenaires de change ;
- fournisseurs de comptes et d’IBAN ;
- opérateurs de compensation ;
- partenaires régionaux.

Le portail permet de gérer :

- les comptes de cantonnement ;
- les comptes de règlement ;
- les comptes techniques ;
- la liquidité ;
- les transferts ;
- les paiements ;
- les dépôts ;
- les retraits ;
- les cartes ;
- les autorisations ;
- les règlements ;
- les compensations ;
- les rapprochements ;
- les fichiers financiers ;
- les écarts ;
- les commissions ;
- les frais ;
- les devises ;
- les taux de change ;
- les plafonds ;
- les rejets ;
- les remboursements ;
- les litiges ;
- les incidents ;
- les API ;
- les webhooks ;
- les rapports ;
- les audits ;
- les validations ;
- la sécurité ;
- la supervision des services.

L’objectif est de permettre à Mansa et à ses partenaires financiers de travailler avec une vision commune, traçable et sécurisée des opérations, sans donner au partenaire un accès global à toute la plateforme Mansa.

---

# 2. Principes fondamentaux

## 2.1 Chaque partenaire possède un périmètre isolé

Un partenaire financier ne doit voir que :

- ses comptes ;
- ses produits ;
- ses opérations ;
- ses clients autorisés ;
- ses commerçants autorisés ;
- ses agents autorisés ;
- ses pays ;
- ses devises ;
- ses fichiers ;
- ses règlements ;
- ses incidents ;
- ses environnements.

Il ne doit jamais accéder librement aux données d’un autre partenaire.

---

## 2.2 Le ledger Mansa reste la source comptable interne de Mansa

Le portail partenaire ne doit pas modifier directement :

- les soldes Mansa ;
- les écritures du ledger ;
- les comptes internes ;
- les suspenses ;
- les corrections financières.

Toute modification financière doit passer par un workflow officiel.

---

## 2.3 Les données du partenaire et celles de Mansa doivent être rapprochées

Le système doit pouvoir comparer :

- écritures Mansa ;
- écritures bancaires ;
- opérations Mobile Money ;
- autorisations carte ;
- captures ;
- règlements ;
- fichiers ;
- relevés ;
- commissions ;
- remboursements ;
- rejets ;
- annulations.

---

## 2.4 Aucun réglage financier critique ne doit être codé en dur

Doivent être configurables :

- frais ;
- commissions ;
- plafonds ;
- taux ;
- délais ;
- calendriers ;
- seuils ;
- devises ;
- règles de règlement ;
- règles de réserve ;
- règles de rapprochement ;
- tolérances ;
- priorités ;
- canaux ;
- pays.

---

## 2.5 Toute action sensible doit être auditée

Chaque action doit enregistrer :

- utilisateur ;
- partenaire ;
- rôle ;
- pays ;
- environnement ;
- appareil ;
- date ;
- heure ;
- ancienne valeur ;
- nouvelle valeur ;
- motif ;
- approbateur ;
- résultat ;
- référence de corrélation.

---

# 3. Types de partenaires financiers

Exemples :

- banque de cantonnement ;
- banque de règlement ;
- banque émettrice ;
- banque acquéreuse ;
- banque sponsor ;
- opérateur Mobile Money ;
- processeur carte ;
- réseau Visa ;
- réseau Mastercard ;
- réseau local ;
- établissement de monnaie électronique ;
- société de transfert ;
- institution de microfinance ;
- fournisseur de change ;
- opérateur de compensation ;
- prestataire de conformité ;
- partenaire de trésorerie.

---

# 4. Produits financiers connectés

Le portail peut couvrir :

- wallet Mansa ;
- comptes bancaires ;
- IBAN ou RIB ;
- cartes physiques ;
- cartes virtuelles ;
- virements ;
- transferts instantanés ;
- Mobile Money ;
- dépôts ;
- retraits ;
- TPE ;
- DAB ;
- règlements commerçants ;
- règlements agents ;
- paiements publics ;
- transferts internationaux ;
- change ;
- prélèvements ;
- décaissements de masse.

---

# 5. Technologie

Technologie recommandée :

```text
Next.js
TypeScript
```

Composants associés :

- authentification forte ;
- SSO ;
- MFA ;
- mTLS ;
- API Gateway ;
- fichiers sécurisés ;
- SFTP ;
- webhooks ;
- tableaux de bord ;
- exports ;
- analytics ;
- audit ;
- gestion des approbations ;
- temps réel lorsque disponible.

---

# 6. Architecture du portail

Structure recommandée :

```text
src/
├── auth/
├── dashboard/
├── organizations/
├── accounts/
├── liquidity/
├── payments/
├── transfers/
├── mobile-money/
├── cards/
├── authorizations/
├── clearing/
├── settlements/
├── reconciliation/
├── files/
├── fees/
├── commissions/
├── foreign-exchange/
├── limits/
├── refunds/
├── disputes/
├── incidents/
├── reports/
├── api-access/
├── webhooks/
├── approvals/
├── audit/
├── security/
└── settings/
```

---

# 7. Navigation principale

Navigation recommandée :

```text
Tableau de bord
Comptes
Opérations
Liquidité
Règlements
Rapprochements
Rapports
Configuration
```

Menu secondaire possible :

- Paiements ;
- Transferts ;
- Mobile Money ;
- Cartes ;
- Autorisations ;
- Compensation ;
- Fichiers ;
- Frais ;
- Commissions ;
- Change ;
- Litiges ;
- Incidents ;
- API ;
- Audit ;
- Sécurité.

---

# 8. Tableau de bord partenaire

Le tableau de bord peut afficher :

- volume du jour ;
- nombre d’opérations ;
- opérations réussies ;
- opérations échouées ;
- montant en attente ;
- liquidité disponible ;
- comptes de règlement ;
- règlements prévus ;
- écarts de rapprochement ;
- fichiers en attente ;
- autorisations carte ;
- remboursements ;
- incidents ;
- disponibilité des services ;
- alertes de sécurité.

---

# 9. Tableaux de bord spécialisés

Vues possibles :

- trésorerie ;
- finance ;
- opérations ;
- cartes ;
- Mobile Money ;
- transferts ;
- règlement ;
- réconciliation ;
- conformité ;
- risque ;
- support ;
- technique ;
- direction.

---

# 10. Utilisateurs du partenaire

Rôles possibles :

```text
PARTNER_OWNER
PARTNER_ADMIN
OPERATIONS_MANAGER
TREASURY_MANAGER
FINANCE_MANAGER
RECONCILIATION_AGENT
CARD_OPERATIONS_AGENT
MOBILE_MONEY_OPERATOR
COMPLIANCE_OFFICER
SECURITY_MANAGER
TECHNICAL_OPERATOR
AUDITOR
VIEWER
```

---

# 11. Permissions

Exemples :

```text
financial_partner.dashboard.read
financial_partner.account.read
financial_partner.liquidity.read
financial_partner.liquidity.manage
financial_partner.payment.read
financial_partner.transfer.read
financial_partner.settlement.read
financial_partner.reconciliation.read
financial_partner.reconciliation.manage
financial_partner.file.upload
financial_partner.file.download
financial_partner.refund.read
financial_partner.dispute.manage
financial_partner.report.read
financial_partner.api.manage
financial_partner.audit.read
financial_partner.security.manage
```

---

# 12. Périmètre des utilisateurs

Un utilisateur peut être limité à :

- un pays ;
- une devise ;
- un compte ;
- un produit ;
- un service ;
- une filiale ;
- un type d’opération ;
- un environnement ;
- un montant maximal ;
- une période ;
- une organisation ;
- un canal.

---

# 13. Authentification

Méthodes possibles :

- mot de passe fort ;
- MFA ;
- passkey ;
- clé de sécurité ;
- certificat ;
- SSO ;
- identité fédérée ;
- appareil enregistré ;
- IP autorisée.

---

# 14. MFA obligatoire

Le MFA doit être obligatoire pour :

- tous les administrateurs ;
- la trésorerie ;
- les règlements ;
- les changements bancaires ;
- les exports sensibles ;
- les modifications de clés ;
- l’accès production ;
- les approbations financières.

---

# 15. Comptes financiers

Le portail doit pouvoir représenter :

- compte de cantonnement ;
- compte de règlement ;
- compte opérationnel ;
- compte de réserve ;
- compte de suspense ;
- compte de commission ;
- compte de frais ;
- compte par devise ;
- compte par pays ;
- compte par produit ;
- compte technique.

---

# 16. Fiche d’un compte

Elle doit contenir :

- identifiant ;
- banque ;
- pays ;
- devise ;
- type ;
- numéro masqué ;
- statut ;
- solde déclaré ;
- solde rapproché ;
- dernière mise à jour ;
- propriétaire ;
- produit ;
- règles ;
- historique ;
- alertes.

---

# 17. Statuts d’un compte

- PENDING ;
- ACTIVE ;
- LIMITED ;
- FROZEN ;
- SUSPENDED ;
- CLOSED ;
- RECONCILIATION_REQUIRED ;
- UNDER_REVIEW.

---

# 18. Comptes de cantonnement

Le portail doit permettre de suivre :

- solde du compte ;
- obligations de couverture ;
- monnaie électronique émise ;
- écarts ;
- mouvements ;
- relevés ;
- réserves ;
- rapprochements ;
- alertes ;
- rapports réglementaires.

---

# 19. Couverture des fonds clients

Le système doit pouvoir comparer :

- total des passifs clients ;
- fonds de cantonnement ;
- fonds en transit ;
- réserves ;
- opérations en attente ;
- ajustements ;
- écarts.

Toute insuffisance doit créer une alerte critique.

---

# 20. Liquidité

Le module doit suivre :

- liquidité bancaire ;
- liquidité Mobile Money ;
- liquidité agent ;
- liquidité DAB ;
- liquidité par pays ;
- liquidité par devise ;
- liquidité disponible ;
- liquidité réservée ;
- besoins prévisionnels ;
- seuils ;
- alertes.

---

# 21. Demande de liquidité

Une demande peut contenir :

- partenaire ;
- compte source ;
- compte destination ;
- montant ;
- devise ;
- motif ;
- urgence ;
- date ;
- approbateur ;
- statut ;
- référence.

---

# 22. Statuts de liquidité

- DRAFT ;
- REQUESTED ;
- APPROVAL_PENDING ;
- APPROVED ;
- PROCESSING ;
- COMPLETED ;
- PARTIALLY_COMPLETED ;
- FAILED ;
- CANCELLED ;
- RECONCILIATION_REQUIRED.

---

# 23. Prévision de liquidité

Le système peut utiliser :

- historique ;
- heure ;
- jour ;
- région ;
- événements ;
- salaires ;
- campagnes ;
- périodes de fête ;
- comportement des agents ;
- retraits DAB ;
- volume commerçant ;
- paiements publics.

Les recommandations restent indicatives.

---

# 24. Paiements

Le portail doit afficher :

- référence ;
- type ;
- client masqué ;
- commerçant ;
- canal ;
- montant ;
- devise ;
- frais ;
- commission ;
- statut ;
- partenaire ;
- date ;
- autorisation ;
- capture ;
- règlement ;
- rapprochement.

---

# 25. Statuts de paiement

- CREATED ;
- PENDING ;
- AUTHORIZED ;
- CAPTURED ;
- COMPLETED ;
- FAILED ;
- DECLINED ;
- CANCELLED ;
- REFUNDED ;
- PARTIALLY_REFUNDED ;
- DISPUTED ;
- REVERSED.

---

# 26. Transferts

Types :

- Mansa vers banque ;
- banque vers Mansa ;
- Mansa vers Mobile Money ;
- Mobile Money vers Mansa ;
- banque vers banque ;
- transfert régional ;
- transfert international ;
- règlement partenaire ;
- décaissement de masse ;
- transfert interne.

---

# 27. Données d’un transfert

- référence ;
- origine ;
- destination ;
- montant ;
- devise ;
- frais ;
- taux ;
- bénéficiaire masqué ;
- canal ;
- partenaire ;
- statut ;
- date ;
- motif ;
- règlement ;
- rapprochement.

---

# 28. Intégration Mobile Money

Le portail doit suivre :

- opérateurs ;
- comptes techniques ;
- dépôts ;
- retraits ;
- transferts ;
- commissions ;
- limites ;
- statuts ;
- erreurs ;
- callbacks ;
- rapprochements ;
- liquidité ;
- incidents.

---

# 29. Opérateurs Mobile Money

Chaque opérateur peut avoir :

- pays ;
- devise ;
- produits ;
- API ;
- comptes ;
- clés ;
- certificats ;
- plafonds ;
- frais ;
- commissions ;
- horaires ;
- SLA ;
- règles de reprise ;
- statut.

---

# 30. Dépôt Mobile Money vers Mansa

Le système doit gérer :

1. initiation ;
2. validation du numéro ;
3. calcul des frais ;
4. demande opérateur ;
5. authentification opérateur ;
6. confirmation ;
7. crédit Mansa ;
8. webhook ;
9. reçu ;
10. rapprochement.

---

# 31. Retrait Mansa vers Mobile Money

Le système doit gérer :

1. vérification du bénéficiaire ;
2. vérification du solde ;
3. frais ;
4. contrôle risque ;
5. débit Mansa ;
6. envoi opérateur ;
7. résultat ;
8. reprise éventuelle ;
9. reçu ;
10. rapprochement.

---

# 32. Cartes

Le portail doit permettre de suivre :

- émission ;
- autorisation ;
- capture ;
- clearing ;
- règlement ;
- opposition ;
- remboursement ;
- chargeback ;
- carte virtuelle ;
- carte physique ;
- carte temporaire ;
- tokenisation ;
- provisioning Wallet.

---

# 33. Autorisations carte

Une autorisation doit contenir :

- référence ;
- carte masquée ;
- montant ;
- devise ;
- commerçant ;
- MCC ;
- pays ;
- date ;
- résultat ;
- code de réponse ;
- risque ;
- expiration ;
- capture liée.

---

# 34. Compensation carte

Le portail doit gérer :

- fichiers de clearing ;
- transactions présentées ;
- captures ;
- commissions réseau ;
- interchange ;
- frais ;
- écarts ;
- rejets ;
- chargebacks ;
- règlements.

---

# 35. DAB et retraits

Le partenaire peut suivre :

- retraits ;
- autorisations ;
- coupures ;
- DAB ;
- frais ;
- rejets ;
- annulations ;
- dispenses ;
- cash non délivré ;
- débit sans dispense ;
- rapprochement ;
- litiges.

---

# 36. Débit sans remise d’espèces

Le système doit détecter :

- débit client confirmé ;
- absence de remise de billets ;
- erreur DAB ;
- timeout ;
- journaux techniques ;
- écart cassette ;
- demande de remboursement.

Un dossier automatique peut être créé.

---

# 37. Règlements

Types :

- règlement commerçant ;
- règlement agent ;
- règlement banque ;
- règlement Mobile Money ;
- règlement institution ;
- règlement opérateur ;
- règlement carte ;
- règlement international.

---

# 38. Dossier de règlement

Il doit contenir :

- période ;
- bénéficiaire ;
- compte ;
- montant brut ;
- frais ;
- commissions ;
- taxes ;
- remboursements ;
- réserves ;
- ajustements ;
- montant net ;
- devise ;
- date ;
- statut ;
- référence bancaire.

---

# 39. Statuts de règlement

- CALCULATED ;
- VALIDATION_PENDING ;
- APPROVED ;
- SUBMITTED ;
- PROCESSING ;
- PAID ;
- PARTIALLY_PAID ;
- FAILED ;
- HELD ;
- CANCELLED ;
- RECONCILIATION_REQUIRED.

---

# 40. Calendrier de règlement

Peut être :

- instantané ;
- intrajournalier ;
- quotidien ;
- hebdomadaire ;
- mensuel ;
- personnalisé ;
- selon seuil ;
- selon jour ouvré ;
- selon disponibilité.

---

# 41. Jours ouvrés

Le système doit prendre en compte :

- pays ;
- fuseau horaire ;
- jours fériés ;
- calendriers bancaires ;
- horaires de cut-off ;
- fermeture réseau ;
- maintenance ;
- devise.

---

# 42. Compensation

Le module doit gérer :

- compensation bilatérale ;
- compensation multilatérale ;
- netting ;
- positions brutes ;
- positions nettes ;
- garanties ;
- réserves ;
- soldes dus ;
- dates ;
- statuts ;
- participants.

---

# 43. Rapprochement

Le rapprochement doit comparer :

- API ;
- ledger ;
- relevé bancaire ;
- relevé Mobile Money ;
- fichier carte ;
- clearing ;
- règlement ;
- compte ;
- commission ;
- frais ;
- remboursement ;
- litige.

---

# 44. Types de rapprochement

- automatique ;
- semi-automatique ;
- manuel contrôlé ;
- intrajournalier ;
- quotidien ;
- fin de période ;
- après incident ;
- après fichier.

---

# 45. Statuts de rapprochement

- NOT_STARTED ;
- RUNNING ;
- MATCHED ;
- PARTIALLY_MATCHED ;
- MISMATCH ;
- REVIEW_REQUIRED ;
- RESOLVED ;
- FAILED ;
- CLOSED.

---

# 46. Règles de rapprochement

Elles peuvent utiliser :

- référence ;
- montant ;
- devise ;
- date ;
- heure ;
- compte ;
- partenaire ;
- identifiant externe ;
- corrélation ;
- tolérance ;
- statut ;
- bénéficiaire.

---

# 47. Tolérances

Les tolérances doivent être configurables selon :

- montant ;
- délai ;
- devise ;
- type d’opération ;
- partenaire ;
- pays ;
- canal ;
- règle contractuelle.

---

# 48. Écarts

Exemples :

- opération absente chez le partenaire ;
- opération absente chez Mansa ;
- différence de montant ;
- différence de devise ;
- double opération ;
- statut différent ;
- frais différents ;
- règlement incomplet ;
- remboursement non reçu ;
- fichier manquant.

---

# 49. Traitement d’un écart

Le workflow doit permettre :

1. détection ;
2. classification ;
3. assignation ;
4. analyse ;
5. pièces ;
6. communication partenaire ;
7. correction ;
8. validation ;
9. clôture ;
10. audit.

---

# 50. Fichiers financiers

Le portail peut gérer :

- fichiers de paiements ;
- fichiers de virements ;
- fichiers de clearing ;
- fichiers de règlement ;
- relevés ;
- retours ;
- rejets ;
- chargebacks ;
- commissions ;
- rapports ;
- fichiers réglementaires.

---

# 51. Canaux de fichiers

- portail sécurisé ;
- API ;
- SFTP ;
- stockage chiffré ;
- flux partenaire ;
- dépôt automatisé.

---

# 52. Sécurité des fichiers

Les fichiers doivent être :

- chiffrés ;
- signés ;
- antivirusés ;
- contrôlés ;
- versionnés ;
- horodatés ;
- liés à un partenaire ;
- soumis à rétention ;
- supprimés selon politique.

---

# 53. Statuts d’un fichier

- UPLOADED ;
- VALIDATING ;
- VALID ;
- INVALID ;
- PROCESSING ;
- PROCESSED ;
- PARTIALLY_PROCESSED ;
- REJECTED ;
- ARCHIVED.

---

# 54. Validation des fichiers

Le système doit vérifier :

- format ;
- schéma ;
- encodage ;
- signature ;
- doublon ;
- taille ;
- nombre de lignes ;
- devise ;
- date ;
- compte ;
- totaux ;
- cohérence.

---

# 55. Frais

Le portail doit afficher les règles de frais applicables au partenaire.

Types :

- frais par opération ;
- frais mensuels ;
- frais de traitement ;
- frais de carte ;
- frais de règlement ;
- frais de change ;
- frais de fichier ;
- frais de service ;
- pénalité contractuelle.

---

# 56. Commissions

Exemples :

- commission banque ;
- commission opérateur ;
- commission acquéreur ;
- commission émetteur ;
- interchange ;
- commission Mansa ;
- commission agent ;
- commission réseau ;
- commission partenaire.

---

# 57. Répartition financière

Chaque opération peut produire une répartition entre :

- montant principal ;
- Mansa ;
- banque ;
- opérateur ;
- réseau ;
- agent ;
- commerçant ;
- taxe ;
- réserve ;
- fonds public ;
- autre partenaire.

---

# 58. Simulation financière

Avant activation d’une règle, le système doit permettre de simuler :

- montant ;
- canal ;
- pays ;
- devise ;
- partenaire ;
- produit ;
- date ;
- frais ;
- commissions ;
- net ;
- répartition ;
- impact.

---

# 59. Versionnement

Chaque règle financière doit contenir :

- version ;
- statut ;
- auteur ;
- approbateur ;
- date de création ;
- date d’effet ;
- date d’expiration ;
- contrat ;
- périmètre ;
- historique.

---

# 60. Change

Le portail peut gérer :

- paires de devises ;
- taux partenaire ;
- taux Mansa ;
- marge ;
- frais ;
- validité ;
- source ;
- heure ;
- limite ;
- règlement ;
- historique.

---

# 61. Statuts d’un taux

- DRAFT ;
- PENDING_APPROVAL ;
- ACTIVE ;
- EXPIRED ;
- SUSPENDED ;
- REPLACED ;
- ARCHIVED.

---

# 62. Conversion

Une conversion doit afficher :

- montant source ;
- devise source ;
- taux ;
- frais ;
- marge ;
- montant destination ;
- durée de validité ;
- référence ;
- partenaire.

---

# 63. Plafonds

Le portail doit gérer :

- plafond par opération ;
- plafond journalier ;
- plafond mensuel ;
- plafond partenaire ;
- plafond compte ;
- plafond devise ;
- plafond pays ;
- plafond produit ;
- plafond hors ligne ;
- plafond de règlement.

---

# 64. Réserves

Le système peut gérer :

- réserve roulante ;
- réserve fixe ;
- réserve de risque ;
- réserve de chargeback ;
- réserve réglementaire ;
- réserve de liquidité ;
- date de libération ;
- montant ;
- justification.

---

# 65. Remboursements

Le partenaire peut consulter :

- demande ;
- transaction ;
- montant ;
- motif ;
- statut ;
- date ;
- compte ;
- règlement ;
- preuve ;
- rapprochement.

---

# 66. Litiges et chargebacks

Le portail doit gérer :

- litige client ;
- litige commerçant ;
- chargeback ;
- pré-arbitrage ;
- arbitrage ;
- preuve ;
- délai ;
- montant ;
- réseau ;
- décision ;
- effet financier.

---

# 67. Statuts de litige

- OPEN ;
- EVIDENCE_REQUIRED ;
- UNDER_REVIEW ;
- ACCEPTED ;
- REJECTED ;
- WON ;
- LOST ;
- PARTIALLY_RESOLVED ;
- CLOSED ;
- ESCALATED.

---

# 68. Incidents

Types :

- API indisponible ;
- fichier manquant ;
- retard de règlement ;
- erreur de solde ;
- écart de rapprochement ;
- carte ;
- Mobile Money ;
- virement ;
- sécurité ;
- certificat ;
- liquidité ;
- fraude ;
- compte suspendu.

---

# 69. Dossier d’incident

Il doit contenir :

- référence ;
- partenaire ;
- service ;
- pays ;
- gravité ;
- début ;
- impact ;
- opérations concernées ;
- responsable ;
- chronologie ;
- actions ;
- résolution ;
- rapport final.

---

# 70. Statuts d’incident

- OPEN ;
- ACKNOWLEDGED ;
- INVESTIGATING ;
- IDENTIFIED ;
- MITIGATING ;
- MONITORING ;
- RESOLVED ;
- CLOSED.

---

# 71. SLA

Le portail doit suivre :

- disponibilité ;
- temps de réponse ;
- taux de succès ;
- délais de règlement ;
- délais de rapprochement ;
- temps de résolution ;
- retards ;
- violations ;
- pénalités éventuelles.

---

# 72. API et intégrations

Le partenaire peut disposer d’un accès à :

- Payments API ;
- Transfers API ;
- Mobile Money API ;
- Cards API ;
- Settlement API ;
- Reconciliation API ;
- Account API ;
- Reporting API ;
- Webhook API ;
- File API.

---

# 73. Authentification API

Méthodes possibles :

- OAuth 2.0 ;
- client credentials ;
- mTLS ;
- certificat ;
- signature ;
- API key limitée ;
- IP allowlist.

---

# 74. Webhooks

Événements possibles :

```text
financial.payment.completed
financial.payment.failed
financial.transfer.completed
financial.transfer.failed
financial.settlement.created
financial.settlement.paid
financial.reconciliation.mismatch
financial.refund.completed
financial.dispute.opened
financial.account.balance.updated
financial.liquidity.warning
financial.file.processed
financial.incident.created
```

---

# 75. Signature et idempotence

Les opérations sensibles doivent utiliser :

```http
Idempotency-Key
X-Request-Id
X-Correlation-Id
Mansa-Signature
Mansa-Timestamp
```

---

# 76. Rapports

Rapports possibles :

- opérations ;
- volumes ;
- liquidité ;
- comptes ;
- paiements ;
- transferts ;
- Mobile Money ;
- cartes ;
- règlements ;
- compensation ;
- rapprochement ;
- écarts ;
- commissions ;
- frais ;
- change ;
- remboursements ;
- litiges ;
- SLA ;
- incidents.

---

# 77. Exports

Formats possibles :

- CSV ;
- XLSX ;
- PDF ;
- JSON ;
- API ;
- SFTP.

Les exports doivent être :

- autorisés ;
- chiffrés ;
- temporaires ;
- limités ;
- masqués ;
- auditables.

---

# 78. Rapports programmés

Un rapport peut être produit :

- chaque heure ;
- quotidiennement ;
- chaque semaine ;
- chaque mois ;
- après règlement ;
- après rapprochement ;
- après incident ;
- à la clôture.

---

# 79. Notifications

Le partenaire peut recevoir :

- liquidité faible ;
- règlement disponible ;
- règlement échoué ;
- fichier rejeté ;
- écart détecté ;
- certificat expirant ;
- clé expirante ;
- incident ;
- maintenance ;
- changement de règle ;
- litige ;
- remboursement ;
- dépassement de seuil.

---

# 80. Approbations

Peuvent exiger une approbation :

- nouveau compte ;
- changement bancaire ;
- modification de plafond ;
- changement de commission ;
- nouveau taux ;
- transfert de liquidité ;
- règlement manuel ;
- correction ;
- export massif ;
- activation production ;
- nouveau pays.

---

# 81. Double validation

Peut être exigée pour :

- mouvement de liquidité important ;
- changement de compte ;
- règlement manuel ;
- correction de rapprochement ;
- modification de taux ;
- augmentation de plafond ;
- ajout d’un administrateur ;
- rotation de certificat ;
- réactivation après incident ;
- activation d’un nouveau produit.

---

# 82. Séparation demandeur-validateur

Le créateur d’une demande critique ne doit pas pouvoir l’approuver seul.

---

# 83. Administration Mansa

Le portail Admin Mansa doit pouvoir gérer :

- partenaires ;
- contrats ;
- produits ;
- pays ;
- comptes ;
- utilisateurs ;
- rôles ;
- permissions ;
- plafonds ;
- frais ;
- commissions ;
- règlements ;
- rapprochements ;
- fichiers ;
- API ;
- certificats ;
- incidents ;
- audits ;
- SLA ;
- feature flags.

---

# 84. Administration partenaire

L’administrateur partenaire peut gérer selon ses droits :

- utilisateurs ;
- équipes ;
- appareils ;
- clés ;
- certificats ;
- webhooks ;
- rapports ;
- notifications ;
- comptes visibles ;
- exports ;
- paramètres locaux ;
- contacts d’urgence.

---

# 85. Actions critiques

Doivent être protégées :

- changement de compte de règlement ;
- mouvement de liquidité ;
- modification de taux ;
- modification de commission ;
- modification de plafond ;
- règlement manuel ;
- correction d’écart ;
- ajout d’un accès production ;
- modification de certificat ;
- export massif ;
- fermeture d’un incident majeur.

---

# 86. Audit

Le journal doit contenir :

- utilisateur ;
- partenaire ;
- rôle ;
- action ;
- ressource ;
- ancienne valeur ;
- nouvelle valeur ;
- date ;
- heure ;
- IP ;
- appareil ;
- pays ;
- environnement ;
- motif ;
- résultat ;
- approbateur ;
- référence.

---

# 87. Immutabilité

Les audits ne doivent pas être :

- modifiés ;
- supprimés ;
- réécrits ;
- désactivés ;
- masqués sans trace ;
- exportés sans permission.

---

# 88. Sécurité

Mesures principales :

- MFA ;
- RBAC ;
- ABAC ;
- SSO ;
- mTLS ;
- certificats ;
- chiffrement ;
- IP allowlist ;
- WAF ;
- rate limiting ;
- surveillance ;
- détection d’anomalie ;
- révocation ;
- audit ;
- gestion des secrets.

---

# 89. Protection des données

Ne pas afficher en clair :

- numéro complet de carte ;
- CVV ;
- PIN ;
- OTP ;
- mot de passe ;
- clé privée ;
- secret API ;
- document complet non nécessaire ;
- donnée biométrique ;
- compte complet non autorisé.

---

# 90. Multi-pays

Chaque pays peut avoir :

- partenaires ;
- banques ;
- opérateurs ;
- devises ;
- comptes ;
- calendriers ;
- jours ouvrés ;
- règles ;
- plafonds ;
- frais ;
- commissions ;
- taux ;
- règlements ;
- obligations réglementaires.

---

# 91. Multi-devises

Le portail doit gérer :

- devise de transaction ;
- devise de règlement ;
- devise du compte ;
- conversion ;
- taux ;
- arrondi ;
- écart de change ;
- gain ou perte ;
- reporting.

---

# 92. Modèles

- FinancialPartner
- FinancialPartnerUser
- FinancialPartnerRole
- FinancialPartnerPermission
- FinancialPartnerAccount
- SafeguardingAccount
- SettlementAccount
- LiquidityPosition
- LiquidityRequest
- PartnerPayment
- PartnerTransfer
- MobileMoneyOperator
- MobileMoneyTransaction
- CardAuthorization
- CardClearingRecord
- FinancialSettlement
- ClearingPosition
- ReconciliationRun
- ReconciliationMatch
- ReconciliationMismatch
- FinancialFile
- FinancialFeeRule
- FinancialCommissionRule
- ForeignExchangeRate
- FinancialLimit
- FinancialReserve
- FinancialRefund
- FinancialDispute
- FinancialIncident
- FinancialSla
- FinancialAudit

---

# 93. API

Exemples :

```http
GET    /financial-partner/dashboard
GET    /financial-partner/accounts
GET    /financial-partner/liquidity

GET    /financial-partner/payments
GET    /financial-partner/transfers
GET    /financial-partner/mobile-money
GET    /financial-partner/card-authorizations

GET    /financial-partner/settlements
GET    /financial-partner/reconciliation
POST   /financial-partner/reconciliation/{id}/mismatches

POST   /financial-partner/files
GET    /financial-partner/files/{id}

GET    /financial-partner/reports
GET    /financial-partner/incidents
POST   /financial-partner/incidents

POST   /financial-partner/liquidity-requests
POST   /financial-partner/production-requests
```

---

# 94. Analytics

Événements possibles :

```text
financial_partner_login_completed
financial_partner_account_opened
financial_partner_liquidity_warning
financial_partner_payment_opened
financial_partner_settlement_opened
financial_partner_reconciliation_started
financial_partner_reconciliation_completed
financial_partner_mismatch_created
financial_partner_file_uploaded
financial_partner_file_processed
financial_partner_report_exported
financial_partner_incident_created
financial_partner_security_alert_created
```

---

# 95. Données analytics interdites

Ne pas transmettre :

- PIN ;
- OTP ;
- CVV ;
- numéro complet de carte ;
- mot de passe ;
- clé privée ;
- secret API ;
- payload financier complet ;
- document complet ;
- donnée biométrique ;
- contenu confidentiel.

---

# 96. Tests

- tests d’authentification ;
- tests MFA ;
- tests de rôles ;
- tests de permissions ;
- tests de périmètres ;
- tests multi-pays ;
- tests multi-devises ;
- tests comptes ;
- tests cantonnement ;
- tests liquidité ;
- tests paiements ;
- tests transferts ;
- tests Mobile Money ;
- tests cartes ;
- tests autorisations ;
- tests clearing ;
- tests règlements ;
- tests compensation ;
- tests rapprochement ;
- tests tolérances ;
- tests écarts ;
- tests fichiers ;
- tests SFTP ;
- tests frais ;
- tests commissions ;
- tests change ;
- tests plafonds ;
- tests réserves ;
- tests remboursements ;
- tests litiges ;
- tests incidents ;
- tests API ;
- tests webhooks ;
- tests sécurité ;
- tests audit ;
- tests performance ;
- tests accessibilité.

---

# 97. Règles métier

1. Chaque partenaire financier possède un périmètre isolé.
2. Les données d’un partenaire ne sont pas visibles par un autre.
3. Le ledger Mansa reste la source interne officielle.
4. Aucun solde ne peut être modifié directement depuis le portail.
5. Les corrections passent par un workflow.
6. Les comptes sont liés à un pays et une devise.
7. Les comptes sensibles sont masqués.
8. Les liquidités sont surveillées.
9. Les insuffisances de couverture créent une alerte.
10. Les règlements sont calculés par le backend.
11. Les frais sont administrables.
12. Les commissions sont administrables.
13. Les taux de change sont versionnés.
14. Les plafonds sont configurables.
15. Les fichiers sont signés et chiffrés.
16. Les rapprochements sont traçables.
17. Les écarts sont assignés et résolus.
18. Les opérations sensibles utilisent l’idempotence.
19. Les webhooks sont signés.
20. Les clés et certificats sont révocables.
21. Les données sensibles sont masquées.
22. Les exports sont audités.
23. Le demandeur ne valide pas seul une action critique.
24. Les audits sont immuables.
25. Les actions critiques peuvent exiger une double validation.

---

# 98. Critères d’acceptation

Le Portail Banques, Mobile Money et Partenaires Financiers Mansa est validé lorsque :

- les partenaires peuvent être onboardés ;
- les utilisateurs possèdent des rôles limités ;
- les périmètres sont appliqués ;
- les comptes sont visibles selon les droits ;
- les comptes de cantonnement sont suivis ;
- la couverture des fonds est contrôlée ;
- la liquidité est supervisée ;
- les paiements sont consultables ;
- les transferts sont consultables ;
- les intégrations Mobile Money sont suivies ;
- les autorisations carte sont visibles ;
- la compensation est prise en charge ;
- les règlements sont gérés ;
- les calendriers sont configurables ;
- les rapprochements sont automatisés ;
- les écarts peuvent être traités ;
- les fichiers sont sécurisés ;
- les frais et commissions sont dynamiques ;
- les taux de change sont versionnés ;
- les plafonds et réserves sont administrables ;
- les remboursements sont suivis ;
- les litiges sont gérés ;
- les incidents sont centralisés ;
- les API et webhooks sont sécurisés ;
- les rapports et exports sont disponibles ;
- les actions sensibles utilisent un workflow ;
- les audits sont immuables ;
- les tests couvrent les parcours essentiels.
