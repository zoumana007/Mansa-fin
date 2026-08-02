# 37 — Gouvernance de l’intelligence artificielle (Jini), automatisation, décisions assistées et IA responsable de Mansa

## 1. Objet du document

Ce document définit l’architecture officielle de gouvernance de l’intelligence artificielle de Mansa.

Il couvre :

- Jini ;
- les assistants IA ;
- les modèles internes ;
- les modèles externes ;
- les agents IA ;
- les automatisations ;
- les recommandations ;
- les décisions assistées ;
- les décisions automatisées ;
- les workflows IA ;
- les permissions ;
- les outils ;
- les prompts ;
- les connaissances ;
- les fournisseurs IA ;
- la sécurité ;
- la confidentialité ;
- les hallucinations ;
- les contrôles humains ;
- l’audit ;
- les métriques ;
- les obligations réglementaires ;
- la gouvernance multi-pays.

L’objectif est de garantir que toute utilisation de l’IA dans Mansa soit :

- utile ;
- sécurisée ;
- explicable ;
- contrôlée ;
- auditable ;
- conforme ;
- réversible ;
- limitée à son périmètre ;
- respectueuse des données personnelles ;
- alignée avec les règles métier.

---

# 2. Principes fondamentaux

## 2.1 L'IA assiste mais ne gouverne pas

Par défaut, Jini assiste les utilisateurs et les employés.

Il ne devient jamais l'autorité finale pour les décisions critiques.

Les décisions importantes restent sous le contrôle :

- des règles métier ;
- des workflows ;
- des responsables habilités ;
- des validations humaines lorsque requises.

---

## 2.2 Les permissions priment sur l’IA

Jini ne peut accéder qu’aux données que l’utilisateur a le droit de consulter.

L’IA ne doit jamais contourner :

- RBAC ;
- ABAC ;
- permissions ;
- restrictions pays ;
- segmentation des organisations ;
- confidentialité.

---

## 2.3 Chaque réponse doit avoir une finalité

Avant d'utiliser une donnée, Jini doit connaître :

- pourquoi ;
- pour qui ;
- dans quel contexte ;
- avec quelles permissions ;
- pendant combien de temps.

---

## 2.4 Les actions critiques sont interdites sans workflow

Jini ne peut jamais seul :

- modifier un solde ;
- créer une écriture ledger ;
- débloquer un compte ;
- supprimer une preuve ;
- valider un remboursement important ;
- approuver un KYC ;
- approuver un commerçant ;
- supprimer des données protégées ;
- modifier une configuration critique.

---

## 2.5 L’humain garde le contrôle

Pour les décisions sensibles :

- fraude ;
- conformité ;
- remboursement ;
- litige ;
- suspension ;
- suppression ;
- changement réglementaire ;
- paiement institutionnel,

l’IA ne fournit qu’une recommandation.

---

# 3. Cas d’usage de Jini

Jini peut assister :

- particuliers ;
- commerçants ;
- employés ;
- administrateurs ;
- partenaires ;
- développeurs ;
- support ;
- conformité ;
- fraude ;
- opérations.

---

# 4. Assistance utilisateur

Jini peut :

- répondre aux questions ;
- guider un paiement ;
- expliquer une transaction ;
- aider au KYC ;
- expliquer une erreur ;
- guider l’utilisation d’un TPE ;
- expliquer des frais ;
- retrouver une fonctionnalité ;
- assister la navigation.

---

# 5. Assistance commerçant

Il peut :

- expliquer les ventes ;
- expliquer les règlements ;
- aider aux remboursements ;
- analyser les performances ;
- expliquer les commissions ;
- assister le catalogue ;
- assister les promotions ;
- guider les employés.

---

# 6. Assistance support

Il peut :

- résumer un ticket ;
- proposer une réponse ;
- traduire ;
- retrouver une procédure ;
- suggérer une catégorie ;
- détecter un doublon ;
- préparer une chronologie ;
- résumer un incident.

---

# 7. Assistance conformité

Il peut :

- résumer un dossier ;
- retrouver des documents ;
- comparer des informations ;
- détecter des incohérences ;
- préparer une analyse.

La décision finale reste humaine.

---

# 8. Assistance fraude

Jini peut :

- signaler une anomalie ;
- expliquer un score ;
- regrouper les alertes ;
- préparer un dossier ;
- suggérer une priorité.

Il ne clôture jamais seul une enquête fraude.

---

# 9. Assistance développement

Il peut aider à :

- expliquer une API ;
- retrouver une documentation ;
- proposer un exemple ;
- expliquer une erreur ;
- générer un squelette de code ;
- résumer un log.

---

# 10. Assistance analytique

Jini peut produire :

- résumés ;
- tableaux ;
- tendances ;
- alertes ;
- comparaisons ;
- recommandations.

Les chiffres doivent provenir des données autorisées.

---

# 11. Types d’IA

Mansa peut utiliser :

- modèles génératifs ;
- modèles de classification ;
- modèles de scoring ;
- modèles OCR ;
- modèles biométriques ;
- modèles NLP ;
- modèles de traduction ;
- modèles d’embedding ;
- modèles spécialisés.

---

# 12. Fournisseurs IA

Le système doit permettre plusieurs fournisseurs configurables.

Exemples :

- fournisseur principal ;
- fournisseur secondaire ;
- modèle interne.

Le choix ne doit pas être codé en dur.

---

# 13. Architecture IA

L’architecture comprend :

- Jini Gateway ;
- orchestrateur ;
- gestionnaire de prompts ;
- gestionnaire de contexte ;
- filtre de sécurité ;
- moteur de permissions ;
- registre des modèles ;
- observabilité ;
- audit.

---

# 14. Registre des modèles

Chaque modèle doit posséder :

- identifiant ;
- fournisseur ;
- version ;
- type ;
- langues ;
- coût ;
- limites ;
- contexte maximal ;
- date d’activation ;
- statut.

---

# 15. Statuts

Exemples :

- DRAFT ;
- TEST ;
- PILOT ;
- ACTIVE ;
- LIMITED ;
- SUSPENDED ;
- RETIRED.

---

# 16. Sélection d’un modèle

La sélection peut dépendre :

- du coût ;
- de la langue ;
- du temps de réponse ;
- du pays ;
- de la confidentialité ;
- du type de tâche ;
- des permissions.

---

# 17. Prompts système

Les prompts système doivent être :

- versionnés ;
- audités ;
- approuvés ;
- séparés du code ;
- modifiables par configuration ;
- limités aux administrateurs autorisés.

---

# 18. Prompts utilisateur

Les prompts utilisateur doivent être :

- journalisés selon la politique ;
- filtrés ;
- protégés ;
- limités en taille ;
- associés au contexte.

---

# 19. Gestion du contexte

Le contexte transmis au modèle doit être :

- minimal ;
- pertinent ;
- autorisé ;
- temporaire ;
- nettoyé des données inutiles.

---

# 20. Protection des données

Avant tout appel IA :

- masquer les secrets ;
- masquer les clés ;
- masquer les PIN ;
- masquer les OTP ;
- masquer les CVV ;
- masquer les données inutiles.

---

# 21. Filtrage

Le système doit filtrer :

- injections de prompt ;
- demandes interdites ;
- données sensibles ;
- tentatives d’exfiltration ;
- contenu malveillant.

---

# 22. Outils IA

Jini peut utiliser des outils contrôlés :

- recherche documentaire ;
- lecture de transactions autorisées ;
- consultation de tickets ;
- consultation de paramètres ;
- génération de rapports ;
- traduction.

Chaque outil possède des permissions.

---

# 23. Appels d’outils

Chaque appel doit enregistrer :

- outil ;
- utilisateur ;
- permissions ;
- durée ;
- succès ;
- données consultées.

---

# 24. Décisions assistées

Jini peut recommander :

- un niveau de priorité ;
- une catégorie ;
- un workflow ;
- une procédure ;
- une équipe ;
- un document.

---

# 25. Décisions interdites

Sans validation humaine, Jini ne peut pas :

- approuver un remboursement critique ;
- fermer un dossier AML ;
- approuver un KYC complexe ;
- modifier des permissions ;
- supprimer un utilisateur ;
- approuver un partenaire.

---

# 26. Explicabilité

Pour chaque recommandation importante, Jini doit pouvoir fournir :

- les principaux facteurs pris en compte ;
- les données utilisées ;
- le niveau de confiance si disponible ;
- les limites de la recommandation.

---

# 27. Gestion des hallucinations

Le système doit :

- détecter les réponses incertaines ;
- privilégier les sources internes autorisées ;
- indiquer lorsqu'une information n'est pas disponible ;
- éviter les affirmations non fondées.

---

# 28. Validation humaine

Les workflows peuvent exiger :

- une validation ;
- une double validation ;
- une justification ;
- une approbation hiérarchique.

---

# 29. Journalisation

Chaque interaction IA doit enregistrer :

- utilisateur ;
- rôle ;
- modèle ;
- version ;
- outils utilisés ;
- durée ;
- coût ;
- statut ;
- identifiant de corrélation.

---

# 30. Administration

Le portail Admin doit permettre :

- gérer les modèles ;
- activer ou suspendre un modèle ;
- gérer les prompts ;
- consulter les journaux ;
- suivre les coûts ;
- consulter les métriques ;
- gérer les permissions IA ;
- gérer les fournisseurs ;
- lancer des tests.

---

# 31. Permissions

Exemples :

```text
ai.chat.use
ai.model.read
ai.model.manage
ai.prompt.read
ai.prompt.manage
ai.audit.read
ai.tool.use
ai.tool.manage
ai.cost.read
ai.provider.manage
ai.test.execute
```

---

# 32. Analytics

Événements possibles :

```text
ai_chat_started
ai_chat_completed
ai_tool_called
ai_prompt_updated
ai_model_activated
ai_model_suspended
ai_recommendation_generated
ai_human_override
ai_provider_switched
```

---

# 33. Tests

- tests de permissions ;
- tests de filtrage ;
- tests d’injection de prompt ;
- tests de confidentialité ;
- tests de sélection de modèle ;
- tests de changement de fournisseur ;
- tests d’outils ;
- tests d’audit ;
- tests de journalisation ;
- tests de validation humaine.

---

# 34. Critères d’acceptation

La gouvernance IA est validée lorsque :

- les modèles sont enregistrés ;
- les permissions sont respectées ;
- les données sensibles sont protégées ;
- les prompts sont versionnés ;
- les outils sont contrôlés ;
- les recommandations restent explicables ;
- les actions critiques nécessitent une validation humaine ;
- les journaux sont disponibles ;
- les coûts sont mesurables ;
- les tests couvrent les principaux scénarios.
