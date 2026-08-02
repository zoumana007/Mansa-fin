# 55 — Portail Support et Centre de relation client Mansa : tickets, assistance omnicanale, réclamations, litiges, remboursements, SLA et supervision

## 1. Objet du document

Ce document définit l’architecture officielle du **Portail Support et Centre de relation client Mansa**.

Ce portail est destiné aux équipes chargées d’accompagner les utilisateurs et partenaires de l’écosystème Mansa.

Il permet de gérer l’assistance pour :

- les particuliers ;
- les commerçants ;
- les agents ;
- les entreprises ;
- les établissements scolaires ;
- les institutions publiques ;
- les partenaires financiers ;
- les développeurs ;
- les employés internes ;
- les utilisateurs du TPE ;
- les utilisateurs des DAB ;
- les détenteurs de cartes ;
- les bénéficiaires de bourses ;
- les utilisateurs de services publics.

Le portail couvre :

- les tickets ;
- les conversations ;
- le chat ;
- les appels ;
- les e-mails ;
- les SMS ;
- les messages dans les applications ;
- les canaux de messagerie autorisés ;
- les formulaires web ;
- les réclamations ;
- les incidents ;
- les litiges ;
- les remboursements ;
- les contestations ;
- les problèmes de cartes ;
- les problèmes de paiement ;
- les problèmes de transfert ;
- les problèmes de retrait ;
- les problèmes de dépôt ;
- les problèmes de compte ;
- le KYC ;
- le KYB ;
- les problèmes TPE ;
- les problèmes DAB ;
- les services publics ;
- les bourses ;
- les cartes étudiantes ;
- les escalades ;
- les SLA ;
- la satisfaction ;
- les audits ;
- les rapports ;
- l’assurance qualité ;
- la base de connaissances ;
- Jini ;
- les intégrations ;
- la sécurité.

L’objectif est de fournir un centre de support :

- centralisé ;
- rapide ;
- traçable ;
- sécurisé ;
- multicanal ;
- multi-pays ;
- multi-langues ;
- adapté au réseau faible ;
- capable de traiter les demandes simples et les incidents critiques ;
- connecté à toutes les applications Mansa ;
- limité par des rôles et des permissions strictes.

---

# 2. Principes fondamentaux

## 2.1 Le support ne doit voir que les données nécessaires

Un conseiller ne doit pas avoir un accès global au compte d’un utilisateur.

Il ne doit voir que les éléments nécessaires au traitement du dossier.

Exemples :

- identité partiellement masquée ;
- statut du compte ;
- dernières opérations pertinentes ;
- carte masquée ;
- statut KYC ;
- tickets précédents ;
- incidents liés ;
- appareils utiles ;
- communications autorisées.

---

## 2.2 Le support ne doit jamais connaître les secrets du client

Il est interdit d’afficher ou de demander :

- le PIN complet ;
- le mot de passe ;
- le CVV ;
- le numéro complet de carte ;
- un OTP complet ;
- une clé privée ;
- un secret API ;
- les données biométriques ;
- les codes de récupération complets.

---

## 2.3 Le support ne doit jamais modifier directement un solde

Une correction financière doit passer par :

- une demande ;
- une justification ;
- une preuve ;
- un workflow ;
- une approbation ;
- une écriture compensatrice ;
- un audit ;
- un rapprochement.

---

## 2.4 Chaque action doit être traçable

Le système doit enregistrer :

- conseiller ;
- rôle ;
- équipe ;
- pays ;
- ticket ;
- utilisateur concerné ;
- date ;
- heure ;
- appareil ;
- IP ;
- action ;
- ancienne valeur ;
- nouvelle valeur ;
- motif ;
- résultat ;
- approbateur éventuel.

---

## 2.5 Les canaux doivent être centralisés

Une demande commencée par un canal doit pouvoir être poursuivie par un autre canal sans perdre l’historique.

Exemple :

```text
Formulaire web
→ appel
→ chat
→ pièce jointe
→ escalade finance
→ décision
→ notification au client
```

---

## 2.6 Le support doit rester isolé par périmètre

Un agent de support peut être limité à :

- un pays ;
- une langue ;
- un produit ;
- un type de client ;
- un canal ;
- un niveau de priorité ;
- une organisation ;
- une équipe ;
- une région ;
- une catégorie de ticket.

---

# 3. Types d’utilisateurs pris en charge

Le portail doit gérer les demandes provenant de :

- client particulier ;
- client mineur avec responsable ;
- commerçant ;
- agent Cash Network ;
- employé d’entreprise ;
- administrateur d’entreprise ;
- étudiant ;
- parent ;
- établissement scolaire ;
- institution publique ;
- agent public ;
- partenaire bancaire ;
- opérateur Mobile Money ;
- développeur ;
- administrateur interne ;
- technicien ;
- auditeur.

---

# 4. Technologie

Technologie recommandée :

```text
Next.js
TypeScript
```

Composants associés :

- interface temps réel ;
- moteur de tickets ;
- gestion omnicanale ;
- téléphonie intégrée ;
- messagerie ;
- base de connaissances ;
- RBAC ;
- ABAC ;
- MFA ;
- analytics ;
- audit ;
- intégration Jini ;
- système de notifications ;
- moteur de SLA ;
- file d’attente ;
- supervision.

---

# 5. Architecture du portail

Structure recommandée :

```text
src/
├── auth/
├── dashboard/
├── tickets/
├── conversations/
├── channels/
├── calls/
├── chat/
├── email/
├── sms/
├── messaging/
├── customers/
├── merchants/
├── agents/
├── institutions/
├── partners/
├── payments/
├── transfers/
├── cards/
├── cash-network/
├── terminals/
├── atms/
├── disputes/
├── complaints/
├── refunds/
├── incidents/
├── escalations/
├── sla/
├── queues/
├── knowledge-base/
├── macros/
├── quality/
├── satisfaction/
├── reports/
├── jini/
├── notifications/
├── integrations/
├── approvals/
├── audit/
├── security/
└── settings/
```

---

# 6. Navigation principale

Navigation recommandée :

```text
Tableau de bord
Tickets
Conversations
Clients
Files
Incidents
Base de connaissances
Rapports
Configuration
```

Menu secondaire possible :

- Appels ;
- Chat ;
- E-mails ;
- SMS ;
- Réclamations ;
- Litiges ;
- Remboursements ;
- Escalades ;
- SLA ;
- Qualité ;
- Satisfaction ;
- Audit ;
- Jini ;
- Intégrations.

La navigation doit dépendre des permissions.

---

# 7. Tableau de bord support

Le tableau de bord peut afficher :

- tickets ouverts ;
- nouveaux tickets ;
- tickets urgents ;
- tickets hors SLA ;
- tickets non assignés ;
- appels en attente ;
- chats actifs ;
- incidents majeurs ;
- remboursements en attente ;
- litiges ouverts ;
- satisfaction moyenne ;
- temps moyen de réponse ;
- temps moyen de résolution ;
- charge par équipe ;
- disponibilité des agents ;
- langues actives ;
- pays concernés.

---

# 8. Tableaux de bord spécialisés

Vues possibles :

- support niveau 1 ;
- support niveau 2 ;
- support financier ;
- support fraude ;
- support cartes ;
- support Cash Network ;
- support TPE ;
- support DAB ;
- support institutions ;
- support développeurs ;
- responsable qualité ;
- responsable pays ;
- direction support ;
- centre d’incidents.

---

# 9. Rôles

Exemples :

```text
SUPPORT_AGENT_L1
SUPPORT_AGENT_L2
SUPPORT_AGENT_L3
SUPPORT_SUPERVISOR
SUPPORT_MANAGER
FINANCIAL_SUPPORT_AGENT
CARD_SUPPORT_AGENT
CASH_NETWORK_SUPPORT_AGENT
MERCHANT_SUPPORT_AGENT
INSTITUTION_SUPPORT_AGENT
PARTNER_SUPPORT_AGENT
FRAUD_SUPPORT_AGENT
QUALITY_ANALYST
KNOWLEDGE_MANAGER
AUDITOR
VIEWER
```

---

# 10. Permissions

Exemples :

```text
support.dashboard.read
support.ticket.read
support.ticket.create
support.ticket.assign
support.ticket.update
support.ticket.close
support.customer.read
support.customer.masked_view
support.payment.read
support.card.read
support.card.block.request
support.refund.request
support.dispute.create
support.incident.read
support.incident.escalate
support.knowledge.read
support.knowledge.manage
support.quality.read
support.report.read
support.export.create
support.audit.read
```

---

# 11. Périmètres

Un utilisateur support peut être limité à :

- pays ;
- langue ;
- canal ;
- produit ;
- segment ;
- niveau ;
- priorité ;
- institution ;
- partenaire ;
- catégorie ;
- équipe ;
- montant ;
- environnement.

---

# 12. Authentification

Méthodes possibles :

- mot de passe fort ;
- MFA ;
- passkey ;
- clé de sécurité ;
- SSO ;
- appareil enregistré ;
- certificat ;
- IP autorisée.

---

# 13. MFA obligatoire

Le MFA doit être obligatoire pour :

- tous les conseillers ;
- les superviseurs ;
- les accès production ;
- les remboursements ;
- les exports ;
- les changements de permission ;
- les escalades fraude ;
- les accès aux données sensibles.

---

# 14. Gestion des sessions

Le système doit gérer :

- durée ;
- inactivité ;
- appareil ;
- IP ;
- pays ;
- risque ;
- réauthentification ;
- révocation ;
- verrouillage ;
- sessions simultanées ;
- accès exceptionnel.

---

# 15. Ticket support

Chaque ticket doit contenir :

- identifiant unique ;
- titre ;
- description ;
- catégorie ;
- sous-catégorie ;
- client ;
- organisation ;
- canal ;
- pays ;
- langue ;
- priorité ;
- statut ;
- équipe ;
- conseiller ;
- produit ;
- transaction éventuelle ;
- pièces jointes ;
- SLA ;
- historique ;
- résolution ;
- satisfaction.

---

# 16. Statuts des tickets

- NEW ;
- OPEN ;
- ASSIGNED ;
- IN_PROGRESS ;
- WAITING_CUSTOMER ;
- WAITING_INTERNAL ;
- WAITING_PARTNER ;
- ESCALATED ;
- RESOLVED ;
- CLOSED ;
- REOPENED ;
- CANCELLED ;
- DUPLICATE.

---

# 17. Priorités

Exemples :

- LOW ;
- NORMAL ;
- HIGH ;
- URGENT ;
- CRITICAL.

La priorité peut dépendre :

- de l’impact ;
- du montant ;
- du nombre d’utilisateurs ;
- du produit ;
- du risque ;
- du délai ;
- du type de client ;
- de l’incident ;
- de la conformité ;
- d’un partenaire.

---

# 18. Catégories de tickets

Exemples :

- création de compte ;
- connexion ;
- KYC ;
- KYB ;
- carte ;
- paiement ;
- transfert ;
- dépôt ;
- retrait ;
- Mobile Money ;
- agent ;
- TPE ;
- DAB ;
- commerce ;
- remboursement ;
- litige ;
- fraude ;
- compte bloqué ;
- application ;
- bourse ;
- frais scolaire ;
- service public ;
- API ;
- sécurité ;
- réclamation ;
- autre.

---

# 19. Sous-catégories

Exemple pour les cartes :

```text
Carte
├── Carte non reçue
├── Carte refusée
├── Carte bloquée
├── Carte perdue
├── Carte volée
├── Paiement inconnu
├── Retrait DAB
├── PIN
├── Sans contact
└── Carte virtuelle
```

---

# 20. Création d’un ticket

Un ticket peut être créé depuis :

- application Client ;
- application Commerce ;
- application Agent ;
- application TPE ;
- portail web ;
- site officiel ;
- e-mail ;
- appel ;
- chat ;
- SMS ;
- formulaire ;
- Jini ;
- administrateur ;
- partenaire ;
- incident automatique.

---

# 21. Détection des doublons

Le système peut détecter :

- même client ;
- même transaction ;
- même problème ;
- même période ;
- même canal ;
- même incident ;
- même référence.

Il doit proposer une fusion sans supprimer l’historique.

---

# 22. Fusion de tickets

La fusion doit conserver :

- tickets d’origine ;
- auteurs ;
- conversations ;
- pièces ;
- dates ;
- SLA ;
- historique ;
- relations ;
- audit.

---

# 23. Files d’attente

Exemples :

- support général ;
- cartes ;
- paiements ;
- transferts ;
- fraude ;
- Cash Network ;
- TPE ;
- DAB ;
- commerçants ;
- partenaires ;
- institutions ;
- développeurs ;
- bourses ;
- sécurité.

---

# 24. Routage automatique

Le routage peut dépendre :

- catégorie ;
- pays ;
- langue ;
- priorité ;
- produit ;
- montant ;
- disponibilité ;
- compétence ;
- niveau ;
- partenaire ;
- incident ;
- horaire.

---

# 25. Affectation

Méthodes :

- manuelle ;
- automatique ;
- round-robin ;
- selon compétence ;
- selon charge ;
- selon langue ;
- selon pays ;
- selon priorité ;
- selon produit.

---

# 26. Vue client 360

La vue client peut afficher, selon permission :

- identité masquée ;
- statut ;
- niveau KYC ;
- pays ;
- langue ;
- compte ;
- cartes masquées ;
- appareils ;
- dernières opérations utiles ;
- tickets ;
- incidents ;
- litiges ;
- restrictions ;
- préférences de contact.

---

# 27. Protection de la vue client

Toute consultation doit être :

- justifiée ;
- liée à un ticket ;
- limitée ;
- journalisée ;
- masquée ;
- soumise au rôle ;
- surveillée.

---

# 28. Vérification de l’identité

Avant certaines actions, le conseiller doit vérifier l’identité par une méthode autorisée.

Exemples :

- informations partielles ;
- notification dans l’application ;
- validation via canal sécurisé ;
- question contextuelle non sensible ;
- vérification d’un appareil reconnu ;
- processus d’identité renforcé.

Le conseiller ne doit jamais demander le PIN complet ou l’OTP complet.

---

# 29. Conversations

Une conversation peut regrouper :

- messages client ;
- réponses conseiller ;
- notes internes ;
- appels ;
- e-mails ;
- pièces jointes ;
- réponses automatiques ;
- actions Jini ;
- notifications.

---

# 30. Notes internes

Les notes internes doivent être :

- invisibles au client ;
- liées à un auteur ;
- horodatées ;
- auditées ;
- interdites aux données inutilement sensibles ;
- soumises à rétention.

---

# 31. Chat

Le chat doit permettre :

- file d’attente ;
- estimation d’attente ;
- transfert ;
- pièces jointes ;
- réponses rapides ;
- historique ;
- traduction ;
- fermeture ;
- satisfaction ;
- escalade.

---

# 32. Appels

Le module d’appel peut gérer :

- appel entrant ;
- appel sortant ;
- identification ;
- enregistrement selon règles ;
- consentement ;
- file ;
- transfert ;
- mise en attente ;
- résumé ;
- classification ;
- ticket automatique ;
- disposition finale.

---

# 33. Enregistrement des appels

L’enregistrement doit dépendre :

- du pays ;
- du consentement ;
- de la politique ;
- du type de demande ;
- de la durée de conservation ;
- du niveau de sensibilité.

Les données de carte ou secrets doivent être masqués ou exclus.

---

# 34. E-mails

Le système doit permettre :

- réception ;
- envoi ;
- modèles ;
- pièces jointes ;
- suivi ;
- threading ;
- anti-spam ;
- détection de phishing ;
- association au ticket ;
- adresse par pays ou produit.

---

# 35. SMS

Les SMS peuvent être utilisés pour :

- accusé de réception ;
- numéro de ticket ;
- rappel ;
- statut ;
- demande de document ;
- confirmation de résolution ;
- alerte.

Les SMS ne doivent pas contenir d’informations sensibles inutiles.

---

# 36. Canaux de messagerie externes

Le portail peut intégrer des canaux autorisés selon les pays et contrats.

Chaque canal doit appliquer :

- consentement ;
- identification ;
- limitation des données ;
- historique ;
- contrôle de sécurité ;
- archivage ;
- révocation.

---

# 37. Pièces jointes

Types possibles :

- image ;
- PDF ;
- reçu ;
- capture d’écran ;
- relevé ;
- document ;
- vidéo courte ;
- fichier technique.

---

# 38. Sécurité des pièces jointes

Les fichiers doivent être :

- antivirusés ;
- chiffrés ;
- limités en taille ;
- limités en type ;
- liés au ticket ;
- soumis à rétention ;
- accessibles selon permission ;
- auditables.

---

# 39. Masquage automatique

Le système doit détecter et masquer :

- numéro complet de carte ;
- CVV ;
- PIN ;
- OTP ;
- mot de passe ;
- clé API ;
- token ;
- secret ;
- numéro de compte sensible ;
- document non nécessaire.

---

# 40. Réponses rapides

Le portail peut proposer :

- macros ;
- modèles ;
- réponses validées ;
- procédures ;
- liens ;
- étapes ;
- messages multilingues.

Les réponses sensibles doivent être versionnées et approuvées.

---

# 41. Base de connaissances

Elle doit contenir :

- articles ;
- procédures ;
- scripts ;
- FAQ ;
- guides ;
- erreurs connues ;
- parcours ;
- documents ;
- solutions ;
- escalades ;
- consignes de sécurité.

---

# 42. Statuts des articles

- DRAFT ;
- REVIEW ;
- APPROVED ;
- PUBLISHED ;
- DEPRECATED ;
- ARCHIVED.

---

# 43. Recherche dans la base de connaissances

La recherche peut utiliser :

- mots-clés ;
- produit ;
- pays ;
- langue ;
- catégorie ;
- erreur ;
- version ;
- rôle ;
- niveau de support.

---

# 44. Jini pour le support

Jini peut aider à :

- résumer un ticket ;
- suggérer une catégorie ;
- proposer une réponse ;
- rechercher une procédure ;
- détecter un doublon ;
- identifier une transaction ;
- préparer une escalade ;
- traduire ;
- générer un résumé d’appel ;
- suggérer les prochaines étapes.

---

# 45. Limites de Jini

Jini ne doit pas :

- modifier un solde ;
- déclencher seul un remboursement ;
- bloquer définitivement un compte ;
- afficher un secret ;
- décider seul d’un litige ;
- fermer un incident critique sans validation ;
- contourner les permissions ;
- inventer une politique.

---

# 46. Réclamations

Une réclamation peut concerner :

- frais ;
- délai ;
- service ;
- comportement d’un agent ;
- paiement ;
- retrait ;
- carte ;
- sécurité ;
- décision ;
- qualité ;
- partenaire ;
- institution.

---

# 47. Dossier de réclamation

Il doit contenir :

- demandeur ;
- motif ;
- service ;
- référence ;
- date ;
- preuves ;
- statut ;
- responsable ;
- réponse ;
- recours ;
- délai ;
- historique.

---

# 48. Statuts de réclamation

- SUBMITTED ;
- RECEIVED ;
- ASSIGNED ;
- UNDER_REVIEW ;
- INFORMATION_REQUIRED ;
- RESPONSE_READY ;
- RESOLVED ;
- REJECTED ;
- ESCALATED ;
- CLOSED.

---

# 49. Litiges

Un litige peut concerner :

- paiement inconnu ;
- paiement en double ;
- retrait non reçu ;
- dépôt non crédité ;
- transfert non reçu ;
- remboursement manquant ;
- commerçant ;
- agent ;
- carte ;
- TPE ;
- DAB ;
- service public.

---

# 50. Création d’un litige

Le conseiller peut :

1. identifier l’opération ;
2. vérifier l’éligibilité ;
3. collecter les preuves ;
4. créer le dossier ;
5. informer le client ;
6. transmettre à l’équipe compétente ;
7. suivre la décision ;
8. notifier le résultat.

---

# 51. Remboursements

Le support peut :

- consulter un remboursement ;
- créer une demande ;
- ajouter une justification ;
- joindre des preuves ;
- suivre le workflow ;
- informer le client.

Le support ne doit pas pouvoir exécuter directement un remboursement critique sans approbation.

---

# 52. Workflow de remboursement

1. demande ;
2. vérification ;
3. contrôle de la transaction ;
4. analyse du risque ;
5. simulation ;
6. approbation ;
7. écriture compensatrice ;
8. notification ;
9. rapprochement ;
10. clôture.

---

# 53. Problèmes de carte

Le portail doit gérer :

- carte perdue ;
- carte volée ;
- carte retenue ;
- carte refusée ;
- paiement inconnu ;
- retrait contesté ;
- PIN bloqué ;
- carte non reçue ;
- carte expirée ;
- carte virtuelle ;
- carte compromise.

---

# 54. Blocage d’une carte

Le conseiller peut, selon permission :

- demander un blocage ;
- déclencher un blocage temporaire ;
- transmettre au service fraude ;
- lancer un remplacement ;
- révoquer un token Wallet ;
- ouvrir un incident.

Les actions sont auditées.

---

# 55. Problèmes Cash Network

Exemples :

- dépôt non crédité ;
- retrait refusé ;
- agent sans liquidité ;
- mauvais montant ;
- reçu manquant ;
- commission contestée ;
- agent fermé ;
- comportement abusif ;
- faux agent ;
- incident de caisse.

---

# 56. Problèmes TPE

Exemples :

- terminal hors ligne ;
- paiement refusé ;
- double paiement ;
- reçu non imprimé ;
- remboursement ;
- certificat expiré ;
- terminal bloqué ;
- mise à jour échouée ;
- matériel défectueux.

---

# 57. Problèmes DAB

Exemples :

- débit sans billets ;
- billets partiels ;
- carte retenue ;
- panne ;
- reçu manquant ;
- coupure incorrecte ;
- dépôt non comptabilisé ;
- DAB indisponible.

---

# 58. Problèmes KYC et KYB

Le support peut :

- expliquer les documents requis ;
- consulter le statut ;
- demander un complément ;
- relancer ;
- transmettre à la conformité ;
- informer du délai.

Le support ne doit pas valider seul un KYC ou KYB sensible sans permission.

---

# 59. Escalades

Types possibles :

- niveau 2 ;
- niveau 3 ;
- finance ;
- conformité ;
- fraude ;
- sécurité ;
- cartes ;
- trésorerie ;
- partenaire ;
- institution ;
- technique ;
- juridique ;
- direction.

---

# 60. Règles d’escalade

Une escalade peut dépendre :

- priorité ;
- montant ;
- délai ;
- type de client ;
- incident ;
- fraude ;
- pays ;
- produit ;
- partenaire ;
- non-respect du SLA ;
- récidive.

---

# 61. Dossier d’escalade

Il doit contenir :

- ticket ;
- raison ;
- équipe source ;
- équipe cible ;
- résumé ;
- preuves ;
- actions déjà effectuées ;
- délai ;
- priorité ;
- responsable ;
- statut.

---

# 62. SLA

Le moteur SLA doit gérer :

- temps de première réponse ;
- temps de prise en charge ;
- temps de résolution ;
- délai partenaire ;
- délai client ;
- pause ;
- reprise ;
- jours ouvrés ;
- horaires ;
- pays ;
- priorité ;
- produit ;
- contrat.

---

# 63. Statuts SLA

- ON_TRACK ;
- AT_RISK ;
- BREACHED ;
- PAUSED ;
- COMPLETED ;
- EXEMPTED.

---

# 64. Calendriers SLA

Chaque pays ou équipe peut avoir :

- horaires ;
- jours ouvrés ;
- jours fériés ;
- astreinte ;
- support 24/7 ;
- support premium ;
- support standard ;
- maintenance.

---

# 65. Alertes SLA

Le système doit alerter :

- conseiller ;
- superviseur ;
- manager ;
- équipe d’escalade ;
- responsable pays ;
- partenaire concerné.

---

# 66. Incidents majeurs

Le support doit pouvoir suivre :

- incident technique ;
- incident financier ;
- incident partenaire ;
- incident carte ;
- incident Mobile Money ;
- incident TPE ;
- incident DAB ;
- incident Cash Network ;
- incident sécurité ;
- incident services publics.

---

# 67. Lien ticket-incident

Les tickets liés à un incident doivent pouvoir être :

- regroupés ;
- mis à jour automatiquement ;
- informés par lot ;
- résolus selon l’incident ;
- analysés ;
- reportés.

---

# 68. Communication d’incident

Le système peut envoyer :

- bannière ;
- notification ;
- SMS ;
- e-mail ;
- message dans le ticket ;
- page de statut ;
- réponse automatique.

---

# 69. Satisfaction client

Après résolution, le client peut évaluer :

- qualité ;
- rapidité ;
- compréhension ;
- résolution ;
- comportement ;
- canal ;
- commentaire.

---

# 70. Indicateurs de satisfaction

Exemples :

- CSAT ;
- taux de réponse ;
- taux de résolution ;
- réouverture ;
- délai ;
- satisfaction par équipe ;
- satisfaction par produit ;
- satisfaction par pays ;
- satisfaction par canal.

---

# 71. Assurance qualité

Le portail doit permettre :

- échantillonnage ;
- revue de ticket ;
- revue d’appel ;
- score qualité ;
- coaching ;
- commentaire ;
- plan d’amélioration ;
- contrôle de conformité ;
- suivi.

---

# 72. Critères qualité

Exemples :

- identification correcte ;
- respect de la procédure ;
- sécurité ;
- clarté ;
- exactitude ;
- empathie ;
- délai ;
- traçabilité ;
- absence de donnée sensible ;
- résolution adaptée.

---

# 73. Supervision des conseillers

Le superviseur peut consulter :

- statut ;
- charge ;
- tickets ;
- appels ;
- chats ;
- SLA ;
- satisfaction ;
- qualité ;
- disponibilité ;
- performance ;
- formations requises.

---

# 74. États de disponibilité

- AVAILABLE ;
- BUSY ;
- ON_CALL ;
- ON_CHAT ;
- AFTER_CALL_WORK ;
- BREAK ;
- TRAINING ;
- OFFLINE.

---

# 75. Planning

Le portail peut gérer :

- horaires ;
- équipes ;
- rotations ;
- pauses ;
- astreintes ;
- congés ;
- capacité ;
- langues ;
- compétences ;
- pays.

---

# 76. Rapports

Rapports possibles :

- tickets ;
- volumes ;
- catégories ;
- canaux ;
- délais ;
- SLA ;
- satisfaction ;
- réclamations ;
- litiges ;
- remboursements ;
- incidents ;
- agents ;
- équipes ;
- pays ;
- produits ;
- qualité ;
- escalades ;
- réouvertures.

---

# 77. Exports

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
- temporaires ;
- audités ;
- soumis aux permissions.

---

# 78. Rapports programmés

Un rapport peut être généré :

- chaque heure ;
- quotidiennement ;
- chaque semaine ;
- chaque mois ;
- après incident ;
- après clôture ;
- après dépassement de SLA.

---

# 79. Notifications internes

Exemples :

- nouveau ticket critique ;
- ticket non assigné ;
- SLA bientôt dépassé ;
- remboursement approuvé ;
- incident majeur ;
- escalade reçue ;
- client VIP ;
- activité suspecte ;
- demande partenaire ;
- contrôle qualité requis.

---

# 80. Notifications au client

Types :

- ticket créé ;
- ticket pris en charge ;
- complément requis ;
- ticket escaladé ;
- incident identifié ;
- remboursement lancé ;
- résolution proposée ;
- ticket fermé ;
- enquête de satisfaction.

---

# 81. Multi-langues

Le portail doit prendre en charge :

- français ;
- bambara ;
- anglais ;
- langues nationales ;
- langues des futurs pays.

Les modèles doivent être traduisibles.

---

# 82. Traduction

Le système peut proposer :

- traduction automatique assistée ;
- traduction validée ;
- glossaire ;
- détection de langue ;
- réponse dans la langue du client ;
- relecture humaine.

---

# 83. Réseau faible

Le portail doit prévoir :

- interface légère ;
- chargement progressif ;
- cache ;
- reprise ;
- pièces compressées ;
- formulaires résilients ;
- sauvegarde de brouillon ;
- synchronisation ;
- mode texte.

---

# 84. Mode dégradé

En cas d’incident, le support peut continuer à :

- créer un ticket ;
- enregistrer un appel ;
- prendre une note ;
- collecter une référence ;
- préparer une réponse ;
- informer le client.

Il ne doit pas confirmer une opération financière sans données fiables.

---

# 85. Intégrations

Le portail peut se connecter à :

- Mansa Client ;
- Mansa Commerce ;
- Mansa Agent ;
- Mansa TPE ;
- Mansa Admin ;
- Hub ;
- site web ;
- banque ;
- Mobile Money ;
- téléphonie ;
- e-mail ;
- SMS ;
- CRM ;
- outil d’incident ;
- outil de fraude ;
- Jini ;
- page de statut.

---

# 86. API

Exemples :

```http
GET    /support/dashboard
GET    /support/tickets
POST   /support/tickets
GET    /support/tickets/{id}
PATCH  /support/tickets/{id}

POST   /support/tickets/{id}/assign
POST   /support/tickets/{id}/escalate
POST   /support/tickets/{id}/resolve
POST   /support/tickets/{id}/close

GET    /support/customers/{id}
GET    /support/conversations
POST   /support/conversations/{id}/messages

POST   /support/refund-requests
POST   /support/disputes
GET    /support/incidents
GET    /support/reports
GET    /support/audit
```

---

# 87. Webhooks

Événements possibles :

```text
support.ticket.created
support.ticket.assigned
support.ticket.updated
support.ticket.escalated
support.ticket.resolved
support.ticket.closed
support.ticket.reopened
support.refund.requested
support.dispute.created
support.sla.at_risk
support.sla.breached
support.incident.linked
support.satisfaction.received
```

---

# 88. Approbations

Peuvent nécessiter une approbation :

- remboursement ;
- geste commercial ;
- blocage définitif ;
- réactivation ;
- suppression logique ;
- export massif ;
- accès exceptionnel ;
- modification de procédure ;
- publication d’une macro ;
- clôture d’un incident sensible.

---

# 89. Double validation

Peut être exigée pour :

- remboursement élevé ;
- réactivation après fraude ;
- déblocage sensible ;
- geste commercial important ;
- export de données ;
- accès à une preuve sensible ;
- modification d’un compte de règlement ;
- clôture d’un litige important.

---

# 90. Séparation des rôles

Le conseiller ayant créé une demande critique ne doit pas être son seul approbateur.

Exemple :

```text
Conseiller crée la demande
→ Superviseur contrôle
→ Finance approuve
→ Backend exécute
```

---

# 91. Sécurité

Mesures principales :

- MFA ;
- RBAC ;
- ABAC ;
- chiffrement ;
- masquage ;
- appareils approuvés ;
- sessions contrôlées ;
- IP autorisées ;
- rate limiting ;
- surveillance ;
- révocation ;
- audit ;
- détection d’anomalie ;
- protection des fichiers.

---

# 92. Alertes de sécurité

Exemples :

- accès à trop de profils ;
- export massif ;
- recherche abusive ;
- consultation sans ticket ;
- tentative d’affichage de secret ;
- téléchargement inhabituel ;
- connexion hors pays ;
- changement de rôle ;
- activité hors horaire ;
- partage de compte suspecté.

---

# 93. Audit

Le journal doit contenir :

- utilisateur ;
- rôle ;
- équipe ;
- ticket ;
- client ;
- ressource ;
- action ;
- ancienne valeur ;
- nouvelle valeur ;
- date ;
- heure ;
- appareil ;
- IP ;
- pays ;
- motif ;
- résultat ;
- approbateur.

---

# 94. Immutabilité des audits

Les audits ne doivent pas être :

- modifiés ;
- supprimés ;
- réécrits ;
- masqués sans trace ;
- désactivés ;
- exportés sans permission.

---

# 95. Modèles principaux

- SupportUser
- SupportRole
- SupportPermission
- SupportTeam
- SupportQueue
- SupportTicket
- SupportTicketCategory
- SupportConversation
- SupportMessage
- SupportCall
- SupportEmail
- SupportAttachment
- SupportMacro
- SupportKnowledgeArticle
- SupportEscalation
- SupportSlaPolicy
- SupportSlaEvent
- SupportComplaint
- SupportDispute
- SupportRefundRequest
- SupportIncidentLink
- SupportSatisfaction
- SupportQualityReview
- SupportSchedule
- SupportNotification
- SupportAudit

---

# 96. Analytics

Événements possibles :

```text
support_login_completed
support_ticket_created
support_ticket_assigned
support_ticket_opened
support_ticket_escalated
support_ticket_resolved
support_ticket_closed
support_chat_started
support_call_completed
support_refund_requested
support_dispute.created
support_sla_warning_created
support_sla_breached
support_quality_review_completed
support_satisfaction_received
support_security_alert_created
```

---

# 97. Données analytics interdites

Ne pas transmettre :

- mot de passe ;
- PIN ;
- OTP ;
- CVV ;
- numéro complet de carte ;
- secret API ;
- clé privée ;
- enregistrement complet sensible ;
- document complet ;
- donnée biométrique ;
- contenu confidentiel ;
- message privé complet sans nécessité.

---

# 98. Tests

- tests d’authentification ;
- tests MFA ;
- tests de rôles ;
- tests de permissions ;
- tests de périmètres ;
- tests de tickets ;
- tests de files ;
- tests de routage ;
- tests d’affectation ;
- tests de chat ;
- tests d’appels ;
- tests d’e-mails ;
- tests SMS ;
- tests de pièces jointes ;
- tests antivirus ;
- tests de masquage ;
- tests client 360 ;
- tests de vérification ;
- tests de macros ;
- tests base de connaissances ;
- tests Jini ;
- tests réclamations ;
- tests litiges ;
- tests remboursements ;
- tests cartes ;
- tests Cash Network ;
- tests TPE ;
- tests DAB ;
- tests KYC ;
- tests escalades ;
- tests SLA ;
- tests incidents ;
- tests satisfaction ;
- tests qualité ;
- tests rapports ;
- tests exports ;
- tests multi-pays ;
- tests multi-langues ;
- tests réseau faible ;
- tests sécurité ;
- tests audit ;
- tests performance ;
- tests accessibilité.

---

# 99. Règles métier

1. Chaque conseiller possède un compte nominatif.
2. Les comptes partagés sont interdits.
3. Le support ne voit que les données nécessaires.
4. Toute consultation sensible est journalisée.
5. Les secrets client ne sont jamais affichés.
6. Le support ne modifie jamais directement un solde.
7. Les remboursements utilisent un workflow.
8. Les tickets possèdent une référence unique.
9. Les tickets peuvent être reliés à une transaction.
10. Les conversations sont historisées.
11. Les notes internes restent invisibles au client.
12. Les pièces jointes sont contrôlées.
13. Les données sensibles sont masquées.
14. Les files sont configurables.
15. Le routage peut être automatisé.
16. Les SLA sont configurables.
17. Les incidents peuvent regrouper plusieurs tickets.
18. Les réponses sensibles sont versionnées.
19. Jini respecte les permissions.
20. Jini ne décide pas seul d’une action financière.
21. Les clients peuvent être informés par plusieurs canaux.
22. Les exports sont audités.
23. Le demandeur ne valide pas seul une action critique.
24. Les audits sont immuables.
25. Les actions critiques peuvent exiger une double validation.

---

# 100. Critères d’acceptation

Le Portail Support et Centre de relation client Mansa est validé lorsque :

- les conseillers peuvent se connecter avec MFA ;
- les rôles et périmètres sont appliqués ;
- les tickets peuvent être créés depuis tous les canaux ;
- les files sont administrables ;
- le routage automatique fonctionne ;
- les tickets peuvent être assignés ;
- les conversations sont centralisées ;
- la vue client est masquée et limitée ;
- les consultations sont auditées ;
- les appels peuvent être rattachés à un ticket ;
- les chats sont pris en charge ;
- les e-mails sont centralisés ;
- les SMS sont intégrés ;
- les pièces jointes sont sécurisées ;
- les données sensibles sont masquées ;
- la base de connaissances est disponible ;
- les réponses rapides sont versionnées ;
- Jini peut assister les conseillers ;
- les réclamations sont suivies ;
- les litiges sont créés ;
- les remboursements utilisent un workflow ;
- les problèmes de cartes sont pris en charge ;
- Cash Network est pris en charge ;
- les TPE et DAB sont pris en charge ;
- les escalades sont centralisées ;
- les SLA sont calculés ;
- les incidents peuvent regrouper les tickets ;
- les notifications clients fonctionnent ;
- la satisfaction est mesurée ;
- les contrôles qualité sont disponibles ;
- les rapports sont exportables ;
- le réseau faible est pris en charge ;
- les audits sont immuables ;
- les actions sensibles sont protégées ;
- les tests couvrent les parcours essentiels.
