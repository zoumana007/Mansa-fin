# 46 — Application Admin Lite Mansa : opérations terrain, contrôle, support, incidents et interventions mobiles

## 1. Objet du document

Ce document définit l’architecture officielle de l’application **Mansa Admin Lite**.

Admin Lite est l’application mobile destinée aux équipes opérationnelles autorisées de Mansa.

Elle permet d’intervenir sur le terrain sans donner accès à l’ensemble du portail Admin Web.

Elle couvre :

- les agents ;
- les commerçants ;
- les TPE ;
- les DAB ;
- les clients ;
- les incidents ;
- les interventions ;
- les contrôles terrain ;
- les vérifications limitées ;
- les demandes de documents ;
- les suspensions temporaires ;
- la maintenance ;
- la fraude terrain ;
- les preuves ;
- les signatures ;
- la géolocalisation ;
- le mode réseau faible ;
- les notifications ;
- les permissions ;
- l’audit ;
- les validations ;
- les rapports ;
- la sécurité ;
- les tests ;
- le multi-pays ;
- le multi-rôle.

L’objectif est de fournir aux équipes terrain une application :

- sécurisée ;
- rapide ;
- simple ;
- limitée aux besoins réels ;
- adaptée aux déplacements ;
- utilisable avec une connexion faible ;
- entièrement traçable ;
- contrôlée par l’administration centrale.

---

# 2. Principes fondamentaux

## 2.1 Admin Lite n’est pas le portail Super Admin

Admin Lite ne doit pas donner automatiquement accès à :

- toutes les données clients ;
- toutes les transactions ;
- tous les paramètres ;
- toutes les permissions ;
- toutes les configurations ;
- tous les pays ;
- tous les partenaires ;
- toutes les actions financières.

L’accès dépend du rôle et du périmètre.

---

## 2.2 L’application est destinée au terrain

Admin Lite doit servir notamment :

- agents de contrôle ;
- agents d’installation ;
- techniciens ;
- superviseurs de zone ;
- support terrain ;
- responsables commerciaux ;
- agents conformité ;
- agents anti-fraude ;
- auditeurs mobiles ;
- responsables DAB ;
- responsables TPE.

---

## 2.3 Les actions critiques restent limitées

Certaines actions peuvent être disponibles en lecture ou en demande uniquement.

Exemple :

- demander une suspension ;
- demander une augmentation de plafond ;
- signaler un risque ;
- demander un remboursement ;
- demander une correction ;
- demander une réactivation.

La validation finale peut rester dans le portail Admin Web.

---

## 2.4 Toute action doit être auditée

Chaque action doit enregistrer :

- administrateur ;
- rôle ;
- appareil ;
- date ;
- heure ;
- pays ;
- localisation si autorisée ;
- ressource ;
- ancienne valeur ;
- nouvelle valeur ;
- motif ;
- pièce jointe ;
- résultat ;
- corrélation.

---

## 2.5 Aucun accès hors périmètre

Un utilisateur Admin Lite ne doit voir que :

- ses pays ;
- ses régions ;
- ses zones ;
- ses organisations ;
- ses établissements ;
- ses types de dossiers ;
- ses niveaux d’autorisation.

---

# 3. Technologie

Technologie recommandée :

```text
React Native
TypeScript
```

Plateformes :

- Android ;
- iOS ;
- tablette ;
- terminaux professionnels compatibles.

Une priorité peut être donnée à Android pour les équipes terrain.

---

# 4. Architecture de l’application

Structure recommandée :

```text
src/
├── auth/
├── dashboard/
├── assignments/
├── agents/
├── merchants/
├── terminals/
├── atms/
├── customers/
├── incidents/
├── inspections/
├── interventions/
├── compliance/
├── fraud/
├── documents/
├── evidence/
├── signatures/
├── reports/
├── map/
├── notifications/
├── support/
├── sync/
├── settings/
├── security/
└── analytics/
```

---

# 5. Navigation principale

Navigation recommandée :

```text
Accueil
Missions
Recherche
Incidents
Profil
```

Menu secondaire possible :

- Agents ;
- Commerçants ;
- TPE ;
- DAB ;
- Contrôles ;
- Documents ;
- Carte ;
- Rapports ;
- Support.

---

# 6. Tableau de bord

Le tableau de bord doit afficher selon le rôle :

- missions du jour ;
- incidents ouverts ;
- interventions urgentes ;
- contrôles à effectuer ;
- agents à visiter ;
- commerçants à vérifier ;
- TPE à installer ;
- DAB à maintenir ;
- dossiers en attente ;
- alertes ;
- tâches terminées ;
- synchronisation.

---

# 7. Missions

Une mission peut concerner :

- installation ;
- activation ;
- contrôle ;
- audit ;
- maintenance ;
- collecte de documents ;
- formation ;
- vérification physique ;
- enquête ;
- incident ;
- rééquilibrage ;
- remplacement ;
- désactivation.

---

# 8. Dossier de mission

Une mission doit contenir :

- référence ;
- type ;
- priorité ;
- pays ;
- région ;
- zone ;
- adresse ;
- acteur concerné ;
- description ;
- date prévue ;
- durée estimée ;
- responsable ;
- participants ;
- pièces jointes ;
- checklist ;
- statut ;
- résultat.

---

# 9. Statuts de mission

- CREATED ;
- ASSIGNED ;
- ACCEPTED ;
- IN_PROGRESS ;
- PAUSED ;
- WAITING_FOR_INFORMATION ;
- COMPLETED ;
- FAILED ;
- CANCELLED ;
- ESCALATED ;
- REVIEW_REQUIRED.

---

# 10. Affectation

Une mission peut être affectée selon :

- zone ;
- compétence ;
- disponibilité ;
- niveau d’accès ;
- langue ;
- type de matériel ;
- criticité ;
- pays ;
- organisation ;
- charge actuelle.

---

# 11. Carte terrain

L’application peut afficher :

- missions proches ;
- agents ;
- commerçants ;
- TPE ;
- DAB ;
- incidents ;
- zones prioritaires ;
- itinéraire ;
- distance ;
- statut ;
- heure prévue.

La localisation doit respecter la politique définie.

---

# 12. Recherche

La recherche doit permettre de retrouver :

- agent ;
- commerçant ;
- établissement ;
- TPE ;
- DAB ;
- client ;
- transaction ;
- ticket ;
- incident ;
- mission ;
- document ;
- référence.

---

# 13. Recherche sécurisée

Les résultats doivent être filtrés selon :

- pays ;
- tenant ;
- rôle ;
- zone ;
- mission ;
- type de ressource ;
- niveau de sensibilité.

---

# 14. Agents

Admin Lite peut permettre selon permission :

- consulter un agent ;
- vérifier son statut ;
- voir son point de service ;
- voir son niveau ;
- consulter ses appareils ;
- consulter ses incidents ;
- vérifier ses documents ;
- lancer un contrôle ;
- demander une suspension ;
- demander une réactivation ;
- signaler une anomalie.

---

# 15. Données Agent visibles

Peuvent être visibles :

- identité professionnelle ;
- point de service ;
- type ;
- statut ;
- niveau ;
- horaires ;
- appareil ;
- float sous forme limitée ;
- alertes ;
- incidents ;
- missions ;
- documents requis.

Les soldes sensibles doivent être limités ou masqués selon le rôle.

---

# 16. Contrôle d’un agent

La checklist peut inclure :

- identité ;
- affichage officiel ;
- appareil ;
- version application ;
- caisse ;
- float ;
- reçus ;
- documents ;
- sécurité ;
- comportement ;
- respect des frais ;
- disponibilité ;
- conformité du point ;
- formation ;
- signalétique.

---

# 17. Commerçants

L’application peut permettre :

- consulter un commerce ;
- vérifier le KYB ;
- consulter les établissements ;
- voir les TPE associés ;
- contrôler l’activité ;
- vérifier la signalétique ;
- vérifier les employés ;
- collecter des documents ;
- signaler une anomalie ;
- demander une suspension.

---

# 18. Contrôle commerce

Checklist possible :

- identité légale ;
- activité réelle ;
- adresse ;
- registre ;
- fiscalité ;
- bénéficiaires effectifs ;
- compte de règlement ;
- établissement ;
- TPE ;
- caisses ;
- affichage des frais ;
- sécurité ;
- conformité ;
- plainte client.

---

# 19. TPE

Admin Lite peut servir à :

- installer ;
- activer ;
- associer ;
- déplacer ;
- tester ;
- diagnostiquer ;
- mettre à jour ;
- suspendre ;
- remplacer ;
- signaler ;
- récupérer.

---

# 20. Activation TPE

Le parcours doit vérifier :

1. mission autorisée ;
2. identité de l’agent terrain ;
3. terminal ;
4. numéro de série ;
5. commerçant ;
6. établissement ;
7. certificat ;
8. version ;
9. réseau ;
10. test de paiement ;
11. signature ;
12. preuve d’installation.

---

# 21. Diagnostic TPE

Contrôles possibles :

- batterie ;
- réseau ;
- NFC ;
- lecteur puce ;
- imprimante ;
- caméra ;
- scanner ;
- stockage ;
- version ;
- certificat ;
- sécurité ;
- synchronisation.

---

# 22. DAB

Admin Lite peut permettre :

- consulter l’état ;
- ouvrir un incident ;
- effectuer un diagnostic ;
- lancer une maintenance ;
- enregistrer une intervention ;
- vérifier les cassettes ;
- confirmer une recharge ;
- joindre des preuves ;
- demander une mise hors service.

---

# 23. Sécurité DAB

L’application ne doit pas exposer sans permission renforcée :

- montants totaux ;
- détails complets de caisse ;
- secrets de maintenance ;
- clés ;
- codes techniques ;
- itinéraires de transport de fonds ;
- procédures sensibles.

---

# 24. Interventions DAB

Une intervention doit enregistrer :

- DAB ;
- technicien ;
- équipe ;
- date ;
- heure ;
- motif ;
- diagnostic ;
- pièces ;
- photos ;
- cassettes ;
- compteur avant ;
- compteur après ;
- statut ;
- signature ;
- validation.

---

# 25. Clients

L’accès aux données client doit être très limité.

Selon le rôle, Admin Lite peut afficher :

- nom masqué ;
- téléphone masqué ;
- statut du compte ;
- niveau KYC ;
- compte limité ou actif ;
- incidents ouverts ;
- demande de document ;
- ticket lié ;
- dernière opération concernée.

---

# 26. Interdictions sur les données client

Admin Lite ne doit pas exposer librement :

- solde complet ;
- historique complet ;
- documents complets ;
- PIN ;
- OTP ;
- secrets ;
- données carte ;
- données biométriques ;
- autres comptes liés.

---

# 27. Demande de document

L’agent peut demander :

- pièce d’identité ;
- registre ;
- justificatif d’adresse ;
- preuve bancaire ;
- document fiscal ;
- contrat ;
- photo du point de vente ;
- preuve de propriété ;
- justificatif d’activité.

---

# 28. Collecte de document

Le document doit être :

- capturé ;
- vérifié ;
- horodaté ;
- lié au dossier ;
- chiffré ;
- soumis à antivirus ;
- envoyé au backend ;
- supprimé du stockage local après synchronisation sécurisée.

---

# 29. Incidents

Types possibles :

- agent ;
- commerçant ;
- client ;
- TPE ;
- DAB ;
- paiement ;
- retrait ;
- dépôt ;
- fraude ;
- sécurité ;
- réseau ;
- caisse ;
- float ;
- document ;
- conformité ;
- support ;
- agression ;
- vol.

---

# 30. Création d’incident

Le dossier peut contenir :

- type ;
- priorité ;
- description ;
- acteur ;
- ressource ;
- opération ;
- photos ;
- vidéos ;
- documents ;
- localisation ;
- témoins ;
- date ;
- heure ;
- action immédiate ;
- besoin d’escalade.

---

# 31. Niveaux d’incident

- LOW ;
- MEDIUM ;
- HIGH ;
- CRITICAL.

---

# 32. Actions immédiates

Selon permission :

- bloquer une session ;
- suspendre temporairement un appareil ;
- désactiver un TPE ;
- arrêter les retraits ;
- signaler un DAB ;
- verrouiller une mission ;
- demander un contrôle renforcé ;
- contacter le support ;
- envoyer une alerte urgente.

---

# 33. Suspension temporaire

Une suspension mobile doit préciser :

- motif ;
- durée ;
- ressource ;
- périmètre ;
- auteur ;
- urgence ;
- preuve ;
- validation ;
- date de révision.

La suspension définitive doit généralement rester soumise à une validation supérieure.

---

# 34. Fraude terrain

Signaux possibles :

- faux point de service ;
- frais non autorisés ;
- agent absent ;
- utilisation d’un autre appareil ;
- déplacement du TPE ;
- faux dépôt ;
- retrait irrégulier ;
- caisse incohérente ;
- documents falsifiés ;
- collusion ;
- identité non conforme ;
- activité non déclarée.

---

# 35. Dossier fraude

Il peut contenir :

- acteur ;
- type ;
- montant ;
- opérations ;
- preuve ;
- appareil ;
- localisation ;
- relations ;
- score ;
- recommandation ;
- statut ;
- assignation.

---

# 36. Contrôles terrain

Types :

- contrôle programmé ;
- contrôle aléatoire ;
- contrôle après alerte ;
- contrôle après plainte ;
- contrôle avant activation ;
- contrôle périodique ;
- contrôle de reprise ;
- audit complet.

---

# 37. Checklist dynamique

La checklist doit être configurable selon :

- pays ;
- type d’acteur ;
- niveau de risque ;
- mission ;
- produit ;
- appareil ;
- incident ;
- version ;
- réglementation.

---

# 38. Preuves

Types de preuves :

- photo ;
- vidéo ;
- audio ;
- document ;
- signature ;
- QR ;
- géolocalisation ;
- horodatage ;
- scan appareil ;
- capture technique.

---

# 39. Intégrité des preuves

Chaque preuve doit comporter :

- identifiant ;
- hash ;
- auteur ;
- appareil ;
- date ;
- heure ;
- localisation si autorisée ;
- ressource ;
- mission ;
- statut ;
- chaîne de conservation.

---

# 40. Signature

Une intervention peut exiger la signature :

- de l’agent terrain ;
- du commerçant ;
- de l’agent Cash Network ;
- du technicien ;
- du superviseur ;
- d’un témoin ;
- d’un responsable Mansa.

---

# 41. Refus de signature

En cas de refus :

- motif ;
- témoin ;
- photo ;
- commentaire ;
- escalade ;
- signature alternative éventuelle.

---

# 42. Rapports terrain

Rapports possibles :

- missions ;
- contrôles ;
- installations ;
- incidents ;
- TPE ;
- DAB ;
- commerçants ;
- agents ;
- conformité ;
- fraude ;
- documents ;
- productivité ;
- zones.

---

# 43. Rapport automatique

À la fin d’une mission, le système peut générer :

- résumé ;
- checklist ;
- anomalies ;
- preuves ;
- signatures ;
- durée ;
- déplacement ;
- actions ;
- recommandations ;
- statut final.

---

# 44. Notifications

Types :

- nouvelle mission ;
- mission modifiée ;
- urgence ;
- incident ;
- document manquant ;
- validation ;
- rejet ;
- TPE en panne ;
- DAB critique ;
- changement de zone ;
- message support ;
- mise à jour obligatoire.

---

# 45. Notifications de sécurité

Exemples :

- nouvelle connexion ;
- appareil inconnu ;
- mission sensible ;
- session révoquée ;
- rôle modifié ;
- localisation inhabituelle ;
- action critique ;
- application obsolète.

---

# 46. Mode réseau faible

L’application doit prévoir :

- missions mises en cache ;
- checklists locales ;
- cartes simplifiées ;
- reprise automatique ;
- compression ;
- envoi différé des preuves ;
- synchronisation ;
- file locale ;
- indicateur réseau ;
- historique récent.

---

# 47. Mode hors ligne

Le mode hors ligne peut permettre :

- consulter les missions téléchargées ;
- remplir une checklist ;
- prendre des photos ;
- enregistrer une signature ;
- créer un brouillon d’incident ;
- consulter une procédure ;
- préparer un rapport.

Il ne doit pas permettre librement :

- une suspension définitive ;
- une validation financière ;
- une correction de transaction ;
- une modification de droits ;
- un remboursement.

---

# 48. Synchronisation

À la reconnexion :

- vérifier les missions ;
- envoyer les preuves ;
- appliquer l’idempotence ;
- éviter les doublons ;
- résoudre les conflits ;
- récupérer les nouvelles permissions ;
- mettre à jour les statuts ;
- supprimer les fichiers locaux sensibles.

---

# 49. Conflits

Exemples :

- mission déjà clôturée ;
- acteur déjà suspendu ;
- TPE déjà déplacé ;
- incident déjà traité ;
- document déjà validé ;
- rôle modifié ;
- ressource supprimée.

Le backend reste la source officielle.

---

# 50. Sécurité de l’application

Mesures :

- appareil enregistré ;
- MFA ;
- biométrie ;
- PIN ;
- session courte ;
- certificats ;
- chiffrement ;
- stockage sécurisé ;
- détection root ;
- détection jailbreak ;
- protection capture d’écran ;
- effacement distant ;
- audit.

---

# 51. Appareils autorisés

Chaque appareil doit contenir :

- utilisateur ;
- rôle ;
- modèle ;
- OS ;
- version ;
- certificat ;
- pays ;
- dernière activité ;
- statut ;
- date d’expiration ;
- révocation.

---

# 52. Session

La session doit gérer :

- durée ;
- inactivité ;
- contexte ;
- appareil ;
- mission ;
- pays ;
- risque ;
- révocation ;
- reconnexion ;
- verrouillage.

---

# 53. Protection capture d’écran

Peut être appliquée aux écrans :

- données client ;
- documents ;
- fraude ;
- sécurité ;
- TPE ;
- DAB ;
- secrets ;
- preuves sensibles.

---

# 54. Géolocalisation

Elle peut être utilisée pour :

- affectation ;
- itinéraire ;
- preuve de présence ;
- sécurité ;
- contrôle ;
- incident ;
- analyse de zone.

Elle doit être :

- justifiée ;
- transparente ;
- configurable ;
- limitée ;
- soumise aux règles locales.

---

# 55. Paramètres

Catégories :

- profil ;
- appareil ;
- sécurité ;
- notifications ;
- langue ;
- synchronisation ;
- carte ;
- stockage ;
- support ;
- version ;
- légal ;
- déconnexion.

---

# 56. Langues

Admin Lite doit être préparée pour :

- français ;
- bambara ;
- anglais ;
- langues des pays déployés.

Les checklists et procédures doivent être traduisibles.

---

# 57. Accessibilité

L’application doit proposer :

- gros boutons ;
- contraste ;
- taille de texte ;
- mode sombre ;
- lecteur d’écran ;
- navigation simple ;
- mode paysage ;
- réduction des animations ;
- formulaires clairs.

---

# 58. Administration centrale

Le portail Admin Web doit pouvoir gérer :

- utilisateurs Admin Lite ;
- rôles ;
- zones ;
- missions ;
- checklists ;
- appareils ;
- versions ;
- permissions ;
- incidents ;
- preuves ;
- rapports ;
- feature flags ;
- politique hors ligne ;
- géolocalisation ;
- sécurité.

---

# 59. Permissions

Exemples :

```text
admin_lite.dashboard.read
admin_lite.mission.read
admin_lite.mission.accept
admin_lite.mission.update
admin_lite.agent.read
admin_lite.agent.inspect
admin_lite.merchant.read
admin_lite.merchant.inspect
admin_lite.terminal.read
admin_lite.terminal.activate
admin_lite.terminal.diagnose
admin_lite.atm.read
admin_lite.atm.intervene
admin_lite.incident.create
admin_lite.incident.read
admin_lite.document.collect
admin_lite.evidence.create
admin_lite.report.create
admin_lite.suspension.request
admin_lite.audit.read
```

---

# 60. Actions critiques

Doivent être protégées :

- suspension temporaire ;
- activation TPE ;
- déplacement TPE ;
- remise en service DAB ;
- collecte de document sensible ;
- accès fraude ;
- accès client ;
- modification d’une mission ;
- suppression d’une preuve ;
- fermeture d’un incident ;
- création d’un accès.

---

# 61. Double validation

Peut être exigée pour :

- suspension critique ;
- réactivation ;
- remise en service DAB ;
- installation d’un TPE sensible ;
- contrôle fraude ;
- modification d’un dossier réglementaire ;
- suppression d’une preuve ;
- accès exceptionnel ;
- clôture d’un incident majeur.

---

# 62. API

Exemples :

```http
GET    /admin-lite/dashboard
GET    /admin-lite/missions
GET    /admin-lite/missions/{id}
POST   /admin-lite/missions/{id}/accept
POST   /admin-lite/missions/{id}/start
POST   /admin-lite/missions/{id}/complete

GET    /admin-lite/agents/{id}
POST   /admin-lite/agents/{id}/inspections

GET    /admin-lite/merchants/{id}
POST   /admin-lite/merchants/{id}/inspections

GET    /admin-lite/terminals/{id}
POST   /admin-lite/terminals/{id}/activate
POST   /admin-lite/terminals/{id}/diagnostics

GET    /admin-lite/atms/{id}
POST   /admin-lite/atms/{id}/interventions

POST   /admin-lite/incidents
POST   /admin-lite/evidence
POST   /admin-lite/documents
POST   /admin-lite/reports
POST   /admin-lite/suspension-requests
POST   /admin-lite/sync
```

---

# 63. Modèles

- AdminLiteUser
- AdminLiteRole
- AdminLitePermission
- AdminLiteDevice
- FieldMission
- FieldMissionAssignment
- FieldChecklist
- FieldChecklistResponse
- FieldInspection
- FieldIntervention
- FieldIncident
- FieldEvidence
- FieldDocument
- FieldSignature
- FieldLocation
- FieldReport
- FieldSuspensionRequest
- FieldSynchronization
- AdminLiteSecurityEvent
- AdminLiteAudit

---

# 64. Analytics

Événements possibles :

```text
admin_lite_login_completed
admin_lite_mission_received
admin_lite_mission_accepted
admin_lite_mission_started
admin_lite_mission_completed
admin_lite_agent_inspection_completed
admin_lite_merchant_inspection_completed
admin_lite_terminal_activated
admin_lite_terminal_diagnostic_completed
admin_lite_atm_intervention_completed
admin_lite_incident_created
admin_lite_evidence_uploaded
admin_lite_document_collected
admin_lite_suspension_requested
admin_lite_sync_completed
admin_lite_security_alert
```

---

# 65. Tests

- tests d’authentification ;
- tests MFA ;
- tests de rôles ;
- tests de permissions ;
- tests de missions ;
- tests d’affectation ;
- tests de carte ;
- tests agents ;
- tests commerçants ;
- tests TPE ;
- tests DAB ;
- tests incidents ;
- tests checklists ;
- tests preuves ;
- tests documents ;
- tests signatures ;
- tests géolocalisation ;
- tests hors ligne ;
- tests synchronisation ;
- tests de conflits ;
- tests multi-pays ;
- tests multi-zones ;
- tests de sécurité ;
- tests d’effacement distant ;
- tests d’accessibilité ;
- tests d’audit.

---

# 66. Règles métier

1. Admin Lite ne remplace pas le portail Admin Web.
2. Chaque utilisateur possède un rôle limité.
3. Chaque utilisateur possède un périmètre géographique.
4. Les données sont filtrées par pays et tenant.
5. Les données client sont masquées.
6. Les secrets ne sont jamais visibles.
7. Chaque mission possède une référence unique.
8. Chaque intervention est auditée.
9. Les preuves sont horodatées et hashées.
10. Les documents sont supprimés du stockage local après synchronisation.
11. Les actions critiques nécessitent une permission.
12. Certaines actions restent des demandes.
13. Les validations financières restent dans le backend.
14. Le mode hors ligne reste limité.
15. La synchronisation est idempotente.
16. Le backend est la source officielle.
17. Les suspensions définitives nécessitent une validation.
18. Les appareils sont enregistrés.
19. Les sessions peuvent être révoquées à distance.
20. La géolocalisation reste encadrée.
21. Les checklists sont dynamiques.
22. Les rapports sont générés automatiquement lorsque possible.
23. Les preuves ne sont pas modifiées silencieusement.
24. Les accès sensibles sont journalisés.
25. Les actions critiques peuvent exiger une double validation.

---

# 67. Critères d’acceptation

L’application Admin Lite est validée lorsque :

- les utilisateurs sont authentifiés ;
- les rôles sont limités ;
- les périmètres géographiques sont appliqués ;
- les missions sont affectées ;
- les missions peuvent être exécutées ;
- les agents peuvent être contrôlés ;
- les commerçants peuvent être contrôlés ;
- les TPE peuvent être installés et diagnostiqués ;
- les DAB peuvent être suivis ;
- les incidents peuvent être créés ;
- les checklists sont configurables ;
- les preuves sont sécurisées ;
- les documents sont collectés ;
- les signatures sont disponibles ;
- les suspensions sont contrôlées ;
- les données client sont masquées ;
- le mode réseau faible fonctionne ;
- le mode hors ligne reste limité ;
- la synchronisation évite les doublons ;
- les appareils peuvent être révoqués ;
- les actions critiques sont auditées ;
- les tests couvrent les parcours essentiels.
