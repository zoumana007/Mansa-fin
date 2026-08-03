# 82 — Référentiel final et matrice globale du projet Mansa : périmètre complet, dépendances, priorités, règles transversales, gouvernance, validation finale et passage à l’exécution

## 1. Objet du document

Ce document constitue le **référentiel final du projet Mansa**.

Il rassemble, structure et relie l’ensemble des modules, applications, services, règles métier, architectures, responsabilités et critères d’acceptation définis dans la documentation du projet.

Il doit servir de référence commune pour :

- le fondateur ;
- la direction ;
- les équipes Produit ;
- les développeurs ;
- les architectes ;
- les designers ;
- les équipes QA ;
- les équipes Sécurité ;
- les équipes Finance ;
- les équipes Conformité ;
- les équipes Opérations ;
- les partenaires bancaires ;
- les opérateurs Mobile Money ;
- les fabricants de TPE ;
- les fournisseurs GAB/DAB ;
- les institutions ;
- les investisseurs ;
- les prestataires ;
- les outils d’intelligence artificielle chargés de participer à la réalisation.

Ce document définit notamment :

- le périmètre final ;
- les applications ;
- les portails ;
- les services backend ;
- les infrastructures ;
- les intégrations ;
- les priorités ;
- les dépendances ;
- les responsabilités ;
- les règles transversales ;
- les étapes de réalisation ;
- les étapes de validation ;
- les conditions du pilote ;
- les conditions de Production ;
- les critères de réussite ;
- le passage de la documentation à l’exécution.

---

# 2. Vision finale de Mansa

Mansa doit devenir une plateforme financière complète capable de connecter :

- les particuliers ;
- les commerçants ;
- les Agents ;
- les entreprises ;
- les établissements scolaires ;
- les administrations ;
- les banques ;
- les opérateurs Mobile Money ;
- les réseaux cartes ;
- les partenaires techniques ;
- les investisseurs ;
- les développeurs.

---

# 3. Objectif fonctionnel

Mansa doit permettre notamment :

- créer un compte ;
- vérifier une identité ;
- conserver une valeur financière ;
- consulter un solde ;
- effectuer un transfert ;
- effectuer un paiement ;
- déposer des espèces ;
- retirer des espèces ;
- utiliser une carte ;
- utiliser un TPE ;
- utiliser un GAB ou DAB ;
- payer une facture ;
- recevoir un salaire ;
- recevoir une bourse ;
- régler des services publics ;
- gérer un commerce ;
- gérer une entreprise ;
- utiliser des API ;
- consulter des rapports ;
- recevoir de l’assistance.

---

# 4. Objectif stratégique

Mansa doit progressivement pouvoir :

- se lancer au Mali ;
- établir un pilote contrôlé ;
- travailler avec une banque partenaire ;
- s’intégrer aux opérateurs Mobile Money ;
- équiper les commerçants ;
- développer un réseau Agent ;
- déployer des TPE ;
- déployer des GAB/DAB ;
- collaborer avec l’État ;
- collaborer avec les écoles ;
- servir les entreprises ;
- s’étendre dans d’autres pays.

---

# 5. Principes fondamentaux globaux

1. Le ledger est la source de vérité financière.
2. Toute opération financière possède une référence unique.
3. Toute opération critique est idempotente.
4. Aucun frais ne doit être caché.
5. Les fonctions doivent être administrables.
6. Les actions critiques doivent être confirmées.
7. Les permissions doivent être limitées.
8. Les changements doivent être audités.
9. Les applications ne doivent pas accéder directement aux bases.
10. Les partenaires doivent être abstraits par des connecteurs.
11. La sécurité doit être intégrée dès la conception.
12. Le lancement doit être progressif.
13. Toute mise en Production doit être réversible.
14. Les données sensibles doivent être minimisées.
15. Les audits critiques doivent être immuables.

---

# 6. Applications mobiles officielles

Les applications mobiles principales sont :

1. Application Client.
2. Application Commerce.
3. Application Agent.
4. Application Admin Lite.
5. Application Annuaire ou Hub de services, si maintenue comme application distincte.

---

# 7. Application Client

Elle doit couvrir :

- onboarding ;
- inscription ;
- connexion ;
- KYC ;
- wallet ;
- solde ;
- historique ;
- transfert ;
- paiement ;
- QR ;
- NFC ;
- dépôt ;
- retrait ;
- cartes ;
- factures ;
- épargne ;
- budgets ;
- abonnements ;
- fidélité ;
- cashback ;
- localisation ;
- support ;
- Jini ;
- sécurité ;
- profil.

---

# 8. Application Commerce

Elle doit couvrir :

- inscription ;
- KYB ;
- points de vente ;
- caisses ;
- employés ;
- encaissements ;
- QR ;
- paiements ;
- remboursements ;
- annulations ;
- catalogue ;
- stock ;
- clients ;
- fidélité ;
- promotions ;
- règlements ;
- rapports ;
- TPE ;
- support.

---

# 9. Application Agent

Elle doit couvrir :

- enrôlement ;
- identité ;
- appareil ;
- ouverture de caisse ;
- float ;
- dépôts ;
- retraits ;
- commissions ;
- cash ;
- réapprovisionnement ;
- clôture ;
- incidents ;
- support ;
- rapports.

---

# 10. Application Admin Lite

Elle doit permettre aux utilisateurs autorisés de consulter et traiter certaines fonctions administratives depuis un mobile.

Elle peut couvrir :

- alertes ;
- utilisateurs ;
- KYC ;
- Agents ;
- commerçants ;
- incidents ;
- support ;
- validation simple ;
- supervision ;
- notifications ;
- rapports synthétiques.

---

# 11. Application TPE

Elle doit couvrir :

- enrôlement ;
- connexion employé ;
- caisse ;
- paiement carte ;
- NFC ;
- QR ;
- Mobile Money ;
- Tap to Pay ;
- préautorisation ;
- pourboire ;
- split payment ;
- remboursement ;
- annulation ;
- impression ;
- clôture ;
- hors ligne ;
- synchronisation ;
- sécurité ;
- supervision ;
- maintenance.

---

# 12. Logiciel GAB/DAB

Il doit couvrir :

- retrait avec carte ;
- retrait sans carte ;
- consultation du solde ;
- mini-relevé ;
- changement PIN ;
- dépôt ;
- recyclage ;
- facture ;
- recharge ;
- transfert ;
- reçus ;
- cassettes ;
- billets ;
- sécurité ;
- alarmes ;
- maintenance ;
- réconciliation.

---

# 13. Portails web officiels

Les portails principaux sont :

- Admin Web ;
- Portail Commerçant ;
- Site Public ;
- Portail Développeurs ;
- Portail Entreprises ;
- Portail Éducation ;
- Portail Institutions ;
- Centre Support ;
- Back-office Finance ;
- Back-office Fraude ;
- Back-office Data.

---

# 14. Admin Web

Il doit permettre une administration complète de :

- utilisateurs ;
- KYC ;
- KYB ;
- Agents ;
- commerçants ;
- entreprises ;
- transactions ;
- wallets ;
- ledger ;
- cartes ;
- TPE ;
- GAB/DAB ;
- partenaires ;
- frais ;
- commissions ;
- plafonds ;
- sécurité ;
- fraude ;
- support ;
- contenu ;
- configuration ;
- pays ;
- audits.

---

# 15. Portail Commerçant

Il doit permettre :

- gestion multi-entreprises ;
- gestion multi-sites ;
- employés ;
- transactions ;
- remboursements ;
- règlements ;
- catalogue ;
- stock ;
- commandes ;
- factures ;
- clients ;
- fidélité ;
- promotions ;
- TPE ;
- API ;
- rapports ;
- exports ;
- support.

---

# 16. Site Public

Il doit permettre :

- présentation de Mansa ;
- présentation des produits ;
- téléchargement des applications ;
- consultation des tarifs ;
- consultation des chiffres clés ;
- présentation de la sécurité ;
- présentation des partenaires ;
- recrutement ;
- investisseurs ;
- actualités ;
- support ;
- demandes commerciales ;
- statut des services ;
- pages légales.

---

# 17. Portail Développeurs

Il doit permettre :

- création de compte ;
- création d’organisation ;
- création d’application ;
- clés API ;
- Sandbox ;
- API Explorer ;
- webhooks ;
- SDK ;
- documentation ;
- changelog ;
- passage en Production ;
- support technique ;
- suivi des quotas ;
- audits.

---

# 18. Portail Entreprises

Il doit permettre :

- comptes professionnels ;
- employés ;
- rôles ;
- dépenses ;
- cartes ;
- validations ;
- salaires ;
- fournisseurs ;
- factures ;
- budgets ;
- rapports ;
- API ;
- intégrations comptables.

---

# 19. Portail Éducation

Il doit permettre :

- établissements ;
- étudiants ;
- cartes étudiantes ;
- inscriptions ;
- paiements ;
- bourses ;
- restauration ;
- transport ;
- bibliothèque ;
- rapports ;
- administration ;
- support.

---

# 20. Portail Institutions

Il doit permettre :

- services publics ;
- agents publics ;
- amendes ;
- taxes ;
- aides ;
- bourses ;
- recouvrement ;
- paiements ;
- rapports ;
- traçabilité ;
- audit ;
- lutte contre la corruption.

---

# 21. Centre Support

Il doit permettre :

- tickets ;
- conversations ;
- SLA ;
- catégories ;
- escalades ;
- litiges ;
- remboursements ;
- fraude ;
- pièces ;
- base de connaissances ;
- satisfaction ;
- rapports.

---

# 22. Back-office Finance

Il doit permettre :

- rapprochement ;
- règlements ;
- comptes ;
- trésorerie ;
- suspenses ;
- commissions ;
- revenus ;
- taxes ;
- clôtures ;
- corrections contrôlées ;
- rapports ;
- audits.

---

# 23. Back-office Fraude

Il doit permettre :

- alertes ;
- règles ;
- scores ;
- dossiers ;
- blocages ;
- gel ;
- appareils suspects ;
- Agents suspects ;
- commerçants suspects ;
- cartes suspectes ;
- TPE suspects ;
- GAB suspects ;
- enquêtes ;
- décisions ;
- rapports.

---

# 24. Back-office Data

Il doit permettre :

- sources ;
- pipelines ;
- qualité ;
- catalogues ;
- lineage ;
- modèles ;
- rapports ;
- accès ;
- anonymisation ;
- gouvernance ;
- alertes ;
- coûts.

---

# 25. Services backend fondamentaux

Les services principaux doivent inclure :

- Identity Service ;
- User Service ;
- KYC Service ;
- KYB Service ;
- Wallet Service ;
- Ledger Service ;
- Payment Service ;
- Transfer Service ;
- Card Service ;
- Merchant Service ;
- Agent Service ;
- TPE Service ;
- ATM Service ;
- Finance Service ;
- Fraud Service ;
- Compliance Service ;
- Notification Service ;
- Support Service ;
- Configuration Service ;
- Document Service ;
- Reporting Service ;
- Data Service ;
- Jini Service.

---

# 26. Identity Service

Il gère :

- authentification ;
- rôles ;
- permissions ;
- sessions ;
- appareils ;
- MFA ;
- passkeys ;
- tokens ;
- révocation ;
- certificats ;
- récupération.

---

# 27. User Service

Il gère :

- profils ;
- coordonnées ;
- adresses ;
- préférences ;
- langues ;
- pays ;
- statuts ;
- relations ;
- historique.

---

# 28. KYC Service

Il gère :

- niveaux ;
- documents ;
- selfie ;
- biométrie ;
- fournisseurs ;
- revues ;
- expiration ;
- statut ;
- audit.

---

# 29. KYB Service

Il gère :

- entreprises ;
- représentants ;
- bénéficiaires effectifs ;
- documents ;
- licences ;
- statut ;
- risque ;
- validation ;
- audit.

---

# 30. Wallet Service

Il gère :

- wallets ;
- devises ;
- statuts ;
- soldes calculés ;
- réservations ;
- limites ;
- gel ;
- blocage ;
- relation ledger.

---

# 31. Ledger Service

Il gère :

- comptes ;
- écritures ;
- débits ;
- crédits ;
- réservations ;
- compensations ;
- reversals ;
- clôtures ;
- références ;
- réconciliation ;
- audit.

---

# 32. Payment Service

Il gère :

- paiements ;
- moyens ;
- autorisations ;
- captures ;
- annulations ;
- remboursements ;
- frais ;
- commissions ;
- partenaires ;
- statuts.

---

# 33. Transfer Service

Il gère :

- Mansa à Mansa ;
- banque ;
- Mobile Money ;
- international ;
- bénéficiaires ;
- limites ;
- conformité ;
- frais ;
- statuts.

---

# 34. Card Service

Il gère :

- cartes physiques ;
- cartes virtuelles ;
- cartes temporaires ;
- cartes jetables ;
- activation ;
- PIN ;
- tokenisation ;
- limites ;
- blocage ;
- opposition ;
- autorisation ;
- remplacement.

---

# 35. Merchant Service

Il gère :

- organisations ;
- points de vente ;
- employés ;
- caisses ;
- catalogue ;
- stock ;
- commandes ;
- factures ;
- promotions ;
- fidélité ;
- règlements.

---

# 36. Agent Service

Il gère :

- Agents ;
- points de vente ;
- float ;
- cash ;
- caisses ;
- dépôt ;
- retrait ;
- commissions ;
- réapprovisionnement ;
- incidents.

---

# 37. TPE Service

Il gère :

- terminaux ;
- enrôlement ;
- certificats ;
- versions ;
- paiements ;
- hors ligne ;
- périphériques ;
- synchronisation ;
- alertes ;
- maintenance.

---

# 38. ATM Service

Il gère :

- GAB ;
- DAB ;
- emplacements ;
- transactions ;
- cassettes ;
- billets ;
- retraits ;
- dépôts ;
- cash ;
- alarmes ;
- maintenance ;
- sécurité.

---

# 39. Finance Service

Il gère :

- frais ;
- commissions ;
- règlements ;
- rapprochement ;
- comptes techniques ;
- suspenses ;
- trésorerie ;
- rapports ;
- clôtures.

---

# 40. Fraud Service

Il gère :

- règles ;
- signaux ;
- scoring ;
- alertes ;
- décisions ;
- dossiers ;
- blocages ;
- investigations ;
- listes ;
- rapports.

---

# 41. Compliance Service

Il gère :

- AML/CFT ;
- PEP ;
- sanctions ;
- screening ;
- risques ;
- revues ;
- déclarations ;
- gel ;
- politiques ;
- preuves.

---

# 42. Notification Service

Il gère :

- push ;
- SMS ;
- e-mail ;
- modèles ;
- langues ;
- préférences ;
- retries ;
- coûts ;
- statut.

---

# 43. Configuration Service

Il gère :

- pays ;
- devises ;
- langues ;
- frais ;
- commissions ;
- limites ;
- partenaires ;
- feature flags ;
- contenus ;
- versions ;
- dates d’effet.

---

# 44. Document Service

Il gère :

- KYC ;
- KYB ;
- contrats ;
- reçus ;
- factures ;
- rapports ;
- preuves ;
- stockage ;
- accès ;
- chiffrement ;
- rétention.

---

# 45. Reporting Service

Il gère :

- rapports synchrones ;
- rapports asynchrones ;
- exports ;
- indicateurs ;
- périodes ;
- filtres ;
- programmations ;
- accès.

---

# 46. Jini Service

Il gère :

- conversations ;
- intentions ;
- connaissances ;
- recherche ;
- outils ;
- permissions ;
- confirmations ;
- historiques ;
- sécurité ;
- escalades.

---

# 47. Partenaires bancaires

L’intégration bancaire doit couvrir :

- comptes de cantonnement ;
- comptes techniques ;
- API ;
- fichiers ;
- transferts ;
- règlements ;
- rapprochement ;
- incidents ;
- SLA ;
- reporting ;
- sécurité.

---

# 48. Mobile Money

L’intégration doit couvrir :

- opérateurs ;
- dépôt ;
- retrait ;
- transfert ;
- paiement ;
- webhooks ;
- frais ;
- commissions ;
- limites ;
- retries ;
- rapprochement.

---

# 49. Réseaux cartes

L’intégration doit couvrir :

- sponsor BIN ;
- émetteur ;
- acquéreur ;
- processeur ;
- HSM ;
- personnalisation ;
- autorisation ;
- clearing ;
- settlement ;
- disputes ;
- fraude ;
- certification.

---

# 50. Fabricants TPE

Le projet doit pouvoir travailler avec plusieurs fabricants.

Le logiciel ne doit pas dépendre exclusivement :

- d’un modèle ;
- d’un SDK ;
- d’un fournisseur ;
- d’un pays ;
- d’un réseau.

---

# 51. Fournisseurs GAB/DAB

Le projet doit encadrer :

- achat ;
- location ;
- installation ;
- logiciel ;
- firmware ;
- sécurité ;
- pièces ;
- maintenance ;
- garantie ;
- formation ;
- supervision ;
- remplacement.

---

# 52. Architecture globale

```text
Applications
→ CDN / WAF
→ API Gateway
→ Services métier
→ Ledger et bases
→ Event Bus
→ Partenaires
→ Data Platform
→ Observabilité
→ Administration
```

---

# 53. API Gateway

Elle doit gérer :

- routage ;
- authentification ;
- autorisation ;
- quotas ;
- rate limiting ;
- sécurité ;
- versions ;
- logs ;
- corrélation ;
- monitoring.

---

# 54. Communication interservices

Elle peut utiliser :

- REST ;
- gRPC ;
- événements ;
- files ;
- commandes asynchrones.

---

# 55. Event Bus

Il doit transporter les événements métier de façon :

- fiable ;
- versionnée ;
- traçable ;
- rejouable lorsque nécessaire ;
- compatible avec les consommateurs multiples.

---

# 56. Files de messages

Elles doivent gérer :

- tâches asynchrones ;
- retries ;
- délais ;
- priorités ;
- DLQ ;
- reprise ;
- monitoring.

---

# 57. Base transactionnelle

PostgreSQL peut être utilisé comme base principale pour :

- utilisateurs ;
- wallets ;
- ledger ;
- paiements ;
- transferts ;
- cartes ;
- Agents ;
- commerçants ;
- support ;
- configurations ;
- audits.

---

# 58. Cache

Redis peut être utilisé pour :

- sessions ;
- cache ;
- verrous ;
- rate limiting ;
- compteurs ;
- données temporaires ;
- configuration.

---

# 59. Stockage objet

Il doit stocker :

- documents ;
- images ;
- rapports ;
- contrats ;
- reçus ;
- exports ;
- preuves ;
- médias ;
- sauvegardes.

---

# 60. Recherche

Un moteur de recherche peut indexer :

- transactions ;
- utilisateurs ;
- commerçants ;
- Agents ;
- tickets ;
- documents ;
- logs ;
- articles.

---

# 61. Data Platform

Elle doit permettre :

- ingestion ;
- nettoyage ;
- transformation ;
- qualité ;
- stockage ;
- reporting ;
- modèles ;
- gouvernance ;
- lineage ;
- anonymisation.

---

# 62. Multi-pays

Chaque pays doit disposer de :

- configuration ;
- devise ;
- langues ;
- KYC ;
- KYB ;
- frais ;
- commissions ;
- limites ;
- partenaires ;
- produits ;
- support ;
- règles ;
- rapports.

---

# 63. Multi-devises

La plateforme doit distinguer :

- devise du wallet ;
- devise de paiement ;
- devise du client ;
- devise de règlement ;
- devise comptable ;
- taux ;
- frais ;
- conversion.

---

# 64. Multi-entités

La plateforme doit supporter :

- utilisateurs individuels ;
- entreprises ;
- groupes ;
- filiales ;
- franchises ;
- institutions ;
- écoles ;
- partenaires ;
- équipes internes.

---

# 65. Multi-environnements

Les environnements officiels sont :

- LOCAL ;
- DEVELOPMENT ;
- TEST ;
- DEMO ;
- RECETTE ;
- SANDBOX ;
- PREPRODUCTION ;
- PRODUCTION ;
- SECURITY ;
- PERFORMANCE ;
- DISASTER_RECOVERY.

---

# 66. Séparation des environnements

Chaque environnement doit posséder :

- données ;
- bases ;
- secrets ;
- clés ;
- certificats ;
- partenaires ;
- logs ;
- accès ;
- configurations séparés.

---

# 67. Priorités P0

Fonctions indispensables :

- authentification ;
- KYC ;
- wallet ;
- ledger ;
- solde ;
- transfert ;
- dépôt Agent ;
- retrait Agent ;
- paiement QR ;
- encaissement Commerce ;
- frais ;
- commissions ;
- notifications ;
- support ;
- Admin Web ;
- monitoring ;
- sécurité ;
- audit.

---

# 68. Priorités P1

Fonctions essentielles après le socle :

- TPE ;
- Mobile Money ;
- cartes ;
- rapprochement ;
- fraude ;
- Finance ;
- portail commerçant ;
- facturation ;
- règlements ;
- rapports ;
- fidélité simple.

---

# 69. Priorités P2

Fonctions de croissance :

- GAB/DAB ;
- entreprises ;
- écoles ;
- institutions ;
- services État ;
- Data avancée ;
- Jini avancé ;
- multi-devises ;
- multi-pays ;
- API avancées.

---

# 70. Priorités P3

Évolutions possibles :

- crédit ;
- assurance ;
- marketplace ;
- investissement ;
- fidélité avancée ;
- recommandations avancées ;
- expansion internationale ;
- nouveaux produits.

---

# 71. Ordre de construction recommandé

```text
Architecture et sécurité
→ Identité et KYC
→ Ledger et Wallet
→ Paiements et transferts
→ Client
→ Agent
→ Commerce
→ Admin
→ Mobile Money
→ TPE
→ Cartes
→ Finance et fraude
→ Pilote
→ GAB/DAB
→ Entreprises et institutions
→ Multi-pays
```

---

# 72. Dépendance Ledger

Dépendent du ledger :

- wallets ;
- paiements ;
- transferts ;
- dépôts ;
- retraits ;
- cartes ;
- TPE ;
- GAB/DAB ;
- commissions ;
- règlements ;
- remboursements ;
- Finance.

---

# 73. Dépendance KYC

Dépendent du KYC :

- limites ;
- transfert ;
- carte ;
- retrait ;
- dépôt ;
- international ;
- crédit ;
- entreprise ;
- conformité.

---

# 74. Dépendance KYB

Dépendent du KYB :

- Commerce ;
- Agent professionnel ;
- Entreprise ;
- Institution ;
- portail commerçant ;
- TPE ;
- règlements ;
- API Production.

---

# 75. Dépendance Partenaires

Dépendent des partenaires :

- cartes ;
- Mobile Money ;
- transfert bancaire ;
- GAB ;
- DAB ;
- Apple Wallet ;
- Google Wallet ;
- paiements internationaux ;
- certaines vérifications KYC.

---

# 76. Dépendance Infrastructure

Dépendent de l’infrastructure :

- applications ;
- APIs ;
- bases ;
- observabilité ;
- sécurité ;
- sauvegardes ;
- reprise ;
- scaling ;
- Production.

---

# 77. Dépendance Support

Aucun lancement public ne doit avoir lieu sans :

- support ;
- base de connaissances ;
- tickets ;
- procédures ;
- contacts ;
- escalades ;
- suivi des incidents.

---

# 78. Dépendance Finance

Aucun flux réel ne doit être ouvert sans :

- comptes ;
- rapprochement ;
- frais ;
- commissions ;
- règlements ;
- rapports ;
- procédures ;
- responsables.

---

# 79. Dépendance Conformité

Aucun produit ne doit être activé sans :

- règles pays ;
- niveau KYC ;
- limites ;
- screening ;
- surveillance ;
- conservation ;
- procédures ;
- validation.

---

# 80. Design System global

Il doit être commun aux applications et portails.

Il doit définir :

- couleurs ;
- typographie ;
- boutons ;
- formulaires ;
- cartes ;
- tableaux ;
- graphiques ;
- icônes ;
- navigation ;
- erreurs ;
- modales ;
- animations ;
- accessibilité.

---

# 81. Design moderne

Le design doit donner une impression :

- technologique ;
- fiable ;
- professionnelle ;
- africaine sans caricature ;
- accessible ;
- premium ;
- simple ;
- cohérente.

---

# 82. Administration centralisée

Le Super Admin doit pouvoir gérer :

- modules ;
- pays ;
- langues ;
- frais ;
- commissions ;
- plafonds ;
- partenaires ;
- applications ;
- versions ;
- cartes ;
- TPE ;
- GAB/DAB ;
- Agents ;
- commerçants ;
- contenus ;
- sécurité ;
- audits.

---

# 83. Feature Flags

Chaque grande fonction doit pouvoir être activée selon :

- pays ;
- ville ;
- utilisateur ;
- segment ;
- niveau KYC ;
- organisation ;
- appareil ;
- application ;
- version ;
- partenaire ;
- pourcentage.

---

# 84. Kill Switches

Des arrêts d’urgence doivent exister pour :

- transfert ;
- paiement ;
- retrait ;
- dépôt ;
- carte ;
- Mobile Money ;
- TPE ;
- GAB/DAB ;
- partenaire ;
- pays ;
- type d’opération.

---

# 85. Frais

Les frais doivent être :

- configurables ;
- versionnés ;
- datés ;
- simulables ;
- affichés ;
- auditables ;
- approuvés ;
- liés au ledger.

---

# 86. Commissions

Les commissions peuvent être réparties entre :

- Mansa ;
- Agent ;
- commerçant ;
- banque ;
- opérateur ;
- acquéreur ;
- processeur ;
- réseau ;
- partenaire ;
- distributeur.

---

# 87. Limites

Les limites peuvent dépendre :

- pays ;
- produit ;
- utilisateur ;
- niveau KYC ;
- risque ;
- partenaire ;
- appareil ;
- période ;
- devise ;
- canal.

---

# 88. Notifications

Chaque opération critique doit pouvoir produire une notification.

Canaux possibles :

- push ;
- SMS ;
- e-mail ;
- portail ;
- application ;
- webhook.

---

# 89. Reçus

Les reçus doivent être :

- liés à une opération ;
- vérifiables ;
- téléchargeables ;
- partageables ;
- masqués ;
- auditables ;
- disponibles selon la durée prévue.

---

# 90. Idempotence

Elle doit être appliquée aux :

- paiements ;
- transferts ;
- dépôts ;
- retraits ;
- remboursements ;
- factures ;
- règlements ;
- synchronisations ;
- webhooks ;
- opérations administratives critiques.

---

# 91. Timeouts

Un timeout ne doit pas être considéré automatiquement comme un échec.

Le système doit :

- vérifier le statut ;
- éviter un doublon ;
- conserver la référence ;
- rapprocher ;
- déclencher un reversal si nécessaire ;
- informer l’utilisateur.

---

# 92. Reversals

Les reversals doivent être gérés pour :

- paiement ;
- carte ;
- TPE ;
- GAB/DAB ;
- transfert ;
- partenaire ;
- timeout ;
- autorisation non finalisée.

---

# 93. Réconciliation

Elle doit comparer :

- demande ;
- service métier ;
- ledger ;
- partenaire ;
- banque ;
- réseau ;
- terminal ;
- machine ;
- reçu ;
- règlement.

---

# 94. Suspense

Les opérations non rapprochées doivent être placées dans un statut ou compte de suspense contrôlé.

Elles doivent être :

- identifiées ;
- assignées ;
- investiguées ;
- corrigées ;
- clôturées ;
- auditées.

---

# 95. Sécurité

La plateforme doit appliquer :

- Zero Trust ;
- MFA ;
- RBAC ;
- ABAC ;
- chiffrement ;
- segmentation ;
- HSM ;
- gestion des secrets ;
- supervision ;
- tests ;
- réponse aux incidents.

---

# 96. Données sensibles

Sont notamment sensibles :

- PIN ;
- CVV ;
- PAN ;
- OTP ;
- mots de passe ;
- clés ;
- secrets ;
- biométrie ;
- documents KYC ;
- coordonnées bancaires ;
- données financières.

---

# 97. Interdictions générales

Il est interdit de :

- stocker un PIN en clair ;
- stocker un secret dans Git ;
- modifier une écriture ledger validée ;
- contourner une permission ;
- publier un tarif non validé ;
- effectuer une correction financière sans audit ;
- exposer des données carte complètes ;
- supprimer une preuve critique ;
- utiliser des données Production en Test sans contrôle.

---

# 98. Protection des données

Le projet doit intégrer :

- minimisation ;
- consentement ;
- droits utilisateurs ;
- rétention ;
- anonymisation ;
- pseudonymisation ;
- Legal Hold ;
- contrôle des transferts ;
- registre des traitements.

---

# 99. Conformité

Le projet doit intégrer :

- KYC ;
- KYB ;
- KYA ;
- PEP ;
- sanctions ;
- AML/CFT ;
- surveillance ;
- dossiers ;
- déclarations ;
- gel ;
- revues ;
- audits.

---

# 100. Fraude

Le projet doit détecter :

- usurpation ;
- compte mule ;
- fraude carte ;
- fraude Agent ;
- fraude commerçant ;
- fraude TPE ;
- fraude GAB/DAB ;
- fraude interne ;
- fraude partenaire ;
- fraude au remboursement.

---

# 101. Séparation des fonctions

Une même personne ne doit pas pouvoir seule :

- créer et valider une correction ;
- changer et approuver des frais ;
- initier et approuver un remboursement élevé ;
- générer et injecter des clés ;
- ouvrir et clôturer une enquête critique sans contrôle.

---

# 102. Rôles globaux

Exemples :

```text
SUPER_ADMIN
COUNTRY_ADMIN
PRODUCT_ADMIN
FINANCE_ADMIN
COMPLIANCE_ADMIN
SECURITY_ADMIN
FRAUD_ADMIN
SUPPORT_ADMIN
OPERATIONS_ADMIN
TECHNICAL_ADMIN
AUDITOR
VIEWER
```

---

# 103. Permissions globales

Les permissions doivent être :

- granulaires ;
- versionnées ;
- testées ;
- limitées ;
- révocables ;
- auditables ;
- liées à un périmètre ;
- liées à une durée si nécessaire.

---

# 104. Double validation

Elle doit être utilisée pour :

- corrections financières ;
- changement de compte bancaire ;
- remboursement élevé ;
- rotation HSM ;
- mise en Production ;
- activation pays ;
- modification nationale de frais ;
- restauration ;
- bascule PRA ;
- dégel réglementaire.

---

# 105. Audits

Les audits doivent enregistrer :

- acteur ;
- rôle ;
- ressource ;
- action ;
- ancienne valeur ;
- nouvelle valeur ;
- date ;
- heure ;
- pays ;
- environnement ;
- motif ;
- résultat ;
- approbateur.

---

# 106. Immutabilité des audits

Les journaux critiques doivent être protégés contre :

- suppression ;
- modification ;
- falsification ;
- réécriture ;
- changement de date ;
- changement d’auteur ;
- export non autorisé.

---

# 107. Observabilité

Chaque service doit produire :

- logs ;
- métriques ;
- traces ;
- health checks ;
- alertes ;
- SLI ;
- SLO ;
- événements.

---

# 108. Tableaux de bord techniques

Ils doivent couvrir :

- disponibilité ;
- erreurs ;
- latence ;
- bases ;
- queues ;
- événements ;
- partenaires ;
- ledger ;
- paiements ;
- transferts ;
- TPE ;
- GAB/DAB ;
- sécurité ;
- coûts.

---

# 109. Tableaux de bord métier

Ils doivent couvrir :

- utilisateurs ;
- KYC ;
- transactions ;
- volume ;
- valeur ;
- Agents ;
- commerçants ;
- TPE ;
- GAB/DAB ;
- revenus ;
- frais ;
- commissions ;
- satisfaction ;
- support.

---

# 110. Sauvegardes

Elles doivent couvrir :

- bases ;
- ledger ;
- documents ;
- configurations ;
- certificats ;
- données critiques ;
- audits ;
- Data Platform.

---

# 111. PRA

Le PRA doit couvrir :

- perte de région ;
- corruption de base ;
- attaque ;
- ransomware ;
- perte de partenaire ;
- indisponibilité humaine ;
- perte de secret ;
- panne réseau ;
- erreur de déploiement.

---

# 112. PCA

Le PCA doit définir :

- services critiques ;
- équipes ;
- sites ;
- partenaires ;
- alternatives ;
- communication ;
- priorités ;
- délais ;
- responsabilités ;
- exercices.

---

# 113. RTO et RPO

Ils doivent être définis pour :

- ledger ;
- paiement ;
- transfert ;
- cartes ;
- authentification ;
- KYC ;
- TPE ;
- GAB/DAB ;
- support ;
- rapports ;
- site public.

---

# 114. CI/CD

La chaîne doit inclure :

- installation ;
- lint ;
- type checking ;
- build ;
- tests ;
- scan ;
- Prisma ;
- migration ;
- artefact ;
- signature ;
- déploiement ;
- smoke test ;
- rollback.

---

# 115. Quality Gates

Une release doit être bloquée si :

- le build échoue ;
- un test critique échoue ;
- une vulnérabilité critique existe ;
- un secret est détecté ;
- une migration échoue ;
- le ledger est déséquilibré ;
- l’approbation manque ;
- le rollback n’est pas prévu.

---

# 116. Branches Git

Structure recommandée :

```text
main
develop
feature/*
fix/*
release/*
hotfix/*
```

---

# 117. Pull Requests

Chaque Pull Request doit contenir :

- objectif ;
- périmètre ;
- fichiers ;
- tests ;
- risques ;
- captures ;
- migration ;
- documentation ;
- validation CI ;
- reviewer.

---

# 118. Utilisation de l’IA pour développer

Une IA peut :

- générer du code ;
- écrire des tests ;
- expliquer ;
- corriger ;
- refactoriser ;
- documenter ;
- créer des maquettes ;
- préparer des migrations.

Mais ses résultats doivent être :

- relus ;
- testés ;
- sécurisés ;
- versionnés ;
- comparés ;
- approuvés.

---

# 119. Instruction à une IA

Chaque mission doit préciser :

- dépôt ;
- branche ;
- module ;
- fichiers autorisés ;
- fichiers interdits ;
- objectif ;
- critères ;
- tests ;
- commandes ;
- commit attendu ;
- rapport attendu.

---

# 120. Protection contre les modifications globales

Une IA ou un prestataire ne doit pas :

- réécrire tout le dépôt sans nécessité ;
- supprimer des modules ;
- modifier les secrets ;
- fusionner sans test ;
- contourner la CI ;
- pousser du code non vérifié ;
- changer l’architecture sans validation.

---

# 121. Tests globaux

Le projet doit inclure :

- tests unitaires ;
- intégration ;
- API ;
- end-to-end ;
- sécurité ;
- performance ;
- charge ;
- résilience ;
- accessibilité ;
- réseau faible ;
- migration ;
- reprise ;
- partenaires ;
- matériel.

---

# 122. Tests financiers

Ils doivent couvrir :

- débit ;
- crédit ;
- réservation ;
- reversal ;
- remboursement ;
- frais ;
- commission ;
- double débit ;
- timeout ;
- rapprochement ;
- solde ;
- clôture.

---

# 123. Tests matériels

Ils doivent couvrir :

- TPE ;
- lecteur carte ;
- NFC ;
- imprimante ;
- batterie ;
- réseau ;
- GAB ;
- DAB ;
- cassettes ;
- distributeur ;
- dépôt ;
- clavier PIN ;
- alarmes.

---

# 124. Tests de sécurité

Ils doivent couvrir :

- authentification ;
- permissions ;
- sessions ;
- root ;
- jailbreak ;
- secrets ;
- API ;
- web ;
- mobile ;
- TPE ;
- GAB/DAB ;
- cloud ;
- réseau ;
- fournisseurs ;
- fraude interne.

---

# 125. Tests de reprise

Ils doivent couvrir :

- sauvegarde ;
- restauration ;
- réplication ;
- perte de région ;
- rollback ;
- reprise de queue ;
- reprise partenaire ;
- reprise ledger ;
- reprise TPE ;
- reprise GAB/DAB.

---

# 126. Recette

La Recette doit impliquer :

- Produit ;
- Finance ;
- Sécurité ;
- Conformité ;
- Opérations ;
- Support ;
- utilisateurs pilotes ;
- Agents pilotes ;
- commerçants pilotes ;
- partenaires.

---

# 127. Pilote

Le pilote peut inclure :

- 100 à 1 000 clients ;
- 5 à 20 Agents ;
- 10 à 50 commerçants ;
- 3 TPE ;
- 1 GAB ;
- 1 banque ;
- 1 opérateur Mobile Money ;
- une zone limitée.

---

# 128. Fonctions pilotes

Le pilote peut couvrir :

- inscription ;
- KYC ;
- wallet ;
- transfert ;
- paiement QR ;
- dépôt Agent ;
- retrait Agent ;
- encaissement Commerce ;
- TPE ;
- notifications ;
- support ;
- rapprochement.

---

# 129. Plafonds pilotes

Ils doivent être réduits pour :

- dépôt ;
- retrait ;
- transfert ;
- paiement ;
- remboursement ;
- volume quotidien ;
- nombre d’opérations ;
- hors ligne.

---

# 130. Critères de réussite du pilote

- ledger équilibré ;
- aucun double débit ;
- aucun argent perdu ;
- rapprochement correct ;
- disponibilité acceptable ;
- support opérationnel ;
- fraude maîtrisée ;
- Agents fonctionnels ;
- commerçants fonctionnels ;
- satisfaction acceptable.

---

# 131. Critères d’arrêt du pilote

- double débit ;
- perte financière ;
- faille critique ;
- fraude importante ;
- ledger déséquilibré ;
- partenaire instable ;
- indisponibilité prolongée ;
- erreur réglementaire ;
- impossibilité de rapprocher.

---

# 132. Lancement limité

Après le pilote :

- augmenter les utilisateurs ;
- augmenter les Agents ;
- augmenter les commerçants ;
- ajouter des TPE ;
- ajouter des zones ;
- ajouter des partenaires ;
- surveiller ;
- corriger ;
- conserver des plafonds contrôlés.

---

# 133. Lancement national

Il nécessite :

- capacité ;
- liquidité ;
- partenaires ;
- support ;
- sécurité ;
- conformité ;
- maintenance ;
- monitoring ;
- PCA ;
- PRA ;
- communication ;
- opérations nationales.

---

# 134. Déploiement GAB/DAB

Il doit être progressif :

```text
Premier GAB pilote
→ quelques DAB
→ grandes zones commerciales
→ grandes villes
→ capitales régionales
→ extension nationale
```

---

# 135. Déploiement TPE

Il doit commencer auprès de :

- supermarchés ;
- pharmacies ;
- stations-service ;
- restaurants ;
- hôtels ;
- boutiques ;
- écoles ;
- administrations ;
- transports ;
- commerces à fort volume.

---

# 136. Déploiement Agent

Il doit tenir compte :

- densité ;
- activité ;
- cash ;
- sécurité ;
- distance ;
- réseau ;
- besoins ;
- concurrence ;
- rentabilité ;
- capacité du candidat.

---

# 137. Formation

Doivent être formés :

- employés Mansa ;
- développeurs ;
- support ;
- Finance ;
- conformité ;
- fraude ;
- Agents ;
- commerçants ;
- techniciens TPE ;
- techniciens GAB ;
- administrateurs ;
- partenaires.

---

# 138. Documentation opérationnelle

Elle doit inclure :

- guides ;
- procédures ;
- runbooks ;
- FAQ ;
- scripts support ;
- procédures incident ;
- procédures Finance ;
- procédures cash ;
- procédures sécurité ;
- procédures maintenance ;
- contacts.

---

# 139. Budget global

Le budget doit être séparé en :

- produit ;
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
- marketing ;
- opérations ;
- cash ;
- maintenance ;
- assurance.

---

# 140. Suivi des coûts

Le projet doit suivre :

- coût par utilisateur ;
- coût par transaction ;
- coût SMS ;
- coût KYC ;
- coût cloud ;
- coût partenaire ;
- coût carte ;
- coût TPE ;
- coût GAB ;
- coût support ;
- coût fraude ;
- coût maintenance.

---

# 141. Indicateurs globaux

Exemples :

- utilisateurs inscrits ;
- utilisateurs actifs ;
- KYC approuvés ;
- transactions ;
- valeur ;
- disponibilité ;
- taux de succès ;
- Agents actifs ;
- commerçants actifs ;
- TPE actifs ;
- GAB/DAB actifs ;
- revenus ;
- pertes ;
- fraude ;
- satisfaction.

---

# 142. Gouvernance du programme

Structure recommandée :

```text
Fondateur et Direction
→ Comité stratégique
→ Produit
→ Technique
→ Finance
→ Sécurité
→ Conformité
→ Opérations
→ Responsables de modules
→ Équipes de réalisation
```

---

# 143. Responsabilité du fondateur

Le fondateur doit :

- porter la vision ;
- décider des priorités ;
- valider les partenaires ;
- contrôler le budget ;
- protéger la propriété intellectuelle ;
- surveiller l’avancement ;
- maintenir la cohérence ;
- éviter la dispersion ;
- préparer les financements ;
- conserver les accès stratégiques.

---

# 144. Propriété intellectuelle

Mansa doit contrôler :

- code ;
- dépôts ;
- marques ;
- domaines ;
- designs ;
- documentation ;
- clés de signature ;
- comptes stores ;
- cloud ;
- données ;
- contrats ;
- accès partenaires.

---

# 145. Passage à l’exécution

Après validation de la documentation, l’exécution doit suivre :

1. audit des dépôts existants ;
2. inventaire du code ;
3. suppression des duplications inutiles ;
4. stabilisation de l’architecture ;
5. validation Prisma ;
6. validation du backend ;
7. création du Design System ;
8. réalisation du ledger ;
9. réalisation des modules P0 ;
10. tests ;
11. Recette ;
12. pilote.

---

# 146. Audit initial du code

Il doit vérifier :

- structure ;
- dépendances ;
- erreurs ;
- sécurité ;
- secrets ;
- modules ;
- duplications ;
- tests ;
- CI ;
- Prisma ;
- configurations ;
- documentation.

---

# 147. Registre de réalisation

Chaque module doit posséder :

- identifiant ;
- document source ;
- priorité ;
- statut ;
- responsable ;
- dépendances ;
- branche ;
- tests ;
- version ;
- date ;
- validation ;
- anomalies.

---

# 148. Statuts de réalisation

- NOT_STARTED ;
- ANALYSIS ;
- READY ;
- IN_PROGRESS ;
- IN_REVIEW ;
- IN_TEST ;
- BLOCKED ;
- DONE ;
- RELEASED ;
- DEPRECATED.

---

# 149. Définition finale de Done

Un module est terminé lorsque :

- code livré ;
- revue effectuée ;
- build réussi ;
- lint réussi ;
- tests réussis ;
- sécurité validée ;
- migrations validées ;
- documentation mise à jour ;
- monitoring ajouté ;
- audit ajouté ;
- Recette validée ;
- release préparée.

---

# 150. Critères d’acceptation finaux de toute la plateforme

La plateforme Mansa est considérée comme correctement définie lorsque :

- toutes les applications principales sont identifiées ;
- tous les portails principaux sont identifiés ;
- les services backend sont séparés ;
- le ledger est la source de vérité ;
- les wallets sont liés au ledger ;
- les paiements sont idempotents ;
- les transferts sont contrôlés ;
- les cartes sont sécurisées ;
- les Agents sont gérés ;
- les commerçants sont gérés ;
- les TPE sont supervisés ;
- les GAB/DAB sont supervisés ;
- Mobile Money est intégré par connecteurs ;
- les banques sont intégrées par connecteurs ;
- les réseaux cartes sont encadrés ;
- les frais sont configurables ;
- les commissions sont configurables ;
- les plafonds sont configurables ;
- le multi-pays est supporté ;
- le multi-devises est supporté ;
- les langues sont administrables ;
- le Design System est commun ;
- l’administration centrale est complète ;
- les feature flags sont disponibles ;
- les kill switches sont disponibles ;
- les reçus sont vérifiables ;
- les notifications sont disponibles ;
- les timeouts sont gérés ;
- les reversals sont gérés ;
- les opérations sont rapprochées ;
- les suspenses sont gérés ;
- la sécurité Zero Trust est appliquée ;
- le MFA est appliqué aux rôles sensibles ;
- les secrets sont centralisés ;
- le HSM est intégré lorsque requis ;
- les données personnelles sont protégées ;
- les données carte sont protégées ;
- le KYC est configurable ;
- le KYB est configurable ;
- les PEP et sanctions sont filtrées ;
- l’AML/CFT est intégré ;
- la fraude temps réel est intégrée ;
- les comptes mules sont détectables ;
- les fraudes Agent sont détectables ;
- les fraudes commerçant sont détectables ;
- les fraudes TPE sont détectables ;
- les fraudes GAB/DAB sont détectables ;
- la séparation des fonctions est appliquée ;
- les double validations sont disponibles ;
- les audits sont complets ;
- les audits sont immuables ;
- les logs sont structurés ;
- les données sensibles sont exclues des logs ;
- les métriques sont disponibles ;
- les traces distribuées sont disponibles ;
- les tableaux de bord sont disponibles ;
- les alertes sont configurables ;
- les sauvegardes sont chiffrées ;
- les restaurations sont testées ;
- le PCA est défini ;
- le PRA est défini ;
- les RTO et RPO sont définis ;
- la CI est active ;
- la CD est encadrée ;
- les Quality Gates sont actifs ;
- les migrations sont versionnées ;
- les artefacts sont signés ;
- les tests fonctionnels existent ;
- les tests financiers existent ;
- les tests sécurité existent ;
- les tests performance existent ;
- les tests résilience existent ;
- les tests matériel existent ;
- la Recette est organisée ;
- le pilote est défini ;
- les critères d’arrêt sont définis ;
- le lancement progressif est défini ;
- le déploiement Agent est planifié ;
- le déploiement TPE est planifié ;
- le déploiement GAB/DAB est planifié ;
- la formation est prévue ;
- le support est prêt ;
- les procédures sont documentées ;
- le budget est suivi ;
- les coûts sont mesurés ;
- les indicateurs sont définis ;
- la gouvernance est définie ;
- la propriété intellectuelle est protégée ;
- les missions IA sont encadrées ;
- le code existant est protégé ;
- le registre de réalisation est disponible ;
- la définition de Done est appliquée ;
- le passage de la documentation à l’exécution est clairement organisé.
