# 36 — Protection des données personnelles, confidentialité, droits utilisateurs et gouvernance des données de Mansa

## 1. Objet du document

Ce document définit l’architecture officielle de protection des données personnelles de Mansa.

Il couvre :

- les données des particuliers ;
- les données des commerçants ;
- les données des employés ;
- les données des partenaires ;
- les données des agents publics ;
- les données biométriques ;
- les données financières ;
- les données KYC et KYB ;
- les données de fraude ;
- les données de localisation ;
- les données des appareils ;
- les consentements ;
- les finalités ;
- les bases de traitement ;
- la minimisation ;
- les durées de conservation ;
- les droits des personnes ;
- les demandes d’accès ;
- les demandes de rectification ;
- les demandes d’effacement ;
- les demandes de portabilité ;
- les oppositions ;
- les restrictions ;
- les transferts internationaux ;
- les sous-traitants ;
- les violations de données ;
- la confidentialité ;
- la gouvernance ;
- l’audit ;
- les obligations multi-pays.

L’objectif est de garantir que les données traitées par Mansa soient :

- collectées pour une finalité légitime ;
- limitées au strict nécessaire ;
- protégées ;
- accessibles uniquement aux personnes autorisées ;
- conservées pendant une durée justifiée ;
- traçables ;
- rectifiables ;
- exportables lorsque nécessaire ;
- supprimables ou anonymisables lorsque possible ;
- traitées conformément aux règles applicables dans chaque pays.

---

# 2. Principes fondamentaux

## 2.1 Privacy by Design

La protection des données doit être intégrée dès la conception de :

- l’application Client ;
- l’application Commerce ;
- l’application TPE ;
- l’application Admin Lite ;
- le Hub ;
- le portail Admin ;
- le backend ;
- les APIs ;
- les bases ;
- les intégrations ;
- Jini ;
- les services publics.

Elle ne doit pas être ajoutée uniquement après le développement.

---

## 2.2 Privacy by Default

Par défaut, le système doit utiliser les paramètres les plus protecteurs compatibles avec le service.

Exemples :

- visibilité limitée ;
- consentements marketing désactivés ;
- données sensibles masquées ;
- géolocalisation désactivée sans besoin ;
- partage partenaire limité ;
- conservation minimale ;
- accès administrateur restreint.

---

## 2.3 Minimisation

Mansa ne collecte que les données nécessaires.

Chaque champ doit avoir :

- une finalité ;
- un propriétaire ;
- une durée ;
- une classification ;
- un niveau de sensibilité ;
- une justification.

---

## 2.4 Séparation des finalités

Une donnée collectée pour une finalité ne doit pas être réutilisée librement pour une autre finalité incompatible.

Exemple :

Une pièce KYC ne doit pas être réutilisée automatiquement pour une campagne marketing.

---

## 2.5 Accès minimal

Chaque utilisateur, employé, service ou partenaire ne doit accéder qu’aux données nécessaires à sa mission.

---

## 2.6 Traçabilité

Toute consultation sensible doit pouvoir être reliée à :

- un acteur ;
- un rôle ;
- une ressource ;
- une finalité ;
- un ticket ou dossier ;
- une date ;
- un pays ;
- un environnement ;
- une corrélation.

---

# 3. Catégories de personnes concernées

Les personnes concernées peuvent être :

- utilisateurs particuliers ;
- représentants légaux ;
- mineurs ;
- commerçants ;
- dirigeants ;
- bénéficiaires effectifs ;
- employés de commerces ;
- agents publics ;
- employés Mansa ;
- prestataires ;
- partenaires ;
- contacts professionnels ;
- bénéficiaires ;
- personnes apparaissant dans des documents ;
- visiteurs des sites ;
- utilisateurs des APIs.

---

# 4. Catégories de données

## 4.1 Identité

- nom ;
- prénom ;
- date de naissance ;
- lieu de naissance ;
- nationalité ;
- sexe lorsque nécessaire ;
- photo ;
- signature ;
- numéro d’identité ;
- document ;
- identifiants administratifs.

---

## 4.2 Coordonnées

- téléphone ;
- e-mail ;
- adresse ;
- pays ;
- région ;
- commune ;
- langue ;
- contact d’urgence lorsque nécessaire.

---

## 4.3 Données financières

- wallet ;
- comptes ;
- soldes ;
- transactions ;
- paiements ;
- transferts ;
- frais ;
- remboursements ;
- cartes ;
- règlements ;
- revenus déclarés ;
- source des fonds.

---

## 4.4 Données professionnelles

- entreprise ;
- emploi ;
- fonction ;
- employeur ;
- activité ;
- registre ;
- numéro fiscal ;
- bénéficiaires effectifs ;
- mandat ;
- autorisations.

---

## 4.5 Données techniques

- adresse IP ;
- identifiant appareil ;
- système d’exploitation ;
- version ;
- logs ;
- session ;
- navigateur ;
- token Push ;
- empreinte technique ;
- paramètres réseau.

---

## 4.6 Données de localisation

- pays ;
- ville ;
- coordonnées ;
- position approximative ;
- position précise lorsque autorisée ;
- emplacement TPE ;
- historique de déplacement strictement nécessaire.

---

## 4.7 Données biométriques

- selfie ;
- représentation faciale ;
- preuve de vie ;
- résultat de comparaison ;
- gabarit biométrique lorsque utilisé ;
- résultat de biométrie locale.

Mansa doit éviter de centraliser une donnée biométrique lorsque la validation peut rester locale sur l’appareil.

---

## 4.8 Données de conformité

- niveau KYC ;
- documents ;
- résultats de vérification ;
- sanctions ;
- PEP ;
- alertes AML ;
- dossiers de conformité ;
- décisions ;
- restrictions.

---

## 4.9 Données de fraude

- score ;
- appareil ;
- signaux ;
- IP ;
- bénéficiaires ;
- alertes ;
- preuves ;
- blocages ;
- modèles ;
- listes internes ;
- décisions.

---

## 4.10 Données de support

- tickets ;
- messages ;
- appels ;
- pièces jointes ;
- réclamations ;
- litiges ;
- médiations ;
- satisfaction ;
- notes internes.

---

# 5. Classification des données

## 5.1 Publique

Exemples :

- contenu du site ;
- coordonnées publiques d’un commerce ;
- horaires ;
- offres publiques ;
- documentation API publique.

## 5.2 Interne

Exemples :

- procédures ;
- métriques non sensibles ;
- configurations non secrètes ;
- documentation interne.

## 5.3 Confidentielle

Exemples :

- profil utilisateur ;
- transactions ;
- contrats ;
- données partenaires ;
- tickets ;
- données d’entreprise.

## 5.4 Hautement sensible

Exemples :

- documents d’identité ;
- biométrie ;
- données de carte ;
- secrets ;
- dossiers fraude ;
- alertes AML ;
- mots de passe ;
- PIN ;
- OTP ;
- clés privées.

---

# 6. Registre des traitements

Mansa doit maintenir un registre contenant :

- nom du traitement ;
- finalité ;
- personnes concernées ;
- données ;
- pays ;
- applications ;
- base applicable ;
- destinataires ;
- partenaires ;
- durée ;
- sécurité ;
- transferts ;
- responsable ;
- date de revue ;
- risques ;
- mesures.

---

# 7. Finalités

Exemples :

- création de compte ;
- authentification ;
- paiement ;
- transfert ;
- émission de carte ;
- fonctionnement TPE ;
- support ;
- KYC ;
- KYB ;
- fraude ;
- AML ;
- conformité ;
- facturation ;
- services publics ;
- statistiques ;
- amélioration produit ;
- marketing ;
- communication ;
- obligations légales.

---

# 8. Bases de traitement

Chaque traitement doit être rattaché à une base reconnue par la politique applicable.

Exemples possibles :

- exécution d’un contrat ;
- obligation réglementaire ;
- consentement ;
- intérêt légitime validé ;
- protection d’une personne ;
- mission de service public ;
- défense d’un droit ;
- prévention de la fraude.

Le choix doit être documenté par pays.

---

# 9. Consentement

Le consentement doit être :

- libre ;
- spécifique ;
- éclairé ;
- explicite lorsque nécessaire ;
- granulaire ;
- traçable ;
- révocable ;
- présenté dans une langue compréhensible.

---

# 10. Consentements distincts

Mansa doit distinguer :

- conditions contractuelles ;
- marketing ;
- cookies ;
- géolocalisation ;
- contacts ;
- biométrie ;
- profilage ;
- partage partenaire ;
- Jini ;
- communication commerciale.

---

# 11. Retrait du consentement

Le retrait doit être :

- simple ;
- accessible ;
- effectif ;
- tracé ;
- appliqué aux canaux concernés ;
- sans conséquence injustifiée sur les services non liés.

---

# 12. Preuve du consentement

Elle peut contenir :

- personne ;
- finalité ;
- version ;
- date ;
- pays ;
- langue ;
- canal ;
- appareil ;
- méthode ;
- statut ;
- date de retrait.

---

# 13. Données obligatoires et facultatives

Chaque formulaire doit indiquer :

- champ obligatoire ;
- champ facultatif ;
- finalité ;
- conséquence en cas de refus ;
- durée ;
- destinataires lorsque nécessaire.

---

# 14. Collecte directe et indirecte

## 14.1 Collecte directe

Lorsque la personne fournit elle-même les données.

## 14.2 Collecte indirecte

Exemples :

- banque ;
- Mobile Money ;
- commerçant ;
- institution ;
- fournisseur KYC ;
- réseau carte ;
- partenaire public ;
- autre utilisateur.

La personne doit être informée lorsque requis.

---

# 15. Données des contacts

L’accès aux contacts du téléphone doit être :

- facultatif ;
- limité ;
- justifié ;
- révocable ;
- non utilisé pour importer tout le carnet sans nécessité.

Une alternative manuelle doit être disponible.

---

# 16. Géolocalisation

La géolocalisation peut être utilisée pour :

- commerces proches ;
- lutte contre la fraude ;
- localisation TPE ;
- sécurité ;
- services publics localisés ;
- conformité pays.

Elle doit distinguer :

- localisation approximative ;
- localisation précise ;
- utilisation en arrière-plan ;
- durée ;
- historique.

---

# 17. Caméra et microphone

La caméra peut être utilisée pour :

- KYC ;
- QR code ;
- document ;
- produit ;
- facture ;
- selfie.

Le microphone ne doit être activé que pour une finalité claire.

---

# 18. Notifications

Les tokens Push doivent être traités comme des identifiants techniques.

Ils doivent être :

- rattachés au bon appareil ;
- révoqués ;
- expirés ;
- protégés ;
- supprimés lorsqu’invalides.

---

# 19. Données biométriques

Le traitement biométrique doit être soumis à des contrôles renforcés.

Il doit préciser :

- finalité ;
- fournisseur ;
- stockage ;
- durée ;
- pays ;
- score ;
- accès ;
- suppression ;
- alternatives ;
- sécurité ;
- consentement ou autre base applicable.

---

# 20. Biométrie locale

Lorsque Face ID, Touch ID ou la biométrie Android est utilisée, Mansa doit privilégier la validation locale fournie par le système d’exploitation.

Mansa ne doit pas recevoir l’empreinte biométrique brute.

---

# 21. Données de carte

Mansa doit minimiser l’accès aux données de carte.

Utiliser :

- tokenisation ;
- masquage ;
- références ;
- chiffrement ;
- séparation ;
- prestataire certifié ;
- logs filtrés.

---

# 22. Données des mineurs

Lorsque les services aux mineurs sont disponibles, le système doit gérer :

- âge ;
- représentant légal ;
- consentement ;
- preuve ;
- plafonds ;
- confidentialité ;
- visibilité du responsable ;
- passage à la majorité.

---

# 23. Données des agents publics

Les données des agents doivent être limitées à :

- identité ;
- institution ;
- rôle ;
- matricule ;
- habilitation ;
- historique d’action ;
- appareil ;
- statut.

Le système doit empêcher la surveillance non justifiée de leur vie privée.

---

# 24. Données des employés Mansa

Elles doivent être séparées des données clients.

Exemples :

- identité ;
- rôle ;
- contrat ;
- accès ;
- formations ;
- actions ;
- incidents ;
- sanctions internes ;
- matériel.

---

# 25. Pseudonymisation

La pseudonymisation peut remplacer les identifiants directs par :

- identifiant opaque ;
- token ;
- hash ;
- référence ;
- clé séparée.

La clé de réidentification doit être protégée.

---

# 26. Anonymisation

Une donnée anonymisée ne doit plus permettre raisonnablement d’identifier une personne.

Les données anonymisées peuvent être utilisées pour :

- statistiques ;
- performance ;
- recherche ;
- amélioration ;
- reporting agrégé.

---

# 27. Différence entre pseudonymisation et anonymisation

Une donnée pseudonymisée reste une donnée personnelle si elle peut être reliée à une personne avec des informations supplémentaires.

Une donnée réellement anonymisée ne doit plus permettre cette réidentification.

---

# 28. Masquage

Exemples :

```text
Téléphone : +223 ** ** 45 67
Carte : **** **** **** 1234
E-mail : z***@example.com
Document : AB******12
```

Le niveau de masquage dépend du rôle.

---

# 29. Chiffrement

Les données doivent être chiffrées :

- en transit ;
- au repos ;
- dans les sauvegardes ;
- dans les exports ;
- dans le stockage documentaire ;
- dans les synchronisations ;
- dans les appareils lorsque nécessaire.

---

# 30. Clés de chiffrement

Les clés doivent être :

- séparées ;
- rotatives ;
- versionnées ;
- protégées ;
- limitées ;
- auditées ;
- récupérables selon une procédure contrôlée.

---

# 31. Accès aux données

L’accès doit dépendre de :

- rôle ;
- permission ;
- pays ;
- organisation ;
- tenant ;
- finalité ;
- ticket ;
- dossier ;
- niveau de sensibilité ;
- durée ;
- contexte de risque.

---

# 32. Accès justifié

Pour certaines données, l’agent doit fournir :

- motif ;
- ticket ;
- dossier ;
- durée ;
- approbation ;
- commentaire.

---

# 33. Accès d’urgence

L’accès d’urgence doit être :

- exceptionnel ;
- temporaire ;
- surveillé ;
- approuvé ;
- audité ;
- revu après usage ;
- révoqué automatiquement.

---

# 34. Consultation par les administrateurs

Chaque consultation sensible doit enregistrer :

- administrateur ;
- donnée ;
- utilisateur concerné ;
- motif ;
- heure ;
- durée ;
- action ;
- export éventuel ;
- environnement ;
- adresse technique.

---

# 35. Portail de confidentialité

L’utilisateur doit pouvoir accéder à :

- données principales ;
- consentements ;
- appareils ;
- sessions ;
- partenaires principaux ;
- préférences ;
- téléchargements ;
- demandes ;
- historique ;
- documents juridiques ;
- paramètres de confidentialité.

---

# 36. Droits des personnes

Selon les règles applicables, Mansa doit pouvoir gérer :

- droit d’information ;
- droit d’accès ;
- droit de rectification ;
- droit d’effacement ;
- droit de restriction ;
- droit d’opposition ;
- droit de portabilité ;
- droit de retrait ;
- droit de contestation d’une décision automatisée ;
- droit de réclamation.

---

# 37. Demande d’accès

La personne peut demander :

- quelles données sont traitées ;
- pourquoi ;
- d’où elles viennent ;
- avec qui elles sont partagées ;
- combien de temps elles sont conservées ;
- quelles décisions sont prises ;
- quels droits sont disponibles.

---

# 38. Vérification d’identité pour une demande

Avant de fournir des données, Mansa doit vérifier l’identité du demandeur.

Le niveau de vérification dépend :

- de la sensibilité ;
- du canal ;
- de l’état du compte ;
- du volume ;
- du représentant ;
- du pays.

---

# 39. Demande de rectification

La personne peut demander la correction de :

- nom ;
- adresse ;
- téléphone ;
- e-mail ;
- informations professionnelles ;
- données déclaratives.

Certaines données nécessitent :

- justificatif ;
- nouvelle vérification ;
- historique ;
- approbation.

---

# 40. Données non modifiables directement

Exemples :

- écriture ledger ;
- transaction validée ;
- historique d’audit ;
- décision réglementaire ;
- preuve d’acceptation.

Une correction doit utiliser :

- contre-écriture ;
- annotation ;
- nouvelle version ;
- rectification tracée ;
- décision complémentaire.

---

# 41. Demande d’effacement

L’effacement peut être refusé ou limité lorsque les données doivent être conservées pour :

- obligations financières ;
- KYC ;
- AML ;
- fraude ;
- litige ;
- audit ;
- contrat ;
- défense de droits ;
- legal hold ;
- sécurité.

---

# 42. Suppression de compte

La suppression visible du compte doit distinguer :

- désactivation ;
- clôture ;
- suppression logique ;
- anonymisation ;
- conservation obligatoire ;
- suppression finale.

---

# 43. Restriction de traitement

Une restriction peut empêcher certaines utilisations tout en conservant la donnée.

Exemples :

- blocage du marketing ;
- suspension d’un profilage ;
- limitation d’un partage ;
- gel pendant litige ;
- conservation sans usage actif.

---

# 44. Opposition

Une personne peut s’opposer à certains traitements lorsque la politique applicable le permet.

Le système doit enregistrer :

- traitement ;
- motif ;
- date ;
- décision ;
- résultat ;
- recours.

---

# 45. Portabilité

L’export peut inclure :

- profil ;
- coordonnées ;
- transactions ;
- bénéficiaires ;
- consentements ;
- préférences ;
- documents fournis ;
- historique pertinent.

Formats possibles :

- JSON ;
- CSV ;
- archive ;
- PDF pour lecture.

---

# 46. Export de données

L’export doit être :

- chiffré ;
- temporaire ;
- limité ;
- vérifié ;
- audité ;
- protégé par authentification ;
- supprimé après expiration.

---

# 47. Décision automatisée

Le système doit identifier les décisions prises principalement par :

- règles ;
- modèles ;
- scoring ;
- fraude ;
- conformité ;
- Jini ;
- éligibilité ;
- limites.

---

# 48. Explication d’une décision

Lorsque nécessaire, Mansa doit pouvoir fournir :

- catégorie de facteurs ;
- règle principale ;
- résultat ;
- impact ;
- possibilité de revue ;
- contact.

Les détails ne doivent pas révéler des mécanismes permettant de contourner la sécurité.

---

# 49. Revue humaine

Une revue humaine doit être disponible pour certaines décisions importantes.

Exemples :

- rejet KYC ;
- blocage fraude ;
- refus commerçant ;
- limitation importante ;
- suspension ;
- fermeture ;
- refus de remboursement.

---

# 50. Gestion des demandes

Chaque demande doit contenir :

- référence ;
- personne ;
- type ;
- pays ;
- canal ;
- date ;
- identité vérifiée ;
- statut ;
- responsable ;
- délai ;
- données concernées ;
- décision ;
- pièces ;
- communication ;
- clôture.

---

# 51. Statuts d’une demande

Valeurs possibles :

- RECEIVED ;
- IDENTITY_VERIFICATION_REQUIRED ;
- IN_REVIEW ;
- INFORMATION_REQUIRED ;
- APPROVED ;
- PARTIALLY_APPROVED ;
- REJECTED ;
- COMPLETED ;
- CLOSED ;
- APPEALED.

---

# 52. Délais

Les délais doivent être configurables par :

- pays ;
- type de demande ;
- complexité ;
- volume ;
- tiers impliqué ;
- litige ;
- réglementation.

---

# 53. Prolongation

Une prolongation doit être :

- justifiée ;
- notifiée ;
- datée ;
- limitée ;
- approuvée si nécessaire.

---

# 54. Représentant

Une demande peut être soumise par :

- représentant légal ;
- mandataire ;
- parent ;
- avocat ;
- organisation.

Le pouvoir doit être vérifié.

---

# 55. Demandes abusives ou répétitives

Mansa peut appliquer une procédure spécifique aux demandes :

- manifestement excessives ;
- répétitives ;
- frauduleuses ;
- impossibles à vérifier.

La décision doit être justifiée et auditable.

---

# 56. Conservation des données

Chaque catégorie doit avoir une règle de conservation.

La politique doit préciser :

- durée active ;
- durée d’archive ;
- événement de départ ;
- base ;
- pays ;
- anonymisation ;
- suppression ;
- legal hold ;
- responsable.

---

# 57. Événements de départ

Exemples :

- création ;
- dernière activité ;
- clôture ;
- fin de contrat ;
- paiement ;
- résolution du litige ;
- expiration du document ;
- fin du partenariat ;
- date de déclaration.

---

# 58. Moteur de rétention

Le système doit pouvoir :

- identifier les données expirées ;
- exclure les legal holds ;
- anonymiser ;
- archiver ;
- supprimer ;
- produire un rapport ;
- notifier les responsables ;
- enregistrer l’exécution.

---

# 59. Legal Hold

Un legal hold suspend la suppression en raison de :

- litige ;
- enquête ;
- fraude ;
- autorité ;
- audit ;
- incident ;
- recours.

Il doit contenir :

- périmètre ;
- motif ;
- responsable ;
- date ;
- durée ;
- levée ;
- audit.

---

# 60. Suppression sécurisée

La suppression doit couvrir lorsque possible :

- base ;
- stockage ;
- cache ;
- index de recherche ;
- fichiers ;
- exports ;
- appareils ;
- réplicas ;
- sauvegardes selon leur cycle.

---

# 61. Sauvegardes

Une donnée supprimée peut rester temporairement dans une sauvegarde protégée.

Elle ne doit pas être restaurée dans l’usage courant sans réapplication des règles de suppression.

---

# 62. Partage interne

Le partage entre équipes doit être limité.

Exemples :

- support ne voit pas tout le KYC ;
- marketing ne voit pas les alertes fraude ;
- commerce ne voit pas les données d’autres commerces ;
- pays A ne voit pas automatiquement le pays B.

---

# 63. Partage externe

Tout partage externe doit préciser :

- partenaire ;
- finalité ;
- données ;
- pays ;
- durée ;
- sécurité ;
- contrat ;
- sous-traitants ;
- suppression ;
- audit.

---

# 64. Sous-traitants

Chaque sous-traitant doit être enregistré avec :

- identité ;
- service ;
- données ;
- pays ;
- régions ;
- contrat ;
- sécurité ;
- durée ;
- sous-traitants ultérieurs ;
- date de revue ;
- statut.

---

# 65. Transferts internationaux

Un transfert doit être évalué selon :

- pays source ;
- pays destination ;
- type de données ;
- fournisseur ;
- nécessité ;
- garanties ;
- accès ;
- chiffrement ;
- contrat ;
- stockage ;
- support ;
- obligations locales.

---

# 66. Localisation des données

Mansa doit pouvoir configurer :

- pays de stockage ;
- région ;
- réplication ;
- sauvegarde ;
- traitement ;
- support ;
- accès administrateur ;
- transfert.

---

# 67. Données souveraines

Certaines données peuvent nécessiter :

- stockage national ;
- région dédiée ;
- base séparée ;
- clés locales ;
- accès restreint ;
- interdiction de transfert ;
- partenaire agréé.

---

# 68. Inventaire des flux

Mansa doit cartographier les flux entre :

- applications ;
- API Gateway ;
- services ;
- bases ;
- partenaires ;
- pays ;
- stockage ;
- analytics ;
- Jini ;
- support ;
- services publics.

---

# 69. Analyse d’impact

Une analyse d’impact doit être réalisée lorsque le traitement présente un risque élevé.

Exemples :

- biométrie ;
- géolocalisation continue ;
- scoring important ;
- fraude ;
- surveillance ;
- données publiques sensibles ;
- croisement massif ;
- IA ;
- mineurs ;
- données à grande échelle.

---

# 70. Contenu d’une analyse d’impact

Elle doit inclure :

- traitement ;
- finalité ;
- données ;
- personnes ;
- nécessité ;
- proportionnalité ;
- risques ;
- mesures ;
- accès ;
- partenaires ;
- conservation ;
- décision ;
- validation ;
- date de revue.

---

# 71. Revue de nouveaux produits

Avant lancement, chaque produit doit répondre à une checklist :

- quelles données ;
- pourquoi ;
- base ;
- pays ;
- accès ;
- partenaires ;
- durée ;
- droits ;
- sécurité ;
- consentement ;
- suppression ;
- risques ;
- tests.

---

# 72. Cookies et traceurs

Le système doit classifier :

- essentiels ;
- préférences ;
- mesure ;
- publicité ;
- partenaires ;
- sécurité.

---

# 73. Gestionnaire de préférences

L’utilisateur doit pouvoir :

- accepter ;
- refuser ;
- personnaliser ;
- modifier ;
- consulter la durée ;
- consulter les partenaires.

---

# 74. Analytics

Les analytics doivent privilégier :

- données agrégées ;
- pseudonymisation ;
- minimisation ;
- limitation de rétention ;
- consentement lorsque nécessaire ;
- exclusion des données sensibles.

---

# 75. Jini et confidentialité

Jini ne doit accéder qu’aux données nécessaires à la demande.

Le système doit contrôler :

- contexte ;
- outils ;
- rôle ;
- finalité ;
- historique ;
- données sensibles ;
- fournisseur ;
- conservation ;
- entraînement ;
- logs ;
- export.

---

# 76. Entraînement des modèles

Les données Mansa ne doivent pas être utilisées pour entraîner un modèle externe sans :

- autorisation ;
- contrat ;
- finalité ;
- protection ;
- anonymisation ;
- gouvernance ;
- validation juridique ;
- information appropriée.

---

# 77. Prompts et réponses

Les prompts et réponses contenant des données sensibles doivent être :

- minimisés ;
- protégés ;
- filtrés ;
- soumis à rétention ;
- accessibles par permission ;
- exclus des logs ordinaires.

---

# 78. Environnements non production

Les environnements hors production ne doivent pas utiliser librement des données réelles.

Utiliser :

- données fictives ;
- données synthétiques ;
- données anonymisées ;
- sous-ensembles contrôlés ;
- masquage ;
- accès limité.

---

# 79. Copies de production

Toute copie doit être :

- approuvée ;
- justifiée ;
- limitée ;
- chiffrée ;
- anonymisée ;
- datée ;
- supprimée après usage ;
- auditée.

---

# 80. Violation de données

Une violation peut concerner :

- accès non autorisé ;
- perte ;
- divulgation ;
- modification ;
- suppression ;
- chiffrement malveillant ;
- export ;
- erreur destinataire ;
- secret exposé ;
- appareil perdu.

---

# 81. Détection d’une violation

Sources possibles :

- alerte sécurité ;
- utilisateur ;
- partenaire ;
- employé ;
- audit ;
- monitoring ;
- support ;
- autorité ;
- fournisseur.

---

# 82. Dossier de violation

Il doit contenir :

- date ;
- découverte ;
- cause ;
- données ;
- personnes ;
- pays ;
- volume ;
- impact ;
- risques ;
- mesures ;
- notification ;
- responsables ;
- clôture ;
- actions correctives.

---

# 83. Réponse à une violation

Étapes :

1. détecter ;
2. contenir ;
3. préserver les preuves ;
4. analyser ;
5. évaluer le risque ;
6. corriger ;
7. notifier selon les obligations ;
8. informer les personnes lorsque nécessaire ;
9. surveiller ;
10. produire un rapport ;
11. améliorer.

---

# 84. Notification d’une violation

La décision doit tenir compte :

- du pays ;
- de la nature ;
- du volume ;
- du chiffrement ;
- du risque ;
- des personnes ;
- des obligations ;
- des délais ;
- des partenaires.

---

# 85. Communication aux personnes

Elle doit expliquer :

- ce qui s’est passé ;
- quelles données ;
- quels risques ;
- quelles mesures ;
- ce que la personne peut faire ;
- comment contacter Mansa ;
- quelles protections sont disponibles.

---

# 86. Confidentialité des employés

Les employés doivent signer et respecter :

- engagement de confidentialité ;
- politique d’accès ;
- politique de sécurité ;
- règles d’usage ;
- interdiction de consultation abusive ;
- procédure d’incident.

---

# 87. Formation

Les formations doivent couvrir :

- données personnelles ;
- phishing ;
- support ;
- fraude interne ;
- droits ;
- incidents ;
- exports ;
- mots de passe ;
- partage ;
- documents ;
- Jini.

---

# 88. Contrôles internes

Exemples :

- revue des accès ;
- échantillonnage ;
- détection de consultation abusive ;
- contrôle des exports ;
- contrôle des suppressions ;
- vérification des consentements ;
- vérification de la rétention ;
- audit partenaires.

---

# 89. Responsable de gouvernance

Mansa doit attribuer des responsabilités claires pour :

- registre ;
- demandes ;
- incidents ;
- partenaires ;
- rétention ;
- analyses d’impact ;
- politiques ;
- formation ;
- audit ;
- pays.

---

# 90. Administration

Le portail Admin doit permettre :

- consulter le registre ;
- gérer les finalités ;
- gérer les durées ;
- consulter les consentements ;
- traiter les demandes ;
- lancer un export ;
- lancer une rectification ;
- lancer une anonymisation ;
- gérer les legal holds ;
- consulter les sous-traitants ;
- suivre les violations ;
- consulter les audits ;
- produire des rapports.

---

# 91. Permissions

Exemples :

```text
privacy.registry.read
privacy.registry.manage
privacy.consent.read
privacy.consent.manage
privacy.request.read
privacy.request.assign
privacy.request.approve
privacy.request.complete
privacy.export.create
privacy.rectification.execute
privacy.erasure.execute
privacy.anonymization.execute
privacy.retention.read
privacy.retention.manage
privacy.legal_hold.manage
privacy.processor.read
privacy.processor.manage
privacy.breach.read
privacy.breach.manage
privacy.audit.read
```

---

# 92. Actions critiques

Doivent être protégées :

- export massif ;
- effacement ;
- anonymisation ;
- levée de legal hold ;
- modification d’une durée ;
- accès aux données biométriques ;
- transfert international ;
- ajout d’un sous-traitant ;
- copie de production ;
- clôture d’une violation.

---

# 93. Double validation

Peut être exigée pour :

- suppression massive ;
- export sensible ;
- données biométriques ;
- changement global de rétention ;
- transfert vers un nouveau pays ;
- ajout d’un fournisseur critique ;
- levée de legal hold ;
- notification de violation ;
- réutilisation de données.

---

# 94. API

Exemples :

```http
GET    /privacy/treatments
POST   /privacy/treatments
PATCH  /privacy/treatments/{id}

GET    /privacy/consents
POST   /privacy/consents
POST   /privacy/consents/{id}/withdraw

POST   /privacy/requests
GET    /privacy/requests
GET    /privacy/requests/{id}
POST   /privacy/requests/{id}/verify
POST   /privacy/requests/{id}/approve
POST   /privacy/requests/{id}/complete

POST   /privacy/exports
POST   /privacy/rectifications
POST   /privacy/erasures
POST   /privacy/anonymizations

GET    /privacy/retention-policies
POST   /privacy/legal-holds

GET    /privacy/breaches
POST   /privacy/breaches
```

---

# 95. Modèles

- DataSubject
- PersonalDataCategory
- DataClassification
- ProcessingActivity
- ProcessingPurpose
- ProcessingLegalBasis
- DataCollectionSource
- PrivacyConsent
- PrivacyConsentVersion
- PrivacyPreference
- PrivacyRequest
- PrivacyRequestVerification
- PrivacyRequestDecision
- PrivacyExport
- PrivacyRectification
- PrivacyErasure
- PrivacyRestriction
- PrivacyObjection
- PrivacyPortability
- RetentionPolicy
- RetentionExecution
- LegalHold
- DataProcessor
- InternationalTransfer
- PrivacyImpactAssessment
- DataBreach
- DataBreachNotification
- PrivacyAudit

---

# 96. Règles métier

1. Toute donnée possède une finalité.
2. Toute donnée possède une classification.
3. Toute donnée possède une durée.
4. Les collectes sont minimisées.
5. Les consentements sont versionnés.
6. Les consentements facultatifs sont révocables.
7. Les données sensibles sont masquées.
8. Les accès sont limités.
9. Les consultations sensibles sont auditées.
10. Les environnements hors production utilisent des données protégées.
11. Les copies de production sont contrôlées.
12. Les droits utilisateurs sont traitables.
13. Les demandes exigent une vérification d’identité.
14. Les exports sont temporaires.
15. Les données financières immuables ne sont pas supprimées directement.
16. Les effacements respectent les obligations de conservation.
17. Les legal holds bloquent la suppression.
18. Les données expirées sont supprimées ou anonymisées.
19. Les sous-traitants sont enregistrés.
20. Les transferts internationaux sont évalués.
21. Les analyses d’impact sont réalisées pour les traitements à risque.
22. Jini respecte les permissions et finalités.
23. Les violations sont documentées.
24. Les employés sont formés.
25. Les actions critiques sont approuvées et auditées.

---

# 97. Analytics

Événements possibles :

```text
privacy_consent_granted
privacy_consent_withdrawn
privacy_preference_updated
privacy_request_created
privacy_request_verified
privacy_request_approved
privacy_request_rejected
privacy_export_created
privacy_rectification_completed
privacy_erasure_started
privacy_erasure_completed
privacy_anonymization_completed
privacy_retention_execution_started
privacy_retention_execution_completed
privacy_legal_hold_created
privacy_legal_hold_removed
privacy_breach_created
privacy_breach_notification_sent
privacy_impact_assessment_completed
```

---

# 98. Tests

- tests de minimisation ;
- tests de consentement ;
- tests de retrait ;
- tests de préférences ;
- tests de masquage ;
- tests de permissions ;
- tests d’accès justifié ;
- tests d’export ;
- tests de rectification ;
- tests d’effacement ;
- tests d’anonymisation ;
- tests de restriction ;
- tests d’opposition ;
- tests de portabilité ;
- tests de legal hold ;
- tests de rétention ;
- tests de suppression ;
- tests de sauvegarde ;
- tests de sous-traitants ;
- tests de transfert ;
- tests multi-pays ;
- tests biométriques ;
- tests Jini ;
- tests de violation ;
- tests de double validation ;
- tests d’audit.

---

# 99. Critères d’acceptation

La protection des données personnelles est validée lorsque :

- les catégories de données sont inventoriées ;
- les finalités sont documentées ;
- les données sont classifiées ;
- les consentements sont versionnés ;
- les préférences sont administrables ;
- les accès sont limités ;
- les données sensibles sont masquées ;
- les consultations sont auditées ;
- les utilisateurs peuvent exercer leurs droits ;
- les demandes sont vérifiées ;
- les exports sont sécurisés ;
- les rectifications sont traçables ;
- les effacements respectent les obligations ;
- les durées sont automatisées ;
- les legal holds sont gérés ;
- les sous-traitants sont enregistrés ;
- les transferts internationaux sont documentés ;
- les traitements à risque disposent d’une analyse d’impact ;
- Jini respecte les règles de confidentialité ;
- les violations disposent d’un workflow ;
- les actions critiques sont protégées ;
- les tests couvrent les scénarios principaux.
