# 07 — Gestion des rôles et permissions de Mansa

## 1. Objet du document

Ce document définit le système officiel de rôles, permissions et périmètres d’accès de Mansa.

Il s’applique à :

- Mansa Client ;
- Mansa Commerce ;
- Mansa TPE ;
- Mansa Admin Lite ;
- Mansa Annuaire / Hub ;
- le site public ;
- le site Professionnels ;
- le portail Admin Web ;
- les API ;
- les services backend ;
- les partenaires ;
- les agents publics ;
- les équipes internes.

L’objectif est de garantir que chaque personne puisse uniquement :

- voir les données nécessaires ;
- effectuer les actions autorisées ;
- agir dans son périmètre ;
- respecter les limites définies ;
- laisser une trace auditable.

---

# 2. Principes fondamentaux

## 2.1 Refus par défaut

Toute action est interdite tant qu’elle n’est pas explicitement autorisée.

L’absence de règle ne doit jamais être interprétée comme une autorisation.

## 2.2 Moindre privilège

Chaque utilisateur reçoit uniquement les droits nécessaires à son activité.

Les droits inutilisés, temporaires ou obsolètes doivent être retirés.

## 2.3 Contrôle côté backend

Masquer un bouton dans l’interface ne constitue pas une protection.

Chaque action doit être contrôlée côté backend selon :

- l’identité ;
- le rôle ;
- la permission ;
- le périmètre ;
- le pays ;
- l’environnement ;
- le montant ;
- le statut ;
- le niveau de risque ;
- les règles métier.

## 2.4 Séparation des responsabilités

Une même personne ne doit pas pouvoir initier, approuver et clôturer seule une opération critique lorsque le risque l’exige.

Exemples :

- remboursement important ;
- modification de commission ;
- activation d’un partenaire ;
- déblocage d’un compte sensible ;
- modification d’un plafond global ;
- suppression d’un administrateur ;
- mise en production d’une configuration critique.

## 2.5 Traçabilité

Toute attribution, modification ou suppression d’un rôle doit enregistrer :

- auteur ;
- bénéficiaire ;
- ancienne valeur ;
- nouvelle valeur ;
- date ;
- heure ;
- motif ;
- périmètre ;
- durée ;
- approbateur éventuel.

---

# 3. Modèle d’autorisation

Mansa combine plusieurs mécanismes.

## 3.1 RBAC

Le RBAC attribue des permissions à des rôles.

Exemple :

```text
Rôle : Agent support
Permissions :
- support.ticket.read
- support.ticket.reply
- user.profile.read_limited
- transaction.read_limited
```

## 3.2 ABAC

L’ABAC ajoute des conditions basées sur des attributs.

Exemples :

- pays de l’utilisateur ;
- niveau KYC ;
- montant ;
- établissement ;
- niveau de risque ;
- heure ;
- appareil ;
- relation avec la ressource ;
- environnement ;
- statut de l’opération.

## 3.3 Permissions par ressource et action

Format recommandé :

```text
resource.action
```

Exemples :

```text
user.read
user.suspend
payment.create
payment.refund
card.freeze
merchant.employee.invite
admin.role.assign
public_service.fine.create
```

## 3.4 Périmètre

Une permission peut être limitée à :

- soi-même ;
- un compte ;
- un wallet ;
- une conversation ;
- un commerce ;
- un établissement ;
- une entreprise ;
- un pays ;
- une région ;
- une administration ;
- un partenaire ;
- un environnement ;
- une équipe ;
- une liste explicite de ressources.

---

# 4. Niveaux de rôles

## 4.1 Utilisateurs particuliers

Rôles possibles :

- invité ;
- utilisateur non vérifié ;
- utilisateur vérifié ;
- utilisateur premium ;
- parent ou responsable familial ;
- bénéficiaire enfant ;
- représentant légal.

## 4.2 Commerce

Rôles possibles :

- propriétaire ;
- administrateur commerce ;
- manager ;
- caissier ;
- vendeur ;
- comptable ;
- gestionnaire stock ;
- responsable marketing ;
- support interne ;
- auditeur lecture seule.

## 4.3 TPE

Rôles possibles :

- propriétaire terminal ;
- administrateur terminal ;
- manager caisse ;
- caissier ;
- agent remboursement ;
- technicien ;
- auditeur.

## 4.4 Administration Mansa

Rôles possibles :

- support niveau 1 ;
- support niveau 2 ;
- support senior ;
- analyste fraude ;
- analyste conformité ;
- agent KYC ;
- agent KYB ;
- responsable cartes ;
- responsable paiements ;
- responsable TPE ;
- responsable partenaires ;
- responsable services publics ;
- responsable investissements ;
- administrateur produit ;
- administrateur technique ;
- auditeur ;
- super administrateur.

## 4.5 Administration publique

Rôles possibles :

- agent terrain ;
- superviseur ;
- agent de validation ;
- comptable public ;
- responsable organisme ;
- auditeur public ;
- administrateur institutionnel.

## 4.6 Partenaires

Rôles possibles :

- opérateur partenaire ;
- responsable partenaire ;
- auditeur partenaire ;
- support partenaire ;
- administrateur d’intégration.

---

# 5. Rôles de l’application Client

## 5.1 Invité

Peut :

- consulter certaines pages publiques ;
- voir des informations générales ;
- commencer l’inscription.

Ne peut pas :

- effectuer une opération financière ;
- consulter un compte ;
- accéder à une carte ;
- utiliser Mansa Connect comme utilisateur authentifié.

## 5.2 Utilisateur inscrit non vérifié

Peut :

- compléter son profil ;
- commencer le KYC ;
- consulter les fonctions autorisées ;
- recevoir certaines notifications.

Les opérations financières peuvent être bloquées ou limitées.

## 5.3 Utilisateur vérifié

Peut selon son pays et son niveau :

- gérer ses comptes ;
- envoyer et recevoir de l’argent ;
- gérer ses cartes ;
- utiliser QR et NFC ;
- utiliser Mansa Connect ;
- créer des budgets et coffres ;
- consulter ses documents ;
- accéder aux services activés.

## 5.4 Responsable familial

Peut selon les autorisations :

- créer un profil enfant ;
- définir des limites ;
- consulter certaines opérations ;
- suspendre une carte enfant ;
- autoriser certaines dépenses.

Il ne doit pas automatiquement accéder à toutes les communications privées du bénéficiaire.

---

# 6. Rôles de Mansa Commerce

## 6.1 Propriétaire

Peut :

- gérer l’entreprise ;
- gérer les établissements ;
- gérer les abonnements ;
- gérer les administrateurs ;
- consulter les rapports globaux ;
- gérer les comptes de règlement ;
- demander des TPE ;
- configurer les permissions internes.

## 6.2 Administrateur commerce

Peut gérer l’organisation selon le périmètre accordé.

Les actions critiques peuvent rester réservées au propriétaire.

## 6.3 Manager

Peut :

- gérer une équipe ;
- consulter les ventes ;
- gérer la caisse ;
- approuver certaines opérations ;
- gérer catalogue et stock selon droits.

## 6.4 Caissier

Peut :

- encaisser ;
- consulter ses ventes ;
- imprimer un reçu ;
- effectuer une annulation immédiate si autorisée.

Ne peut pas automatiquement :

- modifier les commissions ;
- gérer les comptes de règlement ;
- consulter toutes les données de l’entreprise ;
- effectuer un remboursement important.

## 6.5 Comptable

Peut :

- consulter les rapports ;
- exporter les données ;
- consulter factures et règlements ;
- rapprocher certaines opérations.

## 6.6 Gestionnaire de stock

Peut :

- créer et modifier des produits ;
- ajuster les stocks ;
- effectuer des inventaires ;
- gérer les fournisseurs.

---

# 7. Rôles du TPE

## 7.1 Activation

Seuls les rôles autorisés peuvent :

- activer un terminal ;
- changer son commerce associé ;
- changer l’environnement ;
- révoquer un terminal ;
- installer une configuration sensible.

## 7.2 Encaissement

Un caissier peut :

- ouvrir une session ;
- créer un panier ;
- accepter un paiement ;
- imprimer un reçu ;
- consulter son activité.

## 7.3 Remboursement

Une permission spécifique doit contrôler :

```text
terminal.refund.create
```

Elle peut inclure :

- plafond unitaire ;
- plafond journalier ;
- ancienneté maximale de la transaction ;
- approbation requise ;
- motif obligatoire ;
- authentification renforcée.

## 7.4 Annulation

L’annulation peut être limitée :

- à la session ;
- à l’employé ayant créé l’opération ;
- à une période courte ;
- à un montant maximal ;
- à un statut précis.

---

# 8. Rôles du portail Admin

## 8.1 Support

Accès limité aux informations nécessaires au traitement d’un dossier.

Les données sensibles doivent être masquées.

## 8.2 KYC et KYB

Peut :

- consulter un dossier ;
- demander un complément ;
- valider ;
- refuser ;
- escalader ;
- laisser un commentaire interne.

Ne doit pas pouvoir modifier directement un solde.

## 8.3 Fraude

Peut :

- consulter les alertes ;
- analyser les transactions ;
- appliquer certaines restrictions ;
- demander une réauthentification ;
- escalader ;
- proposer un blocage.

## 8.4 Finance

Peut :

- consulter les règlements ;
- contrôler les rapprochements ;
- gérer certaines corrections ;
- exporter les rapports ;
- valider certaines opérations.

## 8.5 Administrateur produit

Peut :

- gérer les fonctionnalités ;
- configurer les limites ;
- gérer les contenus ;
- activer des feature flags autorisés ;
- configurer certaines offres.

## 8.6 Administrateur technique

Peut gérer :

- intégrations ;
- webhooks ;
- certificats ;
- configuration technique ;
- monitoring ;
- accès techniques.

## 8.7 Super administrateur

Le rôle doit être exceptionnel.

Exigences :

- nombre limité ;
- 2FA obligatoire ;
- appareil approuvé ;
- journalisation renforcée ;
- réauthentification ;
- alertes ;
- revue régulière ;
- aucune utilisation quotidienne sans nécessité.

---

# 9. Permissions critiques

Permissions nécessitant une protection renforcée :

```text
user.close
user.suspend
user.unlock
wallet.adjust
ledger.post
payment.override
payment.refund.large
card.issue
card.replace
card.unblock
merchant.activate
merchant.suspend
terminal.activate
terminal.reassign
role.assign
role.delete
permission.override
configuration.update_critical
feature_flag.enable_production
partner.activate
public_service.rule.update
audit.export
secret.rotate
```

---

# 10. Double validation

La double validation peut être exigée pour :

- remboursement supérieur à un seuil ;
- ajustement financier ;
- changement de commission ;
- activation d’un partenaire ;
- modification des règles de fraude ;
- modification d’un plafond national ;
- suppression d’un rôle sensible ;
- export massif de données ;
- activation en production ;
- modification d’une intégration institutionnelle.

Le second approbateur doit être différent de l’auteur.

---

# 11. Permissions temporaires

Une permission temporaire doit contenir :

- bénéficiaire ;
- permission ;
- périmètre ;
- début ;
- expiration ;
- motif ;
- auteur ;
- approbateur ;
- ticket ou incident lié.

À expiration, elle est automatiquement retirée.

---

# 12. Délégation

Un responsable peut déléguer certaines permissions.

La délégation doit préciser :

- ce qui est délégué ;
- à qui ;
- pour combien de temps ;
- dans quel périmètre ;
- avec quelles limites ;
- si une sous-délégation est autorisée.

---

# 13. Rôles personnalisés

Les organisations peuvent créer des rôles personnalisés à partir de permissions autorisées.

Exigences :

- nom unique ;
- description ;
- périmètre ;
- permissions ;
- restrictions ;
- version ;
- historique ;
- validation ;
- liste des membres.

Certaines permissions critiques ne doivent pas être attribuables librement.

---

# 14. Héritage des rôles

Un rôle peut hériter d’un rôle inférieur.

Exemple :

```text
Propriétaire
  └── Administrateur
       └── Manager
            └── Caissier
```

L’héritage doit rester explicite et éviter les cycles.

---

# 15. Conflits de rôles

Le système doit détecter les combinaisons incompatibles.

Exemples :

- initiateur + approbateur ;
- agent KYC + auditeur du même dossier ;
- caissier + contrôleur de caisse ;
- développeur production + auditeur sécurité ;
- agent de saisie d’amende + agent d’annulation sans supervision.

---

# 16. Permissions sur les données

Les permissions doivent distinguer :

- voir ;
- voir partiellement ;
- créer ;
- modifier ;
- supprimer ;
- approuver ;
- exporter ;
- partager ;
- suspendre ;
- restaurer.

Exemple :

```text
user.read_basic
user.read_sensitive
user.export
```

---

# 17. Masquage des données

Selon le rôle, afficher uniquement :

- derniers chiffres d’une carte ;
- téléphone partiellement masqué ;
- e-mail partiellement masqué ;
- identité réduite ;
- montant agrégé ;
- document sans données sensibles ;
- adresse partielle.

---

# 18. Accès par environnement

Les permissions doivent être séparées entre :

- Démo ;
- Recette ;
- Préproduction ;
- Production.

Une personne autorisée en recette ne doit pas automatiquement avoir accès à la production.

---

# 19. Accès par pays

Un rôle peut être limité à :

- un pays ;
- plusieurs pays ;
- une région ;
- une organisation nationale ;
- une entité partenaire.

---

# 20. Accès d’urgence

Un mécanisme d’accès d’urgence peut être prévu.

Exigences :

- motif obligatoire ;
- durée très courte ;
- approbation ;
- notification immédiate ;
- journalisation renforcée ;
- revue après usage ;
- révocation automatique.

---

# 21. API de permissions

Exemples :

```http
GET    /roles
POST   /roles
GET    /roles/{id}
PATCH  /roles/{id}
DELETE /roles/{id}

GET    /permissions
POST   /role-assignments
DELETE /role-assignments/{id}

POST   /permission-grants
POST   /permission-grants/{id}/revoke
POST   /permission-grants/{id}/approve

GET    /access/check
GET    /access/audit
```

---

# 22. Modèles

- Role
- Permission
- RolePermission
- RoleAssignment
- PermissionGrant
- AccessScope
- AccessCondition
- ApprovalPolicy
- Delegation
- TemporaryAccess
- AccessReview
- AccessAudit
- SegregationRule

---

# 23. Règles métier

1. Toute permission est refusée par défaut.
2. Toute autorisation sensible est contrôlée côté backend.
3. Une permission expirée est immédiatement invalide.
4. Un utilisateur suspendu perd les accès concernés.
5. Un rôle supprimé ne doit pas laisser de permissions orphelines.
6. Les conflits de rôles doivent être détectés.
7. Les actions critiques peuvent exiger une seconde approbation.
8. Les accès production sont séparés des autres environnements.
9. Les permissions personnalisées restent limitées à une liste autorisée.
10. Toute modification de rôle est auditée.
11. Le masquage des données dépend du rôle.
12. Une action refusée ne doit pas être contournable depuis une autre application.
13. Une délégation ne peut pas dépasser les droits du délégant.
14. Les permissions temporaires expirent automatiquement.
15. Les super administrateurs doivent faire l’objet de revues régulières.

---

# 24. Analytics

Événements possibles :

```text
role_created
role_updated
role_deleted
role_assigned
role_revoked
permission_granted
permission_revoked
temporary_access_created
temporary_access_expired
access_denied
critical_permission_used
approval_requested
approval_completed
conflict_detected
```

---

# 25. Administration

Le portail Admin doit permettre :

- créer des rôles ;
- dupliquer un rôle ;
- attribuer des permissions ;
- définir des périmètres ;
- définir des limites ;
- définir des conditions ;
- consulter les membres ;
- détecter les conflits ;
- programmer une expiration ;
- demander une approbation ;
- révoquer immédiatement ;
- exporter un rapport ;
- lancer une revue d’accès.

---

# 26. Revue périodique

Les accès sensibles doivent être revus régulièrement.

La revue vérifie :

- utilisateurs inactifs ;
- rôles inutilisés ;
- permissions excessives ;
- comptes de départ ;
- délégations actives ;
- accès temporaires ;
- super administrateurs ;
- accès production ;
- conflits.

---

# 27. Tests

- tests unitaires des politiques ;
- tests RBAC ;
- tests ABAC ;
- tests de périmètre ;
- tests de conflits ;
- tests d’expiration ;
- tests de délégation ;
- tests de double validation ;
- tests d’accès horizontal ;
- tests d’élévation verticale ;
- tests multi-pays ;
- tests multi-environnements ;
- tests d’audit.

---

# 28. Critères d’acceptation

Le système de rôles et permissions est validé lorsque :

- toutes les actions sont refusées par défaut ;
- les permissions sont contrôlées côté backend ;
- les rôles principaux sont définis ;
- les périmètres sont appliqués ;
- les données sensibles sont masquées ;
- les accès temporaires expirent ;
- les délégations sont limitées ;
- les conflits sont détectés ;
- les actions critiques peuvent exiger une double validation ;
- les accès production sont séparés ;
- toutes les modifications sont auditées ;
- les administrateurs peuvent revoir et révoquer les accès ;
- les tests couvrent les contournements possibles.
