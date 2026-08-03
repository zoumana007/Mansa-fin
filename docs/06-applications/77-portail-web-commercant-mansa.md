# 77 — Portail Web Commerçant Mansa : gestion multi-sites, ventes, paiements, catalogue, stocks, employés, facturation, règlements, rapports, API, sécurité et administration centralisée

## 1. Objet du document

Ce document définit le cahier des charges complet du **Portail Web Commerçant Mansa**.

Le portail est destiné aux commerçants, entreprises et responsables de réseau qui ont besoin d’une interface plus complète que l’application mobile pour gérer leurs activités.

Il doit permettre notamment :

- gérer plusieurs commerces ;
- gérer plusieurs points de vente ;
- gérer plusieurs caisses ;
- gérer plusieurs employés ;
- consulter les paiements ;
- rechercher une transaction ;
- effectuer ou demander un remboursement ;
- suivre les annulations ;
- suivre les règlements ;
- consulter les frais et commissions ;
- gérer le catalogue ;
- gérer les stocks ;
- gérer les commandes ;
- gérer les factures ;
- gérer les clients ;
- gérer les promotions ;
- gérer la fidélité ;
- gérer les TPE ;
- gérer les QR Codes ;
- générer des liens de paiement ;
- gérer les accès API ;
- produire des rapports ;
- exporter les données ;
- superviser les risques ;
- contacter le support ;
- administrer les paramètres du commerce.

Le portail doit être :

- professionnel ;
- moderne ;
- responsive ;
- sécurisé ;
- multi-pays ;
- multi-devises ;
- multi-langues ;
- multi-entités ;
- multi-sites ;
- administrable ;
- auditable ;
- compatible avec les navigateurs modernes ;
- adapté aux PME comme aux grands réseaux.

---

# 2. Principes fondamentaux

## 2.1 Une vision consolidée et une vision locale

Le portail doit permettre de consulter :

- toutes les entreprises ;
- une entreprise précise ;
- un point de vente ;
- une caisse ;
- un TPE ;
- un employé ;
- une période ;
- une devise ;
- un pays.

---

## 2.2 Les données financières doivent être fiables

Les tableaux de bord financiers doivent utiliser :

- les transactions validées ;
- les écritures ledger ;
- les remboursements confirmés ;
- les règlements rapprochés ;
- les frais réellement appliqués ;
- les commissions réellement comptabilisées.

---

## 2.3 Les rôles doivent être strictement séparés

Un caissier, un comptable, un manager et le propriétaire ne doivent pas avoir les mêmes droits.

---

## 2.4 Toutes les opérations sensibles doivent être tracées

Doivent être audités :

- connexion ;
- ajout d’utilisateur ;
- changement de rôle ;
- remboursement ;
- modification de compte bancaire ;
- changement de frais ;
- création de clé API ;
- export ;
- suppression ;
- changement de configuration ;
- ajout de point de vente.

---

## 2.5 Le portail ne doit pas dépendre d’un seul modèle de commerce

Il doit pouvoir servir :

- boutique ;
- restaurant ;
- pharmacie ;
- station-service ;
- hôtel ;
- grande surface ;
- établissement scolaire ;
- clinique ;
- plateforme e-commerce ;
- entreprise de services ;
- réseau de franchises ;
- administration autorisée.

---

# 3. Types d’utilisateurs

Le portail peut être utilisé par :

- propriétaire ;
- directeur général ;
- directeur réseau ;
- responsable magasin ;
- manager ;
- comptable ;
- caissier ;
- responsable stock ;
- responsable catalogue ;
- responsable marketing ;
- responsable fidélité ;
- analyste ;
- support interne ;
- auditeur ;
- développeur ;
- administrateur technique.

---

# 4. Rôles

Exemples :

```text
MERCHANT_OWNER
MERCHANT_ADMIN
MERCHANT_MANAGER
STORE_MANAGER
ACCOUNTANT
FINANCE_VIEWER
CASHIER
INVENTORY_MANAGER
CATALOG_MANAGER
MARKETING_MANAGER
LOYALTY_MANAGER
DEVELOPER
AUDITOR
VIEWER
```

---

# 5. Permissions

Exemples :

```text
merchant.read
merchant.update
merchant.store.read
merchant.store.manage
merchant.employee.read
merchant.employee.manage
merchant.transaction.read
merchant.refund.create
merchant.refund.approve
merchant.settlement.read
merchant.invoice.manage
merchant.catalog.manage
merchant.inventory.manage
merchant.promotion.manage
merchant.loyalty.manage
merchant.terminal.manage
merchant.api.manage
merchant.report.export
merchant.audit.read
```

---

# 6. Connexion

La connexion peut utiliser :

- e-mail ;
- téléphone ;
- mot de passe ;
- passkey ;
- biométrie via appareil compatible ;
- MFA ;
- SSO entreprise ;
- appareil approuvé.

---

# 7. MFA

Le MFA peut utiliser :

- application d’authentification ;
- SMS ;
- e-mail ;
- passkey ;
- clé physique ;
- validation dans l’application Mansa.

---

# 8. Nouvel appareil

Une connexion depuis un nouvel appareil peut exiger :

- OTP ;
- MFA ;
- confirmation par un administrateur ;
- délai de sécurité ;
- vérification de localisation ;
- notification au propriétaire.

---

# 9. Gestion des sessions

Le portail doit permettre :

- voir les sessions actives ;
- identifier les appareils ;
- révoquer une session ;
- déconnecter tous les appareils ;
- définir une durée maximale ;
- appliquer un verrouillage automatique.

---

# 10. Tableau de bord principal

Le tableau de bord peut afficher :

- chiffre d’affaires ;
- nombre de transactions ;
- panier moyen ;
- taux de réussite ;
- remboursements ;
- annulations ;
- règlement à venir ;
- net attendu ;
- frais ;
- commissions ;
- meilleurs points de vente ;
- meilleurs produits ;
- alertes ;
- incidents ;
- TPE hors ligne ;
- stocks faibles.

---

# 11. Filtres du tableau de bord

Filtres possibles :

- période ;
- entreprise ;
- pays ;
- ville ;
- point de vente ;
- caisse ;
- employé ;
- TPE ;
- moyen de paiement ;
- devise ;
- catégorie ;
- statut.

---

# 12. Vues du tableau de bord

- vue globale ;
- vue financière ;
- vue ventes ;
- vue opérations ;
- vue règlements ;
- vue stock ;
- vue marketing ;
- vue fidélité ;
- vue risques ;
- vue TPE.

---

# 13. Indicateurs principaux

Exemples :

- GMV ;
- revenu net ;
- nombre de ventes ;
- panier moyen ;
- taux de conversion ;
- taux de remboursement ;
- taux d’annulation ;
- délai de règlement ;
- coût moyen par transaction ;
- taux d’utilisation QR ;
- taux d’utilisation carte ;
- taux d’utilisation Mobile Money.

---

# 14. Gestion des entreprises

Le portail doit permettre de gérer :

- raison sociale ;
- nom commercial ;
- identifiant ;
- pays ;
- secteur ;
- statut ;
- logo ;
- adresses ;
- représentants ;
- comptes de règlement ;
- documents ;
- contrats ;
- paramètres.

---

# 15. Multi-entités

Un groupe peut gérer :

- société mère ;
- filiales ;
- franchises ;
- enseignes ;
- établissements ;
- divisions ;
- pays différents.

---

# 16. Hiérarchie commerciale

Exemple :

```text
Groupe
→ Entreprise
→ Enseigne
→ Région
→ Point de vente
→ Caisse
→ TPE
```

---

# 17. Gestion des points de vente

Chaque point de vente doit posséder :

- identifiant ;
- nom ;
- adresse ;
- géolocalisation ;
- horaires ;
- responsable ;
- employés ;
- caisses ;
- TPE ;
- devise ;
- statut ;
- services ;
- règles ;
- historique.

---

# 18. Statuts d’un point de vente

- DRAFT ;
- PENDING_APPROVAL ;
- ACTIVE ;
- SUSPENDED ;
- TEMPORARILY_CLOSED ;
- CLOSED ;
- UNDER_REVIEW ;
- DECOMMISSIONED.

---

# 19. Horaires

Le portail doit gérer :

- horaires réguliers ;
- horaires exceptionnels ;
- jours fériés ;
- fermetures temporaires ;
- ouvertures spéciales ;
- fuseaux horaires.

---

# 20. Gestion des caisses

Chaque caisse possède :

- identifiant ;
- point de vente ;
- employés autorisés ;
- TPE associé ;
- statut ;
- sessions ;
- transactions ;
- clôtures ;
- écarts éventuels.

---

# 21. Sessions de caisse

Le portail doit afficher :

- heure d’ouverture ;
- heure de fermeture ;
- employé ;
- TPE ;
- ventes ;
- remboursements ;
- annulations ;
- total ;
- anomalies ;
- statut.

---

# 22. Gestion des employés

Le portail doit permettre :

- inviter ;
- créer ;
- modifier ;
- suspendre ;
- supprimer ;
- affecter ;
- changer le rôle ;
- réinitialiser l’accès ;
- consulter l’historique.

---

# 23. Invitation d’un employé

L’invitation peut utiliser :

- e-mail ;
- SMS ;
- lien ;
- QR ;
- code temporaire.

Elle doit être :

- expirante ;
- liée à un rôle ;
- liée à un point de vente ;
- à usage unique ;
- auditable.

---

# 24. Affectation des employés

Un employé peut être affecté à :

- une entreprise ;
- plusieurs entreprises ;
- un magasin ;
- plusieurs magasins ;
- une caisse ;
- plusieurs caisses ;
- un pays ;
- une période.

---

# 25. Restrictions d’employé

Restrictions possibles :

- montant maximum de remboursement ;
- export interdit ;
- accès limité à un magasin ;
- horaires d’accès ;
- consultation sans modification ;
- impossibilité de voir les marges ;
- impossibilité de modifier le catalogue ;
- impossibilité de gérer les clés API.

---

# 26. Historique des connexions

Le portail doit afficher :

- utilisateur ;
- appareil ;
- date ;
- heure ;
- localisation approximative ;
- IP ;
- résultat ;
- MFA ;
- anomalie éventuelle.

---

# 27. Transactions

La page Transactions doit permettre :

- liste ;
- recherche ;
- tri ;
- filtres ;
- export ;
- consultation du détail ;
- remboursement ;
- annulation lorsque possible ;
- ouverture d’un litige ;
- téléchargement du reçu.

---

# 28. Filtres de transactions

- date ;
- statut ;
- montant ;
- devise ;
- moyen ;
- client ;
- caisse ;
- employé ;
- point de vente ;
- TPE ;
- référence ;
- réseau ;
- remboursement ;
- litige.

---

# 29. Statuts

- CREATED ;
- PENDING ;
- AUTHORIZED ;
- PROCESSING ;
- COMPLETED ;
- FAILED ;
- CANCELLED ;
- REVERSED ;
- REFUNDED ;
- PARTIALLY_REFUNDED ;
- DISPUTED ;
- REVIEW_REQUIRED.

---

# 30. Détail d’une transaction

Le détail doit afficher :

- référence ;
- montant brut ;
- frais ;
- commission ;
- montant net ;
- devise ;
- client masqué ;
- moyen de paiement ;
- réseau ;
- point de vente ;
- caisse ;
- TPE ;
- employé ;
- date ;
- heure ;
- statut ;
- reçu ;
- écritures associées ;
- règlement ;
- remboursement ;
- litige ;
- audit.

---

# 31. Recherche avancée

La recherche peut utiliser :

- référence interne ;
- référence acquéreur ;
- référence réseau ;
- montant ;
- quatre derniers chiffres ;
- téléphone masqué ;
- nom ;
- facture ;
- commande ;
- produit ;
- employé ;
- TPE.

---

# 32. Reçus

Le portail doit permettre :

- consulter ;
- télécharger ;
- renvoyer ;
- réimprimer ;
- partager ;
- vérifier ;
- générer un duplicata.

---

# 33. Annulation

L’annulation doit vérifier :

- statut ;
- délai ;
- moyen de paiement ;
- permission ;
- utilisateur ;
- caisse ;
- règlement ;
- motif ;
- authentification.

---

# 34. Remboursement

Le portail doit permettre :

- remboursement total ;
- remboursement partiel ;
- remboursement multiple ;
- demande de remboursement ;
- validation ;
- suivi ;
- export.

---

# 35. Workflow de remboursement

Exemple :

```text
Demande
→ vérification
→ approbation éventuelle
→ exécution
→ écriture ledger
→ notification
→ rapprochement
→ clôture
```

---

# 36. Motifs de remboursement

- retour produit ;
- service non fourni ;
- erreur de montant ;
- double débit ;
- geste commercial ;
- annulation de commande ;
- fraude ;
- autre motif documenté.

---

# 37. Seuils de remboursement

Les seuils peuvent dépendre :

- rôle ;
- montant ;
- pays ;
- moyen ;
- ancienneté ;
- point de vente ;
- risque ;
- catégorie ;
- approbation.

---

# 38. Double validation

Peut être exigée pour :

- remboursement important ;
- remboursement sans transaction ;
- remboursement ancien ;
- correction financière ;
- changement de compte de règlement ;
- export sensible ;
- création de clé API de production.

---

# 39. Litiges

Le portail doit permettre de gérer :

- paiement contesté ;
- paiement non reconnu ;
- service contesté ;
- carte frauduleuse ;
- rétrofacturation ;
- preuve de livraison ;
- preuve de service ;
- réponse au réseau.

---

# 40. Dossier de litige

Il doit contenir :

- transaction ;
- client ;
- motif ;
- montant ;
- date limite ;
- pièces ;
- messages ;
- statut ;
- responsable ;
- décision ;
- impact financier.

---

# 41. Règlements

La page Règlements doit afficher :

- période ;
- montant brut ;
- frais ;
- remboursements ;
- retenues ;
- réserve ;
- net ;
- compte bancaire ;
- date prévue ;
- date effective ;
- statut ;
- référence.

---

# 42. Statuts de règlement

- CALCULATING ;
- PENDING ;
- APPROVED ;
- SENT ;
- COMPLETED ;
- FAILED ;
- HELD ;
- PARTIALLY_COMPLETED ;
- RECONCILIATION_REQUIRED.

---

# 43. Fréquence de règlement

Les règlements peuvent être :

- instantanés ;
- quotidiens ;
- hebdomadaires ;
- mensuels ;
- personnalisés ;
- sur demande ;
- soumis à réserve.

---

# 44. Compte de règlement

Le commerçant peut gérer :

- banque ;
- titulaire ;
- numéro ;
- IBAN ou RIB ;
- devise ;
- pays ;
- statut ;
- validation ;
- historique ;
- date d’effet.

---

# 45. Changement de compte bancaire

Le changement doit exiger :

- authentification forte ;
- preuve ;
- confirmation ;
- délai de sécurité ;
- notification ;
- validation éventuelle ;
- historique ;
- audit.

---

# 46. Rapprochement

Le portail doit rapprocher :

- transactions ;
- ledger ;
- TPE ;
- réseau cartes ;
- Mobile Money ;
- QR ;
- règlement ;
- banque ;
- remboursements ;
- litiges.

---

# 47. Écarts

Un écart doit afficher :

- type ;
- montant ;
- origine ;
- date ;
- transactions ;
- statut ;
- responsable ;
- action ;
- résolution.

---

# 48. Frais

Le portail doit présenter clairement :

- frais fixes ;
- frais variables ;
- commissions ;
- frais réseau ;
- frais partenaires ;
- taxes ;
- promotions ;
- exemptions ;
- date d’effet.

---

# 49. Simulation des frais

Le commerçant peut simuler :

- un montant ;
- un moyen de paiement ;
- une devise ;
- un pays ;
- un produit ;
- un règlement ;
- le net attendu.

---

# 50. Facturation Mansa

Le portail peut générer les factures de services Mansa :

- location TPE ;
- abonnement ;
- frais plateforme ;
- commissions ;
- maintenance ;
- options premium ;
- API ;
- services supplémentaires.

---

# 51. Catalogue

Le catalogue doit permettre de gérer :

- produits ;
- services ;
- catégories ;
- variantes ;
- prix ;
- taxes ;
- images ;
- codes-barres ;
- références ;
- disponibilité ;
- stocks ;
- promotions.

---

# 52. Produit

Chaque produit peut contenir :

- identifiant ;
- nom ;
- description ;
- image ;
- catégorie ;
- SKU ;
- code-barres ;
- prix ;
- coût ;
- taxe ;
- stock ;
- statut ;
- variantes ;
- point de vente ;
- date.

---

# 53. Variantes

Exemples :

- taille ;
- couleur ;
- poids ;
- format ;
- option ;
- supplément ;
- emballage ;
- durée ;
- niveau de service.

---

# 54. Catégories

Les catégories doivent être :

- hiérarchiques ;
- triables ;
- activables ;
- traduisibles ;
- spécifiques à un point de vente ;
- partagées au niveau du groupe.

---

# 55. Import du catalogue

Formats possibles :

- CSV ;
- Excel ;
- API ;
- ERP ;
- caisse ;
- migration ;
- fichier partenaire.

---

# 56. Contrôle d’import

L’import doit vérifier :

- format ;
- doublons ;
- prix ;
- taxes ;
- catégories ;
- références ;
- stocks ;
- images ;
- erreurs ;
- lignes rejetées.

---

# 57. Export du catalogue

Le commerçant peut exporter :

- produits ;
- prix ;
- stock ;
- taxes ;
- variantes ;
- statuts ;
- promotions ;
- références.

---

# 58. Prix

Le portail doit gérer :

- prix standard ;
- prix promotionnel ;
- prix par magasin ;
- prix par pays ;
- prix par devise ;
- prix par client ;
- prix entreprise ;
- prix horaire ;
- prix saisonnier.

---

# 59. Taxes

Les taxes peuvent dépendre :

- pays ;
- produit ;
- service ;
- client ;
- prix HT ;
- prix TTC ;
- exonération ;
- date d’effet ;
- réglementation.

---

# 60. Remises

Types :

- pourcentage ;
- montant fixe ;
- produit offert ;
- remise panier ;
- remise quantité ;
- code promotionnel ;
- remise client ;
- remise employé ;
- remise programmée.

---

# 61. Stock

Le portail peut gérer un stock léger ou avancé selon le module activé.

Il doit permettre :

- quantité ;
- stock disponible ;
- stock réservé ;
- stock minimum ;
- stock maximum ;
- mouvement ;
- inventaire ;
- transfert ;
- perte ;
- ajustement.

---

# 62. Mouvements de stock

- entrée ;
- vente ;
- retour ;
- transfert ;
- perte ;
- casse ;
- correction ;
- inventaire ;
- réservation ;
- annulation.

---

# 63. Alerte stock faible

L’alerte peut dépendre :

- seuil ;
- produit ;
- point de vente ;
- fournisseur ;
- saison ;
- vitesse de vente ;
- délai de réapprovisionnement.

---

# 64. Inventaire

Le portail doit permettre :

- démarrer un inventaire ;
- scanner ;
- saisir ;
- comparer ;
- détecter les écarts ;
- valider ;
- corriger ;
- auditer.

---

# 65. Transfert de stock

Un transfert peut être réalisé :

- entre magasins ;
- entre entrepôt et magasin ;
- entre caisses ;
- vers retour fournisseur ;
- vers quarantaine.

---

# 66. Fournisseurs

Le portail peut gérer :

- fournisseur ;
- contact ;
- adresse ;
- produits ;
- délais ;
- commandes ;
- factures ;
- règlements ;
- performance.

---

# 67. Commandes

Le portail peut gérer :

- commande client ;
- commande en ligne ;
- commande sur place ;
- livraison ;
- retrait magasin ;
- réservation ;
- commande fournisseur.

---

# 68. Statuts de commande

- DRAFT ;
- PENDING_PAYMENT ;
- PAID ;
- PREPARING ;
- READY ;
- SHIPPED ;
- DELIVERED ;
- CANCELLED ;
- REFUNDED ;
- PARTIALLY_REFUNDED.

---

# 69. Détail d’une commande

- client ;
- produits ;
- quantités ;
- prix ;
- taxes ;
- remise ;
- frais ;
- paiement ;
- livraison ;
- statut ;
- historique ;
- employé ;
- point de vente.

---

# 70. Factures clients

Le portail doit permettre :

- créer ;
- envoyer ;
- modifier avant validation ;
- annuler ;
- dupliquer ;
- télécharger ;
- relancer ;
- rapprocher ;
- rembourser.

---

# 71. Numérotation des factures

Elle doit être :

- unique ;
- séquentielle selon règle ;
- configurable par pays ;
- configurable par entreprise ;
- non réutilisable ;
- auditée.

---

# 72. Contenu d’une facture

- entreprise ;
- client ;
- numéro ;
- date ;
- échéance ;
- lignes ;
- quantité ;
- prix ;
- taxes ;
- remise ;
- total ;
- montant payé ;
- solde ;
- coordonnées ;
- mentions légales ;
- statut.

---

# 73. Paiement de facture

Une facture peut être payée via :

- QR ;
- lien ;
- carte ;
- Mansa ;
- Mobile Money ;
- virement ;
- TPE ;
- espèces enregistrées.

---

# 74. Avoir

Le portail doit gérer les avoirs pour :

- remboursement ;
- retour ;
- correction ;
- annulation partielle ;
- geste commercial.

---

# 75. Clients

La base client peut contenir :

- nom ;
- téléphone ;
- e-mail ;
- identifiant ;
- historique ;
- consentements ;
- fidélité ;
- segmentation ;
- notes autorisées ;
- préférences.

---

# 76. Données client minimales

Le commerçant ne doit collecter que les données nécessaires.

Les permissions et finalités doivent être respectées.

---

# 77. Segmentation client

Segments possibles :

- nouveau ;
- régulier ;
- VIP ;
- inactif ;
- gros panier ;
- faible fréquence ;
- entreprise ;
- particulier ;
- membre fidélité ;
- à risque.

---

# 78. Fidélité

Le portail doit gérer :

- programme ;
- points ;
- niveaux ;
- règles ;
- récompenses ;
- expiration ;
- partenaires ;
- historique ;
- campagnes.

---

# 79. Règles de points

Les points peuvent dépendre :

- montant ;
- produit ;
- catégorie ;
- période ;
- point de vente ;
- niveau ;
- moyen de paiement ;
- campagne.

---

# 80. Récompenses

Exemples :

- remise ;
- produit gratuit ;
- cashback ;
- bon d’achat ;
- livraison offerte ;
- accès premium ;
- avantage partenaire.

---

# 81. Promotions

Le portail doit permettre :

- créer ;
- programmer ;
- cibler ;
- suspendre ;
- mesurer ;
- dupliquer ;
- archiver.

---

# 82. Types de promotion

- remise ;
- cashback ;
- coupon ;
- code ;
- offre produit ;
- offre panier ;
- happy hour ;
- fidélité ;
- parrainage ;
- promotion géolocalisée.

---

# 83. Ciblage promotionnel

Le ciblage peut dépendre :

- pays ;
- ville ;
- magasin ;
- client ;
- segment ;
- produit ;
- catégorie ;
- canal ;
- jour ;
- heure ;
- historique ;
- niveau fidélité.

---

# 84. Coupons

Chaque coupon peut avoir :

- code ;
- QR ;
- montant ;
- pourcentage ;
- minimum ;
- maximum ;
- dates ;
- usages ;
- client ;
- magasin ;
- produits ;
- statut.

---

# 85. Liens de paiement

Le portail doit permettre de créer des liens avec :

- montant fixe ;
- montant libre ;
- description ;
- facture ;
- client ;
- date d’expiration ;
- nombre d’utilisations ;
- moyens acceptés ;
- redirection ;
- branding.

---

# 86. Statuts d’un lien

- DRAFT ;
- ACTIVE ;
- PAID ;
- PARTIALLY_PAID ;
- EXPIRED ;
- CANCELLED ;
- DISABLED.

---

# 87. QR Codes

Le portail doit gérer :

- QR statique ;
- QR dynamique ;
- QR par caisse ;
- QR par point de vente ;
- QR par produit ;
- QR par facture ;
- QR événementiel ;
- QR temporaire.

---

# 88. Personnalisation du QR

Le commerçant peut choisir :

- logo ;
- couleur autorisée ;
- format ;
- texte ;
- taille ;
- support d’impression ;
- point de vente ;
- référence.

---

# 89. Gestion des TPE

La page TPE doit afficher :

- terminal ;
- modèle ;
- point de vente ;
- caisse ;
- statut ;
- réseau ;
- batterie ;
- version ;
- imprimante ;
- dernière transaction ;
- dernière synchronisation ;
- alertes ;
- maintenance.

---

# 90. Actions TPE

Selon les droits :

- affecter ;
- désaffecter ;
- suspendre ;
- redémarrer à distance si supporté ;
- synchroniser ;
- mettre à jour ;
- ouvrir un ticket ;
- consulter les diagnostics ;
- modifier la configuration autorisée.

---

# 91. TPE hors ligne

Le portail doit afficher :

- durée ;
- dernière activité ;
- dernière transaction ;
- réseau ;
- cause probable ;
- point de vente ;
- alerte ;
- procédure.

---

# 92. Maintenance TPE

Le commerçant peut :

- créer une demande ;
- choisir le problème ;
- joindre une photo ;
- suivre le technicien ;
- voir le SLA ;
- confirmer la résolution ;
- noter l’intervention.

---

# 93. Gestion des QR statiques

Le portail doit permettre :

- créer ;
- télécharger ;
- imprimer ;
- suspendre ;
- remplacer ;
- associer ;
- suivre les paiements ;
- détecter les QR suspects.

---

# 94. E-commerce

Le portail peut proposer :

- intégration boutique ;
- checkout ;
- plugin ;
- API ;
- lien ;
- panier ;
- statut ;
- remboursement ;
- webhooks.

---

# 95. Plugins

Des plugins peuvent être proposés pour :

- Shopify ;
- WooCommerce ;
- PrestaShop ;
- Magento ;
- plateformes locales ;
- ERP ;
- CMS ;
- caisses.

La disponibilité dépend des partenariats et priorités.

---

# 96. API commerçant

L’API peut permettre :

- créer un paiement ;
- consulter un paiement ;
- créer une facture ;
- créer un remboursement ;
- consulter un règlement ;
- recevoir des webhooks ;
- gérer un lien ;
- récupérer des rapports.

---

# 97. Clés API

Chaque clé doit posséder :

- nom ;
- environnement ;
- permissions ;
- date de création ;
- expiration ;
- dernière utilisation ;
- IP autorisées ;
- statut ;
- propriétaire.

---

# 98. Environnements API

- SANDBOX ;
- TEST ;
- PRODUCTION.

Les clés doivent être séparées par environnement.

---

# 99. Secret API

Le secret doit :

- être affiché une seule fois ;
- être stocké sous forme protégée ;
- pouvoir être renouvelé ;
- pouvoir être révoqué ;
- ne jamais être réaffiché en clair.

---

# 100. Webhooks

Le commerçant doit pouvoir configurer :

- URL ;
- événements ;
- secret ;
- statut ;
- retries ;
- historique ;
- timeout ;
- signature ;
- environnement.

---

# 101. Événements webhook

Exemples :

```text
payment.created
payment.completed
payment.failed
payment.refunded
invoice.paid
settlement.created
settlement.completed
dispute.created
terminal.offline
```

---

# 102. Journaux webhook

Le portail doit afficher :

- événement ;
- URL ;
- date ;
- réponse ;
- code HTTP ;
- durée ;
- tentative ;
- statut ;
- bouton Rejouer.

---

# 103. Sécurité API

Doivent être supportés :

- authentification ;
- signature ;
- idempotence ;
- rate limiting ;
- IP allowlist ;
- rotation ;
- scopes ;
- journalisation ;
- révocation ;
- détection d’abus.

---

# 104. Rapports

Rapports possibles :

- ventes ;
- transactions ;
- règlements ;
- remboursements ;
- frais ;
- commissions ;
- produits ;
- stock ;
- clients ;
- fidélité ;
- promotions ;
- employés ;
- caisses ;
- TPE ;
- taxes ;
- litiges.

---

# 105. Exports

Formats :

- CSV ;
- Excel ;
- PDF ;
- JSON ;
- API ;
- export comptable.

---

# 106. Exports programmés

Le commerçant peut programmer :

- quotidien ;
- hebdomadaire ;
- mensuel ;
- fin de période ;
- destination ;
- format ;
- filtre ;
- chiffrement éventuel.

---

# 107. Intégration comptable

Le portail peut s’intégrer avec :

- logiciel comptable ;
- ERP ;
- export standard ;
- API ;
- fichier ;
- connecteur partenaire.

---

# 108. Données comptables

Exemples :

- ventes ;
- taxes ;
- frais ;
- remboursements ;
- règlements ;
- commissions ;
- créances ;
- avoirs ;
- factures ;
- comptes de passage.

---

# 109. Analytics

Le portail doit afficher :

- évolution ;
- comparaison ;
- tendance ;
- saisonnalité ;
- segmentation ;
- performance ;
- prévision ;
- anomalie ;
- répartition.

---

# 110. Comparaisons

Comparaisons possibles :

- jour précédent ;
- semaine précédente ;
- mois précédent ;
- année précédente ;
- point de vente ;
- produit ;
- employé ;
- région ;
- canal.

---

# 111. Prévisions

Le système peut estimer :

- chiffre d’affaires ;
- volume ;
- besoin de stock ;
- produits en rupture ;
- règlement ;
- tendance client ;
- performance magasin.

Les résultats doivent être présentés comme des estimations.

---

# 112. Jini pour commerçant

Jini peut aider à :

- comprendre les ventes ;
- trouver une transaction ;
- expliquer un règlement ;
- générer un rapport ;
- détecter une anomalie ;
- préparer une promotion ;
- analyser les stocks ;
- répondre sur les frais ;
- créer un ticket.

---

# 113. Limites de Jini

Jini ne doit pas :

- effectuer seul un remboursement ;
- modifier un compte bancaire ;
- créer une clé API ;
- changer les permissions ;
- supprimer une preuve ;
- modifier les frais ;
- approuver une correction financière ;
- contourner une validation.

---

# 114. Actions Jini avec confirmation

Jini peut préparer :

- rapport ;
- filtre ;
- promotion ;
- lien de paiement ;
- facture ;
- ticket ;
- export ;
- recherche ;
- brouillon de remboursement.

L’utilisateur doit confirmer l’action finale.

---

# 115. Support

Le portail doit proposer :

- FAQ ;
- base de connaissances ;
- Jini ;
- chat ;
- ticket ;
- appel ;
- e-mail ;
- diagnostic ;
- statut des services ;
- suivi des incidents.

---

# 116. Ticket support

Le ticket peut contenir :

- catégorie ;
- priorité ;
- transaction ;
- TPE ;
- point de vente ;
- description ;
- capture ;
- document ;
- contact ;
- disponibilité.

---

# 117. Statuts du ticket

- CREATED ;
- OPEN ;
- ASSIGNED ;
- IN_PROGRESS ;
- WAITING_MERCHANT ;
- ESCALATED ;
- RESOLVED ;
- CLOSED ;
- REOPENED.

---

# 118. Centre d’incidents

Le commerçant peut consulter :

- incident général ;
- incident local ;
- service affecté ;
- début ;
- impact ;
- statut ;
- contournement ;
- estimation ;
- résolution.

---

# 119. Notifications

Types :

- paiement ;
- remboursement ;
- règlement ;
- litige ;
- stock ;
- facture ;
- sécurité ;
- employé ;
- TPE ;
- API ;
- maintenance ;
- promotion ;
- conformité.

---

# 120. Préférences de notifications

Canaux :

- web ;
- e-mail ;
- SMS ;
- push ;
- application Commerce ;
- webhook.

---

# 121. Alertes obligatoires

Certaines alertes ne doivent pas être totalement désactivables :

- connexion suspecte ;
- changement de compte bancaire ;
- nouvelle clé API ;
- terminal compromis ;
- règlement bloqué ;
- litige critique ;
- modification de rôle administrateur.

---

# 122. Documents

Le portail peut contenir :

- contrat ;
- KYB ;
- relevé ;
- facture Mansa ;
- rapport ;
- règlement ;
- reçu ;
- attestation ;
- export ;
- preuve ;
- document fiscal.

---

# 123. Paramètres du commerce

- identité ;
- branding ;
- langues ;
- devises ;
- taxes ;
- factures ;
- reçus ;
- paiements ;
- remboursements ;
- employés ;
- sécurité ;
- API ;
- notifications ;
- règlements ;
- horaires ;
- support.

---

# 124. Branding

Le commerçant peut personnaliser dans les limites autorisées :

- logo ;
- nom affiché ;
- couleur secondaire ;
- reçu ;
- facture ;
- lien de paiement ;
- QR ;
- page de paiement ;
- e-mails.

---

# 125. Page de paiement

Elle peut afficher :

- logo ;
- nom ;
- montant ;
- description ;
- facture ;
- moyens ;
- sécurité ;
- conditions ;
- langue ;
- reçu ;
- redirection.

---

# 126. Multi-langues

Le portail peut supporter :

- français ;
- anglais ;
- bambara ;
- arabe ;
- autres langues.

---

# 127. Multi-devises

Le portail doit distinguer :

- devise de vente ;
- devise du client ;
- devise du règlement ;
- devise comptable ;
- taux ;
- frais ;
- conversion ;
- gain ou perte éventuelle.

---

# 128. Accessibilité

Le portail doit prévoir :

- navigation clavier ;
- lecteur d’écran ;
- contraste ;
- taille du texte ;
- libellés ;
- focus visible ;
- erreurs compréhensibles ;
- graphiques accompagnés de données textuelles.

---

# 129. Responsive Design

Le portail doit être utilisable sur :

- ordinateur ;
- tablette ;
- écran large ;
- mobile en consultation limitée.

---

# 130. Navigateurs

Navigateurs supportés :

- Chrome ;
- Edge ;
- Firefox ;
- Safari.

Une politique de versions minimales doit être définie.

---

# 131. Mode sombre

Le portail peut proposer :

- thème système ;
- thème clair ;
- thème sombre.

---

# 132. Réseau faible

Le portail doit :

- optimiser les chargements ;
- paginer ;
- compresser ;
- reprendre les exports ;
- afficher les données en cache lorsque permis ;
- signaler les données non actualisées ;
- éviter les doubles actions.

---

# 133. Prévention du double clic

Les opérations sensibles doivent utiliser :

- bouton bloqué temporairement ;
- clé d’idempotence ;
- confirmation serveur ;
- écran de traitement ;
- vérification de statut.

---

# 134. Timeout

En cas de timeout :

- afficher Vérification en cours ;
- éviter la répétition ;
- interroger le statut ;
- conserver la référence ;
- notifier le résultat final.

---

# 135. Audit

Le portail doit enregistrer :

- utilisateur ;
- rôle ;
- organisation ;
- appareil ;
- IP ;
- action ;
- ressource ;
- ancienne valeur ;
- nouvelle valeur ;
- date ;
- heure ;
- motif ;
- résultat ;
- approbateur éventuel.

---

# 136. Journal d’activité

Le commerçant peut consulter selon ses droits :

- connexions ;
- utilisateurs ;
- remboursements ;
- exports ;
- changements ;
- API ;
- TPE ;
- règlements ;
- paramètres ;
- promotions.

---

# 137. Immutabilité

Les journaux d’audit critiques doivent être protégés contre :

- suppression ;
- modification ;
- remplacement ;
- falsification ;
- export non autorisé ;
- changement de date ;
- changement d’auteur.

---

# 138. Analytics produit

Événements possibles :

```text
merchant_portal_opened
merchant_dashboard_opened
merchant_transaction_searched
merchant_refund_started
merchant_refund_completed
merchant_report_exported
merchant_product_created
merchant_inventory_adjusted
merchant_employee_invited
merchant_api_key_created
merchant_terminal_opened
merchant_support_ticket_created
```

---

# 139. Données analytics interdites

Ne pas transmettre :

- secret API ;
- PAN complet ;
- PIN ;
- CVV ;
- document KYB complet ;
- coordonnées bancaires complètes ;
- données client non nécessaires ;
- mot de passe ;
- OTP ;
- clé privée.

---

# 140. API principales

Exemples :

```http
GET    /merchant-portal/dashboard
GET    /merchant-portal/organizations
GET    /merchant-portal/stores
POST   /merchant-portal/stores
PATCH  /merchant-portal/stores/{id}

GET    /merchant-portal/employees
POST   /merchant-portal/employees/invite
PATCH  /merchant-portal/employees/{id}
POST   /merchant-portal/employees/{id}/suspend

GET    /merchant-portal/transactions
GET    /merchant-portal/transactions/{id}
POST   /merchant-portal/transactions/{id}/refund
POST   /merchant-portal/transactions/{id}/cancel

GET    /merchant-portal/settlements
GET    /merchant-portal/disputes
POST   /merchant-portal/disputes/{id}/evidence

GET    /merchant-portal/catalog/products
POST   /merchant-portal/catalog/products
PATCH  /merchant-portal/catalog/products/{id}

GET    /merchant-portal/inventory
POST   /merchant-portal/inventory/adjustments

GET    /merchant-portal/invoices
POST   /merchant-portal/invoices

GET    /merchant-portal/customers
GET    /merchant-portal/loyalty
GET    /merchant-portal/promotions

GET    /merchant-portal/terminals
GET    /merchant-portal/payment-links
POST   /merchant-portal/payment-links

GET    /merchant-portal/api-keys
POST   /merchant-portal/api-keys
POST   /merchant-portal/api-keys/{id}/rotate

GET    /merchant-portal/reports
POST   /merchant-portal/exports
GET    /merchant-portal/audit
```

---

# 141. Webhooks internes

Événements possibles :

```text
merchant.store.created
merchant.store.activated
merchant.employee.invited
merchant.employee.suspended
merchant.transaction.completed
merchant.transaction.refunded
merchant.settlement.completed
merchant.settlement.failed
merchant.dispute.created
merchant.product.created
merchant.inventory.low
merchant.invoice.created
merchant.invoice.paid
merchant.payment_link.paid
merchant.api_key.created
merchant.terminal.offline
merchant.security.alert.created
```

---

# 142. Modèles principaux

- MerchantOrganization
- MerchantBrand
- MerchantStore
- MerchantRegister
- MerchantEmployee
- MerchantRole
- MerchantPermission
- MerchantTransaction
- MerchantRefund
- MerchantSettlement
- MerchantSettlementAccount
- MerchantReconciliation
- MerchantDispute
- MerchantProduct
- MerchantCategory
- MerchantVariant
- MerchantInventory
- MerchantStockMovement
- MerchantSupplier
- MerchantOrder
- MerchantInvoice
- MerchantCreditNote
- MerchantCustomer
- MerchantSegment
- MerchantLoyaltyProgram
- MerchantPromotion
- MerchantCoupon
- MerchantPaymentLink
- MerchantQRCode
- MerchantAPIKey
- MerchantWebhook
- MerchantReport
- MerchantExport
- MerchantSupportTicket
- MerchantAudit

---

# 143. Administration centrale

L’administration Mansa doit pouvoir gérer :

- organisations ;
- points de vente ;
- employés ;
- rôles ;
- permissions ;
- transactions ;
- règlements ;
- remboursements ;
- litiges ;
- catalogues ;
- stocks ;
- factures ;
- clients ;
- fidélité ;
- promotions ;
- TPE ;
- API ;
- rapports ;
- documents ;
- support ;
- sécurité ;
- configurations ;
- audits.

---

# 144. Feature Flags

Exemples :

- multi-sites ;
- catalogue ;
- stock ;
- facturation ;
- fidélité ;
- promotions ;
- API ;
- e-commerce ;
- plugins ;
- Jini ;
- prévisions ;
- exports programmés ;
- litiges ;
- comptabilité.

---

# 145. Approbations

Peuvent nécessiter une approbation :

- remboursement important ;
- remboursement sans transaction ;
- changement de compte de règlement ;
- création de rôle administrateur ;
- création de clé API Production ;
- export massif ;
- changement de taxes ;
- correction de stock importante ;
- suppression de point de vente.

---

# 146. Double validation

Doit être exigée pour :

- correction financière ;
- changement de compte bancaire ;
- remboursement exceptionnel ;
- rotation de clé critique ;
- export de données sensibles ;
- modification de permissions Owner ;
- suppression d’une preuve ;
- déblocage après fraude critique ;
- modification massive du catalogue.

---

# 147. Reporting

Rapports possibles :

- chiffre d’affaires ;
- transactions ;
- paiements ;
- remboursements ;
- règlements ;
- frais ;
- commissions ;
- produits ;
- stocks ;
- commandes ;
- factures ;
- clients ;
- fidélité ;
- promotions ;
- TPE ;
- employés ;
- caisses ;
- taxes ;
- litiges ;
- API.

---

# 148. Indicateurs

Exemples :

- GMV ;
- net reçu ;
- taux de réussite ;
- panier moyen ;
- taux de remboursement ;
- délai de règlement ;
- produits les plus vendus ;
- magasins les plus performants ;
- stock immobilisé ;
- stock en rupture ;
- clients actifs ;
- taux de réachat ;
- usage fidélité ;
- performance promotionnelle ;
- disponibilité TPE.

---

# 149. Tests fonctionnels

- connexion ;
- MFA ;
- multi-sites ;
- employés ;
- rôles ;
- transactions ;
- recherche ;
- remboursement ;
- annulation ;
- règlement ;
- rapprochement ;
- catalogue ;
- stock ;
- facture ;
- client ;
- fidélité ;
- promotion ;
- TPE ;
- QR ;
- lien ;
- API ;
- export ;
- support.

---

# 150. Tests de sécurité

- session ;
- MFA ;
- permissions ;
- accès multi-organisation ;
- nouvel appareil ;
- export ;
- clé API ;
- secret ;
- webhook ;
- changement bancaire ;
- injection ;
- CSRF ;
- XSS ;
- tentative d’accès interdit ;
- audit.

---

# 151. Tests de performance

- tableau de bord ;
- liste de transactions ;
- recherche ;
- export massif ;
- import catalogue ;
- stock ;
- rapports ;
- multi-sites ;
- graphiques ;
- API ;
- webhooks.

---

# 152. Tests de résilience

- réseau faible ;
- timeout ;
- export interrompu ;
- import interrompu ;
- API indisponible ;
- webhook en échec ;
- service de paiement indisponible ;
- reprise ;
- cache ;
- erreur partielle.

---

# 153. Tests d’accessibilité

- clavier ;
- lecteur d’écran ;
- contraste ;
- focus ;
- formulaires ;
- erreurs ;
- tableaux ;
- graphiques ;
- modales ;
- navigation.

---

# 154. Règles métier

1. Toute transaction affichée provient d’une source financière validée.
2. Les rôles sont séparés.
3. Un utilisateur ne voit que les entités autorisées.
4. Chaque remboursement possède une référence.
5. Les remboursements élevés nécessitent une approbation.
6. Le changement de compte bancaire exige une authentification forte.
7. Les clés API sont séparées par environnement.
8. Les secrets API ne sont affichés qu’une fois.
9. Les webhooks sont signés.
10. Les exports sensibles sont contrôlés.
11. Les produits possèdent une référence unique dans leur périmètre.
12. Les mouvements de stock sont historisés.
13. Les factures ont une numérotation contrôlée.
14. Les promotions ont une période de validité.
15. Les employés peuvent être suspendus immédiatement.
16. Les TPE compromis sont bloqués.
17. Les frais et commissions sont transparents.
18. Les timeouts ne provoquent pas de double action.
19. Jini ne valide pas seul une action sensible.
20. Les données client sont minimisées.
21. Toute modification critique est auditée.
22. Les audits sont immuables.
23. Les fonctionnalités sont activables par pays.
24. Les fonctionnalités sont activables par offre.
25. Les règles financières restent administrables par Mansa selon les droits.

---

# 155. Critères d’acceptation

Le Portail Web Commerçant Mansa est validé lorsque :

- la connexion fonctionne ;
- le MFA est disponible ;
- les sessions sont gérées ;
- le tableau de bord est disponible ;
- les filtres multi-sites fonctionnent ;
- les entreprises sont gérées ;
- les hiérarchies commerciales sont supportées ;
- les points de vente sont gérés ;
- les horaires sont configurables ;
- les caisses sont visibles ;
- les sessions de caisse sont consultables ;
- les employés sont gérés ;
- les invitations expirent ;
- les rôles sont configurables ;
- les permissions sont appliquées ;
- les connexions sont historisées ;
- les transactions sont consultables ;
- la recherche avancée fonctionne ;
- les reçus sont accessibles ;
- les annulations sont contrôlées ;
- les remboursements sont gérés ;
- les seuils de remboursement sont configurables ;
- les litiges sont gérés ;
- les dossiers de litige acceptent des preuves ;
- les règlements sont consultables ;
- les fréquences de règlement sont supportables ;
- les comptes de règlement sont sécurisés ;
- les changements bancaires sont contrôlés ;
- le rapprochement est disponible ;
- les écarts sont visibles ;
- les frais sont transparents ;
- les simulations sont disponibles ;
- les factures Mansa sont disponibles ;
- le catalogue est géré ;
- les variantes sont supportées ;
- les catégories sont hiérarchiques ;
- les imports sont contrôlés ;
- les exports catalogue fonctionnent ;
- les prix avancés sont supportables ;
- les taxes sont configurables ;
- les remises sont gérées ;
- le stock est géré ;
- les mouvements sont historisés ;
- les alertes de stock fonctionnent ;
- les inventaires sont possibles ;
- les transferts de stock sont gérés ;
- les fournisseurs sont supportables ;
- les commandes sont gérées ;
- les statuts de commande sont suivis ;
- les factures clients sont gérées ;
- la numérotation est contrôlée ;
- les avoirs sont supportés ;
- la base client est disponible ;
- les données client sont minimisées ;
- la segmentation fonctionne ;
- la fidélité est configurable ;
- les récompenses sont gérées ;
- les promotions sont configurables ;
- les coupons sont supportés ;
- les liens de paiement sont créables ;
- les QR Codes sont administrables ;
- les TPE sont supervisés ;
- les actions à distance sont contrôlées ;
- les TPE hors ligne sont visibles ;
- la maintenance est suivie ;
- l’e-commerce est intégrable ;
- les plugins sont supportables ;
- l’API commerçant est disponible ;
- les clés API sont sécurisées ;
- les environnements sont séparés ;
- les webhooks sont signés ;
- les journaux webhook sont disponibles ;
- les rapports sont disponibles ;
- les exports sont disponibles ;
- les exports programmés sont supportables ;
- l’intégration comptable est supportable ;
- les analytics sont disponibles ;
- les comparaisons fonctionnent ;
- les prévisions sont présentées comme des estimations ;
- Jini est intégré ;
- Jini respecte les permissions ;
- le support est accessible ;
- les tickets sont suivis ;
- les incidents sont visibles ;
- les notifications sont configurables ;
- les alertes critiques restent obligatoires ;
- les documents sont centralisés ;
- les paramètres sont disponibles ;
- le branding est contrôlé ;
- les pages de paiement sont personnalisables ;
- le multi-langues est pris en charge ;
- le multi-devises est pris en charge ;
- l’accessibilité est intégrée ;
- le responsive design fonctionne ;
- le réseau faible est pris en charge ;
- les doubles actions sont empêchées ;
- les timeouts sont vérifiés ;
- les audits sont complets ;
- les analytics excluent les données sensibles ;
- les API sont définies ;
- les webhooks internes sont définis ;
- les modèles principaux sont définis ;
- les feature flags sont disponibles ;
- les approbations critiques sont protégées ;
- les rapports sont disponibles ;
- les indicateurs sont calculés ;
- les tests couvrent les fonctions, la sécurité, la performance, la résilience et l’accessibilité ;
- les audits sont immuables.
