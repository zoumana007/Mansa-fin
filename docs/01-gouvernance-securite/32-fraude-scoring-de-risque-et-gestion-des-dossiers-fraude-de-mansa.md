# 32 — Fraude, scoring de risque et gestion des dossiers fraude de Mansa

## 1. Objet du document

Ce document définit l’architecture officielle de prévention, détection et gestion de la fraude de Mansa.

Il couvre :

- la fraude à l’identité ;
- la fraude au compte ;
- la fraude aux paiements ;
- la fraude carte ;
- la fraude Mobile Money ;
- la fraude commerçant ;
- la fraude TPE ;
- la fraude aux remboursements ;
- la fraude interne ;
- la fraude partenaire ;
- la fraude sur les services publics ;
- le scoring de risque ;
- les règles ;
- les modèles ;
- les signaux ;
- les alertes ;
- les blocages ;
- les vérifications renforcées ;
- les dossiers fraude ;
- les revues manuelles ;
- les contestations ;
- les preuves ;
- les pertes ;
- les recouvrements ;
- l’audit ;
- les obligations multi-pays.

L’objectif est de permettre à Mansa de :

- détecter les comportements suspects ;
- protéger les utilisateurs légitimes ;
- réduire les pertes financières ;
- limiter les faux positifs ;
- prévenir les abus internes ;
- adapter les contrôles au contexte ;
- expliquer les décisions ;
- répondre rapidement aux incidents ;
- conserver une traçabilité complète.

---

# 2. Principes fondamentaux

## 2.1 Approche multicouche

La détection de fraude ne doit pas dépendre d’un seul contrôle.

Elle doit combiner :

- identité ;
- appareil ;
- session ;
- comportement ;
- transaction ;
- bénéficiaire ;
- commerçant ;
- localisation ;
- partenaire ;
- historique ;
- règles ;
- modèles ;
- revue humaine.

---

## 2.2 Le risque doit être évalué avant, pendant et après l’opération

Le système doit pouvoir intervenir :

- avant l’autorisation ;
- pendant le traitement ;
- après confirmation ;
- lors du rapprochement ;
- lors d’un remboursement ;
- lors d’une contestation ;
- lors d’une revue périodique.

---

## 2.3 Protection sans blocage excessif

Le système doit chercher à réduire :

- la fraude ;
- les pertes ;
- les abus ;

sans bloquer injustement les utilisateurs légitimes.

Les faux positifs doivent être mesurés.

---

## 2.4 Décisions explicables

Toute décision importante doit pouvoir indiquer :

- signaux utilisés ;
- règles déclenchées ;
- score ;
- seuil ;
- version ;
- résultat ;
- date ;
- action ;
- possibilité de revue.

---

## 2.5 Aucune suppression de preuve

Une alerte, une décision ou une action fraude ne doit pas être supprimée silencieusement.

Elle doit rester :

- historisée ;
- auditable ;
- rattachée à un dossier ;
- liée à la transaction ou à l’utilisateur concerné.

---

# 3. Typologies de fraude

## 3.1 Fraude à l’identité

Exemples :

- faux document ;
- document volé ;
- identité synthétique ;
- usurpation ;
- selfie falsifié ;
- preuve de vie contournée ;
- réutilisation d’identité ;
- multiples comptes avec la même identité.

---

## 3.2 Account Takeover

Exemples :

- mot de passe compromis ;
- téléphone volé ;
- SIM swap ;
- récupération de compte frauduleuse ;
- appareil inconnu ;
- changement soudain de comportement ;
- modification de bénéficiaire ;
- transfert immédiat après connexion.

---

## 3.3 Fraude au paiement

Exemples :

- carte volée ;
- paiement non autorisé ;
- compte compromis ;
- paiement répété ;
- montant inhabituel ;
- bénéficiaire risqué ;
- paiement transfrontalier anormal ;
- tentative automatisée.

---

## 3.4 Fraude Mobile Money

Exemples :

- faux numéro ;
- SIM frauduleuse ;
- cash-out anormal ;
- utilisation de plusieurs comptes ;
- confirmation falsifiée ;
- retrait immédiat ;
- opération circulaire ;
- complicité agent.

---

## 3.5 Fraude commerçant

Exemples :

- commerce fictif ;
- volume anormal ;
- fausse vente ;
- auto-paiement ;
- remboursements abusifs ;
- fractionnement ;
- catégorie incorrecte ;
- blanchiment via TPE ;
- collusion client-commerçant.

---

## 3.6 Fraude TPE

Exemples :

- terminal compromis ;
- terminal déplacé ;
- faux terminal ;
- application modifiée ;
- paiement hors ligne abusif ;
- collusion employé ;
- transaction dupliquée ;
- manipulation des reçus ;
- certificat invalide.

---

## 3.7 Fraude aux remboursements

Exemples :

- remboursement multiple ;
- remboursement sans vente ;
- remboursement supérieur ;
- changement de compte de destination ;
- collusion employé-client ;
- remboursement après chargeback ;
- remboursement automatisé abusif.

---

## 3.8 Fraude interne

Exemples :

- accès abusif ;
- modification de limite ;
- levée injustifiée de blocage ;
- suppression de trace ;
- export massif ;
- changement de bénéficiaire ;
- utilisation d’accès d’urgence ;
- manipulation de remboursement ;
- collusion avec un partenaire.

---

## 3.9 Fraude partenaire

Exemples :

- webhook falsifié ;
- double confirmation ;
- règlement incohérent ;
- taux incorrect ;
- opération absente ;
- identifiant réutilisé ;
- manipulation de statut ;
- réponse frauduleuse.

---

## 3.10 Fraude aux services publics

Exemples :

- faux agent ;
- fausse amende ;
- modification du montant ;
- faux dossier ;
- détournement de paiement ;
- suppression de contravention ;
- usurpation d’institution ;
- faux bénéficiaire de bourse.

---

# 4. Signaux de risque

## 4.1 Signaux d’identité

- identité déjà utilisée ;
- document expiré ;
- document falsifié ;
- incohérence nom/date ;
- photo incompatible ;
- plusieurs comptes ;
- pays incohérent ;
- bénéficiaire effectif suspect.

---

## 4.2 Signaux d’appareil

- nouvel appareil ;
- appareil rooté ;
- jailbreak ;
- émulateur ;
- device fingerprint partagé ;
- appareil lié à plusieurs comptes ;
- version obsolète ;
- application modifiée ;
- localisation inhabituelle.

---

## 4.3 Signaux réseau

- IP risquée ;
- proxy ;
- VPN ;
- TOR ;
- bot ;
- pays inattendu ;
- changement fréquent d’IP ;
- réseau associé à plusieurs comptes ;
- automatisation suspecte.

---

## 4.4 Signaux comportementaux

- vitesse de navigation anormale ;
- clics automatisés ;
- création rapide de bénéficiaires ;
- changement de mot de passe suivi d’un transfert ;
- consultation inhabituelle ;
- activité nocturne inhabituelle ;
- répétition d’échecs ;
- changement soudain d’usage.

---

## 4.5 Signaux transactionnels

- montant élevé ;
- montant inhabituel ;
- fréquence élevée ;
- fractionnement ;
- nombreux bénéficiaires ;
- retrait immédiat ;
- paiement circulaire ;
- remboursement rapide ;
- activité internationale inhabituelle ;
- devise inhabituelle.

---

## 4.6 Signaux commerçants

- hausse brutale du volume ;
- panier moyen incohérent ;
- taux de remboursement élevé ;
- taux de chargeback élevé ;
- activité hors catégorie ;
- TPE éloigné ;
- nombreuses cartes différentes ;
- transactions répétées du même montant.

---

## 4.7 Signaux internes

- accès en dehors des horaires ;
- export massif ;
- consultation de comptes sans ticket ;
- modification répétée de limites ;
- usage d’accès d’urgence ;
- approbations inhabituelles ;
- tentative de suppression de trace ;
- accès multi-pays non justifié.

---

# 5. Profil de risque

Chaque entité peut avoir un profil de risque.

Entités concernées :

- utilisateur ;
- organisation ;
- commerçant ;
- établissement ;
- employé ;
- TPE ;
- carte ;
- appareil ;
- bénéficiaire ;
- partenaire ;
- agent public ;
- transaction.

---

# 6. Score de risque

Le score peut être calculé sur une échelle définie.

Exemple :

```text
0 à 29   : faible
30 à 59  : modéré
60 à 79  : élevé
80 à 100 : critique
```

Les seuils doivent être configurables par :

- pays ;
- produit ;
- canal ;
- partenaire ;
- type d’utilisateur ;
- montant ;
- environnement ;
- période.

---

# 7. Composition du score

Le score peut inclure :

- risque identité ;
- risque appareil ;
- risque réseau ;
- risque comportemental ;
- risque transactionnel ;
- risque bénéficiaire ;
- risque commerçant ;
- risque géographique ;
- risque partenaire ;
- historique fraude ;
- résultat KYC ;
- signaux AML.

---

# 8. Versionnement du scoring

Chaque calcul doit contenir :

- version du modèle ;
- version des règles ;
- date ;
- score ;
- facteurs ;
- seuil ;
- action ;
- environnement ;
- pays ;
- corrélation.

---

# 9. Règles de fraude

Chaque règle doit contenir :

- identifiant ;
- nom ;
- description ;
- domaine ;
- pays ;
- seuil ;
- fenêtre ;
- priorité ;
- statut ;
- date d’effet ;
- date d’expiration ;
- action ;
- propriétaire ;
- version ;
- taux de détection ;
- taux de faux positifs.

---

# 10. Exemples de règles

```text
NOUVEL_APPAREIL_ET_TRANSFERT_ELEVE
PLUSIEURS_COMPTES_MEME_APPAREIL
TROP_DE_TENTATIVES_DE_PAIEMENT
REMBOURSEMENT_SUPERIEUR_A_LA_VENTE
TPE_HORS_ZONE_AUTORISEE
CHANGEMENT_TELEPHONE_ET_RETRAIT_IMMEDIAT
MULTIPLES_BENEFICIAIRES_EN_COURTE_PERIODE
UTILISATION_ACCES_URGENCE_SANS_TICKET
```

---

# 11. Fenêtres temporelles

Les règles peuvent analyser :

- quelques secondes ;
- quelques minutes ;
- une heure ;
- une journée ;
- une semaine ;
- un mois ;
- l’historique complet.

---

# 12. Actions automatiques

Selon le risque, le système peut :

- autoriser ;
- autoriser avec surveillance ;
- demander un MFA ;
- demander une biométrie ;
- demander un document ;
- réduire une limite ;
- mettre en attente ;
- bloquer temporairement ;
- refuser ;
- suspendre ;
- créer une alerte ;
- créer un dossier ;
- notifier l’équipe fraude.

---

# 13. Step-Up Authentication

Une vérification supplémentaire peut inclure :

- OTP ;
- biométrie ;
- PIN ;
- passkey ;
- confirmation appareil ;
- appel support ;
- document ;
- selfie ;
- preuve de vie.

---

# 14. Blocage ciblé

Le blocage doit être proportionné.

Exemples :

- bloquer un paiement ;
- bloquer un bénéficiaire ;
- bloquer un appareil ;
- bloquer un canal ;
- bloquer les retraits ;
- bloquer une carte ;
- bloquer un TPE ;
- bloquer un partenaire ;
- bloquer le compte complet uniquement si nécessaire.

---

# 15. Blocage temporaire

Un blocage temporaire doit contenir :

- motif ;
- début ;
- durée ;
- ressource ;
- action ;
- règle ;
- score ;
- auteur ;
- expiration ;
- procédure de levée.

---

# 16. Refus définitif

Un refus définitif doit être réservé aux cas où :

- le risque est confirmé ;
- la politique l’exige ;
- l’opération est impossible ;
- l’identité est frauduleuse ;
- une liste d’interdiction s’applique ;
- le partenaire confirme une fraude.

---

# 17. Statut inconnu

Lorsqu’une opération externe a un statut incertain, elle ne doit pas être automatiquement rejouée.

Le système doit :

- vérifier le partenaire ;
- attendre un webhook ;
- lancer un rapprochement ;
- protéger contre le doublon ;
- créer une alerte si le délai est dépassé.

---

# 18. Alertes fraude

Chaque alerte doit contenir :

- identifiant ;
- type ;
- entité ;
- transaction ;
- score ;
- règles ;
- signaux ;
- priorité ;
- pays ;
- date ;
- statut ;
- analyste ;
- historique ;
- pièces ;
- corrélation ;
- action automatique ;
- décision finale.

---

# 19. Statuts d’alerte

Valeurs possibles :

- OPEN ;
- ASSIGNED ;
- IN_REVIEW ;
- INFORMATION_REQUIRED ;
- ESCALATED ;
- FALSE_POSITIVE ;
- CONFIRMED ;
- ACTION_TAKEN ;
- CLOSED ;
- REOPENED.

---

# 20. Priorités

Exemple :

- LOW ;
- MEDIUM ;
- HIGH ;
- CRITICAL.

La priorité peut dépendre :

- du montant ;
- du type de fraude ;
- du nombre de victimes ;
- du pays ;
- du partenaire ;
- de la répétition ;
- de l’impact réputationnel ;
- du risque réglementaire.

---

# 21. Dossier fraude

Un dossier fraude peut regrouper :

- plusieurs alertes ;
- plusieurs transactions ;
- plusieurs utilisateurs ;
- plusieurs appareils ;
- plusieurs commerçants ;
- plusieurs partenaires ;
- plusieurs preuves.

---

# 22. Contenu du dossier

Le dossier doit contenir :

- référence ;
- titre ;
- typologie ;
- personnes concernées ;
- organisations ;
- transactions ;
- appareils ;
- cartes ;
- TPE ;
- preuves ;
- chronologie ;
- commentaires ;
- actions ;
- pertes ;
- recouvrements ;
- décisions ;
- responsables ;
- statut ;
- audit.

---

# 23. Statuts d’un dossier

Valeurs possibles :

- CREATED ;
- TRIAGE ;
- INVESTIGATION ;
- INFORMATION_REQUIRED ;
- ESCALATED ;
- CONFIRMED_FRAUD ;
- NOT_FRAUD ;
- RECOVERY_IN_PROGRESS ;
- CLOSED ;
- REOPENED.

---

# 24. Triage

Le triage doit permettre de :

- confirmer la priorité ;
- évaluer l’impact ;
- regrouper les alertes ;
- assigner un analyste ;
- bloquer si nécessaire ;
- préserver les preuves ;
- définir les prochaines actions.

---

# 25. Investigation

L’analyste doit pouvoir consulter :

- identité ;
- appareils ;
- sessions ;
- transactions ;
- bénéficiaires ;
- cartes ;
- commerçants ;
- TPE ;
- partenaires ;
- IP ;
- localisation ;
- règles ;
- score ;
- historique ;
- tickets support ;
- KYC ;
- alertes AML.

---

# 26. Chronologie

Le dossier doit présenter une chronologie unifiée :

- connexions ;
- changements de mot de passe ;
- ajout d’appareil ;
- ajout de bénéficiaire ;
- transactions ;
- webhooks ;
- blocages ;
- appels support ;
- actions administratives ;
- remboursements ;
- décisions.

---

# 27. Preuves

Les preuves peuvent inclure :

- logs ;
- traces ;
- documents ;
- captures ;
- enregistrements autorisés ;
- réponses partenaires ;
- données TPE ;
- journaux d’audit ;
- reçus ;
- IP ;
- device fingerprint ;
- événements.

---

# 28. Intégrité des preuves

Une preuve doit contenir :

- identifiant ;
- origine ;
- date ;
- auteur ;
- hash ;
- stockage ;
- niveau de sensibilité ;
- chaîne de conservation ;
- accès ;
- export ;
- expiration éventuelle.

---

# 29. Chaîne de conservation

Les preuves sensibles doivent rester traçables depuis :

- collecte ;
- stockage ;
- consultation ;
- copie ;
- export ;
- transmission ;
- clôture.

---

# 30. Revue manuelle

L’analyste doit pouvoir :

- confirmer ;
- infirmer ;
- demander des informations ;
- appliquer une restriction ;
- proposer un remboursement ;
- escalader ;
- transmettre à conformité ;
- transmettre à sécurité ;
- transmettre à un partenaire ;
- clôturer.

---

# 31. Séparation des responsabilités

Les rôles doivent être séparés entre :

- détection ;
- investigation ;
- validation ;
- remboursement ;
- levée de blocage ;
- modification des règles ;
- audit ;
- reporting.

---

# 32. Faux positifs

Chaque faux positif doit être analysé.

Le système doit mesurer :

- règle concernée ;
- modèle ;
- segment ;
- pays ;
- montant ;
- action ;
- durée du blocage ;
- impact utilisateur ;
- taux de récurrence.

---

# 33. Feedback Loop

Les décisions humaines doivent pouvoir améliorer :

- règles ;
- seuils ;
- modèles ;
- priorités ;
- scénarios ;
- listes internes ;
- simulateurs de test.

---

# 34. Modèles de détection

Des modèles peuvent analyser :

- anomalies ;
- séquences ;
- graphes ;
- relations ;
- comportements ;
- appareils ;
- volumes ;
- catégories ;
- historique.

---

# 35. Gouvernance des modèles

Chaque modèle doit avoir :

- propriétaire ;
- version ;
- description ;
- données utilisées ;
- métriques ;
- seuils ;
- date d’activation ;
- date de revue ;
- biais connus ;
- limites ;
- rollback ;
- validation.

---

# 36. Modèle en mode observation

Avant activation, un modèle peut fonctionner sans bloquer.

Il doit alors :

- produire des scores ;
- mesurer les résultats ;
- comparer avec les décisions humaines ;
- estimer les faux positifs ;
- estimer les fraudes détectées ;
- être validé avant action automatique.

---

# 37. Drift

Le système doit surveiller :

- changement de comportement ;
- baisse de précision ;
- hausse des faux positifs ;
- nouvelles typologies ;
- changement pays ;
- changement produit ;
- changement partenaire ;
- évolution des fraudeurs.

---

# 38. Graphes de fraude

Le système peut relier :

- utilisateurs ;
- appareils ;
- cartes ;
- comptes ;
- bénéficiaires ;
- commerçants ;
- TPE ;
- IP ;
- numéros ;
- documents ;
- partenaires.

Cela permet de détecter :

- réseaux ;
- comptes liés ;
- mule accounts ;
- fraude organisée ;
- collusion.

---

# 39. Listes internes

Mansa peut maintenir :

- appareils bloqués ;
- documents compromis ;
- comptes frauduleux ;
- bénéficiaires suspects ;
- commerçants interdits ;
- TPE compromis ;
- IP risquées ;
- partenaires suspendus.

---

# 40. Gestion des listes

Chaque entrée doit contenir :

- type ;
- valeur ;
- motif ;
- date ;
- source ;
- expiration ;
- statut ;
- propriétaire ;
- approbateur ;
- audit.

---

# 41. Listes temporaires

Une liste temporaire doit expirer automatiquement sauf renouvellement justifié.

---

# 42. Risque bénéficiaire

Le système doit analyser :

- âge du bénéficiaire ;
- relation avec l’émetteur ;
- nombre d’émetteurs ;
- montants reçus ;
- retraits ;
- pays ;
- historique ;
- liens avec des dossiers fraude ;
- appareil partagé.

---

# 43. Mule Accounts

Les signes possibles incluent :

- nombreux virements entrants ;
- retrait immédiat ;
- faible activité habituelle ;
- bénéficiaires multiples ;
- changement récent d’appareil ;
- absence d’usage normal ;
- activité en chaîne.

---

# 44. Fraude carte

Le moteur peut analyser :

- pays ;
- commerçant ;
- catégorie ;
- montant ;
- fréquence ;
- e-commerce ;
- sans contact ;
- terminal ;
- carte présente ;
- 3-D Secure ;
- tokenisation ;
- historique ;
- autorisations précédentes.

---

# 45. Fraude TPE

Le système doit surveiller :

- localisation ;
- appareil ;
- certificat ;
- version ;
- volume ;
- taux d’échec ;
- remboursements ;
- activité hors horaires ;
- changement de réseau ;
- transaction hors ligne ;
- comportement employé.

---

# 46. Fraude commerçant

Signaux possibles :

- hausse brutale ;
- panier incohérent ;
- forte concentration de cartes ;
- remboursements rapides ;
- ventes sans stock ;
- catégorie d’activité incohérente ;
- nombreux paiements du propriétaire ;
- chargebacks ;
- activité nocturne inhabituelle.

---

# 47. Fraude interne et corruption

Le système doit détecter :

- modification d’un dossier sans justification ;
- suppression de pénalité ;
- levée de blocage répétée ;
- accès à des proches ;
- export massif ;
- utilisation d’un compte partagé ;
- action hors institution ;
- modification de montant ;
- validation croisée suspecte.

---

# 48. Quatre yeux

Certaines actions doivent nécessiter une seconde approbation.

Exemples :

- levée d’un blocage critique ;
- remboursement exceptionnel ;
- suppression d’une entrée de liste ;
- clôture d’un dossier majeur ;
- modification d’une règle globale ;
- levée d’un gel ;
- ajustement financier.

---

# 49. Pertes financières

Chaque dossier confirmé doit pouvoir enregistrer :

- montant brut ;
- montant évité ;
- montant perdu ;
- montant récupéré ;
- devise ;
- partenaire responsable ;
- provision ;
- assurance ;
- remboursement client ;
- recouvrement.

---

# 50. Recouvrement

Actions possibles :

- annulation ;
- remboursement partenaire ;
- rappel de fonds ;
- blocage de bénéficiaire ;
- compensation ;
- recours ;
- assurance ;
- recouvrement interne ;
- transmission juridique.

---

# 51. Chargebacks et contestations

Le système doit gérer :

- déclaration ;
- preuve ;
- délai ;
- réseau ;
- statut ;
- montant ;
- décision ;
- remboursement ;
- représentation ;
- perte finale ;
- audit.

---

# 52. Contestation utilisateur

L’utilisateur doit pouvoir signaler :

- transaction non reconnue ;
- carte perdue ;
- compte compromis ;
- remboursement manquant ;
- fraude commerçant ;
- usurpation ;
- TPE suspect.

---

# 53. Mesures immédiates

Selon le cas :

- geler la carte ;
- révoquer la session ;
- bloquer l’appareil ;
- changer le mot de passe ;
- suspendre le bénéficiaire ;
- mettre en attente les transactions ;
- ouvrir un dossier ;
- notifier l’utilisateur.

---

# 54. Communication utilisateur

Les messages doivent être :

- clairs ;
- neutres ;
- sans divulguer les règles internes ;
- adaptés au niveau de risque ;
- traduits ;
- cohérents avec le support ;
- historisés.

---

# 55. Appel et vérification

Pour certains cas, Mansa peut utiliser :

- appel sortant ;
- rappel sécurisé ;
- question de vérification ;
- confirmation dans l’application ;
- rendez-vous ;
- revue vidéo ;
- vérification en agence partenaire.

---

# 56. Multi-pays

Chaque pays doit pouvoir définir :

- typologies prioritaires ;
- seuils ;
- actions ;
- obligations ;
- partenaires ;
- délais ;
- procédures ;
- messages ;
- conservation ;
- reporting.

---

# 57. Multi-devise

Les règles doivent tenir compte :

- de la devise ;
- du taux ;
- du montant converti ;
- de la volatilité ;
- des plafonds ;
- du pays ;
- de la date.

---

# 58. Intégration KYC et AML

Le moteur fraude doit pouvoir utiliser :

- niveau KYC ;
- risque KYC ;
- sanctions ;
- PEP ;
- profil AML ;
- historique conformité ;
- restrictions ;
- documents expirés.

---

# 59. Intégration sécurité

Le moteur fraude doit recevoir :

- connexion suspecte ;
- appareil compromis ;
- élévation de privilège ;
- secret compromis ;
- session anormale ;
- accès d’urgence ;
- activité automatisée.

---

# 60. Intégration partenaires

Chaque partenaire doit transmettre ou permettre de vérifier :

- statut ;
- référence ;
- résultat ;
- score éventuel ;
- motif ;
- webhook ;
- annulation ;
- rapprochement ;
- incident.

---

# 61. Administration

Le portail Admin doit permettre :

- consulter les alertes ;
- consulter les dossiers ;
- filtrer ;
- rechercher ;
- assigner ;
- escalader ;
- bloquer ;
- lever un blocage ;
- ajouter une preuve ;
- voir la chronologie ;
- gérer les listes ;
- gérer les règles ;
- consulter les modèles ;
- suivre les pertes ;
- générer un rapport ;
- auditer les accès.

---

# 62. Permissions

Exemples :

```text
fraud.read
fraud.read_sensitive
fraud.alert.assign
fraud.case.create
fraud.case.review
fraud.case.confirm
fraud.case.close
fraud.block.apply
fraud.block.remove
fraud.rule.read
fraud.rule.manage
fraud.model.read
fraud.model.manage
fraud.watchlist.read
fraud.watchlist.manage
fraud.loss.read
fraud.recovery.manage
fraud.export.create
fraud.audit.read
```

---

# 63. Actions critiques

Doivent être protégées :

- levée de blocage critique ;
- clôture d’un dossier confirmé ;
- suppression d’une preuve ;
- ajout ou retrait d’une liste ;
- modification de seuil global ;
- activation d’un modèle ;
- remboursement exceptionnel ;
- ajustement financier ;
- export sensible ;
- modification de perte.

---

# 64. Double validation

Peut être exigée pour :

- dossier à perte élevée ;
- fraude interne ;
- commerçant majeur ;
- partenaire institutionnel ;
- levée de blocage global ;
- activation d’un modèle ;
- modification de règles critiques ;
- remboursement élevé ;
- clôture de dossier sensible.

---

# 65. API

Exemples :

```http
POST   /fraud/evaluations
GET    /fraud/evaluations/{id}

GET    /fraud/alerts
GET    /fraud/alerts/{id}
PATCH  /fraud/alerts/{id}

POST   /fraud/cases
GET    /fraud/cases/{id}
PATCH  /fraud/cases/{id}
POST   /fraud/cases/{id}/confirm
POST   /fraud/cases/{id}/close

POST   /fraud/blocks
DELETE /fraud/blocks/{id}

GET    /fraud/rules
POST   /fraud/rules
PATCH  /fraud/rules/{id}

GET    /fraud/watchlists
POST   /fraud/watchlists
```

---

# 66. Modèles

- FraudSignal
- FraudEvaluation
- FraudScore
- FraudRule
- FraudRuleVersion
- FraudModel
- FraudModelVersion
- FraudAlert
- FraudCase
- FraudCaseEntity
- FraudCaseTransaction
- FraudEvidence
- FraudTimelineEvent
- FraudBlock
- FraudWatchlist
- FraudLoss
- FraudRecovery
- FraudDecision
- FraudAudit

---

# 67. Règles métier

1. Toute opération sensible peut être évaluée.
2. Les scores sont versionnés.
3. Les règles sont configurables.
4. Les signaux sont minimisés.
5. Les blocages sont proportionnés.
6. Les opérations critiques utilisent une vérification renforcée.
7. Les faux positifs sont mesurés.
8. Les décisions humaines alimentent l’amélioration.
9. Les preuves sont protégées.
10. Les dossiers conservent une chronologie.
11. Les actions critiques sont auditées.
12. Les modèles sont validés avant activation.
13. Les modèles peuvent fonctionner en observation.
14. Le drift est surveillé.
15. Les listes internes sont versionnées.
16. Les listes temporaires expirent.
17. Les fraudes internes sont détectables.
18. Les partenaires sont vérifiables.
19. Les pertes sont enregistrées.
20. Les recouvrements sont suivis.
21. Les contestations sont intégrées.
22. Les utilisateurs légitimes peuvent demander une revue.
23. Les pays possèdent leurs propres seuils.
24. Les données sensibles sont protégées.
25. Les contrôles financiers sont idempotents.

---

# 68. Analytics

Événements possibles :

```text
fraud_evaluation_started
fraud_evaluation_completed
fraud_high_risk_detected
fraud_step_up_required
fraud_transaction_blocked
fraud_alert_created
fraud_alert_escalated
fraud_case_created
fraud_case_confirmed
fraud_case_closed
fraud_false_positive_confirmed
fraud_watchlist_entry_added
fraud_watchlist_entry_removed
fraud_rule_updated
fraud_model_activated
fraud_loss_recorded
fraud_recovery_completed
```

---

# 69. Tests

- tests de scoring ;
- tests de règles ;
- tests de seuils ;
- tests appareil ;
- tests IP ;
- tests comportement ;
- tests paiement ;
- tests carte ;
- tests Mobile Money ;
- tests commerçant ;
- tests TPE ;
- tests remboursement ;
- tests fraude interne ;
- tests partenaire ;
- tests faux positifs ;
- tests blocage ciblé ;
- tests step-up ;
- tests statut inconnu ;
- tests listes ;
- tests modèles ;
- tests drift ;
- tests graphes ;
- tests multi-pays ;
- tests multi-devise ;
- tests permissions ;
- tests double validation ;
- tests pertes ;
- tests recouvrement ;
- tests d’audit.

---

# 70. Critères d’acceptation

La gestion de la fraude est validée lorsque :

- les typologies principales sont définies ;
- les signaux sont collectés ;
- les scores sont calculés ;
- les règles sont versionnées ;
- les seuils sont configurables ;
- les actions automatiques sont disponibles ;
- les blocages sont proportionnés ;
- les faux positifs sont mesurés ;
- les alertes créent des dossiers ;
- les preuves sont protégées ;
- les modèles sont gouvernés ;
- le drift est surveillé ;
- les listes internes sont administrables ;
- les fraudes internes sont prises en compte ;
- les pertes et recouvrements sont suivis ;
- les contestations utilisateurs sont intégrées ;
- les accès sont protégés ;
- les tests couvrent les scénarios critiques.
