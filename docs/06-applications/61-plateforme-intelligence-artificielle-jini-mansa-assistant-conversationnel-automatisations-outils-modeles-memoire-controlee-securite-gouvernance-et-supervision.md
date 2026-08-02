# 61 — Plateforme d’intelligence artificielle Jini Mansa : assistant conversationnel, automatisations, outils, modèles, mémoire contrôlée, sécurité, gouvernance et supervision

## 1. Objet du document

Ce document définit l’architecture officielle de la **Plateforme d’intelligence artificielle Jini Mansa**.

Jini constitue la couche d’assistance intelligente commune à l’ensemble de l’écosystème Mansa.

Jini peut être intégré dans :

- l’application Client ;
- l’application Commerce ;
- l’application Agent ;
- l’application TPE ;
- l’application Admin Lite ;
- le Hub et Annuaire ;
- le site officiel ;
- le portail Admin Web ;
- le portail Développeurs ;
- le portail Institutions ;
- le portail Banques ;
- le portail Entreprises ;
- le portail Écoles et Universités ;
- le portail Support ;
- la console Sécurité et Fraude ;
- la console Finance ;
- la plateforme Data ;
- les interfaces DAB ;
- les outils internes ;
- les futurs services Mansa.

La plateforme doit permettre à Jini de :

- répondre aux questions ;
- expliquer les services ;
- guider les utilisateurs ;
- rechercher des informations autorisées ;
- résumer des données ;
- assister les équipes ;
- suggérer des actions ;
- préparer des opérations ;
- remplir des formulaires ;
- classer des demandes ;
- détecter des anomalies ;
- traduire ;
- générer des rapports ;
- créer des brouillons ;
- automatiser certaines tâches ;
- déclencher des outils autorisés ;
- superviser des workflows ;
- fonctionner dans plusieurs langues ;
- fonctionner sur réseau faible ;
- respecter les rôles et permissions ;
- rester contrôlé par l’administration.

L’objectif est de créer une intelligence artificielle :

- utile ;
- sécurisée ;
- traçable ;
- explicable ;
- multilingue ;
- adaptée à l’Afrique ;
- adaptée aux utilisateurs peu familiarisés avec le numérique ;
- limitée par des permissions ;
- incapable de modifier directement les systèmes financiers sans workflow ;
- capable d’évoluer vers plusieurs pays ;
- indépendante d’un seul fournisseur d’IA.

---

# 2. Principes fondamentaux

## 2.1 Jini ne doit jamais remplacer les systèmes officiels

Les sources officielles restent :

- le ledger pour les soldes et écritures ;
- le backend pour les transactions ;
- le KYC et le KYB pour les identités ;
- le système cartes pour les cartes ;
- le portail Finance pour les données comptables ;
- le moteur de risque pour les décisions de risque ;
- les portails métier pour leurs données ;
- les règles administratives pour les paramètres.

Jini peut consulter, expliquer et préparer.

Jini ne doit pas inventer ou remplacer une donnée officielle.

---

## 2.2 Jini ne doit pas modifier directement un solde

Jini ne doit jamais :

- créditer un compte ;
- débiter un compte ;
- créer une écriture ledger directe ;
- modifier une transaction ;
- modifier une commission ;
- modifier un règlement ;
- supprimer une dette ;
- modifier un compte de cantonnement.

Toute action financière doit passer par :

- un outil autorisé ;
- une validation utilisateur ;
- un workflow ;
- une règle ;
- une approbation ;
- une API officielle ;
- un audit.

---

## 2.3 Jini doit respecter les permissions de l’utilisateur

Jini ne doit accéder qu’aux informations que l’utilisateur pourrait consulter lui-même.

Exemple :

```text
Utilisateur Client
→ accès à ses propres données

Agent Mansa
→ accès aux données nécessaires à son activité

Conseiller support
→ accès aux données autorisées par son ticket

Administrateur
→ accès selon son rôle et son périmètre
```

---

## 2.4 Jini doit distinguer information, suggestion et action

Chaque réponse doit clairement différencier :

- une information ;
- une explication ;
- une recommandation ;
- une simulation ;
- une action préparée ;
- une action exécutée ;
- une action nécessitant validation.

---

## 2.5 Jini doit demander une validation avant une action sensible

Exemples :

- envoyer de l’argent ;
- bloquer une carte ;
- créer un remboursement ;
- modifier une limite ;
- envoyer un rapport ;
- lancer une campagne ;
- créer un utilisateur ;
- suspendre un agent ;
- programmer un règlement ;
- exporter des données.

---

## 2.6 Jini doit être indépendant du fournisseur

La plateforme doit permettre d’utiliser ou remplacer :

- un modèle interne ;
- un modèle externe ;
- un fournisseur cloud ;
- un modèle local ;
- un modèle spécialisé ;
- un moteur de traduction ;
- un moteur vocal ;
- un moteur de vision ;
- un moteur de recherche.

Aucun fournisseur ne doit être codé en dur.

---

# 3. Utilisateurs de Jini

Jini peut être utilisé par :

- client particulier ;
- commerçant ;
- agent Cash Network ;
- employé ;
- administrateur d’entreprise ;
- étudiant ;
- parent ;
- établissement scolaire ;
- agent public ;
- institution ;
- banque ;
- partenaire ;
- développeur ;
- conseiller support ;
- analyste fraude ;
- analyste Finance ;
- administrateur Mansa ;
- auditeur ;
- équipe technique ;
- direction.

---

# 4. Modes de Jini

Jini peut fonctionner en plusieurs modes :

- assistant Client ;
- assistant Commerce ;
- assistant Agent ;
- assistant TPE ;
- assistant Entreprise ;
- assistant Éducation ;
- assistant Institution ;
- assistant Développeur ;
- assistant Support ;
- assistant Sécurité ;
- assistant Finance ;
- assistant Data ;
- assistant Administrateur ;
- assistant vocal ;
- assistant hors ligne limité.

---

# 5. Rôles internes

Exemples :

```text
AI_PLATFORM_ADMIN
AI_PRODUCT_MANAGER
AI_ENGINEER
PROMPT_ENGINEER
AI_SAFETY_MANAGER
AI_EVALUATION_ANALYST
AI_DATA_STEWARD
AI_MODEL_OPERATOR
AI_SECURITY_ANALYST
AI_AUDITOR
AI_SUPPORT_OPERATOR
VIEWER
```

---

# 6. Permissions

Exemples :

```text
ai.dashboard.read
ai.assistant.read
ai.assistant.manage
ai.model.read
ai.model.manage
ai.provider.read
ai.provider.manage
ai.prompt.read
ai.prompt.manage
ai.tool.read
ai.tool.manage
ai.workflow.read
ai.workflow.manage
ai.evaluation.read
ai.evaluation.manage
ai.memory.read
ai.memory.manage
ai.guardrail.read
ai.guardrail.manage
ai.report.read
ai.audit.read
```

---

# 7. Périmètres d’accès

Un utilisateur interne peut être limité à :

- un pays ;
- une application ;
- un assistant ;
- un domaine ;
- un modèle ;
- un fournisseur ;
- un environnement ;
- un outil ;
- une langue ;
- un type de données ;
- une organisation ;
- une équipe ;
- un niveau de sensibilité.

---

# 8. Authentification

Méthodes possibles :

- mot de passe fort ;
- MFA ;
- passkey ;
- clé de sécurité ;
- SSO ;
- certificat ;
- appareil géré ;
- IP autorisée ;
- réseau privé ;
- accès bastion.

---

# 9. MFA obligatoire

Le MFA doit être obligatoire pour :

- tous les administrateurs IA ;
- les accès Production ;
- la modification d’un prompt système ;
- l’activation d’un outil ;
- le changement de fournisseur ;
- l’export de conversations ;
- l’accès aux évaluations sensibles ;
- la modification des garde-fous ;
- le déploiement d’un modèle ;
- l’accès aux données de mémoire.

---

# 10. Architecture du projet

Structure recommandée :

```text
ai-platform/
├── assistants/
├── conversations/
├── orchestration/
├── prompts/
├── models/
├── providers/
├── routing/
├── tools/
├── agents/
├── workflows/
├── knowledge/
├── retrieval/
├── embeddings/
├── memory/
├── context/
├── safety/
├── guardrails/
├── moderation/
├── permissions/
├── approvals/
├── voice/
├── vision/
├── translation/
├── evaluations/
├── monitoring/
├── analytics/
├── costs/
├── audit/
├── security/
└── administration/
```

---

# 11. Composants principaux

La plateforme doit comporter :

- gestion des assistants ;
- gestion des modèles ;
- gestion des fournisseurs ;
- moteur de routage ;
- moteur de prompts ;
- moteur d’outils ;
- moteur de workflows ;
- RAG ;
- base de connaissances ;
- mémoire contrôlée ;
- sécurité ;
- garde-fous ;
- modération ;
- évaluation ;
- observabilité ;
- analytics ;
- coûts ;
- audit.

---

# 12. Assistants spécialisés

Exemples :

- Jini Client ;
- Jini Business ;
- Jini Agent ;
- Jini TPE ;
- Jini Campus ;
- Jini Public ;
- Jini Developer ;
- Jini Support ;
- Jini Fraud ;
- Jini Finance ;
- Jini Data ;
- Jini Admin.

Chaque assistant doit posséder :

- un rôle ;
- un périmètre ;
- des permissions ;
- des outils ;
- des sources ;
- des règles ;
- des langues ;
- un ton ;
- des limites ;
- un propriétaire.

---

# 13. Fiche d’un assistant

Elle doit contenir :

- code ;
- nom ;
- description ;
- application ;
- domaine ;
- utilisateurs ;
- pays ;
- langues ;
- modèle principal ;
- modèle de secours ;
- outils ;
- sources ;
- prompt système ;
- garde-fous ;
- version ;
- statut ;
- propriétaire ;
- environnement.

---

# 14. Statuts d’un assistant

- DRAFT ;
- TESTING ;
- REVIEW ;
- APPROVED ;
- SHADOW ;
- ACTIVE ;
- DEGRADED ;
- SUSPENDED ;
- RETIRED ;
- ARCHIVED.

---

# 15. Conversation

Chaque conversation doit contenir :

- identifiant ;
- assistant ;
- utilisateur ;
- organisation éventuelle ;
- application ;
- langue ;
- pays ;
- canal ;
- début ;
- dernière activité ;
- messages ;
- outils appelés ;
- sources consultées ;
- actions préparées ;
- statut ;
- niveau de sensibilité ;
- consentement ;
- rétention.

---

# 16. Canaux conversationnels

Jini peut être accessible par :

- chat mobile ;
- chat web ;
- voix ;
- TPE ;
- DAB ;
- messagerie interne ;
- portail support ;
- API ;
- widget public ;
- interface administrateur ;
- canal USSD limité ;
- téléphone automatisé.

---

# 17. Types de messages

- message utilisateur ;
- message assistant ;
- message système ;
- résultat d’outil ;
- source ;
- avertissement ;
- confirmation ;
- erreur ;
- action ;
- notification ;
- message de sécurité.

---

# 18. Contexte conversationnel

Le contexte peut inclure :

- langue ;
- application ;
- rôle ;
- pays ;
- organisation ;
- page actuelle ;
- transaction sélectionnée ;
- permissions ;
- préférences ;
- historique autorisé ;
- statut réseau ;
- environnement.

---

# 19. Limitation du contexte

Jini ne doit recevoir que les informations nécessaires.

Il faut éviter d’envoyer systématiquement :

- tout l’historique du compte ;
- toutes les transactions ;
- tous les documents ;
- les secrets ;
- les données non pertinentes ;
- les données d’autres utilisateurs ;
- les journaux complets.

---

# 20. Prompts système

Chaque assistant doit posséder un prompt système versionné.

Le prompt doit définir :

- identité ;
- rôle ;
- objectif ;
- ton ;
- limites ;
- permissions ;
- outils ;
- interdictions ;
- comportement en cas d’incertitude ;
- règles de sécurité ;
- règles d’escalade ;
- langues.

---

# 21. Versionnement des prompts

Chaque modification doit conserver :

- ancienne version ;
- nouvelle version ;
- auteur ;
- date ;
- motif ;
- assistant ;
- environnement ;
- résultats de test ;
- approbateur ;
- date d’effet.

---

# 22. Statuts d’un prompt

- DRAFT ;
- TESTING ;
- REVIEW ;
- APPROVED ;
- SCHEDULED ;
- ACTIVE ;
- SUSPENDED ;
- REPLACED ;
- ARCHIVED.

---

# 23. Variables de prompt

Exemples :

```text
{{user_role}}
{{country}}
{{language}}
{{application}}
{{permissions}}
{{current_page}}
{{selected_transaction}}
{{organization}}
{{environment}}
```

Les variables doivent être filtrées et validées.

---

# 24. Fournisseurs de modèles

Chaque fournisseur doit posséder :

- nom ;
- modèles ;
- régions ;
- langues ;
- capacités ;
- coût ;
- latence ;
- disponibilité ;
- limites ;
- SLA ;
- sécurité ;
- conformité ;
- statut ;
- contrat ;
- environnement.

---

# 25. Types de modèles

La plateforme peut gérer :

- modèle conversationnel ;
- modèle de raisonnement ;
- modèle léger ;
- modèle de classification ;
- modèle d’embedding ;
- modèle de traduction ;
- modèle vocal ;
- modèle de vision ;
- modèle de résumé ;
- modèle de détection d’anomalie ;
- modèle local ;
- modèle spécialisé Finance.

---

# 26. Statuts d’un modèle

- REGISTERED ;
- TESTING ;
- APPROVED ;
- SHADOW ;
- ACTIVE ;
- DEGRADED ;
- SUSPENDED ;
- RETIRED ;
- BLOCKED ;
- ARCHIVED.

---

# 27. Routage des modèles

Le choix du modèle peut dépendre :

- application ;
- tâche ;
- langue ;
- pays ;
- coût ;
- latence ;
- sensibilité ;
- disponibilité ;
- longueur ;
- niveau de raisonnement ;
- canal ;
- environnement ;
- consentement.

---

# 28. Exemple de routage

```text
Question simple
→ modèle léger

Analyse complexe autorisée
→ modèle avancé

Donnée sensible
→ modèle interne ou région autorisée

Traduction
→ moteur spécialisé

Panne fournisseur principal
→ modèle de secours
```

---

# 29. Fallback des modèles

Le système doit gérer :

- modèle principal ;
- modèle secondaire ;
- fournisseur secondaire ;
- modèle local ;
- réponse limitée ;
- transfert vers humain ;
- reprise ;
- mode dégradé.

---

# 30. Outils Jini

Jini peut utiliser des outils autorisés pour :

- consulter un solde ;
- rechercher une transaction ;
- consulter une carte ;
- consulter un ticket ;
- vérifier un statut KYC ;
- rechercher un agent ;
- rechercher un commerçant ;
- générer un reçu ;
- préparer un transfert ;
- préparer un paiement ;
- créer un brouillon ;
- générer un rapport ;
- rechercher une procédure ;
- programmer un rappel ;
- traduire un document.

---

# 31. Fiche d’un outil

Chaque outil doit contenir :

- code ;
- nom ;
- description ;
- domaine ;
- API ;
- paramètres ;
- réponses ;
- permissions ;
- pays ;
- applications ;
- niveau de risque ;
- validation requise ;
- statut ;
- version ;
- propriétaire.

---

# 32. Statuts d’un outil

- DRAFT ;
- TESTING ;
- APPROVED ;
- ACTIVE ;
- RESTRICTED ;
- SUSPENDED ;
- DEPRECATED ;
- RETIRED.

---

# 33. Outils en lecture seule

Exemples :

- consulter un solde ;
- consulter une transaction ;
- consulter un statut ;
- rechercher un document ;
- afficher un règlement ;
- afficher une commission ;
- consulter un incident ;
- consulter une règle.

Ces outils restent soumis aux permissions.

---

# 34. Outils avec action

Exemples :

- bloquer temporairement une carte ;
- préparer un transfert ;
- créer un ticket ;
- demander un remboursement ;
- programmer un rapport ;
- créer une campagne brouillon ;
- demander une liquidité ;
- suspendre une session ;
- créer une alerte.

---

# 35. Validation utilisateur

Avant une action sensible, Jini doit afficher :

- action ;
- montant éventuel ;
- devise ;
- bénéficiaire ;
- frais ;
- conséquence ;
- durée ;
- statut ;
- bouton de confirmation ;
- possibilité d’annuler.

---

# 36. Validation renforcée

Peut être exigée :

- PIN ;
- biométrie ;
- MFA ;
- passkey ;
- OTP ;
- approbation administrateur ;
- double validation ;
- signature ;
- confirmation sur appareil reconnu.

---

# 37. Outils interdits à Jini

Jini ne doit pas disposer d’un outil permettant directement de :

- modifier un solde ;
- supprimer une écriture ;
- afficher un PIN ;
- afficher un CVV ;
- afficher un mot de passe ;
- récupérer une clé privée ;
- supprimer un audit ;
- contourner un KYC ;
- désactiver une règle de sécurité ;
- créer un administrateur sans workflow.

---

# 38. Workflows Jini

Un workflow peut combiner plusieurs étapes.

Exemple :

```text
Demande de remboursement
→ rechercher la transaction
→ vérifier l’éligibilité
→ collecter le motif
→ créer la demande
→ demander validation
→ transmettre au service Finance
→ informer le client
```

---

# 39. Types de workflows

- support ;
- carte ;
- paiement ;
- transfert ;
- remboursement ;
- agent ;
- commerce ;
- entreprise ;
- scolaire ;
- institution ;
- sécurité ;
- fraude ;
- Finance ;
- Data ;
- administration.

---

# 40. Statuts d’un workflow

- DRAFT ;
- TESTING ;
- APPROVED ;
- ACTIVE ;
- PAUSED ;
- DEGRADED ;
- SUSPENDED ;
- RETIRED.

---

# 41. Étapes d’un workflow

Une étape peut être :

- question ;
- collecte d’information ;
- recherche ;
- vérification ;
- calcul ;
- appel d’outil ;
- validation ;
- approbation ;
- attente ;
- notification ;
- escalade ;
- clôture.

---

# 42. Reprise de workflow

Le système doit permettre :

- sauvegarde ;
- reprise ;
- expiration ;
- annulation ;
- changement de canal ;
- transfert à un humain ;
- correction d’une étape ;
- reprise après panne.

---

# 43. Base de connaissances

Jini peut consulter :

- FAQ ;
- procédures ;
- contrats ;
- documents publics ;
- politiques ;
- guides ;
- articles support ;
- documentation API ;
- documentation produit ;
- règles administratives ;
- contenus scolaires ;
- contenus institutionnels.

---

# 44. Sources de connaissances

Chaque source doit posséder :

- propriétaire ;
- domaine ;
- pays ;
- langue ;
- version ;
- statut ;
- date ;
- niveau de sensibilité ;
- permissions ;
- durée de conservation ;
- indexation ;
- historique.

---

# 45. Statuts d’une source

- DRAFT ;
- REVIEW ;
- APPROVED ;
- INDEXED ;
- ACTIVE ;
- STALE ;
- DEPRECATED ;
- ARCHIVED ;
- BLOCKED.

---

# 46. RAG

Le système de recherche augmentée doit :

- identifier la demande ;
- appliquer les permissions ;
- rechercher les sources ;
- classer les résultats ;
- filtrer les données ;
- fournir le contexte ;
- citer les sources internes ;
- limiter le volume ;
- contrôler la fraîcheur ;
- refuser les sources interdites.

---

# 47. Citation des sources

Lorsque Jini utilise une source, il doit pouvoir indiquer :

- document ;
- section ;
- version ;
- date ;
- propriétaire ;
- lien autorisé ;
- niveau de confiance.

---

# 48. Fraîcheur des connaissances

Le système doit détecter :

- document expiré ;
- politique remplacée ;
- procédure obsolète ;
- article non révisé ;
- version ancienne ;
- contradiction ;
- source suspendue.

---

# 49. Contradictions entre sources

En cas de contradiction, Jini doit :

- ne pas inventer ;
- indiquer l’incertitude ;
- privilégier la source officielle ;
- vérifier la version ;
- proposer une escalade ;
- signaler le problème au propriétaire.

---

# 50. Mémoire de conversation

La mémoire peut contenir :

- préférence de langue ;
- préférence de canal ;
- contexte de la conversation ;
- tâches en cours ;
- éléments explicitement autorisés ;
- dernière étape d’un workflow.

---

# 51. Mémoire utilisateur

La mémoire persistante doit être limitée.

Elle peut contenir uniquement des éléments autorisés comme :

- langue préférée ;
- type d’affichage ;
- préférence de communication ;
- objectifs configurés ;
- raccourcis ;
- habitudes non sensibles autorisées.

---

# 52. Données interdites en mémoire

Ne pas conserver dans la mémoire Jini :

- PIN ;
- OTP ;
- CVV ;
- mot de passe ;
- numéro complet de carte ;
- clé privée ;
- secret API ;
- document complet ;
- biométrie ;
- conversation sensible inutile ;
- donnée d’un autre utilisateur ;
- preuve confidentielle.

---

# 53. Contrôle de la mémoire

L’utilisateur doit pouvoir :

- voir les préférences conservées ;
- modifier ;
- supprimer ;
- désactiver la mémoire ;
- retirer un consentement ;
- demander une explication.

---

# 54. Expiration de la mémoire

Chaque mémoire doit posséder :

- date de création ;
- date de mise à jour ;
- finalité ;
- durée ;
- source ;
- consentement ;
- date d’expiration ;
- statut.

---

# 55. Jini vocal

Le mode vocal doit gérer :

- reconnaissance vocale ;
- synthèse vocale ;
- interruption ;
- langue ;
- bruit ;
- confirmation ;
- confidentialité ;
- transcription ;
- suppression ;
- consentement.

---

# 56. Langues vocales

Le système doit être préparé pour :

- français ;
- bambara ;
- anglais ;
- arabe ;
- langues nationales ;
- variantes locales.

La qualité de chaque langue doit être évaluée avant activation.

---

# 57. Confidentialité vocale

Jini vocal doit éviter de prononcer à haute voix :

- solde complet sans autorisation ;
- numéro de carte ;
- PIN ;
- OTP ;
- données d’identité sensibles ;
- détails médicaux ;
- données confidentielles ;
- informations d’un tiers.

---

# 58. Jini Vision

La vision peut permettre :

- lecture d’un reçu ;
- analyse d’une facture ;
- détection d’un document ;
- aide au scan KYC ;
- lecture d’un code ;
- analyse d’un terminal ;
- assistance technique ;
- extraction structurée.

---

# 59. Limites de Jini Vision

Jini Vision ne doit pas :

- valider seul un KYC sensible ;
- déclarer seul un document faux ;
- identifier une personne sans cadre ;
- conserver inutilement une image ;
- afficher des données sensibles ;
- prendre seul une décision réglementaire.

---

# 60. Traduction

Jini peut traduire :

- messages ;
- articles ;
- procédures ;
- tickets ;
- réponses ;
- documents autorisés ;
- contenus d’aide ;
- conversations.

---

# 61. Validation des traductions

Les traductions sensibles doivent pouvoir être :

- relues ;
- approuvées ;
- versionnées ;
- corrigées ;
- liées au texte source ;
- réservées à certaines langues ;
- limitées par pays.

---

# 62. Jini Client

Jini Client peut aider à :

- comprendre le solde ;
- rechercher une opération ;
- expliquer les frais ;
- guider un transfert ;
- aider à bloquer une carte ;
- trouver un agent ;
- trouver un DAB ;
- comprendre un refus ;
- créer un ticket ;
- gérer un budget ;
- expliquer un abonnement.

---

# 63. Jini Commerce

Jini Commerce peut aider à :

- consulter les ventes ;
- rechercher un paiement ;
- générer une facture ;
- comprendre un règlement ;
- gérer les produits ;
- analyser les performances ;
- traiter un remboursement ;
- préparer une campagne ;
- résoudre un problème TPE ;
- consulter les commissions.

---

# 64. Jini Agent

Jini Agent peut aider à :

- consulter le float ;
- expliquer un dépôt ;
- expliquer un retrait ;
- signaler une liquidité faible ;
- rechercher une opération ;
- calculer une commission ;
- ouvrir ou fermer une caisse ;
- signaler un incident ;
- trouver un réapprovisionnement ;
- expliquer une restriction.

---

# 65. Jini TPE

Jini TPE peut aider à :

- lancer un paiement ;
- expliquer un refus ;
- rechercher une transaction ;
- imprimer un reçu ;
- effectuer une clôture ;
- demander une maintenance ;
- vérifier la connexion ;
- préparer un remboursement ;
- guider un commerçant.

---

# 66. Jini Entreprise

Jini Entreprise peut aider à :

- préparer une paie ;
- analyser les dépenses ;
- rechercher un employé ;
- préparer une carte professionnelle ;
- expliquer un budget ;
- générer un rapport ;
- contrôler une note de frais ;
- préparer un paiement fournisseur.

---

# 67. Jini Éducation

Jini Éducation peut aider à :

- consulter une facture ;
- expliquer une bourse ;
- suivre une inscription ;
- trouver un paiement ;
- comprendre un échéancier ;
- générer une attestation autorisée ;
- consulter une carte étudiante ;
- guider un établissement.

---

# 68. Jini Institution

Jini Institution peut aider à :

- rechercher une référence ;
- consulter un paiement ;
- générer un rapport ;
- suivre une aide ;
- suivre une bourse ;
- expliquer une procédure ;
- préparer une campagne d’information ;
- identifier un incident.

---

# 69. Jini Développeur

Jini Développeur peut aider à :

- rechercher dans la documentation ;
- expliquer une API ;
- générer un exemple ;
- analyser une erreur ;
- vérifier un webhook ;
- expliquer un statut ;
- guider une intégration ;
- préparer une requête de test.

Il ne doit jamais exposer un secret réel.

---

# 70. Jini Support

Jini Support peut :

- résumer un ticket ;
- proposer une catégorie ;
- rechercher une procédure ;
- préparer une réponse ;
- traduire ;
- détecter un doublon ;
- préparer une escalade ;
- résumer un appel ;
- suggérer la prochaine étape.

---

# 71. Jini Sécurité et Fraude

Jini peut :

- résumer une alerte ;
- relier des événements ;
- suggérer une priorité ;
- rechercher un playbook ;
- préparer un dossier ;
- expliquer une règle ;
- identifier des incohérences ;
- générer une chronologie.

Il ne doit pas confirmer seul une fraude.

---

# 72. Jini Finance

Jini Finance peut :

- expliquer une écriture ;
- rechercher un écart ;
- résumer un rapprochement ;
- préparer un rapport ;
- analyser une tendance ;
- expliquer une commission ;
- préparer une demande d’ajustement ;
- vérifier une checklist.

Il ne doit pas comptabiliser seul une écriture.

---

# 73. Jini Data

Jini Data peut :

- rechercher un KPI ;
- expliquer une définition ;
- créer une requête brouillon ;
- résumer un tableau de bord ;
- détecter une anomalie ;
- préparer un rapport ;
- expliquer un pipeline ;
- rechercher le lineage.

---

# 74. Jini Admin

Jini Admin peut :

- rechercher une configuration ;
- expliquer un rôle ;
- préparer une modification ;
- résumer un incident ;
- générer une checklist ;
- rechercher un audit ;
- préparer une campagne ;
- guider un administrateur.

Toute action critique reste soumise à validation.

---

# 75. Garde-fous

Les garde-fous doivent couvrir :

- données sensibles ;
- permissions ;
- actions financières ;
- fraude ;
- conformité ;
- sécurité ;
- mineurs ;
- harcèlement ;
- abus ;
- contenu illégal ;
- contournement ;
- fuite de secret ;
- injection de prompt ;
- détournement d’outil.

---

# 76. Prompt injection

Le système doit détecter :

- instruction dans un document ;
- tentative de modifier le rôle ;
- demande d’ignorer les règles ;
- demande de révéler un prompt ;
- tentative d’obtenir un secret ;
- demande d’utiliser un outil interdit ;
- contenu externe malveillant.

---

# 77. Protection contre l’injection

Mesures possibles :

- séparation des instructions ;
- filtrage des documents ;
- validation des outils ;
- limitation des permissions ;
- sortie structurée ;
- allowlist ;
- vérification du contexte ;
- confirmation humaine ;
- journalisation ;
- blocage.

---

# 78. Modération

La modération doit pouvoir analyser :

- entrée utilisateur ;
- sortie du modèle ;
- document ;
- image ;
- audio ;
- appel d’outil ;
- réponse d’outil ;
- fichier.

---

# 79. Réponses incertaines

Lorsque Jini n’est pas certain, il doit :

- le signaler ;
- demander une précision ;
- rechercher une source ;
- proposer une procédure ;
- transférer vers un humain ;
- éviter d’inventer ;
- conserver la référence.

---

# 80. Hallucinations

Le système doit réduire les hallucinations grâce à :

- sources officielles ;
- RAG ;
- outils ;
- validation structurée ;
- contraintes ;
- modèles spécialisés ;
- évaluations ;
- seuil de confiance ;
- refus contrôlé ;
- supervision humaine.

---

# 81. Explicabilité

Pour certaines réponses, Jini doit pouvoir indiquer :

- données utilisées ;
- source ;
- règle ;
- outil ;
- modèle ;
- niveau de confiance ;
- limite ;
- raison de l’escalade.

---

# 82. Transfert vers un humain

Jini doit proposer un transfert humain lorsque :

- il ne comprend pas ;
- une action est interdite ;
- une décision réglementaire est requise ;
- une fraude est suspectée ;
- une urgence existe ;
- un client conteste ;
- une donnée est contradictoire ;
- un outil échoue ;
- le niveau de confiance est insuffisant.

---

# 83. Dossier de transfert

Il doit contenir :

- conversation ;
- résumé ;
- utilisateur ;
- sujet ;
- priorité ;
- langue ;
- actions déjà effectuées ;
- outils utilisés ;
- références ;
- pièces ;
- motif ;
- équipe cible.

---

# 84. Évaluations

La plateforme doit évaluer :

- exactitude ;
- pertinence ;
- sécurité ;
- respect des permissions ;
- qualité des sources ;
- utilité ;
- clarté ;
- ton ;
- latence ;
- coût ;
- taux de résolution ;
- taux d’escalade.

---

# 85. Types d’évaluation

- automatique ;
- humaine ;
- comparative ;
- hors ligne ;
- en ligne ;
- test rouge ;
- test de sécurité ;
- test multilingue ;
- test métier ;
- test de biais ;
- test de performance.

---

# 86. Jeux d’évaluation

Chaque jeu doit contenir :

- domaine ;
- cas ;
- entrée ;
- réponse attendue ;
- critères ;
- langue ;
- pays ;
- niveau de risque ;
- version ;
- propriétaire ;
- date.

---

# 87. Tests adversariaux

Ils doivent couvrir :

- injection ;
- contournement ;
- extraction de secrets ;
- accès à un autre compte ;
- faux rôle ;
- outil interdit ;
- demande de modification de solde ;
- fraude ;
- document malveillant ;
- contenu trompeur ;
- surcharge de contexte.

---

# 88. Évaluation des langues

Chaque langue doit être évaluée sur :

- compréhension ;
- précision ;
- ton ;
- grammaire ;
- vocabulaire financier ;
- vocabulaire local ;
- ambiguïtés ;
- sécurité ;
- qualité vocale ;
- traduction.

---

# 89. Déploiement d’un modèle

Étapes :

1. enregistrement ;
2. tests ;
3. évaluation ;
4. revue sécurité ;
5. revue conformité ;
6. mode Shadow ;
7. déploiement progressif ;
8. monitoring ;
9. généralisation ;
10. retrait éventuel.

---

# 90. Déploiement progressif

Un modèle peut être activé pour :

- équipe interne ;
- pays pilote ;
- petit pourcentage ;
- type d’utilisateur ;
- application ;
- langue ;
- domaine ;
- environnement ;
- feature flag.

---

# 91. Rollback

Le système doit permettre :

- retour au modèle précédent ;
- désactivation d’un outil ;
- restauration d’un prompt ;
- suspension d’un assistant ;
- retour fournisseur ;
- mode dégradé ;
- transfert humain.

---

# 92. Monitoring

Le système doit surveiller :

- disponibilité ;
- latence ;
- erreurs ;
- coût ;
- tokens ;
- appels d’outils ;
- refus ;
- escalades ;
- satisfaction ;
- hallucinations ;
- sécurité ;
- qualité ;
- fournisseurs ;
- modèles.

---

# 93. Alertes opérationnelles

Exemples :

- fournisseur indisponible ;
- latence élevée ;
- coût anormal ;
- hausse des erreurs ;
- hausse des refus ;
- outil défaillant ;
- source obsolète ;
- tentative d’injection ;
- fuite potentielle ;
- chute de satisfaction ;
- modèle dégradé.

---

# 94. Coûts

Le système doit suivre :

- coût par modèle ;
- coût par fournisseur ;
- coût par assistant ;
- coût par application ;
- coût par pays ;
- coût par langue ;
- coût par utilisateur ;
- coût par outil ;
- coût par workflow ;
- coût par conversation.

---

# 95. Budgets IA

Un budget peut être défini par :

- pays ;
- application ;
- équipe ;
- assistant ;
- modèle ;
- fournisseur ;
- environnement ;
- mois ;
- année ;
- organisation.

---

# 96. Optimisation des coûts

Le système peut appliquer :

- modèles légers ;
- cache ;
- résumé du contexte ;
- limitation des tokens ;
- routage ;
- regroupement ;
- quota ;
- priorité ;
- réponse locale ;
- RAG ciblé.

---

# 97. Quotas

Le système doit permettre :

- quota par utilisateur ;
- quota par organisation ;
- quota par application ;
- quota par assistant ;
- quota par pays ;
- quota par outil ;
- quota par fournisseur ;
- quota journalier ;
- quota mensuel.

---

# 98. Mode réseau faible

Jini doit prévoir :

- réponses courtes ;
- interface texte ;
- compression ;
- reprise ;
- conservation du brouillon ;
- synchronisation ;
- mode SMS ;
- USSD limité ;
- réponse vocale légère ;
- désactivation des médias.

---

# 99. Mode hors ligne limité

Jini peut fournir hors ligne :

- FAQ intégrées ;
- guides ;
- procédures locales ;
- aide à la navigation ;
- brouillons ;
- historique récent autorisé ;
- réponses prévalidées.

Il ne doit pas confirmer des données financières non synchronisées.

---

# 100. Multi-pays

Chaque pays peut définir :

- assistants actifs ;
- langues ;
- fournisseurs ;
- modèles ;
- règles ;
- sources ;
- outils ;
- limites ;
- consentements ;
- rétention ;
- procédures ;
- obligations ;
- politiques de transfert.

---

# 101. Multi-langues

La plateforme doit gérer :

- langue utilisateur ;
- langue de l’application ;
- langue du document ;
- langue du modèle ;
- langue de secours ;
- traduction ;
- voix ;
- formats locaux ;
- devise ;
- date ;
- heure.

---

# 102. Langue de secours

Exemple :

```text
Bambara
→ français
→ anglais
```

La chaîne doit être configurable par pays et assistant.

---

# 103. Vie privée

La plateforme doit appliquer :

- minimisation ;
- consentement ;
- pseudonymisation ;
- masquage ;
- chiffrement ;
- séparation ;
- rétention ;
- suppression ;
- accès limité ;
- audit.

---

# 104. Conservation des conversations

La durée peut dépendre :

- du pays ;
- du canal ;
- de l’assistant ;
- du type de conversation ;
- de la sensibilité ;
- du consentement ;
- du ticket ;
- de l’obligation ;
- de l’environnement.

---

# 105. Suppression des conversations

La suppression doit être :

- autorisée ;
- propagée ;
- auditée ;
- compatible avec les obligations ;
- appliquée aux index ;
- appliquée aux mémoires ;
- appliquée aux caches ;
- vérifiée.

---

# 106. Utilisation des conversations pour l’amélioration

Une conversation ne doit pas être utilisée automatiquement pour entraîner un modèle.

L’utilisation doit dépendre :

- du consentement ;
- de l’anonymisation ;
- du pays ;
- de la finalité ;
- de l’autorisation ;
- de la sensibilité ;
- de la politique Mansa.

---

# 107. Données de test

Les environnements de test doivent utiliser :

- conversations fictives ;
- utilisateurs fictifs ;
- données synthétiques ;
- documents anonymisés ;
- comptes de démonstration ;
- transactions fictives ;
- secrets factices.

---

# 108. Administration centrale

L’administration peut gérer :

- assistants ;
- modèles ;
- fournisseurs ;
- prompts ;
- outils ;
- workflows ;
- connaissances ;
- langues ;
- mémoire ;
- garde-fous ;
- modération ;
- évaluations ;
- déploiements ;
- coûts ;
- quotas ;
- feature flags ;
- incidents ;
- accès ;
- audits.

---

# 109. Approbations

Peuvent nécessiter une approbation :

- nouveau fournisseur ;
- nouveau modèle ;
- nouveau prompt système ;
- nouvel outil ;
- nouvel assistant ;
- nouvelle source ;
- mémoire persistante ;
- export de conversations ;
- activation dans un pays ;
- modification d’un garde-fou ;
- activation d’un workflow financier.

---

# 110. Double validation

Peut être exigée pour :

- outil financier ;
- outil de blocage ;
- accès à des données sensibles ;
- prompt administrateur ;
- export massif ;
- activation d’un modèle de fraude ;
- suppression de mémoire ;
- changement de fournisseur principal ;
- activation nationale ;
- modification d’une règle de sécurité.

---

# 111. Séparation des rôles

Exemple :

```text
AI Engineer prépare
→ AI Safety contrôle
→ Responsable métier valide
→ Administrateur déploie
```

Le demandeur ne doit pas être son unique validateur.

---

# 112. API

Exemples :

```http
POST   /ai/conversations
POST   /ai/conversations/{id}/messages
GET    /ai/conversations/{id}

GET    /ai/assistants
POST   /ai/assistants
POST   /ai/assistants/{id}/publish

GET    /ai/models
POST   /ai/models
POST   /ai/models/{id}/deploy

GET    /ai/prompts
POST   /ai/prompts
POST   /ai/prompts/{id}/test
POST   /ai/prompts/{id}/publish

GET    /ai/tools
POST   /ai/tools
POST   /ai/tools/{id}/activate

GET    /ai/workflows
POST   /ai/workflows
POST   /ai/workflows/{id}/run

GET    /ai/evaluations
POST   /ai/evaluations/run

GET    /ai/reports
GET    /ai/audit
```

---

# 113. Webhooks internes

Événements possibles :

```text
ai.conversation.created
ai.message.generated
ai.tool.requested
ai.tool.completed
ai.tool.failed
ai.action.confirmation_required
ai.workflow.started
ai.workflow.completed
ai.workflow.escalated
ai.model.deployed
ai.model.degraded
ai.provider.failed
ai.guardrail.triggered
ai.prompt_injection.detected
ai.evaluation.failed
ai.cost.warning
ai.security.alert
```

---

# 114. Intégrations

La plateforme peut se connecter à :

- backend Mansa ;
- ledger ;
- cartes ;
- KYC ;
- KYB ;
- support ;
- sécurité ;
- fraude ;
- Finance ;
- Data ;
- notifications ;
- institutions ;
- entreprises ;
- établissements ;
- banques ;
- Mobile Money ;
- réseaux cartes ;
- documentation ;
- stockage objet ;
- systèmes vocaux ;
- fournisseurs de modèles ;
- observabilité.

---

# 115. Sécurité

Mesures principales :

- MFA ;
- RBAC ;
- ABAC ;
- chiffrement ;
- filtrage de contexte ;
- séparation des tenants ;
- isolation des outils ;
- signature ;
- gestion des secrets ;
- rotation des clés ;
- validation des sorties ;
- validation des entrées ;
- protection contre l’injection ;
- rate limiting ;
- audit ;
- révocation.

---

# 116. Protection contre les abus internes

Le système doit détecter :

- consultation massive ;
- export inhabituel ;
- modification de prompt ;
- activation d’un outil interdit ;
- utilisation hors pays ;
- désactivation d’un garde-fou ;
- copie de conversation ;
- accès sans motif ;
- usage d’un compte partagé ;
- test sur données réelles non autorisé ;
- contournement d’approbation.

---

# 117. Audit

Le journal doit contenir :

- utilisateur ;
- rôle ;
- assistant ;
- conversation ;
- modèle ;
- fournisseur ;
- prompt ;
- outil ;
- workflow ;
- source ;
- action ;
- date ;
- heure ;
- appareil ;
- IP ;
- pays ;
- environnement ;
- motif ;
- approbateur ;
- résultat.

---

# 118. Immutabilité des audits

Les audits ne doivent pas être :

- modifiés ;
- supprimés ;
- réécrits ;
- désactivés ;
- masqués sans trace ;
- exportés sans permission.

---

# 119. Modèles principaux

- AiAssistant
- AiAssistantVersion
- AiConversation
- AiMessage
- AiContext
- AiModel
- AiModelVersion
- AiProvider
- AiProviderRoute
- AiPrompt
- AiPromptVersion
- AiTool
- AiToolPermission
- AiToolExecution
- AiWorkflow
- AiWorkflowStep
- AiKnowledgeSource
- AiKnowledgeDocument
- AiEmbeddingIndex
- AiMemory
- AiMemoryConsent
- AiGuardrail
- AiModerationResult
- AiEvaluationDataset
- AiEvaluationRun
- AiModelDeployment
- AiIncident
- AiCost
- AiBudget
- AiApproval
- AiAudit

---

# 120. Analytics

Événements possibles :

```text
ai_assistant_opened
ai_conversation_started
ai_message_sent
ai_response_generated
ai_tool_called
ai_tool_completed
ai_tool_failed
ai_workflow_started
ai_workflow_completed
ai_human_escalation_requested
ai_source_opened
ai_feedback_submitted
ai_voice_started
ai_memory_updated
ai_guardrail_triggered
ai_security_alert_created
```

---

# 121. Données analytics interdites

Ne pas transmettre :

- contenu complet sensible ;
- PIN ;
- OTP ;
- CVV ;
- numéro complet de carte ;
- mot de passe ;
- clé privée ;
- secret API ;
- document complet ;
- message privé complet ;
- donnée biométrique ;
- résultat complet d’un outil financier ;
- prompt système complet.

---

# 122. Tests

- tests d’assistants ;
- tests de modèles ;
- tests de fournisseurs ;
- tests de routage ;
- tests de fallback ;
- tests de prompts ;
- tests de variables ;
- tests de conversations ;
- tests de contexte ;
- tests de permissions ;
- tests d’outils ;
- tests de lecture seule ;
- tests d’actions ;
- tests de validation ;
- tests MFA ;
- tests de workflows ;
- tests de reprise ;
- tests de RAG ;
- tests de sources ;
- tests de citations ;
- tests de fraîcheur ;
- tests de contradictions ;
- tests de mémoire ;
- tests de suppression ;
- tests vocaux ;
- tests Vision ;
- tests de traduction ;
- tests Jini Client ;
- tests Jini Commerce ;
- tests Jini Agent ;
- tests Jini TPE ;
- tests Jini Entreprise ;
- tests Jini Éducation ;
- tests Jini Institution ;
- tests Jini Développeur ;
- tests Jini Support ;
- tests Jini Sécurité ;
- tests Jini Finance ;
- tests Jini Data ;
- tests Jini Admin ;
- tests de garde-fous ;
- tests d’injection ;
- tests de modération ;
- tests d’hallucination ;
- tests d’escalade ;
- tests d’évaluation ;
- tests adversariaux ;
- tests multi-langues ;
- tests Shadow ;
- tests de rollback ;
- tests de coûts ;
- tests de quotas ;
- tests réseau faible ;
- tests hors ligne ;
- tests multi-pays ;
- tests vie privée ;
- tests sécurité ;
- tests audit ;
- tests performance ;
- tests accessibilité.

---

# 123. Règles métier

1. Jini ne remplace jamais les sources officielles.
2. Jini ne modifie jamais directement le ledger.
3. Jini respecte les permissions de l’utilisateur.
4. Les assistants sont spécialisés par domaine.
5. Les prompts sont versionnés.
6. Les modèles sont remplaçables.
7. Les outils possèdent des permissions explicites.
8. Les outils sensibles nécessitent une validation.
9. Les actions financières utilisent les API officielles.
10. Les secrets ne sont jamais transmis au modèle.
11. Le contexte est limité au strict nécessaire.
12. Les sources de connaissances sont versionnées.
13. Les réponses peuvent citer les sources.
14. Les sources obsolètes sont signalées.
15. La mémoire persistante exige une finalité.
16. Les utilisateurs peuvent supprimer leurs préférences.
17. Les conversations sensibles sont protégées.
18. Les garde-fous restent actifs en Production.
19. Les injections de prompt sont détectées.
20. Jini indique son incertitude.
21. Jini peut transférer vers un humain.
22. Les modèles sont testés avant activation.
23. Le mode Shadow est utilisé pour les changements importants.
24. Le demandeur ne valide pas seul une action critique.
25. Les audits sont immuables.

---

# 124. Critères d’acceptation

La Plateforme d’intelligence artificielle Jini Mansa est validée lorsque :

- plusieurs assistants spécialisés peuvent être créés ;
- chaque assistant possède un périmètre ;
- les rôles et permissions sont appliqués ;
- les conversations sont centralisées ;
- le contexte est filtré ;
- les prompts sont versionnés ;
- les fournisseurs sont remplaçables ;
- plusieurs modèles peuvent être configurés ;
- le routage des modèles fonctionne ;
- le fallback fonctionne ;
- les outils sont administrables ;
- les outils en lecture seule fonctionnent ;
- les outils sensibles demandent une validation ;
- les workflows sont administrables ;
- les workflows peuvent être repris ;
- la base de connaissances est connectée ;
- le RAG applique les permissions ;
- les réponses peuvent citer les sources ;
- les sources obsolètes sont détectées ;
- les contradictions sont signalées ;
- la mémoire est contrôlée ;
- les utilisateurs peuvent supprimer leurs préférences ;
- Jini vocal est intégrable ;
- Jini Vision est encadré ;
- les traductions sont prises en charge ;
- Jini Client est défini ;
- Jini Commerce est défini ;
- Jini Agent est défini ;
- Jini TPE est défini ;
- Jini Entreprise est défini ;
- Jini Éducation est défini ;
- Jini Institution est défini ;
- Jini Développeur est défini ;
- Jini Support est défini ;
- Jini Sécurité est défini ;
- Jini Finance est défini ;
- Jini Data est défini ;
- Jini Admin est défini ;
- les garde-fous sont actifs ;
- les injections de prompt sont détectées ;
- la modération est intégrée ;
- les hallucinations sont évaluées ;
- les transferts humains fonctionnent ;
- les jeux d’évaluation sont disponibles ;
- les tests adversariaux sont exécutés ;
- les modèles peuvent fonctionner en mode Shadow ;
- le déploiement progressif fonctionne ;
- le rollback est disponible ;
- le monitoring est centralisé ;
- les coûts sont suivis ;
- les budgets sont configurables ;
- les quotas sont appliqués ;
- le réseau faible est pris en charge ;
- le mode hors ligne limité fonctionne ;
- le multi-pays fonctionne ;
- le multi-langues fonctionne ;
- la vie privée est respectée ;
- les données de test sont séparées ;
- les actions critiques utilisent une approbation ;
- les audits sont immuables ;
- les tests couvrent les parcours essentiels.
