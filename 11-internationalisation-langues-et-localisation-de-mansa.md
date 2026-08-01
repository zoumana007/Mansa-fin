# 11 — Internationalisation, langues et localisation de Mansa

## 1. Objet du document

Ce document définit la gestion officielle des langues, traductions, formats locaux et contenus régionalisés dans Mansa.

Il s’applique à :

- Mansa Client ;
- Mansa Commerce ;
- Mansa TPE ;
- Mansa Admin Lite ;
- Mansa Annuaire / Hub ;
- le site public ;
- le site Professionnels ;
- le portail Admin Web ;
- les notifications ;
- les e-mails ;
- les SMS ;
- les reçus ;
- les factures ;
- les documents légaux ;
- les contenus de Jini ;
- les API exposant des messages utilisateur.

L’objectif est de permettre à Mansa d’être utilisé dans plusieurs pays et plusieurs langues sans dupliquer les applications ni intégrer les textes directement dans le code.

---

# 2. Principes fondamentaux

## 2.1 Aucun texte utilisateur codé en dur

Tout texte destiné à l’utilisateur doit utiliser une clé de traduction.

Exemple :

```text
payment.confirmation.title
payment.confirmation.fees
payment.status.pending
```

Le code ne doit pas contenir directement :

```text
« Paiement réussi »
```

sauf pour les messages techniques non exposés à l’utilisateur.

## 2.2 Une langue ne dépend pas uniquement du pays

Le pays du compte et la langue de l’interface sont deux informations distinctes.

Exemple :

- pays du compte : Mali ;
- devise principale : XOF ;
- langue choisie : français.

À terme, un utilisateur pourra utiliser une autre langue disponible sans changer son pays légal.

## 2.3 Langue de référence

Une langue source officielle doit être définie pour chaque contenu.

La langue de référence initiale peut être le français.

Toute traduction doit être liée à :

- une clé ;
- une version ;
- une langue source ;
- une traduction ;
- un statut ;
- un auteur ;
- une date ;
- un contexte.

## 2.4 Traduction humaine pour les contenus critiques

Les contenus suivants doivent être validés humainement :

- documents légaux ;
- messages de sécurité ;
- confirmations financières ;
- erreurs de paiement ;
- conditions tarifaires ;
- consentements ;
- messages réglementaires ;
- procédures de récupération de compte ;
- contenus liés aux investissements ;
- contenus institutionnels.

Une traduction automatique peut aider, mais ne doit pas être publiée sans validation pour ces contenus.

## 2.5 Contexte obligatoire

Une même expression peut avoir plusieurs sens.

Chaque clé doit pouvoir préciser son contexte.

Exemple :

```text
card.action.freeze
```

signifie bloquer temporairement une carte, et non supprimer ou clôturer la carte.

---

# 3. Langues supportées

Chaque langue doit posséder :

- code BCP 47 ;
- nom ;
- nom local ;
- statut ;
- sens d’écriture ;
- pays disponibles ;
- couverture ;
- date d’activation ;
- langue de secours ;
- version ;
- équipe responsable.

Exemples :

```text
fr-FR
fr-ML
en-US
en-GB
bm-ML
ar
```

L’activation réelle dépendra de la qualité des traductions disponibles.

---

# 4. Statuts d’une langue

Une langue peut être :

- brouillon ;
- en traduction ;
- en révision ;
- partiellement disponible ;
- en recette ;
- active ;
- suspendue ;
- retirée.

Une langue partielle doit indiquer clairement les produits et modules couverts.

---

# 5. Langue de secours

Lorsqu’une traduction manque, le système doit utiliser une stratégie de secours.

Exemple :

```text
bm-ML → fr-ML → fr-FR
```

Une clé manquante ne doit pas afficher directement son identifiant technique à l’utilisateur en production.

---

# 6. Sélection de la langue

La langue peut être déterminée par :

1. choix explicite de l’utilisateur ;
2. préférence enregistrée ;
3. configuration du profil ;
4. langue du système ;
5. langue du navigateur ;
6. langue par défaut du pays ;
7. langue globale de secours.

Le choix explicite de l’utilisateur reste prioritaire.

---

# 7. Changement de langue

L’utilisateur doit pouvoir changer de langue depuis les paramètres.

Le changement doit :

- être immédiat lorsque possible ;
- être conservé ;
- s’appliquer aux écrans ;
- s’appliquer aux notifications futures ;
- s’appliquer aux e-mails futurs ;
- ne pas modifier les documents déjà signés ;
- ne pas modifier la langue légale d’un consentement historique.

---

# 8. Clés de traduction

## 8.1 Convention

Format recommandé :

```text
domain.feature.element.state
```

Exemples :

```text
auth.login.title
auth.otp.expired
wallet.balance.available
payment.status.completed
merchant.stock.low
admin.user.suspend.confirmation
```

## 8.2 Règles

Les clés doivent être :

- stables ;
- explicites ;
- non liées à une position visuelle ;
- indépendantes de la langue ;
- versionnées si leur sens change.

Éviter :

```text
button1
textBlue
labelTop
```

---

# 9. Organisation des traductions

Structure possible :

```text
packages/internationalization/
├── locales/
│   ├── fr-FR/
│   ├── fr-ML/
│   ├── en-US/
│   └── bm-ML/
├── schemas/
├── formatters/
├── validators/
└── index.ts
```

Les gros domaines peuvent être séparés :

```text
auth.json
payments.json
cards.json
commerce.json
admin.json
public-services.json
```

---

# 10. Variables dans les traductions

Les textes doivent accepter des variables nommées.

Exemple :

```text
Bonjour {firstName}
```

ou :

```text
Vous allez envoyer {amount} {currency} à {recipientName}.
```

Les variables doivent être :

- validées ;
- échappées ;
- documentées ;
- disponibles dans toutes les langues concernées.

---

# 11. Pluriels

Le système doit gérer les règles de pluriel selon la langue.

Exemples :

```text
0 transaction
1 transaction
2 transactions
```

Les règles ne doivent pas être codées uniquement pour le français.

---

# 12. Genre et accords

Lorsqu’une langue l’exige, les traductions doivent pouvoir gérer :

- genre ;
- nombre ;
- forme formelle ;
- forme informelle ;
- contexte institutionnel ;
- contexte commercial.

Il est préférable de reformuler les textes pour éviter une collecte inutile de données personnelles.

---

# 13. Dates et heures

Les dates doivent respecter :

- langue ;
- pays ;
- fuseau horaire ;
- format court ;
- format long ;
- calendrier applicable ;
- convention 12 h ou 24 h.

Exemples :

```text
02/08/2026
2 août 2026
August 2, 2026
```

Les données doivent être stockées dans un format temporel normalisé.

---

# 14. Fuseaux horaires

Chaque date importante doit distinguer :

- instant UTC ;
- fuseau ;
- date locale affichée ;
- date comptable éventuelle ;
- date partenaire éventuelle.

Les actions financières ne doivent pas dépendre uniquement de l’heure affichée sur l’appareil.

---

# 15. Nombres

Les formats doivent gérer :

- séparateur décimal ;
- séparateur de milliers ;
- nombres négatifs ;
- pourcentages ;
- précision ;
- valeurs abrégées.

Exemples :

```text
1 250,50
1,250.50
12,5 %
12.5%
```

---

# 16. Devises

L’affichage doit respecter :

- code ;
- symbole ;
- position ;
- espacement ;
- décimales ;
- langue ;
- pays.

Exemples :

```text
125 000 FCFA
125 000 XOF
1 250,50 €
€1,250.50
```

La devise ne doit jamais être déduite uniquement du symbole.

---

# 17. Téléphones

Le système doit gérer :

- indicatif ;
- format international ;
- format local ;
- normalisation E.164 ;
- espaces ;
- validation ;
- pays.

Exemple stocké :

```text
+22370000000
```

L’affichage peut être localisé.

---

# 18. Adresses

Les champs d’adresse peuvent varier selon le pays.

Exemples :

- région ;
- cercle ;
- commune ;
- ville ;
- quartier ;
- rue ;
- code postal ;
- point de repère ;
- coordonnées GPS.

L’ordre des champs doit être configurable.

---

# 19. Noms des personnes

Le système ne doit pas supposer que tous les noms suivent :

```text
prénom + nom
```

Il doit permettre :

- plusieurs prénoms ;
- nom composé ;
- nom usuel ;
- ordre local ;
- absence éventuelle de prénom distinct ;
- caractères spéciaux ;
- apostrophes ;
- accents.

---

# 20. Sens d’écriture

Le système doit pouvoir évoluer vers les langues de droite à gauche.

Il faut prévoir :

- inversion des layouts ;
- alignements ;
- ordre des icônes ;
- navigation ;
- tableaux ;
- champs ;
- animations ;
- composants compatibles RTL.

Les chiffres financiers doivent rester compréhensibles.

---

# 21. Longueur des textes

Les interfaces doivent supporter des traductions plus longues que la langue source.

Exigences :

- boutons adaptatifs ;
- aucun texte important tronqué sans alternative ;
- retour à la ligne ;
- tooltip ou détail si nécessaire ;
- tests avec expansion artificielle des textes.

---

# 22. Contenus administrables

Les contenus suivants doivent être traduisibles depuis l’administration :

- pages des sites ;
- FAQ ;
- campagnes ;
- bannières ;
- promotions ;
- catégories ;
- descriptions ;
- abonnements ;
- notifications ;
- modèles d’e-mail ;
- modèles de SMS ;
- reçus ;
- formulaires ;
- documents légaux.

---

# 23. CMS multilingue

Le CMS doit permettre :

- contenu source ;
- variantes de langue ;
- statut de traduction ;
- comparaison ;
- prévisualisation ;
- programmation ;
- validation ;
- publication ;
- historique ;
- retour arrière.

Une langue ne doit pas être publiée si les champs obligatoires manquent.

---

# 24. Notifications

Chaque notification doit disposer de traductions pour :

- titre ;
- corps ;
- action ;
- texte court ;
- texte verrouillé ;
- e-mail éventuel ;
- SMS éventuel.

Les variables financières doivent être formatées dans la langue du destinataire.

---

# 25. E-mails

Les modèles d’e-mail doivent gérer :

- langue ;
- pays ;
- marque ;
- objet ;
- préheader ;
- contenu ;
- bouton ;
- pied de page ;
- mentions légales ;
- adresse de support ;
- version texte brut.

---

# 26. SMS

Les SMS doivent être :

- courts ;
- compréhensibles ;
- localisés ;
- compatibles avec les limites d’encodage ;
- dépourvus de données sensibles inutiles.

Les accents et alphabets peuvent modifier le nombre de segments SMS.

---

# 27. Reçus et factures

Les documents doivent distinguer :

- langue d’affichage ;
- langue légale ;
- devise ;
- format de date ;
- numérotation ;
- mentions obligatoires ;
- pays ;
- taxes.

Un reçu historique doit conserver la langue et la version utilisées lors de sa génération.

---

# 28. Documents légaux

Chaque document légal doit contenir :

- type ;
- pays ;
- langue ;
- version ;
- date d’effet ;
- statut ;
- contenu ;
- auteur ;
- approbateur ;
- historique ;
- empreinte ;
- date de publication.

L’utilisateur doit accepter une version clairement identifiée.

---

# 29. Jini

Jini doit :

- détecter ou utiliser la langue choisie ;
- répondre dans cette langue ;
- signaler les limites de traduction ;
- conserver le sens financier ;
- éviter les traductions ambiguës ;
- ne pas traduire librement des termes réglementaires validés sans contrôle.

---

# 30. Termes financiers officiels

Un glossaire doit définir les traductions officielles de termes comme :

- solde disponible ;
- solde comptable ;
- paiement en attente ;
- remboursement ;
- rétrofacturation ;
- plafond ;
- frais ;
- commission ;
- taux de change ;
- bénéficiaire ;
- émetteur ;
- acquéreur ;
- KYC ;
- KYB.

Ces termes doivent rester cohérents dans toutes les applications.

---

# 31. Recherche multilingue

La recherche doit pouvoir gérer :

- accents ;
- casse ;
- variantes orthographiques ;
- synonymes ;
- translittérations ;
- noms locaux ;
- fautes courantes ;
- pluriels ;
- abréviations.

Les résultats doivent toujours respecter les permissions.

---

# 32. Catégories et taxonomies

Les catégories doivent avoir :

- identifiant stable ;
- nom par langue ;
- description par langue ;
- synonymes ;
- icône ;
- statut ;
- pays ;
- ordre ;
- parent.

Exemple :

```text
categoryId: restaurant
fr: Restaurant
en: Restaurant
```

Le code métier utilise l’identifiant stable, pas le libellé traduit.

---

# 33. API

Les API peuvent accepter :

```http
Accept-Language: fr-ML
```

Le backend doit cependant retourner des codes d’erreur stables.

Exemple :

```json
{
  "code": "PAYMENT_LIMIT_EXCEEDED",
  "message": "Le plafond autorisé est dépassé."
}
```

Le champ `code` reste identique dans toutes les langues.

---

# 34. Messages d’erreur

Les erreurs doivent séparer :

- code technique stable ;
- message utilisateur traduit ;
- détails traduisibles ;
- identifiant de corrélation ;
- action possible.

Le backend ne doit pas exposer directement une exception technique traduite automatiquement.

---

# 35. Administration des traductions

Le portail Admin doit permettre :

- créer une langue ;
- activer une langue ;
- importer des traductions ;
- exporter des traductions ;
- modifier une clé ;
- comparer les versions ;
- rechercher une clé ;
- détecter les clés manquantes ;
- détecter les variables incohérentes ;
- valider ;
- publier ;
- revenir à une version antérieure.

---

# 36. Rôles

Rôles possibles :

- traducteur ;
- réviseur ;
- responsable langue ;
- juriste ;
- administrateur contenu ;
- approbateur ;
- auditeur.

Un traducteur ne doit pas forcément pouvoir publier directement.

---

# 37. Workflow de traduction

Étapes possibles :

1. clé créée ;
2. contenu source rédigé ;
3. traduction demandée ;
4. traduction en cours ;
5. révision ;
6. validation métier ;
7. validation juridique si nécessaire ;
8. recette ;
9. publication ;
10. archivage.

---

# 38. Permissions

Exemples :

```text
translation.read
translation.create
translation.update
translation.review
translation.approve
translation.publish
translation.rollback
language.activate
legal_translation.approve
```

---

# 39. Versionnement

Toute modification importante doit conserver :

- ancienne valeur ;
- nouvelle valeur ;
- langue ;
- clé ;
- auteur ;
- date ;
- motif ;
- date d’effet ;
- version de l’application concernée.

---

# 40. Cache

Les traductions peuvent être mises en cache.

Le cache doit gérer :

- version ;
- invalidation ;
- langue ;
- pays ;
- environnement ;
- fallback ;
- fonctionnement hors ligne.

---

# 41. Mode hors ligne

Les applications doivent embarquer les traductions essentielles.

En mode hors ligne :

- les textes critiques restent disponibles ;
- les traductions déjà téléchargées restent utilisables ;
- une langue récemment ajoutée peut nécessiter un téléchargement ;
- aucune clé brute ne doit apparaître.

---

# 42. Qualité des traductions

Les contrôles automatiques doivent détecter :

- clé manquante ;
- variable manquante ;
- variable supplémentaire ;
- balise invalide ;
- texte vide ;
- format incorrect ;
- traduction identique suspecte ;
- longueur excessive ;
- caractère interdit ;
- pluriel incomplet.

---

# 43. Tests

## 43.1 Tests fonctionnels

- sélection de langue ;
- changement de langue ;
- fallback ;
- persistance ;
- notifications ;
- reçus ;
- documents ;
- API.

## 43.2 Tests visuels

- textes longs ;
- petits écrans ;
- tableaux ;
- boutons ;
- navigation ;
- modales ;
- TPE ;
- portail Admin.

## 43.3 Tests de formats

- devises ;
- dates ;
- nombres ;
- téléphones ;
- adresses ;
- fuseaux horaires ;
- pluriels.

## 43.4 Tests RTL

Lorsque la plateforme active une langue RTL :

- navigation ;
- alignements ;
- graphiques ;
- formulaires ;
- icônes ;
- animations ;
- montants.

---

# 44. Analytics

Événements possibles :

```text
language_selected
language_changed
translation_missing
translation_fallback_used
translation_published
translation_rolled_back
locale_format_error
legal_document_language_accepted
```

Les contenus privés traduits ne doivent pas être enregistrés inutilement dans les analytics.

---

# 45. Modèles

- Language
- Locale
- TranslationKey
- TranslationValue
- TranslationVersion
- TranslationStatus
- TranslationReview
- TranslationPublication
- TranslationFallback
- LocalizedContent
- LocalizedLegalDocument
- LocaleFormat
- TranslationAudit

---

# 46. Règles métier

1. Aucun texte utilisateur important n’est codé en dur.
2. Chaque traduction utilise une clé stable.
3. Les codes d’erreur restent indépendants de la langue.
4. Les contenus critiques sont validés humainement.
5. Les documents légaux sont versionnés par langue et pays.
6. Une langue incomplète ne doit pas être annoncée comme totalement disponible.
7. Les variables doivent être cohérentes entre les traductions.
8. Les formats suivent la locale choisie.
9. Les montants conservent toujours leur devise.
10. Le choix explicite de l’utilisateur est prioritaire.
11. Le fallback est contrôlé.
12. Les traductions sont auditées.
13. Les anciennes versions restent consultables.
14. Le mode hors ligne conserve les textes essentiels.
15. Une traduction ne modifie jamais la donnée financière réelle.
16. Les libellés traduits ne servent pas d’identifiants métier.
17. Les contenus sensibles ne sont pas envoyés à un outil externe sans autorisation.
18. Les rôles de traduction et de publication peuvent être séparés.
19. Toute publication doit être liée à une version.
20. Les interfaces doivent supporter l’expansion des textes.

---

# 47. Critères d’acceptation

L’internationalisation est validée lorsque :

- tous les textes utilisent des clés ;
- les langues sont configurables ;
- la langue utilisateur est persistée ;
- les fallbacks fonctionnent ;
- les formats locaux sont appliqués ;
- les devises restent explicites ;
- les dates et heures respectent les fuseaux ;
- les contenus légaux sont versionnés ;
- les notifications sont traduites ;
- les reçus conservent leur version linguistique ;
- le CMS gère plusieurs langues ;
- les traductions sont révisables ;
- les permissions sont appliquées ;
- les textes longs ne cassent pas les interfaces ;
- les tests automatiques détectent les traductions incomplètes ;
- les changements sont audités.