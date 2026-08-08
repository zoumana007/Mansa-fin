# Volume 1 — Architecture technique

## 1. Objectif

Ce document définit l’architecture technique de référence de Mansa. Il transforme la vision fonctionnelle en un socle modulaire, sécurisé, observable et extensible, capable de desservir les applications Client, Commerçant, TPE, Admin Lite, Annuaire/Hub, portail Admin Web, site public et futures intégrations partenaires.

L’architecture doit permettre un lancement progressif au Mali puis l’ajout d’autres pays sans réécriture du cœur métier.

## 2. Principes d’architecture

1. **Modularité forte** : chaque domaine métier possède ses propres règles, contrats et responsabilités.
2. **Séparation des responsabilités** : présentation, orchestration, métier, persistance et intégrations externes restent découplés.
3. **API-first** : toutes les applications consomment des contrats versionnés.
4. **Idempotence** : toute opération financière ou asynchrone critique est rejouable sans double effet.
5. **Traçabilité** : chaque requête, transaction et action sensible possède un identifiant de corrélation et un audit.
6. **Sécurité par défaut** : moindre privilège, segmentation, chiffrement et validation systématique des entrées.
7. **Configuration par environnement et pays** : règles, plafonds, partenaires et fonctionnalités sont configurables.
8. **Dégradation maîtrisée** : une panne partenaire ne doit pas rendre indisponible toute la plateforme.
9. **Observabilité native** : logs, métriques, traces et alertes sont prévus dès le socle.
10. **Aucune dépendance métier directe à un partenaire externe** : toutes les intégrations passent par des adaptateurs.

## 3. Vue d’ensemble

L’écosystème Mansa est organisé autour des couches suivantes :

- Applications clientes : mobile, web et TPE.
- API Gateway / Backend for Frontend.
- Modules métier internes.
- Services de plateforme transverses.
- Couche de données.
- Bus d’événements et traitements asynchrones.
- Adaptateurs d’intégration externes.
- Observabilité, sécurité et administration.

Flux logique :

`Application -> API Gateway -> Auth/RBAC -> Module métier -> Persistance / Événement -> Adaptateur partenaire`

## 4. Applications

### 4.1 Application Client

Responsabilités principales :

- authentification ;
- consultation du solde ;
- paiements ;
- transferts ;
- QR ;
- cartes ;
- épargne et coffres ;
- reçus ;
- support ;
- notifications ;
- profil et KYC.

### 4.2 Application Commerçant

Responsabilités :

- encaissements ;
- catalogue et produits ;
- factures et reçus ;
- employés ;
- historique ;
- remboursements ;
- promotions ;
- fidélité ;
- reporting ;
- mini-site commerçant.

### 4.3 Application TPE

Le TPE doit être particulièrement isolé du reste du système.

Fonctions :

- paiement carte ;
- QR ;
- NFC ;
- validation commerçant ;
- annulation et remboursement contrôlés ;
- synchronisation différée si le mode offline est autorisé ;
- télémétrie du terminal ;
- mises à jour signées.

Aucune donnée sensible de carte ne doit être conservée en clair sur le terminal.

### 4.4 Admin Lite

Application mobile réservée aux opérations administratives autorisées :

- supervision ;
- validation ciblée ;
- support terrain ;
- consultation d’incidents ;
- actions urgentes selon rôle.

### 4.5 Annuaire / Hub

Fonctions :

- recherche d’entreprises et services ;
- géolocalisation ;
- pages professionnelles ;
- promotions ;
- catégories ;
- liens vers les paiements Mansa.

### 4.6 Portail Admin Web

Le portail Admin est le centre opérationnel de la plateforme.

Il doit gérer :

- utilisateurs ;
- commerçants ;
- agents ;
- KYC/KYB ;
- transactions ;
- frais et commissions ;
- plafonds ;
- partenaires ;
- fraude ;
- support ;
- pays ;
- permissions ;
- audit ;
- fonctionnalités ;
- rapports ;
- module État.

## 5. Backend et monorepo

Architecture de référence : monorepo TypeScript utilisant PNPM et Turborepo.

Structure recommandée :

```text
apps/
  api/
  admin-web/
  public-web/
  merchant-web/
  mobile-client/
  mobile-merchant/
  admin-lite/
  hub/
packages/
  contracts/
  auth/
  config/
  database/
  observability/
  ui/
  validation/
  domain/
  testing/
infra/
  docker/
  ci/
  deployment/
```

Le découpage exact peut évoluer, mais les dépendances doivent rester orientées vers les contrats partagés et jamais créer de dépendances circulaires entre domaines.

## 6. API Gateway

Le Gateway est le point d’entrée principal des clients.

Responsabilités :

- authentification ;
- validation des jetons ;
- contrôle de version d’API ;
- limitation de débit ;
- corrélation des requêtes ;
- normalisation des erreurs ;
- validation des schémas ;
- politique CORS ;
- protection contre les abus ;
- routage vers les modules internes.

Le Gateway ne doit pas contenir les règles métier profondes.

## 7. Modules métier backend

Les modules doivent être indépendants sur le plan logique.

### 7.1 Identité et authentification

- utilisateurs ;
- sessions ;
- MFA ;
- appareils connus ;
- récupération ;
- révocation ;
- biométrie côté appareil ;
- gestion des risques de connexion.

### 7.2 KYC / KYB

- identité ;
- documents ;
- statuts de vérification ;
- bénéficiaires effectifs ;
- conformité commerçant ;
- historique des décisions ;
- renouvellement documentaire.

### 7.3 Wallets

- portefeuille principal ;
- sous-portefeuilles ;
- soldes disponibles et bloqués ;
- réservations ;
- écritures de ledger ;
- rapprochement.

Le solde ne doit jamais être modifié directement sans écriture comptable associée.

### 7.4 Transactions

- paiement ;
- transfert ;
- retrait ;
- dépôt ;
- remboursement ;
- annulation ;
- frais ;
- commission ;
- statut ;
- machine d’états.

### 7.5 Cartes

- carte physique ;
- carte virtuelle ;
- carte temporaire ;
- contrôles de dépenses ;
- gel/dégel ;
- tokenisation ;
- cycle de vie ;
- intégration émetteur/processeur.

### 7.6 Commerçants

- profil ;
- points de vente ;
- employés ;
- terminaux ;
- encaissements ;
- règlements ;
- commissions ;
- facturation.

### 7.7 Mobile Money

- Orange Money et futurs opérateurs ;
- cash-in ;
- cash-out ;
- transfert ;
- statut asynchrone ;
- rapprochement ;
- webhooks.

Chaque opérateur doit avoir son propre adaptateur.

### 7.8 Notifications

- push ;
- SMS ;
- e-mail ;
- notifications in-app ;
- modèles ;
- préférences ;
- priorités ;
- reprise en cas d’échec.

### 7.9 Support

- tickets ;
- incidents ;
- litiges ;
- pièces jointes ;
- historique ;
- SLA ;
- escalade.

### 7.10 Fraude et risque

- règles ;
- scoring ;
- listes de surveillance internes ;
- vélocité ;
- anomalies ;
- blocage temporaire ;
- revue manuelle.

### 7.11 Module État

- amendes ;
- taxes ;
- bourses ;
- scolarité ;
- cartes étudiantes ;
- paiements publics ;
- identification des agents ;
- traçabilité anticorruption.

## 8. Base de données

Technologie de référence : PostgreSQL avec Prisma comme couche d’accès principale.

Exigences :

- migrations versionnées ;
- contraintes d’intégrité en base ;
- index documentés ;
- clés étrangères explicites ;
- transactions ACID pour les opérations critiques ;
- dates enregistrées en UTC ;
- montants en unités mineures entières ;
- devise stockée explicitement ;
- archivage contrôlé ;
- aucune suppression silencieuse de donnée financière.

Les données fortement sensibles doivent être chiffrées au repos ou au niveau applicatif selon leur nature.

## 9. Ledger financier

Le ledger doit constituer la source de vérité des mouvements financiers.

Principes :

- double entrée recommandée pour les flux financiers ;
- écriture immuable ;
- compensation par écriture inverse plutôt que modification historique ;
- référence métier unique ;
- idempotency key ;
- horodatage ;
- acteur ;
- source ;
- devise ;
- montant ;
- statut.

Les vues de solde sont dérivées du ledger ou maintenues par mécanisme transactionnel vérifiable.

## 10. Événements et traitements asynchrones

Les tâches longues ou dépendantes de partenaires externes doivent être traitées de manière asynchrone.

Exemples :

- notification ;
- génération de reçu ;
- export ;
- rapprochement ;
- webhook partenaire ;
- analyse fraude ;
- synchronisation ;
- reporting.

Chaque événement doit contenir :

- identifiant unique ;
- type ;
- version ;
- date ;
- correlationId ;
- causationId si applicable ;
- contexte minimal nécessaire.

Les consommateurs doivent être idempotents.

## 11. Intégrations externes

Aucune API partenaire ne doit être appelée directement depuis les contrôleurs métier.

Chaque partenaire est encapsulé dans un adaptateur exposant une interface interne stable.

Catégories d’intégrations :

- banques ;
- Mobile Money ;
- Visa/Mastercard ;
- processeurs cartes ;
- fournisseurs KYC ;
- SMS ;
- e-mail ;
- push ;
- services publics ;
- stockage ;
- analytics.

Chaque adaptateur doit gérer :

- timeout ;
- retry contrôlé ;
- circuit breaker ;
- idempotence ;
- journalisation ;
- signature ;
- vérification des webhooks ;
- mapping des erreurs ;
- métriques.

## 12. Authentification et autorisation

Le modèle doit combiner RBAC et, lorsque nécessaire, ABAC.

Exemples de rôles :

- CLIENT ;
- MERCHANT_OWNER ;
- MERCHANT_EMPLOYEE ;
- AGENT ;
- PUBLIC_AGENT ;
- SUPPORT ;
- COMPLIANCE ;
- RISK ;
- FINANCE ;
- ADMIN ;
- SUPER_ADMIN.

Les permissions doivent être explicites et auditables.

Les actions à fort impact nécessitent une protection renforcée : MFA, justification, double validation ou politique maker-checker selon le risque.

## 13. Sécurité

Exigences minimales :

- TLS partout ;
- secrets hors dépôt ;
- rotation des secrets ;
- mots de passe hachés avec algorithme robuste ;
- tokens à durée de vie limitée ;
- révocation de session ;
- protection CSRF lorsque pertinente ;
- validation stricte des entrées ;
- requêtes paramétrées ;
- headers de sécurité ;
- rate limiting ;
- détection d’abus ;
- journalisation des actions sensibles ;
- séparation des environnements ;
- sauvegardes chiffrées ;
- contrôle des dépendances ;
- analyse de vulnérabilités dans la CI.

Aucune clé API, aucun mot de passe, aucun certificat privé ni identifiant partenaire réel ne doit être commité.

## 14. Gestion des environnements

Environnements obligatoires :

- Local ;
- Démo ;
- Recette ;
- Production.

Chaque environnement possède :

- ses propres secrets ;
- sa propre base ;
- ses propres endpoints ;
- ses propres clés ;
- ses propres webhooks ;
- ses propres ressources cloud.

Une donnée Production ne doit pas être copiée vers Démo ou Recette sans anonymisation explicite.

## 15. Multi-pays

Les règles ne doivent jamais être codées en dur pour un seul pays.

La configuration pays doit gérer au minimum :

- code pays ;
- devise ;
- fuseau ;
- langues ;
- plafonds ;
- frais ;
- partenaires ;
- formats téléphoniques ;
- documents KYC ;
- fonctionnalités actives ;
- règles réglementaires locales.

Le Mali constitue la configuration initiale, pas une contrainte architecturale.

## 16. Observabilité

Chaque service doit produire :

- logs structurés ;
- métriques ;
- traces distribuées ;
- événements d’audit.

Champs de corrélation recommandés :

- requestId ;
- correlationId ;
- userId ;
- merchantId ;
- transactionId ;
- deviceId ;
- country ;
- environment.

Les données sensibles ne doivent jamais apparaître en clair dans les logs.

## 17. Résilience

La plateforme doit prévoir :

- timeouts courts et explicites ;
- retries avec backoff ;
- circuit breakers ;
- queues de reprise ;
- dead-letter queues ;
- health checks ;
- readiness checks ;
- graceful shutdown ;
- mécanismes de reprise après incident.

Un partenaire indisponible doit être signalé clairement sans provoquer une cascade de panne.

## 18. Cache

Le cache peut être utilisé pour :

- configuration ;
- rate limiting ;
- sessions techniques ;
- données de lecture fréquente ;
- verrous distribués lorsque nécessaire.

Aucun cache ne doit devenir la source de vérité des soldes financiers.

## 19. API et contrats

Les contrats d’API doivent être :

- versionnés ;
- documentés ;
- validés ;
- testés ;
- rétrocompatibles lorsque possible.

Format d’erreur standard recommandé :

```json
{
  "code": "PAYMENT_LIMIT_EXCEEDED",
  "message": "Operation not allowed",
  "requestId": "...",
  "details": {}
}
```

Les messages internes détaillés ne doivent pas exposer d’informations sensibles aux clients.

## 20. Feature flags

Les fonctionnalités à risque ou en déploiement progressif doivent être contrôlées par drapeaux.

Ciblage possible :

- pays ;
- environnement ;
- rôle ;
- segment ;
- utilisateur ;
- partenaire ;
- version d’application.

Un kill switch global doit exister pour les flux critiques.

## 21. CI/CD

Chaque changement doit passer par une chaîne automatisée comprenant au minimum :

1. installation verrouillée des dépendances ;
2. format check ;
3. lint ;
4. TypeScript ;
5. tests unitaires ;
6. tests d’intégration pertinents ;
7. build ;
8. analyse de dépendances ;
9. contrôle des secrets ;
10. génération d’artefacts versionnés.

La production ne doit pas être déployée depuis un poste développeur sans pipeline contrôlé.

## 22. Tests

Niveaux attendus :

- unitaires ;
- intégration ;
- contrats ;
- end-to-end ;
- sécurité ;
- performance ;
- résilience ;
- migrations ;
- reprise.

Les scénarios financiers critiques doivent avoir des tests de non-régression dédiés.

## 23. Sauvegarde et reprise

La stratégie doit prévoir :

- sauvegardes automatisées ;
- chiffrement ;
- réplication adaptée ;
- tests réguliers de restauration ;
- RPO/RTO définis ;
- procédure d’incident documentée.

Une sauvegarde non testée ne doit pas être considérée comme une sauvegarde fiable.

## 24. Performance et capacité

La conception doit permettre :

- montée en charge horizontale des services stateless ;
- files d’attente pour absorber les pointes ;
- indexation contrôlée ;
- pagination obligatoire ;
- limitation des exports lourds ;
- traitement différé des rapports ;
- tests de charge avant lancement majeur.

## 25. Règles de gouvernance technique

- Toute nouvelle intégration externe nécessite un adaptateur.
- Toute nouvelle permission doit être documentée.
- Toute modification du ledger exige revue technique renforcée.
- Toute migration destructive exige plan de retour arrière.
- Toute nouvelle donnée sensible doit avoir une politique de rétention.
- Toute nouvelle fonctionnalité critique doit avoir métriques et alertes avant activation Production.

## 26. Critères d’acceptation

L’architecture technique est considérée correctement implémentée lorsque :

- les domaines sont clairement séparés ;
- l’API est versionnée ;
- les opérations financières sont idempotentes ;
- le ledger est immuable ;
- les rôles et permissions sont centralisés ;
- les secrets sont absents du dépôt ;
- les environnements sont séparés ;
- les partenaires sont isolés par adaptateurs ;
- logs, métriques et traces sont disponibles ;
- la CI bloque les régressions de qualité ;
- les applications peuvent évoluer indépendamment sans dupliquer les règles métier ;
- l’ajout d’un nouveau pays reste principalement une opération de configuration et d’intégration.
