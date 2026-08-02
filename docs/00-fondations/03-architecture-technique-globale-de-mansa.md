# 03 — Architecture technique globale de Mansa

## 1. Objet du document

Ce document définit l’architecture technique globale de Mansa.

Il décrit :

- l’organisation du monorepo ;
- les applications ;
- les services backend ;
- les packages partagés ;
- les bases de données ;
- les communications entre composants ;
- les environnements ;
- les principes de sécurité ;
- la gestion des erreurs ;
- l’observabilité ;
- les performances ;
- les tests ;
- le déploiement ;
- les règles de séparation entre documentation, code et configuration.

Ce document ne remplace pas les spécifications détaillées de chaque application ou module.

---

## 2. Principes techniques fondamentaux

### 2.1 Monorepo modulaire

Mansa doit être organisé dans un monorepo afin de :

- partager les contrats ;
- partager les types ;
- partager le design system ;
- centraliser les règles de qualité ;
- éviter les duplications ;
- faciliter les changements coordonnés ;
- lancer des tests globaux ;
- versionner l’écosystème de manière cohérente.

Le monorepo ne doit pas devenir un bloc monolithique.

Chaque application et package doit conserver :

- son périmètre ;
- ses dépendances explicites ;
- ses scripts ;
- ses tests ;
- sa configuration ;
- sa capacité de déploiement indépendant lorsque nécessaire.

### 2.2 Architecture modulaire avant microservices

La première architecture backend recommandée est un **monolithe modulaire NestJS**, organisé par domaines métiers.

Cela permet :

- un développement plus rapide ;
- moins de complexité opérationnelle ;
- moins de duplication ;
- des transactions cohérentes ;
- une meilleure maîtrise des dépendances ;
- une extraction future progressive.

Un module ne doit pas accéder directement aux détails internes d’un autre module.

Les échanges doivent passer par :

- services publics du module ;
- contrats ;
- événements ;
- interfaces de domaine ;
- files de messages lorsque nécessaire.

Les domaines à forte charge ou forte indépendance pourront être extraits plus tard en services séparés.

### 2.3 Backend comme source d’autorité

Les applications clientes ne doivent jamais être considérées comme source de vérité pour :

- les soldes ;
- les statuts de paiement ;
- les plafonds ;
- les frais ;
- les commissions ;
- les permissions ;
- les validations KYC/KYB ;
- les écritures comptables ;
- les décisions de fraude ;
- les opérations administratives.

Le backend valide chaque action et retourne l’état officiel.

### 2.4 Contrats avant implémentation

Chaque interaction entre une application et le backend doit être définie par un contrat explicite.

Un contrat doit préciser :

- méthode ;
- route ;
- version ;
- authentification ;
- permissions ;
- paramètres ;
- corps de requête ;
- réponse ;
- erreurs ;
- idempotence ;
- pagination ;
- tri ;
- filtrage ;
- audit ;
- événements générés ;
- niveau de sensibilité.

Les contrats partagés doivent être versionnés.

### 2.5 Configuration séparée du code

Les éléments suivants ne doivent pas être codés en dur lorsqu’ils doivent varier :

- pays ;
- devises ;
- langues ;
- frais ;
- plafonds ;
- taux ;
- partenaires ;
- fonctionnalités ;
- abonnements ;
- rôles ;
- règles d’affichage ;
- modèles de notifications ;
- contenus éditoriaux ;
- règles de risque ;
- seuils ;
- versions minimales.

Toute configuration critique doit être :

- typée ;
- validée ;
- auditée ;
- versionnée ;
- limitée par environnement ;
- modifiable uniquement par des rôles autorisés.

---

## 3. Organisation générale du dépôt

Structure cible :

```text
mansa-fin/
├── apps/
│   ├── api-gateway/
│   ├── client-mobile/
│   ├── commerce-mobile/
│   ├── admin-lite-mobile/
│   ├── annuaire-mobile/
│   ├── tpe-android/
│   ├── public-web/
│   ├── professional-web/
│   └── admin-web/
│
├── packages/
│   ├── contracts/
│   ├── domain/
│   ├── sdk/
│   ├── ui-web/
│   ├── ui-mobile/
│   ├── design-tokens/
│   ├── auth/
│   ├── permissions/
│   ├── analytics/
│   ├── notifications/
│   ├── internationalization/
│   ├── validation/
│   ├── errors/
│   ├── config/
│   ├── testing/
│   └── tooling/
│
├── database/
│   ├── prisma/
│   ├── migrations/
│   ├── seeds/
│   └── scripts/
│
├── infrastructure/
│   ├── docker/
│   ├── ci/
│   ├── monitoring/
│   ├── deployment/
│   └── environments/
│
├── docs/
│   ├── architecture/
│   ├── api/
│   ├── security/
│   ├── operations/
│   └── decisions/
│
├── scripts/
├── tests/
├── package.json
├── pnpm-workspace.yaml
├── turbo.json
├── tsconfig.base.json
└── README.md
```

Le nom exact des dossiers peut évoluer, mais les responsabilités doivent rester claires.

---

## 4. Applications

### 4.1 API Gateway

Technologies prévues :

- NestJS ;
- TypeScript ;
- Prisma ;
- PostgreSQL ;
- Redis lorsque nécessaire ;
- OpenAPI ;
- validation DTO ;
- authentification JWT ou sessions sécurisées selon les cas.

Responsabilités :

- authentification ;
- autorisation ;
- orchestration métier ;
- exposition des API ;
- validation ;
- limitation de débit ;
- gestion des erreurs ;
- journalisation ;
- audit ;
- idempotence ;
- publication d’événements ;
- appels aux partenaires ;
- génération de documents ;
- notifications ;
- tâches asynchrones.

### 4.2 Mansa Client Mobile

Technologies prévues :

- React Native ;
- TypeScript ;
- navigation native ;
- stockage sécurisé ;
- gestion d’état ;
- requêtes réseau avec cache ;
- biométrie native ;
- notifications push ;
- modules natifs pour NFC, QR, Wallets et sécurité.

L’application doit séparer :

- présentation ;
- navigation ;
- logique d’écran ;
- état local ;
- appels SDK ;
- stockage sécurisé ;
- analytics ;
- permissions système.

Aucune logique financière critique ne doit être exécutée uniquement côté mobile.

### 4.3 Mansa Commerce Mobile

Technologies proches de l’application Client, avec modules spécialisés :

- catalogue ;
- stocks ;
- ventes ;
- clients ;
- employés ;
- reçus ;
- factures ;
- imprimantes ;
- codes-barres ;
- synchronisation locale.

Le mode hors ligne doit être limité aux actions compatibles avec les règles de sécurité et de rapprochement.

### 4.4 Mansa Admin Lite

Application mobile à surface fonctionnelle réduite.

Elle doit utiliser :

- authentification renforcée ;
- restrictions par appareil ;
- permissions fines ;
- durée de session plus courte ;
- journalisation complète ;
- possibilité de révocation immédiate.

### 4.5 Mansa Annuaire / Hub

Application mobile orientée :

- recherche ;
- carte ;
- géolocalisation ;
- profils ;
- contenus ;
- réservations ;
- favoris ;
- avis ;
- promotions.

Elle doit être optimisée pour :

- recherche rapide ;
- cache géographique ;
- images ;
- faible connexion ;
- pagination ;
- chargement progressif.

### 4.6 Mansa TPE Android

Technologie principale :

- Kotlin ;
- Android natif ;
- SDK constructeurs ;
- SDK paiement ;
- NFC ;
- imprimante ;
- lecteur carte ;
- scanner ;
- gestion des mises à jour ;
- stockage chiffré ;
- verrouillage kiosque lorsque nécessaire.

Le TPE doit être séparé techniquement des applications React Native lorsque les contraintes matérielles l’exigent.

Il doit gérer :

- identification du terminal ;
- activation ;
- certificat ;
- environnement ;
- version ;
- statut ;
- synchronisation ;
- sécurité locale ;
- reprise après interruption.

### 4.7 Site public

Technologies prévues :

- Next.js ;
- React ;
- TypeScript ;
- Tailwind CSS ;
- CMS ;
- optimisation d’images ;
- SEO ;
- analytics ;
- animations progressives ;
- 3D chargée uniquement lorsque utile.

Le site doit rester utilisable sans WebGL avancé.

### 4.8 Site Professionnels

Architecture proche du site public avec fonctions supplémentaires :

- formulaires ;
- devis ;
- démonstrations ;
- collecte de prospects ;
- contenus sectoriels ;
- documentation commerciale ;
- onboarding professionnel ;
- espace partenaire éventuel.

### 4.9 Portail Admin Web

Technologies prévues :

- Next.js ;
- React ;
- TypeScript ;
- design system interne ;
- gestion avancée des tableaux ;
- formulaires typés ;
- permissions fines ;
- authentification renforcée ;
- audit ;
- exports ;
- graphiques ;
- actions en masse contrôlées.

Le portail Admin ne doit pas dépendre directement de la base de données.

Toutes les actions passent par les API autorisées.

---

## 5. Packages partagés

### 5.1 Contracts

Contient :

- DTO ;
- schémas ;
- enums ;
- erreurs publiques ;
- contrats d’événements ;
- types de pagination ;
- modèles de réponse ;
- conventions d’idempotence ;
- métadonnées d’audit.

Il ne doit pas contenir de logique métier sensible.

### 5.2 Domain

Contient les éléments métiers réutilisables :

- objets valeur ;
- règles communes ;
- statuts ;
- calculs purs ;
- interfaces de domaine ;
- invariants.

Ce package ne doit pas dépendre d’un framework d’interface.

### 5.3 SDK

Fournit aux applications :

- client API ;
- gestion de session ;
- renouvellement de jetons ;
- erreurs normalisées ;
- méthodes typées ;
- instrumentation ;
- idempotence ;
- téléchargement de fichiers ;
- pagination ;
- retry contrôlé.

### 5.4 UI Web

Contient :

- composants web ;
- tableaux ;
- formulaires ;
- modales ;
- alertes ;
- navigation ;
- graphiques ;
- états de chargement ;
- composants accessibles.

### 5.5 UI Mobile

Contient :

- composants React Native ;
- boutons ;
- champs ;
- cartes ;
- modales ;
- listes ;
- états ;
- animations ;
- haptics ;
- composants accessibles.

Les composants liés à du matériel spécifique restent dans l’application concernée.

### 5.6 Design Tokens

Contient :

- couleurs ;
- typographies ;
- espacements ;
- rayons ;
- ombres ;
- tailles ;
- animations ;
- niveaux d’élévation ;
- variantes de thème.

### 5.7 Auth

Contient :

- helpers d’authentification ;
- gestion locale de session ;
- protections de route ;
- types d’identité ;
- politiques communes ;
- interfaces de stockage sécurisé.

### 5.8 Permissions

Contient :

- définitions de ressources ;
- actions ;
- rôles ;
- politiques ;
- helpers d’affichage ;
- vérifications côté interface.

La vérification interface ne remplace jamais l’autorisation backend.

### 5.9 Analytics

Contient :

- noms d’événements ;
- schémas ;
- propriétés autorisées ;
- clients ;
- anonymisation ;
- règles de consentement ;
- validation des données.

### 5.10 Internationalisation

Contient :

- clés de traduction ;
- locales ;
- formats ;
- devises ;
- dates ;
- pluriels ;
- langues ;
- règles par pays.

### 5.11 Validation

Contient :

- schémas partagés ;
- validations de formulaires ;
- normalisation ;
- formats ;
- parseurs ;
- erreurs de validation.

### 5.12 Errors

Contient la taxonomie officielle des erreurs :

- code ;
- message utilisateur ;
- message technique ;
- statut HTTP ;
- niveau ;
- réessayable ou non ;
- action recommandée ;
- identifiant de corrélation.

---

## 6. Backend modulaire

### 6.1 Organisation des modules

Structure indicative :

```text
apps/api-gateway/src/
├── modules/
│   ├── auth/
│   ├── identity/
│   ├── users/
│   ├── kyc/
│   ├── kyb/
│   ├── accounts/
│   ├── wallets/
│   ├── ledger/
│   ├── transactions/
│   ├── transfers/
│   ├── payments/
│   ├── cards/
│   ├── qr/
│   ├── nfc/
│   ├── mobile-money/
│   ├── merchants/
│   ├── commerce/
│   ├── terminals/
│   ├── inventory/
│   ├── loyalty/
│   ├── promotions/
│   ├── messaging/
│   ├── notifications/
│   ├── support/
│   ├── fraud/
│   ├── public-services/
│   ├── investments/
│   ├── documents/
│   ├── analytics/
│   ├── audit/
│   ├── configuration/
│   └── jini/
├── common/
├── infrastructure/
├── config/
└── main.ts
```

### 6.2 Structure interne d’un module

Chaque module peut contenir :

```text
module-name/
├── application/
│   ├── commands/
│   ├── queries/
│   ├── services/
│   └── dto/
├── domain/
│   ├── entities/
│   ├── value-objects/
│   ├── rules/
│   ├── events/
│   └── repositories/
├── infrastructure/
│   ├── persistence/
│   ├── integrations/
│   └── mappers/
├── presentation/
│   ├── controllers/
│   ├── guards/
│   └── presenters/
├── module.ts
└── index.ts
```

Cette structure peut être simplifiée pour les petits modules.

### 6.3 Dépendances entre modules

Règles :

1. Les dépendances doivent être explicites.
2. Les cycles sont interdits.
3. Un module ne doit pas importer directement les tables internes d’un autre.
4. Les accès passent par des interfaces ou services publics.
5. Les événements sont utilisés pour les réactions secondaires.
6. Les transactions critiques restent synchrones lorsque nécessaire.
7. Les appels externes sont encapsulés dans des adaptateurs.

---

## 7. Base de données

### 7.1 PostgreSQL

PostgreSQL est la base principale pour :

- identité ;
- comptes ;
- transactions ;
- commerce ;
- cartes ;
- paiements ;
- audit ;
- configuration ;
- documents ;
- services publics ;
- investissements.

### 7.2 Prisma

Prisma sert à :

- définir le schéma ;
- générer le client ;
- créer les migrations ;
- accéder aux données ;
- typage des requêtes ;
- transactions ;
- contraintes.

Le schéma Prisma ne doit pas devenir la définition complète du métier.

Les règles métier restent dans les services et objets de domaine.

### 7.3 Ledger financier

Les soldes ne doivent pas être calculés uniquement à partir d’un simple champ mutable.

Le système financier doit prévoir :

- comptes de ledger ;
- écritures débit/crédit ;
- transactions équilibrées ;
- références métier ;
- idempotence ;
- immutabilité ;
- corrections par contre-écriture ;
- rapprochement ;
- statuts ;
- audit.

Aucune écriture financière confirmée ne doit être supprimée.

### 7.4 Partitionnement logique

Les données doivent être séparables selon :

- pays ;
- organisation ;
- environnement ;
- type d’utilisateur ;
- établissement ;
- partenaire ;
- statut de conservation.

Cela ne signifie pas obligatoirement une base physique par pays au début.

### 7.5 Redis

Redis peut être utilisé pour :

- cache ;
- limitation de débit ;
- verrous distribués ;
- sessions temporaires ;
- OTP ;
- files légères ;
- données éphémères ;
- présence ;
- anti-doublon.

Redis ne doit pas être l’unique stockage d’une information financière durable.

---

## 8. Communication entre composants

### 8.1 API synchrones

Utilisées pour :

- lecture ;
- validation immédiate ;
- commandes nécessitant une réponse ;
- authentification ;
- simulation ;
- confirmation ;
- consultation.

Formats :

- REST JSON comme base ;
- fichiers signés pour certains documents ;
- WebSocket ou SSE pour temps réel lorsque nécessaire.

### 8.2 Événements asynchrones

Utilisés pour :

- notifications ;
- analytics ;
- génération de documents ;
- synchronisation ;
- webhooks ;
- reporting ;
- traitements secondaires ;
- mise à jour de recherche ;
- tâches longues.

Exemples :

- `user.created`
- `kyc.verified`
- `payment.completed`
- `payment.failed`
- `card.blocked`
- `refund.completed`
- `merchant.activated`
- `ticket.created`

### 8.3 Files de messages

Une file doit être utilisée lorsque :

- le traitement doit survivre à un redémarrage ;
- plusieurs tentatives sont nécessaires ;
- l’ordre importe ;
- le partenaire peut être lent ;
- l’opération est longue ;
- un découplage est utile.

Chaque message doit préciser :

- identifiant ;
- type ;
- version ;
- date ;
- producteur ;
- charge utile ;
- corrélation ;
- tentative ;
- statut ;
- stratégie de retry.

### 8.4 Webhooks

Les webhooks servent à recevoir ou transmettre des événements partenaires.

Exigences :

- signature ;
- horodatage ;
- protection anti-rejeu ;
- idempotence ;
- journalisation ;
- retry ;
- statut ;
- stockage de la charge brute lorsque autorisé ;
- validation de schéma ;
- surveillance.

---

## 9. Authentification et sessions

### 9.1 Jetons

Le système peut utiliser :

- access token court ;
- refresh token rotatif ;
- session serveur ;
- passkey ;
- challenge ;
- OTP ;
- jetons d’appareil.

Les secrets ne doivent jamais être stockés en clair.

### 9.2 Rotation des refresh tokens

Chaque renouvellement doit pouvoir :

- invalider l’ancien jeton ;
- détecter sa réutilisation ;
- fermer la famille de sessions en cas de fraude ;
- journaliser l’événement ;
- notifier l’utilisateur lorsque nécessaire.

### 9.3 Appareils

Chaque appareil doit posséder :

- identifiant ;
- utilisateur ;
- type ;
- système ;
- version ;
- clé locale ;
- niveau de confiance ;
- dernière activité ;
- statut ;
- date d’approbation ;
- date de révocation.

### 9.4 Administration

Les sessions administratives doivent avoir :

- durée réduite ;
- réauthentification ;
- double authentification ;
- restriction d’appareil ;
- surveillance renforcée ;
- journalisation ;
- révocation immédiate.

---

## 10. Autorisation

### 10.1 RBAC

Le RBAC gère les rôles :

- utilisateur ;
- commerçant ;
- employé ;
- manager ;
- support ;
- conformité ;
- finance ;
- administrateur ;
- super administrateur ;
- agent public ;
- partenaire.

### 10.2 Permissions fines

Chaque permission combine :

- ressource ;
- action ;
- périmètre ;
- organisation ;
- établissement ;
- pays ;
- environnement ;
- condition.

Exemple :

```text
merchant.refund.create
scope: establishment:123
limit: 100000 XOF
requires_approval: true
```

### 10.3 ABAC

Certaines décisions peuvent dépendre d’attributs :

- pays ;
- niveau KYC ;
- montant ;
- risque ;
- appareil ;
- heure ;
- rôle ;
- relation avec la ressource ;
- statut du compte.

---

## 11. Idempotence

Toute commande financière ou critique doit accepter une clé d’idempotence.

Exemples :

- paiement ;
- transfert ;
- remboursement ;
- création de carte ;
- demande d’argent ;
- activation terminal ;
- appel partenaire ;
- création d’écriture.

Le système doit retourner le même résultat pour une même clé et une même requête.

Une même clé avec un contenu différent doit être rejetée.

---

## 12. Gestion des erreurs

### 12.1 Structure standard

```json
{
  "code": "PAYMENT_LIMIT_EXCEEDED",
  "message": "Le plafond autorisé est dépassé.",
  "status": 422,
  "correlationId": "cor_123",
  "retryable": false,
  "details": {}
}
```

### 12.2 Catégories

- validation ;
- authentification ;
- autorisation ;
- ressource introuvable ;
- conflit ;
- limite ;
- risque ;
- partenaire ;
- temporaire ;
- système ;
- maintenance ;
- version incompatible.

### 12.3 Messages

Le message utilisateur doit être :

- compréhensible ;
- non technique ;
- non révélateur de secrets ;
- traduit ;
- accompagné d’une action possible.

Le message technique doit rester dans les journaux sécurisés.

---

## 13. Fichiers et documents

Les fichiers doivent être gérés via un service dédié.

Exigences :

- taille maximale ;
- formats autorisés ;
- antivirus ;
- métadonnées ;
- chiffrement ;
- contrôle d’accès ;
- URL temporaire ;
- expiration ;
- audit ;
- politique de conservation ;
- suppression logique ou définitive selon les règles.

Les documents sensibles ne doivent pas être publics.

---

## 14. Recherche

La recherche peut utiliser :

- PostgreSQL au début ;
- index dédiés ;
- moteur de recherche externe lorsque le volume le justifie.

Elle doit gérer :

- tolérance aux fautes ;
- filtres ;
- pertinence ;
- permissions ;
- pays ;
- langue ;
- géolocalisation ;
- masquage des données privées.

Un résultat ne doit jamais révéler une ressource inaccessible.

---

## 15. Temps réel

Technologies possibles :

- WebSocket ;
- Server-Sent Events ;
- push notifications ;
- polling contrôlé.

Cas d’usage :

- messages ;
- statut de paiement ;
- notifications ;
- caisse ;
- alertes ;
- présence ;
- synchronisation.

Le temps réel ne remplace pas la consultation de l’état officiel via API.

---

## 16. Mode hors ligne et synchronisation

### 16.1 Données consultables hors ligne

Selon l’application :

- profil ;
- préférences ;
- historique récent ;
- catalogue ;
- panier ;
- documents téléchargés ;
- favoris ;
- conversations récentes ;
- configuration locale.

### 16.2 Actions hors ligne

Seules les actions explicitement autorisées peuvent être mises en attente.

Chaque commande locale doit avoir :

- identifiant ;
- date ;
- appareil ;
- statut ;
- tentative ;
- version ;
- dépendances ;
- politique de conflit.

Aucun écran ne doit afficher une réussite définitive avant confirmation backend.

### 16.3 Résolution des conflits

Stratégies possibles :

- serveur prioritaire ;
- version la plus récente ;
- fusion contrôlée ;
- rejet ;
- validation manuelle.

Les opérations financières ne doivent pas utiliser une fusion automatique ambiguë.

---

## 17. Observabilité

### 17.1 Logs

Chaque log structuré doit pouvoir inclure :

- timestamp ;
- niveau ;
- service ;
- environnement ;
- corrélation ;
- utilisateur masqué ;
- requête ;
- durée ;
- résultat ;
- erreur ;
- partenaire.

Aucun mot de passe, PIN, CVV, OTP ou secret ne doit être journalisé.

### 17.2 Métriques

Métriques techniques :

- disponibilité ;
- latence ;
- erreurs ;
- saturation ;
- files ;
- base de données ;
- cache ;
- partenaires ;
- notifications ;
- déploiements.

Métriques métier :

- paiements ;
- transferts ;
- remboursements ;
- utilisateurs actifs ;
- commerçants actifs ;
- volume ;
- revenus ;
- fraude ;
- support.

### 17.3 Traces distribuées

Les traces doivent relier :

- requête entrante ;
- modules ;
- base ;
- partenaires ;
- événements ;
- traitements asynchrones.

### 17.4 Alertes

Alertes possibles :

- hausse des erreurs ;
- paiement partenaire indisponible ;
- file bloquée ;
- migration échouée ;
- latence excessive ;
- base saturée ;
- fraude anormale ;
- notifications non envoyées ;
- certificat expirant ;
- sauvegarde échouée.

---

## 18. Environnements

Environnements minimum :

- local ;
- test ;
- démonstration ;
- recette ;
- préproduction ;
- production.

Chaque environnement doit avoir :

- base séparée ;
- secrets séparés ;
- partenaires séparés ;
- domaines séparés ;
- logs séparés ;
- feature flags séparés ;
- permissions adaptées.

---

## 19. Gestion des secrets

Les secrets doivent être stockés dans un gestionnaire externe.

Sont concernés :

- clés API ;
- secrets JWT ;
- certificats ;
- mots de passe base ;
- clés de chiffrement ;
- secrets partenaires ;
- clés Apple et Google ;
- certificats TPE ;
- clés de signature.

Aucun secret réel dans :

- GitHub ;
- `.env.example` ;
- logs ;
- captures ;
- tickets ;
- documentation publique.

---

## 20. CI/CD

### 20.1 Validation continue

Chaque changement doit pouvoir déclencher :

- installation ;
- formatage ;
- lint ;
- vérification TypeScript ;
- validation Prisma ;
- génération Prisma ;
- tests unitaires ;
- tests d’intégration ;
- build ;
- analyse de dépendances ;
- contrôle de secrets ;
- contrôle de migrations.

### 20.2 Déploiement

Le déploiement doit être :

- traçable ;
- reproductible ;
- réversible ;
- limité par environnement ;
- protégé par permissions ;
- accompagné d’un health check ;
- accompagné d’une migration contrôlée.

### 20.3 Migrations

Règles :

1. Toute modification de schéma passe par une migration.
2. Les migrations destructives doivent être identifiées.
3. Les données doivent être sauvegardées.
4. Les migrations doivent être testées.
5. Les changements incompatibles doivent être déployés progressivement.
6. Les anciennes versions doivent être supportées pendant la transition si nécessaire.

---

## 21. Tests

### 21.1 Tests unitaires

Pour :

- règles métier ;
- calculs ;
- validations ;
- permissions ;
- transitions d’état ;
- formatage ;
- utilitaires.

### 21.2 Tests d’intégration

Pour :

- base de données ;
- modules ;
- files ;
- cache ;
- webhooks ;
- partenaires simulés ;
- authentification ;
- stockage.

### 21.3 Tests end-to-end

Pour les parcours critiques :

- inscription ;
- connexion ;
- KYC ;
- paiement ;
- transfert ;
- carte ;
- remboursement ;
- commerce ;
- TPE ;
- administration ;
- support.

### 21.4 Tests de contrat

Ils vérifient la compatibilité entre :

- applications ;
- SDK ;
- API ;
- partenaires ;
- événements ;
- webhooks.

### 21.5 Tests de sécurité

- permissions ;
- élévation de privilège ;
- injection ;
- session ;
- jetons ;
- rate limiting ;
- fichiers ;
- secrets ;
- webhooks ;
- accès horizontal ;
- accès vertical.

### 21.6 Tests de performance

- charge ;
- endurance ;
- pics ;
- paiements simultanés ;
- recherche ;
- messages ;
- exports ;
- génération de documents ;
- files.

---

## 22. Performance

Objectifs généraux :

- réponse API rapide pour les lectures courantes ;
- pagination systématique ;
- cache contrôlé ;
- index adaptés ;
- chargement différé ;
- compression ;
- optimisation d’images ;
- réduction des requêtes ;
- traitement asynchrone des tâches longues ;
- surveillance des requêtes lentes.

Les objectifs chiffrés seront définis par module.

---

## 23. Scalabilité

La plateforme doit pouvoir évoluer par :

- réplication des applications stateless ;
- cache ;
- files ;
- lecture répliquée ;
- partitionnement ;
- extraction de services ;
- CDN ;
- traitement asynchrone ;
- séparation géographique lorsque nécessaire.

Aucune optimisation prématurée ne doit augmenter inutilement la complexité.

---

## 24. Résilience

Le système doit prévoir :

- timeout ;
- retry ;
- circuit breaker ;
- idempotence ;
- file d’attente ;
- reprise ;
- health checks ;
- dégradation contrôlée ;
- cache de secours ;
- statut partenaire ;
- procédure d’incident.

Un partenaire indisponible ne doit pas rendre toute la plateforme inutilisable.

---

## 25. Sauvegarde et reprise

Doivent être définis :

- fréquence ;
- durée de conservation ;
- chiffrement ;
- vérification ;
- restauration ;
- responsabilités ;
- RPO ;
- RTO ;
- tests de reprise ;
- stockage hors site.

Une sauvegarde non testée ne doit pas être considérée comme fiable.

---

## 26. Sécurité applicative

Principes :

- validation de toutes les entrées ;
- encodage des sorties ;
- requêtes paramétrées ;
- contrôle d’accès ;
- limitation de débit ;
- protection CSRF si applicable ;
- protection XSS ;
- protection SSRF ;
- protection contre les téléchargements dangereux ;
- dépendances à jour ;
- revue de code ;
- scanners ;
- gestion des vulnérabilités.

---

## 27. Versionnement

### 27.1 API

Format recommandé :

```text
/api/v1/...
```

Les changements incompatibles doivent produire une nouvelle version ou une stratégie de compatibilité.

### 27.2 Applications

Chaque application possède :

- version ;
- build ;
- environnement ;
- date ;
- statut ;
- version minimale supportée.

### 27.3 Événements

Chaque événement doit avoir une version de schéma.

---

## 28. Documentation technique

La documentation doit inclure :

- démarrage local ;
- variables d’environnement ;
- architecture ;
- ADR ;
- API ;
- erreurs ;
- événements ;
- migrations ;
- déploiement ;
- sauvegarde ;
- incidents ;
- intégrations ;
- tests.

Les décisions importantes doivent être enregistrées sous forme d’ADR.

---

## 29. Règles Git

Branches recommandées :

- `main` : version stable ;
- branches fonctionnelles courtes ;
- branches correctives ;
- branches de version uniquement si nécessaires.

Chaque changement doit avoir :

- description ;
- périmètre ;
- tests ;
- migration éventuelle ;
- impact ;
- documentation ;
- approbation.

Les commits doivent être compréhensibles et traçables.

---

## 30. Critères d’acceptation

L’architecture technique est considérée comme validée lorsque :

- le monorepo est clairement organisé ;
- chaque application possède son périmètre ;
- le backend est modulaire ;
- les contrats sont partagés ;
- le ledger financier est séparé des simples soldes mutables ;
- les environnements sont isolés ;
- les secrets sont externes ;
- l’idempotence est prévue ;
- les événements sont versionnés ;
- l’observabilité est prévue ;
- les tests sont structurés ;
- les déploiements sont traçables ;
- les migrations sont contrôlées ;
- le mode hors ligne ne produit pas de fausse confirmation ;
- les dépendances partenaires sont encapsulées ;
- la plateforme peut évoluer sans réécriture complète.
