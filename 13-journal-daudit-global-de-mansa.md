# 13 — Journal d’audit global de Mansa

## 1. Objet du document

Ce document définit le système officiel de journalisation et d’audit de Mansa.

Il couvre :

- les actions utilisateurs ;
- les actions commerçants ;
- les actions TPE ;
- les actions administratives ;
- les actions partenaires ;
- les opérations financières ;
- les changements de configuration ;
- les accès aux données sensibles ;
- les décisions de conformité ;
- les incidents ;
- les exports ;
- les modifications de rôles et permissions ;
- les actions automatisées ;
- les actions de Jini ;
- les événements techniques critiques.

L’objectif est de garantir qu’une action importante puisse toujours être :

- attribuée ;
- datée ;
- expliquée ;
- vérifiée ;
- reconstituée ;
- reliée à son contexte ;
- protégée contre la modification ;
- utilisée lors d’un contrôle, d’un litige ou d’une enquête.

---

# 2. Principes fondamentaux

## 2.1 Toute action critique doit laisser une trace

Une action critique ne doit jamais exister uniquement dans l’interface ou dans un log temporaire.

Elle doit produire un événement d’audit durable.

Exemples :

- suspension d’un compte ;
- remboursement ;
- changement de plafond ;
- modification de frais ;
- attribution d’un rôle ;
- validation KYC ;
- blocage d’une carte ;
- activation d’un terminal ;
- correction ledger ;
- publication d’un document légal.

---

## 2.2 L’audit ne doit pas être modifiable

Un événement d’audit confirmé ne doit pas être modifié ni supprimé par un utilisateur standard ou un administrateur classique.

Toute correction doit produire :

- un nouvel événement ;
- une référence vers l’événement concerné ;
- un motif ;
- un auteur ;
- une date ;
- une approbation éventuelle.

---

## 2.3 L’audit doit être séparé des logs techniques

Les logs techniques servent au diagnostic.

Le journal d’audit sert à prouver et reconstituer une action.

Les deux peuvent être liés, mais ne doivent pas être confondus.

---

## 2.4 Une action doit être attribuable

Chaque événement doit pouvoir indiquer son auteur réel :

- utilisateur ;
- employé ;
- administrateur ;
- partenaire ;
- service automatisé ;
- terminal ;
- application ;
- tâche planifiée ;
- intelligence artificielle ;
- webhook partenaire.

---

## 2.5 L’audit doit respecter la confidentialité

Le journal d’audit ne doit pas contenir inutilement :

- mot de passe ;
- PIN ;
- CVV ;
- OTP ;
- numéro complet de carte ;
- secret API ;
- clé privée ;
- contenu privé complet ;
- document sensible non nécessaire.

---

# 3. Événements audités

## 3.1 Authentification

Événements possibles :

- inscription ;
- connexion réussie ;
- connexion échouée ;
- déconnexion ;
- réinitialisation du mot de passe ;
- modification du PIN ;
- activation biométrique ;
- ajout d’un appareil ;
- révocation d’un appareil ;
- activation 2FA ;
- désactivation 2FA ;
- récupération de compte ;
- session révoquée.

---

## 3.2 Identité et KYC

Événements possibles :

- dossier KYC créé ;
- document ajouté ;
- document remplacé ;
- vérification lancée ;
- vérification réussie ;
- dossier refusé ;
- complément demandé ;
- validation manuelle ;
- escalade ;
- changement de niveau KYC ;
- décision de conformité.

---

## 3.3 KYB et commerce

Événements possibles :

- entreprise créée ;
- établissement ajouté ;
- bénéficiaire effectif ajouté ;
- KYB validé ;
- KYB refusé ;
- commerce activé ;
- commerce suspendu ;
- employé invité ;
- rôle employé modifié ;
- compte de règlement modifié ;
- abonnement professionnel modifié.

---

## 3.4 Paiements

Événements possibles :

- paiement initié ;
- paiement autorisé ;
- paiement refusé ;
- paiement capturé ;
- paiement annulé ;
- paiement remboursé ;
- paiement contesté ;
- frais modifiés ;
- commission modifiée ;
- statut forcé ;
- paiement placé en attente ;
- rapprochement effectué.

---

## 3.5 Ledger

Événements possibles :

- transaction ledger créée ;
- écriture comptabilisée ;
- réservation créée ;
- réservation capturée ;
- réservation libérée ;
- ajustement demandé ;
- ajustement approuvé ;
- contre-écriture créée ;
- période clôturée ;
- écart détecté ;
- écart résolu.

---

## 3.6 Cartes

Événements possibles :

- carte commandée ;
- carte émise ;
- carte activée ;
- carte verrouillée ;
- carte déverrouillée ;
- carte suspendue ;
- carte opposée ;
- PIN révélé ;
- PIN modifié ;
- plafond modifié ;
- design modifié ;
- remplacement demandé ;
- carte ajoutée à un wallet numérique.

---

## 3.7 TPE

Événements possibles :

- terminal créé ;
- terminal activé ;
- terminal associé ;
- terminal réassigné ;
- certificat installé ;
- employé connecté ;
- paiement traité ;
- remboursement effectué ;
- clôture effectuée ;
- terminal suspendu ;
- mise à jour appliquée ;
- configuration modifiée.

---

## 3.8 Notifications

Événements possibles :

- modèle créé ;
- modèle modifié ;
- modèle publié ;
- campagne créée ;
- campagne approuvée ;
- campagne envoyée ;
- notification critique envoyée ;
- consentement marketing modifié ;
- préférence utilisateur modifiée.

---

## 3.9 Administration

Événements possibles :

- rôle créé ;
- rôle modifié ;
- rôle supprimé ;
- permission attribuée ;
- permission révoquée ;
- accès temporaire accordé ;
- accès d’urgence utilisé ;
- configuration modifiée ;
- feature flag activé ;
- export lancé ;
- utilisateur consulté ;
- action sensible effectuée.

---

## 3.10 Services publics

Événements possibles :

- amende créée ;
- amende modifiée ;
- amende annulée ;
- agent identifié ;
- paiement public enregistré ;
- preuve générée ;
- dossier validé ;
- bourse attribuée ;
- carte étudiante émise ;
- opération rejetée ;
- décision institutionnelle.

---

## 3.11 Jini

Événements possibles :

- recommandation générée ;
- action proposée ;
- action confirmée ;
- action refusée ;
- contenu sensible demandé ;
- outil appelé ;
- réponse bloquée ;
- erreur IA ;
- escalade vers un humain ;
- modification de règle IA.

Jini ne doit jamais exécuter une action critique sans qu’un acteur autorisé soit identifiable.

---

# 4. Structure d’un événement d’audit

Chaque événement doit contenir au minimum :

- identifiant unique ;
- type d’événement ;
- catégorie ;
- date et heure ;
- acteur ;
- type d’acteur ;
- action ;
- ressource ;
- identifiant de ressource ;
- résultat ;
- pays ;
- environnement ;
- application ;
- appareil ;
- adresse IP si autorisée ;
- corrélation ;
- session ;
- motif ;
- ancienne valeur éventuelle ;
- nouvelle valeur éventuelle ;
- métadonnées ;
- niveau de sensibilité ;
- niveau de criticité ;
- version ;
- empreinte d’intégrité.

---

# 5. Acteurs

Types possibles :

- USER ;
- MERCHANT_USER ;
- TERMINAL_USER ;
- ADMIN ;
- PUBLIC_AGENT ;
- PARTNER_USER ;
- SERVICE ;
- SCHEDULED_JOB ;
- WEBHOOK ;
- JINI ;
- SYSTEM ;
- UNKNOWN_ACTOR.

Un acteur inconnu sur une action critique doit déclencher une alerte.

---

# 6. Ressources auditées

Exemples :

- User
- Merchant
- Establishment
- Wallet
- LedgerAccount
- Payment
- Transaction
- Card
- Terminal
- Role
- Permission
- Configuration
- NotificationTemplate
- PublicServiceCase
- KycCase
- KybCase
- Document
- SupportTicket
- Partner
- Country
- Currency
- FeatureFlag

---

# 7. Types d’action

Actions standard :

- CREATE ;
- READ ;
- UPDATE ;
- DELETE ;
- APPROVE ;
- REJECT ;
- SUSPEND ;
- ACTIVATE ;
- REVOKE ;
- EXPORT ;
- IMPORT ;
- ASSIGN ;
- UNASSIGN ;
- LOGIN ;
- LOGOUT ;
- RESET ;
- OVERRIDE ;
- EXECUTE ;
- PUBLISH ;
- ARCHIVE ;
- RESTORE.

---

# 8. Résultats

Valeurs possibles :

- SUCCESS ;
- FAILURE ;
- DENIED ;
- PARTIAL ;
- PENDING ;
- CANCELLED ;
- EXPIRED ;
- ERROR ;
- BLOCKED.

Un refus d’accès important doit également être audité.

---

# 9. Niveaux de criticité

## 9.1 Faible

Exemple :

- consultation d’un écran non sensible ;
- changement d’une préférence d’affichage.

## 9.2 Moyenne

Exemple :

- modification d’un profil ;
- modification d’une notification.

## 9.3 Élevée

Exemple :

- modification de plafond ;
- attribution de permission ;
- remboursement ;
- blocage de compte.

## 9.4 Critique

Exemple :

- ajustement ledger ;
- accès d’urgence ;
- activation production ;
- export massif ;
- modification d’un partenaire ;
- suppression d’un administrateur ;
- changement de clé ou certificat.

---

# 10. Ancienne et nouvelle valeur

Pour les modifications importantes, l’événement doit conserver :

- valeur précédente ;
- valeur suivante ;
- champs modifiés ;
- auteur ;
- motif ;
- date d’effet ;
- approbation.

Les valeurs sensibles peuvent être :

- masquées ;
- hachées ;
- remplacées par un indicateur ;
- stockées dans un espace protégé distinct.

---

# 11. Corrélation

Chaque événement doit pouvoir être relié à :

- requête ;
- transaction ;
- paiement ;
- session ;
- ticket ;
- incident ;
- workflow ;
- partenaire ;
- campagne ;
- export ;
- tâche asynchrone.

Un identifiant de corrélation doit permettre de reconstituer un parcours complet.

---

# 12. Audit des lectures sensibles

Certaines consultations doivent être auditées.

Exemples :

- consultation d’un dossier KYC ;
- consultation d’un document d’identité ;
- affichage de données financières détaillées ;
- export d’une liste ;
- consultation d’un utilisateur VIP ;
- accès à un dossier fraude ;
- accès à une clé ou configuration sensible.

---

# 13. Audit des exports

Chaque export doit enregistrer :

- auteur ;
- type ;
- filtre ;
- volume ;
- format ;
- date ;
- destinataire ;
- justification ;
- approbation éventuelle ;
- date d’expiration ;
- statut de téléchargement ;
- empreinte du fichier.

---

# 14. Audit des actions en masse

Une action en masse doit enregistrer :

- nombre de ressources ;
- critères ;
- liste ou référence des ressources ;
- auteur ;
- motif ;
- résultat global ;
- résultats individuels ;
- erreurs ;
- approbation ;
- corrélation.

---

# 15. Audit des actions automatiques

Une action automatique doit enregistrer :

- service ;
- règle ;
- version ;
- déclencheur ;
- données utilisées ;
- décision ;
- résultat ;
- date ;
- configuration ;
- responsable métier.

Exemples :

- blocage automatique ;
- alerte fraude ;
- expiration ;
- suspension ;
- calcul de frais ;
- clôture ;
- génération d’un document.

---

# 16. Audit des décisions IA

Pour une décision ou recommandation Jini, conserver lorsque nécessaire :

- type de modèle ;
- version ;
- prompt système applicable ;
- outils utilisés ;
- données de contexte autorisées ;
- résultat ;
- niveau de confiance éventuel ;
- validation humaine ;
- action finale ;
- motif de blocage ;
- corrélation.

Les conversations privées ne doivent pas être copiées intégralement dans l’audit sans nécessité.

---

# 17. Intégrité

Le système doit protéger les événements contre :

- suppression ;
- altération ;
- réécriture ;
- insertion frauduleuse ;
- changement de date ;
- changement d’auteur.

Techniques possibles :

- stockage append-only ;
- hachage ;
- chaînage d’empreintes ;
- signature ;
- stockage immuable ;
- réplication ;
- contrôle d’intégrité ;
- export scellé.

---

# 18. Horodatage

Chaque événement doit utiliser :

- une date UTC ;
- un fuseau d’affichage ;
- une source d’horloge fiable ;
- un ordre logique ;
- une précision suffisante.

L’heure locale de l’appareil ne doit pas être la seule référence.

---

# 19. Conservation

La durée de conservation dépend de :

- type d’événement ;
- pays ;
- réglementation ;
- finalité ;
- contrat ;
- politique interne ;
- litige ;
- incident ;
- obligation comptable.

Chaque catégorie doit avoir une politique explicite.

---

# 20. Archivage

Les événements anciens peuvent être archivés.

L’archivage doit préserver :

- intégrité ;
- recherche ;
- sécurité ;
- accès autorisé ;
- empreinte ;
- chaîne de conservation ;
- capacité d’export.

---

# 21. Suppression et anonymisation

Un événement d’audit ne doit pas être supprimé uniquement à la demande d’un utilisateur si une obligation légale impose sa conservation.

Lorsque possible, certaines données peuvent être :

- anonymisées ;
- pseudonymisées ;
- masquées ;
- dissociées.

La décision doit être documentée.

---

# 22. Recherche

Le portail Admin doit permettre une recherche par :

- date ;
- acteur ;
- action ;
- ressource ;
- pays ;
- environnement ;
- criticité ;
- résultat ;
- application ;
- corrélation ;
- adresse IP ;
- ticket ;
- événement ;
- partenaire.

---

# 23. Filtres

Filtres possibles :

- période ;
- catégorie ;
- acteur ;
- rôle ;
- criticité ;
- résultat ;
- ressource ;
- type d’action ;
- pays ;
- environnement ;
- application ;
- statut d’intégrité.

---

# 24. Vue chronologique

Une ressource importante doit disposer d’une chronologie.

Exemples :

- utilisateur ;
- commerce ;
- carte ;
- terminal ;
- paiement ;
- dossier KYC ;
- configuration ;
- partenaire.

La chronologie doit regrouper les événements reliés.

---

# 25. Vue avant/après

Pour une modification, le portail peut afficher :

- ancienne valeur ;
- nouvelle valeur ;
- champs modifiés ;
- auteur ;
- motif ;
- approbation ;
- date d’effet.

Les données sensibles restent masquées.

---

# 26. Alertes

Une alerte peut être déclenchée si :

- un super administrateur modifie une permission ;
- un accès d’urgence est utilisé ;
- un export massif est lancé ;
- un ajustement ledger est demandé ;
- un compte VIP est consulté ;
- plusieurs refus sont détectés ;
- un acteur inconnu exécute une action ;
- une empreinte d’intégrité échoue ;
- une action production est effectuée hors procédure.

---

# 27. Accès au journal

L’accès au journal doit être strictement limité.

Rôles possibles :

- auditeur ;
- conformité ;
- sécurité ;
- responsable d’équipe ;
- super administrateur ;
- autorité habilitée ;
- auditeur partenaire limité.

Un utilisateur ne doit voir que son périmètre.

---

# 28. Permissions

Exemples :

```text
audit.read
audit.read_sensitive
audit.search
audit.export
audit.verify_integrity
audit.view_actor
audit.view_before_after
audit.retention.manage
audit.alert.configure
audit.investigation.create
```

---

# 29. Double validation

Les actions suivantes peuvent exiger une double validation :

- export massif ;
- accès à une période archivée ;
- consultation de données très sensibles ;
- modification de la politique de conservation ;
- désactivation d’une alerte ;
- accès à un journal institutionnel ;
- export pour une autorité externe.

---

# 30. Enquêtes

Le système doit permettre de créer une enquête liée à plusieurs événements.

Une enquête contient :

- identifiant ;
- titre ;
- description ;
- responsable ;
- événements liés ;
- ressources ;
- pièces ;
- statut ;
- priorité ;
- notes ;
- décisions ;
- date d’ouverture ;
- date de clôture.

---

# 31. Chaîne de conservation

Pour les preuves sensibles, conserver :

- origine ;
- collecte ;
- auteur ;
- date ;
- transfert ;
- accès ;
- export ;
- copie ;
- empreinte ;
- stockage ;
- décision finale.

---

# 32. Audit partenaire

Les appels partenaires doivent enregistrer :

- partenaire ;
- endpoint logique ;
- type d’opération ;
- requête masquée ;
- réponse masquée ;
- statut ;
- durée ;
- tentative ;
- identifiant partenaire ;
- corrélation ;
- webhook associé.

Aucun secret ne doit apparaître.

---

# 33. Audit des webhooks

Chaque webhook doit enregistrer :

- source ;
- date de réception ;
- signature vérifiée ou non ;
- type ;
- version ;
- identifiant externe ;
- statut ;
- retry ;
- résultat ;
- corrélation ;
- empreinte du contenu brut.

---

# 34. Audit des configurations

Toute modification de configuration doit conserver :

- clé ;
- ancienne valeur ;
- nouvelle valeur ;
- pays ;
- environnement ;
- version ;
- auteur ;
- approbateur ;
- justification ;
- date d’effet ;
- retour arrière éventuel.

---

# 35. Audit des feature flags

Événements possibles :

- flag créé ;
- flag modifié ;
- flag activé ;
- flag désactivé ;
- audience modifiée ;
- déploiement augmenté ;
- rollback ;
- activation production ;
- expiration.

---

# 36. Audit des rôles et permissions

Doit enregistrer :

- rôle créé ;
- rôle supprimé ;
- permission ajoutée ;
- permission retirée ;
- bénéficiaire ;
- périmètre ;
- durée ;
- motif ;
- approbation ;
- conflit détecté ;
- revue effectuée.

---

# 37. Audit des données personnelles

Doit enregistrer lorsque nécessaire :

- consultation ;
- export ;
- modification ;
- correction ;
- anonymisation ;
- suppression ;
- partage ;
- consentement ;
- retrait ;
- demande de droit.

---

# 38. Portail Admin

Le portail doit permettre :

- consultation ;
- recherche ;
- filtrage ;
- chronologie ;
- comparaison ;
- vérification d’intégrité ;
- création d’enquête ;
- ajout de note ;
- export ;
- génération de rapport ;
- configuration d’alertes ;
- suivi de conservation.

---

# 39. API

Exemples :

```http
GET    /audit-events
GET    /audit-events/{id}
GET    /audit-events/{id}/integrity
GET    /audit-resources/{type}/{id}/timeline

POST   /audit-investigations
GET    /audit-investigations
GET    /audit-investigations/{id}
PATCH  /audit-investigations/{id}

POST   /audit-exports
GET    /audit-exports/{id}
```

Les API d’écriture directe d’événements doivent être internes et fortement contrôlées.

---

# 40. Modèles

- AuditEvent
- AuditActor
- AuditResource
- AuditAction
- AuditResult
- AuditSeverity
- AuditMetadata
- AuditChangeSet
- AuditIntegrityRecord
- AuditRetentionPolicy
- AuditArchive
- AuditExport
- AuditAlert
- AuditInvestigation
- AuditEvidence
- AuditAccessLog
- AuditCorrelation

---

# 41. Règles métier

1. Toute action critique produit un événement.
2. Un événement confirmé est immuable.
3. Toute correction produit un nouvel événement.
4. Les données sensibles sont masquées.
5. L’acteur doit être identifiable.
6. Les refus importants sont audités.
7. Les lectures sensibles peuvent être auditées.
8. Les exports sont tracés.
9. Les actions automatiques sont attribuées à un service.
10. Les actions Jini sont attribuables.
11. Les événements sont horodatés en UTC.
12. L’intégrité doit être vérifiable.
13. Les politiques de conservation sont explicites.
14. Les accès au journal sont eux-mêmes audités.
15. Les actions en masse sont détaillées.
16. Les événements sont corrélables.
17. Les logs techniques ne remplacent pas l’audit.
18. Les modifications de configuration conservent un avant/après.
19. Les événements critiques peuvent déclencher une alerte.
20. Aucun secret ne doit apparaître dans l’audit.
21. Les environnements sont séparés.
22. Les pays sont identifiés.
23. Les erreurs d’intégrité sont critiques.
24. Une enquête conserve les événements liés.
25. Toute exportation doit respecter les permissions.

---

# 42. Analytics

Événements possibles :

```text
audit_event_created
audit_event_integrity_verified
audit_event_integrity_failed
audit_sensitive_read_logged
audit_export_requested
audit_export_completed
audit_investigation_created
audit_investigation_closed
audit_alert_triggered
audit_emergency_access_detected
audit_mass_action_detected
audit_retention_policy_updated
```

---

# 43. Tests

- tests de création ;
- tests d’immutabilité ;
- tests d’intégrité ;
- tests de masquage ;
- tests d’attribution ;
- tests de corrélation ;
- tests de chronologie ;
- tests de recherche ;
- tests d’export ;
- tests de conservation ;
- tests d’archivage ;
- tests de permissions ;
- tests multi-pays ;
- tests multi-environnements ;
- tests de charge ;
- tests d’alerte ;
- tests d’accès au journal ;
- tests de modification impossible ;
- tests de webhook ;
- tests d’actions automatiques ;
- tests Jini.

---

# 44. Critères d’acceptation

Le journal d’audit est validé lorsque :

- toutes les actions critiques sont auditées ;
- les événements sont immuables ;
- les auteurs sont identifiables ;
- les ressources sont corrélables ;
- les modifications conservent un avant/après ;
- les lectures sensibles sont traçables ;
- les exports sont audités ;
- les données sensibles sont masquées ;
- l’intégrité est vérifiable ;
- les environnements sont séparés ;
- les politiques de conservation sont configurables ;
- les actions automatiques sont identifiées ;
- les décisions Jini sont traçables ;
- les enquêtes peuvent être créées ;
- les accès au journal sont contrôlés ;
- les actions critiques déclenchent des alertes ;
- les tests couvrent l’immutabilité et l’intégrité.
