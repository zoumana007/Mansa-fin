# 63 — Infrastructure Cloud, DevOps et déploiement Mansa : environnements, CI/CD, conteneurs, sécurité, secrets, réseau, haute disponibilité, mises à jour, rollback et administration centralisée

## 1. Objet du document

Ce document définit l’architecture officielle de l’**Infrastructure Cloud, DevOps et Déploiement Mansa**.

Cette infrastructure doit permettre d’héberger, construire, tester, déployer, mettre à jour, superviser et restaurer l’ensemble de l’écosystème Mansa.

Elle couvre notamment :

- les applications mobiles ;
- les applications web ;
- les portails internes ;
- les portails partenaires ;
- les API ;
- les microservices ;
- le ledger ;
- les bases de données ;
- les files de messages ;
- les caches ;
- les plateformes Data ;
- la plateforme Jini ;
- les services de notifications ;
- les connecteurs partenaires ;
- les TPE ;
- les DAB ;
- les outils d’administration ;
- les environnements de test ;
- les environnements de Production ;
- les sauvegardes ;
- les secrets ;
- les certificats ;
- le réseau ;
- les déploiements ;
- les mises à jour ;
- les rollbacks ;
- la continuité de service ;
- les coûts ;
- les audits.

L’objectif est de fournir une infrastructure :

- sécurisée ;
- hautement disponible ;
- automatisée ;
- reproductible ;
- observable ;
- multi-pays ;
- évolutive ;
- résistante aux pannes ;
- indépendante autant que possible d’un seul fournisseur ;
- capable de démarrer avec une architecture raisonnable ;
- capable d’évoluer vers une plateforme nationale puis régionale.

---

# 2. Principes fondamentaux

## 2.1 Aucun déploiement Production ne doit être manuel et non traçable

Tout déploiement doit passer par :

- une version ;
- un commit ;
- une pipeline ;
- des contrôles ;
- des tests ;
- une approbation ;
- un journal ;
- un mécanisme de rollback.

---

## 2.2 Aucun secret ne doit être stocké dans le code

Il est interdit de stocker dans Git :

- mots de passe ;
- clés API ;
- clés privées ;
- certificats privés ;
- tokens ;
- secrets JWT ;
- identifiants bancaires ;
- identifiants Mobile Money ;
- identifiants de Production ;
- clés de chiffrement ;
- chaînes de connexion sensibles.

---

## 2.3 Les environnements doivent être strictement séparés

Les environnements Développement, Démo, Recette, Préproduction et Production doivent être séparés au niveau :

- des bases ;
- des secrets ;
- des comptes cloud ;
- des réseaux ;
- des certificats ;
- des identités ;
- des partenaires ;
- des données ;
- des journaux ;
- des accès ;
- des budgets.

---

## 2.4 L’infrastructure doit être décrite comme du code

Les ressources doivent être créées et modifiées au moyen de configurations versionnées.

Exemples :

- réseau ;
- bases ;
- stockage ;
- secrets ;
- clusters ;
- règles ;
- files ;
- DNS ;
- certificats ;
- politiques ;
- alertes.

---

## 2.5 Production doit rester déployable sans dépendre d’un poste personnel

Le déploiement ne doit pas dépendre :

- du MacBook d’un développeur ;
- d’un fichier local ;
- d’un mot de passe personnel ;
- d’un script non versionné ;
- d’une action manuelle non documentée ;
- d’un compte partagé.

---

## 2.6 Chaque changement doit être réversible

Avant chaque mise en Production, le système doit disposer :

- d’une version précédente ;
- d’une stratégie de rollback ;
- d’une sauvegarde si nécessaire ;
- d’une migration compatible ;
- d’un plan de reprise ;
- d’une personne responsable ;
- de critères d’arrêt.

---

# 3. Périmètre technique

L’infrastructure couvre :

- frontend web ;
- applications mobiles ;
- backend ;
- API Gateway ;
- services d’authentification ;
- ledger ;
- paiements ;
- cartes ;
- KYC et KYB ;
- fraude ;
- support ;
- Finance ;
- Data ;
- Jini ;
- notifications ;
- intégrations ;
- bases PostgreSQL ;
- Redis ;
- Message Queue ;
- Event Bus ;
- stockage objet ;
- sauvegardes ;
- monitoring ;
- logs ;
- sécurité ;
- DNS ;
- CDN ;
- WAF ;
- VPN ;
- bastion ;
- CI/CD ;
- registres de paquets ;
- registres d’images ;
- gestion des appareils ;
- TPE ;
- DAB.

---

# 4. Environnements officiels

Les environnements recommandés sont :

```text
LOCAL
DEVELOPMENT
DEMO
TEST
RECETTE
PREPRODUCTION
PRODUCTION
DISASTER_RECOVERY
```

---

# 5. Environnement local

L’environnement local sert à :

- développer ;
- tester rapidement ;
- exécuter des services isolés ;
- utiliser des données fictives ;
- lancer des émulateurs ;
- vérifier les migrations ;
- reproduire une erreur ;
- exécuter les tests unitaires.

Il ne doit jamais contenir :

- secrets de Production ;
- base de Production ;
- données clients réelles non autorisées ;
- certificats réels ;
- clés partenaires actives.

---

# 6. Environnement Développement

Il permet :

- l’intégration continue ;
- le test des branches ;
- le test des API ;
- le test des migrations ;
- le test des services ;
- le test des webhooks ;
- le test des composants.

Les déploiements peuvent y être automatiques après validation technique.

---

# 7. Environnement Démo

Il est utilisé pour :

- présentations ;
- partenaires ;
- investisseurs ;
- institutions ;
- démonstrations commerciales ;
- tests d’expérience utilisateur.

Il doit utiliser :

- comptes fictifs ;
- cartes fictives ;
- agents fictifs ;
- commerçants fictifs ;
- transactions simulées ;
- partenaires simulés ;
- données clairement marquées Démo.

---

# 8. Environnement Test

Il est destiné aux :

- tests automatisés ;
- tests d’intégration ;
- tests de charge ;
- tests de sécurité ;
- tests de non-régression ;
- tests de contrats ;
- tests des connecteurs.

Il peut être recréé automatiquement.

---

# 9. Environnement Recette

La Recette permet aux équipes métier de valider :

- les parcours ;
- les règles ;
- les frais ;
- les commissions ;
- les permissions ;
- les rapports ;
- les notifications ;
- les documents ;
- les interfaces ;
- les cas limites.

---

# 10. Préproduction

La Préproduction doit reproduire au maximum la Production :

- architecture ;
- versions ;
- réseau ;
- sécurité ;
- bases ;
- files ;
- monitoring ;
- scaling ;
- configurations.

Elle utilise néanmoins :

- secrets distincts ;
- données fictives ou anonymisées ;
- partenaires de test ;
- endpoints non Production.

---

# 11. Production

La Production héberge les services réels.

Elle doit appliquer :

- contrôle d’accès renforcé ;
- MFA ;
- journaux immuables ;
- changements approuvés ;
- sauvegardes ;
- haute disponibilité ;
- surveillance continue ;
- rollback ;
- séparation des rôles ;
- limites de coûts ;
- politiques de sécurité ;
- procédures d’incident.

---

# 12. Environnement de reprise après sinistre

L’environnement Disaster Recovery doit pouvoir restaurer :

- API critiques ;
- ledger ;
- bases ;
- authentification ;
- paiements ;
- notifications ;
- connecteurs ;
- consoles essentielles.

Il doit être testé régulièrement.

---

# 13. Comptes cloud

Les comptes ou projets cloud doivent être séparés au minimum par :

- Production ;
- non-Production ;
- sécurité ;
- audit ;
- sauvegarde ;
- Data si nécessaire ;
- reprise après sinistre.

---

# 14. Multi-cloud et portabilité

Mansa doit éviter les dépendances irréversibles.

L’architecture doit favoriser :

- conteneurs standards ;
- PostgreSQL ;
- interfaces ouvertes ;
- stockage exportable ;
- infrastructure as code ;
- secrets portables ;
- sauvegardes indépendantes ;
- formats standards ;
- connecteurs remplaçables.

---

# 15. Choix d’hébergement

Les composants peuvent être hébergés sur :

- cloud public ;
- cloud privé ;
- datacenter partenaire ;
- infrastructure hybride ;
- région locale autorisée ;
- région de secours.

Le choix doit dépendre :

- du pays ;
- de la réglementation ;
- de la latence ;
- du coût ;
- de la résilience ;
- de la sécurité ;
- des partenaires ;
- de la souveraineté des données.

---

# 16. Architecture réseau

L’infrastructure doit distinguer :

- zone publique ;
- zone applicative ;
- zone services internes ;
- zone bases de données ;
- zone sécurité ;
- zone administration ;
- zone partenaires ;
- zone sauvegardes ;
- zone monitoring.

---

# 17. Sous-réseaux

Exemples :

```text
public-subnet
application-subnet
internal-services-subnet
database-subnet
security-subnet
management-subnet
partner-subnet
backup-subnet
```

---

# 18. Accès public

Ne doivent être publiquement accessibles que :

- API Gateway ;
- CDN ;
- site officiel ;
- pages publiques ;
- endpoints webhooks autorisés ;
- portails protégés via point d’entrée sécurisé.

Les bases et services internes ne doivent pas être publics.

---

# 19. Pare-feu

Les règles doivent être :

- minimales ;
- documentées ;
- versionnées ;
- limitées par port ;
- limitées par source ;
- limitées par destination ;
- auditées ;
- révisées ;
- désactivées lorsqu’elles ne sont plus utiles.

---

# 20. WAF

Le Web Application Firewall doit protéger contre :

- injections ;
- bots ;
- scans ;
- attaques courantes ;
- surcharge ;
- IP malveillantes ;
- requêtes anormales ;
- contournements ;
- payloads excessifs.

---

# 21. Protection DDoS

Le système doit prévoir :

- filtrage ;
- rate limiting ;
- CDN ;
- protection réseau ;
- blocage géographique configurable ;
- quotas ;
- détection d’anomalie ;
- capacité de montée en charge ;
- procédures d’urgence.

---

# 22. DNS

La gestion DNS doit couvrir :

- domaines publics ;
- sous-domaines ;
- environnements ;
- API ;
- portails ;
- webhooks ;
- statut ;
- documentation ;
- partenaires ;
- bascule ;
- validation de propriété.

---

# 23. Certificats TLS

Les certificats doivent être :

- émis automatiquement lorsque possible ;
- renouvelés automatiquement ;
- surveillés ;
- séparés par environnement ;
- stockés de manière sécurisée ;
- révoqués en cas d’incident ;
- journalisés.

---

# 24. mTLS

Le mTLS peut être obligatoire pour :

- banques ;
- réseaux cartes ;
- partenaires critiques ;
- services internes sensibles ;
- accès administratifs ;
- webhooks hautement sensibles.

---

# 25. VPN

Les accès internes peuvent utiliser :

- VPN d’entreprise ;
- tunnel partenaire ;
- réseau privé ;
- accès Zero Trust ;
- connexion dédiée ;
- bastion.

---

# 26. Bastion

Le bastion doit servir aux accès administratifs exceptionnels.

Il doit imposer :

- MFA ;
- session enregistrée ;
- durée limitée ;
- justification ;
- IP contrôlée ;
- droits minimaux ;
- audit ;
- révocation automatique.

---

# 27. Identités techniques

Chaque service doit disposer de sa propre identité.

Il est interdit d’utiliser :

- un compte partagé ;
- un compte administrateur global ;
- une clé commune à tous les services ;
- une identité personnelle pour la Production.

---

# 28. Gestion des accès

Les accès doivent suivre :

- principe du moindre privilège ;
- séparation des rôles ;
- approbation ;
- durée limitée ;
- revue périodique ;
- suppression automatique ;
- audit.

---

# 29. Accès d’urgence

Un accès d’urgence peut être prévu pour les incidents critiques.

Il doit exiger :

- motif ;
- approbation ;
- MFA renforcé ;
- durée courte ;
- journalisation ;
- revue après incident ;
- révocation immédiate après usage.

---

# 30. Infrastructure as Code

Les outils peuvent gérer :

- réseau ;
- stockage ;
- bases ;
- clusters ;
- secrets ;
- politiques ;
- rôles ;
- files ;
- alertes ;
- DNS ;
- CDN ;
- sauvegardes.

Chaque modification doit être :

- versionnée ;
- testée ;
- revue ;
- approuvée ;
- déployée par pipeline.

---

# 31. Dépôts Git

Les dépôts peuvent être organisés en :

- monorepo ;
- multi-repo ;
- dépôt infrastructure ;
- dépôt documentation ;
- dépôt applications ;
- dépôt backend ;
- dépôt design system ;
- dépôt Data ;
- dépôt modèles IA.

---

# 32. Branches

Stratégie recommandée :

```text
main
develop
feature/*
fix/*
release/*
hotfix/*
```

La stratégie exacte reste configurable.

---

# 33. Protection de la branche principale

La branche principale doit exiger :

- pull request ;
- tests réussis ;
- revue ;
- absence de conflits ;
- analyse de sécurité ;
- approbation ;
- interdiction de push direct ;
- signature lorsque prévue.

---

# 34. Commits

Les commits doivent être :

- traçables ;
- compréhensibles ;
- liés à une tâche ;
- limités en portée ;
- exempts de secret ;
- signés si requis.

---

# 35. Pull Requests

Chaque Pull Request doit contenir :

- objectif ;
- changements ;
- risques ;
- tests ;
- migrations ;
- captures éventuelles ;
- rollback ;
- dépendances ;
- impact sécurité ;
- impact données ;
- approbateurs.

---

# 36. Revue de code

La revue doit vérifier :

- logique ;
- sécurité ;
- qualité ;
- performance ;
- permissions ;
- erreurs ;
- logs ;
- tests ;
- compatibilité ;
- documentation ;
- migrations ;
- accessibilité lorsque applicable.

---

# 37. CI — Intégration continue

La CI doit exécuter automatiquement :

- installation ;
- formatage ;
- lint ;
- compilation ;
- vérification TypeScript ;
- tests unitaires ;
- tests d’intégration ;
- tests de contrat ;
- analyse de dépendances ;
- scan de secrets ;
- scan de code ;
- génération Prisma ;
- validation Prisma ;
- construction ;
- rapport.

---

# 38. Pipeline backend

Exemple :

```text
Checkout
→ installation
→ génération Prisma
→ validation du schéma
→ lint
→ compilation
→ tests unitaires
→ tests d’intégration
→ scan sécurité
→ build
→ image
→ publication
```

---

# 39. Pipeline web

Exemple :

```text
Checkout
→ installation
→ lint
→ TypeScript
→ tests composants
→ tests accessibilité
→ build Next.js
→ scan
→ publication
```

---

# 40. Pipeline mobile

Exemple :

```text
Checkout
→ installation
→ lint
→ TypeScript
→ tests
→ build Android
→ build iOS
→ signature
→ distribution interne
→ tests appareils
```

---

# 41. Pipeline TPE

Le pipeline TPE doit gérer :

- Kotlin ;
- dépendances ;
- signature ;
- version ;
- compatibilité terminal ;
- mode kiosque ;
- périphériques ;
- impression ;
- NFC ;
- tests ;
- distribution contrôlée.

---

# 42. Pipeline DAB

Il doit gérer :

- logiciel applicatif ;
- configuration ;
- drivers ;
- périphériques ;
- cassettes ;
- clavier sécurisé ;
- lecteur de carte ;
- impression ;
- chiffrement ;
- signature ;
- rollback ;
- déploiement progressif.

---

# 43. CD — Déploiement continu

Le CD doit permettre :

- déploiement automatique en Développement ;
- déploiement contrôlé en Recette ;
- déploiement approuvé en Préproduction ;
- déploiement protégé en Production ;
- rollback ;
- suivi ;
- comparaison des versions.

---

# 44. Artefacts

Les artefacts peuvent inclure :

- images conteneurs ;
- packages ;
- APK ;
- AAB ;
- builds iOS ;
- bundles web ;
- migrations ;
- fichiers de configuration ;
- SDK ;
- documentation ;
- signatures.

---

# 45. Registre d’images

Chaque image doit avoir :

- nom ;
- version ;
- hash ;
- date ;
- auteur ;
- scan ;
- environnement ;
- statut ;
- provenance ;
- signature.

---

# 46. Images conteneurs

Les images doivent être :

- minimales ;
- non root ;
- scannées ;
- versionnées ;
- signées ;
- reproductibles ;
- sans secret ;
- mises à jour ;
- protégées contre les modifications.

---

# 47. Conteneurs

Les services doivent être conçus pour :

- démarrage rapide ;
- arrêt propre ;
- health checks ;
- logs standards ;
- configuration externe ;
- absence d’état local critique ;
- scaling ;
- rollback ;
- limites CPU et mémoire.

---

# 48. Orchestrateur

L’orchestrateur doit gérer :

- déploiement ;
- scaling ;
- redémarrage ;
- réseau ;
- secrets ;
- configuration ;
- health checks ;
- répartition de charge ;
- rolling update ;
- rollback ;
- isolation.

---

# 49. Health checks

Chaque service doit exposer :

- liveness ;
- readiness ;
- startup ;
- dépendances ;
- version ;
- état dégradé.

Les health checks ne doivent pas exposer de secrets.

---

# 50. Déploiement Rolling

Le rolling deployment remplace progressivement les instances.

Il doit :

- éviter l’interruption ;
- contrôler la santé ;
- limiter le nombre d’instances indisponibles ;
- arrêter automatiquement en cas d’erreur ;
- permettre le rollback.

---

# 51. Déploiement Blue/Green

Deux environnements sont maintenus :

```text
Blue = version active
Green = nouvelle version
```

Après validation, le trafic est basculé.

Cette méthode est recommandée pour les services critiques.

---

# 52. Déploiement Canary

Le canary permet d’envoyer la nouvelle version à :

- l’équipe interne ;
- un faible pourcentage ;
- un pays pilote ;
- une application ;
- un segment ;
- un partenaire ;
- une région.

La proportion peut être augmentée progressivement.

---

# 53. Feature flags

Les fonctionnalités doivent pouvoir être activées selon :

- environnement ;
- pays ;
- utilisateur ;
- rôle ;
- organisation ;
- appareil ;
- version ;
- pourcentage ;
- partenaire ;
- produit.

---

# 54. Règles des feature flags

Un flag doit posséder :

- nom ;
- description ;
- propriétaire ;
- date ;
- environnement ;
- périmètre ;
- statut ;
- date d’expiration ;
- rollback ;
- historique.

---

# 55. Flags temporaires

Les flags temporaires doivent être supprimés après :

- généralisation ;
- abandon ;
- remplacement ;
- expiration ;
- migration.

Le système doit détecter les flags anciens.

---

# 56. Configuration applicative

La configuration doit être séparée du code.

Exemples :

- URLs ;
- limites ;
- délais ;
- fournisseurs ;
- pays ;
- devises ;
- paramètres ;
- feature flags ;
- niveaux de logs ;
- options d’intégration.

---

# 57. Secrets

Les secrets doivent être stockés dans un coffre dédié.

Exemples :

- clés API ;
- mots de passe ;
- certificats ;
- secrets JWT ;
- identifiants bases ;
- secrets webhooks ;
- clés de chiffrement ;
- comptes partenaires.

---

# 58. Rotation des secrets

Chaque secret doit posséder :

- propriétaire ;
- date de création ;
- date de rotation ;
- date d’expiration ;
- services utilisateurs ;
- environnement ;
- statut ;
- historique.

---

# 59. Rotation automatique

Elle doit être privilégiée pour :

- mots de passe techniques ;
- certificats ;
- tokens ;
- clés d’accès ;
- secrets de bases ;
- identités de service.

---

# 60. Révocation

Un secret doit pouvoir être révoqué immédiatement en cas de :

- fuite ;
- départ d’un employé ;
- compromission ;
- changement de partenaire ;
- fin de contrat ;
- erreur de configuration ;
- incident.

---

# 61. Migrations de base de données

Les migrations doivent être :

- versionnées ;
- testées ;
- réversibles lorsque possible ;
- compatibles avec les versions en cours ;
- séparées des changements destructifs ;
- observables ;
- approuvées.

---

# 62. Migrations compatibles

Pour éviter les pannes :

1. ajouter le nouveau champ ;
2. déployer le code compatible ;
3. migrer les données ;
4. activer le nouveau comportement ;
5. supprimer l’ancien champ ultérieurement.

---

# 63. Migrations destructives

Une migration destructive doit exiger :

- étude d’impact ;
- sauvegarde ;
- approbation ;
- période de maintenance éventuelle ;
- test de restauration ;
- rollback ;
- audit.

---

# 64. Bases PostgreSQL

Les bases doivent être configurées avec :

- réplication ;
- sauvegardes ;
- chiffrement ;
- contrôle d’accès ;
- monitoring ;
- journalisation ;
- maintenance ;
- index ;
- pooling ;
- limites ;
- reprise.

---

# 65. Séparation des bases

Les domaines critiques peuvent avoir des bases séparées :

- identité ;
- ledger ;
- paiements ;
- cartes ;
- KYC ;
- notifications ;
- support ;
- fraude ;
- Finance ;
- Data ;
- Jini.

Le choix dépend du niveau de maturité et de charge.

---

# 66. Pool de connexions

Le système doit limiter :

- connexions ;
- connexions inactives ;
- saturation ;
- timeout ;
- contention.

Les limites doivent être ajustées par environnement.

---

# 67. Réplication

La réplication peut inclure :

- primaire ;
- réplica en lecture ;
- réplica de secours ;
- réplica régional ;
- réplica de sauvegarde.

---

# 68. Cache Redis

Redis peut être utilisé pour :

- sessions ;
- cache ;
- rate limiting ;
- locks ;
- files temporaires ;
- données de courte durée ;
- idempotence ;
- tokens temporaires.

Redis ne doit pas être la seule source de vérité financière.

---

# 69. Message Queue

La file de messages doit gérer :

- ordre si nécessaire ;
- retry ;
- dead-letter ;
- déduplication ;
- priorité ;
- délai ;
- expiration ;
- monitoring ;
- backpressure.

---

# 70. Event Bus

Le bus d’événements permet la communication asynchrone entre :

- paiements ;
- notifications ;
- fraude ;
- Data ;
- Finance ;
- support ;
- cartes ;
- agents ;
- commerçants ;
- partenaires.

---

# 71. Stockage objet

Il peut contenir :

- documents ;
- reçus ;
- rapports ;
- exports ;
- sauvegardes ;
- justificatifs ;
- images ;
- fichiers partenaires ;
- archives ;
- artefacts.

---

# 72. Sécurité du stockage objet

Le stockage doit appliquer :

- chiffrement ;
- permissions ;
- expiration ;
- versionnement ;
- antivirus ;
- liens temporaires ;
- audit ;
- classification ;
- rétention ;
- suppression contrôlée.

---

# 73. CDN

Le CDN peut distribuer :

- site public ;
- images ;
- assets ;
- scripts ;
- styles ;
- documents publics ;
- contenus statiques.

Les contenus sensibles ne doivent pas être mis en cache publiquement.

---

# 74. Scalabilité

Le système doit pouvoir monter en charge selon :

- CPU ;
- mémoire ;
- nombre de requêtes ;
- longueur des files ;
- nombre de transactions ;
- latence ;
- pays ;
- période ;
- campagne ;
- événement national.

---

# 75. Autoscaling

Le scaling peut utiliser :

- seuil CPU ;
- seuil mémoire ;
- requêtes ;
- files ;
- événements ;
- planning ;
- prédiction ;
- seuil métier.

---

# 76. Limites de ressources

Chaque service doit définir :

- CPU minimum ;
- CPU maximum ;
- mémoire minimale ;
- mémoire maximale ;
- disque ;
- connexions ;
- threads ;
- timeouts.

---

# 77. Haute disponibilité

Les composants critiques doivent éviter le point de panne unique.

Exemples :

- plusieurs instances ;
- plusieurs zones ;
- load balancer ;
- réplication ;
- files persistantes ;
- DNS de secours ;
- bascule ;
- sauvegarde ;
- monitoring.

---

# 78. Zones de disponibilité

Lorsque possible, les services critiques doivent être répartis entre plusieurs zones.

Le système doit continuer à fonctionner si une zone devient indisponible.

---

# 79. Régions

Le choix des régions doit tenir compte :

- de la réglementation ;
- de la latence ;
- du coût ;
- de la résilience ;
- de la localisation des données ;
- des partenaires ;
- du plan de secours.

---

# 80. Mode dégradé

En cas de panne partielle :

- les paiements critiques restent prioritaires ;
- les campagnes peuvent être suspendues ;
- les rapports peuvent être retardés ;
- Jini peut passer en mode limité ;
- les notifications peuvent être mises en file ;
- les services non essentiels peuvent être réduits ;
- les utilisateurs doivent être informés.

---

# 81. Dépendances externes

Chaque dépendance doit avoir :

- propriétaire ;
- SLA ;
- timeout ;
- retry ;
- circuit breaker ;
- fallback ;
- monitoring ;
- contact ;
- statut ;
- plan d’incident.

---

# 82. Gestion des paquets

Les dépendances doivent être :

- verrouillées ;
- scannées ;
- mises à jour ;
- inventoriées ;
- approuvées ;
- remplacées si vulnérables ;
- limitées au besoin.

---

# 83. SBOM

Chaque build critique doit produire une nomenclature logicielle contenant :

- packages ;
- versions ;
- licences ;
- sources ;
- hashes ;
- vulnérabilités ;
- dépendances transitives.

---

# 84. Scan de vulnérabilités

Le pipeline doit scanner :

- code ;
- dépendances ;
- images ;
- secrets ;
- IaC ;
- conteneurs ;
- configurations ;
- packages mobiles ;
- bibliothèques natives.

---

# 85. Vulnérabilités critiques

Une vulnérabilité critique peut :

- bloquer la pipeline ;
- empêcher le déploiement ;
- déclencher une alerte ;
- créer un incident ;
- imposer un correctif ;
- nécessiter un rollback.

---

# 86. Correctifs de sécurité

Les correctifs doivent être classés selon :

- criticité ;
- exploitabilité ;
- exposition ;
- service ;
- environnement ;
- données touchées ;
- délai de correction.

---

# 87. Signature des artefacts

Les artefacts peuvent être signés pour garantir :

- origine ;
- intégrité ;
- version ;
- absence de modification ;
- autorisation de déploiement.

---

# 88. Provenance des builds

Le système doit pouvoir retrouver :

```text
Commit
→ pipeline
→ dépendances
→ build
→ image
→ déploiement
→ environnement
```

---

# 89. Mises à jour backend

Une mise à jour backend doit préciser :

- version ;
- services ;
- migrations ;
- compatibilité ;
- impact ;
- stratégie ;
- tests ;
- rollback ;
- approbation.

---

# 90. Mises à jour web

Le web doit permettre :

- déploiement progressif ;
- purge de cache ;
- rollback ;
- feature flags ;
- compatibilité API ;
- surveillance d’erreurs ;
- vérification accessibilité.

---

# 91. Mises à jour mobiles

Les applications mobiles doivent gérer :

- version minimale ;
- version recommandée ;
- mise à jour obligatoire ;
- mise à jour facultative ;
- compatibilité backend ;
- déploiement progressif ;
- stores ;
- distribution interne ;
- rollback fonctionnel via flags.

---

# 92. Mises à jour TPE

Le système doit permettre :

- mise à jour distante ;
- signature ;
- téléchargement sécurisé ;
- installation différée ;
- plage horaire ;
- redémarrage ;
- version minimale ;
- rollback ;
- suivi par terminal ;
- campagne pilote.

---

# 93. Mises à jour DAB

Les mises à jour DAB doivent être :

- signées ;
- chiffrées ;
- testées ;
- planifiées ;
- compatibles matériel ;
- déployées progressivement ;
- vérifiables ;
- réversibles ;
- supervisées.

---

# 94. Compatibilité API

Le backend doit gérer une période de compatibilité avec :

- anciennes applications mobiles ;
- anciens TPE ;
- anciens DAB ;
- partenaires non encore migrés ;
- anciennes versions SDK.

---

# 95. Politique de fin de support

Une version doit posséder :

- date de publication ;
- date de dépréciation ;
- date de fin de support ;
- version minimale ;
- communication ;
- migration ;
- blocage éventuel.

---

# 96. Rollback

Le rollback peut concerner :

- application ;
- backend ;
- base ;
- configuration ;
- feature flag ;
- image ;
- modèle IA ;
- connecteur ;
- règle ;
- certificat.

---

# 97. Conditions de rollback automatique

Exemples :

- hausse d’erreurs ;
- chute du taux de paiement ;
- latence excessive ;
- crash ;
- migration échouée ;
- problème de sécurité ;
- incompatibilité ;
- échec des health checks ;
- perte de données potentielle.

---

# 98. Rollback manuel

Le rollback manuel doit exiger :

- justification ;
- version cible ;
- responsable ;
- approbation selon criticité ;
- journal ;
- communication ;
- vérification après retour.

---

# 99. Sauvegardes

Les sauvegardes doivent couvrir :

- bases ;
- stockage ;
- configurations ;
- secrets selon méthode autorisée ;
- certificats ;
- journaux critiques ;
- modèles ;
- documentation ;
- infrastructure ;
- données partenaires.

---

# 100. Types de sauvegarde

- complète ;
- incrémentale ;
- différentielle ;
- snapshot ;
- journal de transaction ;
- sauvegarde hors ligne ;
- sauvegarde immuable ;
- sauvegarde régionale.

---

# 101. Politique de sauvegarde

Chaque ressource doit préciser :

- fréquence ;
- durée ;
- chiffrement ;
- localisation ;
- propriétaire ;
- test de restauration ;
- RPO ;
- RTO ;
- suppression ;
- audit.

---

# 102. Test de restauration

Une sauvegarde n’est considérée valide que si elle peut être restaurée.

Les restaurations doivent être testées :

- automatiquement ;
- périodiquement ;
- avant migration majeure ;
- après changement d’architecture ;
- après incident.

---

# 103. RPO

Le Recovery Point Objective définit la perte maximale de données acceptable.

Il doit être défini par service.

Exemple :

- ledger : très faible ;
- paiements : très faible ;
- notifications : plus tolérant ;
- analytics : tolérance configurable.

---

# 104. RTO

Le Recovery Time Objective définit le délai maximal de restauration.

Il doit être défini selon la criticité.

---

# 105. Gestion des coûts

L’infrastructure doit suivre :

- calcul ;
- stockage ;
- réseau ;
- bases ;
- sauvegardes ;
- logs ;
- monitoring ;
- CDN ;
- IA ;
- environnements ;
- pays ;
- équipes ;
- services ;
- partenaires.

---

# 106. Budgets

Des budgets peuvent être définis par :

- compte cloud ;
- environnement ;
- équipe ;
- pays ;
- service ;
- produit ;
- projet ;
- mois ;
- année.

---

# 107. Alertes de coût

Le système doit alerter en cas de :

- hausse brutale ;
- ressource inutilisée ;
- environnement oublié ;
- logs excessifs ;
- stockage croissant ;
- transfert réseau anormal ;
- autoscaling inhabituel ;
- budget dépassé ;
- service mal configuré.

---

# 108. Optimisation des coûts

Mesures possibles :

- arrêt des environnements temporaires ;
- ajustement des ressources ;
- archivage ;
- politiques de rétention ;
- compression ;
- cache ;
- scheduling ;
- réservation ;
- mutualisation contrôlée ;
- scaling adapté.

---

# 109. FinOps

Chaque ressource doit pouvoir être rattachée à :

- équipe ;
- pays ;
- produit ;
- environnement ;
- propriétaire ;
- centre de coûts ;
- projet.

---

# 110. Observabilité technique

L’infrastructure doit produire :

- logs ;
- métriques ;
- traces ;
- événements ;
- health checks ;
- alertes ;
- dashboards ;
- rapports de disponibilité.

---

# 111. Logs

Les logs doivent être :

- structurés ;
- horodatés ;
- corrélés ;
- centralisés ;
- filtrés ;
- protégés ;
- limités ;
- soumis à rétention ;
- exempts de secrets.

---

# 112. Données interdites dans les logs

Ne pas enregistrer :

- PIN ;
- OTP ;
- CVV ;
- numéro complet de carte ;
- mot de passe ;
- clé privée ;
- secret API ;
- token complet ;
- biométrie ;
- payload financier complet non nécessaire ;
- document complet.

---

# 113. Métriques

Exemples :

- CPU ;
- mémoire ;
- disque ;
- requêtes ;
- latence ;
- erreurs ;
- files ;
- connexions ;
- transactions ;
- disponibilité ;
- saturation ;
- coûts.

---

# 114. Traces distribuées

Chaque requête doit pouvoir être suivie à travers :

```text
Application
→ API Gateway
→ service
→ base
→ file
→ partenaire
→ réponse
```

---

# 115. Identifiants de corrélation

Les services doivent propager :

```http
X-Request-Id
X-Correlation-Id
Trace-Id
```

---

# 116. Alertes

Les alertes doivent être classées selon :

- information ;
- avertissement ;
- haute ;
- urgente ;
- critique.

---

# 117. Astreinte

Les incidents critiques doivent pouvoir déclencher :

- notification ;
- appel ;
- SMS ;
- escalade ;
- ouverture automatique d’incident ;
- affectation ;
- suivi ;
- communication.

---

# 118. Maintenance

Les maintenances doivent être :

- planifiées ;
- approuvées ;
- communiquées ;
- limitées ;
- testées ;
- réversibles ;
- suivies ;
- clôturées.

---

# 119. Fenêtres de maintenance

Elles peuvent dépendre :

- du pays ;
- du service ;
- du partenaire ;
- du niveau de trafic ;
- du type de changement ;
- de l’urgence ;
- des obligations.

---

# 120. Jobs planifiés

Les tâches planifiées doivent gérer :

- horaire ;
- fuseau ;
- idempotence ;
- verrou ;
- retry ;
- timeout ;
- monitoring ;
- historique ;
- reprise ;
- échec.

---

# 121. Batchs financiers

Les batchs financiers doivent être protégés par :

- verrouillage ;
- contrôles ;
- références ;
- journalisation ;
- validation ;
- reprise ;
- rapprochement ;
- alertes ;
- double exécution interdite.

---

# 122. Administration DevOps

L’administration centrale doit pouvoir gérer :

- environnements ;
- versions ;
- pipelines ;
- artefacts ;
- déploiements ;
- secrets ;
- certificats ;
- configurations ;
- feature flags ;
- clusters ;
- bases ;
- files ;
- stockage ;
- backups ;
- coûts ;
- accès ;
- incidents ;
- audits.

---

# 123. Rôles

Exemples :

```text
PLATFORM_ADMIN
CLOUD_ADMIN
DEVOPS_ENGINEER
SITE_RELIABILITY_ENGINEER
DATABASE_ADMIN
NETWORK_ADMIN
SECURITY_ENGINEER
RELEASE_MANAGER
MOBILE_RELEASE_MANAGER
TERMINAL_RELEASE_MANAGER
BACKUP_ADMIN
FINOPS_ANALYST
AUDITOR
VIEWER
```

---

# 124. Permissions

Exemples :

```text
infrastructure.environment.read
infrastructure.environment.manage
infrastructure.pipeline.read
infrastructure.pipeline.manage
infrastructure.deployment.create
infrastructure.deployment.approve
infrastructure.rollback.execute
infrastructure.secret.read_metadata
infrastructure.secret.rotate
infrastructure.certificate.manage
infrastructure.database.manage
infrastructure.backup.manage
infrastructure.restore.execute
infrastructure.feature_flag.manage
infrastructure.cost.read
infrastructure.audit.read
```

---

# 125. Approbations

Peuvent exiger une approbation :

- déploiement Production ;
- changement réseau ;
- migration destructive ;
- rotation critique ;
- modification d’un secret ;
- nouveau certificat ;
- changement de base ;
- restauration ;
- rollback ;
- modification d’une règle firewall ;
- activation d’un nouveau pays ;
- suppression de ressource.

---

# 126. Double validation

Peut être exigée pour :

- accès Production ;
- suppression de base ;
- migration ledger ;
- changement de clé ;
- modification réseau critique ;
- restauration Production ;
- déploiement d’urgence ;
- changement d’un partenaire ;
- désactivation de sauvegarde ;
- arrêt d’un service critique.

---

# 127. Séparation des rôles

Exemple :

```text
Développeur prépare
→ CI valide
→ Reviewer approuve
→ Release Manager autorise
→ Pipeline déploie
```

Le développeur ne doit pas pouvoir contourner seul le workflow Production.

---

# 128. Déploiement d’urgence

Un hotfix doit préciser :

- incident ;
- impact ;
- correctif ;
- tests minimaux ;
- approbateur ;
- rollback ;
- surveillance ;
- compte rendu après déploiement.

---

# 129. Freeze de déploiement

Un gel peut être activé pendant :

- clôture financière ;
- versement massif ;
- lancement national ;
- période électorale sensible si applicable ;
- fête majeure ;
- incident ;
- audit ;
- migration ;
- événement à forte charge.

---

# 130. Sandbox technique

La Sandbox technique doit permettre :

- test API ;
- test webhooks ;
- données fictives ;
- simulations ;
- erreurs forcées ;
- latence simulée ;
- partenaires fictifs ;
- scénarios de panne ;
- tests de charge limités.

---

# 131. Environnements éphémères

Une Pull Request peut créer temporairement :

- frontend ;
- API ;
- base ;
- données de test ;
- URL de prévisualisation ;
- logs ;
- tests.

L’environnement doit être détruit automatiquement après usage.

---

# 132. Tests avant déploiement

Avant Production, il faut au minimum :

- build réussi ;
- tests unitaires ;
- tests d’intégration ;
- tests de contrat ;
- scan sécurité ;
- tests migration ;
- tests smoke ;
- validation Recette ;
- validation Préproduction ;
- plan de rollback.

---

# 133. Smoke tests

Après déploiement, le système doit vérifier :

- connexion ;
- authentification ;
- endpoint principal ;
- base ;
- file ;
- cache ;
- paiement simulé autorisé ;
- notification ;
- monitoring ;
- version.

---

# 134. Tests de charge

Ils doivent simuler :

- inscriptions ;
- paiements ;
- retraits ;
- dépôts ;
- connexions ;
- webhooks ;
- versements massifs ;
- campagnes ;
- forte activité TPE ;
- forte activité DAB.

---

# 135. Tests de chaos

Le système peut tester :

- perte d’une instance ;
- perte d’une zone ;
- panne Redis ;
- panne partenaire ;
- latence banque ;
- file saturée ;
- disque plein ;
- certificat expiré ;
- DNS indisponible ;
- perte réseau.

---

# 136. Déploiement multi-pays

Chaque pays peut disposer de :

- configuration ;
- région ;
- secrets ;
- partenaires ;
- devise ;
- domaine ;
- données ;
- règles ;
- monitoring ;
- budgets ;
- calendrier ;
- feature flags.

---

# 137. Résidence des données

L’infrastructure doit permettre de définir où sont stockées :

- données clients ;
- données KYC ;
- données financières ;
- sauvegardes ;
- logs ;
- documents ;
- données analytiques.

---

# 138. Horodatage

Tous les systèmes doivent conserver :

- UTC ;
- heure locale ;
- fuseau ;
- date métier ;
- date comptable ;
- date de valeur.

---

# 139. Nommage des ressources

Les ressources doivent suivre une convention.

Exemple :

```text
mansa-{environment}-{country}-{domain}-{resource}
```

---

# 140. Tags

Chaque ressource doit porter :

- environnement ;
- pays ;
- équipe ;
- produit ;
- propriétaire ;
- centre de coûts ;
- sensibilité ;
- criticité ;
- date d’expiration éventuelle.

---

# 141. Documentation d’exploitation

Chaque service critique doit posséder :

- architecture ;
- dépendances ;
- procédures ;
- déploiement ;
- rollback ;
- sauvegarde ;
- restauration ;
- alertes ;
- contacts ;
- incidents connus ;
- runbooks.

---

# 142. Runbooks

Les runbooks doivent couvrir :

- service indisponible ;
- base saturée ;
- file bloquée ;
- partenaire en panne ;
- certificat expiré ;
- secret compromis ;
- rollback ;
- restauration ;
- attaque ;
- fuite ;
- perte de zone.

---

# 143. Modèles principaux

- CloudAccount
- CloudRegion
- InfrastructureEnvironment
- InfrastructureResource
- NetworkSegment
- FirewallRule
- DnsRecord
- TlsCertificate
- ServiceIdentity
- InfrastructureRole
- InfrastructurePermission
- SourceRepository
- BuildPipeline
- DeploymentPipeline
- BuildArtifact
- ContainerImage
- ServiceDeployment
- FeatureFlag
- ApplicationConfiguration
- SecretReference
- SecretRotation
- DatabaseInstance
- CacheInstance
- MessageQueue
- EventBus
- ObjectStorageBucket
- BackupPolicy
- BackupExecution
- RestoreExecution
- InfrastructureIncident
- MaintenanceWindow
- ScheduledJob
- InfrastructureBudget
- InfrastructureCost
- InfrastructureApproval
- InfrastructureAudit

---

# 144. Webhooks internes

Événements possibles :

```text
infrastructure.build.started
infrastructure.build.completed
infrastructure.build.failed
infrastructure.deployment.started
infrastructure.deployment.completed
infrastructure.deployment.failed
infrastructure.rollback.started
infrastructure.rollback.completed
infrastructure.secret.expiring
infrastructure.certificate.expiring
infrastructure.backup.failed
infrastructure.restore.completed
infrastructure.cost.warning
infrastructure.capacity.warning
infrastructure.security.alert
```

---

# 145. Analytics

Événements possibles :

```text
infra_dashboard_opened
infra_deployment_created
infra_deployment_approved
infra_deployment_completed
infra_rollback_executed
infra_secret_rotated
infra_certificate_renewed
infra_backup_started
infra_backup_completed
infra_restore_tested
infra_cost_alert_created
infra_access_denied
infra_security_alert_created
```

---

# 146. Données analytics interdites

Ne pas transmettre :

- secret ;
- clé privée ;
- mot de passe ;
- token ;
- contenu de certificat privé ;
- chaîne de connexion complète ;
- payload sensible ;
- données clients ;
- contenu de sauvegarde ;
- logs complets sensibles.

---

# 147. Tests

- tests des environnements ;
- tests de séparation ;
- tests réseau ;
- tests firewall ;
- tests DNS ;
- tests TLS ;
- tests mTLS ;
- tests VPN ;
- tests bastion ;
- tests IAM ;
- tests IaC ;
- tests Git ;
- tests CI ;
- tests CD ;
- tests d’artefacts ;
- tests de conteneurs ;
- tests d’orchestrateur ;
- tests health checks ;
- tests rolling ;
- tests blue/green ;
- tests canary ;
- tests feature flags ;
- tests de secrets ;
- tests de rotation ;
- tests de migrations ;
- tests PostgreSQL ;
- tests Redis ;
- tests Message Queue ;
- tests Event Bus ;
- tests stockage ;
- tests CDN ;
- tests autoscaling ;
- tests haute disponibilité ;
- tests multi-zones ;
- tests mode dégradé ;
- tests dépendances ;
- tests SBOM ;
- tests vulnérabilités ;
- tests signature ;
- tests mises à jour mobiles ;
- tests mises à jour TPE ;
- tests mises à jour DAB ;
- tests rollback ;
- tests sauvegardes ;
- tests restauration ;
- tests RPO ;
- tests RTO ;
- tests coûts ;
- tests logs ;
- tests métriques ;
- tests traces ;
- tests alertes ;
- tests astreinte ;
- tests jobs ;
- tests batchs ;
- tests hotfix ;
- tests freeze ;
- tests sandbox ;
- tests environnements éphémères ;
- tests smoke ;
- tests charge ;
- tests chaos ;
- tests multi-pays ;
- tests résidence des données ;
- tests audit ;
- tests performance.

---

# 148. Règles métier

1. Aucun secret n’est stocké dans le code.
2. Aucun accès Production n’utilise un compte partagé.
3. Les environnements sont séparés.
4. Les données Production ne sont pas copiées librement.
5. L’infrastructure est versionnée.
6. Les branches principales sont protégées.
7. Tout déploiement passe par une pipeline.
8. La CI doit réussir avant un déploiement.
9. Les artefacts sont versionnés.
10. Les images sont scannées.
11. Les services utilisent des identités propres.
12. Les configurations sont séparées du code.
13. Les secrets sont rotatifs.
14. Les migrations sont testées.
15. Les migrations destructives sont approuvées.
16. Les services critiques sont hautement disponibles.
17. Les déploiements Production sont réversibles.
18. Les mises à jour TPE et DAB sont signées.
19. Les sauvegardes sont chiffrées.
20. Les restaurations sont testées.
21. Les coûts sont suivis.
22. Les journaux ne contiennent pas de secrets.
23. Les accès critiques sont audités.
24. Le demandeur ne valide pas seul une action critique.
25. Les audits sont immuables.

---

# 149. Critères d’acceptation

L’Infrastructure Cloud, DevOps et Déploiement Mansa est validée lorsque :

- les environnements sont séparés ;
- l’environnement Démo utilise des données fictives ;
- la Préproduction reproduit la Production ;
- l’environnement de reprise est défini ;
- les comptes cloud sont séparés ;
- le réseau est segmenté ;
- les bases ne sont pas publiques ;
- le WAF est actif ;
- la protection DDoS est prévue ;
- les certificats sont renouvelables ;
- le mTLS est disponible ;
- les accès internes sont protégés ;
- le bastion est audité ;
- les identités techniques sont séparées ;
- l’IaC est versionnée ;
- les branches sont protégées ;
- les Pull Requests sont obligatoires ;
- la CI exécute lint, build et tests ;
- les scans de sécurité sont actifs ;
- les pipelines backend fonctionnent ;
- les pipelines web fonctionnent ;
- les pipelines mobiles fonctionnent ;
- les pipelines TPE fonctionnent ;
- les pipelines DAB fonctionnent ;
- le CD est contrôlé ;
- les artefacts sont versionnés ;
- les images sont signables ;
- les conteneurs utilisent des health checks ;
- les rolling updates fonctionnent ;
- le blue/green est disponible ;
- le canary est disponible ;
- les feature flags sont administrables ;
- les secrets sont centralisés ;
- la rotation fonctionne ;
- les migrations sont sécurisées ;
- PostgreSQL est sauvegardé ;
- Redis n’est pas utilisé comme source financière officielle ;
- les files possèdent une dead-letter queue ;
- le stockage objet est chiffré ;
- l’autoscaling est configurable ;
- les services critiques sont multi-instances ;
- le mode dégradé est défini ;
- les dépendances utilisent des timeouts et circuit breakers ;
- les dépendances sont scannées ;
- les SBOM sont générables ;
- les correctifs critiques bloquent les déploiements si nécessaire ;
- les builds sont traçables ;
- les mises à jour backend sont réversibles ;
- les mises à jour mobiles sont contrôlées ;
- les mises à jour TPE sont distantes et signées ;
- les mises à jour DAB sont progressives ;
- la compatibilité API est gérée ;
- les fins de support sont planifiées ;
- le rollback automatique est possible ;
- les sauvegardes sont planifiées ;
- les restaurations sont testées ;
- les RPO et RTO sont définis ;
- les coûts sont attribuables ;
- les budgets sont configurables ;
- les logs sont centralisés ;
- les métriques sont disponibles ;
- les traces distribuées fonctionnent ;
- les alertes sont hiérarchisées ;
- l’astreinte est prévue ;
- les maintenances sont planifiées ;
- les batchs sont idempotents ;
- les rôles et permissions sont définis ;
- les actions critiques nécessitent une approbation ;
- les hotfix sont traçables ;
- les gels de déploiement sont possibles ;
- la Sandbox technique fonctionne ;
- les environnements éphémères peuvent être créés ;
- les smoke tests sont automatiques ;
- les tests de charge sont possibles ;
- les tests de chaos sont prévus ;
- le multi-pays est supporté ;
- la résidence des données est configurable ;
- les runbooks sont disponibles ;
- les audits sont immuables ;
- les tests couvrent les parcours essentiels.
