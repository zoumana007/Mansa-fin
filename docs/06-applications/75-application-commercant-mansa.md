# 75 — Application Commerçant Mansa : gestion du commerce, encaissements, catalogue, ventes, remboursements, employés, TPE, QR, statistiques, fidélité, support et administration centralisée

## 1. Objet du document

Ce document définit le cahier des charges complet de l’**Application Commerçant Mansa**.

Cette application est destinée aux commerçants, indépendants, boutiques, restaurants, hôtels, pharmacies, supermarchés, stations-service, artisans, PME, grandes entreprises, établissements scolaires, structures de santé et administrations autorisées.

Elle doit permettre notamment :

- l’inscription et le KYB ;
- la création et la gestion du profil marchand ;
- la gestion de plusieurs magasins, points de vente et caisses ;
- la gestion des employés et des permissions ;
- l’encaissement par QR, NFC, carte, lien, facture, Tap to Pay et TPE ;
- le suivi des ventes en temps réel ;
- les annulations et remboursements ;
- la gestion des reçus, factures et avoirs ;
- la gestion d’un catalogue et d’un stock léger ;
- la gestion des commandes ;
- la gestion des clients ;
- la fidélité, les promotions et les coupons ;
- les règlements vers le compte du commerçant ;
- les rapports et statistiques ;
- la gestion des TPE ;
- l’accès au support et à Jini ;
- la sécurité, l’audit et l’administration centralisée.

L’application doit être moderne, rapide, simple, sécurisée, configurable, multi-pays, multi-langues, multi-devises, compatible Android et iOS, utilisable sur réseau faible et adaptée aux petites comme aux grandes structures.

---

## 2. Principes fondamentaux

1. Chaque paiement possède une référence unique.
2. Toute opération financière passe par le ledger.
3. Les frais sont affichés avant confirmation.
4. Les employés n’accèdent qu’aux fonctions autorisées.
5. Les statistiques proviennent des écritures validées.
6. Les annulations et remboursements sont tracés.
7. Les fonctions sont activables depuis l’administration.
8. Les données de plusieurs magasins restent séparées.
9. Les actions sensibles nécessitent une confirmation.
10. Les audits sont immuables.

---

## 3. Types de commerçants

Le système doit gérer :

- commerce individuel ;
- auto-entrepreneur ;
- PME ;
- grande entreprise ;
- franchise ;
- restaurant ;
- café ;
- hôtel ;
- pharmacie ;
- clinique ;
- station-service ;
- école ;
- administration ;
- marketplace ;
- e-commerce ;
- prestataire de services ;
- association autorisée.

---

## 4. Plateformes

L’application doit être disponible sur :

- Android ;
- iOS.

Elle doit pouvoir être complétée par un portail web commerçant sans dépendre de celui-ci pour les opérations quotidiennes.

---

## 5. Architecture logique

```text
merchant-mobile/
├── onboarding/
├── authentication/
├── kyb/
├── dashboard/
├── payments/
├── qr/
├── tap-to-pay/
├── terminals/
├── transactions/
├── refunds/
├── invoices/
├── receipts/
├── catalog/
├── inventory/
├── orders/
├── customers/
├── loyalty/
├── promotions/
├── stores/
├── registers/
├── employees/
├── settlements/
├── reports/
├── notifications/
├── support/
├── jini/
├── settings/
├── security/
└── shared/
```

---

## 6. Navigation principale

Navigation recommandée :

1. Accueil.
2. Encaisser.
3. Transactions.
4. Catalogue.
5. Plus.

L’ordre et les modules doivent être configurables par l’administration.

---

## 7. Onboarding commerçant

L’onboarding doit présenter :

- les moyens d’encaissement ;
- le QR ;
- le TPE ;
- les règlements ;
- les employés ;
- les rapports ;
- la sécurité ;
- le support.

Les textes, images, langues et écrans doivent être administrables.

---

## 8. Inscription

Le parcours doit pouvoir demander :

- pays ;
- type d’activité ;
- nom commercial ;
- raison sociale ;
- téléphone ;
- e-mail ;
- adresse ;
- représentant ;
- consentements ;
- mot de passe ou PIN ;
- appareil.

---

## 9. KYB

Le KYB peut demander :

- registre de commerce ;
- identifiant fiscal ;
- statuts ;
- autorisation d’activité ;
- représentant légal ;
- bénéficiaires effectifs ;
- compte de règlement ;
- justificatif d’adresse ;
- secteur ;
- volume attendu ;
- source des fonds ;
- documents pays.

---

## 10. Statuts KYB

- NOT_STARTED ;
- IN_PROGRESS ;
- SUBMITTED ;
- AUTOMATIC_REVIEW ;
- MANUAL_REVIEW ;
- ADDITIONAL_INFORMATION_REQUIRED ;
- APPROVED ;
- REJECTED ;
- EXPIRED ;
- SUSPENDED.

---

## 11. Profil commerçant

Le profil doit contenir :

- identifiant marchand ;
- nom commercial ;
- raison sociale ;
- logo ;
- catégorie ;
- description ;
- adresses ;
- horaires ;
- contacts ;
- statut KYB ;
- compte de règlement ;
- devise ;
- pays ;
- magasins ;
- documents ;
- préférences.

---

## 12. Tableau de bord

L’accueil peut afficher :

- chiffre d’affaires du jour ;
- nombre de ventes ;
- panier moyen ;
- paiements réussis ;
- paiements en attente ;
- remboursements ;
- règlements à venir ;
- alertes ;
- dernières transactions ;
- stock faible ;
- raccourcis ;
- statut TPE ;
- messages importants.

---

## 13. Actions rapides

- Nouveau paiement ;
- Générer un QR ;
- Scanner ;
- Envoyer un lien ;
- Créer une facture ;
- Rembourser ;
- Ajouter un produit ;
- Ouvrir une caisse ;
- Consulter les rapports.

---

## 14. Multi-magasins

Le commerçant peut gérer plusieurs :

- magasins ;
- agences ;
- restaurants ;
- stands ;
- franchises ;
- sites temporaires.

Chaque point de vente doit disposer de ses propres employés, caisses, TPE, horaires, catalogue, stock, transactions et rapports.

---

## 15. Fiche point de vente

Chaque point de vente contient :

- identifiant ;
- nom ;
- adresse ;
- coordonnées ;
- horaires ;
- responsable ;
- statut ;
- devise ;
- employés ;
- caisses ;
- terminaux ;
- QR ;
- historique.

---

## 16. Gestion des caisses

Chaque caisse possède :

- identifiant ;
- point de vente ;
- nom ;
- employé actif ;
- appareil ;
- TPE associé ;
- statut ;
- ouverture ;
- fermeture ;
- historique ;
- totaux ;
- écarts éventuels.

---

## 17. Ouverture de caisse

L’ouverture enregistre :

- employé ;
- caisse ;
- heure ;
- appareil ;
- point de vente ;
- fonds initial éventuel ;
- note ;
- géolocalisation si activée.

---

## 18. Fermeture de caisse

La fermeture doit afficher :

- total des ventes ;
- nombre d’opérations ;
- remboursements ;
- annulations ;
- paiements par moyen ;
- espèces déclarées si concerné ;
- écarts ;
- commentaire ;
- signature ou confirmation.

---

## 19. Employés

Chaque employé doit avoir :

- identité ;
- téléphone ;
- e-mail ;
- rôle ;
- permissions ;
- magasins autorisés ;
- caisses autorisées ;
- appareil ;
- statut ;
- horaires ;
- historique de connexion.

---

## 20. Rôles employés

Exemples :

```text
OWNER
ADMIN
MANAGER
SUPERVISOR
CASHIER
ACCOUNTANT
INVENTORY_MANAGER
CATALOG_MANAGER
SUPPORT
VIEWER
```

---

## 21. Permissions employés

Exemples :

- accepter un paiement ;
- saisir un montant ;
- appliquer une remise ;
- annuler ;
- rembourser ;
- consulter les ventes ;
- exporter ;
- gérer le catalogue ;
- gérer le stock ;
- gérer les employés ;
- modifier les prix ;
- consulter les règlements ;
- gérer les TPE ;
- modifier les paramètres.

---

## 22. Connexion employé

La connexion peut utiliser :

- PIN ;
- mot de passe ;
- biométrie ;
- QR ;
- badge ;
- appareil approuvé ;
- MFA pour les rôles sensibles.

---

## 23. Encaissement

Le commerçant doit pouvoir encaisser par :

- QR dynamique ;
- QR statique ;
- NFC ;
- Tap to Pay ;
- carte physique ;
- carte virtuelle ;
- TPE ;
- lien de paiement ;
- facture ;
- demande de paiement ;
- Mobile Money ;
- paiement à distance.

---

## 24. Nouveau paiement

Le parcours doit permettre :

- saisie du montant ;
- choix de la devise ;
- sélection des produits ;
- sélection du client ;
- remise ;
- taxe ;
- pourboire ;
- description ;
- référence ;
- moyen de paiement ;
- confirmation.

---

## 25. Paiement QR dynamique

Le QR doit pouvoir contenir :

- marchand ;
- point de vente ;
- caisse ;
- employé ;
- montant ;
- devise ;
- taxe ;
- remise ;
- pourboire ;
- référence ;
- expiration ;
- signature.

---

## 26. Paiement QR statique

Le QR statique peut être lié à :

- commerçant ;
- point de vente ;
- caisse ;
- employé ;
- produit ;
- campagne.

Le client saisit ou confirme le montant.

---

## 27. Lien de paiement

Le lien peut contenir :

- montant fixe ou libre ;
- devise ;
- produit ;
- description ;
- expiration ;
- nombre d’utilisations ;
- référence ;
- redirection ;
- QR associé.

---

## 28. Tap to Pay

Lorsque disponible, le téléphone du commerçant peut accepter :

- carte sans contact ;
- wallet mobile ;
- appareil NFC compatible.

Le module doit gérer authentification, limites, certificats, reçus, mises à jour et contrôles de sécurité.

---

## 29. Paiement TPE

L’application peut :

- sélectionner un TPE ;
- envoyer le montant ;
- suivre le statut ;
- afficher le résultat ;
- recevoir le reçu ;
- relancer en cas d’échec confirmé ;
- signaler une panne.

---

## 30. Paiement Mobile Money

Le commerçant peut générer une demande liée à :

- opérateur ;
- numéro client ;
- montant ;
- frais ;
- référence ;
- statut ;
- webhook partenaire.

---

## 31. Paiement à distance

Le commerçant peut envoyer une demande par :

- SMS ;
- e-mail ;
- messagerie ;
- QR ;
- lien ;
- notification Mansa.

---

## 32. Pourboire

La fonction peut proposer :

- aucun ;
- montant libre ;
- pourcentage ;
- valeurs prédéfinies.

Les règles doivent être administrables par pays, secteur et point de vente.

---

## 33. Remises

Types possibles :

- montant fixe ;
- pourcentage ;
- coupon ;
- promotion ;
- fidélité ;
- remise employé ;
- remise manager.

Les remises sensibles peuvent exiger une autorisation.

---

## 34. Taxes

L’application doit gérer :

- taxes incluses ;
- taxes ajoutées ;
- taux par produit ;
- taux par pays ;
- exonération ;
- numéro fiscal ;
- ventilation sur facture.

---

## 35. Paiements en attente

Une opération en attente doit afficher :

- référence ;
- moyen ;
- montant ;
- date ;
- délai ;
- statut ;
- bouton Vérifier ;
- bouton Support.

Elle ne doit pas être relancée sans contrôle d’idempotence.

---

## 36. Statuts de paiement

- CREATED ;
- PENDING ;
- PROCESSING ;
- AUTHORIZED ;
- COMPLETED ;
- FAILED ;
- CANCELLED ;
- EXPIRED ;
- REVERSED ;
- REFUNDED ;
- PARTIALLY_REFUNDED ;
- DISPUTED ;
- REVIEW_REQUIRED.

---

## 37. Transactions

L’écran Transactions doit permettre :

- liste ;
- recherche ;
- filtres ;
- tri ;
- date ;
- point de vente ;
- caisse ;
- employé ;
- moyen ;
- statut ;
- montant ;
- client ;
- export.

---

## 38. Détail d’une transaction

Doit afficher :

- référence ;
- montant ;
- frais ;
- taxe ;
- remise ;
- pourboire ;
- total ;
- devise ;
- client masqué ;
- employé ;
- caisse ;
- terminal ;
- moyen ;
- statut ;
- reçu ;
- actions autorisées.

---

## 39. Annulation

Une annulation est possible selon le statut et le canal.

Elle doit enregistrer :

- auteur ;
- motif ;
- montant ;
- référence ;
- approbateur éventuel ;
- résultat ;
- écriture ledger ;
- notification client.

---

## 40. Remboursement

Le remboursement peut être :

- total ;
- partiel ;
- par produit ;
- par quantité ;
- sur le moyen d’origine ;
- sur wallet selon règles.

Il doit respecter droits, délais, limites, frais, taxes, disponibilité du solde et règles du partenaire.

---

## 41. Validation des remboursements

Une approbation peut être demandée selon :

- montant ;
- ancienneté ;
- rôle ;
- type de paiement ;
- pays ;
- risque ;
- historique ;
- fréquence.

---

## 42. Reçus

Les reçus peuvent être :

- imprimés ;
- affichés ;
- envoyés par SMS ;
- envoyés par e-mail ;
- envoyés dans l’application Client ;
- partagés ;
- téléchargés.

---

## 43. Factures

Le commerçant peut créer :

- devis ;
- facture ;
- facture pro forma ;
- facture récurrente ;
- avoir ;
- reçu fiscal ;
- facture partielle.

---

## 44. Contenu d’une facture

- commerçant ;
- client ;
- numéro ;
- date ;
- échéance ;
- produits ;
- quantités ;
- prix ;
- taxes ;
- remises ;
- total ;
- statut ;
- moyen de paiement ;
- coordonnées de règlement.

---

## 45. Statuts facture

- DRAFT ;
- SENT ;
- VIEWED ;
- PARTIALLY_PAID ;
- PAID ;
- OVERDUE ;
- CANCELLED ;
- REFUNDED ;
- WRITTEN_OFF.

---

## 46. Catalogue

Le catalogue doit gérer :

- produits ;
- services ;
- catégories ;
- variantes ;
- options ;
- images ;
- prix ;
- taxes ;
- promotions ;
- disponibilité ;
- codes-barres ;
- SKU.

---

## 47. Fiche produit

Chaque produit peut contenir :

- identifiant ;
- nom ;
- description ;
- catégorie ;
- image ;
- prix ;
- coût ;
- taxe ;
- stock ;
- unité ;
- variantes ;
- code-barres ;
- statut ;
- points de vente.

---

## 48. Variantes et options

Exemples :

- taille ;
- couleur ;
- format ;
- accompagnement ;
- supplément ;
- personnalisation ;
- menu ;
- dose ;
- durée.

---

## 49. Stock léger

Le module doit permettre :

- quantité disponible ;
- entrée ;
- sortie ;
- correction ;
- seuil bas ;
- alerte ;
- inventaire ;
- historique ;
- stock par point de vente.

---

## 50. Mouvements de stock

Types :

- PURCHASE ;
- SALE ;
- RETURN ;
- TRANSFER ;
- ADJUSTMENT ;
- LOSS ;
- DAMAGE ;
- INVENTORY_CORRECTION.

---

## 51. Scanner code-barres

Le commerçant peut :

- scanner un produit ;
- ajouter au panier ;
- créer une fiche ;
- rechercher ;
- vérifier le prix ;
- compter le stock.

---

## 52. Commandes

Le module peut gérer :

- commande sur place ;
- à emporter ;
- livraison ;
- réservation ;
- commande en ligne ;
- commande téléphonique ;
- commande institutionnelle.

---

## 53. Statuts commande

- DRAFT ;
- CREATED ;
- CONFIRMED ;
- PREPARING ;
- READY ;
- OUT_FOR_DELIVERY ;
- COMPLETED ;
- CANCELLED ;
- REFUNDED.

---

## 54. Gestion restaurant

Fonctions activables :

- tables ;
- plans de salle ;
- serveurs ;
- commandes ;
- cuisine ;
- séparation d’addition ;
- pourboire ;
- impression cuisine ;
- clôture table.

---

## 55. Division d’addition

Le commerçant peut diviser :

- à parts égales ;
- par produit ;
- par montant ;
- par participant ;
- par pourcentage ;
- avec plusieurs moyens de paiement.

---

## 56. Clients

Le commerçant peut gérer, avec consentement et selon la réglementation :

- nom ;
- téléphone ;
- e-mail ;
- historique ;
- préférences ;
- fidélité ;
- factures ;
- notes internes limitées ;
- consentements marketing.

---

## 57. Fidélité

Le module peut gérer :

- points ;
- niveaux ;
- cartes digitales ;
- récompenses ;
- avantages ;
- expiration ;
- campagnes ;
- historique ;
- règles par magasin.

---

## 58. Promotions

Types possibles :

- réduction fixe ;
- pourcentage ;
- achat multiple ;
- produit offert ;
- cashback ;
- coupon ;
- promotion horaire ;
- promotion segmentée ;
- offre géolocalisée.

---

## 59. Coupons

Un coupon peut avoir :

- code ;
- QR ;
- période ;
- nombre d’utilisations ;
- montant minimum ;
- produits ;
- magasins ;
- clients éligibles ;
- plafond ;
- statut.

---

## 60. Règlements commerçant

Le commerçant doit consulter :

- solde disponible ;
- solde en attente ;
- réserves ;
- frais ;
- commissions ;
- prochaines dates ;
- compte bancaire ;
- historique ;
- écarts ;
- retenues éventuelles.

---

## 61. Calendrier de règlement

Le règlement peut être :

- instantané ;
- quotidien ;
- hebdomadaire ;
- mensuel ;
- à la demande ;
- selon contrat ;
- selon seuil.

---

## 62. Compte de règlement

Le commerçant peut gérer :

- wallet Mansa ;
- compte bancaire ;
- plusieurs comptes autorisés ;
- devise ;
- compte principal ;
- changement sécurisé ;
- vérification ;
- historique.

---

## 63. Rapports

Rapports possibles :

- ventes ;
- transactions ;
- produits ;
- employés ;
- magasins ;
- caisses ;
- moyens de paiement ;
- taxes ;
- remises ;
- remboursements ;
- règlements ;
- fidélité ;
- stock ;
- rentabilité.

---

## 64. Statistiques

Indicateurs :

- chiffre d’affaires ;
- nombre de ventes ;
- panier moyen ;
- taux de réussite ;
- remboursements ;
- meilleur produit ;
- meilleur point de vente ;
- meilleur employé selon critères autorisés ;
- nouveaux clients ;
- récurrence ;
- heures fortes ;
- frais ;
- revenu net.

---

## 65. Export

Formats :

- PDF ;
- CSV ;
- XLSX ;
- rapport fiscal ;
- rapport comptable ;
- période personnalisée.

Une authentification renforcée peut être exigée.

---

## 66. TPE

L’application doit permettre :

- lister les terminaux ;
- voir le statut ;
- associer un point de vente ;
- associer une caisse ;
- associer un employé ;
- envoyer un montant ;
- consulter les transactions ;
- demander assistance ;
- voir les mises à jour ;
- suspendre selon droit.

---

## 67. Statuts TPE

- PENDING ;
- ACTIVE ;
- OFFLINE ;
- DEGRADED ;
- MAINTENANCE ;
- SUSPENDED ;
- LOST ;
- STOLEN ;
- DECOMMISSIONED.

---

## 68. Notifications

Types :

- paiement reçu ;
- paiement échoué ;
- remboursement ;
- règlement ;
- stock faible ;
- commande ;
- sécurité ;
- TPE ;
- KYB ;
- support ;
- promotion ;
- maintenance.

---

## 69. Support

Le support doit être accessible depuis :

- transaction ;
- TPE ;
- règlement ;
- KYB ;
- employé ;
- facture ;
- stock ;
- paramètres ;
- Jini.

Canaux : FAQ, base de connaissances, chat, ticket, téléphone, e-mail et rappel.

---

## 70. Litiges

Le commerçant peut signaler :

- paiement non reçu ;
- double paiement ;
- remboursement bloqué ;
- règlement manquant ;
- TPE indisponible ;
- fraude ;
- annulation incorrecte ;
- chargeback ;
- écart de caisse.

---

## 71. Jini

Jini peut aider à :

- trouver une vente ;
- expliquer un règlement ;
- créer un rapport ;
- identifier un stock faible ;
- préparer une facture ;
- expliquer les frais ;
- créer un ticket ;
- guider un employé ;
- proposer une promotion ;
- analyser les tendances.

Jini ne doit pas effectuer seul une action financière irréversible.

---

## 72. Sécurité

L’application doit gérer :

- MFA ;
- biométrie ;
- PIN ;
- mot de passe ;
- appareils ;
- sessions ;
- rôles ;
- permissions ;
- limites ;
- alertes ;
- chiffrement ;
- détection root/jailbreak ;
- révocation ;
- journaux.

---

## 73. Centre de sécurité

Il doit afficher :

- appareils actifs ;
- sessions ;
- employés ;
- connexions récentes ;
- TPE ;
- alertes ;
- actions sensibles ;
- recommandations ;
- contacts d’urgence.

---

## 74. Réseau faible et hors ligne

L’application doit :

- conserver les brouillons ;
- afficher les données en cache ;
- éviter les doubles paiements ;
- reprendre les chargements ;
- distinguer données anciennes et données à jour ;
- synchroniser après reconnexion.

Les paiements hors ligne ne sont autorisés que par un mécanisme spécifique, limité et approuvé.

---

## 75. Idempotence

Chaque opération sensible doit utiliser :

- référence unique ;
- clé d’idempotence ;
- statut serveur ;
- blocage temporaire du bouton ;
- vérification avant réessai ;
- historique.

---

## 76. Administration centralisée

L’administration doit pouvoir gérer :

- types de commerçants ;
- pays ;
- devises ;
- KYB ;
- modules ;
- navigation ;
- moyens de paiement ;
- frais ;
- commissions ;
- limites ;
- taxes ;
- remboursements ;
- catalogues ;
- promotions ;
- TPE ;
- règlements ;
- notifications ;
- support ;
- versions ;
- feature flags ;
- contenus ;
- audits.

---

## 77. Segmentation

Les fonctions et contenus peuvent être ciblés selon :

- pays ;
- secteur ;
- taille ;
- volume ;
- ancienneté ;
- risque ;
- version ;
- point de vente ;
- abonnement ;
- partenaire ;
- niveau KYB.

---

## 78. API principales

```http
POST   /merchant/auth/register
POST   /merchant/auth/login
GET    /merchant/profile
PATCH  /merchant/profile

GET    /merchant/kyb
POST   /merchant/kyb

GET    /merchant/stores
POST   /merchant/stores
GET    /merchant/registers
POST   /merchant/registers/{id}/open
POST   /merchant/registers/{id}/close

GET    /merchant/employees
POST   /merchant/employees
PATCH  /merchant/employees/{id}

POST   /merchant/payments
POST   /merchant/payment-links
POST   /merchant/qr
GET    /merchant/transactions
GET    /merchant/transactions/{id}
POST   /merchant/transactions/{id}/cancel
POST   /merchant/transactions/{id}/refund

GET    /merchant/catalog/products
POST   /merchant/catalog/products
PATCH  /merchant/catalog/products/{id}
GET    /merchant/inventory
POST   /merchant/inventory/adjustments

GET    /merchant/orders
POST   /merchant/orders
PATCH  /merchant/orders/{id}

GET    /merchant/invoices
POST   /merchant/invoices
POST   /merchant/invoices/{id}/send

GET    /merchant/customers
GET    /merchant/loyalty
GET    /merchant/promotions

GET    /merchant/settlements
GET    /merchant/reports
GET    /merchant/terminals
POST   /merchant/support/tickets
POST   /merchant/jini/messages
```

---

## 79. Webhooks internes

```text
merchant.registered
merchant.kyb.submitted
merchant.kyb.approved
merchant.store.created
merchant.employee.created
merchant.register.opened
merchant.register.closed
merchant.payment.created
merchant.payment.completed
merchant.payment.failed
merchant.payment.refunded
merchant.invoice.created
merchant.invoice.paid
merchant.order.created
merchant.order.completed
merchant.inventory.low
merchant.settlement.created
merchant.settlement.completed
merchant.terminal.offline
merchant.security.alert.created
```

---

## 80. Modèles principaux

- MerchantProfile
- MerchantKYBProfile
- MerchantStore
- MerchantRegister
- MerchantEmployee
- MerchantRole
- MerchantPermission
- MerchantPayment
- MerchantTransaction
- PaymentLink
- MerchantQRCode
- MerchantRefund
- MerchantReceipt
- MerchantInvoice
- MerchantInvoiceLine
- MerchantProduct
- MerchantCategory
- ProductVariant
- InventoryItem
- InventoryMovement
- MerchantOrder
- MerchantCustomer
- LoyaltyProgram
- LoyaltyAccount
- MerchantPromotion
- MerchantCoupon
- MerchantSettlement
- MerchantTerminal
- MerchantNotification
- MerchantSupportTicket
- MerchantSecurityAlert
- MerchantAudit

---

## 81. Rôles administratifs

```text
MERCHANT_ADMIN
MERCHANT_KYB_REVIEWER
MERCHANT_SUPPORT_OPERATOR
MERCHANT_PAYMENT_OPERATOR
MERCHANT_REFUND_APPROVER
MERCHANT_SETTLEMENT_OPERATOR
MERCHANT_TERMINAL_MANAGER
MERCHANT_CONTENT_MANAGER
MERCHANT_SECURITY_ADMIN
AUDITOR
VIEWER
```

---

## 82. Permissions administratives

```text
merchant.read
merchant.manage
merchant.kyb.read
merchant.kyb.review
merchant.payment.read
merchant.payment.investigate
merchant.refund.approve
merchant.settlement.read
merchant.settlement.manage
merchant.terminal.manage
merchant.employee.manage
merchant.content.manage
merchant.configuration.publish
merchant.audit.read
```

---

## 83. Approbations

Peuvent nécessiter une approbation :

- remboursement important ;
- correction financière ;
- changement de compte de règlement ;
- modification exceptionnelle de limites ;
- dégel du compte ;
- changement de frais nationaux ;
- suppression d’une preuve ;
- activation d’un moyen de paiement sensible ;
- clôture forcée.

---

## 84. Double validation

Doit être exigée pour :

- écriture financière manuelle ;
- correction de solde ;
- remboursement majeur ;
- modification massive des frais ;
- changement du compte de règlement après fraude ;
- suppression d’un audit ;
- réactivation d’un marchand critique ;
- export massif sensible.

---

## 85. Audit

Le journal doit contenir :

- commerçant ;
- magasin ;
- caisse ;
- employé ;
- appareil ;
- action ;
- ressource ;
- ancienne valeur ;
- nouvelle valeur ;
- date ;
- heure ;
- pays ;
- résultat ;
- motif ;
- approbateur ;
- référence.

---

## 86. Analytics

Événements possibles :

```text
merchant_app_opened
merchant_login_completed
merchant_dashboard_opened
merchant_payment_started
merchant_payment_completed
merchant_refund_started
merchant_refund_completed
merchant_product_created
merchant_order_created
merchant_report_exported
merchant_terminal_opened
merchant_support_ticket_created
merchant_jini_opened
```

Ne jamais transmettre PIN, OTP, mot de passe, PAN complet, CVV, secrets, documents complets ou données clients inutiles.

---

## 87. Tests fonctionnels

- inscription ;
- connexion ;
- KYB ;
- magasin ;
- caisse ;
- employé ;
- QR statique ;
- QR dynamique ;
- lien ;
- Tap to Pay ;
- TPE ;
- Mobile Money ;
- annulation ;
- remboursement ;
- facture ;
- catalogue ;
- stock ;
- commande ;
- fidélité ;
- promotion ;
- règlement ;
- rapport ;
- support ;
- Jini.

---

## 88. Tests financiers

- ledger ;
- frais ;
- commissions ;
- taxes ;
- remises ;
- remboursement total ;
- remboursement partiel ;
- reversal ;
- règlement ;
- réserve ;
- timeout ;
- idempotence ;
- rapprochement ;
- écarts.

---

## 89. Tests de sécurité

- rôles ;
- permissions ;
- MFA ;
- appareil ;
- session ;
- root/jailbreak ;
- deep links ;
- export ;
- changement de compte ;
- remboursement ;
- TPE perdu ;
- secrets ;
- logs ;
- révocation.

---

## 90. Tests de performance et résilience

- démarrage ;
- faible réseau ;
- catalogue volumineux ;
- historique long ;
- pic de paiements ;
- synchronisation ;
- TPE hors ligne ;
- partenaire indisponible ;
- timeout ;
- reprise ;
- consommation mémoire ;
- batterie.

---

## 91. Règles métier

1. Toute transaction financière passe par le ledger.
2. Les frais sont affichés avant confirmation.
3. Toute transaction possède une référence unique.
4. Les employés utilisent des permissions limitées.
5. Les magasins sont isolés logiquement.
6. Les caisses sont ouvertes et fermées par un utilisateur identifié.
7. Les remboursements respectent les droits et délais.
8. Les règlements proviennent des écritures validées.
9. Les statistiques n’utilisent pas des montants non confirmés.
10. Les paiements sont idempotents.
11. Un timeout n’est pas un échec définitif sans vérification.
12. Les fonctions sont activables par pays et segment.
13. Les TPE sont associés à un marchand et un point de vente.
14. Les changements de compte de règlement sont sécurisés.
15. Les données clients sont limitées au nécessaire.
16. Les exports sensibles exigent une authentification forte.
17. Jini ne finalise pas seul une opération irréversible.
18. Les opérations hors ligne restent limitées.
19. Toute correction financière est auditée.
20. Les audits sont immuables.

---

## 92. Critères d’acceptation

L’Application Commerçant Mansa est validée lorsque :

- Android et iOS sont supportés ;
- l’onboarding est administrable ;
- l’inscription fonctionne ;
- le KYB est configurable ;
- le profil marchand est complet ;
- le tableau de bord affiche des données fiables ;
- les magasins multiples sont supportés ;
- les caisses multiples sont supportées ;
- l’ouverture et la fermeture de caisse fonctionnent ;
- les employés et rôles sont gérés ;
- les permissions sont appliquées ;
- le QR statique fonctionne ;
- le QR dynamique fonctionne ;
- les liens de paiement fonctionnent ;
- Tap to Pay est supportable ;
- le TPE est intégré ;
- Mobile Money est supportable ;
- les paiements à distance fonctionnent ;
- les pourboires sont configurables ;
- les remises sont contrôlées ;
- les taxes sont gérées ;
- les paiements en attente sont vérifiés ;
- les statuts de paiement sont complets ;
- l’historique et la recherche fonctionnent ;
- le détail de transaction est complet ;
- les annulations sont contrôlées ;
- les remboursements totaux et partiels fonctionnent ;
- les validations de remboursement sont configurables ;
- les reçus sont disponibles ;
- les factures et avoirs sont gérés ;
- le catalogue est disponible ;
- les variantes sont supportées ;
- le stock léger fonctionne ;
- le scanner code-barres fonctionne ;
- les commandes sont gérées ;
- le mode restaurant est activable ;
- la division d’addition fonctionne ;
- les clients sont gérés avec consentement ;
- la fidélité est disponible ;
- les promotions et coupons sont configurables ;
- les règlements sont visibles ;
- le calendrier de règlement est configurable ;
- le compte de règlement est sécurisé ;
- les rapports sont disponibles ;
- les exports sont disponibles ;
- les TPE sont supervisables ;
- les notifications sont centralisées ;
- le support est accessible ;
- les litiges sont gérés ;
- Jini est intégré ;
- la sécurité est appliquée ;
- le centre de sécurité est disponible ;
- le réseau faible est supporté ;
- l’idempotence empêche les doubles paiements ;
- l’administration centralisée peut modifier les modules ;
- la segmentation fonctionne ;
- les API sont définies ;
- les webhooks sont définis ;
- les modèles sont définis ;
- les rôles et permissions administratifs sont définis ;
- les approbations critiques sont protégées ;
- les audits sont immuables ;
- les tests couvrent les parcours fonctionnels, financiers, sécuritaires et de résilience.
