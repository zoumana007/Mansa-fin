# Cahier des charges — Wallets, ledger et gestion des soldes

## 1. Objectif

Ce module constitue le cœur financier de Mansa. Il gère les portefeuilles, comptes techniques, écritures comptables, soldes disponibles et réservés, mouvements internes, rapprochements et règles garantissant qu’aucune opération financière ne crée ou ne détruit de valeur de manière incohérente.

Il sert de source de vérité financière pour les applications Client, Commerçant, TPE, Admin, modules État, cartes, Mobile Money, paiements, transferts et intégrations bancaires.

## 2. Principes fondamentaux

1. Le ledger est en partie double : toute opération équilibrée produit au minimum un débit et un crédit de même valeur dans une même devise.
2. Aucun montant n’est stocké en nombre flottant. Les montants utilisent l’unité monétaire minimale sous forme entière.
3. Une écriture comptabilisée est immuable. Une correction se fait par contre-écriture ou écriture compensatrice.
4. Chaque commande financière mutable exige une clé d’idempotence.
5. Le solde visible n’est jamais modifié directement sans écriture de ledger correspondante.
6. Chaque opération possède un identifiant métier, un identifiant de corrélation et un journal d’audit.
7. Les traitements concurrents doivent empêcher tout double débit et tout dépassement de solde autorisé.
8. Les devises ne sont jamais mélangées dans une même écriture équilibrée sans opération de change explicite.
9. Les environnements Démo, Recette et Production ont des ledgers strictement séparés.
10. Aucun administrateur ne peut réécrire l’historique comptable depuis une interface métier.

## 3. Périmètre

Le module couvre :

- création et cycle de vie des wallets ;
- comptes comptables internes ;
- ledger en partie double ;
- soldes disponibles, réservés, comptables et en attente ;
- holds/réservations ;
- captures, libérations et expirations ;
- transferts internes ;
- frais et commissions ;
- remboursements et annulations ;
- comptes de règlement partenaires ;
- rapprochement ;
- blocages financiers ;
- limites et contrôles préalables ;
- exports comptables et audit.

Les rails externes tels que banque, carte ou Mobile Money sont gérés par des modules d’intégration séparés qui consomment ce ledger.

## 4. Types de wallets

### 4.1 Wallet client

Portefeuille principal d’un particulier. Il peut être associé à une devise et à un pays. Un utilisateur peut posséder plusieurs wallets seulement si la configuration produit et réglementaire l’autorise.

### 4.2 Wallet commerçant

Reçoit les paiements commerciaux et supporte les règlements, remboursements, commissions et transferts autorisés.

### 4.3 Wallet agent

Utilisé pour les opérations d’agent, notamment cash-in/cash-out lorsque le modèle commercial les prévoit.

### 4.4 Wallet administration publique

Utilisé pour les encaissements de taxes, amendes, frais administratifs, scolarité ou autres services publics, avec règles de règlement propres à l’entité publique.

### 4.5 Wallet technique

Réservé aux besoins du système : clearing, suspense, frais, commissions, règlement, remboursements, réserve ou autres fonctions comptables. Il n’est jamais exposé comme wallet client ordinaire.

## 5. Modèle comptable minimal

Entités principales :

- `Wallet` ;
- `LedgerAccount` ;
- `JournalEntry` ;
- `Posting` ;
- `BalanceSnapshot` ;
- `Hold` ;
- `FinancialTransaction` ;
- `FeeAssessment` ;
- `SettlementAccount` ;
- `ReconciliationRecord` ;
- `LedgerAdjustmentRequest` ;
- `FinancialAuditEvent`.

Chaque `JournalEntry` possède au minimum :

- UUID ;
- type d’opération ;
- statut ;
- devise ;
- date de valeur ;
- date de comptabilisation ;
- source métier ;
- référence externe éventuelle ;
- clé d’idempotence ;
- identifiant de corrélation ;
- somme totale des débits ;
- somme totale des crédits ;
- métadonnées structurées non sensibles.

Une entrée ne peut passer à `POSTED` que si total débits = total crédits.

## 6. Soldes

Le système distingue au minimum :

- `ledgerBalance` : solde issu des écritures comptabilisées ;
- `availableBalance` : montant immédiatement utilisable ;
- `reservedBalance` : fonds bloqués par des holds ;
- `pendingCredit` : crédit attendu mais non définitivement réglé lorsque nécessaire ;
- `pendingDebit` : débit en cours lorsqu’un rail externe impose un état intermédiaire.

Invariant principal :

`availableBalance = ledgerBalance - reservedBalance - autres_blocages_applicables`

Les règles exactes sont centralisées et testées. Les applications clientes ne recalculent jamais le solde de manière indépendante.

## 7. Cycle de vie d’un wallet

Statuts minimaux :

- `PENDING` ;
- `ACTIVE` ;
- `RESTRICTED` ;
- `SUSPENDED` ;
- `CLOSING` ;
- `CLOSED`.

Un wallet fermé ne peut plus recevoir de nouvelles opérations sauf mouvements techniques explicitement autorisés pour clôture, correction ou règlement résiduel.

La fermeture exige notamment :

- absence de holds actifs ;
- traitement des opérations en attente ;
- solde conforme aux règles de clôture ;
- conservation de l’historique réglementaire.

## 8. Ledger en partie double

Exemple simplifié d’un transfert de 10 000 FCFA entre deux wallets Mansa :

- débit du compte de passif représentant le wallet émetteur : 10 000 ;
- crédit du compte de passif représentant le wallet destinataire : 10 000.

Pour un frais de 100 FCFA :

- débit du wallet payeur : 100 ;
- crédit du compte de revenus/frais correspondant : 100.

Les règles de posting sont définies dans un catalogue versionné. Le code métier ne construit pas arbitrairement des écritures comptables dispersées dans plusieurs modules.

## 9. Catalogue des opérations

Types initiaux :

- `WALLET_FUNDING` ;
- `INTERNAL_TRANSFER` ;
- `MERCHANT_PAYMENT` ;
- `CASH_IN` ;
- `CASH_OUT` ;
- `CARD_AUTHORIZATION` ;
- `CARD_CAPTURE` ;
- `CARD_REVERSAL` ;
- `MOBILE_MONEY_IN` ;
- `MOBILE_MONEY_OUT` ;
- `BANK_TRANSFER_IN` ;
- `BANK_TRANSFER_OUT` ;
- `FEE` ;
- `COMMISSION` ;
- `REFUND` ;
- `REVERSAL` ;
- `SETTLEMENT` ;
- `ADJUSTMENT` ;
- `PUBLIC_PAYMENT`.

Chaque type référence un schéma de comptabilisation validé.

## 10. Idempotence

Toute commande financière accepte `Idempotency-Key` ou équivalent contractuel.

Le backend associe la clé à :

- acteur ou client API ;
- endpoint/opération ;
- empreinte des paramètres critiques ;
- résultat ;
- durée de conservation.

Une répétition identique retourne le résultat déjà produit. Une réutilisation de la même clé avec des paramètres différents est rejetée et auditée.

## 11. Concurrence et atomicité

Le système garantit qu’un wallet ne peut être débité simultanément au-delà de son solde disponible.

Les mécanismes peuvent utiliser, selon l’architecture retenue :

- transaction PostgreSQL ;
- verrouillage de lignes ciblé ;
- version optimiste ;
- contrainte d’unicité ;
- sérialisation contrôlée sur les ressources financières critiques.

Le choix doit privilégier la correction comptable avant l’optimisation prématurée.

La création de transaction métier, des postings et de l’état financier critique doit être atomique autant que possible dans la même frontière transactionnelle.

## 12. Holds et réservations

Un hold réserve temporairement une partie du solde disponible sans la comptabiliser comme débit définitif.

Cas d’usage :

- autorisation carte ;
- paiement TPE nécessitant confirmation ;
- retrait en cours ;
- transfert vers rail externe ;
- opération soumise à contrôle additionnel.

Statuts :

- `ACTIVE` ;
- `PARTIALLY_CAPTURED` ;
- `CAPTURED` ;
- `RELEASED` ;
- `EXPIRED`.

Un hold possède : montant initial, montant restant, devise, wallet, motif, transaction source, échéance et référence externe.

## 13. Capture et libération

Une capture transforme tout ou partie du hold en débit comptabilisé.

Une libération restitue le montant réservé au solde disponible sans créer de revenu ou perte artificielle.

Toute capture supérieure au montant restant est interdite sauf règle explicite du rail concerné, documentée et contrôlée.

Les expirations sont traitées par un worker idempotent.

## 14. Transferts internes

Un transfert interne Mansa suit :

1. validation de l’émetteur ;
2. contrôle du statut wallet ;
3. contrôle KYC/limites ;
4. contrôle risque ;
5. validation du bénéficiaire ;
6. calcul des frais ;
7. vérification du solde disponible ;
8. écriture atomique ;
9. publication d’événements ;
10. notification asynchrone.

Le bénéficiaire ne doit jamais recevoir deux crédits si l’appel est rejoué.

## 15. Frais et commissions

Les frais sont calculés par un moteur de tarification externe au ledger mais comptabilisés par le ledger.

Un frais contient :

- règle tarifaire ;
- base de calcul ;
- pourcentage éventuel ;
- minimum ;
- maximum ;
- montant final ;
- taxe éventuelle ;
- bénéficiaire comptable ;
- version de règle.

Les commissions agents/partenaires sont des mouvements distincts et auditables.

Une modification de tarification ne modifie jamais rétroactivement une transaction déjà comptabilisée.

## 16. Remboursements et reversals

Un remboursement crée une nouvelle transaction liée à l’originale. Il ne supprime ni ne modifie les postings historiques.

Le système supporte :

- remboursement total ;
- remboursement partiel ;
- plusieurs remboursements partiels dans la limite du montant remboursable ;
- reversal technique lorsque l’opération d’origine doit être neutralisée.

Chaque remboursement contrôle le cumul déjà remboursé et son autorisation métier.

## 17. Ajustements manuels

Aucun opérateur ne peut modifier un solde directement.

Un ajustement exceptionnel nécessite :

- motif structuré ;
- pièce/référence éventuelle ;
- initiateur ;
- montant ;
- comptes concernés ;
- validation par une seconde personne au-delà des seuils définis ;
- journal d’audit ;
- écriture compensatrice explicite.

Les ajustements de production sont réservés à des rôles très limités.

## 18. Blocages et restrictions

Le ledger consomme les décisions des modules conformité et risque.

Restrictions possibles :

- interdiction de débit ;
- interdiction de crédit ;
- blocage d’un montant précis ;
- limitation de certains rails ;
- gel réglementaire ;
- restriction temporaire.

Le motif détaillé peut être masqué au client lorsqu’une obligation réglementaire l’impose, tout en restant disponible dans l’audit autorisé.

## 19. Limites financières

Avant débit, le module vérifie les limites applicables :

- par transaction ;
- journalières ;
- hebdomadaires ;
- mensuelles ;
- par canal ;
- par produit ;
- selon niveau KYC ;
- selon pays ;
- selon partenaire.

Les compteurs de limites doivent être déterministes et résistants à la concurrence.

## 20. Multi-devise

Chaque ledger account possède une devise unique.

Un transfert entre devises exige :

- taux de change explicite ;
- horodatage du taux ;
- fournisseur ou source ;
- spread/frais ;
- comptes de change dédiés ;
- comptabilisation équilibrée par devise selon le modèle comptable retenu.

La conversion implicite est interdite.

## 21. Règlement partenaires

Les intégrations externes disposent de comptes de clearing ou settlement dédiés.

Le système distingue :

- fonds Mansa ;
- dette envers utilisateurs ;
- créance sur partenaire ;
- dette envers partenaire ;
- revenus de frais ;
- commissions à payer.

Les comptes de règlement permettent de rapprocher les flux réels transmis par banques, Mobile Money, processeurs cartes ou autres partenaires.

## 22. Rapprochement

Le rapprochement compare :

- ledger interne ;
- transactions du module d’intégration ;
- fichiers ou APIs partenaires ;
- règlements bancaires réels lorsque disponibles.

Statuts :

- `MATCHED` ;
- `MISSING_INTERNAL` ;
- `MISSING_EXTERNAL` ;
- `AMOUNT_MISMATCH` ;
- `STATUS_MISMATCH` ;
- `DUPLICATE` ;
- `UNDER_REVIEW` ;
- `RESOLVED`.

Les écarts ne sont jamais corrigés automatiquement par modification d’historique.

## 23. APIs principales

Exemples :

- `GET /v1/wallets` ;
- `GET /v1/wallets/{id}` ;
- `GET /v1/wallets/{id}/balance` ;
- `GET /v1/wallets/{id}/transactions` ;
- `POST /v1/transfers/internal` ;
- `POST /v1/holds` ;
- `POST /v1/holds/{id}/capture` ;
- `POST /v1/holds/{id}/release` ;
- `POST /v1/refunds` ;
- `GET /v1/transactions/{id}` ;
- `POST /v1/admin/adjustments` ;
- `POST /v1/admin/adjustments/{id}/approve`.

Les endpoints d’administration financière sont séparés des APIs clientes et protégés par permissions renforcées.

## 24. Événements métier

Événements minimaux :

- `wallet.created` ;
- `wallet.activated` ;
- `wallet.restricted` ;
- `wallet.closed` ;
- `financial_transaction.created` ;
- `financial_transaction.posted` ;
- `financial_transaction.failed` ;
- `hold.created` ;
- `hold.captured` ;
- `hold.released` ;
- `hold.expired` ;
- `transfer.completed` ;
- `refund.completed` ;
- `adjustment.posted` ;
- `reconciliation.mismatch_detected`.

Les consommateurs doivent être idempotents.

## 25. Audit

Toute action sensible enregistre :

- acteur ;
- rôle ;
- organisation ;
- transaction ;
- wallet ;
- action ;
- montant et devise ;
- état précédent et suivant lorsque pertinent ;
- raison ;
- horodatage serveur ;
- corrélation ;
- approbateur éventuel.

Les journaux d’audit ne contiennent jamais de secret d’authentification.

## 26. Observabilité

Métriques minimales :

- volume et valeur des transactions ;
- transactions par statut ;
- latence de posting ;
- taux d’idempotence rejouée ;
- holds actifs et expirés ;
- erreurs d’équilibrage ;
- refus pour solde insuffisant ;
- écarts de rapprochement ;
- ajustements manuels ;
- profondeur des files financières ;
- âge des transactions en attente.

Alerte immédiate si :

- une écriture déséquilibrée est détectée ;
- un solde dérivé devient incohérent ;
- un worker critique accumule du retard ;
- un partenaire présente un écart de règlement anormal.

## 27. Sécurité

- Chiffrement des communications.
- Contrôle d’accès strict par rôle et contexte.
- Aucun accès direct aux tables financières depuis les applications clientes.
- Journalisation des lectures administratives sensibles.
- Séparation des responsabilités pour ajustements et paramétrages critiques.
- Secrets partenaires stockés hors dépôt.
- Protection contre rejeu, double soumission et modification de requête.

## 28. Performance et disponibilité

Objectifs :

- lectures de solde à faible latence ;
- posting transactionnel fiable ;
- montée en charge horizontale des APIs stateless ;
- workers redémarrables sans double effet ;
- reprise après panne sans perte d’écriture comptabilisée.

Les caches ne sont jamais la source de vérité du solde. Ils peuvent accélérer les lectures mais doivent être invalidables et reconstruisibles.

## 29. Sauvegarde et reprise

Le plan de reprise doit couvrir :

- sauvegardes PostgreSQL chiffrées ;
- restauration testée périodiquement ;
- point-in-time recovery lorsque disponible ;
- RPO/RTO documentés ;
- procédure de vérification comptable après restauration ;
- interdiction de reprendre des traitements asynchrones sans contrôle d’idempotence.

## 30. Tests obligatoires

### Tests unitaires

- règles de soldes ;
- frais ;
- holds ;
- remboursements ;
- limites ;
- construction des postings.

### Tests d’intégration

- transaction PostgreSQL ;
- concurrence sur même wallet ;
- idempotence ;
- rollback complet après erreur ;
- publication d’événements cohérente.

### Tests de propriété

Vérifier notamment que pour toute transaction générée :

- somme débits = somme crédits ;
- aucune devise n’est mélangée incorrectement ;
- un remboursement ne dépasse pas le remboursable ;
- une capture ne dépasse pas le hold restant.

### Tests de charge

Couvrir lectures de soldes, transferts concurrents, paiements commerçants et traitements de masse.

## 31. Critères d’acceptation

Le module est acceptable lorsque :

1. aucune opération ne peut produire une écriture déséquilibrée ;
2. un même ordre rejoué avec la même clé d’idempotence ne produit jamais un second débit ;
3. les débits concurrents respectent strictement le solde disponible ;
4. tout changement de solde est explicable par des postings ;
5. les remboursements et reversals conservent l’historique ;
6. les holds sont capturés, libérés et expirés correctement ;
7. le rapprochement identifie les écarts sans altérer silencieusement les comptes ;
8. les ajustements manuels sont contrôlés et auditables ;
9. les tests comptables, concurrence et idempotence passent en CI ;
10. le même contrat est utilisable par les modules paiements, cartes, Mobile Money, TPE, commerçants et État.

## 32. Dépendances

- Authentification et contrôle d’accès ;
- KYC/KYB ;
- moteur de risque ;
- moteur de tarification ;
- configuration pays/devise ;
- audit ;
- notifications ;
- intégrations bancaires, cartes et Mobile Money.

## 33. Hors périmètre initial

- comptabilité générale complète de l’entreprise Mansa ;
- moteur fiscal universel multi-juridiction ;
- trésorerie prédictive ;
- crédit et intérêts complexes ;
- change spéculatif ;
- actifs crypto.

Ces domaines pourront être ajoutés ultérieurement sans compromettre le ledger principal.
