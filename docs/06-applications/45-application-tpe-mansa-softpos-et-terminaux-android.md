# 45 — Application TPE Mansa (SoftPOS & Terminaux Android)

## 1. Objet du document

Ce document définit l'architecture officielle de **l'application TPE Mansa**.

Elle permet d'accepter des paiements professionnels sur :

- terminaux Android certifiés ;
- SoftPOS sur smartphone compatible ;
- terminaux partenaires ;
- futurs terminaux Mansa.

Elle couvre :

- paiements carte ;
- paiements Wallet Mansa ;
- QR ;
- NFC ;
- Mobile Money ;
- paiements mixtes ;
- remboursements ;
- annulations ;
- préautorisations ;
- capture ;
- pourboires ;
- reçus ;
- mode hors ligne contrôlé ;
- sécurité PCI ;
- gestion des terminaux ;
- supervision ;
- maintenance ;
- mises à jour ;
- administration ;
- analytics.

L'objectif est de proposer un terminal professionnel comparable aux meilleures solutions du marché tout en étant totalement intégré à l'écosystème Mansa.

---

# 2. Principes fondamentaux

## 2.1 Le TPE est une application indépendante

Le TPE ne doit pas dépendre de l'application Commerce.

Il peut fonctionner :

- seul ;
- avec Commerce ;
- avec Agent ;
- avec l'API publique ;
- avec un ERP partenaire.

---

## 2.2 Toute validation financière vient du backend

Le terminal ne décide jamais seul :

- qu'un paiement est accepté ;
- qu'un remboursement est validé ;
- qu'un règlement est effectué ;
- qu'une commission est calculée.

Il affiche uniquement le résultat officiel.

---

## 2.3 Aucun montant critique en dur

Tous les paramètres doivent être administrables :

- plafonds ;
- délais ;
- frais ;
- commissions ;
- limites ;
- timeout ;
- règles offline ;
- moyens de paiement.

---

## 2.4 Le terminal appartient toujours à une organisation

Chaque terminal est lié à :

- un commerçant ;
- un établissement ;
- éventuellement une caisse ;
- éventuellement un employé.

---

# 3. Plateformes supportées

L'application doit pouvoir fonctionner sur :

- Android certifié ;
- PAX ;
- Sunmi ;
- Newland ;
- Castles ;
- SoftPOS Android ;
- futurs terminaux partenaires.

---

# 4. Architecture

Structure recommandée :

```text
src/
├── auth/
├── activation/
├── dashboard/
├── payments/
├── refunds/
├── preauthorizations/
├── tips/
├── receipts/
├── printer/
├── qr/
├── nfc/
├── cards/
├── wallet/
├── mobile-money/
├── offline/
├── terminal/
├── diagnostics/
├── updates/
├── settings/
├── security/
├── sync/
├── support/
└── analytics/
```

---

# 5. Activation du terminal

Le terminal doit être activé par :

- QR d'activation ;
- code d'activation ;
- administrateur ;
- portail commerce ;
- administration Mansa.

Chaque activation crée :

- identifiant terminal ;
- certificat ;
- association établissement ;
- journal d'activation.

---

# 6. Tableau de bord

Afficher :

- statut terminal ;
- dernière synchronisation ;
- batterie ;
- connexion ;
- ventes du jour ;
- remboursements ;
- montant encaissé ;
- état imprimante ;
- mises à jour ;
- alertes.

---

# 7. Moyens de paiement acceptés

Le terminal peut accepter :

- Carte Visa ;
- Mastercard ;
- cartes locales compatibles ;
- Wallet Mansa ;
- QR Mansa ;
- NFC Wallet ;
- Mobile Money ;
- paiement mixte ;
- paiement par lien (si initié ailleurs).

---

# 8. Paiement par carte

Le parcours comprend :

1. saisie du montant ;
2. présentation de la carte ;
3. lecture NFC, puce ou bande (si autorisée) ;
4. vérifications backend ;
5. authentification si nécessaire ;
6. autorisation ;
7. impression ou reçu numérique.

---

# 9. Paiement Wallet Mansa

Le client peut payer via :

- QR dynamique ;
- QR statique ;
- NFC ;
- identifiant Mansa si autorisé.

---

# 10. Paiement Mobile Money

Selon les intégrations disponibles :

- sélection opérateur ;
- validation backend ;
- confirmation ;
- reçu.

---

# 11. Paiement mixte

Une transaction peut être répartie entre :

- carte ;
- Wallet Mansa ;
- Mobile Money ;
- espèces (si Commerce associé).

Chaque partie est enregistrée séparément.

---

# 12. Pourboires

Le terminal peut proposer :

- aucun pourboire ;
- pourcentage ;
- montant libre ;
- suggestions rapides.

Cette fonction est activable par commerce.

---

# 13. Préautorisation

Support des opérations :

- création ;
- extension ;
- réduction ;
- capture totale ;
- capture partielle ;
- annulation.

---

# 14. Remboursements

Types :

- total ;
- partiel ;
- technique ;
- commercial.

Les permissions dépendent des rôles.

---

# 15. Annulation

Une opération peut être annulée uniquement selon les règles backend.

Toutes les annulations sont journalisées.

---

# 16. Reçus

Formats :

- impression ;
- numérique ;
- SMS ;
- e-mail ;
- QR.

Le reçu contient :

- référence ;
- terminal ;
- commerçant ;
- établissement ;
- montant ;
- moyen de paiement ;
- date ;
- statut.

---

# 17. Impression

Support :

- imprimante intégrée ;
- Bluetooth ;
- USB ;
- réseau (si compatible).

---

# 18. Gestion du terminal

Le système suit :

- numéro de série ;
- modèle ;
- fabricant ;
- version ;
- certificat ;
- propriétaire ;
- établissement ;
- état.

---

# 19. Diagnostic

Le terminal peut tester :

- réseau ;
- NFC ;
- lecteur carte ;
- imprimante ;
- batterie ;
- stockage ;
- sécurité.

---

# 20. Mises à jour

Support :

- OTA ;
- téléchargement sécurisé ;
- validation de signature ;
- retour arrière contrôlé.

---

# 21. Mode réseau faible

Le terminal doit gérer :

- reprise automatique ;
- synchronisation ;
- file d'attente ;
- états explicites.

---

# 22. Mode hors ligne

Uniquement selon les règles définies par l'administration.

Les plafonds offline doivent être configurables.

Chaque transaction offline doit être resynchronisée.

---

# 23. Sécurité

Le terminal doit intégrer :

- chiffrement ;
- certificats ;
- PIN sécurisé ;
- biométrie si disponible ;
- Secure Element selon matériel ;
- détection root ;
- détection jailbreak (si applicable) ;
- audit.

---

# 24. Permissions

Exemples :

```text
terminal.payment.create
terminal.refund.request
terminal.refund.approve
terminal.receipt.print
terminal.receipt.send
terminal.settings.manage
terminal.diagnostics.run
terminal.update.install
terminal.support.open
```

---

# 25. Administration

L'administration peut gérer :

- activation ;
- désactivation ;
- affectation ;
- changement d'établissement ;
- mises à jour ;
- certificats ;
- plafonds ;
- moyens de paiement ;
- règles offline ;
- journaux.

---

# 26. Analytics

Événements :

```text
terminal_activated
terminal_payment_started
terminal_payment_completed
terminal_payment_failed
terminal_refund_completed
terminal_offline_transaction
terminal_sync_completed
terminal_update_installed
terminal_diagnostic_completed
terminal_security_alert
```

---

# 27. API

Exemples :

```http
POST /terminal/activate
GET  /terminal/status
POST /terminal/payments
POST /terminal/refunds
POST /terminal/preauthorizations
POST /terminal/capture
GET  /terminal/receipts
POST /terminal/sync
GET  /terminal/updates
POST /terminal/diagnostics
```

---

# 28. Modèles

- Terminal
- TerminalActivation
- TerminalCertificate
- TerminalPayment
- TerminalRefund
- TerminalReceipt
- TerminalPrinter
- TerminalUpdate
- TerminalDiagnostic
- TerminalSecurityEvent
- TerminalOfflineTransaction

---

# 29. Tests

- activation ;
- paiement carte ;
- paiement QR ;
- paiement Wallet ;
- paiement Mobile Money ;
- paiement mixte ;
- remboursement ;
- préautorisation ;
- capture ;
- impression ;
- hors ligne ;
- synchronisation ;
- diagnostics ;
- mises à jour ;
- sécurité.

---

# 30. Règles métier

1. Le terminal appartient à un commerce.
2. Toutes les validations viennent du backend.
3. Les paramètres sont administrables.
4. Les transactions possèdent une référence unique.
5. Les remboursements sont tracés.
6. Les opérations offline sont limitées.
7. Les mises à jour sont signées.
8. Les certificats sont obligatoires.
9. Les journaux sont immuables.
10. Les permissions sont appliquées à chaque action.

---

# 31. Critères d'acceptation

L'application TPE est validée lorsque :

- le terminal peut être activé ;
- les paiements fonctionnent ;
- les remboursements sont sécurisés ;
- les reçus sont générés ;
- le mode hors ligne respecte les règles ;
- les mises à jour sont sécurisées ;
- les diagnostics fonctionnent ;
- les terminaux sont administrables ;
- les tests critiques sont validés.
