# 10 — Architecture du Ledger financier de Mansa

## 1. Objet du document

Ce document définit l’architecture officielle du **ledger financier** de Mansa.

Le ledger constitue la source de vérité pour :

- les soldes ;
- les débits ;
- les crédits ;
- les transferts ;
- les paiements ;
- les remboursements ;
- les frais ;
- les commissions ;
- les taxes ;
- les conversions ;
- les règlements ;
- les écarts ;
- les comptes techniques ;
- les opérations partenaires.

L’objectif est de garantir que chaque mouvement financier soit :

- équilibré ;
- traçable ;
- immuable ;
- auditable ;
- idempotent ;
- réconciliable ;
- cohérent dans toutes les applications.

---

# 2. Principes fondamentaux

## 2.1 Le ledger est la source de vérité financière

Les soldes visibles dans les applications doivent être dérivés du ledger ou d’une vue matérialisée synchronisée avec lui.

Aucun simple champ de type :

```text
balance = 100000
```

ne doit être considéré comme source définitive sans écritures correspondantes.

## 2.2 Partie double

Chaque transaction financière doit produire au minimum :

- une écriture débit ;
- une écriture crédit.

La somme des débits doit toujours être égale à la somme des crédits pour une même transaction comptable et une même devise.

## 2.3 Immutabilité

Une écriture confirmée ne doit jamais être modifiée ni supprimée.

Toute correction doit produire :

- une contre-écriture ;
- une nouvelle transaction ;
- une référence vers l’opération corrigée ;
- un motif ;
- un audit.

## 2.4 Idempotence

Une même commande financière ne doit jamais produire plusieurs écritures si elle est rejouée.

Chaque opération critique doit utiliser :

- une clé d’idempotence ;
- une empreinte de requête ;
- un statut ;
- une réponse conservée ;
- une durée de conservation adaptée.

## 2.5 Cohérence transactionnelle

La création des écritures d’une transaction doit être atomique.

Soit toutes les écritures sont enregistrées, soit aucune ne l’est.

---

# 3. Types de comptes ledger

## 3.1 Comptes utilisateurs

Exemples :

- wallet principal ;
- compte secondaire ;
- compte multi-devises ;
- coffre ;
- compte enfant ;
- compte professionnel ;
- compte investissement.

## 3.2 Comptes commerçants

Exemples :

- solde disponible ;
- règlement en attente ;
- réserve ;
- remboursements ;
- commissions dues ;
- taxes collectées.

## 3.3 Comptes Mansa

Exemples :

- revenus ;
- commissions ;
- frais ;
- promotions ;
- cashback ;
- réserve ;
- suspense ;
- différences de change ;
- pertes ;
- ajustements.

## 3.4 Comptes partenaires

Exemples :

- banque ;
- Mobile Money ;
- réseau carte ;
- acquéreur ;
- émetteur ;
- service public ;
- opérateur ;
- partenaire d’investissement.

## 3.5 Comptes techniques

Exemples :

- clearing ;
- règlement ;
- suspense ;
- chargeback ;
- arrondi ;
- change ;
- frais ;
- taxes ;
- compensation ;
- rapprochement.

---

# 4. Structure d’un compte ledger

Chaque compte doit contenir :

- identifiant unique ;
- propriétaire ;
- type ;
- sous-type ;
- devise ;
- pays ;
- environnement ;
- statut ;
- sens normal ;
- date de création ;
- date de fermeture ;
- restrictions ;
- métadonnées ;
- version.

Exemple conceptuel :

```json
{
  "id": "led_acc_123",
  "ownerType": "USER",
  "ownerId": "usr_456",
  "type": "WALLET",
  "currency": "XOF",
  "country": "ML",
  "status": "ACTIVE"
}
```

---

# 5. Structure d’une transaction ledger

Chaque transaction doit contenir :

- identifiant ;
- type ;
- référence métier ;
- clé d’idempotence ;
- statut ;
- devise ;
- date de création ;
- date d’effet ;
- date de comptabilisation ;
- créateur ;
- canal ;
- pays ;
- environnement ;
- partenaire ;
- corrélation ;
- motif ;
- métadonnées ;
- écritures ;
- transaction parent éventuelle.

---

# 6. Structure d’une écriture

Chaque écriture contient :

- identifiant ;
- transaction ;
- compte ;
- sens ;
- montant ;
- devise ;
- date ;
- statut ;
- libellé ;
- référence ;
- position dans la transaction ;
- solde avant éventuel ;
- solde après éventuel ;
- métadonnées.

Exemple :

```json
{
  "accountId": "led_acc_user",
  "direction": "DEBIT",
  "amount": 10000,
  "currency": "XOF"
}
```

---

# 7. Statuts

## 7.1 Transaction ledger

- brouillon ;
- préparée ;
- en attente ;
- réservée ;
- confirmée ;
- échouée ;
- annulée ;
- contre-passée ;
- expirée.

## 7.2 Écriture

- pending ;
- posted ;
- reversed ;
- failed.

Une écriture `posted` ne peut pas être modifiée.

---

# 8. Soldes

Le système doit distinguer :

- solde comptable ;
- solde disponible ;
- solde réservé ;
- solde bloqué ;
- solde en attente ;
- solde estimé.

## 8.1 Solde comptable

Somme officielle des écritures comptabilisées.

## 8.2 Solde disponible

Montant réellement utilisable après prise en compte :

- réservations ;
- blocages ;
- opérations en attente ;
- limites ;
- restrictions.

## 8.3 Solde réservé

Montant mis de côté pour :

- paiement carte ;
- préautorisation ;
- transfert en cours ;
- remboursement ;
- litige ;
- garantie.

---

# 9. Réservations

Une réservation doit contenir :

- identifiant ;
- compte ;
- montant ;
- devise ;
- opération liée ;
- date ;
- expiration ;
- statut ;
- partenaire ;
- motif.

Statuts :

- active ;
- capturée ;
- libérée ;
- expirée ;
- annulée.

---

# 10. Paiement entre utilisateurs

Exemple :

Utilisateur A envoie `10 000 XOF` à l’utilisateur B.

Écritures :

```text
Débit  : compte utilisateur A      10 000 XOF
Crédit : compte utilisateur B      10 000 XOF
```

Avec frais de `100 XOF` :

```text
Débit  : compte utilisateur A      10 100 XOF
Crédit : compte utilisateur B      10 000 XOF
Crédit : compte revenus Mansa         100 XOF
```

La transaction doit rester équilibrée.

---

# 11. Paiement marchand

Exemple :

Client paie `20 000 XOF`.

Commission Mansa : `200 XOF`.

Écritures :

```text
Débit  : compte client             20 000 XOF
Crédit : compte règlement marchand 19 800 XOF
Crédit : compte commission Mansa      200 XOF
```

---

# 12. Paiement par carte

Le flux peut inclure :

- réservation ;
- autorisation ;
- capture ;
- règlement ;
- frais réseau ;
- commission acquéreur ;
- commission Mansa ;
- règlement commerçant.

Le ledger doit conserver chaque étape sans simplification abusive.

---

# 13. Préautorisation et capture

## 13.1 Préautorisation

Le montant est réservé mais pas encore définitivement comptabilisé.

## 13.2 Capture

La réservation devient une écriture comptabilisée.

## 13.3 Capture partielle

Une partie seulement du montant est comptabilisée.

Le reste est libéré.

## 13.4 Capture multiple

Possible uniquement si le partenaire et la règle métier l’autorisent.

---

# 14. Annulation

Une annulation avant comptabilisation peut :

- libérer une réservation ;
- annuler une transaction en attente.

Une annulation après comptabilisation doit produire une contre-écriture.

---

# 15. Remboursement

Un remboursement doit créer une nouvelle transaction liée à l’opération d’origine.

Exemple :

```text
Débit  : compte commerçant
Crédit : compte client
```

Les frais peuvent être :

- remboursés ;
- partiellement remboursés ;
- non remboursés ;
- reclassés.

La politique doit être explicite.

---

# 16. Remboursement partiel

Le système doit contrôler :

- montant déjà remboursé ;
- montant restant remboursable ;
- frais ;
- devise ;
- délai ;
- permissions ;
- nombre de remboursements.

---

# 17. Chargeback et litiges

Un chargeback peut nécessiter :

- réserve ;
- blocage ;
- transfert vers un compte de litige ;
- décision ;
- retour client ;
- débit commerçant ;
- frais ;
- preuve ;
- date limite.

---

# 18. Frais

Chaque frais doit être identifié séparément.

Types :

- fixe ;
- variable ;
- partenaire ;
- réseau ;
- change ;
- service public ;
- retrait ;
- carte ;
- remboursement ;
- urgence ;
- abonnement.

---

# 19. Commissions

Les commissions peuvent être réparties entre :

- Mansa ;
- banque ;
- partenaire ;
- agent ;
- distributeur ;
- État ;
- commerçant ;
- affilié.

Chaque bénéficiaire doit avoir un compte ledger dédié.

---

# 20. Taxes

Les taxes doivent être enregistrées séparément.

Exemple :

```text
Débit  : client
Crédit : commerçant hors taxes
Crédit : compte taxe
Crédit : commission
```

La taxe ne doit pas être confondue avec le revenu Mansa.

---

# 21. Multi-devises

Chaque écriture reste dans une seule devise.

Une conversion produit plusieurs groupes d’écritures.

Exemple :

```text
Débit  : compte EUR client
Crédit : compte de change EUR

Débit  : compte de change XOF
Crédit : compte XOF client
```

Avec conservation du :

- taux ;
- spread ;
- frais ;
- source ;
- date ;
- paire.

---

# 22. Cash-in et cash-out

## 22.1 Cash-in

Exemple :

```text
Débit  : compte partenaire
Crédit : wallet utilisateur
```

## 22.2 Cash-out

Exemple :

```text
Débit  : wallet utilisateur
Crédit : compte partenaire
```

Les écarts entre partenaire et ledger doivent être rapprochés.

---

# 23. Mobile Money

Le ledger doit distinguer :

- initiation ;
- statut partenaire ;
- confirmation ;
- règlement ;
- échec ;
- annulation ;
- retry ;
- doublon ;
- frais.

Une réponse partenaire incertaine ne doit pas produire une réussite définitive.

---

# 24. Services publics

Pour une amende ou une taxe :

```text
Débit  : compte utilisateur
Crédit : compte organisme public
Crédit : compte frais Mansa éventuel
```

Le reçu doit permettre le rapprochement avec l’organisme.

---

# 25. Investissements

Le ledger peut gérer :

- souscription ;
- frais ;
- détention ;
- rendement ;
- retrait ;
- remboursement ;
- distribution ;
- taxes ;
- portefeuille de conservation.

Les avoirs d’investissement ne doivent pas être confondus avec le cash disponible.

---

# 26. Coffres et épargne

Le transfert vers un coffre peut être :

```text
Débit  : wallet principal
Crédit : coffre
```

Le retrait suit le flux inverse.

Un coffre verrouillé reste un compte ledger séparé avec restrictions.

---

# 27. Cashback et fidélité

Le cashback financier doit produire une écriture.

Exemple :

```text
Débit  : compte promotion Mansa
Crédit : compte utilisateur
```

Les points non monétaires doivent rester dans un système distinct, sauf conversion explicite en argent.

---

# 28. Corrections

Une correction doit contenir :

- transaction d’origine ;
- motif ;
- auteur ;
- approbateur ;
- montant ;
- devise ;
- contre-écritures ;
- nouvelles écritures ;
- audit.

Aucune correction manuelle directe du solde n’est autorisée.

---

# 29. Ajustements

Un ajustement exceptionnel doit être limité à des permissions spécifiques.

Exigences :

- motif obligatoire ;
- document justificatif ;
- double validation ;
- plafond ;
- journalisation ;
- alerte ;
- rapport.

---

# 30. Comptes de suspense

Utilisés lorsque :

- le partenaire ne confirme pas ;
- le bénéficiaire est inconnu ;
- une référence manque ;
- un rapprochement échoue ;
- une conversion est incomplète ;
- un remboursement reste en attente.

Les comptes de suspense doivent être surveillés et vidés selon une procédure.

---

# 31. Rapprochement

Le rapprochement compare :

- ledger Mansa ;
- banque ;
- Mobile Money ;
- carte ;
- TPE ;
- organisme public ;
- partenaire d’investissement.

Chaque écart doit avoir :

- identifiant ;
- catégorie ;
- montant ;
- devise ;
- date ;
- source ;
- statut ;
- responsable ;
- résolution ;
- audit.

---

# 32. Clôture

Des clôtures peuvent être nécessaires :

- journalières ;
- hebdomadaires ;
- mensuelles ;
- par partenaire ;
- par devise ;
- par pays ;
- par établissement.

Une période clôturée ne doit pas être modifiable sans procédure spéciale.

---

# 33. Recalcul des soldes

Le système doit pouvoir reconstruire les soldes à partir des écritures.

Un écart entre :

- vue de solde ;
- cache ;
- agrégat ;
- ledger ;

doit déclencher une alerte.

---

# 34. Performance

Le ledger doit supporter :

- forte concurrence ;
- verrouillage maîtrisé ;
- transactions atomiques ;
- indexation ;
- partitionnement ;
- lecture optimisée ;
- agrégats ;
- files ;
- reprise.

Les optimisations ne doivent jamais compromettre la cohérence.

---

# 35. Concurrence

Le système doit empêcher :

- double dépense ;
- solde négatif non autorisé ;
- capture multiple ;
- double remboursement ;
- double règlement.

Techniques possibles :

- verrouillage pessimiste ;
- verrouillage optimiste ;
- version ;
- contrainte unique ;
- transaction SQL ;
- verrou distribué ;
- sérialisation ciblée.

---

# 36. Idempotence

Chaque commande financière doit enregistrer :

- clé ;
- utilisateur ;
- endpoint ;
- empreinte ;
- résultat ;
- statut ;
- expiration ;
- date.

Une même clé avec un contenu différent doit être rejetée.

---

# 37. Audit

Chaque transaction ledger doit être liée à :

- utilisateur ;
- application ;
- appareil ;
- administrateur éventuel ;
- IP si disponible ;
- corrélation ;
- partenaire ;
- ticket ;
- motif ;
- version ;
- environnement.

---

# 38. Sécurité

Le ledger doit être inaccessible directement aux applications clientes.

Seuls les services autorisés peuvent :

- créer une transaction ;
- consulter des écritures ;
- effectuer une correction ;
- exporter ;
- rapprocher ;
- clôturer.

---

# 39. Permissions

Exemples :

```text
ledger.account.read
ledger.transaction.read
ledger.transaction.create
ledger.adjustment.create
ledger.adjustment.approve
ledger.reconciliation.read
ledger.reconciliation.resolve
ledger.period.close
ledger.export
```

---

# 40. API

Exemples internes :

```http
GET    /ledger/accounts
GET    /ledger/accounts/{id}
GET    /ledger/accounts/{id}/balance
GET    /ledger/accounts/{id}/entries

POST   /ledger/transactions
GET    /ledger/transactions/{id}

POST   /ledger/reservations
POST   /ledger/reservations/{id}/capture
POST   /ledger/reservations/{id}/release

POST   /ledger/adjustments
POST   /ledger/adjustments/{id}/approve

GET    /ledger/reconciliations
POST   /ledger/reconciliations/{id}/resolve
```

Ces API ne doivent pas toutes être publiques.

---

# 41. Modèles

- LedgerAccount
- LedgerTransaction
- LedgerEntry
- LedgerBalance
- LedgerReservation
- LedgerAdjustment
- LedgerReversal
- LedgerPeriod
- LedgerReconciliation
- LedgerDiscrepancy
- LedgerAccountType
- LedgerTransactionType
- LedgerAudit
- LedgerSnapshot
- LedgerIdempotencyRecord

---

# 42. Règles métier

1. Toute transaction est équilibrée.
2. Une écriture confirmée est immuable.
3. Toute correction utilise une contre-écriture.
4. Aucun solde n’est modifié directement.
5. Chaque montant possède une devise.
6. Les débits et crédits sont atomiques.
7. Toute opération critique est idempotente.
8. Une réservation expirée est libérée.
9. Un remboursement ne dépasse pas le montant disponible.
10. Une transaction échouée ne produit pas d’écriture confirmée.
11. Les comptes techniques sont séparés.
12. Les comptes de suspense sont surveillés.
13. Les différences de change sont comptabilisées.
14. Les frais et taxes sont séparés.
15. Les permissions sont contrôlées côté backend.
16. Les ajustements nécessitent une justification.
17. Les périodes clôturées sont protégées.
18. Les soldes peuvent être reconstruits.
19. Les rapprochements sont historisés.
20. Les opérations partenaires incertaines restent en attente.

---

# 43. Analytics

Événements possibles :

```text
ledger_transaction_created
ledger_transaction_posted
ledger_transaction_failed
ledger_entry_posted
ledger_reservation_created
ledger_reservation_captured
ledger_reservation_released
ledger_adjustment_requested
ledger_adjustment_approved
ledger_reconciliation_started
ledger_discrepancy_detected
ledger_discrepancy_resolved
ledger_period_closed
ledger_balance_mismatch_detected
```

---

# 44. Tests

- tests d’équilibre ;
- tests d’atomicité ;
- tests d’idempotence ;
- tests de concurrence ;
- tests de double dépense ;
- tests de réservation ;
- tests de capture ;
- tests de remboursement ;
- tests multi-devises ;
- tests d’arrondi ;
- tests de rapprochement ;
- tests de contre-écriture ;
- tests de clôture ;
- tests de performance ;
- tests de reprise ;
- tests d’autorisation ;
- tests de reconstruction de solde.

---

# 45. Critères d’acceptation

Le ledger est validé lorsque :

- chaque transaction est équilibrée ;
- les écritures sont immuables ;
- les soldes sont reconstructibles ;
- les corrections utilisent des contre-écritures ;
- les réservations fonctionnent ;
- les remboursements sont contrôlés ;
- les frais, taxes et commissions sont séparés ;
- le multi-devises est pris en charge ;
- l’idempotence empêche les doublons ;
- la concurrence empêche la double dépense ;
- les rapprochements détectent les écarts ;
- les comptes de suspense sont gérés ;
- les périodes peuvent être clôturées ;
- toutes les opérations sont auditées ;
- les permissions sont appliquées ;
- les tests couvrent les scénarios critiques.
