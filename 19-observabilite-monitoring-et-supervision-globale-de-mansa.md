# 19 — Observabilité, monitoring et supervision globale de Mansa

## 1. Objet du document

Ce document définit le système officiel d’observabilité de Mansa.

Il couvre :

- les métriques ;
- les logs techniques ;
- les traces distribuées ;
- les tableaux de bord ;
- les alertes ;
- les services ;
- les bases de données ;
- les files ;
- les partenaires ;
- les applications mobiles ;
- les applications web ;
- les TPE ;
- les API ;
- le ledger ;
- les paiements ;
- les incidents ;
- les performances ;
- la capacité ;
- la disponibilité ;
- les coûts techniques.

L’objectif est de permettre aux équipes Mansa de comprendre rapidement :

- ce qui se passe ;
- où se trouve le problème ;
- depuis quand il existe ;
- quels utilisateurs sont affectés ;
- quel pays est concerné ;
- quel partenaire est concerné ;
- quel impact financier existe ;
- quelle action doit être prise.

---

# 2. Principes fondamentaux

## 2.1 Tout service critique doit être observable

Un service critique doit exposer au minimum :

- état de santé ;
- disponibilité ;
- latence ;
- taux d’erreur ;
- volume ;
- saturation ;
- dépendances ;
- version ;
- environnement ;
- pays ;
- corrélation.

---

## 2.2 L’observabilité doit être prévue dès la conception

Les métriques, logs et traces ne doivent pas être ajoutés seulement après un incident.

Chaque nouveau module doit définir :

- ce qui doit être mesuré ;
- ce qui doit être journalisé ;
- ce qui doit être tracé ;
- les seuils ;
- les alertes ;
- les tableaux de bord ;
- les données interdites.

---

## 2.3 Une alerte doit être actionnable

Une alerte utile doit indiquer :

- problème ;
- service ;
- gravité ;
- impact ;
- heure ;
- lien vers le tableau de bord ;
- procédure ;
- responsable ;
- identifiant d’incident éventuel.

Les alertes sans action possible doivent être supprimées ou transformées en métriques.

---

## 2.4 Aucune donnée sensible inutile

Les outils d’observabilité ne doivent pas contenir :

- mot de passe ;
- PIN ;
- OTP ;
- CVV ;
- numéro complet de carte ;
- secret ;
- clé privée ;
- token complet ;
- document d’identité ;
- contenu privé complet ;
- données financières non nécessaires.

---

## 2.5 Corrélation de bout en bout

Une opération doit pouvoir être suivie depuis :

- l’application ;
- l’API Gateway ;
- le service métier ;
- le partenaire ;
- le ledger ;
- la notification ;
- l’audit ;
- le support.

Un identifiant de corrélation unique doit être propagé.

---

# 3. Piliers de l’observabilité

Le système repose sur :

- métriques ;
- logs ;
- traces ;
- événements ;
- profils de performance ;
- health checks ;
- audits ;
- données métier agrégées.

---

# 4. Métriques techniques

Chaque service doit exposer des métriques comme :

- nombre de requêtes ;
- requêtes par seconde ;
- taux d’erreur ;
- latence moyenne ;
- percentiles ;
- consommation CPU ;
- mémoire ;
- connexions ;
- pool ;
- saturation ;
- taille des files ;
- retries ;
- timeouts ;
- cache hit rate ;
- stockage ;
- espace disque ;
- redémarrages.

---

# 5. Métriques métier

Exemples :

- paiements initiés ;
- paiements réussis ;
- paiements refusés ;
- paiements en attente ;
- transferts ;
- remboursements ;
- montants ;
- commissions ;
- frais ;
- cartes actives ;
- TPE actifs ;
- utilisateurs actifs ;
- dossiers KYC ;
- tickets support ;
- opérations Mobile Money ;
- règlements commerçants ;
- services publics payés.

Les métriques métier doivent être agrégées et protéger la confidentialité.

---

# 6. Métriques financières critiques

Le système doit surveiller :

- volume financier ;
- nombre de transactions ;
- échecs ;
- doublons ;
- remboursements ;
- chargebacks ;
- écarts de rapprochement ;
- suspense ;
- ajustements ;
- solde global par devise ;
- différences ledger ;
- commissions ;
- règlements ;
- réservations expirées.

---

# 7. Golden Signals

Pour chaque service, suivre au minimum :

- latence ;
- trafic ;
- erreurs ;
- saturation.

---

# 8. Percentiles

Les performances ne doivent pas être suivies uniquement avec une moyenne.

Percentiles recommandés :

```text
p50
p75
p90
p95
p99
```

Les opérations financières critiques doivent particulièrement surveiller `p95` et `p99`.

---

# 9. SLI, SLO et SLA

## 9.1 SLI

Indicateur mesuré.

Exemples :

- taux de réussite des paiements ;
- disponibilité API ;
- latence ;
- délai de traitement.

## 9.2 SLO

Objectif interne.

Exemple :

```text
99,9 % des demandes de consultation de solde réussissent en moins de 2 secondes.
```

## 9.3 SLA

Engagement contractuel éventuel envers :

- partenaires ;
- commerçants ;
- administrations ;
- clients professionnels.

---

# 10. Budget d’erreur

Chaque SLO peut avoir un budget d’erreur.

Exemple :

Si l’objectif est `99,9 %`, le budget d’erreur autorise une petite proportion d’échecs.

Lorsque le budget est consommé trop rapidement :

- les déploiements risqués sont ralentis ;
- les corrections deviennent prioritaires ;
- les responsables sont alertés ;
- un plan d’amélioration est déclenché.

---

# 11. Logs techniques

Chaque log doit contenir lorsque pertinent :

- timestamp ;
- niveau ;
- service ;
- version ;
- environnement ;
- pays ;
- application ;
- corrélation ;
- trace ;
- span ;
- message ;
- code ;
- durée ;
- résultat ;
- partenaire ;
- tentative ;
- erreur normalisée.

---

# 12. Niveaux de logs

Niveaux recommandés :

- TRACE ;
- DEBUG ;
- INFO ;
- WARN ;
- ERROR ;
- FATAL.

En production :

- TRACE et DEBUG doivent être limités ;
- ERROR ne doit pas être utilisé pour des erreurs métier normales ;
- FATAL correspond à une situation critique.

---

# 13. Logs structurés

Les logs doivent être structurés.

Exemple :

```json
{
  "level": "ERROR",
  "service": "payment-service",
  "code": "PARTNER_TIMEOUT",
  "correlationId": "cor_123",
  "partner": "orange_money",
  "durationMs": 30000
}
```

Éviter les logs uniquement textuels impossibles à filtrer.

---

# 14. Masquage

Les données sensibles doivent être :

- supprimées ;
- masquées ;
- hachées ;
- tronquées ;
- remplacées par un identifiant technique.

Exemple :

```text
**** **** **** 1234
```

---

# 15. Traces distribuées

Une trace doit suivre une requête à travers plusieurs services.

Elle doit contenir :

- trace ID ;
- span ID ;
- parent span ;
- service ;
- opération ;
- durée ;
- statut ;
- erreur ;
- dépendance ;
- version ;
- pays ;
- environnement.

---

# 16. Propagation

Les identifiants de trace et corrélation doivent être propagés dans :

- HTTP ;
- événements ;
- files ;
- webhooks ;
- tâches asynchrones ;
- appels partenaires ;
- notifications ;
- traitements batch.

---

# 17. Échantillonnage

Toutes les traces ne doivent pas forcément être conservées.

Stratégies :

- échantillonnage aléatoire ;
- conservation des erreurs ;
- conservation des opérations lentes ;
- conservation des transactions critiques ;
- conservation des partenaires sensibles ;
- taux différent selon l’environnement.

---

# 18. Profiling

Le profiling peut être utilisé pour comprendre :

- CPU ;
- mémoire ;
- allocations ;
- fonctions lentes ;
- fuites ;
- verrous ;
- requêtes coûteuses.

Il doit être activé de manière contrôlée en production.

---

# 19. Health Checks

Chaque service doit exposer :

- liveness ;
- readiness ;
- dépendances ;
- base ;
- cache ;
- file ;
- stockage ;
- partenaire critique ;
- certificat ;
- espace disque.

---

# 20. Base de données

Surveiller :

- disponibilité ;
- connexions ;
- temps de requête ;
- verrous ;
- deadlocks ;
- réplication ;
- retard ;
- espace ;
- index ;
- requêtes lentes ;
- migrations ;
- erreurs ;
- sauvegardes.

---

# 21. Cache

Surveiller :

- disponibilité ;
- mémoire ;
- taux de hit ;
- taux de miss ;
- évictions ;
- clés expirées ;
- latence ;
- erreurs ;
- divergence ;
- taille.

---

# 22. Files et workers

Surveiller :

- taille ;
- âge du message le plus ancien ;
- débit ;
- échecs ;
- retries ;
- dead letters ;
- workers actifs ;
- saturation ;
- temps de traitement ;
- blocage ;
- priorité.

---

# 23. API Gateway

Surveiller :

- requêtes ;
- latence ;
- erreurs ;
- authentification ;
- autorisations refusées ;
- rate limiting ;
- endpoints ;
- versions ;
- clients ;
- pays ;
- appareils ;
- partenaires ;
- codes HTTP.

---

# 24. Paiements

Tableau de bord minimum :

- initiés ;
- réussis ;
- refusés ;
- échoués ;
- en attente ;
- inconnus ;
- temps moyen ;
- montant ;
- devise ;
- pays ;
- canal ;
- partenaire ;
- application ;
- version.

---

# 25. Ledger

Surveiller :

- écritures ;
- transactions ;
- déséquilibres ;
- réservations ;
- contre-écritures ;
- ajustements ;
- suspense ;
- écarts ;
- clôtures ;
- temps de comptabilisation ;
- reconstruction de solde ;
- divergences de cache.

---

# 26. Cartes

Surveiller :

- autorisations ;
- refus ;
- captures ;
- annulations ;
- remboursements ;
- tokenisation ;
- ajout wallet ;
- activation ;
- blocage ;
- remplacement ;
- incidents réseau ;
- chargebacks.

---

# 27. Mobile Money

Surveiller par partenaire :

- requêtes ;
- confirmations ;
- timeouts ;
- statuts inconnus ;
- webhooks ;
- retries ;
- montant ;
- frais ;
- délais ;
- rapprochement ;
- disponibilité.

---

# 28. TPE

Surveiller :

- terminaux actifs ;
- terminaux hors ligne ;
- version ;
- modèle ;
- paiements ;
- latence ;
- refus ;
- synchronisation ;
- imprimante ;
- batterie ;
- certificats ;
- mises à jour ;
- crashs ;
- espace disponible.

---

# 29. Applications mobiles

Surveiller :

- sessions ;
- utilisateurs actifs ;
- crashs ;
- ANR ;
- temps de démarrage ;
- temps d’écran ;
- erreurs réseau ;
- versions ;
- appareils ;
- systèmes ;
- pays ;
- abandons ;
- mises à jour.

---

# 30. Applications web

Surveiller :

- Core Web Vitals ;
- erreurs JavaScript ;
- temps de chargement ;
- API lentes ;
- navigation ;
- sessions ;
- navigateurs ;
- appareils ;
- conversions ;
- disponibilité ;
- erreurs d’authentification.

---

# 31. Jini

Surveiller :

- requêtes ;
- latence ;
- tokens ;
- coût ;
- erreurs ;
- outils appelés ;
- actions refusées ;
- escalades humaines ;
- langue ;
- pays ;
- modèle ;
- version ;
- taux de satisfaction ;
- catégories bloquées.

Aucun contenu privé complet ne doit apparaître dans les métriques.

---

# 32. Partenaires

Chaque partenaire doit avoir un tableau de bord dédié.

Mesures :

- disponibilité ;
- latence ;
- taux d’erreur ;
- timeouts ;
- volume ;
- montants ;
- webhooks ;
- certificats ;
- SLA ;
- statut ;
- environnement ;
- rapprochement.

---

# 33. Tableaux de bord

Types :

- direction ;
- produit ;
- finance ;
- sécurité ;
- support ;
- pays ;
- partenaire ;
- application ;
- infrastructure ;
- incident ;
- ledger ;
- paiements ;
- TPE ;
- Jini.

---

# 34. Tableau de bord direction

Doit rester synthétique.

Exemples :

- utilisateurs actifs ;
- volume transactionnel ;
- revenus ;
- paiements réussis ;
- disponibilité ;
- incidents majeurs ;
- pays actifs ;
- partenaires ;
- croissance ;
- risque opérationnel.

---

# 35. Tableau de bord support

Doit montrer :

- incidents actifs ;
- erreurs fréquentes ;
- utilisateurs affectés ;
- partenaires indisponibles ;
- transactions en attente ;
- communications officielles ;
- procédures ;
- statut des files.

---

# 36. Alertes techniques

Exemples :

- service indisponible ;
- erreur élevée ;
- latence élevée ;
- saturation ;
- file bloquée ;
- disque plein ;
- sauvegarde échouée ;
- réplication en retard ;
- certificat expirant ;
- crash massif ;
- migration échouée.

---

# 37. Alertes métier

Exemples :

- taux de paiement réussi en baisse ;
- remboursements anormaux ;
- hausse des refus ;
- montant inhabituel ;
- écart ledger ;
- suspense élevé ;
- baisse de conversion ;
- cartes non activées ;
- TPE hors ligne ;
- partenaires dégradés.

---

# 38. Alertes financières

Exemples :

- déséquilibre ledger ;
- double transaction ;
- règlement manquant ;
- écart de rapprochement ;
- réserve incohérente ;
- solde négatif non autorisé ;
- commission inhabituelle ;
- remboursement excessif.

---

# 39. Alertes de sécurité

Exemples :

- tentatives de connexion ;
- élévation de privilège ;
- accès d’urgence ;
- export massif ;
- clé expirante ;
- signature invalide ;
- webhook suspect ;
- activité anormale ;
- modification de rôle critique.

---

# 40. Seuils

Les seuils doivent être :

- versionnés ;
- adaptés par service ;
- adaptés par pays ;
- adaptés par partenaire ;
- testés ;
- révisés ;
- limités pour éviter le bruit.

---

# 41. Déduplication des alertes

Le système doit éviter :

- répétitions ;
- avalanche ;
- doublons multi-services ;
- alertes identiques ;
- notifications continues sans changement.

Une alerte existante doit être mise à jour lorsque possible.

---

# 42. Escalade

Une alerte peut suivre :

1. équipe de garde ;
2. responsable service ;
3. Incident Commander ;
4. sécurité ou finance ;
5. direction ;
6. partenaire ;
7. communication.

---

# 43. Astreinte

Le système doit définir :

- planning ;
- personne de garde ;
- moyen de contact ;
- escalade ;
- temps de réponse ;
- remplacement ;
- rapport de garde.

---

# 44. Runbooks

Chaque alerte critique doit avoir un runbook.

Il contient :

- symptômes ;
- vérifications ;
- commandes autorisées ;
- tableaux de bord ;
- dépendances ;
- actions ;
- rollback ;
- responsables ;
- critères de résolution ;
- communication.

---

# 45. Rétention

La durée de conservation varie selon :

- métriques ;
- logs ;
- traces ;
- profils ;
- incidents ;
- audits ;
- pays ;
- conformité ;
- coûts.

Les logs techniques ne doivent pas être conservés indéfiniment sans besoin.

---

# 46. Coûts d’observabilité

Surveiller :

- volume de logs ;
- volume de traces ;
- stockage ;
- ingestion ;
- requêtes ;
- rétention ;
- partenaires ;
- coût par service ;
- coût par environnement.

Des quotas et politiques d’échantillonnage doivent éviter les dépenses incontrôlées.

---

# 47. Environnements

Les données doivent être séparées entre :

- local ;
- test ;
- Démo ;
- Recette ;
- Préproduction ;
- Production.

Les alertes production doivent être clairement distinguées.

---

# 48. Multi-pays

Les tableaux doivent pouvoir filtrer par :

- pays ;
- région ;
- devise ;
- partenaire ;
- langue ;
- application ;
- canal ;
- environnement.

---

# 49. Administration

Le portail Admin doit permettre :

- consulter les tableaux de bord ;
- rechercher une corrélation ;
- consulter les erreurs ;
- consulter les traces ;
- voir les dépendances ;
- configurer des alertes ;
- consulter les SLO ;
- gérer les runbooks ;
- suivre les incidents ;
- exporter des rapports ;
- consulter les coûts.

---

# 50. Permissions

Exemples :

```text
observability.read
observability.logs.read
observability.traces.read
observability.metrics.read
observability.alert.create
observability.alert.update
observability.slo.manage
observability.runbook.manage
observability.cost.read
observability.sensitive.read
```

---

# 51. Données sensibles

Les accès aux logs ou traces contenant des données potentiellement sensibles doivent être limités.

Toute consultation sensible peut être auditée.

---

# 52. API

Exemples internes :

```http
GET    /observability/health
GET    /observability/metrics
GET    /observability/logs
GET    /observability/traces/{traceId}
GET    /observability/correlations/{correlationId}

GET    /observability/slos
POST   /observability/slos
PATCH  /observability/slos/{id}

GET    /observability/alerts
POST   /observability/alerts
PATCH  /observability/alerts/{id}
```

---

# 53. Modèles

- MetricDefinition
- MetricSeries
- LogEvent
- Trace
- Span
- ServiceHealth
- ServiceDependency
- Dashboard
- DashboardWidget
- AlertRule
- AlertOccurrence
- AlertEscalation
- SliDefinition
- SloDefinition
- ErrorBudget
- Runbook
- OnCallSchedule
- ObservabilityRetentionPolicy
- ObservabilityCost
- ObservabilityAudit

---

# 54. Règles métier

1. Tout service critique est observable.
2. Les métriques doivent être définies avant la production.
3. Les logs sont structurés.
4. Les secrets ne sont jamais journalisés.
5. Les opérations sont corrélables.
6. Les erreurs conservent un code stable.
7. Les alertes doivent être actionnables.
8. Les alertes sont dédupliquées.
9. Les services critiques possèdent des SLO.
10. Les budgets d’erreur sont suivis.
11. Les partenaires possèdent des tableaux dédiés.
12. Le ledger possède des alertes financières.
13. Les TPE remontent leur santé.
14. Les versions sont identifiables.
15. Les environnements sont séparés.
16. Les pays sont filtrables.
17. Les traces sensibles sont échantillonnées et protégées.
18. Les logs ont une politique de rétention.
19. Les coûts sont surveillés.
20. Les alertes critiques ont un runbook.
21. Les accès sensibles sont limités.
22. Les tableaux de bord restent cohérents.
23. Les données métier sont agrégées.
24. Les incidents sont reliés aux alertes.
25. L’observabilité elle-même doit être disponible et surveillée.

---

# 55. Analytics

Événements possibles :

```text
observability_dashboard_viewed
observability_alert_triggered
observability_alert_acknowledged
observability_alert_resolved
observability_slo_breached
observability_error_budget_consumed
observability_trace_searched
observability_runbook_opened
observability_cost_threshold_exceeded
observability_sensitive_log_accessed
```

---

# 56. Tests

- tests de métriques ;
- tests de logs ;
- tests de masquage ;
- tests de traces ;
- tests de propagation ;
- tests de corrélation ;
- tests de health checks ;
- tests d’alertes ;
- tests de seuils ;
- tests de déduplication ;
- tests d’escalade ;
- tests de SLO ;
- tests de budget d’erreur ;
- tests multi-pays ;
- tests multi-environnements ;
- tests de permissions ;
- tests de rétention ;
- tests de charge ;
- tests de panne de l’outil d’observabilité.

---

# 57. Critères d’acceptation

L’observabilité est validée lorsque :

- les services critiques exposent leurs métriques ;
- les logs sont structurés ;
- les données sensibles sont masquées ;
- les traces distribuées fonctionnent ;
- les corrélations sont propagées ;
- les health checks existent ;
- les tableaux de bord couvrent les domaines critiques ;
- les partenaires sont surveillés ;
- le ledger possède des alertes dédiées ;
- les applications remontent leurs crashs ;
- les TPE remontent leur état ;
- les alertes sont actionnables ;
- les SLO sont définis ;
- les budgets d’erreur sont suivis ;
- les runbooks existent ;
- les coûts d’observabilité sont maîtrisés ;
- les accès sont protégés ;
- les tests couvrent les scénarios critiques.
