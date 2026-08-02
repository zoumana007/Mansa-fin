# 64 — Observabilité, supervision et gestion des incidents techniques Mansa : logs, métriques, traces, alertes, SLA/SLO, centre d’incidents, astreinte, communication, post-mortem et administration centralisée

## 1. Objet du document

Ce document définit l’architecture officielle de la **Plateforme d’observabilité, de supervision et de gestion des incidents techniques Mansa**.

Cette plateforme doit permettre de surveiller en continu l’ensemble de l’écosystème Mansa, de détecter rapidement les anomalies, de comprendre leur origine, de coordonner la réponse, d’informer les utilisateurs concernés et de rétablir le service dans les meilleurs délais.

Elle couvre notamment :

- les applications mobiles ;
- les applications web ;
- les portails internes ;
- les portails partenaires ;
- les API ;
- l’API Gateway ;
- les microservices ;
- le ledger ;
- les paiements ;
- les cartes ;
- le KYC et le KYB ;
- les connecteurs bancaires ;
- les connecteurs Mobile Money ;
- les TPE ;
- les DAB ;
- le Cash Network ;
- les notifications ;
- la plateforme Data ;
- Jini ;
- les bases de données ;
- Redis ;
- les files de messages ;
- les bus d’événements ;
- le stockage ;
- le réseau ;
- les certificats ;
- les sauvegardes ;
- les fournisseurs externes ;
- les infrastructures cloud ;
- les environnements ;
- les incidents ;
- les astreintes ;
- les communications de crise ;
- les post-mortems ;
- les indicateurs de disponibilité ;
- les SLA, SLO et SLI ;
- les audits.

L’objectif est de fournir une plateforme :

- centralisée ;
- temps réel ;
- sécurisée ;
- traçable ;
- multi-pays ;
- multi-environnements ;
- capable de corréler les événements ;
- capable de détecter les incidents avant les utilisateurs ;
- capable de mesurer l’impact métier ;
- capable d’orienter rapidement les équipes ;
- capable de soutenir une croissance nationale puis régionale.

---

# 2. Principes fondamentaux

## 2.1 Tout service critique doit être observable

Aucun service critique ne doit fonctionner sans produire au minimum :

- des logs ;
- des métriques ;
- des traces ;
- des health checks ;
- des alertes ;
- un tableau de bord ;
- un responsable ;
- un runbook ;
- un historique.

---

## 2.2 La supervision technique doit être reliée à l’impact métier

Une erreur technique doit pouvoir être reliée à :

- un paiement ;
- un transfert ;
- un dépôt ;
- un retrait ;
- un client ;
- un commerçant ;
- un agent ;
- un TPE ;
- un DAB ;
- un partenaire ;
- un pays ;
- un service ;
- un produit ;
- un montant ;
- un revenu ;
- une obligation.

---

## 2.3 Les alertes doivent être utiles

Une alerte ne doit pas être créée uniquement parce qu’une métrique existe.

Chaque alerte doit avoir :

- un risque réel ;
- un seuil ;
- un propriétaire ;
- une sévérité ;
- une action ;
- un canal ;
- un runbook ;
- une règle d’escalade ;
- une condition de résolution.

---

## 2.4 Les journaux ne doivent jamais exposer de secrets

Il est interdit d’enregistrer dans les logs :

- PIN ;
- OTP ;
- CVV ;
- mot de passe ;
- numéro complet de carte ;
- clé privée ;
- secret API ;
- token complet ;
- clé de chiffrement ;
- donnée biométrique ;
- document complet ;
- payload financier sensible inutile.

---

## 2.5 Un incident doit avoir un responsable unique

Chaque incident doit avoir :

- un Incident Commander ;
- un responsable technique ;
- un responsable communication ;
- des équipes assignées ;
- une priorité ;
- une chronologie ;
- une décision ;
- une résolution ;
- un post-mortem lorsque requis.

---

## 2.6 Les incidents doivent servir à améliorer le système

Chaque incident important doit conduire à :

- une cause identifiée ;
- une action corrective ;
- une action préventive ;
- un responsable ;
- une échéance ;
- une vérification ;
- une mise à jour de documentation ;
- une amélioration du monitoring.

---

# 3. Périmètre de supervision

La plateforme doit superviser :

- disponibilité ;
- performance ;
- erreurs ;
- sécurité ;
- capacité ;
- coûts ;
- données ;
- intégrations ;
- opérations ;
- utilisateurs ;
- transactions ;
- appareils ;
- réseau ;
- certificats ;
- sauvegardes ;
- déploiements ;
- dépendances externes ;
- qualité de service ;
- incidents ;
- changements ;
- risques opérationnels.

---

# 4. Sources d’observabilité

La plateforme reçoit des données depuis :

- applications mobiles ;
- applications web ;
- TPE ;
- DAB ;
- backend ;
- API Gateway ;
- bases ;
- caches ;
- files ;
- Event Bus ;
- systèmes d’exploitation ;
- conteneurs ;
- orchestrateur ;
- load balancers ;
- firewalls ;
- WAF ;
- CDN ;
- DNS ;
- VPN ;
- bastion ;
- partenaires ;
- banques ;
- Mobile Money ;
- réseaux cartes ;
- fournisseurs SMS ;
- fournisseurs e-mail ;
- outils de sécurité ;
- outils Data ;
- outils IA ;
- pipelines CI/CD ;
- systèmes de sauvegarde.

---

# 5. Architecture logique

Structure recommandée :

```text
observability-platform/
├── logs/
├── metrics/
├── traces/
├── events/
├── health-checks/
├── dashboards/
├── alerts/
├── routing/
├── on-call/
├── incidents/
├── status-pages/
├── communications/
├── runbooks/
├── postmortems/
├── slo/
├── sla/
├── error-budgets/
├── synthetic-monitoring/
├── real-user-monitoring/
├── infrastructure-monitoring/
├── application-monitoring/
├── business-monitoring/
├── partner-monitoring/
├── security-monitoring/
├── cost-monitoring/
├── audit/
└── administration/
```

---

# 6. Environnements surveillés

Les environnements doivent être distingués :

- LOCAL ;
- DEVELOPMENT ;
- DEMO ;
- TEST ;
- RECETTE ;
- PREPRODUCTION ;
- PRODUCTION ;
- DISASTER_RECOVERY.

Les alertes de Production doivent avoir une priorité supérieure.

---

# 7. Logs

Les logs doivent permettre de comprendre :

- ce qui s’est passé ;
- où ;
- quand ;
- pour quel service ;
- pour quel environnement ;
- pour quel pays ;
- pour quelle requête ;
- avec quel résultat ;
- avec quelle erreur ;
- avec quelle dépendance.

---

# 8. Format des logs

Les logs doivent être structurés.

Exemple :

```json
{
  "timestamp": "2026-08-02T20:45:00Z",
  "level": "ERROR",
  "service": "payment-service",
  "environment": "production",
  "country": "ML",
  "requestId": "req_123",
  "correlationId": "corr_456",
  "event": "payment.authorization.failed",
  "partner": "bank-partner",
  "errorCode": "PARTNER_TIMEOUT",
  "durationMs": 12000
}
```

---

# 9. Niveaux de logs

Niveaux recommandés :

- TRACE ;
- DEBUG ;
- INFO ;
- WARN ;
- ERROR ;
- FATAL.

En Production, TRACE et DEBUG doivent être limités.

---

# 10. Contenu minimal d’un log

Chaque log doit pouvoir contenir :

- date ;
- heure ;
- service ;
- version ;
- environnement ;
- pays ;
- niveau ;
- événement ;
- message ;
- request ID ;
- correlation ID ;
- trace ID ;
- utilisateur pseudonymisé si nécessaire ;
- organisation ;
- partenaire ;
- durée ;
- code d’erreur ;
- résultat.

---

# 11. Données sensibles dans les logs

Les données suivantes doivent être :

- supprimées ;
- masquées ;
- tronquées ;
- pseudonymisées ;
- chiffrées si strictement nécessaires.

Exemples :

```text
Carte : **** **** **** 4821
Téléphone : +223 ** ** ** 67
Compte : ********1234
Utilisateur : usr_9f3a...
```

---

# 12. Rétention des logs

La durée dépend :

- de l’environnement ;
- de la sensibilité ;
- du pays ;
- de la réglementation ;
- du service ;
- de la criticité ;
- de l’usage ;
- du coût ;
- de l’audit.

---

# 13. Logs immuables

Les logs critiques doivent être protégés contre :

- modification ;
- suppression ;
- réécriture ;
- altération ;
- désactivation ;
- accès non autorisé.

---

# 14. Recherche dans les logs

La console doit permettre de filtrer par :

- période ;
- service ;
- environnement ;
- pays ;
- version ;
- niveau ;
- utilisateur pseudonymisé ;
- partenaire ;
- transaction ;
- appareil ;
- request ID ;
- correlation ID ;
- code d’erreur ;
- incident.

---

# 15. Métriques

Les métriques doivent couvrir :

- infrastructure ;
- application ;
- base ;
- réseau ;
- partenaires ;
- sécurité ;
- transactions ;
- qualité ;
- coûts ;
- expérience utilisateur ;
- capacité.

---

# 16. Métriques infrastructure

Exemples :

- CPU ;
- mémoire ;
- disque ;
- IOPS ;
- bande passante ;
- connexions ;
- saturation ;
- température appareil si disponible ;
- disponibilité ;
- redémarrages ;
- capacité restante.

---

# 17. Métriques applicatives

Exemples :

- requêtes par seconde ;
- temps de réponse ;
- erreurs ;
- taux de succès ;
- timeouts ;
- exceptions ;
- crashes ;
- appels partenaires ;
- files d’attente ;
- retries ;
- cache hit ratio.

---

# 18. Métriques bases de données

Exemples :

- connexions ;
- requêtes lentes ;
- transactions ;
- locks ;
- deadlocks ;
- réplication ;
- lag ;
- taille ;
- index ;
- cache ;
- erreurs ;
- disponibilité ;
- sauvegardes.

---

# 19. Métriques Redis

Exemples :

- mémoire ;
- clés ;
- évictions ;
- hit ratio ;
- connexions ;
- latence ;
- réplication ;
- erreurs ;
- disponibilité.

---

# 20. Métriques Message Queue

Exemples :

- messages en attente ;
- messages traités ;
- temps d’attente ;
- retries ;
- dead-letter ;
- consumer lag ;
- throughput ;
- erreurs ;
- saturation.

---

# 21. Métriques API Gateway

Exemples :

- trafic ;
- latence ;
- codes HTTP ;
- refus ;
- rate limiting ;
- authentification échouée ;
- partenaires ;
- pays ;
- versions ;
- cache ;
- WAF ;
- DDoS.

---

# 22. Métriques mobiles

Exemples :

- crash-free users ;
- crash-free sessions ;
- démarrages ;
- temps d’ouverture ;
- erreurs réseau ;
- version ;
- appareil ;
- OS ;
- écran ;
- taux d’abandon ;
- mode hors ligne ;
- synchronisation.

---

# 23. Métriques web

Exemples :

- temps de chargement ;
- Largest Contentful Paint ;
- erreurs JavaScript ;
- disponibilité ;
- session ;
- navigateur ;
- appareil ;
- abandon ;
- pages lentes ;
- erreurs API.

---

# 24. Métriques TPE

Exemples :

- terminal en ligne ;
- terminal hors ligne ;
- version ;
- batterie ;
- réseau ;
- imprimante ;
- NFC ;
- paiements ;
- refus ;
- crashes ;
- redémarrages ;
- stockage ;
- synchronisation.

---

# 25. Métriques DAB

Exemples :

- disponibilité ;
- état des cassettes ;
- billets disponibles ;
- capteurs ;
- lecteur de carte ;
- clavier ;
- imprimante ;
- réseau ;
- version ;
- pannes ;
- tentatives ;
- retraits ;
- dépôts ;
- maintenance.

---

# 26. Métriques partenaires

Exemples :

- disponibilité ;
- latence ;
- taux de succès ;
- taux d’échec ;
- timeout ;
- erreurs ;
- volume ;
- montant ;
- SLA ;
- file d’attente ;
- retries ;
- maintenance.

---

# 27. Métriques métier

Exemples :

- paiements réussis ;
- paiements échoués ;
- transferts ;
- dépôts ;
- retraits ;
- règlements ;
- commissions ;
- inscriptions ;
- KYC ;
- cartes ;
- agents actifs ;
- commerçants actifs ;
- TPE actifs ;
- DAB actifs.

---

# 28. Golden Signals

Les services critiques doivent surveiller au minimum :

- latence ;
- trafic ;
- erreurs ;
- saturation.

---

# 29. Méthode RED

Pour les services de requêtes :

- Rate ;
- Errors ;
- Duration.

---

# 30. Méthode USE

Pour les ressources :

- Utilization ;
- Saturation ;
- Errors.

---

# 31. Traces distribuées

Les traces doivent permettre de suivre une opération de bout en bout.

Exemple :

```text
Application Client
→ API Gateway
→ Payment Service
→ Risk Engine
→ Ledger
→ Banque partenaire
→ Notification Service
→ Réponse Client
```

---

# 32. Champs d’une trace

Chaque trace peut contenir :

- trace ID ;
- span ID ;
- parent span ;
- service ;
- opération ;
- début ;
- fin ;
- durée ;
- statut ;
- erreur ;
- environnement ;
- pays ;
- partenaire ;
- version ;
- référence pseudonymisée.

---

# 33. Propagation des identifiants

Les systèmes doivent propager :

```http
X-Request-Id
X-Correlation-Id
Traceparent
Tracestate
```

---

# 34. Échantillonnage des traces

L’échantillonnage peut dépendre :

- de l’environnement ;
- de la criticité ;
- de l’erreur ;
- du service ;
- du partenaire ;
- du montant ;
- du pays ;
- du coût ;
- de la performance.

Les erreurs critiques peuvent être tracées à 100 %.

---

# 35. Événements techniques

Exemples :

```text
service.started
service.stopped
deployment.completed
database.failover
queue.saturated
certificate.expiring
partner.degraded
backup.failed
atm.offline
terminal.crashed
payment.error_rate_high
```

---

# 36. Health checks

Chaque service doit exposer :

- liveness ;
- readiness ;
- startup ;
- dépendances ;
- version ;
- état dégradé ;
- capacité minimale.

---

# 37. Health check simple

Exemple :

```json
{
  "status": "UP",
  "service": "payment-service",
  "version": "2.4.1",
  "environment": "production"
}
```

---

# 38. Health check détaillé

Il peut vérifier :

- base ;
- cache ;
- queue ;
- stockage ;
- partenaire ;
- certificat ;
- dépendance ;
- capacité.

Les détails sensibles doivent rester protégés.

---

# 39. Statuts de santé

- UP ;
- DEGRADED ;
- PARTIAL ;
- DOWN ;
- UNKNOWN ;
- MAINTENANCE.

---

# 40. Monitoring synthétique

Le monitoring synthétique doit simuler :

- connexion ;
- inscription ;
- consultation du solde ;
- paiement ;
- transfert ;
- dépôt ;
- retrait ;
- création de carte ;
- recherche d’agent ;
- ouverture du portail ;
- webhook ;
- API partenaire.

---

# 41. Fréquence des tests synthétiques

La fréquence peut dépendre :

- du service ;
- du pays ;
- de la criticité ;
- de l’environnement ;
- de l’heure ;
- du coût ;
- du partenaire.

---

# 42. Real User Monitoring

Le système peut mesurer l’expérience réelle :

- temps de chargement ;
- erreurs ;
- crash ;
- latence ;
- réseau ;
- appareil ;
- OS ;
- version ;
- écran ;
- parcours ;
- pays.

Les données personnelles doivent être minimisées.

---

# 43. Monitoring des transactions

Le système doit suivre :

- volume ;
- montant ;
- taux de succès ;
- taux de refus ;
- taux d’échec technique ;
- délai ;
- canal ;
- partenaire ;
- pays ;
- produit ;
- version ;
- incident associé.

---

# 44. Monitoring du ledger

Le ledger doit être surveillé sur :

- écritures ;
- équilibre débit/crédit ;
- délais ;
- erreurs ;
- duplications ;
- suspenses ;
- files ;
- locks ;
- réplication ;
- clôtures ;
- disponibilité.

---

# 45. Monitoring Cash Network

Exemples :

- agents actifs ;
- float faible ;
- caisse non clôturée ;
- retraits inhabituels ;
- dépôts inhabituels ;
- terminal agent hors ligne ;
- commission non calculée ;
- écart de caisse ;
- zone sans liquidité.

---

# 46. Monitoring des cartes

Exemples :

- autorisations ;
- refus ;
- activation ;
- blocage ;
- tokenisation ;
- fraude ;
- personnalisation ;
- émission ;
- expiration ;
- incidents réseau.

---

# 47. Monitoring KYC et KYB

Exemples :

- demandes ;
- temps de traitement ;
- échecs ;
- documents rejetés ;
- fournisseur indisponible ;
- file d’attente ;
- dossier bloqué ;
- taux de validation ;
- incidents.

---

# 48. Monitoring Notifications

Exemples :

- push envoyées ;
- SMS envoyés ;
- e-mails ;
- taux de livraison ;
- fournisseurs ;
- coût ;
- retries ;
- dead-letter ;
- retard ;
- OTP non délivrés.

---

# 49. Monitoring Jini

Exemples :

- disponibilité ;
- latence ;
- erreurs ;
- fournisseur ;
- modèle ;
- outil ;
- garde-fou ;
- injection ;
- hallucination signalée ;
- coût ;
- escalade ;
- satisfaction.

---

# 50. Monitoring Data

Exemples :

- pipelines ;
- retards ;
- fraîcheur ;
- qualité ;
- volumes ;
- échecs ;
- duplications ;
- coûts ;
- exports ;
- incidents ;
- rapports.

---

# 51. Monitoring sécurité

La plateforme doit recevoir ou corréler :

- authentifications échouées ;
- MFA échoué ;
- accès inhabituel ;
- élévation de privilège ;
- secret utilisé anormalement ;
- IP malveillante ;
- tentative d’injection ;
- téléchargement massif ;
- désactivation d’alerte ;
- changement de configuration critique.

---

# 52. Monitoring des certificats

Chaque certificat doit être surveillé sur :

- date d’expiration ;
- validité ;
- révocation ;
- chaîne ;
- domaine ;
- partenaire ;
- environnement ;
- algorithme ;
- propriétaire.

---

# 53. Monitoring des sauvegardes

Le système doit suivre :

- sauvegarde démarrée ;
- sauvegarde terminée ;
- sauvegarde échouée ;
- durée ;
- taille ;
- chiffrement ;
- localisation ;
- test de restauration ;
- ancienneté ;
- couverture.

---

# 54. Monitoring des coûts

Le système doit détecter :

- hausse soudaine ;
- service surdimensionné ;
- logs excessifs ;
- stockage anormal ;
- requête coûteuse ;
- environnement oublié ;
- boucle de retry ;
- surconsommation IA ;
- transfert réseau inhabituel.

---

# 55. Tableaux de bord

Types recommandés :

- direction ;
- NOC ;
- SRE ;
- backend ;
- mobile ;
- web ;
- bases ;
- paiements ;
- partenaires ;
- TPE ;
- DAB ;
- Cash Network ;
- sécurité ;
- Data ;
- Jini ;
- coûts ;
- incidents ;
- pays.

---

# 56. Tableau de bord direction

Il peut afficher :

- disponibilité globale ;
- volume ;
- taux de succès ;
- incidents majeurs ;
- pays touchés ;
- utilisateurs affectés ;
- revenus potentiellement impactés ;
- partenaires dégradés ;
- temps moyen de résolution ;
- tendance.

---

# 57. Tableau de bord NOC

Le NOC doit voir :

- services ;
- statuts ;
- alertes ;
- incidents ;
- dépendances ;
- files ;
- bases ;
- partenaires ;
- TPE ;
- DAB ;
- pays ;
- escalades ;
- astreintes.

---

# 58. Tableau de bord d’un service

Il doit contenir :

- disponibilité ;
- trafic ;
- latence ;
- erreurs ;
- saturation ;
- versions ;
- déploiements ;
- dépendances ;
- incidents ;
- SLO ;
- error budget.

---

# 59. Cartographie des dépendances

Le système doit représenter :

```text
Client
→ API Gateway
→ Paiement
→ Risque
→ Ledger
→ Banque
→ Notification
```

Chaque dépendance doit afficher son état.

---

# 60. Service Map

La carte doit permettre de filtrer par :

- environnement ;
- pays ;
- produit ;
- service ;
- partenaire ;
- version ;
- incident ;
- équipe ;
- criticité.

---

# 61. Alertes

Une alerte doit contenir :

- identifiant ;
- titre ;
- description ;
- service ;
- métrique ;
- seuil ;
- valeur ;
- environnement ;
- pays ;
- sévérité ;
- propriétaire ;
- date ;
- runbook ;
- incident lié ;
- statut.

---

# 62. Sévérités d’alerte

- INFO ;
- LOW ;
- MEDIUM ;
- HIGH ;
- CRITICAL.

---

# 63. Sévérités d’incident

Niveaux recommandés :

- SEV-4 : impact faible ;
- SEV-3 : impact limité ;
- SEV-2 : impact important ;
- SEV-1 : incident critique majeur.

---

# 64. Exemples SEV-1

Exemples :

- ledger indisponible ;
- paiements nationaux indisponibles ;
- perte potentielle de données ;
- faille de sécurité active ;
- transactions incorrectes ;
- plusieurs partenaires critiques indisponibles ;
- impossibilité générale de connexion ;
- compromission d’un secret majeur.

---

# 65. Exemples SEV-2

Exemples :

- retraits indisponibles ;
- Mobile Money partiellement indisponible ;
- TPE massivement hors ligne ;
- forte hausse des erreurs ;
- notifications OTP dégradées ;
- réplication base en difficulté ;
- incident régional important.

---

# 66. Exemples SEV-3

Exemples :

- fonctionnalité secondaire indisponible ;
- tableau de bord retardé ;
- un fournisseur non critique indisponible ;
- bug touchant un segment limité ;
- campagne suspendue ;
- lenteur modérée.

---

# 67. Exemples SEV-4

Exemples :

- erreur isolée ;
- problème visuel ;
- documentation incorrecte ;
- alerte informative ;
- anomalie sans impact utilisateur.

---

# 68. Déduplication des alertes

Le système doit éviter :

- plusieurs alertes identiques ;
- alertes répétées à chaque instance ;
- alertes pour la même cause ;
- bruit inutile ;
- escalades multiples non nécessaires.

---

# 69. Corrélation

La plateforme doit pouvoir regrouper :

- erreurs simultanées ;
- même partenaire ;
- même déploiement ;
- même région ;
- même base ;
- même certificat ;
- même cause ;
- même transaction ;
- même incident.

---

# 70. Suppression temporaire d’alertes

Une alerte peut être suspendue pendant :

- maintenance ;
- test ;
- migration ;
- exercice ;
- incident déjà connu ;
- déploiement contrôlé.

La suspension doit être :

- limitée ;
- justifiée ;
- auditée ;
- automatiquement expirante.

---

# 71. Routage des alertes

Le routage peut dépendre :

- service ;
- pays ;
- environnement ;
- sévérité ;
- heure ;
- équipe ;
- partenaire ;
- type ;
- niveau d’impact ;
- astreinte.

---

# 72. Canaux d’alerte

Canaux possibles :

- notification interne ;
- push ;
- SMS ;
- e-mail ;
- appel ;
- messagerie d’équipe ;
- ticket ;
- tableau NOC ;
- portail incident.

---

# 73. Escalade

Exemple :

```text
Alerte HIGH
→ équipe de garde
→ responsable service
→ Incident Commander
→ direction technique
→ direction générale si impact majeur
```

---

# 74. Politique d’acquittement

Une alerte critique doit être acquittée dans un délai défini.

Le système doit enregistrer :

- personne ;
- heure ;
- commentaire ;
- action ;
- incident créé ;
- délai d’acquittement.

---

# 75. Alertes non acquittées

En cas d’absence d’acquittement :

- nouvelle notification ;
- escalade ;
- appel ;
- changement de niveau ;
- affectation de secours ;
- ouverture automatique d’incident.

---

# 76. Astreinte

Le système doit gérer :

- planning ;
- équipe ;
- fuseau ;
- remplaçant ;
- niveau ;
- spécialité ;
- contact ;
- période ;
- absence ;
- rotation ;
- escalade.

---

# 77. Planning d’astreinte

Il peut être défini par :

- semaine ;
- week-end ;
- nuit ;
- jour férié ;
- pays ;
- produit ;
- équipe ;
- niveau de support.

---

# 78. Relève d’astreinte

La relève doit inclure :

- incidents ouverts ;
- alertes surveillées ;
- changements en cours ;
- maintenance ;
- risques ;
- partenaires dégradés ;
- actions attendues ;
- contacts utiles.

---

# 79. Fatigue d’alerte

Le système doit mesurer :

- nombre d’alertes ;
- alertes inutiles ;
- alertes répétées ;
- alertes nocturnes ;
- temps d’acquittement ;
- escalades ;
- surcharge ;
- qualité des seuils.

---

# 80. Centre d’incidents

Le centre doit permettre :

- création ;
- classification ;
- affectation ;
- chronologie ;
- communication ;
- décisions ;
- tâches ;
- participants ;
- preuves ;
- statut ;
- résolution ;
- post-mortem.

---

# 81. Fiche d’incident

Elle doit contenir :

- référence ;
- titre ;
- description ;
- sévérité ;
- service ;
- pays ;
- environnement ;
- début ;
- détection ;
- impact ;
- utilisateurs affectés ;
- partenaires affectés ;
- montant potentiel ;
- Incident Commander ;
- équipes ;
- statut ;
- chronologie ;
- cause ;
- résolution ;
- actions.

---

# 82. Statuts d’un incident

- DETECTED ;
- INVESTIGATING ;
- IDENTIFIED ;
- MITIGATING ;
- MONITORING ;
- RESOLVED ;
- CLOSED ;
- REOPENED.

---

# 83. Incident Commander

Il est responsable de :

- coordination ;
- priorisation ;
- répartition des tâches ;
- décisions ;
- escalade ;
- communication ;
- maintien de la chronologie ;
- clôture ;
- post-mortem.

Il ne doit pas nécessairement effectuer lui-même les corrections techniques.

---

# 84. Rôles pendant un incident

Exemples :

- Incident Commander ;
- Technical Lead ;
- Communications Lead ;
- Operations Lead ;
- Security Lead ;
- Finance Representative ;
- Partner Manager ;
- Scribe ;
- Executive Sponsor.

---

# 85. Chronologie

Chaque événement doit être enregistré avec :

- heure ;
- personne ;
- action ;
- observation ;
- décision ;
- résultat ;
- lien ;
- preuve ;
- communication ;
- changement.

---

# 86. War Room

Pour les incidents majeurs, le système doit pouvoir créer :

- canal dédié ;
- réunion ;
- liste des participants ;
- tableau des actions ;
- chronologie ;
- documents ;
- liens ;
- communication ;
- enregistrement autorisé.

---

# 87. Checklist SEV-1

Exemple :

1. déclarer l’incident ;
2. nommer l’Incident Commander ;
3. figer les changements non essentiels ;
4. identifier l’impact ;
5. vérifier le ledger ;
6. isoler la cause ;
7. lancer la mitigation ;
8. informer les équipes ;
9. informer les utilisateurs si nécessaire ;
10. surveiller la reprise ;
11. clôturer ;
12. lancer le post-mortem.

---

# 88. Gel des déploiements

Pendant un incident critique, il peut être nécessaire de bloquer :

- déploiements ;
- migrations ;
- rotations ;
- campagnes ;
- changements de configuration ;
- feature flags non liés à l’incident.

---

# 89. Mitigation

Une mitigation peut inclure :

- rollback ;
- désactivation d’une fonctionnalité ;
- bascule partenaire ;
- activation du mode dégradé ;
- réduction du trafic ;
- augmentation de capacité ;
- blocage temporaire ;
- restauration ;
- correction de configuration ;
- changement de route.

---

# 90. Résolution

Un incident peut être déclaré résolu lorsque :

- le service est rétabli ;
- les métriques sont revenues à la normale ;
- l’impact est terminé ;
- les données sont vérifiées ;
- les files sont traitées ;
- les partenaires sont synchronisés ;
- la communication finale est envoyée ;
- la surveillance est maintenue.

---

# 91. Réouverture

Un incident peut être réouvert si :

- le problème revient ;
- la mitigation échoue ;
- de nouvelles conséquences apparaissent ;
- les données restent incohérentes ;
- des utilisateurs restent affectés.

---

# 92. Communication interne

La communication interne doit préciser :

- référence ;
- sévérité ;
- début ;
- impact ;
- services touchés ;
- pays ;
- statut ;
- actions ;
- prochaine mise à jour ;
- responsable.

---

# 93. Communication utilisateur

La communication externe doit être :

- claire ;
- factuelle ;
- rassurante ;
- sans détails techniques inutiles ;
- traduite ;
- adaptée au pays ;
- mise à jour ;
- cohérente entre canaux.

---

# 94. Exemples de messages

```text
Nous rencontrons actuellement des difficultés sur certains paiements.
Nos équipes travaillent au rétablissement du service.
Votre solde reste protégé.
```

```text
Le service de retrait est temporairement indisponible dans certaines zones.
Les paiements et transferts restent disponibles.
```

---

# 95. Communications interdites

Ne pas communiquer :

- information non confirmée ;
- détail de sécurité exploitable ;
- secret ;
- nom d’un employé sans raison ;
- accusation non vérifiée ;
- délai irréaliste ;
- cause supposée présentée comme certaine ;
- donnée client.

---

# 96. Page de statut

La page de statut peut afficher :

- services ;
- état ;
- incidents ;
- maintenances ;
- historique ;
- pays ;
- régions ;
- partenaires ;
- abonnements ;
- mises à jour.

---

# 97. Statuts publics

- OPERATIONAL ;
- DEGRADED_PERFORMANCE ;
- PARTIAL_OUTAGE ;
- MAJOR_OUTAGE ;
- MAINTENANCE.

---

# 98. Composants de la page de statut

Exemples :

- application ;
- paiements ;
- transferts ;
- Mobile Money ;
- cartes ;
- retraits ;
- dépôts ;
- portail commerçant ;
- portail agent ;
- API partenaires ;
- notifications ;
- DAB ;
- TPE.

---

# 99. Abonnement aux incidents

Les utilisateurs ou partenaires peuvent s’abonner par :

- e-mail ;
- SMS ;
- webhook ;
- RSS ;
- notification interne.

---

# 100. Maintenance planifiée

Une maintenance doit préciser :

- titre ;
- service ;
- date ;
- heure ;
- durée ;
- pays ;
- impact ;
- responsable ;
- plan ;
- rollback ;
- communication ;
- statut.

---

# 101. Statuts de maintenance

- PLANNED ;
- SCHEDULED ;
- IN_PROGRESS ;
- COMPLETED ;
- CANCELLED ;
- POSTPONED ;
- FAILED.

---

# 102. Fenêtres de maintenance

Elles doivent être choisies selon :

- trafic ;
- pays ;
- jour ;
- heure ;
- partenaire ;
- période financière ;
- campagne ;
- paie ;
- bourse ;
- événements importants.

---

# 103. SLA

Le Service Level Agreement formalise l’engagement de service envers :

- clients ;
- commerçants ;
- agents ;
- banques ;
- institutions ;
- entreprises ;
- partenaires ;
- équipes internes.

---

# 104. SLO

Le Service Level Objective définit un objectif interne mesurable.

Exemples :

- disponibilité ;
- latence ;
- taux de succès ;
- temps de résolution ;
- fraîcheur des données ;
- délai de notification ;
- délai de rapprochement.

---

# 105. SLI

Le Service Level Indicator est la métrique réelle utilisée pour mesurer le SLO.

Exemples :

- pourcentage de requêtes réussies ;
- temps de réponse p95 ;
- taux de paiements terminés ;
- nombre de minutes disponibles ;
- délai moyen de traitement.

---

# 106. Exemple SLO

```text
99,95 % des requêtes de paiement autorisées
doivent être traitées sans erreur technique
sur une période mensuelle.
```

---

# 107. SLO par service

Chaque service critique doit définir :

- disponibilité ;
- latence ;
- erreur ;
- fraîcheur ;
- capacité ;
- récupération ;
- couverture ;
- propriétaire ;
- période.

---

# 108. Error Budget

L’error budget représente la marge d’erreur compatible avec le SLO.

Il permet de décider :

- poursuivre les déploiements ;
- ralentir les changements ;
- prioriser la fiabilité ;
- suspendre les nouveautés ;
- lancer une action corrective.

---

# 109. Consommation de l’error budget

Le système doit suivre :

- budget total ;
- budget consommé ;
- vitesse de consommation ;
- incidents contributeurs ;
- service ;
- période ;
- cause ;
- tendance.

---

# 110. Burn Rate

Le burn rate mesure la vitesse à laquelle l’error budget est consommé.

Une consommation trop rapide doit déclencher une alerte.

---

# 111. Politique liée à l’error budget

Exemple :

```text
Budget sain
→ déploiements normaux

Budget fortement consommé
→ déploiements limités

Budget épuisé
→ priorité à la fiabilité
```

---

# 112. Disponibilité

La disponibilité doit pouvoir être calculée par :

- service ;
- pays ;
- produit ;
- partenaire ;
- canal ;
- environnement ;
- mois ;
- année.

---

# 113. Exclusions de disponibilité

Les exclusions doivent être strictement définies :

- maintenance annoncée ;
- force majeure ;
- dépendance externe contractuellement exclue ;
- environnement de test ;
- interruption volontaire approuvée.

---

# 114. Indicateurs de gestion d’incidents

Exemples :

- MTTD ;
- MTTA ;
- MTTR ;
- MTBF ;
- nombre d’incidents ;
- incidents par service ;
- réouvertures ;
- incidents répétés ;
- temps de communication ;
- temps de mitigation.

---

# 115. MTTD

Mean Time To Detect :

temps moyen entre le début réel du problème et sa détection.

---

# 116. MTTA

Mean Time To Acknowledge :

temps moyen entre l’alerte et son acquittement.

---

# 117. MTTR

Mean Time To Restore :

temps moyen nécessaire pour restaurer le service.

---

# 118. MTBF

Mean Time Between Failures :

temps moyen entre deux pannes.

---

# 119. Post-mortem

Un post-mortem doit être produit pour :

- incident SEV-1 ;
- incident SEV-2 ;
- perte de données ;
- erreur financière ;
- compromission ;
- panne répétée ;
- incident réglementaire ;
- incident partenaire majeur.

---

# 120. Principes du post-mortem

Le post-mortem doit être :

- factuel ;
- sans recherche de coupable ;
- précis ;
- documenté ;
- orienté amélioration ;
- approuvé ;
- suivi ;
- partagé aux équipes concernées.

---

# 121. Contenu du post-mortem

Il doit contenir :

- résumé ;
- impact ;
- début ;
- détection ;
- chronologie ;
- cause racine ;
- facteurs contributifs ;
- résolution ;
- ce qui a bien fonctionné ;
- ce qui a échoué ;
- actions correctives ;
- actions préventives ;
- responsables ;
- échéances.

---

# 122. Analyse de cause racine

Méthodes possibles :

- 5 pourquoi ;
- arbre des causes ;
- analyse chronologique ;
- analyse de dépendances ;
- analyse de changement ;
- reproduction ;
- comparaison ;
- revue des contrôles.

---

# 123. Causes possibles

Exemples :

- bug ;
- configuration ;
- capacité ;
- dépendance ;
- déploiement ;
- certificat ;
- secret ;
- base ;
- réseau ;
- erreur humaine ;
- défaut de monitoring ;
- procédure absente ;
- donnée incorrecte ;
- architecture insuffisante.

---

# 124. Actions correctives

Une action doit contenir :

- description ;
- incident ;
- priorité ;
- responsable ;
- échéance ;
- statut ;
- preuve ;
- résultat ;
- vérification.

---

# 125. Statuts d’une action

- OPEN ;
- PLANNED ;
- IN_PROGRESS ;
- BLOCKED ;
- COMPLETED ;
- VERIFIED ;
- CANCELLED.

---

# 126. Suivi des actions

Les actions en retard doivent déclencher :

- rappel ;
- escalade ;
- reporting ;
- reclassification ;
- revue de risque.

---

# 127. Problèmes récurrents

La plateforme doit détecter :

- mêmes erreurs ;
- mêmes services ;
- mêmes partenaires ;
- mêmes causes ;
- mêmes périodes ;
- mêmes versions ;
- mêmes pays ;
- incidents non corrigés.

---

# 128. Problem Management

Un problème récurrent peut créer un dossier distinct contenant :

- incidents liés ;
- hypothèses ;
- cause ;
- solution temporaire ;
- solution définitive ;
- responsable ;
- priorité ;
- calendrier ;
- risque.

---

# 129. Runbooks

Chaque runbook doit contenir :

- symptôme ;
- impact ;
- vérifications ;
- commandes autorisées ;
- métriques ;
- logs ;
- actions ;
- rollback ;
- escalade ;
- communication ;
- propriétaire ;
- version.

---

# 130. Runbooks prioritaires

Exemples :

- API indisponible ;
- base saturée ;
- file bloquée ;
- ledger dégradé ;
- paiement en échec ;
- partenaire timeout ;
- certificat expiré ;
- TPE hors ligne ;
- DAB hors ligne ;
- SMS OTP non délivré ;
- sauvegarde échouée ;
- failover ;
- attaque ;
- secret compromis.

---

# 131. Automatisation des runbooks

Certaines actions peuvent être automatisées :

- redémarrage ;
- scaling ;
- bascule ;
- purge contrôlée ;
- rotation ;
- désactivation de route ;
- activation du mode dégradé ;
- rollback ;
- création d’incident ;
- communication.

Les actions sensibles doivent rester protégées.

---

# 132. Auto-remédiation

L’auto-remédiation peut être autorisée si :

- le cas est connu ;
- l’action est réversible ;
- le risque est faible ;
- le test est validé ;
- le périmètre est limité ;
- l’audit est actif ;
- l’escalade existe.

---

# 133. Limites de l’auto-remédiation

Elle ne doit pas :

- modifier le ledger ;
- supprimer une donnée ;
- effacer un audit ;
- désactiver une sécurité critique ;
- effectuer une migration destructive ;
- résoudre seule une fraude ;
- modifier une commission ;
- révoquer massivement des comptes sans validation.

---

# 134. Déploiements et incidents

La plateforme doit corréler :

- version ;
- commit ;
- pipeline ;
- heure ;
- service ;
- erreur ;
- incident ;
- rollback ;
- métrique ;
- pays.

---

# 135. Change Intelligence

Le système doit pouvoir identifier :

- dernier déploiement ;
- dernière configuration ;
- dernière migration ;
- dernier secret ;
- dernier certificat ;
- dernier feature flag ;
- dernière règle réseau ;
- dernier changement partenaire.

---

# 136. Alerte après déploiement

Une période renforcée de surveillance doit suivre chaque déploiement Production.

Exemples :

- 15 minutes ;
- 30 minutes ;
- 1 heure ;
- période configurable.

---

# 137. Détection d’anomalie

Le système peut détecter :

- hausse inhabituelle ;
- chute de trafic ;
- latence anormale ;
- erreurs inhabituelles ;
- volume anormal ;
- comportement inattendu ;
- saturation ;
- coût anormal ;
- panne partielle.

---

# 138. Seuils dynamiques

Les seuils peuvent utiliser :

- moyenne mobile ;
- historique ;
- saisonnalité ;
- jour ;
- heure ;
- pays ;
- événement ;
- partenaire ;
- percentile ;
- modèle statistique.

---

# 139. Intelligence artificielle pour l’observabilité

L’IA peut aider à :

- regrouper les alertes ;
- résumer un incident ;
- proposer une cause ;
- rechercher un runbook ;
- générer une chronologie ;
- identifier un changement récent ;
- suggérer une action ;
- détecter une anomalie ;
- préparer un post-mortem.

Elle ne doit pas prendre seule une décision critique non réversible.

---

# 140. Résumé automatique d’incident

Le résumé peut inclure :

- impact ;
- services ;
- pays ;
- durée ;
- métriques ;
- causes probables ;
- actions ;
- statut ;
- prochaine étape.

---

# 141. Sécurité de la plateforme d’observabilité

Mesures principales :

- MFA ;
- RBAC ;
- ABAC ;
- chiffrement ;
- accès limité ;
- données masquées ;
- secrets séparés ;
- audit ;
- rétention ;
- verrouillage ;
- réseau privé ;
- IP autorisée.

---

# 142. Accès aux logs sensibles

L’accès peut exiger :

- rôle spécifique ;
- justification ;
- durée limitée ;
- approbation ;
- environnement ;
- périmètre ;
- audit ;
- masquage.

---

# 143. Protection contre les abus internes

Le système doit détecter :

- recherche massive ;
- export massif ;
- accès hors horaires ;
- accès hors pays ;
- désactivation d’alertes ;
- modification de seuil ;
- suppression de logs ;
- accès à un incident sensible ;
- compte partagé ;
- contournement de rétention.

---

# 144. Administration centrale

L’administration peut gérer :

- sources ;
- logs ;
- métriques ;
- traces ;
- tableaux de bord ;
- alertes ;
- seuils ;
- routage ;
- astreintes ;
- incidents ;
- maintenances ;
- SLO ;
- SLA ;
- error budgets ;
- runbooks ;
- post-mortems ;
- actions ;
- rétention ;
- accès ;
- intégrations ;
- coûts ;
- audits.

---

# 145. Rôles

Exemples :

```text
OBSERVABILITY_ADMIN
NOC_OPERATOR
SITE_RELIABILITY_ENGINEER
INCIDENT_COMMANDER
ON_CALL_ENGINEER
APPLICATION_OWNER
DATABASE_OPERATOR
NETWORK_OPERATOR
SECURITY_OPERATOR
PARTNER_OPERATIONS_MANAGER
SERVICE_LEVEL_MANAGER
POSTMORTEM_REVIEWER
AUDITOR
VIEWER
```

---

# 146. Permissions

Exemples :

```text
observability.dashboard.read
observability.log.read
observability.log.export
observability.metric.read
observability.trace.read
observability.alert.read
observability.alert.manage
observability.incident.create
observability.incident.manage
observability.incident.close
observability.oncall.manage
observability.runbook.manage
observability.slo.manage
observability.postmortem.create
observability.postmortem.approve
observability.audit.read
```

---

# 147. Approbations

Peuvent exiger une approbation :

- suppression de logs ;
- modification de rétention ;
- désactivation d’une alerte critique ;
- modification d’un SLO ;
- export sensible ;
- fermeture d’un SEV-1 ;
- modification d’un runbook critique ;
- auto-remédiation ;
- changement de routage critique ;
- publication d’un post-mortem externe.

---

# 148. Double validation

Peut être exigée pour :

- désactivation globale d’alertes ;
- suppression de preuves ;
- accès à des logs hautement sensibles ;
- clôture d’un incident financier majeur ;
- modification d’un SLA contractuel ;
- activation d’une auto-remédiation critique ;
- suppression d’un historique ;
- export massif d’incidents.

---

# 149. API

Exemples :

```http
GET    /observability/dashboards
GET    /observability/logs
GET    /observability/metrics
GET    /observability/traces

GET    /observability/alerts
POST   /observability/alerts
POST   /observability/alerts/{id}/acknowledge

GET    /observability/incidents
POST   /observability/incidents
PATCH  /observability/incidents/{id}
POST   /observability/incidents/{id}/resolve

GET    /observability/on-call
POST   /observability/on-call/schedules

GET    /observability/slo
POST   /observability/slo
GET    /observability/error-budgets

GET    /observability/runbooks
POST   /observability/runbooks

GET    /observability/postmortems
POST   /observability/postmortems

GET    /observability/audit
```

---

# 150. Webhooks internes

Événements possibles :

```text
observability.alert.created
observability.alert.acknowledged
observability.alert.escalated
observability.incident.created
observability.incident.updated
observability.incident.mitigated
observability.incident.resolved
observability.incident.reopened
observability.maintenance.started
observability.maintenance.completed
observability.slo.breached
observability.error_budget.warning
observability.postmortem.created
observability.action.overdue
observability.security.alert
```

---

# 151. Intégrations

La plateforme doit pouvoir se connecter à :

- infrastructure cloud ;
- orchestrateur ;
- API Gateway ;
- backend ;
- bases ;
- caches ;
- files ;
- Event Bus ;
- applications mobiles ;
- applications web ;
- TPE ;
- DAB ;
- banques ;
- Mobile Money ;
- réseaux cartes ;
- notifications ;
- support ;
- sécurité ;
- Finance ;
- Data ;
- Jini ;
- CI/CD ;
- gestion de projets ;
- messagerie ;
- téléphonie ;
- page de statut.

---

# 152. Multi-pays

Chaque pays peut avoir :

- tableaux de bord ;
- seuils ;
- astreintes ;
- équipes ;
- horaires ;
- SLA ;
- partenaires ;
- page de statut ;
- canaux ;
- langues ;
- incidents ;
- règles de communication ;
- calendriers.

---

# 153. Fuseaux horaires

Les incidents doivent conserver :

- heure UTC ;
- heure locale ;
- fuseau ;
- pays ;
- date de début ;
- date de détection ;
- date de résolution ;
- date de clôture.

---

# 154. Coûts d’observabilité

Le système doit suivre :

- volume de logs ;
- stockage ;
- requêtes ;
- métriques ;
- traces ;
- rétention ;
- tableaux de bord ;
- alertes ;
- pays ;
- environnement ;
- équipe ;
- service.

---

# 155. Optimisation des coûts

Mesures possibles :

- réduction des logs inutiles ;
- échantillonnage ;
- compression ;
- archivage ;
- rétention différenciée ;
- suppression automatique ;
- filtrage ;
- agrégation ;
- limitation des traces ;
- gestion des index.

---

# 156. Modèles principaux

- ObservabilitySource
- LogEntry
- LogRetentionPolicy
- MetricDefinition
- MetricDataPoint
- Trace
- TraceSpan
- HealthCheck
- SyntheticCheck
- RealUserMetric
- ServiceMap
- ServiceDependency
- Dashboard
- DashboardWidget
- AlertRule
- Alert
- AlertAcknowledgement
- AlertRoutingRule
- OnCallSchedule
- OnCallShift
- Incident
- IncidentTimelineEntry
- IncidentParticipant
- IncidentCommunication
- MaintenanceWindow
- ServiceLevelIndicator
- ServiceLevelObjective
- ServiceLevelAgreement
- ErrorBudget
- Runbook
- Postmortem
- CorrectiveAction
- RecurringProblem
- ObservabilityApproval
- ObservabilityCost
- ObservabilityAudit

---

# 157. Analytics

Événements possibles :

```text
observability_dashboard_opened
observability_log_search_started
observability_trace_opened
observability_alert_acknowledged
observability_incident_created
observability_incident_resolved
observability_runbook_opened
observability_slo_breached
observability_error_budget_warning
observability_postmortem_published
observability_action_completed
observability_access_denied
```

---

# 158. Données analytics interdites

Ne pas transmettre :

- logs complets ;
- secrets ;
- tokens ;
- cartes ;
- OTP ;
- PIN ;
- payloads financiers ;
- documents ;
- données clients ;
- messages privés ;
- contenu sensible d’incident ;
- clés privées.

---

# 159. Tests

- tests de collecte de logs ;
- tests de structure ;
- tests de masquage ;
- tests de rétention ;
- tests d’immutabilité ;
- tests de recherche ;
- tests de métriques ;
- tests de traces ;
- tests de propagation ;
- tests de health checks ;
- tests synthétiques ;
- tests RUM ;
- tests de monitoring transactionnel ;
- tests ledger ;
- tests cartes ;
- tests Cash Network ;
- tests notifications ;
- tests Jini ;
- tests Data ;
- tests partenaires ;
- tests certificats ;
- tests sauvegardes ;
- tests tableaux de bord ;
- tests cartographie ;
- tests alertes ;
- tests déduplication ;
- tests corrélation ;
- tests routage ;
- tests escalade ;
- tests acquittement ;
- tests astreinte ;
- tests War Room ;
- tests incidents ;
- tests communication ;
- tests page de statut ;
- tests maintenance ;
- tests SLA ;
- tests SLO ;
- tests SLI ;
- tests error budget ;
- tests burn rate ;
- tests MTTD ;
- tests MTTA ;
- tests MTTR ;
- tests post-mortem ;
- tests actions correctives ;
- tests problèmes récurrents ;
- tests runbooks ;
- tests auto-remédiation ;
- tests changements ;
- tests détection d’anomalie ;
- tests IA ;
- tests sécurité ;
- tests rôles ;
- tests multi-pays ;
- tests coûts ;
- tests audit ;
- tests performance ;
- tests haute disponibilité.

---

# 160. Règles métier

1. Tout service critique doit être observable.
2. Les logs sont structurés.
3. Les secrets ne sont jamais enregistrés.
4. Les logs critiques sont immuables.
5. Les requêtes utilisent un identifiant de corrélation.
6. Les métriques couvrent les Golden Signals.
7. Les traces suivent les opérations de bout en bout.
8. Les health checks n’exposent pas de données sensibles.
9. Les alertes possèdent un propriétaire.
10. Les alertes critiques possèdent un runbook.
11. Les alertes sont dédupliquées.
12. Les alertes non acquittées sont escaladées.
13. Chaque incident possède un Incident Commander.
14. Les incidents majeurs utilisent une War Room.
15. Les communications sont factuelles.
16. Les pages de statut sont mises à jour.
17. Les SLO sont mesurables.
18. Les error budgets sont suivis.
19. Les incidents SEV-1 et SEV-2 ont un post-mortem.
20. Les actions correctives ont un responsable.
21. Les problèmes récurrents sont regroupés.
22. L’auto-remédiation reste réversible.
23. Les changements sont corrélés aux incidents.
24. Le demandeur ne valide pas seul une action critique.
25. Les audits sont immuables.

---

# 161. Critères d’acceptation

La Plateforme d’observabilité, de supervision et de gestion des incidents techniques Mansa est validée lorsque :

- tous les services critiques produisent des logs ;
- les logs sont structurés ;
- les données sensibles sont masquées ;
- les logs critiques sont immuables ;
- la recherche centralisée fonctionne ;
- les métriques infrastructure sont disponibles ;
- les métriques applicatives sont disponibles ;
- les bases sont surveillées ;
- Redis est surveillé ;
- les files sont surveillées ;
- l’API Gateway est surveillée ;
- les applications mobiles sont surveillées ;
- les applications web sont surveillées ;
- les TPE sont surveillés ;
- les DAB sont surveillés ;
- les partenaires sont surveillés ;
- les transactions sont surveillées ;
- le ledger est surveillé ;
- le Cash Network est surveillé ;
- les cartes sont surveillées ;
- le KYC et le KYB sont surveillés ;
- les notifications sont surveillées ;
- Jini est surveillé ;
- la plateforme Data est surveillée ;
- les certificats sont surveillés ;
- les sauvegardes sont surveillées ;
- les coûts sont surveillés ;
- les traces distribuées fonctionnent ;
- les identifiants de corrélation sont propagés ;
- les health checks sont disponibles ;
- le monitoring synthétique fonctionne ;
- le Real User Monitoring est disponible ;
- les tableaux de bord sont centralisés ;
- la cartographie des dépendances fonctionne ;
- les alertes sont classées par sévérité ;
- les alertes sont dédupliquées ;
- la corrélation fonctionne ;
- le routage est configurable ;
- les alertes critiques sont escaladées ;
- les plannings d’astreinte sont administrables ;
- le centre d’incidents est disponible ;
- les SEV-1 et SEV-2 sont formalisés ;
- la War Room peut être créée ;
- la chronologie est conservée ;
- les communications internes sont centralisées ;
- les communications utilisateur sont administrables ;
- la page de statut est disponible ;
- les maintenances sont planifiables ;
- les SLA sont gérés ;
- les SLO sont mesurables ;
- les SLI sont définis ;
- les error budgets sont calculés ;
- les burn rates sont surveillés ;
- le MTTD est calculé ;
- le MTTA est calculé ;
- le MTTR est calculé ;
- les post-mortems sont centralisés ;
- les actions correctives sont suivies ;
- les problèmes récurrents sont détectés ;
- les runbooks sont disponibles ;
- l’auto-remédiation est encadrée ;
- les déploiements sont corrélés aux incidents ;
- les changements récents sont visibles ;
- la détection d’anomalie fonctionne ;
- l’IA peut assister sans prendre seule une décision critique ;
- les accès sensibles sont protégés ;
- les rôles et permissions sont définis ;
- le multi-pays est pris en charge ;
- les coûts d’observabilité sont mesurés ;
- les audits sont immuables ;
- les tests couvrent les parcours essentiels.
