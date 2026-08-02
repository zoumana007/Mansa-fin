# 48 — Site web officiel Mansa : vitrine, produits, confiance, chiffres, partenaires, recrutement et conversion

## 1. Objet du document

Ce document définit l’architecture officielle du **site web public de Mansa**.

Le site présente :

- l’entreprise ;
- la vision ;
- les produits ;
- les applications ;
- les cartes ;
- les paiements ;
- Mansa Cash Network ;
- Mansa Agent ;
- Mansa Commerce ;
- les TPE ;
- le Hub ;
- les services publics ;
- Jini ;
- les partenaires ;
- les chiffres clés ;
- la sécurité ;
- les tarifs publics ;
- les actualités ;
- les offres d’emploi ;
- le support ;
- les documents légaux ;
- les téléchargements ;
- les formulaires de contact ;
- les demandes de partenariat.

L’objectif est de créer un site :

- moderne ;
- premium ;
- crédible ;
- rapide ;
- animé ;
- accessible ;
- multilingue ;
- adapté au mobile ;
- administrable ;
- conçu pour convertir les visiteurs en utilisateurs, commerçants, agents ou partenaires.

---

# 2. Principes fondamentaux

## 2.1 Le site est une vitrine publique

Le site ne doit pas exposer :

- les outils internes ;
- les secrets techniques ;
- les données clients ;
- les journaux internes ;
- les configurations sensibles ;
- les contrats privés ;
- les informations de sécurité exploitables.

---

## 2.2 Les données affichées doivent être vérifiables

Les chiffres publics doivent provenir de sources administrées.

Exemples :

- nombre d’utilisateurs ;
- nombre de commerçants ;
- nombre d’agents ;
- volume de transactions ;
- nombre de pays ;
- nombre de partenaires ;
- disponibilité des services.

Aucun chiffre ne doit être codé directement dans les pages.

---

## 2.3 Le site doit évoluer sans modification du code

L’administration doit pouvoir gérer :

- textes ;
- images ;
- vidéos ;
- chiffres ;
- partenaires ;
- pages ;
- menus ;
- formulaires ;
- campagnes ;
- langues ;
- tarifs ;
- articles ;
- offres d’emploi ;
- bannières ;
- messages de maintenance.

---

## 2.4 Le site ne remplace pas les applications

Le site présente les services et redirige vers :

- l’application Client ;
- l’application Commerce ;
- Mansa Agent ;
- le portail web ;
- le téléchargement mobile ;
- les formulaires d’inscription ;
- les partenaires.

---

## 2.5 Le site doit inspirer confiance

Il doit expliquer clairement :

- qui est Mansa ;
- comment Mansa fonctionne ;
- comment les fonds sont protégés ;
- avec quels partenaires Mansa travaille ;
- comment contacter le support ;
- quelles règles s’appliquent ;
- quelles fonctionnalités sont disponibles dans chaque pays.

---

# 3. Technologie

Technologie recommandée :

```text
Next.js
TypeScript
```

Composants possibles :

- App Router ;
- rendu serveur ;
- génération statique ;
- CMS ;
- système de design ;
- animations ;
- analytics ;
- formulaires sécurisés ;
- gestion des traductions ;
- optimisation des images ;
- CDN ;
- protection anti-abus.

---

# 4. Architecture du projet

Structure recommandée :

```text
src/
├── app/
├── pages/
├── layouts/
├── components/
├── sections/
├── products/
├── solutions/
├── partners/
├── security/
├── pricing/
├── careers/
├── newsroom/
├── support/
├── legal/
├── forms/
├── cms/
├── analytics/
├── localization/
├── seo/
├── theme/
└── utils/
```

---

# 5. Navigation principale

Navigation possible :

```text
Particuliers
Entreprises
Agents
TPE
Services publics
À propos
Aide
```

Actions principales :

```text
Télécharger l’application
Ouvrir un compte
Devenir partenaire
Se connecter
```

---

# 6. Page d’accueil

La page d’accueil doit présenter :

- proposition de valeur ;
- produits principaux ;
- applications ;
- cartes ;
- paiements ;
- transferts ;
- Cash Network ;
- TPE ;
- commerces ;
- Hub ;
- sécurité ;
- partenaires ;
- chiffres clés ;
- témoignages ;
- téléchargements ;
- appel à l’action.

---

# 7. Hero principal

Le hero peut contenir :

- titre fort ;
- sous-titre ;
- visuel de l’application ;
- animation légère ;
- bouton de téléchargement ;
- bouton de découverte ;
- QR de téléchargement ;
- disponibilité par pays.

---

# 8. Visuels de l’application

Le site peut afficher :

- écrans mobiles ;
- cartes Mansa ;
- tableaux de bord ;
- TPE ;
- agents ;
- DAB ;
- paiements ;
- animations de transactions ;
- graphiques ;
- démonstrations interactives.

Les visuels doivent rester cohérents avec l’application réelle.

---

# 9. Animations

Les animations peuvent utiliser :

- CSS ;
- Framer Motion ;
- GSAP ;
- WebGL ou Three.js pour certains éléments ;
- transitions au défilement ;
- parallax léger ;
- micro-interactions ;
- animations de chiffres ;
- démonstrations de parcours.

Les animations doivent rester :

- fluides ;
- accessibles ;
- désactivables ;
- légères ;
- compatibles avec les appareils modestes.

---

# 10. Réduction des animations

Le site doit respecter :

```text
prefers-reduced-motion
```

Les utilisateurs doivent pouvoir consulter le contenu sans animation.

---

# 11. Page Particuliers

Elle doit présenter :

- wallet ;
- paiements ;
- transferts ;
- cartes ;
- dépôts ;
- retraits ;
- budgets ;
- coffres ;
- abonnements ;
- reçus ;
- sécurité ;
- support ;
- Jini.

---

# 12. Page Cartes

Elle peut présenter :

- carte physique ;
- carte virtuelle ;
- carte temporaire ;
- carte jetable ;
- carte étudiante ;
- carte employé ;
- carte de fidélité ;
- compatibilité Wallet ;
- plafonds ;
- sécurité ;
- disponibilité par pays.

---

# 13. Page Cash Network

Elle doit expliquer :

- dépôts chez les agents ;
- retraits chez les agents ;
- agents agréés ;
- DAB Mansa ;
- fonctionnement sans Internet côté client ;
- reçus ;
- authentification des retraits ;
- recherche des points de service ;
- sécurité.

---

# 14. Page Entreprises

Elle doit présenter :

- paiements ;
- Mansa Commerce ;
- TPE ;
- catalogue ;
- stock ;
- employés ;
- caisses ;
- facturation ;
- mini-site ;
- fidélité ;
- rapports ;
- règlements ;
- intégration API.

---

# 15. Page Mansa Agent

Elle doit expliquer :

- rôle de l’agent ;
- dépôts ;
- retraits ;
- float ;
- commissions ;
- caisse ;
- liquidité ;
- sécurité ;
- conditions d’adhésion ;
- procédure de candidature ;
- avantages.

---

# 16. Page TPE

Elle doit présenter :

- terminaux Android ;
- SoftPOS ;
- cartes ;
- QR ;
- Wallet Mansa ;
- Mobile Money ;
- reçus ;
- remboursements ;
- sécurité ;
- installation ;
- tarifs ;
- demande de TPE.

---

# 17. Page Hub

Elle doit présenter :

- annuaire ;
- recherche locale ;
- commerces ;
- produits ;
- promotions ;
- mini-sites ;
- avis ;
- réservations ;
- commandes ;
- agents ;
- DAB ;
- services publics.

---

# 18. Page Services publics

Elle peut présenter :

- amendes ;
- taxes ;
- scolarité ;
- université ;
- bourses ;
- cartes étudiantes ;
- documents administratifs ;
- factures publiques ;
- paiements officiels ;
- traçabilité.

Les services doivent être affichés uniquement lorsqu’ils sont officiellement disponibles.

---

# 19. Page Jini

Elle doit expliquer :

- assistant financier ;
- recherche d’opérations ;
- aide au paiement ;
- accompagnement KYC ;
- analyse de dépenses ;
- aide aux commerçants ;
- aide au support ;
- limites de l’IA ;
- confidentialité.

---

# 20. Page Sécurité

Elle doit présenter de manière compréhensible :

- authentification ;
- biométrie ;
- appareils reconnus ;
- chiffrement ;
- surveillance ;
- lutte contre la fraude ;
- notifications ;
- protection des cartes ;
- récupération de compte ;
- support en cas d’incident.

---

# 21. Page Confiance et conformité

Elle peut contenir :

- partenaires réglementés ;
- banque partenaire ;
- licences ou statuts applicables ;
- politiques ;
- mesures de conformité ;
- KYC ;
- KYB ;
- lutte contre le blanchiment ;
- traitement des réclamations.

Aucune autorisation ne doit être annoncée avant validation officielle.

---

# 22. Chiffres clés

Exemples :

- utilisateurs actifs ;
- commerçants ;
- agents ;
- TPE ;
- villes ;
- pays ;
- transactions ;
- paiements réussis ;
- disponibilité du service.

Chaque chiffre doit avoir :

- valeur ;
- date de référence ;
- source interne ;
- statut de publication ;
- validation ;
- fréquence de mise à jour.

---

# 23. Animation des chiffres

Les compteurs peuvent s’animer à l’apparition.

Le contenu réel doit rester visible sans JavaScript.

---

# 24. Partenaires

Le site peut afficher :

- banques ;
- opérateurs Mobile Money ;
- réseaux cartes ;
- institutions ;
- commerçants ;
- fournisseurs technologiques ;
- partenaires publics ;
- établissements d’enseignement.

Chaque partenaire doit être publié avec autorisation.

---

# 25. Fiche partenaire

Elle peut contenir :

- logo ;
- nom ;
- type ;
- pays ;
- services concernés ;
- date de partenariat ;
- description validée ;
- lien officiel ;
- statut.

---

# 26. Tarifs publics

Le site peut afficher :

- frais de cartes ;
- abonnements ;
- tarifs TPE ;
- frais de retrait ;
- frais de transfert ;
- frais professionnels ;
- offres promotionnelles.

Les données doivent venir du moteur tarifaire ou d’un CMS connecté.

---

# 27. Tarifs dynamiques

Les tarifs peuvent varier selon :

- pays ;
- devise ;
- produit ;
- segment ;
- canal ;
- partenaire ;
- période ;
- campagne.

Le site doit afficher :

- date d’effet ;
- conditions ;
- taxes éventuelles ;
- disponibilité ;
- exclusions.

---

# 28. Simulateur de frais

Le site peut proposer un simulateur permettant de choisir :

- pays ;
- type d’opération ;
- montant ;
- devise ;
- canal ;
- destinataire ;
- mode de paiement.

Le résultat doit provenir du backend.

---

# 29. Téléchargement des applications

Le site doit proposer :

- App Store ;
- Google Play ;
- QR ;
- version minimale ;
- pays disponible ;
- liens officiels ;
- programme bêta ;
- application Commerce ;
- application Agent ;
- application Hub.

---

# 30. Liens de téléchargement

Les liens doivent être :

- administrables ;
- validés ;
- suivis ;
- adaptés au pays ;
- adaptés au système d’exploitation ;
- protégés contre la redirection frauduleuse.

---

# 31. Page À propos

Elle peut contenir :

- histoire ;
- mission ;
- vision ;
- valeurs ;
- fondateur ;
- équipe ;
- gouvernance ;
- implantation ;
- engagements ;
- feuille de route publique.

---

# 32. Présentation du fondateur

Le site peut afficher :

- nom ;
- fonction ;
- photo ;
- biographie ;
- vision ;
- message ;
- liens professionnels.

La publication doit être administrable.

---

# 33. Page Équipe

Elle peut présenter :

- direction ;
- technologie ;
- produit ;
- conformité ;
- opérations ;
- partenariats ;
- support ;
- sécurité.

Les informations sensibles ne doivent pas être exposées.

---

# 34. Page Carrières

Elle doit afficher :

- offres ouvertes ;
- type de contrat ;
- localisation ;
- équipe ;
- mission ;
- compétences ;
- candidature ;
- statut ;
- date de publication ;
- date de clôture.

---

# 35. Candidature

Le formulaire peut demander :

- identité ;
- e-mail ;
- téléphone ;
- poste ;
- CV ;
- lettre ;
- portfolio ;
- pays ;
- disponibilité ;
- consentement.

---

# 36. Protection des candidatures

Les fichiers doivent être :

- chiffrés ;
- contrôlés par antivirus ;
- limités en taille ;
- soumis à rétention ;
- accessibles uniquement aux recruteurs autorisés.

---

# 37. Actualités

Le site peut publier :

- lancements ;
- partenariats ;
- nouveaux produits ;
- nouveaux pays ;
- campagnes ;
- événements ;
- communiqués ;
- rapports ;
- mises à jour majeures.

---

# 38. Centre média

Il peut contenir :

- logos ;
- charte ;
- photos officielles ;
- communiqués ;
- contacts presse ;
- biographies ;
- chiffres validés.

---

# 39. Blog éducatif

Thèmes possibles :

- finance personnelle ;
- sécurité ;
- fraude ;
- paiements ;
- commerce ;
- digitalisation ;
- entrepreneuriat ;
- Mobile Money ;
- cartes ;
- services publics numériques.

---

# 40. Centre d’aide

Le site doit permettre :

- recherche d’articles ;
- catégories ;
- questions fréquentes ;
- tutoriels ;
- guides ;
- vidéos ;
- contact ;
- suivi de ticket ;
- statut des services.

---

# 41. Recherche d’aide

La recherche peut être alimentée par :

- mots-clés ;
- catégories ;
- suggestions ;
- Jini ;
- historique ;
- langue ;
- pays ;
- produit.

---

# 42. Formulaire de contact

Catégories possibles :

- particulier ;
- commerçant ;
- agent ;
- partenaire ;
- institution ;
- presse ;
- investisseur ;
- recrutement ;
- sécurité ;
- réclamation.

---

# 43. Demande de partenariat

Le formulaire peut demander :

- organisation ;
- pays ;
- secteur ;
- représentant ;
- e-mail ;
- téléphone ;
- type de partenariat ;
- description ;
- volume estimé ;
- documents ;
- consentement.

---

# 44. Demande TPE

Le formulaire peut demander :

- commerce ;
- pays ;
- ville ;
- nombre de terminaux ;
- type d’activité ;
- volume estimé ;
- moyens de paiement souhaités ;
- contact ;
- établissement.

---

# 45. Candidature Agent

Le formulaire peut demander :

- identité ;
- commerce ;
- adresse ;
- localisation ;
- téléphone ;
- type de point ;
- horaires ;
- capital disponible ;
- expérience ;
- documents ;
- zone souhaitée.

---

# 46. Formulaires sécurisés

Tous les formulaires doivent appliquer :

- validation ;
- rate limiting ;
- CAPTCHA adaptatif ;
- antivirus ;
- contrôle de taille ;
- consentement ;
- chiffrement ;
- traçabilité ;
- anti-spam ;
- messages d’erreur clairs.

---

# 47. Prise de rendez-vous

Le site peut permettre de réserver :

- démonstration ;
- rendez-vous commercial ;
- entretien partenaire ;
- installation TPE ;
- présentation institutionnelle ;
- support premium.

---

# 48. Site de statut

Le site doit renvoyer vers une page de statut publique présentant :

- application Client ;
- paiements ;
- cartes ;
- transferts ;
- Cash Network ;
- TPE ;
- Commerce ;
- Hub ;
- API ;
- partenaires.

---

# 49. Statuts publics

Valeurs possibles :

- OPERATIONAL ;
- DEGRADED ;
- PARTIAL_OUTAGE ;
- MAJOR_OUTAGE ;
- MAINTENANCE.

---

# 50. Maintenance

Le site doit pouvoir afficher :

- bannière ;
- service concerné ;
- début ;
- fin estimée ;
- pays ;
- impact ;
- alternatives ;
- mise à jour.

---

# 51. SEO

Le site doit gérer :

- titres ;
- descriptions ;
- données structurées ;
- sitemap ;
- robots ;
- canonical ;
- Open Graph ;
- cartes sociales ;
- pages locales ;
- pages produits ;
- pages partenaires.

---

# 52. SEO local

Des pages peuvent être créées pour :

- pays ;
- villes ;
- services ;
- agents ;
- DAB ;
- commerces ;
- catégories.

Les pages ne doivent pas être générées avec du contenu vide ou trompeur.

---

# 53. Performance

Objectifs :

- chargement rapide ;
- images optimisées ;
- JavaScript limité ;
- cache ;
- CDN ;
- rendu serveur ;
- chargement différé ;
- polices optimisées ;
- animations légères.

---

# 54. Core Web Vitals

Le site doit surveiller :

- LCP ;
- INP ;
- CLS ;
- TTFB ;
- erreurs JavaScript ;
- poids des pages.

---

# 55. Réseau faible

Le site doit proposer :

- images réduites ;
- vidéos facultatives ;
- mode sans animation ;
- contenu prioritaire ;
- chargement progressif ;
- pages statiques ;
- formulaires résilients.

---

# 56. Mode sombre

Le site peut proposer :

- thème clair ;
- thème sombre ;
- préférence système.

---

# 57. Accessibilité

Le site doit prendre en charge :

- navigation clavier ;
- lecteur d’écran ;
- contraste ;
- texte redimensionnable ;
- labels ;
- focus visible ;
- réduction des animations ;
- sous-titres ;
- textes alternatifs ;
- formulaires accessibles.

---

# 58. Multi-langues

Langues initiales possibles :

- français ;
- bambara ;
- anglais.

Le site doit pouvoir ajouter d’autres langues sans modifier toute l’architecture.

---

# 59. Multi-pays

Le contenu peut varier selon :

- pays ;
- devise ;
- réglementation ;
- applications disponibles ;
- partenaires ;
- tarifs ;
- services ;
- langues ;
- coordonnées ;
- documents légaux.

---

# 60. Sélecteur de pays

Le site peut détecter ou proposer :

- pays actuel ;
- pays choisi ;
- langue ;
- devise ;
- disponibilité.

Le choix manuel doit toujours rester possible.

---

# 61. CMS

Le CMS doit gérer :

- pages ;
- blocs ;
- menus ;
- images ;
- vidéos ;
- formulaires ;
- articles ;
- chiffres ;
- partenaires ;
- offres ;
- tarifs ;
- traductions ;
- SEO ;
- redirections ;
- bannières.

---

# 62. Workflow éditorial

Statuts possibles :

- DRAFT ;
- REVIEW ;
- APPROVED ;
- SCHEDULED ;
- PUBLISHED ;
- UNPUBLISHED ;
- ARCHIVED.

---

# 63. Validation éditoriale

Certaines publications peuvent exiger :

- auteur ;
- relecteur ;
- juridique ;
- conformité ;
- marketing ;
- direction ;
- approbation finale.

---

# 64. Planification

Les contenus peuvent être :

- publiés immédiatement ;
- programmés ;
- expirés ;
- archivés ;
- remplacés automatiquement.

---

# 65. Historique des modifications

Chaque modification doit enregistrer :

- auteur ;
- date ;
- ancienne version ;
- nouvelle version ;
- motif ;
- approbateur ;
- date de publication.

---

# 66. Analytics

Événements possibles :

```text
website_opened
website_product_opened
website_app_download_clicked
website_partner_form_started
website_partner_form_submitted
website_agent_application_started
website_agent_application_submitted
website_terminal_request_submitted
website_pricing_opened
website_fee_simulation_completed
website_support_opened
website_article_opened
website_career_application_submitted
```

---

# 67. Données analytics interdites

Ne pas transmettre :

- mots de passe ;
- OTP ;
- PIN ;
- documents ;
- données bancaires ;
- contenu complet des formulaires ;
- CV ;
- données biométriques ;
- secrets ;
- informations financières sensibles.

---

# 68. Consentement analytics

Le site doit permettre :

- accepter ;
- refuser ;
- personnaliser ;
- modifier le choix ;
- consulter les catégories ;
- enregistrer la preuve du consentement.

---

# 69. Sécurité

Mesures principales :

- HTTPS ;
- CSP ;
- HSTS ;
- protection XSS ;
- protection CSRF ;
- validation des entrées ;
- WAF ;
- rate limiting ;
- gestion sécurisée des cookies ;
- contrôle des dépendances ;
- scans ;
- surveillance.

---

# 70. Protection contre l’usurpation

Le site doit expliquer clairement :

- les domaines officiels ;
- les applications officielles ;
- les comptes officiels ;
- les moyens de contact ;
- les alertes contre les faux agents ;
- les alertes contre les faux sites.

---

# 71. Redirections

Les redirections doivent être :

- administrables ;
- validées ;
- limitées aux domaines autorisés ;
- journalisées ;
- protégées contre les redirections ouvertes.

---

# 72. Documents légaux

Le site doit publier selon le pays :

- conditions générales ;
- politique de confidentialité ;
- politique cookies ;
- mentions légales ;
- tarifs ;
- conditions des cartes ;
- conditions commerçants ;
- conditions agents ;
- politique de réclamation ;
- politique de remboursement ;
- accessibilité.

---

# 73. Versions légales

Chaque document doit avoir :

- version ;
- pays ;
- langue ;
- date d’effet ;
- statut ;
- historique ;
- fichier téléchargeable ;
- validation juridique.

---

# 74. Administration centrale

Le portail Admin doit pouvoir gérer :

- pages ;
- menus ;
- contenus ;
- langues ;
- pays ;
- partenaires ;
- chiffres ;
- formulaires ;
- tarifs ;
- actualités ;
- emplois ;
- SEO ;
- redirections ;
- campagnes ;
- bannières ;
- maintenance ;
- analytics ;
- versions légales.

---

# 75. Permissions

Exemples :

```text
website.page.read
website.page.create
website.page.update
website.page.publish
website.menu.manage
website.media.manage
website.partner.manage
website.metric.manage
website.pricing.manage
website.form.read
website.form.export
website.career.manage
website.news.manage
website.seo.manage
website.redirect.manage
website.legal.manage
website.analytics.read
website.audit.read
```

---

# 76. Actions critiques

Doivent être protégées :

- publication de tarifs ;
- publication d’un partenariat ;
- publication de chiffres financiers ;
- modification d’un document légal ;
- redirection globale ;
- changement de domaine ;
- publication d’une alerte de sécurité ;
- activation d’un pays ;
- export massif de formulaires ;
- suppression d’un contenu officiel.

---

# 77. Double validation

Peut être exigée pour :

- modification de tarifs ;
- publication d’une licence ;
- annonce d’un partenaire bancaire ;
- changement juridique ;
- publication de chiffres sensibles ;
- communication de crise ;
- redirection d’un domaine ;
- activation d’un nouveau pays ;
- publication d’un communiqué officiel.

---

# 78. API

Exemples :

```http
GET    /public/site/configuration
GET    /public/site/pages/{slug}
GET    /public/site/products
GET    /public/site/partners
GET    /public/site/metrics
GET    /public/site/pricing
GET    /public/site/news
GET    /public/site/careers
GET    /public/site/legal

POST   /public/forms/contact
POST   /public/forms/partnership
POST   /public/forms/agent
POST   /public/forms/terminal
POST   /public/forms/career
POST   /public/pricing/preview
```

---

# 79. Modèles

- Website
- WebsiteCountry
- WebsiteLanguage
- WebsitePage
- WebsiteSection
- WebsiteMenu
- WebsiteMedia
- WebsitePartner
- WebsiteMetric
- WebsitePricingView
- WebsiteForm
- WebsiteFormSubmission
- WebsiteArticle
- WebsiteCareer
- WebsiteLegalDocument
- WebsiteBanner
- WebsiteRedirect
- WebsiteSeoMetadata
- WebsitePublication
- WebsiteAudit

---

# 80. Tests

- tests de pages ;
- tests de navigation ;
- tests de CMS ;
- tests de publication ;
- tests de formulaires ;
- tests anti-spam ;
- tests de téléchargement ;
- tests de chiffres ;
- tests de tarifs ;
- tests multi-pays ;
- tests multi-langues ;
- tests SEO ;
- tests de redirections ;
- tests de performance ;
- tests réseau faible ;
- tests d’animations ;
- tests sans animation ;
- tests d’accessibilité ;
- tests de sécurité ;
- tests de consentement ;
- tests analytics ;
- tests d’audit.

---

# 81. Règles métier

1. Le site public ne doit pas exposer les outils internes.
2. Les chiffres viennent d’une source administrée.
3. Les chiffres possèdent une date de référence.
4. Les partenaires sont publiés avec autorisation.
5. Les tarifs ne sont pas codés en dur.
6. Les tarifs affichés dépendent du pays.
7. Les services indisponibles ne doivent pas être annoncés comme actifs.
8. Les téléchargements pointent vers des sources officielles.
9. Les formulaires sont protégés.
10. Les contenus passent par un workflow.
11. Les publications sont versionnées.
12. Les documents légaux sont historisés.
13. Le site fonctionne sans animations.
14. Le site fonctionne sur réseau faible.
15. Le site respecte les règles d’accessibilité.
16. Les contenus sont traduisibles.
17. Les pages sont adaptées au pays.
18. Les analytics excluent les données sensibles.
19. Les consentements sont enregistrés.
20. Les redirections sont contrôlées.
21. Les domaines officiels sont clairement identifiés.
22. Les contenus sponsorisés sont signalés.
23. Les formulaires sensibles sont soumis à rétention.
24. Les actions critiques sont auditées.
25. Les publications importantes peuvent exiger une double validation.

---

# 82. Critères d’acceptation

Le site officiel Mansa est validé lorsque :

- la page d’accueil est disponible ;
- les produits sont présentés ;
- les applications sont téléchargeables ;
- les cartes sont expliquées ;
- Cash Network est présenté ;
- Mansa Commerce est présenté ;
- Mansa Agent est présenté ;
- le TPE est présenté ;
- le Hub est présenté ;
- les services publics sont présentés selon disponibilité ;
- Jini est présenté ;
- la sécurité est expliquée ;
- les chiffres sont administrables ;
- les partenaires sont administrables ;
- les tarifs sont dynamiques ;
- les formulaires sont sécurisés ;
- les candidatures sont gérées ;
- les actualités sont publiables ;
- les documents légaux sont versionnés ;
- les contenus sont multilingues ;
- le site est adapté au mobile ;
- le réseau faible est pris en charge ;
- l’accessibilité est testée ;
- les animations sont désactivables ;
- le CMS fonctionne ;
- les actions sensibles sont auditées ;
- les tests couvrent les parcours principaux.
