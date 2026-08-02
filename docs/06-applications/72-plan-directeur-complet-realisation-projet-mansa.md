# 72 — Plan directeur complet de réalisation du projet Mansa : organisation, priorités, phases, équipes, livrables, dépendances, calendrier, budget, contrôle et passage à l’exécution

## 1. Objet du document

Ce document définit le **plan directeur officiel de réalisation du projet Mansa**.

Il transforme l’ensemble des cahiers des charges, architectures, règles métier et stratégies déjà définis en un programme concret de réalisation.

Il doit permettre de savoir :

- quoi construire ;
- dans quel ordre ;
- avec quelles équipes ;
- avec quelles dépendances ;
- avec quels partenaires ;
- avec quels critères de validation ;
- avec quels budgets ;
- avec quels délais ;
- avec quels risques ;
- avec quelles priorités ;
- avec quelles versions ;
- avec quelles étapes de lancement.

Le plan directeur couvre notamment :

- les applications ;
- le backend ;
- les bases de données ;
- le ledger ;
- les intégrations bancaires ;
- le Mobile Money ;
- les cartes ;
- le réseau Agent ;
- les commerçants ;
- les TPE ;
- les GAB et DAB ;
- les portails ;
- l’administration ;
- la sécurité ;
- la conformité ;
- la Finance ;
- la fraude ;
- la Data ;
- Jini ;
- le support ;
- l’infrastructure ;
- la qualité ;
- le déploiement ;
- la documentation ;
- l’exploitation ;
- le lancement au Mali ;
- l’extension régionale.

---

# 2. Principe général

Mansa ne doit pas être construit comme un seul bloc livré à la fin.

Le projet doit être réalisé sous forme de plateformes, modules, applications et versions successives.

Ordre général :

```text
Fondations
→ Socle financier
→ Applications principales
→ Réseau de paiement
→ Partenaires
→ Administration
→ Sécurité et conformité
→ Pilote
→ Lancement limité
→ Lancement national
→ Extension régionale
```

---

# 3. Objectif de la première version

La première version opérationnelle doit permettre au minimum :

- inscription ;
- connexion ;
- KYC ;
- création de wallet ;
- consultation du solde ;
- transfert Mansa à Mansa ;
- dépôt chez un Agent ;
- retrait chez un Agent ;
- paiement QR ;
- encaissement commerçant ;
- notifications ;
- reçus ;
- support ;
- administration ;
- ledger ;
- frais ;
- commissions ;
- audit ;
- supervision.

---

# 4. Fonctions non obligatoires pour la première version

Peuvent être ajoutées après le socle :

- cartes physiques ;
- cartes virtuelles avancées ;
- GAB/DAB ;
- crédit ;
- épargne avancée ;
- assurance ;
- paiements internationaux ;
- services État ;
- éducation ;
- entreprises ;
- Jini avancé ;
- fidélité avancée ;
- multi-pays.

---

# 5. Découpage global du programme

Le programme peut être divisé en douze grands chantiers :

1. Gouvernance et produit.
2. Architecture et fondations techniques.
3. Identité, KYC et sécurité.
4. Ledger, wallets et services financiers.
5. Applications mobiles et web.
6. Réseau Agent et Commerce.
7. TPE, cartes et GAB/DAB.
8. Partenaires bancaires et Mobile Money.
9. Administration, Finance, fraude et conformité.
10. Infrastructure, CI/CD et observabilité.
11. Tests, Recette et pilote.
12. Lancement et montée en charge.

---

# 6. Chantier 1 — Gouvernance et Produit

Ce chantier doit produire :

- vision produit ;
- périmètre ;
- priorités ;
- roadmap ;
- backlog ;
- critères d’acceptation ;
- responsabilités ;
- gouvernance ;
- budget ;
- planning ;
- gestion des changements ;
- reporting de programme.

---

# 7. Gouvernance du programme

Structure recommandée :

```text
Direction Mansa
→ Comité stratégique
→ Direction Produit
→ Direction Technique
→ Direction Opérations
→ Direction Finance
→ Sécurité et Conformité
→ Responsables de domaines
→ Équipes de réalisation
```

---

# 8. Comité stratégique

Il doit décider :

- priorités ;
- budget ;
- partenaires ;
- pays ;
- calendrier ;
- risques majeurs ;
- modifications importantes ;
- Go / No-Go ;
- lancement ;
- arrêt éventuel.

---

# 9. Comité produit

Il doit gérer :

- besoins ;
- parcours ;
- fonctionnalités ;
- priorités ;
- designs ;
- retours utilisateurs ;
- règles métier ;
- validation fonctionnelle ;
- roadmap.

---

# 10. Comité technique

Il doit gérer :

- architecture ;
- technologies ;
- sécurité ;
- données ;
- intégrations ;
- performances ;
- qualité ;
- dette technique ;
- versions ;
- exploitation.

---

# 11. Direction de programme

Elle doit suivre :

- planning ;
- dépendances ;
- ressources ;
- budget ;
- risques ;
- décisions ;
- livrables ;
- blocages ;
- qualité ;
- communication.

---

# 12. Méthode de réalisation

La réalisation peut fonctionner par cycles courts :

```text
Besoin
→ spécification
→ design
→ développement
→ test
→ démonstration
→ correction
→ validation
→ livraison
```

---

# 13. Organisation en lots

Chaque lot doit contenir :

- objectif ;
- périmètre ;
- responsable ;
- dépendances ;
- livrables ;
- tests ;
- risques ;
- budget ;
- critères de validation ;
- date cible.

---

# 14. Priorisation

Niveaux possibles :

- P0 : indispensable au lancement ;
- P1 : essentiel à court terme ;
- P2 : important après le pilote ;
- P3 : amélioration ;
- P4 : évolution future.

---

# 15. Priorités P0

Les priorités P0 comprennent :

- authentification ;
- identité ;
- KYC ;
- wallet ;
- ledger ;
- transfert ;
- dépôt Agent ;
- retrait Agent ;
- paiement commerçant ;
- QR ;
- frais ;
- commissions ;
- notifications ;
- Admin Web ;
- support ;
- monitoring ;
- audit ;
- sauvegardes ;
- sécurité.

---

# 16. Priorités P1

Les priorités P1 peuvent comprendre :

- Application TPE ;
- cartes ;
- Mobile Money ;
- rapprochement avancé ;
- fraude ;
- rapports Finance ;
- gestion multi-agents ;
- gestion multi-points de vente ;
- Admin Lite ;
- fidélité simple ;
- facturation avancée.

---

# 17. Priorités P2

Les priorités P2 peuvent comprendre :

- GAB/DAB ;
- entreprises ;
- éducation ;
- services État ;
- Data avancée ;
- Jini avancé ;
- multi-devises ;
- multi-pays ;
- cashback avancé ;
- marketplace.

---

# 18. Chantier 2 — Architecture et fondations techniques

Livrables :

- architecture cible ;
- monorepo ou organisation des dépôts ;
- conventions de code ;
- API Gateway ;
- gestion des environnements ;
- configuration centralisée ;
- secrets ;
- authentification technique ;
- Event Bus ;
- files de messages ;
- observabilité ;
- documentation technique.

---

# 19. Organisation des dépôts

Organisation possible :

```text
mansa-platform/
├── apps/
│   ├── client-mobile/
│   ├── merchant-mobile/
│   ├── agent-mobile/
│   ├── admin-lite/
│   ├── admin-web/
│   ├── website/
│   ├── tpe/
│   └── portals/
├── services/
├── packages/
├── infrastructure/
├── documentation/
├── tests/
└── tools/
```

---

# 20. Packages partagés

Peuvent être mutualisés :

- design system ;
- types ;
- SDK API ;
- authentification ;
- validation ;
- erreurs ;
- logs ;
- traduction ;
- analytics ;
- configuration ;
- composants UI ;
- sécurité ;
- tests.

---

# 21. Chantier 3 — Identité et authentification

Livrables :

- création utilisateur ;
- gestion téléphone ;
- gestion e-mail ;
- OTP ;
- mot de passe ;
- PIN ;
- MFA ;
- biométrie ;
- appareils ;
- sessions ;
- récupération ;
- révocation ;
- rôles ;
- permissions.

---

# 22. KYC

Livrables :

- niveaux KYC ;
- documents ;
- selfie ;
- biométrie si activée ;
- vérification ;
- revue manuelle ;
- rejet ;
- recours ;
- expiration ;
- mise à jour ;
- historique ;
- intégration fournisseur.

---

# 23. KYB

Livrables :

- entreprise ;
- documents ;
- représentant légal ;
- bénéficiaires effectifs ;
- activité ;
- statut ;
- risque ;
- validation ;
- suspension ;
- mise à jour.

---

# 24. Chantier 4 — Ledger et Wallet

Le ledger doit être réalisé avant les opérations financières réelles.

Livrables :

- comptes ledger ;
- écritures ;
- débit ;
- crédit ;
- devises ;
- références ;
- statuts ;
- idempotence ;
- réservations ;
- compensations ;
- annulations ;
- rapprochement ;
- audit ;
- rapports.

---

# 25. Wallet

Livrables :

- wallet Client ;
- wallet Agent ;
- wallet Commerce ;
- wallet Entreprise ;
- wallet Institution ;
- soldes ;
- limites ;
- blocage ;
- gel ;
- historique ;
- devise ;
- relations ledger.

---

# 26. Moteur de frais

Il doit permettre :

- montant fixe ;
- pourcentage ;
- minimum ;
- maximum ;
- gratuité ;
- promotion ;
- pays ;
- produit ;
- segment ;
- date d’effet ;
- historique ;
- approbation.

---

# 27. Moteur de commissions

Il doit répartir les revenus entre :

- Mansa ;
- agent ;
- commerçant ;
- banque ;
- opérateur ;
- partenaire ;
- réseau cartes ;
- distributeur.

---

# 28. Chantier 5 — Applications principales

Les premières applications à construire sont :

1. Application Client.
2. Application Commerce.
3. Application Agent.
4. Admin Web.

L’Application TPE peut être développée en parallèle selon les ressources.

---

# 29. Application Client — ordre de réalisation

Ordre recommandé :

1. Splash et onboarding.
2. Inscription.
3. Connexion.
4. OTP.
5. KYC.
6. Accueil.
7. Solde.
8. Historique.
9. Transfert.
10. Paiement QR.
11. Dépôt.
12. Retrait.
13. Notifications.
14. Support.
15. Profil.
16. Sécurité.
17. Cartes.
18. Budgets.
19. Coffres.
20. Jini.

---

# 30. Application Commerce — ordre de réalisation

1. Inscription.
2. KYB.
3. Connexion.
4. Accueil.
5. Encaissement.
6. QR.
7. Transactions.
8. Remboursement.
9. Reçus.
10. Caisse.
11. Employés.
12. Points de vente.
13. Règlement.
14. Rapports.
15. TPE.
16. Catalogue.
17. Promotions.
18. Fidélité.
19. Support.

---

# 31. Application Agent — ordre de réalisation

1. Enrôlement.
2. Connexion.
3. Appareil.
4. Ouverture de caisse.
5. Float.
6. Dépôt.
7. Retrait.
8. Reçu.
9. Historique.
10. Commission.
11. Réapprovisionnement.
12. Incident.
13. Fermeture de caisse.
14. Support.
15. Rapports.

---

# 32. Admin Web — ordre de réalisation

1. Authentification.
2. Rôles.
3. Permissions.
4. Tableau de bord.
5. Utilisateurs.
6. KYC.
7. Commerçants.
8. Agents.
9. Transactions.
10. Wallets.
11. Frais.
12. Commissions.
13. Support.
14. Fraude.
15. Finance.
16. Configuration.
17. Partenaires.
18. Appareils.
19. TPE.
20. GAB/DAB.
21. Rapports.
22. Audits.

---

# 33. Design System

Le Design System doit être créé avant la multiplication des écrans.

Il doit définir :

- couleurs ;
- typographie ;
- espacements ;
- boutons ;
- cartes ;
- formulaires ;
- tableaux ;
- icônes ;
- modales ;
- alertes ;
- graphiques ;
- navigation ;
- accessibilité ;
- thème sombre éventuel ;
- animations.

---

# 34. Chantier 6 — Réseau Agent

Livrables :

- modèle Agent ;
- enrôlement ;
- point de vente ;
- contrats ;
- float ;
- caisse ;
- dépôts ;
- retraits ;
- commissions ;
- limites ;
- réapprovisionnement ;
- supervision ;
- fraude ;
- support ;
- rapports.

---

# 35. Réseau Commerce

Livrables :

- commerçants ;
- points de vente ;
- employés ;
- encaissement ;
- QR ;
- remboursements ;
- règlements ;
- factures ;
- promotions ;
- fidélité ;
- rapports ;
- support.

---

# 36. Chantier 7 — TPE

Livrables :

- application TPE ;
- enrôlement ;
- paiement carte ;
- NFC ;
- QR ;
- Mobile Money ;
- impression ;
- remboursement ;
- clôture ;
- mode hors ligne ;
- synchronisation ;
- mise à jour ;
- supervision ;
- maintenance.

---

# 37. Cartes

Livrables :

- partenaire émetteur ;
- programme cartes ;
- cartes physiques ;
- cartes virtuelles ;
- activation ;
- PIN ;
- blocage ;
- limites ;
- tokenisation ;
- autorisation ;
- fraude ;
- rapprochement ;
- support ;
- personnalisation.

---

# 38. GAB/DAB

Livrables :

- spécification matérielle ;
- fournisseur ;
- logiciel ;
- retrait ;
- dépôt ;
- consultation ;
- mini-relevé ;
- carte ;
- QR ;
- code sécurisé ;
- cassettes ;
- billets ;
- HSM ;
- sécurité ;
- maintenance ;
- supervision ;
- rapports ;
- intégration ledger.

---

# 39. Ordre recommandé pour GAB/DAB

1. Choix du modèle.
2. Définition des fonctionnalités.
3. Choix du fournisseur.
4. Intégration logicielle.
5. Connexion backend.
6. Sécurité.
7. HSM.
8. Tests matériels.
9. Tests retrait.
10. Tests dépôt si disponible.
11. Monitoring.
12. Installation pilote.
13. Recette terrain.
14. Mise en service.
15. Extension.

---

# 40. Chantier 8 — Partenaires bancaires

Livrables :

- contrat ;
- compte de cantonnement ;
- API ;
- fichiers ;
- règlement ;
- rapprochement ;
- horaires ;
- certificats ;
- support ;
- incidents ;
- reporting ;
- SLA.

---

# 41. Mobile Money

Livrables :

- connecteur opérateur ;
- dépôt ;
- retrait ;
- transfert ;
- statuts ;
- webhooks ;
- frais ;
- commissions ;
- timeout ;
- retry ;
- rapprochement ;
- rapports.

---

# 42. Réseaux cartes

Livrables :

- sponsor BIN ;
- acquéreur ;
- émetteur ;
- processeur ;
- personnalisation ;
- HSM ;
- autorisation ;
- clearing ;
- settlement ;
- disputes ;
- fraude ;
- certification.

---

# 43. Chantier 9 — Finance

Livrables :

- rapprochement ;
- suspenses ;
- règlement ;
- trésorerie ;
- commissions ;
- revenus ;
- taxes ;
- clôtures ;
- exports ;
- contrôles ;
- reporting ;
- audit.

---

# 44. Fraude

Livrables :

- règles ;
- scoring ;
- alertes ;
- dossiers ;
- investigations ;
- blocage ;
- gel ;
- appareils suspects ;
- transactions suspectes ;
- reporting ;
- audit.

---

# 45. Conformité

Livrables :

- AML ;
- CFT ;
- PEP ;
- sanctions ;
- gel des avoirs ;
- revue KYC ;
- revue KYB ;
- alertes ;
- dossiers ;
- déclarations ;
- preuves ;
- audit.

---

# 46. Support

Livrables :

- tickets ;
- catégories ;
- SLA ;
- assignation ;
- escalade ;
- litiges ;
- remboursements ;
- fraude ;
- chat ;
- base de connaissances ;
- satisfaction ;
- rapports.

---

# 47. Chantier 10 — Infrastructure

Livrables :

- cloud ;
- réseaux ;
- bases ;
- cache ;
- files ;
- stockage ;
- secrets ;
- certificats ;
- CI/CD ;
- logs ;
- métriques ;
- traces ;
- alertes ;
- sauvegardes ;
- PRA ;
- sécurité.

---

# 48. CI/CD

La pipeline doit inclure :

- installation ;
- lint ;
- compilation ;
- validation Prisma ;
- génération ;
- tests ;
- scan ;
- build ;
- artefact ;
- signature ;
- déploiement ;
- smoke test ;
- rollback.

---

# 49. Environnements

Ordre de mise en place :

1. Local.
2. Développement.
3. Test.
4. Démo.
5. Recette.
6. Préproduction.
7. Production.
8. PRA.

---

# 50. Observabilité

À construire avant le pilote :

- logs centralisés ;
- métriques ;
- traces ;
- alertes ;
- dashboards ;
- health checks ;
- statut partenaires ;
- statut ledger ;
- statut paiements ;
- statut agents ;
- statut TPE ;
- statut GAB/DAB.

---

# 51. Sauvegardes

Doivent couvrir :

- bases ;
- ledger ;
- documents ;
- configurations ;
- secrets selon politique ;
- rapports ;
- preuves ;
- stockage ;
- audits.

---

# 52. Chantier 11 — Qualité

Livrables :

- stratégie QA ;
- tests unitaires ;
- tests d’intégration ;
- tests API ;
- tests end-to-end ;
- tests de sécurité ;
- tests de performance ;
- tests réseau faible ;
- tests hors ligne ;
- tests de migration ;
- tests de reprise ;
- non-régression.

---

# 53. Recette

La Recette doit impliquer :

- Produit ;
- Finance ;
- Support ;
- Opérations ;
- Sécurité ;
- Conformité ;
- agents pilotes ;
- commerçants pilotes ;
- partenaires.

---

# 54. Pilote

Configuration indicative :

- 100 à 1 000 clients ;
- 5 à 20 agents ;
- 10 à 50 commerçants ;
- 3 TPE ;
- 1 GAB ;
- 1 banque ;
- 1 opérateur Mobile Money ;
- une zone géographique limitée.

---

# 55. Critères de réussite du pilote

- ledger équilibré ;
- transactions cohérentes ;
- absence de double débit ;
- rapprochement correct ;
- support opérationnel ;
- fraude maîtrisée ;
- agents fonctionnels ;
- commerçants fonctionnels ;
- disponibilité conforme ;
- utilisateurs satisfaits.

---

# 56. Chantier 12 — Lancement

Étapes :

1. pilote interne ;
2. pilote terrain ;
3. lancement limité ;
4. extension Bamako ;
5. grandes villes ;
6. couverture nationale ;
7. extension régionale.

---

# 57. Roadmap indicative

## Phase A — Fondations

Durée indicative : 2 à 4 mois.

Livrables :

- architecture ;
- dépôts ;
- bases ;
- API Gateway ;
- authentification ;
- configuration ;
- CI/CD ;
- monitoring initial.

## Phase B — Socle financier

Durée indicative : 3 à 6 mois.

Livrables :

- ledger ;
- wallet ;
- transfert ;
- frais ;
- commissions ;
- KYC ;
- notifications.

## Phase C — Applications principales

Durée indicative : 4 à 8 mois.

Livrables :

- Client ;
- Commerce ;
- Agent ;
- Admin Web ;
- support initial.

## Phase D — Réseau de paiement

Durée indicative : 4 à 8 mois.

Livrables :

- TPE ;
- Mobile Money ;
- cartes ;
- agents ;
- commerçants ;
- rapprochement.

## Phase E — Pilote

Durée indicative : 1 à 3 mois.

Livrables :

- Recette ;
- formation ;
- tests terrain ;
- correction ;
- validation.

## Phase F — Croissance

Durée continue.

Livrables :

- GAB/DAB ;
- État ;
- entreprises ;
- éducation ;
- Data ;
- IA ;
- multi-pays.

---

# 58. Planning réaliste

Un projet de cette taille ne doit pas être considéré comme terminé en quelques semaines.

Une première version pilote sérieuse peut nécessiter environ :

- 9 à 18 mois avec une équipe expérimentée ;
- davantage si l’équipe est réduite ;
- davantage si les partenariats bancaires prennent du temps ;
- davantage si les cartes et GAB sont inclus dès le départ.

---

# 59. Équipe minimale recommandée

Pour le premier socle :

- 1 Product Manager ;
- 1 Project Manager ;
- 1 Architecte ;
- 2 à 4 développeurs backend ;
- 2 à 4 développeurs mobile ;
- 1 à 2 développeurs web ;
- 1 UX/UI Designer ;
- 1 QA ;
- 1 DevOps ;
- 1 spécialiste sécurité ;
- 1 spécialiste paiement/Finance ;
- 1 spécialiste conformité ;
- 1 support/opérations.

---

# 60. Équipe cible plus complète

Elle peut inclure :

- équipes Client ;
- Commerce ;
- Agent ;
- TPE ;
- Admin ;
- Backend ;
- Ledger ;
- Paiement ;
- Cartes ;
- GAB/DAB ;
- Data ;
- IA ;
- Sécurité ;
- SRE ;
- QA ;
- Support ;
- Finance ;
- Conformité ;
- Opérations ;
- Partenariats.

---

# 61. Responsabilités du fondateur

Le fondateur doit notamment :

- porter la vision ;
- décider des priorités ;
- choisir les partenaires ;
- valider le design ;
- surveiller les coûts ;
- contrôler la gouvernance ;
- suivre le développement ;
- protéger la propriété intellectuelle ;
- préparer les financements ;
- éviter les changements permanents non planifiés.

---

# 62. Responsabilité du Product Manager

- transformer la vision en backlog ;
- définir les fonctionnalités ;
- rédiger les critères d’acceptation ;
- prioriser ;
- coordonner Produit et Technique ;
- valider les démonstrations ;
- préparer les releases.

---

# 63. Responsabilité de l’architecte

- garantir la cohérence ;
- définir les standards ;
- contrôler les dépendances ;
- éviter les doublons ;
- sécuriser la scalabilité ;
- valider les intégrations ;
- gérer la dette technique.

---

# 64. Responsabilité QA

- plans de test ;
- automatisation ;
- non-régression ;
- campagnes ;
- anomalies ;
- rapports ;
- Quality Gates ;
- validation avant release.

---

# 65. Responsabilité DevOps/SRE

- environnements ;
- pipelines ;
- infrastructure ;
- monitoring ;
- sauvegardes ;
- disponibilité ;
- incidents ;
- capacité ;
- coûts ;
- reprise.

---

# 66. Gestion du backlog

Chaque élément doit avoir :

- identifiant ;
- titre ;
- description ;
- priorité ;
- domaine ;
- application ;
- critères d’acceptation ;
- dépendances ;
- estimation ;
- responsable ;
- statut ;
- version cible.

---

# 67. Statuts du backlog

- IDEA ;
- TO_ANALYZE ;
- READY ;
- IN_PROGRESS ;
- IN_REVIEW ;
- IN_TEST ;
- BLOCKED ;
- DONE ;
- RELEASED ;
- CANCELLED.

---

# 68. Définition de Ready

Une tâche est prête lorsqu’elle possède :

- description claire ;
- maquette éventuelle ;
- règles métier ;
- critères d’acceptation ;
- API définie ;
- dépendances identifiées ;
- données définies ;
- risques connus ;
- estimation.

---

# 69. Définition de Done

Une tâche est terminée lorsque :

- code terminé ;
- revue effectuée ;
- tests réussis ;
- sécurité vérifiée ;
- documentation mise à jour ;
- critères validés ;
- logs ajoutés ;
- métriques ajoutées ;
- migration validée ;
- fonctionnalité démontrée.

---

# 70. Dépendances critiques

Exemples :

- les paiements dépendent du ledger ;
- les cartes dépendent du partenaire émetteur ;
- le Mobile Money dépend de l’opérateur ;
- les GAB dépendent du fournisseur matériel ;
- les agents dépendent du Cash Network ;
- la Finance dépend des écritures correctes ;
- la fraude dépend des événements ;
- la Data dépend de la qualité des sources.

---

# 71. Registre des dépendances

Chaque dépendance doit contenir :

- source ;
- cible ;
- responsable ;
- date ;
- risque ;
- statut ;
- blocage ;
- solution temporaire ;
- plan de sortie.

---

# 72. Gestion des risques

Chaque risque doit avoir :

- identifiant ;
- description ;
- probabilité ;
- impact ;
- priorité ;
- propriétaire ;
- mesures ;
- échéance ;
- statut ;
- plan de secours.

---

# 73. Principaux risques

- équipe insuffisante ;
- budget insuffisant ;
- partenaire bancaire lent ;
- retard réglementaire ;
- architecture trop complexe ;
- mauvaise sécurité ;
- dette technique ;
- fraude ;
- mauvaise qualité des données ;
- difficultés de liquidité ;
- réseau faible ;
- faible adoption ;
- coûts GAB/DAB élevés.

---

# 74. Gestion des changements

Toute nouvelle demande importante doit être évaluée selon :

- valeur ;
- urgence ;
- coût ;
- impact ;
- dépendances ;
- sécurité ;
- délai ;
- priorité ;
- version cible ;
- risque de perturber le lancement.

---

# 75. Gel du périmètre

Avant le pilote, un gel partiel du périmètre doit être appliqué.

Seuls peuvent être acceptés :

- corrections ;
- sécurité ;
- conformité ;
- blocages ;
- exigences partenaires obligatoires ;
- anomalies critiques.

---

# 76. Budget

Le budget doit être séparé par postes :

- développement ;
- design ;
- infrastructure ;
- sécurité ;
- conformité ;
- partenaires ;
- cartes ;
- TPE ;
- GAB/DAB ;
- support ;
- formation ;
- marketing ;
- matériel ;
- licences ;
- maintenance ;
- liquidité.

---

# 77. Budget logiciel

Il peut inclure :

- développeurs ;
- QA ;
- DevOps ;
- design ;
- gestion de projet ;
- architecture ;
- sécurité ;
- licences ;
- cloud ;
- outils ;
- tests ;
- audits.

---

# 78. Budget matériel

Il peut inclure :

- smartphones Agent ;
- tablettes ;
- TPE ;
- imprimantes ;
- lecteurs ;
- GAB ;
- DAB ;
- serveurs éventuels ;
- réseau ;
- alimentation ;
- caméras ;
- sécurité physique.

---

# 79. Budget opérationnel

Il peut inclure :

- équipes support ;
- équipes Finance ;
- équipes fraude ;
- maintenance ;
- convoyage ;
- assurance ;
- locaux ;
- formation ;
- communication ;
- déplacement ;
- supervision.

---

# 80. Suivi FinOps

À suivre :

- coût cloud ;
- coût SMS ;
- coût KYC ;
- coût e-mail ;
- coût stockage ;
- coût API ;
- coût par utilisateur ;
- coût par transaction ;
- coût partenaire ;
- coût support ;
- coût matériel.

---

# 81. Financement par étapes

Mansa peut rechercher des financements selon les étapes :

1. Prototype.
2. MVP.
3. Pilote.
4. Lancement.
5. Croissance nationale.
6. Expansion régionale.

---

# 82. Livrables par phase

Chaque phase doit fournir :

- code ;
- application ;
- documentation ;
- tests ;
- rapport ;
- démonstration ;
- validation ;
- décision ;
- budget consommé ;
- risques restants.

---

# 83. Démonstrations

Une démonstration régulière doit présenter :

- fonctions terminées ;
- parcours ;
- anomalies ;
- performances ;
- décisions attendues ;
- prochaines étapes.

---

# 84. Reporting de programme

Le rapport doit contenir :

- avancement ;
- budget ;
- planning ;
- risques ;
- dépendances ;
- qualité ;
- anomalies ;
- décisions ;
- partenaires ;
- prochaines étapes.

---

# 85. Indicateurs de réalisation

Exemples :

- fonctionnalités terminées ;
- tâches livrées ;
- taux de tests ;
- anomalies ;
- vitesse ;
- budget consommé ;
- retard ;
- disponibilité équipe ;
- qualité ;
- dette technique.

---

# 86. Indicateurs produit

- inscriptions ;
- KYC validés ;
- utilisateurs actifs ;
- transactions ;
- valeur ;
- agents ;
- commerçants ;
- TPE ;
- GAB/DAB ;
- revenus ;
- satisfaction ;
- rétention.

---

# 87. Gestion de la documentation

Chaque livraison doit mettre à jour :

- cahier des charges ;
- API ;
- architecture ;
- base ;
- règles métier ;
- procédures ;
- tests ;
- release notes ;
- guide utilisateur ;
- guide support ;
- runbook.

---

# 88. Formation avant pilote

Doivent être formés :

- support ;
- agents ;
- commerçants ;
- administrateurs ;
- Finance ;
- fraude ;
- techniciens TPE ;
- techniciens GAB ;
- partenaires.

---

# 89. Préparation opérationnelle

Avant pilote :

- support prêt ;
- procédures prêtes ;
- cash disponible ;
- float disponible ;
- partenaires prêts ;
- monitoring actif ;
- sauvegardes testées ;
- incidents simulés ;
- équipe d’astreinte prête.

---

# 90. Préparation réglementaire

À vérifier :

- statut juridique ;
- licences ;
- partenariat bancaire ;
- KYC ;
- AML/CFT ;
- protection des données ;
- contrats ;
- sécurité ;
- conservation ;
- déclarations ;
- audits.

---

# 91. Propriété intellectuelle

Mansa doit conserver :

- droits sur le code ;
- droits sur le design ;
- documentation ;
- marques ;
- domaines ;
- comptes développeurs ;
- clés de signature ;
- dépôts ;
- accès cloud ;
- contrats prestataires.

---

# 92. Développement externe

Tout prestataire doit avoir :

- contrat ;
- périmètre ;
- confidentialité ;
- propriété intellectuelle ;
- accès limité ;
- livrables ;
- documentation ;
- tests ;
- transfert de compétences ;
- révocation des accès.

---

# 93. Utilisation de l’IA pour coder

L’IA peut aider à :

- générer ;
- expliquer ;
- tester ;
- documenter ;
- corriger ;
- refactoriser ;
- créer des maquettes ;
- préparer des migrations.

Mais toute production doit être :

- relue ;
- testée ;
- sécurisée ;
- intégrée proprement ;
- versionnée ;
- validée.

---

# 94. Règle de travail avec Codex ou une IA

Chaque mission doit préciser :

- dépôt ;
- branche ;
- périmètre ;
- fichiers autorisés ;
- résultat attendu ;
- tests ;
- interdictions ;
- commande de validation ;
- commit attendu ;
- rapport final.

---

# 95. Protection du code existant

Avant chaque mission :

- vérifier Git ;
- créer une branche ;
- sauvegarder ;
- limiter les fichiers ;
- éviter les réécritures globales ;
- exécuter les tests ;
- comparer les changements ;
- valider avant fusion.

---

# 96. Stratégie de branches

Exemple :

```text
main
→ version stable

develop
→ intégration

feature/*
→ nouvelle fonction

fix/*
→ correction

release/*
→ préparation d’une version

hotfix/*
→ urgence Production
```

---

# 97. Pull Requests

Chaque PR doit avoir :

- titre ;
- description ;
- périmètre ;
- captures éventuelles ;
- tests ;
- risques ;
- migration ;
- documentation ;
- reviewer ;
- validation CI.

---

# 98. Fusion

Une fusion doit être interdite si :

- build en échec ;
- tests critiques en échec ;
- secret détecté ;
- conflit ;
- absence de revue ;
- migration non validée ;
- vulnérabilité critique ;
- documentation obligatoire absente.

---

# 99. Release mobile

Étapes :

- version ;
- build ;
- tests ;
- signature ;
- store ;
- validation ;
- publication progressive ;
- monitoring ;
- communication ;
- rollback fonctionnel si nécessaire.

---

# 100. Release backend

Étapes :

- build ;
- tests ;
- migration ;
- scan ;
- artefact ;
- déploiement ;
- smoke tests ;
- monitoring ;
- validation ;
- rollback.

---

# 101. Lancement du réseau GAB/DAB

Le GAB/DAB ne doit pas bloquer le lancement initial de Mansa.

Ordre conseillé :

1. lancer les wallets ;
2. lancer les Agents ;
3. lancer les commerçants ;
4. lancer les TPE ;
5. stabiliser les flux ;
6. intégrer le premier GAB ;
7. tester ;
8. étendre progressivement ;
9. ajouter les DAB de retrait ;
10. ajouter les GAB avec dépôt.

---

# 102. Premier GAB recommandé

Le premier GAB peut proposer :

- retrait avec carte ;
- retrait sans carte ;
- consultation du solde ;
- mini-relevé ;
- changement PIN ;
- reçus ;
- langues ;
- supervision ;
- alertes ;
- gestion des billets.

Le dépôt peut être ajouté si le budget et le matériel le permettent.

---

# 103. Déploiement des DAB

Les DAB peuvent être déployés ensuite dans :

- marchés ;
- stations-service ;
- centres commerciaux ;
- universités ;
- hôpitaux ;
- gares ;
- aéroports ;
- grandes boutiques ;
- agences partenaires.

---

# 104. Déploiement des GAB

Les GAB complets sont recommandés dans :

- agences Mansa ;
- agences partenaires ;
- centres commerciaux majeurs ;
- quartiers d’affaires ;
- universités principales ;
- administrations ;
- capitales régionales ;
- grandes zones commerciales.

---

# 105. Passage à la phase applicative détaillée

Après validation du présent document, la documentation doit continuer avec les cahiers des charges détaillés des applications.

Ordre recommandé :

1. Application Client.
2. Application Commerce.
3. Application Agent.
4. Application TPE.
5. Logiciel GAB/DAB.
6. Admin Lite.
7. Admin Web.
8. Site vitrine.
9. Portail Développeurs.
10. Portail Entreprises.
11. Portail Éducation.
12. Portail Institutions.
13. Centre Support.
14. Back-office Finance.
15. Back-office Fraude.
16. Back-office Data.
17. Jini.

---

# 106. Administration du programme

L’administration doit pouvoir gérer :

- phases ;
- lots ;
- équipes ;
- tâches ;
- dépendances ;
- risques ;
- budgets ;
- livrables ;
- validations ;
- versions ;
- partenaires ;
- décisions ;
- documents ;
- rapports ;
- audits.

---

# 107. Rôles

Exemples :

```text
PROGRAM_DIRECTOR
PRODUCT_DIRECTOR
TECHNICAL_DIRECTOR
PROJECT_MANAGER
PRODUCT_MANAGER
ARCHITECT
ENGINEERING_MANAGER
QA_MANAGER
SECURITY_MANAGER
FINANCE_MANAGER
COMPLIANCE_MANAGER
OPERATIONS_MANAGER
PARTNERSHIP_MANAGER
RELEASE_MANAGER
AUDITOR
VIEWER
```

---

# 108. Permissions

Exemples :

```text
program.read
program.manage
roadmap.read
roadmap.manage
budget.read
budget.manage
risk.read
risk.manage
delivery.approve
phase.start
phase.complete
release.approve
pilot.approve
report.read
audit.read
```

---

# 109. Approbations

Peuvent nécessiter une approbation :

- changement de périmètre ;
- augmentation de budget ;
- changement d’architecture ;
- changement de partenaire ;
- report de lancement ;
- passage en pilote ;
- passage en Production ;
- déploiement GAB ;
- ouverture d’un nouveau pays.

---

# 110. Audit

Le journal doit contenir :

- utilisateur ;
- rôle ;
- programme ;
- phase ;
- lot ;
- action ;
- budget ;
- décision ;
- date ;
- heure ;
- ancienne valeur ;
- nouvelle valeur ;
- motif ;
- approbateur ;
- résultat.

---

# 111. Tests du programme

Le plan directeur doit être vérifié sur :

- cohérence des dépendances ;
- disponibilité des équipes ;
- faisabilité ;
- budget ;
- planning ;
- risques ;
- qualité ;
- conformité ;
- sécurité ;
- capacité opérationnelle ;
- capacité de lancement ;
- montée en charge.

---

# 112. Règles métier

1. Le ledger est construit avant les flux financiers réels.
2. Les fonctions P0 sont prioritaires.
3. Le GAB/DAB ne bloque pas le MVP.
4. Toute phase possède des livrables.
5. Toute tâche possède des critères d’acceptation.
6. Toute dépendance critique est suivie.
7. Tout risque possède un propriétaire.
8. Toute release est testée.
9. Aucun pilote sans sécurité et monitoring.
10. Aucun lancement sans support.
11. Les changements importants sont approuvés.
12. Les documents sont mis à jour.
13. Les prestataires ont des accès limités.
14. La propriété intellectuelle appartient à Mansa.
15. Les branches protègent le code stable.
16. Les PR doivent être revues.
17. Les tests critiques bloquent la fusion.
18. Les coûts sont suivis.
19. Le pilote est limité.
20. Le lancement est progressif.
21. Les GAB/DAB sont déployés progressivement.
22. Chaque nouveau pays commence par une étude et un pilote.
23. Le fondateur garde la maîtrise des priorités.
24. Le demandeur ne valide pas seul une décision critique.
25. Les audits sont immuables.

---

# 113. Critères d’acceptation

Le Plan directeur complet de réalisation du projet Mansa est validé lorsque :

- le programme est découpé en chantiers ;
- les priorités P0 à P4 sont définies ;
- le MVP est identifié ;
- les fondations techniques sont identifiées ;
- le ledger est priorisé ;
- le Wallet est priorisé ;
- les applications principales sont ordonnées ;
- le Design System est prévu ;
- le réseau Agent est planifié ;
- le réseau Commerce est planifié ;
- le TPE est planifié ;
- les cartes sont planifiées ;
- le GAB/DAB est planifié ;
- les partenaires bancaires sont planifiés ;
- Mobile Money est planifié ;
- la Finance est planifiée ;
- la fraude est planifiée ;
- la conformité est planifiée ;
- le support est planifié ;
- l’infrastructure est planifiée ;
- la CI/CD est planifiée ;
- l’observabilité est planifiée ;
- les sauvegardes sont planifiées ;
- la QA est planifiée ;
- la Recette est planifiée ;
- le pilote est structuré ;
- le lancement est structuré ;
- la roadmap est définie ;
- les délais indicatifs sont définis ;
- l’équipe minimale est définie ;
- l’équipe cible est définie ;
- les responsabilités sont définies ;
- le backlog est structuré ;
- la définition de Ready existe ;
- la définition de Done existe ;
- les dépendances sont suivies ;
- les risques sont suivis ;
- les changements sont contrôlés ;
- le gel du périmètre est prévu ;
- les budgets sont séparés ;
- les coûts sont suivis ;
- les financements peuvent être organisés par étapes ;
- les livrables sont définis ;
- le reporting est défini ;
- les indicateurs sont définis ;
- la documentation est intégrée ;
- la formation est prévue ;
- l’opérationnel est préparé ;
- le réglementaire est préparé ;
- la propriété intellectuelle est protégée ;
- les prestataires sont encadrés ;
- l’usage de l’IA est encadré ;
- le code existant est protégé ;
- les branches sont définies ;
- les Pull Requests sont contrôlées ;
- les releases sont contrôlées ;
- le lancement GAB/DAB est progressif ;
- le premier GAB est défini ;
- les DAB sont planifiés ;
- les GAB complets sont planifiés ;
- l’ordre des applications détaillées est défini ;
- les rôles et permissions sont définis ;
- les approbations critiques sont protégées ;
- les audits sont immuables.
