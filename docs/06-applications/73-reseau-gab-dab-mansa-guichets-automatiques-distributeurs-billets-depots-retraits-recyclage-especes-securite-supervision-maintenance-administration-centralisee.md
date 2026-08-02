# 73 — Réseau GAB/DAB Mansa : guichets automatiques, distributeurs de billets, dépôts, retraits, recyclage d’espèces, sécurité, supervision, maintenance et administration centralisée

## 1. Objet du document

Ce document définit l’architecture officielle du **réseau GAB/DAB Mansa**.

Il couvre les machines permettant aux clients, commerçants, agents, entreprises et institutions d’effectuer des opérations financières en libre-service.

Le réseau doit distinguer clairement :

- les **DAB**, principalement destinés au retrait d’espèces ;
- les **GAB**, proposant des services bancaires plus complets ;
- les GAB avec dépôt ;
- les GAB avec recyclage des billets ;
- les machines installées en agence ;
- les machines installées hors agence ;
- les machines exploitées par Mansa ;
- les machines exploitées avec une banque partenaire ;
- les machines appartenant à un prestataire ;
- les machines mobiles ou temporaires éventuelles.

Le système doit permettre notamment :

- le retrait avec carte ;
- le retrait sans carte ;
- la consultation du solde ;
- la consultation de l’historique ;
- l’impression d’un mini-relevé ;
- le changement du code PIN ;
- le dépôt d’espèces ;
- le dépôt sur son propre compte ;
- le dépôt sur un compte tiers lorsque cela est autorisé ;
- le recyclage des billets déposés ;
- le paiement de factures ;
- la recharge Mobile Money ;
- le transfert ;
- l’assistance ;
- la gestion des billets ;
- la gestion des cassettes ;
- la supervision ;
- la maintenance ;
- la sécurité ;
- la fraude ;
- la journalisation ;
- le rapprochement ;
- l’administration centralisée.

---

# 2. Principes fondamentaux

## 2.1 Le GAB et le DAB sont deux catégories distinctes

Le système doit gérer séparément :

### DAB Mansa

Fonction principale :

- retrait d’espèces.

Fonctions complémentaires possibles :

- consultation du solde ;
- mini-relevé ;
- changement du PIN ;
- retrait sans carte ;
- paiement de facture ;
- recharge ;
- reçu.

### GAB Mansa

Fonctions possibles :

- retrait ;
- dépôt ;
- consultation ;
- mini-relevé ;
- transfert ;
- paiement ;
- recharge ;
- changement PIN ;
- retrait sans carte ;
- dépôt sans carte ;
- assistance ;
- services institutionnels.

---

## 2.2 Toutes les machines ne doivent pas proposer les mêmes fonctions

Les fonctionnalités doivent être activables selon :

- type de machine ;
- modèle ;
- pays ;
- emplacement ;
- partenaire ;
- capacité matérielle ;
- version logicielle ;
- niveau de sécurité ;
- contrat ;
- rentabilité ;
- risque.

---

## 2.3 Toute opération financière doit passer par le ledger

Aucun retrait, dépôt, paiement, transfert ou remboursement ne doit être considéré comme terminé sans écriture correspondante dans le ledger.

---

## 2.4 Une distribution de billets doit toujours être confirmée

Le débit du client ne doit être finalisé que lorsque la machine confirme correctement la distribution des billets.

En cas d’incertitude :

- l’opération doit être mise en attente ;
- une réconciliation doit être déclenchée ;
- le client doit être informé ;
- aucune correction manuelle ne doit être faite sans preuve.

---

## 2.5 Une machine incertaine doit arrêter les opérations sensibles

Un GAB ou DAB doit être placé hors service lorsque :

- l’intégrité logicielle est incertaine ;
- le coffre est ouvert ;
- le distributeur fonctionne mal ;
- le clavier PIN est compromis ;
- une tentative de skimming est détectée ;
- les cassettes sont incohérentes ;
- le réseau est instable au-delà du seuil autorisé ;
- une fraude est suspectée ;
- la comptabilité des billets est incohérente.

---

# 3. Types de machines

Le système doit gérer au minimum :

- DAB de retrait intérieur ;
- DAB de retrait extérieur ;
- GAB standard ;
- GAB multifonction ;
- GAB avec dépôt d’espèces ;
- GAB avec recyclage de billets ;
- GAB mural ;
- GAB autonome ;
- GAB en agence ;
- GAB hors agence ;
- GAB mobile ;
- GAB institutionnel ;
- GAB partenaire ;
- GAB de démonstration ;
- GAB de test.

---

# 4. Classification par emplacement

Les emplacements possibles comprennent :

- agence Mansa ;
- agence bancaire partenaire ;
- centre commercial ;
- supermarché ;
- station-service ;
- université ;
- hôpital ;
- gare ;
- aéroport ;
- administration ;
- marché ;
- hôtel ;
- quartier d’affaires ;
- entreprise ;
- site industriel ;
- zone rurale ;
- événement temporaire.

---

# 5. Critères de choix d’un emplacement

Chaque emplacement doit être évalué selon :

- trafic ;
- demande ;
- sécurité ;
- accessibilité ;
- éclairage ;
- électricité ;
- réseau ;
- proximité d’une équipe de maintenance ;
- proximité d’un centre de cash ;
- risque de vandalisme ;
- rentabilité ;
- concurrence ;
- disponibilité foncière ;
- visibilité ;
- facilité de réapprovisionnement ;
- disponibilité d’un gardiennage ;
- accessibilité aux personnes à mobilité réduite.

---

# 6. Fiche d’une machine

Chaque machine doit posséder :

- identifiant unique ;
- numéro de série ;
- fabricant ;
- modèle ;
- type ;
- propriétaire ;
- exploitant ;
- pays ;
- ville ;
- adresse ;
- coordonnées ;
- statut ;
- version logicielle ;
- version firmware ;
- date d’installation ;
- date de mise en service ;
- contrat de maintenance ;
- capacité ;
- devises ;
- cassettes ;
- périphériques ;
- certificat ;
- clé ;
- historique ;
- dernière transaction ;
- dernière maintenance.

---

# 7. Statuts d’une machine

- PENDING_INSTALLATION ;
- INSTALLED ;
- TESTING ;
- ACTIVE ;
- LIMITED ;
- OUT_OF_SERVICE ;
- MAINTENANCE ;
- CASH_LOW ;
- CASH_EMPTY ;
- CASH_FULL ;
- DEGRADED ;
- OFFLINE ;
- SECURITY_ALERT ;
- QUARANTINED ;
- DECOMMISSIONED.

---

# 8. Parcours d’identification

Le client peut être identifié par :

- carte physique ;
- carte virtuelle tokenisée ;
- QR Code ;
- code de retrait ;
- numéro de téléphone ;
- identifiant Mansa ;
- NFC ;
- biométrie si autorisée ;
- combinaison de plusieurs facteurs.

---

# 9. Retrait avec carte

Le parcours doit inclure :

1. insertion ou lecture de la carte ;
2. détection du réseau ;
3. choix de la langue ;
4. saisie du PIN ;
5. vérification ;
6. choix du compte ;
7. choix du montant ;
8. contrôle du solde ;
9. contrôle des limites ;
10. contrôle fraude ;
11. autorisation ;
12. préparation des billets ;
13. distribution ;
14. confirmation ;
15. écriture ledger ;
16. reçu ;
17. notification ;
18. fin de session.

---

# 10. Retrait sans carte

Le retrait sans carte peut utiliser :

- QR dynamique ;
- QR statique associé à une session ;
- code à usage unique ;
- code généré dans l’application ;
- NFC ;
- token sécurisé ;
- numéro de téléphone et OTP ;
- identifiant bénéficiaire.

---

# 11. Génération d’un retrait sans carte

Le client peut générer une demande contenant :

- montant ;
- devise ;
- durée de validité ;
- bénéficiaire ;
- nombre d’utilisations ;
- machine ou zone ;
- type de retrait ;
- frais ;
- référence ;
- niveau d’authentification.

---

# 12. Retrait par un tiers

Le client peut autoriser une autre personne à retirer.

Le système doit gérer :

- identité du bénéficiaire ;
- téléphone ;
- code ;
- durée ;
- montant ;
- notification ;
- preuve ;
- annulation ;
- limitation ;
- contrôle fraude.

---

# 13. Expiration d’un code de retrait

Le code doit expirer après :

- utilisation ;
- annulation ;
- durée maximale ;
- nombre d’échecs ;
- suspicion de fraude ;
- changement de compte ;
- blocage du client.

---

# 14. Limites de retrait

Les limites peuvent dépendre :

- du pays ;
- du client ;
- du niveau KYC ;
- du type de carte ;
- de la machine ;
- de l’emplacement ;
- de la devise ;
- de l’heure ;
- du niveau de risque ;
- de la disponibilité des billets ;
- du partenaire ;
- du jour.

---

# 15. Montants rapides

La machine peut proposer des montants adaptés aux billets disponibles.

Exemple :

```text
5 000 FCFA
10 000 FCFA
20 000 FCFA
40 000 FCFA
Autre montant
```

---

# 16. Algorithme de distribution

L’algorithme doit choisir les billets selon :

- montant demandé ;
- coupures disponibles ;
- stock de chaque cassette ;
- stratégie d’équilibrage ;
- qualité des billets ;
- nombre maximal de billets ;
- préférences du client ;
- règles du pays.

---

# 17. Choix des coupures

Le client peut éventuellement choisir :

- petites coupures ;
- grandes coupures ;
- mélange ;
- proposition automatique.

La fonction dépend du matériel disponible.

---

# 18. Préautorisation

Avant la distribution, le système peut réserver le montant.

Statut possible :

- AUTHORIZATION_PENDING ;
- AUTHORIZED ;
- DISPENSING ;
- DISPENSED ;
- PARTIALLY_DISPENSED ;
- FAILED ;
- REVERSED ;
- RECONCILIATION_REQUIRED.

---

# 19. Débit sans distribution

Si le client est débité mais ne reçoit pas les billets :

- la machine doit remonter l’incident ;
- la transaction doit être rapprochée ;
- une annulation automatique doit être tentée ;
- le client doit recevoir une notification ;
- un ticket peut être créé automatiquement ;
- le journal matériel doit être conservé.

---

# 20. Distribution partielle

En cas de distribution partielle :

- le nombre de billets réellement distribués doit être confirmé ;
- le montant réel doit être calculé ;
- le ledger doit être corrigé ;
- le client doit être informé ;
- l’incident doit être enregistré ;
- la machine peut être suspendue.

---

# 21. Billet non récupéré

Si le client ne prend pas les billets :

- la machine doit les reprendre lorsque le matériel le permet ;
- les billets doivent être placés dans un compartiment de rejet ;
- l’opération doit être annulée ou réconciliée ;
- le client doit être notifié ;
- l’événement doit être audité.

---

# 22. Carte retenue

La carte peut être retenue en cas de :

- carte déclarée volée ;
- carte bloquée ;
- ordre de l’émetteur ;
- tentatives PIN dépassées ;
- anomalie technique ;
- suspicion de fraude.

La politique doit être configurable.

---

# 23. Restitution de la carte

La machine doit normalement restituer la carte avant ou après les billets selon la configuration.

Le parcours doit minimiser le risque d’oubli.

---

# 24. Consultation du solde

La consultation doit permettre :

- solde disponible ;
- solde comptable ;
- sommes réservées ;
- devise ;
- date de mise à jour ;
- comptes disponibles.

Le montant peut être masqué à l’écran selon le choix du client.

---

# 25. Mini-relevé

Le mini-relevé peut afficher :

- date ;
- type d’opération ;
- montant ;
- devise ;
- statut ;
- solde après opération ;
- référence partiellement masquée.

---

# 26. Historique

Le nombre d’opérations visibles doit être configurable.

Exemples :

- 5 dernières opérations ;
- 10 dernières opérations ;
- période sélectionnée ;
- envoi dans l’application ;
- envoi par SMS ou e-mail.

---

# 27. Changement du PIN

Le processus doit vérifier :

- ancienne authentification ;
- nouvelle valeur ;
- confirmation ;
- règles de complexité ;
- HSM ;
- carte autorisée ;
- statut de la carte ;
- nombre de tentatives ;
- journalisation.

Le PIN ne doit jamais apparaître en clair.

---

# 28. Déblocage du PIN

Le déblocage peut nécessiter :

- authentification forte ;
- application Mansa ;
- OTP ;
- biométrie ;
- validation du support ;
- carte compatible ;
- autorisation de l’émetteur.

---

# 29. Dépôt d’espèces

Le dépôt peut être réalisé :

- sur son propre wallet ;
- sur son compte bancaire partenaire ;
- sur un compte commerçant ;
- sur un compte d’entreprise ;
- sur un compte tiers autorisé ;
- sur un compte institutionnel ;
- pour paiement d’une facture.

---

# 30. Parcours de dépôt

1. identification ;
2. choix du compte ;
3. ouverture du module de dépôt ;
4. insertion des billets ;
5. comptage ;
6. reconnaissance des coupures ;
7. détection des faux billets ;
8. affichage du montant ;
9. confirmation du client ;
10. stockage ou recyclage ;
11. crédit ledger ;
12. reçu ;
13. notification ;
14. rapprochement.

---

# 31. Dépôt sans carte

Le dépôt sans carte peut utiliser :

- numéro de téléphone ;
- QR ;
- identifiant Mansa ;
- code bénéficiaire ;
- facture ;
- référence de paiement ;
- identifiant entreprise.

---

# 32. Dépôt sur le compte d’un tiers

Le système doit vérifier :

- bénéficiaire ;
- nom partiellement masqué ;
- compte ;
- limite ;
- origine des fonds ;
- frais ;
- réglementation ;
- validation du déposant ;
- reçu.

---

# 33. Limites de dépôt

Les limites peuvent dépendre :

- niveau KYC ;
- type de compte ;
- pays ;
- machine ;
- période ;
- montant ;
- nombre de billets ;
- risque ;
- source des fonds ;
- bénéficiaire ;
- réglementation.

---

# 34. Validation des billets

Le module de dépôt doit analyser :

- dimension ;
- image ;
- filigrane ;
- encre ;
- caractéristiques UV ;
- magnétisme ;
- série ;
- orientation ;
- état ;
- authenticité.

---

# 35. Billets suspects

Un billet suspect peut être :

- refusé et rendu ;
- conservé si la loi et la procédure l’autorisent ;
- placé en cassette dédiée ;
- journalisé ;
- photographié par le module ;
- relié à une transaction ;
- signalé au support ou à la conformité.

---

# 36. Billets abîmés

Le système doit définir les règles pour :

- billet plié ;
- billet déchiré ;
- billet très usé ;
- billet humide ;
- billet collé ;
- billet incomplet ;
- billet non reconnu.

---

# 37. Confirmation du dépôt

Avant validation, l’écran doit afficher :

- nombre de billets ;
- coupures ;
- montant total ;
- frais éventuels ;
- compte crédité ;
- avertissement ;
- bouton confirmer ;
- bouton annuler.

---

# 38. Annulation d’un dépôt

Avant confirmation, la machine doit restituer les billets lorsque possible.

Après confirmation, une annulation doit suivre une procédure financière contrôlée.

---

# 39. Dépôt bloqué

Si les billets restent bloqués :

- la machine doit créer un incident ;
- le compartiment doit être sécurisé ;
- les images et journaux doivent être conservés ;
- le client doit recevoir un reçu d’incident ;
- une équipe doit vérifier physiquement ;
- le crédit doit attendre la preuve.

---

# 40. GAB avec recyclage

Un GAB recycleur peut utiliser les billets déposés pour de futurs retraits.

Cela permet :

- réduction des réapprovisionnements ;
- meilleure disponibilité ;
- réduction des coûts ;
- équilibre local du cash ;
- amélioration de la rentabilité.

---

# 41. Conditions du recyclage

Seuls les billets :

- authentifiés ;
- correctement identifiés ;
- en bon état ;
- autorisés ;
- conformes aux règles de la banque centrale ;
- traçables,

peuvent être replacés dans les cassettes de distribution.

---

# 42. Paiement de factures

Le GAB peut permettre le paiement de :

- électricité ;
- eau ;
- télécommunications ;
- Internet ;
- télévision ;
- scolarité ;
- taxes ;
- amendes ;
- assurances ;
- factures commerçantes ;
- services publics.

---

# 43. Parcours de paiement de facture

Le système doit vérifier :

- fournisseur ;
- référence ;
- identité ;
- montant ;
- frais ;
- solde ;
- limite ;
- confirmation ;
- ledger ;
- partenaire ;
- reçu ;
- notification.

---

# 44. Recharge Mobile Money

Le GAB peut permettre :

- recharge depuis le wallet Mansa ;
- recharge par carte ;
- recharge par espèces ;
- recharge de son propre numéro ;
- recharge d’un tiers ;
- choix de l’opérateur ;
- vérification du numéro ;
- reçu.

---

# 45. Transfert depuis un GAB

Le transfert peut être effectué vers :

- un wallet Mansa ;
- un compte bancaire ;
- un opérateur Mobile Money ;
- une entreprise ;
- un bénéficiaire enregistré ;
- un service public.

---

# 46. Assistance

La machine peut proposer :

- bouton d’aide ;
- FAQ ;
- instructions audio ;
- appel support ;
- chat ;
- visioconférence éventuelle ;
- signalement de problème ;
- création de ticket ;
- affichage d’un numéro d’urgence.

---

# 47. Langues

Le réseau doit pouvoir supporter :

- français ;
- bambara ;
- anglais ;
- arabe ;
- langues locales supplémentaires.

Les traductions doivent être administrables.

---

# 48. Accessibilité

Les machines doivent prévoir, selon le matériel :

- hauteur adaptée ;
- accès fauteuil roulant ;
- contraste élevé ;
- texte agrandi ;
- guidage vocal ;
- prise casque ;
- touches tactiles ;
- clavier braille ou repères ;
- temps de session adaptable ;
- écrans simples.

---

# 49. Reçus

Les reçus peuvent être :

- imprimés ;
- envoyés dans l’application ;
- envoyés par SMS ;
- envoyés par e-mail ;
- affichés sous forme de QR ;
- refusés par le client.

---

# 50. Contenu du reçu

Le reçu peut contenir :

- identifiant machine ;
- localisation ;
- date ;
- heure ;
- type d’opération ;
- montant ;
- frais ;
- devise ;
- référence ;
- solde masqué ;
- statut ;
- contact support.

Aucune donnée sensible complète ne doit apparaître.

---

# 51. Imprimante

L’administration doit suivre :

- présence papier ;
- niveau papier ;
- bourrage ;
- statut ;
- dernière impression ;
- erreur ;
- température ;
- maintenance ;
- modèle ;
- firmware.

---

# 52. Gestion des cassettes

Chaque cassette doit avoir :

- identifiant ;
- machine ;
- position ;
- devise ;
- coupure ;
- capacité ;
- quantité théorique ;
- quantité physique ;
- seuil bas ;
- seuil critique ;
- statut ;
- date de remplissage ;
- opérateur ;
- scellé ;
- historique.

---

# 53. Types de cassettes

- cassette de distribution ;
- cassette de dépôt ;
- cassette de recyclage ;
- cassette de rejet ;
- cassette de billets suspects ;
- cassette de récupération ;
- cassette de test.

---

# 54. Statuts d’une cassette

- EMPTY ;
- LOW ;
- AVAILABLE ;
- FULL ;
- JAMMED ;
- SEALED ;
- OPENED ;
- REMOVED ;
- DISCREPANCY ;
- MAINTENANCE ;
- UNKNOWN.

---

# 55. Chargement des cassettes

Le processus doit inclure :

- planification ;
- préparation des billets ;
- comptage ;
- double contrôle ;
- scellé ;
- transport ;
- identification du personnel ;
- ouverture sécurisée ;
- installation ;
- confirmation ;
- test ;
- clôture ;
- audit.

---

# 56. Déchargement des cassettes

Le déchargement doit enregistrer :

- quantité attendue ;
- quantité physique ;
- billets rejetés ;
- billets suspects ;
- écart ;
- opérateurs ;
- date ;
- scellé ;
- preuve ;
- destination des fonds.

---

# 57. Gestion du cash

Le système doit gérer :

- stock par machine ;
- stock par cassette ;
- prévision de consommation ;
- prévision de dépôt ;
- seuils ;
- réapprovisionnement ;
- collecte ;
- convoyage ;
- assurance ;
- rapprochement ;
- écarts ;
- coûts.

---

# 58. Prévision des besoins

Les prévisions peuvent utiliser :

- historique ;
- jour de la semaine ;
- salaire ;
- fête ;
- événement ;
- localisation ;
- météo ;
- saison ;
- volume récent ;
- disponibilité des agents ;
- distribution des coupures.

---

# 59. Cash faible

Lorsque le cash est faible :

- alerte ;
- estimation d’autonomie ;
- planification du réapprovisionnement ;
- limitation de certains montants ;
- désactivation de certaines coupures ;
- redirection vers une autre machine ;
- notification aux opérations.

---

# 60. Cash vide

Lorsque la machine ne peut plus distribuer :

- le retrait doit être désactivé ;
- les autres services peuvent rester actifs ;
- le client doit être informé avant authentification ;
- la machine doit indiquer un point proche ;
- une alerte critique doit être créée.

---

# 61. Cash plein

Pour un module de dépôt plein :

- le dépôt doit être suspendu ;
- le retrait peut rester disponible ;
- une collecte doit être planifiée ;
- les clients doivent être informés ;
- l’état doit apparaître dans l’administration.

---

# 62. Convoyage de fonds

La plateforme doit gérer :

- prestataire ;
- véhicule ;
- équipe ;
- mission ;
- itinéraire ;
- horaires ;
- montants ;
- scellés ;
- machine ;
- validation ;
- incidents ;
- preuve ;
- assurance.

---

# 63. Principe de double contrôle

Les opérations de cash sensibles doivent nécessiter au minimum deux personnes autorisées lorsque les procédures l’exigent.

---

# 64. Rapprochement cash

Le rapprochement doit comparer :

```text
Stock initial
+ dépôts
- retraits
- billets rejetés
- billets récupérés
=
Stock théorique final
```

Puis comparer avec le stock physique.

---

# 65. Écart de caisse

Un écart doit être :

- détecté ;
- quantifié ;
- bloqué selon seuil ;
- investigué ;
- relié aux transactions ;
- relié aux journaux matériels ;
- attribué ;
- corrigé ;
- audité.

---

# 66. Réconciliation transactionnelle

Le système doit rapprocher :

- demande ;
- autorisation ;
- ledger ;
- confirmation machine ;
- journal électronique ;
- mouvement physique ;
- partenaire bancaire ;
- réseau cartes ;
- reçu ;
- incident éventuel.

---

# 67. Journal électronique

Chaque machine doit produire un journal électronique contenant :

- démarrage ;
- arrêt ;
- session ;
- opération ;
- distribution ;
- dépôt ;
- erreur ;
- ouverture ;
- cassette ;
- maintenance ;
- alarme ;
- version ;
- configuration.

---

# 68. Données interdites dans les journaux

Ne pas enregistrer :

- PIN ;
- CVV ;
- clé privée ;
- numéro complet de carte ;
- mot de passe ;
- OTP complet ;
- donnée biométrique brute ;
- secret HSM ;
- contenu confidentiel inutile.

---

# 69. Sécurité physique

La sécurité physique doit couvrir :

- coffre ;
- serrure ;
- ancrage ;
- capteurs ;
- alarme ;
- caméra ;
- éclairage ;
- protection anti-effraction ;
- protection anti-explosion ;
- protection incendie ;
- accès technique ;
- scellés ;
- environnement.

---

# 70. Coffre

Le coffre doit être adapté :

- au niveau de risque ;
- à l’emplacement ;
- aux exigences du partenaire ;
- au volume de billets ;
- aux normes applicables ;
- aux conditions d’assurance.

---

# 71. Serrures

Les serrures peuvent être :

- mécaniques ;
- électroniques ;
- à combinaison ;
- temporelles ;
- contrôlées à distance ;
- à double authentification.

---

# 72. Capteurs

Capteurs possibles :

- ouverture ;
- vibration ;
- choc ;
- inclinaison ;
- chaleur ;
- fumée ;
- gaz ;
- forage ;
- mouvement ;
- présence ;
- retrait du panneau ;
- coffre.

---

# 73. Caméra

Les caméras peuvent surveiller :

- visage du client ;
- zone devant la machine ;
- compartiment billets ;
- environnement ;
- intervention technique.

Elles ne doivent pas filmer la saisie du PIN.

---

# 74. Conservation vidéo

La conservation dépend :

- pays ;
- réglementation ;
- incident ;
- assurance ;
- sécurité ;
- politique de rétention ;
- enquête ;
- demande légale.

---

# 75. Protection anti-skimming

Le système doit prévoir :

- lecteur anti-skimming ;
- détection de surcouche ;
- capteur de lecteur ;
- brouillage ;
- inspection ;
- caméra ;
- alerte ;
- blocage automatique ;
- vérification régulière.

---

# 76. Protection du clavier PIN

Le clavier doit :

- être certifié ;
- chiffrer le PIN ;
- résister à la manipulation ;
- détecter l’ouverture ;
- protéger la vue ;
- utiliser des clés sécurisées ;
- être remplacé si compromis.

---

# 77. Sécurité logicielle

Le logiciel doit utiliser :

- système durci ;
- démarrage sécurisé ;
- disque chiffré ;
- liste blanche d’applications ;
- antivirus ou protection adaptée ;
- pare-feu ;
- signature des packages ;
- accès limité ;
- certificats ;
- monitoring ;
- mises à jour.

---

# 78. Mode kiosque

La machine doit empêcher :

- l’accès au bureau ;
- l’ouverture d’autres applications ;
- la modification des paramètres ;
- l’installation non autorisée ;
- l’accès aux ports ;
- la sortie de l’application ;
- l’utilisation d’un navigateur libre.

---

# 79. Ports physiques

Les ports USB, réseau ou maintenance doivent être :

- bloqués ;
- protégés ;
- scellés ;
- limités ;
- contrôlés ;
- journalisés ;
- accessibles uniquement aux techniciens autorisés.

---

# 80. Réseau

La connectivité peut utiliser :

- fibre ;
- Ethernet ;
- 4G ;
- 5G ;
- double SIM ;
- satellite ;
- VPN ;
- réseau privé ;
- connexion de secours.

---

# 81. Double connectivité

Les machines critiques peuvent disposer de :

- connexion principale ;
- connexion secondaire ;
- bascule automatique ;
- supervision indépendante ;
- alerte en cas de dégradation.

---

# 82. Communication sécurisée

La communication doit utiliser :

- chiffrement ;
- authentification mutuelle ;
- certificats ;
- VPN si nécessaire ;
- rotation de clés ;
- restriction réseau ;
- contrôle d’intégrité ;
- protection contre le rejeu.

---

# 83. Mode hors ligne

Par défaut, les opérations financières critiques ne doivent pas être autorisées hors ligne.

Un mode limité peut être prévu uniquement pour :

- affichage d’information ;
- diagnostic ;
- maintenance ;
- réception différée de configuration ;
- opérations expressément approuvées.

---

# 84. HSM

Le HSM peut être utilisé pour :

- vérification PIN ;
- génération de PIN ;
- clés cartes ;
- authentification ;
- chiffrement ;
- signature ;
- gestion de clés TPE et GAB ;
- opérations réseau cartes.

---

# 85. Gestion des clés

Les clés doivent être :

- générées dans un environnement sécurisé ;
- injectées selon procédure ;
- séparées par environnement ;
- renouvelées ;
- révocables ;
- protégées ;
- auditées ;
- jamais exposées en clair.

---

# 86. Injection de clés

L’injection doit suivre :

- identification de la machine ;
- identification des opérateurs ;
- double contrôle ;
- canal sécurisé ;
- confirmation ;
- test ;
- scellé ;
- rapport ;
- audit.

---

# 87. Certificats de machine

Chaque machine doit posséder un certificat unique lié à :

- identifiant ;
- numéro de série ;
- propriétaire ;
- pays ;
- environnement ;
- date d’expiration ;
- autorité ;
- statut.

---

# 88. Attestation de la machine

Le backend peut vérifier :

- version ;
- signature ;
- firmware ;
- certificat ;
- intégrité ;
- matériel ;
- configuration ;
- statut de sécurité ;
- heure ;
- localisation.

---

# 89. Fraude

Les risques comprennent :

- skimming ;
- trapping ;
- carding ;
- retrait avec carte volée ;
- code volé ;
- malware ;
- jackpotting ;
- attaque réseau ;
- manipulation de cassette ;
- faux dépôt ;
- blanchiment ;
- mule ;
- fraude interne ;
- fausse maintenance.

---

# 90. Règles antifraude

Les règles peuvent utiliser :

- montant ;
- fréquence ;
- horaire ;
- localisation ;
- appareil ;
- carte ;
- client ;
- compte ;
- échecs PIN ;
- retraits successifs ;
- vitesse ;
- pays ;
- bénéficiaire ;
- comportement.

---

# 91. Blocage antifraude

Le système peut :

- refuser ;
- limiter ;
- demander une authentification supplémentaire ;
- retenir la carte selon règles ;
- suspendre la machine ;
- geler la transaction ;
- ouvrir un cas ;
- notifier la fraude ;
- alerter le client.

---

# 92. Jackpotting

La protection contre le jackpotting doit inclure :

- système durci ;
- démarrage sécurisé ;
- chiffrement ;
- contrôle du distributeur ;
- isolation réseau ;
- liste blanche ;
- surveillance ;
- alerte d’ouverture ;
- contrôle des ports ;
- arrêt automatique.

---

# 93. Authentification supplémentaire

Elle peut être exigée pour :

- montant élevé ;
- retrait sans carte ;
- comportement inhabituel ;
- machine sensible ;
- premier retrait ;
- changement PIN ;
- retrait international ;
- risque élevé.

---

# 94. OTP

L’OTP peut être envoyé par :

- application ;
- SMS ;
- canal sécurisé ;
- token matériel.

Il doit avoir :

- durée courte ;
- nombre d’essais ;
- usage unique ;
- liaison à l’opération.

---

# 95. Biométrie

La biométrie peut être utilisée uniquement si :

- autorisée ;
- sécurisée ;
- nécessaire ;
- protégée ;
- encadrée ;
- une alternative existe ;
- aucune donnée brute inutile n’est stockée.

---

# 96. Supervision temps réel

L’administration doit voir :

- statut ;
- réseau ;
- énergie ;
- version ;
- cash ;
- cassettes ;
- imprimante ;
- lecteur ;
- clavier ;
- température ;
- caméra ;
- alarmes ;
- transactions ;
- disponibilité ;
- erreurs ;
- maintenance.

---

# 97. Carte du réseau

La plateforme doit afficher :

- machines ;
- type ;
- statut ;
- disponibilité ;
- cash ;
- services ;
- incidents ;
- emplacement ;
- zone ;
- proximité ;
- dernière activité.

---

# 98. Disponibilité publique

L’application Client peut afficher :

- GAB/DAB proches ;
- distance ;
- itinéraire ;
- horaires ;
- retrait disponible ;
- dépôt disponible ;
- langues ;
- accessibilité ;
- frais ;
- statut ;
- espèces disponibles sans exposer le montant exact.

---

# 99. Alertes

Exemples :

- machine hors ligne ;
- cash faible ;
- cash vide ;
- dépôt plein ;
- cassette incohérente ;
- imprimante vide ;
- lecteur défaillant ;
- clavier suspect ;
- porte ouverte ;
- vibration ;
- température ;
- skimming ;
- malware ;
- échec logiciel ;
- certificat expirant ;
- caméra indisponible.

---

# 100. Niveaux d’alerte

- INFO ;
- WARNING ;
- MAJOR ;
- CRITICAL ;
- SECURITY ;
- FINANCIAL.

---

# 101. Escalade

Chaque alerte doit définir :

- équipe ;
- délai ;
- canal ;
- responsable ;
- astreinte ;
- action ;
- seuil ;
- fermeture ;
- preuve.

---

# 102. Maintenance préventive

La maintenance préventive peut couvrir :

- nettoyage ;
- lecteur ;
- imprimante ;
- clavier ;
- écran ;
- distributeur ;
- module dépôt ;
- capteurs ;
- caméra ;
- réseau ;
- batterie ;
- alimentation ;
- logiciel ;
- coffre.

---

# 103. Maintenance corrective

Elle intervient pour :

- panne ;
- blocage ;
- erreur ;
- casse ;
- vandalisme ;
- problème réseau ;
- problème logiciel ;
- billet bloqué ;
- pièce défectueuse ;
- alarme.

---

# 104. Statuts de maintenance

- REQUESTED ;
- ASSIGNED ;
- TRAVELING ;
- ON_SITE ;
- DIAGNOSING ;
- REPAIRING ;
- WAITING_PART ;
- TESTING ;
- COMPLETED ;
- FAILED ;
- CANCELLED ;
- VERIFIED.

---

# 105. Techniciens

Chaque technicien doit avoir :

- identité ;
- employeur ;
- certification ;
- rôle ;
- zone ;
- accès ;
- appareil ;
- planning ;
- historique ;
- statut ;
- habilitations.

---

# 106. Accès maintenance

L’accès doit utiliser :

- ordre de mission ;
- identification ;
- code temporaire ;
- MFA ;
- créneau ;
- machine ciblée ;
- contrôle central ;
- journalisation ;
- fermeture de session.

---

# 107. Mode maintenance

En mode maintenance :

- les opérations clients sont bloquées ;
- un écran d’indisponibilité est affiché ;
- les actions sont journalisées ;
- les périphériques peuvent être testés ;
- l’accès réseau reste limité ;
- le technicien ne doit pas voir les secrets.

---

# 108. Test après maintenance

Avant remise en service :

- démarrage ;
- intégrité ;
- réseau ;
- lecteur ;
- clavier ;
- imprimante ;
- cassettes ;
- distributeur ;
- dépôt ;
- caméra ;
- alarme ;
- transaction de test ;
- télémetrie.

---

# 109. Pièces détachées

Le système peut gérer :

- référence ;
- fabricant ;
- modèle ;
- stock ;
- fournisseur ;
- coût ;
- compatibilité ;
- garantie ;
- historique ;
- emplacement.

---

# 110. Garantie

Chaque machine doit suivre :

- fournisseur ;
- date d’achat ;
- durée ;
- conditions ;
- pièces ;
- intervention ;
- remplacement ;
- expiration.

---

# 111. SLA de maintenance

Le SLA peut dépendre :

- emplacement ;
- criticité ;
- type de panne ;
- ville ;
- partenaire ;
- contrat ;
- sécurité ;
- revenu ;
- disponibilité d’une autre machine.

---

# 112. Mise à jour logicielle

Les mises à jour doivent être :

- signées ;
- testées ;
- ciblées ;
- progressives ;
- planifiées ;
- réversibles ;
- surveillées ;
- bloquées pendant une transaction.

---

# 113. Mise à jour firmware

Elle peut concerner :

- lecteur ;
- clavier ;
- distributeur ;
- imprimante ;
- module dépôt ;
- modem ;
- caméra ;
- contrôleur ;
- capteurs.

---

# 114. Version de secours

La machine doit conserver, lorsque possible :

- version active ;
- version précédente ;
- configuration de secours ;
- image de restauration ;
- procédure de rollback.

---

# 115. Golden Image

Une image de référence doit contenir :

- système ;
- drivers ;
- logiciel GAB/DAB ;
- sécurité ;
- certificats initiaux ;
- configuration ;
- monitoring ;
- outils de diagnostic.

---

# 116. Décommissionnement

Le retrait d’une machine doit inclure :

- arrêt ;
- vidage du cash ;
- retrait des cassettes ;
- révocation des certificats ;
- effacement ;
- retrait des clés ;
- mise à jour de l’inventaire ;
- transport ;
- destruction ou recyclage ;
- preuve.

---

# 117. Frais

Les frais peuvent dépendre :

- type d’opération ;
- client ;
- carte ;
- partenaire ;
- machine ;
- emplacement ;
- montant ;
- devise ;
- pays ;
- heure ;
- réseau ;
- abonnement ;
- promotion.

---

# 118. Affichage des frais

Les frais doivent être affichés avant confirmation.

Le client doit pouvoir :

- accepter ;
- refuser ;
- annuler ;
- choisir une alternative.

---

# 119. Commission

Une transaction peut générer des commissions pour :

- Mansa ;
- banque partenaire ;
- propriétaire du site ;
- réseau cartes ;
- opérateur ;
- exploitant du GAB ;
- prestataire technique ;
- convoyeur selon contrat.

---

# 120. Partage des revenus

Les règles doivent être :

- configurables ;
- versionnées ;
- datées ;
- approuvées ;
- liées au ledger ;
- rapprochées ;
- auditables.

---

# 121. Multi-devises

Une machine peut gérer une ou plusieurs devises selon :

- pays ;
- cassettes ;
- réglementation ;
- contrat ;
- demande ;
- capacité ;
- risque.

---

# 122. Conversion de devise

La conversion doit afficher :

- devise source ;
- devise cible ;
- taux ;
- marge ;
- frais ;
- montant débité ;
- montant distribué ;
- date ;
- fournisseur du taux.

---

# 123. DCC

La conversion dynamique de devise, si activée, doit être :

- clairement expliquée ;
- facultative ;
- transparente ;
- confirmée par le client ;
- conforme ;
- auditée.

---

# 124. Réseau cartes

Le GAB/DAB peut accepter :

- cartes Mansa ;
- cartes de la banque partenaire ;
- Visa ;
- Mastercard ;
- cartes régionales ;
- cartes locales ;
- autres réseaux activés.

---

# 125. Routage des transactions

Le routage dépend :

- BIN ;
- réseau ;
- carte ;
- pays ;
- type de transaction ;
- partenaire ;
- disponibilité ;
- coût ;
- règle de priorité.

---

# 126. Acquéreur

L’acquéreur peut être :

- banque partenaire ;
- processeur ;
- Mansa via partenaire autorisé ;
- opérateur spécialisé.

---

# 127. Autorisation

Le processus doit gérer :

- demande ;
- authentification ;
- montant ;
- devise ;
- frais ;
- réponse ;
- timeout ;
- retry contrôlé ;
- reversals ;
- code réponse ;
- référence.

---

# 128. Timeout

En cas de timeout :

- ne pas supposer l’échec ;
- vérifier le statut ;
- ne pas redistribuer sans confirmation ;
- utiliser la référence ;
- déclencher un reversal si nécessaire ;
- rapprocher.

---

# 129. Idempotence

Chaque transaction doit avoir :

- référence unique ;
- identifiant machine ;
- identifiant session ;
- identifiant réseau ;
- clé d’idempotence ;
- statut ;
- historique.

---

# 130. API principales

Exemples :

```http
GET    /atm-machines
POST   /atm-machines
GET    /atm-machines/{id}
PATCH  /atm-machines/{id}

POST   /atm-machines/{id}/activate
POST   /atm-machines/{id}/suspend
POST   /atm-machines/{id}/maintenance
POST   /atm-machines/{id}/quarantine

POST   /atm/withdrawals
POST   /atm/cardless-withdrawals
POST   /atm/deposits
POST   /atm/balance-inquiries
POST   /atm/pin-change
POST   /atm/bill-payments
POST   /atm/mobile-money-topups

GET    /atm-machines/{id}/cassettes
POST   /atm-machines/{id}/cash-loading
POST   /atm-machines/{id}/cash-unloading

GET    /atm-machines/{id}/telemetry
GET    /atm-machines/{id}/incidents
GET    /atm-machines/{id}/maintenance
GET    /atm/reconciliation
GET    /atm/audit
```

---

# 131. Webhooks internes

Événements possibles :

```text
atm.machine.installed
atm.machine.activated
atm.machine.offline
atm.machine.cash_low
atm.machine.cash_empty
atm.machine.deposit_full
atm.machine.security_alert
atm.machine.maintenance_started
atm.machine.maintenance.completed

atm.withdrawal.started
atm.withdrawal.authorized
atm.withdrawal.dispensed
atm.withdrawal.failed
atm.withdrawal.reversed
atm.withdrawal.reconciliation_required

atm.deposit.started
atm.deposit.accepted
atm.deposit.failed
atm.deposit.suspect_banknote_detected

atm.card.retained
atm.cash.discrepancy_detected
atm.cassette.loaded
atm.cassette.unloaded
```

---

# 132. Modèles principaux

- ATMMachine
- ATMType
- ATMLocation
- ATMOwner
- ATMOperator
- ATMCapability
- ATMConfiguration
- ATMSoftwareVersion
- ATMCertificate
- ATMKey
- ATMSession
- ATMTransaction
- ATMWithdrawal
- ATMCardlessWithdrawal
- ATMDeposit
- ATMDepositBanknote
- ATMCassette
- ATMCashMovement
- ATMCashForecast
- ATMReconciliation
- ATMDiscrepancy
- ATMPeripheral
- ATMAlarm
- ATMIncident
- ATMMaintenance
- ATMTechnician
- ATMWorkOrder
- ATMReceipt
- ATMAudit

---

# 133. Administration centrale

L’administration doit permettre de gérer :

- machines ;
- types ;
- modèles ;
- fabricants ;
- emplacements ;
- services ;
- frais ;
- commissions ;
- limites ;
- devises ;
- cassettes ;
- billets ;
- cash ;
- transactions ;
- incidents ;
- alarmes ;
- versions ;
- configurations ;
- certificats ;
- techniciens ;
- convoyeurs ;
- maintenance ;
- rapports ;
- audits.

---

# 134. Rôles

Exemples :

```text
ATM_NETWORK_ADMIN
ATM_OPERATIONS_MANAGER
ATM_CASH_MANAGER
ATM_SECURITY_MANAGER
ATM_SOFTWARE_MANAGER
ATM_MAINTENANCE_MANAGER
ATM_TECHNICIAN
ATM_RECONCILIATION_OPERATOR
ATM_FRAUD_ANALYST
ATM_SUPPORT_OPERATOR
CASH_IN_TRANSIT_OPERATOR
FINANCE_APPROVER
SECURITY_APPROVER
AUDITOR
VIEWER
```

---

# 135. Permissions

Exemples :

```text
atm.read
atm.create
atm.update
atm.activate
atm.suspend
atm.quarantine

atm.transaction.read
atm.withdrawal.read
atm.deposit.read
atm.reconciliation.manage

atm.cash.read
atm.cash.load
atm.cash.unload
atm.cassette.manage
atm.discrepancy.manage

atm.maintenance.create
atm.maintenance.assign
atm.maintenance.complete

atm.configuration.manage
atm.software.deploy
atm.certificate.rotate
atm.security.alert.manage
atm.audit.read
```

---

# 136. Approbations

Peuvent nécessiter une approbation :

- activation d’une machine ;
- ouverture du coffre ;
- chargement de cash ;
- déchargement ;
- correction d’écart ;
- changement de frais ;
- changement de limite ;
- mise à jour logicielle ;
- rotation de clés ;
- mise hors service ;
- remboursement manuel ;
- décommissionnement.

---

# 137. Double validation

Doit être exigée pour :

- chargement important de cash ;
- déchargement ;
- ouverture du coffre ;
- injection de clés ;
- correction financière ;
- changement HSM ;
- activation d’un nouveau GAB ;
- modification nationale des frais ;
- déploiement logiciel global ;
- suppression d’une transaction ;
- décommissionnement.

---

# 138. Reporting

Rapports possibles :

- machines actives ;
- machines hors ligne ;
- disponibilité ;
- retraits ;
- dépôts ;
- montants ;
- frais ;
- commissions ;
- cash ;
- cassettes ;
- écarts ;
- incidents ;
- maintenance ;
- sécurité ;
- fraude ;
- coûts ;
- rentabilité ;
- performance par site.

---

# 139. Indicateurs

Exemples :

- taux de disponibilité ;
- volume de retraits ;
- volume de dépôts ;
- valeur distribuée ;
- valeur déposée ;
- taux de succès ;
- taux d’échec ;
- cash-out ;
- coût par transaction ;
- revenu par machine ;
- temps moyen de réparation ;
- fréquence de réapprovisionnement ;
- écarts de caisse ;
- incidents de fraude ;
- satisfaction.

---

# 140. Rentabilité

La rentabilité doit prendre en compte :

- achat ;
- installation ;
- loyer ;
- sécurité ;
- énergie ;
- réseau ;
- cash ;
- convoyage ;
- maintenance ;
- assurance ;
- licences ;
- frais partenaires ;
- revenu ;
- volume ;
- disponibilité.

---

# 141. Tests fonctionnels

- retrait avec carte ;
- retrait sans carte ;
- retrait tiers ;
- consultation ;
- mini-relevé ;
- changement PIN ;
- dépôt ;
- dépôt tiers ;
- paiement de facture ;
- recharge ;
- transfert ;
- reçu ;
- choix de langue ;
- accessibilité.

---

# 142. Tests matériels

- lecteur ;
- NFC ;
- clavier ;
- écran ;
- imprimante ;
- distributeur ;
- dépôt ;
- recycleur ;
- cassettes ;
- caméra ;
- capteurs ;
- coffre ;
- alimentation ;
- batterie ;
- réseau.

---

# 143. Tests financiers

- autorisation ;
- ledger ;
- frais ;
- commission ;
- reversal ;
- distribution partielle ;
- billet non pris ;
- débit sans distribution ;
- dépôt bloqué ;
- écart ;
- rapprochement ;
- remboursement.

---

# 144. Tests de sécurité

- skimming ;
- PIN ;
- ports ;
- malware ;
- jackpotting ;
- certificat ;
- clé ;
- ouverture ;
- alarme ;
- caméra ;
- réseau ;
- accès technicien ;
- mise à jour ;
- rollback ;
- falsification.

---

# 145. Tests de résilience

- panne réseau ;
- bascule SIM ;
- panne électrique ;
- redémarrage ;
- timeout ;
- partenaire indisponible ;
- base indisponible ;
- HSM indisponible ;
- cassette bloquée ;
- imprimante défaillante ;
- reprise après incident.

---

# 146. Tests de performance

- temps d’authentification ;
- temps d’autorisation ;
- temps de distribution ;
- temps de dépôt ;
- capacité ;
- sessions simultanées ;
- volume journalier ;
- télémetrie ;
- reporting.

---

# 147. Règles métier

1. Les GAB et les DAB sont deux catégories distinctes.
2. Toute machine possède un identifiant unique.
3. Toute opération financière passe par le ledger.
4. Aucun débit définitif sans confirmation de distribution.
5. Les retraits sans carte utilisent un token à durée limitée.
6. Les frais sont affichés avant confirmation.
7. Les billets déposés sont contrôlés.
8. Les billets suspects sont isolés.
9. Le recyclage n’utilise que les billets conformes.
10. Toute cassette est identifiée.
11. Les mouvements de cash sont rapprochés.
12. Les écarts sont investigués.
13. Toute machine critique est supervisée.
14. Toute alarme de sécurité est tracée.
15. Les machines compromises sont mises en quarantaine.
16. Les clés ne sont jamais exposées en clair.
17. Les mises à jour sont signées.
18. Une version de secours est prévue.
19. Les techniciens ont des accès temporaires.
20. Les opérations de cash sensibles utilisent un double contrôle.
21. Les journaux ne contiennent pas de PIN.
22. Les caméras ne filment pas la saisie du PIN.
23. Une machine sans cash peut continuer les services non liés au retrait.
24. Le dépôt peut être désactivé indépendamment du retrait.
25. Les audits sont immuables.

---

# 148. Critères d’acceptation

Le Réseau GAB/DAB Mansa est validé lorsque :

- les types de machines sont définis ;
- les GAB et DAB sont séparés ;
- les emplacements sont gérés ;
- chaque machine possède une fiche complète ;
- les statuts sont administrables ;
- le retrait avec carte fonctionne ;
- le retrait sans carte fonctionne ;
- le retrait par tiers est supporté ;
- les codes expirent ;
- les limites sont configurables ;
- les montants rapides sont dynamiques ;
- la distribution tient compte des coupures ;
- les préautorisations sont gérées ;
- le débit sans distribution est traité ;
- la distribution partielle est gérée ;
- les billets non récupérés sont traités ;
- les cartes retenues sont gérées ;
- la consultation du solde fonctionne ;
- les mini-relevés fonctionnent ;
- le changement PIN est sécurisé ;
- le dépôt d’espèces fonctionne sur les modèles compatibles ;
- le dépôt sans carte est supporté ;
- le dépôt tiers est contrôlé ;
- les limites de dépôt sont configurables ;
- les billets sont authentifiés ;
- les billets suspects sont isolés ;
- les billets abîmés sont traités ;
- le dépôt est confirmé par le client ;
- les dépôts bloqués créent un incident ;
- le recyclage est supporté ;
- le paiement de factures est intégré ;
- la recharge Mobile Money est intégrée ;
- le transfert est supporté ;
- l’assistance est disponible ;
- les langues sont configurables ;
- l’accessibilité est prise en charge ;
- les reçus papier et numériques sont disponibles ;
- l’imprimante est supervisée ;
- les cassettes sont inventoriées ;
- les statuts de cassette sont gérés ;
- les chargements sont tracés ;
- les déchargements sont tracés ;
- le cash est supervisé ;
- les besoins sont prévisibles ;
- les alertes cash faible fonctionnent ;
- le cash vide désactive le retrait ;
- le dépôt plein désactive le dépôt ;
- les missions de convoyage sont suivies ;
- le double contrôle est appliqué ;
- le rapprochement cash fonctionne ;
- les écarts sont détectés ;
- la réconciliation transactionnelle fonctionne ;
- les journaux électroniques sont conservés ;
- les données sensibles sont exclues des logs ;
- la sécurité physique est définie ;
- les coffres sont protégés ;
- les serrures sont gérées ;
- les capteurs sont intégrés ;
- les caméras sont contrôlées ;
- l’anti-skimming est disponible ;
- le clavier PIN est sécurisé ;
- le système est durci ;
- le mode kiosque est appliqué ;
- les ports sont contrôlés ;
- la connectivité de secours est supportée ;
- les communications sont chiffrées ;
- le mode hors ligne est limité ;
- le HSM est intégré ;
- les clés sont gérées ;
- l’injection de clés est sécurisée ;
- les certificats sont uniques ;
- l’attestation de machine fonctionne ;
- les règles antifraude sont appliquées ;
- le jackpotting est pris en compte ;
- l’authentification supplémentaire est disponible ;
- la supervision temps réel fonctionne ;
- la carte du réseau est disponible ;
- l’application Client peut afficher les machines disponibles ;
- les alertes sont configurables ;
- les escalades sont définies ;
- la maintenance préventive est gérée ;
- la maintenance corrective est gérée ;
- les techniciens sont habilités ;
- les accès maintenance sont temporaires ;
- les tests après maintenance sont obligatoires ;
- les pièces détachées sont suivies ;
- les garanties sont suivies ;
- les SLA sont mesurés ;
- les mises à jour logicielles sont signées ;
- les firmwares sont versionnés ;
- une version de secours est disponible ;
- une Golden Image existe ;
- le décommissionnement est sécurisé ;
- les frais sont configurables ;
- les commissions sont configurables ;
- le multi-devises est supporté ;
- la conversion est transparente ;
- les réseaux cartes sont routables ;
- les timeouts sont rapprochés ;
- l’idempotence est appliquée ;
- les API sont disponibles ;
- les webhooks sont disponibles ;
- les rôles et permissions sont définis ;
- les approbations critiques sont protégées ;
- les rapports sont disponibles ;
- les indicateurs sont calculés ;
- la rentabilité est mesurable ;
- les tests couvrent les parcours fonctionnels, matériels, financiers, sécuritaires et de résilience ;
- les audits sont immuables.
