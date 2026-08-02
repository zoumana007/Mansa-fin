# 26 — Infrastructure cloud, environnements, hébergement et déploiement de Mansa

## 1. Objet du document

Ce document définit l’architecture officielle d’infrastructure de Mansa.

Il couvre :

- l’hébergement ;
- les environnements ;
- les régions ;
- les réseaux ;
- les domaines ;
- les certificats ;
- les conteneurs ;
- les services applicatifs ;
- les bases de données ;
- les caches ;
- les files ;
- le stockage ;
- les sauvegardes ;
- les secrets ;
- les journaux ;
- le monitoring ;
- la haute disponibilité ;
- la reprise après incident ;
- la scalabilité ;
- les coûts ;
- la sécurité ;
- les déploiements ;
- les accès techniques ;
- les obligations multi-pays.

L’objectif est de fournir une infrastructure :

- sécurisée ;
- résiliente ;
- observable ;
- évolutive ;
- automatisée ;
- maîtrisable ;
- compatible avec une croissance progressive ;
- séparée entre les environnements ;
- adaptée aux contraintes financières et réglementaires.

---

# 2. Principes fondamentaux

## 2.1 Infrastructure as Code

Toute infrastructure durable doit être définie dans du code.

Cela concerne notamment :

- réseaux ;
- sous-réseaux ;
- bases de données ;
- clusters ;
- stockage ;
- files ;
- caches ;
- secrets ;
- rôles ;
- politiques ;
- alertes ;
- sauvegardes ;
- certificats ;
- DNS.

L’infrastructure ne doit pas dépendre uniquement de modifications manuelles dans une console cloud.

---

## 2.2 Environnements strictement séparés

Mansa doit séparer au minimum :

- local ;
- développement ;
- test ;
- Démo ;
- Recette ;
- Préproduction ;
- Production.

Chaque environnement doit disposer de :

- secrets distincts ;
- bases distinctes ;
- domaines distincts ;
- partenaires distincts ;
- journaux distincts ;
- alertes distinctes ;
- permissions distinctes ;
- données distinctes.

---

## 2.3 Production protégée

La production doit être plus protégée que les autres environnements.

Elle doit exiger :

- permissions renforcées ;
- MFA ;
- validation des changements ;
- journalisation ;
- approbation ;
- sauvegardes ;
- rollback ;
- monitoring ;
- accès limités ;
- procédures d’urgence.

---

## 2.4 Aucun secret dans GitHub

Les secrets ne doivent jamais être stockés dans :

- code source ;
- fichiers `.env` committés ;
- documentation publique ;
- logs ;
- tickets non sécurisés ;
- variables en clair dans des scripts.

---

## 2.5 Services remplaçables

Les composants d’infrastructure doivent être encapsulés pour éviter une dépendance excessive envers un fournisseur unique lorsque cela est raisonnable.

---

# 3. Structure des environnements

Exemple :

```text
local
development
test
demo
staging
preproduction
production
```

Chaque environnement doit avoir un identifiant stable.

---

# 4. Environnement local

Il doit permettre :

- développement ;
- tests ;
- base locale ;
- services simulés ;
- données fictives ;
- mocks partenaires ;
- exécution hors ligne limitée.

Il ne doit pas utiliser de secrets de production.

---

# 5. Développement

Utilisé pour :

- intégration continue ;
- validation technique ;
- tests manuels ;
- développement partagé ;
- vérification des migrations.

Les données doivent être fictives ou anonymisées.

---

# 6. Démo

Utilisé pour :

- démonstrations ;
- présentations ;
- investisseurs ;
- partenaires ;
- tests commerciaux ;
- prototypes visibles.

Il doit utiliser :

- transactions fictives ;
- cartes fictives ;
- faux utilisateurs ;
- faux commerces ;
- faux partenaires ;
- aucun argent réel.

---

# 7. Recette

Utilisée pour :

- validation produit ;
- validation métier ;
- tests utilisateurs ;
- tests partenaires ;
- tests de compatibilité ;
- tests de configuration.

---

# 8. Préproduction

La préproduction doit être proche de la production.

Elle doit permettre :

- tests de charge ;
- tests de migration ;
- tests de déploiement ;
- tests de rollback ;
- tests d’incident ;
- validation des certificats ;
- validation des intégrations.

---

# 9. Production

La production héberge les services réels.

Elle doit avoir :

- haute disponibilité ;
- sauvegardes ;
- monitoring 24/7 ;
- alertes ;
- journaux sécurisés ;
- réplication ;
- accès limités ;
- procédures d’incident ;
- capacité de rollback.

---

# 10. Choix du fournisseur cloud

Le fournisseur peut varier selon :

- pays ;
- disponibilité ;
- coûts ;
- conformité ;
- souveraineté ;
- résilience ;
- services managés ;
- support ;
- partenaires.

Mansa doit pouvoir documenter pour chaque fournisseur :

- région ;
- services utilisés ;
- dépendances ;
- limites ;
- plan de sortie ;
- localisation des données.

---

# 11. Régions

Les régions doivent être choisies selon :

- proximité utilisateurs ;
- latence ;
- disponibilité ;
- réglementation ;
- résilience ;
- localisation des données ;
- capacité de reprise.

---

# 12. Multi-régions

Une architecture multi-régions peut être utilisée pour :

- haute disponibilité ;
- reprise ;
- réduction de latence ;
- exigences réglementaires ;
- séparation pays.

Elle doit tenir compte :

- de la cohérence des données ;
- du ledger ;
- de la réplication ;
- des conflits ;
- des coûts ;
- des procédures de bascule.

---

# 13. Réseau

L’infrastructure doit utiliser :

- réseau privé ;
- sous-réseaux ;
- segmentation ;
- pare-feu ;
- règles minimales ;
- accès sortants contrôlés ;
- accès entrants limités.

---

# 14. Zones réseau

Exemples :

- zone publique ;
- zone applicative ;
- zone données ;
- zone administration ;
- zone partenaires ;
- zone observabilité.

---

# 15. Services publics

Seuls les composants nécessaires doivent être exposés publiquement.

Exemples :

- API Gateway ;
- sites web ;
- endpoints webhook ;
- CDN ;
- statut public.

Les bases de données ne doivent pas être exposées publiquement.

---

# 16. DNS

Le DNS doit être géré centralement.

Exemples :

```text
api.mansa.*
admin.mansa.*
pro.mansa.*
status.mansa.*
webhooks.mansa.*
```

Les domaines doivent être séparés par environnement.

---

# 17. Certificats TLS

Les certificats doivent être :

- valides ;
- renouvelés automatiquement ;
- surveillés ;
- révoqués si nécessaire ;
- séparés par environnement.

---

# 18. CDN

Un CDN peut être utilisé pour :

- site public ;
- site professionnel ;
- images ;
- fichiers statiques ;
- téléchargements ;
- contenu public ;
- protection DDoS.

Les contenus privés ne doivent pas être mis en cache publiquement.

---

# 19. Conteneurs

Les applications peuvent être conteneurisées.

Chaque image doit être :

- minimale ;
- versionnée ;
- scannée ;
- reproductible ;
- signée lorsque possible ;
- liée à un commit ;
- non exécutée en root lorsque possible.

---

# 20. Registre d’images

Le registre doit :

- être privé ;
- gérer les permissions ;
- conserver les versions ;
- scanner les vulnérabilités ;
- bloquer les images critiques ;
- auditer les accès.

---

# 21. Orchestration

Selon la maturité, Mansa peut utiliser :

- services managés ;
- conteneurs orchestrés ;
- Kubernetes ;
- plateformes serverless ;
- machines virtuelles contrôlées.

Le choix doit rester proportionné au besoin.

---

# 22. Kubernetes

Si Kubernetes est utilisé, il doit gérer :

- namespaces ;
- secrets ;
- services ;
- ingress ;
- autoscaling ;
- network policies ;
- probes ;
- resource limits ;
- rolling updates ;
- pod disruption budgets.

---

# 23. Services managés

Privilégier les services managés pour :

- PostgreSQL ;
- Redis ;
- stockage objet ;
- files ;
- monitoring ;
- secrets ;
- certificats ;
- sauvegardes.

Cela réduit la charge opérationnelle.

---

# 24. API Gateway

L’API Gateway doit être hautement disponible.

Elle doit gérer :

- terminaison TLS ;
- authentification ;
- rate limiting ;
- routage ;
- WAF ;
- observabilité ;
- versionnement ;
- restrictions IP ;
- protection DDoS.

---

# 25. Backend

Le backend doit pouvoir être déployé sur plusieurs instances.

Chaque instance doit être :

- stateless lorsque possible ;
- remplaçable ;
- observable ;
- versionnée ;
- autoscalable ;
- indépendante des données locales.

---

# 26. Stockage local interdit pour les données critiques

Les conteneurs ne doivent pas conserver localement des données critiques non répliquées.

Utiliser :

- PostgreSQL ;
- stockage objet ;
- Redis ;
- file ;
- volume persistant ;
- service managé.

---

# 27. PostgreSQL

La base de production doit disposer de :

- chiffrement ;
- réplication ;
- sauvegardes ;
- PITR ;
- monitoring ;
- accès privé ;
- rotation des accès ;
- maintenance planifiée ;
- haute disponibilité.

---

# 28. Redis

Redis peut être utilisé pour :

- cache ;
- sessions ;
- rate limiting ;
- locks ;
- files ;
- données temporaires.

Il ne doit pas devenir la seule source de vérité financière.

---

# 29. Message Broker

Le broker doit être :

- persistant ;
- surveillé ;
- redondant ;
- sécurisé ;
- séparé par environnement ;
- dimensionné ;
- sauvegardé lorsque nécessaire.

---

# 30. Stockage objet

Utilisé pour :

- documents ;
- pièces jointes ;
- reçus ;
- factures ;
- exports ;
- images ;
- sauvegardes ;
- logs archivés.

---

# 31. Classes de stockage

Les fichiers peuvent être classés selon :

- accès fréquent ;
- accès rare ;
- archivage ;
- conservation légale ;
- suppression automatique.

---

# 32. URLs temporaires

Les téléchargements privés doivent utiliser :

- URLs signées ;
- expiration ;
- permissions ;
- audit ;
- limite de téléchargement ;
- chiffrement.

---

# 33. Secrets

Le gestionnaire de secrets doit stocker :

- clés API ;
- certificats ;
- mots de passe ;
- secrets JWT ;
- secrets partenaires ;
- clés de chiffrement ;
- tokens.

---

# 34. Rotation

Chaque secret doit avoir :

- propriétaire ;
- version ;
- date de création ;
- date d’expiration ;
- politique de rotation ;
- statut ;
- audit.

---

# 35. IAM

Les accès techniques doivent utiliser :

- comptes de service ;
- rôles ;
- politiques minimales ;
- identités temporaires ;
- MFA ;
- séparation des responsabilités.

---

# 36. Comptes humains

Les comptes partagés sont interdits.

Chaque accès humain doit être individuel et traçable.

---

# 37. Accès administrateur

L’accès privilégié doit être :

- limité ;
- temporaire ;
- justifié ;
- approuvé ;
- audité ;
- révocable.

---

# 38. Bastion ou accès sécurisé

L’accès à certaines ressources peut passer par :

- bastion ;
- VPN ;
- tunnel sécurisé ;
- identité fédérée ;
- accès sans clé permanente.

---

# 39. WAF

Le Web Application Firewall doit protéger contre :

- attaques automatisées ;
- injections ;
- scanners ;
- abus ;
- bots ;
- règles connues ;
- trafic malveillant.

---

# 40. Protection DDoS

La plateforme doit prévoir :

- CDN ;
- filtrage ;
- rate limiting ;
- autoscaling ;
- protection fournisseur ;
- règles d’urgence ;
- communication incident.

---

# 41. Autoscaling

Le scaling peut dépendre :

- CPU ;
- mémoire ;
- requêtes ;
- latence ;
- taille de file ;
- sessions ;
- charge TPE ;
- pics horaires.

---

# 42. Limites de ressources

Chaque service doit définir :

- CPU minimum ;
- CPU maximum ;
- mémoire minimum ;
- mémoire maximum ;
- concurrence ;
- timeout ;
- nombre d’instances.

---

# 43. Haute disponibilité

Les services critiques doivent éviter le point unique de défaillance.

Cela concerne :

- API ;
- base ;
- cache ;
- file ;
- stockage ;
- DNS ;
- secrets ;
- monitoring.

---

# 44. Health checks

Chaque service doit exposer :

- liveness ;
- readiness ;
- dépendances ;
- version ;
- état critique.

---

# 45. Load Balancer

Le load balancer doit gérer :

- répartition ;
- TLS ;
- health checks ;
- timeouts ;
- connexions ;
- logs ;
- règles de routage.

---

# 46. Déploiement progressif

Stratégies possibles :

- rolling ;
- blue/green ;
- canary ;
- par région ;
- par pays ;
- par pourcentage ;
- par type d’utilisateur.

---

# 47. Blue/Green

Deux environnements identiques sont maintenus :

- actif ;
- nouveau.

Le trafic bascule après validation.

---

# 48. Canary

Une petite part du trafic reçoit la nouvelle version.

Surveiller :

- erreurs ;
- latence ;
- paiements ;
- crashs ;
- CPU ;
- incidents ;
- support.

---

# 49. Rollback

Un rollback doit pouvoir restaurer :

- application ;
- configuration ;
- image ;
- route ;
- feature flag ;
- base compatible ;
- version de package.

---

# 50. Migrations de base

Les migrations doivent être compatibles avec le déploiement progressif.

Éviter :

- suppression immédiate ;
- changement cassant ;
- verrou long ;
- migration non testée ;
- dépendance à un seul ordre fragile.

---

# 51. CI/CD

Le pipeline doit gérer :

- lint ;
- typecheck ;
- tests ;
- build ;
- scan ;
- image ;
- signature ;
- déploiement ;
- migration ;
- smoke tests ;
- rollback.

---

# 52. Branches

La stratégie de branches doit être définie.

Exemples :

- `main` ;
- branches de fonctionnalité ;
- branches de correction ;
- branches de release si nécessaire.

---

# 53. Production depuis une source contrôlée

Seuls les commits validés doivent pouvoir être déployés en production.

---

# 54. Artefacts

Chaque artefact doit être :

- immuable ;
- versionné ;
- lié au commit ;
- signé ;
- scanné ;
- conservé selon la politique.

---

# 55. Observabilité

L’infrastructure doit exposer :

- métriques ;
- logs ;
- traces ;
- événements ;
- coûts ;
- capacité ;
- versions ;
- déploiements ;
- erreurs.

---

# 56. Logs infrastructure

Inclure :

- accès ;
- réseau ;
- API cloud ;
- changements IAM ;
- déploiements ;
- certificats ;
- sauvegardes ;
- erreurs ;
- alertes.

---

# 57. Rétention des logs

La rétention dépend :

- sensibilité ;
- conformité ;
- coûts ;
- audit ;
- incident ;
- environnement.

---

# 58. Alertes infrastructure

Exemples :

- service indisponible ;
- CPU élevé ;
- mémoire élevée ;
- disque faible ;
- réplication en retard ;
- certificat expirant ;
- sauvegarde échouée ;
- coût anormal ;
- accès suspect ;
- image vulnérable ;
- scaling impossible.

---

# 59. Sauvegardes

Les sauvegardes doivent couvrir :

- bases ;
- configurations ;
- stockage ;
- secrets de référence ;
- manifests ;
- infrastructure code ;
- documents critiques.

---

# 60. RPO et RTO

Chaque service critique doit définir :

- RPO ;
- RTO ;
- priorité ;
- procédure ;
- test ;
- responsable.

---

# 61. Plan de reprise

Le plan de reprise doit documenter :

- panne région ;
- panne base ;
- perte de cluster ;
- corruption ;
- compromission ;
- suppression accidentelle ;
- panne partenaire ;
- indisponibilité DNS.

---

# 62. Tests de reprise

Il faut tester régulièrement :

- restauration ;
- bascule ;
- reconstruction ;
- récupération de secrets ;
- redéploiement ;
- reprise des files ;
- validation du ledger.

---

# 63. Plan de continuité

Le plan de continuité doit prévoir :

- service minimum ;
- mode lecture seule ;
- suspension de paiements ;
- bascule partenaire ;
- communication ;
- support ;
- reprise progressive.

---

# 64. Coûts

Les coûts doivent être suivis par :

- environnement ;
- service ;
- pays ;
- stockage ;
- réseau ;
- base ;
- observabilité ;
- IA ;
- partenaire.

---

# 65. Budgets

Chaque environnement peut avoir :

- budget ;
- seuil d’alerte ;
- responsable ;
- prévision ;
- limite ;
- action de réduction.

---

# 66. Optimisation

Mesures possibles :

- autoscaling ;
- extinction des environnements inutilisés ;
- stockage froid ;
- compression ;
- échantillonnage ;
- nettoyage ;
- réservations ;
- mutualisation raisonnable.

---

# 67. Multi-pays

L’infrastructure doit pouvoir varier par pays selon :

- réglementation ;
- partenaires ;
- localisation ;
- volume ;
- latence ;
- coût ;
- exigences institutionnelles.

---

# 68. Souveraineté des données

Certaines données peuvent nécessiter :

- stockage local ;
- région dédiée ;
- chiffrement distinct ;
- accès local ;
- contrat spécifique ;
- réplication limitée.

---

# 69. Séparation logique ou physique

Selon le risque, utiliser :

- tenant logique ;
- cluster séparé ;
- base séparée ;
- compte cloud séparé ;
- région séparée ;
- projet séparé.

---

# 70. Environnements partenaires

Chaque partenaire doit être relié au bon environnement Mansa.

Exemple :

```text
Mansa Recette → Partenaire Sandbox
Mansa Préproduction → Partenaire Préproduction
Mansa Production → Partenaire Production
```

---

# 71. Configuration

Les configurations doivent être injectées par environnement.

Elles ne doivent pas être codées en dur.

---

# 72. Feature flags

Les feature flags doivent permettre :

- activation progressive ;
- désactivation ;
- pays ;
- partenaire ;
- application ;
- version ;
- urgence.

---

# 73. Maintenance

Le système doit pouvoir activer :

- maintenance globale ;
- maintenance par service ;
- lecture seule ;
- blocage par pays ;
- blocage partenaire ;
- blocage application.

---

# 74. Procédures opérationnelles

Chaque composant critique doit disposer de :

- runbook ;
- procédure de redémarrage ;
- procédure de rollback ;
- procédure de récupération ;
- procédure d’escalade ;
- contacts.

---

# 75. Administration

Le portail Admin peut afficher :

- santé des services ;
- version ;
- environnement ;
- incidents ;
- coûts ;
- capacité ;
- sauvegardes ;
- certificats ;
- déploiements ;
- maintenance.

Il ne doit pas exposer directement les secrets.

---

# 76. Permissions

Exemples :

```text
infrastructure.read
infrastructure.deploy
infrastructure.rollback
infrastructure.scale
infrastructure.maintenance.manage
infrastructure.backup.read
infrastructure.restore.execute
infrastructure.secret.reference
infrastructure.cost.read
infrastructure.production.access
```

---

# 77. Actions critiques

Doivent être protégées :

- accès production ;
- restauration ;
- suppression d’environnement ;
- rotation clé principale ;
- modification réseau ;
- désactivation WAF ;
- changement DNS ;
- bascule région ;
- arrêt base ;
- modification IAM.

---

# 78. Double validation

Recommandée pour :

- restauration production ;
- suppression ;
- bascule région ;
- modification IAM critique ;
- changement de certificat principal ;
- arrêt global ;
- accès d’urgence ;
- modification réseau sensible.

---

# 79. Audit

Chaque changement doit enregistrer :

- auteur ;
- approbateur ;
- environnement ;
- ressource ;
- ancienne valeur ;
- nouvelle valeur ;
- date ;
- ticket ;
- résultat ;
- rollback ;
- corrélation.

---

# 80. API internes

Exemples :

```http
GET    /infrastructure/environments
GET    /infrastructure/services
GET    /infrastructure/health
GET    /infrastructure/deployments
GET    /infrastructure/backups
GET    /infrastructure/costs

POST   /infrastructure/deployments
POST   /infrastructure/rollbacks
POST   /infrastructure/maintenance
POST   /infrastructure/restores
```

---

# 81. Modèles

- CloudEnvironment
- CloudRegion
- InfrastructureService
- InfrastructureResource
- Deployment
- DeploymentArtifact
- DeploymentApproval
- Rollback
- Backup
- RestoreExecution
- CertificateRecord
- SecretReference
- NetworkRule
- ScalingPolicy
- CostRecord
- InfrastructureIncident
- InfrastructureAudit

---

# 82. Règles métier

1. L’infrastructure est définie comme code.
2. Les environnements sont séparés.
3. Les secrets ne sont jamais committés.
4. La production est protégée.
5. Les services critiques sont redondants.
6. Les données critiques ne dépendent pas du stockage local.
7. Les bases ne sont pas publiques.
8. Les certificats sont surveillés.
9. Les images sont scannées.
10. Les artefacts sont immuables.
11. Les déploiements sont traçables.
12. Les rollbacks sont préparés.
13. Les migrations sont compatibles.
14. Les accès humains sont individuels.
15. Les permissions sont minimales.
16. Les sauvegardes sont testées.
17. Les RPO/RTO sont définis.
18. Les coûts sont surveillés.
19. Les environnements partenaires sont correctement reliés.
20. Les feature flags permettent une désactivation rapide.
21. Les logs sont centralisés.
22. Les actions critiques sont auditées.
23. Les données sont localisées selon les règles applicables.
24. Les tests de reprise sont réguliers.
25. L’infrastructure peut être reconstruite.

---

# 83. Analytics

Événements possibles :

```text
infrastructure_deployment_started
infrastructure_deployment_completed
infrastructure_deployment_failed
infrastructure_rollback_started
infrastructure_rollback_completed
infrastructure_backup_completed
infrastructure_restore_test_completed
infrastructure_certificate_expiring
infrastructure_cost_threshold_exceeded
infrastructure_scaling_started
infrastructure_region_failover_started
infrastructure_maintenance_enabled
infrastructure_production_access_granted
```

---

# 84. Tests

- tests Infrastructure as Code ;
- tests réseau ;
- tests DNS ;
- tests TLS ;
- tests WAF ;
- tests DDoS ;
- tests autoscaling ;
- tests déploiement ;
- tests canary ;
- tests blue/green ;
- tests rollback ;
- tests migration ;
- tests sauvegarde ;
- tests restauration ;
- tests failover ;
- tests multi-régions ;
- tests IAM ;
- tests secrets ;
- tests coûts ;
- tests monitoring ;
- tests de reprise complète.

---

# 85. Critères d’acceptation

L’infrastructure est validée lorsque :

- les environnements sont isolés ;
- l’infrastructure est reproductible ;
- les secrets sont sécurisés ;
- les services critiques sont redondants ;
- les bases sont privées ;
- les certificats sont renouvelés automatiquement ;
- les artefacts sont versionnés ;
- les déploiements progressifs fonctionnent ;
- les rollbacks sont testés ;
- les sauvegardes sont automatiques ;
- les restaurations sont vérifiées ;
- les RPO et RTO sont définis ;
- les accès production sont limités ;
- les changements sont audités ;
- les coûts sont suivis ;
- les alertes sont actives ;
- la reprise après panne est documentée ;
- les tests couvrent les scénarios critiques.
