# 16 — Gestion globale des rôles, permissions et contrôle d'accès (RBAC) de Mansa

## 1. Objet du document

Ce document définit le système officiel de gestion des rôles, des permissions et du contrôle d'accès de Mansa.

Il couvre :

- les utilisateurs ;
- les commerçants ;
- les employés ;
- les TPE ;
- les administrateurs ;
- les partenaires ;
- les organismes publics ;
- les API ;
- les services internes ;
- Jini ;
- les permissions granulaires ;
- les rôles ;
- les groupes ;
- les délégations ;
- les accès temporaires ;
- les approbations ;
- les audits ;
- les environnements ;
- les pays.

L'objectif est de garantir que chaque action dans Mansa soit autorisée uniquement aux acteurs disposant des droits appropriés, avec une traçabilité complète.

---

# 2. Principes fondamentaux

## 2.1 Principe du moindre privilège

Chaque utilisateur, employé ou système ne doit disposer que des permissions strictement nécessaires à l'exécution de ses missions.

Aucune permission excessive ne doit être accordée par défaut.

---

## 2.2 Refus par défaut

Toute action non explicitement autorisée doit être refusée.

Le système doit considérer qu'une permission absente équivaut à une interdiction.

---

## 2.3 Vérification côté backend

Les contrôles d'accès doivent toujours être effectués côté backend.

Le masquage d'un bouton dans l'interface ne constitue jamais une protection suffisante.

---

## 2.4 Permissions granulaires

Les permissions doivent être suffisamment fines pour éviter de créer des rôles trop puissants.

Exemple :

```text
payment.read
payment.create
payment.cancel
payment.refund
payment.force_status
```

---

## 2.5 Séparation des responsabilités

Les actions sensibles doivent être réparties entre plusieurs rôles lorsque nécessaire.

Exemples :

- création d'un remboursement ;
- approbation d'un remboursement ;
- validation d'un ajustement ledger ;
- activation d'un partenaire ;
- publication d'une configuration critique.

---

# 3. Types d'acteurs

Le système doit gérer notamment :

- utilisateur particulier ;
- utilisateur professionnel ;
- commerçant ;
- employé de commerce ;
- caissier ;
- responsable magasin ;
- administrateur d'organisation ;
- administrateur Mansa ;
- super administrateur ;
- support ;
- conformité ;
- fraude ;
- finance ;
- partenaire ;
- agent public ;
- service automatisé ;
- webhook ;
- Jini.

---

# 4. Structure d'un rôle

Chaque rôle doit contenir :

- identifiant ;
- nom ;
- description ;
- catégorie ;
- portée ;
- permissions ;
- contraintes ;
- pays ;
- organisation ;
- environnement ;
- statut ;
- version ;
- historique ;
- auteur ;
- approbateur.

---

# 5. Types de rôles

Exemples :

- Client ;
- Merchant Owner ;
- Merchant Manager ;
- Cashier ;
- Inventory Manager ;
- Support Agent ;
- Compliance Officer ;
- Fraud Analyst ;
- Finance Manager ;
- Super Admin ;
- Public Agent ;
- Partner Admin.

---

# 6. Permissions

Les permissions suivent une convention stable.

Exemple :

```text
wallet.read
wallet.transfer
wallet.close

card.create
card.freeze
card.unfreeze

merchant.employee.create
merchant.employee.delete

ledger.adjustment.approve
```

Les permissions doivent être documentées et versionnées.

---

# 7. Portées

Une permission peut être limitée à :

- soi-même ;
- son organisation ;
- un établissement ;
- un pays ;
- une région ;
- un partenaire ;
- un environnement ;
- une ressource spécifique.

---

# 8. Héritage des rôles

Un rôle peut hériter d'un autre.

Exemple :

```text
Merchant Manager
    ↓
Cashier
```

L'héritage ne doit jamais créer de boucle.

---

# 9. Permissions temporaires

Le système doit permettre des accès limités dans le temps.

Exemples :

- accès support ;
- accès d'urgence ;
- intervention technique ;
- audit externe.

Chaque accès temporaire doit avoir :

- une durée ;
- un motif ;
- un approbateur ;
- une expiration automatique.

---

# 10. Double validation

Certaines actions exigent deux validations.

Exemples :

- remboursement important ;
- ajustement ledger ;
- suppression d'un administrateur ;
- modification des permissions ;
- activation d'un partenaire ;
- changement des frais.

---

# 11. Délégation

Un utilisateur peut déléguer certaines responsabilités à un autre utilisateur.

La délégation doit préciser :

- périmètre ;
- durée ;
- permissions déléguées ;
- révocation.

---

# 12. Permissions API

Les API internes et externes doivent utiliser des permissions dédiées.

Exemples :

```text
api.payment.create
api.payment.read
api.partner.webhook.receive
api.admin.configuration.update
```

---

# 13. Sessions

Les sessions doivent conserver :

- utilisateur ;
- rôle ;
- permissions calculées ;
- environnement ;
- pays ;
- appareil ;
- heure de création ;
- expiration.

---

# 14. Accès d'urgence

Le système doit prévoir un mécanisme d'accès d'urgence ("break glass").

Chaque utilisation doit être :

- exceptionnelle ;
- justifiée ;
- approuvée ;
- auditée ;
- notifiée.

---

# 15. Audit

Toute modification de rôle ou de permission doit être enregistrée.

Le journal doit inclure :

- auteur ;
- ancienne valeur ;
- nouvelle valeur ;
- justification ;
- approbation ;
- date.

---

# 16. Administration

Le portail Admin doit permettre :

- créer un rôle ;
- modifier un rôle ;
- archiver un rôle ;
- attribuer un rôle ;
- retirer un rôle ;
- rechercher une permission ;
- comparer deux rôles ;
- simuler les permissions ;
- exporter les rôles ;
- consulter l'historique.

---

# 17. Simulation

Avant de publier un changement, l'administration doit pouvoir vérifier :

- les permissions effectives ;
- les conflits ;
- les permissions redondantes ;
- les accès implicites ;
- les impacts.

---

# 18. Permissions critiques

Exemples :

- ledger.adjustment.approve
- configuration.production.publish
- partner.activate
- payment.force_status
- audit.export
- feature_flag.kill_switch.use
- fraud.case.close

Ces permissions nécessitent des protections renforcées.

---

# 19. Contraintes

Les permissions peuvent être conditionnées par :

- le pays ;
- le niveau KYC ;
- le montant ;
- l'environnement ;
- le rôle ;
- l'heure ;
- le partenaire ;
- le type d'organisation.

---

# 20. API

Exemples :

```http
GET    /roles
GET    /roles/{id}
POST   /roles
PATCH  /roles/{id}

GET    /permissions
POST   /roles/{id}/assign
POST   /roles/{id}/revoke

POST   /access/simulate
POST   /access/delegate
POST   /access/emergency
```

---

# 21. Modèles

- Role
- Permission
- RoleAssignment
- PermissionAssignment
- AccessPolicy
- AccessConstraint
- Delegation
- TemporaryAccess
- EmergencyAccess
- RoleVersion
- PermissionGroup
- AccessAudit

---

# 22. Règles métier

1. Toute action nécessite une permission.
2. Les permissions sont vérifiées côté backend.
3. Les rôles sont versionnés.
4. Les permissions critiques sont protégées.
5. Les délégations expirent automatiquement.
6. Les accès d'urgence sont audités.
7. Les rôles peuvent être simulés avant publication.
8. Les permissions sont granulaires.
9. Les conflits sont détectés.
10. Les héritages sont validés.
11. Les boucles d'héritage sont interdites.
12. Les environnements sont séparés.
13. Les pays sont pris en compte.
14. Les permissions API sont distinctes.
15. Les modifications sont historisées.
16. Les rôles archivés ne sont plus attribuables.
17. Les permissions temporaires expirent.
18. Les doubles validations sont respectées.
19. Les exports sont protégés.
20. Toute modification est auditée.

---

# 23. Analytics

Événements possibles :

```text
role_created
role_updated
role_archived
permission_assigned
permission_revoked
temporary_access_granted
temporary_access_expired
emergency_access_used
role_simulation_executed
permission_denied
```

---

# 24. Tests

- tests RBAC ;
- tests de portée ;
- tests d'héritage ;
- tests de délégation ;
- tests d'expiration ;
- tests de simulation ;
- tests API ;
- tests d'audit ;
- tests multi-pays ;
- tests multi-environnements ;
- tests de permissions critiques ;
- tests de montée en charge.

---

# 25. Critères d'acceptation

Le système RBAC est validé lorsque :

- toutes les actions sont protégées ;
- les permissions sont granulaires ;
- les rôles sont versionnés ;
- les simulations fonctionnent ;
- les accès temporaires expirent ;
- les accès d'urgence sont tracés ;
- les permissions API sont séparées ;
- les modifications sont auditées ;
- les contraintes sont appliquées ;
- les tests couvrent les scénarios critiques.
