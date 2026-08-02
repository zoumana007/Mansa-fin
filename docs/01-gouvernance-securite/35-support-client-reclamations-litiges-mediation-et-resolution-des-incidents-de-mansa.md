# 35 — Support client, réclamations, litiges, médiation et résolution des incidents de Mansa

## 1. Objet du document

Ce document définit l’architecture officielle du support client et de la gestion des réclamations de Mansa.

Il couvre :

- le support des particuliers ;
- le support des commerçants ;
- le support TPE ;
- le support des partenaires ;
- le support des institutions publiques ;
- les demandes d’assistance ;
- les réclamations ;
- les contestations de transaction ;
- les incidents ;
- les remboursements ;
- les litiges ;
- les médiations ;
- les escalades ;
- les SLA ;
- les priorités ;
- les canaux ;
- les preuves ;
- les communications ;
- les équipes ;
- les permissions ;
- l’audit ;
- la satisfaction ;
- les obligations multi-pays.

L’objectif est de permettre à Mansa de :

- répondre rapidement aux utilisateurs ;
- traiter les demandes de manière cohérente ;
- protéger les données sensibles ;
- résoudre les incidents financiers ;
- assurer la traçabilité ;
- limiter les délais ;
- éviter les réponses contradictoires ;
- mesurer la qualité du support ;
- gérer les recours ;
- améliorer continuellement les produits.

---

# 2. Principes fondamentaux

## 2.1 Un ticket unique par problème

Chaque demande doit créer un identifiant unique.

Exemple :

```text
SUP-2026-000123
```

Le ticket doit regrouper :

- les messages ;
- les pièces jointes ;
- les actions ;
- les décisions ;
- les escalades ;
- les transactions concernées ;
- l’historique ;
- les délais ;
- les responsables.

---

## 2.2 Aucun traitement sensible sans vérification d’identité

Avant de communiquer ou modifier une information sensible, l’agent doit vérifier l’identité de la personne.

La méthode peut dépendre :

- du canal ;
- du risque ;
- du type de demande ;
- du montant ;
- de l’état du compte ;
- du pays ;
- du rôle.

---

## 2.3 Le support ne modifie pas directement le ledger

Un agent support ne doit jamais modifier directement :

- un solde ;
- une écriture comptable ;
- une transaction ;
- un remboursement ;
- une commission ;
- un règlement.

Il doit utiliser un workflow contrôlé.

---

## 2.4 Les réponses doivent être cohérentes

Le support doit utiliser :

- procédures officielles ;
- réponses validées ;
- base de connaissances ;
- modèles ;
- règles pays ;
- règles produit ;
- règles partenaires.

---

## 2.5 Toute action importante doit être auditée

Les actions suivantes doivent être enregistrées :

- consultation sensible ;
- modification ;
- remboursement ;
- blocage ;
- déblocage ;
- changement de statut ;
- export ;
- escalade ;
- clôture ;
- réouverture.

---

# 3. Catégories de support

Mansa doit gérer au minimum :

- support particulier ;
- support commerçant ;
- support TPE ;
- support partenaire ;
- support institutionnel ;
- support développeur API ;
- support interne ;
- support fraude ;
- support conformité ;
- support technique ;
- support facturation.

---

# 4. Canaux de support

Canaux possibles :

- centre d’aide ;
- chat intégré ;
- formulaire ;
- e-mail ;
- téléphone ;
- WhatsApp lorsque autorisé ;
- SMS ;
- portail commerçant ;
- portail partenaire ;
- portail institutionnel ;
- application Admin Lite ;
- guichet physique partenaire ;
- réseau social public limité.

---

# 5. Sécurité par canal

## 5.1 Chat intégré

Avantages :

- utilisateur authentifié ;
- contexte disponible ;
- historique ;
- pièces jointes ;
- notifications.

## 5.2 E-mail

Doit utiliser :

- vérification ;
- liens sécurisés ;
- limitation des données sensibles ;
- prévention de l’usurpation ;
- conservation.

## 5.3 Téléphone

L’agent doit vérifier l’identité avec plusieurs éléments adaptés au risque.

## 5.4 Réseaux sociaux

Aucune donnée sensible ne doit être traitée publiquement.

L’utilisateur doit être redirigé vers un canal sécurisé.

---

# 6. Création d’un ticket

Un ticket doit contenir :

- référence ;
- utilisateur ;
- organisation ;
- pays ;
- canal ;
- catégorie ;
- sous-catégorie ;
- priorité ;
- produit ;
- application ;
- transaction éventuelle ;
- partenaire éventuel ;
- description ;
- pièces jointes ;
- langue ;
- statut ;
- équipe ;
- agent ;
- dates ;
- SLA ;
- corrélation.

---

# 7. Types de tickets

Exemples :

- accès au compte ;
- KYC ;
- wallet ;
- paiement ;
- transfert ;
- carte ;
- remboursement ;
- transaction inconnue ;
- fraude ;
- commerçant ;
- TPE ;
- stock ;
- facture ;
- abonnement ;
- frais ;
- Mobile Money ;
- banque ;
- service public ;
- données personnelles ;
- contrat ;
- incident technique ;
- suggestion ;
- réclamation.

---

# 8. Statuts du ticket

Valeurs possibles :

- CREATED ;
- OPEN ;
- ASSIGNED ;
- IN_PROGRESS ;
- WAITING_FOR_CUSTOMER ;
- WAITING_FOR_PARTNER ;
- WAITING_FOR_INTERNAL_TEAM ;
- ESCALATED ;
- RESOLVED ;
- CLOSED ;
- REOPENED ;
- CANCELLED ;
- DUPLICATE.

---

# 9. Priorités

## 9.1 Critique

Exemples :

- perte financière importante ;
- compte compromis ;
- carte volée ;
- service national indisponible ;
- erreur de solde ;
- fraude active ;
- incident de sécurité ;
- paiement public bloqué.

## 9.2 Haute

Exemples :

- paiement non reconnu ;
- retrait bloqué ;
- TPE principal indisponible ;
- règlement commerçant en retard ;
- compte suspendu à tort.

## 9.3 Normale

Exemples :

- question sur frais ;
- modification de profil ;
- document manquant ;
- facture ;
- demande d’information.

## 9.4 Faible

Exemples :

- suggestion ;
- amélioration ;
- question générale ;
- demande non urgente.

---

# 10. Calcul de priorité

La priorité peut dépendre :

- du montant ;
- du nombre d’utilisateurs ;
- du type de service ;
- de la fraude ;
- de la sécurité ;
- du pays ;
- du partenaire ;
- du délai ;
- de la vulnérabilité du client ;
- de l’impact réglementaire.

---

# 11. SLA du support

Chaque catégorie doit avoir :

- délai de première réponse ;
- délai de prise en charge ;
- délai cible de résolution ;
- fréquence de mise à jour ;
- délai d’escalade ;
- horaires applicables ;
- jours ouvrés ;
- exclusions.

---

# 12. Exemple de SLA

```text
Critique :
- première réponse : 10 minutes ;
- prise en charge : immédiate ;
- mise à jour : toutes les 30 minutes ;
- résolution cible : selon le type d’incident.

Haute :
- première réponse : 1 heure ;
- mise à jour : toutes les 4 heures.

Normale :
- première réponse : 24 heures ouvrées.
```

Les valeurs doivent être configurables par pays et produit.

---

# 13. Calendriers

Les SLA doivent tenir compte :

- du fuseau ;
- des jours ouvrés ;
- des jours fériés ;
- du support 24/7 ;
- du niveau de service ;
- du type de partenaire ;
- du contrat.

---

# 14. Pause du SLA

Le SLA peut être suspendu lorsque :

- Mansa attend une réponse utilisateur ;
- Mansa attend un document ;
- Mansa attend un partenaire ;
- un délai légal s’applique ;
- l’utilisateur a demandé un report.

La pause doit être tracée.

---

# 15. Affectation

Un ticket peut être affecté selon :

- pays ;
- langue ;
- produit ;
- niveau de risque ;
- type d’utilisateur ;
- montant ;
- partenaire ;
- compétence ;
- disponibilité ;
- spécialisation.

---

# 16. Files d’attente

Files possibles :

- Support Client ;
- Support Commerce ;
- Support TPE ;
- Support Cartes ;
- Support Paiements ;
- Fraude ;
- KYC ;
- Conformité ;
- Technique ;
- Partenaires ;
- Services publics ;
- Réclamations ;
- Médiation.

---

# 17. Distribution automatique

Le système peut utiliser :

- round-robin ;
- compétence ;
- priorité ;
- charge ;
- pays ;
- langue ;
- spécialité ;
- disponibilité ;
- historique du dossier.

---

# 18. Vérification d’identité

Méthodes possibles :

- session authentifiée ;
- OTP ;
- confirmation dans l’application ;
- passkey ;
- biométrie ;
- question contrôlée ;
- document ;
- appel sécurisé ;
- code commerçant ;
- certificat partenaire.

---

# 19. Niveaux de vérification

## 19.1 Vérification simple

Pour :

- information générale ;
- suivi non sensible ;
- aide à la navigation.

## 19.2 Vérification renforcée

Pour :

- changement de téléphone ;
- réinitialisation ;
- déblocage ;
- remboursement ;
- changement de compte ;
- carte ;
- transaction contestée ;
- données personnelles.

---

# 20. Données visibles par l’agent

L’agent doit voir uniquement les données nécessaires.

Exemples :

- nom masqué ;
- téléphone partiellement masqué ;
- identifiant ;
- statut ;
- transactions pertinentes ;
- historique du ticket ;
- niveau KYC ;
- alertes utiles.

---

# 21. Données interdites

Un agent support ne doit jamais voir en clair :

- mot de passe ;
- PIN ;
- CVV ;
- OTP ;
- clé privée ;
- secret ;
- token complet ;
- numéro complet de carte sauf besoin strict et protection adaptée.

---

# 22. Vue 360 contrôlée

La vue support peut afficher :

- profil ;
- appareils ;
- sessions ;
- wallet ;
- cartes ;
- transactions ;
- tickets ;
- litiges ;
- KYC ;
- restrictions ;
- notifications ;
- commerçants liés ;
- TPE liés.

Chaque bloc reste soumis aux permissions.

---

# 23. Notes internes

Les notes internes doivent être :

- invisibles pour l’utilisateur ;
- datées ;
- attribuées ;
- auditées ;
- limitées aux informations nécessaires ;
- respectueuses ;
- non discriminatoires.

---

# 24. Messages utilisateurs

Les messages doivent être :

- clairs ;
- polis ;
- compréhensibles ;
- adaptés à la langue ;
- sans jargon inutile ;
- sans révéler les règles internes de fraude ;
- cohérents avec le statut réel.

---

# 25. Modèles de réponse

Les modèles doivent être :

- versionnés ;
- traduits ;
- validés ;
- reliés à une catégorie ;
- modifiables ;
- personnalisables ;
- audités.

---

# 26. Base de connaissances

Elle doit contenir :

- articles ;
- procédures ;
- diagnostics ;
- questions fréquentes ;
- guides ;
- règles pays ;
- règles partenaires ;
- scripts d’appel ;
- réponses de crise ;
- escalades.

---

# 27. Versionnement de la base de connaissances

Chaque article doit contenir :

- version ;
- auteur ;
- approbateur ;
- date ;
- pays ;
- langue ;
- produit ;
- validité ;
- historique.

---

# 28. Suggestions automatiques

Le système peut proposer à l’agent :

- article ;
- réponse ;
- procédure ;
- diagnostic ;
- formulaire ;
- équipe d’escalade.

La décision finale reste contrôlée.

---

# 29. Jini pour le support

Jini peut aider à :

- résumer un dossier ;
- proposer une réponse ;
- rechercher une procédure ;
- classer un ticket ;
- détecter un doublon ;
- traduire ;
- extraire des informations ;
- préparer une chronologie.

Jini ne doit pas :

- rembourser seul ;
- débloquer seul ;
- modifier un solde ;
- clôturer une fraude ;
- donner accès à des données interdites.

---

# 30. Pièces jointes

Types possibles :

- capture ;
- reçu ;
- facture ;
- document ;
- vidéo ;
- photo ;
- fichier partenaire ;
- rapport.

Les fichiers doivent être :

- scannés ;
- chiffrés ;
- limités ;
- classés ;
- conservés ;
- accessibles selon permission.

---

# 31. Détection de contenu sensible

Le système doit détecter ou avertir si un fichier contient :

- carte complète ;
- code PIN ;
- secret ;
- document sensible ;
- données personnelles excessives ;
- malware.

---

# 32. Diagnostic

Un workflow de diagnostic peut vérifier :

- statut service ;
- statut utilisateur ;
- version application ;
- appareil ;
- réseau ;
- partenaire ;
- transaction ;
- logs ;
- incident connu ;
- configuration ;
- feature flag.

---

# 33. Incidents connus

Le support doit pouvoir voir :

- incident en cours ;
- impact ;
- pays ;
- services ;
- début ;
- contournement ;
- message validé ;
- prochaine mise à jour ;
- statut.

---

# 34. Liaison ticket-incident

Plusieurs tickets peuvent être reliés à un incident.

Cela permet :

- réponse cohérente ;
- notification groupée ;
- mesure de l’impact ;
- clôture automatique contrôlée ;
- analyse post-incident.

---

# 35. Contestation de transaction

L’utilisateur peut contester :

- paiement ;
- transfert ;
- retrait ;
- frais ;
- carte ;
- Mobile Money ;
- paiement commerçant ;
- service public ;
- remboursement ;
- prélèvement.

---

# 36. Données de contestation

Le dossier doit contenir :

- transaction ;
- montant ;
- devise ;
- date ;
- motif ;
- utilisateur ;
- commerçant ;
- partenaire ;
- preuves ;
- délai ;
- statut ;
- décision ;
- remboursement éventuel.

---

# 37. Motifs de contestation

Exemples :

- transaction non reconnue ;
- montant incorrect ;
- double débit ;
- service non reçu ;
- remboursement absent ;
- paiement annulé ;
- retrait non reçu ;
- frais contesté ;
- fraude ;
- erreur TPE.

---

# 38. Statuts de contestation

Valeurs possibles :

- SUBMITTED ;
- ELIGIBILITY_CHECK ;
- INFORMATION_REQUIRED ;
- UNDER_REVIEW ;
- PARTNER_REVIEW ;
- PROVISIONAL_CREDIT_GRANTED ;
- ACCEPTED ;
- REJECTED ;
- PARTIALLY_ACCEPTED ;
- CLOSED ;
- APPEALED.

---

# 39. Éligibilité

Le système doit vérifier :

- délai ;
- type de transaction ;
- statut ;
- montant ;
- preuve ;
- contrat ;
- réseau ;
- pays ;
- partenaire ;
- historique.

---

# 40. Crédit provisoire

Un remboursement provisoire peut être accordé selon :

- réglementation ;
- produit ;
- risque ;
- montant ;
- historique ;
- type de fraude ;
- partenaire.

Il doit être enregistré séparément.

---

# 41. Remboursement

Un remboursement doit utiliser un workflow contrôlé.

Il doit contenir :

- transaction d’origine ;
- montant ;
- devise ;
- motif ;
- type ;
- approbateur ;
- état ;
- écriture ledger ;
- notification ;
- audit.

---

# 42. Types de remboursement

- total ;
- partiel ;
- provisoire ;
- commercial ;
- réglementaire ;
- partenaire ;
- erreur technique ;
- geste exceptionnel.

---

# 43. Remboursement exceptionnel

Il doit exiger :

- justification ;
- montant ;
- budget ;
- permission ;
- approbation ;
- audit ;
- contrôle de doublon.

---

# 44. Litige

Un litige peut concerner :

- transaction ;
- frais ;
- contrat ;
- commerçant ;
- partenaire ;
- service ;
- données ;
- suspension ;
- remboursement ;
- engagement SLA.

---

# 45. Dossier de litige

Il doit contenir :

- parties ;
- objet ;
- montant ;
- contrat ;
- transaction ;
- faits ;
- preuves ;
- communications ;
- décisions ;
- statut ;
- délais ;
- médiation ;
- recours ;
- clôture.

---

# 46. Statuts de litige

Valeurs possibles :

- OPEN ;
- UNDER_REVIEW ;
- INFORMATION_REQUIRED ;
- NEGOTIATION ;
- MEDIATION ;
- ESCALATED ;
- SETTLED ;
- REJECTED ;
- CLOSED ;
- REOPENED.

---

# 47. Réclamation formelle

Une réclamation formelle doit être distinguée d’une simple demande d’assistance.

Elle doit déclencher :

- accusé de réception ;
- délai officiel ;
- responsable ;
- analyse ;
- réponse motivée ;
- voie de recours ;
- archivage ;
- audit.

---

# 48. Contenu d’une réclamation

- identité ;
- référence ;
- objet ;
- service ;
- faits ;
- date ;
- montant ;
- preuves ;
- solution demandée ;
- canal ;
- pays ;
- contrat ;
- statut.

---

# 49. Accusé de réception

L’utilisateur doit recevoir :

- référence ;
- date ;
- résumé ;
- délai indicatif ;
- canal de suivi ;
- pièces reçues ;
- prochaines étapes.

---

# 50. Réponse motivée

La réponse finale doit inclure lorsque possible :

- décision ;
- faits retenus ;
- règles appliquées ;
- montant ;
- action ;
- remboursement ;
- délai ;
- recours ;
- contact.

---

# 51. Recours

L’utilisateur peut demander :

- réexamen ;
- escalade ;
- responsable supérieur ;
- médiation ;
- autorité compétente ;
- recours contractuel ;
- recours judiciaire.

---

# 52. Médiation

La médiation peut être :

- interne ;
- externe ;
- sectorielle ;
- institutionnelle ;
- réglementaire.

Le dossier doit contenir :

- médiateur ;
- date ;
- parties ;
- pièces ;
- échanges ;
- proposition ;
- décision ;
- acceptation ;
- clôture.

---

# 53. Indépendance du médiateur

Le rôle de médiation doit être séparé des agents ayant pris la décision initiale lorsque nécessaire.

---

# 54. Escalade interne

Niveaux possibles :

1. agent support ;
2. superviseur ;
3. équipe spécialisée ;
4. responsable opérationnel ;
5. conformité ou fraude ;
6. juridique ;
7. direction ;
8. comité de décision.

---

# 55. Critères d’escalade

- montant élevé ;
- fraude ;
- sécurité ;
- utilisateur vulnérable ;
- répétition ;
- risque médiatique ;
- partenaire majeur ;
- service public ;
- dépassement SLA ;
- conflit de règles ;
- menace juridique.

---

# 56. Support fraude

Le support doit pouvoir :

- bloquer immédiatement une carte selon permission ;
- révoquer une session ;
- signaler une transaction ;
- sécuriser un compte ;
- ouvrir un dossier fraude ;
- guider l’utilisateur ;
- préserver les preuves.

---

# 57. Support KYC

Le support peut :

- expliquer les documents requis ;
- demander une nouvelle capture ;
- informer du statut ;
- escalader une erreur ;
- guider l’utilisateur.

Il ne doit pas approuver seul un dossier sans permission.

---

# 58. Support TPE

Il doit gérer :

- activation ;
- appareil ;
- connexion ;
- impression ;
- NFC ;
- puce ;
- réseau ;
- synchronisation ;
- mise à jour ;
- remboursement ;
- clôture ;
- remplacement ;
- panne matérielle.

---

# 59. Diagnostic TPE

Le portail support peut afficher :

- modèle ;
- numéro ;
- commerçant ;
- établissement ;
- version ;
- batterie ;
- réseau ;
- certificat ;
- dernière synchronisation ;
- erreurs ;
- mises à jour ;
- statut.

---

# 60. Intervention TPE

Types :

- assistance distante ;
- redémarrage guidé ;
- mise à jour ;
- réinitialisation contrôlée ;
- remplacement ;
- récupération ;
- intervention physique ;
- suspension.

---

# 61. Support commerçant

Il doit gérer :

- KYB ;
- produits ;
- stock ;
- employés ;
- ventes ;
- remboursements ;
- règlements ;
- factures ;
- abonnements ;
- TPE ;
- promotions ;
- litiges clients.

---

# 62. Support partenaire

Le support partenaire peut traiter :

- API ;
- certificats ;
- webhooks ;
- environnements ;
- quotas ;
- rapprochement ;
- incident ;
- facturation ;
- SLA ;
- version ;
- intégration.

---

# 63. Support institutionnel

Il peut traiter :

- agent ;
- accès ;
- service public ;
- paiement ;
- dossier ;
- amende ;
- bourse ;
- carte étudiante ;
- rapprochement ;
- audit ;
- contestation ;
- corruption présumée.

---

# 64. Lutte contre les abus internes

Le système doit détecter :

- consultation sans ticket ;
- modification sans motif ;
- clôture répétée ;
- remboursement anormal ;
- accès à un proche ;
- export massif ;
- usage d’un compte partagé ;
- contournement de validation ;
- suppression de note.

---

# 65. Séparation des responsabilités

Les rôles doivent être séparés entre :

- agent ;
- superviseur ;
- remboursement ;
- fraude ;
- conformité ;
- médiation ;
- juridique ;
- administration des procédures ;
- audit.

---

# 66. Supervision

Le superviseur doit pouvoir :

- voir les files ;
- réaffecter ;
- prioriser ;
- suivre les SLA ;
- valider certaines actions ;
- écouter ou relire selon les règles ;
- coacher ;
- escalader ;
- gérer la charge.

---

# 67. Contrôle qualité

Le contrôle qualité peut évaluer :

- exactitude ;
- sécurité ;
- politesse ;
- délai ;
- procédure ;
- résolution ;
- documentation ;
- satisfaction ;
- conformité ;
- confidentialité.

---

# 68. Échantillonnage

Le système peut sélectionner des tickets selon :

- hasard ;
- risque ;
- agent ;
- catégorie ;
- montant ;
- réclamation ;
- faible satisfaction ;
- remboursement ;
- fraude ;
- pays.

---

# 69. Satisfaction

Mesures possibles :

- CSAT ;
- effort client ;
- taux de résolution ;
- réouverture ;
- délai ;
- recommandation ;
- commentaire.

---

# 70. Enquête de satisfaction

Elle doit être :

- facultative ;
- courte ;
- reliée au ticket ;
- traduite ;
- non biaisée ;
- distincte de la décision.

---

# 71. Indicateurs opérationnels

Exemples :

- nombre de tickets ;
- délai de première réponse ;
- délai de résolution ;
- taux de résolution au premier contact ;
- taux de réouverture ;
- taux d’escalade ;
- backlog ;
- dépassement SLA ;
- satisfaction ;
- remboursement ;
- plaintes ;
- litiges.

---

# 72. Indicateurs par produit

Suivre séparément :

- Client ;
- Commerce ;
- TPE ;
- cartes ;
- paiements ;
- Mobile Money ;
- services publics ;
- partenaires ;
- Jini ;
- KYC.

---

# 73. Analyse des causes

Les tickets doivent permettre d’identifier :

- bug ;
- mauvaise UX ;
- panne partenaire ;
- mauvaise documentation ;
- configuration ;
- fraude ;
- incompréhension ;
- formation ;
- erreur humaine ;
- produit défectueux.

---

# 74. Boucle d’amélioration produit

Les tickets récurrents doivent créer :

- problème connu ;
- demande produit ;
- correctif ;
- amélioration UX ;
- mise à jour de procédure ;
- formation ;
- alerte partenaire ;
- modification de configuration.

---

# 75. Problème majeur

Plusieurs tickets similaires peuvent être regroupés dans un problème.

Le problème doit contenir :

- symptômes ;
- cause ;
- impact ;
- services ;
- correctif ;
- contournement ;
- responsables ;
- statut ;
- incidents liés.

---

# 76. Automatisations

Le système peut automatiser :

- accusé de réception ;
- relance ;
- rappel SLA ;
- affectation ;
- demande d’information ;
- notification de résolution ;
- enquête de satisfaction ;
- détection de doublon ;
- clôture après délai ;
- réouverture contrôlée.

---

# 77. Clôture automatique

Un ticket peut être clôturé après :

- résolution ;
- confirmation ;
- absence de réponse ;
- délai configurable ;
- notification préalable.

Les tickets sensibles ne doivent pas être clôturés trop rapidement.

---

# 78. Réouverture

Un ticket peut être réouvert si :

- problème persistant ;
- nouvelle preuve ;
- erreur de décision ;
- remboursement absent ;
- réponse incomplète ;
- recours ;
- incident lié.

---

# 79. Conservation

La durée dépend :

- du pays ;
- du type ;
- de la sensibilité ;
- du litige ;
- du contrat ;
- de la fraude ;
- de la conformité ;
- du legal hold.

---

# 80. Anonymisation

Les tickets peuvent être anonymisés après la durée applicable, tout en conservant :

- métriques ;
- catégorie ;
- résultat ;
- cause ;
- données agrégées ;
- références nécessaires.

---

# 81. Export

Les exports doivent être :

- autorisés ;
- limités ;
- masqués ;
- chiffrés ;
- temporaires ;
- audités ;
- liés à un motif.

---

# 82. Multi-pays

Chaque pays doit pouvoir définir :

- langues ;
- horaires ;
- SLA ;
- canaux ;
- recours ;
- médiateur ;
- délais ;
- autorités ;
- modèles ;
- règles de remboursement ;
- conservation.

---

# 83. Langues

Le support doit gérer :

- langue préférée ;
- traduction ;
- modèles locaux ;
- routage par compétence ;
- version de référence ;
- relecture humaine pour les cas sensibles.

---

# 84. Accessibilité

Le support doit être utilisable par :

- personnes malvoyantes ;
- personnes malentendantes ;
- personnes ayant des difficultés de lecture ;
- personnes utilisant un appareil faible ;
- utilisateurs avec connexion limitée.

---

# 85. Utilisateurs vulnérables

Une attention renforcée peut concerner :

- mineurs ;
- personnes âgées ;
- personnes handicapées ;
- victimes de fraude ;
- utilisateurs en difficulté financière ;
- personnes sous menace ou contrainte.

---

# 86. Administration

Le portail Admin doit permettre :

- créer un ticket ;
- rechercher ;
- filtrer ;
- affecter ;
- prioriser ;
- répondre ;
- ajouter une note ;
- joindre une pièce ;
- demander une vérification ;
- escalader ;
- créer une réclamation ;
- créer un litige ;
- lancer un remboursement ;
- consulter les SLA ;
- consulter les métriques ;
- auditer les actions.

---

# 87. Permissions

Exemples :

```text
support.ticket.read
support.ticket.create
support.ticket.assign
support.ticket.update
support.ticket.close
support.ticket.reopen
support.customer.read
support.customer.read_sensitive
support.note.create
support.attachment.read
support.escalate
support.refund.request
support.refund.approve
support.complaint.read
support.complaint.manage
support.dispute.read
support.dispute.manage
support.mediation.manage
support.quality.read
support.audit.read
```

---

# 88. Actions critiques

Doivent être protégées :

- remboursement ;
- levée de blocage ;
- changement de téléphone ;
- réinitialisation d’accès ;
- consultation sensible ;
- export ;
- suppression de pièce ;
- clôture de litige ;
- modification de décision ;
- accès d’urgence.

---

# 89. Double validation

Peut être exigée pour :

- remboursement élevé ;
- geste commercial important ;
- litige majeur ;
- levée de blocage fraude ;
- changement d’identité ;
- suppression de preuve ;
- décision institutionnelle ;
- médiation sensible.

---

# 90. API

Exemples :

```http
POST   /support/tickets
GET    /support/tickets
GET    /support/tickets/{id}
PATCH  /support/tickets/{id}

POST   /support/tickets/{id}/assign
POST   /support/tickets/{id}/messages
POST   /support/tickets/{id}/notes
POST   /support/tickets/{id}/escalate
POST   /support/tickets/{id}/resolve
POST   /support/tickets/{id}/close
POST   /support/tickets/{id}/reopen

POST   /support/complaints
GET    /support/complaints/{id}

POST   /support/disputes
GET    /support/disputes/{id}
POST   /support/disputes/{id}/appeal

POST   /support/refunds
GET    /support/sla
GET    /support/metrics
```

---

# 91. Modèles

- SupportTicket
- SupportCategory
- SupportQueue
- SupportMessage
- SupportInternalNote
- SupportAttachment
- SupportAssignment
- SupportStatusHistory
- SupportSla
- SupportEscalation
- SupportVerification
- SupportKnowledgeArticle
- SupportTemplate
- SupportQualityReview
- SupportSatisfaction
- Complaint
- ComplaintDecision
- Dispute
- DisputeEvidence
- MediationCase
- RefundRequest
- SupportIncidentLink
- SupportAudit

---

# 92. Règles métier

1. Toute demande possède une référence.
2. Toute action sensible exige une vérification.
3. Le support ne modifie jamais directement le ledger.
4. Les remboursements passent par un workflow.
5. Les données visibles sont limitées.
6. Les informations sensibles sont masquées.
7. Les tickets sont affectés selon la compétence.
8. Les SLA sont configurables.
9. Les pauses SLA sont tracées.
10. Les incidents connus sont reliés aux tickets.
11. Les réclamations formelles sont distinguées.
12. Les contestations sont reliées aux transactions.
13. Les recours sont possibles.
14. Les médiations sont tracées.
15. Les notes internes restent auditées.
16. Les modèles de réponse sont versionnés.
17. La base de connaissances est maintenue.
18. Jini ne prend pas seul de décision financière.
19. Les pièces jointes sont sécurisées.
20. Les abus internes sont détectables.
21. Les actions critiques peuvent exiger deux validations.
22. Les utilisateurs sont informés du statut.
23. Les tickets récurrents alimentent l’amélioration produit.
24. Les données sont conservées selon la politique.
25. Les actions support sont auditables.

---

# 93. Analytics

Événements possibles :

```text
support_ticket_created
support_ticket_assigned
support_ticket_first_response_sent
support_ticket_escalated
support_ticket_resolved
support_ticket_closed
support_ticket_reopened
support_sla_warning
support_sla_breached
support_complaint_created
support_complaint_resolved
support_dispute_created
support_dispute_appealed
support_refund_requested
support_refund_approved
support_mediation_started
support_mediation_completed
support_satisfaction_received
support_quality_review_completed
```

---

# 94. Tests

- tests de création de ticket ;
- tests de routage ;
- tests de priorité ;
- tests SLA ;
- tests de pause ;
- tests de vérification d’identité ;
- tests de permissions ;
- tests de masquage ;
- tests de pièces jointes ;
- tests d’escalade ;
- tests d’incident ;
- tests de contestation ;
- tests de remboursement ;
- tests de réclamation ;
- tests de litige ;
- tests de médiation ;
- tests de réouverture ;
- tests de clôture ;
- tests multi-pays ;
- tests multi-langues ;
- tests d’accessibilité ;
- tests de double validation ;
- tests d’audit ;
- tests de satisfaction ;
- tests de qualité.

---

# 95. Critères d’acceptation

Le support client est validé lorsque :

- les catégories sont définies ;
- les canaux sont intégrés ;
- les tickets possèdent une référence ;
- les files et priorités sont configurées ;
- les SLA sont mesurés ;
- les vérifications d’identité fonctionnent ;
- les données sensibles sont protégées ;
- les incidents sont reliés aux tickets ;
- les contestations de transaction sont gérées ;
- les remboursements passent par un workflow ;
- les réclamations formelles sont tracées ;
- les litiges et recours sont gérés ;
- la médiation est disponible ;
- les réponses sont versionnées ;
- la base de connaissances est disponible ;
- Jini est limité par des permissions ;
- les actions critiques sont approuvées ;
- les métriques sont disponibles ;
- les actions sont auditées ;
- les tests couvrent les scénarios principaux.
