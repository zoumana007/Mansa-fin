# Mansa — Cahier des charges du module Fraude & Risk Engine

## 1. Objet

Le module Fraude & Risk Engine est le moteur central de prévention, détection, décision et investigation des risques de fraude au sein de l’écosystème Mansa.

Il doit protéger les opérations réalisées depuis les applications Client, Commerçant, TPE, Admin Lite, Annuaire/Hub, les intégrations Mobile Money, les cartes, les paiements QR/NFC, les transferts, les retraits, les encaissements marchands et les services publics.

Le module ne doit pas dépendre d’un seul fournisseur externe. Les règles critiques et le moteur de décision principal restent contrôlés par Mansa, tandis que des services tiers peuvent être branchés comme sources de signaux additionnelles.

## 2. Objectifs

- Évaluer le risque de chaque opération en temps réel.
- Détecter les comportements anormaux avant perte financière.
- Bloquer, ralentir, authentifier davantage ou soumettre à revue les opérations suspectes.
- Réduire les faux positifs pour ne pas détériorer l’expérience utilisateur.
- Fournir une traçabilité complète des décisions prises par le moteur de risque.
- Permettre aux équipes fraude et conformité de modifier les règles sans déploiement applicatif.
- Conserver une architecture multi-pays et multi-partenaire.
- Produire des preuves exploitables pour les investigations, contestations et audits.

## 3. Périmètre

Le module couvre notamment :

- authentification et prise de contrôle de compte ;
- création et modification de bénéficiaires ;
- transferts P2P ;
- paiements marchands ;
- paiements QR et NFC ;
- opérations TPE ;
- cartes physiques et virtuelles ;
- retraits et cash-out ;
- cash-in ;
- Mobile Money ;
- recharge de compte ;
- remboursements ;
- facturation récurrente ;
- paiement de taxes, amendes, frais scolaires et services publics ;
- opérations administratives sensibles ;
- changement d’appareil, numéro de téléphone, e-mail ou données KYC ;
- ajout ou remplacement de moyen de paiement ;
- tentatives d’accès administrateur ;
- API partenaires.

## 4. Principes de décision

Chaque événement évalué doit produire un résultat de risque structuré comprenant au minimum :

- `risk_score` : score numérique normalisé ;
- `risk_level` : LOW, MEDIUM, HIGH, CRITICAL ;
- `decision` : ALLOW, CHALLENGE, REVIEW, HOLD, DECLINE, BLOCK ;
- `reason_codes` : liste des facteurs ayant déclenché la décision ;
- `rules_triggered` : règles concernées ;
- `model_version` : version éventuelle du modèle statistique ou ML ;
- `policy_version` : version de la politique de risque ;
- `correlation_id` : identifiant de corrélation ;
- `evaluated_at` : horodatage serveur.

Une décision ne doit jamais reposer uniquement sur une valeur opaque impossible à expliquer.

## 5. Sources de signaux

### 5.1 Identité et compte

- âge du compte ;
- niveau KYC/KYB ;
- statut conformité ;
- historique de blocage ;
- changements récents de profil ;
- tentatives d’authentification échouées ;
- récupération récente de compte ;
- changements de PIN ou mot de passe ;
- réinitialisation de biométrie ;
- ancienneté du bénéficiaire.

### 5.2 Appareil

- identifiant d’appareil pseudonymisé ;
- nouveau téléphone ;
- appareil partagé entre plusieurs comptes ;
- système d’exploitation ;
- version applicative ;
- intégrité appareil ;
- détection root/jailbreak lorsque disponible ;
- émulateur ;
- anomalies de fuseau horaire ;
- signaux d’automatisation abusive.

### 5.3 Réseau

- adresse IP ;
- ASN ;
- pays estimé ;
- proxy ou VPN à risque ;
- changement inhabituel de localisation ;
- nombre de comptes utilisant la même IP ;
- vélocité des connexions.

### 5.4 Transaction

- montant ;
- devise ;
- type d’opération ;
- fréquence ;
- heure ;
- bénéficiaire ;
- marchand ;
- canal ;
- historique de montants du client ;
- écart avec le comportement habituel ;
- succession rapide de petites opérations ;
- tentative après plusieurs refus ;
- fractionnement de montants ;
- remboursement inhabituel ;
- montants proches des plafonds.

### 5.5 Marchand et TPE

- âge du marchand ;
- secteur ;
- profil de chiffre d’affaires ;
- taux de remboursement ;
- taux de litige ;
- nombre de cartes ou comptes distincts ;
- localisation habituelle du TPE ;
- terminal nouvellement activé ;
- transaction hors zone prévue ;
- séquences d’annulations ;
- comportement anormal d’un employé.

### 5.6 Partenaires externes

- signaux banque partenaire ;
- signaux processeur cartes ;
- signaux Mobile Money ;
- listes de fraude internes ;
- listes réglementaires lorsque légalement applicables ;
- données partenaires prévues contractuellement.

## 6. Moteur de règles

Le moteur de règles doit permettre :

- règles conditionnelles versionnées ;
- activation/désactivation immédiate ;
- portée par pays ;
- portée par produit ;
- portée par canal ;
- portée par segment client ;
- périodes d’effet ;
- seuils configurables ;
- listes autorisées et bloquées ;
- combinaison AND/OR ;
- priorités ;
- règles de vélocité ;
- règles cumulatives ;
- exceptions contrôlées ;
- mode simulation avant activation ;
- comparaison de politiques A/B lorsque autorisée.

Exemples :

- nouveau bénéficiaire + appareil inconnu + montant élevé => CHALLENGE ;
- 5 tentatives de paiement refusées en 10 minutes => HOLD ;
- carte utilisée dans deux pays incompatibles dans un délai impossible => DECLINE ;
- compte récemment récupéré + retrait important => REVIEW ;
- TPE déplacé hors zone autorisée => REVIEW ou BLOCK selon contexte.

## 7. Vélocité

Le système doit pouvoir compter en temps réel :

- nombre de transactions par minute, heure, jour ;
- montant total par période ;
- nombre de bénéficiaires distincts ;
- nombre de cartes utilisées ;
- nombre d’appareils ;
- nombre d’IP ;
- nombre de comptes liés à un appareil ;
- nombre de remboursements ;
- nombre d’échecs d’authentification.

Les fenêtres de temps doivent être configurables.

## 8. Actions disponibles

### ALLOW
Autorisation normale.

### CHALLENGE
Demande d’authentification renforcée : PIN, biométrie, OTP, confirmation depuis appareil de confiance ou autre mécanisme selon le contexte.

### REVIEW
L’opération ou le compte est envoyé vers une file de revue manuelle.

### HOLD
L’opération est temporairement retenue dans les limites réglementaires et contractuelles applicables.

### DECLINE
L’opération est refusée sans nécessairement bloquer le compte.

### BLOCK
Blocage du compte, du moyen de paiement, du terminal, de l’appareil ou du partenaire selon le niveau de risque et les permissions autorisées.

## 9. Revue manuelle

Une console fraude doit afficher :

- identité du client ou marchand ;
- score de risque ;
- motifs ;
- chronologie ;
- transactions liées ;
- appareils ;
- IP ;
- bénéficiaires ;
- moyens de paiement ;
- TPE ;
- documents KYC/KYB selon habilitation ;
- liens entre comptes ;
- décisions précédentes ;
- notes des analystes ;
- pièces justificatives ;
- actions disponibles.

Chaque action d’un analyste doit être auditée.

## 10. Gestion des cas

Un cas fraude comprend au minimum :

- identifiant unique ;
- type de cas ;
- priorité ;
- statut ;
- score ;
- entités concernées ;
- propriétaire ;
- date de création ;
- SLA ;
- preuves ;
- journal ;
- décision finale ;
- montant exposé ;
- montant évité ;
- perte confirmée ;
- motif de clôture.

Statuts recommandés :

- OPEN ;
- TRIAGE ;
- INVESTIGATING ;
- WAITING_CUSTOMER ;
- WAITING_PARTNER ;
- ESCALATED ;
- CONFIRMED_FRAUD ;
- FALSE_POSITIVE ;
- CLOSED.

## 11. Listes et graphes de relations

Le système doit gérer :

- liste noire ;
- liste grise ;
- liste blanche exceptionnelle ;
- appareils à risque ;
- comptes liés ;
- numéros de téléphone liés ;
- IP à risque ;
- bénéficiaires suspects ;
- marchands suspects ;
- TPE suspects.

Un graphe de relations doit permettre d’identifier des clusters de comptes reliés par appareil, téléphone, IP, bénéficiaire, carte, marchand ou autre identifiant autorisé.

## 12. Fraude spécifique Mobile Money

Le moteur doit détecter notamment :

- cash-in/cash-out circulaire ;
- forte augmentation soudaine du volume ;
- fractionnement de transactions ;
- bénéficiaires nouvellement créés ;
- schémas répétitifs agent-client ;
- comptes servant de relais ;
- divergences entre identité Mansa et partenaire ;
- multiples échecs de validation partenaire.

## 13. Fraude cartes

Prévoir :

- vélocité carte ;
- comportement géographique ;
- MCC à risque ;
- paiements en ligne inhabituels ;
- tentatives répétées ;
- token ou carte nouvellement provisionné ;
- utilisation anormale de carte virtuelle ;
- remboursement marchand suspect ;
- changement brutal de panier moyen.

Les détails PCI sensibles ne doivent pas être stockés hors du périmètre autorisé.

## 14. Fraude TPE et marchands

Détecter :

- auto-paiement ;
- collusion ;
- faux achats ;
- remboursements artificiels ;
- création rapide de multiples transactions proches ;
- terminal utilisé hors établissement ;
- volumes incohérents avec le secteur ;
- comportement inhabituel d’un employé ;
- utilisation d’un même instrument sur de nombreux comptes marchands liés.

## 15. Services État

Les opérations publiques doivent intégrer des règles spécifiques :

- identité de l’agent public ;
- appareil ou terminal autorisé ;
- géolocalisation lorsque applicable et licite ;
- référence officielle du dossier ;
- interdiction de modification du montant hors règles autorisées ;
- traçabilité des annulations ;
- double validation pour opérations sensibles ;
- détection d’abus répétés d’un agent ;
- rapprochement avec l’organisme public.

## 16. Sécurité du moteur de risque

- accès strictement RBAC/ABAC ;
- MFA obligatoire pour analystes et administrateurs ;
- journalisation immuable des modifications de règles ;
- séparation maker/checker pour règles critiques ;
- chiffrement en transit et au repos ;
- secrets hors dépôt ;
- rotation des clés ;
- protection anti-abus API ;
- contrôle des exports ;
- rétention selon politique de données.

## 17. Architecture logique

Composants recommandés :

- Risk API ;
- Rule Engine ;
- Velocity Store ;
- Feature Service ;
- Decision Service ;
- Case Management ;
- Watchlist Service ;
- Device Intelligence Adapter ;
- Partner Signal Adapters ;
- Event Consumer ;
- Audit Service ;
- Risk Admin Console.

Le flux synchrone critique doit rester rapide et isolé des traitements analytiques lourds.

## 18. Événements

Événements principaux :

- `risk.evaluation.requested` ;
- `risk.evaluation.completed` ;
- `risk.challenge.required` ;
- `risk.transaction.held` ;
- `risk.transaction.declined` ;
- `risk.entity.blocked` ;
- `risk.case.created` ;
- `risk.case.updated` ;
- `risk.rule.changed` ;
- `risk.watchlist.changed`.

Chaque événement contient `event_id`, `correlation_id`, `occurred_at`, version de schéma et identifiants d’entités pseudonymisés lorsque nécessaire.

## 19. API indicative

- `POST /v1/risk/evaluate`
- `POST /v1/risk/challenges/{id}/complete`
- `GET /v1/risk/cases`
- `GET /v1/risk/cases/{id}`
- `POST /v1/risk/cases/{id}/actions`
- `GET /v1/risk/rules`
- `POST /v1/risk/rules`
- `POST /v1/risk/rules/{id}/simulate`
- `POST /v1/risk/watchlists`
- `GET /v1/risk/entities/{id}/signals`

Toutes les opérations d’écriture sensibles doivent être idempotentes et auditées.

## 20. Modèle de données principal

Entités :

- `RiskEvaluation` ;
- `RiskDecision` ;
- `RiskRule` ;
- `RiskPolicy` ;
- `RiskSignal` ;
- `VelocityCounter` ;
- `RiskCase` ;
- `CaseEvent` ;
- `WatchlistEntry` ;
- `EntityRelationship` ;
- `RiskOverride` ;
- `FraudLoss`.

Les identifiants métier sensibles doivent être séparés des données analytiques lorsque possible.

## 21. Performance

Objectifs initiaux à valider par tests de charge :

- disponibilité du service de décision >= 99,95 % en production ;
- p95 d’une évaluation synchrone simple <= 150 ms hors dépendance externe lente ;
- p99 <= 300 ms dans les conditions nominales ;
- dégradation contrôlée si une source secondaire est indisponible ;
- aucune dépendance non critique ne doit bloquer un paiement.

## 22. Résilience

- timeout strict des fournisseurs externes ;
- circuit breakers ;
- files de reprise ;
- idempotence ;
- retries bornés ;
- réplication du stockage critique ;
- stratégie fail-open/fail-closed configurable par type d’opération ;
- mode dégradé documenté.

Une opération à très haut risque ne doit jamais passer automatiquement en fail-open sans règle explicite.

## 23. Observabilité

Mesurer :

- volume d’évaluations ;
- latence ;
- taux de refus ;
- taux de challenge ;
- taux de revue ;
- taux de faux positifs ;
- fraude confirmée ;
- pertes ;
- pertes évitées ;
- règles les plus déclenchées ;
- fournisseurs de signaux indisponibles ;
- backlog des cas ;
- SLA des analystes.

## 24. Gouvernance des règles

Toute règle critique doit avoir :

- propriétaire ;
- justification ;
- version ;
- date d’entrée en vigueur ;
- métrique de suivi ;
- historique ;
- approbateur ;
- possibilité de rollback.

Les modifications sensibles nécessitent un mécanisme maker/checker.

## 25. Modèles ML éventuels

Le machine learning peut compléter les règles mais ne doit pas être obligatoire pour le MVP.

Si utilisé :

- versionner les modèles ;
- documenter les variables ;
- surveiller dérive et biais ;
- permettre rollback ;
- conserver l’explicabilité suffisante ;
- séparer entraînement et production ;
- ne jamais utiliser des données sans base légale ou consentement approprié.

## 26. Protection des données

- minimisation ;
- pseudonymisation ;
- rétention configurable ;
- contrôle des accès ;
- journalisation des consultations sensibles ;
- export encadré ;
- suppression ou anonymisation lorsque la conservation n’est plus justifiée ;
- séparation des données analytiques et des secrets.

## 27. Tests obligatoires

- unitaires du moteur de règles ;
- tests de vélocité ;
- tests d’idempotence ;
- tests de concurrence ;
- tests de latence ;
- tests de bascule fournisseur ;
- tests de charge ;
- tests de sécurité ;
- tests des permissions ;
- tests de simulation de fraude ;
- tests de non-régression des décisions ;
- tests de faux positifs.

## 28. Environnements

### Démo
Données fictives et scénarios simulés.

### Recette
Règles proches de la production, partenaires sandbox, tests automatisés et jeux de fraude synthétiques.

### Production
Règles approuvées, secrets gérés par coffre, supervision, journaux protégés et procédures d’incident actives.

## 29. Indicateurs métier

- fraude en points de base du volume ;
- taux de fraude confirmée ;
- taux de faux positifs ;
- taux de challenge réussi ;
- taux de blocage ;
- montant de pertes évitées ;
- délai moyen de détection ;
- délai moyen de clôture d’un cas ;
- part des décisions automatisées ;
- taux de récupération après fraude.

## 30. Critères d’acceptation MVP

Le MVP est acceptable si :

1. chaque transaction majeure peut être évaluée via une API unique ;
2. les règles sont versionnées et modifiables sans redéploiement ;
3. la vélocité fonctionne au minimum par compte, appareil et bénéficiaire ;
4. les décisions ALLOW, CHALLENGE, REVIEW, HOLD, DECLINE et BLOCK sont supportées ;
5. les analystes disposent d’une file de cas ;
6. toutes les décisions et modifications de règles sont auditables ;
7. les appels sont corrélés de bout en bout ;
8. un fournisseur secondaire indisponible ne fait pas tomber tout le moteur ;
9. le module est multi-pays et configurable ;
10. aucun secret ni donnée PCI interdite n’est ajouté au dépôt.

## 31. Évolutions

- détection par graphes ;
- modèles comportementaux avancés ;
- scoring marchand ;
- scoring appareil ;
- partage de signaux avec partenaires sous cadre contractuel ;
- orchestration automatique d’investigations ;
- détection de mule accounts ;
- détection de fraude organisée ;
- adaptation temps réel des seuils selon contexte ;
- outils de simulation et replay massif d’événements.

## 32. Dépendances

Le module dépend notamment de :

- Authentification ;
- KYC/KYB ;
- Wallets ;
- Transactions ;
- Paiements ;
- Cartes ;
- Mobile Money ;
- TPE ;
- Commerçants ;
- Notifications ;
- Support/Litiges ;
- Audit ;
- Analytics ;
- Services État.

Les dépendances doivent passer par contrats API ou événements versionnés afin d’éviter un couplage direct aux bases de données d’autres modules.
