# 15 — Gestion des paramètres globaux et de la configuration centrale de Mansa

## 1. Objet du document

Ce document définit le système officiel de configuration centrale de Mansa.

Il couvre :

- les paramètres globaux ;
- les paramètres par pays ;
- les paramètres par environnement ;
- les paramètres par application ;
- les paramètres par partenaire ;
- les paramètres financiers ;
- les paramètres opérationnels ;
- les limites ;
- les frais ;
- les délais ;
- les règles d’affichage ;
- les versions minimales ;
- les configurations TPE ;
- les configurations de sécurité ;
- les paramètres administrables sans modification du code ;
- le versionnement ;
- les validations ;
- les approbations ;
- le déploiement ;
- le rollback ;
- l’audit.

L’objectif est de permettre à Mansa d’évoluer rapidement sans devoir modifier et redéployer le code pour chaque changement métier ou opérationnel.

---

# 2. Principes fondamentaux

## 2.1 La configuration doit être séparée du code

Les valeurs susceptibles d’évoluer ne doivent pas être codées en dur.

Exemples :

- plafonds ;
- frais ;
- commissions ;
- délais ;
- pays disponibles ;
- devises ;
- partenaires ;
- versions minimales ;
- catégories ;
- horaires ;
- règles de remboursement ;
- limites de fichiers ;
- messages de maintenance ;
- seuils de sécurité ;
- coordonnées de support.

## 2.2 Le backend reste l’autorité

Une configuration utilisée pour une règle métier doit être récupérée ou validée côté backend.

Une valeur présente uniquement dans l’application cliente ne doit pas être considérée comme officielle.

## 2.3 Valeur sûre par défaut

Chaque paramètre doit disposer d’une valeur par défaut sûre.

En cas :

- d’erreur ;
- d’absence de configuration ;
- de configuration invalide ;
- de problème de cache ;
- d’échec de synchronisation ;

le système doit adopter le comportement le moins risqué.

## 2.4 Configuration typée

Chaque paramètre doit avoir un type explicite.

Types possibles :

- booléen ;
- entier ;
- décimal ;
- montant ;
- chaîne ;
- date ;
- durée ;
- liste ;
- objet ;
- enum ;
- pourcentage ;
- référence ;
- expression contrôlée.

## 2.5 Validation obligatoire

Une configuration ne doit pas être publiée si elle ne respecte pas :

- son type ;
- son schéma ;
- ses limites ;
- ses dépendances ;
- ses règles métier ;
- les permissions ;
- les contraintes de pays ;
- les contraintes de partenaire ;
- les règles de sécurité.

---

# 3. Catégories de paramètres

## 3.1 Paramètres globaux

Ils s’appliquent à toute la plateforme.

Exemples :

```text
platform.maintenance.enabled
platform.support.default_email
platform.default_locale
platform.session.default_timeout
```

## 3.2 Paramètres par pays

Exemples :

```text
country.ml.default_currency
country.ml.minimum_age
country.ml.support_phone
country.ml.kyc.required_level
```

## 3.3 Paramètres par application

Exemples :

```text
client.home.max_widgets
commerce.catalog.max_products
tpe.receipt.default_print
admin.session.timeout
```

## 3.4 Paramètres par environnement

Exemples :

- Démo ;
- Recette ;
- Préproduction ;
- Production.

Une valeur en recette ne doit jamais modifier automatiquement la production.

## 3.5 Paramètres par partenaire

Exemples :

```text
partner.orange_money.timeout
partner.bdm.card_order.enabled
partner.visa.webhook.retry_limit
```

## 3.6 Paramètres par produit

Exemples :

- cartes ;
- transferts ;
- Mobile Money ;
- commerce ;
- fidélité ;
- investissements ;
- services publics ;
- Jini ;
- TPE.

## 3.7 Paramètres par organisation

Un commerce, une institution ou un partenaire peut disposer de paramètres spécifiques.

Exemples :

- devise de règlement ;
- politique de remboursement ;
- couleur du mini-site ;
- nombre maximal d’employés ;
- règles de caisse ;
- horaires ;
- reçus ;
- permissions personnalisées.

---

# 4. Structure d’un paramètre

Chaque paramètre doit contenir :

- identifiant ;
- clé unique ;
- nom ;
- description ;
- catégorie ;
- domaine ;
- type ;
- valeur par défaut ;
- valeur courante ;
- schéma de validation ;
- unité ;
- environnement ;
- pays ;
- application ;
- organisation ;
- partenaire ;
- niveau de sensibilité ;
- statut ;
- date de création ;
- date d’effet ;
- date d’expiration ;
- auteur ;
- approbateur ;
- version ;
- source ;
- historique ;
- procédure de rollback.

---

# 5. Convention de nommage

Format recommandé :

```text
scope.domain.parameter
```

Exemples :

```text
global.security.session_timeout
country.ml.payment.daily_limit
client.cards.maximum_virtual_cards
commerce.inventory.low_stock_threshold
tpe.refund.maximum_amount
partner.orange_money.request_timeout
```

Les clés doivent être :

- stables ;
- uniques ;
- compréhensibles ;
- indépendantes du texte affiché ;
- documentées ;
- non ambiguës.

---

# 6. Statuts

Un paramètre peut être :

- brouillon ;
- en validation ;
- approuvé ;
- planifié ;
- actif ;
- suspendu ;
- expiré ;
- remplacé ;
- archivé ;
- rejeté.

---

# 7. Hiérarchie et priorité

Plusieurs niveaux peuvent définir la même clé.

Ordre recommandé :

1. blocage de sécurité ;
2. blocage réglementaire ;
3. valeur globale obligatoire ;
4. valeur environnement ;
5. valeur pays ;
6. valeur partenaire ;
7. valeur organisation ;
8. valeur application ;
9. valeur utilisateur autorisée ;
10. valeur par défaut.

Une valeur locale ne doit pas contourner une restriction supérieure.

---

# 8. Héritage

Un paramètre peut hériter d’une valeur supérieure.

Exemple :

```text
global.payment.timeout = 30 secondes
country.ml.payment.timeout = 45 secondes
partner.orange_money.payment.timeout = 60 secondes
```

Le système doit indiquer clairement :

- valeur effective ;
- source ;
- niveau d’héritage ;
- éventuelle surcharge ;
- date d’effet.

---

# 9. Valeur effective

L’API de configuration doit pouvoir retourner :

- la valeur finale ;
- la valeur brute ;
- la source ;
- le niveau ;
- la version ;
- la date d’effet ;
- les règles appliquées.

Exemple :

```json
{
  "key": "payment.timeout",
  "value": 45,
  "unit": "seconds",
  "source": "country.ml",
  "version": 8
}
```

---

# 10. Paramètres financiers

Exemples :

- frais fixes ;
- frais variables ;
- commissions ;
- taux ;
- marges ;
- plafonds ;
- minimums ;
- maximums ;
- règles d’arrondi ;
- délais de règlement ;
- réserves ;
- seuils d’approbation ;
- limites de remboursement ;
- limites de retrait ;
- limites de transfert.

Toute modification financière doit être :

- versionnée ;
- datée ;
- testée ;
- approuvée ;
- auditée ;
- liée à une date d’effet.

---

# 11. Paramètres de paiement

Exemples :

```text
payment.minimum_amount
payment.maximum_amount
payment.default_timeout
payment.pending_expiration
payment.refund_window
payment.retry_limit
payment.idempotency_retention
```

---

# 12. Paramètres de transfert

Exemples :

- plafond par transaction ;
- plafond journalier ;
- plafond mensuel ;
- nombre maximal de bénéficiaires ;
- délai d’annulation ;
- authentification requise ;
- niveau KYC ;
- frais ;
- pays autorisés ;
- devises autorisées.

---

# 13. Paramètres de carte

Exemples :

- nombre maximal de cartes ;
- délai d’activation ;
- nombre d’essais PIN ;
- plafond sans contact ;
- plafond de retrait ;
- durée de carte virtuelle ;
- durée de carte temporaire ;
- coût de remplacement ;
- pays autorisés ;
- catégories marchandes interdites ;
- délai d’expédition estimé.

---

# 14. Paramètres Mobile Money

Exemples :

- opérateur actif ;
- timeout ;
- nombre de retries ;
- limites ;
- frais ;
- montant minimum ;
- montant maximum ;
- délai d’expiration ;
- délai de confirmation ;
- règle de statut incertain ;
- réconciliation.

---

# 15. Paramètres Commerce

Exemples :

- nombre maximal d’établissements ;
- nombre maximal d’employés ;
- nombre maximal de produits ;
- seuil de stock faible ;
- règle d’inventaire ;
- délai de remboursement ;
- montant d’approbation manager ;
- formats de reçus ;
- taxes ;
- horaires ;
- devise de règlement.

---

# 16. Paramètres TPE

Exemples :

- durée de session ;
- verrouillage automatique ;
- montant maximal caissier ;
- remboursement maximal ;
- impression automatique ;
- pourboire activé ;
- mode hors ligne ;
- nombre maximal d’opérations en attente ;
- délai de synchronisation ;
- version minimale ;
- mise à jour obligatoire ;
- langue par défaut.

---

# 17. Paramètres de sécurité

Exemples :

- durée de session ;
- nombre de tentatives ;
- délai de verrouillage ;
- durée OTP ;
- longueur PIN ;
- 2FA obligatoire ;
- biométrie autorisée ;
- expiration des appareils ;
- réauthentification ;
- délai d’inactivité ;
- limite de requêtes ;
- seuils de fraude ;
- rotation des secrets.

Les valeurs critiques doivent avoir des limites minimales ou maximales non contournables.

---

# 18. Paramètres KYC et KYB

Exemples :

- niveau requis ;
- documents acceptés ;
- taille maximale ;
- durée de validité ;
- vérification automatique ;
- revue manuelle ;
- délai d’expiration ;
- âge minimal ;
- seuil de transaction ;
- seuil de revue renforcée.

---

# 19. Paramètres de notifications

Exemples :

- canaux actifs ;
- nombre maximal quotidien ;
- délai de retry ;
- plage silencieuse ;
- expiration ;
- fallback ;
- priorité ;
- durée de conservation ;
- contenu écran verrouillé ;
- fréquence marketing.

---

# 20. Paramètres Jini

Exemples :

- modèle actif ;
- outils autorisés ;
- limites de requêtes ;
- longueur maximale ;
- langue ;
- pays ;
- données accessibles ;
- durée de conservation ;
- escalade humaine ;
- catégories bloquées ;
- température ;
- seuil de confiance ;
- budget d’usage.

---

# 21. Paramètres de fichiers

Exemples :

- taille maximale ;
- formats autorisés ;
- nombre maximal ;
- durée de conservation ;
- antivirus ;
- compression ;
- qualité d’image ;
- résolution ;
- chiffrement ;
- délai d’URL temporaire.

---

# 22. Paramètres de recherche

Exemples :

- nombre de résultats ;
- distance géographique ;
- tolérance aux fautes ;
- catégories ;
- filtres ;
- classement ;
- contenus sponsorisés ;
- délai de cache ;
- langues ;
- pays.

---

# 23. Paramètres de support

Exemples :

- horaires ;
- canaux ;
- SLA ;
- priorités ;
- délai de réponse ;
- escalade ;
- pays ;
- langue ;
- catégories ;
- nombre maximal de pièces jointes ;
- délai de clôture automatique.

---

# 24. Paramètres de maintenance

Exemples :

```text
maintenance.enabled
maintenance.start_at
maintenance.end_at
maintenance.message
maintenance.allowed_roles
maintenance.read_only_mode
```

Le système doit pouvoir activer :

- maintenance complète ;
- lecture seule ;
- maintenance par module ;
- maintenance par pays ;
- maintenance par partenaire ;
- maintenance par application.

---

# 25. Paramètres de version d’application

Le système doit gérer :

- version minimale ;
- version recommandée ;
- version bloquée ;
- mise à jour obligatoire ;
- mise à jour facultative ;
- message ;
- lien de téléchargement ;
- date d’effet ;
- plateforme ;
- pays ;
- environnement.

---

# 26. Paramètres d’abonnement

Exemples :

- prix ;
- période ;
- essai ;
- fonctionnalités ;
- limites ;
- commissions ;
- remise ;
- période de grâce ;
- suspension ;
- facturation ;
- pays ;
- devise.

---

# 27. Paramètres réglementaires

Ils peuvent inclure :

- niveau KYC ;
- seuils AML ;
- conservation ;
- limites ;
- pays interdits ;
- documents ;
- mentions obligatoires ;
- consentements ;
- âge ;
- restrictions de service.

Ces paramètres doivent être protégés par des permissions renforcées.

---

# 28. Paramètres éditoriaux

Exemples :

- texte d’accueil ;
- bannières ;
- FAQ ;
- messages d’aide ;
- contenus de maintenance ;
- catégories ;
- descriptions ;
- pages légales ;
- annonces ;
- campagnes.

Le contenu éditorial ne doit pas être mélangé aux règles financières critiques.

---

# 29. Secrets et configuration sensible

Les secrets ne doivent pas être stockés dans le système de paramètres classique.

Sont concernés :

- clés API ;
- mots de passe ;
- certificats ;
- clés privées ;
- secrets de signature ;
- tokens partenaires ;
- secrets JWT.

Le paramètre peut uniquement référencer un secret stocké dans un gestionnaire sécurisé.

Exemple :

```text
partner.orange_money.api_secret_ref
```

---

# 30. Administration

Le portail Admin doit permettre :

- rechercher un paramètre ;
- filtrer ;
- consulter sa valeur effective ;
- consulter l’héritage ;
- modifier ;
- dupliquer ;
- programmer ;
- valider ;
- approuver ;
- publier ;
- suspendre ;
- restaurer ;
- comparer ;
- exporter ;
- importer ;
- consulter l’historique ;
- simuler l’impact.

---

# 31. Éditeur selon le type

L’interface doit adapter le champ au type.

Exemples :

- interrupteur pour booléen ;
- champ numérique pour montant ;
- date picker ;
- liste déroulante ;
- sélecteur de pays ;
- éditeur JSON validé ;
- durée ;
- pourcentage ;
- référence partenaire ;
- multi-sélection.

---

# 32. Validation en temps réel

Avant enregistrement, l’administration doit afficher :

- type invalide ;
- valeur hors limite ;
- dépendance manquante ;
- conflit ;
- pays incompatible ;
- partenaire inactif ;
- risque ;
- valeur effective après modification ;
- impact estimé.

---

# 33. Simulation d’impact

Avant publication, le système doit pouvoir simuler :

- utilisateurs concernés ;
- pays ;
- applications ;
- partenaires ;
- opérations ;
- montants ;
- règles dépendantes ;
- écrans affectés ;
- risques ;
- changements de frais ;
- changements de plafonds.

---

# 34. Prévisualisation

Pour un paramètre d’interface ou de contenu, le portail doit pouvoir afficher un aperçu.

Exemples :

- bannière ;
- message ;
- reçu ;
- e-mail ;
- notification ;
- écran de maintenance ;
- format tarifaire.

---

# 35. Import et export

Les paramètres peuvent être importés ou exportés dans un format structuré.

Exigences :

- schéma ;
- version ;
- environnement ;
- pays ;
- validation ;
- aperçu des changements ;
- approbation ;
- rapport d’erreur ;
- audit.

Un import ne doit jamais écraser silencieusement une configuration critique.

---

# 36. Comparaison

Le portail doit permettre de comparer :

- deux versions ;
- deux pays ;
- deux environnements ;
- deux partenaires ;
- deux organisations ;
- avant et après ;
- valeur brute et valeur effective.

---

# 37. Planification

Une modification peut être programmée.

Elle doit définir :

- valeur ;
- date d’effet ;
- date de fin ;
- fuseau ;
- périmètre ;
- approbation ;
- rollback ;
- notification ;
- responsable.

---

# 38. Expiration

Un paramètre temporaire doit pouvoir expirer automatiquement.

Exemples :

- promotion ;
- plafond exceptionnel ;
- période de maintenance ;
- règle pilote ;
- remise ;
- configuration d’incident.

À expiration :

- la valeur précédente est restaurée ;
- une valeur de secours est appliquée ;
- un événement d’audit est créé ;
- les responsables sont notifiés.

---

# 39. Rollback

Toute modification importante doit pouvoir être annulée.

Le rollback doit :

- restaurer une version précédente ;
- vérifier les dépendances ;
- être audité ;
- exiger une justification ;
- être limité par permission ;
- déclencher une synchronisation ;
- notifier les responsables.

---

# 40. Cache

Les paramètres peuvent être mis en cache.

Le cache doit gérer :

- clé ;
- version ;
- date ;
- TTL ;
- environnement ;
- pays ;
- application ;
- invalidation ;
- fallback ;
- synchronisation.

---

# 41. Invalidation

Une modification publiée doit invalider les caches concernés.

Méthodes possibles :

- événement ;
- message ;
- version globale ;
- rafraîchissement ;
- expiration ;
- push de configuration.

---

# 42. Mode hors ligne

Les applications peuvent utiliser une copie locale de certains paramètres.

Exigences :

- signature ou contrôle d’intégrité ;
- date ;
- version ;
- expiration ;
- valeur sûre ;
- liste de paramètres autorisés hors ligne.

Les paramètres financiers sensibles ne doivent pas dépendre uniquement d’une copie locale.

---

# 43. Cohérence multi-applications

Une configuration partagée doit produire un comportement cohérent entre :

- Client ;
- Commerce ;
- TPE ;
- Admin Lite ;
- Annuaire ;
- sites web ;
- portail Admin ;
- backend ;
- notifications ;
- Jini.

---

# 44. Dépendances

Un paramètre peut dépendre d’un autre.

Exemple :

```text
cards.virtual.enabled = true
nécessite
cards.module.enabled = true
```

Le système doit détecter :

- dépendance inactive ;
- cycle ;
- valeur incompatible ;
- référence inexistante ;
- dépendance expirée.

---

# 45. Contraintes

Une contrainte peut définir :

- minimum ;
- maximum ;
- liste autorisée ;
- expression ;
- dépendance ;
- compatibilité ;
- pays ;
- devise ;
- rôle ;
- environnement ;
- version.

---

# 46. Approbation

Les paramètres critiques peuvent exiger :

- responsable produit ;
- finance ;
- sécurité ;
- conformité ;
- responsable pays ;
- responsable partenaire ;
- direction ;
- double validation.

---

# 47. Paramètres critiques

Exemples :

- plafonds financiers ;
- frais ;
- commissions ;
- taux ;
- règles KYC ;
- seuils fraude ;
- durée OTP ;
- règles ledger ;
- activation partenaire ;
- version minimale ;
- maintenance globale ;
- règles de remboursement ;
- restrictions pays.

---

# 48. Permissions

Exemples :

```text
configuration.read
configuration.create
configuration.update
configuration.validate
configuration.approve
configuration.publish
configuration.schedule
configuration.rollback
configuration.import
configuration.export
configuration.critical.update
configuration.production.publish
configuration.audit.read
```

---

# 49. Double validation

Recommandée pour :

- production ;
- paiements ;
- cartes ;
- ledger ;
- frais ;
- commissions ;
- plafonds ;
- sécurité ;
- KYC ;
- fraude ;
- partenaires ;
- services publics ;
- investissements.

---

# 50. Audit

Chaque modification doit enregistrer :

- clé ;
- ancienne valeur ;
- nouvelle valeur ;
- valeur effective ;
- auteur ;
- approbateur ;
- environnement ;
- pays ;
- partenaire ;
- organisation ;
- date ;
- motif ;
- ticket ;
- version ;
- date d’effet ;
- rollback éventuel.

---

# 51. Alertes

Une alerte peut être déclenchée si :

- un paramètre critique change ;
- un plafond augmente fortement ;
- un frais passe à zéro ;
- une règle sécurité est affaiblie ;
- une valeur de production est modifiée sans planification ;
- une configuration expire ;
- une valeur devient invalide ;
- une dépendance disparaît ;
- un cache ne se met pas à jour ;
- un partenaire reçoit une configuration incompatible.

---

# 52. Monitoring

Le système doit surveiller :

- erreurs de chargement ;
- clés manquantes ;
- valeurs invalides ;
- divergence de versions ;
- cache obsolète ;
- délai de propagation ;
- rollback ;
- échec de publication ;
- incohérence entre applications ;
- utilisation d’une valeur de secours.

---

# 53. API

Exemples :

```http
GET    /configurations
GET    /configurations/{key}
POST   /configurations
PATCH  /configurations/{key}

GET    /configurations/{key}/effective-value
GET    /configurations/{key}/history
GET    /configurations/{key}/dependencies

POST   /configurations/{key}/validate
POST   /configurations/{key}/approve
POST   /configurations/{key}/publish
POST   /configurations/{key}/rollback
POST   /configurations/{key}/simulate

GET    /configuration-bundles
POST   /configuration-bundles/import
POST   /configuration-bundles/export
```

---

# 54. Récupération groupée

Les applications doivent pouvoir récupérer plusieurs paramètres en une seule requête.

Exemple :

```http
GET /configurations/bundle?app=client&country=ML&version=2.4.0
```

La réponse doit inclure :

- version du bundle ;
- date ;
- expiration ;
- paramètres ;
- signature éventuelle ;
- environnement ;
- fallback.

---

# 55. Version du bundle

Chaque ensemble de configuration doit avoir une version globale.

Cela permet :

- invalidation rapide ;
- comparaison ;
- rollback ;
- détection de divergence ;
- cache ;
- synchronisation.

---

# 56. Modèles

- ConfigurationDefinition
- ConfigurationValue
- ConfigurationType
- ConfigurationScope
- ConfigurationEnvironment
- ConfigurationCountry
- ConfigurationPartner
- ConfigurationOrganization
- ConfigurationApplication
- ConfigurationConstraint
- ConfigurationDependency
- ConfigurationVersion
- ConfigurationApproval
- ConfigurationSchedule
- ConfigurationRollback
- ConfigurationBundle
- ConfigurationCache
- ConfigurationAudit
- ConfigurationAlert

---

# 57. Règles métier

1. Une configuration dynamique n’est pas codée en dur.
2. Chaque paramètre possède un type.
3. Chaque paramètre possède une valeur par défaut.
4. Les valeurs sont validées avant publication.
5. Le backend reste l’autorité.
6. Les environnements sont séparés.
7. Les pays sont séparés.
8. Les secrets sont stockés hors du système de configuration.
9. Les valeurs critiques sont auditées.
10. Les modifications production sont protégées.
11. Les dépendances doivent être valides.
12. Les cycles sont interdits.
13. Les paramètres temporaires peuvent expirer.
14. Les rollbacks sont disponibles.
15. Les caches sont invalidés après publication.
16. Les applications connaissent la version utilisée.
17. Les valeurs hors ligne utilisent une stratégie sûre.
18. Une valeur locale ne contourne pas une restriction globale.
19. Les imports sont validés.
20. Les modifications importantes sont simulables.
21. Les paramètres critiques peuvent exiger une double validation.
22. La valeur effective doit être explicable.
23. Les valeurs précédentes restent consultables.
24. Une configuration invalide ne doit pas être appliquée.
25. Les divergences doivent déclencher une alerte.

---

# 58. Analytics

Événements possibles :

```text
configuration_created
configuration_updated
configuration_validated
configuration_approved
configuration_published
configuration_scheduled
configuration_expired
configuration_rolled_back
configuration_imported
configuration_exported
configuration_dependency_failed
configuration_invalid_detected
configuration_cache_refreshed
configuration_fallback_used
configuration_production_updated
```

---

# 59. Tests

- tests de types ;
- tests de validation ;
- tests de valeurs par défaut ;
- tests d’héritage ;
- tests de priorité ;
- tests de pays ;
- tests d’environnement ;
- tests de partenaire ;
- tests d’organisation ;
- tests de dépendance ;
- tests de cycle ;
- tests d’expiration ;
- tests de planification ;
- tests de rollback ;
- tests d’import ;
- tests d’export ;
- tests de cache ;
- tests hors ligne ;
- tests de permissions ;
- tests de double validation ;
- tests d’audit ;
- tests de cohérence multi-applications ;
- tests de charge.

---

# 60. Critères d’acceptation

Le système de paramètres globaux est validé lorsque :

- les valeurs évolutives ne sont pas codées en dur ;
- les paramètres sont typés ;
- les paramètres sont validés ;
- les valeurs effectives sont explicables ;
- les environnements sont isolés ;
- les pays sont configurables ;
- les partenaires sont configurables ;
- les paramètres financiers sont versionnés ;
- les paramètres critiques sont protégés ;
- les changements sont auditables ;
- les valeurs peuvent être planifiées ;
- les paramètres temporaires expirent ;
- le rollback fonctionne ;
- les caches sont synchronisés ;
- les applications connaissent la version utilisée ;
- les secrets ne sont pas exposés ;
- les imports et exports sont contrôlés ;
- les tests couvrent les configurations critiques.
