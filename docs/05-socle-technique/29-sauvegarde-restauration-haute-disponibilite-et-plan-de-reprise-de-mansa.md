# 29 — Sauvegarde, restauration, haute disponibilité et plan de reprise de Mansa

## 1. Objet du document

Ce document définit la stratégie officielle de continuité technique et de reprise de Mansa.

Il couvre :

- les sauvegardes ;
- les restaurations ;
- PostgreSQL ;
- les documents ;
- les fichiers ;
- les configurations ;
- les secrets de référence ;
- les files ;
- les événements ;
- les applications ;
- les infrastructures ;
- les partenaires ;
- les régions ;
- la haute disponibilité ;
- le basculement ;
- le Plan de Reprise d’Activité ;
- le Plan de Continuité d’Activité ;
- les RPO ;
- les RTO ;
- les tests de restauration ;
- les exercices de crise ;
- la reconstruction ;
- la communication ;
- l’audit.

L’objectif est de garantir qu’après :

- une panne ;
- une erreur humaine ;
- une suppression accidentelle ;
- une corruption ;
- une attaque ;
- une indisponibilité régionale ;
- un déploiement défectueux ;
- une perte d’infrastructure ;
- une panne partenaire ;

Mansa puisse protéger les données, maintenir un service minimum et reprendre ses activités de manière contrôlée.

---

# 2. Principes fondamentaux

## 2.1 Une sauvegarde non testée n’est pas considérée comme fiable

La réussite d’une tâche de sauvegarde ne suffit pas.

Mansa doit vérifier régulièrement :

- que la sauvegarde existe ;
- qu’elle est lisible ;
- qu’elle est complète ;
- qu’elle peut être déchiffrée ;
- qu’elle peut être restaurée ;
- que les données restaurées sont cohérentes ;
- que le ledger reste équilibré ;
- que les applications peuvent redémarrer.

---

## 2.2 La sauvegarde ne remplace pas la haute disponibilité

La haute disponibilité réduit l’interruption.

La sauvegarde permet de récupérer après une perte ou une corruption.

Les deux mécanismes sont complémentaires.

---

## 2.3 La réplication ne remplace pas la sauvegarde

Une suppression ou une corruption peut être répliquée.

Mansa doit donc disposer :

- de réplicas ;
- de sauvegardes indépendantes ;
- de snapshots ;
- d’un Point-in-Time Recovery ;
- d’une politique d’immutabilité.

---

## 2.4 Les données financières ont la priorité maximale

Les domaines suivants doivent bénéficier des protections les plus fortes :

- ledger ;
- paiements ;
- transferts ;
- cartes ;
- remboursements ;
- règlements ;
- commissions ;
- rapprochements ;
- comptes de suspense ;
- audits financiers.

---

## 2.5 Les procédures doivent être exécutables sans dépendre d’une seule personne

Les procédures doivent être :

- documentées ;
- versionnées ;
- accessibles aux personnes autorisées ;
- testées ;
- suffisamment claires ;
- accompagnées de contacts et responsabilités.

---

# 3. Définitions

## 3.1 RPO

Le Recovery Point Objective représente la perte maximale de données acceptable.

Exemple :

```text
RPO = 5 minutes
```

Cela signifie que Mansa doit pouvoir revenir à un état datant au maximum de cinq minutes avant l’incident.

---

## 3.2 RTO

Le Recovery Time Objective représente le délai maximal acceptable pour rétablir le service.

Exemple :

```text
RTO = 30 minutes
```

---

## 3.3 PRA

Le Plan de Reprise d’Activité définit comment restaurer les systèmes après une interruption majeure.

---

## 3.4 PCA

Le Plan de Continuité d’Activité définit comment maintenir un service minimum pendant l’incident.

---

## 3.5 Haute disponibilité

La haute disponibilité vise à réduire l’interruption grâce à :

- redondance ;
- réplication ;
- basculement ;
- autoscaling ;
- surveillance ;
- remplacement automatique.

---

# 4. Classification des services

Chaque service doit être classé selon sa criticité.

## 4.1 Niveau 1 — Critique

Exemples :

- authentification ;
- API Gateway ;
- ledger ;
- wallets ;
- paiements ;
- cartes ;
- base principale ;
- secrets ;
- audit financier.

## 4.2 Niveau 2 — Majeur

Exemples :

- KYC ;
- Mobile Money ;
- TPE ;
- notifications de sécurité ;
- fraude ;
- rapprochement ;
- portail Admin critique.

## 4.3 Niveau 3 — Important

Exemples :

- Commerce ;
- Annuaire ;
- support ;
- documents ;
- rapports ;
- analytics opérationnels.

## 4.4 Niveau 4 — Secondaire

Exemples :

- contenus marketing ;
- campagnes ;
- recommandations ;
- statistiques non critiques ;
- site éditorial non transactionnel.

---

# 5. Matrice RPO/RTO

Chaque service doit avoir des objectifs explicites.

Exemple :

| Domaine | RPO cible | RTO cible |
|---|---:|---:|
| Ledger | proche de zéro | très court |
| Paiements | quelques minutes maximum | très court |
| Authentification | quelques minutes | court |
| Documents KYC | faible perte acceptable | court |
| Notifications marketing | plusieurs heures | plusieurs heures |
| Analytics | une journée possible selon le cas | plusieurs heures |

Les valeurs définitives doivent être adaptées :

- au pays ;
- aux partenaires ;
- aux contrats ;
- aux obligations ;
- aux coûts ;
- à la maturité de Mansa.

---

# 6. Périmètre des sauvegardes

Les sauvegardes doivent couvrir :

- bases PostgreSQL ;
- schémas Prisma ;
- migrations ;
- données du ledger ;
- fichiers utilisateurs ;
- documents KYC/KYB ;
- reçus ;
- factures ;
- configurations ;
- feature flags ;
- modèles de notifications ;
- workflows ;
- données partenaires ;
- journaux d’audit ;
- infrastructure as code ;
- manifests ;
- certificats publics ;
- références de secrets ;
- configurations DNS ;
- artefacts critiques.

---

# 7. Données qui ne doivent pas être sauvegardées en clair

Exemples :

- mots de passe ;
- PIN ;
- OTP ;
- CVV ;
- secrets d’API ;
- clés privées ;
- tokens complets ;
- données de carte non nécessaires ;
- secrets partenaires.

Les sauvegardes doivent être chiffrées.

---

# 8. Types de sauvegardes

Mansa peut utiliser :

- sauvegarde complète ;
- sauvegarde incrémentale ;
- sauvegarde différentielle ;
- snapshot ;
- export logique ;
- sauvegarde physique ;
- journal de transactions ;
- Point-in-Time Recovery ;
- copie interrégionale ;
- archivage.

---

# 9. Sauvegarde PostgreSQL

La base principale doit disposer de :

- sauvegardes automatiques ;
- réplication ;
- journaux WAL ;
- PITR ;
- snapshots ;
- chiffrement ;
- contrôle d’intégrité ;
- surveillance ;
- tests de restauration.

---

# 10. Sauvegardes logiques

Les sauvegardes logiques peuvent être utilisées pour :

- migrations ;
- tests ;
- archivage ;
- extraction contrôlée ;
- restauration ciblée ;
- vérification.

Elles ne doivent pas être l’unique mécanisme de reprise pour une base importante.

---

# 11. Sauvegardes physiques

Les sauvegardes physiques sont adaptées à :

- restauration complète ;
- gros volumes ;
- récupération rapide ;
- réplication ;
- PITR.

---

# 12. Point-in-Time Recovery

Le PITR doit permettre de restaurer la base à une date précise.

Cas d’usage :

- suppression accidentelle ;
- migration défectueuse ;
- corruption logique ;
- erreur administrative ;
- écriture massive invalide.

---

# 13. Sauvegarde du ledger

Le ledger doit bénéficier de contrôles supplémentaires :

- sauvegarde fréquente ;
- réplication ;
- checksum ;
- vérification de l’équilibre ;
- conservation des écritures ;
- protection contre la modification ;
- contrôle après restauration ;
- rapprochement post-reprise.

---

# 14. Reconstruction du ledger

Mansa doit pouvoir :

- reconstruire les soldes ;
- recalculer les agrégats ;
- vérifier les écritures ;
- détecter les transactions déséquilibrées ;
- comparer avant et après incident ;
- produire un rapport.

---

# 15. Sauvegarde des documents

Le stockage objet doit couvrir :

- documents KYC ;
- contrats ;
- factures ;
- reçus ;
- pièces jointes ;
- exports importants ;
- documents publics officiels.

---

# 16. Versionnement des fichiers

Le stockage peut activer :

- versioning ;
- rétention ;
- suppression différée ;
- verrouillage ;
- restauration de version ;
- journal d’accès.

---

# 17. Immutabilité

Certaines sauvegardes doivent être protégées contre :

- suppression ;
- modification ;
- ransomware ;
- compte compromis ;
- erreur humaine.

Mécanismes possibles :

- Object Lock ;
- WORM ;
- compte séparé ;
- coffre de sauvegarde ;
- permissions spécifiques ;
- période de rétention obligatoire.

---

# 18. Copies indépendantes

Les sauvegardes critiques doivent être conservées dans plusieurs emplacements.

Exemple de logique :

- copie principale ;
- copie dans une autre zone ;
- copie dans une autre région ;
- copie isolée ou immuable.

---

# 19. Règle de diversification

Une stratégie inspirée du principe `3-2-1` peut être utilisée :

- au moins trois copies ;
- sur au moins deux types ou emplacements de stockage ;
- avec au moins une copie isolée.

---

# 20. Sauvegarde des configurations

Les configurations importantes doivent être sauvegardées ou versionnées :

- paramètres globaux ;
- paramètres pays ;
- partenaires ;
- limites ;
- frais ;
- feature flags ;
- règles de maintenance ;
- versions minimales ;
- modèles ;
- rôles ;
- permissions.

---

# 21. Sauvegarde de l’infrastructure

L’Infrastructure as Code doit permettre de reconstruire :

- réseaux ;
- clusters ;
- bases ;
- caches ;
- files ;
- stockage ;
- monitoring ;
- IAM ;
- certificats ;
- DNS ;
- environnements.

---

# 22. Sauvegarde des secrets

Les secrets eux-mêmes doivent être protégés par le gestionnaire dédié.

Mansa doit sauvegarder ou documenter :

- références ;
- versions ;
- propriétaires ;
- politiques de rotation ;
- procédures de récupération ;
- accès d’urgence.

La récupération des clés doit être particulièrement protégée.

---

# 23. Sauvegarde des files

Les files critiques doivent définir :

- persistance ;
- réplication ;
- rétention ;
- reprise ;
- dead-letter queue ;
- rejeu ;
- duplication ;
- conservation du statut en base.

La file ne doit pas être la seule source d’une opération métier.

---

# 24. Sauvegarde des événements

Les événements importants peuvent être archivés pour :

- audit ;
- reconstruction ;
- rejeu ;
- investigation ;
- analytics ;
- conformité.

---

# 25. Sauvegarde des journaux d’audit

Les journaux d’audit doivent être :

- protégés ;
- horodatés ;
- chiffrés ;
- conservés ;
- non modifiables lorsque nécessaire ;
- restaurables ;
- séparés des logs ordinaires.

---

# 26. Fréquence

La fréquence dépend de :

- criticité ;
- volume ;
- RPO ;
- coût ;
- réglementation ;
- capacité de restauration.

Exemples :

- continu ou quasi continu pour le ledger ;
- très fréquent pour les paiements ;
- quotidien pour certains documents ;
- hebdomadaire pour certains contenus ;
- archivage mensuel ou annuel selon les obligations.

---

# 27. Politique de rétention

La rétention doit définir :

- sauvegardes horaires ;
- quotidiennes ;
- hebdomadaires ;
- mensuelles ;
- annuelles ;
- archivées ;
- immuables ;
- expirées.

---

# 28. Rotation des sauvegardes

Une politique de type Grandfather-Father-Son peut être utilisée pour organiser :

- sauvegardes quotidiennes ;
- sauvegardes hebdomadaires ;
- sauvegardes mensuelles ;
- sauvegardes annuelles.

---

# 29. Chiffrement des sauvegardes

Les sauvegardes doivent être chiffrées :

- en transit ;
- au repos ;
- lors de la copie ;
- lors de l’archivage ;
- lors du téléchargement.

---

# 30. Gestion des clés

Les clés de sauvegarde doivent :

- être séparées des données ;
- être versionnées ;
- être rotatives ;
- avoir des propriétaires ;
- avoir une procédure de récupération ;
- être accessibles à très peu de rôles ;
- être auditées.

---

# 31. Contrôle d’intégrité

Chaque sauvegarde doit pouvoir être vérifiée par :

- checksum ;
- taille ;
- manifest ;
- signature ;
- validation de structure ;
- test de lecture ;
- comparaison.

---

# 32. Statuts des sauvegardes

Valeurs possibles :

- SCHEDULED ;
- RUNNING ;
- COMPLETED ;
- COMPLETED_WITH_WARNINGS ;
- FAILED ;
- CORRUPTED ;
- EXPIRED ;
- DELETED ;
- RESTORED ;
- VERIFIED.

---

# 33. Monitoring des sauvegardes

Surveiller :

- dernière réussite ;
- durée ;
- taille ;
- croissance ;
- erreurs ;
- retard ;
- corruption ;
- absence de sauvegarde ;
- échec de chiffrement ;
- échec de copie ;
- rétention ;
- coût.

---

# 34. Alertes

Une alerte doit être déclenchée si :

- sauvegarde absente ;
- sauvegarde échouée ;
- sauvegarde trop ancienne ;
- copie secondaire manquante ;
- checksum invalide ;
- chiffrement échoue ;
- stockage est saturé ;
- restauration échoue ;
- PITR est indisponible ;
- réplication est en retard.

---

# 35. Restauration

Une restauration doit suivre une procédure officielle.

Étapes possibles :

1. identifier l’incident ;
2. définir le point de restauration ;
3. obtenir les approbations ;
4. isoler la cible ;
5. restaurer ;
6. vérifier l’intégrité ;
7. vérifier les données financières ;
8. tester les services ;
9. basculer ;
10. surveiller ;
11. clôturer ;
12. produire un rapport.

---

# 36. Types de restauration

- restauration complète ;
- restauration partielle ;
- restauration de table ;
- restauration de fichier ;
- restauration de configuration ;
- restauration de région ;
- restauration d’environnement ;
- restauration à un instant précis ;
- reconstruction depuis les événements.

---

# 37. Restauration ciblée

Une restauration ciblée peut concerner :

- un document ;
- un utilisateur ;
- une configuration ;
- une table ;
- un partenaire ;
- une période ;
- un fichier supprimé.

Elle doit éviter d’écraser des données plus récentes sans contrôle.

---

# 38. Environnement de restauration

La restauration doit d’abord être exécutée dans un environnement isolé lorsque la situation le permet.

Cela permet :

- vérification ;
- comparaison ;
- analyse ;
- extraction ciblée ;
- contrôle de sécurité ;
- validation métier.

---

# 39. Validation après restauration

Vérifications minimales :

- schéma ;
- migrations ;
- utilisateurs ;
- comptes ;
- paiements ;
- ledger ;
- soldes ;
- documents ;
- permissions ;
- configurations ;
- files ;
- partenaires ;
- audits.

---

# 40. Validation financière

Après une restauration financière, il faut vérifier :

- équilibre du ledger ;
- soldes ;
- transactions ;
- réservations ;
- remboursements ;
- suspense ;
- rapprochement ;
- opérations dupliquées ;
- opérations manquantes.

---

# 41. Reprise des opérations en attente

Après restauration, le système doit identifier :

- jobs non terminés ;
- paiements pending ;
- statuts inconnus ;
- webhooks non traités ;
- messages en dead letter ;
- opérations TPE non synchronisées ;
- rapprochements interrompus.

---

# 42. Prévention des doublons après reprise

Avant de reprendre :

- vérifier l’idempotence ;
- vérifier les références externes ;
- vérifier les événements déjà consommés ;
- vérifier les opérations partenaires ;
- restaurer les Inbox et Outbox ;
- protéger les jobs.

---

# 43. Tests de restauration

Les tests doivent couvrir :

- base complète ;
- PITR ;
- fichier ;
- configuration ;
- stockage objet ;
- secrets de référence ;
- infrastructure ;
- application ;
- ledger ;
- région.

---

# 44. Fréquence des tests

La fréquence doit dépendre de la criticité.

Exemples :

- tests réguliers des sauvegardes critiques ;
- exercice trimestriel de restauration ;
- exercice annuel de reprise complète ;
- test après changement majeur ;
- test après migration importante.

---

# 45. Rapports de restauration

Chaque test doit enregistrer :

- sauvegarde utilisée ;
- point choisi ;
- environnement ;
- durée ;
- résultat ;
- erreurs ;
- RPO mesuré ;
- RTO mesuré ;
- intégrité ;
- écarts ;
- actions correctives.

---

# 46. Haute disponibilité applicative

Les services critiques doivent utiliser :

- plusieurs instances ;
- plusieurs zones ;
- load balancer ;
- health checks ;
- remplacement automatique ;
- autoscaling ;
- déploiement progressif.

---

# 47. Haute disponibilité PostgreSQL

Elle peut utiliser :

- instance principale ;
- standby ;
- réplication synchrone ou asynchrone ;
- failover automatique ;
- réplicas de lecture ;
- monitoring ;
- fencing.

---

# 48. Failover

Le failover doit définir :

- condition de déclenchement ;
- décision automatique ou manuelle ;
- cible ;
- vérifications ;
- bascule ;
- retour ;
- audit ;
- communication.

---

# 49. Split-Brain

L’architecture doit prévenir la présence de deux instances principales écrivant simultanément de manière incohérente.

Mesures :

- quorum ;
- fencing ;
- verrou ;
- leader election ;
- autorité unique ;
- contrôle de réplication.

---

# 50. Haute disponibilité Redis

Selon l’usage :

- réplication ;
- Sentinel ;
- cluster ;
- service managé ;
- persistance ;
- failover.

Une perte Redis ne doit pas provoquer une perte financière définitive.

---

# 51. Haute disponibilité des files

Le broker doit prévoir :

- réplication ;
- persistance ;
- acquittement ;
- reprise ;
- consommateurs multiples ;
- dead-letter queue ;
- monitoring.

---

# 52. Haute disponibilité du stockage

Le stockage doit utiliser :

- réplication ;
- versionnement ;
- durabilité élevée ;
- copie interrégionale si nécessaire ;
- contrôle d’intégrité ;
- restauration.

---

# 53. Haute disponibilité DNS

Le DNS doit disposer de :

- plusieurs serveurs ;
- protection ;
- accès limité ;
- contrôle des changements ;
- procédure de bascule ;
- sauvegarde de configuration.

---

# 54. Haute disponibilité des secrets

Le gestionnaire de secrets doit rester disponible pendant :

- déploiement ;
- bascule ;
- redémarrage ;
- reprise régionale.

Une panne de secret ne doit pas être contournée par une exposition manuelle non sécurisée.

---

# 55. Mode dégradé

Pendant un incident, Mansa peut activer :

- lecture seule ;
- consultation uniquement ;
- blocage des paiements ;
- blocage d’un partenaire ;
- blocage d’un pays ;
- support uniquement ;
- gel des nouvelles inscriptions ;
- gel des exports ;
- TPE limité ;
- maintenance complète.

---

# 56. Service minimum

Le service minimum peut inclure :

- consultation du solde ;
- consultation de l’historique ;
- blocage de carte ;
- accès au support ;
- téléchargement de documents ;
- communication d’incident.

---

# 57. Plan de Continuité d’Activité

Le PCA doit définir :

- services prioritaires ;
- dépendances ;
- équipe ;
- partenaires ;
- procédures ;
- mode dégradé ;
- communication ;
- durée ;
- critères de retour à la normale.

---

# 58. Plan de Reprise d’Activité

Le PRA doit contenir :

- scénario ;
- déclencheur ;
- responsable ;
- contacts ;
- ressources ;
- sauvegardes ;
- ordre de restauration ;
- validations ;
- bascule ;
- reprise ;
- retour à la normale ;
- clôture.

---

# 59. Scénarios de reprise

Le PRA doit couvrir au minimum :

- panne complète de région ;
- perte de base ;
- corruption de données ;
- ransomware ;
- compromission de compte cloud ;
- suppression accidentelle ;
- panne DNS ;
- panne secrets ;
- perte du broker ;
- panne stockage ;
- déploiement destructif ;
- panne partenaire majeure.

---

# 60. Ordre de reprise

Ordre indicatif :

1. identité et IAM ;
2. réseau ;
3. secrets ;
4. base ;
5. ledger ;
6. cache et files ;
7. API Gateway ;
8. services critiques ;
9. partenaires ;
10. applications ;
11. documents ;
12. services secondaires ;
13. analytics.

L’ordre réel doit être documenté par environnement.

---

# 61. Dépendances critiques

Pour chaque service, documenter :

- base ;
- cache ;
- file ;
- secrets ;
- DNS ;
- partenaire ;
- stockage ;
- certificat ;
- service interne ;
- configuration.

---

# 62. Région de secours

Une région de secours peut être :

- active-active ;
- active-passive ;
- warm standby ;
- pilot light ;
- backup and restore.

Le choix dépend :

- du RTO ;
- du RPO ;
- des coûts ;
- de la complexité ;
- des obligations.

---

# 63. Active-Active

Avantages :

- bascule rapide ;
- disponibilité élevée ;
- répartition.

Risques :

- cohérence ;
- conflits ;
- complexité ;
- coût ;
- ledger multi-région.

---

# 64. Active-Passive

Une région principale sert le trafic.

Une région secondaire est prête à prendre le relais.

Elle doit être testée régulièrement.

---

# 65. Warm Standby

La région secondaire dispose de ressources réduites mais fonctionnelles.

Elle est augmentée lors de la reprise.

---

# 66. Pilot Light

Seuls les composants essentiels restent actifs.

Le reste est reconstruit au besoin.

---

# 67. Reconstruction complète

Mansa doit pouvoir reconstruire un environnement depuis :

- GitHub ;
- Infrastructure as Code ;
- artefacts ;
- migrations ;
- sauvegardes ;
- configurations ;
- secrets ;
- procédures.

---

# 68. Exercices de crise

Les exercices peuvent simuler :

- base indisponible ;
- région indisponible ;
- corruption ;
- suppression ;
- file bloquée ;
- perte de secret ;
- panne partenaire ;
- attaque ;
- restauration urgente.

---

# 69. Tabletop Exercise

Un exercice théorique réunit les responsables pour dérouler un scénario.

Il doit identifier :

- dépendances oubliées ;
- responsabilités floues ;
- documents manquants ;
- décisions lentes ;
- contacts invalides ;
- étapes impraticables.

---

# 70. Exercice technique

Un exercice technique doit réellement tester :

- sauvegarde ;
- restauration ;
- bascule ;
- reconstruction ;
- reprise ;
- communication ;
- monitoring.

---

# 71. Responsabilités

Rôles possibles :

- Incident Commander ;
- responsable infrastructure ;
- responsable base ;
- responsable sécurité ;
- responsable backend ;
- responsable finance ;
- responsable conformité ;
- responsable pays ;
- communication ;
- support ;
- partenaire.

---

# 72. Déclenchement du PRA

Le déclenchement doit être réservé à des rôles autorisés.

Il peut nécessiter :

- constat ;
- gravité ;
- validation ;
- justification ;
- notification ;
- journalisation.

---

# 73. Communication interne

Elle doit préciser :

- scénario ;
- impact ;
- équipe ;
- décisions ;
- point de restauration ;
- progression ;
- risques ;
- prochaine mise à jour.

---

# 74. Communication externe

Selon l’incident, informer :

- utilisateurs ;
- commerçants ;
- partenaires ;
- banques ;
- autorités ;
- administrations ;
- équipes pays.

---

# 75. Statut public

Le statut peut afficher :

- service opérationnel ;
- performance dégradée ;
- incident partiel ;
- incident majeur ;
- maintenance ;
- reprise en cours ;
- incident résolu.

---

# 76. Retour à la normale

Le retour doit vérifier :

- disponibilité ;
- intégrité ;
- performance ;
- transactions ;
- partenaires ;
- sécurité ;
- files ;
- monitoring ;
- support ;
- communication.

---

# 77. Retour arrière après failover

Le retour vers la région principale doit être planifié.

Il doit éviter :

- perte de données ;
- double écriture ;
- conflit ;
- interruption supplémentaire ;
- divergence de configuration.

---

# 78. Données créées pendant le mode dégradé

Le système doit identifier :

- données locales ;
- opérations en attente ;
- paiements non confirmés ;
- tickets ;
- fichiers ;
- événements ;
- actions manuelles.

Elles doivent être réconciliées après reprise.

---

# 79. Sécurité pendant la reprise

Une situation d’urgence ne doit pas supprimer les contrôles essentiels.

Maintenir :

- authentification ;
- autorisation ;
- chiffrement ;
- audit ;
- approbation ;
- séparation des responsabilités.

---

# 80. Accès d’urgence

L’accès d’urgence doit être :

- temporaire ;
- limité ;
- approuvé ;
- surveillé ;
- enregistré ;
- révoqué après l’incident ;
- revu après usage.

---

# 81. Permissions

Exemples :

```text
backup.read
backup.create
backup.verify
backup.retention.manage
restore.request
restore.approve
restore.execute
restore.production.execute
failover.read
failover.execute
disaster_recovery.activate
disaster_recovery.close
business_continuity.manage
recovery.audit.read
```

---

# 82. Actions critiques

Doivent être particulièrement protégées :

- restauration production ;
- restauration du ledger ;
- choix du point de récupération ;
- suppression de sauvegarde ;
- modification de rétention ;
- désactivation de l’immutabilité ;
- failover ;
- retour vers la région principale ;
- reconstruction des soldes ;
- activation du PRA.

---

# 83. Double validation

Recommandée pour :

- restauration production ;
- restauration financière ;
- suppression de sauvegarde critique ;
- changement RPO/RTO ;
- bascule régionale ;
- modification du stockage immuable ;
- récupération de clé ;
- clôture d’un PRA majeur.

---

# 84. Administration

Le portail Admin technique peut afficher :

- statut des sauvegardes ;
- dernière réussite ;
- prochaine exécution ;
- rétention ;
- copies ;
- tests de restauration ;
- RPO ;
- RTO ;
- réplication ;
- failover ;
- exercices ;
- rapports ;
- alertes.

Il ne doit pas permettre le téléchargement libre de sauvegardes sensibles.

---

# 85. API internes

Exemples :

```http
GET    /continuity/backups
GET    /continuity/backups/{id}
GET    /continuity/restores
GET    /continuity/replication
GET    /continuity/rpo-rto
GET    /continuity/recovery-plans

POST   /continuity/backups/{id}/verify
POST   /continuity/restores
POST   /continuity/restores/{id}/approve
POST   /continuity/failovers
POST   /continuity/disaster-recovery/activate
POST   /continuity/exercises
```

---

# 86. Modèles

- BackupPolicy
- BackupExecution
- BackupCopy
- BackupVerification
- BackupRetention
- RestoreRequest
- RestoreExecution
- RestoreValidation
- RecoveryPoint
- RecoveryObjective
- ReplicationStatus
- FailoverPlan
- FailoverExecution
- BusinessContinuityPlan
- DisasterRecoveryPlan
- RecoveryExercise
- RecoveryReport
- RecoveryAction
- RecoveryAudit

---

# 87. Audit

Chaque opération doit enregistrer :

- auteur ;
- approbateur ;
- environnement ;
- ressource ;
- sauvegarde ;
- point de restauration ;
- date ;
- motif ;
- durée ;
- résultat ;
- erreur ;
- RPO mesuré ;
- RTO mesuré ;
- bascule ;
- rollback ;
- ticket.

---

# 88. Monitoring

Surveiller :

- sauvegardes ;
- réplication ;
- PITR ;
- stockage ;
- checksum ;
- copies ;
- rétention ;
- restauration ;
- bascule ;
- RPO réel ;
- RTO réel ;
- état des régions ;
- capacité de secours.

---

# 89. Analytics

Événements possibles :

```text
backup_started
backup_completed
backup_failed
backup_verification_started
backup_verification_failed
restore_requested
restore_started
restore_completed
restore_failed
restore_validation_failed
replication_lag_detected
failover_started
failover_completed
failover_failed
disaster_recovery_activated
business_continuity_mode_enabled
recovery_exercise_started
recovery_exercise_completed
rpo_target_missed
rto_target_missed
```

---

# 90. Tests

- tests de sauvegarde ;
- tests de chiffrement ;
- tests de checksum ;
- tests de copie ;
- tests de rétention ;
- tests d’immutabilité ;
- tests PostgreSQL ;
- tests PITR ;
- tests ledger ;
- tests documents ;
- tests configurations ;
- tests infrastructure ;
- tests de restauration complète ;
- tests de restauration ciblée ;
- tests de reconstruction ;
- tests de failover ;
- tests de retour ;
- tests de mode dégradé ;
- tests de PCA ;
- tests de PRA ;
- tests de permissions ;
- tests de double validation ;
- exercices de crise.

---

# 91. Règles métier

1. Toute donnée critique est sauvegardée.
2. Les sauvegardes sont chiffrées.
3. Les sauvegardes critiques possèdent plusieurs copies.
4. Une copie critique est isolée ou immuable.
5. La réplication ne remplace pas la sauvegarde.
6. Les sauvegardes sont testées.
7. Le ledger bénéficie de contrôles renforcés.
8. Le PITR est activé pour les bases critiques lorsque possible.
9. Les restaurations sont d’abord vérifiées en environnement isolé lorsque possible.
10. Une restauration financière exige une validation renforcée.
11. Les opérations en attente sont réconciliées après reprise.
12. L’idempotence empêche les doublons.
13. Chaque service critique possède un RPO.
14. Chaque service critique possède un RTO.
15. Les RPO/RTO sont mesurés pendant les exercices.
16. Les services critiques sont redondants.
17. Les failovers sont testés.
18. Les régions de secours sont maintenues.
19. Le PRA est documenté.
20. Le PCA définit un service minimum.
21. Les accès d’urgence sont temporaires.
22. Les procédures sont versionnées.
23. Les exercices produisent des actions correctives.
24. Les restaurations sont auditées.
25. Mansa peut reconstruire son infrastructure depuis des sources contrôlées.

---

# 92. Critères d’acceptation

La stratégie de sauvegarde et de reprise est validée lorsque :

- les services critiques sont classés ;
- les RPO et RTO sont définis ;
- les bases sont sauvegardées automatiquement ;
- le PITR est disponible pour les données critiques ;
- le stockage de documents est versionné ;
- les sauvegardes sont chiffrées ;
- plusieurs copies existent ;
- une copie critique est protégée contre la suppression ;
- les sauvegardes sont surveillées ;
- les restaurations sont testées ;
- le ledger est contrôlé après restauration ;
- les opérations en attente peuvent être reprises ;
- les services critiques sont redondants ;
- les failovers sont documentés ;
- le mode dégradé est prévu ;
- le PCA est défini ;
- le PRA est défini ;
- les exercices sont organisés ;
- les accès de reprise sont protégés ;
- les actions critiques sont auditées ;
- les tests couvrent les scénarios majeurs.
