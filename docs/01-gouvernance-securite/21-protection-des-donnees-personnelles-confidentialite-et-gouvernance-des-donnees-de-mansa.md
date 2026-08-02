# 21 — Protection des données personnelles, confidentialité et gouvernance des données de Mansa

## 1. Objet du document

Ce document définit la politique officielle de protection des données personnelles et de gouvernance des données de Mansa.

Il couvre :

- les données des utilisateurs particuliers ;
- les données des commerçants ;
- les données des employés ;
- les données des administrateurs ;
- les données des partenaires ;
- les données des agents publics ;
- les données financières ;
- les données d’identité ;
- les données de localisation ;
- les données biométriques indirectes ;
- les données issues de Jini ;
- les documents ;
- les journaux ;
- les analytics ;
- les exports ;
- les sauvegardes ;
- les durées de conservation ;
- les consentements ;
- les droits des personnes ;
- le partage avec des tiers ;
- les transferts internationaux ;
- l’anonymisation ;
- la suppression ;
- la gouvernance des accès.

L’objectif est de garantir que les données traitées par Mansa soient :

- collectées pour une finalité claire ;
- limitées au strict nécessaire ;
- exactes ;
- protégées ;
- accessibles uniquement aux personnes autorisées ;
- conservées pendant une durée justifiée ;
- supprimées ou anonymisées lorsque possible ;
- traçables ;
- conformes aux obligations applicables.

---

# 2. Principes fondamentaux

## 2.1 Privacy by Design

La protection de la vie privée doit être intégrée dès la conception de chaque fonctionnalité.

Avant de développer un module, il faut déterminer :

- quelles données sont nécessaires ;
- pourquoi elles sont nécessaires ;
- qui peut y accéder ;
- combien de temps elles seront conservées ;
- avec quels partenaires elles seront partagées ;
- comment elles seront protégées ;
- comment l’utilisateur pourra exercer ses droits.

---

## 2.2 Privacy by Default

Les paramètres par défaut doivent être les plus protecteurs raisonnablement possibles.

Exemples :

- profil non public par défaut ;
- localisation précise désactivée sans nécessité ;
- communications marketing désactivables ;
- aperçu sensible masqué sur écran verrouillé ;
- partage de données limité ;
- visibilité des transactions privées restreinte.

---

## 2.3 Minimisation des données

Mansa ne doit collecter que les données nécessaires à une finalité définie.

Une donnée ne doit pas être collectée uniquement parce qu’elle pourrait être utile plus tard.

---

## 2.4 Limitation des finalités

Une donnée collectée pour une finalité ne doit pas être réutilisée pour une finalité incompatible sans base appropriée.

Exemple :

Un document KYC ne doit pas être réutilisé automatiquement à des fins publicitaires.

---

## 2.5 Exactitude

Les données doivent pouvoir être :

- corrigées ;
- mises à jour ;
- vérifiées ;
- marquées comme anciennes ;
- remplacées sans perdre l’historique nécessaire.

---

## 2.6 Conservation limitée

Chaque catégorie de données doit avoir une durée de conservation définie.

Une conservation indéfinie sans justification est interdite.

---

## 2.7 Responsabilité

Chaque traitement doit avoir :

- un propriétaire métier ;
- une finalité ;
- une base ;
- une durée ;
- des destinataires ;
- des mesures de sécurité ;
- une documentation ;
- un audit.

---

# 3. Catégories de données

## 3.1 Données d’identité

Exemples :

- nom ;
- prénom ;
- date de naissance ;
- sexe lorsque nécessaire ;
- nationalité ;
- numéro de document ;
- photographie ;
- signature ;
- pays de résidence.

---

## 3.2 Données de contact

Exemples :

- téléphone ;
- e-mail ;
- adresse ;
- ville ;
- quartier ;
- pays ;
- contact d’urgence ;
- préférences de communication.

---

## 3.3 Données financières

Exemples :

- solde ;
- transactions ;
- bénéficiaires ;
- comptes ;
- cartes ;
- virements ;
- paiements ;
- remboursements ;
- investissements ;
- revenus déclarés ;
- frais ;
- commissions.

---

## 3.4 Données KYC et KYB

Exemples :

- documents d’identité ;
- justificatif de domicile ;
- registre du commerce ;
- bénéficiaires effectifs ;
- activité professionnelle ;
- origine des fonds ;
- justificatifs ;
- résultat de vérification ;
- niveau de risque.

---

## 3.5 Données techniques

Exemples :

- adresse IP ;
- appareil ;
- système d’exploitation ;
- version d’application ;
- identifiant de session ;
- navigateur ;
- identifiant du terminal ;
- journaux techniques ;
- identifiants de corrélation.

---

## 3.6 Données de localisation

Exemples :

- pays ;
- ville ;
- position approximative ;
- position précise ;
- localisation d’un paiement ;
- localisation d’un TPE ;
- zone de connexion.

La précision collectée doit être proportionnée à la finalité.

---

## 3.7 Données comportementales

Exemples :

- écrans consultés ;
- fonctions utilisées ;
- fréquence ;
- parcours ;
- clics ;
- abandons ;
- préférences ;
- catégories de dépenses.

Ces données doivent être utilisées de manière transparente.

---

## 3.8 Données de communication

Exemples :

- messages Mansa Connect ;
- demandes d’argent ;
- échanges avec le support ;
- commentaires ;
- pièces jointes ;
- notifications ;
- préférences.

Le contenu privé doit bénéficier de protections renforcées.

---

## 3.9 Données sensibles ou hautement sensibles

Exemples :

- identité ;
- documents ;
- données financières détaillées ;
- secrets d’authentification ;
- informations de fraude ;
- données de santé si un service futur en traite ;
- données judiciaires si une obligation l’exige ;
- informations politiques ou religieuses si elles apparaissent accidentellement.

Mansa ne doit pas collecter de données sensibles sans nécessité explicite.

---

# 4. Classification des données

Chaque donnée doit être classée.

Niveaux recommandés :

- PUBLIC ;
- INTERNAL ;
- CONFIDENTIAL ;
- SENSITIVE ;
- HIGHLY_SENSITIVE.

Chaque niveau définit :

- les personnes autorisées ;
- le chiffrement ;
- le masquage ;
- la conservation ;
- l’export ;
- le partage ;
- l’audit ;
- la sauvegarde.

---

# 5. Registre des traitements

Mansa doit maintenir un registre des traitements.

Chaque traitement doit indiquer :

- nom ;
- description ;
- finalité ;
- catégories de personnes ;
- catégories de données ;
- base de traitement ;
- destinataires ;
- partenaires ;
- pays ;
- durée de conservation ;
- mesures de sécurité ;
- transferts ;
- propriétaire ;
- date de revue ;
- risques ;
- sous-traitants.

---

# 6. Bases de traitement

Selon le pays et la situation, une opération peut reposer sur :

- exécution d’un contrat ;
- obligation légale ;
- consentement ;
- intérêt légitime ;
- mission d’intérêt public ;
- protection contre la fraude ;
- obligation de conformité.

La base doit être documentée.

---

# 7. Consentement

Un consentement doit être :

- libre ;
- spécifique ;
- éclairé ;
- explicite lorsque nécessaire ;
- distinct ;
- révocable ;
- traçable.

Il ne doit pas être caché dans un texte général.

---

# 8. Structure d’un consentement

Chaque consentement doit contenir :

- utilisateur ;
- type ;
- finalité ;
- version ;
- langue ;
- pays ;
- date ;
- canal ;
- statut ;
- retrait ;
- preuve ;
- appareil ;
- document associé ;
- date d’effet.

---

# 9. Retrait du consentement

Le retrait doit être :

- simple ;
- accessible ;
- pris en compte rapidement ;
- sans conséquence injustifiée ;
- audité.

Le retrait ne doit pas supprimer les traitements nécessaires à :

- l’exécution du contrat ;
- la sécurité ;
- la conformité ;
- la conservation légale ;
- la prévention de fraude.

---

# 10. Transparence

L’utilisateur doit pouvoir comprendre :

- quelles données sont collectées ;
- pourquoi ;
- pendant combien de temps ;
- avec qui elles sont partagées ;
- quels droits il possède ;
- comment contacter Mansa ;
- comment déposer une demande ;
- comment retirer un consentement.

---

# 11. Politique de confidentialité

La politique doit être :

- claire ;
- accessible ;
- traduite ;
- versionnée ;
- adaptée au pays ;
- datée ;
- liée aux traitements réels ;
- consultable avant l’inscription ;
- consultable après acceptation.

---

# 12. Droits des personnes

Le système doit pouvoir prendre en charge, selon les règles applicables :

- droit d’accès ;
- droit de rectification ;
- droit à l’effacement ;
- droit à la limitation ;
- droit d’opposition ;
- droit à la portabilité ;
- retrait du consentement ;
- droit à l’information ;
- contestation d’une décision automatisée ;
- demande de copie.

---

# 13. Demande d’exercice de droit

Une demande doit contenir :

- identifiant ;
- personne ;
- type de droit ;
- pays ;
- date ;
- statut ;
- identité vérifiée ;
- périmètre ;
- délai ;
- responsable ;
- réponse ;
- pièces ;
- décision ;
- motif éventuel ;
- audit.

---

# 14. Vérification d’identité

Avant de remettre ou modifier des données, Mansa doit vérifier l’identité du demandeur.

La vérification doit être proportionnée et ne pas demander plus de données que nécessaire.

---

# 15. Portabilité

Lorsque applicable, l’utilisateur peut recevoir ses données dans un format exploitable.

Formats possibles :

- JSON ;
- CSV ;
- PDF pour lecture ;
- archive structurée.

L’export doit être :

- sécurisé ;
- temporaire ;
- chiffré si nécessaire ;
- protégé par authentification ;
- audité ;
- expirant.

---

# 16. Droit à l’effacement

Une demande d’effacement peut être partiellement refusée lorsque des données doivent être conservées pour :

- obligations légales ;
- comptabilité ;
- lutte contre la fraude ;
- litiges ;
- sécurité ;
- obligations partenaires ;
- services publics ;
- conservation de preuves.

La décision doit être expliquée.

---

# 17. Anonymisation

L’anonymisation doit empêcher raisonnablement toute réidentification.

Elle peut être utilisée pour :

- statistiques ;
- recherche ;
- amélioration produit ;
- rapports ;
- apprentissage interne ;
- conservation longue.

Une donnée seulement masquée n’est pas forcément anonymisée.

---

# 18. Pseudonymisation

La pseudonymisation remplace les identifiants directs par des identifiants techniques.

La table de correspondance doit être :

- séparée ;
- protégée ;
- chiffrée ;
- accessible à très peu de rôles ;
- auditée.

---

# 19. Masquage des données

Exemples :

```text
Téléphone : +223 ** ** ** 45
E-mail : z***@example.com
Carte : **** **** **** 1234
Document : ********89
```

Le niveau de masquage dépend :

- du rôle ;
- du contexte ;
- du canal ;
- de la sensibilité ;
- de l’action.

---

# 20. Accès aux données personnelles

L’accès doit reposer sur :

- rôle ;
- permission ;
- finalité ;
- pays ;
- organisation ;
- dossier ;
- niveau de sensibilité ;
- besoin métier ;
- justification ;
- durée.

---

# 21. Accès support

Le support ne doit voir que les données nécessaires.

Exemples :

- identité limitée ;
- statut du compte ;
- transaction concernée ;
- derniers chiffres de carte ;
- historique du ticket.

L’accès à un document complet doit nécessiter une permission spécifique.

---

# 22. Accès administrateur

Les administrateurs ne doivent pas disposer automatiquement de tous les accès.

Les accès doivent être séparés entre :

- support ;
- conformité ;
- fraude ;
- finance ;
- technique ;
- sécurité ;
- audit ;
- direction.

---

# 23. Accès temporaire

Un accès temporaire doit contenir :

- personne ;
- raison ;
- périmètre ;
- début ;
- expiration ;
- approbateur ;
- ticket ;
- actions autorisées.

Il doit expirer automatiquement.

---

# 24. Accès d’urgence

L’accès d’urgence doit être :

- exceptionnel ;
- justifié ;
- limité ;
- surveillé ;
- notifié ;
- audité ;
- revu après usage.

---

# 25. Journalisation des accès

Les accès sensibles doivent enregistrer :

- utilisateur ;
- rôle ;
- ressource ;
- date ;
- action ;
- pays ;
- environnement ;
- motif ;
- résultat ;
- corrélation.

---

# 26. Partage avec des partenaires

Avant tout partage, Mansa doit vérifier :

- nécessité ;
- finalité ;
- base ;
- contrat ;
- sécurité ;
- pays ;
- durée ;
- sous-traitants ;
- droits de la personne ;
- procédure d’incident ;
- suppression.

---

# 27. Minimisation des échanges partenaires

Un partenaire ne doit recevoir que les champs nécessaires.

Exemple :

Pour vérifier un paiement, il peut être inutile de transmettre l’adresse complète ou le document d’identité du client.

---

# 28. Sous-traitants

Chaque sous-traitant doit être enregistré avec :

- nom ;
- service ;
- pays ;
- données traitées ;
- finalité ;
- contrat ;
- mesures de sécurité ;
- date de revue ;
- sous-traitants secondaires ;
- statut ;
- plan de sortie.

---

# 29. Transferts internationaux

Les transferts de données entre pays doivent être identifiés.

Chaque transfert doit documenter :

- pays d’origine ;
- pays de destination ;
- catégories de données ;
- destinataire ;
- base ;
- garanties ;
- durée ;
- chiffrement ;
- contrat ;
- risque.

---

# 30. Hébergement

La localisation des données doit pouvoir être définie selon :

- pays ;
- réglementation ;
- partenaire ;
- type de données ;
- environnement ;
- niveau de sensibilité.

---

# 31. Localisation des données

Certaines données peuvent devoir rester dans un pays ou une région.

Le système doit permettre :

- stockage local ;
- réplication contrôlée ;
- séparation logique ;
- séparation physique éventuelle ;
- chiffrement distinct ;
- contrôle d’accès par région.

---

# 32. Durées de conservation

Chaque catégorie doit avoir une politique.

Exemples :

- données de compte actif ;
- données KYC ;
- transactions ;
- tickets support ;
- logs ;
- audits ;
- notifications ;
- consentements ;
- fichiers temporaires ;
- exports ;
- données Jini ;
- données marketing.

---

# 33. Déclencheurs de conservation

La durée peut commencer à partir de :

- création ;
- dernière activité ;
- clôture du compte ;
- fin du contrat ;
- fin du litige ;
- date de transaction ;
- expiration du document ;
- retrait du consentement ;
- fin du service.

---

# 34. Legal Hold

Une suppression peut être suspendue en cas de :

- litige ;
- enquête ;
- fraude ;
- obligation légale ;
- demande d’autorité ;
- incident ;
- audit.

Le legal hold doit être :

- limité ;
- justifié ;
- documenté ;
- audité ;
- levé dès que possible.

---

# 35. Suppression automatisée

Le système doit pouvoir supprimer ou anonymiser automatiquement les données arrivées à expiration.

Le processus doit :

- identifier les données ;
- vérifier les exceptions ;
- créer une preuve ;
- journaliser ;
- contrôler les dépendances ;
- traiter les sauvegardes selon la politique.

---

# 36. Sauvegardes

Les données supprimées peuvent rester temporairement dans les sauvegardes.

La politique doit préciser :

- durée ;
- chiffrement ;
- accès ;
- restauration ;
- propagation de la suppression ;
- expiration naturelle.

Une donnée supprimée ne doit pas être restaurée définitivement par erreur.

---

# 37. Environnements hors production

Les données réelles ne doivent pas être copiées librement dans :

- développement ;
- test ;
- démonstration ;
- recette.

Lorsque des données réalistes sont nécessaires, elles doivent être :

- synthétiques ;
- anonymisées ;
- pseudonymisées ;
- réduites ;
- protégées.

---

# 38. Données de démonstration

Le mode Démo doit utiliser :

- comptes fictifs ;
- transactions fictives ;
- identités fictives ;
- documents fictifs ;
- cartes fictives ;
- partenaires simulés.

---

# 39. Analytics

Les analytics doivent appliquer :

- minimisation ;
- pseudonymisation ;
- agrégation ;
- consentement lorsque nécessaire ;
- limitation de conservation ;
- séparation produit et marketing ;
- contrôle des accès.

---

# 40. Publicité et personnalisation

La personnalisation doit être transparente.

L’utilisateur doit pouvoir distinguer :

- recommandations fonctionnelles ;
- recommandations financières ;
- promotions ;
- publicité ;
- contenu sponsorisé.

Les données sensibles ne doivent pas être utilisées pour du ciblage publicitaire sans base claire.

---

# 41. Profilage

Le profilage peut inclure :

- catégories de dépenses ;
- habitudes ;
- risques ;
- préférences ;
- segmentation ;
- recommandations.

Il doit être :

- documenté ;
- limité ;
- explicable ;
- sécurisé ;
- contestable lorsque nécessaire.

---

# 42. Décisions automatisées

Une décision automatisée importante doit pouvoir indiquer :

- finalité ;
- données utilisées ;
- règle ;
- modèle ;
- version ;
- résultat ;
- intervention humaine possible ;
- procédure de contestation.

---

# 43. Jini et données personnelles

Jini ne doit accéder qu’aux données nécessaires à la demande.

Il faut définir :

- contexte autorisé ;
- données interdites ;
- durée de conservation ;
- journalisation ;
- fournisseurs ;
- pays ;
- chiffrement ;
- consentement éventuel ;
- suppression.

---

# 44. Contenu des conversations Jini

Le contenu ne doit pas être utilisé automatiquement pour :

- publicité ;
- entraînement externe ;
- profilage sensible ;
- partage partenaire ;

sans règle explicite et transparente.

---

# 45. Pièces jointes

Les fichiers doivent être :

- analysés ;
- chiffrés ;
- limités en format ;
- limités en taille ;
- liés à une finalité ;
- soumis à une durée ;
- supprimés lorsque leur conservation n’est plus nécessaire.

---

# 46. Documents d’identité

Les documents d’identité doivent bénéficier de protections renforcées :

- chiffrement ;
- accès restreint ;
- masquage ;
- journalisation ;
- URL temporaires ;
- absence dans les logs ;
- suppression selon la politique ;
- interdiction de téléchargement non autorisé.

---

# 47. Données de carte

Mansa doit limiter le stockage des données de carte.

Les données sensibles doivent être :

- tokenisées ;
- masquées ;
- chiffrées ;
- traitées par des partenaires autorisés ;
- absentes des journaux ;
- protégées selon les obligations applicables.

---

# 48. Données de localisation

La localisation doit être :

- facultative lorsque possible ;
- précise uniquement si nécessaire ;
- limitée dans le temps ;
- visible dans les paramètres ;
- désactivable ;
- protégée ;
- non utilisée à une finalité cachée.

---

# 49. Contacts du téléphone

L’accès aux contacts doit être optionnel.

Le système doit proposer une alternative manuelle.

Mansa ne doit pas importer tous les contacts sans explication ni nécessité.

---

# 50. Caméra et microphone

Les permissions doivent être demandées au moment utile.

Exemples :

- scan de document ;
- scan QR ;
- preuve de vie ;
- support audio ;
- appel.

Une permission refusée doit avoir une alternative lorsque possible.

---

# 51. Notifications

Les notifications doivent éviter d’afficher des informations sensibles sur l’écran verrouillé.

L’utilisateur doit pouvoir choisir :

- aperçu complet ;
- aperçu limité ;
- contenu masqué ;
- aucune notification sensible.

---

# 52. Exports administratifs

Tout export doit contenir :

- demandeur ;
- finalité ;
- périmètre ;
- colonnes ;
- volume ;
- date ;
- expiration ;
- chiffrement ;
- approbation ;
- audit.

---

# 53. Téléchargements temporaires

Les fichiers exportés doivent utiliser :

- liens signés ;
- durée courte ;
- authentification ;
- nombre de téléchargements limité ;
- journalisation ;
- suppression automatique.

---

# 54. Violation de données

Une violation peut inclure :

- accès non autorisé ;
- perte ;
- divulgation ;
- altération ;
- suppression ;
- export frauduleux ;
- fuite partenaire ;
- secret compromis.

---

# 55. Gestion d’une violation

Le processus doit prévoir :

1. détection ;
2. confinement ;
3. analyse ;
4. identification des données ;
5. identification des personnes ;
6. évaluation de l’impact ;
7. notification interne ;
8. notification réglementaire si nécessaire ;
9. information des personnes si nécessaire ;
10. correction ;
11. suivi ;
12. rapport final.

---

# 56. Inventaire des données

Mansa doit savoir :

- quelles données existent ;
- où elles sont stockées ;
- qui en est propriétaire ;
- qui y accède ;
- quels services les utilisent ;
- quels partenaires les reçoivent ;
- combien de temps elles sont conservées.

---

# 57. Data Lineage

Le système doit pouvoir retracer le parcours d’une donnée :

- origine ;
- transformation ;
- stockage ;
- utilisation ;
- partage ;
- export ;
- suppression.

---

# 58. Qualité des données

Les contrôles doivent détecter :

- doublons ;
- valeurs manquantes ;
- formats invalides ;
- incohérences ;
- données expirées ;
- documents obsolètes ;
- références orphelines ;
- données contradictoires.

---

# 59. Propriétaires de données

Chaque domaine doit avoir un propriétaire.

Exemples :

- identité ;
- KYC ;
- paiements ;
- cartes ;
- commerce ;
- support ;
- Jini ;
- services publics ;
- analytics ;
- sécurité.

---

# 60. Administration

Le portail Admin doit permettre :

- consulter le registre ;
- consulter les politiques ;
- gérer les consentements ;
- traiter les demandes de droits ;
- suivre les exports ;
- suivre les suppressions ;
- consulter les accès sensibles ;
- configurer les durées ;
- appliquer un legal hold ;
- consulter les sous-traitants ;
- consulter les transferts ;
- générer des rapports.

---

# 61. Permissions

Exemples :

```text
privacy.read
privacy.policy.manage
privacy.consent.read
privacy.consent.manage
privacy.request.read
privacy.request.process
privacy.export.create
privacy.deletion.approve
privacy.legal_hold.manage
privacy.vendor.read
privacy.vendor.manage
privacy.transfer.read
privacy.audit.read
```

---

# 62. API

Exemples :

```http
GET    /privacy/policies
GET    /privacy/consents
PATCH  /privacy/consents

POST   /privacy/requests
GET    /privacy/requests
GET    /privacy/requests/{id}
PATCH  /privacy/requests/{id}

POST   /privacy/exports
POST   /privacy/deletions
POST   /privacy/legal-holds
DELETE /privacy/legal-holds/{id}

GET    /privacy/vendors
GET    /privacy/data-map
```

---

# 63. Modèles

- DataCategory
- DataClassification
- ProcessingActivity
- ProcessingPurpose
- LegalBasis
- Consent
- ConsentVersion
- PrivacyPolicy
- PrivacyRequest
- PrivacyRequestStatus
- DataExport
- DataDeletion
- DataRetentionPolicy
- LegalHold
- DataTransfer
- DataProcessor
- DataSubprocessor
- DataAccessRecord
- DataLineage
- DataOwner
- DataBreach
- PrivacyAudit

---

# 64. Règles métier

1. Toute donnée collectée possède une finalité.
2. Toute donnée possède une classification.
3. La collecte est limitée au nécessaire.
4. Les consentements sont versionnés.
5. Le retrait du consentement est traçable.
6. Les droits sont traités dans un workflow dédié.
7. Les données sensibles sont chiffrées.
8. Les accès sensibles sont audités.
9. Les exports expirent.
10. Les documents d’identité sont fortement protégés.
11. Les environnements de test n’utilisent pas librement de vraies données.
12. Les durées de conservation sont explicites.
13. Les suppressions respectent les exceptions légales.
14. Les données arrivées à expiration sont supprimées ou anonymisées.
15. Les transferts internationaux sont documentés.
16. Les partenaires reçoivent uniquement les données nécessaires.
17. Les décisions automatisées importantes sont explicables.
18. Jini respecte les permissions et finalités.
19. Les violations suivent une procédure officielle.
20. Les accès d’urgence sont audités.
21. Les exports administratifs sont protégés.
22. Les données de carte ne sont pas exposées.
23. Les permissions appareil sont demandées au moment utile.
24. La localisation précise n’est pas collectée sans nécessité.
25. Toute modification de politique est historisée.

---

# 65. Analytics

Événements possibles :

```text
privacy_policy_viewed
privacy_policy_accepted
privacy_consent_granted
privacy_consent_withdrawn
privacy_request_created
privacy_request_identity_verified
privacy_request_completed
privacy_export_generated
privacy_deletion_started
privacy_deletion_completed
privacy_legal_hold_created
privacy_sensitive_data_accessed
privacy_data_breach_detected
privacy_vendor_added
privacy_retention_policy_updated
```

---

# 66. Tests

- tests de consentement ;
- tests de retrait ;
- tests de droits ;
- tests d’export ;
- tests de suppression ;
- tests de conservation ;
- tests de legal hold ;
- tests de masquage ;
- tests d’autorisation ;
- tests d’accès support ;
- tests d’anonymisation ;
- tests de pseudonymisation ;
- tests de transfert ;
- tests multi-pays ;
- tests de sauvegarde ;
- tests de fichiers ;
- tests de notifications ;
- tests de localisation ;
- tests Jini ;
- tests de violation ;
- tests d’audit.

---

# 67. Critères d’acceptation

La protection des données personnelles est validée lorsque :

- les traitements sont inventoriés ;
- les finalités sont documentées ;
- les données sont classifiées ;
- les consentements sont traçables ;
- les utilisateurs peuvent exercer leurs droits ;
- les exports sont sécurisés ;
- les suppressions sont contrôlées ;
- les durées de conservation sont appliquées ;
- les accès sensibles sont audités ;
- les environnements hors production sont protégés ;
- les partenaires sont documentés ;
- les transferts internationaux sont identifiés ;
- les données Jini sont encadrées ;
- les documents d’identité sont protégés ;
- les violations suivent une procédure ;
- les politiques sont versionnées ;
- les tests couvrent les principaux risques.
