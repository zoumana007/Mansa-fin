# 04 — Design System global de Mansa

## 1. Objet du document

Ce document définit le système de design officiel de Mansa.

Il sert de référence commune pour :

- Mansa Client ;
- Mansa Commerce ;
- Mansa TPE ;
- Mansa Admin Lite ;
- Mansa Annuaire / Hub ;
- le site public Mansa ;
- le site Mansa Professionnels ;
- le portail Admin Web ;
- les documents numériques ;
- les reçus ;
- les notifications ;
- les interfaces partenaires.

Le Design System doit garantir :

- une identité visuelle cohérente ;
- une expérience premium ;
- une meilleure vitesse de développement ;
- une accessibilité constante ;
- une maintenance simplifiée ;
- une personnalisation contrôlée ;
- une adaptation multi-pays ;
- une compatibilité mobile, web et TPE.

---

# 2. Principes fondamentaux

## 2.1 Cohérence

Une même action doit conserver :

- le même sens ;
- la même terminologie ;
- le même comportement ;
- le même niveau de priorité ;
- la même logique visuelle.

Exemple :

Le bouton de validation principal doit rester identifiable comme action principale dans toutes les applications.

## 2.2 Simplicité

L’interface doit présenter en priorité :

- l’information essentielle ;
- l’action attendue ;
- le statut réel ;
- les erreurs compréhensibles ;
- les éléments de sécurité nécessaires.

Les détails secondaires doivent rester accessibles sans surcharger l’écran.

## 2.3 Confiance

Une fintech doit inspirer immédiatement confiance.

Le design doit éviter :

- les messages ambigus ;
- les animations excessives pendant une opération financière ;
- les couleurs trompeuses ;
- les confirmations prématurées ;
- les interfaces ressemblant à des jeux ;
- les effets visuels qui masquent un statut réel.

## 2.4 Clarté financière

Chaque montant doit afficher clairement :

- la valeur ;
- la devise ;
- le signe ;
- la nature du mouvement ;
- les frais éventuels ;
- le statut ;
- la date ;
- le bénéficiaire ou l’émetteur.

Les montants ne doivent jamais être confondus avec des points, récompenses ou valeurs estimées.

## 2.5 Accessibilité

Tous les composants doivent être conçus pour :

- VoiceOver ;
- TalkBack ;
- navigation clavier ;
- tailles de police dynamiques ;
- contraste suffisant ;
- lecteur d’écran ;
- daltonisme ;
- réduction des animations ;
- utilisateurs peu familiers avec la technologie.

## 2.6 Performance

Une interface premium ne doit pas être lourde.

Les animations, ombres, 3D, gradients et effets doivent être :

- progressifs ;
- chargés à la demande ;
- désactivables ;
- remplacés par des fallbacks simples ;
- adaptés aux appareils moins puissants.

# 3. Identité visuelle de Mansa

## 3.1 Positionnement

Mansa doit transmettre :

- modernité ;
- sécurité ;
- ambition ;
- proximité ;
- innovation ;
- sérieux ;
- accessibilité ;
- identité africaine contemporaine ;
- puissance financière ;
- élégance.

L’identité ne doit pas copier directement une banque, une fintech ou une marque existante.

## 3.2 Direction artistique

Le style général doit combiner :

- minimalisme premium ;
- surfaces propres ;
- profondeur légère ;
- contrastes maîtrisés ;
- animations fluides ;
- touches technologiques ;
- éléments chaleureux ;
- iconographie simple ;
- lecture immédiate.

## 3.3 Logo

Le logo Mansa doit exister en plusieurs versions :

- principal ;
- horizontal ;
- vertical ;
- symbole seul ;
- monochrome sombre ;
- monochrome clair ;
- version petite taille ;
- version animation ;
- version application ;
- version favicon ;
- version imprimable.

Chaque version doit définir :

- zone de protection ;
- taille minimale ;
- fond autorisé ;
- fond interdit ;
- alignement ;
- variantes de couleur.

## 3.4 Utilisations interdites du logo

Il est interdit de :

- déformer le logo ;
- modifier ses proportions ;
- changer ses couleurs librement ;
- ajouter des contours non prévus ;
- appliquer des ombres excessives ;
- placer le logo sur un fond illisible ;
- ajouter un effet 3D non validé ;
- le combiner à un autre logo sans règle partenaire ;
- utiliser une ancienne version.

# 4. Couleurs

## 4.1 Structure des couleurs

Le système doit distinguer :

- couleurs de marque ;
- couleurs sémantiques ;
- couleurs neutres ;
- couleurs de surface ;
- couleurs de texte ;
- couleurs de statut ;
- couleurs de graphiques ;
- couleurs spécifiques par produit ;
- couleurs partenaires ;
- couleurs de pays lorsque nécessaire.

## 4.2 Palette principale

La palette officielle doit utiliser des tokens, par exemple :

```text
brand.primary
brand.primary.hover
brand.primary.active
brand.primary.subtle
brand.secondary
brand.accent
brand.onPrimary
```

Les valeurs exactes pourront évoluer sans obliger les composants à être réécrits.

## 4.3 Couleurs sémantiques

Tokens minimum :

```text
success
success.subtle
warning
warning.subtle
danger
danger.subtle
info
info.subtle
neutral
```

Utilisation :

- succès : opération confirmée ;
- avertissement : risque ou attention ;
- danger : erreur, suppression, blocage ;
- information : conseil ou contexte ;
- neutre : état sans priorité particulière.

## 4.4 Couleurs financières

Les couleurs ne doivent jamais être l’unique moyen de compréhension.

Exemples :

- entrée d’argent : signe positif + libellé + couleur ;
- sortie d’argent : signe négatif + libellé + couleur ;
- transaction en attente : icône + texte + couleur ;
- transaction échouée : icône + statut + message.

## 4.5 Couleurs neutres

Échelle recommandée :

```text
neutral.0
neutral.50
neutral.100
neutral.200
neutral.300
neutral.400
neutral.500
neutral.600
neutral.700
neutral.800
neutral.900
neutral.950
```

Utilisations :

- arrière-plans ;
- bordures ;
- textes secondaires ;
- séparateurs ;
- états désactivés ;
- surfaces.

## 4.6 Mode clair et mode sombre

Chaque token doit avoir une valeur adaptée au thème.

Le mode sombre ne doit pas être une simple inversion.

Il doit préserver :

- contraste ;
- hiérarchie ;
- lisibilité ;
- confort ;
- identité ;
- distinction des surfaces.

## 4.7 Couleurs personnalisables

L’administration peut autoriser certaines personnalisations :

- thème d’un commerce ;
- couleur d’un mini-site ;
- couleur d’un reçu ;
- thème d’une campagne ;
- couleur d’un programme de fidélité.

Les personnalisations doivent rester dans une plage accessible et ne doivent pas modifier les couleurs critiques de sécurité.

# 5. Typographie

## 5.1 Principes

La typographie doit être :

- lisible ;
- moderne ;
- adaptée au français et aux langues africaines prévues ;
- compatible avec les chiffres ;
- claire pour les montants ;
- performante ;
- disponible sur web et mobile.

## 5.2 Hiérarchie

Échelle recommandée :

```text
display.large
display.medium
display.small

heading.h1
heading.h2
heading.h3
heading.h4
heading.h5
heading.h6

body.large
body.medium
body.small

label.large
label.medium
label.small

caption
overline
```

## 5.3 Chiffres et montants

Les montants doivent utiliser :

- chiffres tabulaires lorsque nécessaire ;
- alignement cohérent ;
- séparateurs locaux ;
- symbole ou code de devise ;
- précision adaptée à la devise ;
- contraste suffisant.

Exemple :

```text
125 000 FCFA
1 250,50 EUR
$1,250.50
```

## 5.4 Graisses

Graisses recommandées :

- Regular ;
- Medium ;
- SemiBold ;
- Bold.

Les graisses très fines sont interdites pour les informations importantes.

## 5.5 Longueur des textes

Les interfaces doivent éviter :

- les paragraphes très longs ;
- les phrases techniques ;
- les messages d’erreur complexes ;
- les labels ambigus ;
- les titres trop larges.

# 6. Espacements

## 6.1 Échelle

Échelle recommandée :

```text
space.0
space.1
space.2
space.3
space.4
space.5
space.6
space.8
space.10
space.12
space.16
space.20
space.24
```

Chaque valeur doit correspondre à un multiple cohérent.

## 6.2 Règles

- Ne pas utiliser de valeurs arbitraires sans justification.
- Conserver une respiration suffisante.
- Réduire les espacements sur TPE compact.
- Augmenter les zones tactiles sur mobile.
- Éviter les interfaces trop denses pour les particuliers.
- Autoriser des vues denses dans le portail Admin.

# 7. Rayons, bordures et ombres

## 7.1 Rayons

Tokens recommandés :

```text
radius.none
radius.xs
radius.sm
radius.md
radius.lg
radius.xl
radius.full
```

## 7.2 Bordures

Types :

- bordure standard ;
- bordure focus ;
- bordure erreur ;
- bordure succès ;
- bordure sélection ;
- séparateur.

Les bordures doivent rester visibles en mode sombre.

## 7.3 Ombres

Niveaux :

```text
shadow.none
shadow.sm
shadow.md
shadow.lg
shadow.overlay
shadow.floating
```

Les ombres excessives sont interdites dans les écrans financiers sensibles.

# 8. Grille et responsive

## 8.1 Mobile

Priorité :

- une colonne ;
- actions importantes accessibles au pouce ;
- zones tactiles suffisantes ;
- navigation simple ;
- contenu essentiel visible rapidement.

## 8.2 Tablette

Utilisations :

- deux colonnes ;
- panneaux latéraux ;
- tableaux adaptés ;
- vues détaillées ;
- caisse ;
- administration légère.

## 8.3 Desktop

Utilisations :

- grilles multiples ;
- navigation latérale ;
- tableaux ;
- filtres ;
- panneaux simultanés ;
- dashboards ;
- outils d’administration.

## 8.4 TPE

Contraintes :

- écran variable ;
- usage debout ;
- interactions rapides ;
- gants éventuels ;
- luminosité forte ;
- saisie répétée ;
- imprimante ;
- bouton retour matériel possible.

## 8.5 Breakpoints

Les breakpoints doivent être centralisés dans les tokens et non définis séparément dans chaque application.

# 9. Iconographie

## 9.1 Style

Les icônes doivent être :

- simples ;
- cohérentes ;
- reconnaissables ;
- accessibles ;
- lisibles en petite taille ;
- non décoratives lorsqu’elles portent un sens.

## 9.2 Familles

Prévoir :

- navigation ;
- paiement ;
- sécurité ;
- carte ;
- transfert ;
- commerce ;
- support ;
- documents ;
- administration ;
- messages ;
- localisation ;
- statut ;
- analytics.

## 9.3 Icônes critiques

Les icônes critiques doivent toujours être accompagnées de texte lorsque le risque de mauvaise interprétation existe.

Exemples :

- supprimer ;
- bloquer ;
- rembourser ;
- opposer une carte ;
- valider un paiement ;
- fermer un compte.

## 9.4 Animations d’icônes

Autorisées pour :

- chargement ;
- succès ;
- synchronisation ;
- notification ;
- scan ;
- connexion NFC.

Elles doivent rester courtes et désactivables.

# 10. Illustrations et images

## 10.1 Illustrations

Les illustrations doivent :

- respecter l’identité Mansa ;
- représenter la diversité ;
- éviter les clichés ;
- rester modernes ;
- être légères ;
- pouvoir être désactivées dans les interfaces opérationnelles.

## 10.2 Photographies

Les photos doivent :

- être authentiques ;
- être correctement licenciées ;
- éviter les banques d’images trop artificielles ;
- respecter la confidentialité ;
- être optimisées ;
- avoir un texte alternatif.

## 10.3 Images de commerces

Les professionnels peuvent publier :

- logo ;
- bannière ;
- photos ;
- produits ;
- services.

Le système doit prévoir :

- recadrage ;
- compression ;
- modération ;
- formats autorisés ;
- suppression ;
- ordre ;
- droits d’utilisation.

# 11. Animations et mouvements

## 11.1 Principes

Les animations doivent :

- expliquer un changement ;
- guider l’attention ;
- confirmer une action ;
- rendre la navigation fluide ;
- améliorer la perception de qualité.

Elles ne doivent pas ralentir une opération.

## 11.2 Durées

Tokens recommandés :

```text
motion.instant
motion.fast
motion.normal
motion.slow
motion.cinematic
```

Les interfaces financières utilisent principalement les durées rapides et normales.

## 11.3 Courbes

Prévoir des courbes centralisées :

```text
easing.standard
easing.enter
easing.exit
easing.emphasized
easing.linear
```

## 11.4 Animations autorisées

- apparition ;
- disparition ;
- déplacement ;
- changement d’état ;
- skeleton ;
- progression ;
- feedback haptique ;
- transition de page ;
- carte 3D ;
- scroll storytelling sur les sites ;
- animation de graphiques.

## 11.5 Animations interdites

- succès avant confirmation backend ;
- animation longue pendant un paiement ;
- clignotement agressif ;
- mouvement continu inutile ;
- rotation infinie sans statut ;
- vibration excessive ;
- animation qui empêche la lecture ;
- animation qui masque une erreur.

## 11.6 Réduction des animations

Le système doit respecter :

- `prefers-reduced-motion` ;
- réglage interne ;
- contraintes de performance ;
- batterie faible ;
- appareils limités.

# 12. Sons et haptics

## 12.1 Haptics

Utilisations possibles :

- pression d’un bouton ;
- erreur ;
- succès ;
- scan ;
- confirmation ;
- paiement NFC.

## 12.2 Sons

Les sons doivent être optionnels sauf contraintes matérielles particulières.

Cas possibles :

- paiement accepté ;
- paiement refusé ;
- scan ;
- alerte terminal ;
- impression terminée.

Les sons ne doivent jamais être l’unique confirmation.

# 13. Composants de base

## 13.1 Boutons

Types :

- principal ;
- secondaire ;
- tertiaire ;
- texte ;
- danger ;
- icône ;
- flottant ;
- pleine largeur ;
- compact ;
- chargement.

États :

- normal ;
- hover ;
- focus ;
- pressé ;
- désactivé ;
- chargement ;
- succès ;
- erreur.

## 13.2 Champs

Types :

- texte ;
- téléphone ;
- e-mail ;
- mot de passe ;
- PIN ;
- OTP ;
- montant ;
- devise ;
- date ;
- recherche ;
- sélection ;
- adresse ;
- document ;
- commentaire.

États :

- vide ;
- actif ;
- rempli ;
- invalide ;
- valide ;
- désactivé ;
- lecture seule ;
- chargement.

## 13.3 Cartes d’interface

Types :

- compte ;
- carte bancaire ;
- transaction ;
- commerce ;
- promotion ;
- message ;
- document ;
- alerte ;
- statistique ;
- service public ;
- investissement.

## 13.4 Modales

Types :

- confirmation ;
- information ;
- formulaire ;
- choix ;
- erreur ;
- action critique ;
- plein écran mobile.

Les modales imbriquées sont à éviter.

## 13.5 Toasts

Utilisés pour les retours non critiques.

Un toast ne doit pas être utilisé comme unique preuve d’une opération financière.

## 13.6 Bannières

Types :

- information ;
- avertissement ;
- sécurité ;
- maintenance ;
- campagne ;
- action requise.

## 13.7 Listes

Doivent prendre en charge :

- chargement progressif ;
- état vide ;
- erreur ;
- recherche ;
- filtre ;
- sélection ;
- actions ;
- pagination ;
- rafraîchissement.

## 13.8 Tableaux

Pour le portail Admin et les interfaces professionnelles.

Fonctions possibles :

- tri ;
- filtre ;
- recherche ;
- pagination ;
- colonnes configurables ;
- export ;
- sélection multiple ;
- actions en masse ;
- densité ;
- sticky headers.

# 14. Composants financiers spécialisés

## 14.1 Affichage de solde

Doit gérer :

- devise ;
- masquage ;
- biométrie ;
- solde disponible ;
- solde bloqué ;
- valeur estimée ;
- mise à jour ;
- hors ligne.

## 14.2 Carte bancaire visuelle

Doit afficher :

- design ;
- réseau ;
- titulaire ;
- quatre derniers chiffres ;
- statut ;
- type.

Les données sensibles sont masquées par défaut.

## 14.3 Sélecteur de montant

Doit gérer :

- clavier numérique ;
- montants rapides ;
- devise ;
- frais ;
- conversion ;
- minimum ;
- maximum ;
- solde disponible.

## 14.4 Transaction

Doit afficher :

- type ;
- montant ;
- devise ;
- signe ;
- statut ;
- bénéficiaire ;
- date ;
- icône ;
- catégorie.

## 14.5 Reçu

Doit contenir :

- référence ;
- montant ;
- devise ;
- date ;
- parties ;
- frais ;
- statut ;
- identifiant ;
- informations légales ;
- QR de vérification si nécessaire.

## 14.6 Statut financier

Statuts minimum :

- brouillon ;
- en attente ;
- en traitement ;
- réussi ;
- refusé ;
- échoué ;
- annulé ;
- remboursé ;
- contesté ;
- expiré.

# 15. Composants de sécurité

## 15.1 Saisie OTP

Doit gérer :

- collage ;
- remplissage automatique ;
- expiration ;
- renvoi ;
- compteur ;
- erreur ;
- accessibilité.

## 15.2 Saisie PIN

Doit éviter :

- journalisation ;
- affichage prolongé ;
- capture involontaire ;
- stockage en clair.

## 15.3 Biométrie

Le composant doit expliquer :

- pourquoi elle est demandée ;
- quelle action est validée ;
- quoi faire en cas d’échec ;
- alternative disponible.

## 15.4 Appareil inconnu

Écran spécifique avec :

- appareil ;
- lieu approximatif ;
- date ;
- action de confirmation ;
- action de refus ;
- support ;
- révocation.

# 16. Navigation

## 16.1 Mobile Client

Navigation principale possible :

- Accueil ;
- Paiements ;
- Cartes ;
- Mansa Connect ;
- Profil.

Elle peut être configurée selon pays, profil ou disponibilité.

## 16.2 Commerce

Navigation possible :

- Accueil ;
- Ventes ;
- Catalogue ;
- Clients ;
- Gestion.

## 16.3 Admin Lite

Navigation limitée et orientée tâches.

## 16.4 Annuaire

Navigation possible :

- Découvrir ;
- Carte ;
- Favoris ;
- Réservations ;
- Profil.

## 16.5 Portail Admin

Navigation latérale avec :

- groupes ;
- sous-menus ;
- recherche ;
- favoris ;
- historique récent ;
- raccourcis ;
- permissions.

# 17. États d’interface

Chaque écran doit prévoir :

- chargement ;
- skeleton ;
- vide ;
- erreur ;
- succès ;
- accès refusé ;
- hors ligne ;
- maintenance ;
- synchronisation ;
- contenu partiel ;
- version incompatible ;
- service indisponible.

# 18. États vides

Un état vide doit :

- expliquer pourquoi il est vide ;
- proposer une action ;
- rester visuellement simple ;
- éviter de faire croire à une erreur.

Exemple :

> Aucune transaction pour le moment.  
> Vos prochains paiements apparaîtront ici.

# 19. Messages d’erreur

Un message d’erreur doit :

- expliquer le problème ;
- éviter le jargon ;
- proposer une solution ;
- indiquer si l’action peut être recommencée ;
- inclure un identifiant de corrélation si nécessaire.

# 20. Formulaires

## 20.1 Validation

La validation doit être :

- progressive ;
- compréhensible ;
- proche du champ ;
- compatible lecteur d’écran ;
- cohérente côté client et serveur.

## 20.2 Sauvegarde

Les formulaires longs doivent prévoir :

- brouillon ;
- sauvegarde automatique ;
- reprise ;
- confirmation de sortie ;
- historique lorsque nécessaire.

## 20.3 Actions critiques

Elles exigent :

- résumé ;
- confirmation ;
- authentification ;
- délai éventuel ;
- double validation selon le risque.

# 21. Accessibilité

## 21.1 Contraste

Les contrastes doivent respecter les standards reconnus.

## 21.2 Focus

Chaque composant interactif doit avoir un focus visible.

## 21.3 Zones tactiles

Les zones tactiles doivent être suffisamment grandes.

## 21.4 Lecteurs d’écran

Chaque composant doit avoir :

- rôle ;
- nom accessible ;
- état ;
- instruction si nécessaire.

## 21.5 Ordre de lecture

L’ordre visuel et l’ordre technique doivent être cohérents.

## 21.6 Langage simple

Les libellés doivent être compréhensibles par le grand public.

# 22. Internationalisation

Le Design System doit gérer :

- textes plus longs ;
- langues de droite à gauche si ajoutées ;
- formats de date ;
- formats de nombre ;
- devises ;
- numéros ;
- pluriels ;
- noms ;
- adresses ;
- alphabets ;
- tailles de boutons adaptatives.

Aucun texte important ne doit être intégré directement dans une image.

# 23. Graphiques et données

## 23.1 Types

- ligne ;
- barre ;
- aire ;
- donut ;
- progression ;
- comparaison ;
- heatmap ;
- timeline.

## 23.2 Règles

Les graphiques doivent :

- rester lisibles ;
- avoir une légende ;
- proposer une alternative textuelle ;
- ne pas dépendre uniquement des couleurs ;
- afficher les unités ;
- gérer les valeurs nulles ;
- gérer les données partielles.

# 24. Portail Admin

Le portail Admin possède une variante du Design System plus dense.

Priorités :

- efficacité ;
- auditabilité ;
- information ;
- rapidité ;
- permissions ;
- tableaux ;
- actions en masse ;
- confirmations ;
- lisibilité.

Les animations décoratives doivent être limitées.

# 25. TPE

Le Design System TPE doit privilégier :

- gros boutons ;
- contraste élevé ;
- textes courts ;
- montants lisibles ;
- confirmation immédiate ;
- peu d’étapes ;
- retours sonores et haptiques ;
- fonctionnement faible réseau ;
- erreurs simples ;
- reprise rapide.

# 26. Sites web premium

Les sites web peuvent utiliser :

- GSAP ;
- ScrollTrigger ;
- Lenis ;
- Framer Motion ;
- Three.js ;
- React Three Fiber ;
- Drei ;
- Blender ;
- Spline si utile.

Exigences :

- fallback ;
- accessibilité ;
- lazy loading ;
- optimisation ;
- réduction des animations ;
- contrôle CPU/GPU ;
- fluidité ;
- SEO ;
- responsive.

# 27. Personnalisation

## 27.1 Utilisateur

Peut personnaliser selon autorisation :

- thème ;
- affichage ;
- ordre de widgets ;
- densité ;
- solde masqué ;
- raccourcis ;
- animations ;
- langue.

## 27.2 Commerçant

Peut personnaliser :

- logo ;
- couleurs ;
- bannière ;
- mini-site ;
- reçus ;
- promotions ;
- profil Annuaire.

## 27.3 Administration

Peut configurer :

- thèmes ;
- tokens ;
- campagnes ;
- logos partenaires ;
- contenus ;
- fonctionnalités ;
- restrictions.

Les modifications globales doivent être versionnées.

# 28. Design Tokens

Les tokens doivent être centralisés.

Catégories :

```text
color
typography
spacing
radius
shadow
motion
breakpoint
zIndex
opacity
size
icon
```

Exemple :

```json
{
  "color": {
    "brand": {
      "primary": {
        "value": "#..."
      }
    }
  }
}
```

# 29. Architecture des composants

Chaque composant doit définir :

- nom ;
- objectif ;
- variantes ;
- tailles ;
- états ;
- props ;
- accessibilité ;
- exemples ;
- limitations ;
- analytics éventuels ;
- tests ;
- version.

# 30. Versionnement du Design System

Chaque changement doit recevoir :

- version ;
- date ;
- auteur ;
- impact ;
- composants concernés ;
- guide de migration ;
- compatibilité ;
- statut.

Les changements cassants doivent être identifiés.

# 31. Gouvernance

Toute modification importante doit être validée par :

- produit ;
- design ;
- développement ;
- accessibilité ;
- sécurité lorsque concernée.

# 32. Documentation

Chaque composant doit être documenté dans un catalogue interne avec :

- aperçu ;
- code ;
- exemples ;
- variantes ;
- accessibilité ;
- erreurs fréquentes ;
- bonnes pratiques ;
- mauvaises pratiques.

# 33. Tests

## 33.1 Tests visuels

- régression visuelle ;
- thèmes ;
- tailles ;
- responsive ;
- états ;
- navigateurs.

## 33.2 Tests fonctionnels

- clic ;
- saisie ;
- focus ;
- clavier ;
- lecteur d’écran ;
- validation ;
- désactivation ;
- chargement.

## 33.3 Tests d’accessibilité

- contraste ;
- ARIA ;
- ordre ;
- focus ;
- zoom ;
- tailles dynamiques ;
- réduction des animations.

## 33.4 Tests de performance

- poids ;
- temps de rendu ;
- re-rendus ;
- images ;
- animations ;
- mémoire ;
- GPU.

# 34. Analytics UI

Les événements UI doivent être centralisés.

Exemples :

```text
button_clicked
modal_opened
form_submitted
filter_applied
tab_changed
widget_moved
theme_changed
error_displayed
```

Aucun événement ne doit contenir :

- mot de passe ;
- PIN ;
- OTP ;
- CVV ;
- numéro complet de carte ;
- contenu privé inutile.

# 35. Critères d’acceptation

Le Design System est validé lorsque :

- toutes les applications utilisent les mêmes tokens ;
- les composants principaux sont réutilisables ;
- le mode clair et sombre sont prévus ;
- les montants sont lisibles ;
- les statuts sont cohérents ;
- les composants sont accessibles ;
- les animations sont contrôlées ;
- le TPE possède une variante adaptée ;
- le portail Admin possède une variante dense ;
- les sites premium conservent de bonnes performances ;
- les personnalisations restent encadrées ;
- les composants sont documentés ;
- les tests sont prévus ;
- les changements sont versionnés.
