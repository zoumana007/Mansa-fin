# 24 — Architecture événementielle, files, webhooks et traitements asynchrones de Mansa

## 1. Objet du document

Ce document définit l’architecture officielle des échanges asynchrones de Mansa.

Il couvre :

- les événements métier ;
- les événements techniques ;
- les files de messages ;
- les workers ;
- les tâches différées ;
- les tâches planifiées ;
- les webhooks entrants ;
- les webhooks sortants ;
- les retries ;
- les dead-letter queues ;
- l’idempotence ;
- l’ordre des messages ;
- les doublons ;
- les statuts incertains ;
- les sagas ;
- les compensations ;
- les traitements batch ;
- les imports ;
- les exports ;
- les notifications ;
- les synchronisations partenaires ;
- le rapprochement ;
- l’observabilité ;
- la sécurité ;
- l’audit ;
- la reprise après incident.

L’objectif est de permettre à Mansa de traiter de manière fiable des opérations qui :

- ne doivent pas bloquer une requête utilisateur ;
- prennent du temps ;
- dépendent d’un partenaire ;
- doivent être reprises après une panne ;
- nécessitent plusieurs étapes ;
- doivent être rejouées ;
- doivent supporter une forte montée en charge ;
- doivent rester traçables de bout en bout.

---

# 2. Principes fondamentaux

## 2.1 Synchrone lorsque le résultat est immédiatement nécessaire

Une communication synchrone peut être utilisée lorsque :

- l’utilisateur attend une réponse immédiate ;
- le résultat peut être calculé rapidement ;
- aucun traitement long n’est nécessaire ;
- l’indisponibilité du service doit empêcher l’action ;
- la cohérence immédiate est obligatoire.

Exemples :

- authentification ;
- vérification de permission ;
- consultation de solde officiel ;
- prévisualisation de frais ;
- validation d’un bénéficiaire ;
- vérification d’une version.

---

## 2.2 Asynchrone pour les traitements longs ou distribués

Un traitement asynchrone doit être privilégié pour :

- notification ;
- génération de document ;
- rapprochement ;
- export ;
- import ;
- traitement de fichier ;
- synchronisation partenaire ;
- analyse de fraude secondaire ;
- analytics ;
- indexation ;
- mise à jour de recherche ;
- campagne ;
- traitement Jini non immédiat ;
- traitement batch ;
- relance de webhook.

---

## 2.3 Aucun faux succès

Le fait qu’un message soit placé dans une file ne signifie pas que l’opération finale a réussi.

Le système doit distinguer :

- demande acceptée ;
- traitement programmé ;
- traitement en cours ;
- traitement réussi ;
- traitement partiellement réussi ;
- traitement échoué ;
- traitement expiré ;
- traitement placé en attente ;
- statut inconnu.

---

## 2.4 Livraison au moins une fois

L’architecture doit considérer qu’un message peut être livré plusieurs fois.

Par conséquent :

- les consommateurs doivent être idempotents ;
- les doublons doivent être détectés ;
- les opérations financières ne doivent jamais être exécutées deux fois ;
- le résultat déjà produit doit pouvoir être retourné.

---

## 2.5 La file n’est pas une base métier

Une file transporte un message.

Elle ne remplace pas :

- PostgreSQL ;
- le ledger ;
- le journal d’audit ;
- la source officielle du statut ;
- l’historique métier.

Le statut durable doit être conservé dans une base appropriée.

---

# 3. Composants principaux

L’architecture asynchrone de Mansa peut comprendre :

```text
Producteurs
    │
    ├── API Gateway
    ├── Services métier
    ├── Applications internes
    ├── Schedulers
    ├── Webhooks partenaires
    └── Portail Admin
          │
          ▼
Event Bus / Message Broker
          │
    ├── Files métier
    ├── Files prioritaires
    ├── Files de retry
    ├── Dead-letter queues
    └── Topics d’événements
          │
          ▼
Consommateurs / Workers
    ├── Notifications
    ├── Documents
    ├── Rapprochement
    ├── Paiements
    ├── Fraud
    ├── Analytics
    ├── Webhooks sortants
    ├── Jini
    └── Synchronisations
```

---

# 4. Technologies possibles

Selon le volume et la maturité du projet, Mansa peut utiliser :

- Redis Streams ;
- BullMQ ;
- RabbitMQ ;
- Apache Kafka ;
- service managé équivalent ;
- scheduler distribué ;
- stockage durable de jobs.

La première version peut utiliser une solution plus simple, à condition qu’elle supporte :

- persistance ;
- retries ;
- délais ;
- priorités ;
- concurrence ;
- dead-letter queue ;
- observabilité ;
- reprise après redémarrage.

---

# 5. Types d’événements

## 5.1 Événements métier

Ils décrivent un fait important du domaine.

Exemples :

```text
user.created
user.kyc.approved
wallet.created
payment.initiated
payment.completed
payment.failed
card.activated
merchant.approved
terminal.assigned
refund.completed
support.ticket.created
```

Un événement métier exprime un fait déjà survenu.

---

## 5.2 Commandes asynchrones

Une commande demande l’exécution d’une action.

Exemples :

```text
notification.send
document.generate
partner.payment.verify
reconciliation.run
export.generate
webhook.deliver
fraud.case.review
```

Une commande peut échouer ou être refusée.

---

## 5.3 Événements techniques

Ils décrivent l’état d’un composant.

Exemples :

```text
worker.started
worker.failed
queue.saturated
database.replication_lag_detected
certificate.expiring
cache.invalidated
```

---

## 5.4 Événements d’intégration

Ils sont destinés à relier plusieurs services ou partenaires.

Exemples :

```text
partner.mobile_money.confirmed
partner.card.authorization.received
public_service.payment.acknowledged
```

---

# 6. Convention de nommage

Format recommandé :

```text
domain.entity.action
```

Exemples :

```text
payment.transaction.completed
merchant.establishment.activated
card.authorization.declined
notification.delivery.failed
```

Les noms doivent être :

- stables ;
- explicites ;
- versionnables ;
- indépendants du texte affiché ;
- documentés.

---

# 7. Structure standard d’un événement

Chaque événement doit contenir au minimum :

```json
{
  "eventId": "evt_123",
  "eventType": "payment.completed",
  "eventVersion": 1,
  "occurredAt": "2026-08-02T12:00:00Z",
  "producer": "payment-service",
  "environment": "production",
  "country": "ML",
  "correlationId": "cor_123",
  "causationId": "cmd_456",
  "aggregateId": "pay_789",
  "data": {}
}
```

Champs recommandés :

- identifiant unique ;
- type ;
- version ;
- date ;
- producteur ;
- environnement ;
- pays ;
- tenant ;
- corrélation ;
- causalité ;
- acteur ;
- ressource ;
- données ;
- métadonnées ;
- niveau de sensibilité ;
- trace ID.

---

# 8. Versionnement des événements

Chaque événement doit avoir une version de schéma.

Exemple :

```text
payment.completed.v1
payment.completed.v2
```

ou :

```json
{
  "eventType": "payment.completed",
  "eventVersion": 2
}
```

Un changement incompatible nécessite :

- nouvelle version ;
- documentation ;
- période de compatibilité ;
- adaptation des consommateurs ;
- suivi d’adoption ;
- date de retrait.

---

# 9. Compatibilité

Bonnes pratiques :

- ajouter des champs optionnels ;
- ne pas changer le sens d’un champ ;
- ne pas supprimer brutalement ;
- ignorer les champs inconnus ;
- prévoir une valeur `UNKNOWN` ;
- utiliser des adaptateurs ;
- tester les consommateurs.

---

# 10. Producteurs

Un producteur doit :

- créer un identifiant unique ;
- renseigner la corrélation ;
- utiliser un schéma validé ;
- éviter les données sensibles inutiles ;
- garantir la persistance ;
- enregistrer le statut de publication ;
- supporter les retries.

---

# 11. Consommateurs

Un consommateur doit :

- valider le message ;
- vérifier la version ;
- appliquer l’idempotence ;
- traiter ou rejeter proprement ;
- journaliser le résultat ;
- produire des métriques ;
- gérer les erreurs ;
- envoyer vers la dead-letter queue si nécessaire.

---

# 12. Pattern Outbox

Pour éviter qu’une opération soit enregistrée en base sans publier son événement, utiliser le pattern Outbox.

Exemple :

1. créer le paiement ;
2. créer l’événement Outbox dans la même transaction ;
3. valider la transaction ;
4. publier l’événement ;
5. marquer l’événement comme publié.

Modèles possibles :

- OutboxEvent
- OutboxAttempt
- OutboxStatus
- OutboxLock

---

# 13. Pattern Inbox

Pour éviter le retraitement d’un message déjà consommé, utiliser une Inbox.

Elle conserve :

- eventId ;
- consumer ;
- date de réception ;
- statut ;
- résultat ;
- nombre de tentatives ;
- empreinte ;
- expiration.

---

# 14. Idempotence des consommateurs

Exemple :

Si `payment.completed` est reçu deux fois, le consommateur de notification ne doit pas envoyer deux SMS identiques si la règle l’interdit.

Pour une opération financière, le consommateur doit vérifier :

- identifiant de commande ;
- clé d’idempotence ;
- référence métier ;
- état existant ;
- résultat déjà appliqué.

---

# 15. Ordre des événements

L’ordre global de tous les événements n’est pas garanti.

Lorsque l’ordre est important, utiliser :

- clé de partition ;
- séquence ;
- version d’agrégat ;
- timestamp serveur ;
- verrouillage ;
- sérialisation par ressource.

Exemples :

- événements d’une même carte ;
- écritures d’un même wallet ;
- statuts d’un même paiement ;
- opérations d’un même terminal.

---

# 16. Séquence d’agrégat

Un événement peut contenir :

```json
{
  "aggregateId": "pay_123",
  "aggregateVersion": 7
}
```

Le consommateur peut détecter :

- événement en retard ;
- événement manquant ;
- doublon ;
- ordre impossible.

---

# 17. Files métier

Files possibles :

- payments ;
- notifications ;
- documents ;
- webhooks ;
- reconciliation ;
- fraud ;
- support ;
- analytics ;
- imports ;
- exports ;
- jini ;
- public-services ;
- terminal-sync.

Chaque file doit avoir :

- propriétaire ;
- volume prévu ;
- priorité ;
- timeout ;
- retry ;
- dead-letter queue ;
- métriques ;
- politique de rétention.

---

# 18. Files prioritaires

Une file peut distinguer :

- critique ;
- élevée ;
- normale ;
- basse.

Exemples :

- alerte sécurité : critique ;
- confirmation de paiement : élevée ;
- campagne marketing : basse ;
- génération de rapport : normale.

Les tâches de faible priorité ne doivent pas bloquer les opérations critiques.

---

# 19. Files différées

Une tâche peut être planifiée pour plus tard.

Exemples :

- rappel ;
- expiration ;
- relance ;
- vérification de statut ;
- paiement programmé ;
- notification avant échéance ;
- fermeture automatique de ticket.

---

# 20. Workers

Chaque worker doit définir :

- type de tâche ;
- nombre d’instances ;
- concurrence ;
- mémoire ;
- timeout ;
- stratégie de retry ;
- arrêt propre ;
- métriques ;
- health check ;
- version.

---

# 21. Scalabilité des workers

Les workers doivent pouvoir être augmentés horizontalement.

L’autoscaling peut utiliser :

- taille de file ;
- âge du plus ancien message ;
- taux d’arrivée ;
- temps de traitement ;
- CPU ;
- mémoire ;
- latence cible.

---

# 22. Arrêt propre

Lors d’un déploiement ou redémarrage, le worker doit :

- arrêter de prendre de nouveaux messages ;
- terminer ou libérer le message en cours ;
- enregistrer son checkpoint ;
- éviter la perte ;
- éviter une double exécution non contrôlée.

---

# 23. Timeout d’un job

Chaque type de job doit avoir un timeout adapté.

Un job dépassant le timeout peut être :

- interrompu ;
- marqué échoué ;
- remis en file ;
- placé en vérification ;
- envoyé en dead-letter queue.

Un timeout ne doit pas provoquer une relance aveugle d’une opération financière.

---

# 24. Retry

Une politique de retry doit définir :

- nombre maximal ;
- délai initial ;
- backoff ;
- jitter ;
- erreurs réessayables ;
- erreurs définitives ;
- date d’expiration ;
- file de retry ;
- alerte.

---

# 25. Backoff exponentiel

Exemple :

```text
Tentative 1 : 10 secondes
Tentative 2 : 30 secondes
Tentative 3 : 2 minutes
Tentative 4 : 10 minutes
Tentative 5 : 1 heure
```

Le rythme dépend du partenaire et de l’opération.

---

# 26. Erreurs non réessayables

Exemples :

- schéma invalide ;
- permission refusée ;
- signature invalide ;
- identifiant inconnu ;
- montant impossible ;
- compte clôturé ;
- version non supportée ;
- commande déjà annulée.

---

# 27. Dead-Letter Queue

Une dead-letter queue reçoit les messages non traitables après plusieurs tentatives.

Elle doit permettre :

- recherche ;
- filtrage ;
- inspection ;
- masquage des données sensibles ;
- correction ;
- rejeu ;
- abandon ;
- export ;
- audit ;
- création d’incident.

---

# 28. Rejeu

Un rejeu doit être :

- autorisé ;
- justifié ;
- limité ;
- idempotent ;
- audité ;
- contrôlé par permission ;
- éventuellement soumis à double validation.

Le rejeu massif doit être particulièrement protégé.

---

# 29. Statuts d’un job

Valeurs possibles :

- CREATED ;
- QUEUED ;
- SCHEDULED ;
- RUNNING ;
- RETRYING ;
- SUCCEEDED ;
- PARTIALLY_SUCCEEDED ;
- FAILED ;
- DEAD_LETTERED ;
- CANCELLED ;
- EXPIRED ;
- UNKNOWN.

---

# 30. Persistance des jobs

Les jobs importants doivent avoir une représentation durable en base.

Modèles possibles :

- AsyncJob
- AsyncJobAttempt
- AsyncJobResult
- AsyncJobError
- AsyncJobSchedule
- AsyncJobAudit

---

# 31. Tâches planifiées

Exemples :

- rapprochement quotidien ;
- expiration de sessions ;
- expiration d’OTP ;
- expiration de cartes virtuelles ;
- calcul de rapports ;
- clôture ;
- renouvellement ;
- purge ;
- anonymisation ;
- vérification de certificats ;
- relance de webhooks ;
- contrôle de sauvegardes.

---

# 32. Scheduler distribué

Dans un environnement multi-instance, une tâche planifiée ne doit pas s’exécuter plusieurs fois sans contrôle.

Utiliser :

- verrou distribué ;
- leader election ;
- job unique ;
- clé d’idempotence ;
- calendrier central ;
- lease avec expiration.

---

# 33. Fuseaux horaires

Les tâches sont stockées en UTC.

L’exécution peut dépendre de :

- pays ;
- fuseau ;
- organisation ;
- utilisateur ;
- calendrier ;
- jours ouvrés ;
- jours fériés.

---

# 34. Tâches récurrentes

Une tâche récurrente doit contenir :

- fréquence ;
- date de début ;
- date de fin ;
- fuseau ;
- règle ;
- propriétaire ;
- dernière exécution ;
- prochaine exécution ;
- statut ;
- nombre d’échecs.

---

# 35. Webhooks entrants

Un webhook entrant doit être traité en plusieurs étapes :

1. réception ;
2. validation de la signature ;
3. validation du schéma ;
4. détection de doublon ;
5. réponse rapide ;
6. stockage sécurisé ;
7. mise en file ;
8. traitement métier ;
9. audit ;
10. rapprochement éventuel.

---

# 36. Réponse rapide aux partenaires

Le endpoint webhook ne doit pas effectuer un traitement long avant de répondre.

Il doit généralement :

- valider ;
- enregistrer ;
- mettre en file ;
- répondre avec un statut approprié.

---

# 37. Signature des webhooks

Méthodes possibles :

- HMAC ;
- signature asymétrique ;
- certificat ;
- mTLS ;
- secret rotatif ;
- timestamp signé.

Le système doit vérifier :

- signature ;
- date ;
- nonce ;
- tolérance temporelle ;
- secret actif ;
- version.

---

# 38. Protection contre le rejeu

Un webhook doit contenir un élément unique.

Exemples :

- eventId ;
- nonce ;
- timestamp ;
- identifiant partenaire ;
- empreinte.

Un événement déjà accepté doit être détecté.

---

# 39. Stockage du contenu brut

Le contenu brut peut être conservé temporairement pour :

- preuve ;
- vérification de signature ;
- investigation ;
- rapprochement.

Il doit être :

- chiffré ;
- limité ;
- masqué ;
- soumis à une rétention ;
- accessible par permission.

---

# 40. Webhooks sortants

Mansa peut envoyer des webhooks à :

- commerçants ;
- partenaires ;
- banques ;
- organismes publics ;
- services professionnels ;
- plateformes intégrées.

---

# 41. Structure d’un webhook sortant

Exemple :

```json
{
  "id": "wh_evt_123",
  "type": "payment.completed",
  "version": 1,
  "createdAt": "2026-08-02T12:00:00Z",
  "data": {
    "paymentId": "pay_123",
    "status": "COMPLETED"
  }
}
```

---

# 42. Livraison d’un webhook sortant

Le système doit :

- signer ;
- envoyer ;
- enregistrer la réponse ;
- gérer le timeout ;
- réessayer ;
- détecter l’expiration ;
- désactiver un endpoint défaillant si nécessaire ;
- alerter le destinataire.

---

# 43. Réponses aux webhooks

Statuts à interpréter :

- 2xx : accepté ;
- 4xx : erreur potentiellement définitive ;
- 401/403 : problème d’authentification ;
- 404/410 : endpoint supprimé ;
- 429 : limitation ;
- 5xx : erreur temporaire.

La stratégie doit rester configurable par partenaire.

---

# 44. Endpoints webhook

Chaque endpoint doit contenir :

- URL ;
- propriétaire ;
- événements abonnés ;
- secret de référence ;
- statut ;
- environnement ;
- pays ;
- version ;
- date de création ;
- date de dernière réussite ;
- taux d’erreur ;
- limite ;
- certificat éventuel.

---

# 45. Rotation des secrets webhook

La rotation doit permettre une période de coexistence entre :

- ancien secret ;
- nouveau secret.

La date de fin de validité de l’ancien secret doit être définie.

---

# 46. Test de webhook

Le portail partenaire doit permettre :

- envoyer un événement de test ;
- consulter la signature ;
- voir la réponse ;
- voir le temps ;
- consulter les erreurs ;
- rejouer un test.

Les données de test doivent être fictives.

---

# 47. Rapprochement des webhooks

Un webhook ne doit pas toujours être considéré comme la seule preuve.

Pour une opération financière :

- comparer avec l’API partenaire ;
- comparer avec les fichiers de rapprochement ;
- comparer avec le ledger ;
- vérifier le statut interne ;
- résoudre les divergences.

---

# 48. Sagas

Une saga orchestre une opération distribuée.

Exemple de paiement :

1. créer la demande ;
2. réserver les fonds ;
3. appeler le partenaire ;
4. attendre la confirmation ;
5. capturer les fonds ;
6. créer les écritures ;
7. notifier ;
8. rapprocher.

Chaque étape doit avoir :

- statut ;
- timeout ;
- retry ;
- compensation ;
- audit ;
- corrélation.

---

# 49. Orchestration et chorégraphie

## 49.1 Orchestration

Un orchestrateur contrôle les étapes.

Avantages :

- visibilité ;
- contrôle ;
- reprise ;
- gestion claire des compensations.

## 49.2 Chorégraphie

Les services réagissent à des événements.

Avantages :

- découplage ;
- extensibilité.

Les processus financiers critiques doivent conserver une orchestration suffisamment explicite.

---

# 50. Compensation

Une compensation annule logiquement une étape déjà réalisée.

Exemples :

- libérer une réservation ;
- créer une contre-écriture ;
- annuler une commande ;
- révoquer un avantage ;
- restaurer un stock ;
- annuler une notification programmée.

---

# 51. Compensation non destructive

Une compensation ne doit pas supprimer silencieusement la preuve de l’action originale.

Elle doit créer :

- nouvel événement ;
- référence à l’original ;
- motif ;
- date ;
- auteur ou service ;
- audit.

---

# 52. Statut inconnu

Une opération est `UNKNOWN` lorsque son résultat externe n’est pas confirmé.

Le workflow doit :

- ne pas relancer automatiquement l’opération financière ;
- interroger le partenaire ;
- attendre un webhook ;
- lancer une vérification planifiée ;
- rapprocher ;
- alerter après un délai ;
- notifier l’utilisateur lorsque résolu.

---

# 53. Files de vérification

Une file dédiée peut traiter :

- statuts inconnus ;
- confirmations manquantes ;
- paiements en attente ;
- webhooks absents ;
- opérations hors ligne ;
- transactions TPE non synchronisées.

---

# 54. Batch

Les traitements batch concernent notamment :

- rapprochement ;
- règlements ;
- rapports ;
- imports ;
- exports ;
- anonymisation ;
- migration ;
- nettoyage ;
- analyse fraude ;
- indexation.

---

# 55. Traitement par lots

Un batch doit utiliser :

- taille de lot ;
- checkpoint ;
- reprise ;
- progression ;
- rapport ;
- erreurs partielles ;
- limite de mémoire ;
- délai maximal ;
- audit.

---

# 56. Import asynchrone

Un import doit suivre :

1. téléversement ;
2. analyse antivirus ;
3. validation de format ;
4. prévisualisation ;
5. approbation ;
6. mise en file ;
7. traitement ;
8. rapport ;
9. correction éventuelle ;
10. archivage ou suppression.

---

# 57. Export asynchrone

Un export important doit :

- créer une demande ;
- vérifier les permissions ;
- mettre en file ;
- générer le fichier ;
- chiffrer si nécessaire ;
- créer un lien temporaire ;
- notifier ;
- expirer ;
- auditer le téléchargement.

---

# 58. Notifications asynchrones

La création d’un événement métier peut déclencher :

- notification interne ;
- push ;
- e-mail ;
- SMS ;
- WhatsApp lorsque autorisé ;
- message partenaire.

Le paiement ne doit pas être annulé uniquement parce qu’une notification échoue.

---

# 59. Analytics asynchrones

Les événements analytics ne doivent pas ralentir les opérations métier.

Ils doivent être :

- validés ;
- pseudonymisés ;
- limités ;
- agrégés ;
- soumis au consentement lorsque nécessaire ;
- envoyés dans une file séparée.

---

# 60. Jini asynchrone

Jini peut utiliser des jobs pour :

- génération de rapport ;
- analyse longue ;
- classement documentaire ;
- résumé ;
- aide support ;
- traitement de fichier ;
- recommandation différée.

Une action financière critique proposée par Jini doit toujours repasser par les contrôles métier.

---

# 61. TPE et synchronisation asynchrone

Le TPE peut mettre en file locale :

- reçus ;
- journaux ;
- données de santé ;
- synchronisations ;
- opérations hors ligne autorisées ;
- mises à jour de catalogue.

Une opération financière ne doit pas être considérée comme définitive uniquement à partir de la file locale.

---

# 62. Déduplication

La déduplication peut utiliser :

- eventId ;
- messageId ;
- idempotencyKey ;
- externalReference ;
- hash ;
- consumer + eventId ;
- fenêtre temporelle.

---

# 63. Expiration des messages

Un message doit pouvoir avoir une date d’expiration.

Exemples :

- OTP ;
- notification promotionnelle ;
- paiement programmé ;
- rappel ;
- offre ;
- session TPE ;
- commande temporaire.

Un message expiré ne doit pas être exécuté sans nouvelle validation.

---

# 64. Rétention

Chaque file doit définir :

- durée des messages réussis ;
- durée des messages échoués ;
- durée des dead letters ;
- archivage ;
- suppression ;
- obligations légales ;
- capacité de rejeu.

---

# 65. Sécurité

Les messages doivent être protégés par :

- authentification des producteurs ;
- authentification des consommateurs ;
- chiffrement en transit ;
- chiffrement au repos lorsque nécessaire ;
- permissions par file ;
- séparation des environnements ;
- rotation des secrets ;
- audit.

---

# 66. Données sensibles

Un message ne doit pas contenir inutilement :

- mot de passe ;
- PIN ;
- OTP ;
- CVV ;
- numéro complet de carte ;
- document complet ;
- secret ;
- clé privée ;
- token complet.

Préférer une référence sécurisée.

---

# 67. Séparation des environnements

Les files doivent être séparées entre :

- développement ;
- test ;
- Démo ;
- Recette ;
- Préproduction ;
- Production.

Un message de test ne doit jamais être consommé en production.

---

# 68. Multi-pays

Les messages doivent contenir le pays lorsque le traitement varie selon :

- devise ;
- réglementation ;
- partenaire ;
- langue ;
- fuseau ;
- disponibilité ;
- conservation.

---

# 69. Multi-tenant

Les messages professionnels doivent contenir lorsque pertinent :

- organizationId ;
- merchantId ;
- establishmentId ;
- tenantId.

Le consommateur doit vérifier son périmètre.

---

# 70. Observabilité

Surveiller :

- taille des files ;
- âge du message le plus ancien ;
- débit ;
- temps de traitement ;
- retries ;
- échecs ;
- dead letters ;
- saturation ;
- workers actifs ;
- messages expirés ;
- doublons ;
- statut inconnu ;
- taux de réussite webhook.

---

# 71. Métriques par type de message

Exemples :

```text
queue_messages_published_total
queue_messages_consumed_total
queue_messages_failed_total
queue_message_processing_duration
queue_oldest_message_age
queue_dead_letter_total
webhook_delivery_success_rate
webhook_delivery_latency
```

---

# 72. Corrélation

Une opération doit pouvoir être suivie dans :

- requête API ;
- événement ;
- commande ;
- job ;
- worker ;
- appel partenaire ;
- webhook ;
- ledger ;
- notification ;
- audit.

---

# 73. Alertes

Déclencher une alerte si :

- une file grossit rapidement ;
- l’âge des messages dépasse un seuil ;
- aucun worker n’est actif ;
- les retries augmentent ;
- la dead-letter queue augmente ;
- un partenaire ne répond plus ;
- un webhook échoue massivement ;
- un scheduler ne s’exécute pas ;
- une opération reste inconnue ;
- un doublon financier est détecté.

---

# 74. Administration

Le portail Admin doit permettre :

- consulter les files ;
- consulter les jobs ;
- filtrer ;
- rechercher par corrélation ;
- consulter les tentatives ;
- voir les dead letters ;
- rejouer un message ;
- annuler un job ;
- suspendre un worker ;
- consulter les webhooks ;
- envoyer un test ;
- désactiver un endpoint ;
- consulter les métriques ;
- créer un incident.

---

# 75. Permissions

Exemples :

```text
queue.read
queue.job.read
queue.job.retry
queue.job.cancel
queue.dead_letter.read
queue.dead_letter.replay
queue.worker.manage
scheduler.read
scheduler.manage
webhook.read
webhook.endpoint.manage
webhook.test.send
webhook.replay
async_job.audit.read
```

---

# 76. Actions critiques

Doivent être particulièrement protégées :

- rejeu d’un message financier ;
- rejeu massif ;
- suppression d’une dead letter ;
- modification d’une file ;
- changement de concurrence ;
- suspension d’un worker critique ;
- désactivation d’un webhook partenaire ;
- modification d’un scheduler financier ;
- annulation d’un job de rapprochement.

---

# 77. Double validation

Peut être exigée pour :

- rejeu financier ;
- rejeu massif ;
- reprise d’un règlement ;
- relance d’une compensation ;
- modification d’un scheduler de clôture ;
- suppression définitive de messages ;
- changement d’un endpoint institutionnel.

---

# 78. API internes

Exemples :

```http
GET    /async/jobs
GET    /async/jobs/{id}
POST   /async/jobs/{id}/retry
POST   /async/jobs/{id}/cancel

GET    /queues
GET    /queues/{name}/metrics

GET    /dead-letters
POST   /dead-letters/{id}/replay
POST   /dead-letters/{id}/discard

GET    /webhooks/endpoints
POST   /webhooks/endpoints
PATCH  /webhooks/endpoints/{id}
POST   /webhooks/endpoints/{id}/test

GET    /webhook-deliveries
POST   /webhook-deliveries/{id}/retry
```

---

# 79. Modèles

- EventDefinition
- EventSchemaVersion
- EventEnvelope
- OutboxEvent
- OutboxAttempt
- InboxEvent
- QueueDefinition
- QueueMessage
- QueueAttempt
- DeadLetterMessage
- AsyncJob
- AsyncJobAttempt
- AsyncJobResult
- WorkerDefinition
- WorkerInstance
- ScheduledTask
- ScheduledExecution
- WebhookEndpoint
- WebhookSubscription
- WebhookDelivery
- WebhookAttempt
- Saga
- SagaStep
- SagaCompensation
- AsyncAudit

---

# 80. Règles métier

1. Les traitements longs sont asynchrones.
2. Une mise en file ne signifie pas un succès final.
3. Les messages peuvent être livrés plusieurs fois.
4. Les consommateurs sont idempotents.
5. Les événements sont versionnés.
6. Les schémas sont validés.
7. Les événements critiques utilisent une Outbox.
8. Les consommateurs peuvent utiliser une Inbox.
9. Les doublons sont détectés.
10. Les files ne remplacent pas la base métier.
11. Les dead letters sont surveillées.
12. Les retries sont limités.
13. Les erreurs définitives ne sont pas réessayées.
14. Les statuts inconnus sont vérifiés.
15. Les opérations financières ne sont pas relancées aveuglément.
16. Les webhooks sont signés.
17. Les webhooks entrants sont idempotents.
18. Les webhooks sortants sont auditables.
19. Les schedulers distribués évitent les doubles exécutions.
20. Les tâches possèdent une date d’expiration lorsque nécessaire.
21. Les compensations conservent l’historique.
22. Les sagas sont reprenables.
23. Les environnements sont séparés.
24. Les messages sensibles sont minimisés.
25. Les opérations sont corrélables.
26. Les workers possèdent des health checks.
27. Les files critiques ont une priorité dédiée.
28. Les batchs possèdent des checkpoints.
29. Les rejeux sont audités.
30. Les métriques sont disponibles.

---

# 81. Analytics

Événements possibles :

```text
event_published
event_consumed
event_duplicate_detected
event_version_rejected
queue_message_enqueued
queue_message_processed
queue_message_failed
queue_message_retried
dead_letter_created
dead_letter_replayed
worker_started
worker_stopped
worker_failed
scheduled_task_started
scheduled_task_completed
scheduled_task_failed
webhook_received
webhook_signature_failed
webhook_delivery_started
webhook_delivery_succeeded
webhook_delivery_failed
saga_started
saga_completed
saga_compensated
unknown_status_check_started
unknown_status_resolved
```

---

# 82. Tests

- tests de publication ;
- tests Outbox ;
- tests Inbox ;
- tests d’idempotence ;
- tests de doublon ;
- tests d’ordre ;
- tests de version ;
- tests de retry ;
- tests de backoff ;
- tests de dead-letter queue ;
- tests de rejeu ;
- tests de timeout ;
- tests de worker ;
- tests de scheduler ;
- tests de verrou distribué ;
- tests de webhook entrant ;
- tests de signature ;
- tests de rejeu webhook ;
- tests de webhook sortant ;
- tests de saga ;
- tests de compensation ;
- tests de statut inconnu ;
- tests de batch ;
- tests de reprise ;
- tests de charge ;
- tests de sécurité ;
- tests multi-pays ;
- tests multi-tenant ;
- tests de monitoring.

---

# 83. Critères d’acceptation

L’architecture asynchrone est validée lorsque :

- les traitements longs utilisent des jobs ;
- les événements sont versionnés ;
- les producteurs publient de manière fiable ;
- les consommateurs sont idempotents ;
- les doublons sont détectés ;
- les files possèdent des retries ;
- les files critiques possèdent une dead-letter queue ;
- les messages peuvent être rejoués de manière contrôlée ;
- les webhooks entrants sont signés et dédupliqués ;
- les webhooks sortants sont signés et suivis ;
- les schedulers évitent les doubles exécutions ;
- les sagas sont reprenables ;
- les compensations sont auditées ;
- les statuts inconnus sont vérifiés ;
- les batchs possèdent des checkpoints ;
- les workers peuvent être mis à l’échelle ;
- les messages sensibles sont minimisés ;
- les environnements sont isolés ;
- les métriques et alertes sont disponibles ;
- les tests couvrent les scénarios critiques.
