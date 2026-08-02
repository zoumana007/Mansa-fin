# 54 — Portail Écoles et Universités Mansa : inscriptions, scolarité, paiements, cartes étudiantes, bourses, services campus et administration académique

## 1. Objet du document

Ce document définit l’architecture officielle du **Portail Écoles et Universités Mansa**.

Ce portail est destiné aux établissements d’enseignement souhaitant gérer leurs étudiants, leurs paiements, leurs cartes, leurs services et leurs flux administratifs depuis l’écosystème Mansa.

Le portail peut être utilisé par :

- écoles primaires ;
- collèges ;
- lycées ;
- centres de formation ;
- universités ;
- instituts ;
- grandes écoles ;
- écoles privées ;
- établissements publics ;
- centres d’apprentissage ;
- résidences universitaires ;
- restaurants universitaires ;
- bibliothèques ;
- services de transport scolaire ;
- organismes de bourses.

Le portail permet de gérer :

- les établissements ;
- les campus ;
- les étudiants ;
- les parents ou responsables ;
- les inscriptions ;
- les réinscriptions ;
- les frais scolaires ;
- les frais universitaires ;
- les échéanciers ;
- les paiements ;
- les bourses ;
- les exonérations ;
- les remises ;
- les cartes étudiantes ;
- les cartes du personnel ;
- les accès aux bâtiments ;
- les bibliothèques ;
- les restaurants ;
- les résidences ;
- les transports ;
- les examens ;
- les activités ;
- les documents ;
- les remboursements ;
- les reçus ;
- les rapports ;
- les rôles ;
- les permissions ;
- les audits ;
- les intégrations ;
- les API ;
- les webhooks ;
- la sécurité ;
- le multi-campus ;
- le multi-pays.

L’objectif est de fournir aux établissements une plateforme complète permettant de centraliser les opérations financières et administratives liées à la vie scolaire et universitaire.

---

# 2. Principes fondamentaux

## 2.1 Chaque établissement possède un espace isolé

Un établissement ne doit voir que :

- ses étudiants ;
- ses employés ;
- ses campus ;
- ses paiements ;
- ses cartes ;
- ses rapports ;
- ses documents ;
- ses services ;
- ses paramètres.

Aucune donnée d’un autre établissement ne doit être visible sans autorisation explicite.

---

## 2.2 Les paiements restent séparés des décisions académiques

Mansa peut gérer :

- l’encaissement ;
- le suivi ;
- le reçu ;
- le remboursement ;
- le rapprochement ;
- le versement d’une bourse.

L’établissement reste responsable de :

- l’admission ;
- l’inscription ;
- la validation pédagogique ;
- les notes ;
- les sanctions ;
- l’éligibilité ;
- les décisions académiques ;
- l’attribution des logements ;
- l’attribution des bourses.

---

## 2.3 Aucun tarif ne doit être codé en dur

Les montants doivent être administrables selon :

- établissement ;
- campus ;
- niveau ;
- filière ;
- année ;
- programme ;
- nationalité ;
- statut ;
- bourse ;
- exonération ;
- période ;
- échéancier ;
- service.

---

## 2.4 Toute opération doit être traçable

Chaque action sensible doit enregistrer :

- utilisateur ;
- rôle ;
- établissement ;
- campus ;
- étudiant concerné ;
- date ;
- heure ;
- appareil ;
- ancienne valeur ;
- nouvelle valeur ;
- motif ;
- approbateur ;
- résultat.

---

# 3. Types d’établissements

Le portail doit supporter :

- école publique ;
- école privée ;
- université publique ;
- université privée ;
- centre de formation ;
- institut ;
- grande école ;
- lycée ;
- collège ;
- école technique ;
- école professionnelle ;
- organisme de formation continue.

---

# 4. Hiérarchie académique

Le système doit pouvoir représenter :

```text
Établissement
└── Campus
    └── Faculté
        └── Département
            └── Filière
                └── Niveau
                    └── Classe ou Groupe
```

La structure doit rester configurable.

---

# 5. Technologie

Technologie recommandée :

```text
Next.js
TypeScript
```

Pour les applications mobiles associées :

```text
React Native
TypeScript
```

---

# 6. Architecture du portail

Structure recommandée :

```text
src/
├── auth/
├── dashboard/
├── institutions/
├── campuses/
├── faculties/
├── departments/
├── programs/
├── students/
├── guardians/
├── admissions/
├── enrollments/
├── fees/
├── invoices/
├── payments/
├── scholarships/
├── exemptions/
├── student-cards/
├── staff-cards/
├── library/
├── cafeteria/
├── housing/
├── transport/
├── attendance/
├── exams/
├── activities/
├── documents/
├── refunds/
├── reports/
├── integrations/
├── notifications/
├── approvals/
├── audit/
├── security/
└── settings/
```

---

# 7. Navigation principale

Navigation recommandée :

```text
Tableau de bord
Étudiants
Inscriptions
Paiements
Cartes
Services campus
Rapports
Configuration
```

Menu secondaire :

- Admissions ;
- Frais ;
- Factures ;
- Bourses ;
- Exonérations ;
- Bibliothèque ;
- Restauration ;
- Résidences ;
- Transport ;
- Examens ;
- Documents ;
- Remboursements ;
- Audit ;
- Intégrations.

---

# 8. Tableau de bord

Le tableau de bord peut afficher :

- nombre d’étudiants ;
- nouvelles inscriptions ;
- réinscriptions ;
- paiements du jour ;
- frais impayés ;
- échéances proches ;
- bourses versées ;
- cartes actives ;
- cartes bloquées ;
- logements occupés ;
- repas servis ;
- passages bibliothèque ;
- remboursements ;
- incidents ;
- alertes ;
- rapprochements en attente.

---

# 9. Utilisateurs du portail

Rôles possibles :

```text
SCHOOL_OWNER
SCHOOL_ADMIN
CAMPUS_ADMIN
REGISTRAR
FINANCE_MANAGER
ACCOUNTANT
SCHOLARSHIP_MANAGER
STUDENT_CARD_MANAGER
LIBRARY_MANAGER
HOUSING_MANAGER
CAFETERIA_MANAGER
TRANSPORT_MANAGER
TEACHER
STUDENT
PARENT
AUDITOR
VIEWER
```

---

# 10. Permissions

Exemples :

```text
school.dashboard.read
school.student.read
school.student.manage
school.enrollment.manage
school.fee.manage
school.payment.read
school.invoice.manage
school.scholarship.manage
school.student_card.manage
school.library.manage
school.housing.manage
school.report.read
school.audit.read
school.configuration.manage
```

---

# 11. Gestion des étudiants

Chaque étudiant peut avoir :

- identité ;
- photo ;
- numéro étudiant ;
- date de naissance ;
- coordonnées ;
- responsable légal ;
- établissement ;
- campus ;
- filière ;
- niveau ;
- classe ;
- statut ;
- date d’inscription ;
- compte Mansa lié ;
- carte étudiante ;
- historique de paiement ;
- bourses ;
- documents.

---

# 12. Statuts d’un étudiant

- APPLICANT ;
- ADMITTED ;
- ENROLLED ;
- ACTIVE ;
- SUSPENDED ;
- GRADUATED ;
- DROPPED_OUT ;
- TRANSFERRED ;
- ARCHIVED.

---

# 13. Admissions

Le portail doit permettre :

- dépôt de dossier ;
- vérification ;
- demande de complément ;
- validation ;
- rejet ;
- liste d’attente ;
- notification ;
- paiement des frais d’inscription ;
- transformation en étudiant actif.

---

# 14. Inscriptions

Une inscription peut contenir :

- année académique ;
- établissement ;
- campus ;
- filière ;
- niveau ;
- classe ;
- statut ;
- frais ;
- pièces ;
- bourse ;
- exonération ;
- échéancier ;
- date de validation.

---

# 15. Réinscriptions

Le système doit permettre :

- rappel automatique ;
- mise à jour du dossier ;
- choix de niveau ;
- choix de filière ;
- calcul des frais ;
- paiement ;
- validation ;
- génération du reçu ;
- renouvellement de carte.

---

# 16. Frais scolaires

Exemples :

- frais d’inscription ;
- frais de réinscription ;
- scolarité ;
- laboratoire ;
- bibliothèque ;
- examen ;
- assurance ;
- transport ;
- restauration ;
- logement ;
- uniforme ;
- activités ;
- carte étudiante ;
- documents ;
- pénalités.

---

# 17. Règles tarifaires

Les frais peuvent dépendre :

- établissement ;
- campus ;
- niveau ;
- filière ;
- année ;
- étudiant ;
- bourse ;
- exonération ;
- nationalité ;
- paiement anticipé ;
- échéancier ;
- remise ;
- programme.

---

# 18. Échéanciers

Le système peut gérer :

- paiement unique ;
- mensualité ;
- trimestre ;
- semestre ;
- paiement personnalisé ;
- acompte ;
- paiement partiel ;
- échéance finale ;
- pénalité de retard.

---

# 19. Facturation

Chaque facture doit contenir :

- étudiant ;
- établissement ;
- service ;
- année ;
- montant ;
- remise ;
- exonération ;
- pénalité ;
- total ;
- échéance ;
- statut ;
- référence ;
- QR ;
- reçu lié.

---

# 20. Statuts d’une facture

- DRAFT ;
- ISSUED ;
- PARTIALLY_PAID ;
- PAID ;
- OVERDUE ;
- CANCELLED ;
- REFUNDED ;
- DISPUTED ;
- CLOSED.

---

# 21. Paiements

Le paiement peut être effectué par :

- wallet Mansa ;
- carte ;
- Mobile Money ;
- virement ;
- agent Mansa ;
- TPE ;
- DAB ;
- portail web ;
- paiement groupé ;
- parent ou responsable.

---

# 22. Paiement par un tiers

Un parent, employeur, organisme ou proche peut payer pour un étudiant.

Le système doit enregistrer :

- payeur ;
- étudiant ;
- facture ;
- montant ;
- canal ;
- date ;
- référence ;
- reçu ;
- lien éventuel.

---

# 23. Reçus

Chaque reçu doit contenir :

- établissement ;
- campus ;
- étudiant masqué ;
- référence ;
- service ;
- montant ;
- frais ;
- total ;
- date ;
- canal ;
- statut ;
- QR de vérification ;
- signature numérique.

---

# 24. Vérification des reçus

Une page publique sécurisée peut permettre de vérifier :

- authenticité ;
- référence ;
- établissement ;
- montant ;
- date ;
- statut ;
- service.

Les données personnelles restent masquées.

---

# 25. Bourses

Le portail doit gérer :

- programmes ;
- critères ;
- demandes ;
- bénéficiaires ;
- montants ;
- périodes ;
- calendriers ;
- versements ;
- suspensions ;
- renouvellements ;
- recours ;
- rapports.

---

# 26. Types de bourses

- bourse nationale ;
- bourse interne ;
- bourse sociale ;
- bourse au mérite ;
- bourse sportive ;
- bourse privée ;
- aide d’urgence ;
- prise en charge partielle ;
- prise en charge complète.

---

# 27. Versement des bourses

Canaux possibles :

- wallet Mansa ;
- compte bancaire ;
- carte Mansa ;
- Mobile Money ;
- réduction directe de facture ;
- versement à l’établissement.

---

# 28. Exonérations et remises

Le système doit permettre :

- exonération totale ;
- exonération partielle ;
- remise ;
- prise en charge ;
- tarif social ;
- tarif employé ;
- tarif fratrie ;
- tarif partenaire.

Chaque décision doit être justifiée et auditée.

---

# 29. Carte étudiante

Le portail permet :

- création ;
- personnalisation ;
- émission ;
- activation ;
- blocage ;
- remplacement ;
- renouvellement ;
- expiration ;
- opposition ;
- intégration à un wallet ;
- lien avec les services campus.

---

# 30. Données de la carte étudiante

Peuvent apparaître :

- nom ;
- photo ;
- numéro étudiant ;
- établissement ;
- campus ;
- filière ;
- année ;
- date d’expiration ;
- QR ;
- puce ;
- fonctions d’accès ;
- fonctions de paiement.

---

# 31. Carte du personnel

Le portail peut également gérer :

- enseignants ;
- administratifs ;
- agents ;
- prestataires ;
- visiteurs ;
- accès temporaires.

---

# 32. Accès campus

La carte peut servir à :

- entrer sur le campus ;
- accéder à une salle ;
- accéder à un laboratoire ;
- accéder à une résidence ;
- emprunter un livre ;
- prendre un repas ;
- utiliser un transport ;
- s’identifier à un examen.

---

# 33. Bibliothèque

Le module doit gérer :

- abonnements ;
- emprunts ;
- retours ;
- retards ;
- pénalités ;
- réservations ;
- accès ;
- historique ;
- paiement des frais.

---

# 34. Restauration

Le portail peut gérer :

- comptes repas ;
- forfaits ;
- tickets ;
- menus ;
- quotas ;
- subventions ;
- paiements ;
- passages ;
- statistiques ;
- remboursements.

---

# 35. Résidences

Le module logement peut gérer :

- résidences ;
- chambres ;
- lits ;
- demandes ;
- attributions ;
- contrats ;
- loyers ;
- cautions ;
- paiements ;
- incidents ;
- états des lieux ;
- sorties.

---

# 36. Transport scolaire

Le portail peut gérer :

- lignes ;
- arrêts ;
- abonnements ;
- cartes ;
- paiements ;
- contrôle ;
- fréquentation ;
- incidents ;
- horaires.

---

# 37. Examens

La carte étudiante peut servir à :

- vérifier l’identité ;
- contrôler l’éligibilité ;
- confirmer l’inscription ;
- enregistrer la présence ;
- empêcher les doublons ;
- générer une preuve de passage.

---

# 38. Documents étudiants

Le portail peut gérer :

- certificat de scolarité ;
- reçu ;
- attestation de paiement ;
- attestation d’inscription ;
- carte ;
- relevé ;
- attestation de bourse ;
- document de logement ;
- autorisation.

---

# 39. Génération de documents

Chaque document doit avoir :

- référence ;
- étudiant ;
- établissement ;
- date ;
- version ;
- statut ;
- QR ;
- signature ;
- modèle ;
- langue ;
- historique.

---

# 40. Remboursements

Un remboursement peut concerner :

- paiement en double ;
- annulation d’inscription ;
- service non fourni ;
- logement annulé ;
- bourse recalculée ;
- erreur de montant ;
- activité annulée.

---

# 41. Workflow de remboursement

1. demande ;
2. justification ;
3. contrôle ;
4. approbation ;
5. exécution ;
6. notification ;
7. rapprochement ;
8. audit.

---

# 42. Parents et responsables

Un parent ou responsable peut :

- consulter les factures ;
- payer ;
- voir les reçus ;
- suivre les échéances ;
- recevoir les notifications ;
- consulter les documents autorisés ;
- gérer plusieurs enfants.

---

# 43. Portail étudiant

L’étudiant peut :

- consulter son profil ;
- payer ;
- suivre ses factures ;
- voir ses reçus ;
- consulter sa carte ;
- voir ses bourses ;
- télécharger ses documents ;
- suivre son logement ;
- suivre son transport ;
- recevoir des notifications.

---

# 44. Notifications

Types :

- admission ;
- inscription validée ;
- paiement reçu ;
- échéance ;
- retard ;
- bourse ;
- carte disponible ;
- carte expirante ;
- document prêt ;
- logement attribué ;
- remboursement ;
- incident ;
- maintenance.

---

# 45. Multi-campus

Un établissement doit pouvoir gérer :

- plusieurs campus ;
- plusieurs villes ;
- plusieurs pays ;
- plusieurs devises ;
- plusieurs calendriers ;
- plusieurs équipes ;
- plusieurs comptes de règlement ;
- plusieurs catalogues de frais.

---

# 46. Multi-année académique

Le système doit conserver :

- année en cours ;
- années passées ;
- inscriptions historiques ;
- factures ;
- paiements ;
- cartes ;
- bourses ;
- documents ;
- archives.

---

# 47. Intégrations

Le portail peut se connecter à :

- système de scolarité ;
- ERP ;
- logiciel comptable ;
- bibliothèque ;
- contrôle d’accès ;
- transport ;
- restaurant ;
- résidence ;
- ministère ;
- organisme de bourses ;
- banque ;
- Mobile Money.

---

# 48. API

Exemples :

```http
GET    /school/dashboard
GET    /school/students
GET    /school/students/{id}
POST   /school/students

GET    /school/enrollments
POST   /school/enrollments

GET    /school/invoices
POST   /school/invoices
POST   /school/invoices/{id}/pay

GET    /school/scholarships
POST   /school/scholarships

GET    /school/student-cards
POST   /school/student-cards

GET    /school/housing
GET    /school/library
GET    /school/reports
GET    /school/audit
```

---

# 49. Webhooks

Événements possibles :

```text
school.student.created
school.student.enrolled
school.invoice.created
school.invoice.paid
school.payment.failed
school.scholarship.awarded
school.scholarship.paid
school.student_card.issued
school.student_card.blocked
school.housing.assigned
school.refund.completed
school.document.generated
```

---

# 50. Rapports

Rapports possibles :

- inscriptions ;
- réinscriptions ;
- paiements ;
- impayés ;
- échéanciers ;
- bourses ;
- exonérations ;
- cartes ;
- bibliothèque ;
- restauration ;
- logements ;
- transports ;
- remboursements ;
- campus ;
- étudiants ;
- années académiques.

---

# 51. Exports

Formats :

- CSV ;
- XLSX ;
- PDF ;
- JSON ;
- API.

Les exports doivent être :

- limités ;
- masqués ;
- chiffrés ;
- audités ;
- temporaires ;
- soumis aux permissions.

---

# 52. Approbations

Peuvent exiger une approbation :

- modification de frais ;
- exonération ;
- remboursement ;
- création d’une bourse ;
- paiement de masse ;
- import étudiant ;
- émission massive de cartes ;
- changement de compte bancaire ;
- export massif ;
- suppression logique d’un dossier.

---

# 53. Double validation

Peut être exigée pour :

- remboursements élevés ;
- exonérations importantes ;
- versements de bourses ;
- changement de tarif ;
- changement de compte de règlement ;
- import de masse ;
- émission de cartes ;
- réactivation après fraude.

---

# 54. Séparation des rôles

Le demandeur ne doit pas pouvoir valider seul une action critique.

Exemple :

- scolarité crée ;
- finance contrôle ;
- direction approuve ;
- système exécute.

---

# 55. Sécurité

Mesures principales :

- MFA ;
- RBAC ;
- ABAC ;
- chiffrement ;
- appareils approuvés ;
- sessions contrôlées ;
- masquage des données ;
- journal d’audit ;
- rate limiting ;
- révocation ;
- détection d’anomalie ;
- sauvegardes ;
- contrôle d’accès.

---

# 56. Protection des étudiants mineurs

Le système doit prévoir :

- consentement du responsable ;
- accès limité ;
- données masquées ;
- contrôle des communications ;
- limitation des exports ;
- journalisation des consultations ;
- règles spécifiques selon l’âge et le pays.

---

# 57. Audit

Le journal doit contenir :

- utilisateur ;
- rôle ;
- établissement ;
- campus ;
- étudiant ;
- action ;
- ressource ;
- ancienne valeur ;
- nouvelle valeur ;
- date ;
- heure ;
- appareil ;
- IP ;
- motif ;
- résultat ;
- approbateur.

---

# 58. Immutabilité

Les audits ne doivent pas être :

- supprimés ;
- modifiés ;
- réécrits ;
- masqués sans trace ;
- désactivés par un administrateur local.

---

# 59. Modèles principaux

- EducationInstitution
- Campus
- Faculty
- Department
- AcademicProgram
- Student
- Guardian
- AdmissionApplication
- Enrollment
- AcademicYear
- SchoolFeeRule
- StudentInvoice
- StudentPayment
- ScholarshipProgram
- ScholarshipBeneficiary
- FeeExemption
- StudentCard
- StaffCard
- LibraryAccount
- LibraryLoan
- CafeteriaAccount
- HousingResidence
- HousingAssignment
- TransportSubscription
- StudentDocument
- StudentRefund
- SchoolApproval
- SchoolAudit

---

# 60. Analytics

Événements possibles :

```text
school_login_completed
school_student_created
school_enrollment_completed
school_invoice_created
school_payment_completed
school_payment_failed
school_scholarship_awarded
school_scholarship_paid
school_student_card_issued
school_housing_assigned
school_document_generated
school_refund_completed
school_security_alert_created
```

---

# 61. Données analytics interdites

Ne pas transmettre :

- mot de passe ;
- PIN ;
- OTP ;
- numéro complet de carte ;
- données biométriques ;
- document complet ;
- note académique complète non nécessaire ;
- identité complète inutile ;
- données de santé ;
- informations financières sensibles ;
- secrets.

---

# 62. Tests

- tests d’authentification ;
- tests MFA ;
- tests rôles ;
- tests permissions ;
- tests isolation établissement ;
- tests multi-campus ;
- tests admissions ;
- tests inscriptions ;
- tests réinscriptions ;
- tests factures ;
- tests paiements ;
- tests paiement tiers ;
- tests échéanciers ;
- tests bourses ;
- tests exonérations ;
- tests cartes ;
- tests accès campus ;
- tests bibliothèque ;
- tests restauration ;
- tests logement ;
- tests transport ;
- tests documents ;
- tests remboursements ;
- tests parents ;
- tests étudiants mineurs ;
- tests rapports ;
- tests exports ;
- tests API ;
- tests webhooks ;
- tests audit ;
- tests sécurité ;
- tests performance ;
- tests accessibilité.

---

# 63. Règles métier

1. Chaque établissement possède un périmètre isolé.
2. Les données sont filtrées par établissement et campus.
3. Les rôles limitent les accès.
4. Les décisions académiques restent sous la responsabilité de l’établissement.
5. Les frais sont configurables.
6. Les paiements utilisent une référence unique.
7. Les paiements peuvent être effectués par un tiers.
8. Les reçus sont vérifiables.
9. Les bourses sont tracées.
10. Les exonérations sont justifiées.
11. Les cartes sont liées à un étudiant ou un membre du personnel.
12. Les cartes peuvent contrôler l’accès aux services.
13. Les remboursements passent par un workflow.
14. Les documents sont versionnés.
15. Les années académiques sont historisées.
16. Les données des mineurs sont protégées.
17. Les exports sont audités.
18. Les actions critiques nécessitent une approbation.
19. Le demandeur ne valide pas seul sa propre action critique.
20. Les audits sont immuables.

---

# 64. Critères d’acceptation

Le Portail Écoles et Universités Mansa est validé lorsque :

- les établissements peuvent être créés ;
- les campus sont administrables ;
- les étudiants sont gérés ;
- les admissions sont intégrées ;
- les inscriptions et réinscriptions fonctionnent ;
- les frais sont configurables ;
- les factures sont générées ;
- les paiements sont suivis ;
- les échéanciers sont disponibles ;
- les paiements par des tiers fonctionnent ;
- les reçus sont vérifiables ;
- les bourses sont gérées ;
- les exonérations sont administrables ;
- les cartes étudiantes sont émises ;
- les cartes du personnel sont prises en charge ;
- les services campus sont intégrés ;
- la bibliothèque est gérée ;
- la restauration est gérée ;
- les logements sont gérés ;
- le transport est géré ;
- les documents sont générés ;
- les remboursements utilisent un workflow ;
- les parents disposent d’un accès limité ;
- les étudiants disposent d’un espace personnel ;
- les données des mineurs sont protégées ;
- les rapports sont exportables ;
- les API et webhooks sont disponibles ;
- les audits sont complets ;
- les actions critiques sont protégées ;
- les tests couvrent les parcours essentiels.
