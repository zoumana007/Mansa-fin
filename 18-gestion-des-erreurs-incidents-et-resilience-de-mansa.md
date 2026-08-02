# 18 — Gestion des erreurs, incidents et résilience de Mansa

## 1. Objet du document

Ce document définit le système officiel de gestion des erreurs, incidents, dégradations et mécanismes de résilience de Mansa.

Il couvre :

- les erreurs fonctionnelles ;
- les erreurs techniques ;
- les erreurs partenaires ;
- les erreurs financières ;
- les erreurs réseau ;
- les erreurs de sécurité ;
- les erreurs TPE ;
- les erreurs mobiles et web ;
- les statuts incertains ;
- les retries ;
- les timeouts ;
- les circuit breakers ;
- les files d’attente ;
- les reprises ;
- les incidents ;
- les alertes ;
- les procédures de résolution ;
- la communication aux utilisateurs ;
- la continuité de service ;
- les retours d’expérience.

L’objectif est de garantir qu’une panne, une erreur ou l’indisponibilité d’un partenaire ne provoque pas :

- de double paiement ;
- de perte d’argent ;
- de faux succès ;
- de données incohérentes ;
- de blocage général de la plateforme ;
- de perte de traçabilité ;
- de message incompréhensible ;
- de reprise manuelle dangereuse.

---

# 2. Principes fondamentaux

## 2.1 Aucun faux succès

Une opération ne doit jamais être présentée comme réussie si son état réel n’est pas confirmé.

Le système doit distinguer clairement :

- réussie ;
- refusée ;
- échouée ;
- en attente ;
- en traitement ;
- statut inconnu ;
- annulée ;
- expirée ;
- à vérifier.

---

## 2.2 Une erreur ne doit pas produire de doublon

Toute opération critique doit être idempotente.

Un retry ne doit jamais créer :

- deux transferts ;
- deux paiements ;
- deux remboursements ;
- deux cartes ;
- deux écritures ledger ;
- deux commandes TPE ;
- deux dossiers administratifs.

---

## 2.3 Dégradation contrôlée

Lorsqu’un module est indisponible, les autres modules doivent rester utilisables lorsque cela est possible.

Exemple :

Si un partenaire Mobile Money est indisponible, l’utilisateur peut encore :

- consulter son compte ;
- utiliser ses cartes ;
- consulter ses transactions ;
- accéder au support ;
- utiliser les autres moyens de paiement disponibles.

---

## 2.4 Erreur compréhensible

Une erreur utilisateur doit expliquer :

- ce qui s’est passé ;
- si l’argent a été débité ;
- si l’opération peut être recommencée ;
- si une action est nécessaire ;
- quand réessayer ;
- comment contacter le support ;
- quelle référence communiquer.

---

## 2.5 Traçabilité complète

Toute erreur importante doit pouvoir être reliée à :

- requête ;
- utilisateur ;
- transaction ;
- appareil ;
- application ;
- partenaire ;
- environnement ;
- version ;
- corrélation ;
- tentative ;
- incident éventuel.

---

# 3. Catégories d’erreurs

## 3.1 Erreurs de validation

Exemples :

- montant invalide ;
- devise non autorisée ;
- champ manquant ;
- format téléphone incorrect ;
- document trop volumineux ;
- bénéficiaire incomplet ;
- date invalide.

Ces erreurs ne doivent généralement pas être réessayées automatiquement.

---

## 3.2 Erreurs d’authentification

Exemples :

- session expirée ;
- jeton invalide ;
- OTP expiré ;
- appareil révoqué ;
- PIN incorrect ;
- biométrie échouée.

---

## 3.3 Erreurs d’autorisation

Exemples :

- permission absente ;
- rôle insuffisant ;
- pays non autorisé ;
- périmètre invalide ;
- montant supérieur à la limite autorisée ;
- action nécessitant une approbation.

---

## 3.4 Erreurs métier

Exemples :

- solde insuffisant ;
- plafond dépassé ;
- carte bloquée ;
- compte suspendu ;
- remboursement impossible ;
- transaction déjà remboursée ;
- KYC insuffisant ;
- devise indisponible ;
- commerce non actif.

---

## 3.5 Erreurs partenaires

Exemples :

- timeout ;
- réponse invalide ;
- service indisponible ;
- signature incorrecte ;
- webhook manquant ;
- statut incohérent ;
- erreur de règlement ;
- certificat expiré.

---

## 3.6 Erreurs financières

Exemples :

- transaction déséquilibrée ;
- double écriture ;
- solde incohérent ;
- réservation non libérée ;
- remboursement supérieur au montant disponible ;
- écart de rapprochement ;
- devise incorrecte ;
- statut partenaire incertain.

---

## 3.7 Erreurs techniques

Exemples :

- exception serveur ;
- base de données indisponible ;
- cache indisponible ;
- file bloquée ;
- stockage inaccessible ;
- mémoire saturée ;
- service non démarré ;
- migration échouée.

---

## 3.8 Erreurs réseau

Exemples :

- absence de connexion ;
- connexion lente ;
- requête interrompue ;
- DNS indisponible ;
- certificat réseau invalide ;
- perte de connexion pendant un paiement.

---

## 3.9 Erreurs de sécurité

Exemples :

- tentative de rejeu ;
- signature invalide ;
- secret compromis ;
- accès interdit ;
- appareil suspect ;
- élévation de privilège ;
- activité automatisée anormale ;
- fichier malveillant.

---

## 3.10 Erreurs de version

Exemples :

- application trop ancienne ;
- contrat incompatible ;
- version API retirée ;
- firmware TPE non supporté ;
- schéma local obsolète ;
- configuration incompatible.

---

# 4. Taxonomie officielle des erreurs

Chaque erreur doit disposer d’un code stable.

Format recommandé :

```text
DOMAIN_ERROR_NAME
```

Exemples :

```text
AUTH_SESSION_EXPIRED
PAYMENT_LIMIT_EXCEEDED
PAYMENT_STATUS_UNKNOWN
CARD_BLOCKED
LEDGER_IMBALANCED_TRANSACTION
PARTNER_TIMEOUT
CONFIGURATION_INVALID
VERSION_NOT_SUPPORTED
```

Le code ne doit pas changer selon la langue.

---

# 5. Structure standard d’une réponse d’erreur

Exemple :

```json
{
  "code": "PAYMENT_LIMIT_EXCEEDED",
  "message": "Le plafond autorisé est dépassé.",
  "status": 422,
  "correlationId": "cor_123",
  "retryable": false,
  "action": "REDUCE_AMOUNT",
  "details": {}
}
```

Champs possibles :

- code ;
- message ;
- statut HTTP ;
- identifiant de corrélation ;
- réessayable ou non ;
- action recommandée ;
- niveau de gravité ;
- détails autorisés ;
- délai avant retry ;
- lien support éventuel.

---

# 6. Messages utilisateur et messages techniques

## 6.1 Message utilisateur

Il doit être :

- simple ;
- traduit ;
- non technique ;
- non anxiogène ;
- orienté solution ;
- respectueux de la confidentialité.

## 6.2 Message technique

Il peut contenir :

- stack trace ;
- service ;
- requête ;
- version ;
- partenaire ;
- code interne ;
- durée ;
- tentative ;
- cause.

Il doit rester dans les journaux sécurisés.

---

# 7. Statut inconnu

Une opération peut avoir un statut inconnu lorsque :

- le partenaire ne répond pas ;
- la connexion est coupée après envoi ;
- le webhook tarde ;
- le terminal redémarre ;
- l’application se ferme ;
- la réponse est invalide.

Dans ce cas, le système doit :

1. ne pas annoncer un succès ;
2. ne pas relancer aveuglément ;
3. conserver la référence ;
4. interroger le partenaire ;
5. attendre le webhook ;
6. lancer un rapprochement ;
7. afficher « en vérification » ;
8. notifier l’utilisateur après résolution.

---

# 8. Timeouts

Chaque appel externe doit définir :

- timeout de connexion ;
- timeout de lecture ;
- timeout global ;
- type d’opération ;
- comportement après expiration ;
- nombre de retries ;
- statut temporaire ;
- méthode de vérification.

Un timeout ne signifie pas automatiquement que l’opération a échoué.

---

# 9. Retry

## 9.1 Retry autorisé

Pour :

- erreur réseau temporaire ;
- service momentanément indisponible ;
- limite temporaire partenaire ;
- file saturée ;
- verrou temporaire ;
- erreur 5xx réessayable.

## 9.2 Retry interdit ou contrôlé

Pour :

- paiement non idempotent ;
- validation invalide ;
- authentification refusée ;
- permission refusée ;
- solde insuffisant ;
- opération déjà exécutée ;
- signature invalide.

## 9.3 Stratégie

Le retry peut utiliser :

- délai fixe ;
- backoff exponentiel ;
- jitter ;
- nombre maximal ;
- date d’expiration ;
- file dédiée ;
- dead-letter queue.

---

# 10. Idempotence

Chaque opération critique doit posséder :

- clé d’idempotence ;
- empreinte de requête ;
- auteur ;
- endpoint ;
- statut ;
- résultat ;
- date de création ;
- date d’expiration ;
- référence métier.

Une même clé avec un contenu différent doit être rejetée.

---

# 11. Circuit Breaker

Un circuit breaker doit protéger les appels vers :

- banque ;
- Mobile Money ;
- réseau carte ;
- service KYC ;
- service SMS ;
- stockage ;
- service de change ;
- partenaire public ;
- partenaire d’investissement.

États :

- fermé ;
- ouvert ;
- semi-ouvert.

Lorsqu’il est ouvert :

- les appels sont bloqués temporairement ;
- un fallback peut être utilisé ;
- une alerte est déclenchée ;
- l’interface affiche l’indisponibilité.

---

# 12. Bulkhead Isolation

Les ressources doivent être isolées afin qu’un service défaillant ne consomme pas toute la capacité.

Exemples :

- file séparée par partenaire ;
- pool de connexions séparé ;
- worker séparé ;
- limite de concurrence ;
- timeout dédié ;
- quota par service.

---

# 13. Files d’attente

Les opérations asynchrones doivent utiliser des files lorsque nécessaire.

Exemples :

- notifications ;
- webhooks ;
- génération de documents ;
- rapprochement ;
- synchronisation ;
- exports ;
- traitement d’images ;
- tâches Jini ;
- rapports.

Chaque message doit contenir :

- identifiant ;
- type ;
- version ;
- tentative ;
- date ;
- corrélation ;
- priorité ;
- statut ;
- date d’expiration.

---

# 14. Dead-Letter Queue

Une tâche doit être envoyée en dead-letter queue lorsqu’elle dépasse le nombre maximal de tentatives.

Le système doit permettre :

- consultation ;
- diagnostic ;
- correction ;
- relance ;
- annulation ;
- archivage ;
- audit ;
- création d’incident.

---

# 15. Compensation

Pour une opération composée de plusieurs étapes, une compensation doit être prévue.

Exemple :

1. débit client ;
2. appel partenaire ;
3. crédit bénéficiaire.

Si une étape échoue, le système doit appliquer la stratégie définie :

- annulation ;
- contre-écriture ;
- mise en suspense ;
- reprise ;
- intervention manuelle.

---

# 16. Saga

Les workflows distribués peuvent utiliser une saga.

Chaque saga doit définir :

- étapes ;
- ordre ;
- statut ;
- timeout ;
- retry ;
- compensation ;
- corrélation ;
- responsable ;
- reprise ;
- audit.

---

# 17. Comptes de suspense

Une opération financière incertaine peut être placée sur un compte de suspense.

Le suspense doit contenir :

- référence ;
- montant ;
- devise ;
- origine ;
- partenaire ;
- motif ;
- statut ;
- date ;
- responsable ;
- échéance ;
- résolution.

Aucune opération ne doit rester indéfiniment en suspense.

---

# 18. Reprise après incident

Le système doit pouvoir reprendre après :

- redémarrage ;
- crash ;
- coupure réseau ;
- panne base de données ;
- panne partenaire ;
- perte de worker ;
- mise à jour interrompue ;
- fermeture TPE ;
- fermeture application.

Les états nécessaires à la reprise doivent être persistés.

---

# 19. Mode hors ligne

Les applications doivent afficher clairement :

- statut hors ligne ;
- données en cache ;
- actions disponibles ;
- actions interdites ;
- commandes en attente ;
- date de dernière synchronisation.

Une opération financière ne doit pas être annoncée comme finalisée hors ligne sans mécanisme sécurisé prévu.

---

# 20. Résilience TPE

Le TPE doit gérer :

- coupure réseau ;
- coupure de batterie ;
- redémarrage ;
- imprimante indisponible ;
- carte retirée ;
- NFC interrompu ;
- mise à jour interrompue ;
- synchronisation incomplète.

Chaque paiement doit avoir une référence locale et backend permettant sa vérification.

---

# 21. Résilience mobile

L’application mobile doit gérer :

- fermeture pendant une opération ;
- changement de réseau ;
- mode avion ;
- session expirée ;
- application en arrière-plan ;
- double clic ;
- appui répété ;
- reprise après crash.

---

# 22. Résilience web

Les applications web doivent gérer :

- rafraîchissement ;
- double soumission ;
- onglets multiples ;
- expiration de session ;
- perte de connexion ;
- requête longue ;
- téléchargement interrompu ;
- action en masse partiellement réussie.

---

# 23. Dégradation des fonctionnalités

Modes possibles :

- fonctionnement normal ;
- lecture seule ;
- paiements suspendus ;
- transferts suspendus ;
- partenaire spécifique suspendu ;
- pays spécifique suspendu ;
- TPE uniquement ;
- support uniquement ;
- maintenance complète.

---

# 24. Health Checks

Chaque service doit exposer des contrôles de santé.

Types :

- liveness ;
- readiness ;
- dépendances ;
- base de données ;
- cache ;
- file ;
- partenaire ;
- stockage ;
- certificat ;
- espace disque.

Un service ne doit pas être déclaré prêt si ses dépendances essentielles sont indisponibles.

---

# 25. Monitoring

Le système doit surveiller :

- taux d’erreur ;
- latence ;
- timeouts ;
- retries ;
- files ;
- dead letters ;
- statuts inconnus ;
- suspense ;
- erreurs partenaires ;
- crashs ;
- saturation ;
- disponibilité ;
- erreurs par version ;
- erreurs par pays ;
- erreurs par application.

---

# 26. Alertes

Des alertes doivent être déclenchées en cas :

- de hausse des erreurs ;
- de paiement en statut inconnu ;
- de double écriture détectée ;
- de solde incohérent ;
- de file bloquée ;
- de partenaire indisponible ;
- de retry anormal ;
- de dead-letter queue croissante ;
- de certificat expirant ;
- de sauvegarde échouée ;
- de migration échouée ;
- de crash massif.

---

# 27. Niveaux d’incident

## 27.1 SEV-1 — Critique

Exemples :

- perte financière potentielle ;
- double débit ;
- fuite de données ;
- indisponibilité totale ;
- compromission de sécurité ;
- ledger incohérent.

## 27.2 SEV-2 — Majeur

Exemples :

- moyen de paiement principal indisponible ;
- pays fortement affecté ;
- TPE nombreux indisponibles ;
- KYC bloqué ;
- files importantes en retard.

## 27.3 SEV-3 — Modéré

Exemples :

- fonctionnalité secondaire indisponible ;
- partenaire limité ;
- erreur contournable ;
- retard de notifications.

## 27.4 SEV-4 — Mineur

Exemples :

- défaut visuel ;
- texte incorrect ;
- lenteur faible ;
- problème sans impact financier.

---

# 28. Cycle de gestion d’un incident

1. Détection.
2. Qualification.
3. Attribution du niveau.
4. Désignation du responsable.
5. Confinement.
6. Communication.
7. Correction.
8. Vérification.
9. Rétablissement.
10. Surveillance.
11. Clôture.
12. Retour d’expérience.

---

# 29. Rôles d’incident

Rôles possibles :

- Incident Commander ;
- responsable technique ;
- responsable produit ;
- sécurité ;
- conformité ;
- communication ;
- support ;
- responsable partenaire ;
- responsable pays ;
- finance ;
- observateur.

---

# 30. Communication d’incident

La communication doit préciser :

- services concernés ;
- début estimé ;
- impact ;
- pays ;
- moyens de contournement ;
- état actuel ;
- prochaine mise à jour ;
- résolution ;
- référence d’incident.

La communication ne doit pas révéler d’informations exploitables par un attaquant.

---

# 31. Statut public

Un système de statut peut afficher :

- opérationnel ;
- performance dégradée ;
- indisponibilité partielle ;
- indisponibilité majeure ;
- maintenance ;
- incident résolu.

---

# 32. Support utilisateur

Le support doit pouvoir consulter :

- incident actif ;
- services affectés ;
- message officiel ;
- opérations concernées ;
- statut utilisateur ;
- procédure ;
- compensation éventuelle ;
- date de prochaine mise à jour.

---

# 33. Gestion des compensations clients

Une compensation peut être accordée en cas :

- de double débit ;
- d’indisponibilité prolongée ;
- de frais incorrect ;
- d’erreur Mansa ;
- de retard important ;
- de préjudice confirmé.

Toute compensation doit être :

- justifiée ;
- approuvée ;
- enregistrée dans le ledger ;
- auditée ;
- limitée ;
- liée à l’incident.

---

# 34. Post-mortem

Tout incident important doit produire un rapport comprenant :

- résumé ;
- impact ;
- chronologie ;
- cause racine ;
- facteurs aggravants ;
- détection ;
- réaction ;
- actions correctives ;
- propriétaire ;
- échéance ;
- preuve de réalisation.

Le post-mortem doit être orienté amélioration, pas accusation.

---

# 35. Cause racine

La cause racine peut concerner :

- code ;
- configuration ;
- infrastructure ;
- partenaire ;
- procédure ;
- permission ;
- déploiement ;
- données ;
- sécurité ;
- manque de test ;
- erreur humaine ;
- dépendance externe.

---

# 36. Actions correctives

Chaque action corrective doit contenir :

- description ;
- priorité ;
- propriétaire ;
- date limite ;
- statut ;
- incident lié ;
- preuve ;
- validation ;
- résultat.

---

# 37. Administration

Le portail Admin doit permettre :

- consulter les erreurs ;
- rechercher par corrélation ;
- filtrer ;
- consulter les incidents ;
- créer un incident ;
- attribuer un responsable ;
- changer la gravité ;
- déclencher un kill switch ;
- relancer une tâche ;
- consulter les dead letters ;
- résoudre un suspense ;
- publier une communication ;
- clôturer ;
- générer un post-mortem.

---

# 38. Permissions

Exemples :

```text
error.read
error.read_sensitive
error.retry
error.resolve
incident.create
incident.update
incident.severity.change
incident.communication.publish
incident.close
incident.postmortem.read
incident.postmortem.create
queue.dead_letter.retry
suspense.resolve
resilience.kill_switch.use
```

---

# 39. Actions critiques

Doivent être particulièrement protégées :

- relance d’une opération financière ;
- résolution d’un suspense ;
- compensation ;
- modification manuelle de statut ;
- déclenchement d’un kill switch ;
- fermeture d’un incident critique ;
- suppression d’une tâche ;
- réexécution d’un webhook ;
- annulation d’un rapprochement.

---

# 40. Double validation

Peut être exigée pour :

- compensation importante ;
- reprise d’écriture ;
- résolution ledger ;
- fermeture SEV-1 ;
- relance massive ;
- activation d’un mode dégradé global ;
- reprise après incident financier.

---

# 41. API

Exemples :

```http
GET    /errors
GET    /errors/{id}
GET    /errors/correlation/{correlationId}

GET    /incidents
POST   /incidents
GET    /incidents/{id}
PATCH  /incidents/{id}

POST   /incidents/{id}/contain
POST   /incidents/{id}/resolve
POST   /incidents/{id}/close

GET    /dead-letters
POST   /dead-letters/{id}/retry
POST   /dead-letters/{id}/discard

GET    /suspense-cases
POST   /suspense-cases/{id}/resolve
```

---

# 42. Modèles

- ErrorDefinition
- ErrorOccurrence
- ErrorCategory
- ErrorSeverity
- ErrorCorrelation
- RetryPolicy
- CircuitBreaker
- QueueFailure
- DeadLetter
- SuspenseCase
- Incident
- IncidentSeverity
- IncidentTimeline
- IncidentCommunication
- IncidentAction
- IncidentPostmortem
- IncidentCompensation
- RecoveryProcedure
- ResiliencePolicy
- HealthCheck
- ResilienceAudit

---

# 43. Règles métier

1. Aucun faux succès n’est autorisé.
2. Toute opération critique est idempotente.
3. Un timeout ne signifie pas automatiquement un échec.
4. Un statut inconnu doit être vérifié.
5. Les retries sont contrôlés.
6. Les erreurs de validation ne sont pas réessayées automatiquement.
7. Les écritures financières restent cohérentes.
8. Les opérations incertaines peuvent être placées en suspense.
9. Les files possèdent une dead-letter queue.
10. Les circuit breakers protègent les partenaires.
11. Les erreurs importantes sont corrélables.
12. Les messages utilisateur restent compréhensibles.
13. Les détails techniques restent protégés.
14. Les fonctionnalités peuvent être dégradées séparément.
15. Les applications doivent reprendre après interruption.
16. Les incidents sont classés.
17. Les incidents critiques sont audités.
18. Les compensations passent par le ledger.
19. Les actions critiques peuvent exiger une double validation.
20. Les post-mortems produisent des actions suivies.
21. Les partenaires sont isolés.
22. Les dead letters ne restent pas sans traitement.
23. Les comptes de suspense sont surveillés.
24. Les utilisateurs sont informés du statut réel.
25. Les environnements restent séparés.

---

# 44. Analytics

Événements possibles :

```text
error_occurred
error_retry_started
error_retry_succeeded
error_retry_failed
partner_timeout_detected
unknown_status_detected
unknown_status_resolved
dead_letter_created
dead_letter_retried
suspense_case_created
suspense_case_resolved
incident_created
incident_severity_changed
incident_contained
incident_resolved
incident_closed
kill_switch_activated
service_degraded
service_recovered
postmortem_created
```

---

# 45. Tests

- tests de validation ;
- tests d’idempotence ;
- tests de timeout ;
- tests de retry ;
- tests de backoff ;
- tests de circuit breaker ;
- tests de file ;
- tests de dead-letter queue ;
- tests de compensation ;
- tests de saga ;
- tests de suspense ;
- tests de statut inconnu ;
- tests de reprise mobile ;
- tests de reprise TPE ;
- tests hors ligne ;
- tests de charge ;
- tests de panne partenaire ;
- tests de panne base ;
- tests de rollback ;
- tests de permissions ;
- tests de double validation ;
- tests d’audit ;
- exercices d’incident.

---

# 46. Critères d’acceptation

Le système de gestion des erreurs et incidents est validé lorsque :

- les erreurs disposent de codes stables ;
- les messages utilisateurs sont clairs ;
- les détails techniques sont protégés ;
- les opérations critiques sont idempotentes ;
- les statuts inconnus sont gérés ;
- les retries sont contrôlés ;
- les circuit breakers fonctionnent ;
- les files possèdent une dead-letter queue ;
- les opérations financières incertaines sont isolées ;
- les applications peuvent reprendre après interruption ;
- les partenaires peuvent être désactivés séparément ;
- les incidents sont classés ;
- les alertes sont configurées ;
- les communications d’incident sont prévues ;
- les compensations sont auditées ;
- les post-mortems sont obligatoires pour les incidents majeurs ;
- les tests couvrent les pannes critiques.
