# 53 — Portail Entreprises et Employeurs Mansa : gestion RH, paie, dépenses, cartes professionnelles, budgets, avantages et administration complète

## 1. Objet du document

Ce document définit l'architecture officielle du **Portail Entreprises et Employeurs Mansa**.

Ce portail est destiné aux entreprises publiques et privées souhaitant gérer leurs collaborateurs, leurs flux financiers et leurs dépenses professionnelles directement depuis l'écosystème Mansa.

Le portail est compatible avec :

- PME ;
- grandes entreprises ;
- multinationales ;
- administrations ;
- ministères ;
- collectivités ;
- ONG ;
- associations ;
- banques ;
- assurances ;
- hôpitaux ;
- écoles ;
- universités ;
- sociétés industrielles ;
- sociétés de transport ;
- sociétés de télécommunications ;
- sociétés minières ;
- entreprises de BTP ;
- commerces ;
- franchises.

Le portail permet de gérer :

- les entreprises ;
- les filiales ;
- les établissements ;
- les départements ;
- les employés ;
- les managers ;
- les salaires ;
- les avances ;
- les acomptes ;
- les primes ;
- les indemnités ;
- les avantages ;
- les cartes professionnelles ;
- les dépenses professionnelles ;
- les notes de frais ;
- les fournisseurs ;
- les paiements fournisseurs ;
- les budgets ;
- les centres de coûts ;
- les projets ;
- les missions ;
- les validations ;
- les remboursements ;
- les rapports ;
- les exports ;
- les audits ;
- les rôles ;
- les permissions ;
- les API ;
- les webhooks ;
- les intégrations RH ;
- les intégrations comptables.

L'objectif est de fournir aux entreprises une plateforme complète de gestion financière, tout en gardant une séparation stricte entre les données de chaque organisation.

---

# 2. Principes fondamentaux

## 2.1 Isolation des entreprises

Chaque entreprise possède un environnement totalement isolé.

Elle ne peut accéder qu'à :

- ses employés ;
- ses administrateurs ;
- ses cartes ;
- ses comptes ;
- ses dépenses ;
- ses paiements ;
- ses rapports ;
- ses documents ;
- ses budgets ;
- ses fournisseurs ;
- ses API.

Aucune donnée d'une autre entreprise ne doit être visible.

---

## 2.2 Le Ledger Mansa reste la référence

Les écritures financières restent enregistrées dans le Ledger Mansa.

Le portail ne peut jamais modifier directement :

- un solde ;
- une écriture comptable ;
- une transaction validée ;
- un règlement.

Toute correction passe par un workflow officiel.

---

## 2.3 Paramètres entièrement administrables

Aucun élément financier ne doit être codé en dur.

Doivent être configurables :

- budgets ;
- plafonds ;
- politiques de dépenses ;
- validations ;
- commissions ;
- avances ;
- acomptes ;
- remboursements ;
- cartes ;
- devises ;
- catégories ;
- centres de coûts.

---

## 2.4 Audit complet

Chaque action doit enregistrer :

- utilisateur ;
- entreprise ;
- rôle ;
- appareil ;
- IP ;
- date ;
- heure ;
- ancienne valeur ;
- nouvelle valeur ;
- motif ;
- résultat ;
- approbateur.

---

# 3. Types d'organisations

Le portail prend en charge :

- entreprise privée ;
- entreprise publique ;
- administration ;
- ministère ;
- mairie ;
- région ;
- ONG ;
- association ;
- école ;
- université ;
- hôpital ;
- banque ;
- compagnie d'assurance ;
- société industrielle ;
- société minière ;
- entreprise BTP ;
- société de transport ;
- groupe international.

---

# 4. Tableau de bord

Le tableau de bord affiche en temps réel :

- nombre d'employés ;
- masse salariale ;
- salaires en attente ;
- paiements réalisés ;
- avances accordées ;
- dépenses du jour ;
- dépenses du mois ;
- budgets consommés ;
- budgets restants ;
- cartes actives ;
- cartes bloquées ;
- remboursements ;
- notes de frais ;
- fournisseurs ;
- incidents ;
- alertes.

---

# 5. Structure organisationnelle

Le portail permet de créer :

- entreprise ;
- filiale ;
- établissement ;
- agence ;
- direction ;
- département ;
- équipe ;
- centre de coûts ;
- projet.

---

# 6. Gestion des employés

Chaque employé possède :

- identité ;
- matricule ;
- poste ;
- département ;
- manager ;
- coordonnées ;
- date d'embauche ;
- contrat ;
- statut ;
- compte Mansa ;
- cartes attribuées ;
- historique.

---

# 7. Cycle de vie d'un employé

Statuts possibles :

- INVITED ;
- ACTIVE ;
- PROBATION ;
- ON_LEAVE ;
- SUSPENDED ;
- TERMINATED ;
- ARCHIVED.

---

# 8. Rôles

Exemples :

```text
COMPANY_OWNER
COMPANY_ADMIN
HR_MANAGER
PAYROLL_MANAGER
FINANCE_MANAGER
ACCOUNTANT
TEAM_MANAGER
PROJECT_MANAGER
EMPLOYEE
AUDITOR
VIEWER
```

---

# 9. Permissions

Exemples :

```text
company.dashboard.read
company.employee.read
company.employee.manage
company.payroll.manage
company.expense.manage
company.card.manage
company.budget.manage
company.report.read
company.audit.read
company.settings.manage
```

---

# 10. Gestion de la paie

Le système doit permettre :

- import des salaires ;
- simulation ;
- validation ;
- paiement de masse ;
- génération des bulletins ;
- génération des reçus ;
- suivi des paiements ;
- export comptable.

---

# 11. Workflow de paie

Le workflow comprend :

1. import ;
2. contrôle ;
3. validation RH ;
4. validation Finance ;
5. validation Direction (si nécessaire) ;
6. exécution ;
7. crédit des comptes ;
8. notifications ;
9. audit.

---

# 12. Avances sur salaire

Fonctionnalités :

- demande ;
- plafond configurable ;
- validation ;
- remboursement automatique ;
- échéancier ;
- retenues ;
- historique.

---

# 13. Acomptes

Le portail peut gérer :

- demandes ;
- validations ;
- paiements ;
- retenues sur salaire ;
- historique.

---

# 14. Primes et indemnités

Exemples :

- prime annuelle ;
- prime exceptionnelle ;
- prime de performance ;
- indemnité de déplacement ;
- indemnité logement ;
- indemnité repas ;
- indemnité transport.

Toutes les règles sont administrables.

---

# 15. Notes de frais

Catégories possibles :

- carburant ;
- transport ;
- avion ;
- train ;
- hôtel ;
- restauration ;
- fournitures ;
- matériel ;
- télécommunications ;
- mission ;
- représentation ;
- autres.

Chaque note peut contenir :

- justificatifs ;
- photos ;
- facture ;
- TVA ;
- devise ;
- catégorie ;
- montant ;
- statut.

---

# 16. Workflow des notes de frais

1. création ;
2. dépôt des justificatifs ;
3. contrôle ;
4. validation manager ;
5. validation Finance ;
6. remboursement ;
7. clôture.

---

# 17. Cartes professionnelles

Le portail permet :

- émission ;
- remplacement ;
- blocage ;
- déblocage ;
- renouvellement ;
- plafonds ;
- catégories autorisées ;
- pays autorisés ;
- devises ;
- dépenses en temps réel.

---

# 18. Paramètres des cartes

Restrictions possibles :

- type de commerçant ;
- MCC ;
- montant maximum ;
- retrait autorisé ;
- paiement en ligne ;
- paiement international ;
- sans contact ;
- jours autorisés ;
- horaires.

---

# 19. Budgets

Budgets possibles :

- entreprise ;
- département ;
- équipe ;
- projet ;
- collaborateur ;
- mission ;
- événement.

---

# 20. Centres de coûts

Chaque dépense peut être associée à :

- département ;
- agence ;
- projet ;
- chantier ;
- événement ;
- filiale ;
- centre analytique.

---

# 21. Dépenses

Chaque dépense contient :

- employé ;
- commerçant ;
- catégorie ;
- carte ;
- justificatif ;
- montant ;
- devise ;
- TVA ;
- approbateur ;
- statut.

---

# 22. Fournisseurs

Le portail gère :

- fournisseurs ;
- contrats ;
- comptes bancaires ;
- IBAN/RIB ;
- devises ;
- échéances ;
- paiements ;
- historique.

---

# 23. Paiements fournisseurs

Workflow :

1. création ;
2. validation ;
3. exécution ;
4. confirmation ;
5. rapprochement ;
6. audit.

---

# 24. Validation hiérarchique

Le système peut utiliser :

- manager ;
- directeur ;
- RH ;
- finance ;
- DG ;
- workflow personnalisé.

---

# 25. Budgets dynamiques

Le portail doit permettre :

- augmentation ;
- réduction ;
- gel ;
- réouverture ;
- transfert entre budgets ;
- alertes de dépassement.

---

# 26. Rapports

Rapports disponibles :

- masse salariale ;
- dépenses ;
- budgets ;
- centres de coûts ;
- cartes ;
- fournisseurs ;
- avances ;
- acomptes ;
- TVA ;
- remboursements ;
- exports comptables.

---

# 27. Exports

Formats :

- PDF ;
- CSV ;
- XLSX ;
- JSON.

---

# 28. Notifications

Exemples :

- salaire versé ;
- demande approuvée ;
- demande refusée ;
- budget dépassé ;
- carte bloquée ;
- carte expirant bientôt ;
- remboursement effectué ;
- incident.

---

# 29. API

Exemples :

```http
GET    /company/dashboard
GET    /company/employees
GET    /company/payroll
GET    /company/cards
GET    /company/budgets

POST   /company/payroll/run
POST   /company/expense-reports
POST   /company/cards
POST   /company/suppliers

GET    /company/reports
GET    /company/audit
```

---

# 30. Sécurité

Le portail applique :

- MFA ;
- RBAC ;
- chiffrement ;
- journal d'audit ;
- appareils approuvés ;
- IP autorisées ;
- signatures numériques ;
- séparation des rôles.

---

# 31. Audit

Chaque action conserve :

- utilisateur ;
- entreprise ;
- rôle ;
- action ;
- ancienne valeur ;
- nouvelle valeur ;
- appareil ;
- IP ;
- date ;
- heure ;
- motif.

Les journaux sont immuables.

---

# 32. Modèles principaux

- Company
- CompanyUser
- Employee
- Department
- CostCenter
- PayrollRun
- PayrollEntry
- SalaryAdvance
- SalaryInstallment
- ExpenseReport
- ExpenseItem
- CorporateCard
- Budget
- Supplier
- SupplierPayment
- CompanyApproval
- CompanyAudit

---

# 33. Règles métier

1. Chaque entreprise est totalement isolée.
2. Les rôles limitent les accès.
3. Les validations sont configurables.
4. Les budgets sont administrables.
5. Les cartes peuvent être restreintes.
6. Les dépenses nécessitent des justificatifs selon les règles définies.
7. Les paiements sont audités.
8. Les rapports sont exportables.
9. Les actions sensibles exigent une validation.
10. Les audits sont immuables.

---

# 34. Critères d'acceptation

Le Portail Entreprises et Employeurs est validé lorsque :

- les entreprises peuvent être créées ;
- les employés sont administrables ;
- les rôles et permissions fonctionnent ;
- la paie de masse est opérationnelle ;
- les avances et acomptes sont gérés ;
- les notes de frais fonctionnent ;
- les cartes professionnelles sont administrables ;
- les budgets sont dynamiques ;
- les fournisseurs sont gérés ;
- les paiements fournisseurs sont sécurisés ;
- les rapports sont exportables ;
- les API sont disponibles ;
- les audits sont complets ;
- toutes les actions sensibles sont traçables.
