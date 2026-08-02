# 14 — Gestion globale des Feature Flags et du déploiement progressif de Mansa

## 1. Objet du document

Ce document définit le système officiel de **Feature Flags** de Mansa.

Les Feature Flags permettent de contrôler l’activation d’une fonctionnalité sans devoir redéployer immédiatement toutes les applications.

Ils servent notamment à :

- activer une fonctionnalité progressivement ;
- limiter une fonction à un pays ;
- limiter une fonction à un groupe d’utilisateurs ;
- tester une nouveauté ;
- désactiver rapidement un module défaillant ;
- gérer les dépendances partenaires ;
- séparer Démo, Recette, Préproduction et Production ;
- lancer un pilote ;
- contrôler une expérimentation ;
- imposer une version minimale ;
- préparer une fonctionnalité avant sa publication ;
- effectuer un rollback immédiat.

L’objectif est que toute fonctionnalité importante puisse être activée, désactivée ou limitée de manière :

- sécurisée ;
- traçable ;
- configurable ;
- progressive ;
- réversible ;
- auditable ;
- cohérente entre les applications et le backend.

---

# 2. Principes fondamentaux

## 2.1 Désactivation par défaut

Toute nouvelle fonctionnalité sensible doit être désactivée par défaut tant que :

- les tests ne sont pas terminés ;
- les dépendances ne sont pas prêtes ;
- les permissions ne sont pas définies ;
- les partenaires ne sont pas activés ;
- les documents légaux ne sont pas publiés ;
- la sécurité n’est pas validée ;
- le pays n’est pas autorisé ;
- le déploiement n’est pas approuvé.

---

## 2.2 Le backend reste l’autorité

Même si une fonctionnalité est masquée dans une application, le backend doit également refuser son utilisation lorsqu’elle est désactivée.

Masquer un écran ou un bouton ne suffit pas.

---

## 2.3 Activation explicite

Une fonctionnalité ne doit jamais devenir active uniquement parce que son code a été déployé.

L’activation doit être contrôlée par :

- un Feature Flag ;
- une configuration ;
- une politique ;
- une version ;
- une approbation ;
- un périmètre.

---

## 2.4 Rollback immédiat

Toute fonctionnalité risquée doit pouvoir être désactivée rapidement sans nouveau déploiement.

Le rollback doit être :

- rapide ;
- audité ;
- limité par permission ;
- disponible en urgence ;
- testé avant la production.

---

## 2.5 Pas de dépendance permanente inutile

Les Feature Flags temporaires doivent être supprimés lorsque :

- le déploiement est terminé ;
- la fonctionnalité est stable ;
- l’ancienne version est supprimée ;
- l’expérimentation est clôturée.

Un flag permanent doit être justifié.

---

# 3. Types de Feature Flags

## 3.1 Release Flag

Utilisé pour préparer une fonctionnalité avant son activation publique.

Exemple :

```text
client.cards.disposable.enabled
```

---

## 3.2 Operational Flag

Utilisé pour désactiver rapidement un service ou une fonction.

Exemple :

```text
payments.mobile_money.orange_money.enabled
```

---

## 3.3 Permission Flag

Utilisé pour limiter une fonction à certains rôles ou profils.

Exemple :

```text
admin.ledger.adjustment.enabled
```

Ce type ne remplace pas les permissions backend.

---

## 3.4 Experiment Flag

Utilisé pour tester plusieurs variantes.

Exemple :

```text
client.home.layout.experiment
```

Les expérimentations sont interdites sur certaines fonctions critiques.

---

## 3.5 Country Flag

Utilisé pour activer une fonction par pays.

Exemple :

```text
country.ml.public_services.fines.enabled
```

---

## 3.6 Partner Flag

Utilisé pour contrôler une intégration partenaire.

Exemple :

```text
partner.bdm.cards.issuance.enabled
```

---

## 3.7 Version Flag

Utilisé selon la version de l’application.

Exemple :

```text
client.nfc.min_version
```

---

## 3.8 Emergency Kill Switch

Utilisé pour désactiver immédiatement une fonction critique.

Exemple :

```text
payments.global.kill_switch
```

---

# 4. Structure d’un Feature Flag

Chaque Feature Flag doit contenir :

- identifiant ;
- clé ;
- nom ;
- description ;
- type ;
- propriétaire ;
- domaine ;
- application ;
- environnement ;
- pays ;
- segments ;
- statut ;
- valeur par défaut ;
- valeur active ;
- date de création ;
- date d’effet ;
- date d’expiration ;
- stratégie ;
- pourcentage de déploiement ;
- dépendances ;
- risques ;
- procédure de rollback ;
- permissions ;
- historique ;
- justification ;
- approbateur ;
- version.

---

# 5. Convention de nommage

Format recommandé :

```text
product.domain.feature.setting
```

Exemples :

```text
client.cards.virtual.enabled
client.connect.group_payments.enabled
commerce.inventory.offline_mode.enabled
tpe.tap_to_phone.enabled
admin.fraud.case_management.enabled
backend.payments.mobile_money.enabled
country.ml.investments.enabled
partner.orange_money.cashout.enabled
```

Les clés doivent être :

- stables ;
- explicites ;
- uniques ;
- indépendantes du texte affiché ;
- non liées à une personne ;
- non ambiguës.

---

# 6. Statuts d’un Feature Flag

Un Feature Flag peut être :

- brouillon ;
- configuré ;
- en test ;
- en recette ;
- en pilote ;
- actif ;
- partiellement actif ;
- suspendu ;
- expiré ;
- archivé ;
- supprimé logiquement.

---

# 7. Valeurs possibles

Un flag peut être :

## 7.1 Booléen

```text
true / false
```

## 7.2 Chaîne

```text
variant_a
```

## 7.3 Nombre

```text
25
```

## 7.4 Pourcentage

```text
10 %
```

## 7.5 Objet de configuration

```json
{
  "enabled": true,
  "dailyLimit": 100000,
  "countries": ["ML"]
}
```

Les objets complexes doivent utiliser un schéma validé.

---

# 8. Périmètres d’activation

Un Feature Flag peut être activé selon :

- environnement ;
- pays ;
- devise ;
- langue ;
- utilisateur ;
- segment ;
- rôle ;
- type de compte ;
- niveau KYC ;
- niveau KYB ;
- abonnement ;
- commerce ;
- établissement ;
- terminal ;
- partenaire ;
- version d’application ;
- appareil ;
- système d’exploitation ;
- canal ;
- heure ;
- pourcentage ;
- cohorte ;
- liste blanche ;
- liste noire.

---

# 9. Priorité des règles

Ordre recommandé :

1. kill switch global ;
2. blocage réglementaire ;
3. blocage pays ;
4. blocage partenaire ;
5. blocage sécurité ;
6. blocage environnement ;
7. règle de version ;
8. règle de permission ;
9. règle de segment ;
10. règle utilisateur ;
11. déploiement progressif ;
12. valeur par défaut.

Une règle plus spécifique ne doit pas contourner une interdiction globale.

---

# 10. Environnements

Chaque flag doit être séparé entre :

- local ;
- test ;
- démonstration ;
- recette ;
- préproduction ;
- production.

Une activation en recette ne doit pas activer automatiquement la production.

---

# 11. Déploiement progressif

Une fonctionnalité peut être déployée par étapes.

Exemple :

```text
Étape 1 : équipe interne
Étape 2 : 1 % des utilisateurs
Étape 3 : 5 %
Étape 4 : 20 %
Étape 5 : 50 %
Étape 6 : 100 %
```

Chaque étape doit définir :

- audience ;
- durée ;
- métriques ;
- critères de réussite ;
- seuils d’arrêt ;
- responsable ;
- date ;
- rollback.

---

# 12. Déploiement par cohorte

Une cohorte doit être déterministe.

Le même utilisateur doit rester dans la même variante tant que l’expérimentation est active.

Techniques possibles :

- hachage de l’identifiant ;
- cohorte persistée ;
- affectation explicite ;
- segment administré.

---

# 13. Pilotes

Un pilote peut être limité à :

- employés Mansa ;
- commerçants sélectionnés ;
- utilisateurs volontaires ;
- région ;
- établissement ;
- partenaire ;
- université ;
- administration ;
- nombre limité de TPE.

Le pilote doit contenir :

- objectifs ;
- participants ;
- durée ;
- support ;
- métriques ;
- procédure d’arrêt ;
- consentement éventuel ;
- rapport final.

---

# 14. Expérimentations A/B

Une expérimentation doit définir :

- hypothèse ;
- variantes ;
- audience ;
- durée ;
- métrique principale ;
- métriques secondaires ;
- seuil statistique ;
- risques ;
- exclusion ;
- propriétaire ;
- décision finale.

---

# 15. Expérimentations interdites

Les tests A/B sont interdits ou fortement limités sur :

- authentification critique ;
- affichage des frais ;
- confirmation de paiement ;
- affichage du bénéficiaire ;
- consentement légal ;
- sécurité ;
- OTP ;
- litiges ;
- fraude ;
- KYC ;
- KYB ;
- remboursement ;
- taux de change final ;
- documents réglementaires ;
- accessibilité obligatoire.

---

# 16. Dépendances entre Feature Flags

Un flag peut dépendre d’un autre.

Exemple :

```text
client.cards.disposable.enabled
dépend de
backend.cards.disposable.enabled
```

Le système doit détecter :

- dépendance manquante ;
- dépendance inactive ;
- cycle ;
- contradiction ;
- activation partielle dangereuse.

---

# 17. Activation d’une fonctionnalité complète

Une fonctionnalité multi-applications peut nécessiter plusieurs flags.

Exemple :

```text
backend.connect.payments.enabled
client.connect.payments.enabled
admin.connect.payments.enabled
notifications.connect.payments.enabled
analytics.connect.payments.enabled
```

Une activation globale doit vérifier toutes les dépendances.

---

# 18. Feature Flags et partenaires

Une intégration partenaire doit pouvoir être contrôlée par :

- pays ;
- environnement ;
- opération ;
- canal ;
- montant ;
- version ;
- horaire ;
- statut partenaire.

Exemple :

```text
partner.orange_money.ml.cash_in.enabled
partner.orange_money.ml.cash_out.enabled
```

---

# 19. Feature Flags et services publics

Un service public doit pouvoir être activé par :

- organisme ;
- pays ;
- région ;
- agent ;
- type de service ;
- canal ;
- version ;
- environnement.

---

# 20. Feature Flags et cartes

Les fonctions cartes peuvent être séparées :

- commande ;
- activation ;
- carte virtuelle ;
- carte jetable ;
- carte temporaire ;
- NFC ;
- Apple Wallet ;
- Google Wallet ;
- remplacement ;
- révélation PIN ;
- contrôle géographique ;
- paiement international.

---

# 21. Feature Flags et TPE

Exemples :

```text
tpe.contactless.enabled
tpe.qr.enabled
tpe.mobile_money.enabled
tpe.refunds.enabled
tpe.offline_mode.enabled
tpe.tip.enabled
tpe.split_payment.enabled
tpe.receipt.print.enabled
```

---

# 22. Feature Flags et Jini

Jini doit avoir des flags distincts pour :

- assistant client ;
- assistant commerce ;
- assistant support ;
- recommandations ;
- actions ;
- analyse financière ;
- génération de contenu ;
- outils sensibles ;
- accès aux données ;
- modèles ;
- pays ;
- langues.

---

# 23. Kill Switch global

Le système doit prévoir des interrupteurs d’urgence.

Exemples :

```text
payments.global.enabled
cards.global.enabled
mobile_money.global.enabled
transfers.global.enabled
jini.actions.global.enabled
public_services.global.enabled
```

L’usage d’un kill switch doit déclencher :

- audit ;
- alerte ;
- notification interne ;
- incident ;
- procédure de reprise ;
- revue post-incident.

---

# 24. Kill Switch par partenaire

Exemples :

```text
partner.visa.enabled
partner.mastercard.enabled
partner.orange_money.enabled
partner.bdm.enabled
```

---

# 25. Kill Switch par pays

Exemple :

```text
country.ml.payments.enabled
```

Ce mécanisme peut être utilisé en cas :

- d’incident ;
- de demande réglementaire ;
- de panne partenaire ;
- de problème de sécurité ;
- de maintenance ;
- de risque financier.

---

# 26. Configuration locale et cache

Les applications peuvent mettre en cache les flags.

Le cache doit définir :

- durée ;
- version ;
- date ;
- environnement ;
- pays ;
- utilisateur ;
- fallback ;
- invalidation ;
- signature éventuelle.

---

# 27. Comportement hors ligne

En mode hors ligne :

- les flags critiques doivent utiliser la valeur la plus sûre ;
- une fonctionnalité sensible doit être désactivée si l’état n’est pas fiable ;
- les flags déjà validés peuvent rester actifs pour les fonctions non critiques ;
- le cache doit être daté ;
- l’application doit vérifier à la reconnexion.

---

# 28. Valeur de secours

Chaque flag doit posséder une valeur de secours.

Pour une fonctionnalité risquée, la valeur de secours recommandée est :

```text
disabled
```

---

# 29. Synchronisation

La synchronisation doit être disponible via :

- récupération au démarrage ;
- actualisation périodique ;
- événement temps réel ;
- push de configuration ;
- rafraîchissement manuel ;
- invalidation du cache.

---

# 30. Cohérence entre applications

Une fonctionnalité ne doit pas être :

- visible sur mobile ;
- refusée par le backend ;
- absente du portail Admin ;
- non supportée par les notifications ;
- non prise en charge par les analytics ;

sans comportement explicite.

---

# 31. Administration

Le portail Admin doit permettre :

- créer un flag ;
- dupliquer un flag ;
- modifier sa valeur ;
- définir les règles ;
- choisir les pays ;
- choisir les segments ;
- définir un pourcentage ;
- programmer une activation ;
- programmer une désactivation ;
- définir une expiration ;
- prévisualiser l’audience ;
- tester ;
- demander une approbation ;
- activer ;
- suspendre ;
- rollback ;
- archiver ;
- consulter l’historique.

---

# 32. Prévisualisation

Avant activation, l’administration doit pouvoir voir :

- nombre d’utilisateurs concernés ;
- pays ;
- segments ;
- versions ;
- appareils ;
- partenaires ;
- applications ;
- conflits ;
- dépendances ;
- risques ;
- valeur actuelle ;
- nouvelle valeur.

---

# 33. Simulation

Le système doit permettre une simulation sans activation réelle.

La simulation doit montrer :

- qui serait éligible ;
- quel résultat serait retourné ;
- quelles règles sont appliquées ;
- quelles dépendances échouent ;
- quels conflits existent.

---

# 34. Approbation

Une activation peut nécessiter :

- propriétaire produit ;
- responsable technique ;
- sécurité ;
- conformité ;
- responsable pays ;
- responsable partenaire ;
- direction ;
- double validation.

---

# 35. Permissions

Exemples :

```text
feature_flag.read
feature_flag.create
feature_flag.update
feature_flag.test
feature_flag.schedule
feature_flag.activate
feature_flag.deactivate
feature_flag.rollback
feature_flag.delete
feature_flag.production.activate
feature_flag.kill_switch.use
feature_flag.audit.read
```

---

# 36. Actions critiques

Actions particulièrement sensibles :

- activation en production ;
- activation à 100 % ;
- modification d’un kill switch ;
- désactivation des paiements ;
- activation d’un partenaire ;
- modification d’un flag de sécurité ;
- modification d’une règle pays ;
- suppression d’un flag actif ;
- modification d’un flag réglementaire.

---

# 37. Double validation

La double validation est recommandée pour :

- production ;
- paiements ;
- ledger ;
- cartes ;
- KYC ;
- fraude ;
- services publics ;
- investissements ;
- accès administratifs ;
- kill switches ;
- partenaires.

---

# 38. Programmation

Une activation peut être programmée.

Elle doit contenir :

- date ;
- heure ;
- fuseau ;
- durée ;
- audience ;
- valeur ;
- approbation ;
- expiration ;
- rollback ;
- responsable.

---

# 39. Expiration

Les flags temporaires doivent avoir une date d’expiration.

À l’expiration :

- ils utilisent leur valeur de secours ;
- une alerte est déclenchée ;
- le propriétaire est notifié ;
- une revue est demandée ;
- le flag peut être archivé.

---

# 40. Gestion de la dette de flags

Chaque flag doit être classé :

- permanent ;
- temporaire ;
- expérimentation ;
- opérationnel ;
- sécurité ;
- partenaire.

Les flags temporaires doivent avoir :

- propriétaire ;
- date de suppression ;
- ticket ;
- condition de clôture.

---

# 41. Nettoyage

Le système doit détecter :

- flag jamais utilisé ;
- flag expiré ;
- flag actif à 100 % depuis longtemps ;
- flag sans propriétaire ;
- flag sans description ;
- flag avec dépendance supprimée ;
- flag contradictoire ;
- code mort associé.

---

# 42. Audit

Chaque modification doit enregistrer :

- flag ;
- ancienne valeur ;
- nouvelle valeur ;
- règles ;
- audience ;
- auteur ;
- approbateur ;
- date ;
- environnement ;
- pays ;
- justification ;
- ticket ;
- métriques ;
- rollback éventuel.

---

# 43. Alertes

Des alertes doivent être déclenchées en cas :

- d’activation production non planifiée ;
- de kill switch utilisé ;
- d’augmentation rapide du pourcentage ;
- de conflit ;
- d’échec de synchronisation ;
- d’activation sans approbation ;
- de flag expiré ;
- de dépendance inactive ;
- de hausse d’erreurs après activation ;
- de baisse de conversion ;
- d’incident de sécurité.

---

# 44. Monitoring

Chaque déploiement doit suivre :

- erreurs ;
- latence ;
- crashs ;
- paiements échoués ;
- taux de réussite ;
- support ;
- fraude ;
- abandon ;
- conversion ;
- satisfaction ;
- revenus ;
- remboursements ;
- anomalies.

---

# 45. Rollback automatique

Un rollback automatique peut être déclenché si :

- taux d’erreur dépasse un seuil ;
- latence dépasse un seuil ;
- taux de paiement réussi baisse ;
- crashs augmentent ;
- fraude augmente ;
- partenaire devient indisponible ;
- seuil de support est dépassé.

Toute règle automatique doit être :

- versionnée ;
- testée ;
- auditable ;
- désactivable ;
- supervisée.

---

# 46. Rapports

Le portail Admin doit fournir :

- flags actifs ;
- flags par pays ;
- flags par application ;
- flags par environnement ;
- pilotes actifs ;
- expérimentations ;
- flags expirés ;
- flags sans propriétaire ;
- historique ;
- performances ;
- rollbacks ;
- incidents liés.

---

# 47. API

Exemples :

```http
GET    /feature-flags
GET    /feature-flags/{key}
POST   /feature-flags
PATCH  /feature-flags/{key}

POST   /feature-flags/{key}/activate
POST   /feature-flags/{key}/deactivate
POST   /feature-flags/{key}/rollback
POST   /feature-flags/{key}/simulate

GET    /feature-flags/evaluate
POST   /feature-flags/evaluate/batch

GET    /feature-flags/{key}/history
GET    /feature-flags/{key}/audience-preview
```

---

# 48. Évaluation backend

Exemple conceptuel :

```json
{
  "key": "client.cards.virtual.enabled",
  "context": {
    "userId": "usr_123",
    "country": "ML",
    "appVersion": "2.3.0",
    "environment": "production"
  }
}
```

Réponse :

```json
{
  "enabled": true,
  "variant": "default",
  "reason": "country_rule",
  "version": 12
}
```

---

# 49. Évaluation en lot

Les applications doivent pouvoir récupérer plusieurs flags en une seule requête afin de :

- réduire la latence ;
- éviter les appels multiples ;
- garantir une version cohérente ;
- faciliter le cache.

---

# 50. Modèles

- FeatureFlag
- FeatureFlagType
- FeatureFlagStatus
- FeatureFlagValue
- FeatureFlagRule
- FeatureFlagCondition
- FeatureFlagSegment
- FeatureFlagAudience
- FeatureFlagEnvironment
- FeatureFlagCountry
- FeatureFlagDependency
- FeatureFlagSchedule
- FeatureFlagApproval
- FeatureFlagVersion
- FeatureFlagEvaluation
- FeatureFlagExperiment
- FeatureFlagVariant
- FeatureFlagMetric
- FeatureFlagRollback
- FeatureFlagAudit

---

# 51. Règles métier

1. Toute nouvelle fonction sensible est désactivée par défaut.
2. Le backend contrôle toujours le flag.
3. Une activation en interface ne suffit pas.
4. Les environnements sont séparés.
5. Les pays sont séparés.
6. Les dépendances doivent être actives.
7. Les cycles de dépendance sont interdits.
8. Les kill switches sont prioritaires.
9. Une interdiction réglementaire ne peut pas être contournée.
10. Les activations production sont auditées.
11. Les flags temporaires expirent.
12. Les flags expirés utilisent une valeur sûre.
13. Les expérimentations critiques sont interdites.
14. Les cohortes doivent être stables.
15. Le rollback doit être disponible.
16. Les valeurs sont typées.
17. Les règles doivent être validées.
18. Les applications utilisent une version cohérente.
19. Les flags critiques ne dépendent pas uniquement du cache.
20. Les changements sont historisés.
21. Les permissions sont appliquées.
22. Les activations sensibles peuvent exiger une double validation.
23. Le monitoring accompagne chaque déploiement.
24. Les flags obsolètes doivent être supprimés.
25. Les actions automatiques sont auditées.

---

# 52. Analytics

Événements possibles :

```text
feature_flag_created
feature_flag_updated
feature_flag_activated
feature_flag_deactivated
feature_flag_rolled_back
feature_flag_evaluated
feature_flag_dependency_failed
feature_flag_expired
feature_flag_kill_switch_used
feature_flag_rollout_started
feature_flag_rollout_increased
feature_flag_rollout_completed
feature_flag_experiment_started
feature_flag_experiment_completed
feature_flag_cleanup_required
```

---

# 53. Tests

- tests de valeur par défaut ;
- tests de règles ;
- tests pays ;
- tests environnement ;
- tests utilisateur ;
- tests segment ;
- tests pourcentage ;
- tests de cohorte stable ;
- tests de dépendance ;
- tests de cycle ;
- tests de kill switch ;
- tests de cache ;
- tests hors ligne ;
- tests de fallback ;
- tests d’expiration ;
- tests de programmation ;
- tests de rollback ;
- tests de permissions ;
- tests de double validation ;
- tests d’audit ;
- tests de monitoring ;
- tests de charge ;
- tests de cohérence multi-applications.

---

# 54. Critères d’acceptation

Le système de Feature Flags est validé lorsque :

- les fonctionnalités peuvent être activées sans redéploiement ;
- le backend applique les règles ;
- les environnements sont séparés ;
- les pays sont configurables ;
- les partenaires sont contrôlables ;
- les déploiements progressifs fonctionnent ;
- les cohortes restent stables ;
- les expérimentations sont encadrées ;
- les kill switches fonctionnent ;
- les rollbacks sont rapides ;
- les dépendances sont vérifiées ;
- les règles sont typées ;
- les activations sensibles sont approuvées ;
- les historiques sont conservés ;
- les flags expirent correctement ;
- les flags obsolètes sont détectés ;
- les métriques sont suivies ;
- les tests couvrent les scénarios critiques.
