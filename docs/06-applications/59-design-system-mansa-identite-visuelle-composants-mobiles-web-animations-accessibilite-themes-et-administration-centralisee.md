# 59 — Design System Mansa : identité visuelle, composants mobiles et web, animations, accessibilité, thèmes et administration centralisée

## 1. Objet du document

Ce document définit l’architecture officielle du **Design System Mansa**.

Le Design System Mansa constitue la base visuelle, ergonomique et interactive commune à l’ensemble de l’écosystème.

Il doit être utilisé par :

- l’application Client ;
- l’application Commerce ;
- l’application Agent ;
- l’application TPE ;
- l’application Admin Lite ;
- le Hub et Annuaire ;
- le site officiel ;
- le portail Admin Web ;
- le portail Partenaires et Développeurs ;
- le portail Institutions ;
- le portail Banques et partenaires financiers ;
- le portail Entreprises ;
- le portail Écoles et Universités ;
- le portail Support ;
- la console Sécurité et Fraude ;
- la console Finance ;
- les interfaces DAB ;
- les écrans de terminaux ;
- les documents numériques ;
- les reçus ;
- les e-mails ;
- les notifications ;
- les futures applications Mansa.

Le Design System doit gérer :

- l’identité visuelle ;
- les couleurs ;
- les typographies ;
- les espacements ;
- les grilles ;
- les icônes ;
- les boutons ;
- les champs ;
- les cartes ;
- les tableaux ;
- les menus ;
- les graphiques ;
- les formulaires ;
- les animations ;
- les transitions ;
- les illustrations ;
- les états d’erreur ;
- les états de chargement ;
- les thèmes ;
- le mode sombre ;
- l’accessibilité ;
- les langues ;
- le responsive ;
- les écrans mobiles ;
- les écrans web ;
- les terminaux ;
- la personnalisation par pays ;
- la personnalisation institutionnelle ;
- l’administration centrale ;
- le versionnement ;
- les tests ;
- la documentation.

L’objectif est d’assurer une expérience :

- cohérente ;
- moderne ;
- premium ;
- claire ;
- rapide ;
- rassurante ;
- accessible ;
- professionnelle ;
- reconnaissable ;
- adaptée aux usages financiers ;
- adaptée aux utilisateurs peu familiarisés avec le numérique ;
- adaptée aux réseaux faibles ;
- évolutive pour plusieurs pays.

---

# 2. Principes fondamentaux

## 2.1 Une seule identité Mansa

Toutes les interfaces Mansa doivent partager une identité commune.

Cela concerne notamment :

- les couleurs ;
- la typographie ;
- les formes ;
- les icônes ;
- le ton ;
- les animations ;
- les états ;
- les illustrations ;
- les interactions ;
- les composants.

Chaque application peut conserver des adaptations propres à son usage, sans casser l’identité générale.

---

## 2.2 Aucun élément graphique principal ne doit être codé en dur

Les valeurs principales doivent provenir de tokens ou de configurations centralisées.

Exemples :

- couleurs ;
- tailles ;
- rayons ;
- ombres ;
- espacements ;
- durées d’animation ;
- typographies ;
- tailles d’icônes ;
- niveaux de contraste ;
- thèmes ;
- variantes pays ;
- paramètres de marque.

---

## 2.3 La sécurité doit rester prioritaire sur l’esthétique

Une interface financière ne doit pas masquer ou minimiser :

- le montant ;
- les frais ;
- la devise ;
- le bénéficiaire ;
- le commerçant ;
- la confirmation ;
- l’erreur ;
- le risque ;
- le statut ;
- la référence ;
- l’action irréversible.

Les animations et effets visuels ne doivent jamais empêcher la compréhension.

---

## 2.4 L’interface doit rester simple pour les nouveaux utilisateurs

Le Design System doit prévoir :

- des textes directs ;
- de grands boutons ;
- des icônes compréhensibles ;
- des parcours guidés ;
- des confirmations claires ;
- des erreurs explicites ;
- des écrans peu chargés ;
- des alternatives textuelles ;
- une aide contextuelle ;
- un mode simplifié lorsque nécessaire.

---

## 2.5 L’accessibilité est obligatoire

Les composants doivent être utilisables par :

- les personnes malvoyantes ;
- les personnes daltoniennes ;
- les personnes ayant des difficultés motrices ;
- les personnes utilisant un lecteur d’écran ;
- les utilisateurs âgés ;
- les utilisateurs peu habitués aux applications ;
- les utilisateurs utilisant un petit écran ;
- les utilisateurs utilisant un réseau lent.

---

# 3. Périmètre du Design System

Le Design System comprend :

```text
Fondations
Tokens
Composants
Patterns
Templates
Layouts
Animations
Illustrations
Contenus
Accessibilité
Documentation
Gouvernance
```

---

# 4. Technologies recommandées

Pour le web :

```text
React
Next.js
TypeScript
CSS Variables
Storybook
```

Pour les applications mobiles :

```text
React Native
TypeScript
```

Pour le TPE Android natif :

```text
Kotlin
Jetpack Compose
```

Pour la documentation et les tests visuels :

```text
Storybook
Visual Regression Testing
Component Testing
Accessibility Testing
```

---

# 5. Architecture du projet

Structure recommandée :

```text
design-system/
├── foundations/
├── tokens/
├── colors/
├── typography/
├── spacing/
├── radius/
├── shadows/
├── icons/
├── illustrations/
├── motion/
├── accessibility/
├── components/
├── patterns/
├── layouts/
├── templates/
├── mobile/
├── web/
├── terminal/
├── atm/
├── email/
├── documents/
├── themes/
├── localization/
├── documentation/
├── testing/
└── governance/
```

---

# 6. Identité de marque

L’identité doit transmettre :

- confiance ;
- stabilité ;
- innovation ;
- proximité ;
- modernité ;
- sécurité ;
- simplicité ;
- ambition africaine ;
- ouverture internationale ;
- sérieux financier.

---

# 7. Logo Mansa

Le système doit prévoir :

- logo principal ;
- logo horizontal ;
- logo vertical ;
- symbole seul ;
- version claire ;
- version sombre ;
- version monochrome ;
- version petite taille ;
- icône d’application ;
- favicon ;
- version imprimée ;
- version terminal ;
- zone de protection ;
- taille minimale ;
- usages interdits.

---

# 8. Variantes du logo

Variantes possibles :

- Mansa principal ;
- Mansa Business ;
- Mansa Agent ;
- Mansa Pay ;
- Mansa TPE ;
- Mansa Campus ;
- Mansa Public ;
- Mansa Developer ;
- Mansa Partner.

Ces variantes doivent rester cohérentes et validées centralement.

---

# 9. Couleurs principales

Le Design System doit définir :

- couleur principale ;
- couleur secondaire ;
- couleur d’accent ;
- couleurs neutres ;
- couleurs de fond ;
- couleurs de surface ;
- couleurs de texte ;
- couleurs de bordure ;
- couleurs d’interaction ;
- couleurs d’état.

Les valeurs exactes doivent être centralisées dans des tokens.

---

# 10. Couleurs sémantiques

Exemples :

- succès ;
- erreur ;
- avertissement ;
- information ;
- attente ;
- indisponible ;
- bloqué ;
- actif ;
- désactivé ;
- risque faible ;
- risque moyen ;
- risque élevé ;
- risque critique.

La couleur seule ne doit jamais être l’unique moyen d’indiquer un état.

---

# 11. Tokens de couleurs

Exemples :

```text
color.brand.primary
color.brand.secondary
color.surface.default
color.surface.elevated
color.text.primary
color.text.secondary
color.border.default
color.status.success
color.status.warning
color.status.error
color.status.info
```

---

# 12. Thème clair

Le thème clair doit définir :

- fond principal ;
- surfaces ;
- cartes ;
- champs ;
- bordures ;
- textes ;
- ombres ;
- états ;
- overlays ;
- graphiques ;
- illustrations.

---

# 13. Thème sombre

Le mode sombre doit :

- réduire l’éblouissement ;
- préserver le contraste ;
- éviter les noirs absolus excessifs ;
- conserver la lisibilité ;
- adapter les ombres ;
- adapter les illustrations ;
- adapter les graphiques ;
- adapter les états de risque ;
- rester cohérent avec la marque.

---

# 14. Thème système

Les applications peuvent suivre :

- thème clair ;
- thème sombre ;
- préférence système ;
- thème imposé par l’administrateur dans certains contextes ;
- thème spécial d’accessibilité.

---

# 15. Personnalisation institutionnelle

Certaines interfaces partenaires peuvent permettre :

- logo partenaire ;
- nom de l’institution ;
- couleur secondaire ;
- bannière ;
- document personnalisé ;
- reçus personnalisés ;
- page de paiement personnalisée.

La personnalisation ne doit pas masquer l’identité Mansa lorsque Mansa reste opérateur du service.

---

# 16. Typographie

Le système doit définir :

- police principale ;
- police secondaire éventuelle ;
- police monospace ;
- tailles ;
- graisses ;
- interlignages ;
- espacements de lettres ;
- hiérarchie ;
- styles de chiffres ;
- styles financiers ;
- styles techniques.

---

# 17. Hiérarchie typographique

Exemples :

```text
Display
Heading 1
Heading 2
Heading 3
Heading 4
Body Large
Body Medium
Body Small
Label
Caption
Financial Amount
Code
```

---

# 18. Affichage des montants

Les montants financiers doivent être :

- très lisibles ;
- correctement groupés ;
- associés à une devise ;
- alignés dans les tableaux ;
- compatibles avec les décimales ;
- adaptés aux grandes valeurs ;
- adaptés aux devises sans décimales ;
- accessibles aux lecteurs d’écran.

Exemples :

```text
25 000 FCFA
1 250,50 EUR
125,00 USD
```

---

# 19. Nombres et formats locaux

Le système doit gérer :

- séparateurs de milliers ;
- séparateurs décimaux ;
- symbole monétaire ;
- code de devise ;
- position du symbole ;
- formats de date ;
- formats d’heure ;
- numéros de téléphone ;
- formats locaux.

---

# 20. Espacements

Le Design System doit utiliser une échelle cohérente.

Exemple :

```text
spacing.0
spacing.1
spacing.2
spacing.3
spacing.4
spacing.6
spacing.8
spacing.12
spacing.16
spacing.24
```

---

# 21. Grilles

Le système doit prévoir :

- grille mobile ;
- grille tablette ;
- grille desktop ;
- grille large écran ;
- grille terminal ;
- grille DAB ;
- grilles de tableaux ;
- zones sécurisées.

---

# 22. Responsive design

Les interfaces doivent s’adapter à :

- petits téléphones ;
- grands téléphones ;
- tablettes ;
- ordinateurs portables ;
- écrans desktop ;
- écrans larges ;
- terminaux tactiles ;
- TPE ;
- DAB ;
- affichage portrait ;
- affichage paysage.

---

# 23. Rayons

Les rayons doivent être centralisés.

Exemples :

```text
radius.none
radius.small
radius.medium
radius.large
radius.xlarge
radius.full
```

Les formes doivent refléter une identité moderne sans réduire la lisibilité.

---

# 24. Ombres

Les ombres doivent être utilisées avec modération pour :

- surfaces élevées ;
- menus ;
- modales ;
- cartes ;
- boutons flottants ;
- éléments drag-and-drop.

Elles ne doivent pas remplacer les bordures nécessaires.

---

# 25. Icônes

Le système doit fournir des icônes pour :

- accueil ;
- paiement ;
- transfert ;
- carte ;
- dépôt ;
- retrait ;
- QR ;
- commerçant ;
- agent ;
- TPE ;
- DAB ;
- banque ;
- Mobile Money ;
- sécurité ;
- support ;
- notification ;
- profil ;
- paramètres ;
- documents ;
- rapports ;
- filtres ;
- validation ;
- erreur.

---

# 26. Règles d’icônes

Les icônes doivent :

- partager le même style ;
- avoir des tailles standardisées ;
- fonctionner en clair et sombre ;
- rester compréhensibles ;
- disposer d’un label accessible ;
- ne pas être utilisées seules lorsqu’elles sont ambiguës ;
- respecter la direction du texte.

---

# 27. Illustrations

Les illustrations peuvent être utilisées pour :

- onboarding ;
- état vide ;
- réussite ;
- échec ;
- maintenance ;
- sécurité ;
- éducation ;
- commerce ;
- services publics ;
- assistance ;
- campagnes.

Elles doivent représenter la diversité des utilisateurs de manière respectueuse.

---

# 28. Images et photographies

Les images doivent respecter :

- qualité ;
- droits d’utilisation ;
- cohérence visuelle ;
- poids optimisé ;
- responsive ;
- texte alternatif ;
- cadrage ;
- diversité ;
- sécurité ;
- absence d’informations sensibles.

---

# 29. Composants fondamentaux

Le Design System doit inclure :

- Button ;
- IconButton ;
- Link ;
- TextField ;
- TextArea ;
- Select ;
- Checkbox ;
- Radio ;
- Switch ;
- Slider ;
- DatePicker ;
- TimePicker ;
- SearchField ;
- Badge ;
- Chip ;
- Tooltip ;
- Divider ;
- Avatar ;
- Progress ;
- Spinner ;
- Skeleton ;
- Alert ;
- Toast ;
- Modal ;
- Drawer ;
- BottomSheet ;
- Tabs ;
- Accordion ;
- Pagination.

---

# 30. Boutons

Variantes possibles :

- primaire ;
- secondaire ;
- tertiaire ;
- texte ;
- danger ;
- succès ;
- icône ;
- flottant ;
- plein écran ;
- compact.

---

# 31. États des boutons

Chaque bouton doit gérer :

- normal ;
- hover ;
- focus ;
- active ;
- loading ;
- disabled ;
- success ;
- error.

---

# 32. Boutons financiers sensibles

Les actions comme :

- payer ;
- envoyer ;
- retirer ;
- rembourser ;
- bloquer ;
- supprimer ;
- confirmer ;
- valider un règlement ;

doivent être clairement différenciées.

Une action irréversible doit être explicitement signalée.

---

# 33. Champs de formulaire

Les champs doivent gérer :

- label ;
- placeholder ;
- aide ;
- erreur ;
- succès ;
- valeur ;
- préfixe ;
- suffixe ;
- icône ;
- obligatoire ;
- lecture seule ;
- désactivé ;
- chargement ;
- masquage.

---

# 34. Champs financiers

Exemples :

- montant ;
- devise ;
- numéro de compte ;
- carte ;
- bénéficiaire ;
- référence ;
- commission ;
- frais ;
- taxe ;
- taux.

Les formats doivent être validés visuellement et techniquement.

---

# 35. Saisie de montant

Le composant doit :

- afficher la devise ;
- appliquer le bon séparateur ;
- empêcher les caractères invalides ;
- gérer les limites ;
- afficher les frais ;
- afficher le total ;
- signaler le solde insuffisant ;
- rester utilisable avec un clavier numérique.

---

# 36. Sélecteurs

Les sélecteurs doivent gérer :

- recherche ;
- grandes listes ;
- regroupement ;
- favori ;
- récent ;
- pays ;
- devise ;
- bénéficiaire ;
- commerçant ;
- compte ;
- partenaire ;
- statut.

---

# 37. Cartes d’interface

Types possibles :

- carte de compte ;
- carte bancaire ;
- carte virtuelle ;
- carte transaction ;
- carte commerçant ;
- carte agent ;
- carte produit ;
- carte statistique ;
- carte action ;
- carte notification ;
- carte document ;
- carte institution.

---

# 38. Représentation des cartes bancaires

Le composant carte doit permettre :

- carte physique ;
- carte virtuelle ;
- carte temporaire ;
- carte professionnelle ;
- carte étudiante ;
- carte premium ;
- carte bloquée ;
- carte expirée ;
- carte en commande.

Les données sensibles doivent rester masquées.

---

# 39. Tableaux

Le système doit fournir :

- tableau simple ;
- tableau triable ;
- tableau filtrable ;
- tableau paginé ;
- tableau sélectionnable ;
- tableau avec actions ;
- tableau financier ;
- tableau de rapprochement ;
- tableau de logs ;
- tableau de permissions.

---

# 40. Tableaux sur mobile

Sur petit écran, un tableau peut devenir :

- liste ;
- cartes ;
- vue condensée ;
- défilement horizontal contrôlé ;
- vue détail séparée.

---

# 41. Navigation mobile

Éléments possibles :

- barre inférieure ;
- en-tête ;
- bouton retour ;
- menu profil ;
- actions rapides ;
- navigation contextuelle ;
- raccourcis ;
- bouton central d’action.

---

# 42. Navigation web

Éléments possibles :

- barre latérale ;
- barre supérieure ;
- fil d’Ariane ;
- menu contextuel ;
- onglets ;
- recherche globale ;
- raccourcis ;
- centre de notifications ;
- sélecteur d’organisation.

---

# 43. Navigation TPE

La navigation TPE doit privilégier :

- gros boutons ;
- parcours courts ;
- montant visible ;
- accès rapide au paiement ;
- accès rapide au remboursement ;
- historique ;
- clôture ;
- paramètres ;
- assistance ;
- mode hors ligne.

---

# 44. Navigation DAB

La navigation DAB doit privilégier :

- choix de langue immédiat ;
- gros textes ;
- fort contraste ;
- peu d’options par écran ;
- boutons physiques ou tactiles ;
- minuterie ;
- confidentialité ;
- assistance ;
- retour de carte ;
- récupération des billets.

---

# 45. Modales

Les modales doivent être réservées aux informations ou actions nécessitant une interruption.

Elles doivent prévoir :

- titre ;
- description ;
- action principale ;
- action secondaire ;
- fermeture ;
- focus ;
- clavier ;
- lecteur d’écran ;
- petits écrans.

---

# 46. Bottom sheets

Sur mobile, les bottom sheets peuvent être utilisés pour :

- choix de compte ;
- choix de bénéficiaire ;
- filtres ;
- actions rapides ;
- détails ;
- confirmation ;
- sélection de carte.

---

# 47. Notifications visuelles

Types :

- toast ;
- snackbar ;
- bannière ;
- alerte inline ;
- modale ;
- badge ;
- message de page ;
- état global.

---

# 48. Toasts

Les toasts doivent :

- être courts ;
- disparaître automatiquement lorsque possible ;
- rester accessibles ;
- ne pas contenir une décision critique ;
- proposer une action éventuelle ;
- ne pas masquer un bouton important.

---

# 49. Alertes

Variantes :

- information ;
- succès ;
- avertissement ;
- erreur ;
- sécurité ;
- fraude ;
- maintenance ;
- réglementaire.

---

# 50. États de chargement

Le système doit prévoir :

- spinner ;
- skeleton ;
- progression ;
- étape en cours ;
- chargement silencieux ;
- attente réseau ;
- synchronisation ;
- traitement financier.

---

# 51. Traitement financier en cours

Lorsqu’une opération est en cours, l’interface doit :

- empêcher les doublons ;
- afficher une progression ;
- conserver la référence ;
- permettre la reprise ;
- informer l’utilisateur ;
- ne pas annoncer un succès avant confirmation ;
- gérer les délais partenaires.

---

# 52. États vides

Chaque écran vide doit indiquer :

- ce que représente l’écran ;
- pourquoi il est vide ;
- ce que l’utilisateur peut faire ;
- une action claire ;
- une illustration éventuelle ;
- une aide.

---

# 53. États d’erreur

Les erreurs doivent être :

- compréhensibles ;
- non techniques pour le grand public ;
- précises pour les équipes techniques ;
- accompagnées d’une action ;
- liées à une référence ;
- traduisibles ;
- accessibles.

---

# 54. Codes d’erreur

Le système doit distinguer :

- code technique interne ;
- message utilisateur ;
- message support ;
- niveau de sévérité ;
- action recommandée ;
- référence de corrélation.

---

# 55. Formulaires longs

Les formulaires longs doivent utiliser :

- étapes ;
- progression ;
- sauvegarde ;
- brouillon ;
- validation progressive ;
- résumé final ;
- retour en arrière ;
- reprise ;
- aide contextuelle.

---

# 56. Onboarding

L’onboarding doit pouvoir inclure :

- écrans d’introduction ;
- choix de langue ;
- numéro de téléphone ;
- création de compte ;
- vérification ;
- KYC ;
- code PIN ;
- biométrie ;
- préférences ;
- tutoriel ;
- première action.

---

# 57. Parcours guidés

Le Design System doit prévoir des patterns pour :

- envoyer de l’argent ;
- payer ;
- retirer ;
- déposer ;
- créer une carte ;
- bloquer une carte ;
- créer un commerce ;
- ouvrir une caisse ;
- effectuer une clôture ;
- demander une aide ;
- payer une facture ;
- verser un salaire.

---

# 58. Confirmation d’opération

Une confirmation doit afficher :

- montant ;
- devise ;
- bénéficiaire ;
- source ;
- frais ;
- total ;
- date ;
- délai ;
- référence éventuelle ;
- action principale ;
- retour possible.

Les règles spécifiques au dépôt, au retrait et aux opérations hors ligne doivent être respectées selon les modules concernés.

---

# 59. Reçu

Le composant reçu doit pouvoir afficher :

- logo ;
- type d’opération ;
- montant ;
- devise ;
- frais ;
- commission visible si applicable ;
- date ;
- heure ;
- payeur ;
- bénéficiaire masqué ;
- référence ;
- statut ;
- QR de vérification ;
- actions de partage ;
- téléchargement ;
- impression.

---

# 60. Statuts financiers

Les statuts doivent avoir une représentation cohérente :

- créée ;
- en attente ;
- autorisée ;
- terminée ;
- échouée ;
- annulée ;
- remboursée ;
- expirée ;
- en révision ;
- contestée ;
- partiellement terminée.

---

# 61. Graphiques

Le système doit fournir :

- courbe ;
- barres ;
- camembert lorsque pertinent ;
- aire ;
- histogramme ;
- jauge ;
- évolution ;
- comparaison ;
- répartition ;
- carte géographique ;
- heatmap ;
- funnel.

---

# 62. Graphiques financiers

Les graphiques doivent :

- afficher les valeurs exactes ;
- afficher la devise ;
- rester lisibles en noir et blanc ;
- utiliser des légendes ;
- éviter les effets trompeurs ;
- permettre l’export ;
- proposer une vue tableau ;
- gérer les valeurs négatives ;
- gérer les données manquantes.

---

# 63. Cartes géographiques

Elles peuvent représenter :

- agents ;
- commerces ;
- DAB ;
- incidents ;
- transactions ;
- liquidité ;
- couverture ;
- utilisateurs ;
- établissements ;
- services publics.

---

# 64. Animations

Le système doit définir :

- durées ;
- accélérations ;
- transitions ;
- apparitions ;
- disparitions ;
- déplacements ;
- transformations ;
- feedbacks tactiles ;
- micro-interactions.

---

# 65. Tokens d’animation

Exemples :

```text
motion.duration.instant
motion.duration.fast
motion.duration.normal
motion.duration.slow
motion.easing.standard
motion.easing.enter
motion.easing.exit
```

---

# 66. Micro-interactions

Exemples :

- bouton pressé ;
- carte sélectionnée ;
- paiement réussi ;
- QR détecté ;
- carte bloquée ;
- copie réussie ;
- chargement ;
- actualisation ;
- validation de champ ;
- navigation.

---

# 67. Animation de réussite

Elle doit être :

- courte ;
- claire ;
- non ambiguë ;
- accompagnée d’un texte ;
- désactivable ou réduite ;
- déclenchée uniquement après confirmation réelle.

---

# 68. Animation d’échec

Elle doit :

- signaler clairement l’échec ;
- éviter l’agressivité ;
- expliquer l’action suivante ;
- conserver les données saisies lorsque possible ;
- afficher une référence si nécessaire.

---

# 69. Réduction des animations

Le système doit respecter les préférences de réduction des mouvements.

Lorsque cette option est active :

- réduire les transitions ;
- supprimer les effets de profondeur ;
- éviter les mouvements rapides ;
- conserver uniquement les feedbacks utiles.

---

# 70. Haptique

Sur mobile ou terminal compatible, le retour haptique peut être utilisé pour :

- confirmation ;
- erreur ;
- sélection ;
- scan QR ;
- paiement ;
- action critique.

Il doit rester discret et configurable.

---

# 71. Sons

Les sons peuvent être utilisés pour :

- paiement réussi ;
- erreur ;
- scan ;
- notification ;
- alerte TPE ;
- assistance DAB.

Ils doivent être :

- désactivables ;
- adaptés au contexte ;
- non intrusifs ;
- accompagnés d’un retour visuel.

---

# 72. Accessibilité visuelle

Le système doit garantir :

- contraste suffisant ;
- taille minimale ;
- zoom ;
- focus visible ;
- textes lisibles ;
- zones tactiles suffisantes ;
- absence de dépendance à la couleur ;
- alternatives aux images.

---

# 73. Accessibilité clavier

Les interfaces web doivent être entièrement utilisables avec :

- Tab ;
- Shift + Tab ;
- Entrée ;
- Espace ;
- Échap ;
- touches directionnelles ;
- raccourcis documentés.

---

# 74. Lecteurs d’écran

Les composants doivent prévoir :

- labels ;
- rôles ;
- descriptions ;
- ordre logique ;
- annonces dynamiques ;
- erreurs accessibles ;
- statut des opérations ;
- titres ;
- alternatives textuelles.

---

# 75. Zones tactiles

Les zones tactiles doivent être suffisamment grandes pour :

- téléphone ;
- tablette ;
- TPE ;
- DAB ;
- utilisateurs avec difficultés motrices.

---

# 76. Mode texte agrandi

Le système doit supporter :

- taille système ;
- agrandissement ;
- reflow ;
- boutons adaptatifs ;
- tableaux convertis ;
- modales adaptatives ;
- textes longs.

---

# 77. Langues et direction du texte

Le système doit gérer :

- français ;
- bambara ;
- anglais ;
- arabe ;
- langues nationales ;
- langues futures ;
- texte de gauche à droite ;
- texte de droite à gauche.

---

# 78. Contenus

Le Design System doit fournir des règles pour :

- titres ;
- boutons ;
- erreurs ;
- confirmations ;
- aides ;
- notifications ;
- reçus ;
- textes juridiques ;
- messages de sécurité ;
- messages commerciaux.

---

# 79. Ton de Mansa

Le ton doit être :

- clair ;
- respectueux ;
- professionnel ;
- rassurant ;
- direct ;
- non infantilisant ;
- compréhensible ;
- adapté au contexte.

---

# 80. Rédaction des boutons

Préférer des actions explicites :

```text
Envoyer l’argent
Payer maintenant
Bloquer la carte
Télécharger le reçu
Demander un remboursement
```

Éviter les termes vagues lorsque l’action est importante.

---

# 81. Messages d’erreur

Un message d’erreur doit répondre à trois questions :

1. Que s’est-il passé ?
2. Pourquoi, lorsque l’information est disponible ?
3. Que faire maintenant ?

---

# 82. Réseau faible

Les composants doivent prévoir :

- chargement progressif ;
- images optimisées ;
- faible poids ;
- cache ;
- skeleton ;
- reprise ;
- sauvegarde locale ;
- synchronisation ;
- mode texte ;
- absence d’animation lourde ;
- retour clair sur la connexion.

---

# 83. Mode hors ligne

Le Design System doit fournir des patterns pour :

- statut hors ligne ;
- opération en attente ;
- brouillon local ;
- synchronisation ;
- conflit ;
- nouvelle tentative ;
- opération non disponible ;
- dernière mise à jour.

---

# 84. Performance

Les composants doivent être conçus pour :

- chargement rapide ;
- rendu fluide ;
- faible consommation mémoire ;
- faible consommation réseau ;
- listes longues ;
- pagination ;
- virtualisation ;
- images optimisées ;
- animations légères.

---

# 85. Mode Démo, Recette et Production

Chaque environnement doit être clairement identifiable.

Exemples :

- bannière Démo ;
- bannière Recette ;
- badge environnement ;
- couleurs d’avertissement ;
- données fictives ;
- actions limitées.

La Production doit rester visuellement distincte des environnements de test.

---

# 86. Composants administratifs

Le Design System doit inclure :

- tableau avancé ;
- filtre ;
- recherche ;
- sélecteur de pays ;
- sélecteur d’organisation ;
- éditeur de permissions ;
- audit timeline ;
- diff ancienne/nouvelle valeur ;
- approbation ;
- double validation ;
- export ;
- alerte critique ;
- graphique ;
- console de logs.

---

# 87. Composants de sécurité

Exemples :

- score de risque ;
- niveau de sévérité ;
- timeline d’incident ;
- graphe de relations ;
- preuve ;
- restriction ;
- appareil ;
- session ;
- blocage ;
- alerte ;
- playbook.

---

# 88. Composants Finance

Exemples :

- compte ledger ;
- écriture ;
- débit/crédit ;
- balance ;
- rapprochement ;
- écart ;
- règlement ;
- cantonnement ;
- liquidité ;
- clôture ;
- taux ;
- commission ;
- taxe.

---

# 89. Composants Support

Exemples :

- ticket ;
- conversation ;
- file ;
- priorité ;
- SLA ;
- note interne ;
- vue client masquée ;
- macro ;
- satisfaction ;
- escalade ;
- incident lié.

---

# 90. Composants scolaires

Exemples :

- étudiant ;
- carte étudiante ;
- facture ;
- échéancier ;
- bourse ;
- inscription ;
- logement ;
- bibliothèque ;
- transport ;
- parent.

---

# 91. Composants entreprises

Exemples :

- employé ;
- paie ;
- carte professionnelle ;
- note de frais ;
- budget ;
- centre de coûts ;
- fournisseur ;
- validation hiérarchique.

---

# 92. Composants partenaires

Exemples :

- API key ;
- webhook ;
- environnement ;
- certificat ;
- métrique ;
- incident ;
- règlement ;
- fichier ;
- rapprochement ;
- quota.

---

# 93. Templates

Le Design System doit fournir des templates pour :

- connexion ;
- inscription ;
- tableau de bord ;
- liste ;
- détail ;
- formulaire ;
- tunnel financier ;
- confirmation ;
- reçu ;
- paramètres ;
- rapport ;
- incident ;
- erreur ;
- maintenance ;
- écran vide ;
- page publique ;
- page partenaire.

---

# 94. Templates de paiement

Exemples :

```text
Sélection du moyen
→ saisie ou scan
→ vérification
→ frais et total
→ confirmation selon le parcours
→ traitement
→ résultat
→ reçu
```

---

# 95. Templates de transaction

Les applications doivent partager une structure commune pour :

- icône ;
- type ;
- montant ;
- devise ;
- date ;
- statut ;
- contrepartie ;
- référence ;
- frais ;
- reçu ;
- aide ;
- contestation.

---

# 96. Documents numériques

Le système doit fournir des modèles pour :

- reçu ;
- facture ;
- relevé ;
- rapport ;
- attestation ;
- contrat ;
- document institutionnel ;
- notification officielle ;
- document scolaire.

---

# 97. Impression

Les composants imprimables doivent gérer :

- A4 ;
- ticket thermique ;
- reçu TPE ;
- reçu DAB ;
- noir et blanc ;
- QR ;
- signature ;
- marges ;
- pagination ;
- coupures de page ;
- densité d’information.

---

# 98. E-mails

Le Design System doit définir :

- en-tête ;
- logo ;
- titre ;
- corps ;
- bouton ;
- pied de page ;
- informations réglementaires ;
- texte brut ;
- responsive ;
- mode sombre ;
- langue ;
- lien sécurisé.

---

# 99. Administration du Design System

L’administration centrale doit pouvoir gérer :

- tokens ;
- thèmes ;
- logos ;
- illustrations ;
- composants activés ;
- variantes ;
- pays ;
- langues ;
- marques partenaires ;
- animations ;
- accessibilité ;
- modèles ;
- feature flags ;
- versions ;
- publications ;
- dépréciations.

---

# 100. Rôles

Exemples :

```text
DESIGN_SYSTEM_OWNER
DESIGN_LEAD
PRODUCT_DESIGNER
UX_WRITER
ACCESSIBILITY_SPECIALIST
BRAND_MANAGER
FRONTEND_ENGINEER
MOBILE_ENGINEER
DESIGN_SYSTEM_REVIEWER
DESIGN_SYSTEM_AUDITOR
VIEWER
```

---

# 101. Permissions

Exemples :

```text
design_system.token.read
design_system.token.manage
design_system.component.read
design_system.component.manage
design_system.theme.manage
design_system.brand.manage
design_system.translation.manage
design_system.accessibility.review
design_system.release.create
design_system.release.approve
design_system.audit.read
```

---

# 102. Versionnement

Chaque version doit contenir :

- numéro ;
- date ;
- changements ;
- composants ajoutés ;
- composants modifiés ;
- composants supprimés ;
- migrations ;
- compatibilité ;
- auteur ;
- approbateur ;
- statut.

---

# 103. Version sémantique

Exemple :

```text
MAJOR.MINOR.PATCH
```

- MAJOR : rupture importante ;
- MINOR : ajout compatible ;
- PATCH : correction compatible.

---

# 104. Statuts d’un composant

- EXPERIMENTAL ;
- BETA ;
- STABLE ;
- DEPRECATED ;
- RETIRED.

---

# 105. Dépréciation

Lorsqu’un composant est déprécié, le système doit fournir :

- raison ;
- composant de remplacement ;
- date ;
- délai de migration ;
- guide ;
- applications concernées ;
- suivi d’adoption.

---

# 106. Documentation

Chaque composant doit documenter :

- objectif ;
- anatomie ;
- variantes ;
- états ;
- comportements ;
- accessibilité ;
- contenu ;
- mobile ;
- web ;
- exemples ;
- code ;
- erreurs à éviter ;
- compatibilité.

---

# 107. Catalogue interactif

Le catalogue doit permettre :

- prévisualisation ;
- modification des propriétés ;
- changement de thème ;
- changement de langue ;
- changement d’écran ;
- état d’erreur ;
- état de chargement ;
- mode sombre ;
- accessibilité ;
- copie du code.

---

# 108. Gouvernance

Toute évolution importante doit suivre :

1. proposition ;
2. analyse ;
3. maquette ;
4. revue produit ;
5. revue technique ;
6. revue accessibilité ;
7. test ;
8. validation ;
9. publication ;
10. suivi.

---

# 109. Demande de nouveau composant

Une demande doit contenir :

- besoin ;
- application ;
- utilisateurs ;
- cas d’usage ;
- variantes ;
- alternatives étudiées ;
- accessibilité ;
- comportement ;
- priorité ;
- responsable.

---

# 110. Cohérence entre plateformes

Un même composant peut avoir des adaptations selon :

- web ;
- iOS ;
- Android ;
- TPE ;
- DAB ;
- terminal ;
- e-mail ;
- impression.

Son sens, ses états et son vocabulaire doivent rester cohérents.

---

# 111. Tests unitaires

Chaque composant doit tester :

- rendu ;
- propriétés ;
- variantes ;
- états ;
- événements ;
- erreurs ;
- clavier ;
- accessibilité ;
- thèmes ;
- langues.

---

# 112. Tests visuels

Les tests doivent détecter :

- décalage ;
- changement de couleur ;
- problème de taille ;
- débordement ;
- régression ;
- thème sombre incorrect ;
- texte tronqué ;
- icône absente ;
- responsive cassé.

---

# 113. Tests d’accessibilité

Les tests doivent vérifier :

- contraste ;
- labels ;
- focus ;
- navigation clavier ;
- lecteur d’écran ;
- ordre ;
- tailles tactiles ;
- zoom ;
- animations ;
- erreurs.

---

# 114. Tests multi-langues

Ils doivent couvrir :

- textes courts ;
- textes longs ;
- caractères spéciaux ;
- accents ;
- arabe ;
- direction RTL ;
- devise ;
- date ;
- pluralisation ;
- débordement ;
- troncature.

---

# 115. Tests de performance

Ils doivent vérifier :

- poids du package ;
- temps de rendu ;
- listes ;
- animations ;
- images ;
- mémoire ;
- chargement ;
- réseau faible ;
- appareils anciens ;
- TPE limités.

---

# 116. Tests utilisateurs

Le Design System doit être testé avec :

- clients ;
- commerçants ;
- agents ;
- étudiants ;
- employés ;
- administrateurs ;
- utilisateurs âgés ;
- utilisateurs peu familiers avec le numérique ;
- personnes en situation de handicap ;
- utilisateurs de réseau faible.

---

# 117. Analytics UX

Événements possibles :

```text
design_component_rendered
design_component_error
design_form_abandoned
design_validation_failed
design_accessibility_mode_enabled
design_dark_mode_enabled
design_language_changed
design_offline_state_shown
design_retry_action_used
design_help_opened
```

---

# 118. Données analytics interdites

Ne pas transmettre :

- PIN ;
- OTP ;
- CVV ;
- numéro complet de carte ;
- mot de passe ;
- contenu complet d’un champ sensible ;
- document ;
- donnée biométrique ;
- secret API ;
- clé privée ;
- message privé ;
- donnée financière complète inutile.

---

# 119. Sécurité

Le Design System doit protéger :

- les champs sensibles ;
- les captures ;
- le copier-coller lorsque nécessaire ;
- les aperçus ;
- les écrans verrouillés ;
- les données masquées ;
- les liens ;
- les documents ;
- les composants administratifs ;
- les actions critiques.

---

# 120. Audit

Les modifications centrales doivent enregistrer :

- utilisateur ;
- rôle ;
- composant ;
- token ;
- thème ;
- ancienne valeur ;
- nouvelle valeur ;
- date ;
- heure ;
- environnement ;
- motif ;
- approbateur ;
- version ;
- résultat.

---

# 121. Modèles principaux

- DesignToken
- DesignTokenGroup
- BrandTheme
- ThemeVariant
- TypographyStyle
- ColorPalette
- SpacingScale
- RadiusScale
- ShadowStyle
- IconAsset
- IllustrationAsset
- MotionToken
- DesignComponent
- ComponentVariant
- ComponentState
- DesignPattern
- DesignTemplate
- AccessibilityRule
- LocalizationRule
- BrandCustomization
- DesignSystemRelease
- ComponentDeprecation
- DesignSystemApproval
- DesignSystemAudit

---

# 122. Règles métier

1. Toutes les applications utilisent les fondations communes.
2. Les valeurs principales proviennent de tokens.
3. Les couleurs sont sémantiques.
4. La couleur seule ne suffit pas à indiquer un état.
5. Les montants restent toujours lisibles.
6. Les frais et devises sont clairement affichés.
7. Les actions critiques sont explicites.
8. Les composants prennent en charge le mode sombre.
9. Les composants respectent les préférences système.
10. Les interfaces restent utilisables sur réseau faible.
11. Les animations ne doivent pas gêner la compréhension.
12. La réduction des mouvements est prise en charge.
13. Les composants sont accessibles au clavier.
14. Les lecteurs d’écran sont pris en charge.
15. Les zones tactiles sont suffisamment grandes.
16. Les langues et formats locaux sont pris en charge.
17. Les environnements de test sont clairement identifiables.
18. Les composants sont versionnés.
19. Les composants dépréciés possèdent une migration.
20. Les évolutions importantes utilisent une validation.
21. Les modèles sont documentés.
22. Les régressions visuelles sont testées.
23. Les données sensibles restent masquées.
24. Les modifications centrales sont auditées.
25. L’identité Mansa reste cohérente sur toutes les plateformes.

---

# 123. Critères d’acceptation

Le Design System Mansa est validé lorsque :

- l’identité visuelle est définie ;
- le logo possède toutes ses variantes ;
- les couleurs sont tokenisées ;
- les thèmes clair et sombre sont disponibles ;
- la personnalisation partenaire est encadrée ;
- la typographie est documentée ;
- les montants sont correctement affichés ;
- les espacements et grilles sont normalisés ;
- le responsive fonctionne ;
- les icônes sont cohérentes ;
- les illustrations sont encadrées ;
- les composants fondamentaux sont disponibles ;
- les boutons possèdent tous leurs états ;
- les champs financiers sont sécurisés ;
- les cartes et tableaux sont adaptatifs ;
- la navigation mobile est définie ;
- la navigation web est définie ;
- les TPE et DAB possèdent des règles adaptées ;
- les modales et bottom sheets sont accessibles ;
- les états de chargement sont cohérents ;
- les états d’erreur sont clairs ;
- les formulaires longs sont pris en charge ;
- les parcours financiers sont standardisés ;
- les reçus sont uniformisés ;
- les statuts financiers sont cohérents ;
- les graphiques sont accessibles ;
- les animations sont tokenisées ;
- la réduction des mouvements fonctionne ;
- l’haptique et les sons sont encadrés ;
- l’accessibilité visuelle est respectée ;
- la navigation clavier fonctionne ;
- les lecteurs d’écran sont pris en charge ;
- le texte agrandi fonctionne ;
- le RTL est pris en charge ;
- les règles de contenu sont définies ;
- le mode réseau faible est prévu ;
- le mode hors ligne est cohérent ;
- les composants sont performants ;
- les environnements sont clairement distingués ;
- les composants spécialisés sont disponibles ;
- les templates sont documentés ;
- les documents et e-mails sont uniformisés ;
- l’administration centrale peut gérer les thèmes ;
- les rôles et permissions sont définis ;
- le versionnement est opérationnel ;
- les dépréciations sont contrôlées ;
- la documentation interactive est disponible ;
- la gouvernance est définie ;
- les tests unitaires sont couverts ;
- les tests visuels sont couverts ;
- les tests d’accessibilité sont couverts ;
- les tests multi-langues sont couverts ;
- les tests de performance sont couverts ;
- les modifications sont auditées.
