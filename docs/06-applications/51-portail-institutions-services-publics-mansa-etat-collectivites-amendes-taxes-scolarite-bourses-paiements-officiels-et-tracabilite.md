# 51 — Portail Institutions et Services Publics Mansa : État, collectivités, amendes, taxes, scolarité, bourses, paiements officiels et traçabilité

## 1. Objet du document

Ce document définit l’architecture officielle du **Portail Institutions et Services Publics Mansa**.

Ce portail est destiné aux organismes publics et institutions autorisées souhaitant utiliser Mansa pour :

- encaisser des paiements officiels ;
- émettre des références de paiement ;
- enregistrer des amendes ;
- collecter des taxes ;
- gérer des frais administratifs ;
- encaisser des frais scolaires ;
- distribuer des bourses ;
- gérer des aides publiques ;
- émettre des cartes étudiantes ;
- gérer des cartes professionnelles ;
- suivre les paiements ;
- produire des reçus officiels ;
- effectuer des rapprochements ;
- lutter contre la corruption ;
- assurer la traçabilité des agents ;
- suivre les recours ;
- superviser les opérations ;
- produire des rapports ;
- connecter les systèmes publics aux API Mansa.

Le portail peut servir :

- l’État ;
- les ministères ;
- les mairies ;
- les collectivités territoriales ;
- la police ;
- la gendarmerie ;
- les administrations fiscales ;
- les établissements scolaires ;
- les universités ;
- les hôpitaux publics ;
- les agences publiques ;
- les entreprises publiques ;
- les services d’eau ;
- les services d’électricité ;
- les services de transport ;
- les organismes de bourses ;
- les programmes sociaux.

L’objectif est de construire une plateforme permettant de numériser les paiements publics tout en garantissant :

- l’identification des agents ;
- la transparence ;
- la séparation des rôles ;
- la traçabilité ;
- l’impossibilité de modifier une opération après validation ;
- la réduction des paiements en espèces ;
- la réduction des détournements ;
- le suivi en temps réel ;
- le contrôle centralisé ;
- la gestion des recours ;
- l’intégration progressive des institutions.

---

# 2. Principes fondamentaux

## 2.1 Le portail institutionnel est séparé du portail Admin Mansa

Les utilisateurs institutionnels ne doivent pas avoir accès :

- aux autres clients Mansa ;
- aux autres institutions ;
- aux paramètres globaux de Mansa ;
- au ledger complet ;
- aux données des commerçants ;
- aux configurations internes ;
- aux secrets techniques ;
- aux opérations d’autres pays.

Chaque institution dispose de son propre périmètre.

---

## 2.2 Aucun agent public ne doit agir sans identification

Chaque agent doit disposer :

- d’un compte nominatif ;
- d’un rôle ;
- d’un matricule ;
- d’une institution ;
- d’un service ;
- d’une zone ;
- d’un appareil autorisé ;
- d’un statut ;
- d’un historique ;
- de permissions limitées.

Les comptes partagés doivent être interdits.

---

## 2.3 Les opérations officielles sont immuables

Une opération validée ne doit pas être modifiée directement.

En cas d’erreur, le système doit utiliser :

- une annulation contrôlée ;
- une écriture compensatrice ;
- un recours ;
- une décision ;
- un nouveau document ;
- un historique complet.

---

## 2.4 Les frais sont entièrement configurables

Aucun montant ne doit être codé en dur.

Les frais peuvent dépendre :

- de l’institution ;
- du service ;
- du pays ;
- de la région ;
- de la commune ;
- du type de dossier ;
- du montant ;
- de la catégorie ;
- de la date ;
- de la réglementation ;
- d’une exonération ;
- d’une campagne ;
- d’un programme public.

---

## 2.5 Le paiement doit être distinct de la décision administrative

Mansa exécute et trace le paiement.

L’institution reste responsable de :

- la qualification de l’infraction ;
- le montant légal ;
- la décision administrative ;
- l’éligibilité à une bourse ;
- l’attribution d’une aide ;
- l’émission d’un document ;
- la validation d’un dossier ;
- le traitement du recours.

---

## 2.6 Toute action sensible doit être auditée

Chaque action doit enregistrer :

- agent ;
- rôle ;
- matricule ;
- institution ;
- service ;
- appareil ;
- date ;
- heure ;
- localisation si activée ;
- ressource ;
- ancienne valeur ;
- nouvelle valeur ;
- motif ;
- résultat ;
- approbateur ;
- référence de corrélation.

---

# 3. Types d’institutions

Exemples :

- ministère ;
- direction nationale ;
- mairie ;
- commune ;
- région ;
- préfecture ;
- établissement scolaire ;
- université ;
- hôpital ;
- police ;
- gendarmerie ;
- douane ;
- administration fiscale ;
- agence publique ;
- entreprise publique ;
- programme social ;
- organisme de bourses ;
- service public délégué.

---

# 4. Hiérarchie institutionnelle

Le système doit pouvoir représenter :

```text
État
└── Ministère
    └── Direction
        └── Service
            └── Région
                └── Commune
                    └── Point de service
                        └── Agent
```

La hiérarchie doit rester configurable.

---

# 5. Technologie

Technologie recommandée :

```text
Next.js
TypeScript
```

Pour les agents terrain :

```text
React Native
TypeScript
```

ou terminal Android sécurisé selon le matériel.

---

# 6. Architecture du portail

Structure recommandée :

```text
src/
├── auth/
├── dashboard/
├── institutions/
├── departments/
├── agents/
├── citizens/
├── services/
├── fines/
├── taxes/
├── invoices/
├── school-fees/
├── scholarships/
├── social-programs/
├── student-cards/
├── payments/
├── receipts/
├── refunds/
├── appeals/
├── settlements/
├── reconciliation/
├── reports/
├── inspections/
├── fraud/
├── documents/
├── notifications/
├── integrations/
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
Services
Paiements
Agents
Citoyens
Recours
Rapports
Configuration
```

Menu secondaire :

- Amendes ;
- Taxes ;
- Factures ;
- Scolarité ;
- Bourses ;
- Aides ;
- Cartes ;
- Reçus ;
- Règlements ;
- Rapprochements ;
- Incidents ;
- Audit ;
- Intégrations.

La navigation dépend du rôle.

---

# 8. Tableau de bord institutionnel

Le tableau de bord peut afficher :

- paiements du jour ;
- montant collecté ;
- nombre de références émises ;
- amendes enregistrées ;
- taxes payées ;
- frais scolaires encaissés ;
- bourses distribuées ;
- opérations échouées ;
- recours ouverts ;
- agents actifs ;
- appareils actifs ;
- incidents ;
- anomalies ;
- rapprochements en attente ;
- disponibilité des services.

---

# 9. Tableaux de bord spécialisés

Vues possibles :

- direction générale ;
- finance ;
- trésorerie ;
- police ;
- université ;
- mairie ;
- service social ;
- contrôle interne ;
- audit ;
- support ;
- région ;
- commune ;
- établissement.

---

# 10. Utilisateurs institutionnels

Types possibles :

- administrateur institution ;
- administrateur service ;
- responsable national ;
- responsable régional ;
- responsable communal ;
- agent terrain ;
- caissier ;
- contrôleur ;
- comptable ;
- auditeur ;
- gestionnaire de recours ;
- responsable bourses ;
- responsable scolarité ;
- observateur.

---

# 11. Rôles

Exemples :

```text
INSTITUTION_OWNER
INSTITUTION_ADMIN
NATIONAL_SUPERVISOR
REGIONAL_SUPERVISOR
LOCAL_SUPERVISOR
FIELD_AGENT
CASHIER
ACCOUNTANT
APPEAL_OFFICER
AUDITOR
VIEWER
```

---

# 12. Permissions

Exemples :

```text
institution.dashboard.read
institution.agent.read
institution.agent.manage
institution.service.read
institution.service.manage
institution.fine.create
institution.fine.read
institution.fine.cancel.request
institution.tax.read
institution.tax.issue
institution.payment.read
institution.receipt.read
institution.refund.request
institution.appeal.read
institution.appeal.manage
institution.scholarship.manage
institution.report.read
institution.reconciliation.read
institution.audit.read
institution.configuration.manage
```

---

# 13. Périmètre d’accès

Un utilisateur peut être limité à :

- une institution ;
- un ministère ;
- une direction ;
- une région ;
- une commune ;
- un établissement ;
- un service ;
- un type d’opération ;
- une période ;
- un montant ;
- un groupe de citoyens ;
- un environnement.

---

# 14. Authentification

Méthodes possibles :

- mot de passe ;
- MFA ;
- passkey ;
- clé de sécurité ;
- certificat ;
- biométrie système ;
- SSO gouvernemental ;
- carte professionnelle ;
- appareil enregistré.

---

# 15. MFA obligatoire

Le MFA doit être obligatoire pour :

- les administrateurs ;
- les responsables financiers ;
- les auditeurs ;
- les opérations de remboursement ;
- les modifications de tarifs ;
- les exports ;
- les changements de compte bancaire ;
- les actions de production.

---

# 16. Appareils autorisés

Chaque appareil doit contenir :

- agent ;
- institution ;
- service ;
- modèle ;
- numéro de série ;
- OS ;
- certificat ;
- date d’activation ;
- dernière activité ;
- localisation autorisée ;
- statut ;
- révocation.

---

# 17. Identification du citoyen

Selon le service, le citoyen peut être identifié par :

- numéro de téléphone ;
- identifiant Mansa ;
- QR Mansa ;
- numéro de dossier ;
- numéro étudiant ;
- numéro fiscal ;
- numéro de permis ;
- immatriculation ;
- numéro de carte nationale ;
- référence administrative.

Les données visibles doivent être limitées.

---

# 18. Protection des données citoyennes

Un agent ne doit voir que les informations nécessaires.

Exemples :

- nom partiellement masqué ;
- identifiant ;
- statut du dossier ;
- montant dû ;
- référence ;
- service concerné ;
- justificatifs autorisés.

Il ne doit pas voir librement :

- solde Mansa ;
- historique bancaire ;
- autres paiements ;
- documents non liés ;
- PIN ;
- OTP ;
- carte complète ;
- données biométriques ;
- informations d’autres services.

---

# 19. Catalogue de services publics

Chaque institution peut publier des services.

Exemples :

- paiement d’amende ;
- taxe municipale ;
- impôt ;
- frais de dossier ;
- permis ;
- document administratif ;
- scolarité ;
- inscription universitaire ;
- carte étudiante ;
- frais hospitaliers ;
- facture publique ;
- redevance ;
- autorisation ;
- licence ;
- abonnement public.

---

# 20. Fiche d’un service

Elle doit contenir :

- code ;
- nom ;
- institution ;
- description ;
- pays ;
- zone ;
- montant ;
- règle tarifaire ;
- pièces requises ;
- délai ;
- canal ;
- statut ;
- date d’effet ;
- conditions ;
- recours ;
- compte de règlement.

---

# 21. Statuts d’un service

- DRAFT ;
- REVIEW ;
- APPROVED ;
- ACTIVE ;
- SUSPENDED ;
- MAINTENANCE ;
- EXPIRED ;
- ARCHIVED.

---

# 22. Référence de paiement

Une institution peut générer une référence contenant :

- identifiant unique ;
- citoyen ;
- institution ;
- service ;
- montant ;
- devise ;
- date d’émission ;
- date d’expiration ;
- statut ;
- canal ;
- QR ;
- conditions ;
- pièces associées.

---

# 23. Statuts d’une référence

- CREATED ;
- ACTIVE ;
- PARTIALLY_PAID ;
- PAID ;
- EXPIRED ;
- CANCELLED ;
- DISPUTED ;
- REFUNDED ;
- UNDER_REVIEW.

---

# 24. Paiement d’une référence

Le citoyen peut payer par :

- wallet Mansa ;
- carte ;
- Mobile Money ;
- virement ;
- agent Mansa ;
- DAB ;
- TPE ;
- portail web ;
- application Client ;
- paiement groupé autorisé.

---

# 25. Reçu officiel

Le reçu doit contenir :

- institution ;
- service ;
- citoyen masqué ;
- référence ;
- montant ;
- frais ;
- taxe ;
- total ;
- date ;
- heure ;
- canal ;
- statut ;
- agent éventuel ;
- QR de vérification ;
- signature numérique ;
- procédure de recours.

---

# 26. Vérification publique d’un reçu

Le système peut proposer une page permettant de vérifier :

- authenticité ;
- institution ;
- référence ;
- statut ;
- montant ;
- date ;
- service.

Les données personnelles doivent rester masquées.

---

# 27. Module Amendes

Le module permet de gérer :

- infractions ;
- catégories ;
- montants ;
- agents ;
- lieux ;
- véhicules ;
- personnes ;
- preuves ;
- références ;
- paiements ;
- recours ;
- annulations ;
- rapports.

---

# 28. Types d’amendes

Exemples :

- circulation ;
- stationnement ;
- transport ;
- commerce ;
- environnement ;
- urbanisme ;
- marché ;
- fiscalité locale ;
- réglementation sectorielle.

---

# 29. Création d’une amende sur le terrain

Parcours :

1. l’agent s’authentifie ;
2. il sélectionne le type d’infraction ;
3. il identifie le contrevenant ;
4. il saisit les éléments ;
5. il joint les preuves autorisées ;
6. le système calcule le montant ;
7. l’agent vérifie le résumé ;
8. l’amende est émise ;
9. une référence est générée ;
10. le citoyen reçoit le reçu ou la notification ;
11. le paiement peut être effectué sur place ou ultérieurement.

---

# 30. Paiement sur place

Le citoyen peut payer immédiatement par :

- Mansa ;
- carte ;
- Mobile Money ;
- QR ;
- TPE ;
- autre canal autorisé.

Le policier ou l’agent public ne doit pas encaisser sur son compte personnel.

---

# 31. Paiement en espèces

Si l’institution autorise exceptionnellement les espèces :

- l’encaissement doit passer par une caisse officielle ;
- un reçu doit être généré ;
- l’agent doit être identifié ;
- la caisse doit être ouverte ;
- la caisse doit être clôturée ;
- l’opération doit être rapprochée ;
- les écarts doivent être signalés.

L’usage des espèces doit pouvoir être désactivé.

---

# 32. Anti-corruption

Le système doit empêcher ou détecter :

- paiement sur compte personnel ;
- modification manuelle du montant ;
- suppression de l’amende ;
- création sans matricule ;
- réutilisation d’un reçu ;
- perception de frais supplémentaires ;
- annulation injustifiée ;
- appareil non autorisé ;
- localisation incohérente ;
- opérations hors horaires ;
- volume anormal ;
- collusion ;
- références fictives.

---

# 33. Preuves d’infraction

Types :

- photo ;
- vidéo ;
- document ;
- immatriculation ;
- géolocalisation ;
- horodatage ;
- témoignage ;
- signature ;
- scan ;
- référence radar ou appareil.

---

# 34. Intégrité des preuves

Chaque preuve doit avoir :

- identifiant ;
- hash ;
- auteur ;
- appareil ;
- date ;
- heure ;
- localisation si autorisée ;
- dossier ;
- statut ;
- chaîne de conservation ;
- règle de rétention.

---

# 35. Recours contre une amende

Le citoyen doit pouvoir :

- consulter l’amende ;
- lire le motif ;
- consulter les preuves autorisées ;
- soumettre un recours ;
- joindre des documents ;
- suivre le statut ;
- recevoir la décision ;
- être remboursé si nécessaire.

---

# 36. Statuts d’un recours

- DRAFT ;
- SUBMITTED ;
- RECEIVED ;
- UNDER_REVIEW ;
- INFORMATION_REQUIRED ;
- ACCEPTED ;
- PARTIALLY_ACCEPTED ;
- REJECTED ;
- CLOSED ;
- ESCALATED.

---

# 37. Séparation des rôles pour les recours

L’agent ayant créé l’amende ne doit pas décider seul du recours.

Le recours doit être traité par :

- un autre agent ;
- un superviseur ;
- une commission ;
- un service juridique ;
- une autorité compétente.

---

# 38. Annulation d’une amende

Une annulation doit exiger :

- motif ;
- preuve ;
- demandeur ;
- approbateur ;
- date ;
- référence ;
- effet financier ;
- notification ;
- audit.

L’amende d’origine reste visible dans l’historique.

---

# 39. Module Taxes et redevances

Le système doit gérer :

- taxes nationales ;
- taxes régionales ;
- taxes municipales ;
- redevances ;
- droits ;
- licences ;
- autorisations ;
- pénalités ;
- exonérations ;
- échéanciers.

---

# 40. Avis de paiement

Un avis peut contenir :

- contribuable ;
- service ;
- période ;
- base ;
- taux ;
- montant ;
- pénalité ;
- remise ;
- échéance ;
- référence ;
- statut ;
- pièces.

---

# 41. Paiement partiel

Selon les règles, une taxe peut être :

- payable en une fois ;
- payable en plusieurs échéances ;
- partiellement payable ;
- automatiquement répartie ;
- soumise à un minimum ;
- soumise à une date limite.

---

# 42. Exonérations

Une exonération doit être :

- réglementée ;
- documentée ;
- datée ;
- limitée ;
- approuvée ;
- auditée ;
- liée à une base légale ou à un programme.

---

# 43. Module Scolarité

Le portail doit permettre de gérer :

- établissements ;
- étudiants ;
- inscriptions ;
- frais scolaires ;
- échéanciers ;
- factures ;
- paiements ;
- reçus ;
- exonérations ;
- bourses ;
- cartes étudiantes ;
- rapports.

---

# 44. Identification étudiant

Par :

- numéro étudiant ;
- matricule ;
- QR ;
- carte étudiante ;
- téléphone ;
- identifiant national ;
- référence d’inscription.

---

# 45. Frais scolaires

Exemples :

- inscription ;
- réinscription ;
- scolarité ;
- bibliothèque ;
- laboratoire ;
- examen ;
- logement ;
- transport ;
- restauration ;
- carte étudiante ;
- activité pédagogique.

---

# 46. Échéancier scolaire

Le système doit pouvoir gérer :

- paiement unique ;
- mensualités ;
- trimestres ;
- semestres ;
- échéances personnalisées ;
- pénalités ;
- remises ;
- bourses ;
- prise en charge.

---

# 47. Carte étudiante

Le portail peut permettre :

- demande ;
- validation ;
- personnalisation ;
- émission ;
- activation ;
- remplacement ;
- opposition ;
- expiration ;
- renouvellement ;
- accès à des services ;
- paiement ;
- identité étudiante.

---

# 48. Données de la carte étudiante

Peuvent inclure :

- nom ;
- photo ;
- numéro étudiant ;
- établissement ;
- année ;
- filière ;
- date d’expiration ;
- QR ;
- puce ;
- fonctions de paiement selon activation.

Les données doivent être configurables.

---

# 49. Module Bourses

Le système doit gérer :

- programmes ;
- critères ;
- candidats ;
- bénéficiaires ;
- montants ;
- calendriers ;
- contrôles ;
- validations ;
- versements ;
- suspensions ;
- recours ;
- rapports.

---

# 50. Versement des bourses

Canaux possibles :

- wallet Mansa ;
- compte bancaire ;
- Mobile Money ;
- carte Mansa ;
- autre canal approuvé.

Le versement doit être nominatif et traçable.

---

# 51. Contrôle des doublons de bourse

Le système doit détecter :

- doublon d’identité ;
- doublon de compte ;
- doublon de téléphone ;
- bénéficiaire décédé ou inactif selon source autorisée ;
- bénéficiaire non éligible ;
- versement multiple ;
- document réutilisé ;
- compte suspect.

---

# 52. Suspension d’une bourse

Elle doit préciser :

- motif ;
- programme ;
- bénéficiaire ;
- date ;
- durée ;
- autorité ;
- recours ;
- effet ;
- notification ;
- audit.

---

# 53. Programmes sociaux

Le portail peut gérer :

- aides directes ;
- subventions ;
- coupons ;
- allocations ;
- aides alimentaires ;
- aides scolaires ;
- aides énergétiques ;
- programmes d’urgence ;
- paiements ciblés.

---

# 54. Critères d’éligibilité

Ils peuvent dépendre :

- du programme ;
- du revenu ;
- de la zone ;
- de l’âge ;
- du statut ;
- du foyer ;
- du handicap ;
- de la scolarité ;
- d’une catastrophe ;
- d’une décision administrative.

Mansa ne doit pas inventer l’éligibilité.

---

# 55. Versements de masse

Le portail doit permettre :

- import de bénéficiaires ;
- validation ;
- simulation ;
- détection d’erreurs ;
- approbation ;
- exécution ;
- suivi ;
- reprise ;
- rapport ;
- rapprochement.

---

# 56. Import de masse

Les imports doivent être :

- validés ;
- antivirusés ;
- comparés ;
- simulés ;
- versionnés ;
- limités ;
- approuvés ;
- audités.

---

# 57. Paiement groupé

Une institution peut lancer un lot contenant :

- identifiant ;
- programme ;
- bénéficiaires ;
- montants ;
- devise ;
- date ;
- statut ;
- approbateurs ;
- total ;
- résultat ;
- erreurs.

---

# 58. Statuts d’un lot

- DRAFT ;
- VALIDATING ;
- READY ;
- APPROVAL_PENDING ;
- APPROVED ;
- PROCESSING ;
- PARTIALLY_COMPLETED ;
- COMPLETED ;
- FAILED ;
- CANCELLED ;
- RECONCILIATION_REQUIRED.

---

# 59. Double validation des paiements de masse

Le demandeur ne doit pas valider seul le lot.

Une validation supplémentaire peut être exigée selon :

- montant total ;
- nombre de bénéficiaires ;
- programme ;
- pays ;
- institution ;
- risque ;
- urgence.

---

# 60. Remboursements

Un remboursement peut concerner :

- paiement en double ;
- annulation de service ;
- recours accepté ;
- erreur de montant ;
- paiement non applicable ;
- service non fourni ;
- décision institutionnelle.

---

# 61. Workflow de remboursement

1. demande ;
2. contrôle ;
3. justification ;
4. preuve ;
5. calcul ;
6. approbation ;
7. exécution ;
8. notification ;
9. rapprochement ;
10. audit.

---

# 62. Règlements institutionnels

Le système doit afficher :

- montant brut ;
- frais ;
- taxes ;
- remboursements ;
- ajustements ;
- montant net ;
- période ;
- compte de destination ;
- référence ;
- statut ;
- date ;
- rapprochement.

---

# 63. Comptes de destination

Une institution peut disposer de :

- compte Trésor ;
- compte bancaire ;
- compte de règlement ;
- sous-compte par service ;
- sous-compte par région ;
- sous-compte par programme ;
- compte de suspense.

---

# 64. Répartition automatique

Un paiement peut être réparti entre :

- Trésor ;
- ministère ;
- collectivité ;
- établissement ;
- Mansa ;
- banque partenaire ;
- opérateur ;
- taxe ;
- fonds spécifique.

La répartition est configurée par contrat et réglementation.

---

# 65. Frais et commissions

Le système doit gérer :

- frais payés par le citoyen ;
- frais pris en charge par l’institution ;
- frais subventionnés ;
- frais partagés ;
- commission Mansa ;
- commission banque ;
- commission agent ;
- commission opérateur ;
- taxe.

---

# 66. Transparence des frais

Avant paiement, le citoyen doit voir :

- montant principal ;
- pénalité ;
- frais ;
- taxe ;
- réduction ;
- total ;
- bénéficiaire ;
- référence ;
- date d’effet.

---

# 67. Rapprochement

Le portail doit comparer :

- références émises ;
- paiements reçus ;
- reçus ;
- ledger ;
- banque ;
- Mobile Money ;
- TPE ;
- agents ;
- lots ;
- règlements ;
- comptes institutionnels.

---

# 68. Écarts

Exemples :

- paiement sans référence ;
- référence payée deux fois ;
- montant incorrect ;
- paiement non rapproché ;
- reçu manquant ;
- règlement incomplet ;
- double versement ;
- paiement annulé ;
- opération en suspense.

---

# 69. Rapports

Rapports possibles :

- paiements ;
- amendes ;
- taxes ;
- scolarité ;
- bourses ;
- aides ;
- agents ;
- services ;
- communes ;
- régions ;
- institutions ;
- recours ;
- remboursements ;
- règlements ;
- écarts ;
- fraude ;
- performance ;
- disponibilité.

---

# 70. Rapports publics

Certaines statistiques peuvent être publiées :

- montant collecté ;
- nombre de paiements ;
- délai moyen ;
- taux numérique ;
- répartition par service ;
- nombre de recours ;
- taux de résolution.

La publication doit respecter la confidentialité.

---

# 71. Exports

Formats possibles :

- CSV ;
- XLSX ;
- PDF ;
- JSON ;
- API ;
- SFTP.

Les exports doivent être :

- autorisés ;
- masqués ;
- chiffrés ;
- temporaires ;
- audités ;
- limités au périmètre.

---

# 72. Notifications citoyennes

Canaux :

- notification Mansa ;
- SMS ;
- e-mail ;
- reçu papier ;
- portail ;
- message institutionnel.

Types :

- référence créée ;
- paiement reçu ;
- échéance ;
- pénalité ;
- recours mis à jour ;
- remboursement ;
- bourse versée ;
- carte disponible ;
- document prêt.

---

# 73. Notifications internes

Exemples :

- agent suspendu ;
- montant inhabituel ;
- paiement en double ;
- recours urgent ;
- écart de rapprochement ;
- lot rejeté ;
- appareil inconnu ;
- activité hors zone ;
- service indisponible ;
- règlement échoué.

---

# 74. Fraude et anomalie

Le système doit détecter :

- agent trop actif ;
- référence répétée ;
- annulations fréquentes ;
- montant modifié ;
- paiement détourné ;
- appareil inconnu ;
- faux bénéficiaire ;
- doublon ;
- compte de destination changé ;
- versement anormal ;
- export massif ;
- opération hors périmètre.

---

# 75. Dossier fraude

Il peut contenir :

- institution ;
- agent ;
- citoyen ;
- opération ;
- montant ;
- règles déclenchées ;
- appareil ;
- localisation ;
- preuves ;
- analyste ;
- décision ;
- statut ;
- actions.

---

# 76. Suspension d’un agent public

Une suspension doit pouvoir être :

- temporaire ;
- limitée à un service ;
- limitée à un appareil ;
- limitée à une zone ;
- totale ;
- programmée ;
- soumise à révision.

Elle doit toujours être auditée.

---

# 77. Incidents

Types :

- financier ;
- technique ;
- sécurité ;
- fraude ;
- agent ;
- institution ;
- paiement ;
- bourse ;
- amende ;
- taxe ;
- carte ;
- intégration ;
- rapprochement.

---

# 78. Intégrations institutionnelles

Le portail doit pouvoir se connecter à :

- registre national ;
- système fiscal ;
- police ;
- université ;
- école ;
- trésor ;
- banque ;
- Mobile Money ;
- système de bourses ;
- système d’identité ;
- système hospitalier ;
- système municipal ;
- ERP public.

Les intégrations dépendent des autorisations officielles.

---

# 79. API

Exemples :

```http
GET    /institutions
GET    /institutions/{id}
GET    /institutions/{id}/services

POST   /public-services/references
GET    /public-services/references/{id}
POST   /public-services/references/{id}/cancel

POST   /public-services/fines
GET    /public-services/fines/{id}
POST   /public-services/fines/{id}/appeals

POST   /public-services/taxes
GET    /public-services/taxes/{id}

POST   /public-services/school-fees
GET    /public-services/students/{id}

POST   /public-services/scholarship-batches
GET    /public-services/scholarship-batches/{id}

GET    /public-services/payments
GET    /public-services/receipts/{id}
POST   /public-services/refunds

GET    /public-services/settlements
GET    /public-services/reconciliation
GET    /public-services/reports
```

---

# 80. Webhooks

Événements possibles :

```text
public_service.reference.created
public_service.reference.paid
public_service.reference.expired
public_service.fine.created
public_service.fine.paid
public_service.appeal.created
public_service.appeal.updated
public_service.tax.paid
public_service.school_fee.paid
public_service.scholarship.paid
public_service.refund.completed
public_service.settlement.completed
```

---

# 81. Administration Mansa

Le portail Admin Mansa doit pouvoir gérer :

- institutions ;
- contrats ;
- produits ;
- services ;
- utilisateurs ;
- rôles ;
- périmètres ;
- appareils ;
- frais ;
- commissions ;
- plafonds ;
- comptes de règlement ;
- intégrations ;
- incidents ;
- audits ;
- pays ;
- versions ;
- maintenances ;
- feature flags.

---

# 82. Administration institutionnelle

L’administrateur institution peut gérer, selon ses droits :

- services ;
- agents ;
- régions ;
- communes ;
- établissements ;
- références ;
- catalogues ;
- tarifs autorisés ;
- rapports ;
- notifications ;
- recours ;
- appareils ;
- exports ;
- paramètres locaux.

---

# 83. Actions critiques

Doivent être protégées :

- modification de tarif ;
- modification de compte de règlement ;
- annulation d’une amende ;
- remboursement ;
- activation d’un agent ;
- suppression d’un service ;
- import de bénéficiaires ;
- paiement de masse ;
- changement de rôle ;
- export massif ;
- modification d’une règle ;
- réactivation après fraude.

---

# 84. Double validation

Peut être exigée pour :

- paiements de masse ;
- remboursements élevés ;
- annulations sensibles ;
- modification de tarif ;
- changement bancaire ;
- création d’un administrateur ;
- modification d’un programme social ;
- import important ;
- activation nationale ;
- réactivation d’un agent suspendu.

---

# 85. Audit

Le journal d’audit doit enregistrer :

- utilisateur ;
- matricule ;
- institution ;
- rôle ;
- action ;
- ressource ;
- ancienne valeur ;
- nouvelle valeur ;
- date ;
- heure ;
- appareil ;
- IP ;
- localisation si autorisée ;
- motif ;
- résultat ;
- approbateur ;
- référence.

---

# 86. Immutabilité des audits

Les audits ne doivent pas être :

- modifiés ;
- supprimés ;
- réécrits ;
- masqués sans trace ;
- exportés sans permission ;
- désactivés par un administrateur local.

---

# 87. Mode hors ligne terrain

Le mode hors ligne peut permettre :

- consulter une liste de missions ;
- préparer une amende ;
- scanner un document ;
- prendre une preuve ;
- générer un brouillon ;
- consulter une procédure.

Il ne doit pas valider librement :

- une amende définitive ;
- un paiement ;
- un remboursement ;
- une annulation ;
- un versement ;
- une modification tarifaire.

---

# 88. Réseau faible

Le système doit prévoir :

- formulaires légers ;
- cache ;
- reprise ;
- compression ;
- synchronisation ;
- files locales ;
- reçus différés ;
- SMS ;
- QR ;
- affichage textuel ;
- statut clair.

---

# 89. Multi-langues

Le portail doit être préparé pour :

- français ;
- bambara ;
- anglais ;
- langues nationales ;
- langues des futurs pays.

Les reçus et notifications doivent être traduisibles.

---

# 90. Multi-pays

Chaque pays peut avoir :

- institutions ;
- devises ;
- langues ;
- hiérarchies ;
- services ;
- règles ;
- taxes ;
- documents ;
- tarifs ;
- procédures de recours ;
- comptes ;
- partenaires ;
- obligations légales.

---

# 91. Sécurité

Mesures principales :

- MFA ;
- RBAC ;
- ABAC ;
- chiffrement ;
- certificats ;
- appareils enregistrés ;
- journaux immuables ;
- contrôle des sessions ;
- géolocalisation encadrée ;
- détection root ;
- protection des preuves ;
- rate limiting ;
- surveillance ;
- révocation à distance.

---

# 92. Modèles

- PublicInstitution
- PublicInstitutionUnit
- PublicInstitutionUser
- PublicInstitutionRole
- PublicInstitutionPermission
- PublicInstitutionDevice
- PublicService
- PublicServiceFeeRule
- PublicPaymentReference
- PublicPayment
- PublicReceipt
- PublicFine
- PublicFineEvidence
- PublicAppeal
- PublicTax
- PublicTaxAssessment
- School
- Student
- SchoolFee
- StudentCard
- ScholarshipProgram
- ScholarshipBeneficiary
- ScholarshipBatch
- SocialProgram
- SocialBenefit
- PublicRefund
- PublicSettlement
- PublicReconciliation
- PublicIncident
- PublicFraudCase
- PublicAudit

---

# 93. Analytics

Événements possibles :

```text
institution_login_completed
institution_service_created
institution_reference_created
institution_payment_completed
institution_fine_created
institution_fine_paid
institution_appeal_created
institution_tax_paid
institution_school_fee_paid
institution_student_card_issued
institution_scholarship_batch_created
institution_scholarship_paid
institution_refund_completed
institution_reconciliation_completed
institution_security_alert_created
```

---

# 94. Données analytics interdites

Ne pas transmettre :

- PIN ;
- OTP ;
- mot de passe ;
- numéro complet de carte ;
- données biométriques ;
- document complet ;
- preuve complète ;
- identité complète inutile ;
- secret ;
- clé privée ;
- données financières non nécessaires.

---

# 95. Tests

- tests d’authentification ;
- tests MFA ;
- tests de rôles ;
- tests de périmètres ;
- tests institutions ;
- tests services ;
- tests références ;
- tests paiements ;
- tests reçus ;
- tests amendes ;
- tests preuves ;
- tests recours ;
- tests taxes ;
- tests paiements partiels ;
- tests scolarité ;
- tests cartes étudiantes ;
- tests bourses ;
- tests doublons ;
- tests paiements de masse ;
- tests remboursements ;
- tests règlements ;
- tests rapprochement ;
- tests fraude ;
- tests appareils ;
- tests hors ligne ;
- tests réseau faible ;
- tests multi-pays ;
- tests multi-langues ;
- tests sécurité ;
- tests audit ;
- tests accessibilité ;
- tests performance.

---

# 96. Règles métier

1. Chaque institution possède un périmètre isolé.
2. Chaque agent utilise un compte nominatif.
3. Les comptes partagés sont interdits.
4. Chaque agent possède un matricule.
5. Les permissions sont vérifiées côté backend.
6. Une opération officielle validée est immuable.
7. Une correction passe par un workflow.
8. Les montants viennent des règles officielles.
9. Les frais ne sont pas codés en dur.
10. Mansa n’invente pas une décision administrative.
11. L’agent créateur ne valide pas seul son propre recours.
12. Les paiements vont vers des comptes officiels.
13. Les comptes personnels des agents sont interdits.
14. Les reçus possèdent une référence unique.
15. Les preuves sont horodatées et hashées.
16. Les audits sont immuables.
17. Les remboursements nécessitent une justification.
18. Les paiements de masse sont contrôlés.
19. Les doublons de bénéficiaires sont détectés.
20. Les comptes de règlement sont protégés.
21. Les données citoyennes sont limitées.
22. Le mode hors ligne reste limité.
23. Les exports sensibles sont audités.
24. Les agents peuvent être suspendus à distance.
25. Les actions critiques peuvent exiger une double validation.

---

# 97. Critères d’acceptation

Le Portail Institutions et Services Publics Mansa est validé lorsque :

- les institutions peuvent être onboardées ;
- les hiérarchies sont configurables ;
- les agents possèdent des comptes nominatifs ;
- les rôles et périmètres sont appliqués ;
- les services publics peuvent être créés ;
- les références de paiement sont générées ;
- les paiements sont traçables ;
- les reçus officiels sont vérifiables ;
- les amendes peuvent être émises ;
- les paiements sur place sont sécurisés ;
- les paiements sur comptes personnels sont impossibles ;
- les preuves sont protégées ;
- les recours sont gérés ;
- les taxes sont prises en charge ;
- les paiements partiels sont configurables ;
- les frais scolaires sont gérés ;
- les cartes étudiantes sont administrables ;
- les bourses peuvent être versées ;
- les doublons sont détectés ;
- les programmes sociaux sont pris en charge ;
- les paiements de masse utilisent un workflow ;
- les remboursements sont contrôlés ;
- les règlements sont visibles ;
- les rapprochements sont automatisés ;
- les rapports sont disponibles ;
- les anomalies sont détectées ;
- les appareils sont administrables ;
- le réseau faible est pris en charge ;
- les audits sont immuables ;
- les actions critiques sont protégées ;
- les tests couvrent les parcours essentiels.
