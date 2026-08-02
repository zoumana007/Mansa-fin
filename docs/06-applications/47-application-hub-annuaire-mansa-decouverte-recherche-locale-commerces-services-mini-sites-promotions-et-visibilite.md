# 47 — Application Hub & Annuaire Mansa : découverte, recherche locale, commerces, services, mini-sites, promotions et visibilité

## 1. Objet du document

Ce document définit l’architecture officielle de l’application **Mansa Hub & Annuaire**.

Le Hub est l’espace de découverte de l’écosystème Mansa.

Il permet aux utilisateurs de rechercher, découvrir et contacter :

- des commerces ;
- des restaurants ;
- des pharmacies ;
- des artisans ;
- des prestataires ;
- des écoles ;
- des professionnels ;
- des transports ;
- des services publics ;
- des agents Mansa ;
- des distributeurs automatiques ;
- des offres ;
- des promotions ;
- des événements ;
- des points de service.

Il couvre :

- la recherche ;
- la géolocalisation ;
- les catégories ;
- les fiches professionnelles ;
- les mini-sites ;
- les catalogues ;
- les produits ;
- les services ;
- les promotions ;
- les avis ;
- les favoris ;
- les recommandations ;
- les abonnements professionnels ;
- la mise en avant ;
- les campagnes sponsorisées ;
- les réservations ;
- les commandes ;
- les paiements ;
- les itinéraires ;
- les contacts ;
- la modération ;
- la vérification des profils ;
- les statistiques ;
- la sécurité ;
- le mode réseau faible ;
- le multi-pays ;
- le multi-langues ;
- l’administration ;
- les tests.

L’objectif est de construire un annuaire moderne capable de :

- donner de la visibilité aux professionnels ;
- faciliter la découverte locale ;
- connecter les clients et les commerces ;
- générer du trafic vers les services Mansa ;
- permettre le paiement directement depuis une fiche ;
- fonctionner comme un véritable moteur de recherche économique local ;
- évoluer vers plusieurs villes, pays et secteurs.

---

# 2. Principes fondamentaux

## 2.1 Le Hub est indépendant mais connecté

Le Hub doit pouvoir exister comme :

- module dans l’application Client ;
- application mobile indépendante ;
- site web public ;
- moteur de recherche interne ;
- API pour partenaires.

Il reste connecté à :

- Mansa Client ;
- Mansa Commerce ;
- Mansa Agent ;
- Mansa TPE ;
- Mansa Admin ;
- Jini ;
- les services publics ;
- les partenaires.

---

## 2.2 Aucun commerce n’est favorisé arbitrairement

La visibilité doit être fondée sur des règles administrables et explicables.

Elle peut dépendre :

- de la proximité ;
- de la pertinence ;
- de la disponibilité ;
- de la vérification ;
- de la qualité du profil ;
- des avis ;
- du paiement Mansa ;
- d’un abonnement ;
- d’une campagne sponsorisée ;
- d’une promotion ;
- du contexte de recherche.

---

## 2.3 Les résultats sponsorisés doivent être identifiés

Toute mise en avant payante doit être clairement distinguée.

Exemples :

- Sponsorisé ;
- À la une ;
- Promotion ;
- Partenaire ;
- Recommandé par Mansa.

---

## 2.4 Les données doivent être administrables

L’administration doit pouvoir configurer :

- catégories ;
- secteurs ;
- filtres ;
- villes ;
- zones ;
- règles de classement ;
- abonnements ;
- promotions ;
- campagnes ;
- badges ;
- modération ;
- langues ;
- contenus ;
- visibilité ;
- limites.

---

## 2.5 Le Hub doit fonctionner sur réseau faible

Il doit prévoir :

- listes légères ;
- compression ;
- cache ;
- images optimisées ;
- pagination ;
- recherche locale ;
- reprise ;
- géolocalisation facultative ;
- affichage textuel alternatif.

---

# 3. Technologie

Technologie recommandée :

```text
React Native
TypeScript
```

Pour le site web public :

```text
Next.js
TypeScript
```

Le backend doit exposer des APIs dédiées au Hub.

---

# 4. Architecture fonctionnelle

Structure recommandée :

```text
src/
├── auth/
├── home/
├── search/
├── categories/
├── directory/
├── businesses/
├── professionals/
├── products/
├── services/
├── promotions/
├── recommendations/
├── favorites/
├── reviews/
├── reservations/
├── orders/
├── payments/
├── maps/
├── agents/
├── atms/
├── public-services/
├── minisites/
├── subscriptions/
├── campaigns/
├── notifications/
├── support/
├── jini/
├── settings/
├── moderation/
├── analytics/
└── security/
```

---

# 5. Navigation principale

Navigation recommandée :

```text
Accueil
Explorer
Carte
Favoris
Profil
```

Autres variantes possibles :

```text
Accueil
Catégories
Promotions
Autour de moi
Compte
```

La navigation doit rester configurable.

---

# 6. Accueil du Hub

L’accueil peut afficher :

- barre de recherche ;
- catégories populaires ;
- commerces proches ;
- promotions ;
- services recommandés ;
- agents Mansa ;
- DAB proches ;
- nouveautés ;
- profils vérifiés ;
- événements ;
- services publics ;
- suggestions Jini ;
- campagnes sponsorisées.

---

# 7. Barre de recherche

La recherche doit accepter :

- nom ;
- activité ;
- produit ;
- service ;
- profession ;
- marque ;
- catégorie ;
- quartier ;
- ville ;
- mot-clé ;
- besoin exprimé en langage naturel.

Exemples :

```text
restaurant ouvert près de moi
pharmacie de garde
maçon à Bamako
boutique qui accepte Mansa
agent pour retirer de l’argent
```

---

# 8. Recherche intelligente

Le moteur peut utiliser :

- recherche textuelle ;
- synonymes ;
- tolérance aux fautes ;
- recherche phonétique ;
- géolocalisation ;
- historique ;
- popularité ;
- préférences ;
- disponibilité ;
- recherche sémantique ;
- suggestions Jini.

---

# 9. Catégories

Exemples :

- alimentation ;
- restaurants ;
- santé ;
- pharmacie ;
- transport ;
- logement ;
- construction ;
- éducation ;
- beauté ;
- services professionnels ;
- artisanat ;
- commerce ;
- agriculture ;
- finance ;
- technologie ;
- administration ;
- loisirs ;
- tourisme ;
- événements ;
- agents Mansa ;
- distributeurs.

---

# 10. Sous-catégories

Une catégorie peut contenir plusieurs niveaux.

Exemple :

```text
Construction
├── Maçonnerie
├── Électricité
├── Plomberie
├── Peinture
├── Menuiserie
├── Carrelage
└── Bureau d’études
```

---

# 11. Filtres

Filtres possibles :

- proximité ;
- ville ;
- quartier ;
- ouvert maintenant ;
- vérifié ;
- note ;
- prix ;
- paiement Mansa ;
- livraison ;
- réservation ;
- promotion ;
- accessible ;
- disponible ;
- secteur ;
- type d’établissement ;
- distance ;
- langue ;
- horaire ;
- service à domicile.

---

# 12. Tri

Options possibles :

- pertinence ;
- proximité ;
- mieux noté ;
- plus populaire ;
- nouveau ;
- promotion ;
- prix croissant ;
- prix décroissant ;
- ouvert maintenant ;
- disponibilité.

---

# 13. Carte

La carte doit pouvoir afficher :

- commerces ;
- professionnels ;
- agents ;
- DAB ;
- services publics ;
- événements ;
- promotions ;
- zones couvertes ;
- itinéraires ;
- regroupements de points.

---

# 14. Géolocalisation

L’utilisateur doit pouvoir choisir :

- position précise ;
- position approximative ;
- ville manuelle ;
- quartier manuel ;
- aucune localisation.

La recherche doit fonctionner même sans autorisation GPS.

---

# 15. Fiche commerce

Une fiche commerce peut contenir :

- nom ;
- logo ;
- photos ;
- description ;
- catégorie ;
- adresse ;
- carte ;
- horaires ;
- téléphone ;
- e-mail ;
- réseaux sociaux ;
- site web ;
- catalogue ;
- promotions ;
- avis ;
- moyens de paiement ;
- services ;
- livraison ;
- réservation ;
- commande ;
- bouton payer ;
- badge de vérification ;
- date de dernière mise à jour.

---

# 16. Fiche professionnel

Elle peut contenir :

- nom professionnel ;
- photo ;
- métier ;
- expérience ;
- zone d’intervention ;
- services ;
- tarifs indicatifs ;
- disponibilités ;
- certifications ;
- avis ;
- téléphone ;
- messagerie ;
- paiement Mansa ;
- portfolio ;
- badge vérifié.

---

# 17. Mini-site automatique

Chaque professionnel ou commerce peut disposer automatiquement d’un mini-site.

Exemple :

```text
mansa.app/nom-du-commerce
```

Le mini-site peut inclure :

- présentation ;
- galerie ;
- produits ;
- services ;
- horaires ;
- localisation ;
- contact ;
- avis ;
- réservation ;
- paiement ;
- promotions ;
- liens sociaux.

---

# 18. Personnalisation du mini-site

Le commerçant peut configurer :

- logo ;
- couverture ;
- couleurs ;
- description ;
- photos ;
- sections ;
- ordre des éléments ;
- catalogue ;
- boutons ;
- horaires ;
- liens ;
- promotions ;
- langue.

---

# 19. Domaine personnalisé

Selon l’abonnement, le commerce peut utiliser :

- sous-domaine Mansa ;
- domaine personnalisé ;
- redirection ;
- QR de mini-site ;
- lien court.

---

# 20. Catalogue

La fiche peut afficher :

- produits ;
- services ;
- catégories ;
- prix ;
- variantes ;
- photos ;
- disponibilité ;
- promotions ;
- stock indicatif ;
- bouton commander ;
- bouton payer.

---

# 21. Produit

Une fiche produit peut contenir :

- nom ;
- description ;
- prix ;
- ancien prix ;
- promotion ;
- images ;
- variantes ;
- disponibilité ;
- livraison ;
- retrait ;
- note ;
- commerce ;
- bouton acheter ;
- bouton partager.

---

# 22. Service

Une fiche service peut contenir :

- nom ;
- description ;
- durée ;
- prix ;
- zone ;
- disponibilité ;
- réservation ;
- professionnel ;
- conditions ;
- paiement ;
- avis.

---

# 23. Promotions

Types possibles :

- réduction ;
- coupon ;
- cashback ;
- produit offert ;
- offre limitée ;
- happy hour ;
- promotion locale ;
- remise Mansa ;
- fidélité ;
- lancement ;
- événement.

---

# 24. Éligibilité d’une promotion

Elle peut dépendre :

- du pays ;
- de la ville ;
- du commerce ;
- du produit ;
- du paiement Mansa ;
- du montant ;
- de la date ;
- de l’heure ;
- du niveau de fidélité ;
- du nombre d’utilisations ;
- d’un code ;
- d’une campagne.

---

# 25. Favoris

L’utilisateur peut enregistrer :

- commerces ;
- professionnels ;
- produits ;
- services ;
- promotions ;
- agents ;
- DAB ;
- recherches ;
- catégories.

---

# 26. Listes personnelles

Exemples :

- à tester ;
- restaurants ;
- artisans ;
- boutiques ;
- favoris famille ;
- services fréquents ;
- voyage ;
- achats futurs.

---

# 27. Avis

Un avis peut contenir :

- note ;
- commentaire ;
- photos ;
- date ;
- achat vérifié ;
- réponse du commerce ;
- signalement ;
- statut de modération.

---

# 28. Avis vérifié

Le système peut marquer un avis comme vérifié si :

- un paiement Mansa est lié ;
- une commande est liée ;
- une réservation est liée ;
- un reçu est vérifié ;
- une interaction réelle est confirmée.

---

# 29. Modération des avis

Le système doit détecter :

- insultes ;
- faux avis ;
- spam ;
- publicité ;
- contenu illégal ;
- harcèlement ;
- informations personnelles ;
- manipulation de note ;
- conflits d’intérêt.

---

# 30. Réponse du commerce

Le commerce peut répondre à un avis.

La réponse doit être :

- visible ;
- modifiable selon règles ;
- modérée ;
- horodatée ;
- liée au représentant autorisé.

---

# 31. Signalement

Un utilisateur peut signaler :

- faux commerce ;
- mauvaise adresse ;
- faux agent ;
- fraude ;
- contenu trompeur ;
- prix incorrect ;
- profil fermé ;
- service inexistant ;
- harcèlement ;
- avis abusif.

---

# 32. Vérification des profils

Le badge vérifié peut dépendre de :

- KYC ;
- KYB ;
- documents ;
- activité réelle ;
- compte bancaire ;
- localisation ;
- contrat ;
- contrôle terrain ;
- historique ;
- absence de sanction.

---

# 33. Types de badges

Exemples :

- Vérifié ;
- Partenaire Mansa ;
- Agent agréé ;
- Commerce officiel ;
- Service public ;
- Premium ;
- Nouveau ;
- Populaire ;
- Accessible ;
- Ouvert maintenant.

---

# 34. Abonnements professionnels

Plans possibles :

- Gratuit ;
- Standard ;
- Premium ;
- Business ;
- Enterprise ;
- Institutionnel ;
- Personnalisé.

---

# 35. Fonctions par abonnement

Exemples :

- nombre de photos ;
- nombre de produits ;
- mini-site ;
- domaine personnalisé ;
- statistiques ;
- promotions ;
- campagnes ;
- réservation ;
- commande ;
- paiement ;
- réponse aux avis ;
- badge ;
- position sponsorisée ;
- support prioritaire ;
- API.

---

# 36. Mise en avant

Options possibles :

- profil à la une ;
- bannière ;
- catégorie sponsorisée ;
- produit sponsorisé ;
- promotion sponsorisée ;
- recommandation locale ;
- recherche sponsorisée ;
- campagne géolocalisée.

---

# 37. Règles de mise en avant

Elles peuvent dépendre :

- du budget ;
- de la zone ;
- de la durée ;
- de la catégorie ;
- de l’audience ;
- de la disponibilité ;
- du paiement ;
- de la qualité du profil ;
- de la conformité ;
- du plafond publicitaire.

---

# 38. Campagnes sponsorisées

Une campagne peut contenir :

- objectif ;
- budget ;
- dates ;
- zone ;
- audience ;
- format ;
- commerce ;
- produit ;
- promotion ;
- limite d’impression ;
- limite de clic ;
- statut ;
- résultats.

---

# 39. Formats publicitaires

Exemples :

- bannière ;
- carte sponsorisée ;
- profil sponsorisé ;
- produit sponsorisé ;
- promotion ;
- notification autorisée ;
- contenu recommandé ;
- résultat de recherche sponsorisé.

---

# 40. Transparence publicitaire

Tout contenu sponsorisé doit afficher une mention visible.

L’utilisateur doit pouvoir :

- comprendre pourquoi il le voit ;
- signaler ;
- masquer ;
- gérer certaines préférences.

---

# 41. Réservation

Le Hub peut permettre de réserver :

- restaurant ;
- coiffeur ;
- médecin ;
- hôtel ;
- artisan ;
- événement ;
- service ;
- transport ;
- salle ;
- rendez-vous professionnel.

---

# 42. Parcours de réservation

1. choisir le service ;
2. choisir une date ;
3. choisir une heure ;
4. choisir un professionnel ;
5. ajouter une note ;
6. consulter le prix ;
7. verser un acompte si nécessaire ;
8. confirmer ;
9. recevoir un rappel.

---

# 43. Commande

Le Hub peut permettre :

- commande de produits ;
- livraison ;
- retrait sur place ;
- commande à emporter ;
- précommande ;
- commande programmée ;
- commande groupée.

---

# 44. Paiement

Depuis une fiche, l’utilisateur peut :

- payer le commerce ;
- payer une commande ;
- payer un acompte ;
- payer une réservation ;
- acheter un produit ;
- utiliser un coupon ;
- utiliser Mansa Wallet ;
- utiliser une carte ;
- utiliser Mobile Money.

---

# 45. Lien avec Mansa Commerce

Les données peuvent être synchronisées avec Mansa Commerce :

- catalogue ;
- stock ;
- horaires ;
- prix ;
- promotions ;
- commandes ;
- réservations ;
- avis ;
- règlements ;
- mini-site.

---

# 46. Lien avec Mansa Agent

Le Hub peut afficher :

- agents proches ;
- disponibilité des services ;
- horaires ;
- dépôt ;
- retrait ;
- carte ;
- itinéraire ;
- statut ;
- badge agréé.

---

# 47. Lien avec les DAB

Le Hub peut afficher :

- DAB proches ;
- services disponibles ;
- horaires ;
- statut ;
- retrait QR ;
- retrait carte ;
- dépôt ;
- accessibilité ;
- itinéraire.

---

# 48. Services publics

Le Hub peut référencer :

- mairies ;
- écoles ;
- universités ;
- hôpitaux ;
- centres administratifs ;
- services d’eau ;
- électricité ;
- transports ;
- impôts ;
- documents ;
- services municipaux.

---

# 49. Événements

Le Hub peut afficher :

- événements commerciaux ;
- foires ;
- salons ;
- concerts ;
- formations ;
- campagnes publiques ;
- journées promotionnelles ;
- marchés ;
- événements sportifs.

---

# 50. Recommandations

Le système peut recommander selon :

- localisation ;
- historique ;
- favoris ;
- catégories ;
- horaires ;
- popularité ;
- paiements récents ;
- préférences ;
- saison ;
- promotion ;
- budget ;
- contexte.

---

# 51. Limites des recommandations

Le système ne doit pas :

- manipuler l’utilisateur ;
- cacher les résultats organiques ;
- révéler des données sensibles ;
- utiliser des critères interdits ;
- favoriser un partenaire sans transparence ;
- recommander un commerce suspendu.

---

# 52. Jini dans le Hub

Jini peut :

- rechercher un commerce ;
- trouver un agent ;
- trouver un DAB ;
- comparer des options ;
- proposer un itinéraire ;
- expliquer une promotion ;
- trouver un service ;
- aider à réserver ;
- aider à commander ;
- aider à payer.

---

# 53. Recherche conversationnelle

Exemples :

```text
Trouve-moi un restaurant ouvert à moins de 2 km
Je cherche un plombier disponible aujourd’hui
Où retirer 50 000 FCFA près de moi ?
Trouve une pharmacie ouverte maintenant
```

---

# 54. Notifications

Types :

- nouvelle promotion ;
- baisse de prix ;
- commerce favori ;
- réservation ;
- commande ;
- événement ;
- réponse à un avis ;
- nouvel agent ;
- DAB disponible ;
- campagne locale ;
- recommandation.

---

# 55. Préférences de notifications

L’utilisateur peut gérer :

- promotions ;
- favoris ;
- proximité ;
- événements ;
- recommandations ;
- commandes ;
- réservations ;
- agents ;
- DAB ;
- services publics.

---

# 56. Mode réseau faible

Mesures :

- listes textuelles ;
- miniatures légères ;
- cache ;
- pagination ;
- carte facultative ;
- compression ;
- affichage des dernières données ;
- reprise ;
- faible nombre de requêtes ;
- recherche par ville.

---

# 57. Mode hors ligne

Le mode hors ligne peut permettre :

- consulter les favoris ;
- voir les dernières fiches ;
- consulter des reçus ;
- lire des informations enregistrées ;
- retrouver un itinéraire simple ;
- afficher les derniers agents consultés.

Il ne doit pas confirmer :

- une commande ;
- une réservation ;
- un paiement ;
- une promotion ;
- une disponibilité temps réel.

---

# 58. Accessibilité

Le Hub doit prendre en charge :

- lecteur d’écran ;
- contraste ;
- taille de texte ;
- gros boutons ;
- mode sombre ;
- navigation simple ;
- carte alternative ;
- recherche vocale éventuelle ;
- langue simple ;
- réduction des animations.

---

# 59. Multi-langues

Le Hub doit être préparé pour :

- français ;
- bambara ;
- anglais ;
- langues régionales ;
- langues des pays déployés.

Les fiches peuvent contenir plusieurs traductions.

---

# 60. Multi-pays

Chaque pays peut avoir :

- catégories ;
- villes ;
- quartiers ;
- devises ;
- langues ;
- partenaires ;
- services publics ;
- formats d’adresse ;
- règles publicitaires ;
- règles de modération ;
- moyens de paiement ;
- abonnements.

---

# 61. Sécurité

Le système doit protéger :

- comptes professionnels ;
- fiches ;
- avis ;
- campagnes ;
- paiements ;
- réservations ;
- commandes ;
- données personnelles ;
- données de localisation ;
- contenus administratifs.

---

# 62. Protection contre les abus

Le système doit détecter :

- faux profils ;
- spam ;
- scraping ;
- faux avis ;
- fraude publicitaire ;
- faux agents ;
- manipulation de classement ;
- usurpation ;
- contenu illégal ;
- bots ;
- paiements frauduleux.

---

# 63. Administration centrale

Le portail Admin doit pouvoir gérer :

- catégories ;
- profils ;
- vérification ;
- mini-sites ;
- abonnements ;
- campagnes ;
- promotions ;
- avis ;
- modération ;
- signalements ;
- badges ;
- règles de classement ;
- pays ;
- villes ;
- langues ;
- contenus ;
- événements ;
- statistiques ;
- feature flags.

---

# 64. Permissions

Exemples :

```text
hub.profile.read
hub.profile.manage
hub.profile.verify
hub.category.manage
hub.review.read
hub.review.moderate
hub.report.read
hub.report.resolve
hub.campaign.read
hub.campaign.manage
hub.promotion.manage
hub.subscription.manage
hub.ranking.manage
hub.badge.manage
hub.analytics.read
hub.audit.read
```

---

# 65. Actions critiques

Doivent être protégées :

- vérification d’un profil ;
- retrait d’un badge ;
- suspension d’un commerce ;
- modification du classement ;
- activation d’une campagne ;
- modification d’un abonnement ;
- suppression d’un avis ;
- publication d’un service public ;
- modification massive de catégories ;
- export de données.

---

# 66. Double validation

Peut être exigée pour :

- suspension d’un profil important ;
- modification globale de classement ;
- grande campagne nationale ;
- suppression massive de contenus ;
- activation d’un partenaire public ;
- modification d’un abonnement global ;
- réactivation après fraude ;
- badge institutionnel ;
- campagne sensible.

---

# 67. API

Exemples :

```http
GET    /hub/home
GET    /hub/search
GET    /hub/categories
GET    /hub/businesses
GET    /hub/businesses/{id}
GET    /hub/professionals
GET    /hub/products
GET    /hub/services
GET    /hub/promotions
GET    /hub/events
GET    /hub/agents
GET    /hub/atms

POST   /hub/favorites
DELETE /hub/favorites/{id}

POST   /hub/reviews
POST   /hub/reports
POST   /hub/reservations
POST   /hub/orders
POST   /hub/payments

GET    /hub/minisites/{slug}
GET    /hub/recommendations
```

---

# 68. Modèles

- HubProfile
- HubBusinessProfile
- HubProfessionalProfile
- HubCategory
- HubSubcategory
- HubLocation
- HubOpeningHour
- HubProduct
- HubService
- HubPromotion
- HubFavorite
- HubList
- HubReview
- HubReviewResponse
- HubReport
- HubBadge
- HubSubscription
- HubCampaign
- HubSponsoredPlacement
- HubReservation
- HubOrder
- HubEvent
- HubMiniSite
- HubRecommendation
- HubSearchEvent
- HubAudit

---

# 69. Analytics

Événements possibles :

```text
hub_opened
hub_search_started
hub_search_completed
hub_category_opened
hub_profile_opened
hub_business_contacted
hub_route_requested
hub_favorite_added
hub_review_created
hub_promotion_opened
hub_reservation_created
hub_order_created
hub_payment_started
hub_payment_completed
hub_agent_opened
hub_atm_opened
hub_sponsored_content_viewed
hub_sponsored_content_clicked
```

---

# 70. Indicateurs professionnels

Le commerce peut consulter :

- vues ;
- recherches ;
- clics ;
- appels ;
- itinéraires ;
- favoris ;
- commandes ;
- réservations ;
- paiements ;
- conversions ;
- avis ;
- performance des promotions ;
- performance des campagnes.

---

# 71. Données analytics interdites

Ne pas transmettre :

- PIN ;
- OTP ;
- données carte ;
- documents ;
- localisation précise inutile ;
- données biométriques ;
- contenus privés ;
- données financières sensibles ;
- secrets professionnels.

---

# 72. Tests

- tests de recherche ;
- tests de fautes de frappe ;
- tests de catégories ;
- tests de filtres ;
- tests de tri ;
- tests de géolocalisation ;
- tests sans géolocalisation ;
- tests de profils ;
- tests de mini-sites ;
- tests de catalogue ;
- tests de promotions ;
- tests d’avis ;
- tests de modération ;
- tests de favoris ;
- tests de campagnes ;
- tests de mise en avant ;
- tests de réservation ;
- tests de commande ;
- tests de paiement ;
- tests agents ;
- tests DAB ;
- tests multi-pays ;
- tests multi-langues ;
- tests réseau faible ;
- tests hors ligne ;
- tests sécurité ;
- tests accessibilité ;
- tests analytics ;
- tests audit.

---

# 73. Règles métier

1. Chaque profil appartient à une organisation ou un professionnel identifié.
2. Les résultats sont filtrés par pays et disponibilité.
3. Les contenus sponsorisés sont identifiés.
4. Les règles de classement sont administrables.
5. Un profil suspendu ne doit pas être recommandé.
6. Les badges sont attribués selon des règles définies.
7. Les avis peuvent être liés à un achat vérifié.
8. Les faux avis sont modérés.
9. Les profils peuvent être signalés.
10. Les mini-sites sont générés automatiquement.
11. Les catalogues sont synchronisables avec Mansa Commerce.
12. Les paiements sont confirmés par le backend.
13. Les promotions sont versionnées.
14. Les abonnements sont configurables.
15. Les campagnes possèdent un budget et une période.
16. Les données de localisation sont limitées.
17. Le Hub fonctionne sans GPS.
18. Le mode hors ligne ne confirme pas d’opération.
19. Jini reste soumis aux permissions.
20. Les données professionnelles sensibles sont protégées.
21. Les résultats organiques restent distingués des résultats payants.
22. Les services publics sont vérifiés.
23. Les agents Mansa affichés doivent être actifs.
24. Les DAB indisponibles doivent être signalés.
25. Les actions critiques sont auditées.

---

# 74. Critères d’acceptation

L’application Hub & Annuaire est validée lorsque :

- la recherche fonctionne ;
- les catégories sont administrables ;
- les filtres et tris sont disponibles ;
- la recherche fonctionne avec ou sans GPS ;
- les commerces peuvent être découverts ;
- les professionnels disposent d’une fiche ;
- les mini-sites sont générés ;
- les catalogues sont visibles ;
- les promotions sont affichées ;
- les favoris fonctionnent ;
- les avis sont modérés ;
- les profils peuvent être vérifiés ;
- les abonnements sont administrables ;
- les contenus sponsorisés sont identifiés ;
- les campagnes sont mesurables ;
- les réservations fonctionnent ;
- les commandes sont prises en charge ;
- les paiements sont intégrés ;
- les agents et DAB sont visibles ;
- Jini est intégré ;
- le réseau faible est pris en charge ;
- les langues sont configurables ;
- les données sont protégées ;
- les actions sensibles sont auditées ;
- les tests couvrent les parcours essentiels.
