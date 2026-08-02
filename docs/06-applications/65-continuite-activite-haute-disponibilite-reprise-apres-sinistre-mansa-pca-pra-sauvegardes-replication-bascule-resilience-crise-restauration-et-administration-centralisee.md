# 65 — Continuité d’activité, haute disponibilité et reprise après sinistre Mansa : PCA, PRA, sauvegardes, réplication, bascule, résilience, crise, restauration et administration centralisée

## 1. Objet du document

Ce document définit l’architecture officielle de la **Continuité d’activité, de la Haute Disponibilité et de la Reprise après Sinistre Mansa**.

Ce dispositif doit permettre à Mansa de continuer à fournir ses services essentiels, ou de les rétablir rapidement, lorsqu’un incident grave affecte :

- un service applicatif ;
- une base de données ;
- le ledger ;
- une région cloud ;
- un datacenter ;
- un fournisseur ;
- une banque partenaire ;
- un opérateur Mobile Money ;
- un réseau cartes ;
- le réseau Internet ;
- un TPE ;
- un DAB ;
- une équipe opérationnelle ;
- un bâtiment ;
- un pays ;
- une infrastructure de télécommunication ;
- une alimentation électrique ;
- un certificat ;
- une clé ;
- une sauvegarde ;
- une plateforme critique ;
- un partenaire stratégique.

Le dispositif couvre notamment :

- le Plan de Continuité d’Activité ;
- le Plan de Reprise d’Activité ;
- la haute disponibilité ;
- la réplication ;
- les sauvegardes ;
- les restaurations ;
- les bascules ;
- les modes dégradés ;
- les procédures de crise ;
- les exercices ;
- les communications ;
- les dépendances ;
- les fournisseurs ;
- les équipes ;
- les sites de secours ;
- les objectifs RPO et RTO ;
- les contrôles ;
- les preuves ;
- les audits ;
- l’amélioration continue.

L’objectif est de garantir que les services critiques Mansa restent :

- disponibles ;
- récupérables ;
- sécurisés ;
- cohérents ;
- traçables ;
- protégés contre la perte de données ;
- capables de fonctionner en mode dégradé ;
- capables de basculer vers une infrastructure de secours ;
- capables de revenir vers l’infrastructure principale ;
- adaptés à une exploitation nationale puis régionale.

---

# 2. Principes fondamentaux

## 2.1 La continuité doit être conçue avant la panne

La continuité ne doit pas dépendre d’une improvisation au moment de l’incident.

Chaque service critique doit posséder :

- une classification ;
- un propriétaire ;
- un RPO ;
- un RTO ;
- une architecture de secours ;
- une sauvegarde ;
- un plan de restauration ;
- un plan de bascule ;
- un runbook ;
- des contacts ;
- des tests ;
- des preuves.

---

## 2.2 Le ledger et les données financières sont prioritaires

En cas de crise, la priorité doit être donnée à :

1. l’intégrité du ledger ;
2. la protection des soldes ;
3. l’arrêt des doubles opérations ;
4. la conservation des écritures ;
5. la synchronisation des partenaires ;
6. la reprise des paiements ;
7. la reprise des dépôts et retraits ;
8. la reprise des services secondaires.

---

## 2.3 Une sauvegarde non restaurée n’est pas considérée comme fiable

Une sauvegarde n’est valide que si :

- elle est complète ;
- elle est lisible ;
- elle est chiffrée ;
- elle est accessible ;
- elle peut être restaurée ;
- la restauration a été testée ;
- son contenu a été vérifié ;
- son ancienneté respecte le RPO.

---

## 2.4 La haute disponibilité ne remplace pas la sauvegarde

La réplication protège contre certaines pannes.

Elle ne protège pas toujours contre :

- suppression accidentelle ;
- corruption logique ;
- ransomware ;
- erreur applicative ;
- mauvaise migration ;
- modification malveillante ;
- synchronisation d’une donnée incorrecte.

La réplication et les sauvegardes doivent être complémentaires.

---

## 2.5 Le plan de secours doit rester indépendant

Les sauvegardes et infrastructures de secours ne doivent pas toutes dépendre :

- du même compte cloud ;
- du même fournisseur ;
- de la même région ;
- de la même identité ;
- de la même clé ;
- du même réseau ;
- du même administrateur ;
- du même site physique.

---

## 2.6 Toute bascule doit être contrôlée et réversible

Avant une bascule, il faut connaître :

- la cause ;
- l’impact ;
- la cible ;
- l’état des données ;
- le dernier point cohérent ;
- les risques ;
- le responsable ;
- les utilisateurs affectés ;
- le plan de retour ;
- les contrôles post-bascule.

---

# 3. Périmètre

Le dispositif couvre :

- application Client ;
- application Commerce ;
- application Agent ;
- application TPE ;
- application Admin Lite ;
- site officiel ;
- portails web ;
- API Gateway ;
- services d’identité ;
- ledger ;
- paiements ;
- transferts ;
- dépôts ;
- retraits ;
- cartes ;
- KYC ;
- KYB ;
- notifications ;
- fraude ;
- support ;
- Finance ;
- Data ;
- Jini ;
- bases PostgreSQL ;
- Redis ;
- files de messages ;
- Event Bus ;
- stockage objet ;
- certificats ;
- secrets ;
- DNS ;
- réseau ;
- partenaires ;
- TPE ;
- DAB ;
- Cash Network ;
- équipes ;
- locaux ;
- centres opérationnels ;
- fournisseurs.

---

# 4. Architecture du dispositif

Structure recommandée :

```text
business-continuity/
├── business-impact-analysis/
├── critical-services/
├── continuity-plans/
├── disaster-recovery-plans/
├── backups/
├── replication/
├── failover/
├── failback/
├── crisis-management/
├── degraded-modes/
├── suppliers/
├── communications/
├── exercises/
├── recovery-tests/
├── evidence/
├── reporting/
├── audit/
└── administration/
```

---

# 5. Plan de Continuité d’Activité

Le PCA décrit comment maintenir les fonctions essentielles pendant une perturbation.

Il doit couvrir :

- services prioritaires ;
- équipes minimales ;
- outils de secours ;
- sites alternatifs ;
- procédures manuelles ;
- canaux de communication ;
- accès d’urgence ;
- partenaires ;
- fonctionnement hors ligne ;
- mode dégradé ;
- retour à la normale.

---

# 6. Plan de Reprise d’Activité

Le PRA décrit comment restaurer les systèmes après un sinistre.

Il doit préciser :

- infrastructure cible ;
- ordre de restauration ;
- sauvegardes ;
- réplication ;
- responsables ;
- dépendances ;
- commandes ;
- validations ;
- RPO ;
- RTO ;
- tests ;
- rollback ;
- retour au site principal.

---

# 7. Différence entre PCA et PRA

```text
PCA
→ continuer à fonctionner pendant la crise

PRA
→ restaurer les systèmes après le sinistre
```

Les deux plans doivent être liés.

---

# 8. Business Impact Analysis

L’analyse d’impact métier doit identifier :

- services essentiels ;
- processus critiques ;
- dépendances ;
- volumes ;
- périodes sensibles ;
- risques financiers ;
- risques clients ;
- risques réglementaires ;
- risques réputationnels ;
- durée maximale d’interruption ;
- perte maximale admissible.

---

# 9. Fiche d’un processus critique

Chaque processus doit contenir :

- code ;
- nom ;
- description ;
- propriétaire ;
- pays ;
- utilisateurs ;
- services techniques ;
- partenaires ;
- criticité ;
- MTPD ;
- RPO ;
- RTO ;
- mode dégradé ;
- procédure de reprise ;
- contacts ;
- dernière date de test.

---

# 10. MTPD

Le **Maximum Tolerable Period of Disruption** correspond à la durée maximale pendant laquelle un processus peut rester indisponible avant que l’impact devienne inacceptable.

Exemples de processus :

- autorisation de paiement ;
- consultation du solde ;
- retrait ;
- dépôt ;
- versement de salaires ;
- bourses ;
- règlement commerçant ;
- rapprochement ;
- support ;
- génération de rapports.

---

# 11. Classification de criticité

Niveaux recommandés :

- CRITICAL ;
- HIGH ;
- MEDIUM ;
- LOW.

---

# 12. Services critiques

Exemples :

- authentification ;
- ledger ;
- consultation de solde ;
- paiements ;
- transferts ;
- dépôts ;
- retraits ;
- cartes ;
- prévention des doublons ;
- API Gateway ;
- notifications de sécurité ;
- connecteurs bancaires critiques.

---

# 13. Services importants

Exemples :

- support ;
- portail commerçant ;
- portail agent ;
- rapprochement ;
- règlements ;
- KYC ;
- KYB ;
- rapports opérationnels ;
- gestion TPE ;
- gestion DAB.

---

# 14. Services secondaires

Exemples :

- campagnes marketing ;
- statistiques non temps réel ;
- recommandations ;
- contenus promotionnels ;
- certaines fonctions Jini ;
- exports non urgents ;
- rapports historiques.

---

# 15. RPO

Le Recovery Point Objective définit la perte maximale de données acceptable.

Exemples indicatifs :

- ledger : quasi nul ;
- paiements : très faible ;
- identité : faible ;
- notifications : tolérance modérée ;
- analytics : tolérance plus élevée ;
- contenus marketing : tolérance élevée.

Les valeurs exactes doivent être validées par service.

---

# 16. RTO

Le Recovery Time Objective définit le délai maximal de restauration.

Il doit être calculé selon :

- criticité ;
- impact ;
- capacité technique ;
- coût ;
- partenaires ;
- obligations ;
- utilisateurs ;
- période.

---

# 17. Matrice de criticité

Exemple :

```text
Service                  RPO              RTO
Ledger                   quasi nul        très court
Paiements                très faible      court
Authentification         faible           court
Notifications            modéré           moyen
Analytics                plusieurs heures plusieurs heures
Marketing                un jour          un jour
```

Les valeurs définitives doivent rester administrables.

---

# 18. Dépendances

Chaque service doit déclarer ses dépendances :

- base ;
- cache ;
- queue ;
- réseau ;
- stockage ;
- identité ;
- partenaire ;
- certificat ;
- secret ;
- DNS ;
- fournisseur ;
- équipe ;
- appareil ;
- bâtiment.

---

# 19. Cartographie de dépendances

Exemple :

```text
Paiement
→ API Gateway
→ Authentification
→ Risk Engine
→ Ledger
→ Banque
→ Notification
```

La panne d’une dépendance doit permettre d’identifier les services affectés.

---

# 20. Scénarios de sinistre

Le plan doit couvrir au minimum :

- panne d’une instance ;
- panne d’une zone ;
- panne d’une région ;
- panne cloud ;
- panne base ;
- corruption de base ;
- perte de stockage ;
- suppression accidentelle ;
- ransomware ;
- compromission ;
- perte de clé ;
- expiration de certificat ;
- panne Internet ;
- panne opérateur télécom ;
- panne électrique ;
- panne partenaire ;
- panne réseau cartes ;
- panne Mobile Money ;
- indisponibilité banque ;
- indisponibilité des équipes ;
- perte de bâtiment ;
- catastrophe naturelle ;
- crise nationale ;
- indisponibilité d’un pays.

---

# 21. Panne d’instance

Le système doit pouvoir :

- redémarrer automatiquement ;
- recréer une instance ;
- redistribuer le trafic ;
- vérifier la santé ;
- alerter ;
- conserver les logs ;
- éviter la perte de données.

---

# 22. Panne de zone

Les services critiques doivent pouvoir continuer grâce à :

- plusieurs instances ;
- plusieurs zones ;
- load balancing ;
- réplication ;
- stockage redondé ;
- files persistantes ;
- routage automatique.

---

# 23. Panne de région

Le dispositif doit prévoir :

- région secondaire ;
- réplication inter-région ;
- sauvegardes hors région ;
- DNS de bascule ;
- secrets disponibles ;
- certificats disponibles ;
- images disponibles ;
- procédures de bascule ;
- tests réguliers.

---

# 24. Panne complète du fournisseur cloud

Mansa doit pouvoir restaurer ses services critiques à partir de :

- sauvegardes exportables ;
- infrastructure as code ;
- images ;
- configurations ;
- certificats ;
- secrets protégés ;
- documentation ;
- fournisseur alternatif ;
- infrastructure de secours.

---

# 25. Panne PostgreSQL

Le plan doit couvrir :

- failover vers réplica ;
- promotion d’un secondaire ;
- vérification de réplication ;
- contrôle de cohérence ;
- remise en service ;
- reconnexion des applications ;
- resynchronisation ;
- retour au primaire.

---

# 26. Corruption logique

En cas de corruption :

- isoler la source ;
- arrêter la propagation ;
- identifier le point de restauration ;
- préserver les preuves ;
- restaurer dans un environnement isolé ;
- comparer ;
- rejouer les journaux autorisés ;
- valider les soldes ;
- réconcilier ;
- remettre en Production.

---

# 27. Suppression accidentelle

Le système doit permettre :

- récupération point-in-time ;
- versionnement ;
- restauration ciblée ;
- comparaison ;
- approbation ;
- audit ;
- vérification post-restauration.

---

# 28. Ransomware

Le plan doit prévoir :

- isolement immédiat ;
- révocation des accès ;
- rotation des secrets ;
- arrêt de la propagation ;
- activation des sauvegardes immuables ;
- analyse de sécurité ;
- restauration propre ;
- contrôle d’intégrité ;
- communication ;
- conservation des preuves.

---

# 29. Compromission d’un compte administrateur

Mesures :

- suspension du compte ;
- révocation des sessions ;
- rotation des secrets ;
- revue des actions ;
- comparaison des configurations ;
- vérification des sauvegardes ;
- analyse des accès ;
- restauration éventuelle ;
- notification sécurité ;
- audit.

---

# 30. Perte d’une clé de chiffrement

Le plan doit définir :

- copies sécurisées ;
- sauvegarde HSM ;
- procédure de récupération ;
- approbateurs ;
- rotation ;
- révocation ;
- récupération des données ;
- preuves ;
- audit.

---

# 31. Expiration de certificat

Le système doit :

- surveiller l’expiration ;
- renouveler automatiquement ;
- alerter à l’avance ;
- disposer d’un certificat de secours ;
- permettre une rotation contrôlée ;
- vérifier les partenaires ;
- tester le mTLS.

---

# 32. Panne Internet

Le fonctionnement doit prévoir :

- plusieurs fournisseurs ;
- bascule réseau ;
- liens mobiles ;
- tunnels de secours ;
- files locales ;
- mode hors ligne ;
- synchronisation différée ;
- communication par SMS.

---

# 33. Panne télécom

En cas d’indisponibilité d’un opérateur :

- utiliser un autre opérateur ;
- retarder les notifications non critiques ;
- activer USSD si possible ;
- proposer un canal alternatif ;
- conserver les opérations en attente ;
- informer les utilisateurs ;
- surveiller la reprise.

---

# 34. Panne électrique

Les sites physiques critiques doivent prévoir :

- onduleurs ;
- groupe électrogène ;
- batteries ;
- carburant ;
- maintenance ;
- test de charge ;
- bascule automatique ;
- surveillance ;
- accès sécurisé.

---

# 35. Indisponibilité d’une banque

Le système doit permettre :

- circuit breaker ;
- file d’attente ;
- partenaire alternatif ;
- routage ;
- suspension contrôlée ;
- reprise ;
- rapprochement ;
- communication ;
- résolution des opérations en attente.

---

# 36. Indisponibilité Mobile Money

Le système doit :

- identifier l’opérateur affecté ;
- empêcher les doublons ;
- conserver les références ;
- proposer un autre canal ;
- gérer les opérations en attente ;
- relancer après reprise ;
- rapprocher ;
- informer client et agent.

---

# 37. Indisponibilité réseau cartes

Le plan doit gérer :

- paiement refusé technique ;
- transaction en attente ;
- mode stand-in si autorisé ;
- limites offline ;
- journalisation ;
- reprise ;
- rapprochement ;
- remboursement si nécessaire ;
- communication commerçant.

---

# 38. Indisponibilité des équipes

Le PCA doit prévoir :

- suppléants ;
- rotation ;
- accès distant ;
- documentation ;
- procédures ;
- délégation ;
- équipes multi-sites ;
- contacts secondaires ;
- astreinte ;
- seuil minimal d’effectif.

---

# 39. Perte d’un bâtiment

Le plan doit permettre :

- télétravail ;
- site alternatif ;
- accès distant ;
- redirection des appels ;
- transfert du support ;
- mise à disposition de matériel ;
- accès aux documents ;
- communication interne ;
- sécurité des personnes.

---

# 40. Catastrophe naturelle

Le plan doit prévoir :

- sécurité des employés ;
- évacuation ;
- sites de secours ;
- bascule régionale ;
- communication ;
- coordination locale ;
- priorisation des services ;
- reprise progressive ;
- suivi des partenaires.

---

# 41. Haute disponibilité

Les services critiques doivent être conçus avec :

- plusieurs instances ;
- plusieurs zones ;
- load balancer ;
- réplication ;
- stockage redondé ;
- files persistantes ;
- health checks ;
- autoscaling ;
- failover ;
- monitoring.

---

# 42. Architecture Active/Active

Deux sites ou régions peuvent servir le trafic simultanément.

Avantages :

- meilleure disponibilité ;
- réduction de latence ;
- bascule rapide.

Contraintes :

- cohérence ;
- réplication ;
- conflits ;
- complexité ;
- coût ;
- tests.

---

# 43. Architecture Active/Passive

Un site principal sert le trafic et un site secondaire attend.

Avantages :

- simplicité ;
- coût réduit ;
- contrôle.

Contraintes :

- temps de bascule ;
- risque d’écart ;
- nécessité de tests ;
- risque d’infrastructure froide.

---

# 44. Warm Standby

Le site de secours possède :

- infrastructure active ;
- capacité réduite ;
- données répliquées ;
- services essentiels démarrés ;
- capacité de montée en charge rapide.

---

# 45. Pilot Light

Le site de secours conserve :

- données ;
- configurations ;
- images ;
- services essentiels minimaux.

Les autres composants sont démarrés lors de la crise.

---

# 46. Cold Standby

Le site de secours nécessite une reconstruction.

Cette stratégie convient uniquement aux services non critiques.

---

# 47. Choix de stratégie

La stratégie dépend :

- du RTO ;
- du RPO ;
- du coût ;
- de la criticité ;
- de la réglementation ;
- du volume ;
- des partenaires ;
- de la complexité ;
- du pays.

---

# 48. Réplication

La réplication peut être :

- synchrone ;
- asynchrone ;
- locale ;
- inter-zone ;
- inter-région ;
- continue ;
- programmée.

---

# 49. Réplication synchrone

Elle réduit la perte de données mais peut augmenter :

- latence ;
- dépendance réseau ;
- coût ;
- complexité.

Elle doit être utilisée lorsque le besoin l’exige.

---

# 50. Réplication asynchrone

Elle offre plus de souplesse mais peut provoquer un écart de données.

Le lag doit être :

- surveillé ;
- limité ;
- alerté ;
- pris en compte dans le RPO.

---

# 51. Réplication du ledger

Le ledger doit privilégier :

- intégrité ;
- ordre ;
- unicité ;
- contrôle débit/crédit ;
- journalisation ;
- réplication ;
- récupération point-in-time ;
- rapprochement.

---

# 52. Prévention du split-brain

Le système doit empêcher deux nœuds de devenir simultanément source officielle sans contrôle.

Mesures possibles :

- quorum ;
- fencing ;
- leader election ;
- verrou distribué ;
- témoin ;
- règles de promotion ;
- validation manuelle pour les cas sensibles.

---

# 53. Sauvegardes

Les sauvegardes doivent couvrir :

- bases ;
- ledger ;
- stockage objet ;
- documents ;
- configurations ;
- secrets selon méthode autorisée ;
- certificats ;
- infrastructure as code ;
- référentiels ;
- modèles ;
- logs critiques ;
- données partenaires.

---

# 54. Types de sauvegardes

- complète ;
- incrémentale ;
- différentielle ;
- snapshot ;
- journal transactionnel ;
- point-in-time ;
- immuable ;
- hors ligne ;
- inter-région ;
- hors fournisseur.

---

# 55. Règle 3-2-1

Lorsque possible :

- trois copies ;
- deux supports différents ;
- une copie hors site.

Pour les services les plus critiques, une copie immuable supplémentaire doit être prévue.

---

# 56. Sauvegardes immuables

Elles doivent être protégées contre :

- modification ;
- suppression ;
- ransomware ;
- compte administrateur compromis ;
- erreur humaine ;
- rétention réduite sans approbation.

---

# 57. Chiffrement des sauvegardes

Les sauvegardes doivent être chiffrées :

- au repos ;
- en transit ;
- avec gestion de clés ;
- avec rotation ;
- avec contrôle d’accès ;
- avec audit.

---

# 58. Index des sauvegardes

Chaque sauvegarde doit contenir :

- identifiant ;
- ressource ;
- date ;
- heure ;
- type ;
- taille ;
- emplacement ;
- hash ;
- chiffrement ;
- statut ;
- expiration ;
- test de restauration ;
- propriétaire.

---

# 59. Statuts de sauvegarde

- SCHEDULED ;
- RUNNING ;
- COMPLETED ;
- PARTIAL ;
- FAILED ;
- CORRUPTED ;
- EXPIRED ;
- DELETED ;
- RESTORED.

---

# 60. Fréquence

La fréquence doit dépendre :

- du RPO ;
- du service ;
- du volume ;
- du coût ;
- de la criticité ;
- du type de données ;
- de la réglementation.

---

# 61. Rétention

La rétention peut inclure :

- quotidien ;
- hebdomadaire ;
- mensuel ;
- annuel ;
- réglementaire ;
- légal ;
- archivage long terme.

---

# 62. Suppression des sauvegardes

La suppression doit être :

- autorisée ;
- planifiée ;
- auditée ;
- compatible avec les obligations ;
- empêchée pendant une enquête ;
- soumise à double validation pour les sauvegardes critiques.

---

# 63. Monitoring des sauvegardes

Le système doit surveiller :

- échec ;
- retard ;
- durée ;
- taille ;
- couverture ;
- ancienneté ;
- réplication ;
- chiffrement ;
- espace ;
- test de restauration ;
- conformité au RPO.

---

# 64. Restauration

Une restauration peut être :

- complète ;
- partielle ;
- ciblée ;
- point-in-time ;
- dans un environnement isolé ;
- sur infrastructure principale ;
- sur infrastructure de secours.

---

# 65. Processus de restauration

Exemple :

1. déclarer la restauration ;
2. identifier la sauvegarde ;
3. vérifier l’intégrité ;
4. valider le point de restauration ;
5. isoler l’environnement ;
6. restaurer ;
7. contrôler les données ;
8. rejouer les journaux autorisés ;
9. rapprocher ;
10. approuver ;
11. remettre en service ;
12. surveiller.

---

# 66. Restauration isolée

Toute restauration critique doit d’abord pouvoir être exécutée dans un environnement isolé pour :

- éviter la contamination ;
- comparer les données ;
- vérifier l’intégrité ;
- rechercher la cause ;
- valider la cohérence ;
- préparer la remise en service.

---

# 67. Contrôles post-restauration

Ils doivent vérifier :

- comptes ;
- soldes ;
- écritures ;
- transactions ;
- utilisateurs ;
- permissions ;
- partenaires ;
- files ;
- documents ;
- horodatages ;
- rapports ;
- réconciliation.

---

# 68. Point-in-Time Recovery

Le système doit permettre, lorsque techniquement possible, de restaurer une base à un instant donné.

Cela nécessite :

- sauvegarde de base ;
- journaux ;
- horodatage ;
- rétention ;
- capacité de rejeu ;
- tests.

---

# 69. Bascule

La bascule peut être :

- automatique ;
- semi-automatique ;
- manuelle ;
- applicative ;
- base de données ;
- réseau ;
- région ;
- partenaire ;
- DNS.

---

# 70. Critères de bascule

Exemples :

- région indisponible ;
- base irrécupérable ;
- taux d’erreur critique ;
- perte réseau ;
- partenaire principal indisponible ;
- corruption ;
- attaque ;
- incident physique ;
- RTO en danger.

---

# 71. Autorité de bascule

La décision peut appartenir à :

- Incident Commander ;
- Responsable Infrastructure ;
- Responsable Base ;
- Responsable Sécurité ;
- Responsable Finance ;
- Direction technique ;
- comité de crise.

Le niveau dépend de la criticité.

---

# 72. Checklist de bascule

- incident déclaré ;
- impact identifié ;
- données vérifiées ;
- destination prête ;
- secrets disponibles ;
- certificats valides ;
- DNS prêt ;
- partenaires informés ;
- équipes mobilisées ;
- rollback défini ;
- communication préparée ;
- approbation obtenue.

---

# 73. Bascule DNS

La bascule DNS doit gérer :

- TTL ;
- propagation ;
- cache ;
- certificat ;
- santé cible ;
- surveillance ;
- retour ;
- validation depuis plusieurs régions.

---

# 74. Bascule base de données

Elle doit inclure :

- arrêt des écritures si nécessaire ;
- vérification du lag ;
- promotion ;
- protection contre split-brain ;
- reconnexion ;
- validation ;
- surveillance ;
- réconciliation.

---

# 75. Bascule partenaire

Le système peut rediriger vers :

- banque secondaire ;
- fournisseur SMS secondaire ;
- opérateur Mobile Money secondaire ;
- fournisseur cloud secondaire ;
- moteur IA secondaire ;
- service KYC secondaire.

---

# 76. Retour vers le site principal

Le failback doit être planifié.

Il comprend :

- vérification du site principal ;
- synchronisation ;
- gel des écritures si nécessaire ;
- comparaison ;
- bascule ;
- validation ;
- surveillance ;
- retour des équipes ;
- clôture.

---

# 77. Mode dégradé

Le système doit pouvoir maintenir les fonctions essentielles en réduisant ou suspendant :

- analytics ;
- campagnes ;
- recommandations ;
- rapports lourds ;
- médias ;
- certaines fonctions Jini ;
- fonctions non essentielles ;
- exports ;
- notifications non urgentes.

---

# 78. Priorisation en mode dégradé

Ordre recommandé :

1. sécurité ;
2. authentification ;
3. ledger ;
4. consultation du solde ;
5. paiements essentiels ;
6. transferts essentiels ;
7. dépôts et retraits ;
8. notifications de sécurité ;
9. support ;
10. services secondaires.

---

# 79. Mode lecture seule

Le mode lecture seule peut être activé lorsque :

- l’intégrité des écritures est incertaine ;
- la base primaire est indisponible ;
- une migration est en cours ;
- un incident ledger existe ;
- le risque de double écriture est élevé.

---

# 80. Mode file d’attente

Lorsqu’un partenaire est indisponible :

- conserver la demande ;
- attribuer une référence ;
- empêcher le doublon ;
- informer l’utilisateur ;
- relancer ;
- expirer si nécessaire ;
- rapprocher après reprise.

---

# 81. Mode hors ligne TPE

Le mode hors ligne doit être strictement encadré par :

- commerçant ;
- pays ;
- type de carte ;
- montant ;
- cumul ;
- durée ;
- risque ;
- liste noire locale ;
- clé ;
- synchronisation ;
- règles d’acceptation.

---

# 82. Mode hors ligne Agent

Pour les agents, le système peut autoriser uniquement des fonctions limitées :

- consultation locale non garantie ;
- brouillon ;
- file d’attente ;
- reçu provisoire ;
- préparation d’opération.

Les opérations financières finales doivent respecter les règles définies.

---

# 83. Mode hors ligne DAB

Le DAB ne doit pas débiter ou délivrer des espèces sans règles d’autorisation sûres.

Tout mode hors ligne doit être :

- explicitement autorisé ;
- limité ;
- journalisé ;
- contrôlé ;
- synchronisé ;
- audité.

---

# 84. Cohérence des opérations en attente

Chaque opération doit avoir un état clair :

- créée ;
- envoyée ;
- reçue ;
- autorisée ;
- comptabilisée ;
- terminée ;
- échouée ;
- expirée ;
- annulée ;
- en rapprochement.

---

# 85. Rejeu des événements

Le système doit permettre de rejouer certains événements sans provoquer :

- double paiement ;
- double écriture ;
- double notification critique ;
- double commission ;
- double règlement.

L’idempotence est obligatoire.

---

# 86. Dead Letter Queue

Les événements non traitables doivent être placés dans une file dédiée avec :

- raison ;
- date ;
- payload masqué ;
- service ;
- retry ;
- propriétaire ;
- incident ;
- action.

---

# 87. Réconciliation après sinistre

Après reprise, il faut vérifier :

- ledger ;
- banques ;
- Mobile Money ;
- réseaux cartes ;
- agents ;
- commerçants ;
- TPE ;
- DAB ;
- notifications ;
- règlements ;
- commissions ;
- suspenses.

---

# 88. Écarts après reprise

Un écart doit créer :

- dossier ;
- référence ;
- source ;
- montant ;
- cause ;
- statut ;
- responsable ;
- action ;
- preuve ;
- résolution.

---

# 89. Communication de crise

La communication doit couvrir :

- équipes ;
- direction ;
- clients ;
- commerçants ;
- agents ;
- partenaires ;
- institutions ;
- régulateurs ;
- fournisseurs ;
- médias lorsque nécessaire.

---

# 90. Message interne

Il doit préciser :

- incident ;
- impact ;
- services ;
- pays ;
- début ;
- statut ;
- actions ;
- prochaine mise à jour ;
- responsables ;
- consignes.

---

# 91. Message client

Le message doit être :

- clair ;
- précis ;
- sans jargon ;
- factuel ;
- rassurant ;
- traduit ;
- adapté au canal ;
- mis à jour.

---

# 92. Communication partenaire

Elle doit inclure :

- référence ;
- environnement ;
- endpoints ;
- opérations affectées ;
- données attendues ;
- actions ;
- contacts ;
- heure de prochaine mise à jour.

---

# 93. Communication réglementaire

La notification peut dépendre :

- du pays ;
- du type d’incident ;
- de la durée ;
- des données ;
- du montant ;
- des utilisateurs ;
- de la sécurité ;
- des obligations contractuelles.

---

# 94. Comité de crise

Le comité peut inclure :

- direction générale ;
- direction technique ;
- sécurité ;
- opérations ;
- Finance ;
- juridique ;
- conformité ;
- communication ;
- partenaires ;
- pays ;
- continuité d’activité.

---

# 95. Rôles de crise

Exemples :

```text
CRISIS_DIRECTOR
INCIDENT_COMMANDER
TECHNICAL_RECOVERY_LEAD
BUSINESS_CONTINUITY_MANAGER
SECURITY_LEAD
FINANCE_LEAD
COMMUNICATIONS_LEAD
LEGAL_LEAD
PARTNER_COORDINATOR
COUNTRY_MANAGER
SCRIBE
```

---

# 96. Centre de crise

Le centre doit permettre :

- réunion ;
- canal dédié ;
- chronologie ;
- tâches ;
- documents ;
- contacts ;
- décisions ;
- communications ;
- preuves ;
- clôture.

---

# 97. Déclenchement du PCA

Le PCA peut être déclenché lorsque :

- un site est indisponible ;
- une équipe ne peut plus travailler ;
- une infrastructure est fortement dégradée ;
- un fournisseur critique est indisponible ;
- une crise nationale affecte les opérations ;
- la durée estimée dépasse un seuil ;
- la sécurité l’exige.

---

# 98. Déclenchement du PRA

Le PRA peut être déclenché lorsque :

- la restauration normale est insuffisante ;
- un site principal est perdu ;
- une région est indisponible ;
- une base est corrompue ;
- le RTO est menacé ;
- une reconstruction complète est nécessaire.

---

# 99. Statuts d’un plan

- DRAFT ;
- REVIEW ;
- APPROVED ;
- ACTIVE ;
- TESTING ;
- INVOKED ;
- SUSPENDED ;
- DEPRECATED ;
- ARCHIVED.

---

# 100. Activation d’un plan

L’activation doit enregistrer :

- plan ;
- incident ;
- date ;
- heure ;
- déclencheur ;
- décisionnaire ;
- pays ;
- services ;
- équipes ;
- statut ;
- preuves ;
- résultat.

---

# 101. Exercices

Types d’exercice :

- revue documentaire ;
- tabletop ;
- simulation ;
- test technique ;
- test de restauration ;
- test de bascule ;
- test régional ;
- test fournisseur ;
- test surprise contrôlé ;
- exercice complet.

---

# 102. Exercice Tabletop

Les équipes simulent un incident sans couper les systèmes réels.

L’exercice doit tester :

- rôles ;
- décisions ;
- communication ;
- procédures ;
- escalade ;
- dépendances ;
- documents ;
- compréhension.

---

# 103. Test de restauration

Il doit vérifier :

- sauvegarde ;
- accès ;
- clés ;
- durée ;
- intégrité ;
- application ;
- données ;
- cohérence ;
- RPO ;
- RTO.

---

# 104. Test de bascule

Il doit vérifier :

- infrastructure de secours ;
- réseau ;
- DNS ;
- secrets ;
- certificats ;
- bases ;
- files ;
- applications ;
- partenaires ;
- surveillance ;
- retour.

---

# 105. Fréquence des tests

La fréquence peut dépendre de la criticité.

Exemple :

- restauration critique : régulière ;
- bascule régionale : périodique ;
- exercice de crise : annuel ou semestriel ;
- sauvegarde : contrôle continu ;
- plan : revue après chaque changement majeur.

---

# 106. Résultat d’un exercice

Il doit contenir :

- scénario ;
- participants ;
- objectif ;
- début ;
- fin ;
- étapes ;
- résultats ;
- écarts ;
- RPO atteint ;
- RTO atteint ;
- difficultés ;
- actions ;
- responsables ;
- échéances.

---

# 107. Échec d’un test

Un test échoué doit créer :

- incident ou problème ;
- action corrective ;
- responsable ;
- date cible ;
- nouveau test ;
- preuve de résolution ;
- escalade si critique.

---

# 108. Preuves

Les preuves peuvent inclure :

- captures ;
- logs ;
- rapports ;
- hashes ;
- métriques ;
- temps ;
- commandes ;
- validations ;
- documents ;
- approbations ;
- résultats de comparaison.

---

# 109. Documentation

Chaque plan doit contenir :

- périmètre ;
- responsables ;
- architecture ;
- dépendances ;
- scénarios ;
- procédures ;
- contacts ;
- accès ;
- sauvegardes ;
- RPO ;
- RTO ;
- communication ;
- retour à la normale ;
- date de test ;
- version.

---

# 110. Contacts d’urgence

Les contacts doivent être :

- à jour ;
- testés ;
- disponibles hors système principal ;
- accessibles hors ligne ;
- classés par rôle ;
- classés par pays ;
- doublés par un remplaçant.

---

# 111. Documentation hors ligne

Une copie sécurisée doit être disponible hors ligne pour :

- plans ;
- contacts ;
- procédures ;
- architecture ;
- certificats de secours selon règles ;
- informations de connexion d’urgence ;
- checklists.

---

# 112. Fournisseurs critiques

Chaque fournisseur critique doit posséder :

- contrat ;
- SLA ;
- contacts ;
- escalade ;
- plan de continuité ;
- site de secours ;
- tests ;
- historique ;
- dépendances ;
- solution alternative.

---

# 113. Évaluation d’un fournisseur

Critères :

- disponibilité ;
- résilience ;
- sécurité ;
- localisation ;
- sauvegardes ;
- reprise ;
- communication ;
- performance ;
- historique ;
- dépendance unique ;
- capacité financière.

---

# 114. Partenaire unique

Lorsqu’un seul partenaire existe, Mansa doit documenter :

- risque ;
- impact ;
- solution temporaire ;
- délai ;
- plan d’alternative ;
- dépendance ;
- acceptation du risque ;
- responsable.

---

# 115. Multi-fournisseurs

Pour certains services, prévoir plusieurs fournisseurs :

- SMS ;
- e-mail ;
- cloud ;
- réseau ;
- KYC ;
- IA ;
- Mobile Money ;
- banque ;
- stockage ;
- DNS.

---

# 116. Continuité du Cash Network

Le dispositif doit couvrir :

- agents indisponibles ;
- zones sans liquidité ;
- panne Mobile Money ;
- panne banque ;
- perte de connexion ;
- fermeture d’agence ;
- transport d’espèces ;
- réapprovisionnement ;
- DAB indisponible ;
- communication.

---

# 117. Continuité des agents

Le système doit permettre :

- redirection vers un autre agent ;
- carte des agents actifs ;
- alerte de liquidité ;
- rééquilibrage ;
- remplacement ;
- suspension temporaire ;
- reprise ;
- historique.

---

# 118. Continuité des DAB

Le plan doit couvrir :

- DAB hors ligne ;
- panne réseau ;
- panne électrique ;
- cassette vide ;
- carte retenue ;
- billets non délivrés ;
- incident physique ;
- maintenance ;
- remplacement ;
- surveillance.

---

# 119. Continuité des TPE

Le plan doit couvrir :

- panne terminal ;
- panne application ;
- panne NFC ;
- panne imprimante ;
- panne réseau ;
- mise à jour échouée ;
- remplacement ;
- mode hors ligne autorisé ;
- support commerçant.

---

# 120. Continuité du support

Le support doit pouvoir basculer vers :

- autre site ;
- télétravail ;
- autre numéro ;
- autre canal ;
- équipe de secours ;
- messagerie ;
- formulaire ;
- support prioritaire.

---

# 121. Continuité de la Finance

Les fonctions prioritaires sont :

- contrôle des soldes ;
- rapprochement ;
- règlements ;
- suspenses ;
- liquidité ;
- cantonnement ;
- écritures ;
- rapports critiques ;
- validation.

---

# 122. Continuité de la sécurité

La sécurité doit maintenir :

- détection ;
- alertes ;
- authentification ;
- MFA ;
- révocation ;
- surveillance ;
- investigations ;
- collecte de preuves ;
- réponse à incident.

---

# 123. Continuité Data

La plateforme Data peut fonctionner en mode retardé.

Priorités :

- conserver les événements ;
- éviter la perte ;
- reprendre les pipelines ;
- vérifier les doublons ;
- restaurer les rapports critiques ;
- reconstruire les agrégats.

---

# 124. Continuité Jini

Jini peut basculer vers :

- modèle secondaire ;
- fournisseur secondaire ;
- mode limité ;
- FAQ locale ;
- réponses prévalidées ;
- transfert humain ;
- désactivation des outils sensibles.

---

# 125. Continuité des notifications

Le système doit :

- prioriser sécurité et OTP ;
- basculer de fournisseur ;
- conserver les messages ;
- réessayer ;
- utiliser un canal alternatif ;
- limiter le marketing ;
- surveiller les coûts ;
- rapprocher les statuts.

---

# 126. Continuité des environnements

Les environnements non Production peuvent être réduits ou arrêtés pendant une crise afin de préserver :

- capacité ;
- budget ;
- personnel ;
- réseau ;
- stockage ;
- attention opérationnelle.

---

# 127. Administration centrale

L’administration doit permettre de gérer :

- processus critiques ;
- plans PCA ;
- plans PRA ;
- RPO ;
- RTO ;
- MTPD ;
- sauvegardes ;
- restaurations ;
- réplication ;
- sites de secours ;
- bascules ;
- modes dégradés ;
- exercices ;
- fournisseurs ;
- communications ;
- contacts ;
- preuves ;
- actions ;
- audits.

---

# 128. Rôles

Exemples :

```text
BUSINESS_CONTINUITY_MANAGER
DISASTER_RECOVERY_MANAGER
CRISIS_DIRECTOR
TECHNICAL_RECOVERY_LEAD
BACKUP_ADMIN
DATABASE_RECOVERY_ADMIN
NETWORK_RECOVERY_ADMIN
APPLICATION_RECOVERY_OWNER
SECURITY_RECOVERY_LEAD
COUNTRY_CONTINUITY_MANAGER
SUPPLIER_CONTINUITY_MANAGER
AUDITOR
VIEWER
```

---

# 129. Permissions

Exemples :

```text
continuity.plan.read
continuity.plan.manage
continuity.plan.approve
continuity.plan.invoke
continuity.backup.read
continuity.backup.manage
continuity.restore.request
continuity.restore.execute
continuity.failover.request
continuity.failover.approve
continuity.failover.execute
continuity.exercise.manage
continuity.evidence.read
continuity.supplier.manage
continuity.audit.read
```

---

# 130. Approbations

Peuvent nécessiter une approbation :

- activation PRA ;
- restauration Production ;
- bascule régionale ;
- suppression de sauvegarde ;
- modification RPO ;
- modification RTO ;
- modification d’un plan critique ;
- activation du mode lecture seule ;
- retour vers le site principal ;
- utilisation d’une sauvegarde sensible.

---

# 131. Double validation

Peut être exigée pour :

- restauration du ledger ;
- promotion d’une base ;
- bascule globale ;
- suppression d’une sauvegarde immuable ;
- récupération d’une clé ;
- retour après sinistre ;
- activation d’un plan national ;
- modification d’un RPO critique ;
- arrêt prolongé d’un service financier.

---

# 132. Séparation des rôles

Exemple :

```text
Équipe technique prépare
→ Responsable continuité vérifie
→ Direction autorise
→ Opérateur exécute
→ Auditeur contrôle
```

Le même utilisateur ne doit pas approuver et exécuter seul une opération critique.

---

# 133. API

Exemples :

```http
GET    /continuity/processes
POST   /continuity/processes

GET    /continuity/plans
POST   /continuity/plans
POST   /continuity/plans/{id}/approve
POST   /continuity/plans/{id}/invoke

GET    /continuity/backups
POST   /continuity/backups/run

GET    /continuity/restores
POST   /continuity/restores
POST   /continuity/restores/{id}/approve
POST   /continuity/restores/{id}/execute

GET    /continuity/failovers
POST   /continuity/failovers
POST   /continuity/failovers/{id}/execute

GET    /continuity/exercises
POST   /continuity/exercises

GET    /continuity/suppliers
GET    /continuity/reports
GET    /continuity/audit
```

---

# 134. Webhooks internes

Événements possibles :

```text
continuity.plan.approved
continuity.plan.invoked
continuity.backup.started
continuity.backup.completed
continuity.backup.failed
continuity.restore.requested
continuity.restore.completed
continuity.failover.started
continuity.failover.completed
continuity.failback.completed
continuity.rpo.breached
continuity.rto.breached
continuity.exercise.completed
continuity.exercise.failed
continuity.supplier.degraded
continuity.security.alert
```

---

# 135. Modèles principaux

- BusinessProcess
- BusinessImpactAnalysis
- CriticalService
- ContinuityPlan
- DisasterRecoveryPlan
- RecoveryObjective
- Dependency
- RecoverySite
- ReplicationConfiguration
- BackupPolicy
- BackupExecution
- BackupArtifact
- RestoreRequest
- RestoreExecution
- FailoverPlan
- FailoverExecution
- FailbackExecution
- DegradedMode
- CrisisActivation
- CrisisTeam
- CrisisCommunication
- ContinuityExercise
- ExerciseResult
- RecoveryTest
- SupplierContinuityProfile
- ContinuityEvidence
- CorrectiveAction
- ContinuityApproval
- ContinuityAudit

---

# 136. Analytics

Événements possibles :

```text
continuity_dashboard_opened
continuity_plan_created
continuity_plan_approved
continuity_plan_invoked
continuity_backup_failed
continuity_restore_requested
continuity_restore_completed
continuity_failover_started
continuity_failover_completed
continuity_exercise_started
continuity_exercise_completed
continuity_rpo_breached
continuity_rto_breached
continuity_action_overdue
```

---

# 137. Données analytics interdites

Ne pas transmettre :

- contenu de sauvegarde ;
- données clients ;
- clés ;
- secrets ;
- mots de passe ;
- numéros de carte ;
- documents ;
- contenu financier détaillé ;
- commandes sensibles ;
- plans complets contenant des accès ;
- informations de sécurité exploitables.

---

# 138. Audit

Le journal doit contenir :

- utilisateur ;
- rôle ;
- plan ;
- sauvegarde ;
- restauration ;
- bascule ;
- service ;
- pays ;
- environnement ;
- date ;
- heure ;
- approbateur ;
- exécutant ;
- motif ;
- résultat ;
- preuve ;
- incident lié.

---

# 139. Immutabilité des audits

Les audits doivent être protégés contre :

- modification ;
- suppression ;
- réécriture ;
- désactivation ;
- remplacement ;
- export sans permission.

---

# 140. Reporting

Rapports possibles :

- couverture PCA ;
- couverture PRA ;
- conformité RPO ;
- conformité RTO ;
- sauvegardes réussies ;
- restaurations testées ;
- bascules testées ;
- exercices réalisés ;
- fournisseurs critiques ;
- actions en retard ;
- risques ouverts ;
- capacité de reprise.

---

# 141. Indicateurs

Exemples :

- taux de services couverts ;
- taux de plans à jour ;
- taux de sauvegardes réussies ;
- taux de restaurations réussies ;
- délai moyen de restauration ;
- RPO réellement atteint ;
- RTO réellement atteint ;
- nombre de tests ;
- nombre d’échecs ;
- actions ouvertes ;
- fournisseurs sans plan.

---

# 142. Revue périodique

Les plans doivent être revus :

- périodiquement ;
- après incident ;
- après migration ;
- après changement fournisseur ;
- après changement d’architecture ;
- après ouverture d’un pays ;
- après changement réglementaire ;
- après exercice échoué.

---

# 143. Gestion des versions

Chaque plan doit conserver :

- version ;
- auteur ;
- approbateur ;
- date ;
- changements ;
- services ;
- pays ;
- RPO ;
- RTO ;
- statut ;
- date d’effet.

---

# 144. Statuts d’une action corrective

- OPEN ;
- PLANNED ;
- IN_PROGRESS ;
- BLOCKED ;
- COMPLETED ;
- VERIFIED ;
- CANCELLED.

---

# 145. Tests

- tests PCA ;
- tests PRA ;
- tests BIA ;
- tests MTPD ;
- tests RPO ;
- tests RTO ;
- tests de criticité ;
- tests de dépendances ;
- tests Active/Active ;
- tests Active/Passive ;
- tests réplication ;
- tests split-brain ;
- tests sauvegardes ;
- tests sauvegardes immuables ;
- tests chiffrement ;
- tests restauration ;
- tests point-in-time ;
- tests bascule ;
- tests failback ;
- tests DNS ;
- tests bases ;
- tests réseau ;
- tests cloud ;
- tests perte de région ;
- tests ransomware ;
- tests suppression accidentelle ;
- tests corruption ;
- tests clés ;
- tests certificats ;
- tests partenaires ;
- tests télécom ;
- tests électrique ;
- tests équipes ;
- tests bâtiment ;
- tests mode dégradé ;
- tests lecture seule ;
- tests file d’attente ;
- tests offline TPE ;
- tests offline Agent ;
- tests DAB ;
- tests réconciliation ;
- tests communication ;
- tests comité de crise ;
- tests exercices ;
- tests fournisseurs ;
- tests multi-pays ;
- tests accès ;
- tests approbations ;
- tests audit ;
- tests performance.

---

# 146. Règles métier

1. Chaque service critique possède un RPO.
2. Chaque service critique possède un RTO.
3. Chaque processus critique possède un MTPD.
4. Chaque plan possède un propriétaire.
5. La haute disponibilité ne remplace pas la sauvegarde.
6. Les sauvegardes critiques sont chiffrées.
7. Les sauvegardes critiques sont testées.
8. Les sauvegardes immuables sont protégées.
9. Les restaurations sont exécutables.
10. Les bascules sont documentées.
11. Les bascules critiques sont approuvées.
12. Le split-brain est empêché.
13. Le ledger reste prioritaire.
14. Les opérations en attente sont idempotentes.
15. Le mode dégradé protège les fonctions essentielles.
16. Le mode lecture seule peut protéger l’intégrité.
17. Les partenaires critiques possèdent un plan.
18. Les contacts d’urgence sont maintenus.
19. Les plans sont disponibles hors ligne.
20. Les exercices produisent des actions.
21. Les échecs de test sont corrigés.
22. Le retour au site principal est planifié.
23. Les preuves sont conservées.
24. Le demandeur ne valide pas seul une action critique.
25. Les audits sont immuables.

---

# 147. Critères d’acceptation

Le dispositif de Continuité d’activité, Haute Disponibilité et Reprise après Sinistre Mansa est validé lorsque :

- les processus critiques sont identifiés ;
- la BIA est disponible ;
- les MTPD sont définis ;
- les RPO sont définis ;
- les RTO sont définis ;
- les dépendances sont cartographiées ;
- les scénarios de sinistre sont documentés ;
- la panne d’instance est couverte ;
- la panne de zone est couverte ;
- la panne de région est couverte ;
- la panne cloud est couverte ;
- la panne PostgreSQL est couverte ;
- la corruption logique est couverte ;
- la suppression accidentelle est couverte ;
- le ransomware est couvert ;
- la compromission d’un administrateur est couverte ;
- la perte de clé est couverte ;
- l’expiration de certificat est couverte ;
- la panne Internet est couverte ;
- la panne télécom est couverte ;
- la panne électrique est couverte ;
- la panne bancaire est couverte ;
- la panne Mobile Money est couverte ;
- la panne réseau cartes est couverte ;
- l’indisponibilité des équipes est couverte ;
- la perte d’un bâtiment est couverte ;
- la haute disponibilité est définie ;
- les stratégies Active/Active et Active/Passive sont évaluées ;
- la réplication est surveillée ;
- le split-brain est empêché ;
- le ledger est sauvegardé ;
- les sauvegardes suivent une politique ;
- les sauvegardes immuables sont disponibles ;
- les sauvegardes sont chiffrées ;
- les restaurations sont testées ;
- la restauration isolée fonctionne ;
- les contrôles post-restauration existent ;
- le point-in-time recovery est disponible lorsque requis ;
- les bascules sont documentées ;
- les bascules DNS sont testées ;
- les bascules de bases sont testées ;
- les partenaires secondaires sont prévus lorsque possible ;
- le failback est documenté ;
- le mode dégradé est défini ;
- le mode lecture seule est disponible ;
- les files d’attente sont idempotentes ;
- le mode hors ligne TPE est encadré ;
- le mode hors ligne Agent est limité ;
- le DAB respecte les règles de sécurité ;
- la réconciliation après sinistre est définie ;
- la communication de crise est prête ;
- le comité de crise est défini ;
- le PCA peut être activé ;
- le PRA peut être activé ;
- les exercices sont planifiés ;
- les restaurations sont régulièrement testées ;
- les bascules sont régulièrement testées ;
- les échecs de tests produisent des actions ;
- les contacts d’urgence sont disponibles ;
- les plans existent hors ligne ;
- les fournisseurs critiques sont évalués ;
- le Cash Network possède un plan ;
- les TPE et DAB possèdent un plan ;
- le support possède un plan ;
- Finance possède un plan ;
- Sécurité possède un plan ;
- Data possède un plan ;
- Jini possède un plan ;
- les notifications possèdent un plan ;
- les rôles et permissions sont définis ;
- les actions critiques nécessitent une approbation ;
- les rapports de continuité sont disponibles ;
- les plans sont versionnés ;
- les audits sont immuables ;
- les tests couvrent les parcours essentiels.
