# 08 — Gestion multi-pays de Mansa

## 1. Objet du document

Ce document définit la manière dont Mansa doit gérer plusieurs pays sans dupliquer toute la plateforme.

Il couvre :

- les pays activés ;
- les devises ;
- les langues ;
- les formats locaux ;
- les réglementations ;
- les partenaires ;
- les plafonds ;
- les frais ;
- les moyens de paiement ;
- les services publics ;
- les cartes ;
- les taxes ;
- les conditions d’utilisation ;
- les différences d’interface ;
- les règles d’administration ;
- les dépendances par pays.

L’objectif est que Mansa puisse être lancé d’abord au Mali, puis étendu à d’autres pays africains, sans devoir reconstruire les applications.

---

# 2. Principes fondamentaux

## 2.1 Un socle commun, des règles locales

Les fonctions communes doivent être développées une seule fois.

Les différences locales doivent être pilotées par configuration lorsque cela est raisonnable.

Exemples :

- devise ;
- langue ;
- moyens de paiement ;
- frais ;
- plafonds ;
- format téléphone ;
- format adresse ;
- règles KYC ;
- cartes disponibles ;
- partenaires ;
- services publics ;
- taxes.

## 2.2 Aucun pays codé en dur

Les règles pays ne doivent pas être dispersées dans le code.

Elles doivent être centralisées dans :

- configuration ;
- tables ;
- services dédiés ;
- feature flags ;
- politiques ;
- catalogues de partenaires.

## 2.3 Disponibilité par pays

Chaque fonctionnalité doit avoir un statut par pays :

- indisponible ;
- prévue ;
- en test ;
- disponible en démonstration ;
- dépend d’un partenaire ;
- dépend d’une autorisation ;
- active ;
- suspendue.

## 2.4 Conformité locale

Une fonctionnalité ne doit pas être activée dans un pays si :

- la réglementation ne le permet pas ;
- le partenaire requis n’est pas disponible ;
- les autorisations ne sont pas obtenues ;
- les conditions techniques ne sont pas remplies ;
- les documents légaux ne sont pas adaptés.

---

# 3. Entité pays

Chaque pays doit être défini par une configuration officielle.

Exemple de données :

```text
code ISO
nom
nom local
statut
devise principale
devises secondaires
langues
préfixe téléphonique
formats de téléphone
formats de date
formats de nombre
fuseaux horaires
régions
règles fiscales
partenaires
services disponibles
version des documents légaux
```

---

# 4. Statuts d’un pays

Un pays peut être :

- brouillon ;
- configuré ;
- en intégration ;
- en recette ;
- en pilote ;
- actif ;
- limité ;
- suspendu ;
- fermé.

Aucun pays ne doit passer en production sans checklist de validation.

---

# 5. Configuration par pays

Chaque pays doit pouvoir définir :

- nom commercial local ;
- devise ;
- langues ;
- logo ou variation si autorisée ;
- moyens de paiement ;
- Mobile Money ;
- banques partenaires ;
- cartes disponibles ;
- plafonds ;
- frais ;
- commissions ;
- seuils KYC ;
- taxes ;
- jours fériés ;
- services publics ;
- support ;
- horaires ;
- documents légaux ;
- règles de conservation ;
- limites d’âge ;
- restrictions ;
- messages spécifiques.

---

# 6. Multi-devises

La gestion multi-pays doit être compatible avec plusieurs devises.

Chaque pays définit :

- devise par défaut ;
- devises autorisées ;
- précision ;
- symbole ;
- position du symbole ;
- format d’affichage ;
- règles de conversion ;
- frais ;
- partenaires de change.

Une devise disponible dans un pays ne doit pas être supposée disponible dans tous les autres.

---

# 7. Langues

Chaque pays peut avoir :

- langue principale ;
- langues secondaires ;
- langues de support ;
- langue légale ;
- langue par défaut.

Les applications doivent permettre une configuration indépendante du pays lorsque cela est pertinent.

Exemple :

un utilisateur au Mali peut choisir le français ou une autre langue disponible.

---

# 8. Téléphones

Chaque pays doit définir :

- indicatif ;
- longueur ;
- formats ;
- opérateurs ;
- validation ;
- normalisation E.164 ;
- affichage local.

Le numéro doit être stocké dans un format normalisé.

---

# 9. Adresses

Les formulaires d’adresse doivent varier selon le pays.

Champs possibles :

- pays ;
- région ;
- cercle ;
- commune ;
- ville ;
- quartier ;
- rue ;
- code postal ;
- repère ;
- coordonnées GPS.

Les champs obligatoires doivent être configurables.

---

# 10. Identité et KYC

Les exigences KYC peuvent varier selon :

- pays ;
- âge ;
- type de compte ;
- montant ;
- service ;
- réglementation ;
- partenaire.

Documents possibles :

- carte nationale ;
- passeport ;
- titre de séjour ;
- permis ;
- acte de naissance ;
- justificatif de domicile ;
- photo ;
- preuve de vie ;
- numéro fiscal.

Chaque document doit avoir :

- type ;
- pays ;
- statut ;
- règles de validation ;
- expiration ;
- formats acceptés ;
- fournisseur de vérification.

---

# 11. KYB

Les exigences professionnelles peuvent varier selon le pays.

Documents possibles :

- registre du commerce ;
- numéro fiscal ;
- statuts ;
- licence ;
- identité du dirigeant ;
- bénéficiaires effectifs ;
- justificatif d’adresse ;
- compte bancaire ;
- autorisation sectorielle.

---

# 12. Moyens de paiement par pays

Chaque pays peut activer :

- wallet Mansa ;
- carte ;
- virement ;
- Mobile Money ;
- QR ;
- NFC ;
- cash-in ;
- cash-out ;
- paiement marchand ;
- paiement public ;
- Tap to Phone.

La disponibilité doit être affichée avant que l’utilisateur commence un parcours.

---

# 13. Mobile Money

Chaque opérateur doit être configuré par pays.

Données possibles :

- opérateur ;
- code ;
- statut ;
- API ;
- frais ;
- limites ;
- délais ;
- webhook ;
- environnement ;
- méthodes disponibles ;
- types d’opérations ;
- messages utilisateurs.

---

# 14. Banques partenaires

Chaque banque peut avoir :

- pays ;
- rôle ;
- comptes ;
- émission de cartes ;
- acquisition ;
- virements ;
- règlement ;
- KYC ;
- limites ;
- horaires ;
- SLA ;
- statut ;
- environnement.

---

# 15. Cartes

Les programmes de cartes peuvent varier selon le pays.

Chaque programme doit définir :

- réseau ;
- banque émettrice ;
- BIN ;
- devise ;
- catégories ;
- frais ;
- limites ;
- designs ;
- disponibilité ;
- conditions ;
- logistique ;
- wallets compatibles ;
- services autorisés.

---

# 16. Frais et commissions

Les frais doivent pouvoir varier par :

- pays ;
- devise ;
- service ;
- canal ;
- montant ;
- type d’utilisateur ;
- abonnement ;
- partenaire ;
- heure ;
- promotion.

Les frais doivent toujours être affichés avant confirmation.

---

# 17. Plafonds

Les plafonds peuvent dépendre de :

- pays ;
- réglementation ;
- niveau KYC ;
- type de compte ;
- moyen de paiement ;
- devise ;
- canal ;
- partenaire ;
- risque.

Types :

- par transaction ;
- journalier ;
- hebdomadaire ;
- mensuel ;
- annuel ;
- par bénéficiaire ;
- par commerçant ;
- par canal.

---

# 18. Taxes

Chaque pays peut définir :

- TVA ;
- taxes locales ;
- taxes spécifiques ;
- retenues ;
- exemptions ;
- règles d’arrondi ;
- catégories ;
- taux ;
- date d’effet ;
- documents.

Les taxes doivent être versionnées.

---

# 19. Services publics

Les services publics peuvent varier fortement selon le pays.

Exemples :

- amendes ;
- taxes ;
- frais scolaires ;
- cartes étudiantes ;
- bourses ;
- documents administratifs ;
- factures publiques ;
- redevances ;
- services municipaux.

Chaque service doit être lié à :

- organisme ;
- pays ;
- règles ;
- API ;
- références ;
- reçus ;
- statuts ;
- permissions ;
- procédures d’annulation.

---

# 20. Investissements

Les produits d’investissement doivent être configurés par pays selon :

- réglementation ;
- partenaire ;
- catégorie ;
- risque ;
- devise ;
- montant minimum ;
- investisseurs autorisés ;
- documents ;
- restrictions ;
- fiscalité.

Aucun produit ne doit être activé automatiquement dans un nouveau pays.

---

# 21. Support

Chaque pays peut avoir :

- équipe dédiée ;
- horaires ;
- téléphone ;
- e-mail ;
- WhatsApp ;
- langues ;
- SLA ;
- catégories ;
- procédures ;
- escalades.

---

# 22. Documents légaux

Chaque pays doit disposer de versions adaptées :

- conditions générales ;
- politique de confidentialité ;
- tarification ;
- politique de remboursement ;
- politique de cookies ;
- conditions cartes ;
- conditions commerçants ;
- conditions investissements ;
- mentions réglementaires.

L’utilisateur doit accepter la version applicable à son pays.

---

# 23. Consentements

Chaque consentement doit enregistrer :

- utilisateur ;
- pays ;
- document ;
- version ;
- langue ;
- date ;
- appareil ;
- IP si autorisée ;
- statut ;
- retrait éventuel.

---

# 24. Géolocalisation

La géolocalisation peut être utilisée pour :

- proposer le pays ;
- détecter une incohérence ;
- trouver des commerces ;
- adapter les services ;
- gérer la fraude.

Elle ne doit pas remplacer le pays légal du compte sans validation.

---

# 25. Changement de pays

Le changement de pays doit être encadré.

Cas possibles :

- voyage temporaire ;
- changement de résidence ;
- erreur d’inscription ;
- compte multi-pays ;
- migration.

Le changement peut nécessiter :

- nouveau KYC ;
- nouveaux documents ;
- nouvelle devise ;
- nouvelles conditions ;
- changement de partenaire ;
- restrictions ;
- approbation.

---

# 26. Comptes multi-pays

Un utilisateur peut éventuellement avoir accès à plusieurs environnements pays.

Cela doit être défini explicitement.

Exemples :

- résident d’un pays ;
- travailleur transfrontalier ;
- entreprise multi-pays ;
- partenaire ;
- administrateur.

---

# 27. Administration multi-pays

Le portail Admin doit permettre :

- créer un pays ;
- dupliquer une configuration ;
- activer une fonction ;
- gérer les partenaires ;
- définir les frais ;
- définir les plafonds ;
- définir les documents ;
- gérer les langues ;
- configurer le support ;
- gérer les taxes ;
- publier les conditions ;
- suspendre un service ;
- consulter l’état de préparation.

---

# 28. Rôles pays

Rôles possibles :

- administrateur global ;
- administrateur pays ;
- responsable conformité pays ;
- responsable support pays ;
- responsable partenaires pays ;
- responsable finance pays ;
- auditeur pays.

Un administrateur pays ne doit pas automatiquement accéder aux autres pays.

---

# 29. Feature flags par pays

Chaque fonctionnalité peut être activée selon :

- pays ;
- utilisateur ;
- segment ;
- environnement ;
- version ;
- partenaire ;
- pourcentage de déploiement.

---

# 30. Configuration technique

Exemple conceptuel :

```json
{
  "country": "ML",
  "status": "active",
  "defaultCurrency": "XOF",
  "languages": ["fr"],
  "features": {
    "cards": true,
    "investments": false,
    "publicServices": true
  }
}
```

Les valeurs réelles doivent être stockées dans une configuration validée et auditée.

---

# 31. API

Exemples :

```http
GET    /countries
GET    /countries/{code}
POST   /countries
PATCH  /countries/{code}

GET    /countries/{code}/features
PATCH  /countries/{code}/features

GET    /countries/{code}/limits
PATCH  /countries/{code}/limits

GET    /countries/{code}/fees
PATCH  /countries/{code}/fees

GET    /countries/{code}/partners
GET    /countries/{code}/legal-documents
```

---

# 32. Modèles

- Country
- CountryStatus
- CountryFeature
- CountryCurrency
- CountryLanguage
- CountryPartner
- CountryLimit
- CountryFee
- CountryTax
- CountryLegalDocument
- CountrySupportConfig
- CountryKycPolicy
- CountryKybPolicy
- CountryService
- CountryAudit

---

# 33. Règles métier

1. Une fonctionnalité est inactive par défaut dans un nouveau pays.
2. Toute activation doit être explicite.
3. Les frais doivent être versionnés.
4. Les plafonds doivent être appliqués côté backend.
5. Les documents légaux doivent être adaptés.
6. Les partenaires doivent être actifs.
7. Les devises doivent être autorisées.
8. Les rôles pays ne dépassent pas leur périmètre.
9. Le changement de pays doit être contrôlé.
10. Les configurations critiques doivent être auditées.
11. Les fonctionnalités réglementées nécessitent une autorisation.
12. Les états Démo, Recette et Production doivent être séparés.
13. Une indisponibilité pays doit être visible dans l’interface.
14. Les règles locales ne doivent pas contourner les règles globales de sécurité.
15. Toute configuration doit avoir une date d’effet.

---

# 34. Checklist de lancement d’un pays

Avant activation :

- configuration validée ;
- devise validée ;
- langues disponibles ;
- KYC/KYB validés ;
- partenaires intégrés ;
- moyens de paiement testés ;
- frais validés ;
- plafonds validés ;
- documents légaux publiés ;
- support opérationnel ;
- sécurité testée ;
- monitoring actif ;
- sauvegarde active ;
- procédure d’incident ;
- environnement production séparé ;
- validation finale.

---

# 35. Analytics

Événements possibles :

```text
country_configured
country_activated
country_suspended
feature_enabled_for_country
feature_disabled_for_country
country_fee_updated
country_limit_updated
country_partner_activated
country_legal_document_published
country_launch_completed
```

---

# 36. Tests

- tests de configuration ;
- tests multi-pays ;
- tests multi-devises ;
- tests de langues ;
- tests de plafonds ;
- tests de frais ;
- tests de permissions ;
- tests de changement de pays ;
- tests de partenaires ;
- tests de documents légaux ;
- tests de feature flags ;
- tests de non-régression ;
- tests d’isolation.

---

# 37. Critères d’acceptation

La gestion multi-pays est validée lorsque :

- les pays sont configurables ;
- les règles ne sont pas codées en dur ;
- les devises sont gérées ;
- les langues sont adaptées ;
- les moyens de paiement varient par pays ;
- les frais et plafonds sont appliqués ;
- les documents légaux sont versionnés ;
- les partenaires sont séparés ;
- les rôles sont limités au pays ;
- les feature flags fonctionnent ;
- les changements sont audités ;
- la checklist de lancement est complète ;
- aucun pays ne peut être activé sans validation.
