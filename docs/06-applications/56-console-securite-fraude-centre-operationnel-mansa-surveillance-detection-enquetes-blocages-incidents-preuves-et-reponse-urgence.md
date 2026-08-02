# 56 — Console Sécurité, Fraude et Centre opérationnel Mansa : surveillance, détection, enquêtes, blocages, incidents, preuves et réponse d’urgence

## 1. Objet du document

Ce document définit l’architecture officielle de la **Console Sécurité, Fraude et Centre opérationnel Mansa**.

Cette console est destinée aux équipes spécialisées chargées de protéger l’ensemble de l’écosystème Mansa.

Elle couvre notamment :

- les comptes clients ;
- les comptes commerçants ;
- les agents ;
- les administrateurs ;
- les institutions ;
- les entreprises ;
- les établissements scolaires ;
- les partenaires financiers ;
- les développeurs ;
- les cartes ;
- les paiements ;
- les transferts ;
- les dépôts ;
- les retraits ;
- les TPE ;
- les DAB ;
- les appareils ;
- les API ;
- les webhooks ;
- les sessions ;
- les clés ;
- les certificats ;
- les incidents ;
- les alertes ;
- les enquêtes ;
- les preuves ;
- les blocages ;
- les restrictions ;
- les réponses d’urgence ;
- les rapports ;
- les audits ;
- la conformité ;
- la collaboration avec les partenaires autorisés.

L’objectif est de créer un centre de contrôle capable de :

- détecter les comportements suspects ;
- analyser les risques ;
- surveiller les transactions ;
- protéger les comptes ;
- bloquer rapidement un canal compromis ;
- ouvrir et suivre des enquêtes ;
- protéger les preuves ;
- répondre aux incidents majeurs ;
- coordonner les équipes ;
- produire une traçabilité complète ;
- réduire les pertes financières ;
- prévenir la fraude interne et externe ;
- protéger les utilisateurs ;
- protéger les partenaires ;
- protéger les infrastructures Mansa.

---

# 2. Principes fondamentaux

## 2.1 Séparation entre sécurité, fraude et conformité

La console peut regrouper plusieurs équipes, mais leurs responsabilités doivent rester distinctes.

Exemples :

- la sécurité protège les systèmes et accès ;
- la fraude analyse les comportements suspects ;
- la conformité traite les obligations réglementaires ;
- le support accompagne le client ;
- la finance exécute les corrections comptables ;
- l’administration valide certaines actions critiques.

---

## 2.2 Aucune action critique ne doit être exécutée sans traçabilité

Toute action doit enregistrer :

- utilisateur ;
- rôle ;
- équipe ;
- pays ;
- environnement ;
- ressource ;
- date ;
- heure ;
- appareil ;
- IP ;
- ancienne valeur ;
- nouvelle valeur ;
- motif ;
- preuve ;
- approbateur ;
- résultat ;
- référence de corrélation.

---

## 2.3 Aucun analyste ne doit pouvoir modifier directement le ledger

Un analyste peut :

- signaler ;
- recommander ;
- restreindre ;
- suspendre ;
- ouvrir un dossier ;
- demander une correction ;
- demander un remboursement.

Il ne doit pas modifier directement :

- un solde ;
- une écriture ;
- une transaction ;
- un règlement ;
- un compte de cantonnement.

---

## 2.4 Les blocages doivent être proportionnés

Le système doit permettre plusieurs niveaux de réponse :

- surveillance renforcée ;
- restriction d’un canal ;
- limitation temporaire ;
- blocage de carte ;
- révocation de session ;
- suspension de compte ;
- suspension d’agent ;
- suspension de TPE ;
- blocage total d’urgence.

---

## 2.5 Les actions automatiques doivent rester contrôlées

Le moteur de risque peut déclencher automatiquement certaines actions limitées.

Exemples :

- demander une authentification renforcée ;
- refuser une transaction ;
- réduire temporairement un plafond ;
- suspendre une session ;
- créer une alerte ;
- mettre une transaction en révision.

Les actions lourdes ou durables doivent suivre un workflow.

---

# 3. Utilisateurs de la console

Rôles possibles :

```text
SECURITY_OPERATIONS_ANALYST
SECURITY_INCIDENT_MANAGER
FRAUD_ANALYST_L1
FRAUD_ANALYST_L2
FRAUD_INVESTIGATOR
FRAUD_MANAGER
AML_ANALYST
COMPLIANCE_OFFICER
CARD_FRAUD_ANALYST
MERCHANT_RISK_ANALYST
AGENT_RISK_ANALYST
CYBERSECURITY_ENGINEER
DIGITAL_FORENSICS_ANALYST
THREAT_INTELLIGENCE_ANALYST
AUDITOR
VIEWER
```

---

# 4. Permissions

Exemples :

```text
security.dashboard.read
security.alert.read
security.alert.assign
security.alert.manage
security.incident.create
security.incident.manage
security.session.revoke
security.device.restrict
security.api_key.revoke
security.certificate.revoke
security.rule.read
security.rule.manage
fraud.case.read
fraud.case.create
fraud.case.assign
fraud.case.manage
fraud.account.restrict
fraud.card.block
fraud.transaction.review
fraud.evidence.read
fraud.evidence.manage
fraud.report.read
security.audit.read
```

---

# 5. Périmètres

Un utilisateur peut être limité à :

- un pays ;
- une région ;
- un produit ;
- un type de client ;
- un canal ;
- un partenaire ;
- un niveau de risque ;
- une organisation ;
- un environnement ;
- un type d’incident ;
- un montant ;
- une file d’enquête.

---

# 6. Authentification

Méthodes possibles :

- mot de passe fort ;
- MFA ;
- passkey ;
- clé de sécurité ;
- certificat ;
- SSO ;
- appareil géré ;
- IP autorisée ;
- réseau privé ;
- accès bastion.

---

# 7. MFA obligatoire

Le MFA doit être obligatoire pour :

- tous les analystes ;
- tous les accès production ;
- toute révocation ;
- tout blocage ;
- tout export ;
- tout accès à une preuve sensible ;
- toute modification de règle ;
- toute clôture d’incident majeur ;
- tout accès d’urgence.

---

# 8. Architecture du projet

Structure recommandée :

```text
src/
├── auth/
├── dashboard/
├── alerts/
├── cases/
├── investigations/
├── transactions/
├── accounts/
├── cards/
├── devices/
├── sessions/
├── merchants/
├── agents/
├── terminals/
├── atms/
├── api-security/
├── webhooks/
├── identities/
├── threat-intelligence/
├── rules/
├── scoring/
├── monitoring/
├── incidents/
├── response/
├── evidence/
├── forensics/
├── sanctions/
├── reports/
├── approvals/
├── notifications/
├── integrations/
├── audit/
└── settings/
```

---

# 9. Navigation principale

Navigation recommandée :

```text
Tableau de bord
Alertes
Dossiers
Transactions
Comptes
Incidents
Règles
Rapports
Configuration
```

Menu secondaire :

- Cartes ;
- Appareils ;
- Sessions ;
- Agents ;
- Commerçants ;
- TPE ;
- DAB ;
- API ;
- Webhooks ;
- Preuves ;
- Forensique ;
- Renseignement ;
- Approbations ;
- Audit.

---

# 10. Tableau de bord sécurité

Le tableau de bord peut afficher :

- alertes ouvertes ;
- alertes critiques ;
- incidents majeurs ;
- comptes restreints ;
- cartes bloquées ;
- appareils suspects ;
- sessions révoquées ;
- agents suspendus ;
- TPE suspendus ;
- tentatives de connexion ;
- échecs MFA ;
- transactions refusées ;
- pertes évitées estimées ;
- dossiers en attente ;
- temps moyen de traitement ;
- pays les plus touchés ;
- disponibilité des systèmes.

---

# 11. Tableau de bord fraude

Il peut afficher :

- volume analysé ;
- transactions suspectes ;
- montants à risque ;
- fraudes confirmées ;
- faux positifs ;
- cas ouverts ;
- cas escaladés ;
- remboursements liés ;
- chargebacks ;
- comptes mule ;
- agents suspects ;
- commerçants suspects ;
- cartes compromises ;
- tendances par canal.

---

# 12. Alertes

Une alerte peut concerner :

- connexion ;
- appareil ;
- session ;
- paiement ;
- transfert ;
- dépôt ;
- retrait ;
- carte ;
- Mobile Money ;
- TPE ;
- DAB ;
- agent ;
- commerçant ;
- institution ;
- administrateur ;
- API ;
- clé ;
- certificat ;
- webhook ;
- export ;
- infrastructure.

---

# 13. Données d’une alerte

Chaque alerte doit contenir :

- identifiant ;
- type ;
- règle déclenchée ;
- score ;
- sévérité ;
- ressource ;
- utilisateur ;
- montant éventuel ;
- pays ;
- appareil ;
- IP ;
- localisation ;
- date ;
- statut ;
- analyste ;
- décision ;
- actions liées ;
- preuves ;
- historique.

---

# 14. Sévérités

- INFO ;
- LOW ;
- MEDIUM ;
- HIGH ;
- CRITICAL.

---

# 15. Statuts des alertes

- NEW ;
- ASSIGNED ;
- UNDER_REVIEW ;
- INFORMATION_REQUIRED ;
- ACTION_REQUIRED ;
- ESCALATED ;
- CONFIRMED ;
- FALSE_POSITIVE ;
- RESOLVED ;
- CLOSED.

---

# 16. Routage des alertes

Le routage peut dépendre :

- type ;
- pays ;
- produit ;
- montant ;
- partenaire ;
- niveau de risque ;
- heure ;
- compétence ;
- disponibilité ;
- équipe ;
- environnement ;
- incident lié.

---

# 17. Scores de risque

Le système peut calculer un score selon :

- identité ;
- appareil ;
- comportement ;
- historique ;
- transaction ;
- montant ;
- localisation ;
- bénéficiaire ;
- commerçant ;
- agent ;
- heure ;
- fréquence ;
- pays ;
- partenaire ;
- réseau ;
- incident.

---

# 18. Niveaux de risque

Exemple :

```text
0–20   : faible
21–40  : modéré
41–60  : élevé
61–80  : très élevé
81–100 : critique
```

Les seuils doivent être administrables.

---

# 19. Facteurs de risque

Exemples :

- nouvel appareil ;
- nouvelle localisation ;
- IP anonyme ;
- VPN suspect ;
- appareil rooté ;
- appareil compromis ;
- vitesse de transaction anormale ;
- bénéficiaire récent ;
- montant inhabituel ;
- pays à risque ;
- marchand inhabituel ;
- carte récemment créée ;
- plusieurs échecs ;
- changement de téléphone ;
- changement de mot de passe ;
- comportement automatisé ;
- compte dormant réactivé.

---

# 20. Vélocité

Le moteur doit analyser :

- transactions par minute ;
- transactions par heure ;
- tentatives ;
- bénéficiaires ;
- cartes ;
- appareils ;
- IP ;
- agents ;
- commerçants ;
- retraits ;
- dépôts ;
- connexions ;
- changements de profil.

---

# 21. Fraude liée aux comptes

Exemples :

- prise de contrôle de compte ;
- vol d’identité ;
- compte mule ;
- identité synthétique ;
- faux documents ;
- plusieurs comptes liés ;
- récupération de compte abusive ;
- changement de téléphone suspect ;
- changement de mot de passe suivi d’un transfert.

---

# 22. Fraude liée aux cartes

Exemples :

- carte volée ;
- carte copiée ;
- paiement à distance suspect ;
- paiement international inhabituel ;
- essais multiples ;
- carte virtuelle compromise ;
- token Wallet compromis ;
- retrait DAB suspect ;
- paiement après opposition ;
- carte utilisée dans plusieurs pays rapidement.

---

# 23. Fraude liée aux agents

Exemples :

- faux dépôt ;
- retrait frauduleux ;
- manipulation de caisse ;
- collusion ;
- création de clients fictifs ;
- utilisation de comptes personnels ;
- volume anormal ;
- annulations fréquentes ;
- sous-déclaration de caisse ;
- détournement de liquidité ;
- faux reçu ;
- utilisation hors zone.

---

# 24. Fraude liée aux commerçants

Exemples :

- transactions fictives ;
- auto-paiement ;
- fractionnement ;
- remboursements abusifs ;
- collusion ;
- faux commerce ;
- changement bancaire suspect ;
- activité incompatible avec le secteur déclaré ;
- chargebacks élevés ;
- volume brutalement augmenté.

---

# 25. Fraude liée aux TPE

Exemples :

- terminal cloné ;
- certificat compromis ;
- localisation incohérente ;
- application modifiée ;
- version non autorisée ;
- terminal rooté ;
- paiements automatisés ;
- répétition de petits montants ;
- utilisation par un autre commerce ;
- réseau suspect.

---

# 26. Fraude liée aux DAB

Exemples :

- skimming ;
- cash trapping ;
- jackpotting ;
- ouverture non autorisée ;
- retrait sans carte suspect ;
- multiples erreurs cassette ;
- activité hors horaire ;
- débit sans remise ;
- maintenance frauduleuse ;
- accès technique non autorisé.

---

# 27. Fraude liée aux services publics

Exemples :

- fausse amende ;
- faux reçu ;
- suppression de référence ;
- compte personnel d’agent ;
- faux bénéficiaire de bourse ;
- doublon d’aide ;
- modification tarifaire non autorisée ;
- annulation injustifiée ;
- versement massif suspect ;
- détournement de compte de règlement.

---

# 28. Fraude interne

Le système doit surveiller :

- consultation abusive ;
- export massif ;
- modification de rôle ;
- changement de compte bancaire ;
- suppression tentée ;
- consultation sans dossier ;
- utilisation d’un compte partagé ;
- action hors horaire ;
- accès hors pays ;
- changement de règle ;
- approbation inhabituelle ;
- contournement de workflow.

---

# 29. Dossiers fraude

Chaque dossier doit contenir :

- référence ;
- type ;
- sujet ;
- transactions ;
- comptes ;
- personnes ;
- organisations ;
- alertes ;
- score ;
- montant ;
- analyste ;
- équipe ;
- priorité ;
- preuves ;
- décisions ;
- actions ;
- historique ;
- conclusion.

---

# 30. Statuts des dossiers

- OPEN ;
- TRIAGE ;
- ASSIGNED ;
- INVESTIGATING ;
- INFORMATION_REQUIRED ;
- ACTION_PENDING ;
- ESCALATED ;
- CONFIRMED ;
- FALSE_POSITIVE ;
- RECOVERY_PENDING ;
- CLOSED ;
- ARCHIVED.

---

# 31. Relations entre entités

Le système doit pouvoir relier :

- comptes ;
- téléphones ;
- appareils ;
- IP ;
- cartes ;
- bénéficiaires ;
- commerçants ;
- agents ;
- TPE ;
- DAB ;
- adresses ;
- documents ;
- partenaires ;
- transactions.

---

# 32. Graphes de fraude

La console peut afficher un graphe permettant d’identifier :

- comptes liés ;
- appareils partagés ;
- bénéficiaires communs ;
- IP communes ;
- documents réutilisés ;
- commerçants liés ;
- agents liés ;
- transferts circulaires ;
- réseaux de comptes mule ;
- chaînes de blanchiment.

---

# 33. Chronologie d’enquête

Chaque dossier doit afficher :

- événements ;
- transactions ;
- connexions ;
- changements ;
- actions ;
- communications ;
- blocages ;
- pièces ;
- décisions ;
- remboursements ;
- clôture.

---

# 34. Preuves

Types possibles :

- journal système ;
- transaction ;
- capture ;
- document ;
- photo ;
- vidéo ;
- appel ;
- e-mail ;
- SMS ;
- message ;
- fichier ;
- rapport ;
- donnée appareil ;
- géolocalisation ;
- relevé partenaire ;
- preuve DAB ;
- preuve TPE.

---

# 35. Intégrité des preuves

Chaque preuve doit contenir :

- identifiant ;
- hash ;
- auteur ;
- source ;
- date ;
- heure ;
- dossier ;
- statut ;
- accès ;
- chaîne de conservation ;
- politique de rétention ;
- historique de consultation.

---

# 36. Chaîne de conservation

Le système doit enregistrer :

- création ;
- collecte ;
- transfert ;
- consultation ;
- copie ;
- export ;
- analyse ;
- archivage ;
- suppression autorisée.

---

# 37. Accès aux preuves

L’accès doit dépendre :

- du rôle ;
- du dossier ;
- du pays ;
- de la sensibilité ;
- de l’équipe ;
- de la mission ;
- de l’autorisation ;
- de la durée.

---

# 38. Forensique numérique

Le module peut permettre :

- collecte de journaux ;
- analyse d’appareil ;
- analyse de session ;
- analyse d’IP ;
- analyse de certificat ;
- analyse de clé ;
- analyse de fichier ;
- chronologie ;
- corrélation ;
- génération de rapport.

---

# 39. Surveillance des appareils

Le système doit suivre :

- modèle ;
- OS ;
- version ;
- identifiant ;
- état root ou jailbreak ;
- certificat ;
- intégrité ;
- dernière activité ;
- IP ;
- pays ;
- sessions ;
- comptes liés ;
- risque ;
- statut.

---

# 40. Statuts d’un appareil

- TRUSTED ;
- RECOGNIZED ;
- NEW ;
- SUSPICIOUS ;
- COMPROMISED ;
- BLOCKED ;
- REVOKED ;
- UNDER_REVIEW.

---

# 41. Actions sur les appareils

Selon permission :

- demander une vérification ;
- retirer la confiance ;
- révoquer une session ;
- bloquer l’appareil ;
- limiter les opérations ;
- exiger un nouveau KYC ;
- ouvrir une enquête ;
- alerter l’utilisateur.

---

# 42. Surveillance des sessions

La console doit afficher :

- utilisateur ;
- appareil ;
- IP ;
- pays ;
- début ;
- dernière activité ;
- authentification ;
- risque ;
- canal ;
- environnement ;
- statut.

---

# 43. Actions sur les sessions

- révoquer ;
- suspendre ;
- forcer la reconnexion ;
- exiger MFA ;
- limiter ;
- marquer comme suspecte ;
- relier à un incident ;
- notifier.

---

# 44. Surveillance des cartes

La console doit suivre :

- statut ;
- transactions ;
- pays ;
- commerçants ;
- tentatives ;
- retraits ;
- e-commerce ;
- sans contact ;
- tokenisation ;
- Wallet ;
- risque ;
- opposition ;
- incidents.

---

# 45. Blocage de carte

Types :

- temporaire ;
- canal spécifique ;
- e-commerce ;
- international ;
- sans contact ;
- retrait ;
- total ;
- définitif.

---

# 46. Surveillance des comptes

La console doit afficher :

- statut ;
- niveau KYC ;
- risque ;
- restrictions ;
- appareils ;
- sessions ;
- transactions ;
- bénéficiaires ;
- incidents ;
- litiges ;
- historique ;
- dossiers liés.

---

# 47. Restrictions de compte

Exemples :

- transfert interdit ;
- retrait interdit ;
- paiement interdit ;
- carte bloquée ;
- changement de profil interdit ;
- nouveaux bénéficiaires interdits ;
- limite réduite ;
- accès lecture seule ;
- compte suspendu.

---

# 48. Durée des restrictions

Une restriction doit pouvoir être :

- temporaire ;
- jusqu’à vérification ;
- jusqu’à date ;
- jusqu’à décision ;
- permanente selon procédure ;
- révisable ;
- automatiquement expirante.

---

# 49. Révision des restrictions

Chaque restriction doit contenir :

- motif ;
- demandeur ;
- date ;
- durée ;
- preuve ;
- approbateur ;
- effet ;
- révision ;
- statut ;
- audit.

---

# 50. Surveillance des API

Le système doit détecter :

- hausse anormale ;
- abus de quota ;
- clé compromise ;
- IP inconnue ;
- appels interdits ;
- erreurs répétées ;
- injection ;
- scraping ;
- contournement ;
- tentative d’accès à un autre périmètre ;
- webhook frauduleux ;
- payload inhabituel.

---

# 51. Clés et certificats

La console doit permettre :

- consultation sécurisée ;
- révocation ;
- rotation ;
- expiration ;
- suspension ;
- analyse d’usage ;
- alerte ;
- lien avec partenaire ;
- lien avec incident.

Les secrets ne doivent pas être affichés.

---

# 52. Renseignement sur les menaces

Le système peut centraliser :

- IP malveillantes ;
- domaines frauduleux ;
- appareils compromis ;
- numéros suspects ;
- comptes mule ;
- cartes compromises ;
- signatures ;
- indicateurs ;
- campagnes de phishing ;
- faux sites ;
- faux agents ;
- nouveaux modes opératoires.

---

# 53. Listes de surveillance

Types :

- comptes ;
- personnes ;
- appareils ;
- IP ;
- commerçants ;
- agents ;
- partenaires ;
- domaines ;
- numéros ;
- pays ;
- cartes ;
- bénéficiaires.

---

# 54. Listes d’autorisation

Le système peut également gérer :

- IP autorisées ;
- appareils approuvés ;
- domaines officiels ;
- partenaires approuvés ;
- comptes techniques ;
- certificats ;
- clés ;
- réseaux ;
- exceptions temporaires.

---

# 55. Règles de détection

Une règle doit contenir :

- code ;
- nom ;
- description ;
- produit ;
- pays ;
- canal ;
- condition ;
- score ;
- action ;
- statut ;
- version ;
- auteur ;
- approbateur ;
- date d’effet ;
- historique.

---

# 56. Types de règles

- seuil ;
- fréquence ;
- séquence ;
- comportement ;
- géographique ;
- identité ;
- appareil ;
- liste ;
- relation ;
- montant ;
- partenaire ;
- modèle statistique ;
- modèle IA ;
- règle manuelle ;
- règle réglementaire.

---

# 57. Statuts des règles

- DRAFT ;
- TESTING ;
- REVIEW ;
- APPROVED ;
- ACTIVE ;
- SHADOW ;
- SUSPENDED ;
- RETIRED ;
- ARCHIVED.

---

# 58. Mode Shadow

Une règle en mode Shadow doit :

- analyser ;
- produire un score ;
- générer des statistiques ;
- ne pas bloquer ;
- ne pas affecter le client ;
- permettre une évaluation avant activation.

---

# 59. Simulation de règle

Avant activation, le système doit permettre de tester :

- historique ;
- faux positifs ;
- vrais positifs ;
- montants ;
- pays ;
- produits ;
- segments ;
- impacts ;
- blocages potentiels ;
- charge opérationnelle.

---

# 60. Actions automatiques

Exemples :

- autoriser ;
- demander MFA ;
- demander OTP ;
- refuser ;
- mettre en attente ;
- limiter ;
- suspendre une session ;
- bloquer une carte ;
- créer une alerte ;
- ouvrir un dossier ;
- notifier ;
- exiger une revue manuelle.

---

# 61. Actions manuelles

Selon permissions :

- confirmer une fraude ;
- classer un faux positif ;
- restreindre un compte ;
- bloquer une carte ;
- suspendre un agent ;
- suspendre un TPE ;
- révoquer une session ;
- révoquer une clé ;
- demander un remboursement ;
- escalader ;
- clôturer.

---

# 62. Approbations

Peuvent nécessiter une approbation :

- blocage permanent ;
- suspension d’un partenaire ;
- fermeture de compte ;
- réactivation après fraude ;
- remboursement élevé ;
- suppression logique ;
- export de preuves ;
- modification de règle active ;
- révocation massive ;
- activation d’un blocage national.

---

# 63. Double validation

Peut être exigée pour :

- fermeture de compte ;
- déblocage après fraude confirmée ;
- modification d’une règle critique ;
- suspension d’un opérateur ;
- blocage massif ;
- remboursement important ;
- export judiciaire ;
- révocation d’un certificat racine ;
- arrêt d’un service ;
- réponse d’urgence majeure.

---

# 64. Séparation demandeur-validateur

Le demandeur ne doit pas approuver seul une action critique.

Exemple :

```text
Analyste propose
→ Manager fraude contrôle
→ Sécurité ou conformité approuve
→ Backend exécute
```

---

# 65. Centre opérationnel de sécurité

Le centre doit surveiller :

- authentification ;
- infrastructures ;
- API ;
- bases ;
- certificats ;
- secrets ;
- journaux ;
- applications ;
- réseaux ;
- partenaires ;
- terminaux ;
- disponibilité ;
- vulnérabilités ;
- incidents.

---

# 66. Incidents de sécurité

Exemples :

- compromission de compte ;
- fuite de données ;
- attaque API ;
- déni de service ;
- clé compromise ;
- certificat compromis ;
- malware ;
- terminal compromis ;
- intrusion ;
- phishing ;
- faux site ;
- exfiltration ;
- erreur de configuration ;
- activité interne suspecte.

---

# 67. Gravité d’un incident

- SEV_4 : faible ;
- SEV_3 : modéré ;
- SEV_2 : important ;
- SEV_1 : critique.

---

# 68. Statuts d’incident

- DETECTED ;
- ACKNOWLEDGED ;
- INVESTIGATING ;
- CONTAINING ;
- MITIGATING ;
- RECOVERING ;
- MONITORING ;
- RESOLVED ;
- CLOSED.

---

# 69. Dossier d’incident

Il doit contenir :

- référence ;
- gravité ;
- service ;
- pays ;
- environnement ;
- début ;
- détection ;
- impact ;
- utilisateurs touchés ;
- montants ;
- responsable ;
- équipe ;
- chronologie ;
- actions ;
- communications ;
- preuves ;
- résolution ;
- post-mortem.

---

# 70. Réponse à incident

Étapes possibles :

1. détection ;
2. qualification ;
3. confinement ;
4. analyse ;
5. éradication ;
6. récupération ;
7. surveillance ;
8. communication ;
9. clôture ;
10. retour d’expérience.

---

# 71. Playbooks

La console doit fournir des procédures pour :

- compte compromis ;
- carte compromise ;
- clé API compromise ;
- DAB compromis ;
- TPE compromis ;
- faux agent ;
- fraude massive ;
- fuite de données ;
- phishing ;
- incident Mobile Money ;
- incident banque ;
- panne critique ;
- fraude interne ;
- compte mule.

---

# 72. Mode d’urgence

Le système doit pouvoir activer :

- lecture seule ;
- blocage de canal ;
- suspension par pays ;
- blocage de paiements ;
- blocage de retraits ;
- blocage de transferts ;
- suspension d’un partenaire ;
- révocation massive de sessions ;
- maintenance forcée ;
- limite réduite.

---

# 73. Contrôle du mode d’urgence

Toute activation doit préciser :

- demandeur ;
- approbateur ;
- raison ;
- périmètre ;
- date ;
- heure ;
- durée ;
- services concernés ;
- impact ;
- stratégie de sortie ;
- audit.

---

# 74. Communication de crise

Le système doit permettre de coordonner :

- équipe sécurité ;
- direction ;
- support ;
- finance ;
- conformité ;
- juridique ;
- partenaires ;
- institutions ;
- communication ;
- autorités compétentes selon cadre légal.

---

# 75. Notifications d’incident

Canaux possibles :

- portail ;
- Push ;
- SMS ;
- e-mail ;
- téléphone ;
- messagerie interne ;
- page de statut ;
- canal d’astreinte.

---

# 76. Gestion des faux positifs

Le système doit enregistrer :

- alerte ;
- règle ;
- analyste ;
- décision ;
- motif ;
- segment ;
- impact ;
- correction ;
- retour au moteur de risque.

---

# 77. Réentraînement et amélioration

Les données validées peuvent servir à :

- améliorer les règles ;
- réduire les faux positifs ;
- détecter de nouveaux schémas ;
- ajuster les seuils ;
- évaluer les modèles ;
- renforcer les playbooks.

Les données doivent être utilisées selon les règles de confidentialité.

---

# 78. IA et modèles de risque

Les modèles peuvent aider à :

- classer les alertes ;
- détecter les anomalies ;
- identifier des relations ;
- suggérer une priorité ;
- résumer un dossier ;
- détecter des schémas ;
- estimer un risque ;
- proposer une prochaine action.

---

# 79. Limites de l’IA

L’IA ne doit pas :

- fermer seule un compte ;
- déclarer seule une personne frauduleuse ;
- exécuter seule un remboursement ;
- modifier le ledger ;
- supprimer une preuve ;
- contourner les permissions ;
- inventer un motif ;
- bloquer durablement sans règle et validation.

---

# 80. Sanctions et PEP

La console peut être connectée aux modules de conformité pour :

- sanctions ;
- PEP ;
- listes internes ;
- pays à risque ;
- bénéficiaires ;
- entités liées ;
- vérification continue ;
- alertes de correspondance.

---

# 81. Rapprochement avec les partenaires

La console doit pouvoir comparer :

- alertes Mansa ;
- incidents banque ;
- incidents Mobile Money ;
- chargebacks ;
- fichiers carte ;
- DAB ;
- TPE ;
- règlements ;
- rapports partenaires ;
- fraude confirmée.

---

# 82. Collaboration interéquipes

Un dossier peut être partagé avec :

- support ;
- conformité ;
- finance ;
- juridique ;
- sécurité ;
- partenaire ;
- institution ;
- direction ;
- audit.

Les accès doivent rester limités.

---

# 83. Rapports

Rapports possibles :

- alertes ;
- fraude ;
- pertes ;
- pertes évitées ;
- faux positifs ;
- incidents ;
- comptes compromis ;
- cartes ;
- agents ;
- commerçants ;
- TPE ;
- DAB ;
- API ;
- sessions ;
- appareils ;
- règles ;
- pays ;
- produits ;
- partenaires ;
- temps de traitement ;
- performance analystes.

---

# 84. Rapports réglementaires

Selon les obligations, la console peut préparer :

- déclaration d’opération suspecte ;
- rapport d’incident ;
- rapport de fraude ;
- rapport de sécurité ;
- conservation de preuve ;
- journal de décision ;
- rapport de pertes ;
- rapport de contrôle interne.

La transmission doit suivre un workflow autorisé.

---

# 85. Exports

Formats possibles :

- CSV ;
- XLSX ;
- PDF ;
- JSON ;
- paquet de preuve ;
- API.

Les exports doivent être :

- justifiés ;
- limités ;
- chiffrés ;
- signés ;
- temporaires ;
- auditables ;
- approuvés selon sensibilité.

---

# 86. Rapports programmés

Un rapport peut être généré :

- chaque heure ;
- chaque jour ;
- chaque semaine ;
- chaque mois ;
- après incident ;
- après fraude confirmée ;
- après clôture ;
- après changement de règle.

---

# 87. API

Exemples :

```http
GET    /security/dashboard
GET    /security/alerts
GET    /security/alerts/{id}
POST   /security/alerts/{id}/assign
POST   /security/alerts/{id}/resolve

GET    /fraud/cases
POST   /fraud/cases
GET    /fraud/cases/{id}
PATCH  /fraud/cases/{id}

POST   /fraud/accounts/{id}/restriction-requests
POST   /fraud/cards/{id}/block-requests
POST   /security/sessions/{id}/revoke

GET    /security/incidents
POST   /security/incidents
POST   /security/incidents/{id}/emergency-actions

GET    /security/rules
POST   /security/rules
POST   /security/rules/{id}/simulate
POST   /security/rules/{id}/publish

GET    /security/evidence
GET    /security/reports
GET    /security/audit
```

---

# 88. Webhooks

Événements possibles :

```text
security.alert.created
security.alert.escalated
security.session.revoked
security.device.blocked
security.api_key.revoked
security.incident.created
security.incident.updated
security.incident.resolved
fraud.case.created
fraud.case.confirmed
fraud.account.restricted
fraud.card.blocked
fraud.agent.suspended
fraud.rule.triggered
fraud.false_positive.confirmed
```

---

# 89. Intégrations

La console peut se connecter à :

- applications Mansa ;
- API Gateway ;
- moteur de risque ;
- SIEM ;
- observabilité ;
- banque ;
- Mobile Money ;
- réseau carte ;
- KYC ;
- KYB ;
- sanctions ;
- support ;
- ledger ;
- TPE ;
- DAB ;
- gestion des secrets ;
- gestion des certificats ;
- page de statut ;
- outil d’astreinte.

---

# 90. Multi-pays

Chaque pays peut avoir :

- règles ;
- seuils ;
- équipes ;
- obligations ;
- calendriers ;
- partenaires ;
- procédures ;
- listes ;
- langues ;
- rapports ;
- durées de conservation ;
- autorités compétentes.

---

# 91. Réseau faible

La console doit prévoir :

- interface légère ;
- chargement progressif ;
- mode texte ;
- sauvegarde de brouillon ;
- reprise ;
- cache contrôlé ;
- files locales limitées ;
- synchronisation ;
- priorité aux alertes critiques.

---

# 92. Sécurité de la console

Mesures principales :

- MFA ;
- RBAC ;
- ABAC ;
- chiffrement ;
- appareil géré ;
- certificat ;
- IP allowlist ;
- accès bastion ;
- session courte ;
- réauthentification ;
- watermark ;
- masquage ;
- détection de capture ;
- audit ;
- surveillance ;
- révocation.

---

# 93. Protection contre les abus internes

Le système doit détecter :

- recherche massive ;
- consultation sans dossier ;
- téléchargement inhabituel ;
- export massif ;
- accès hors horaire ;
- partage de compte ;
- modification de preuve ;
- fermeture rapide de dossiers ;
- déblocages répétés ;
- accès à des proches ;
- activité incompatible avec le rôle.

---

# 94. Audit

Le journal doit contenir :

- utilisateur ;
- rôle ;
- équipe ;
- dossier ;
- incident ;
- ressource ;
- action ;
- ancienne valeur ;
- nouvelle valeur ;
- date ;
- heure ;
- appareil ;
- IP ;
- pays ;
- environnement ;
- motif ;
- résultat ;
- approbateur.

---

# 95. Immutabilité des audits

Les audits ne doivent pas être :

- modifiés ;
- supprimés ;
- réécrits ;
- désactivés ;
- masqués sans trace ;
- exportés sans permission.

---

# 96. Modèles principaux

- SecurityUser
- SecurityRole
- SecurityPermission
- SecurityAlert
- SecurityAlertRule
- SecurityRiskScore
- FraudCase
- FraudCaseEntity
- FraudCaseRelation
- FraudDecision
- FraudRestriction
- SecurityDevice
- SecuritySession
- SecurityApiKeyEvent
- SecurityCertificateEvent
- SecurityIncident
- SecurityIncidentAction
- SecurityPlaybook
- SecurityEvidence
- EvidenceCustodyEvent
- ThreatIndicator
- Watchlist
- Allowlist
- FraudRule
- FraudRuleVersion
- FraudRuleSimulation
- SecurityApproval
- SecurityNotification
- SecurityReport
- SecurityAudit

---

# 97. Analytics

Événements possibles :

```text
security_login_completed
security_alert_created
security_alert_assigned
security_alert_resolved
fraud_case_created
fraud_case_confirmed
fraud_false_positive_confirmed
fraud_account_restricted
fraud_card_blocked
security_session_revoked
security_device_blocked
security_incident_created
security_incident_resolved
security_rule_simulated
security_rule_published
security_emergency_mode_enabled
security_evidence_exported
security_audit_opened
```

---

# 98. Données analytics interdites

Ne pas transmettre :

- PIN ;
- OTP ;
- CVV ;
- numéro complet de carte ;
- clé privée ;
- secret API ;
- mot de passe ;
- preuve complète ;
- document complet ;
- données biométriques ;
- payload sensible complet ;
- rapport d’enquête complet ;
- contenu confidentiel.

---

# 99. Tests

- tests d’authentification ;
- tests MFA ;
- tests de rôles ;
- tests de permissions ;
- tests de périmètres ;
- tests d’alertes ;
- tests de routage ;
- tests de score ;
- tests de vélocité ;
- tests de règles ;
- tests Shadow ;
- tests de simulation ;
- tests de comptes ;
- tests de cartes ;
- tests d’appareils ;
- tests de sessions ;
- tests d’agents ;
- tests commerçants ;
- tests TPE ;
- tests DAB ;
- tests API ;
- tests de clés ;
- tests de certificats ;
- tests de dossiers ;
- tests de graphes ;
- tests de preuves ;
- tests de chaîne de conservation ;
- tests forensiques ;
- tests de restrictions ;
- tests de blocages ;
- tests d’approbation ;
- tests d’incident ;
- tests de playbooks ;
- tests de mode d’urgence ;
- tests de notifications ;
- tests d’IA ;
- tests de faux positifs ;
- tests multi-pays ;
- tests réseau faible ;
- tests sécurité ;
- tests audit ;
- tests performance ;
- tests accessibilité.

---

# 100. Règles métier

1. Chaque utilisateur possède un compte nominatif.
2. Les comptes partagés sont interdits.
3. Les accès sont limités par rôle et périmètre.
4. Toute consultation sensible est auditée.
5. Aucun analyste ne modifie directement le ledger.
6. Les restrictions sont proportionnées.
7. Les actions automatiques sont limitées.
8. Les actions durables utilisent un workflow.
9. Les preuves sont hashées.
10. La chaîne de conservation est enregistrée.
11. Les dossiers possèdent une référence unique.
12. Les alertes peuvent être regroupées.
13. Les règles sont versionnées.
14. Les règles peuvent être testées en mode Shadow.
15. Les faux positifs sont enregistrés.
16. Les appareils compromis peuvent être bloqués.
17. Les sessions peuvent être révoquées.
18. Les cartes peuvent être bloquées par canal.
19. Les partenaires restent isolés.
20. Les incidents utilisent des playbooks.
21. Le mode d’urgence est temporaire et audité.
22. L’IA respecte les permissions.
23. Les exports de preuves sont protégés.
24. Le demandeur ne valide pas seul une action critique.
25. Les audits sont immuables.

---

# 101. Critères d’acceptation

La Console Sécurité, Fraude et Centre opérationnel Mansa est validée lorsque :

- les équipes peuvent se connecter avec MFA ;
- les rôles et périmètres sont appliqués ;
- les alertes sont centralisées ;
- les scores de risque sont disponibles ;
- les règles sont configurables ;
- le mode Shadow fonctionne ;
- les simulations sont disponibles ;
- les dossiers fraude sont administrables ;
- les relations entre entités sont visibles ;
- les graphes de fraude sont disponibles ;
- les preuves sont protégées ;
- la chaîne de conservation est complète ;
- les appareils sont surveillés ;
- les sessions peuvent être révoquées ;
- les cartes peuvent être bloquées ;
- les comptes peuvent être restreints ;
- les agents et commerçants suspects peuvent être traités ;
- les TPE et DAB sont surveillés ;
- les API, clés et certificats sont surveillés ;
- les listes de surveillance sont administrables ;
- les incidents sont centralisés ;
- les playbooks sont disponibles ;
- le mode d’urgence est contrôlé ;
- les notifications de crise fonctionnent ;
- les faux positifs sont mesurés ;
- les rapports sont exportables ;
- les actions critiques utilisent une approbation ;
- les audits sont immuables ;
- les tests couvrent les parcours essentiels.
