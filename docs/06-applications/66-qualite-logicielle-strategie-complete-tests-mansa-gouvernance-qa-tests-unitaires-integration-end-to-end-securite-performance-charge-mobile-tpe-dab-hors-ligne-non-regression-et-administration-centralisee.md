# 66 — Qualité logicielle et stratégie complète de tests Mansa : gouvernance QA, tests unitaires, intégration, end-to-end, sécurité, performance, charge, mobile, TPE, DAB, hors ligne, non-régression et administration centralisée

## 1. Objet du document

Ce document définit l’architecture officielle de la **Qualité logicielle et de la Stratégie complète de tests Mansa**.

Ce dispositif doit permettre de vérifier que l’ensemble de l’écosystème Mansa fonctionne correctement, reste sécurisé, respecte les règles métier, protège les données financières et peut évoluer sans provoquer de régression.

Il couvre notamment :

- les applications mobiles ;
- les applications web ;
- les portails internes ;
- les portails partenaires ;
- le backend ;
- les API ;
- l’API Gateway ;
- le ledger ;
- les paiements ;
- les cartes ;
- le KYC et le KYB ;
- le Cash Network ;
- les agents ;
- les commerçants ;
- les TPE ;
- les DAB ;
- les notifications ;
- la fraude ;
- la Finance ;
- la Data ;
- Jini ;
- les intégrations bancaires ;
- les intégrations Mobile Money ;
- les réseaux cartes ;
- les fonctionnalités hors ligne ;
- les migrations ;
- les déploiements ;
- la sécurité ;
- la performance ;
- l’accessibilité ;
- la compatibilité ;
- le multi-pays ;
- le multi-langues ;
- la non-régression ;
- la validation métier ;
- la gestion des anomalies ;
- les preuves de test ;
- les audits.

L’objectif est de mettre en place une stratégie qualité :

- centralisée ;
- automatisée ;
- reproductible ;
- traçable ;
- sécurisée ;
- adaptée à une plateforme financière ;
- compatible avec plusieurs applications ;
- compatible avec plusieurs pays ;
- capable de tester les cas normaux et les cas d’échec ;
- capable de bloquer un déploiement dangereux ;
- capable de garantir qu’une nouvelle version ne dégrade pas les fonctions existantes.

---

# 2. Principes fondamentaux

## 2.1 Aucun service critique ne doit être livré sans test

Tout service critique doit avoir au minimum :

- des tests unitaires ;
- des tests d’intégration ;
- des tests de contrat ;
- des tests end-to-end ;
- des tests de sécurité ;
- des tests de non-régression ;
- des tests de reprise ;
- des critères d’acceptation ;
- des preuves ;
- un responsable qualité.

---

## 2.2 Le test ne doit pas se limiter au cas où tout fonctionne

Chaque fonctionnalité doit être testée sur :

- succès ;
- échec ;
- annulation ;
- timeout ;
- doublon ;
- réseau faible ;
- absence de réseau ;
- donnée invalide ;
- permission insuffisante ;
- partenaire indisponible ;
- reprise après incident ;
- concurrence ;
- limite atteinte ;
- erreur utilisateur ;
- erreur technique.

---

## 2.3 Les tests financiers doivent vérifier les écritures

Pour toute opération financière, les tests doivent contrôler :

- le montant ;
- la devise ;
- les frais ;
- les commissions ;
- le débit ;
- le crédit ;
- l’équilibre ;
- l’unicité ;
- l’idempotence ;
- la référence ;
- le statut ;
- la date comptable ;
- le rapprochement ;
- la possibilité de reprise.

---

## 2.4 Les données de Production ne doivent pas être utilisées librement

Les environnements de test doivent utiliser :

- données fictives ;
- données synthétiques ;
- comptes de démonstration ;
- cartes de test ;
- utilisateurs fictifs ;
- documents anonymisés ;
- partenaires Sandbox ;
- transactions simulées.

---

## 2.5 Un test automatisé instable doit être traité comme une anomalie

Un test qui échoue de manière aléatoire ne doit pas être ignoré.

Il doit être :

- identifié ;
- isolé ;
- corrigé ;
- suivi ;
- éventuellement mis en quarantaine ;
- remis en service après preuve de stabilité.

---

## 2.6 Une version ne doit pas être déclarée prête sans preuve

La validation doit s’appuyer sur :

- résultats ;
- rapports ;
- logs ;
- captures ;
- vidéos éventuelles ;
- métriques ;
- références ;
- couverture ;
- anomalies ;
- validations métier ;
- approbations.

---

# 3. Périmètre qualité

La stratégie qualité couvre :

- qualité fonctionnelle ;
- qualité technique ;
- qualité de sécurité ;
- qualité financière ;
- qualité des données ;
- qualité d’expérience utilisateur ;
- qualité mobile ;
- qualité web ;
- qualité TPE ;
- qualité DAB ;
- qualité API ;
- qualité des intégrations ;
- qualité des déploiements ;
- qualité des migrations ;
- qualité des documents ;
- qualité des traductions ;
- qualité de l’accessibilité ;
- qualité des performances ;
- qualité de la résilience.

---

# 4. Architecture du dispositif QA

Structure recommandée :

```text
quality-platform/
├── test-strategy/
├── test-plans/
├── test-cases/
├── unit-tests/
├── integration-tests/
├── contract-tests/
├── end-to-end-tests/
├── security-tests/
├── performance-tests/
├── load-tests/
├── mobile-tests/
├── web-tests/
├── terminal-tests/
├── atm-tests/
├── offline-tests/
├── accessibility-tests/
├── localization-tests/
├── data-quality-tests/
├── migration-tests/
├── resilience-tests/
├── regression/
├── test-data/
├── environments/
├── defects/
├── reports/
├── evidence/
├── approvals/
├── audit/
└── administration/
```

---

# 5. Gouvernance qualité

La gouvernance doit définir :

- standards ;
- responsabilités ;
- niveaux de test ;
- critères de sortie ;
- seuils de couverture ;
- priorités ;
- processus de validation ;
- gestion des anomalies ;
- gestion des risques ;
- qualité par environnement ;
- qualité par application ;
- qualité par pays.

---

# 6. Rôles qualité

Exemples :

```text
QUALITY_DIRECTOR
QA_MANAGER
QA_ENGINEER
TEST_AUTOMATION_ENGINEER
SECURITY_TESTER
PERFORMANCE_ENGINEER
MOBILE_QA_ENGINEER
WEB_QA_ENGINEER
TERMINAL_QA_ENGINEER
ATM_QA_ENGINEER
DATA_QUALITY_ANALYST
BUSINESS_TESTER
RELEASE_QUALITY_MANAGER
ACCESSIBILITY_TESTER
AUDITOR
VIEWER
```

---

# 7. Responsabilités

## Équipe développement

Elle doit :

- écrire les tests unitaires ;
- maintenir les tests proches du code ;
- corriger les anomalies ;
- fournir les données de test ;
- documenter les changements ;
- assurer la testabilité.

## Équipe QA

Elle doit :

- définir les plans ;
- automatiser les parcours ;
- exécuter les campagnes ;
- vérifier les anomalies ;
- produire les rapports ;
- contrôler la non-régression.

## Équipe métier

Elle doit :

- valider les règles ;
- vérifier les parcours ;
- approuver la Recette ;
- confirmer les cas d’acceptation ;
- signaler les incohérences.

## Équipe sécurité

Elle doit :

- tester les contrôles ;
- analyser les vulnérabilités ;
- réaliser les tests offensifs autorisés ;
- valider les corrections critiques.

---

# 8. Niveaux de test

Les niveaux principaux sont :

1. tests statiques ;
2. tests unitaires ;
3. tests composants ;
4. tests d’intégration ;
5. tests de contrat ;
6. tests système ;
7. tests end-to-end ;
8. tests métier ;
9. tests d’acceptation ;
10. tests de Production contrôlés.

---

# 9. Tests statiques

Ils comprennent :

- lint ;
- formatage ;
- vérification TypeScript ;
- compilation ;
- validation Prisma ;
- analyse de code ;
- scan de dépendances ;
- scan de secrets ;
- analyse IaC ;
- analyse des licences ;
- détection de code mort.

---

# 10. Tests unitaires

Les tests unitaires doivent vérifier :

- fonctions ;
- services ;
- règles métier ;
- calculs ;
- validateurs ;
- convertisseurs ;
- états ;
- erreurs ;
- limites ;
- permissions ;
- frais ;
- commissions ;
- arrondis ;
- devises.

---

# 11. Isolation des tests unitaires

Les tests unitaires doivent éviter les dépendances réelles.

Ils peuvent utiliser :

- mocks ;
- stubs ;
- fakes ;
- données en mémoire ;
- horloge simulée ;
- fournisseurs simulés ;
- réponses contrôlées.

---

# 12. Tests de composants

Ils vérifient un composant plus large comme :

- module d’authentification ;
- module paiement ;
- module carte ;
- module agent ;
- module commerçant ;
- module notification ;
- module de frais ;
- module de commission ;
- module KYC ;
- module de règlement.

---

# 13. Tests d’intégration

Ils vérifient les interactions entre :

- service et base ;
- service et Redis ;
- service et queue ;
- service et Event Bus ;
- API et backend ;
- backend et ledger ;
- backend et partenaire ;
- application et API ;
- module et fournisseur.

---

# 14. Tests de contrat

Les contrats doivent être testés entre :

- frontend et backend ;
- service et service ;
- Mansa et banque ;
- Mansa et Mobile Money ;
- Mansa et réseau cartes ;
- Mansa et fournisseur KYC ;
- Mansa et fournisseur SMS ;
- Mansa et partenaire public.

---

# 15. Contrats API

Les tests doivent vérifier :

- endpoint ;
- méthode ;
- paramètres ;
- authentification ;
- schéma ;
- champs obligatoires ;
- type ;
- statut HTTP ;
- codes d’erreur ;
- compatibilité ;
- version ;
- idempotence.

---

# 16. Tests end-to-end

Ils doivent reproduire les parcours complets.

Exemples :

```text
Inscription
→ vérification téléphone
→ KYC
→ création du compte
→ création du wallet
→ connexion
```

```text
Paiement commerçant
→ saisie du montant
→ autorisation
→ contrôle du risque
→ écriture ledger
→ confirmation
→ reçu
→ règlement
```

---

# 17. Tests d’acceptation métier

Ils permettent aux responsables métier de vérifier :

- règles ;
- frais ;
- commissions ;
- plafonds ;
- parcours ;
- documents ;
- notifications ;
- statuts ;
- délais ;
- permissions ;
- rapports.

---

# 18. Critères d’acceptation

Chaque fonctionnalité doit avoir des critères :

- mesurables ;
- vérifiables ;
- non ambigus ;
- liés au besoin ;
- liés aux risques ;
- liés au comportement attendu.

---

# 19. Tests exploratoires

Les testeurs doivent pouvoir explorer :

- comportements inattendus ;
- enchaînements inhabituels ;
- mauvaises saisies ;
- navigation rapide ;
- interruption ;
- changement d’appareil ;
- rotation d’écran ;
- réseau instable ;
- double clic ;
- retour arrière ;
- reprise.

---

# 20. Tests de non-régression

La non-régression doit couvrir :

- fonctionnalités critiques ;
- anciens bugs ;
- parcours essentiels ;
- compatibilité ;
- règles métier ;
- permissions ;
- intégrations ;
- performance ;
- sécurité ;
- données ;
- appareils.

---

# 21. Suite de régression critique

Elle doit inclure au minimum :

- inscription ;
- connexion ;
- MFA ;
- consultation du solde ;
- transfert ;
- paiement ;
- dépôt ;
- retrait ;
- carte ;
- reçu ;
- remboursement ;
- KYC ;
- agent ;
- commerçant ;
- TPE ;
- DAB ;
- notifications ;
- ledger ;
- rapprochement.

---

# 22. Tests de régression ciblée

Après un changement, les tests doivent couvrir :

- composant modifié ;
- dépendances directes ;
- parcours liés ;
- données liées ;
- permissions liées ;
- versions liées ;
- intégrations concernées.

---

# 23. Tests Smoke

Les smoke tests doivent vérifier après déploiement :

- application accessible ;
- API disponible ;
- authentification ;
- base ;
- cache ;
- queue ;
- transaction de test ;
- notification ;
- version ;
- monitoring.

---

# 24. Tests Sanity

Les sanity tests permettent de vérifier rapidement qu’une correction ou une fonctionnalité principale fonctionne avant une campagne plus large.

---

# 25. Tests de sécurité

Ils doivent couvrir :

- authentification ;
- autorisation ;
- rôles ;
- sessions ;
- tokens ;
- secrets ;
- chiffrement ;
- injections ;
- fichiers ;
- API ;
- mobile ;
- web ;
- TPE ;
- DAB ;
- réseau ;
- partenaires ;
- journalisation.

---

# 26. Tests d’authentification

Exemples :

- mot de passe correct ;
- mot de passe incorrect ;
- compte bloqué ;
- compte suspendu ;
- OTP incorrect ;
- OTP expiré ;
- MFA ;
- passkey ;
- biométrie ;
- changement d’appareil ;
- session expirée ;
- révocation.

---

# 27. Tests d’autorisation

Ils doivent vérifier qu’un utilisateur ne peut pas :

- voir les données d’un autre client ;
- modifier un autre commerçant ;
- accéder à un autre pays ;
- consulter un rôle supérieur ;
- changer un frais sans permission ;
- exécuter une action non autorisée ;
- contourner l’administration ;
- appeler une API interne interdite.

---

# 28. Tests contre les injections

Ils doivent couvrir :

- SQL ;
- NoSQL ;
- commande ;
- LDAP ;
- template ;
- script ;
- HTML ;
- JavaScript ;
- CSV ;
- prompt injection ;
- fichier malveillant.

---

# 29. Tests de gestion des sessions

Ils doivent vérifier :

- expiration ;
- rotation ;
- révocation ;
- déconnexion ;
- multi-appareils ;
- appareil perdu ;
- changement de mot de passe ;
- changement de rôle ;
- changement de pays ;
- session administrateur.

---

# 30. Tests de secrets

Ils doivent vérifier :

- absence dans Git ;
- absence dans les logs ;
- absence dans les builds ;
- absence dans les réponses API ;
- rotation ;
- révocation ;
- droits ;
- expiration ;
- environnement.

---

# 31. Tests cryptographiques

Ils doivent contrôler :

- TLS ;
- mTLS ;
- algorithmes ;
- taille des clés ;
- certificats ;
- rotation ;
- stockage ;
- signature ;
- intégrité ;
- chiffrement au repos ;
- chiffrement en transit.

---

# 32. Tests de vulnérabilité

Ils incluent :

- analyse statique ;
- analyse dynamique ;
- dépendances ;
- conteneurs ;
- images ;
- configuration ;
- infrastructure ;
- mobile ;
- web ;
- API ;
- cloud.

---

# 33. Tests d’intrusion

Les tests d’intrusion doivent être :

- autorisés ;
- planifiés ;
- limités ;
- tracés ;
- exécutés dans un environnement adapté ;
- suivis d’un rapport ;
- suivis d’une correction ;
- retestés.

---

# 34. Tests de fraude

Ils doivent simuler :

- compte compromis ;
- appareil inconnu ;
- transaction inhabituelle ;
- vitesse élevée ;
- multi-comptes ;
- faux agent ;
- faux commerçant ;
- retrait inhabituel ;
- dépôt fractionné ;
- fraude à la carte ;
- remboursement abusif ;
- collusion.

---

# 35. Tests du ledger

Ils doivent vérifier :

- débit égal crédit ;
- aucune écriture orpheline ;
- références uniques ;
- ordre ;
- statut ;
- date de valeur ;
- date comptable ;
- idempotence ;
- compensation ;
- annulation ;
- reprise ;
- audit.

---

# 36. Tests de paiement

Cas à tester :

- paiement réussi ;
- refus solde insuffisant ;
- refus risque ;
- timeout partenaire ;
- double soumission ;
- annulation ;
- remboursement ;
- paiement partiel ;
- paiement fractionné ;
- devise différente ;
- frais ;
- commission ;
- reçu ;
- rapprochement.

---

# 37. Tests de transfert

Ils doivent couvrir :

- compte à compte ;
- banque ;
- Mobile Money ;
- international ;
- bénéficiaire nouveau ;
- bénéficiaire existant ;
- limite ;
- frais ;
- confirmation ;
- erreur ;
- doublon ;
- annulation ;
- reprise.

---

# 38. Tests de dépôt

Ils doivent vérifier :

- dépôt agent ;
- dépôt Mobile Money ;
- dépôt carte ;
- dépôt banque ;
- float suffisant ;
- float insuffisant ;
- compte suspendu ;
- montant limite ;
- reçu ;
- commission ;
- notification ;
- SMS ;
- absence d’Internet client.

---

# 39. Tests de retrait

Ils doivent vérifier :

- retrait agent ;
- retrait DAB ;
- retrait carte ;
- retrait QR ;
- authentification ;
- PIN ;
- OTP ;
- USSD si disponible ;
- carte Mansa ;
- solde suffisant ;
- espèces disponibles ;
- float ;
- coupures ;
- frais ;
- commission ;
- annulation ;
- billet non délivré.

---

# 40. Tests des frais

Ils doivent vérifier :

- montant fixe ;
- pourcentage ;
- fixe + pourcentage ;
- minimum ;
- maximum ;
- gratuité ;
- promotion ;
- pays ;
- région ;
- type de client ;
- type d’agent ;
- horaire ;
- date d’effet ;
- historique ;
- priorité entre règles.

---

# 41. Tests des commissions

Ils doivent vérifier la répartition entre :

- Mansa ;
- agent ;
- commerçant ;
- banque ;
- partenaire ;
- distributeur ;
- opérateur ;
- réseau cartes.

---

# 42. Tests des arrondis

Ils doivent contrôler :

- précision ;
- devise ;
- décimales ;
- arrondi commercial ;
- cumul ;
- partage ;
- commission ;
- taxe ;
- conversion ;
- total débit/crédit.

---

# 43. Tests multi-devises

Ils doivent vérifier :

- taux ;
- devise source ;
- devise cible ;
- date ;
- frais ;
- arrondi ;
- limite ;
- annulation ;
- affichage ;
- historique ;
- comptabilisation.

---

# 44. Tests KYC

Ils doivent couvrir :

- document valide ;
- document expiré ;
- document illisible ;
- doublon ;
- mineur ;
- pays ;
- preuve d’adresse ;
- biométrie ;
- contrôle manuel ;
- fournisseur indisponible ;
- reprise ;
- rejet ;
- recours.

---

# 45. Tests KYB

Ils doivent vérifier :

- entreprise ;
- registre ;
- représentant légal ;
- bénéficiaire effectif ;
- documents ;
- statut fiscal ;
- activité ;
- risque ;
- expiration ;
- mise à jour ;
- suspension ;
- validation manuelle.

---

# 46. Tests cartes

Ils doivent couvrir :

- carte virtuelle ;
- carte physique ;
- carte jetable ;
- activation ;
- PIN ;
- changement PIN ;
- blocage ;
- déblocage ;
- limite ;
- paiement ;
- retrait ;
- tokenisation ;
- expiration ;
- remplacement ;
- opposition ;
- portefeuille mobile.

---

# 47. Tests TPE

Ils doivent couvrir :

- paiement carte ;
- paiement NFC ;
- QR ;
- Mobile Money ;
- PIN ;
- impression ;
- reçus ;
- remboursement ;
- clôture ;
- réseau faible ;
- mode hors ligne ;
- synchronisation ;
- batterie ;
- redémarrage ;
- mise à jour ;
- périphériques ;
- mode kiosque.

---

# 48. Tests DAB

Ils doivent couvrir :

- insertion carte ;
- lecture carte ;
- QR ;
- code sécurisé ;
- PIN ;
- choix du montant ;
- choix des coupures ;
- débit ;
- distribution ;
- reçu ;
- carte retenue ;
- billet bloqué ;
- cassette vide ;
- panne réseau ;
- panne électrique ;
- reprise ;
- rapprochement.

---

# 49. Tests Agent

Ils doivent vérifier :

- connexion ;
- identité ;
- appareil autorisé ;
- caisse ;
- float ;
- dépôt ;
- retrait ;
- commission ;
- reçu ;
- réapprovisionnement ;
- fermeture ;
- écart ;
- alerte ;
- suspension ;
- localisation si activée.

---

# 50. Tests Commerce

Ils doivent couvrir :

- encaissement ;
- catalogue ;
- facture ;
- remboursement ;
- employé ;
- caisse ;
- règlement ;
- promotion ;
- fidélité ;
- reporting ;
- permissions ;
- plusieurs points de vente ;
- fonctionnement hors ligne.

---

# 51. Tests Client

Ils doivent couvrir :

- onboarding ;
- connexion ;
- profil ;
- solde ;
- transactions ;
- transfert ;
- paiement ;
- carte ;
- budget ;
- coffre ;
- abonnement ;
- support ;
- notifications ;
- paramètres ;
- sécurité ;
- réseau faible.

---

# 52. Tests Admin Web

Ils doivent vérifier :

- rôles ;
- permissions ;
- recherche ;
- modification ;
- approbation ;
- double validation ;
- historique ;
- audit ;
- export ;
- configuration ;
- pays ;
- frais ;
- commissions ;
- suspension ;
- réactivation ;
- reporting.

---

# 53. Tests Admin Lite

Ils doivent couvrir :

- consultation mobile ;
- alerte ;
- approbation limitée ;
- blocage urgent ;
- incident ;
- notification ;
- droits restreints ;
- biométrie ;
- appareil enregistré ;
- mode réseau faible.

---

# 54. Tests Jini

Ils doivent vérifier :

- réponse ;
- source ;
- permissions ;
- outils ;
- garde-fous ;
- mémoire ;
- hallucination ;
- injection ;
- données sensibles ;
- escalade humaine ;
- langues ;
- coût ;
- indisponibilité fournisseur ;
- fallback.

---

# 55. Tests Data

Ils doivent couvrir :

- ingestion ;
- transformation ;
- déduplication ;
- fraîcheur ;
- qualité ;
- schéma ;
- lineage ;
- agrégation ;
- rapport ;
- export ;
- suppression ;
- anonymisation ;
- reprise.

---

# 56. Tests de notifications

Ils doivent vérifier :

- push ;
- SMS ;
- e-mail ;
- OTP ;
- traduction ;
- préférence ;
- priorité ;
- retry ;
- fournisseur secondaire ;
- déduplication ;
- statut de livraison ;
- coût ;
- consentement.

---

# 57. Tests de support

Ils doivent couvrir :

- ticket ;
- catégorie ;
- priorité ;
- affectation ;
- SLA ;
- pièce jointe ;
- conversation ;
- escalade ;
- remboursement ;
- fraude ;
- clôture ;
- réouverture ;
- satisfaction.

---

# 58. Tests de performance

Ils doivent mesurer :

- temps de réponse ;
- débit ;
- saturation ;
- consommation CPU ;
- mémoire ;
- disque ;
- réseau ;
- base ;
- file ;
- cache ;
- expérience utilisateur.

---

# 59. Types de tests de performance

- test de charge ;
- test de stress ;
- test de pic ;
- test d’endurance ;
- test de volume ;
- test de scalabilité ;
- test de capacité ;
- test de latence.

---

# 60. Tests de charge

Ils doivent simuler :

- utilisateurs simultanés ;
- paiements simultanés ;
- transferts simultanés ;
- dépôts ;
- retraits ;
- connexions ;
- webhooks ;
- TPE ;
- DAB ;
- campagnes ;
- versements massifs.

---

# 61. Tests de stress

Ils doivent déterminer :

- point de rupture ;
- comportement sous saturation ;
- erreurs ;
- reprise ;
- perte de messages ;
- files ;
- autoscaling ;
- stabilité ;
- temps de récupération.

---

# 62. Tests de pic

Ils doivent simuler :

- lancement national ;
- versement de bourses ;
- paiement de salaires ;
- fête ;
- campagne ;
- panne partenaire puis reprise ;
- notification massive ;
- événement public.

---

# 63. Tests d’endurance

Ils doivent vérifier sur plusieurs heures ou jours :

- fuite mémoire ;
- saturation ;
- accumulation de files ;
- dégradation ;
- connexions ;
- logs ;
- stockage ;
- stabilité ;
- coûts.

---

# 64. Tests de volume

Ils doivent tester :

- millions de transactions ;
- historique long ;
- grand nombre d’utilisateurs ;
- grand nombre d’agents ;
- grand nombre de commerçants ;
- grand nombre de documents ;
- grands exports ;
- gros volumes Data.

---

# 65. Seuils de performance

Chaque service doit définir :

- p50 ;
- p95 ;
- p99 ;
- débit ;
- erreur maximale ;
- saturation maximale ;
- temps de démarrage ;
- temps de récupération ;
- capacité cible.

---

# 66. Tests mobile

Ils doivent couvrir :

- iOS ;
- Android ;
- versions supportées ;
- tailles d’écran ;
- rotation ;
- clavier ;
- biométrie ;
- caméra ;
- NFC ;
- QR ;
- notification ;
- batterie ;
- réseau ;
- stockage ;
- mise à jour.

---

# 67. Matrice d’appareils mobiles

Elle doit inclure :

- appareils récents ;
- appareils anciens supportés ;
- faible mémoire ;
- faible stockage ;
- écran petit ;
- écran grand ;
- réseau 2G/3G/4G/5G ;
- Wi-Fi instable ;
- double SIM ;
- langue locale.

---

# 68. Tests web

Ils doivent couvrir :

- navigateurs ;
- résolutions ;
- responsive ;
- clavier ;
- souris ;
- tactile ;
- cache ;
- cookies ;
- session ;
- sécurité ;
- compatibilité ;
- accessibilité ;
- performance.

---

# 69. Navigateurs supportés

La matrice doit préciser les versions supportées de :

- Chrome ;
- Safari ;
- Edge ;
- Firefox ;
- navigateurs Android ;
- WebView TPE lorsque applicable.

---

# 70. Tests réseau faible

Ils doivent simuler :

- forte latence ;
- perte de paquets ;
- faible débit ;
- coupure ;
- reprise ;
- changement Wi-Fi/mobile ;
- timeout ;
- duplication ;
- synchronisation différée.

---

# 71. Tests hors ligne

Ils doivent vérifier :

- données disponibles localement ;
- limitations ;
- brouillons ;
- opérations en attente ;
- références ;
- synchronisation ;
- conflits ;
- reprise ;
- sécurité locale ;
- expiration ;
- information utilisateur.

---

# 72. Tests de synchronisation

Ils doivent couvrir :

- succès ;
- doublon ;
- conflit ;
- suppression ;
- ordre ;
- reprise ;
- lot partiel ;
- réseau coupé ;
- appareil redémarré ;
- version ancienne ;
- horloge incorrecte.

---

# 73. Tests de compatibilité des versions

Ils doivent vérifier :

- ancienne app avec nouveau backend ;
- nouvelle app avec ancien backend temporaire ;
- ancien TPE ;
- ancien DAB ;
- ancienne API partenaire ;
- ancienne base ;
- migration progressive ;
- feature flag.

---

# 74. Tests de mises à jour

Ils doivent couvrir :

- mise à jour normale ;
- mise à jour obligatoire ;
- téléchargement interrompu ;
- espace insuffisant ;
- signature invalide ;
- rollback ;
- version non compatible ;
- redémarrage ;
- migration locale ;
- reprise.

---

# 75. Tests de migrations de base

Ils doivent vérifier :

- création ;
- modification ;
- migration de données ;
- compatibilité ;
- rollback ;
- performance ;
- verrouillage ;
- intégrité ;
- données manquantes ;
- anciennes versions.

---

# 76. Tests de migration destructive

Ils doivent exiger :

- sauvegarde ;
- restauration testée ;
- validation ;
- copie de test ;
- comparaison ;
- rollback ;
- preuve ;
- contrôle post-migration.

---

# 77. Tests de résilience

Ils doivent simuler :

- perte d’instance ;
- perte de zone ;
- base indisponible ;
- Redis indisponible ;
- queue saturée ;
- partenaire lent ;
- partenaire indisponible ;
- certificat expiré ;
- réseau coupé ;
- stockage plein ;
- DNS défaillant.

---

# 78. Tests de chaos

Ils peuvent introduire volontairement :

- arrêt de service ;
- latence ;
- perte réseau ;
- erreur ;
- saturation ;
- suppression d’instance ;
- panne de dépendance ;
- perte de zone.

Ils doivent rester :

- autorisés ;
- limités ;
- observables ;
- réversibles ;
- planifiés ;
- sécurisés.

---

# 79. Tests PCA et PRA

Ils doivent vérifier :

- sauvegarde ;
- restauration ;
- bascule ;
- failback ;
- DNS ;
- secrets ;
- certificats ;
- bases ;
- files ;
- applications ;
- partenaires ;
- RPO ;
- RTO.

---

# 80. Tests d’accessibilité

Ils doivent couvrir :

- navigation clavier ;
- lecteur d’écran ;
- contraste ;
- taille de texte ;
- labels ;
- erreurs ;
- focus ;
- formulaires ;
- boutons ;
- alternatives textuelles ;
- sous-titres ;
- accessibilité mobile.

---

# 81. Tests linguistiques

Ils doivent vérifier :

- français ;
- bambara ;
- anglais ;
- arabe ;
- autres langues activées ;
- texte tronqué ;
- sens ;
- terminologie ;
- pluriel ;
- genre ;
- format date ;
- devise ;
- nombre ;
- sens de lecture.

---

# 82. Tests de localisation

Chaque pays doit être testé sur :

- devise ;
- numéro de téléphone ;
- adresse ;
- fuseau ;
- date ;
- heure ;
- jours fériés ;
- langue ;
- règles ;
- partenaires ;
- plafonds ;
- frais ;
- documents.

---

# 83. Tests de qualité des données

Ils doivent vérifier :

- complétude ;
- unicité ;
- exactitude ;
- cohérence ;
- fraîcheur ;
- format ;
- référence ;
- doublon ;
- relation ;
- plage ;
- source ;
- lineage.

---

# 84. Tests de confidentialité

Ils doivent vérifier :

- minimisation ;
- consentement ;
- accès ;
- suppression ;
- export ;
- masquage ;
- anonymisation ;
- rétention ;
- journalisation ;
- partage partenaire.

---

# 85. Tests de suppression

Ils doivent vérifier la suppression dans :

- base principale ;
- caches ;
- index ;
- stockage ;
- sauvegardes selon politique ;
- Data ;
- Jini ;
- logs lorsque applicable ;
- partenaires ;
- appareils.

---

# 86. Tests de permissions

Chaque rôle doit être testé sur :

- consultation ;
- création ;
- modification ;
- suppression ;
- approbation ;
- export ;
- audit ;
- pays ;
- organisation ;
- produit ;
- environnement.

---

# 87. Tests multi-tenant

Ils doivent garantir la séparation entre :

- clients ;
- commerçants ;
- entreprises ;
- écoles ;
- institutions ;
- pays ;
- partenaires ;
- environnements.

---

# 88. Tests de concurrence

Ils doivent couvrir :

- double clic ;
- deux paiements ;
- deux retraits ;
- deux administrateurs ;
- deux modifications ;
- deux remboursements ;
- deux clôtures ;
- deux promotions de base ;
- deux mises à jour.

---

# 89. Tests d’idempotence

Ils doivent vérifier qu’une même requête répétée ne provoque pas :

- double débit ;
- double crédit ;
- double commission ;
- double règlement ;
- double notification critique ;
- double création ;
- double remboursement.

---

# 90. Tests temporels

Ils doivent couvrir :

- heure UTC ;
- heure locale ;
- changement de jour ;
- changement de mois ;
- fin d’année ;
- fuseau ;
- expiration ;
- date d’effet ;
- jour férié ;
- clôture ;
- heure d’été si applicable.

---

# 91. Tests de limites

Ils doivent vérifier :

- montant minimum ;
- montant maximum ;
- plafond journalier ;
- plafond mensuel ;
- nombre d’opérations ;
- taille de fichier ;
- longueur de texte ;
- nombre de bénéficiaires ;
- nombre de cartes ;
- nombre d’appareils.

---

# 92. Données de test

La plateforme doit gérer :

- utilisateurs fictifs ;
- commerçants fictifs ;
- agents fictifs ;
- banques fictives ;
- comptes fictifs ;
- cartes fictives ;
- documents fictifs ;
- transactions fictives ;
- incidents fictifs ;
- scénarios prédéfinis.

---

# 93. Génération de données synthétiques

Les données doivent pouvoir être générées selon :

- pays ;
- profil ;
- risque ;
- devise ;
- statut ;
- âge ;
- entreprise ;
- volume ;
- historique ;
- comportement ;
- anomalie.

---

# 94. Masquage des données

Lorsqu’une donnée réelle autorisée est utilisée, elle doit être :

- anonymisée ;
- pseudonymisée ;
- tronquée ;
- remplacée ;
- chiffrée ;
- limitée ;
- auditée.

---

# 95. Environnements de test

Les environnements officiels peuvent inclure :

- LOCAL ;
- DEVELOPMENT ;
- TEST ;
- DEMO ;
- RECETTE ;
- PREPRODUCTION ;
- SANDBOX ;
- PERFORMANCE ;
- SECURITY.

---

# 96. Environnement Performance

Il doit permettre :

- charge ;
- stress ;
- endurance ;
- volume ;
- scalabilité ;
- tests sans perturber les autres équipes.

---

# 97. Environnement Sécurité

Il doit permettre :

- scans ;
- tests offensifs ;
- fichiers malveillants ;
- attaques simulées ;
- contrôles ;
- analyse ;
- isolation.

---

# 98. Test en Production

Les tests en Production doivent être limités à :

- smoke tests contrôlés ;
- transactions de test identifiées ;
- monitoring synthétique ;
- tests de disponibilité ;
- canary ;
- chaos très encadré ;
- vérifications non destructives.

---

# 99. Comptes de test Production

Ils doivent être :

- identifiés ;
- séparés ;
- limités ;
- auditables ;
- sans accès excessif ;
- exclus des rapports métier lorsque nécessaire ;
- supprimables ;
- surveillés.

---

# 100. Gestion des anomalies

Chaque anomalie doit contenir :

- identifiant ;
- titre ;
- description ;
- environnement ;
- version ;
- application ;
- pays ;
- sévérité ;
- priorité ;
- étapes ;
- résultat attendu ;
- résultat observé ;
- preuve ;
- responsable ;
- statut ;
- correction ;
- retest.

---

# 101. Sévérité d’anomalie

- BLOCKER ;
- CRITICAL ;
- MAJOR ;
- MINOR ;
- TRIVIAL.

---

# 102. Priorité

- P0 ;
- P1 ;
- P2 ;
- P3 ;
- P4.

La sévérité mesure l’impact.

La priorité mesure l’urgence de correction.

---

# 103. Exemples de Blocker

- impossible de déployer ;
- impossible de se connecter ;
- ledger déséquilibré ;
- double débit ;
- perte de données ;
- faille critique ;
- paiements entièrement bloqués ;
- corruption de base.

---

# 104. Exemples de Critical

- retrait incorrect ;
- commission incorrecte ;
- accès aux données d’un autre utilisateur ;
- remboursement multiple ;
- contournement MFA ;
- erreur financière majeure ;
- DAB délivrant sans débit correct.

---

# 105. Cycle de vie d’une anomalie

- NEW ;
- TRIAGED ;
- ASSIGNED ;
- IN_PROGRESS ;
- FIXED ;
- READY_FOR_RETEST ;
- VERIFIED ;
- CLOSED ;
- REOPENED ;
- REJECTED ;
- DUPLICATE ;
- DEFERRED.

---

# 106. Triage

Le triage doit décider :

- validité ;
- sévérité ;
- priorité ;
- responsable ;
- version cible ;
- risque ;
- blocage de livraison ;
- besoin d’incident ;
- besoin de communication.

---

# 107. Retest

Une correction doit être retestée sur :

- cas initial ;
- cas voisins ;
- non-régression ;
- environnement cible ;
- version cible ;
- données concernées ;
- appareils concernés.

---

# 108. Critères de blocage d’une release

Une release doit être bloquée si :

- test critique échoué ;
- anomalie Blocker ouverte ;
- anomalie Critical non acceptée ;
- scan critique non corrigé ;
- migration non validée ;
- couverture insuffisante sur domaine critique ;
- performance sous seuil ;
- rollback absent ;
- Recette non validée ;
- preuve manquante.

---

# 109. Dérogation

Une anomalie peut être acceptée temporairement uniquement avec :

- analyse de risque ;
- propriétaire ;
- justification ;
- impact ;
- mesure compensatoire ;
- date de correction ;
- approbation ;
- traçabilité.

---

# 110. Couverture de test

La couverture peut être mesurée par :

- lignes ;
- branches ;
- fonctions ;
- règles métier ;
- parcours ;
- exigences ;
- risques ;
- appareils ;
- pays ;
- intégrations.

---

# 111. Couverture minimale

Les seuils doivent être plus élevés pour :

- ledger ;
- paiements ;
- cartes ;
- frais ;
- commissions ;
- authentification ;
- permissions ;
- KYC ;
- retraits ;
- rapprochement.

---

# 112. Couverture par risque

Une fonctionnalité à fort risque doit recevoir davantage de tests même si sa taille de code est faible.

---

# 113. Matrice de traçabilité

Elle doit relier :

```text
Besoin
→ exigence
→ fonctionnalité
→ code
→ test
→ résultat
→ anomalie
→ preuve
```

---

# 114. Plans de test

Chaque plan doit contenir :

- périmètre ;
- objectifs ;
- hors périmètre ;
- risques ;
- environnements ;
- données ;
- types de tests ;
- responsables ;
- calendrier ;
- critères d’entrée ;
- critères de sortie ;
- rapports.

---

# 115. Critères d’entrée

Exemples :

- build disponible ;
- environnement prêt ;
- données chargées ;
- dépendances disponibles ;
- documentation disponible ;
- testabilité validée ;
- version identifiée ;
- anomalies bloquantes connues.

---

# 116. Critères de sortie

Exemples :

- tests critiques réussis ;
- anomalies Blocker fermées ;
- anomalies Critical traitées ;
- couverture atteinte ;
- performance conforme ;
- sécurité validée ;
- Recette approuvée ;
- rapport publié ;
- rollback vérifié.

---

# 117. Campagne de test

Une campagne doit contenir :

- version ;
- application ;
- environnement ;
- périmètre ;
- cas ;
- résultats ;
- anomalies ;
- couverture ;
- responsable ;
- début ;
- fin ;
- statut ;
- décision.

---

# 118. Statuts de campagne

- PLANNED ;
- READY ;
- RUNNING ;
- BLOCKED ;
- COMPLETED ;
- FAILED ;
- CANCELLED ;
- APPROVED.

---

# 119. Automatisation

Les tests automatisés doivent être intégrés à :

- CI ;
- Pull Requests ;
- nightly builds ;
- Recette ;
- Préproduction ;
- déploiement ;
- monitoring synthétique ;
- régression ;
- release.

---

# 120. Priorité d’automatisation

Automatiser en priorité :

- parcours critiques ;
- tests répétitifs ;
- tests de régression ;
- tests API ;
- tests de contrat ;
- tests ledger ;
- tests paiement ;
- tests permissions ;
- tests multi-pays ;
- tests de données.

---

# 121. Tests manuels

Les tests manuels restent utiles pour :

- exploration ;
- expérience utilisateur ;
- accessibilité ;
- matériel ;
- TPE ;
- DAB ;
- traduction ;
- scénarios complexes ;
- validation métier ;
- situations nouvelles.

---

# 122. Tests instables

Un test instable doit avoir :

- identifiant ;
- fréquence ;
- cause probable ;
- propriétaire ;
- date ;
- environnement ;
- statut ;
- plan de correction ;
- date d’expiration de quarantaine.

---

# 123. Quarantaine

La quarantaine ne doit pas permettre d’ignorer indéfiniment un test critique.

Un test critique en quarantaine doit déclencher :

- alerte ;
- suivi ;
- correction prioritaire ;
- contrôle manuel temporaire.

---

# 124. Rapports de test

Les rapports doivent afficher :

- nombre de tests ;
- réussis ;
- échoués ;
- ignorés ;
- bloqués ;
- couverture ;
- durée ;
- anomalies ;
- tendances ;
- environnement ;
- version ;
- décision.

---

# 125. Tableau de bord qualité

Il peut afficher :

- qualité par application ;
- qualité par version ;
- couverture ;
- anomalies ;
- stabilité ;
- performance ;
- sécurité ;
- régression ;
- dette qualité ;
- tendances ;
- pays ;
- équipe.

---

# 126. Indicateurs qualité

Exemples :

- taux de réussite ;
- densité d’anomalies ;
- temps moyen de correction ;
- taux de réouverture ;
- couverture ;
- taux d’automatisation ;
- taux de tests instables ;
- défauts échappés en Production ;
- fréquence des régressions ;
- temps de campagne.

---

# 127. Défauts échappés

Une anomalie trouvée en Production doit être reliée à :

- exigence ;
- test manquant ;
- test inefficace ;
- environnement ;
- cause ;
- correction ;
- action préventive ;
- mise à jour de la suite de régression.

---

# 128. Qualité par version

Chaque version doit avoir un score ou statut basé sur :

- tests ;
- anomalies ;
- sécurité ;
- performance ;
- couverture ;
- stabilité ;
- validation métier ;
- risque ;
- rollback.

---

# 129. Quality Gate

Un Quality Gate peut vérifier :

- lint ;
- build ;
- tests ;
- couverture ;
- vulnérabilités ;
- dette technique ;
- duplications ;
- complexité ;
- anomalies ;
- performance ;
- approbation.

---

# 130. Quality Gate Production

Il doit être plus strict et inclure :

- Recette approuvée ;
- sécurité approuvée ;
- performance conforme ;
- migrations validées ;
- rollback disponible ;
- smoke tests prêts ;
- monitoring actif ;
- anomalie critique acceptée formellement si présente.

---

# 131. API

Exemples :

```http
GET    /quality/test-plans
POST   /quality/test-plans

GET    /quality/test-cases
POST   /quality/test-cases

GET    /quality/campaigns
POST   /quality/campaigns
POST   /quality/campaigns/{id}/start
POST   /quality/campaigns/{id}/complete

GET    /quality/results
POST   /quality/results

GET    /quality/defects
POST   /quality/defects
PATCH  /quality/defects/{id}

GET    /quality/coverage
GET    /quality/reports

POST   /quality/releases/{id}/approve
GET    /quality/audit
```

---

# 132. Webhooks internes

Événements possibles :

```text
quality.test.started
quality.test.completed
quality.test.failed
quality.campaign.started
quality.campaign.completed
quality.campaign.failed
quality.defect.created
quality.defect.reopened
quality.coverage.below_threshold
quality.security_test.failed
quality.performance_test.failed
quality.release.blocked
quality.release.approved
quality.flaky_test.detected
quality.audit.alert
```

---

# 133. Modèles principaux

- QualityStandard
- TestStrategy
- TestPlan
- TestRequirement
- TestCase
- TestStep
- TestDataset
- TestEnvironment
- TestCampaign
- TestExecution
- TestResult
- TestEvidence
- TestCoverage
- RegressionSuite
- PerformanceScenario
- SecurityTest
- DeviceMatrix
- BrowserMatrix
- LocalizationTest
- DataQualityRule
- Defect
- DefectComment
- DefectEvidence
- ReleaseQualityAssessment
- QualityGate
- QualityException
- QualityApproval
- QualityMetric
- QualityAudit

---

# 134. Intégrations

La plateforme qualité doit se connecter à :

- GitHub ;
- CI/CD ;
- gestion de projet ;
- backend ;
- API Gateway ;
- bases ;
- mobile ;
- web ;
- TPE ;
- DAB ;
- observabilité ;
- sécurité ;
- Data ;
- Jini ;
- sandbox partenaires ;
- gestion des releases ;
- documentation.

---

# 135. Multi-pays

Chaque pays peut avoir :

- scénarios ;
- règles ;
- devises ;
- langues ;
- partenaires ;
- limites ;
- documents ;
- appareils ;
- réseaux ;
- campagnes ;
- validations métier ;
- matrices de test.

---

# 136. Administration centrale

L’administration peut gérer :

- standards ;
- stratégies ;
- plans ;
- cas ;
- données ;
- environnements ;
- campagnes ;
- résultats ;
- anomalies ;
- couverture ;
- appareils ;
- navigateurs ;
- pays ;
- automatisation ;
- quality gates ;
- dérogations ;
- rapports ;
- accès ;
- audits.

---

# 137. Permissions

Exemples :

```text
quality.strategy.read
quality.strategy.manage
quality.plan.read
quality.plan.manage
quality.case.read
quality.case.manage
quality.campaign.create
quality.campaign.execute
quality.result.read
quality.defect.create
quality.defect.manage
quality.release.approve
quality.exception.approve
quality.report.read
quality.audit.read
```

---

# 138. Approbations

Peuvent nécessiter une approbation :

- plan de test critique ;
- dérogation ;
- acceptation d’anomalie ;
- validation Recette ;
- validation sécurité ;
- validation performance ;
- validation Production ;
- suppression de preuve ;
- modification de seuil ;
- test en Production.

---

# 139. Double validation

Peut être exigée pour :

- accepter un Blocker ;
- accepter une anomalie financière critique ;
- ignorer un test ledger ;
- désactiver un Quality Gate ;
- autoriser un test destructif ;
- approuver une release nationale ;
- supprimer une campagne ;
- modifier les seuils de sécurité.

---

# 140. Audit

Le journal doit contenir :

- utilisateur ;
- rôle ;
- test ;
- campagne ;
- résultat ;
- anomalie ;
- version ;
- application ;
- environnement ;
- pays ;
- date ;
- heure ;
- approbation ;
- dérogation ;
- décision ;
- preuve.

---

# 141. Immutabilité des preuves

Les preuves critiques doivent être protégées contre :

- modification ;
- suppression ;
- remplacement ;
- réécriture ;
- changement de résultat ;
- export non autorisé.

---

# 142. Tests de la stratégie QA elle-même

Le dispositif qualité doit également être testé sur :

- disponibilité ;
- permissions ;
- intégrité des résultats ;
- fiabilité des rapports ;
- conservation des preuves ;
- automatisation ;
- reprise ;
- audit ;
- performance ;
- sécurité.

---

# 143. Règles métier

1. Chaque service critique possède des tests.
2. Chaque opération financière vérifie le ledger.
3. Les cas d’échec sont testés.
4. Les tests utilisent des données contrôlées.
5. Les données de Production sont protégées.
6. Les contrats API sont testés.
7. Les parcours essentiels possèdent des tests end-to-end.
8. La non-régression est obligatoire.
9. Les tests de sécurité sont intégrés.
10. Les permissions sont testées.
11. L’idempotence est testée.
12. Les frais et commissions sont testés.
13. Les migrations sont testées avant Production.
14. Les appareils supportés sont couverts.
15. Les modes réseau faible et hors ligne sont testés.
16. Les tests instables sont corrigés.
17. Les anomalies critiques peuvent bloquer une release.
18. Les dérogations sont formelles.
19. Les preuves sont conservées.
20. Les quality gates sont automatisés.
21. Les versions sont évaluées avant déploiement.
22. Les défauts Production améliorent la régression.
23. Les pays possèdent leurs scénarios.
24. Le demandeur ne valide pas seul une exception critique.
25. Les audits sont immuables.

---

# 144. Critères d’acceptation

La Qualité logicielle et la Stratégie complète de tests Mansa sont validées lorsque :

- la gouvernance QA est définie ;
- les rôles sont définis ;
- les niveaux de test sont formalisés ;
- les tests statiques fonctionnent ;
- les tests unitaires existent ;
- les tests de composants existent ;
- les tests d’intégration existent ;
- les tests de contrat existent ;
- les tests end-to-end existent ;
- les critères d’acceptation sont documentés ;
- les tests exploratoires sont prévus ;
- la non-régression est automatisée ;
- les smoke tests sont disponibles ;
- les tests de sécurité sont intégrés ;
- l’authentification est testée ;
- les permissions sont testées ;
- les sessions sont testées ;
- les secrets sont testés ;
- le chiffrement est testé ;
- les vulnérabilités sont scannées ;
- les tests d’intrusion sont encadrés ;
- la fraude est testée ;
- le ledger est testé ;
- les paiements sont testés ;
- les transferts sont testés ;
- les dépôts sont testés ;
- les retraits sont testés ;
- les frais sont testés ;
- les commissions sont testées ;
- les arrondis sont testés ;
- le multi-devises est testé ;
- le KYC est testé ;
- le KYB est testé ;
- les cartes sont testées ;
- les TPE sont testés ;
- les DAB sont testés ;
- l’application Agent est testée ;
- l’application Commerce est testée ;
- l’application Client est testée ;
- Admin Web est testé ;
- Admin Lite est testé ;
- Jini est testé ;
- la Data est testée ;
- les notifications sont testées ;
- le support est testé ;
- les tests de performance sont disponibles ;
- les tests de charge sont disponibles ;
- les tests de stress sont disponibles ;
- les tests de pic sont disponibles ;
- les tests d’endurance sont disponibles ;
- les tests de volume sont disponibles ;
- les seuils de performance sont définis ;
- les appareils mobiles sont couverts ;
- les navigateurs sont couverts ;
- le réseau faible est testé ;
- le hors ligne est testé ;
- la synchronisation est testée ;
- la compatibilité des versions est testée ;
- les mises à jour sont testées ;
- les migrations sont testées ;
- la résilience est testée ;
- les tests de chaos sont encadrés ;
- le PCA et le PRA sont testés ;
- l’accessibilité est testée ;
- les langues sont testées ;
- la localisation est testée ;
- la qualité des données est testée ;
- la confidentialité est testée ;
- la suppression est testée ;
- le multi-tenant est testé ;
- la concurrence est testée ;
- l’idempotence est testée ;
- les cas temporels sont testés ;
- les limites sont testées ;
- les données synthétiques sont disponibles ;
- les environnements de test sont séparés ;
- les tests Production sont limités ;
- les anomalies sont centralisées ;
- les sévérités sont définies ;
- le cycle de vie des anomalies est géré ;
- les critères de blocage de release sont appliqués ;
- les dérogations sont tracées ;
- la couverture est mesurée ;
- la matrice de traçabilité existe ;
- les plans de test sont centralisés ;
- les campagnes sont gérées ;
- l’automatisation est intégrée à la CI/CD ;
- les tests instables sont détectés ;
- les rapports sont disponibles ;
- les indicateurs qualité sont calculés ;
- les défauts échappés sont analysés ;
- les Quality Gates sont actifs ;
- les rôles et permissions sont appliqués ;
- les approbations critiques sont protégées ;
- les preuves sont immuables ;
- les audits sont immuables ;
- les tests couvrent les parcours essentiels.
