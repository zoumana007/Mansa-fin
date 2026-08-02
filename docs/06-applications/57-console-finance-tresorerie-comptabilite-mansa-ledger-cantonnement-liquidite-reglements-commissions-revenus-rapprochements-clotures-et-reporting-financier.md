# 57 — Console Finance, Trésorerie et Comptabilité Mansa : ledger, cantonnement, liquidité, règlements, commissions, revenus, rapprochements, clôtures et reporting financier

## 1. Objet du document

Ce document définit l’architecture officielle de la **Console Finance, Trésorerie et Comptabilité Mansa**.

Cette console est destinée aux équipes financières, comptables, de trésorerie, de contrôle interne et de direction de Mansa.

Elle permet de superviser et administrer :

- le ledger ;
- les comptes internes ;
- les comptes clients ;
- les comptes commerçants ;
- les comptes agents ;
- les comptes partenaires ;
- les comptes de cantonnement ;
- les comptes bancaires ;
- les comptes Mobile Money ;
- les comptes de règlement ;
- les comptes techniques ;
- les suspenses ;
- la liquidité ;
- les réserves ;
- les règlements ;
- les compensations ;
- les rapprochements ;
- les frais ;
- les commissions ;
- les revenus Mansa ;
- les coûts partenaires ;
- les taxes ;
- les remboursements ;
- les chargebacks ;
- les corrections ;
- les ajustements ;
- les clôtures ;
- les rapports comptables ;
- les rapports de gestion ;
- les rapports réglementaires ;
- les exports ;
- les validations ;
- les audits ;
- les prévisions ;
- le multi-pays ;
- le multi-devises.

L’objectif est de fournir une console financière centralisée permettant de :

- garantir l’équilibre du ledger ;
- suivre les fonds clients ;
- contrôler les comptes de cantonnement ;
- superviser la trésorerie ;
- anticiper les besoins de liquidité ;
- automatiser les règlements ;
- calculer les commissions ;
- mesurer les revenus ;
- rapprocher toutes les sources ;
- identifier les écarts ;
- clôturer les périodes ;
- produire des rapports fiables ;
- protéger les actions sensibles ;
- assurer une traçabilité complète ;
- préparer l’expansion régionale de Mansa.

---

# 2. Principes fondamentaux

## 2.1 Le ledger est la source comptable interne officielle

Tous les soldes Mansa doivent être calculés à partir d’écritures comptables.

Aucun solde ne doit être modifié directement.

Toute variation doit provenir :

- d’une transaction ;
- d’une écriture ;
- d’un ajustement autorisé ;
- d’une écriture compensatrice ;
- d’un remboursement ;
- d’un règlement ;
- d’une conversion ;
- d’une clôture.

---

## 2.2 Le système doit respecter la partie double

Chaque opération financière doit générer au minimum :

- un débit ;
- un crédit ;
- un montant identique ;
- une devise cohérente ;
- une référence ;
- une date comptable ;
- une date de valeur ;
- un journal ;
- une origine ;
- un statut.

Une opération ne doit pas être validée si elle déséquilibre le ledger.

---

## 2.3 Une écriture validée est immuable

Une écriture validée ne doit pas être :

- modifiée ;
- supprimée ;
- remplacée silencieusement ;
- réécrite ;
- antidatée sans procédure.

Toute correction doit passer par :

- une contrepassation ;
- une écriture compensatrice ;
- une nouvelle écriture ;
- une justification ;
- une approbation ;
- un audit complet.

---

## 2.4 Les fonds clients doivent être séparés des fonds propres Mansa

Le système doit distinguer :

- passifs envers les clients ;
- fonds de cantonnement ;
- revenus Mansa ;
- commissions partenaires ;
- frais ;
- taxes ;
- réserves ;
- fonds propres ;
- fonds en transit ;
- suspenses.

---

## 2.5 Aucun paramètre financier ne doit être codé en dur

Doivent être administrables :

- plans comptables ;
- frais ;
- commissions ;
- taxes ;
- taux ;
- seuils ;
- plafonds ;
- calendriers ;
- règles de règlement ;
- règles de rapprochement ;
- règles de clôture ;
- méthodes d’arrondi ;
- périodes ;
- devises ;
- comptes ;
- partenaires ;
- journaux.

---

## 2.6 Toute action sensible doit être auditée

Chaque action doit enregistrer :

- utilisateur ;
- rôle ;
- équipe ;
- pays ;
- entité ;
- compte ;
- période ;
- ancienne valeur ;
- nouvelle valeur ;
- motif ;
- preuve ;
- date ;
- heure ;
- appareil ;
- IP ;
- approbateur ;
- résultat ;
- référence de corrélation.

---

# 3. Utilisateurs de la console

Rôles possibles :

```text
CHIEF_FINANCIAL_OFFICER
FINANCE_DIRECTOR
HEAD_OF_TREASURY
TREASURY_ANALYST
CHIEF_ACCOUNTANT
ACCOUNTANT
FINANCIAL_CONTROLLER
RECONCILIATION_MANAGER
RECONCILIATION_ANALYST
SETTLEMENT_MANAGER
SETTLEMENT_ANALYST
REVENUE_ANALYST
TAX_MANAGER
FINANCIAL_REPORTING_MANAGER
INTERNAL_CONTROLLER
INTERNAL_AUDITOR
EXTERNAL_AUDITOR
VIEWER
```

---

# 4. Permissions

Exemples :

```text
finance.dashboard.read
finance.ledger.read
finance.ledger.export
finance.account.read
finance.account.manage
finance.entry.read
finance.adjustment.request
finance.adjustment.approve
finance.treasury.read
finance.treasury.manage
finance.liquidity.read
finance.liquidity.manage
finance.settlement.read
finance.settlement.manage
finance.reconciliation.read
finance.reconciliation.manage
finance.fee.read
finance.fee.manage
finance.commission.read
finance.commission.manage
finance.revenue.read
finance.tax.read
finance.tax.manage
finance.close.read
finance.close.manage
finance.report.read
finance.report.export
finance.audit.read
```

---

# 5. Périmètres d’accès

Un utilisateur peut être limité à :

- un pays ;
- une devise ;
- une entité juridique ;
- une filiale ;
- un compte ;
- un journal ;
- un produit ;
- un partenaire ;
- un canal ;
- un type d’opération ;
- une période ;
- un montant maximal ;
- un environnement ;
- un centre de coûts.

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

- tous les utilisateurs Finance ;
- les accès production ;
- les ajustements ;
- les règlements ;
- les changements de compte bancaire ;
- les exports sensibles ;
- les clôtures ;
- les modifications de règles ;
- les approbations ;
- les réouvertures de période.

---

# 8. Architecture du projet

Structure recommandée :

```text
src/
├── auth/
├── dashboard/
├── ledger/
├── chart-of-accounts/
├── accounts/
├── journals/
├── entries/
├── balances/
├── treasury/
├── liquidity/
├── safeguarding/
├── bank-accounts/
├── mobile-money-accounts/
├── settlements/
├── clearing/
├── reconciliation/
├── suspenses/
├── fees/
├── commissions/
├── revenues/
├── costs/
├── taxes/
├── foreign-exchange/
├── reserves/
├── refunds/
├── chargebacks/
├── adjustments/
├── closing/
├── forecasts/
├── budgets/
├── reports/
├── approvals/
├── integrations/
├── notifications/
├── audit/
├── security/
└── settings/
```

---

# 9. Navigation principale

Navigation recommandée :

```text
Tableau de bord
Ledger
Comptes
Trésorerie
Règlements
Rapprochements
Clôtures
Rapports
Configuration
```

Menu secondaire :

- Plan comptable ;
- Journaux ;
- Écritures ;
- Soldes ;
- Cantonnement ;
- Liquidité ;
- Banques ;
- Mobile Money ;
- Compensation ;
- Suspenses ;
- Frais ;
- Commissions ;
- Revenus ;
- Coûts ;
- Taxes ;
- Change ;
- Réserves ;
- Ajustements ;
- Prévisions ;
- Audit.

---

# 10. Tableau de bord financier

Le tableau de bord peut afficher :

- total des soldes clients ;
- total du cantonnement ;
- taux de couverture ;
- liquidité disponible ;
- liquidité réservée ;
- fonds en transit ;
- comptes en suspense ;
- règlements à venir ;
- règlements échoués ;
- écarts de rapprochement ;
- revenus du jour ;
- revenus du mois ;
- commissions dues ;
- taxes collectées ;
- remboursements ;
- chargebacks ;
- opérations non comptabilisées ;
- périodes ouvertes ;
- alertes critiques.

---

# 11. Tableaux de bord spécialisés

Vues possibles :

- direction financière ;
- trésorerie ;
- comptabilité ;
- rapprochement ;
- règlement ;
- revenus ;
- fiscalité ;
- contrôle interne ;
- audit ;
- pays ;
- produit ;
- partenaire ;
- devise.

---

# 12. Ledger

Le ledger doit gérer :

- comptes ;
- sous-comptes ;
- journaux ;
- écritures ;
- soldes ;
- devises ;
- dates comptables ;
- dates de valeur ;
- références ;
- statuts ;
- sources ;
- événements ;
- liens transactionnels ;
- réconciliations ;
- audits.

---

# 13. Types de comptes ledger

Exemples :

- actif ;
- passif ;
- produit ;
- charge ;
- capitaux propres ;
- compte de transit ;
- compte de suspense ;
- compte de réserve ;
- compte de commission ;
- compte de taxe ;
- compte de règlement ;
- compte technique.

---

# 14. Plan comptable

Le plan comptable doit être configurable selon :

- pays ;
- entité ;
- devise ;
- produit ;
- réglementation ;
- type de compte ;
- exercice ;
- norme comptable ;
- partenaire.

---

# 15. Fiche d’un compte comptable

Elle doit contenir :

- code ;
- nom ;
- type ;
- parent ;
- entité ;
- pays ;
- devise ;
- produit ;
- statut ;
- solde ;
- sens normal ;
- date d’ouverture ;
- date de clôture ;
- règles ;
- restrictions ;
- historique.

---

# 16. Statuts d’un compte

- DRAFT ;
- ACTIVE ;
- LIMITED ;
- FROZEN ;
- CLOSING ;
- CLOSED ;
- ARCHIVED.

---

# 17. Journaux comptables

Exemples :

- journal paiements ;
- journal transferts ;
- journal cartes ;
- journal Mobile Money ;
- journal Cash Network ;
- journal commerçants ;
- journal agents ;
- journal règlements ;
- journal remboursements ;
- journal commissions ;
- journal frais ;
- journal taxes ;
- journal change ;
- journal ajustements ;
- journal clôture.

---

# 18. Écriture comptable

Chaque écriture doit contenir :

- identifiant ;
- journal ;
- compte débit ;
- compte crédit ;
- montant ;
- devise ;
- date comptable ;
- date de valeur ;
- référence ;
- événement source ;
- transaction ;
- pays ;
- entité ;
- statut ;
- description ;
- métadonnées ;
- auteur technique ;
- historique.

---

# 19. Statuts d’une écriture

- DRAFT ;
- PENDING ;
- POSTED ;
- REVERSED ;
- REJECTED ;
- CANCELLED ;
- UNDER_REVIEW.

---

# 20. Groupes d’écritures

Une transaction complexe peut générer plusieurs lignes comptables.

Exemples :

- montant principal ;
- frais client ;
- commission agent ;
- commission banque ;
- commission Mansa ;
- taxe ;
- réserve ;
- règlement ;
- change.

Le groupe doit rester équilibré.

---

# 21. Validation de l’équilibre

Avant comptabilisation, le système doit vérifier :

- total débit = total crédit ;
- devise cohérente ;
- comptes actifs ;
- période ouverte ;
- référence unique ;
- règles respectées ;
- montants valides ;
- droits disponibles ;
- événement source existant.

---

# 22. Soldes

Le système doit distinguer :

- solde comptable ;
- solde disponible ;
- solde réservé ;
- solde en attente ;
- solde bloqué ;
- solde en transit ;
- solde de clôture ;
- solde rapproché.

---

# 23. Reconstruction des soldes

Le système doit pouvoir reconstruire un solde à partir :

- des écritures ;
- de la date ;
- du compte ;
- de la devise ;
- du journal ;
- de l’entité ;
- du pays.

---

# 24. Snapshots de solde

Des snapshots peuvent être générés :

- intrajournaliers ;
- quotidiens ;
- hebdomadaires ;
- mensuels ;
- à la clôture ;
- avant migration ;
- après incident.

Ils ne remplacent pas les écritures.

---

# 25. Comptes clients

Le système doit distinguer :

- portefeuille principal ;
- portefeuille secondaire ;
- coffre ;
- budget ;
- solde promotionnel ;
- solde bloqué ;
- solde en transit ;
- solde de carte ;
- solde de récompense ;
- devise.

---

# 26. Comptes commerçants

Le système doit gérer :

- encaissements ;
- montants bruts ;
- frais ;
- commissions ;
- remboursements ;
- réserves ;
- règlements ;
- impayés ;
- chargebacks ;
- soldes en attente.

---

# 27. Comptes agents

Le système doit distinguer :

- float ;
- espèces déclarées ;
- commissions ;
- bonus ;
- réserves ;
- montants en transit ;
- suspenses ;
- remboursements ;
- compte personnel séparé.

---

# 28. Comptes partenaires

Exemples :

- banque ;
- Mobile Money ;
- réseau carte ;
- acquéreur ;
- émetteur ;
- processeur ;
- institution ;
- entreprise ;
- établissement ;
- opérateur de règlement.

---

# 29. Comptes de cantonnement

Le système doit suivre :

- compte bancaire ;
- banque ;
- pays ;
- devise ;
- solde bancaire ;
- solde ledger ;
- obligations de couverture ;
- écarts ;
- relevés ;
- rapprochements ;
- alertes ;
- réserves ;
- statut.

---

# 30. Couverture des fonds clients

Le calcul doit comparer :

```text
Fonds cantonnés disponibles
+ fonds autorisés en transit
- éléments non éligibles
÷ passifs clients éligibles
```

Le résultat doit produire :

- montant couvert ;
- montant requis ;
- écart ;
- ratio ;
- statut ;
- alerte ;
- action recommandée.

---

# 31. Statuts de couverture

- OVER_COVERED ;
- FULLY_COVERED ;
- WARNING ;
- UNDER_COVERED ;
- CRITICAL ;
- UNKNOWN ;
- RECONCILIATION_REQUIRED.

---

# 32. Alertes de cantonnement

Exemples :

- couverture insuffisante ;
- relevé manquant ;
- écart de solde ;
- compte gelé ;
- mouvement inhabituel ;
- règlement non reçu ;
- transfert non confirmé ;
- compte inactif ;
- risque de liquidité.

---

# 33. Trésorerie

Le module Trésorerie doit suivre :

- positions bancaires ;
- positions Mobile Money ;
- positions en espèces ;
- positions DAB ;
- positions agents ;
- positions par pays ;
- positions par devise ;
- besoins ;
- excédents ;
- prévisions ;
- seuils ;
- transferts ;
- risques.

---

# 34. Position de trésorerie

Elle doit afficher :

- solde d’ouverture ;
- entrées ;
- sorties ;
- solde courant ;
- solde disponible ;
- solde réservé ;
- engagements ;
- prévisions ;
- seuil minimum ;
- seuil maximum ;
- devise ;
- compte ;
- date.

---

# 35. Liquidité

Le système doit suivre :

- liquidité disponible ;
- liquidité mobilisable ;
- liquidité réservée ;
- liquidité opérationnelle ;
- liquidité réglementaire ;
- liquidité agent ;
- liquidité DAB ;
- liquidité partenaire ;
- liquidité projetée.

---

# 36. Demande de liquidité

Une demande doit contenir :

- source ;
- destination ;
- montant ;
- devise ;
- pays ;
- motif ;
- urgence ;
- date prévue ;
- demandeur ;
- approbateur ;
- statut ;
- référence ;
- effet attendu.

---

# 37. Statuts d’une demande de liquidité

- DRAFT ;
- REQUESTED ;
- REVIEW ;
- APPROVED ;
- SCHEDULED ;
- PROCESSING ;
- COMPLETED ;
- PARTIALLY_COMPLETED ;
- FAILED ;
- CANCELLED ;
- RECONCILIATION_REQUIRED.

---

# 38. Prévisions de trésorerie

Les prévisions peuvent utiliser :

- historique ;
- jours de paie ;
- périodes de fête ;
- campagnes ;
- saisonnalité ;
- volumes clients ;
- volumes commerçants ;
- retraits DAB ;
- retraits agents ;
- paiements publics ;
- règlements ;
- échéances partenaires ;
- change.

---

# 39. Scénarios de trésorerie

Exemples :

- scénario normal ;
- croissance forte ;
- retraits élevés ;
- panne d’un partenaire ;
- indisponibilité bancaire ;
- crise de liquidité ;
- forte demande Mobile Money ;
- lancement dans un nouveau pays ;
- campagne nationale ;
- versement massif de bourses.

---

# 40. Règlements

Le système doit gérer :

- règlements commerçants ;
- règlements agents ;
- règlements institutions ;
- règlements entreprises ;
- règlements écoles ;
- règlements banques ;
- règlements Mobile Money ;
- règlements cartes ;
- règlements partenaires ;
- règlements internationaux.

---

# 41. Calcul d’un règlement

Le calcul peut inclure :

```text
Volume brut
- remboursements
- chargebacks
- frais
- commissions
- taxes
- réserves
+ ajustements
= montant net à régler
```

Chaque composant doit être traçable.

---

# 42. Dossier de règlement

Il doit contenir :

- bénéficiaire ;
- période ;
- compte ;
- devise ;
- volume brut ;
- frais ;
- commissions ;
- taxes ;
- remboursements ;
- réserves ;
- ajustements ;
- montant net ;
- date prévue ;
- statut ;
- référence ;
- rapprochement ;
- pièces.

---

# 43. Statuts d’un règlement

- DRAFT ;
- CALCULATED ;
- REVIEW_REQUIRED ;
- APPROVAL_PENDING ;
- APPROVED ;
- SUBMITTED ;
- PROCESSING ;
- PAID ;
- PARTIALLY_PAID ;
- FAILED ;
- HELD ;
- CANCELLED ;
- RECONCILIATION_REQUIRED ;
- CLOSED.

---

# 44. Calendrier de règlement

Le calendrier peut être :

- instantané ;
- intrajournalier ;
- quotidien ;
- hebdomadaire ;
- bimensuel ;
- mensuel ;
- personnalisé ;
- selon seuil ;
- selon jour ouvré ;
- selon contrat.

---

# 45. Règlements retenus

Un règlement peut être retenu pour :

- fraude ;
- litige ;
- réserve ;
- compte bancaire invalide ;
- KYC ou KYB incomplet ;
- écart de rapprochement ;
- décision de conformité ;
- incident ;
- dette ;
- document manquant ;
- instruction réglementaire.

---

# 46. Règlement manuel

Un règlement manuel doit exiger :

- justification ;
- bénéficiaire ;
- montant ;
- compte ;
- pièces ;
- simulation ;
- demandeur ;
- double validation ;
- audit ;
- rapprochement.

---

# 47. Compensation

Le système doit gérer :

- compensation bilatérale ;
- compensation multilatérale ;
- positions brutes ;
- positions nettes ;
- netting ;
- garanties ;
- réserves ;
- obligations ;
- participants ;
- dates ;
- statuts.

---

# 48. Rapprochements

Le système doit rapprocher :

- ledger ;
- banque ;
- Mobile Money ;
- carte ;
- TPE ;
- DAB ;
- agent ;
- commerçant ;
- institution ;
- partenaire ;
- fichiers ;
- règlements ;
- remboursements ;
- chargebacks.

---

# 49. Types de rapprochement

- transactionnel ;
- comptable ;
- bancaire ;
- partenaire ;
- carte ;
- Mobile Money ;
- caisse agent ;
- DAB ;
- règlement ;
- cantonnement ;
- fiscal ;
- intercompagnie.

---

# 50. Statuts d’un rapprochement

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

# 51. Règles de rapprochement

Les correspondances peuvent utiliser :

- référence ;
- identifiant externe ;
- montant ;
- devise ;
- date ;
- heure ;
- compte ;
- bénéficiaire ;
- partenaire ;
- type ;
- statut ;
- tolérance ;
- groupe d’écritures.

---

# 52. Tolérances

Les tolérances peuvent dépendre :

- du partenaire ;
- du produit ;
- de la devise ;
- du délai ;
- du montant ;
- du pays ;
- du canal ;
- du contrat ;
- du type d’opération.

---

# 53. Écarts de rapprochement

Exemples :

- opération absente du ledger ;
- opération absente chez le partenaire ;
- montant différent ;
- devise différente ;
- statut différent ;
- date différente ;
- doublon ;
- frais incorrects ;
- commission incorrecte ;
- règlement incomplet ;
- relevé manquant ;
- remboursement non reçu.

---

# 54. Dossier d’écart

Il doit contenir :

- référence ;
- source ;
- type ;
- montant ;
- devise ;
- pays ;
- partenaire ;
- cause probable ;
- analyste ;
- priorité ;
- statut ;
- preuves ;
- actions ;
- correction ;
- approbation ;
- clôture.

---

# 55. Suspenses

Les comptes de suspense peuvent contenir :

- transaction non identifiée ;
- paiement non rapproché ;
- transfert incomplet ;
- règlement échoué ;
- montant sans référence ;
- différence de change ;
- erreur partenaire ;
- fichier incomplet ;
- opération en investigation.

---

# 56. Gestion d’un suspense

Chaque élément doit avoir :

- date d’entrée ;
- montant ;
- devise ;
- origine ;
- motif ;
- compte ;
- responsable ;
- âge ;
- statut ;
- action attendue ;
- date limite ;
- résolution.

---

# 57. Vieillissement des suspenses

Le système doit afficher :

- moins de 24 heures ;
- 1 à 3 jours ;
- 4 à 7 jours ;
- 8 à 30 jours ;
- plus de 30 jours ;
- plus de 90 jours.

Les seuils restent configurables.

---

# 58. Frais

Le moteur de frais doit gérer :

- frais fixes ;
- frais variables ;
- combinaison fixe et pourcentage ;
- minimum ;
- maximum ;
- gratuité ;
- subvention ;
- partage ;
- promotion ;
- frais par pays ;
- frais par canal ;
- frais par partenaire ;
- frais par segment.

---

# 59. Commissions

Le système doit gérer :

- commission Mansa ;
- commission agent ;
- commission commerçant ;
- commission banque ;
- commission Mobile Money ;
- commission émetteur ;
- commission acquéreur ;
- interchange ;
- commission réseau ;
- commission institution ;
- commission partenaire ;
- commission apporteur.

---

# 60. Versionnement des frais et commissions

Chaque règle doit contenir :

- version ;
- auteur ;
- approbateur ;
- date de création ;
- date d’effet ;
- date d’expiration ;
- pays ;
- produit ;
- partenaire ;
- statut ;
- historique ;
- contrat lié.

---

# 61. Statuts d’une règle financière

- DRAFT ;
- SIMULATION ;
- REVIEW ;
- APPROVED ;
- SCHEDULED ;
- ACTIVE ;
- SUSPENDED ;
- EXPIRED ;
- REPLACED ;
- ARCHIVED.

---

# 62. Simulation financière

Avant activation, le système doit permettre de simuler :

- volume ;
- montant ;
- canal ;
- pays ;
- partenaire ;
- client ;
- agent ;
- commerçant ;
- frais ;
- commissions ;
- taxes ;
- revenus ;
- net ;
- impact mensuel ;
- impact annuel.

---

# 63. Revenus Mansa

Sources possibles :

- frais de transfert ;
- frais de retrait ;
- frais de carte ;
- frais commerçant ;
- frais TPE ;
- frais DAB ;
- frais premium ;
- frais entreprise ;
- frais institution ;
- frais partenaire ;
- frais API ;
- frais de change ;
- commissions ;
- abonnements ;
- services additionnels.

---

# 64. Reconnaissance des revenus

Le système doit distinguer :

- revenu facturé ;
- revenu encaissé ;
- revenu acquis ;
- revenu différé ;
- revenu en attente ;
- revenu annulé ;
- revenu remboursé ;
- revenu contesté.

---

# 65. Coûts Mansa

Exemples :

- banque partenaire ;
- Mobile Money ;
- réseau carte ;
- processeur ;
- SMS ;
- e-mail ;
- KYC ;
- KYB ;
- cloud ;
- support ;
- agent ;
- terminal ;
- DAB ;
- assurance ;
- fraude ;
- chargeback ;
- change ;
- partenaire externe.

---

# 66. Marge

Le système doit calculer :

```text
Revenus
- coûts directs
- commissions
- pertes
- remboursements
- taxes non récupérables
= marge
```

La marge peut être analysée par :

- produit ;
- pays ;
- canal ;
- partenaire ;
- client ;
- commerçant ;
- agent ;
- période ;
- devise.

---

# 67. Taxes

Le système doit gérer :

- taxes sur frais ;
- taxes sur commissions ;
- TVA ;
- retenues ;
- taxes locales ;
- taxes partenaires ;
- taxes par pays ;
- exonérations ;
- règles de déclaration ;
- comptes dédiés.

---

# 68. Fiche d’une taxe

Elle doit contenir :

- code ;
- nom ;
- pays ;
- taux ;
- base ;
- produit ;
- canal ;
- date d’effet ;
- compte comptable ;
- statut ;
- règle d’arrondi ;
- historique.

---

# 69. Change

Le module change doit suivre :

- devise source ;
- devise destination ;
- taux de marché ;
- taux partenaire ;
- taux Mansa ;
- marge ;
- frais ;
- date ;
- validité ;
- source ;
- position ;
- gain ou perte ;
- règlement.

---

# 70. Gains et pertes de change

Le système doit distinguer :

- gain réalisé ;
- perte réalisée ;
- gain latent ;
- perte latente ;
- écart de conversion ;
- écart de règlement ;
- écart d’arrondi.

---

# 71. Réserves

Types possibles :

- réserve de liquidité ;
- réserve de chargeback ;
- réserve commerçant ;
- réserve agent ;
- réserve partenaire ;
- réserve fraude ;
- réserve réglementaire ;
- réserve de remboursement ;
- réserve roulante ;
- réserve fixe.

---

# 72. Remboursements

Le système doit suivre :

- transaction d’origine ;
- demande ;
- montant ;
- devise ;
- motif ;
- compte ;
- écritures ;
- statut ;
- approbations ;
- date ;
- rapprochement ;
- impact sur le règlement.

---

# 73. Chargebacks

Le système doit gérer :

- montant ;
- réseau ;
- transaction ;
- commerçant ;
- client ;
- étape ;
- preuve ;
- délai ;
- provision ;
- résultat ;
- effet financier ;
- règlement ;
- écritures.

---

# 74. Ajustements comptables

Types possibles :

- erreur de compte ;
- erreur de montant ;
- erreur de devise ;
- correction de frais ;
- correction de commission ;
- correction de taxe ;
- différence de rapprochement ;
- perte ;
- récupération ;
- reclassement ;
- contrepassation.

---

# 75. Demande d’ajustement

Elle doit contenir :

- compte ;
- période ;
- montant ;
- devise ;
- motif ;
- écriture liée ;
- pièce ;
- demandeur ;
- approbateur ;
- date ;
- statut ;
- impact ;
- référence.

---

# 76. Statuts d’un ajustement

- DRAFT ;
- SUBMITTED ;
- REVIEW ;
- APPROVAL_PENDING ;
- APPROVED ;
- POSTED ;
- REJECTED ;
- CANCELLED ;
- REVERSED.

---

# 77. Double validation des ajustements

Le demandeur ne doit pas pouvoir valider seul son ajustement.

Une validation supplémentaire peut dépendre :

- du montant ;
- du compte ;
- du pays ;
- de la période ;
- du motif ;
- de la sensibilité ;
- du produit ;
- de l’impact réglementaire.

---

# 78. Périodes comptables

Le système doit gérer :

- jour ;
- semaine ;
- mois ;
- trimestre ;
- semestre ;
- exercice ;
- période spéciale ;
- période de migration.

---

# 79. Statuts d’une période

- FUTURE ;
- OPEN ;
- SOFT_CLOSED ;
- REVIEW ;
- HARD_CLOSED ;
- REOPENED ;
- ARCHIVED.

---

# 80. Clôture journalière

La clôture journalière doit vérifier :

- équilibre du ledger ;
- opérations en attente ;
- écritures rejetées ;
- rapprochements ;
- cantonnement ;
- liquidité ;
- règlements ;
- suspenses ;
- frais ;
- commissions ;
- taxes ;
- revenus ;
- alertes ;
- fichiers partenaires.

---

# 81. Clôture mensuelle

La clôture mensuelle peut inclure :

- contrôle des soldes ;
- provisions ;
- charges à payer ;
- produits à recevoir ;
- revenus différés ;
- réévaluation change ;
- rapprochements bancaires ;
- rapprochements partenaires ;
- suspenses ;
- taxes ;
- commissions ;
- règlements ;
- rapport de gestion ;
- validation finale.

---

# 82. Soft close

La clôture souple doit :

- empêcher certaines écritures ;
- autoriser les corrections contrôlées ;
- signaler les éléments manquants ;
- maintenir une piste d’audit ;
- préparer la clôture définitive.

---

# 83. Hard close

La clôture définitive doit :

- verrouiller la période ;
- empêcher toute écriture ordinaire ;
- générer les soldes de clôture ;
- produire les rapports ;
- archiver les validations ;
- nécessiter une procédure pour toute réouverture.

---

# 84. Réouverture d’une période

Une réouverture doit exiger :

- motif ;
- période ;
- comptes concernés ;
- impact ;
- demandeur ;
- approbation renforcée ;
- durée ;
- journal spécial ;
- audit ;
- reclôture.

---

# 85. Checklist de clôture

Exemples :

- ledger équilibré ;
- comptes bancaires rapprochés ;
- cantonnement validé ;
- Mobile Money rapproché ;
- cartes rapprochées ;
- suspenses contrôlés ;
- règlements validés ;
- commissions calculées ;
- taxes vérifiées ;
- revenus reconnus ;
- ajustements validés ;
- rapports générés ;
- approbations obtenues.

---

# 86. Prévisions financières

Le système peut prévoir :

- revenus ;
- coûts ;
- liquidité ;
- volumes ;
- règlements ;
- commissions ;
- taxes ;
- pertes fraude ;
- chargebacks ;
- besoins en capital ;
- croissance par pays ;
- croissance par produit.

---

# 87. Budgets internes

La console peut suivre :

- budget global ;
- budget par pays ;
- budget par équipe ;
- budget par produit ;
- budget marketing ;
- budget infrastructure ;
- budget support ;
- budget fraude ;
- budget cartes ;
- budget expansion.

---

# 88. Écart budget-réel

Le système doit afficher :

- budget ;
- réel ;
- écart ;
- pourcentage ;
- cause ;
- tendance ;
- prévision ;
- commentaire ;
- responsable.

---

# 89. Rapports comptables

Rapports possibles :

- balance générale ;
- grand livre ;
- journal ;
- balance auxiliaire ;
- état des comptes ;
- bilan ;
- compte de résultat ;
- flux de trésorerie ;
- variation des capitaux propres ;
- détails des suspenses ;
- détail des ajustements.

---

# 90. Rapports de gestion

Exemples :

- revenus par produit ;
- revenus par pays ;
- marge par canal ;
- coût par transaction ;
- coût partenaire ;
- rentabilité commerçant ;
- rentabilité agent ;
- rentabilité carte ;
- rentabilité Mobile Money ;
- croissance ;
- prévisions ;
- pertes.

---

# 91. Rapports de trésorerie

Exemples :

- position quotidienne ;
- liquidité ;
- prévision ;
- flux entrants ;
- flux sortants ;
- comptes bancaires ;
- comptes Mobile Money ;
- exposition devises ;
- besoins de financement ;
- concentration bancaire.

---

# 92. Rapports réglementaires

Selon le pays, le système peut préparer :

- couverture des fonds ;
- monnaie électronique en circulation ;
- fonds cantonnés ;
- volumes ;
- comptes actifs ;
- transactions ;
- fraude ;
- suspenses ;
- liquidité ;
- revenus ;
- commissions ;
- taxes ;
- incidents.

La transmission doit suivre un workflow autorisé.

---

# 93. Rapports partenaires

Le système peut produire des rapports pour :

- banques ;
- Mobile Money ;
- réseaux cartes ;
- institutions ;
- entreprises ;
- écoles ;
- commerçants ;
- agents ;
- opérateurs ;
- investisseurs ;
- auditeurs.

---

# 94. Exports

Formats possibles :

- CSV ;
- XLSX ;
- PDF ;
- JSON ;
- API ;
- SFTP ;
- format comptable ;
- paquet d’audit.

Les exports doivent être :

- autorisés ;
- chiffrés ;
- signés ;
- limités ;
- temporaires ;
- auditables ;
- masqués selon le rôle.

---

# 95. Rapports programmés

Un rapport peut être généré :

- intrajournalier ;
- quotidiennement ;
- chaque semaine ;
- mensuellement ;
- chaque trimestre ;
- à la clôture ;
- après règlement ;
- après incident ;
- après rapprochement.

---

# 96. Notifications

Exemples :

- couverture insuffisante ;
- liquidité faible ;
- compte non rapproché ;
- règlement échoué ;
- suspense ancien ;
- clôture bloquée ;
- écriture déséquilibrée ;
- ajustement en attente ;
- commission anormale ;
- taxe manquante ;
- compte bancaire modifié ;
- période réouverte ;
- export sensible.

---

# 97. Approbations

Peuvent nécessiter une approbation :

- création de compte ;
- modification du plan comptable ;
- ajustement ;
- règlement manuel ;
- transfert de liquidité ;
- changement bancaire ;
- modification de frais ;
- modification de commission ;
- modification de taxe ;
- clôture ;
- réouverture ;
- export massif ;
- changement de taux ;
- annulation comptable.

---

# 98. Double validation

Peut être exigée pour :

- ajustement élevé ;
- règlement manuel ;
- changement de compte de cantonnement ;
- transfert important ;
- modification de commission ;
- modification de taxe ;
- changement de taux ;
- réouverture de période ;
- correction d’un compte sensible ;
- export réglementaire ;
- clôture définitive.

---

# 99. Séparation des rôles

Exemple :

```text
Comptable prépare
→ Contrôleur vérifie
→ Responsable Finance approuve
→ Backend comptabilise
```

Le demandeur ne doit pas être son unique validateur.

---

# 100. Intégrations

La console doit pouvoir se connecter à :

- backend Mansa ;
- ledger ;
- banques ;
- Mobile Money ;
- réseaux cartes ;
- processeurs ;
- TPE ;
- DAB ;
- Cash Network ;
- partenaires ;
- ERP ;
- logiciel comptable ;
- outil fiscal ;
- BI ;
- SFTP ;
- outils d’audit ;
- outils de trésorerie ;
- observabilité.

---

# 101. API

Exemples :

```http
GET    /finance/dashboard
GET    /finance/ledger/accounts
GET    /finance/ledger/entries
GET    /finance/ledger/balances

GET    /finance/treasury/positions
GET    /finance/liquidity
POST   /finance/liquidity-requests

GET    /finance/settlements
POST   /finance/settlements/{id}/approve
POST   /finance/settlements/{id}/submit

GET    /finance/reconciliations
GET    /finance/reconciliations/{id}/mismatches
POST   /finance/reconciliations/{id}/resolve

GET    /finance/fees
GET    /finance/commissions
GET    /finance/revenues
GET    /finance/taxes

POST   /finance/adjustments
POST   /finance/adjustments/{id}/approve

GET    /finance/periods
POST   /finance/periods/{id}/soft-close
POST   /finance/periods/{id}/hard-close
POST   /finance/periods/{id}/reopen

GET    /finance/reports
GET    /finance/audit
```

---

# 102. Webhooks

Événements possibles :

```text
finance.entry.posted
finance.entry.reversed
finance.ledger.unbalanced
finance.safeguarding.warning
finance.safeguarding.underfunded
finance.liquidity.warning
finance.liquidity.requested
finance.settlement.calculated
finance.settlement.approved
finance.settlement.paid
finance.settlement.failed
finance.reconciliation.mismatch
finance.suspense.created
finance.adjustment.requested
finance.adjustment.posted
finance.period.soft_closed
finance.period.hard_closed
finance.period.reopened
```

---

# 103. Multi-pays

Chaque pays peut avoir :

- entité juridique ;
- plan comptable ;
- devise ;
- comptes bancaires ;
- cantonnement ;
- partenaires ;
- taxes ;
- règles ;
- clôtures ;
- calendriers ;
- rapports ;
- obligations ;
- seuils ;
- normes ;
- formats d’export.

---

# 104. Multi-devises

Le système doit gérer :

- devise de transaction ;
- devise du compte ;
- devise fonctionnelle ;
- devise de présentation ;
- taux ;
- conversion ;
- arrondi ;
- exposition ;
- gain ;
- perte ;
- règlement ;
- consolidation.

---

# 105. Consolidation

La console doit pouvoir consolider :

- plusieurs pays ;
- plusieurs entités ;
- plusieurs devises ;
- plusieurs produits ;
- plusieurs filiales ;
- plusieurs plans comptables.

Les éliminations intercompagnies doivent être traçables.

---

# 106. Sécurité de la console

Mesures principales :

- MFA ;
- RBAC ;
- ABAC ;
- chiffrement ;
- appareils gérés ;
- certificats ;
- IP allowlist ;
- réseau privé ;
- accès bastion ;
- réauthentification ;
- sessions courtes ;
- masquage ;
- watermark ;
- audit ;
- surveillance ;
- révocation.

---

# 107. Protection contre la fraude interne

Le système doit détecter :

- ajustements fréquents ;
- règlements manuels inhabituels ;
- changement bancaire ;
- réouverture répétée ;
- export massif ;
- modification de taux ;
- modification de commission ;
- utilisation d’un compte partagé ;
- actions hors horaires ;
- approbations croisées suspectes ;
- contournement de workflow ;
- consultation sans justification.

---

# 108. Audit

Le journal doit contenir :

- utilisateur ;
- rôle ;
- équipe ;
- pays ;
- entité ;
- compte ;
- écriture ;
- période ;
- action ;
- ancienne valeur ;
- nouvelle valeur ;
- date ;
- heure ;
- appareil ;
- IP ;
- motif ;
- résultat ;
- approbateur ;
- référence.

---

# 109. Immutabilité des audits

Les audits ne doivent pas être :

- modifiés ;
- supprimés ;
- réécrits ;
- désactivés ;
- masqués sans trace ;
- exportés sans permission.

---

# 110. Modèles principaux

- FinanceUser
- FinanceRole
- FinancePermission
- LedgerAccount
- LedgerAccountGroup
- LedgerJournal
- LedgerEntry
- LedgerEntryLine
- LedgerBalance
- LedgerSnapshot
- FinancialEntity
- BankAccount
- MobileMoneyAccount
- SafeguardingAccount
- SafeguardingPosition
- TreasuryPosition
- LiquidityPosition
- LiquidityRequest
- FinancialSettlement
- SettlementLine
- ClearingPosition
- ReconciliationRun
- ReconciliationMatch
- ReconciliationMismatch
- SuspenseItem
- FeeRule
- CommissionRule
- RevenueEntry
- CostEntry
- TaxRule
- ForeignExchangeRate
- ForeignExchangePosition
- FinancialReserve
- FinancialRefund
- ChargebackProvision
- AccountingAdjustment
- AccountingPeriod
- ClosingChecklist
- FinancialForecast
- FinancialBudget
- FinancialReport
- FinanceApproval
- FinanceNotification
- FinanceAudit

---

# 111. Analytics

Événements possibles :

```text
finance_login_completed
finance_ledger_account_opened
finance_entry_opened
finance_safeguarding_warning_created
finance_liquidity_warning_created
finance_liquidity_request_created
finance_settlement_opened
finance_settlement_approved
finance_reconciliation_started
finance_reconciliation_completed
finance_mismatch_created
finance_suspense_opened
finance_adjustment_requested
finance_adjustment_approved
finance_period_soft_closed
finance_period_hard_closed
finance_period_reopened
finance_report_exported
finance_security_alert_created
```

---

# 112. Données analytics interdites

Ne pas transmettre :

- PIN ;
- OTP ;
- CVV ;
- numéro complet de carte ;
- numéro complet de compte non autorisé ;
- clé privée ;
- secret API ;
- mot de passe ;
- payload financier complet ;
- relevé complet ;
- document confidentiel ;
- détail complet d’écriture sensible ;
- donnée biométrique.

---

# 113. Tests

- tests d’authentification ;
- tests MFA ;
- tests de rôles ;
- tests de permissions ;
- tests de périmètres ;
- tests du plan comptable ;
- tests des comptes ;
- tests des journaux ;
- tests des écritures ;
- tests partie double ;
- tests d’équilibre ;
- tests d’immutabilité ;
- tests de contrepassation ;
- tests de soldes ;
- tests de snapshots ;
- tests clients ;
- tests commerçants ;
- tests agents ;
- tests partenaires ;
- tests cantonnement ;
- tests couverture ;
- tests trésorerie ;
- tests liquidité ;
- tests prévisions ;
- tests règlements ;
- tests compensation ;
- tests rapprochement ;
- tests tolérances ;
- tests écarts ;
- tests suspenses ;
- tests vieillissement ;
- tests frais ;
- tests commissions ;
- tests revenus ;
- tests coûts ;
- tests marge ;
- tests taxes ;
- tests change ;
- tests réserves ;
- tests remboursements ;
- tests chargebacks ;
- tests ajustements ;
- tests approbations ;
- tests clôture journalière ;
- tests clôture mensuelle ;
- tests soft close ;
- tests hard close ;
- tests réouverture ;
- tests rapports ;
- tests exports ;
- tests multi-pays ;
- tests multi-devises ;
- tests consolidation ;
- tests sécurité ;
- tests audit ;
- tests performance ;
- tests accessibilité.

---

# 114. Règles métier

1. Le ledger est la source comptable interne officielle.
2. Aucun solde n’est modifié directement.
3. Toute opération respecte la partie double.
4. Le total des débits égale le total des crédits.
5. Une écriture validée est immuable.
6. Une correction utilise une contrepassation ou une écriture compensatrice.
7. Les fonds clients sont séparés des fonds propres Mansa.
8. Les comptes sont liés à une entité et une devise.
9. Les périodes contrôlent la comptabilisation.
10. Les comptes de cantonnement sont rapprochés.
11. Toute insuffisance de couverture crée une alerte.
12. La liquidité est suivie par pays et devise.
13. Les règlements sont calculés par le backend.
14. Les règlements manuels nécessitent une approbation.
15. Les rapprochements sont traçables.
16. Les écarts sont assignés et résolus.
17. Les suspenses sont suivis par ancienneté.
18. Les frais sont versionnés.
19. Les commissions sont versionnées.
20. Les taxes sont administrables.
21. Les ajustements nécessitent une justification.
22. Les clôtures utilisent une checklist.
23. Une période fermée ne reçoit pas d’écriture ordinaire.
24. Le demandeur ne valide pas seul une action critique.
25. Les audits sont immuables.

---

# 115. Critères d’acceptation

La Console Finance, Trésorerie et Comptabilité Mansa est validée lorsque :

- les utilisateurs se connectent avec MFA ;
- les rôles et périmètres sont appliqués ;
- le plan comptable est configurable ;
- les comptes sont administrables ;
- les écritures respectent la partie double ;
- le ledger reste équilibré ;
- les écritures validées sont immuables ;
- les contrepassations fonctionnent ;
- les soldes sont reconstructibles ;
- les snapshots sont disponibles ;
- les comptes clients sont séparés ;
- les comptes commerçants sont suivis ;
- les comptes agents sont séparés de leurs comptes personnels ;
- les comptes partenaires sont rapprochés ;
- les comptes de cantonnement sont supervisés ;
- la couverture des fonds est calculée ;
- les alertes de couverture fonctionnent ;
- la trésorerie est visible ;
- la liquidité est supervisée ;
- les prévisions sont disponibles ;
- les règlements sont calculés ;
- les règlements manuels sont contrôlés ;
- la compensation est prise en charge ;
- les rapprochements sont automatisés ;
- les écarts peuvent être résolus ;
- les suspenses sont suivis ;
- les frais et commissions sont dynamiques ;
- les revenus et coûts sont calculés ;
- les marges sont analysables ;
- les taxes sont configurables ;
- le change est pris en charge ;
- les réserves sont administrables ;
- les remboursements et chargebacks sont comptabilisés ;
- les ajustements utilisent un workflow ;
- les périodes comptables sont administrables ;
- les clôtures journalières fonctionnent ;
- les clôtures mensuelles fonctionnent ;
- la réouverture est contrôlée ;
- les rapports comptables sont disponibles ;
- les rapports de gestion sont disponibles ;
- les rapports réglementaires sont préparables ;
- les exports sont sécurisés ;
- le multi-pays fonctionne ;
- le multi-devises fonctionne ;
- la consolidation est possible ;
- les actions critiques sont protégées ;
- les audits sont immuables ;
- les tests couvrent les parcours essentiels.
