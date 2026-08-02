# 68 — Gestion documentaire, base de connaissances et documentation technique Mansa : cahiers des charges, procédures, API, architecture, versions, recherche, validation, publication, traduction, accès et administration centralisée

## 1. Objet du document

Ce document définit l’architecture officielle de la **Gestion documentaire, de la Base de connaissances et de la Documentation technique Mansa**.

Cette plateforme doit permettre de centraliser, organiser, sécuriser, versionner, valider, publier et retrouver tous les documents nécessaires au fonctionnement de l’écosystème Mansa.

Elle couvre notamment :

- les cahiers des charges ;
- les spécifications fonctionnelles ;
- les spécifications techniques ;
- la documentation des API ;
- la documentation des applications ;
- les procédures internes ;
- les procédures opérationnelles ;
- les procédures de sécurité ;
- les procédures de support ;
- les procédures Finance ;
- les procédures KYC et KYB ;
- les procédures agents ;
- les procédures commerçants ;
- les procédures TPE ;
- les procédures DAB ;
- les procédures de continuité ;
- les runbooks ;
- les guides utilisateurs ;
- les guides administrateurs ;
- les guides partenaires ;
- les contrats techniques ;
- les schémas d’architecture ;
- les modèles de données ;
- les politiques ;
- les rapports ;
- les comptes rendus ;
- les décisions ;
- les preuves ;
- les documents réglementaires ;
- les documents de conformité ;
- les documents par pays ;
- les traductions ;
- les versions ;
- les validations ;
- les publications ;
- les archives ;
- les audits.

L’objectif est de fournir une plateforme documentaire :

- centralisée ;
- structurée ;
- recherchable ;
- versionnée ;
- sécurisée ;
- multi-pays ;
- multi-langues ;
- multi-organisation ;
- accessible selon les rôles ;
- reliée aux applications ;
- reliée au code ;
- reliée aux incidents ;
- reliée aux releases ;
- reliée aux exigences ;
- capable de conserver l’historique complet ;
- capable de servir de source officielle.

---

# 2. Principes fondamentaux

## 2.1 Une seule source officielle

Pour chaque document important, une seule version doit être considérée comme officielle.

La plateforme doit indiquer clairement :

- la version actuelle ;
- le statut ;
- le propriétaire ;
- la date d’effet ;
- l’approbateur ;
- le pays ;
- le périmètre ;
- la langue ;
- la dernière mise à jour.

---

## 2.2 Aucun document critique ne doit rester sans propriétaire

Chaque document critique doit avoir :

- un auteur ;
- un propriétaire ;
- un relecteur ;
- un approbateur ;
- une date de revue ;
- une durée de validité ;
- un statut ;
- un historique.

---

## 2.3 Les documents doivent être versionnés

Toute modification importante doit créer une nouvelle version avec :

- ancienne version ;
- nouvelle version ;
- auteur ;
- date ;
- heure ;
- motif ;
- résumé des changements ;
- approbation ;
- date d’effet.

---

## 2.4 Les documents sensibles doivent être protégés

Les documents sensibles ne doivent pas être accessibles à tous.

La plateforme doit contrôler :

- consultation ;
- téléchargement ;
- modification ;
- partage ;
- impression ;
- export ;
- copie ;
- publication ;
- suppression ;
- archivage.

---

## 2.5 La documentation doit évoluer avec le produit

Toute modification importante du produit doit entraîner une revue de la documentation associée.

Exemples :

- nouvelle fonctionnalité ;
- changement d’API ;
- nouveau pays ;
- nouveau partenaire ;
- nouvelle règle de frais ;
- changement de sécurité ;
- changement d’architecture ;
- nouvelle version ;
- nouvel appareil ;
- nouvel incident ;
- nouvelle procédure.

---

## 2.6 Un document non à jour doit être signalé

La plateforme doit pouvoir détecter :

- document expiré ;
- document non revu ;
- document sans propriétaire ;
- lien cassé ;
- version obsolète ;
- procédure incompatible ;
- contenu non traduit ;
- document sans approbation ;
- document en conflit avec une version plus récente.

---

# 3. Périmètre documentaire

La plateforme couvre :

- documents métier ;
- documents techniques ;
- documents opérationnels ;
- documents réglementaires ;
- documents de sécurité ;
- documents Finance ;
- documents Data ;
- documents IA ;
- documents partenaires ;
- documents RH techniques ;
- procédures ;
- politiques ;
- guides ;
- modèles ;
- diagrammes ;
- décisions ;
- preuves ;
- rapports ;
- contrats ;
- fiches pratiques ;
- FAQ ;
- tutoriels ;
- notes de version ;
- archives.

---

# 4. Architecture logique

Structure recommandée :

```text
knowledge-and-documentation-platform/
├── specifications/
├── architecture/
├── api-documentation/
├── application-guides/
├── operational-procedures/
├── security-policies/
├── finance-procedures/
├── compliance/
├── partner-documentation/
├── user-guides/
├── admin-guides/
├── runbooks/
├── knowledge-base/
├── faq/
├── decisions/
├── templates/
├── reports/
├── evidence/
├── translations/
├── publication/
├── archives/
├── search/
├── audit/
└── administration/
```

---

# 5. Types de documents

Le système doit gérer au minimum :

- cahier des charges ;
- spécification fonctionnelle ;
- spécification technique ;
- document d’architecture ;
- procédure ;
- politique ;
- guide ;
- manuel ;
- FAQ ;
- article de connaissance ;
- runbook ;
- post-mortem ;
- rapport ;
- compte rendu ;
- décision ;
- contrat technique ;
- schéma ;
- diagramme ;
- modèle ;
- checklist ;
- formulaire ;
- preuve ;
- note de version ;
- document de formation ;
- document réglementaire.

---

# 6. Classification documentaire

Chaque document peut être classé selon :

- domaine ;
- produit ;
- application ;
- service ;
- pays ;
- partenaire ;
- environnement ;
- organisation ;
- niveau de sensibilité ;
- langue ;
- statut ;
- version ;
- propriétaire ;
- date ;
- criticité.

---

# 7. Domaines documentaires

Exemples :

- identité ;
- authentification ;
- utilisateurs ;
- paiements ;
- transferts ;
- cartes ;
- ledger ;
- agents ;
- commerçants ;
- TPE ;
- DAB ;
- KYC ;
- KYB ;
- fraude ;
- support ;
- Finance ;
- Data ;
- Jini ;
- sécurité ;
- infrastructure ;
- observabilité ;
- continuité ;
- qualité ;
- versions ;
- partenaires ;
- conformité.

---

# 8. Métadonnées obligatoires

Chaque document doit contenir :

- identifiant ;
- titre ;
- description ;
- type ;
- domaine ;
- propriétaire ;
- auteur ;
- version ;
- statut ;
- langue ;
- pays ;
- date de création ;
- date de modification ;
- date d’effet ;
- date de prochaine revue ;
- sensibilité ;
- mots-clés ;
- références ;
- approbateurs.

---

# 9. Identifiant documentaire

Exemple :

```text
MANSA-DOC-SEC-000124
```

Structure possible :

```text
Organisation
→ domaine
→ numéro unique
```

---

# 10. Statuts d’un document

- DRAFT ;
- IN_REVIEW ;
- CHANGES_REQUESTED ;
- APPROVED ;
- PUBLISHED ;
- ACTIVE ;
- EXPIRED ;
- SUPERSEDED ;
- SUSPENDED ;
- ARCHIVED ;
- REJECTED ;
- DELETED.

---

# 11. Cycle de vie

Exemple :

```text
DRAFT
→ IN_REVIEW
→ APPROVED
→ PUBLISHED
→ ACTIVE
→ SUPERSEDED
→ ARCHIVED
```

---

# 12. Création d’un document

La création doit permettre :

- choix du modèle ;
- définition du titre ;
- domaine ;
- pays ;
- langue ;
- sensibilité ;
- propriétaire ;
- contributeurs ;
- structure ;
- contenu ;
- pièces jointes ;
- liens ;
- références ;
- workflow de validation.

---

# 13. Modèles documentaires

La plateforme doit proposer des modèles pour :

- cahier des charges ;
- spécification fonctionnelle ;
- spécification technique ;
- procédure opérationnelle ;
- runbook ;
- politique de sécurité ;
- post-mortem ;
- rapport d’audit ;
- guide utilisateur ;
- guide partenaire ;
- note de version ;
- compte rendu ;
- fiche de décision ;
- plan de test ;
- plan de continuité.

---

# 14. Contenu structuré

Les documents doivent pouvoir contenir :

- titres ;
- paragraphes ;
- listes ;
- tableaux ;
- diagrammes ;
- images ;
- vidéos ;
- fichiers ;
- code ;
- API ;
- liens ;
- checklists ;
- avertissements ;
- exemples ;
- blocs de configuration ;
- décisions ;
- références.

---

# 15. Documentation technique

Elle doit couvrir :

- architecture ;
- modules ;
- services ;
- dépendances ;
- bases ;
- flux ;
- événements ;
- API ;
- queues ;
- sécurité ;
- déploiement ;
- configuration ;
- monitoring ;
- reprise ;
- tests ;
- versions.

---

# 16. Documentation d’architecture

Chaque système critique doit documenter :

- objectif ;
- contexte ;
- composants ;
- flux ;
- dépendances ;
- stockage ;
- sécurité ;
- disponibilité ;
- scalabilité ;
- limites ;
- risques ;
- décisions ;
- responsables.

---

# 17. Diagrammes

Types supportés :

- diagramme de contexte ;
- diagramme de composants ;
- diagramme de séquence ;
- diagramme de déploiement ;
- diagramme réseau ;
- diagramme de données ;
- diagramme de processus ;
- diagramme de dépendances ;
- diagramme de sécurité ;
- diagramme de reprise.

---

# 18. Documentation API

Chaque API doit préciser :

- nom ;
- description ;
- version ;
- base URL ;
- authentification ;
- permissions ;
- endpoints ;
- paramètres ;
- schémas ;
- exemples ;
- erreurs ;
- idempotence ;
- rate limits ;
- webhooks ;
- changelog ;
- compatibilité ;
- environnement Sandbox.

---

# 19. Exemple d’endpoint documenté

```http
POST /payments
```

La documentation doit présenter :

- usage ;
- autorisation requise ;
- headers ;
- corps ;
- exemple ;
- réponse ;
- codes d’erreur ;
- idempotency key ;
- timeout ;
- retry ;
- événement généré.

---

# 20. Documentation des événements

Chaque événement doit contenir :

- nom ;
- version ;
- producteur ;
- consommateurs ;
- schéma ;
- date ;
- ordre ;
- idempotence ;
- exemples ;
- politique de rétention ;
- compatibilité.

---

# 21. Documentation du modèle de données

Elle doit préciser :

- entités ;
- attributs ;
- relations ;
- contraintes ;
- index ;
- statuts ;
- historique ;
- sensibilité ;
- rétention ;
- propriétaire ;
- source ;
- destination.

---

# 22. Documentation des règles métier

Chaque règle métier doit contenir :

- identifiant ;
- description ;
- domaine ;
- conditions ;
- exceptions ;
- priorité ;
- date d’effet ;
- pays ;
- propriétaire ;
- approbateur ;
- tests associés.

---

# 23. Documentation des frais et commissions

Elle doit documenter :

- type ;
- formule ;
- montant fixe ;
- pourcentage ;
- minimum ;
- maximum ;
- acteurs ;
- pays ;
- date d’effet ;
- règles de priorité ;
- exemptions ;
- campagnes ;
- historique.

---

# 24. Documentation du ledger

Elle doit préciser :

- types de comptes ;
- types d’écritures ;
- règles débit/crédit ;
- références ;
- événements ;
- compensation ;
- annulation ;
- rapprochement ;
- suspenses ;
- clôture ;
- audit ;
- restauration.

---

# 25. Documentation KYC et KYB

Elle doit couvrir :

- niveaux ;
- documents ;
- parcours ;
- règles ;
- pays ;
- limites ;
- vérifications ;
- recours ;
- expiration ;
- mise à jour ;
- rejet ;
- sécurité ;
- fournisseurs.

---

# 26. Documentation agents

Elle doit contenir :

- enrôlement ;
- vérification ;
- float ;
- caisse ;
- dépôt ;
- retrait ;
- commissions ;
- limites ;
- incidents ;
- sécurité ;
- appareils ;
- maintenance ;
- procédures.

---

# 27. Documentation commerçants

Elle doit contenir :

- inscription ;
- KYB ;
- points de vente ;
- employés ;
- TPE ;
- encaissement ;
- remboursement ;
- règlement ;
- commissions ;
- factures ;
- support ;
- sécurité.

---

# 28. Documentation TPE

Elle doit couvrir :

- modèles ;
- installation ;
- enrôlement ;
- configuration ;
- réseau ;
- cartes ;
- NFC ;
- QR ;
- imprimante ;
- mises à jour ;
- offline ;
- incidents ;
- maintenance ;
- sécurité.

---

# 29. Documentation DAB

Elle doit couvrir :

- constructeur ;
- modèle ;
- localisation ;
- composants ;
- cassettes ;
- billets ;
- réseau ;
- logiciel ;
- sécurité ;
- transactions ;
- maintenance ;
- procédures ;
- incidents ;
- reprise.

---

# 30. Documentation des applications

Chaque application doit posséder :

- présentation ;
- utilisateurs ;
- fonctionnalités ;
- écrans ;
- permissions ;
- dépendances ;
- sécurité ;
- versions ;
- compatibilité ;
- tests ;
- déploiement ;
- support.

---

# 31. Guides utilisateurs

Ils doivent être adaptés à :

- clients ;
- agents ;
- commerçants ;
- employés ;
- administrateurs ;
- partenaires ;
- techniciens ;
- institutions ;
- écoles ;
- entreprises.

---

# 32. Guide Client

Il peut couvrir :

- création de compte ;
- connexion ;
- KYC ;
- solde ;
- transfert ;
- paiement ;
- carte ;
- sécurité ;
- récupération ;
- support ;
- frais ;
- notifications.

---

# 33. Guide Agent

Il peut couvrir :

- ouverture de caisse ;
- dépôt ;
- retrait ;
- float ;
- commission ;
- reçu ;
- incident ;
- fermeture de caisse ;
- réapprovisionnement ;
- sécurité ;
- assistance.

---

# 34. Guide Commerçant

Il peut couvrir :

- encaissement ;
- TPE ;
- QR ;
- facture ;
- remboursement ;
- employés ;
- clôture ;
- règlement ;
- promotions ;
- support ;
- maintenance.

---

# 35. Guide Administrateur

Il doit préciser :

- rôles ;
- permissions ;
- navigation ;
- approbations ;
- recherches ;
- suspensions ;
- configurations ;
- audits ;
- rapports ;
- incidents ;
- sécurité.

---

# 36. Base de connaissances

La base de connaissances doit permettre :

- articles ;
- catégories ;
- mots-clés ;
- recherche ;
- suggestions ;
- liens ;
- images ;
- vidéos ;
- pièces jointes ;
- commentaires internes ;
- versions ;
- traductions ;
- publication ciblée.

---

# 37. Articles de connaissance

Chaque article doit contenir :

- problème ;
- symptômes ;
- cause ;
- solution ;
- étapes ;
- avertissements ;
- références ;
- public visé ;
- date ;
- version ;
- statut ;
- propriétaire.

---

# 38. FAQ

Les FAQ peuvent être organisées par :

- application ;
- utilisateur ;
- pays ;
- produit ;
- service ;
- thème ;
- niveau ;
- langue ;
- partenaire.

---

# 39. Recherche

La recherche doit fonctionner sur :

- titre ;
- contenu ;
- métadonnées ;
- mots-clés ;
- auteurs ;
- domaines ;
- pays ;
- langue ;
- version ;
- identifiant ;
- pièces jointes ;
- texte de code ;
- erreur ;
- endpoint ;
- incident.

---

# 40. Recherche avancée

Filtres possibles :

- type ;
- statut ;
- date ;
- pays ;
- application ;
- domaine ;
- propriétaire ;
- langue ;
- sensibilité ;
- version ;
- partenaire ;
- environnement ;
- organisation.

---

# 41. Recherche sémantique

La plateforme peut utiliser une recherche sémantique pour retrouver un document même lorsque les mots exacts ne sont pas utilisés.

Elle doit respecter :

- permissions ;
- périmètre ;
- sensibilité ;
- langue ;
- version officielle ;
- séparation des organisations.

---

# 42. Suggestions automatiques

La plateforme peut proposer :

- documents liés ;
- procédures associées ;
- articles utiles ;
- version plus récente ;
- traduction disponible ;
- runbook ;
- incident lié ;
- API liée ;
- guide utilisateur.

---

# 43. Assistant documentaire

Jini peut aider à :

- retrouver un document ;
- résumer ;
- expliquer ;
- comparer deux versions ;
- générer une FAQ ;
- proposer une structure ;
- trouver une procédure ;
- identifier les documents obsolètes ;
- préparer une traduction.

Jini ne doit pas contourner les permissions.

---

# 44. Réponse fondée sur les sources

Lorsqu’il répond depuis la documentation, Jini doit pouvoir indiquer :

- document source ;
- version ;
- section ;
- date ;
- statut ;
- niveau de confiance ;
- lien.

---

# 45. Versionnement

Chaque version doit conserver :

- numéro ;
- auteur ;
- date ;
- changement ;
- motif ;
- statut ;
- approbateur ;
- date d’effet ;
- lien vers la version précédente.

---

# 46. Comparaison de versions

La plateforme doit permettre de visualiser :

- ajouts ;
- suppressions ;
- modifications ;
- déplacements ;
- changements de statut ;
- changements de métadonnées ;
- changement d’approbateur ;
- changement de date d’effet.

---

# 47. Version majeure

Elle doit être créée lorsque :

- périmètre modifié ;
- architecture modifiée ;
- règle majeure modifiée ;
- responsabilité modifiée ;
- procédure critique modifiée ;
- pays ajouté ;
- obligation nouvelle ;
- incompatibilité introduite.

---

# 48. Version mineure

Elle peut concerner :

- précision ;
- exemple ;
- reformulation ;
- ajout limité ;
- mise à jour de contact ;
- correction non structurelle ;
- amélioration visuelle.

---

# 49. Brouillons

Les brouillons doivent être accessibles uniquement aux personnes autorisées.

Ils ne doivent pas être présentés comme source officielle.

---

# 50. Relecture

La relecture peut vérifier :

- exactitude ;
- cohérence ;
- sécurité ;
- conformité ;
- orthographe ;
- architecture ;
- règles métier ;
- confidentialité ;
- traduction ;
- accessibilité.

---

# 51. Workflow de validation

Exemple :

```text
Auteur
→ Relecteur métier
→ Relecteur technique
→ Sécurité ou conformité
→ Approbateur
→ Publication
```

---

# 52. Validation simple

Elle peut être utilisée pour :

- FAQ ;
- guide non critique ;
- documentation interne mineure ;
- correction de forme ;
- article support.

---

# 53. Validation renforcée

Elle doit être utilisée pour :

- politique de sécurité ;
- ledger ;
- procédure financière ;
- procédure DAB ;
- procédure TPE ;
- PCA/PRA ;
- frais ;
- commissions ;
- réglementation ;
- données personnelles ;
- accès administrateur.

---

# 54. Double validation

Elle peut être exigée pour :

- politique de sécurité ;
- règle financière critique ;
- procédure de restauration ;
- procédure de bascule ;
- changement réglementaire ;
- suppression d’un document critique ;
- publication partenaire ;
- changement national.

---

# 55. Approbation

L’approbation doit enregistrer :

- approbateur ;
- rôle ;
- date ;
- heure ;
- décision ;
- commentaire ;
- version ;
- date d’effet ;
- signature éventuelle.

---

# 56. Rejet

Le rejet doit contenir :

- motif ;
- commentaires ;
- sections concernées ;
- auteur ;
- relecteur ;
- date ;
- action attendue.

---

# 57. Publication

Un document publié doit préciser :

- public ;
- canal ;
- langue ;
- pays ;
- version ;
- date ;
- durée ;
- restrictions ;
- responsable.

---

# 58. Publics de publication

- interne ;
- administrateurs ;
- support ;
- agents ;
- commerçants ;
- clients ;
- partenaires ;
- banques ;
- institutions ;
- développeurs ;
- public général.

---

# 59. Canaux de publication

- portail documentaire ;
- application ;
- site web ;
- portail développeurs ;
- portail partenaire ;
- e-mail ;
- notification ;
- PDF ;
- centre d’aide ;
- API ;
- téléchargement contrôlé.

---

# 60. Publication ciblée

Le ciblage peut dépendre :

- pays ;
- langue ;
- application ;
- rôle ;
- organisation ;
- partenaire ;
- version ;
- appareil ;
- statut ;
- environnement.

---

# 61. Documentation embarquée

Certaines aides peuvent être affichées directement dans :

- application Client ;
- application Agent ;
- application Commerce ;
- TPE ;
- DAB ;
- Admin Web ;
- Admin Lite ;
- portail développeurs.

---

# 62. Aide contextuelle

L’aide peut apparaître selon :

- écran ;
- erreur ;
- fonction ;
- statut ;
- pays ;
- rôle ;
- version ;
- incident ;
- première utilisation.

---

# 63. Tutoriels

La plateforme doit gérer :

- texte ;
- images ;
- vidéo ;
- animation ;
- étapes interactives ;
- checklist ;
- quiz ;
- validation ;
- progression.

---

# 64. Traductions

La plateforme doit supporter :

- français ;
- bambara ;
- anglais ;
- arabe ;
- autres langues activées.

---

# 65. Workflow de traduction

Exemple :

```text
Document source approuvé
→ traduction
→ relecture linguistique
→ relecture métier
→ validation
→ publication
```

---

# 66. Statuts de traduction

- NOT_STARTED ;
- IN_PROGRESS ;
- IN_REVIEW ;
- APPROVED ;
- PUBLISHED ;
- OUTDATED ;
- REJECTED.

---

# 67. Détection de traduction obsolète

Lorsqu’un document source change, les traductions liées doivent être marquées :

- à vérifier ;
- partiellement obsolètes ;
- obsolètes ;
- bloquées si critique.

---

# 68. Terminologie

Un glossaire officiel doit gérer :

- terme ;
- définition ;
- traduction ;
- domaine ;
- usage ;
- terme interdit ;
- terme recommandé ;
- exemples ;
- pays ;
- version.

---

# 69. Cohérence terminologique

La plateforme peut détecter :

- termes différents pour la même fonction ;
- ancienne marque ;
- ancienne appellation ;
- terme réglementaire incorrect ;
- mauvaise traduction ;
- abréviation non définie.

---

# 70. Documentation multi-pays

Chaque pays peut avoir :

- réglementation ;
- produits ;
- partenaires ;
- devises ;
- frais ;
- plafonds ;
- documents ;
- procédures ;
- langues ;
- contacts ;
- formulaires ;
- versions spécifiques.

---

# 71. Document global et variantes pays

Un document global peut avoir :

- version principale ;
- annexes ;
- exceptions ;
- variantes ;
- traductions ;
- date d’effet par pays ;
- approbateurs locaux.

---

# 72. Documentation partenaire

Elle doit couvrir :

- intégration ;
- API ;
- authentification ;
- certificats ;
- Sandbox ;
- erreurs ;
- tests ;
- SLA ;
- support ;
- sécurité ;
- webhooks ;
- version ;
- contact.

---

# 73. Portail développeurs

Le portail doit proposer :

- guides ;
- API ;
- SDK ;
- exemples ;
- Sandbox ;
- clés de test ;
- changelog ;
- statuts ;
- erreurs ;
- webhooks ;
- support ;
- annonces.

---

# 74. SDK

Chaque SDK doit documenter :

- langage ;
- version ;
- installation ;
- configuration ;
- authentification ;
- exemples ;
- erreurs ;
- compatibilité ;
- licence ;
- changelog ;
- fin de support.

---

# 75. Exemples de code

Les exemples doivent être :

- testés ;
- versionnés ;
- sécurisés ;
- sans secret ;
- compatibles ;
- simples ;
- liés à la version d’API.

---

# 76. Documentation de sécurité

Elle doit couvrir :

- politiques ;
- contrôles ;
- accès ;
- chiffrement ;
- clés ;
- certificats ;
- incidents ;
- vulnérabilités ;
- réponses ;
- audit ;
- sensibilisation ;
- fournisseurs.

---

# 77. Documents hautement sensibles

Exemples :

- architecture de sécurité détaillée ;
- procédures de récupération de clés ;
- plans d’accès d’urgence ;
- secrets de configuration ;
- résultats d’intrusion complets ;
- plans de défense ;
- informations HSM ;
- procédures de failover critiques.

---

# 78. Niveaux de sensibilité

- PUBLIC ;
- INTERNAL ;
- CONFIDENTIAL ;
- RESTRICTED ;
- HIGHLY_RESTRICTED.

---

# 79. Contrôle d’accès

L’accès peut dépendre :

- rôle ;
- organisation ;
- pays ;
- équipe ;
- projet ;
- niveau de sensibilité ;
- environnement ;
- durée ;
- appareil ;
- approbation.

---

# 80. Accès temporaire

Un accès temporaire doit préciser :

- document ;
- utilisateur ;
- motif ;
- début ;
- expiration ;
- approbateur ;
- permissions ;
- audit.

---

# 81. Partage externe

Le partage externe doit être :

- limité ;
- protégé ;
- expirant ;
- traçable ;
- éventuellement filigrané ;
- révocable ;
- approuvé ;
- conforme.

---

# 82. Liens de partage

Un lien peut comporter :

- expiration ;
- mot de passe ;
- restriction de domaine ;
- nombre de consultations ;
- interdiction de téléchargement ;
- watermark ;
- journalisation.

---

# 83. Téléchargement

Le téléchargement peut être :

- autorisé ;
- interdit ;
- limité ;
- filigrané ;
- chiffré ;
- soumis à justification ;
- soumis à approbation.

---

# 84. Impression

L’impression peut être :

- autorisée ;
- interdite ;
- limitée ;
- filigranée ;
- tracée ;
- réservée à certains rôles.

---

# 85. Filigrane

Il peut contenir :

- utilisateur ;
- date ;
- heure ;
- organisation ;
- identifiant document ;
- niveau de sensibilité ;
- mention confidentielle.

---

# 86. Protection contre la copie

Pour les documents sensibles, la plateforme peut limiter :

- copier-coller ;
- capture ;
- export ;
- téléchargement ;
- impression ;
- partage.

Ces protections ne sont jamais considérées comme suffisantes seules.

---

# 87. Archivage

Un document peut être archivé lorsque :

- remplacé ;
- expiré ;
- produit arrêté ;
- partenaire terminé ;
- pays fermé ;
- procédure supprimée ;
- version obsolète ;
- obligation terminée.

---

# 88. Rétention

La durée dépend :

- type ;
- pays ;
- réglementation ;
- contrat ;
- audit ;
- sécurité ;
- importance ;
- litige ;
- enquête.

---

# 89. Legal Hold

Un document sous conservation légale ne peut pas être :

- supprimé ;
- modifié ;
- remplacé ;
- purgé ;
- anonymisé sans validation ;
- déplacé hors périmètre autorisé.

---

# 90. Suppression

La suppression doit vérifier :

- droit ;
- rétention ;
- statut ;
- dépendances ;
- litige ;
- audit ;
- sauvegarde ;
- approbation ;
- remplacement éventuel.

---

# 91. Suppression logique

Un document peut être masqué tout en restant conservé pour :

- audit ;
- historique ;
- preuve ;
- réglementation ;
- restauration.

---

# 92. Suppression définitive

Elle doit être :

- rare ;
- justifiée ;
- approuvée ;
- auditée ;
- compatible avec la rétention ;
- vérifiée ;
- irréversible.

---

# 93. Documents liés

Un document peut être relié à :

- application ;
- service ;
- API ;
- incident ;
- release ;
- appareil ;
- partenaire ;
- contrat ;
- exigence ;
- test ;
- audit ;
- décision ;
- action corrective.

---

# 94. Liaison avec GitHub

La documentation technique peut être reliée à :

- dépôt ;
- branche ;
- commit ;
- Pull Request ;
- fichier ;
- release ;
- issue ;
- tag.

---

# 95. Documentation as Code

Certains documents peuvent être gérés dans Git sous forme de :

- Markdown ;
- YAML ;
- JSON ;
- OpenAPI ;
- AsyncAPI ;
- diagrammes ;
- configurations ;
- schémas.

---

# 96. Synchronisation Git

La plateforme peut :

- importer ;
- publier ;
- comparer ;
- détecter un changement ;
- relier une version ;
- ouvrir une revue ;
- conserver l’historique.

---

# 97. Conflits de documentation

Un conflit doit être signalé lorsque :

- deux documents actifs se contredisent ;
- deux versions sont publiées ;
- un document local contredit un document global ;
- une API documentée ne correspond plus au code ;
- une procédure ne correspond plus à l’application.

---

# 98. Détection de contenu obsolète

Le système peut utiliser :

- date de revue ;
- version liée ;
- release ;
- commit ;
- API ;
- propriétaire ;
- changement d’architecture ;
- incident ;
- test échoué ;
- signalement utilisateur.

---

# 99. Revue périodique

La fréquence peut être :

- mensuelle ;
- trimestrielle ;
- semestrielle ;
- annuelle ;
- après incident ;
- après release ;
- après changement réglementaire ;
- après changement de partenaire.

---

# 100. Rappels de revue

La plateforme doit envoyer des rappels avant :

- date de revue ;
- date d’expiration ;
- fin de support ;
- changement de version ;
- changement de pays ;
- fin de contrat ;
- suppression prévue.

---

# 101. Signalement d’un document

Un utilisateur peut signaler :

- erreur ;
- incohérence ;
- contenu ancien ;
- lien cassé ;
- traduction incorrecte ;
- information dangereuse ;
- procédure impossible ;
- problème de permission.

---

# 102. Cycle d’un signalement

- OPEN ;
- TRIAGED ;
- ASSIGNED ;
- IN_PROGRESS ;
- RESOLVED ;
- REJECTED ;
- CLOSED ;
- REOPENED.

---

# 103. Commentaires

Les documents peuvent autoriser :

- commentaire interne ;
- suggestion ;
- question ;
- mention ;
- réponse ;
- résolution ;
- historique.

---

# 104. Coédition

La coédition peut permettre :

- plusieurs auteurs ;
- suivi des modifications ;
- verrouillage de section ;
- commentaires ;
- mentions ;
- comparaison ;
- fusion ;
- restauration.

---

# 105. Verrouillage

Un document critique peut être verrouillé pendant :

- validation ;
- publication ;
- audit ;
- incident ;
- enquête ;
- migration ;
- archivage.

---

# 106. Notifications documentaires

Événements possibles :

- document créé ;
- revue demandée ;
- modification ;
- approbation ;
- rejet ;
- publication ;
- expiration ;
- traduction obsolète ;
- commentaire ;
- signalement ;
- accès demandé ;
- suppression prévue.

---

# 107. Abonnements

Un utilisateur peut suivre :

- document ;
- domaine ;
- application ;
- pays ;
- partenaire ;
- API ;
- procédure ;
- type de changement.

---

# 108. Tableau de bord documentaire

Il peut afficher :

- documents actifs ;
- brouillons ;
- revues en attente ;
- documents expirés ;
- documents sans propriétaire ;
- traductions en retard ;
- signalements ;
- publications ;
- documents sensibles ;
- statistiques de consultation.

---

# 109. Tableau de bord propriétaire

Le propriétaire doit voir :

- documents à revoir ;
- approbations en attente ;
- signalements ;
- traductions ;
- versions ;
- dates d’expiration ;
- documents liés ;
- actions requises.

---

# 110. Statistiques

Exemples :

- documents par type ;
- documents par domaine ;
- documents par pays ;
- taux de revue ;
- taux de publication ;
- délai moyen d’approbation ;
- taux de traduction ;
- nombre de consultations ;
- recherches sans résultat ;
- articles utiles.

---

# 111. Mesure d’utilité

Un article peut recevoir :

- utile ;
- non utile ;
- commentaire ;
- problème résolu ;
- temps de lecture ;
- abandon ;
- partage ;
- escalade vers support.

---

# 112. Recherches sans résultat

La plateforme doit analyser :

- termes recherchés ;
- langue ;
- pays ;
- rôle ;
- domaine ;
- fréquence ;
- besoin non couvert.

Cela peut créer une proposition de nouvel article.

---

# 113. Accessibilité documentaire

La plateforme doit supporter :

- navigation clavier ;
- lecteur d’écran ;
- contraste ;
- taille de texte ;
- alternatives ;
- structure sémantique ;
- sous-titres ;
- transcription ;
- formats accessibles.

---

# 114. Documents hors ligne

Certains documents peuvent être disponibles hors ligne :

- procédures d’urgence ;
- contacts ;
- runbooks ;
- guides Agent ;
- guides TPE ;
- guides DAB ;
- PCA ;
- PRA ;
- checklists.

---

# 115. Synchronisation hors ligne

Elle doit gérer :

- version ;
- expiration ;
- révocation ;
- mise à jour ;
- suppression ;
- chiffrement ;
- accès ;
- conflit ;
- historique.

---

# 116. Export

Formats possibles :

- PDF ;
- Markdown ;
- HTML ;
- JSON ;
- CSV ;
- DOCX ;
- OpenAPI ;
- archive ZIP contrôlée.

---

# 117. Export PDF

Il doit pouvoir inclure :

- titre ;
- version ;
- date ;
- statut ;
- propriétaire ;
- filigrane ;
- pagination ;
- sommaire ;
- confidentialité ;
- signature éventuelle.

---

# 118. Import

La plateforme peut importer :

- Markdown ;
- PDF ;
- DOCX ;
- OpenAPI ;
- AsyncAPI ;
- images ;
- diagrammes ;
- archives ;
- documents partenaires.

---

# 119. Contrôle d’import

Avant publication, l’import doit vérifier :

- virus ;
- format ;
- taille ;
- métadonnées ;
- secrets ;
- données personnelles ;
- contenu interdit ;
- version ;
- propriétaire ;
- permissions.

---

# 120. Détection de secrets

Les documents techniques doivent être scannés pour détecter :

- clé API ;
- mot de passe ;
- token ;
- clé privée ;
- secret cloud ;
- identifiant sensible ;
- chaîne de connexion ;
- certificat privé.

---

# 121. Réaction à un secret détecté

Le système doit pouvoir :

- bloquer la publication ;
- masquer ;
- alerter ;
- ouvrir un incident ;
- demander une rotation ;
- informer la sécurité ;
- conserver une preuve.

---

# 122. Données personnelles

Les documents ne doivent contenir des données personnelles que si nécessaire.

Le système doit permettre :

- masquage ;
- anonymisation ;
- restriction ;
- justification ;
- rétention ;
- suppression ;
- audit.

---

# 123. Administration centrale

L’administration peut gérer :

- types de documents ;
- domaines ;
- modèles ;
- métadonnées ;
- workflows ;
- rôles ;
- permissions ;
- pays ;
- langues ;
- glossaire ;
- publication ;
- archivage ;
- rétention ;
- recherche ;
- imports ;
- exports ;
- intégrations ;
- signalements ;
- audits.

---

# 124. Rôles

Exemples :

```text
DOCUMENTATION_ADMIN
KNOWLEDGE_MANAGER
TECHNICAL_WRITER
API_DOCUMENTATION_MANAGER
BUSINESS_DOCUMENT_OWNER
SECURITY_DOCUMENT_OWNER
COMPLIANCE_DOCUMENT_OWNER
TRANSLATION_MANAGER
TRANSLATOR
REVIEWER
APPROVER
PUBLISHER
ARCHIVIST
AUDITOR
VIEWER
```

---

# 125. Permissions

Exemples :

```text
documentation.read
documentation.create
documentation.update
documentation.review
documentation.approve
documentation.publish
documentation.archive
documentation.delete
documentation.export
documentation.share
documentation.translate
documentation.manage_templates
documentation.manage_glossary
documentation.manage_retention
documentation.audit.read
```

---

# 126. Approbations

Peuvent nécessiter une approbation :

- publication externe ;
- procédure critique ;
- politique de sécurité ;
- document réglementaire ;
- partage partenaire ;
- suppression ;
- archivage anticipé ;
- export sensible ;
- modification de rétention ;
- traduction officielle.

---

# 127. Double validation

Peut être exigée pour :

- suppression définitive ;
- publication d’une politique de sécurité ;
- publication d’une procédure financière ;
- diffusion d’une architecture sensible ;
- export massif ;
- partage externe restreint ;
- changement de document national ;
- modification d’une procédure de reprise.

---

# 128. Séparation des rôles

Exemple :

```text
Auteur rédige
→ Relecteur vérifie
→ Approbateur valide
→ Éditeur publie
→ Auditeur contrôle
```

Le même utilisateur ne doit pas pouvoir rédiger, approuver et publier seul un document critique.

---

# 129. API

Exemples :

```http
GET    /documentation/documents
POST   /documentation/documents
GET    /documentation/documents/{id}
PATCH  /documentation/documents/{id}

POST   /documentation/documents/{id}/submit-review
POST   /documentation/documents/{id}/approve
POST   /documentation/documents/{id}/reject
POST   /documentation/documents/{id}/publish
POST   /documentation/documents/{id}/archive

GET    /documentation/search
GET    /documentation/categories
GET    /documentation/templates
GET    /documentation/glossary

POST   /documentation/translations
POST   /documentation/access-requests

GET    /documentation/reports
GET    /documentation/audit
```

---

# 130. Webhooks internes

Événements possibles :

```text
documentation.document.created
documentation.document.updated
documentation.document.submitted
documentation.document.approved
documentation.document.rejected
documentation.document.published
documentation.document.expired
documentation.document.archived
documentation.translation.outdated
documentation.review.overdue
documentation.access.requested
documentation.secret.detected
documentation.report.created
documentation.audit.alert
```

---

# 131. Intégrations

La plateforme doit pouvoir se connecter à :

- GitHub ;
- CI/CD ;
- API Gateway ;
- portail développeurs ;
- applications mobiles ;
- applications web ;
- support ;
- sécurité ;
- conformité ;
- Finance ;
- Data ;
- Jini ;
- incidents ;
- releases ;
- tests ;
- PCA/PRA ;
- gestion de projet ;
- stockage ;
- signature électronique.

---

# 132. Modèles principaux

- Document
- DocumentType
- DocumentCategory
- DocumentVersion
- DocumentSection
- DocumentMetadata
- DocumentTemplate
- DocumentAttachment
- DocumentLink
- DocumentRelationship
- DocumentReview
- DocumentApproval
- DocumentPublication
- DocumentTranslation
- TranslationTerm
- GlossaryEntry
- KnowledgeArticle
- FAQEntry
- DocumentationSearchIndex
- AccessRequest
- ExternalShare
- RetentionPolicy
- LegalHold
- DocumentReport
- DocumentationNotification
- DocumentationSubscription
- DocumentationAudit

---

# 133. Analytics

Événements possibles :

```text
documentation_home_opened
documentation_document_opened
documentation_search_started
documentation_search_no_result
documentation_document_created
documentation_document_updated
documentation_document_submitted
documentation_document_approved
documentation_document_published
documentation_article_marked_useful
documentation_article_marked_not_useful
documentation_translation_started
documentation_export_started
documentation_access_denied
```

---

# 134. Données analytics interdites

Ne pas transmettre :

- contenu confidentiel complet ;
- secrets ;
- clés ;
- données personnelles ;
- documents sensibles ;
- contrats privés ;
- plans de sécurité ;
- résultats d’intrusion ;
- pièces jointes privées ;
- données réglementées.

---

# 135. Audit

Le journal doit contenir :

- utilisateur ;
- rôle ;
- document ;
- version ;
- action ;
- pays ;
- organisation ;
- date ;
- heure ;
- ancienne valeur ;
- nouvelle valeur ;
- motif ;
- approbateur ;
- statut ;
- résultat ;
- IP ou appareil lorsque requis.

---

# 136. Immutabilité des audits

Les audits doivent être protégés contre :

- modification ;
- suppression ;
- réécriture ;
- remplacement ;
- désactivation ;
- changement d’auteur ;
- changement de date ;
- export non autorisé.

---

# 137. Reporting

Rapports possibles :

- documents actifs ;
- documents expirés ;
- documents sans propriétaire ;
- documents non revus ;
- publications ;
- approbations ;
- traductions ;
- recherches ;
- articles utiles ;
- signalements ;
- documents sensibles ;
- accès externes ;
- suppressions ;
- archives.

---

# 138. Indicateurs

Exemples :

- taux de documents à jour ;
- délai moyen de validation ;
- taux de traduction ;
- taux de documents avec propriétaire ;
- nombre de recherches sans résultat ;
- taux d’utilité des articles ;
- nombre de documents expirés ;
- nombre de signalements ;
- temps moyen de correction ;
- nombre d’accès refusés.

---

# 139. Tests

- tests de création ;
- tests de modèles ;
- tests de métadonnées ;
- tests de versionnement ;
- tests de comparaison ;
- tests de revue ;
- tests d’approbation ;
- tests de rejet ;
- tests de publication ;
- tests de publication ciblée ;
- tests de traduction ;
- tests de glossaire ;
- tests de recherche ;
- tests de recherche sémantique ;
- tests de suggestions ;
- tests Jini ;
- tests de permissions ;
- tests de partage externe ;
- tests d’expiration ;
- tests de téléchargement ;
- tests d’impression ;
- tests de filigrane ;
- tests d’archivage ;
- tests de rétention ;
- tests Legal Hold ;
- tests de suppression ;
- tests de liaison GitHub ;
- tests Documentation as Code ;
- tests de conflits ;
- tests d’obsolescence ;
- tests de revue périodique ;
- tests de signalement ;
- tests de coédition ;
- tests de verrouillage ;
- tests de notification ;
- tests hors ligne ;
- tests d’export ;
- tests d’import ;
- tests antivirus ;
- tests de détection de secrets ;
- tests de données personnelles ;
- tests multi-pays ;
- tests multi-langues ;
- tests multi-organisation ;
- tests d’approbation ;
- tests d’audit ;
- tests de performance ;
- tests de haute disponibilité.

---

# 140. Règles métier

1. Chaque document critique possède un propriétaire.
2. Chaque document officiel possède une version.
3. Une seule version est officielle à un instant donné.
4. Les brouillons ne sont pas présentés comme officiels.
5. Les documents sensibles sont protégés.
6. Les modifications importantes sont historisées.
7. Les documents critiques sont approuvés.
8. Les documents expirés sont signalés.
9. Les traductions obsolètes sont marquées.
10. La terminologie officielle est centralisée.
11. Les documents partenaires sont versionnés.
12. Les API sont documentées.
13. Les règles métier sont documentées.
14. Les documents sont liés aux releases lorsque nécessaire.
15. Les documents techniques peuvent être liés à GitHub.
16. Les conflits sont détectés.
17. Les secrets ne doivent pas être publiés.
18. Les documents sous Legal Hold ne sont pas supprimés.
19. Les partages externes sont limités.
20. Les accès temporaires expirent.
21. Les procédures d’urgence sont disponibles hors ligne.
22. Les signalements sont suivis.
23. Les revues périodiques sont obligatoires.
24. Le demandeur ne valide pas seul une publication critique.
25. Les audits sont immuables.

---

# 141. Critères d’acceptation

La Gestion documentaire, la Base de connaissances et la Documentation technique Mansa sont validées lorsque :

- les types de documents sont définis ;
- les domaines sont définis ;
- les métadonnées sont obligatoires ;
- chaque document possède un identifiant ;
- les statuts sont gérés ;
- le cycle de vie est appliqué ;
- les modèles documentaires sont disponibles ;
- les contenus structurés sont supportés ;
- l’architecture est documentable ;
- les diagrammes sont supportés ;
- les API sont documentées ;
- les événements sont documentés ;
- les modèles de données sont documentés ;
- les règles métier sont documentées ;
- les frais et commissions sont documentés ;
- le ledger est documenté ;
- le KYC et le KYB sont documentés ;
- les agents sont documentés ;
- les commerçants sont documentés ;
- les TPE sont documentés ;
- les DAB sont documentés ;
- les applications sont documentées ;
- les guides utilisateurs sont disponibles ;
- les guides administrateurs sont disponibles ;
- la base de connaissances est disponible ;
- les FAQ sont organisées ;
- la recherche fonctionne ;
- la recherche avancée fonctionne ;
- la recherche sémantique respecte les permissions ;
- les suggestions sont disponibles ;
- Jini peut répondre depuis les sources autorisées ;
- les versions sont gérées ;
- la comparaison de versions fonctionne ;
- les brouillons sont séparés ;
- les relectures sont gérées ;
- les workflows de validation sont configurables ;
- les validations renforcées existent ;
- les approbations sont historisées ;
- les rejets sont gérés ;
- les publications sont ciblables ;
- les aides contextuelles sont supportées ;
- les tutoriels sont supportés ;
- les traductions sont versionnées ;
- les traductions obsolètes sont détectées ;
- le glossaire est centralisé ;
- le multi-pays est pris en charge ;
- les variantes locales sont supportées ;
- la documentation partenaire est disponible ;
- le portail développeurs est alimenté ;
- les SDK peuvent être documentés ;
- les exemples de code sont versionnés ;
- la documentation de sécurité est protégée ;
- les niveaux de sensibilité sont appliqués ;
- les contrôles d’accès fonctionnent ;
- les accès temporaires expirent ;
- le partage externe est contrôlé ;
- les téléchargements sont administrables ;
- les impressions sont administrables ;
- les filigranes sont supportés ;
- l’archivage fonctionne ;
- les politiques de rétention sont appliquées ;
- le Legal Hold est supporté ;
- les suppressions sont protégées ;
- les documents peuvent être liés aux services ;
- la liaison GitHub fonctionne ;
- Documentation as Code est supportée ;
- les conflits sont détectés ;
- les documents obsolètes sont détectés ;
- les revues périodiques sont planifiées ;
- les rappels sont envoyés ;
- les signalements sont gérés ;
- les commentaires sont supportés ;
- la coédition est supportée ;
- le verrouillage fonctionne ;
- les notifications sont disponibles ;
- les abonnements sont disponibles ;
- les tableaux de bord sont disponibles ;
- les statistiques sont calculées ;
- les recherches sans résultat sont analysées ;
- l’accessibilité est prise en charge ;
- les documents hors ligne sont supportés ;
- les exports sont disponibles ;
- les imports sont contrôlés ;
- les fichiers sont scannés ;
- les secrets sont détectés ;
- les données personnelles sont protégées ;
- les rôles et permissions sont définis ;
- les approbations critiques sont protégées ;
- les intégrations fonctionnent ;
- les rapports sont disponibles ;
- les audits sont immuables ;
- les tests couvrent les parcours essentiels.
