# 30 — Gestion des coûts techniques, capacité, performance et montée en charge de Mansa

## 1. Objet du document

Ce document définit la stratégie officielle de maîtrise des coûts techniques et de capacité de Mansa.

Il couvre :

- les coûts cloud ;
- les coûts de base de données ;
- les coûts réseau ;
- les coûts de stockage ;
- les coûts d’observabilité ;
- les coûts de sauvegarde ;
- les coûts de sécurité ;
- les coûts des partenaires ;
- les coûts Mobile Money ;
- les coûts des réseaux cartes ;
- les coûts SMS ;
- les coûts e-mail ;
- les coûts Push ;
- les coûts Jini ;
- les coûts de traitement documentaire ;
- les coûts des TPE ;
- les coûts par application ;
- les coûts par pays ;
- la capacité ;
- la prévision ;
- l’autoscaling ;
- la performance ;
- la montée en charge ;
- les limites ;
- les budgets ;
- les alertes ;
- l’optimisation ;
- la répartition des coûts ;
- la rentabilité technique.

L’objectif est de permettre à Mansa de croître sans :

- perdre le contrôle de ses dépenses ;
- surdimensionner inutilement son infrastructure ;
- sous-dimensionner les services critiques ;
- dégrader les performances ;
- bloquer les paiements ;
- dépendre d’un fournisseur trop coûteux ;
- créer des coûts invisibles ;
- subir une facture imprévue ;
- rendre un service non rentable.

---

# 2. Principes fondamentaux

## 2.1 Chaque coût doit avoir un propriétaire

Toute dépense importante doit être rattachée à :

- un service ;
- une application ;
- un pays ;
- un environnement ;
- un partenaire ;
- une équipe ;
- un produit ;
- un centre de coût ;
- un responsable.

Une dépense sans propriétaire doit être considérée comme un problème de gouvernance.

---

## 2.2 Les coûts doivent être mesurés avant d’être optimisés

Mansa ne doit pas réduire les coûts à l’aveugle.

Avant toute optimisation, il faut connaître :

- le coût actuel ;
- le service concerné ;
- le volume ;
- l’usage ;
- la criticité ;
- l’impact utilisateur ;
- la marge ;
- le risque ;
- l’évolution prévue.

---

## 2.3 La réduction des coûts ne doit pas compromettre la sécurité

Il est interdit de réduire les coûts en supprimant sans analyse :

- sauvegardes ;
- chiffrement ;
- redondance critique ;
- monitoring ;
- audit ;
- protections réseau ;
- tests ;
- reprise ;
- conservation réglementaire.

---

## 2.4 La capacité doit précéder la croissance

Avant une campagne, un lancement national ou un partenariat avec l’État, Mansa doit estimer :

- le nombre d’utilisateurs ;
- le nombre de transactions ;
- les pics ;
- le volume de données ;
- le nombre de TPE ;
- les appels partenaires ;
- les notifications ;
- la charge de support ;
- la capacité de la base ;
- la capacité des files ;
- les coûts associés.

---

## 2.5 Les services critiques doivent conserver une marge de sécurité

Les services financiers ne doivent pas fonctionner constamment à leur capacité maximale.

Une marge doit être prévue pour :

- les pics ;
- les incidents ;
- les retries ;
- les campagnes ;
- les pannes partenaires ;
- les traitements de rattrapage ;
- les rapprochements ;
- les bascules.

---

# 3. Périmètre des coûts

Les coûts techniques de Mansa peuvent inclure :

- hébergement backend ;
- conteneurs ;
- serveurs ;
- fonctions serverless ;
- PostgreSQL ;
- Redis ;
- brokers ;
- stockage objet ;
- CDN ;
- DNS ;
- certificats ;
- monitoring ;
- logs ;
- traces ;
- sauvegardes ;
- réseau sortant ;
- stockage froid ;
- CI/CD ;
- registres d’images ;
- sécurité ;
- scans ;
- outils de support ;
- services d’IA ;
- OCR ;
- vérification d’identité ;
- SMS ;
- e-mail ;
- Push ;
- cartographie ;
- géolocalisation ;
- Mobile Money ;
- banques ;
- Visa ;
- Mastercard ;
- TPE ;
- licences ;
- assistance fournisseur.

---

# 4. Catégories de coûts

## 4.1 Coûts fixes

Exemples :

- abonnement mensuel ;
- réserve minimale ;
- licence ;
- environnement permanent ;
- support entreprise ;
- coût de certification ;
- maintenance TPE ;
- contrat partenaire.

---

## 4.2 Coûts variables

Exemples :

- nombre de transactions ;
- volume SMS ;
- volume de stockage ;
- appels KYC ;
- appels Jini ;
- trafic réseau ;
- nombre d’utilisateurs actifs ;
- nombre de documents traités ;
- volume de logs ;
- nombre de TPE actifs.

---

## 4.3 Coûts exceptionnels

Exemples :

- migration ;
- incident ;
- audit ;
- certification ;
- campagne nationale ;
- charge exceptionnelle ;
- double hébergement ;
- reprise ;
- test de charge ;
- changement de fournisseur.

---

# 5. Répartition des coûts

Les coûts doivent pouvoir être analysés par :

- application ;
- service ;
- domaine ;
- pays ;
- environnement ;
- partenaire ;
- organisation ;
- produit ;
- type d’utilisateur ;
- canal ;
- transaction ;
- devise ;
- période.

---

# 6. Tags de coûts

Chaque ressource cloud doit disposer de tags.

Exemples :

```text
project=mansa
environment=production
country=ML
service=payment
owner=platform-team
cost_center=payments
criticality=high
```

Les ressources sans tags doivent être détectées.

---

# 7. Environnements

Les coûts doivent être séparés entre :

- local ;
- développement ;
- test ;
- Démo ;
- Recette ;
- Préproduction ;
- Production.

La production ne doit pas financer des ressources de test inutilisées sans visibilité.

---

# 8. Budgets

Chaque environnement doit avoir :

- budget mensuel ;
- budget annuel ;
- seuil d’alerte ;
- responsable ;
- prévision ;
- marge ;
- action en cas de dépassement.

---

# 9. Seuils budgétaires

Exemples :

- 50 % du budget ;
- 75 % ;
- 90 % ;
- 100 % ;
- dépassement prévu ;
- anomalie quotidienne ;
- anomalie horaire.

Une alerte précoce doit être envoyée avant le dépassement réel.

---

# 10. Prévision des coûts

La prévision doit tenir compte de :

- croissance utilisateurs ;
- volume de transactions ;
- expansion pays ;
- nombre de TPE ;
- nouveaux partenaires ;
- stockage ;
- logs ;
- Jini ;
- campagnes ;
- services publics ;
- saisonnalité ;
- inflation fournisseur ;
- change ;
- taxes.

---

# 11. Scénarios de prévision

Prévoir au minimum :

- scénario prudent ;
- scénario central ;
- scénario de forte croissance ;
- scénario de lancement national ;
- scénario de crise ;
- scénario de panne partenaire ;
- scénario de migration ;
- scénario multi-pays.

---

# 12. Unités de coût

Mansa doit calculer des indicateurs unitaires.

Exemples :

- coût par utilisateur actif ;
- coût par transaction ;
- coût par paiement réussi ;
- coût par TPE actif ;
- coût par commerce ;
- coût par dossier KYC ;
- coût par notification ;
- coût par document ;
- coût par requête Jini ;
- coût par pays ;
- coût par million de requêtes.

---

# 13. Coût par utilisateur

Le coût par utilisateur peut inclure :

- stockage ;
- base ;
- notifications ;
- support ;
- authentification ;
- KYC ;
- activité ;
- documents ;
- analytics ;
- Jini.

---

# 14. Coût par transaction

Il peut inclure :

- infrastructure ;
- partenaire ;
- réseau carte ;
- Mobile Money ;
- banque ;
- fraude ;
- notification ;
- ledger ;
- audit ;
- rapprochement ;
- support ;
- change ;
- taxes.

---

# 15. Marge technique

Chaque produit doit distinguer :

- revenu brut ;
- coût partenaire ;
- coût technique ;
- coût support ;
- coût fraude ;
- coût réglementaire ;
- marge avant autres charges.

---

# 16. Coûts partenaires

Chaque partenaire doit avoir une fiche de coûts.

Elle doit inclure :

- coût fixe ;
- coût variable ;
- coût minimum ;
- coût par transaction ;
- coût par pays ;
- coût par devise ;
- coût par canal ;
- frais de mise en place ;
- frais de certification ;
- SLA ;
- pénalités ;
- taxes ;
- coût de sortie.

---

# 17. Mobile Money

Les coûts peuvent inclure :

- cash-in ;
- cash-out ;
- transfert ;
- interrogation de statut ;
- webhook ;
- règlement ;
- frais opérateur ;
- minimum mensuel ;
- commission ;
- reversement ;
- taxes.

---

# 18. Réseaux cartes

Les coûts peuvent inclure :

- émission ;
- personnalisation ;
- autorisation ;
- clearing ;
- settlement ;
- tokenisation ;
- 3-D Secure ;
- chargeback ;
- fraude ;
- remplacement ;
- livraison ;
- certification ;
- BIN sponsor ;
- processeur.

---

# 19. KYC et KYB

Le coût doit être suivi par :

- vérification documentaire ;
- selfie ;
- preuve de vie ;
- AML ;
- sanctions ;
- PEP ;
- revue manuelle ;
- pays ;
- fournisseur ;
- taux d’échec ;
- nombre de reprises.

---

# 20. SMS

Le coût SMS doit être suivi par :

- pays ;
- opérateur ;
- type de message ;
- OTP ;
- sécurité ;
- transaction ;
- marketing ;
- taux de livraison ;
- échec ;
- fallback.

Les SMS marketing ne doivent pas consommer le budget des messages critiques.

---

# 21. E-mail

Le coût e-mail peut dépendre de :

- volume ;
- pièce jointe ;
- réputation ;
- stockage ;
- domaine ;
- fournisseur ;
- taux d’échec.

---

# 22. Push

Les notifications Push ont souvent un coût technique faible, mais nécessitent :

- infrastructure ;
- stockage des tokens ;
- workers ;
- monitoring ;
- support ;
- fallback.

---

# 23. Jini

Les coûts Jini doivent être suivis par :

- modèle ;
- fournisseur ;
- requête ;
- utilisateur ;
- pays ;
- application ;
- cas d’usage ;
- tokens ;
- outils ;
- stockage ;
- durée ;
- taux d’erreur ;
- résultat.

---

# 24. Coût des modèles IA

Chaque appel doit pouvoir mesurer :

- tokens entrants ;
- tokens sortants ;
- modèle ;
- version ;
- coût estimé ;
- coût réel ;
- cache ;
- latence ;
- retry ;
- outil appelé.

---

# 25. Budgets Jini

Des limites peuvent être définies par :

- utilisateur ;
- rôle ;
- pays ;
- application ;
- organisation ;
- fonctionnalité ;
- période ;
- niveau d’abonnement.

---

# 26. Réduction des coûts IA

Méthodes possibles :

- modèles plus petits ;
- routage intelligent ;
- cache ;
- résumé de contexte ;
- limitation des tokens ;
- traitement batch ;
- réponses pré-calculées ;
- règles métier sans IA ;
- suppression du contexte inutile.

---

# 27. Observabilité

Les coûts d’observabilité incluent :

- ingestion logs ;
- stockage ;
- traces ;
- métriques ;
- dashboards ;
- alertes ;
- profiling ;
- rétention ;
- requêtes.

---

# 28. Maîtrise des logs

Pour éviter une explosion des coûts :

- limiter DEBUG en production ;
- échantillonner ;
- compresser ;
- agréger ;
- supprimer les doublons ;
- réduire les payloads ;
- appliquer une rétention ;
- archiver les logs anciens.

---

# 29. Stockage

Le coût doit être suivi par :

- type de donnée ;
- volume ;
- croissance ;
- classe ;
- pays ;
- environnement ;
- durée ;
- lecture ;
- écriture ;
- transfert ;
- récupération.

---

# 30. Stockage chaud et froid

## 30.1 Stockage chaud

Pour les données fréquemment utilisées.

## 30.2 Stockage froid

Pour :

- archives ;
- sauvegardes ;
- anciens rapports ;
- vieux documents ;
- historiques rarement consultés.

La restauration depuis le stockage froid peut être plus lente.

---

# 31. Réseau

Les coûts réseau peuvent inclure :

- trafic sortant ;
- trafic interrégional ;
- CDN ;
- partenaires ;
- téléchargement ;
- images ;
- fichiers ;
- réplication ;
- sauvegardes.

---

# 32. Réduction du trafic

Méthodes :

- compression ;
- CDN ;
- cache ;
- pagination ;
- sélection de champs ;
- limitation des images ;
- formats optimisés ;
- synchronisation différentielle ;
- regroupement de requêtes.

---

# 33. Base de données

Les coûts PostgreSQL dépendent de :

- CPU ;
- mémoire ;
- stockage ;
- IOPS ;
- réplication ;
- sauvegardes ;
- rétention ;
- read replicas ;
- haute disponibilité ;
- transfert ;
- licences éventuelles.

---

# 34. Optimisation PostgreSQL

Mesures possibles :

- index utiles ;
- suppression des index inutiles ;
- requêtes optimisées ;
- partitionnement ;
- archivage ;
- pagination ;
- réduction des jointures ;
- vues matérialisées ;
- taille correcte des instances ;
- pool de connexions.

---

# 35. Cache

Le cache doit réduire :

- la charge base ;
- la latence ;
- le coût des requêtes ;
- les appels partenaires.

Il ne doit pas créer :

- incohérences ;
- données financières fausses ;
- dépendance critique ;
- coût supérieur au gain.

---

# 36. Files et workers

Le coût dépend de :

- nombre de messages ;
- rétention ;
- volume ;
- concurrence ;
- workers ;
- retries ;
- dead letters ;
- stockage ;
- fréquence.

---

# 37. Retry et coût

Un retry excessif augmente :

- appels partenaires ;
- CPU ;
- files ;
- logs ;
- latence ;
- risque de doublon ;
- facture.

Chaque retry doit être justifié.

---

# 38. Environnements non production

Les environnements non critiques peuvent utiliser :

- extinction nocturne ;
- scaling minimal ;
- bases plus petites ;
- rétention courte ;
- données limitées ;
- services simulés ;
- activation à la demande.

---

# 39. Ressources inutilisées

Le système doit détecter :

- disques orphelins ;
- IP inutilisées ;
- snapshots anciens ;
- load balancers inutiles ;
- bases inactives ;
- environnements oubliés ;
- images anciennes ;
- logs sans usage ;
- branches de preview permanentes.

---

# 40. Nettoyage automatique

Des tâches peuvent supprimer ou archiver :

- artefacts expirés ;
- previews fermées ;
- images anciennes ;
- logs dépassant la rétention ;
- caches ;
- fichiers temporaires ;
- exports expirés ;
- snapshots non protégés.

---

# 41. Engagements fournisseurs

Des réductions peuvent être obtenues via :

- instances réservées ;
- plans d’épargne ;
- engagement de volume ;
- contrats entreprise ;
- crédits startup ;
- remises partenaires.

Ces engagements doivent être pris avec prudence.

---

# 42. Risque d’engagement

Avant un engagement long, analyser :

- croissance ;
- architecture ;
- migration possible ;
- changement de fournisseur ;
- volume réel ;
- besoin de flexibilité ;
- devise de facturation.

---

# 43. Multi-cloud

Le multi-cloud peut augmenter :

- résilience ;
- capacité de négociation ;
- souveraineté.

Mais il augmente aussi :

- complexité ;
- coûts ;
- compétences nécessaires ;
- duplication ;
- monitoring ;
- support.

Il ne doit pas être adopté sans justification.

---

# 44. Capacité

La capacité doit être planifiée pour :

- API ;
- base ;
- cache ;
- file ;
- stockage ;
- réseau ;
- workers ;
- TPE ;
- partenaires ;
- support ;
- monitoring.

---

# 45. Indicateurs de capacité

Exemples :

- requêtes par seconde ;
- transactions par seconde ;
- utilisateurs simultanés ;
- connexions base ;
- taille de file ;
- latence ;
- CPU ;
- mémoire ;
- stockage ;
- IOPS ;
- bande passante ;
- workers actifs.

---

# 46. Capacité nominale

La capacité nominale correspond au fonctionnement attendu en conditions normales.

---

# 47. Capacité de pointe

La capacité de pointe doit couvrir :

- heures de forte activité ;
- jours de paie ;
- bourses ;
- campagnes ;
- taxes ;
- événements ;
- lancement de carte ;
- fin de mois ;
- fêtes ;
- promotions.

---

# 48. Capacité de crise

Une marge supplémentaire doit être prévue pour :

- retries ;
- panne partenaire ;
- reprise ;
- rejeu ;
- failover ;
- incident régional ;
- traitement de rattrapage ;
- activité frauduleuse.

---

# 49. Planification par pays

Chaque pays doit avoir une prévision :

- population cible ;
- utilisateurs actifs ;
- commerces ;
- TPE ;
- paiements ;
- partenaires ;
- devise ;
- pics ;
- stockage ;
- support ;
- coût mensuel ;
- coût annuel.

---

# 50. Prévision utilisateurs

Segments possibles :

- inscrits ;
- vérifiés ;
- actifs mensuels ;
- actifs quotidiens ;
- commerçants ;
- employés ;
- agents publics ;
- TPE actifs ;
- partenaires API.

---

# 51. Prévision transactionnelle

Mesurer :

- transactions quotidiennes ;
- transactions par utilisateur ;
- montant moyen ;
- pics ;
- répartition par canal ;
- succès ;
- échecs ;
- retries ;
- remboursements ;
- rapprochements.

---

# 52. Tests de capacité

Les tests doivent déterminer :

- limite actuelle ;
- point de saturation ;
- comportement dégradé ;
- temps de récupération ;
- besoin de scaling ;
- coût marginal ;
- goulot d’étranglement.

---

# 53. Goulots d’étranglement

Ils peuvent apparaître dans :

- base ;
- partenaire ;
- file ;
- API Gateway ;
- réseau ;
- cache ;
- worker ;
- stockage ;
- application mobile ;
- TPE ;
- monitoring.

---

# 54. Scalabilité horizontale

Ajouter plusieurs instances pour :

- API ;
- workers ;
- services ;
- frontend ;
- traitements.

Les services doivent être stateless lorsque possible.

---

# 55. Scalabilité verticale

Augmenter :

- CPU ;
- mémoire ;
- stockage ;
- IOPS.

Elle est simple mais possède des limites.

---

# 56. Autoscaling

Les règles peuvent utiliser :

- CPU ;
- mémoire ;
- latence ;
- trafic ;
- taille de file ;
- nombre de connexions ;
- temps du plus ancien message ;
- taux d’erreur.

---

# 57. Limites d’autoscaling

L’autoscaling doit définir :

- minimum ;
- maximum ;
- délai ;
- vitesse ;
- seuil ;
- cooldown ;
- budget ;
- protection contre l’emballement.

---

# 58. Emballement de coûts

Un incident peut provoquer une augmentation automatique des ressources.

Exemples :

- boucle de retry ;
- attaque ;
- bug ;
- file infinie ;
- logs massifs ;
- requêtes abusives ;
- bots ;
- synchronisation cassée.

Des plafonds et alertes sont nécessaires.

---

# 59. Rate Limiting

Le rate limiting protège :

- capacité ;
- partenaires ;
- coûts ;
- sécurité ;
- disponibilité.

Il peut être défini par :

- utilisateur ;
- IP ;
- appareil ;
- clé API ;
- partenaire ;
- endpoint ;
- pays ;
- organisation.

---

# 60. Quotas

Des quotas peuvent limiter :

- appels API ;
- exports ;
- Jini ;
- SMS ;
- stockage ;
- documents ;
- rapports ;
- recherches ;
- webhooks ;
- imports.

---

# 61. Dégradation contrôlée

En cas de saturation, Mansa peut prioriser :

1. authentification ;
2. consultation de solde ;
3. blocage de carte ;
4. paiements ;
5. transferts ;
6. support ;
7. notifications de sécurité ;
8. fonctions secondaires ;
9. marketing ;
10. analytics non critiques.

---

# 62. Priorisation des charges

Les charges critiques doivent utiliser :

- files dédiées ;
- workers dédiés ;
- quotas réservés ;
- capacité minimale ;
- monitoring spécifique.

---

# 63. Performance

Les objectifs doivent être définis par opération.

Exemples :

- connexion ;
- consultation ;
- paiement ;
- transfert ;
- recherche ;
- génération de reçu ;
- chargement d’écran ;
- réponse Jini ;
- synchronisation TPE.

---

# 64. Objectifs de latence

Mesurer :

- p50 ;
- p75 ;
- p90 ;
- p95 ;
- p99.

Un objectif peut varier selon :

- pays ;
- réseau ;
- appareil ;
- partenaire ;
- type d’opération.

---

# 65. Performance mobile

Surveiller :

- temps de démarrage ;
- taille de l’application ;
- mémoire ;
- batterie ;
- données mobiles ;
- nombre de requêtes ;
- cache ;
- animations ;
- crashs ;
- appareils faibles.

---

# 66. Performance web

Surveiller :

- temps de chargement ;
- Core Web Vitals ;
- JavaScript ;
- images ;
- requêtes ;
- cache ;
- CDN ;
- rendu ;
- erreurs navigateur.

---

# 67. Performance TPE

Surveiller :

- lancement ;
- connexion ;
- lecture carte ;
- NFC ;
- autorisation ;
- impression ;
- synchronisation ;
- batterie ;
- stockage ;
- réseau.

---

# 68. Performance partenaires

Chaque partenaire doit avoir :

- latence ;
- disponibilité ;
- taux d’erreur ;
- capacité ;
- limite ;
- quota ;
- coût ;
- SLA ;
- tendance.

---

# 69. Coût de la résilience

Les mécanismes suivants ont un coût :

- réplication ;
- régions multiples ;
- sauvegardes ;
- warm standby ;
- instances minimales ;
- files persistantes ;
- monitoring.

Ce coût doit être comparé au risque évité.

---

# 70. Arbitrage coût-risque

Chaque décision importante doit considérer :

- criticité ;
- impact financier ;
- impact utilisateur ;
- conformité ;
- probabilité ;
- coût de l’incident ;
- coût de la prévention ;
- capacité de reprise.

---

# 71. FinOps

Mansa doit appliquer une démarche FinOps comprenant :

- visibilité ;
- responsabilité ;
- optimisation ;
- prévision ;
- collaboration ;
- suivi ;
- gouvernance.

---

# 72. Revues FinOps

Des revues régulières doivent analyser :

- budget ;
- dépenses ;
- anomalies ;
- croissance ;
- services coûteux ;
- ressources inutilisées ;
- partenaires ;
- coûts unitaires ;
- marges ;
- actions.

---

# 73. Fréquence des revues

Exemples :

- quotidienne pour anomalies ;
- hebdomadaire pour suivi ;
- mensuelle pour budget ;
- trimestrielle pour architecture ;
- annuelle pour contrats majeurs.

---

# 74. Anomalies de coût

Une anomalie peut être :

- hausse soudaine ;
- service inconnu ;
- région inattendue ;
- logs excessifs ;
- trafic anormal ;
- retry massif ;
- stockage croissant ;
- ressource oubliée ;
- facture partenaire incorrecte.

---

# 75. Détection automatique

Le système doit comparer :

- coût réel ;
- prévision ;
- moyenne ;
- période précédente ;
- volume ;
- coût unitaire ;
- budget.

---

# 76. Alertes de coût

Une alerte doit préciser :

- montant ;
- variation ;
- service ;
- pays ;
- environnement ;
- propriétaire ;
- cause probable ;
- lien ;
- action.

---

# 77. Kill switch financier

Pour certains services non critiques, un mécanisme peut limiter ou désactiver :

- Jini coûteux ;
- campagnes ;
- exports massifs ;
- génération de rapports ;
- analytics lourds ;
- traitement secondaire.

Il ne doit pas couper les services financiers critiques sans procédure.

---

# 78. Tableau de bord coûts

Il doit afficher :

- coût total ;
- coût par service ;
- coût par application ;
- coût par pays ;
- coût par environnement ;
- coût par partenaire ;
- coût par transaction ;
- budget ;
- prévision ;
- anomalies ;
- tendance ;
- marge technique.

---

# 79. Tableau de bord capacité

Il doit afficher :

- charge actuelle ;
- capacité utilisée ;
- marge ;
- saturation ;
- croissance ;
- prévision ;
- point de rupture ;
- autoscaling ;
- stockage ;
- base ;
- files ;
- partenaires.

---

# 80. Administration

Le portail Admin technique peut permettre :

- consulter les coûts ;
- filtrer ;
- définir un budget ;
- définir une alerte ;
- consulter la capacité ;
- consulter les prévisions ;
- consulter les ressources inutilisées ;
- suivre les optimisations ;
- consulter les coûts unitaires ;
- générer un rapport.

Il ne doit pas permettre de supprimer directement une ressource critique sans workflow contrôlé.

---

# 81. Permissions

Exemples :

```text
cost.read
cost.budget.read
cost.budget.manage
cost.alert.manage
cost.forecast.read
cost.optimization.read
cost.optimization.approve
capacity.read
capacity.plan.manage
capacity.scale.approve
capacity.limit.manage
finops.audit.read
```

---

# 82. Actions critiques

Doivent être protégées :

- réduction de capacité critique ;
- suppression de redondance ;
- réduction de rétention ;
- extinction d’un environnement ;
- modification de budget production ;
- plafonnement d’autoscaling ;
- désactivation d’un partenaire ;
- changement de classe de stockage ;
- suppression de sauvegarde.

---

# 83. Double validation

Recommandée pour :

- réduction d’infrastructure production ;
- diminution de haute disponibilité ;
- réduction du RPO/RTO ;
- suppression de ressources ;
- arrêt d’un environnement ;
- changement majeur de fournisseur ;
- limite d’autoscaling critique ;
- kill switch financier global.

---

# 84. API internes

Exemples :

```http
GET    /costs
GET    /costs/summary
GET    /costs/by-service
GET    /costs/by-country
GET    /costs/unit-economics
GET    /costs/forecasts
GET    /costs/anomalies

GET    /capacity
GET    /capacity/services
GET    /capacity/forecasts
GET    /capacity/bottlenecks

POST   /costs/budgets
PATCH  /costs/budgets/{id}
POST   /capacity/plans
POST   /capacity/scaling-recommendations
```

---

# 85. Modèles

- CostRecord
- CostCategory
- CostAllocation
- CostCenter
- CostBudget
- CostForecast
- CostAnomaly
- UnitCost
- PartnerCost
- InfrastructureCost
- CapacityMetric
- CapacityPlan
- CapacityForecast
- CapacityThreshold
- ScalingPolicy
- ScalingRecommendation
- OptimizationAction
- FinOpsReview
- FinOpsAudit

---

# 86. Audit

Chaque action importante doit enregistrer :

- auteur ;
- approbateur ;
- service ;
- environnement ;
- pays ;
- ancienne valeur ;
- nouvelle valeur ;
- budget ;
- capacité ;
- justification ;
- risque ;
- date ;
- résultat ;
- rollback.

---

# 87. Analytics

Événements possibles :

```text
cost_budget_created
cost_budget_updated
cost_threshold_exceeded
cost_anomaly_detected
cost_forecast_updated
cost_optimization_identified
cost_optimization_applied
capacity_threshold_reached
capacity_forecast_updated
capacity_scaling_started
capacity_scaling_completed
capacity_bottleneck_detected
capacity_limit_changed
finops_review_completed
```

---

# 88. Tests

- tests de collecte des coûts ;
- tests de tags ;
- tests d’allocation ;
- tests de budget ;
- tests d’alerte ;
- tests de prévision ;
- tests d’anomalie ;
- tests de coût unitaire ;
- tests partenaires ;
- tests de capacité ;
- tests d’autoscaling ;
- tests de limites ;
- tests de saturation ;
- tests de dégradation ;
- tests de quotas ;
- tests de rate limiting ;
- tests de kill switch ;
- tests de permissions ;
- tests de double validation ;
- tests d’audit.

---

# 89. Règles métier

1. Toute ressource possède un propriétaire.
2. Toute ressource possède des tags de coût.
3. Les coûts sont séparés par environnement.
4. Les budgets sont définis.
5. Les anomalies sont surveillées.
6. Les coûts unitaires sont calculés.
7. Les partenaires sont suivis séparément.
8. Les coûts Jini sont mesurés.
9. Les coûts d’observabilité sont maîtrisés.
10. Les logs ont une rétention.
11. Les ressources inutilisées sont détectées.
12. Les environnements non production sont optimisés.
13. Les coûts ne sont pas réduits au détriment de la sécurité.
14. Les services critiques conservent une marge.
15. La capacité est prévue avant les lancements.
16. Les pics sont testés.
17. L’autoscaling possède des limites.
18. Le rate limiting protège les coûts.
19. Les quotas sont administrables.
20. Les services critiques sont prioritaires.
21. Les partenaires possèdent des limites connues.
22. Les coûts sont comparés aux revenus.
23. Les optimisations sont suivies.
24. Les décisions critiques sont auditées.
25. Les prévisions sont régulièrement mises à jour.

---

# 90. Critères d’acceptation

La gestion des coûts et de la capacité est validée lorsque :

- les ressources sont correctement taguées ;
- les coûts sont répartis par service ;
- les coûts sont séparés par environnement ;
- les budgets et alertes sont configurés ;
- les prévisions existent ;
- les coûts unitaires sont calculés ;
- les coûts partenaires sont suivis ;
- les coûts Jini sont mesurés ;
- les ressources inutilisées sont détectées ;
- la capacité actuelle est connue ;
- les pics sont modélisés ;
- les goulots d’étranglement sont identifiés ;
- l’autoscaling est configuré ;
- les limites évitent l’emballement de coûts ;
- le rate limiting et les quotas sont actifs ;
- les performances sont mesurées ;
- les tableaux de bord sont disponibles ;
- les optimisations sont auditées ;
- les tests couvrent les scénarios critiques.
