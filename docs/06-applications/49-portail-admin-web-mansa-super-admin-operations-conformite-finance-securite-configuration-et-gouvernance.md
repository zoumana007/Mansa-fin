# 49 — Portail Admin Web Mansa : Super Admin, opérations, conformité, finance, sécurité, configuration et gouvernance

## 1. Objet du document

Ce document définit l’architecture officielle du **portail Admin Web Mansa**.

Le portail Admin Web constitue l’outil central de pilotage de l’écosystème Mansa.

Il permet de gérer :

- les utilisateurs ;
- les clients ;
- les commerçants ;
- les agents ;
- les employés ;
- les organisations ;
- les établissements ;
- les cartes ;
- les paiements ;
- les transferts ;
- les dépôts ;
- les retraits ;
- le Cash Network ;
- les TPE ;
- les DAB ;
- les règlements ;
- le ledger ;
- les frais ;
- les commissions ;
- les plafonds ;
- le KYC ;
- le KYB ;
- la conformité ;
- la fraude ;
- les risques ;
- les litiges ;
- les remboursements ;
- les services publics ;
- le Hub ;
- le site officiel ;
- les applications ;
- les versions ;
- les campagnes ;
- les notifications ;
- Jini ;
- le support ;
- les incidents ;
- les rapports ;
- les audits ;
- les configurations ;
- les pays ;
- les devises ;
- les partenaires ;
- les permissions ;
- les validations ;
- la sécurité ;
- l’infrastructure ;
- les sauvegardes ;
- les opérations quotidiennes.

L’objectif est de fournir une plateforme centrale :

- sécurisée ;
- modulaire ;
- traçable ;
- multi-pays ;
- multi-organisation ;
- multi-rôle ;
- entièrement administrable ;
- adaptée aux opérations financières critiques ;
- utilisable par les équipes internes et certains partenaires autorisés ;
- capable de contrôler l’ensemble des produits Mansa.

---

# 2. Principes fondamentaux

## 2.1 Le portail Admin est la plateforme centrale de gouvernance

Le portail doit permettre de superviser l’ensemble des applications et services Mansa sans regrouper toutes les responsabilités dans un seul compte.

Il doit appliquer :

- séparation des rôles ;
- séparation des environnements ;
- séparation des pays ;
- séparation des organisations ;
- moindre privilège ;
- approbations ;
- audit ;
- traçabilité.

---

## 2.2 Le Super Admin ne doit pas être utilisé au quotidien

Le rôle Super Admin doit rester :

- rare ;
- protégé ;
- fortement authentifié ;
- surveillé ;
- réservé aux opérations exceptionnelles ;
- limité à des utilisateurs explicitement approuvés.

Les tâches quotidiennes doivent être effectuées avec des rôles spécialisés.

---

## 2.3 Rien de critique ne doit être modifié silencieusement

Toute modification importante doit enregistrer :

- auteur ;
- rôle ;
- date ;
- heure ;
- ancienne valeur ;
- nouvelle valeur ;
- motif ;
- approbateur ;
- pays ;
- environnement ;
- ressource ;
- résultat.

---

## 2.4 Les règles doivent être administrables

Le portail doit permettre de configurer sans modification du code :

- frais ;
- commissions ;
- plafonds ;
- statuts ;
- workflows ;
- règles de risque ;
- rôles ;
- permissions ;
- produits ;
- fonctionnalités ;
- menus ;
- pays ;
- devises ;
- langues ;
- partenaires ;
- campagnes ;
- notifications ;
- versions ;
- maintenances.

---

## 2.5 Le portail ne doit jamais contourner le ledger

Une action administrative ne doit pas modifier directement un solde officiel.

Toute correction financière doit passer par :

- un workflow ;
- une écriture comptable ;
- une justification ;
- une approbation ;
- une référence ;
- un audit ;
- un rapprochement.

---

# 3. Technologie

Technologie recommandée :

```text
Next.js
TypeScript
```

Composants possibles :

- App Router ;
- rendu serveur ;
- design system ;
- gestion d’état ;
- authentification centralisée ;
- RBAC ;
- ABAC ;
- formulaires dynamiques ;
- tableaux ;
- graphiques ;
- exports ;
- temps réel ;
- feature flags ;
- audit ;
- analytics ;
- notifications internes.

---

# 4. Architecture du projet

Structure recommandée :

```text
src/
├── app/
├── auth/
├── dashboard/
├── users/
├── customers/
├── merchants/
├── agents/
├── organizations/
├── establishments/
├── cards/
├── payments/
├── transfers/
├── cash-network/
├── terminals/
├── atms/
├── ledger/
├── settlements/
├── fees/
├── commissions/
├── limits/
├── kyc/
├── kyb/
├── compliance/
├── fraud/
├── risk/
├── disputes/
├── refunds/
├── public-services/
├── hub/
├── website/
├── applications/
├── releases/
├── campaigns/
├── notifications/
├── jini/
├── support/
├── incidents/
├── infrastructure/
├── reports/
├── audits/
├── configuration/
├── countries/
├── partners/
├── roles/
├── approvals/
├── security/
└── settings/
```

---

# 5. Navigation principale

Navigation possible :

```text
Tableau de bord
Opérations
Clients
Entreprises
Cash Network
Paiements
Finance
Conformité
Support
Configuration
```

Menu secondaire :

- Cartes ;
- TPE ;
- DAB ;
- Ledger ;
- Règlements ;
- Frais ;
- Commissions ;
- Risque ;
- Fraude ;
- Litiges ;
- Services publics ;
- Hub ;
- Applications ;
- Site web ;
- Jini ;
- Rapports ;
- Audit ;
- Sécurité ;
- Infrastructure.

La navigation doit être générée selon les permissions.

---

# 6. Tableau de bord global

Le tableau de bord peut afficher :

- utilisateurs actifs ;
- nouveaux comptes ;
- paiements ;
- transferts ;
- dépôts ;
- retraits ;
- volume total ;
- transactions échouées ;
- incidents ;
- alertes fraude ;
- agents actifs ;
- commerçants actifs ;
- TPE actifs ;
- DAB actifs ;
- règlements ;
- rapprochements ;
- disponibilité des services ;
- alertes de sécurité ;
- pays actifs.

---

# 7. Tableaux de bord spécialisés

Le système doit proposer des vues différentes selon le rôle.

Exemples :

- opérations ;
- finance ;
- conformité ;
- fraude ;
- sécurité ;
- support ;
- Cash Network ;
- TPE ;
- DAB ;
- produit ;
- marketing ;
- direction ;
- infrastructure ;
- pays.

---

# 8. Widgets personnalisables

Un administrateur autorisé peut configurer :

- widgets visibles ;
- ordre ;
- période ;
- pays ;
- devise ;
- segment ;
- seuils ;
- rafraîchissement ;
- filtres ;
- alertes.

---

# 9. Recherche globale

La recherche doit permettre de retrouver :

- utilisateur ;
- compte ;
- téléphone ;
- e-mail ;
- commerçant ;
- agent ;
- organisation ;
- carte ;
- transaction ;
- transfert ;
- dépôt ;
- retrait ;
- TPE ;
- DAB ;
- incident ;
- ticket ;
- règlement ;
- facture ;
- référence ;
- partenaire.

---

# 10. Recherche sécurisée

Les résultats doivent être filtrés selon :

- rôle ;
- permission ;
- pays ;
- organisation ;
- environnement ;
- sensibilité ;
- périmètre ;
- besoin opérationnel.

---

# 11. Gestion des utilisateurs internes

Le portail doit permettre :

- création ;
- invitation ;
- activation ;
- suspension ;
- révocation ;
- changement de rôle ;
- changement de périmètre ;
- réinitialisation MFA ;
- gestion des appareils ;
- expiration d’accès ;
- consultation d’activité.

---

# 12. Types d’utilisateurs internes

Exemples :

- Super Admin ;
- Admin plateforme ;
- Admin pays ;
- Admin opérations ;
- Admin finance ;
- Admin conformité ;
- Analyste fraude ;
- Support ;
- Technicien ;
- Auditeur ;
- Responsable produit ;
- Responsable marketing ;
- Partenaire bancaire ;
- Institution publique ;
- Observateur.

---

# 13. RBAC

Le système doit utiliser un contrôle d’accès par rôles.

Exemples :

```text
SUPER_ADMIN
PLATFORM_ADMIN
COUNTRY_ADMIN
OPERATIONS_ADMIN
FINANCE_ADMIN
COMPLIANCE_ADMIN
FRAUD_ANALYST
SUPPORT_AGENT
SECURITY_ADMIN
INFRASTRUCTURE_ADMIN
AUDITOR
PARTNER_VIEWER
```

---

# 14. ABAC

Des règles contextuelles peuvent compléter le RBAC.

Exemples :

- pays ;
- environnement ;
- montant ;
- type de ressource ;
- niveau de risque ;
- heure ;
- appareil ;
- mission ;
- partenaire ;
- organisation ;
- statut.

---

# 15. Périmètre d’un administrateur

Un administrateur peut être limité à :

- un pays ;
- une région ;
- une ville ;
- une organisation ;
- un établissement ;
- un partenaire ;
- un produit ;
- un type d’opération ;
- un environnement ;
- une période ;
- un niveau de montant.

---

# 16. Authentification

Méthodes possibles :

- mot de passe fort ;
- passkey ;
- MFA ;
- clé de sécurité ;
- biométrie système ;
- SSO ;
- identité fédérée ;
- certificat ;
- accès temporaire.

---

# 17. MFA obligatoire

Le MFA doit être obligatoire pour :

- tous les administrateurs ;
- tous les accès production ;
- tous les rôles sensibles ;
- tous les accès partenaires critiques ;
- toutes les actions financières importantes.

---

# 18. Gestion des sessions

La session doit gérer :

- durée ;
- inactivité ;
- appareil ;
- pays ;
- adresse IP ;
- risque ;
- renouvellement ;
- révocation ;
- verrouillage ;
- accès simultanés ;
- réauthentification.

---

# 19. Réauthentification

Une réauthentification peut être exigée pour :

- remboursement ;
- correction financière ;
- changement de compte bancaire ;
- rotation de clé ;
- export massif ;
- accès à une donnée sensible ;
- modification de permission ;
- activation d’un pays ;
- déploiement production.

---

# 20. Gestion des clients

Le portail peut permettre :

- recherche ;
- consultation ;
- statut ;
- KYC ;
- wallets ;
- cartes ;
- appareils ;
- limites ;
- transactions ;
- tickets ;
- litiges ;
- fraude ;
- restrictions ;
- documents ;
- historique.

---

# 21. Protection des données client

Les données doivent être masquées selon le rôle.

Exemples :

- téléphone partiel ;
- e-mail partiel ;
- carte masquée ;
- solde masqué ;
- documents floutés ;
- adresse limitée ;
- historique réduit.

---

# 22. Actions sur un client

Selon permission :

- demander un complément KYC ;
- limiter un compte ;
- suspendre une fonctionnalité ;
- révoquer une session ;
- bloquer une carte ;
- modifier un plafond via workflow ;
- ouvrir un incident ;
- ouvrir un dossier fraude ;
- créer un ticket ;
- demander une réactivation.

---

# 23. Actions interdites directes

Un administrateur ne doit pas pouvoir librement :

- modifier le solde ;
- créer de l’argent ;
- effacer une transaction ;
- modifier une écriture ledger ;
- connaître un PIN ;
- connaître un CVV ;
- lire un OTP ;
- désactiver un audit ;
- effacer une preuve.

---

# 24. Gestion des commerçants

Le portail doit permettre :

- onboarding ;
- KYB ;
- établissements ;
- bénéficiaires effectifs ;
- employés ;
- TPE ;
- règlements ;
- abonnements ;
- catalogues ;
- litiges ;
- incidents ;
- rapports ;
- suspension ;
- réactivation.

---

# 25. Gestion des agents

Le portail doit permettre :

- onboarding ;
- KYC/KYB ;
- points de service ;
- appareils ;
- employés ;
- float ;
- caisse ;
- commissions ;
- plafonds ;
- liquidité ;
- incidents ;
- audits ;
- suspension ;
- réactivation.

---

# 26. Gestion du Cash Network

Le portail doit afficher :

- agents actifs ;
- dépôts ;
- retraits ;
- positions de float ;
- caisse déclarée ;
- liquidité ;
- demandes ;
- rééquilibrages ;
- commissions ;
- anomalies ;
- incidents ;
- cartes de couverture ;
- performances par zone.

---

# 27. Gestion des TPE

Le portail doit permettre :

- inventaire ;
- affectation ;
- activation ;
- suspension ;
- certificat ;
- version ;
- diagnostic ;
- mises à jour ;
- paiements ;
- incidents ;
- remplacement ;
- récupération ;
- historique.

---

# 28. Gestion des DAB

Le portail doit permettre :

- inventaire ;
- statut ;
- emplacement ;
- cassettes ;
- billets ;
- capacité ;
- alertes ;
- maintenance ;
- réapprovisionnement ;
- incidents ;
- transactions ;
- disponibilité ;
- journaux techniques.

---

# 29. Gestion des cartes

Le portail doit permettre :

- émission ;
- activation ;
- suspension ;
- remplacement ;
- opposition ;
- plafonds ;
- règles ;
- réseau ;
- pays ;
- statut ;
- cycle de vie ;
- incidents ;
- fraude ;
- provisioning Wallet.

---

# 30. Gestion des paiements

L’écran Paiements doit afficher :

- référence ;
- utilisateur ;
- commerce ;
- canal ;
- montant ;
- frais ;
- devise ;
- statut ;
- risque ;
- date ;
- partenaire ;
- règlement ;
- ledger ;
- remboursement ;
- litige.

---

# 31. Gestion des transferts

Le portail doit distinguer :

- interne ;
- bancaire ;
- Mobile Money ;
- international ;
- programmé ;
- masse ;
- service public ;
- partenaire.

---

# 32. Gestion des remboursements

Le portail doit permettre :

- demande ;
- analyse ;
- approbation ;
- rejet ;
- exécution ;
- suivi ;
- preuve ;
- rapprochement ;
- audit.

---

# 33. Gestion des litiges

Un dossier peut contenir :

- transaction ;
- client ;
- commerce ;
- motif ;
- preuve ;
- montant ;
- statut ;
- délai ;
- responsable ;
- décision ;
- recours ;
- historique.

---

# 34. Ledger

Le portail financier doit permettre en lecture contrôlée :

- comptes ;
- écritures ;
- journaux ;
- soldes ;
- références ;
- événements ;
- rapprochements ;
- suspenses ;
- corrections ;
- rapports.

---

# 35. Correction financière

Toute correction doit passer par :

1. demande ;
2. justification ;
3. preuve ;
4. simulation ;
5. approbation ;
6. écriture compensatrice ;
7. contrôle ;
8. audit ;
9. rapprochement.

---

# 36. Règlements

Le portail doit gérer :

- commerçants ;
- agents ;
- partenaires ;
- banques ;
- Mobile Money ;
- institutions ;
- calendriers ;
- réserves ;
- frais ;
- montants nets ;
- statuts ;
- rapprochements ;
- échecs.

---

# 37. Frais

L’administration peut créer des règles pour :

- dépôt ;
- retrait ;
- transfert ;
- paiement ;
- carte ;
- TPE ;
- Mobile Money ;
- banque ;
- change ;
- abonnement ;
- service public ;
- partenaire.

---

# 38. Commissions

Le portail doit gérer :

- commission agent ;
- commission commerçant ;
- commission banque ;
- commission Mansa ;
- commission DAB ;
- commission opérateur ;
- commission superviseur ;
- commission partenaire ;
- taxes.

---

# 39. Formules tarifaires

Types :

- fixe ;
- pourcentage ;
- fixe + pourcentage ;
- palier ;
- seuil ;
- minimum ;
- maximum ;
- volume ;
- promotion ;
- gratuité ;
- subvention.

---

# 40. Simulation tarifaire

Avant activation, l’administrateur doit pouvoir simuler :

- montant ;
- pays ;
- canal ;
- client ;
- agent ;
- commerce ;
- partenaire ;
- date ;
- heure ;
- résultat ;
- répartition.

---

# 41. Versionnement des règles

Chaque règle doit avoir :

- version ;
- statut ;
- date de création ;
- date d’effet ;
- date d’expiration ;
- auteur ;
- approbateur ;
- périmètre ;
- historique.

---

# 42. Plafonds

Le portail doit gérer :

- plafonds utilisateur ;
- plafonds carte ;
- plafonds agent ;
- plafonds TPE ;
- plafonds DAB ;
- plafonds commerçant ;
- plafonds par opération ;
- plafonds journaliers ;
- plafonds mensuels ;
- plafonds offline.

---

# 43. KYC

Le portail conformité doit permettre :

- revue ;
- validation ;
- rejet ;
- complément ;
- comparaison ;
- documents ;
- selfie ;
- preuve de vie ;
- sanctions ;
- PEP ;
- historique ;
- score de risque.

---

# 44. KYB

Le portail doit gérer :

- entreprise ;
- registre ;
- fiscalité ;
- dirigeants ;
- bénéficiaires effectifs ;
- établissement ;
- banque ;
- activité ;
- documents ;
- risque ;
- contrôle terrain ;
- décision.

---

# 45. Conformité

Fonctions possibles :

- KYC ;
- KYB ;
- AML ;
- sanctions ;
- PEP ;
- surveillance ;
- rapports ;
- dossiers ;
- conservation ;
- demandes officielles ;
- blocages ;
- escalades.

---

# 46. Fraude

Le portail fraude doit afficher :

- alertes ;
- score ;
- règles déclenchées ;
- transactions ;
- appareils ;
- localisation ;
- relations ;
- historique ;
- analyste ;
- décision ;
- action.

---

# 47. Cas fraude

Statuts possibles :

- OPEN ;
- ASSIGNED ;
- INVESTIGATING ;
- INFORMATION_REQUIRED ;
- ACTION_REQUIRED ;
- CONFIRMED ;
- FALSE_POSITIVE ;
- CLOSED ;
- ESCALATED.

---

# 48. Actions fraude

Selon permission :

- geler une carte ;
- bloquer un canal ;
- limiter un compte ;
- révoquer une session ;
- suspendre un agent ;
- suspendre un TPE ;
- ouvrir un litige ;
- demander un contrôle ;
- transmettre à la conformité.

---

# 49. Services publics

Le portail doit permettre de gérer :

- institutions ;
- agents publics ;
- amendes ;
- taxes ;
- frais scolaires ;
- universités ;
- bourses ;
- cartes étudiantes ;
- factures ;
- références ;
- paiements ;
- reçus ;
- audits ;
- recours ;
- rapports.

---

# 50. Hub et Annuaire

Le portail doit permettre :

- gestion des catégories ;
- validation des profils ;
- badges ;
- avis ;
- signalements ;
- mini-sites ;
- campagnes ;
- abonnements ;
- promotions ;
- classement ;
- événements ;
- services publics ;
- modération.

---

# 51. Site officiel

Le portail doit gérer :

- pages ;
- textes ;
- médias ;
- partenaires ;
- chiffres ;
- tarifs ;
- formulaires ;
- articles ;
- emplois ;
- SEO ;
- redirections ;
- documents légaux ;
- bannières ;
- maintenance.

---

# 52. Applications

Le portail doit gérer :

- application Client ;
- Agent ;
- Commerce ;
- TPE ;
- Admin Lite ;
- Hub ;
- site web ;
- versions ;
- builds ;
- disponibilité ;
- pays ;
- maintenance ;
- versions minimales ;
- mises à jour obligatoires.

---

# 53. Feature Flags

Une fonctionnalité peut être activée selon :

- application ;
- pays ;
- organisation ;
- utilisateur ;
- segment ;
- version ;
- environnement ;
- pourcentage ;
- partenaire ;
- appareil.

---

# 54. Campagnes

Le portail doit gérer :

- marketing ;
- promotions ;
- cashback ;
- frais réduits ;
- commissions renforcées ;
- notifications ;
- ciblage ;
- budget ;
- période ;
- pays ;
- résultats.

---

# 55. Notifications

Le portail doit permettre de créer :

- Push ;
- SMS ;
- e-mail ;
- notification interne ;
- bannière ;
- alerte sécurité ;
- message transactionnel ;
- campagne ;
- rappel.

---

# 56. Modèles de notification

Chaque modèle doit avoir :

- code ;
- canal ;
- langue ;
- pays ;
- variables ;
- version ;
- statut ;
- contenu ;
- validation ;
- test ;
- historique.

---

# 57. Jini

Le portail doit permettre de gérer :

- fonctionnalités ;
- permissions ;
- sources ;
- réponses ;
- limites ;
- outils ;
- modèles ;
- prompts système ;
- incidents ;
- évaluations ;
- analytics ;
- activation par pays.

---

# 58. Actions Jini sensibles

Jini ne doit pas exécuter sans workflow :

- remboursement ;
- modification de solde ;
- changement de frais ;
- changement de rôle ;
- suspension définitive ;
- suppression de preuve ;
- modification ledger ;
- accès à un secret.

---

# 59. Support

Le portail support doit permettre :

- tickets ;
- files ;
- priorités ;
- catégories ;
- SLA ;
- utilisateurs ;
- transactions ;
- pièces jointes ;
- réponses ;
- escalades ;
- satisfaction ;
- rapports.

---

# 60. Vue client 360

Le support peut disposer d’une vue limitée regroupant :

- identité masquée ;
- statut ;
- dernières opérations utiles ;
- tickets ;
- appareil ;
- incidents ;
- KYC ;
- cartes ;
- communications.

L’accès doit être journalisé.

---

# 61. Incidents

Le portail doit gérer :

- incident technique ;
- incident financier ;
- fraude ;
- sécurité ;
- partenaire ;
- TPE ;
- DAB ;
- agent ;
- commerce ;
- service public ;
- infrastructure.

---

# 62. Gestion d’incident

Chaque incident doit contenir :

- référence ;
- gravité ;
- impact ;
- pays ;
- service ;
- début ;
- responsable ;
- participants ;
- chronologie ;
- actions ;
- communications ;
- résolution ;
- post-mortem.

---

# 63. Infrastructure

Le portail technique peut afficher :

- environnements ;
- services ;
- versions ;
- déploiements ;
- santé ;
- bases ;
- files ;
- certificats ;
- sauvegardes ;
- coûts ;
- alertes ;
- incidents ;
- capacité.

Les modifications sensibles doivent rester contrôlées.

---

# 64. Rapports

Rapports possibles :

- finance ;
- paiements ;
- transferts ;
- Cash Network ;
- agents ;
- commerçants ;
- TPE ;
- DAB ;
- fraude ;
- conformité ;
- support ;
- services publics ;
- campagnes ;
- infrastructure ;
- revenus ;
- commissions ;
- pays.

---

# 65. Exports

Formats possibles :

- CSV ;
- XLSX ;
- PDF ;
- JSON ;
- impression ;
- API.

Les exports doivent appliquer :

- permissions ;
- masquage ;
- limite ;
- chiffrement ;
- expiration ;
- audit ;
- justification.

---

# 66. Rapports programmés

Un rapport peut être envoyé :

- quotidiennement ;
- chaque semaine ;
- chaque mois ;
- à une date ;
- après clôture ;
- après incident ;
- après rapprochement.

---

# 67. Approvals Center

Le portail doit centraliser les demandes d’approbation.

Exemples :

- remboursement ;
- correction financière ;
- augmentation de plafond ;
- changement bancaire ;
- activation agent ;
- activation pays ;
- frais ;
- commissions ;
- déploiement ;
- export massif ;
- accès exceptionnel.

---

# 68. Statuts d’approbation

- DRAFT ;
- SUBMITTED ;
- PENDING ;
- APPROVED ;
- REJECTED ;
- EXPIRED ;
- CANCELLED ;
- EXECUTED ;
- FAILED.

---

# 69. Double validation

Peut être exigée selon :

- montant ;
- type d’action ;
- pays ;
- environnement ;
- rôle ;
- risque ;
- partenaire ;
- ressource.

---

# 70. Séparation demandeur-validateur

Le demandeur ne doit pas pouvoir approuver seul sa propre demande pour une action critique.

---

# 71. Audit

Le portail doit offrir un journal central contenant :

- acteur ;
- rôle ;
- action ;
- ressource ;
- ancienne valeur ;
- nouvelle valeur ;
- date ;
- heure ;
- IP ;
- appareil ;
- pays ;
- environnement ;
- résultat ;
- motif ;
- corrélation.

---

# 72. Immutabilité des audits

Les audits ne doivent pas être :

- modifiés ;
- supprimés ;
- masqués sans trace ;
- réécrits ;
- exportés sans permission.

---

# 73. Alertes de sécurité

Exemples :

- connexion inhabituelle ;
- échec MFA ;
- export massif ;
- changement de rôle ;
- accès sensible ;
- modification tarifaire ;
- correction financière ;
- session compromise ;
- accès hors pays ;
- suppression tentée.

---

# 74. Appareils administrateurs

Chaque appareil doit avoir :

- utilisateur ;
- modèle ;
- OS ;
- navigateur ;
- certificat ;
- dernière activité ;
- pays ;
- IP ;
- statut ;
- confiance ;
- révocation.

---

# 75. Accès d’urgence

Un accès d’urgence doit être :

- temporaire ;
- justifié ;
- approuvé ;
- limité ;
- surveillé ;
- enregistré ;
- révoqué automatiquement ;
- revu après utilisation.

---

# 76. Mode lecture seule

Le portail doit pouvoir être placé en lecture seule pour :

- maintenance ;
- incident ;
- audit ;
- migration ;
- sécurité ;
- partenaire ;
- pays ;
- module.

---

# 77. Maintenance

Le portail doit permettre :

- maintenance globale ;
- maintenance par pays ;
- maintenance par service ;
- maintenance partenaire ;
- maintenance application ;
- message utilisateur ;
- date ;
- impact ;
- alternative ;
- fin estimée.

---

# 78. Multi-pays

Chaque pays doit pouvoir avoir :

- administrateurs ;
- rôles ;
- devise ;
- langue ;
- partenaires ;
- tarifs ;
- plafonds ;
- conformité ;
- services ;
- rapports ;
- infrastructure ;
- documents légaux ;
- règles fiscales.

---

# 79. Isolation pays

Un administrateur pays ne doit pas accéder aux données d’un autre pays sans permission explicite.

---

# 80. Multi-environnements

Le portail doit distinguer clairement :

- développement ;
- test ;
- démo ;
- staging ;
- préproduction ;
- production.

Le design doit empêcher la confusion entre les environnements.

---

# 81. Indicateur d’environnement

Chaque page doit afficher visiblement :

- environnement ;
- pays ;
- organisation ;
- rôle actif ;
- périmètre.

---

# 82. Configuration globale

Le portail doit gérer :

- pays ;
- régions ;
- villes ;
- devises ;
- langues ;
- fuseaux horaires ;
- formats ;
- jours fériés ;
- partenaires ;
- produits ;
- canaux ;
- statuts ;
- catégories ;
- règles.

---

# 83. Import de configuration

Les imports doivent être :

- validés ;
- simulés ;
- comparés ;
- approuvés ;
- versionnés ;
- annulables lorsque possible ;
- audités.

---

# 84. API Admin

Exemples :

```http
GET    /admin/dashboard
GET    /admin/search

GET    /admin/users
POST   /admin/users
PATCH  /admin/users/{id}

GET    /admin/customers
GET    /admin/customers/{id}
POST   /admin/customers/{id}/restriction-requests

GET    /admin/merchants
GET    /admin/agents
GET    /admin/terminals
GET    /admin/atms

GET    /admin/payments
GET    /admin/transfers
GET    /admin/ledger
GET    /admin/settlements

GET    /admin/fee-rules
POST   /admin/fee-rules
POST   /admin/fee-rules/{id}/publish

GET    /admin/approvals
POST   /admin/approvals/{id}/approve
POST   /admin/approvals/{id}/reject

GET    /admin/audits
GET    /admin/reports
POST   /admin/exports
```

---

# 85. Permissions

Exemples :

```text
admin.dashboard.read
admin.search.use
admin.user.read
admin.user.manage
admin.customer.read
admin.customer.restrict
admin.merchant.read
admin.merchant.manage
admin.agent.read
admin.agent.manage
admin.payment.read
admin.payment.refund
admin.ledger.read
admin.ledger.adjustment.request
admin.fee.read
admin.fee.manage
admin.commission.manage
admin.limit.manage
admin.kyc.review
admin.kyb.review
admin.fraud.read
admin.fraud.manage
admin.support.manage
admin.report.read
admin.export.create
admin.approval.execute
admin.audit.read
admin.security.manage
admin.configuration.manage
```

---

# 86. Actions critiques

Doivent être particulièrement protégées :

- modification de frais ;
- modification de commission ;
- modification de plafond ;
- correction financière ;
- remboursement élevé ;
- activation pays ;
- changement bancaire ;
- changement de rôle ;
- accès production ;
- export massif ;
- suppression de ressource ;
- rotation de secret ;
- publication légale ;
- modification du ledger ;
- réactivation après fraude.

---

# 87. Modèles

- AdminUser
- AdminRole
- AdminPermission
- AdminScope
- AdminSession
- AdminDevice
- AdminAction
- AdminApproval
- AdminApprovalStep
- AdminDashboard
- AdminWidget
- AdminSavedView
- AdminExport
- AdminReport
- AdminAlert
- AdminIncident
- AdminSecurityEvent
- AdminConfiguration
- AdminFeatureFlag
- AdminMaintenance
- AdminAudit

---

# 88. Analytics

Événements possibles :

```text
admin_login_completed
admin_dashboard_opened
admin_search_completed
admin_customer_opened
admin_merchant_opened
admin_agent_opened
admin_payment_opened
admin_refund_requested
admin_fee_rule_created
admin_fee_rule_published
admin_limit_changed
admin_kyc_review_completed
admin_fraud_case_opened
admin_approval_submitted
admin_approval_completed
admin_export_created
admin_security_alert_created
admin_session_revoked
```

---

# 89. Données analytics interdites

Ne pas transmettre :

- mot de passe ;
- OTP ;
- PIN ;
- CVV ;
- numéro complet de carte ;
- secret ;
- document complet ;
- clé privée ;
- données biométriques ;
- contenu confidentiel ;
- détails financiers non nécessaires.

---

# 90. Tests

- tests d’authentification ;
- tests MFA ;
- tests SSO ;
- tests RBAC ;
- tests ABAC ;
- tests de périmètre ;
- tests multi-pays ;
- tests multi-tenant ;
- tests de recherche ;
- tests clients ;
- tests commerçants ;
- tests agents ;
- tests Cash Network ;
- tests TPE ;
- tests DAB ;
- tests cartes ;
- tests paiements ;
- tests transferts ;
- tests remboursements ;
- tests ledger ;
- tests règlements ;
- tests frais ;
- tests commissions ;
- tests plafonds ;
- tests KYC ;
- tests KYB ;
- tests fraude ;
- tests litiges ;
- tests support ;
- tests approbations ;
- tests exports ;
- tests audit ;
- tests sécurité ;
- tests infrastructure ;
- tests d’accessibilité ;
- tests de performance.

---

# 91. Règles métier

1. Le portail Admin est protégé par MFA.
2. Le Super Admin reste exceptionnel.
3. Chaque administrateur possède un rôle.
4. Chaque administrateur possède un périmètre.
5. Les données sont filtrées par pays et tenant.
6. Les permissions sont vérifiées côté backend.
7. Les actions critiques nécessitent une justification.
8. Le demandeur ne valide pas seul sa propre demande critique.
9. Les modifications sont historisées.
10. Les audits sont immuables.
11. Les secrets ne sont jamais affichés.
12. Les données sensibles sont masquées.
13. Les corrections financières passent par le ledger.
14. Les soldes ne sont jamais modifiés directement.
15. Les règles tarifaires sont versionnées.
16. Les frais sont administrables.
17. Les commissions sont administrables.
18. Les plafonds sont administrables.
19. Les environnements sont clairement séparés.
20. Les accès d’urgence sont temporaires.
21. Les exports sensibles sont audités.
22. Les sessions peuvent être révoquées.
23. Les actions partenaires sont limitées.
24. Les applications sont pilotées par feature flags.
25. Les actions critiques peuvent exiger une double validation.

---

# 92. Critères d’acceptation

Le portail Admin Web Mansa est validé lorsque :

- les administrateurs peuvent se connecter avec MFA ;
- les rôles sont configurables ;
- les permissions sont appliquées ;
- les périmètres géographiques sont respectés ;
- les clients sont administrables selon les droits ;
- les commerçants sont administrables ;
- les agents sont administrables ;
- le Cash Network est supervisé ;
- les TPE sont gérés ;
- les DAB sont gérés ;
- les cartes sont administrables ;
- les paiements et transferts sont consultables ;
- les remboursements utilisent un workflow ;
- le ledger est consultable de manière sécurisée ;
- les corrections financières sont contrôlées ;
- les frais et commissions sont dynamiques ;
- les plafonds sont configurables ;
- le KYC et le KYB sont intégrés ;
- les cas fraude sont gérés ;
- les litiges sont suivis ;
- les règlements sont visibles ;
- les services publics sont administrables ;
- le Hub et le site officiel sont administrables ;
- les applications et versions sont pilotées ;
- les notifications sont configurables ;
- Jini est administrable ;
- le support est intégré ;
- les incidents sont suivis ;
- les rapports et exports sont disponibles ;
- les approbations sont centralisées ;
- les audits sont immuables ;
- les actions critiques sont protégées ;
- les tests couvrent les parcours essentiels.
