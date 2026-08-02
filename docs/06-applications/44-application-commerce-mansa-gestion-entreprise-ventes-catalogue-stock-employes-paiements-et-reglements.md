# 44 — Application Commerce Mansa : gestion d’entreprise, ventes, catalogue, stock, employés, paiements et règlements

## 1. Objet du document

Ce document définit l’architecture officielle de l’application **Mansa Commerce**.

Il couvre :

- l’onboarding commerçant ;
- le KYB ;
- les entreprises ;
- les établissements ;
- les employés ;
- les rôles ;
- les caisses ;
- les produits ;
- les services ;
- les catégories ;
- le stock ;
- les ventes ;
- les paiements ;
- les remboursements ;
- les reçus ;
- les factures ;
- les devis ;
- les commandes ;
- les clients ;
- les promotions ;
- la fidélité ;
- les règlements ;
- les commissions ;
- les frais ;
- les abonnements ;
- les rapports ;
- les taxes ;
- le mini-site commerce ;
- le Hub ;
- les TPE associés ;
- le support ;
- Jini ;
- la sécurité ;
- le mode réseau faible ;
- l’administration ;
- les tests ;
- le multi-pays ;
- le multi-établissements.

L’objectif est de fournir une application professionnelle capable de servir :

- un petit commerçant ;
- une boutique ;
- un restaurant ;
- une pharmacie ;
- une station-service ;
- un supermarché ;
- un artisan ;
- un prestataire de services ;
- une PME ;
- une chaîne de magasins ;
- une organisation multi-sites.

---

# 2. Principes fondamentaux

## 2.1 Une seule application pour plusieurs types de commerces

Mansa Commerce ne doit pas être limitée :

- aux restaurants ;
- aux boutiques ;
- aux supermarchés ;
- à un seul secteur.

Elle doit être configurable selon :

- l’activité ;
- le pays ;
- la taille ;
- le nombre d’employés ;
- le nombre d’établissements ;
- les fonctionnalités activées ;
- les équipements disponibles.

---

## 2.2 Toute la logique financière officielle reste dans le backend

L’application ne doit pas calculer seule :

- les frais officiels ;
- les commissions ;
- les taxes ;
- les règlements ;
- les plafonds ;
- les droits ;
- les remboursements ;
- les soldes officiels ;
- les règles de fraude ;
- les décisions KYB.

---

## 2.3 Les données doivent être isolées par organisation

Un commerce ne doit jamais voir les données :

- d’un autre commerce ;
- d’un autre groupe ;
- d’un autre établissement non autorisé ;
- d’un autre pays ;
- d’un autre tenant.

---

## 2.4 Toutes les fonctions doivent être administrables

L’administration doit pouvoir configurer :

- modules ;
- menus ;
- rôles ;
- frais ;
- commissions ;
- taxes ;
- plafonds ;
- promotions ;
- règles ;
- pays ;
- langues ;
- fonctionnalités ;
- version minimale.

---

## 2.5 L’application doit servir autant le propriétaire que l’employé

L’interface doit s’adapter au rôle :

- propriétaire ;
- directeur ;
- responsable ;
- comptable ;
- vendeur ;
- caissier ;
- gestionnaire de stock ;
- support ;
- livreur ;
- auditeur.

---

# 3. Technologie

Technologie recommandée :

```text
React Native
TypeScript
```

L’application doit être disponible sur :

- Android ;
- iOS ;
- tablette lorsque nécessaire.

Une version web commerce peut compléter l’application mobile pour les usages plus avancés.

---

# 4. Architecture de l’application

Structure recommandée :

```text
src/
├── auth/
├── onboarding/
├── organization/
├── establishments/
├── employees/
├── dashboard/
├── sales/
├── payments/
├── refunds/
├── catalog/
├── inventory/
├── customers/
├── orders/
├── invoices/
├── quotations/
├── promotions/
├── loyalty/
├── settlements/
├── reports/
├── taxes/
├── subscriptions/
├── minisite/
├── hub/
├── terminals/
├── support/
├── jini/
├── settings/
├── security/
├── sync/
└── analytics/
```

---

# 5. Navigation principale

Navigation recommandée :

```text
Accueil
Ventes
Catalogue
Activité
Plus
```

Le menu peut varier selon le commerce.

Exemples d’onglets alternatifs :

```text
Accueil
Commandes
Stock
Clients
Profil
```

---

# 6. Onboarding commerçant

Le parcours doit pouvoir gérer :

1. création du compte ;
2. vérification du téléphone ;
3. identité du représentant ;
4. entreprise ;
5. type d’activité ;
6. registre ;
7. numéro fiscal ;
8. bénéficiaires effectifs ;
9. compte bancaire ;
10. établissements ;
11. documents ;
12. contrat ;
13. KYB ;
14. activation ;
15. configuration initiale.

---

# 7. Types d’organisation

Exemples :

- entreprise individuelle ;
- société ;
- association ;
- institution ;
- profession libérale ;
- franchise ;
- chaîne ;
- établissement public ;
- commerçant informel selon politique ;
- agent Mansa ;
- organisation partenaire.

---

# 8. Statuts du commerce

- DRAFT ;
- ONBOARDING ;
- KYB_PENDING ;
- INFORMATION_REQUIRED ;
- APPROVAL_PENDING ;
- ACTIVE ;
- LIMITED ;
- SUSPENDED ;
- BLOCKED ;
- TERMINATED ;
- ARCHIVED.

---

# 9. Dossier commerce

Le dossier doit contenir :

- identité légale ;
- nom commercial ;
- secteur ;
- pays ;
- adresse ;
- contacts ;
- registre ;
- fiscalité ;
- bénéficiaires effectifs ;
- dirigeants ;
- établissements ;
- comptes ;
- documents ;
- contrats ;
- statuts ;
- risques ;
- incidents ;
- audit.

---

# 10. Tableau de bord

L’écran d’accueil doit afficher selon le rôle :

- chiffre d’affaires du jour ;
- nombre de ventes ;
- paiements reçus ;
- remboursements ;
- règlements attendus ;
- stock faible ;
- commandes en attente ;
- meilleures ventes ;
- commissions ;
- frais ;
- alertes ;
- TPE actifs ;
- employés connectés ;
- activité récente.

---

# 11. Widgets configurables

Exemples :

- ventes du jour ;
- ventes de la semaine ;
- panier moyen ;
- produit le plus vendu ;
- stock critique ;
- paiements échoués ;
- règlements ;
- factures impayées ;
- commissions ;
- promotions ;
- nouveaux clients ;
- objectifs.

---

# 12. Multi-établissements

Une organisation peut gérer :

- siège ;
- boutiques ;
- agences ;
- entrepôts ;
- restaurants ;
- points mobiles ;
- caisses ;
- succursales ;
- dépôts ;
- franchises.

Chaque établissement doit avoir :

- nom ;
- adresse ;
- horaires ;
- responsable ;
- employés ;
- caisses ;
- stock ;
- TPE ;
- règles ;
- compte de règlement ;
- statut.

---

# 13. Changement d’établissement

L’utilisateur doit pouvoir changer d’établissement selon ses permissions.

Le contexte actif doit être visible en permanence.

---

# 14. Employés

Le propriétaire ou un administrateur autorisé peut :

- inviter ;
- activer ;
- suspendre ;
- désactiver ;
- affecter ;
- modifier ;
- révoquer ;
- consulter l’activité.

---

# 15. Rôles employés

Exemples :

- OWNER ;
- ADMIN ;
- MANAGER ;
- ACCOUNTANT ;
- CASHIER ;
- SELLER ;
- INVENTORY_MANAGER ;
- SUPPORT ;
- AUDITOR ;
- DELIVERY ;
- VIEWER.

---

# 16. Permissions

Exemples :

```text
commerce.dashboard.read
commerce.sale.create
commerce.sale.cancel
commerce.refund.request
commerce.refund.approve
commerce.catalog.read
commerce.catalog.manage
commerce.inventory.read
commerce.inventory.manage
commerce.employee.read
commerce.employee.manage
commerce.invoice.create
commerce.settlement.read
commerce.report.read
commerce.settings.manage
```

---

# 17. Gestion des horaires employés

Le système peut gérer :

- planning ;
- heure d’arrivée ;
- heure de départ ;
- point de vente ;
- pauses ;
- retard ;
- absence ;
- session ;
- activité de caisse.

Cette fonction doit rester configurable.

---

# 18. Ouverture de session employé

Méthodes possibles :

- PIN ;
- mot de passe ;
- biométrie ;
- badge ;
- carte employé ;
- QR ;
- appareil autorisé.

---

# 19. Gestion des caisses

Chaque caisse doit contenir :

- établissement ;
- appareil ;
- employé ;
- session ;
- montant d’ouverture ;
- ventes ;
- remboursements ;
- espèces ;
- paiements électroniques ;
- écart ;
- fermeture ;
- statut.

---

# 20. Ouverture de caisse

L’employé doit pouvoir saisir :

- montant initial ;
- coupures ;
- date ;
- heure ;
- caisse ;
- appareil ;
- commentaire ;
- validation éventuelle.

---

# 21. Fermeture de caisse

Le système doit calculer :

- ventes théoriques ;
- remboursements ;
- espèces attendues ;
- espèces réelles ;
- paiements numériques ;
- écarts ;
- commissions ;
- total ;
- rapport de clôture.

---

# 22. Vente rapide

Le commerce doit pouvoir enregistrer une vente par :

- montant libre ;
- produit ;
- service ;
- catalogue ;
- code-barres ;
- QR ;
- commande ;
- facture ;
- devis accepté.

---

# 23. Écran de vente

Afficher :

- produits ;
- quantités ;
- prix ;
- remises ;
- taxes ;
- frais ;
- total ;
- client ;
- vendeur ;
- établissement ;
- moyen de paiement ;
- note ;
- bouton encaisser.

---

# 24. Moyens de paiement

L’application peut accepter :

- wallet Mansa ;
- QR Mansa ;
- carte ;
- TPE ;
- Mobile Money ;
- virement ;
- espèces ;
- paiement mixte ;
- lien de paiement ;
- crédit autorisé ;
- bon ;
- service public lorsque pertinent.

---

# 25. Paiement mixte

Une vente peut être réglée par plusieurs moyens.

Exemple :

```text
Total : 50 000 XOF
Espèces : 20 000 XOF
Carte : 15 000 XOF
Mansa : 15 000 XOF
```

Chaque part doit être tracée séparément.

---

# 26. Paiement partagé

Pour les restaurants ou groupes :

- division égale ;
- division par article ;
- division manuelle ;
- plusieurs moyens ;
- suivi des parts ;
- clôture partielle ;
- reste à payer.

Cette fonctionnalité ne doit pas être limitée aux restaurants.

---

# 27. Vente en attente

Une vente peut être :

- sauvegardée ;
- reprise ;
- transférée à un autre employé ;
- annulée ;
- fusionnée ;
- divisée ;
- transformée en facture.

---

# 28. Statuts de vente

- DRAFT ;
- OPEN ;
- PAYMENT_PENDING ;
- PARTIALLY_PAID ;
- PAID ;
- FAILED ;
- CANCELLED ;
- REFUNDED ;
- PARTIALLY_REFUNDED ;
- DISPUTED.

---

# 29. Reçu de vente

Il doit contenir :

- référence ;
- commerce ;
- établissement ;
- vendeur ;
- date ;
- articles ;
- quantité ;
- prix ;
- remises ;
- taxes ;
- frais ;
- total ;
- paiements ;
- statut ;
- QR de vérification ;
- coordonnées ;
- politique de retour.

---

# 30. Reçu numérique

Le client peut recevoir son reçu par :

- application ;
- SMS ;
- e-mail ;
- QR ;
- impression ;
- lien sécurisé.

---

# 31. Remboursement

Types :

- total ;
- partiel ;
- par article ;
- commercial ;
- technique ;
- erreur ;
- retour produit ;
- annulation de service.

---

# 32. Parcours de remboursement

1. retrouver la vente ;
2. vérifier l’éligibilité ;
3. sélectionner le montant ou les articles ;
4. choisir le motif ;
5. vérifier les permissions ;
6. demander une approbation si nécessaire ;
7. exécuter ;
8. générer le reçu ;
9. mettre à jour le stock ;
10. notifier le client.

---

# 33. Règles de remboursement

Elles peuvent dépendre :

- du commerce ;
- du produit ;
- du délai ;
- de l’état ;
- du moyen de paiement ;
- du montant ;
- du rôle ;
- du pays ;
- du risque ;
- de la politique de retour.

---

# 34. Catalogue

Le catalogue doit gérer :

- produits ;
- services ;
- variantes ;
- catégories ;
- collections ;
- options ;
- suppléments ;
- unités ;
- prix ;
- taxes ;
- images ;
- codes-barres ;
- disponibilité ;
- établissements.

---

# 35. Produit

Un produit peut contenir :

- nom ;
- description ;
- référence ;
- SKU ;
- code-barres ;
- catégorie ;
- prix ;
- coût ;
- taxe ;
- unité ;
- images ;
- stock ;
- variantes ;
- fournisseur ;
- statut ;
- points fidélité.

---

# 36. Service

Un service peut contenir :

- nom ;
- durée ;
- prix ;
- employé ;
- calendrier ;
- réservation ;
- conditions ;
- lieu ;
- capacité ;
- taxes ;
- disponibilité.

---

# 37. Variantes

Exemples :

- taille ;
- couleur ;
- poids ;
- format ;
- matière ;
- parfum ;
- modèle ;
- niveau ;
- durée.

---

# 38. Options et suppléments

Exemples :

- accompagnement ;
- livraison ;
- emballage ;
- personnalisation ;
- ajout ;
- retrait d’un composant ;
- garantie ;
- priorité.

---

# 39. Prix

Le système doit gérer :

- prix de vente ;
- prix de revient ;
- prix promotionnel ;
- prix par établissement ;
- prix par segment ;
- prix par volume ;
- prix horaire ;
- prix saisonnier ;
- prix en plusieurs devises.

---

# 40. Aucun prix critique codé en dur

Les prix doivent être administrables.

Le backend doit valider :

- prix autorisé ;
- remise ;
- taxe ;
- minimum ;
- maximum ;
- période ;
- établissement ;
- rôle.

---

# 41. Gestion du stock

Le stock doit gérer :

- quantité disponible ;
- quantité réservée ;
- quantité en commande ;
- quantité endommagée ;
- quantité retournée ;
- quantité en transfert ;
- seuil minimum ;
- seuil maximum ;
- emplacement ;
- lot ;
- expiration.

---

# 42. Mouvements de stock

Types :

- entrée ;
- vente ;
- retour ;
- transfert ;
- correction ;
- perte ;
- vol ;
- casse ;
- expiration ;
- production ;
- réception fournisseur ;
- inventaire.

---

# 43. Inventaire

Le commerce doit pouvoir :

- lancer un inventaire ;
- scanner ;
- compter ;
- comparer ;
- corriger ;
- justifier ;
- valider ;
- produire un rapport.

---

# 44. Stock multi-sites

Le stock doit pouvoir être séparé par :

- établissement ;
- entrepôt ;
- caisse ;
- véhicule ;
- dépôt ;
- zone ;
- rayon.

---

# 45. Transfert de stock

Un transfert doit contenir :

- origine ;
- destination ;
- produits ;
- quantités ;
- responsable ;
- date ;
- statut ;
- réception ;
- écart ;
- preuve.

---

# 46. Alertes de stock

Exemples :

- stock faible ;
- rupture ;
- surstock ;
- produit expirant ;
- anomalie ;
- écart d’inventaire ;
- vente sans stock ;
- mouvement inhabituel.

---

# 47. Commandes

Types :

- commande comptoir ;
- commande en ligne ;
- commande téléphonique ;
- commande Hub ;
- commande livrée ;
- commande à emporter ;
- commande fournisseur ;
- réservation.

---

# 48. Statuts de commande

- DRAFT ;
- CONFIRMED ;
- PREPARING ;
- READY ;
- IN_DELIVERY ;
- DELIVERED ;
- COMPLETED ;
- CANCELLED ;
- REFUNDED ;
- DISPUTED.

---

# 49. Gestion des tables

Pour les restaurants et établissements similaires :

- tables ;
- zones ;
- couverts ;
- serveurs ;
- commandes ;
- division ;
- transfert de table ;
- fusion ;
- clôture.

Cette fonction doit être activable uniquement pour les secteurs concernés.

---

# 50. Devis

Le commerce doit pouvoir créer :

- devis simple ;
- devis détaillé ;
- devis avec validité ;
- devis avec acompte ;
- devis avec signature ;
- devis transformable en facture.

---

# 51. Factures

Types :

- facture simple ;
- facture pro forma ;
- facture finale ;
- facture récurrente ;
- facture d’acompte ;
- avoir ;
- facture électronique.

---

# 52. Numérotation des factures

Elle doit être :

- unique ;
- séquentielle selon règle ;
- configurable par pays ;
- configurable par établissement ;
- non modifiable après émission ;
- auditée.

---

# 53. Contenu d’une facture

- vendeur ;
- client ;
- références légales ;
- articles ;
- quantités ;
- prix ;
- remises ;
- taxes ;
- total HT ;
- total taxes ;
- total TTC ;
- paiements ;
- date ;
- échéance ;
- statut ;
- signature ;
- QR éventuel.

---

# 54. Clients

Le commerce peut gérer :

- clients particuliers ;
- entreprises ;
- contacts ;
- historique ;
- préférences ;
- fidélité ;
- factures ;
- commandes ;
- crédit ;
- notes autorisées ;
- consentements.

---

# 55. Fiche client

Elle peut afficher :

- nom ;
- téléphone ;
- e-mail ;
- historique ;
- total dépensé ;
- commandes ;
- factures ;
- points ;
- préférences ;
- statut ;
- consentement marketing.

---

# 56. Crédit client

Lorsque autorisé, le commerce peut gérer :

- plafond ;
- solde dû ;
- échéance ;
- factures ;
- paiements ;
- relances ;
- blocage ;
- historique.

---

# 57. Promotions

Types :

- pourcentage ;
- montant fixe ;
- deuxième produit offert ;
- lot ;
- coupon ;
- code promo ;
- remise par volume ;
- happy hour ;
- segment ;
- établissement ;
- anniversaire ;
- fidélité.

---

# 58. Conditions promotionnelles

Elles peuvent dépendre :

- date ;
- heure ;
- produit ;
- catégorie ;
- panier minimum ;
- quantité ;
- client ;
- fidélité ;
- établissement ;
- pays ;
- moyen de paiement ;
- stock.

---

# 59. Fidélité

Le commerce peut créer :

- points ;
- cashback ;
- tampons ;
- niveaux ;
- statuts ;
- récompenses ;
- avantages ;
- coupons ;
- cartes de fidélité.

---

# 60. Carte de fidélité

Elle peut être :

- numérique ;
- intégrée à Mansa ;
- liée au profil ;
- liée au commerce ;
- visible dans l’application Client ;
- utilisable par QR ;
- administrable.

---

# 61. Mini-site commerce

Chaque commerce peut disposer d’un mini-site contenant :

- nom ;
- logo ;
- description ;
- photos ;
- horaires ;
- adresse ;
- contact ;
- catalogue ;
- promotions ;
- avis ;
- paiement ;
- commande ;
- réservation ;
- réseaux sociaux.

---

# 62. Hub / Annuaire

Le commerce peut gérer sa présence dans le Hub :

- catégorie ;
- localisation ;
- images ;
- description ;
- offres ;
- produits ;
- horaires ;
- mise en avant ;
- contact ;
- visibilité ;
- badge vérifié.

---

# 63. Mise en avant

Options possibles :

- profil premium ;
- produit sponsorisé ;
- promotion à la une ;
- position locale ;
- bannière ;
- campagne ;
- recommandation ;
- catégorie prioritaire.

Les règles doivent être transparentes et administrables.

---

# 64. Avis clients

Le système peut permettre :

- note ;
- commentaire ;
- réponse commerce ;
- signalement ;
- modération ;
- vérification d’achat ;
- classement.

---

# 65. Règlements

Le commerce doit voir :

- ventes brutes ;
- remboursements ;
- frais ;
- commissions ;
- taxes ;
- réserves ;
- ajustements ;
- montant net ;
- date prévue ;
- statut ;
- compte de destination.

---

# 66. Statuts de règlement

- CALCULATED ;
- PENDING ;
- APPROVED ;
- SUBMITTED ;
- PAID ;
- PARTIALLY_PAID ;
- FAILED ;
- HELD ;
- RECONCILIATION_REQUIRED ;
- CANCELLED.

---

# 67. Calendrier de règlement

Il peut être :

- instantané ;
- quotidien ;
- hebdomadaire ;
- mensuel ;
- personnalisé ;
- déclenché à partir d’un seuil ;
- soumis à réserve.

---

# 68. Compte de règlement

Le commerce peut choisir selon les règles :

- wallet Mansa ;
- compte bancaire ;
- Mobile Money ;
- compte partenaire ;
- autre canal approuvé.

---

# 69. Frais et commissions

L’application doit afficher :

- frais par vente ;
- frais par moyen ;
- commissions ;
- abonnements ;
- frais TPE ;
- frais de remboursement ;
- frais de règlement ;
- taxes ;
- part Mansa ;
- part partenaire lorsque visible.

---

# 70. Gestion dynamique

Aucune valeur ne doit être codée en dur.

Les règles peuvent varier selon :

- pays ;
- commerce ;
- secteur ;
- établissement ;
- volume ;
- montant ;
- moyen ;
- contrat ;
- abonnement ;
- période ;
- promotion ;
- risque ;
- partenaire.

---

# 71. Abonnements commerce

Plans possibles :

- gratuit ;
- starter ;
- standard ;
- premium ;
- entreprise ;
- institutionnel ;
- personnalisé.

---

# 72. Fonctions par abonnement

Exemples :

- nombre d’employés ;
- nombre d’établissements ;
- nombre de produits ;
- rapports ;
- mini-site ;
- promotions ;
- fidélité ;
- API ;
- support prioritaire ;
- gestion avancée du stock ;
- multi-caisse ;
- facturation avancée.

---

# 73. Rapports

Rapports possibles :

- ventes ;
- produits ;
- employés ;
- établissements ;
- paiements ;
- remboursements ;
- règlements ;
- commissions ;
- stock ;
- clients ;
- promotions ;
- fidélité ;
- taxes ;
- rentabilité ;
- commandes ;
- factures.

---

# 74. Rapport de rentabilité

Le système peut calculer :

- chiffre d’affaires ;
- coût des produits ;
- marge brute ;
- remises ;
- frais ;
- commissions ;
- remboursements ;
- taxes ;
- marge estimée.

---

# 75. Export

Formats possibles :

- PDF ;
- CSV ;
- XLSX ;
- JSON ;
- impression.

Les exports sensibles doivent être autorisés et audités.

---

# 76. Taxes

Le système doit gérer :

- TVA ;
- taxes locales ;
- taxes sectorielles ;
- exonérations ;
- taux ;
- dates d’effet ;
- pays ;
- règles d’arrondi ;
- affichage sur facture.

---

# 77. TPE associés

Le commerce doit pouvoir consulter :

- terminaux ;
- statut ;
- établissement ;
- employé ;
- dernière activité ;
- version ;
- batterie ;
- connexion ;
- paiements ;
- incidents ;
- maintenance.

---

# 78. Gestion TPE

Actions possibles selon permission :

- affecter ;
- activer ;
- suspendre ;
- renommer ;
- déplacer ;
- mettre à jour ;
- signaler une panne ;
- demander un remplacement ;
- consulter les journaux.

---

# 79. Jini Commerce

Jini peut aider à :

- expliquer les ventes ;
- résumer la journée ;
- identifier les produits les plus vendus ;
- expliquer un règlement ;
- signaler un stock faible ;
- préparer un rapport ;
- créer un brouillon de promotion ;
- retrouver une facture ;
- orienter vers le support.

---

# 80. Limites de Jini

Jini ne doit pas seul :

- rembourser ;
- modifier un prix critique ;
- changer un compte bancaire ;
- ajouter un administrateur ;
- clôturer un écart ;
- changer les commissions ;
- supprimer une preuve ;
- valider un KYB.

---

# 81. Notifications

Types :

- vente ;
- paiement ;
- remboursement ;
- règlement ;
- stock ;
- commande ;
- facture ;
- employé ;
- sécurité ;
- TPE ;
- promotion ;
- support ;
- système.

---

# 82. Notifications de sécurité

Exemples :

- nouvelle connexion ;
- nouvel administrateur ;
- changement de compte bancaire ;
- remboursement important ;
- fermeture inhabituelle ;
- appareil inconnu ;
- TPE déplacé ;
- changement de rôle.

---

# 83. Support

Le commerçant doit pouvoir :

- consulter le centre d’aide ;
- parler à Jini ;
- créer un ticket ;
- joindre des preuves ;
- sélectionner une vente ;
- sélectionner un TPE ;
- suivre un incident ;
- contester un règlement ;
- demander une intervention.

---

# 84. Mode réseau faible

L’application doit prévoir :

- cache ;
- chargement progressif ;
- synchronisation ;
- reprise ;
- compression ;
- file locale ;
- historique récent ;
- états clairs ;
- reçus différés.

---

# 85. Mode hors ligne

Le mode hors ligne peut permettre :

- consultation du catalogue ;
- préparation d’une vente ;
- lecture du stock local ;
- création de commande ;
- saisie d’inventaire ;
- ouverture d’un incident.

Une vente financière ne doit pas être affichée comme payée sans confirmation du backend ou du TPE autorisé.

---

# 86. Synchronisation

À la reconnexion :

- vérifier les statuts ;
- envoyer les opérations autorisées ;
- détecter les doublons ;
- appliquer l’idempotence ;
- résoudre les conflits ;
- mettre à jour le stock ;
- récupérer les reçus ;
- informer l’utilisateur.

---

# 87. Sécurité

Mesures possibles :

- appareil enregistré ;
- biométrie ;
- PIN ;
- MFA ;
- session ;
- rôles ;
- permissions ;
- chiffrement ;
- masquage ;
- détection root ;
- verrouillage ;
- audit ;
- géolocalisation selon politique.

---

# 88. Stockage local

Ne pas stocker en clair :

- mots de passe ;
- PIN ;
- OTP ;
- CVV ;
- numéro complet de carte ;
- secrets ;
- documents ;
- données bancaires complètes ;
- tokens non protégés.

---

# 89. Multi-pays

Chaque pays peut avoir :

- devise ;
- taxes ;
- facturation ;
- moyens de paiement ;
- règles KYB ;
- règles de remboursement ;
- formats de reçus ;
- langues ;
- partenaires ;
- plafonds ;
- abonnements.

---

# 90. Multi-langues

L’application doit être préparée pour :

- français ;
- bambara ;
- anglais ;
- langues régionales ;
- langues des futurs pays.

---

# 91. Accessibilité

L’application doit prendre en charge :

- gros boutons ;
- lecteur d’écran ;
- contraste ;
- taille de texte ;
- navigation simple ;
- tablettes ;
- mode paysage ;
- réduction des animations ;
- langage clair.

---

# 92. Feature Flags

Fonctions activables :

- stock ;
- factures ;
- fidélité ;
- mini-site ;
- commandes ;
- tables ;
- devis ;
- crédits clients ;
- multi-établissements ;
- Jini ;
- Hub ;
- livraison ;
- abonnements.

---

# 93. Administration centrale

Le portail Admin doit pouvoir gérer :

- commerces ;
- KYB ;
- établissements ;
- abonnements ;
- plafonds ;
- frais ;
- commissions ;
- taxes ;
- secteurs ;
- rôles ;
- TPE ;
- règlements ;
- promotions ;
- visibilité Hub ;
- incidents ;
- versions ;
- feature flags.

---

# 94. Actions critiques

Doivent être protégées :

- changement de compte de règlement ;
- remboursement élevé ;
- ajout d’un administrateur ;
- modification de rôle ;
- export massif ;
- correction de caisse ;
- annulation de facture ;
- modification globale de prix ;
- désactivation d’un établissement ;
- transfert de propriété.

---

# 95. Double validation

Peut être exigée pour :

- changement bancaire ;
- remboursement important ;
- suppression d’un administrateur principal ;
- transfert de propriété ;
- modification de règle fiscale ;
- correction financière ;
- clôture de caisse avec gros écart ;
- activation d’une API sensible ;
- export financier complet.

---

# 96. API

Exemples :

```http
POST   /merchants
GET    /merchants/{id}
PATCH  /merchants/{id}

GET    /merchant/establishments
POST   /merchant/establishments
GET    /merchant/employees
POST   /merchant/employees

POST   /merchant/sales
GET    /merchant/sales
GET    /merchant/sales/{id}
POST   /merchant/sales/{id}/refund

GET    /merchant/products
POST   /merchant/products
PATCH  /merchant/products/{id}

GET    /merchant/inventory
POST   /merchant/inventory/movements
POST   /merchant/inventory/counts

POST   /merchant/orders
GET    /merchant/orders

POST   /merchant/invoices
GET    /merchant/invoices

GET    /merchant/settlements
GET    /merchant/reports
GET    /merchant/terminals
```

---

# 97. Modèles

- Merchant
- MerchantLegalEntity
- MerchantBeneficialOwner
- MerchantEstablishment
- MerchantEmployee
- MerchantRole
- MerchantPermission
- MerchantCashRegister
- MerchantCashSession
- Product
- ProductVariant
- ProductCategory
- Service
- InventoryItem
- InventoryMovement
- InventoryCount
- Sale
- SaleItem
- SalePayment
- Refund
- Customer
- Order
- Invoice
- InvoiceLine
- Quotation
- Promotion
- LoyaltyProgram
- LoyaltyAccount
- Settlement
- MerchantSubscription
- MerchantMiniSite
- MerchantTerminal
- MerchantAudit

---

# 98. Analytics

Événements possibles :

```text
merchant_onboarding_started
merchant_activated
merchant_establishment_created
merchant_employee_invited
merchant_sale_started
merchant_sale_completed
merchant_refund_requested
merchant_refund_completed
merchant_product_created
merchant_inventory_low
merchant_inventory_count_completed
merchant_order_created
merchant_invoice_created
merchant_settlement_completed
merchant_promotion_created
merchant_loyalty_reward_earned
merchant_terminal_assigned
merchant_support_ticket_created
```

---

# 99. Tests

- tests onboarding ;
- tests KYB ;
- tests multi-tenant ;
- tests établissements ;
- tests employés ;
- tests permissions ;
- tests caisses ;
- tests ventes ;
- tests paiement mixte ;
- tests paiement partagé ;
- tests remboursements ;
- tests catalogue ;
- tests variantes ;
- tests stock ;
- tests inventaire ;
- tests commandes ;
- tests factures ;
- tests devis ;
- tests promotions ;
- tests fidélité ;
- tests règlements ;
- tests abonnements ;
- tests mini-site ;
- tests Hub ;
- tests TPE ;
- tests mode faible connexion ;
- tests synchronisation ;
- tests multi-pays ;
- tests multi-langues ;
- tests sécurité ;
- tests accessibilité ;
- tests audit.

---

# 100. Règles métier

1. Chaque commerce appartient à un tenant.
2. Chaque établissement possède son propre périmètre.
3. Les employés possèdent des rôles limités.
4. Les caisses sont ouvertes et fermées avec traçabilité.
5. Toute vente possède une référence.
6. Les paiements sont confirmés par le backend ou un terminal autorisé.
7. Les ventes peuvent être partiellement payées.
8. Les paiements mixtes sont séparés par moyen.
9. Les remboursements référencent la vente d’origine.
10. Le stock est mis à jour par des mouvements.
11. Les corrections de stock sont justifiées.
12. Les factures validées ne sont pas modifiées silencieusement.
13. Les prix sont administrables.
14. Les taxes sont configurables par pays.
15. Les promotions sont versionnées.
16. Les règlements sont calculés par le backend.
17. Les frais ne sont pas codés en dur.
18. Les commissions sont traçables.
19. Les données client sont limitées au besoin.
20. Le mode hors ligne ne confirme pas librement un paiement.
21. La synchronisation est idempotente.
22. Jini reste soumis aux permissions.
23. Les exports sensibles sont audités.
24. Les TPE sont liés à un établissement.
25. Les actions critiques peuvent exiger une double validation.

---

# 101. Critères d’acceptation

L’application Mansa Commerce est validée lorsque :

- le commerce peut être onboardé ;
- le KYB est géré ;
- les établissements sont administrables ;
- les employés et rôles sont configurables ;
- les caisses sont suivies ;
- les ventes fonctionnent ;
- les paiements mixtes sont pris en charge ;
- les paiements partagés fonctionnent ;
- les remboursements sont contrôlés ;
- le catalogue est complet ;
- le stock est traçable ;
- les inventaires sont disponibles ;
- les commandes sont gérées ;
- les factures et devis sont disponibles ;
- les promotions sont configurables ;
- la fidélité est intégrée ;
- les règlements sont visibles ;
- les commissions et frais sont détaillés ;
- les abonnements sont administrables ;
- le mini-site est disponible ;
- le Hub est intégré ;
- les TPE associés sont visibles ;
- le support et Jini sont intégrés ;
- le réseau faible est pris en charge ;
- les actions sensibles sont protégées ;
- les tests couvrent les parcours critiques.
