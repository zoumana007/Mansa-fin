# 71 — Stratégie de lancement, migration, déploiement progressif et mise en production de Mansa

## 1. Objet du document

Ce document définit la stratégie officielle de **lancement, migration, déploiement progressif et mise en production de Mansa**.

Il décrit comment passer :

```text
Développement
→ Test
→ Démonstration
→ Recette
→ Pilote
→ Préproduction
→ Production limitée
→ Production nationale
→ Extension régionale
```

Il couvre notamment :

- la préparation du lancement ;
- les environnements ;
- les versions ;
- la migration des données ;
- les intégrations partenaires ;
- le pilote ;
- les agents ;
- les commerçants ;
- les TPE ;
- les GAB et DAB ;
- les cartes ;
- les applications mobiles ;
- les portails web ;
- le backend ;
- le ledger ;
- les tests ;
- la sécurité ;
- la conformité ;
- la formation ;
- le support ;
- la communication ;
- la surveillance ;
- les incidents ;
- les rollbacks ;
- la continuité d’activité ;
- le passage à l’échelle ;
- le multi-pays ;
- l’administration centralisée.

L’objectif est de garantir un lancement :

- progressif ;
- sécurisé ;
- contrôlé ;
- réversible ;
- mesurable ;
- traçable ;
- conforme ;
- compatible avec un démarrage limité ;
- capable de monter progressivement à l’échelle nationale puis régionale.

---

# 2. Principes fondamentaux

## 2.1 Ne pas lancer toutes les fonctions en même temps

Le lancement doit être organisé par phases.

Les premières versions doivent se concentrer sur les fonctions indispensables :

- création de compte ;
- authentification ;
- KYC ;
- wallet ;
- consultation du solde ;
- transfert ;
- paiement ;
- dépôt Agent ;
- retrait Agent ;
- QR ;
- notifications ;
- support ;
- administration ;
- ledger ;
- rapports essentiels.

Les fonctions complexes peuvent être ajoutées progressivement :

- cartes ;
- TPE avancé ;
- GAB/DAB ;
- crédit ;
- épargne avancée ;
- entreprises ;
- État ;
- écoles ;
- multi-pays ;
- IA avancée.

---

## 2.2 Aucun lancement sans pilote

Avant un lancement national, Mansa doit réaliser un pilote contrôlé avec :

- utilisateurs sélectionnés ;
- agents sélectionnés ;
- commerçants sélectionnés ;
- TPE sélectionnés ;
- un premier GAB si disponible ;
- plafonds réduits ;
- supervision renforcée ;
- support dédié ;
- tests en conditions réelles ;
- capacité de suspension immédiate.

---

## 2.3 Toute mise en production doit être réversible

Chaque déploiement doit prévoir :

- sauvegarde ;
- version précédente ;
- rollback ;
- plan de reprise ;
- critères d’arrêt ;
- responsable ;
- approbation ;
- journalisation ;
- communication.

---

## 2.4 Les données financières doivent rester cohérentes

Lors d’une migration ou d’un déploiement, le système doit garantir :

- aucun double débit ;
- aucun double crédit ;
- aucune perte d’écriture ;
- aucune écriture orpheline ;
- aucun solde incorrect ;
- rapprochement complet ;
- contrôle avant et après migration ;
- conservation des références ;
- audit.

---

## 2.5 Une activation peut être progressive

Une fonction peut être activée selon :

- pays ;
- région ;
- ville ;
- application ;
- version ;
- agent ;
- commerçant ;
- appareil ;
- groupe d’utilisateurs ;
- partenaire ;
- pourcentage ;
- période ;
- niveau de risque.

---

# 3. Phases globales du lancement

Le lancement peut être structuré en huit phases :

1. préparation ;
2. environnement de démonstration ;
3. tests internes ;
4. Recette ;
5. pilote terrain ;
6. lancement limité ;
7. lancement national ;
8. extension régionale.

---

# 4. Phase 1 — Préparation

Cette phase doit couvrir :

- validation de l’architecture ;
- validation des besoins ;
- validation des partenaires ;
- validation des responsabilités ;
- préparation des environnements ;
- préparation des données ;
- préparation des contrats ;
- préparation de la sécurité ;
- préparation de la conformité ;
- préparation du support ;
- préparation de la communication ;
- préparation de la formation.

---

# 5. Conditions minimales avant lancement

Avant tout pilote, Mansa doit disposer au minimum de :

- backend fonctionnel ;
- API Gateway ;
- authentification ;
- wallet ;
- ledger ;
- KYC ;
- paiement ;
- transfert ;
- Cash Network ;
- notifications ;
- Admin Web ;
- support ;
- monitoring ;
- sauvegardes ;
- procédures d’incident ;
- environnement de Recette ;
- version mobile installable ;
- partenaires Sandbox ou Production prêts.

---

# 6. Environnements officiels

Les environnements recommandés sont :

- LOCAL ;
- DEVELOPMENT ;
- TEST ;
- DEMO ;
- RECETTE ;
- SANDBOX PARTENAIRE ;
- PREPRODUCTION ;
- PRODUCTION ;
- DISASTER RECOVERY.

---

# 7. Environnement Démo

L’environnement Démo doit permettre :

- présentation aux partenaires ;
- présentation aux investisseurs ;
- présentation à l’État ;
- présentation aux banques ;
- démonstration TPE ;
- démonstration Agent ;
- démonstration Client ;
- démonstration GAB ;
- transactions fictives ;
- utilisateurs fictifs ;
- rapports fictifs ;
- aucun impact financier réel.

---

# 8. Environnement Recette

La Recette doit permettre aux responsables métier de vérifier :

- parcours ;
- frais ;
- commissions ;
- limites ;
- rôles ;
- notifications ;
- documents ;
- rapports ;
- intégrations ;
- conformité ;
- sécurité ;
- expérience utilisateur.

---

# 9. Préproduction

La Préproduction doit être proche de la Production sur :

- architecture ;
- versions ;
- configurations ;
- sécurité ;
- bases ;
- monitoring ;
- réseau ;
- certificats ;
- charge ;
- procédures ;
- partenaires lorsque possible.

---

# 10. Production

La Production doit être réservée aux :

- utilisateurs réels ;
- transactions réelles ;
- partenaires réels ;
- fonds réels ;
- appareils autorisés ;
- versions approuvées ;
- administrateurs autorisés ;
- données vérifiées.

---

# 11. Gestion des branches

Organisation recommandée :

```text
main
→ Production

release/*
→ Préproduction

develop
→ Développement

feature/*
→ Fonctionnalités

hotfix/*
→ Correctifs urgents
```

---

# 12. Gestion des releases

Chaque release doit posséder :

- numéro de version ;
- numéro de build ;
- commit ;
- changelog ;
- fonctionnalités ;
- corrections ;
- migrations ;
- compatibilité ;
- risques ;
- résultats de tests ;
- approbations ;
- rollback ;
- responsable.

---

# 13. Types de releases

- version majeure ;
- version mineure ;
- patch ;
- hotfix ;
- version pilote ;
- version interne ;
- version bêta ;
- release candidate ;
- version nationale ;
- version pays.

---

# 14. Release Candidate

Une Release Candidate doit avoir passé :

- build ;
- lint ;
- tests unitaires ;
- tests d’intégration ;
- tests end-to-end ;
- tests sécurité ;
- tests performance ;
- tests de migration ;
- tests de rollback ;
- validation métier.

---

# 15. Quality Gate

La release ne doit pas avancer si :

- le build échoue ;
- une migration échoue ;
- le ledger est déséquilibré ;
- un test critique échoue ;
- une vulnérabilité critique reste ouverte ;
- une anomalie Blocker est présente ;
- le rollback n’est pas possible ;
- la Recette n’est pas validée ;
- les partenaires ne sont pas prêts.

---

# 16. Approbation de release

L’approbation peut suivre :

```text
Développement
→ QA
→ Sécurité
→ Conformité
→ Finance
→ Produit
→ Release Manager
→ Production
```

---

# 17. Déploiement progressif

Le déploiement progressif peut suivre :

```text
Équipe interne
→ 1 % des utilisateurs
→ 5 %
→ 10 %
→ 25 %
→ 50 %
→ 100 %
```

Chaque étape doit être validée avant la suivante.

---

# 18. Critères de passage entre les étapes

Exemples :

- taux de crash acceptable ;
- taux de paiement conforme ;
- aucun double débit ;
- aucune perte d’écriture ;
- latence acceptable ;
- erreurs sous seuil ;
- tickets support maîtrisés ;
- fraude sous contrôle ;
- partenaires stables ;
- aucun incident majeur.

---

# 19. Canary Release

La version Canary peut être réservée à :

- employés Mansa ;
- testeurs internes ;
- agents pilotes ;
- commerçants pilotes ;
- utilisateurs volontaires ;
- TPE pilotes ;
- GAB pilote.

---

# 20. Blue-Green Deployment

Mansa peut utiliser deux environnements :

```text
Blue
→ version active

Green
→ nouvelle version
```

Une fois Green validé, le trafic peut être basculé progressivement.

---

# 21. Rolling Deployment

Les instances peuvent être mises à jour progressivement afin d’éviter une interruption globale.

Le système doit :

- garder des instances disponibles ;
- vérifier les health checks ;
- arrêter en cas d’erreur ;
- restaurer la version précédente ;
- surveiller la capacité.

---

# 22. Feature Flags

Les feature flags permettent de déployer du code sans activer immédiatement la fonction.

Exemples :

- cartes virtuelles ;
- paiement QR ;
- GAB ;
- dépôt GAB ;
- crédit ;
- cashback ;
- Jini ;
- bourses ;
- services État ;
- pays supplémentaire.

---

# 23. Activation par pays

Une fonctionnalité peut être :

- active au Mali ;
- inactive ailleurs ;
- pilote dans une région ;
- réservée à un partenaire ;
- limitée à une version ;
- programmée à une date précise.

---

# 24. Activation par population

Ciblage possible :

- employés ;
- testeurs ;
- nouveaux clients ;
- anciens clients ;
- agents ;
- commerçants ;
- clients premium ;
- étudiants ;
- entreprises ;
- institutions.

---

# 25. Kill Switch

Chaque fonction critique doit pouvoir être désactivée rapidement.

Exemples :

- transferts ;
- dépôts ;
- retraits ;
- Mobile Money ;
- cartes ;
- GAB/DAB ;
- TPE ;
- partenaire précis ;
- pays précis ;
- type de transaction.

---

# 26. Déploiement backend

Le déploiement backend doit contrôler :

- compatibilité API ;
- base de données ;
- cache ;
- queues ;
- événements ;
- partenaires ;
- secrets ;
- certificats ;
- monitoring ;
- rollback.

---

# 27. Déploiement mobile

Le déploiement mobile doit gérer :

- iOS ;
- Android ;
- version minimale ;
- version recommandée ;
- publication stores ;
- TestFlight ;
- bêta Android ;
- mise à jour obligatoire ;
- compatibilité backend ;
- communication utilisateur.

---

# 28. Déploiement web

Le déploiement web doit gérer :

- build ;
- cache ;
- CDN ;
- variables ;
- version ;
- rollback ;
- compatibilité navigateur ;
- monitoring ;
- sécurité ;
- accessibilité.

---

# 29. Déploiement TPE

Le déploiement TPE doit gérer :

- modèle ;
- OS ;
- firmware ;
- application ;
- configuration ;
- certificat ;
- périphériques ;
- réseau ;
- caisse ;
- synchronisation ;
- rollback ;
- test de paiement.

---

# 30. Déploiement GAB/DAB

Le déploiement GAB/DAB doit gérer :

- modèle de machine ;
- logiciel ;
- firmware ;
- cassettes ;
- billets ;
- lecteur ;
- clavier PIN ;
- imprimante ;
- réseau ;
- certificat ;
- HSM ;
- caméra ;
- alarme ;
- transaction de test ;
- supervision ;
- rollback.

---

# 31. Déploiement Agent

Avant l’activation d’un agent, vérifier :

- KYC/KYB ;
- contrat ;
- formation ;
- appareil ;
- identité ;
- float ;
- caisse ;
- limites ;
- commissions ;
- localisation ;
- sécurité ;
- transaction de test.

---

# 32. Déploiement Commerce

Avant l’activation d’un commerçant, vérifier :

- KYB ;
- représentant ;
- compte de règlement ;
- point de vente ;
- employé ;
- TPE ;
- QR ;
- frais ;
- commissions ;
- formation ;
- support ;
- test d’encaissement.

---

# 33. Déploiement Client

Le lancement Client doit vérifier :

- inscription ;
- OTP ;
- KYC ;
- création wallet ;
- transfert ;
- paiement ;
- support ;
- notification ;
- récupération ;
- sécurité ;
- compatibilité appareil.

---

# 34. Déploiement cartes

Le lancement cartes nécessite :

- partenaire émetteur ;
- BIN sponsor ;
- personnalisation ;
- tokenisation ;
- réseau cartes ;
- autorisation ;
- PIN ;
- HSM ;
- dispute ;
- fraude ;
- rapprochement ;
- règlement ;
- support.

---

# 35. Déploiement Mobile Money

Avant activation :

- contrat opérateur ;
- API ;
- certificats ;
- Sandbox ;
- tests ;
- frais ;
- commissions ;
- limites ;
- timeout ;
- retry ;
- webhooks ;
- rapprochement ;
- support.

---

# 36. Déploiement bancaire

Avant activation :

- compte de cantonnement ;
- compte technique ;
- flux bancaires ;
- API ;
- fichiers ;
- règlement ;
- rapprochement ;
- reporting ;
- horaires ;
- SLA ;
- contacts ;
- procédure incident.

---

# 37. Déploiement État

Le lancement avec une institution publique doit commencer par un périmètre limité.

Exemples :

- un type d’amende ;
- un service ;
- une commune ;
- une école ;
- un programme de bourse ;
- un ministère ;
- un groupe d’agents publics.

---

# 38. Déploiement Éducation

Le pilote peut commencer avec :

- un établissement ;
- un groupe d’étudiants ;
- paiement scolaire ;
- carte étudiante ;
- bourse ;
- restauration ;
- transport ;
- portail administratif.

---

# 39. Stratégie de migration

La migration peut concerner :

- utilisateurs ;
- comptes ;
- wallets ;
- soldes ;
- historiques ;
- commerçants ;
- agents ;
- cartes ;
- appareils ;
- partenaires ;
- configurations ;
- documents ;
- rôles ;
- permissions.

---

# 40. Types de migration

- migration initiale ;
- migration progressive ;
- migration complète ;
- migration par lot ;
- migration en temps réel ;
- migration à double écriture ;
- migration pays par pays ;
- migration partenaire par partenaire.

---

# 41. Inventaire avant migration

Avant toute migration, établir :

- sources ;
- volumes ;
- formats ;
- propriétaires ;
- qualité ;
- doublons ;
- dépendances ;
- données sensibles ;
- règles ;
- historiques ;
- contraintes ;
- risques.

---

# 42. Mapping des données

Chaque champ source doit être relié à un champ cible.

Exemple :

```text
legacy_customer_id
→ externalReference

legacy_balance
→ openingBalance

legacy_status
→ accountStatus
```

---

# 43. Nettoyage des données

Avant migration :

- supprimer les doublons ;
- corriger les formats ;
- vérifier les identités ;
- harmoniser les numéros ;
- normaliser les adresses ;
- vérifier les devises ;
- corriger les statuts ;
- isoler les données invalides.

---

# 44. Données rejetées

Une donnée impossible à migrer doit être :

- identifiée ;
- isolée ;
- expliquée ;
- assignée ;
- corrigée ;
- validée ;
- auditée.

Elle ne doit pas être ignorée silencieusement.

---

# 45. Migration des utilisateurs

Elle doit vérifier :

- identifiant ;
- nom ;
- téléphone ;
- e-mail ;
- pays ;
- KYC ;
- statut ;
- langue ;
- consentement ;
- appareils ;
- historique.

---

# 46. Migration des soldes

La migration des soldes doit utiliser des écritures d’ouverture dans le ledger.

Elle doit conserver :

- référence source ;
- montant ;
- devise ;
- date ;
- utilisateur ;
- compte ;
- justification ;
- approbateur ;
- preuve.

---

# 47. Contrôle des soldes

Avant et après migration, comparer :

```text
Total source
=
Total cible
=
Total ledger d’ouverture
```

Tout écart doit être bloquant.

---

# 48. Migration du ledger

Si un ancien ledger existe, il faut décider entre :

- reprise complète ;
- reprise synthétique ;
- reprise des soldes uniquement ;
- conservation en archive ;
- accès en lecture seule.

---

# 49. Migration des historiques

Les historiques peuvent être :

- migrés complètement ;
- migrés partiellement ;
- archivés ;
- accessibles via un ancien système ;
- exportés dans un stockage sécurisé.

---

# 50. Migration des commerçants

Vérifier :

- identité entreprise ;
- KYB ;
- bénéficiaire effectif ;
- point de vente ;
- compte ;
- règlement ;
- TPE ;
- employés ;
- historique ;
- commissions.

---

# 51. Migration des agents

Vérifier :

- identité ;
- contrat ;
- point de vente ;
- float ;
- caisse ;
- commissions ;
- limites ;
- appareil ;
- historique ;
- statut.

---

# 52. Migration des cartes

Elle doit traiter :

- token ;
- statut ;
- client ;
- PAN tokenisé ;
- expiration ;
- réseau ;
- limites ;
- PIN ;
- historique ;
- opposition ;
- remplacement.

Les données carte sensibles ne doivent pas être migrées sans environnement sécurisé.

---

# 53. Migration des configurations

Les configurations doivent être :

- exportées ;
- versionnées ;
- validées ;
- comparées ;
- importées ;
- testées ;
- approuvées ;
- auditables.

---

# 54. Migration des rôles

Chaque rôle source doit être mappé vers :

- rôle cible ;
- permissions ;
- pays ;
- organisation ;
- périmètre ;
- durée ;
- niveau de risque.

---

# 55. Double Run

Pendant une période, deux systèmes peuvent fonctionner en parallèle.

Il faut comparer :

- soldes ;
- transactions ;
- statuts ;
- frais ;
- commissions ;
- notifications ;
- rapports ;
- rapprochement.

---

# 56. Shadow Mode

Le nouveau système peut traiter les opérations en arrière-plan sans produire l’effet financier final.

Cela permet de comparer ses résultats à l’ancien système.

---

# 57. Double écriture

La double écriture doit être utilisée avec prudence.

Elle doit gérer :

- ordre ;
- idempotence ;
- erreur partielle ;
- retry ;
- référence commune ;
- rapprochement ;
- désactivation ;
- audit.

---

# 58. Fenêtre de migration

La migration peut être réalisée :

- de nuit ;
- pendant une faible activité ;
- par pays ;
- par partenaire ;
- par produit ;
- par lot ;
- avec interruption contrôlée ;
- sans interruption si l’architecture le permet.

---

# 59. Gel des changements

Avant migration, certains changements peuvent être temporairement interdits :

- création de comptes ;
- changement de configuration ;
- changement de frais ;
- modification de rôles ;
- nouvelle carte ;
- changement de partenaire ;
- opération administrative sensible.

---

# 60. Sauvegarde avant migration

Avant migration :

- sauvegarde complète ;
- vérification ;
- copie secondaire ;
- test de restauration ;
- hash ;
- horodatage ;
- propriétaire ;
- preuve.

---

# 61. Rollback de migration

Le plan doit expliquer :

- quand revenir en arrière ;
- comment restaurer ;
- quelles données annuler ;
- comment traiter les transactions survenues ;
- qui décide ;
- comment communiquer ;
- comment rapprocher.

---

# 62. Validation après migration

Contrôles :

- nombre d’utilisateurs ;
- nombre de comptes ;
- nombre de wallets ;
- soldes ;
- écritures ;
- commerçants ;
- agents ;
- appareils ;
- rôles ;
- documents ;
- erreurs ;
- performances.

---

# 63. Réconciliation post-migration

La réconciliation doit comparer :

- source ;
- cible ;
- banque ;
- Mobile Money ;
- réseau cartes ;
- ledger ;
- rapports ;
- comptes de cantonnement.

---

# 64. Pilote terrain

Le pilote doit avoir :

- durée ;
- zone ;
- utilisateurs ;
- agents ;
- commerçants ;
- TPE ;
- GAB ;
- partenaires ;
- plafonds ;
- fonctions ;
- critères ;
- support ;
- monitoring ;
- plan de sortie.

---

# 65. Taille du pilote

Exemple de démarrage :

- 100 à 1 000 clients ;
- 5 à 20 agents ;
- 10 à 50 commerçants ;
- 3 TPE ;
- 1 GAB ;
- une banque partenaire ;
- un opérateur Mobile Money ;
- une zone géographique limitée.

Ces chiffres restent entièrement configurables.

---

# 66. Fonctions du pilote

Le pilote peut commencer avec :

- inscription ;
- KYC ;
- transfert ;
- paiement QR ;
- paiement TPE ;
- dépôt Agent ;
- retrait Agent ;
- consultation ;
- reçus ;
- notifications ;
- support.

---

# 67. Plafonds du pilote

Les plafonds peuvent être réduits pour :

- dépôt ;
- retrait ;
- transfert ;
- paiement ;
- nombre d’opérations ;
- volume journalier ;
- commissions ;
- remboursement.

---

# 68. Utilisateurs pilotes

Les utilisateurs pilotes doivent être :

- identifiés ;
- informés ;
- formés ;
- consentants ;
- accompagnés ;
- surveillés ;
- capables de signaler rapidement un problème.

---

# 69. Agents pilotes

Ils doivent recevoir :

- formation ;
- appareil ;
- float initial ;
- caisse ;
- procédures ;
- support direct ;
- contacts d’urgence ;
- limites ;
- rémunération ;
- suivi quotidien.

---

# 70. Commerçants pilotes

Ils doivent recevoir :

- formation ;
- QR ;
- TPE si prévu ;
- documentation ;
- support ;
- procédure de remboursement ;
- procédure de clôture ;
- compte de règlement ;
- suivi.

---

# 71. GAB pilote

Le premier GAB doit être installé dans un lieu :

- sécurisé ;
- fréquenté ;
- accessible ;
- connecté ;
- alimenté ;
- surveillé ;
- facilement maintenable ;
- proche d’une équipe d’intervention.

---

# 72. Supervision du pilote

Pendant le pilote, surveiller :

- utilisateurs actifs ;
- transactions ;
- échecs ;
- fraudes ;
- incidents ;
- latence ;
- disponibilité ;
- cash Agent ;
- cash GAB ;
- float ;
- tickets ;
- satisfaction.

---

# 73. Réunion quotidienne pilote

Une réunion quotidienne peut couvrir :

- incidents ;
- anomalies ;
- volumes ;
- utilisateurs ;
- agents ;
- commerçants ;
- partenaires ;
- cash ;
- fraude ;
- actions ;
- décision de poursuivre.

---

# 74. Critères de réussite du pilote

Exemples :

- aucun incident financier majeur ;
- ledger équilibré ;
- disponibilité conforme ;
- taux de succès élevé ;
- agents opérationnels ;
- utilisateurs satisfaits ;
- rapprochement correct ;
- fraude maîtrisée ;
- support réactif ;
- partenaires stables.

---

# 75. Critères d’arrêt du pilote

Le pilote doit pouvoir être suspendu en cas de :

- double débit ;
- perte d’argent ;
- faille critique ;
- ledger déséquilibré ;
- fraude importante ;
- panne prolongée ;
- partenaire instable ;
- problème réglementaire ;
- impossibilité de rapprocher les comptes.

---

# 76. Passage au lancement limité

Après le pilote, Mansa peut élargir à :

- plusieurs quartiers ;
- plusieurs villes ;
- plusieurs milliers d’utilisateurs ;
- davantage d’agents ;
- davantage de commerçants ;
- plus de TPE ;
- plusieurs GAB/DAB ;
- nouvelles fonctionnalités.

---

# 77. Lancement national

Le lancement national nécessite :

- capacité technique ;
- support national ;
- couverture agents ;
- partenaires stables ;
- liquidité ;
- maintenance ;
- sécurité ;
- conformité ;
- communication ;
- monitoring ;
- PCA/PRA ;
- procédures d’urgence.

---

# 78. Stratégie géographique

Déploiement possible :

```text
Bamako pilote
→ grandes villes
→ capitales régionales
→ villes secondaires
→ zones rurales
→ couverture nationale
```

---

# 79. Réseau Agent

Le réseau Agent peut être développé par :

- zones ;
- densité de population ;
- volume attendu ;
- distance ;
- couverture bancaire ;
- présence Mobile Money ;
- sécurité ;
- disponibilité de cash ;
- proximité des marchés.

---

# 80. Réseau TPE

Les premiers TPE peuvent être placés chez :

- supermarchés ;
- pharmacies ;
- stations-service ;
- restaurants ;
- hôtels ;
- boutiques ;
- écoles ;
- administrations ;
- transporteurs ;
- commerces à fort volume.

---

# 81. Réseau GAB/DAB

Le déploiement doit distinguer :

- GAB complets ;
- DAB de retrait ;
- GAB avec dépôt ;
- GAB avec recyclage ;
- machines en agence ;
- machines hors agence ;
- machines mobiles éventuelles.

---

# 82. Stratégie de placement GAB/DAB

Critères :

- trafic ;
- sécurité ;
- électricité ;
- réseau ;
- accessibilité ;
- maintenance ;
- rentabilité ;
- proximité d’un point de cash ;
- couverture existante ;
- besoin local.

---

# 83. Cash Management

Le lancement doit prévoir :

- approvisionnement Agent ;
- approvisionnement GAB/DAB ;
- collecte ;
- convoyage ;
- assurance ;
- prévision ;
- seuils ;
- alertes ;
- rapprochement ;
- incidents.

---

# 84. Formation

Les formations doivent couvrir :

- employés Mansa ;
- support ;
- agents ;
- commerçants ;
- administrateurs ;
- techniciens ;
- partenaires ;
- convoyeurs ;
- équipes Finance ;
- équipes Fraude.

---

# 85. Formation Agents

Contenu :

- ouverture ;
- dépôt ;
- retrait ;
- authentification client ;
- float ;
- caisse ;
- commission ;
- reçu ;
- fraude ;
- incident ;
- fermeture ;
- support.

---

# 86. Formation Commerçants

Contenu :

- encaissement ;
- TPE ;
- QR ;
- remboursement ;
- employé ;
- caisse ;
- règlement ;
- fraude ;
- sécurité ;
- support.

---

# 87. Formation Support

Contenu :

- applications ;
- parcours ;
- erreurs ;
- transactions ;
- KYC ;
- Agent ;
- Commerce ;
- TPE ;
- GAB/DAB ;
- fraude ;
- incidents ;
- escalades.

---

# 88. Formation Administrateurs

Contenu :

- rôles ;
- permissions ;
- configurations ;
- frais ;
- commissions ;
- plafonds ;
- utilisateurs ;
- partenaires ;
- incidents ;
- audits ;
- double validation.

---

# 89. Certification interne

Les rôles sensibles peuvent nécessiter une certification avant accès.

Exemples :

- agent ;
- technicien GAB ;
- administrateur ;
- analyste fraude ;
- opérateur Finance ;
- support niveau 2 ;
- convoyeur.

---

# 90. Documentation de lancement

Documents nécessaires :

- runbooks ;
- guides ;
- procédures ;
- FAQ ;
- scripts support ;
- procédures de rollback ;
- procédures incident ;
- procédures cash ;
- procédures sécurité ;
- contacts ;
- escalades.

---

# 91. Communication interne

Avant lancement, communiquer :

- date ;
- périmètre ;
- version ;
- risques ;
- contacts ;
- horaires ;
- responsabilités ;
- procédures ;
- canaux d’urgence.

---

# 92. Communication client

Elle peut inclure :

- disponibilité ;
- fonctions ;
- frais ;
- sécurité ;
- téléchargement ;
- assistance ;
- limitations ;
- conditions ;
- nouveautés ;
- zones couvertes.

---

# 93. Communication partenaire

Elle doit préciser :

- date ;
- version ;
- environnement ;
- API ;
- certificats ;
- tests ;
- contacts ;
- SLA ;
- procédure incident ;
- rollback ;
- maintenance.

---

# 94. Support de lancement

Pendant le lancement, prévoir :

- war room ;
- support renforcé ;
- horaires élargis ;
- astreinte ;
- canaux directs ;
- responsables ;
- tableaux de bord ;
- points réguliers ;
- escalade rapide.

---

# 95. War Room

La War Room peut réunir :

- Produit ;
- Développement ;
- QA ;
- Sécurité ;
- Finance ;
- Fraude ;
- Support ;
- Opérations ;
- Partenaires ;
- Direction.

---

# 96. Hypercare

La période d’Hypercare suit immédiatement le lancement.

Elle peut durer :

- quelques jours ;
- deux semaines ;
- un mois ;
- davantage selon le risque.

---

# 97. Activités Hypercare

- surveillance renforcée ;
- revue quotidienne ;
- support prioritaire ;
- correction rapide ;
- analyse des incidents ;
- rapprochement quotidien ;
- suivi cash ;
- suivi partenaires ;
- suivi satisfaction.

---

# 98. Monitoring de lancement

Tableaux de bord essentiels :

- disponibilité ;
- latence ;
- erreurs ;
- utilisateurs ;
- transactions ;
- paiements ;
- transferts ;
- dépôts ;
- retraits ;
- ledger ;
- cash ;
- float ;
- fraude ;
- support ;
- partenaires.

---

# 99. Indicateurs de lancement

Exemples :

- inscriptions ;
- KYC validés ;
- utilisateurs actifs ;
- transactions réussies ;
- volume ;
- valeur ;
- agents actifs ;
- commerçants actifs ;
- TPE actifs ;
- GAB/DAB actifs ;
- incidents ;
- fraude ;
- satisfaction.

---

# 100. Seuils d’alerte

Exemples :

- taux d’échec élevé ;
- baisse de disponibilité ;
- augmentation des tickets ;
- écart ledger ;
- écart de rapprochement ;
- cash faible ;
- float faible ;
- fraude anormale ;
- partenaire indisponible ;
- crash mobile.

---

# 101. Incident de lancement

Chaque incident doit contenir :

- identifiant ;
- heure ;
- service ;
- pays ;
- impact ;
- utilisateurs ;
- transactions ;
- responsable ;
- mitigation ;
- résolution ;
- communication ;
- preuve ;
- post-mortem.

---

# 102. Gravité

- SEV0 : critique national ;
- SEV1 : critique majeur ;
- SEV2 : important ;
- SEV3 : limité ;
- SEV4 : mineur.

---

# 103. Incident financier

Un incident financier exige :

- blocage si nécessaire ;
- protection du ledger ;
- identification des transactions ;
- rapprochement ;
- correction contrôlée ;
- validation Finance ;
- audit ;
- notification ;
- compensation éventuelle.

---

# 104. Incident de sécurité

Il peut déclencher :

- suspension ;
- révocation ;
- rotation de clés ;
- blocage d’appareils ;
- coupure de partenaire ;
- enquête ;
- conservation de preuves ;
- communication contrôlée.

---

# 105. Incident GAB/DAB

Il peut concerner :

- billet non délivré ;
- débit sans distribution ;
- billet bloqué ;
- cassette vide ;
- carte retenue ;
- panne réseau ;
- panne électrique ;
- fraude ;
- vandalisme ;
- alarme.

---

# 106. Incident Agent

Il peut concerner :

- float insuffisant ;
- caisse incorrecte ;
- fraude ;
- appareil perdu ;
- faux dépôt ;
- retrait contesté ;
- agent indisponible ;
- cash insuffisant ;
- sécurité du point de vente.

---

# 107. Rollback applicatif

Le rollback doit pouvoir restaurer :

- backend ;
- web ;
- mobile géré ;
- TPE ;
- GAB/DAB ;
- configuration ;
- feature flag ;
- API ;
- firmware lorsque possible.

---

# 108. Rollback fonctionnel

Une fonction peut être désactivée sans restaurer toute l’application.

Exemples :

- paiement QR ;
- dépôt GAB ;
- retrait sans carte ;
- Mobile Money ;
- cashback ;
- carte virtuelle ;
- service État.

---

# 109. Rollback de configuration

Il doit restaurer :

- ancienne version ;
- frais ;
- commissions ;
- plafonds ;
- partenaire ;
- règles ;
- textes ;
- workflows ;
- feature flags.

---

# 110. Décision Go / No-Go

Avant lancement, une réunion doit décider :

- GO ;
- GO WITH CONDITIONS ;
- DELAY ;
- NO-GO.

---

# 111. Critères Go

- tests validés ;
- sécurité validée ;
- Finance validée ;
- partenaires prêts ;
- support prêt ;
- données prêtes ;
- monitoring actif ;
- rollback testé ;
- responsabilités claires ;
- aucun Blocker.

---

# 112. Critères No-Go

- ledger non fiable ;
- migration non validée ;
- partenaire non prêt ;
- faille critique ;
- absence de rollback ;
- support non prêt ;
- conformité non validée ;
- rapprochement impossible ;
- incident ouvert critique.

---

# 113. Checklist de lancement

La checklist doit inclure :

- code ;
- tests ;
- sécurité ;
- données ;
- partenaires ;
- certificats ;
- clés ;
- configuration ;
- monitoring ;
- sauvegardes ;
- support ;
- communication ;
- rollback ;
- validation ;
- contacts.

---

# 114. Approvals

Les validations peuvent être exigées de :

- Direction ;
- Produit ;
- Technique ;
- QA ;
- Sécurité ;
- Finance ;
- Conformité ;
- Opérations ;
- Support ;
- Partenaire bancaire.

---

# 115. Double validation

Doit être requise pour :

- lancement Production ;
- migration des soldes ;
- modification du ledger ;
- activation nationale ;
- rollback global ;
- changement de frais ;
- mise en service GAB ;
- rotation de clés ;
- ouverture d’un nouveau pays.

---

# 116. Lancement d’un nouveau pays

Étapes :

- analyse réglementaire ;
- entité locale ;
- partenaires ;
- devise ;
- langue ;
- KYC ;
- KYB ;
- produits ;
- frais ;
- taxes ;
- agents ;
- commerçants ;
- support ;
- infrastructure ;
- pilote ;
- lancement.

---

# 117. Configuration pays

Chaque pays doit disposer de :

- devise ;
- langues ;
- formats ;
- fuseau ;
- partenaires ;
- frais ;
- commissions ;
- plafonds ;
- KYC ;
- KYB ;
- documents ;
- support ;
- calendriers ;
- règles.

---

# 118. Migration pays

Une migration pays doit rester isolée des autres pays.

Elle doit avoir :

- données ;
- configurations ;
- secrets ;
- certificats ;
- partenaires ;
- rapports ;
- rollback ;
- audit propres.

---

# 119. Passage à l’échelle

La montée en charge doit être testée sur :

- utilisateurs ;
- paiements ;
- transferts ;
- agents ;
- commerçants ;
- TPE ;
- GAB/DAB ;
- notifications ;
- KYC ;
- rapports ;
- support.

---

# 120. Capacité

La plateforme doit prévoir :

- capacité actuelle ;
- capacité cible ;
- seuil d’alerte ;
- marge ;
- autoscaling ;
- plan d’augmentation ;
- coûts ;
- dépendances.

---

# 121. FinOps de lancement

Le suivi des coûts doit couvrir :

- cloud ;
- SMS ;
- KYC ;
- stockage ;
- données ;
- cartes ;
- TPE ;
- GAB/DAB ;
- support ;
- partenaires ;
- licences ;
- sécurité.

---

# 122. Budget pilote

Le budget pilote peut inclure :

- développement ;
- intégration ;
- infrastructure ;
- appareils ;
- TPE ;
- GAB ;
- agents ;
- marketing ;
- support ;
- formation ;
- sécurité ;
- assurance ;
- maintenance ;
- liquidité.

---

# 123. Risques de lancement

Risques principaux :

- produit incomplet ;
- architecture instable ;
- fraude ;
- manque de cash ;
- manque de float ;
- partenaire indisponible ;
- mauvaise formation ;
- support insuffisant ;
- faible adoption ;
- surcharge ;
- erreur réglementaire ;
- mauvaise communication.

---

# 124. Réduction des risques

Mesures :

- pilote ;
- plafonds ;
- déploiement progressif ;
- monitoring ;
- formation ;
- support ;
- fallback ;
- multi-fournisseurs ;
- sauvegardes ;
- rollback ;
- communication ;
- audit ;
- revue quotidienne.

---

# 125. Modèles principaux

- LaunchPlan
- LaunchPhase
- Release
- Deployment
- DeploymentTarget
- FeatureRollout
- MigrationPlan
- MigrationBatch
- MigrationMapping
- MigrationError
- ReconciliationResult
- PilotProgram
- PilotParticipant
- GoNoGoDecision
- LaunchChecklist
- RollbackPlan
- LaunchIncident
- HypercarePeriod
- LaunchMetric
- LaunchApproval
- LaunchAudit

---

# 126. API

Exemples :

```http
GET    /launch/plans
POST   /launch/plans
GET    /launch/phases
POST   /launch/go-no-go

GET    /releases
POST   /releases
POST   /releases/{id}/approve
POST   /releases/{id}/deploy
POST   /releases/{id}/rollback

GET    /migrations
POST   /migrations
POST   /migrations/{id}/validate
POST   /migrations/{id}/execute
POST   /migrations/{id}/rollback

GET    /pilots
POST   /pilots
POST   /pilots/{id}/start
POST   /pilots/{id}/stop

GET    /launch/metrics
GET    /launch/incidents
GET    /launch/audit
```

---

# 127. Webhooks internes

Événements possibles :

```text
launch.plan.created
launch.phase.started
launch.phase.completed
launch.go.approved
launch.no_go.declared
release.deployment.started
release.deployment.completed
release.deployment.failed
release.rollback.started
release.rollback.completed
migration.started
migration.completed
migration.failed
migration.reconciliation.break
pilot.started
pilot.suspended
pilot.completed
hypercare.started
hypercare.completed
```

---

# 128. Administration centrale

L’administration doit pouvoir gérer :

- plans ;
- phases ;
- releases ;
- migrations ;
- pilotes ;
- utilisateurs pilotes ;
- agents pilotes ;
- commerçants pilotes ;
- TPE pilotes ;
- GAB pilotes ;
- feature flags ;
- configurations ;
- critères Go/No-Go ;
- approbations ;
- incidents ;
- indicateurs ;
- rollbacks ;
- audits.

---

# 129. Rôles

Exemples :

```text
LAUNCH_DIRECTOR
RELEASE_MANAGER
MIGRATION_MANAGER
PILOT_MANAGER
COUNTRY_LAUNCH_MANAGER
OPERATIONS_MANAGER
QA_MANAGER
SECURITY_APPROVER
FINANCE_APPROVER
COMPLIANCE_APPROVER
SUPPORT_MANAGER
ROLLBACK_OPERATOR
AUDITOR
VIEWER
```

---

# 130. Permissions

Exemples :

```text
launch.plan.read
launch.plan.manage
launch.phase.start
launch.phase.stop
launch.go_no_go.approve
release.deploy
release.rollback
migration.create
migration.execute
migration.approve
pilot.manage
pilot.suspend
feature_rollout.manage
launch.incident.manage
launch.report.read
launch.audit.read
```

---

# 131. Audit

Le journal doit enregistrer :

- utilisateur ;
- rôle ;
- plan ;
- release ;
- migration ;
- pilote ;
- pays ;
- environnement ;
- action ;
- ancienne valeur ;
- nouvelle valeur ;
- date ;
- heure ;
- motif ;
- approbateur ;
- résultat ;
- preuve.

---

# 132. Immutabilité

Les preuves de lancement doivent être protégées contre :

- modification ;
- suppression ;
- falsification ;
- remplacement ;
- réécriture ;
- changement de résultat ;
- export non autorisé.

---

# 133. Tests

- tests de release ;
- tests de pipeline ;
- tests de déploiement ;
- tests Canary ;
- tests Blue-Green ;
- tests Rolling ;
- tests feature flags ;
- tests kill switch ;
- tests backend ;
- tests mobile ;
- tests web ;
- tests TPE ;
- tests GAB/DAB ;
- tests Agent ;
- tests Commerce ;
- tests cartes ;
- tests Mobile Money ;
- tests bancaires ;
- tests migration ;
- tests mapping ;
- tests nettoyage ;
- tests soldes ;
- tests ledger ;
- tests double run ;
- tests shadow ;
- tests double écriture ;
- tests rollback ;
- tests pilote ;
- tests plafonds ;
- tests monitoring ;
- tests incidents ;
- tests Hypercare ;
- tests Go/No-Go ;
- tests multi-pays ;
- tests de capacité ;
- tests de sécurité ;
- tests d’audit.

---

# 134. Règles métier

1. Aucun lancement national sans pilote.
2. Toute release est versionnée.
3. Toute release critique est approuvée.
4. Tout déploiement possède un rollback.
5. Toute migration possède une sauvegarde.
6. Toute migration de solde utilise le ledger.
7. Les totaux source et cible doivent correspondre.
8. Toute erreur de migration est tracée.
9. Les fonctions sont activables progressivement.
10. Un kill switch est prévu pour les fonctions critiques.
11. Le pilote utilise des plafonds limités.
12. Les agents pilotes sont formés.
13. Les commerçants pilotes sont accompagnés.
14. Le premier GAB est fortement supervisé.
15. Les indicateurs sont suivis en temps réel.
16. Les incidents financiers sont prioritaires.
17. Les partenaires doivent être prêts avant activation.
18. Les environnements sont séparés.
19. Les configurations Production sont approuvées.
20. Le lancement peut être interrompu.
21. L’Hypercare est obligatoire après lancement.
22. La montée en charge est progressive.
23. Chaque nouveau pays commence par un pilote.
24. Le demandeur ne valide pas seul une mise en production critique.
25. Les audits sont immuables.

---

# 135. Critères d’acceptation

La stratégie de lancement, migration et déploiement progressif de Mansa est validée lorsque :

- les phases de lancement sont définies ;
- les environnements sont séparés ;
- l’environnement Démo est disponible ;
- la Recette est disponible ;
- la Préproduction est proche de la Production ;
- les branches sont organisées ;
- les releases sont versionnées ;
- les Release Candidates sont testées ;
- les Quality Gates sont actifs ;
- les validations sont définies ;
- le déploiement progressif est supporté ;
- le Canary est supporté ;
- le Blue-Green est supporté ;
- le Rolling Deployment est supporté ;
- les feature flags sont disponibles ;
- l’activation par pays fonctionne ;
- l’activation par population fonctionne ;
- le kill switch fonctionne ;
- le backend peut être déployé ;
- le mobile peut être déployé ;
- le web peut être déployé ;
- les TPE peuvent être déployés ;
- les GAB/DAB peuvent être déployés ;
- les agents peuvent être activés ;
- les commerçants peuvent être activés ;
- les cartes peuvent être lancées ;
- Mobile Money peut être lancé ;
- les banques peuvent être intégrées ;
- les institutions peuvent être lancées progressivement ;
- les établissements scolaires peuvent être pilotés ;
- les migrations sont planifiées ;
- les données sources sont inventoriées ;
- les mappings sont définis ;
- les données sont nettoyées ;
- les erreurs sont isolées ;
- les utilisateurs peuvent être migrés ;
- les soldes sont migrés par écritures d’ouverture ;
- les totaux sont rapprochés ;
- le ledger peut être repris ;
- les historiques sont traités ;
- les commerçants sont migrables ;
- les agents sont migrables ;
- les cartes sont migrables ;
- les configurations sont migrables ;
- les rôles sont migrables ;
- le Double Run est possible ;
- le Shadow Mode est possible ;
- la double écriture est contrôlée ;
- les fenêtres de migration sont définies ;
- le gel des changements est disponible ;
- les sauvegardes sont testées ;
- le rollback de migration est défini ;
- la validation post-migration est automatisée ;
- la réconciliation post-migration fonctionne ;
- le pilote terrain est structuré ;
- les participants pilotes sont identifiés ;
- les fonctions pilotes sont définies ;
- les plafonds pilotes sont configurables ;
- les agents pilotes sont formés ;
- les commerçants pilotes sont formés ;
- le GAB pilote est supervisé ;
- les indicateurs pilotes sont suivis ;
- les réunions quotidiennes sont organisées ;
- les critères de réussite sont définis ;
- les critères d’arrêt sont définis ;
- le lancement limité est prévu ;
- le lancement national est préparé ;
- la stratégie géographique est définie ;
- le réseau Agent est planifié ;
- le réseau TPE est planifié ;
- le réseau GAB/DAB est planifié ;
- le Cash Management est défini ;
- les formations sont préparées ;
- les certifications internes sont prévues ;
- la documentation de lancement est disponible ;
- la communication interne est préparée ;
- la communication Client est préparée ;
- la communication partenaire est préparée ;
- le support de lancement est renforcé ;
- la War Room est définie ;
- l’Hypercare est défini ;
- le monitoring est actif ;
- les seuils d’alerte sont configurés ;
- les incidents sont gérés ;
- les incidents financiers sont encadrés ;
- les incidents de sécurité sont encadrés ;
- les incidents GAB/DAB sont encadrés ;
- les incidents Agent sont encadrés ;
- les rollbacks applicatifs sont possibles ;
- les rollbacks fonctionnels sont possibles ;
- les rollbacks de configuration sont possibles ;
- les critères Go/No-Go sont définis ;
- les checklists sont disponibles ;
- les approbations critiques sont protégées ;
- les nouveaux pays peuvent être lancés progressivement ;
- la configuration par pays est disponible ;
- les migrations pays sont isolées ;
- la montée en charge est testée ;
- la capacité est mesurée ;
- les coûts sont suivis ;
- les risques sont identifiés ;
- les audits sont immuables ;
- les tests couvrent les parcours essentiels.
