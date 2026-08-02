# 31 — KYC, KYB, AML, sanctions et conformité globale de Mansa

## 1. Objet du document

Ce document définit l’architecture officielle de conformité de Mansa.

Il couvre :

- le KYC des particuliers ;
- le KYB des commerçants et organisations ;
- l’identification des bénéficiaires effectifs ;
- la vérification documentaire ;
- la preuve de vie ;
- les niveaux de vérification ;
- la lutte contre le blanchiment ;
- le financement du terrorisme ;
- les sanctions ;
- les personnes politiquement exposées ;
- les listes de surveillance ;
- la surveillance transactionnelle ;
- les alertes ;
- les dossiers de conformité ;
- les revues manuelles ;
- les déclarations réglementaires ;
- la conservation des preuves ;
- les obligations multi-pays ;
- la gestion des partenaires de conformité ;
- les règles d’administration ;
- l’audit.

L’objectif est de permettre à Mansa de :

- identifier correctement ses utilisateurs et partenaires ;
- appliquer des niveaux de service adaptés au risque ;
- prévenir les usages illicites ;
- détecter les opérations suspectes ;
- respecter les obligations applicables ;
- protéger les utilisateurs légitimes ;
- conserver une traçabilité complète ;
- adapter les contrôles à chaque pays ;
- éviter les blocages injustifiés ;
- permettre des décisions explicables et révisables.

---

# 2. Principes fondamentaux

## 2.1 Approche fondée sur le risque

Les contrôles doivent être proportionnés au risque.

Le niveau de contrôle peut dépendre de :

- pays ;
- profil ;
- activité ;
- montant ;
- fréquence ;
- canal ;
- produit ;
- partenaire ;
- bénéficiaire ;
- historique ;
- appareil ;
- localisation ;
- statut de conformité.

---

## 2.2 Aucun accès financier important sans niveau de vérification suffisant

Les services sensibles doivent être conditionnés à un niveau KYC ou KYB défini.

Exemples :

- plafonds élevés ;
- cartes physiques ;
- paiements internationaux ;
- retraits importants ;
- règlement commerçant ;
- accès partenaire ;
- services publics ;
- produits d’investissement.

---

## 2.3 Les décisions doivent être traçables

Toute décision doit pouvoir indiquer :

- données utilisées ;
- règle appliquée ;
- fournisseur éventuel ;
- score ;
- version ;
- résultat ;
- auteur ;
- date ;
- motif ;
- possibilité de recours ;
- historique des modifications.

---

## 2.4 Les contrôles automatisés ne remplacent pas toujours la revue humaine

Une revue manuelle doit être possible lorsque :

- le document est ambigu ;
- le score est intermédiaire ;
- une sanction potentielle est détectée ;
- un PEP est identifié ;
- les données sont incohérentes ;
- une activité inhabituelle apparaît ;
- un faux positif est probable ;
- une décision importante doit être confirmée.

---

## 2.5 Les données sont minimisées

Mansa ne doit demander que les données nécessaires au niveau de service et aux obligations applicables.

---

# 3. Périmètre des personnes concernées

Les processus de conformité peuvent concerner :

- particuliers ;
- commerçants individuels ;
- sociétés ;
- associations ;
- administrations ;
- établissements scolaires ;
- agents publics ;
- employés ;
- partenaires ;
- bénéficiaires effectifs ;
- représentants légaux ;
- mandataires ;
- fournisseurs ;
- développeurs utilisant les API.

---

# 4. Niveaux KYC particuliers

Exemple de structure :

## 4.1 Niveau 0 — Non vérifié

Fonctions limitées :

- découverte de l’application ;
- consultation publique ;
- création de compte incomplète ;
- aucun mouvement financier réel.

## 4.2 Niveau 1 — Vérification de base

Éléments possibles :

- téléphone vérifié ;
- identité déclarative ;
- date de naissance ;
- pays ;
- consentements ;
- contrôle minimum.

Fonctions possibles :

- wallet limité ;
- faibles plafonds ;
- paiements simples ;
- transferts limités.

## 4.3 Niveau 2 — Identité vérifiée

Éléments possibles :

- document d’identité ;
- selfie ;
- preuve de vie ;
- vérification documentaire ;
- sanctions ;
- PEP ;
- adresse ou justificatif si requis.

Fonctions possibles :

- plafonds supérieurs ;
- carte ;
- retraits ;
- transferts plus importants ;
- services avancés.

## 4.4 Niveau 3 — Vérification renforcée

Éléments possibles :

- origine des fonds ;
- justificatif de revenus ;
- activité professionnelle ;
- entretien ;
- justificatifs complémentaires ;
- revue manuelle.

Fonctions possibles :

- volumes élevés ;
- produits sensibles ;
- opérations internationales ;
- services professionnels spécifiques.

---

# 5. Niveaux KYB

## 5.1 KYB de base

Éléments possibles :

- nom commercial ;
- activité ;
- adresse ;
- téléphone ;
- représentant ;
- document d’enregistrement ;
- pays ;
- catégorie.

## 5.2 KYB complet

Éléments possibles :

- registre du commerce ;
- numéro fiscal ;
- statuts ;
- bénéficiaires effectifs ;
- dirigeants ;
- compte de règlement ;
- documents d’identité ;
- preuve d’activité ;
- sanctions ;
- PEP ;
- vérification de l’établissement.

## 5.3 KYB renforcé

Éléments possibles :

- structure capitalistique complexe ;
- activité sensible ;
- pays à risque ;
- volumes élevés ;
- contrats ;
- source des fonds ;
- revue juridique ;
- visite ;
- entretien ;
- approbation renforcée.

---

# 6. Bénéficiaires effectifs

Mansa doit pouvoir identifier les personnes contrôlant réellement une organisation.

Le dossier doit contenir :

- identité ;
- pourcentage détenu ;
- type de contrôle ;
- pays ;
- document ;
- statut de vérification ;
- sanctions ;
- PEP ;
- relation avec l’organisation ;
- date de revue.

---

# 7. Représentants légaux et mandataires

Chaque représentant doit avoir :

- identité vérifiée ;
- qualité ;
- mandat ;
- date de début ;
- date de fin ;
- périmètre ;
- preuve ;
- statut ;
- historique.

---

# 8. Données KYC

Exemples :

- nom ;
- prénom ;
- date de naissance ;
- lieu de naissance ;
- nationalité ;
- sexe si nécessaire ;
- adresse ;
- profession ;
- employeur ;
- téléphone ;
- e-mail ;
- document ;
- numéro de document ;
- date d’expiration ;
- pays émetteur ;
- source de fonds ;
- usage prévu.

---

# 9. Documents acceptés

Les documents peuvent inclure :

- passeport ;
- carte nationale ;
- titre de séjour ;
- permis si autorisé ;
- registre du commerce ;
- certificat d’immatriculation ;
- statuts ;
- justificatif d’adresse ;
- attestation fiscale ;
- relevé bancaire ;
- preuve d’activité.

La liste doit être configurable par pays.

---

# 10. Vérification documentaire

La vérification peut contrôler :

- format ;
- lisibilité ;
- expiration ;
- zone MRZ ;
- code-barres ;
- hologramme ;
- cohérence ;
- photo ;
- falsification ;
- capture d’écran ;
- réutilisation ;
- correspondance avec les données saisies.

---

# 11. OCR

L’OCR peut extraire :

- nom ;
- prénom ;
- numéro ;
- date de naissance ;
- date d’expiration ;
- nationalité ;
- pays ;
- sexe ;
- adresse.

Les données extraites doivent être vérifiées et corrigibles.

---

# 12. Selfie et preuve de vie

Le système peut utiliser :

- selfie simple ;
- vidéo ;
- mouvement ;
- challenge ;
- comparaison faciale ;
- détection de présentation.

Les données biométriques doivent être traitées avec un niveau de protection élevé.

---

# 13. Comparaison faciale

La comparaison doit produire :

- score ;
- seuil ;
- fournisseur ;
- version ;
- résultat ;
- date ;
- décision ;
- revue éventuelle.

Une faible confiance ne doit pas entraîner automatiquement une exclusion définitive sans possibilité de revue.

---

# 14. Vérification d’adresse

Méthodes possibles :

- justificatif ;
- relevé ;
- attestation ;
- courrier ;
- géolocalisation lorsque autorisée ;
- vérification partenaire ;
- déclaration renforcée.

---

# 15. Vérification de téléphone

Le numéro peut être vérifié par :

- OTP ;
- appel ;
- SIM check ;
- vérification opérateur ;
- contrôle de portabilité ;
- réputation.

---

# 16. Vérification e-mail

Méthodes possibles :

- lien ;
- OTP ;
- contrôle de domaine ;
- réputation ;
- vérification d’entreprise.

---

# 17. Statuts KYC/KYB

Valeurs possibles :

- NOT_STARTED ;
- IN_PROGRESS ;
- PENDING_REVIEW ;
- ADDITIONAL_INFORMATION_REQUIRED ;
- APPROVED ;
- APPROVED_WITH_LIMITS ;
- REJECTED ;
- EXPIRED ;
- SUSPENDED ;
- UNDER_INVESTIGATION ;
- CLOSED.

---

# 18. Raisons de décision

Les décisions doivent utiliser des codes stables.

Exemples :

```text
DOCUMENT_EXPIRED
DOCUMENT_UNREADABLE
IDENTITY_MISMATCH
SANCTIONS_POTENTIAL_MATCH
PEP_REVIEW_REQUIRED
ADDRESS_MISSING
BENEFICIAL_OWNER_MISSING
SOURCE_OF_FUNDS_REQUIRED
FRAUD_RISK_HIGH
```

---

# 19. Demande de complément

Le système doit permettre de demander :

- nouveau document ;
- photo plus claire ;
- justificatif d’adresse ;
- identité d’un dirigeant ;
- bénéficiaire effectif ;
- origine des fonds ;
- explication d’une transaction ;
- preuve d’activité.

Chaque demande doit contenir :

- motif ;
- date ;
- délai ;
- statut ;
- documents attendus ;
- message utilisateur ;
- responsable ;
- relances.

---

# 20. Expiration

Un dossier peut expirer en raison de :

- document expiré ;
- durée de validité ;
- changement réglementaire ;
- changement d’activité ;
- changement de dirigeant ;
- nouveau risque ;
- absence de mise à jour ;
- partenaire exigeant une revue.

---

# 21. Re-KYC et Re-KYB

Le système doit relancer une vérification selon :

- périodicité ;
- risque ;
- pays ;
- produit ;
- partenaire ;
- événement ;
- changement de données ;
- incident ;
- seuil transactionnel.

---

# 22. Événements déclencheurs

Exemples :

- changement de téléphone ;
- changement d’adresse ;
- nouveau pays ;
- augmentation de plafond ;
- changement d’actionnaire ;
- changement de dirigeant ;
- activité inhabituelle ;
- document expiré ;
- alerte sanctions ;
- opération internationale.

---

# 23. Sanctions

Mansa doit pouvoir filtrer les personnes et organisations contre :

- listes nationales ;
- listes régionales ;
- listes internationales ;
- listes partenaires ;
- listes internes ;
- listes d’interdiction.

---

# 24. Matching des sanctions

Le matching peut considérer :

- nom ;
- alias ;
- date de naissance ;
- nationalité ;
- pays ;
- adresse ;
- document ;
- organisation ;
- translittération ;
- similarité phonétique.

---

# 25. Faux positifs

Un résultat potentiel ne doit pas être automatiquement considéré comme confirmé.

Le dossier doit permettre :

- comparaison ;
- analyse ;
- exclusion ;
- justification ;
- approbation ;
- conservation de la preuve ;
- réouverture si nouvelles données.

---

# 26. Personnes politiquement exposées

Le système doit gérer :

- PEP nationales ;
- PEP étrangères ;
- proches ;
- associés ;
- anciens PEP ;
- durée de surveillance ;
- niveau de risque ;
- approbation renforcée.

Être PEP ne signifie pas automatiquement être interdit.

---

# 27. Adverse Media

Lorsque pertinent, Mansa peut surveiller :

- fraude ;
- corruption ;
- blanchiment ;
- financement illicite ;
- crime organisé ;
- sanctions ;
- escroquerie ;
- abus financier.

Les résultats doivent être vérifiés avant décision.

---

# 28. AML

Le dispositif AML doit couvrir :

- connaissance client ;
- compréhension de l’activité ;
- profil transactionnel ;
- surveillance ;
- détection d’anomalies ;
- alertes ;
- enquêtes ;
- décisions ;
- reporting ;
- conservation.

---

# 29. Profil de risque

Chaque utilisateur ou organisation peut recevoir un profil de risque.

Facteurs possibles :

- pays ;
- activité ;
- produit ;
- volume ;
- fréquence ;
- partenaires ;
- source des fonds ;
- historique ;
- PEP ;
- sanctions ;
- appareil ;
- comportement ;
- bénéficiaires.

---

# 30. Niveaux de risque

Exemple :

- LOW ;
- MEDIUM ;
- HIGH ;
- VERY_HIGH ;
- PROHIBITED.

Le niveau doit être versionné et explicable.

---

# 31. Surveillance transactionnelle

Elle peut analyser :

- montants ;
- fréquence ;
- répétition ;
- fractionnement ;
- contreparties ;
- pays ;
- heure ;
- canal ;
- type de transaction ;
- historique ;
- activité déclarée ;
- relation ;
- appareil ;
- retrait rapide ;
- circulation des fonds.

---

# 32. Typologies d’alerte

Exemples :

- dépôts et retraits rapides ;
- fractionnement ;
- volumes incohérents ;
- nombreuses contreparties ;
- compte dormant devenu actif ;
- activité transfrontalière inhabituelle ;
- utilisation de plusieurs appareils ;
- paiements circulaires ;
- remboursements anormaux ;
- retraits inhabituels ;
- TPE à activité atypique ;
- commerce ne correspondant pas à sa catégorie.

---

# 33. Règles de détection

Chaque règle doit contenir :

- identifiant ;
- description ;
- pays ;
- produit ;
- seuil ;
- fenêtre temporelle ;
- niveau de risque ;
- version ;
- date d’effet ;
- propriétaire ;
- statut ;
- résultat ;
- taux de faux positifs.

---

# 34. Scoring

Un score peut être calculé à partir :

- règles ;
- comportement ;
- historique ;
- partenaire ;
- modèle ;
- listes ;
- profil ;
- pays ;
- données transactionnelles.

Le score ne doit pas être utilisé seul sans gouvernance.

---

# 35. Alertes de conformité

Chaque alerte doit contenir :

- identifiant ;
- type ;
- utilisateur ;
- organisation ;
- transactions ;
- règle ;
- score ;
- date ;
- priorité ;
- statut ;
- analyste ;
- pays ;
- corrélation ;
- pièces ;
- commentaires ;
- décision.

---

# 36. Statuts d’alerte

Valeurs possibles :

- OPEN ;
- ASSIGNED ;
- IN_REVIEW ;
- INFORMATION_REQUIRED ;
- ESCALATED ;
- FALSE_POSITIVE ;
- CONFIRMED ;
- REPORTED ;
- CLOSED ;
- REOPENED.

---

# 37. Dossier de conformité

Un dossier peut regrouper plusieurs alertes.

Il doit contenir :

- personne ;
- organisation ;
- historique ;
- transactions ;
- documents ;
- décisions ;
- analystes ;
- chronologie ;
- communication ;
- actions ;
- restrictions ;
- reporting ;
- audit.

---

# 38. Revue manuelle

L’analyste doit pouvoir :

- consulter le profil ;
- consulter les transactions pertinentes ;
- voir les documents ;
- voir les alertes ;
- demander des informations ;
- ajouter une note ;
- joindre une pièce ;
- escalader ;
- décider ;
- proposer une restriction ;
- clôturer.

---

# 39. Séparation des responsabilités

Les rôles doivent être séparés entre :

- collecte ;
- vérification ;
- analyse ;
- approbation ;
- déclaration ;
- audit ;
- administration des règles.

---

# 40. Restrictions possibles

Selon le risque, Mansa peut :

- réduire un plafond ;
- bloquer une fonction ;
- suspendre les retraits ;
- suspendre les transferts ;
- suspendre une carte ;
- exiger une vérification ;
- mettre une opération en attente ;
- suspendre le compte ;
- clôturer la relation lorsque autorisé.

---

# 41. Restriction ciblée

Une restriction doit être proportionnée.

Exemple :

Il peut être inutile de bloquer tout le compte si seul un partenaire ou un canal est concerné.

---

# 42. Gel

Le gel doit contenir :

- base ;
- autorité ;
- périmètre ;
- montant ;
- devise ;
- date ;
- durée ;
- décisionnaire ;
- audit ;
- statut ;
- levée.

---

# 43. Demande d’explication

Le système doit permettre de demander :

- raison de l’opération ;
- relation avec le bénéficiaire ;
- source des fonds ;
- destination ;
- facture ;
- contrat ;
- justificatif ;
- preuve de livraison.

---

# 44. Déclarations réglementaires

Lorsque requis, Mansa doit pouvoir préparer :

- rapport d’opération suspecte ;
- rapport transactionnel ;
- rapport périodique ;
- déclaration de seuil ;
- réponse à une autorité ;
- gel ;
- suivi d’enquête.

---

# 45. Approbation des déclarations

Une déclaration importante doit être :

- préparée ;
- revue ;
- approuvée ;
- transmise ;
- horodatée ;
- conservée ;
- auditée.

---

# 46. Confidentialité des déclarations

Les informations relatives à une déclaration sensible doivent être accessibles uniquement aux rôles autorisés.

---

# 47. Non-divulgation à la personne concernée

Lorsque les règles applicables l’exigent, certaines informations ne doivent pas être communiquées à la personne concernée.

Les messages doivent rester neutres et validés.

---

# 48. Conservation

Les données KYC, KYB et AML doivent être conservées selon :

- pays ;
- produit ;
- partenaire ;
- contrat ;
- obligations ;
- clôture du compte ;
- litige ;
- enquête ;
- legal hold.

---

# 49. Audit

Les événements suivants doivent être audités :

- soumission ;
- vérification ;
- décision ;
- changement de risque ;
- consultation sensible ;
- téléchargement ;
- demande de complément ;
- restriction ;
- levée ;
- déclaration ;
- modification de règle ;
- export ;
- suppression.

---

# 50. Fournisseurs externes

Les prestataires peuvent fournir :

- OCR ;
- preuve de vie ;
- comparaison faciale ;
- sanctions ;
- PEP ;
- adverse media ;
- KYB ;
- données d’entreprise ;
- scoring ;
- surveillance continue.

---

# 51. Multi-fournisseurs

Mansa doit pouvoir utiliser plusieurs fournisseurs selon :

- pays ;
- disponibilité ;
- coût ;
- qualité ;
- document ;
- langue ;
- conformité ;
- performance ;
- taux d’échec.

---

# 52. Fallback fournisseur

En cas d’indisponibilité :

- mettre le dossier en attente ;
- utiliser un autre fournisseur ;
- lancer une revue manuelle ;
- limiter temporairement les fonctions ;
- informer l’utilisateur ;
- éviter un faux rejet.

---

# 53. Contrôle des fournisseurs

Mesures :

- disponibilité ;
- taux de réussite ;
- taux de faux positifs ;
- latence ;
- coût ;
- erreurs ;
- qualité OCR ;
- qualité biométrique ;
- pays supportés ;
- incidents ;
- conformité contractuelle.

---

# 54. Multi-pays

Chaque pays doit définir :

- documents acceptés ;
- âge minimum ;
- niveaux KYC ;
- seuils ;
- durées ;
- règles AML ;
- listes applicables ;
- exigences KYB ;
- données obligatoires ;
- procédures de recours ;
- partenaires ;
- langue ;
- conservation.

---

# 55. Résidence et nationalité

Le système doit distinguer :

- nationalité ;
- pays de résidence ;
- pays d’activité ;
- pays du document ;
- pays d’inscription ;
- pays de transaction.

---

# 56. Profil attendu

Lors de l’entrée en relation, le système peut collecter :

- usage prévu ;
- montant mensuel estimé ;
- fréquence ;
- source de fonds ;
- destination ;
- profession ;
- activité ;
- pays concernés ;
- produits souhaités.

---

# 57. Cohérence du profil

La surveillance doit comparer l’activité réelle au profil attendu.

Une différence importante peut déclencher :

- alerte ;
- demande d’information ;
- revue ;
- mise à jour du profil ;
- restriction temporaire.

---

# 58. KYC simplifié

Un KYC simplifié peut être autorisé lorsque :

- le risque est faible ;
- les plafonds sont bas ;
- le produit est limité ;
- le pays l’autorise ;
- aucun signal élevé n’est détecté.

---

# 59. Vigilance renforcée

Elle peut être exigée pour :

- pays à risque ;
- PEP ;
- activité sensible ;
- structure complexe ;
- volume élevé ;
- bénéficiaire inhabituel ;
- origine de fonds difficile à vérifier ;
- correspondance potentielle ;
- incident précédent.

---

# 60. Activités sensibles

Exemples possibles selon la politique :

- change ;
- transfert d’argent ;
- jeux ;
- cryptoactifs ;
- métaux précieux ;
- immobilier ;
- association à risque ;
- commerce transfrontalier ;
- activité à forte circulation d’espèces.

---

# 61. Produits interdits ou restreints

Mansa doit pouvoir interdire ou restreindre certains usages selon :

- pays ;
- réglementation ;
- partenaire ;
- politique interne ;
- risque ;
- contrat.

---

# 62. Mineurs

Le système doit gérer lorsque le service l’autorise :

- âge ;
- représentant légal ;
- consentement ;
- plafonds ;
- produits disponibles ;
- restrictions ;
- vérification du responsable.

---

# 63. Agents publics et services de l’État

Les agents doivent être vérifiés selon :

- identité ;
- matricule ;
- institution ;
- rôle ;
- périmètre ;
- appareil ;
- autorisation ;
- date d’expiration.

Le contrôle doit protéger contre :

- faux agent ;
- usurpation ;
- accès hors périmètre ;
- modification non autorisée ;
- corruption ;
- suppression de trace.

---

# 64. Commerçants

Le KYB doit permettre de vérifier :

- existence ;
- activité ;
- localisation ;
- propriétaire ;
- bénéficiaires ;
- compte de règlement ;
- catégorie ;
- produits vendus ;
- risques ;
- volume attendu ;
- TPE associés.

---

# 65. Révision périodique des commerçants

Elle peut considérer :

- activité réelle ;
- litiges ;
- chargebacks ;
- remboursements ;
- fraude ;
- volume ;
- changement de dirigeant ;
- changement d’adresse ;
- changement de compte ;
- nouvelle catégorie.

---

# 66. Administration

Le portail Admin doit permettre :

- consulter les dossiers ;
- filtrer ;
- rechercher ;
- affecter un analyste ;
- demander un complément ;
- approuver ;
- rejeter ;
- limiter ;
- escalader ;
- consulter les alertes ;
- gérer les règles ;
- gérer les fournisseurs ;
- préparer un rapport ;
- exporter selon permission ;
- auditer les consultations.

---

# 67. Permissions

Exemples :

```text
kyc.read
kyc.read_sensitive
kyc.review
kyc.approve
kyc.reject
kyc.request_information
kyc.override
kyb.read
kyb.review
kyb.approve
aml.alert.read
aml.alert.assign
aml.case.create
aml.case.review
aml.case.close
aml.report.prepare
aml.report.approve
sanctions.review
pep.review
compliance.rule.manage
compliance.export.create
compliance.audit.read
```

---

# 68. Actions critiques

Doivent être particulièrement protégées :

- approbation d’un dossier à risque élevé ;
- override fournisseur ;
- suppression d’une alerte ;
- clôture d’un dossier confirmé ;
- levée de restriction ;
- déclaration réglementaire ;
- modification de règle AML ;
- export sensible ;
- accès massif aux documents ;
- modification d’un bénéficiaire effectif.

---

# 69. Double validation

Peut être exigée pour :

- PEP élevé ;
- sanction potentielle ;
- risque très élevé ;
- levée de gel ;
- déclaration ;
- override ;
- clôture d’un dossier majeur ;
- commerçant à fort volume ;
- partenaire institutionnel.

---

# 70. API

Exemples :

```http
POST   /kyc/cases
GET    /kyc/cases/{id}
PATCH  /kyc/cases/{id}
POST   /kyc/cases/{id}/documents
POST   /kyc/cases/{id}/submit
POST   /kyc/cases/{id}/approve
POST   /kyc/cases/{id}/reject
POST   /kyc/cases/{id}/request-information

POST   /kyb/cases
GET    /kyb/cases/{id}
POST   /kyb/cases/{id}/beneficial-owners

GET    /aml/alerts
GET    /aml/alerts/{id}
POST   /aml/cases
PATCH  /aml/cases/{id}
POST   /aml/cases/{id}/report

GET    /compliance/rules
POST   /compliance/screenings
```

---

# 71. Modèles

- KycCase
- KycLevel
- KycDocument
- KycVerification
- KycDecision
- KycReview
- KycProviderRequest
- KybCase
- BusinessEntity
- BeneficialOwner
- LegalRepresentative
- BusinessDocument
- RiskProfile
- RiskFactor
- SanctionScreening
- SanctionMatch
- PepScreening
- AdverseMediaScreening
- AmlRule
- AmlAlert
- ComplianceCase
- ComplianceCaseTransaction
- ComplianceDecision
- RegulatoryReport
- ComplianceRestriction
- ComplianceAudit

---

# 72. Règles métier

1. Toute personne utilisant un service financier possède un niveau KYC.
2. Toute organisation active possède un niveau KYB.
3. Les bénéficiaires effectifs sont identifiés lorsque requis.
4. Les documents sont vérifiés avant approbation.
5. Les décisions sont versionnées.
6. Les sanctions sont contrôlées.
7. Les PEP font l’objet d’une approche renforcée.
8. Un match potentiel n’est pas automatiquement confirmé.
9. Les faux positifs sont documentés.
10. Les profils de risque sont explicables.
11. Les règles AML sont versionnées.
12. Les alertes sont traçables.
13. Les dossiers peuvent être revus manuellement.
14. Les restrictions sont proportionnées.
15. Les opérations suspectes peuvent être mises en attente.
16. Les déclarations sont approuvées.
17. Les données sensibles sont limitées.
18. Les accès sont audités.
19. Les fournisseurs sont surveillés.
20. Les pays ont leurs propres règles.
21. Les re-KYC sont automatisables.
22. Les documents expirés déclenchent une action.
23. Les plafonds dépendent du niveau de vérification.
24. Les décisions importantes sont contestables lorsque possible.
25. Les données sont conservées selon la politique applicable.

---

# 73. Analytics

Événements possibles :

```text
kyc_case_created
kyc_document_uploaded
kyc_verification_started
kyc_verification_completed
kyc_review_required
kyc_approved
kyc_rejected
kyc_information_requested
kyc_expired
kyb_case_created
kyb_beneficial_owner_added
sanctions_potential_match_detected
sanctions_match_cleared
pep_detected
aml_alert_created
aml_alert_escalated
aml_case_created
aml_case_closed
compliance_restriction_applied
compliance_restriction_removed
regulatory_report_prepared
regulatory_report_submitted
```

---

# 74. Tests

- tests KYC niveau 0 à 3 ;
- tests KYB ;
- tests bénéficiaires effectifs ;
- tests document valide ;
- tests document expiré ;
- tests OCR ;
- tests preuve de vie ;
- tests comparaison faciale ;
- tests sanctions ;
- tests PEP ;
- tests faux positifs ;
- tests adverse media ;
- tests scoring ;
- tests AML ;
- tests transaction monitoring ;
- tests demande de complément ;
- tests expiration ;
- tests re-KYC ;
- tests multi-pays ;
- tests fournisseurs ;
- tests fallback ;
- tests de permissions ;
- tests de double validation ;
- tests d’audit ;
- tests de conservation ;
- tests de reporting.

---

# 75. Critères d’acceptation

La conformité globale est validée lorsque :

- les niveaux KYC et KYB sont définis ;
- les documents sont vérifiables ;
- les bénéficiaires effectifs sont gérés ;
- les fournisseurs sont intégrés ;
- les sanctions et PEP sont contrôlés ;
- les faux positifs peuvent être traités ;
- les profils de risque sont calculés ;
- la surveillance transactionnelle fonctionne ;
- les alertes créent des dossiers ;
- les revues manuelles sont possibles ;
- les restrictions sont configurables ;
- les re-KYC sont planifiables ;
- les obligations multi-pays sont prises en charge ;
- les déclarations sont traçables ;
- les données sensibles sont protégées ;
- les accès sont audités ;
- les tests couvrent les scénarios critiques.
