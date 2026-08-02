# 27 — CI/CD, GitHub, qualité du code et stratégie de déploiement de Mansa

## 1. Objet du document

Ce document définit le système officiel de gestion du code source, d’intégration continue, de livraison continue et de qualité logicielle de Mansa.

Il couvre :

- GitHub ;
- l’organisation du dépôt ;
- les branches ;
- les commits ;
- les pull requests ;
- les revues de code ;
- les règles de protection ;
- les workflows CI ;
- les workflows CD ;
- les tests ;
- le lint ;
- le formatage ;
- le typage ;
- Prisma ;
- les builds ;
- les artefacts ;
- les dépendances ;
- les scans de sécurité ;
- les déploiements ;
- les migrations ;
- les rollbacks ;
- les releases ;
- les versions ;
- les environnements ;
- les validations manuelles ;
- les journaux ;
- les permissions ;
- la traçabilité.

L’objectif est de garantir que chaque changement appliqué à Mansa soit :

- contrôlé ;
- testé ;
- reproductible ;
- sécurisé ;
- traçable ;
- réversible ;
- compatible avec les autres composants ;
- déployé dans le bon environnement ;
- approuvé selon son niveau de risque.

---

# 2. Principes fondamentaux

## 2.1 GitHub comme source officielle du code

Le dépôt GitHub officiel de Mansa doit être la source de vérité pour :

- le code ;
- les configurations non secrètes ;
- les workflows ;
- les migrations ;
- les contrats ;
- les scripts ;
- les tests ;
- la documentation technique ;
- les décisions d’architecture.

Aucune modification durable ne doit exister uniquement sur un ordinateur local.

## 2.2 Aucun déploiement manuel non traçable

Un déploiement doit être déclenché depuis un mécanisme contrôlé.

Il ne doit pas dépendre uniquement de commandes lancées manuellement sur un serveur.

## 2.3 Chaque changement doit être vérifiable

Chaque changement doit pouvoir être relié à :

- un commit ;
- une branche ;
- une pull request ;
- un auteur ;
- des tests ;
- un workflow ;
- un artefact ;
- un environnement ;
- un déploiement ;
- une version ;
- un éventuel rollback.

## 2.4 La CI valide, la CD déploie

La CI doit vérifier la qualité et la compatibilité.

La CD doit livrer uniquement ce qui a déjà été validé.

## 2.5 Production protégée

La production ne doit jamais accepter un code :

- non testé ;
- non revu ;
- non versionné ;
- non traçable ;
- construit localement ;
- provenant d’une branche non autorisée ;
- dépendant de secrets exposés ;
- contenant des migrations non validées.

---

# 3. Organisation du dépôt

Structure recommandée :

```text
mansa-fin/
├── apps/
├── packages/
├── database/
├── infrastructure/
├── docs/
├── scripts/
├── tests/
├── .github/
│   ├── workflows/
│   ├── ISSUE_TEMPLATE/
│   ├── PULL_REQUEST_TEMPLATE.md
│   ├── CODEOWNERS
│   └── dependabot.yml
├── package.json
├── pnpm-workspace.yaml
├── turbo.json
├── tsconfig.base.json
├── eslint.config.js
├── prettier.config.js
├── README.md
└── SECURITY.md
```

---

# 4. Stratégie de branches

Branches recommandées :

```text
main
feature/*
fix/*
hotfix/*
release/*
chore/*
docs/*
```

`main` représente l’état officiel stable.

---

# 5. Branche principale

La branche `main` doit être protégée.

Elle ne doit pas accepter :

- push direct non autorisé ;
- force push ;
- suppression ;
- commit non validé ;
- fusion sans checks obligatoires.

---

# 6. Branches de fonctionnalité

Format recommandé :

```text
feature/client-card-freeze
feature/merchant-stock-alert
feature/tpe-offline-sync
```

Une branche doit rester limitée à un périmètre clair.

---

# 7. Branches de correction

Exemples :

```text
fix/payment-timeout-status
fix/admin-permission-check
fix/prisma-migration-index
```

---

# 8. Hotfix

Les hotfix concernent :

- incident critique ;
- faille de sécurité ;
- erreur financière ;
- blocage production ;
- régression majeure.

Ils doivent rester soumis à :

- revue ;
- tests ;
- traçabilité ;
- validation ;
- rollback.

---

# 9. Commits

Les commits doivent être :

- explicites ;
- limités ;
- cohérents ;
- relisibles ;
- liés à un sujet précis.

Convention recommandée :

```text
feat:
fix:
docs:
refactor:
test:
chore:
ci:
build:
perf:
security:
```

Exemples :

```text
feat: ajouter le gel temporaire des cartes
fix: corriger le statut inconnu après timeout partenaire
docs: ajouter l’architecture CI/CD
ci: valider Prisma avant le build API
```

---

# 10. Commits interdits

Éviter :

```text
update
fix
test
changes
final
ok
```

Un message de commit doit expliquer ce qui a changé.

---

# 11. Pull Requests

Toute modification importante doit passer par une pull request.

Une PR doit contenir :

- objectif ;
- contexte ;
- changements ;
- impacts ;
- risques ;
- tests exécutés ;
- captures si interface ;
- migrations ;
- configuration ;
- rollback ;
- tickets liés.

---

# 12. Taille des Pull Requests

Une PR doit rester suffisamment petite pour être revue correctement.

Les très gros changements doivent être découpés lorsque possible.

---

# 13. Modèle de Pull Request

Exemple :

```markdown
## Objectif

## Changements

## Applications concernées

## Risques

## Tests exécutés

## Migration

## Configuration

## Captures

## Rollback

## Checklist
```

---

# 14. Revue de code

La revue doit vérifier :

- logique métier ;
- sécurité ;
- permissions ;
- erreurs ;
- tests ;
- performance ;
- lisibilité ;
- architecture ;
- données ;
- migrations ;
- compatibilité ;
- observabilité ;
- audit.

---

# 15. CODEOWNERS

Le fichier `CODEOWNERS` doit désigner les responsables de certains domaines.

Exemples :

```text
/apps/api-gateway/        @backend-team
/apps/tpe-android/        @tpe-team
/database/                @backend-team @database-reviewers
/infrastructure/          @platform-team
/packages/permissions/    @security-team
/docs/                    @product-architecture
```

---

# 16. Approbations

Le nombre d’approbations peut dépendre du risque.

Exemples :

- documentation : une approbation ;
- fonctionnalité standard : une ou deux ;
- sécurité : sécurité obligatoire ;
- ledger : backend + finance ;
- migration destructive : backend + plateforme ;
- production critique : double validation.

---

# 17. Conflits d’intérêts

Une personne ne doit pas être seule à :

- développer ;
- approuver ;
- déployer ;
- valider une opération critique.

---

# 18. Checks obligatoires

Avant fusion, les checks peuvent inclure :

- formatage ;
- lint ;
- typecheck ;
- tests unitaires ;
- tests d’intégration ;
- tests E2E ;
- build ;
- Prisma validate ;
- Prisma generate ;
- migration check ;
- scan dépendances ;
- scan secrets ;
- scan code ;
- tests de contrats ;
- tests de permissions.

---

# 19. Intégration continue

La CI doit se déclencher sur :

- pull request ;
- push sur branches contrôlées ;
- tag ;
- exécution manuelle autorisée ;
- planification pour certains scans.

---

# 20. Pipeline standard

Exemple :

```text
checkout
install
cache
lint
typecheck
prisma validate
prisma generate
unit tests
integration tests
build
security scan
artifact
report
```

---

# 21. Installation des dépendances

Le pipeline doit utiliser un lockfile.

Exemples :

```text
pnpm-lock.yaml
package-lock.json
yarn.lock
```

L’installation doit être déterministe.

---

# 22. Gestionnaire de paquets

Dans un monorepo TypeScript, une stratégie recommandée peut utiliser :

- pnpm ;
- workspaces ;
- Turborepo ;
- cache de build.

Le choix doit rester stable.

---

# 23. Cache CI

Le cache peut couvrir :

- dépendances ;
- builds ;
- tests ;
- client Prisma ;
- outils.

Le cache ne doit pas masquer une erreur de dépendance.

---

# 24. Lint

Le lint doit détecter :

- erreurs de syntaxe ;
- variables inutilisées ;
- imports incohérents ;
- promesses non gérées ;
- pratiques interdites ;
- dépendances non autorisées ;
- règles d’architecture.

---

# 25. Formatage

Le formatage doit être automatisé.

Outils possibles :

- Prettier ;
- formatters natifs ;
- règles par langage.

---

# 26. Typecheck

Le typage TypeScript doit être vérifié sans génération implicite non contrôlée.

Commande possible :

```bash
pnpm typecheck
```

---

# 27. Prisma Validate

La CI doit exécuter :

```bash
prisma validate
```

Elle doit échouer si :

- le schéma est invalide ;
- une relation est cassée ;
- une datasource est incohérente ;
- un générateur est invalide.

---

# 28. Prisma Generate

Le pipeline doit exécuter :

```bash
prisma generate
```

Le client doit être généré à partir du schéma du commit.

---

# 29. Vérification des migrations

La CI doit détecter :

- migration manquante ;
- migration invalide ;
- drift ;
- changement destructif ;
- divergence entre schéma et migrations ;
- migration non reproductible.

---

# 30. Build

Chaque application doit pouvoir être buildée indépendamment.

Exemples :

```bash
pnpm build:api
pnpm build:client
pnpm build:commerce
pnpm build:admin
pnpm build:web
```

---

# 31. Build global

Le monorepo doit aussi proposer un build global.

Exemple :

```bash
pnpm build
```

---

# 32. Tests unitaires

Les tests unitaires couvrent :

- fonctions ;
- services ;
- règles métier ;
- validations ;
- calculs ;
- permissions ;
- erreurs ;
- adaptateurs.

---

# 33. Tests d’intégration

Ils couvrent :

- base de données ;
- Prisma ;
- files ;
- cache ;
- modules backend ;
- webhooks ;
- partenaires simulés ;
- contrats.

---

# 34. Tests End-to-End

Ils couvrent les parcours critiques.

Exemples :

- inscription ;
- connexion ;
- paiement ;
- transfert ;
- remboursement ;
- carte ;
- création commerce ;
- activation TPE ;
- configuration admin.

---

# 35. Tests de contrats

Ils vérifient la compatibilité entre :

- mobile et API ;
- web et API ;
- TPE et API ;
- services ;
- webhooks ;
- événements ;
- partenaires.

---

# 36. Tests de permissions

Chaque rôle important doit être testé.

Exemples :

- autorisé ;
- interdit ;
- accès limité ;
- accès tenant ;
- accès pays ;
- accès temporaire ;
- accès expiré.

---

# 37. Tests de sécurité

La CI doit inclure selon le contexte :

- SAST ;
- scan de dépendances ;
- scan de secrets ;
- scan conteneur ;
- scan IaC ;
- tests de permissions ;
- tests d’injection ;
- vérification des packages compromis.

---

# 38. Scan de secrets

Le pipeline doit bloquer :

- clé API ;
- token ;
- mot de passe ;
- certificat privé ;
- secret JWT ;
- fichier `.env` sensible.

---

# 39. Dépendances

Les dépendances doivent être :

- versionnées ;
- contrôlées ;
- scannées ;
- mises à jour ;
- limitées ;
- justifiées.

---

# 40. Dependabot ou équivalent

Un outil automatisé peut proposer :

- mises à jour de sécurité ;
- mises à jour mineures ;
- mises à jour majeures ;
- correctifs.

Les mises à jour ne doivent pas être fusionnées sans tests.

---

# 41. Licences

Les dépendances doivent être vérifiées pour éviter :

- licence incompatible ;
- obligation non respectée ;
- package non maintenu ;
- code douteux ;
- dépendance supprimée.

---

# 42. Artefacts

Les builds doivent produire des artefacts identifiables.

Exemples :

- image conteneur ;
- bundle web ;
- APK ;
- AAB ;
- archive ;
- rapport ;
- documentation OpenAPI ;
- client SDK.

---

# 43. Immutabilité des artefacts

Un artefact publié ne doit pas être modifié.

Chaque artefact doit être lié à :

- commit ;
- tag ;
- version ;
- date ;
- environnement cible ;
- checksum ;
- signature.

---

# 44. Signature

Les artefacts sensibles peuvent être signés.

Exemples :

- images conteneurs ;
- APK ;
- mises à jour TPE ;
- packages ;
- bundles de configuration.

---

# 45. Registre

Les artefacts doivent être stockés dans un registre contrôlé.

Exemples :

- registry conteneur ;
- GitHub Packages ;
- stockage release ;
- dépôt interne.

---

# 46. Releases

Une release doit contenir :

- version ;
- notes ;
- changements ;
- corrections ;
- migrations ;
- limitations ;
- dépendances ;
- risques ;
- rollback ;
- date ;
- responsable.

---

# 47. Tags Git

Format recommandé :

```text
v1.0.0
api-v1.4.2
client-v2.3.1
tpe-v1.8.0
```

La stratégie doit être cohérente avec le monorepo.

---

# 48. Versionnement sémantique

Format :

```text
MAJOR.MINOR.PATCH
```

- `MAJOR` : changement incompatible ;
- `MINOR` : nouvelle fonctionnalité compatible ;
- `PATCH` : correction compatible.

---

# 49. Changelog

Le changelog doit distinguer :

- ajouté ;
- modifié ;
- corrigé ;
- déprécié ;
- supprimé ;
- sécurité ;
- migration.

---

# 50. Environnements de déploiement

Les déploiements doivent suivre une progression contrôlée :

```text
development
test
demo
staging
preproduction
production
```

---

# 51. Promotion d’artefact

Le même artefact doit être promu entre environnements.

Il ne doit pas être reconstruit différemment pour la production sans raison.

---

# 52. Déploiement en développement

Peut être automatique après fusion selon les règles.

---

# 53. Déploiement en test

Peut être automatique après validation CI.

---

# 54. Déploiement en préproduction

Doit exiger :

- checks réussis ;
- artefact identifié ;
- migrations validées ;
- tests ;
- approbation éventuelle.

---

# 55. Déploiement en production

Doit exiger selon le risque :

- branche ou tag autorisé ;
- CI réussie ;
- artefact signé ;
- approbation ;
- fenêtre de déploiement ;
- plan de rollback ;
- monitoring ;
- communication.

---

# 56. GitHub Environments

Les environnements GitHub peuvent protéger :

- secrets ;
- approbateurs ;
- branches autorisées ;
- délais ;
- logs ;
- variables.

---

# 57. Secrets CI/CD

Les secrets doivent être stockés dans :

- GitHub Secrets ;
- gestionnaire de secrets cloud ;
- identités temporaires ;
- OIDC.

Éviter les clés permanentes lorsque possible.

---

# 58. OIDC

La CI peut utiliser une identité temporaire pour accéder au cloud.

Avantages :

- pas de clé longue durée ;
- permissions limitées ;
- expiration ;
- audit ;
- rotation simplifiée.

---

# 59. Déploiement progressif

Les stratégies peuvent inclure :

- rolling ;
- canary ;
- blue/green ;
- feature flags ;
- pays ;
- cohorte ;
- région ;
- pourcentage.

---

# 60. Smoke tests

Après déploiement, exécuter :

- health check ;
- authentification ;
- endpoint principal ;
- lecture base ;
- accès cache ;
- file ;
- version ;
- test partenaire non financier si possible.

---

# 61. Tests post-déploiement

Pour un changement critique :

- test paiement simulé ;
- test rollback ;
- vérification métriques ;
- vérification erreurs ;
- vérification version ;
- vérification migration ;
- vérification permissions.

---

# 62. Rollback

Le pipeline doit permettre :

- retour à l’artefact précédent ;
- restauration de configuration ;
- désactivation par feature flag ;
- retrait du trafic ;
- rollback application ;
- procédure base compatible.

---

# 63. Rollback automatique

Peut être déclenché si :

- erreurs dépassent un seuil ;
- latence augmente fortement ;
- health checks échouent ;
- crashs augmentent ;
- paiements échouent ;
- migration échoue ;
- service ne démarre pas.

---

# 64. Migrations pendant déploiement

Les migrations doivent être traitées séparément du simple démarrage applicatif lorsque nécessaire.

Elles doivent être :

- uniques ;
- contrôlées ;
- observables ;
- interrompables si possible ;
- auditées ;
- approuvées.

---

# 65. Migration destructive

Elle doit exiger :

- backup ;
- revue ;
- validation ;
- test sur volume ;
- plan de retour ;
- fenêtre ;
- double approbation ;
- communication.

---

# 66. Database Drift

Le pipeline doit détecter les divergences entre :

- schéma Prisma ;
- migrations ;
- base cible ;
- client généré.

---

# 67. Déploiement mobile

Les applications mobiles nécessitent :

- build signé ;
- numéro de version ;
- numéro de build ;
- environnement ;
- certificats ;
- tests appareils ;
- publication progressive ;
- notes de version.

---

# 68. iOS

Le pipeline iOS peut gérer :

- archive ;
- signature ;
- provisioning ;
- TestFlight ;
- App Store ;
- validation ;
- version ;
- symboles de crash.

---

# 69. Android

Le pipeline Android peut gérer :

- APK ;
- AAB ;
- signature ;
- Play Console ;
- tracks internes ;
- bêta ;
- production progressive ;
- mapping de crash.

---

# 70. TPE

Les mises à jour TPE doivent être :

- signées ;
- ciblées ;
- versionnées ;
- progressives ;
- compatibles matériel ;
- planifiées ;
- réversibles.

---

# 71. Sites web

Les sites peuvent utiliser :

- preview par PR ;
- staging ;
- production ;
- invalidation CDN ;
- vérification SEO ;
- tests visuels ;
- Core Web Vitals.

---

# 72. Preview de Pull Request

Une preview peut être créée pour :

- site public ;
- site professionnel ;
- portail Admin ;
- composants UI.

Elle ne doit pas utiliser les secrets ni les données de production.

---

# 73. Documentation OpenAPI

La CI doit pouvoir :

- générer OpenAPI ;
- vérifier les changements ;
- publier une documentation ;
- détecter les changements cassants ;
- versionner les contrats.

---

# 74. Génération SDK

Les SDK internes peuvent être générés depuis les contrats.

Ils doivent être :

- versionnés ;
- testés ;
- publiés ;
- liés à l’API ;
- compatibles.

---

# 75. Rapports CI

Le pipeline doit conserver :

- résultats de tests ;
- couverture ;
- lint ;
- build ;
- scans ;
- artefacts ;
- migrations ;
- temps d’exécution ;
- erreurs.

---

# 76. Couverture de tests

La couverture ne doit pas être le seul indicateur.

Elle doit être utilisée pour détecter :

- parties non testées ;
- baisse importante ;
- domaines critiques sans tests.

---

# 77. Seuils

Des seuils plus élevés peuvent être imposés pour :

- ledger ;
- paiements ;
- auth ;
- permissions ;
- cartes ;
- fraude ;
- migrations.

---

# 78. Flaky tests

Les tests instables doivent être :

- identifiés ;
- corrigés ;
- suivis ;
- isolés temporairement ;
- non ignorés durablement.

---

# 79. Temps de pipeline

Le pipeline doit rester suffisamment rapide.

Optimisations possibles :

- parallélisation ;
- cache ;
- détection des packages affectés ;
- tests ciblés ;
- matrice ;
- réutilisation d’artefacts.

---

# 80. Monorepo et changements affectés

La CI peut exécuter uniquement les tâches affectées, tout en gardant des validations globales périodiques.

---

# 81. Workflows réutilisables

Créer des workflows communs pour :

- installation ;
- tests ;
- build ;
- scan ;
- déploiement ;
- notification ;
- rollback.

---

# 82. Workflows planifiés

Exemples :

- scan sécurité quotidien ;
- vérification dépendances ;
- test restauration ;
- build complet ;
- tests E2E ;
- contrôle certificats ;
- vérification drift.

---

# 83. Exécution manuelle

Un workflow manuel doit préciser :

- acteur ;
- environnement ;
- version ;
- raison ;
- paramètres ;
- confirmation ;
- approbation ;
- audit.

---

# 84. Permissions GitHub Actions

Les workflows doivent utiliser les permissions minimales.

Exemple :

```yaml
permissions:
  contents: read
```

Des permissions supplémentaires ne sont ajoutées que si nécessaires.

---

# 85. Actions tierces

Les actions tierces doivent être :

- vérifiées ;
- épinglées à une version ou un SHA ;
- maintenues ;
- limitées ;
- remplacées si compromises.

---

# 86. Sécurité de la Supply Chain

Le pipeline doit protéger :

- dépendances ;
- actions ;
- artefacts ;
- images ;
- signatures ;
- provenance ;
- secrets ;
- registres.

---

# 87. SBOM

Les artefacts critiques peuvent inclure une Software Bill of Materials.

Elle liste :

- composants ;
- versions ;
- licences ;
- vulnérabilités ;
- origine.

---

# 88. Provenance

Chaque artefact doit pouvoir prouver :

- quel code l’a généré ;
- quel workflow ;
- quelle version ;
- quel environnement de build ;
- quels contrôles.

---

# 89. Accès GitHub

Les accès doivent être gérés par rôle.

Exemples :

- lecture ;
- triage ;
- écriture ;
- maintenance ;
- administration.

---

# 90. Comptes personnels

Les accès doivent être individuels.

Les comptes partagés sont interdits.

---

# 91. MFA

Le MFA doit être obligatoire pour les comptes ayant accès au dépôt sensible.

---

# 92. Protection des branches

Les règles peuvent exiger :

- PR obligatoire ;
- approbation ;
- checks ;
- branche à jour ;
- conversations résolues ;
- commits signés ;
- historique linéaire ;
- restrictions de push.

---

# 93. Commits signés

Les commits critiques peuvent exiger une signature vérifiée.

---

# 94. Force Push

Le force push doit être interdit sur :

- `main` ;
- branches de release ;
- branches protégées.

---

# 95. Suppression de branche

Les branches fusionnées peuvent être supprimées automatiquement.

Les branches protégées ne doivent pas être supprimables librement.

---

# 96. Audit GitHub

Surveiller :

- ajout de membre ;
- changement de permission ;
- modification de protection ;
- création de secret ;
- workflow modifié ;
- déploiement ;
- suppression ;
- force push ;
- accès anormal.

---

# 97. Incidents CI/CD

Exemples :

- secret exposé ;
- artefact compromis ;
- workflow modifié ;
- dépendance malveillante ;
- déploiement erroné ;
- migration échouée ;
- rollback impossible ;
- compte compromis.

---

# 98. Réponse à incident

Le processus doit prévoir :

1. arrêt des déploiements ;
2. révocation des accès ;
3. rotation des secrets ;
4. isolation de l’artefact ;
5. rollback ;
6. analyse ;
7. correction ;
8. communication ;
9. reprise ;
10. post-mortem.

---

# 99. Administration

Le portail Admin technique peut afficher :

- versions ;
- déploiements ;
- environnements ;
- état CI ;
- artefacts ;
- migrations ;
- rollbacks ;
- incidents ;
- dernières releases.

Il ne doit pas permettre un accès GitHub complet sans permission.

---

# 100. Permissions

Exemples :

```text
cicd.read
cicd.workflow.run
cicd.deployment.read
cicd.deployment.approve
cicd.production.deploy
cicd.rollback.execute
cicd.artifact.read
cicd.release.create
cicd.migration.approve
cicd.audit.read
```

---

# 101. Actions critiques

Doivent être protégées :

- déploiement production ;
- rollback production ;
- modification workflow ;
- ajout secret ;
- migration ;
- publication mobile ;
- publication TPE ;
- suppression artefact ;
- modification de protection de branche.

---

# 102. Double validation

Recommandée pour :

- production ;
- migration destructive ;
- hotfix financier ;
- changement sécurité ;
- workflow avec accès secrets ;
- publication TPE ;
- rollback critique ;
- modification IAM CI/CD.

---

# 103. API internes

Exemples :

```http
GET    /cicd/workflows
GET    /cicd/runs
GET    /cicd/deployments
GET    /cicd/releases
GET    /cicd/artifacts

POST   /cicd/deployments/{id}/approve
POST   /cicd/deployments/{id}/rollback
POST   /cicd/releases
```

---

# 104. Modèles

- Repository
- BranchPolicy
- PullRequest
- CodeReview
- CiWorkflow
- CiRun
- CiJob
- CiCheck
- BuildArtifact
- ArtifactSignature
- Deployment
- DeploymentApproval
- Release
- ReleaseNote
- Rollback
- MigrationDeployment
- SecurityScan
- DependencyUpdate
- CicdIncident
- CicdAudit

---

# 105. Règles métier

1. GitHub est la source officielle du code.
2. `main` est protégée.
3. Les changements importants passent par une PR.
4. Les checks obligatoires doivent réussir.
5. Les secrets ne sont jamais committés.
6. Les dépendances sont verrouillées.
7. Les artefacts sont immuables.
8. Les artefacts sont liés à un commit.
9. La production utilise un artefact validé.
10. Les environnements sont séparés.
11. Les migrations sont contrôlées.
12. Les déploiements sont traçables.
13. Les rollbacks sont préparés.
14. Les workflows utilisent des permissions minimales.
15. Les actions tierces sont vérifiées.
16. Les scans de sécurité sont obligatoires.
17. Les tests de permissions couvrent les rôles critiques.
18. Les hotfix restent audités.
19. Les applications mobiles sont signées.
20. Les mises à jour TPE sont signées.
21. Les previews n’utilisent pas de données production.
22. Les approbations dépendent du risque.
23. Les accès GitHub sont individuels.
24. Le MFA est obligatoire.
25. Les incidents CI/CD suivent une procédure officielle.

---

# 106. Analytics

Événements possibles :

```text
cicd_pull_request_created
cicd_pull_request_approved
cicd_check_failed
cicd_check_succeeded
cicd_build_started
cicd_build_completed
cicd_security_scan_failed
cicd_artifact_created
cicd_deployment_started
cicd_deployment_completed
cicd_deployment_failed
cicd_rollback_started
cicd_rollback_completed
cicd_release_created
cicd_migration_started
cicd_migration_failed
cicd_production_approval_granted
```

---

# 107. Tests

- tests de workflow ;
- tests de branches ;
- tests de protection ;
- tests de permissions ;
- tests de lint ;
- tests de typecheck ;
- tests de build ;
- tests Prisma ;
- tests de migration ;
- tests de scan ;
- tests d’artefact ;
- tests de signature ;
- tests de promotion ;
- tests de déploiement ;
- tests canary ;
- tests rollback ;
- tests mobile ;
- tests TPE ;
- tests de secret ;
- tests de provenance ;
- tests d’incident CI/CD.

---

# 108. Critères d’acceptation

Le système CI/CD est validé lorsque :

- la branche principale est protégée ;
- les pull requests sont obligatoires pour les changements importants ;
- les checks de qualité sont exécutés ;
- Prisma est validé ;
- les builds sont reproductibles ;
- les tests sont automatisés ;
- les scans de sécurité sont actifs ;
- les secrets sont protégés ;
- les artefacts sont versionnés ;
- les déploiements utilisent des artefacts immuables ;
- les environnements sont séparés ;
- les approbations production sont configurées ;
- les migrations sont contrôlées ;
- les déploiements progressifs fonctionnent ;
- les rollbacks sont testés ;
- les versions mobiles et TPE sont signées ;
- les actions sont auditables ;
- les tests couvrent les scénarios critiques.
