# 76 — Application TPE Mansa : encaissement, carte, NFC, QR, Mobile Money, remboursement, annulation, impression, mode hors ligne, sécurité, supervision et administration centralisée

## 1. Objet du document

Ce document définit le cahier des charges complet de l’**Application TPE Mansa**.

L’Application TPE constitue l’interface utilisée sur les terminaux de paiement Android ou sur certains appareils compatibles afin de permettre aux commerçants, entreprises, agents et institutions d’accepter des paiements.

Elle doit fonctionner notamment sur :

- TPE Android ;
- terminaux avec lecteur de carte ;
- terminaux avec NFC ;
- terminaux avec imprimante ;
- smartphones Android compatibles avec Tap to Pay ;
- tablettes professionnelles ;
- appareils intégrés à une caisse ;
- terminaux fournis par Mansa ;
- terminaux fournis par un partenaire.

L’application doit permettre notamment :

- les paiements par carte ;
- les paiements sans contact ;
- les paiements par QR Code ;
- les paiements Mobile Money ;
- les paiements Mansa à Mansa ;
- les remboursements ;
- les annulations ;
- les préautorisations ;
- les cautions ;
- les pourboires ;
- le partage d’addition ;
- les reçus papier et numériques ;
- la fermeture de caisse ;
- le mode hors ligne contrôlé ;
- la synchronisation ;
- la gestion des périphériques ;
- la mise à jour distante ;
- la supervision ;
- la sécurité ;
- le support ;
- la maintenance ;
- l’administration centralisée.

L’application doit être :

- simple ;
- rapide ;
- robuste ;
- sécurisée ;
- administrable ;
- multilingue ;
- multi-pays ;
- multi-devises ;
- compatible avec les réseaux faibles ;
- adaptée à différents modèles de terminaux ;
- utilisable par des employés peu formés ;
- capable de fonctionner dans un environnement professionnel intensif.

---

# 2. Principes fondamentaux

## 2.1 Toute transaction doit être traçable

Chaque transaction doit posséder :

- un identifiant unique ;
- un identifiant commerçant ;
- un identifiant point de vente ;
- un identifiant terminal ;
- un identifiant employé ;
- un identifiant caisse ;
- une référence ledger ;
- une référence acquéreur ;
- une référence réseau ;
- un statut ;
- une date ;
- une heure ;
- un reçu ;
- un journal d’audit.

---

## 2.2 Aucun paiement ne doit rester dans un état indéterminé

Une transaction doit toujours finir dans un état connu :

- COMPLETED ;
- FAILED ;
- CANCELLED ;
- REVERSED ;
- REFUNDED ;
- PARTIALLY_REFUNDED ;
- PENDING_RECONCILIATION ;
- REVIEW_REQUIRED.

En cas d’incertitude, le terminal ne doit pas proposer de relancer immédiatement sans vérifier le statut précédent.

---

## 2.3 Aucun double paiement

L’application doit empêcher :

- double appui ;
- double présentation de carte ;
- double scan ;
- double synchronisation ;
- double reprise après timeout ;
- double débit lors d’un redémarrage ;
- double émission de reçu comme preuve de paiement.

---

## 2.4 Les frais doivent être transparents

Avant confirmation, l’écran doit afficher lorsque nécessaire :

- montant ;
- devise ;
- frais ;
- pourboire ;
- conversion ;
- total ;
- bénéficiaire ;
- moyen de paiement.

---

## 2.5 Le TPE ne doit jamais exposer les données carte sensibles

L’application ne doit jamais afficher ou stocker en clair :

- PAN complet ;
- PIN ;
- CVV ;
- clés cryptographiques ;
- données de piste ;
- secrets HSM ;
- token de sécurité complet.

---

# 3. Types de terminaux

Le système doit gérer :

- TPE Android avec imprimante ;
- TPE Android sans imprimante ;
- TPE fixe ;
- TPE portable ;
- TPE mobile ;
- TPE de restaurant ;
- TPE de grande distribution ;
- TPE Agent ;
- TPE institutionnel ;
- TPE de démonstration ;
- SoftPOS ;
- Tap to Pay ;
- caisse Android avec paiement intégré ;
- terminal partenaire.

---

# 4. Fabricants et modèles

Le système doit pouvoir gérer plusieurs fabricants, notamment selon les contrats disponibles :

- PAX ;
- Ingenico ;
- Verifone ;
- Newland ;
- Sunmi ;
- Castles ;
- Nexgo ;
- autres fabricants compatibles.

La logique métier ne doit pas dépendre d’un seul fabricant.

---

# 5. Fiche d’un terminal

Chaque terminal doit posséder :

- identifiant unique ;
- numéro de série ;
- fabricant ;
- modèle ;
- version matérielle ;
- version Android ;
- version de l’application ;
- version du firmware ;
- commerçant ;
- point de vente ;
- caisse ;
- utilisateur affecté ;
- pays ;
- devise ;
- statut ;
- certificat ;
- date d’installation ;
- dernière activité ;
- dernière synchronisation ;
- dernière maintenance ;
- batterie ;
- réseau ;
- périphériques ;
- capacités.

---

# 6. Statuts du terminal

- PENDING_ENROLLMENT ;
- ENROLLED ;
- ACTIVE ;
- INACTIVE ;
- SUSPENDED ;
- OFFLINE ;
- DEGRADED ;
- MAINTENANCE ;
- LOST ;
- STOLEN ;
- COMPROMISED ;
- QUARANTINED ;
- DECOMMISSIONED.

---

# 7. Capacités d’un terminal

Chaque terminal peut avoir des capacités différentes :

- puce EMV ;
- sans contact ;
- bande magnétique ;
- QR ;
- caméra ;
- imprimante ;
- clavier PIN ;
- écran tactile ;
- scanner ;
- NFC ;
- 4G ;
- Wi-Fi ;
- Ethernet ;
- double SIM ;
- batterie ;
- caisse connectée ;
- lecteur code-barres.

---

# 8. Enrôlement du terminal

Le processus doit inclure :

1. création du terminal dans l’administration ;
2. affectation au commerçant ;
3. affectation au point de vente ;
4. génération d’un code d’enrôlement ;
5. installation de l’application ;
6. identification de l’appareil ;
7. attestation d’intégrité ;
8. téléchargement de la configuration ;
9. installation du certificat ;
10. activation ;
11. transaction de test ;
12. validation finale.

---

# 9. Code d’enrôlement

Le code d’enrôlement doit être :

- temporaire ;
- à usage unique ;
- lié à un terminal ;
- lié à un commerçant ;
- lié à un environnement ;
- expirant ;
- audité ;
- invalidé après utilisation.

---

# 10. Connexion d’un employé

La connexion peut utiliser :

- PIN employé ;
- mot de passe ;
- badge ;
- QR ;
- biométrie ;
- appareil déjà approuvé ;
- authentification forte.

---

# 11. Session employé

La session doit enregistrer :

- utilisateur ;
- terminal ;
- caisse ;
- point de vente ;
- date ;
- heure ;
- rôle ;
- permissions ;
- statut ;
- fermeture ;
- anomalies.

---

# 12. Ouverture de caisse

Avant d’accepter des paiements, l’employé peut devoir :

- s’identifier ;
- choisir la caisse ;
- vérifier le terminal ;
- confirmer le fond de caisse éventuel ;
- vérifier le papier ;
- vérifier la connexion ;
- confirmer l’ouverture.

---

# 13. Écran d’accueil

L’écran d’accueil doit proposer :

- Nouveau paiement ;
- Scanner un QR ;
- Rembourser ;
- Annuler ;
- Transactions ;
- Caisse ;
- Reçus ;
- Paramètres ;
- Support ;
- Synchroniser.

L’ordre doit être configurable.

---

# 14. Nouveau paiement

Le commerçant peut :

- saisir un montant ;
- ajouter une description ;
- choisir une devise ;
- ajouter un pourboire ;
- choisir un client ;
- sélectionner un produit ;
- lancer la lecture carte ;
- générer un QR ;
- choisir Mobile Money ;
- envoyer un lien.

---

# 15. Saisie du montant

L’écran doit :

- utiliser un pavé numérique ;
- éviter les erreurs de décimales ;
- afficher la devise ;
- afficher les limites ;
- permettre une correction ;
- empêcher un montant négatif ;
- empêcher un montant nul ;
- appliquer un plafond ;
- vérifier les droits.

---

# 16. Vente depuis le catalogue

Le terminal peut permettre :

- recherche produit ;
- catégories ;
- ajout d’articles ;
- quantité ;
- remise ;
- taxe ;
- variation ;
- supplément ;
- suppression ;
- total ;
- panier.

---

# 17. Paiement par carte à puce

Le parcours doit inclure :

1. saisie du montant ;
2. insertion de la carte ;
3. lecture EMV ;
4. détection du réseau ;
5. sélection d’application si nécessaire ;
6. saisie du PIN ;
7. demande d’autorisation ;
8. affichage du résultat ;
9. retrait de la carte ;
10. reçu ;
11. écriture ledger ;
12. notification.

---

# 18. Paiement sans contact

Le parcours doit permettre :

- présentation de la carte ;
- présentation d’un téléphone ;
- lecture NFC ;
- tokenisation ;
- vérification du montant ;
- authentification si nécessaire ;
- confirmation ;
- reçu.

---

# 19. Limite sans contact

La limite peut dépendre :

- du pays ;
- du réseau ;
- de la carte ;
- du montant cumulé ;
- de la réglementation ;
- du niveau de risque ;
- du terminal ;
- de l’émetteur.

Au-delà du seuil, un PIN ou une autre authentification peut être exigé.

---

# 20. Paiement par bande magnétique

Ce mode doit être :

- désactivable ;
- réservé aux pays ou réseaux autorisés ;
- surveillé ;
- soumis à des règles antifraude renforcées ;
- refusé si une carte à puce doit être utilisée.

---

# 21. Saisie manuelle de carte

La saisie manuelle doit être fortement limitée.

Elle peut être autorisée uniquement pour certains rôles et parcours, avec :

- permission ;
- justification ;
- authentification ;
- masque des données ;
- contrôle fraude ;
- audit ;
- restrictions PCI.

---

# 22. Paiement QR Mansa

Le terminal peut générer un QR contenant :

- commerçant ;
- caisse ;
- terminal ;
- montant ;
- devise ;
- référence ;
- expiration ;
- signature ;
- point de vente.

---

# 23. Paiement QR statique

Le commerçant peut afficher un QR permanent.

Le client doit :

- scanner ;
- vérifier le commerçant ;
- saisir le montant ;
- confirmer ;
- payer ;
- attendre la confirmation du terminal.

---

# 24. Paiement QR dynamique

Le terminal génère un QR à usage unique lié à la transaction.

Le QR doit expirer :

- après paiement ;
- après annulation ;
- après délai ;
- après fermeture de session ;
- après changement de montant.

---

# 25. Paiement Mobile Money

Le terminal doit permettre :

- choix de l’opérateur ;
- saisie ou scan du numéro ;
- demande de paiement ;
- validation côté client ;
- réception du statut ;
- reçu ;
- réconciliation.

---

# 26. Demande Mobile Money

La demande doit contenir :

- montant ;
- devise ;
- commerçant ;
- numéro ;
- opérateur ;
- référence ;
- expiration ;
- frais ;
- statut.

---

# 27. Paiement Mansa

Un client Mansa peut payer via :

- QR ;
- NFC ;
- téléphone ;
- identifiant ;
- lien ;
- notification ;
- code.

---

# 28. Tap to Pay

Le SoftPOS peut transformer un téléphone compatible en terminal de paiement.

Il doit vérifier :

- compatibilité matérielle ;
- sécurité de l’appareil ;
- NFC ;
- intégrité ;
- version Android ;
- attestation ;
- certificat ;
- commerçant ;
- limites ;
- pays.

---

# 29. Restriction SoftPOS

Le SoftPOS peut être limité selon :

- montant ;
- carte ;
- pays ;
- type de commerçant ;
- appareil ;
- niveau de risque ;
- connexion ;
- version.

---

# 30. Paiement par lien

Le terminal peut générer un lien contenant :

- montant ;
- devise ;
- description ;
- référence ;
- expiration ;
- commerçant ;
- options de paiement ;
- reçu.

---

# 31. Paiement à distance

Le paiement à distance peut être utilisé pour :

- commande téléphonique ;
- livraison ;
- réservation ;
- service ;
- facture ;
- acompte.

Il doit être soumis à des règles de risque spécifiques.

---

# 32. Pourboire

Le terminal peut proposer :

- aucun pourboire ;
- montant fixe ;
- pourcentage ;
- montant libre ;
- valeurs prédéfinies.

Le pourboire doit être séparé dans le reporting.

---

# 33. Split Payment

Une addition peut être divisée :

- à parts égales ;
- par montant ;
- par article ;
- par moyen de paiement ;
- entre plusieurs personnes ;
- entre espèces et paiement numérique ;
- entre plusieurs cartes.

---

# 34. Paiement multiple

Le terminal doit suivre :

- montant total ;
- part payée ;
- reste ;
- participants ;
- moyens de paiement ;
- statuts ;
- annulations ;
- reçus.

---

# 35. Paiement partiel

Un paiement partiel peut être autorisé selon :

- commerce ;
- type de vente ;
- utilisateur ;
- configuration ;
- produit ;
- facture.

---

# 36. Préautorisation

La préautorisation peut être utilisée pour :

- hôtel ;
- location ;
- carburant ;
- caution ;
- réservation ;
- restaurant ;
- service.

Elle doit gérer :

- montant réservé ;
- durée ;
- augmentation ;
- confirmation ;
- annulation ;
- expiration ;
- libération.

---

# 37. Finalisation d’une préautorisation

Le commerçant peut :

- confirmer le montant initial ;
- diminuer ;
- augmenter selon règles ;
- ajouter un pourboire ;
- annuler ;
- transformer en paiement final.

---

# 38. Annulation d’une transaction

L’annulation peut être autorisée avant règlement ou avant clôture selon les règles.

Elle doit vérifier :

- transaction ;
- statut ;
- utilisateur ;
- délai ;
- montant ;
- permission ;
- authentification ;
- raison.

---

# 39. Remboursement

Le remboursement peut être :

- total ;
- partiel ;
- multiple ;
- lié à une transaction ;
- vers le moyen de paiement d’origine ;
- soumis à validation.

---

# 40. Parcours de remboursement

1. rechercher la transaction ;
2. vérifier le statut ;
3. saisir le montant ;
4. choisir le motif ;
5. vérifier les permissions ;
6. authentifier ;
7. envoyer la demande ;
8. recevoir la confirmation ;
9. imprimer ou envoyer le reçu ;
10. mettre à jour le ledger.

---

# 41. Limites de remboursement

Les limites peuvent dépendre :

- employé ;
- rôle ;
- montant ;
- ancienneté de la vente ;
- commerçant ;
- pays ;
- moyen de paiement ;
- risque ;
- approbation.

---

# 42. Remboursement sans transaction

Il doit être interdit par défaut.

S’il est exceptionnellement autorisé, il doit exiger :

- rôle élevé ;
- double validation ;
- justification ;
- preuve ;
- plafond ;
- audit ;
- rapprochement.

---

# 43. Transaction refusée

L’écran doit afficher un message compréhensible sans exposer d’informations sensibles.

Exemples :

- Paiement refusé ;
- Fonds insuffisants ;
- Carte expirée ;
- PIN incorrect ;
- Moyen non accepté ;
- Réessaie avec un autre moyen.

---

# 44. Timeout

En cas de timeout :

- afficher Vérification en cours ;
- ne pas relancer automatiquement ;
- interroger le statut ;
- conserver la référence ;
- créer une réconciliation si nécessaire ;
- informer le commerçant ;
- éviter un double débit.

---

# 45. Reversal

Un reversal doit être envoyé lorsque :

- l’autorisation a réussi mais le terminal n’a pas finalisé ;
- la communication a été interrompue ;
- le paiement ne peut être confirmé ;
- la transaction a été abandonnée après autorisation.

---

# 46. Reçu papier

Le reçu papier peut contenir :

- nom du commerçant ;
- adresse ;
- terminal ;
- caisse ;
- employé ;
- date ;
- heure ;
- montant ;
- devise ;
- frais ;
- pourboire ;
- moyen masqué ;
- référence ;
- statut ;
- contact support.

---

# 47. Reçu numérique

Le reçu peut être envoyé par :

- QR ;
- SMS ;
- e-mail ;
- application Mansa ;
- lien ;
- impression différée.

---

# 48. Choix du reçu

Le client peut choisir :

- papier ;
- numérique ;
- les deux ;
- aucun.

Certaines transactions réglementaires peuvent imposer un reçu.

---

# 49. Imprimante

L’application doit suivre :

- état ;
- papier ;
- température ;
- couvercle ;
- bourrage ;
- erreur ;
- test ;
- dernière impression ;
- modèle.

---

# 50. Réimpression

La réimpression doit être :

- liée à une transaction ;
- marquée comme DUPLICATA ;
- soumise à permission ;
- auditée ;
- limitée dans le temps si nécessaire.

---

# 51. Historique des transactions

Le terminal doit permettre :

- liste ;
- recherche ;
- filtres ;
- période ;
- statut ;
- moyen de paiement ;
- employé ;
- caisse ;
- montant ;
- référence.

---

# 52. Détail d’une transaction

Le détail doit afficher :

- montant ;
- devise ;
- statut ;
- type ;
- réseau ;
- carte masquée ;
- date ;
- heure ;
- référence ;
- reçu ;
- remboursement ;
- annulation ;
- synchronisation ;
- employé ;
- caisse.

---

# 53. Recherche

La recherche peut utiliser :

- référence ;
- montant ;
- date ;
- heure ;
- quatre derniers chiffres ;
- client ;
- reçu ;
- employé ;
- caisse.

---

# 54. Ouverture et fermeture de caisse

La caisse doit enregistrer :

- heure d’ouverture ;
- heure de fermeture ;
- employé ;
- terminal ;
- ventes ;
- remboursements ;
- annulations ;
- pourboires ;
- commissions ;
- écarts ;
- signature.

---

# 55. Clôture journalière

La clôture peut afficher :

- total brut ;
- total net ;
- ventes ;
- remboursements ;
- frais ;
- commissions ;
- moyens de paiement ;
- volume ;
- nombre de transactions ;
- anomalies ;
- statut de règlement.

---

# 56. Lot de transactions

Les transactions peuvent être regroupées par :

- journée ;
- caisse ;
- terminal ;
- commerçant ;
- point de vente ;
- acquéreur ;
- devise ;
- réseau.

---

# 57. Règlement commerçant

Le commerçant doit pouvoir consulter :

- montant brut ;
- frais ;
- commission ;
- remboursement ;
- réserve ;
- montant net ;
- date de règlement ;
- compte destinataire ;
- statut ;
- référence.

---

# 58. Statuts de règlement

- PENDING ;
- CALCULATED ;
- APPROVED ;
- SENT ;
- COMPLETED ;
- FAILED ;
- HELD ;
- RECONCILIATION_REQUIRED.

---

# 59. Mode hors ligne

Le mode hors ligne doit être limité et contrôlé.

Il peut être activé selon :

- pays ;
- commerçant ;
- terminal ;
- montant ;
- carte ;
- durée ;
- nombre de transactions ;
- niveau de risque ;
- réseau ;
- contrat.

---

# 60. Principes du mode hors ligne

Le terminal doit :

- afficher clairement le mode hors ligne ;
- appliquer des limites réduites ;
- chiffrer les transactions ;
- conserver l’ordre ;
- empêcher les doublons ;
- synchroniser rapidement ;
- refuser au-delà des seuils ;
- informer le commerçant du risque.

---

# 61. Transactions hors ligne

Chaque transaction hors ligne doit contenir :

- référence ;
- heure locale ;
- heure sécurisée ;
- montant ;
- moyen ;
- données chiffrées ;
- compteur ;
- statut ;
- preuve d’intégrité ;
- appareil ;
- employé.

---

# 62. Limites hors ligne

Limites possibles :

- montant par transaction ;
- montant cumulé ;
- nombre de transactions ;
- durée maximale ;
- carte autorisée ;
- pays ;
- commerçant ;
- catégorie ;
- risque.

---

# 63. Synchronisation

Après reconnexion, le terminal doit :

1. vérifier son intégrité ;
2. vérifier sa session ;
3. charger la configuration ;
4. envoyer les transactions dans l’ordre ;
5. recevoir les statuts ;
6. traiter les refus ;
7. rapprocher ;
8. mettre à jour le commerçant ;
9. envoyer les alertes.

---

# 64. Refus après synchronisation

Une transaction hors ligne peut être refusée après reconnexion.

Le système doit :

- notifier le commerçant ;
- créer une créance ou un dossier si nécessaire ;
- conserver la preuve ;
- mettre à jour le reporting ;
- appliquer les règles contractuelles ;
- ouvrir un cas fraude éventuel.

---

# 65. Queue locale

La queue locale doit être :

- chiffrée ;
- ordonnée ;
- durable ;
- limitée ;
- signée ;
- protégée contre la modification ;
- supprimée après confirmation sécurisée.

---

# 66. Réseau faible

L’application doit :

- détecter la qualité réseau ;
- réduire les appels ;
- reprendre les demandes ;
- afficher le statut ;
- éviter les doubles envois ;
- utiliser des timeouts adaptés ;
- changer de réseau si possible.

---

# 67. Connectivité

Le terminal peut utiliser :

- Wi-Fi ;
- Ethernet ;
- 4G ;
- 5G ;
- double SIM ;
- réseau privé ;
- VPN ;
- connexion de secours.

---

# 68. Bascule réseau

La bascule doit être :

- automatique ;
- rapide ;
- journalisée ;
- surveillée ;
- sans double transaction ;
- configurable.

---

# 69. Sécurité du terminal

La sécurité doit couvrir :

- enrôlement ;
- certificat ;
- appareil ;
- système ;
- application ;
- stockage ;
- réseau ;
- clés ;
- utilisateur ;
- session ;
- périphériques ;
- mise à jour ;
- logs.

---

# 70. Mode kiosque

Le terminal doit empêcher :

- sortie de l’application ;
- accès au bureau ;
- installation libre ;
- navigation web libre ;
- accès aux paramètres ;
- accès aux fichiers ;
- usage personnel ;
- capture non autorisée.

---

# 71. Démarrage sécurisé

Le terminal doit vérifier :

- système ;
- bootloader ;
- signature ;
- application ;
- firmware ;
- certificat ;
- intégrité ;
- date ;
- configuration.

---

# 72. Détection root

Un terminal rooté ou compromis doit être :

- bloqué ;
- limité ;
- placé en quarantaine ;
- signalé ;
- audité ;
- désactivé à distance selon le risque.

---

# 73. Attestation d’intégrité

Le backend peut vérifier :

- modèle ;
- OS ;
- version ;
- application ;
- signature ;
- état root ;
- certificat ;
- identifiant ;
- configuration ;
- heure ;
- localisation éventuelle.

---

# 74. Certificat du terminal

Chaque terminal doit posséder un certificat unique avec :

- identité ;
- commerçant ;
- environnement ;
- expiration ;
- statut ;
- autorité ;
- date d’émission ;
- révocation.

---

# 75. Gestion des clés

Les clés doivent être :

- générées dans un environnement sécurisé ;
- injectées selon procédure ;
- séparées par environnement ;
- rotatives ;
- révocables ;
- auditées ;
- protégées par HSM lorsque nécessaire.

---

# 76. Injection de clés

L’injection doit suivre :

- identification du terminal ;
- canal sécurisé ;
- double contrôle ;
- preuve ;
- test ;
- confirmation ;
- audit ;
- séparation des rôles.

---

# 77. PIN

La saisie du PIN doit utiliser :

- clavier sécurisé ;
- chiffrement immédiat ;
- protection visuelle ;
- nombre d’essais ;
- détection de manipulation ;
- HSM ;
- aucune journalisation en clair.

---

# 78. Protection PCI

La conception doit prendre en compte les exigences applicables au traitement des cartes, notamment :

- réduction des données ;
- tokenisation ;
- chiffrement ;
- segmentation ;
- journalisation ;
- contrôle d’accès ;
- tests ;
- gestion des clés ;
- certification du matériel.

---

# 79. Protection des données locales

Les données locales doivent être :

- minimales ;
- chiffrées ;
- temporaires ;
- protégées par le système ;
- supprimables à distance ;
- non exportables ;
- séparées par profil.

---

# 80. Effacement à distance

L’administration doit pouvoir :

- suspendre ;
- révoquer ;
- verrouiller ;
- effacer les données sensibles ;
- désactiver les certificats ;
- empêcher la connexion ;
- mettre en quarantaine.

---

# 81. Terminal perdu ou volé

Le processus doit :

- signaler ;
- suspendre ;
- révoquer ;
- géolocaliser si autorisé ;
- effacer ;
- protéger les clés ;
- créer un incident ;
- remplacer ;
- auditer.

---

# 82. Fraude

Les risques comprennent :

- terminal volé ;
- faux commerçant ;
- saisie manuelle abusive ;
- remboursement frauduleux ;
- double paiement ;
- contournement hors ligne ;
- manipulation logicielle ;
- carte volée ;
- collusion ;
- faux reçu ;
- fausse annulation ;
- modification de montant.

---

# 83. Règles antifraude

Les règles peuvent analyser :

- montant ;
- fréquence ;
- commerçant ;
- employé ;
- terminal ;
- carte ;
- pays ;
- localisation ;
- heure ;
- réseau ;
- remboursement ;
- annulation ;
- hors ligne ;
- vitesse.

---

# 84. Action antifraude

Le système peut :

- refuser ;
- demander un PIN ;
- demander une confirmation ;
- suspendre le terminal ;
- bloquer un employé ;
- retarder le règlement ;
- ouvrir un dossier ;
- alerter le commerçant ;
- alerter Mansa.

---

# 85. Géolocalisation

La géolocalisation peut être utilisée pour :

- vérifier le point de vente ;
- détecter un terminal déplacé ;
- sécuriser une opération ;
- assister la maintenance ;
- lutter contre la fraude.

Elle doit respecter les règles de confidentialité.

---

# 86. Restriction géographique

Un terminal peut être limité à :

- un pays ;
- une ville ;
- un magasin ;
- une zone ;
- une adresse ;
- un événement ;
- une période.

---

# 87. Gestion des périphériques

L’application doit gérer :

- lecteur carte ;
- lecteur sans contact ;
- clavier PIN ;
- imprimante ;
- caméra ;
- scanner ;
- batterie ;
- modem ;
- SIM ;
- haut-parleur ;
- écran ;
- caisse.

---

# 88. État des périphériques

Chaque périphérique doit avoir un état :

- AVAILABLE ;
- BUSY ;
- DEGRADED ;
- ERROR ;
- DISCONNECTED ;
- COMPROMISED ;
- MAINTENANCE.

---

# 89. Tests périphériques

Le menu diagnostic doit permettre :

- test imprimante ;
- test carte ;
- test NFC ;
- test caméra ;
- test scanner ;
- test réseau ;
- test batterie ;
- test écran ;
- test clavier ;
- test audio.

---

# 90. Batterie

L’application doit suivre :

- niveau ;
- charge ;
- température ;
- état ;
- autonomie estimée ;
- usure ;
- alerte ;
- économie d’énergie.

---

# 91. Imprimante sans papier

Lorsque le papier manque :

- avertir avant paiement ;
- proposer reçu numérique ;
- autoriser ou bloquer selon la règle ;
- alerter le responsable ;
- journaliser.

---

# 92. Mise à jour de l’application

Les mises à jour doivent être :

- signées ;
- testées ;
- ciblées ;
- progressives ;
- planifiées ;
- réversibles ;
- surveillées ;
- interrompues si le terminal est en transaction.

---

# 93. Types de mise à jour

- application ;
- configuration ;
- firmware ;
- certificats ;
- clés ;
- traductions ;
- règles ;
- catalogue ;
- design ;
- paramètres réseau.

---

# 94. Mise à jour obligatoire

L’administration peut imposer une version selon :

- date ;
- pays ;
- modèle ;
- commerçant ;
- risque ;
- conformité ;
- partenaire.

---

# 95. Mise à jour progressive

Déploiement possible :

```text
Terminals internes
→ 1 %
→ 5 %
→ 20 %
→ 50 %
→ 100 %
```

Chaque phase doit être surveillée.

---

# 96. Rollback

Le terminal doit pouvoir revenir à :

- version précédente ;
- configuration précédente ;
- certificat valide ;
- firmware précédent lorsque possible ;
- Golden Image.

---

# 97. Golden Image

La Golden Image peut contenir :

- système durci ;
- pilotes ;
- application ;
- certificats initiaux ;
- monitoring ;
- outils ;
- configuration de base ;
- paramètres de sécurité.

---

# 98. Supervision temps réel

L’administration doit voir :

- terminal ;
- statut ;
- commerçant ;
- localisation ;
- version ;
- réseau ;
- batterie ;
- imprimante ;
- dernière transaction ;
- dernière synchronisation ;
- erreurs ;
- périphériques ;
- sécurité ;
- maintenance.

---

# 99. Alertes

Exemples :

- terminal hors ligne ;
- batterie faible ;
- imprimante vide ;
- application ancienne ;
- certificat expirant ;
- root détecté ;
- déplacement inhabituel ;
- trop de refus ;
- remboursement anormal ;
- volume inhabituel ;
- synchronisation bloquée ;
- périphérique défaillant.

---

# 100. Niveaux d’alerte

- INFO ;
- WARNING ;
- MAJOR ;
- CRITICAL ;
- SECURITY ;
- FINANCIAL.

---

# 101. Télémetrie

Le terminal peut envoyer :

- CPU ;
- mémoire ;
- stockage ;
- température ;
- batterie ;
- réseau ;
- signal ;
- uptime ;
- crash ;
- version ;
- périphériques ;
- latence.

Aucune donnée carte sensible ne doit être incluse.

---

# 102. Maintenance

La maintenance peut être :

- préventive ;
- corrective ;
- distante ;
- sur site ;
- logicielle ;
- matérielle ;
- de sécurité.

---

# 103. Ticket de maintenance

Il doit contenir :

- terminal ;
- commerçant ;
- erreur ;
- périphérique ;
- priorité ;
- technicien ;
- date ;
- diagnostic ;
- pièce ;
- action ;
- résultat ;
- preuve.

---

# 104. Accès technicien

L’accès doit être :

- temporaire ;
- limité ;
- lié à un ordre de mission ;
- authentifié ;
- journalisé ;
- révocable ;
- sans accès aux secrets.

---

# 105. Mode maintenance

En mode maintenance :

- les paiements sont bloqués ;
- l’état est visible ;
- les diagnostics sont disponibles ;
- les actions sont tracées ;
- les données financières restent protégées ;
- la sortie exige une validation.

---

# 106. Test après maintenance

Avant réactivation :

- démarrage ;
- intégrité ;
- réseau ;
- carte ;
- NFC ;
- clavier ;
- imprimante ;
- caméra ;
- synchronisation ;
- transaction de test ;
- reçu.

---

# 107. Support

Le terminal doit proposer :

- FAQ ;
- diagnostic ;
- ticket ;
- appel ;
- chat ;
- assistance Jini ;
- contact commerçant ;
- statut du service ;
- partage de référence.

---

# 108. Ticket lié à une transaction

Le terminal doit préremplir :

- référence ;
- montant ;
- date ;
- heure ;
- statut ;
- terminal ;
- caisse ;
- employé ;
- moyen ;
- erreur.

---

# 109. Jini sur TPE

Jini peut :

- expliquer une erreur ;
- guider un paiement ;
- aider à retrouver une transaction ;
- expliquer une clôture ;
- aider à diagnostiquer l’imprimante ;
- préparer un ticket ;
- rappeler les procédures ;
- guider un remboursement.

---

# 110. Limites de Jini

Jini ne doit pas :

- effectuer seul un remboursement ;
- modifier les frais ;
- contourner une permission ;
- afficher un PIN ;
- afficher des données carte ;
- activer un terminal compromis ;
- supprimer une transaction ;
- valider une clôture à la place du commerçant.

---

# 111. Langues

Le terminal peut supporter :

- français ;
- bambara ;
- anglais ;
- arabe ;
- autres langues activées.

Les traductions doivent être administrables.

---

# 112. Accessibilité

L’interface doit prévoir :

- gros boutons ;
- contraste ;
- texte lisible ;
- retour sonore ;
- vibration ;
- navigation simple ;
- messages clairs ;
- réduction des étapes ;
- lecture audio éventuelle.

---

# 113. Mode restaurant

Le mode restaurant peut gérer :

- tables ;
- serveurs ;
- commandes ;
- addition ;
- séparation ;
- pourboire ;
- préautorisation ;
- impression cuisine éventuelle ;
- clôture.

---

# 114. Division d’addition

Le serveur peut diviser :

- à parts égales ;
- par article ;
- par personne ;
- par montant ;
- par pourcentage ;
- entre plusieurs moyens.

---

# 115. Mode hôtel

Le mode hôtel peut gérer :

- préautorisation ;
- caution ;
- chambre ;
- client ;
- consommation ;
- augmentation ;
- finalisation ;
- libération de caution ;
- reçu.

---

# 116. Mode station-service

Le mode station-service peut gérer :

- pompe ;
- montant ;
- préautorisation ;
- litre ;
- carburant ;
- caissier ;
- clôture ;
- flotte entreprise ;
- carte carburant.

---

# 117. Mode livraison

Le terminal mobile peut gérer :

- commande ;
- livreur ;
- client ;
- localisation ;
- paiement ;
- reçu ;
- retour ;
- remboursement ;
- preuve de livraison.

---

# 118. Mode transport

Le TPE peut être adapté à :

- bus ;
- taxi ;
- autocar ;
- train ;
- péage ;
- parking.

Il peut gérer :

- ticket ;
- trajet ;
- tarif ;
- QR ;
- NFC ;
- abonnement ;
- mode réseau faible.

---

# 119. Mode institutionnel

Il peut servir à :

- amendes ;
- taxes ;
- frais administratifs ;
- inscriptions ;
- services publics ;
- paiements scolaires ;
- justificatifs ;
- reçus officiels.

---

# 120. Intégration avec une caisse

Le TPE peut recevoir depuis une caisse :

- montant ;
- devise ;
- facture ;
- panier ;
- référence ;
- TVA ;
- employé ;
- caisse.

---

# 121. Protocole caisse-TPE

L’intégration doit gérer :

- authentification ;
- signature ;
- timeout ;
- statut ;
- annulation ;
- retry ;
- idempotence ;
- reçus ;
- rapprochement.

---

# 122. Catalogue

Le catalogue peut être synchronisé depuis :

- Application Commerce ;
- Portail Web Commerce ;
- API ;
- ERP ;
- fichier ;
- caisse.

---

# 123. Stock léger

Le terminal peut afficher :

- stock disponible ;
- rupture ;
- seuil ;
- variation ;
- synchronisation.

La gestion complète peut rester dans l’Application Commerce.

---

# 124. Remises

Les remises peuvent être :

- pourcentage ;
- montant fixe ;
- article ;
- panier ;
- client ;
- campagne ;
- code ;
- employé autorisé.

---

# 125. Taxes

Le terminal peut calculer :

- TVA ;
- taxe locale ;
- taxe service ;
- taxe spécifique ;
- exonération ;
- prix TTC ;
- prix HT.

Les règles doivent être configurables.

---

# 126. Fidélité

Le terminal peut :

- identifier un client ;
- attribuer des points ;
- utiliser des points ;
- appliquer une remise ;
- afficher le solde ;
- imprimer un avantage ;
- proposer une promotion.

---

# 127. Identification client

Le client peut être reconnu par :

- QR ;
- téléphone ;
- carte ;
- identifiant ;
- NFC ;
- code fidélité ;
- application Mansa.

---

# 128. Coupons

Le terminal peut accepter :

- QR coupon ;
- code ;
- coupon numérique ;
- offre automatique ;
- promotion liée au client ;
- coupon partenaire.

---

# 129. Administration centrale

L’administration doit pouvoir gérer :

- terminaux ;
- modèles ;
- fabricants ;
- commerçants ;
- points de vente ;
- caisses ;
- employés ;
- rôles ;
- permissions ;
- paiements ;
- remboursements ;
- annulations ;
- frais ;
- commissions ;
- devises ;
- moyens de paiement ;
- mode hors ligne ;
- versions ;
- certificats ;
- clés ;
- périphériques ;
- alertes ;
- maintenance ;
- support ;
- rapports ;
- audits.

---

# 130. Configuration du terminal

Elle doit inclure :

- langue ;
- devise ;
- navigation ;
- actions rapides ;
- moyens acceptés ;
- limites ;
- remboursement ;
- pourboire ;
- reçu ;
- hors ligne ;
- réseau ;
- imprimante ;
- catalogue ;
- fidélité ;
- accessibilité.

---

# 131. Feature Flags

Exemples :

- paiement carte ;
- NFC ;
- QR ;
- Mobile Money ;
- remboursement ;
- préautorisation ;
- split ;
- pourboire ;
- catalogue ;
- fidélité ;
- hors ligne ;
- SoftPOS ;
- Jini.

---

# 132. Frais

Les frais peuvent dépendre :

- moyen ;
- réseau ;
- montant ;
- commerçant ;
- pays ;
- catégorie ;
- abonnement ;
- devise ;
- transaction ;
- partenaire ;
- campagne.

---

# 133. Commission

La commission peut être répartie entre :

- Mansa ;
- commerçant ;
- banque ;
- acquéreur ;
- processeur ;
- réseau ;
- partenaire ;
- distributeur du terminal.

---

# 134. Affichage des frais au commerçant

Le commerçant doit pouvoir consulter :

- taux ;
- montant ;
- frais fixes ;
- frais variables ;
- frais réseau ;
- commission ;
- net attendu ;
- date de règlement.

---

# 135. Multi-devises

Le terminal peut accepter plusieurs devises selon :

- pays ;
- commerçant ;
- banque ;
- réseau ;
- règlement ;
- contrat ;
- appareil.

---

# 136. Conversion

Le terminal doit afficher :

- devise ;
- taux ;
- frais ;
- montant d’origine ;
- montant converti ;
- total ;
- fournisseur du taux ;
- date.

---

# 137. DCC

La conversion dynamique de devise doit être :

- optionnelle ;
- transparente ;
- expliquée ;
- confirmée ;
- conforme ;
- auditée.

---

# 138. API principales

Exemples :

```http
POST   /terminals/enroll
POST   /terminals/activate
GET    /terminals/{id}
PATCH  /terminals/{id}
POST   /terminals/{id}/suspend
POST   /terminals/{id}/quarantine

POST   /tpe/payments
POST   /tpe/payments/qr
POST   /tpe/payments/mobile-money
POST   /tpe/preauthorizations
POST   /tpe/preauthorizations/{id}/capture

POST   /tpe/transactions/{id}/cancel
POST   /tpe/transactions/{id}/refund
GET    /tpe/transactions
GET    /tpe/transactions/{id}

POST   /tpe/sessions/open
POST   /tpe/sessions/close
GET    /tpe/settlements

POST   /tpe/offline/synchronize
GET    /tpe/configuration
GET    /tpe/catalog
GET    /tpe/telemetry
POST   /tpe/support/tickets
```

---

# 139. Webhooks internes

Événements possibles :

```text
terminal.enrolled
terminal.activated
terminal.suspended
terminal.offline
terminal.compromised
terminal.configuration.updated
terminal.software.updated

tpe.payment.started
tpe.payment.authorized
tpe.payment.completed
tpe.payment.failed
tpe.payment.reversed
tpe.payment.offline_recorded

tpe.refund.started
tpe.refund.completed
tpe.refund.failed

tpe.session.opened
tpe.session.closed
tpe.settlement.created
tpe.synchronization.failed
tpe.security.alert.created
```

---

# 140. Modèles principaux

- PaymentTerminal
- TerminalModel
- TerminalCapability
- TerminalConfiguration
- TerminalEnrollment
- TerminalCertificate
- TerminalKey
- TerminalPeripheral
- TerminalEmployeeSession
- TPEPayment
- TPECardPayment
- TPEQRPayment
- TPEMobileMoneyPayment
- TPEPreauthorization
- TPERefund
- TPECancellation
- TPEOfflineTransaction
- TPESynchronizationBatch
- TPEReceipt
- TPECashierSession
- TPESettlement
- TPETelemetry
- TPEAlert
- TPEMaintenanceTicket
- TPEAudit

---

# 141. Rôles

Exemples :

```text
TPE_NETWORK_ADMIN
TPE_OPERATIONS_MANAGER
TPE_SECURITY_MANAGER
TPE_SOFTWARE_MANAGER
TPE_MAINTENANCE_MANAGER
TPE_SUPPORT_OPERATOR
TPE_RECONCILIATION_OPERATOR
TPE_FRAUD_ANALYST
MERCHANT_OWNER
MERCHANT_MANAGER
MERCHANT_CASHIER
FINANCE_APPROVER
SECURITY_APPROVER
AUDITOR
VIEWER
```

---

# 142. Permissions

Exemples :

```text
terminal.read
terminal.create
terminal.enroll
terminal.activate
terminal.suspend
terminal.quarantine

tpe.payment.create
tpe.payment.read
tpe.payment.cancel
tpe.refund.create
tpe.refund.approve
tpe.preauthorization.manage

tpe.session.open
tpe.session.close
tpe.settlement.read
tpe.offline.manage

tpe.configuration.manage
tpe.software.deploy
tpe.certificate.rotate
tpe.security.alert.manage
tpe.maintenance.manage
tpe.audit.read
```

---

# 143. Approbations

Peuvent nécessiter une approbation :

- activation du terminal ;
- remboursement élevé ;
- remboursement sans transaction ;
- activation hors ligne ;
- augmentation de limite ;
- mise à jour globale ;
- rotation de certificat ;
- saisie manuelle carte ;
- déblocage après compromission ;
- décommissionnement.

---

# 144. Double validation

Doit être exigée pour :

- remboursement exceptionnel ;
- modification nationale des frais ;
- activation massive du hors ligne ;
- injection de clés ;
- correction financière ;
- déploiement logiciel global ;
- réactivation d’un terminal compromis ;
- effacement d’un journal ;
- changement HSM ;
- suppression d’une preuve.

---

# 145. Reporting

Rapports possibles :

- ventes ;
- transactions ;
- remboursements ;
- annulations ;
- moyens de paiement ;
- terminaux actifs ;
- terminaux hors ligne ;
- commerçants ;
- points de vente ;
- caisses ;
- employés ;
- règlements ;
- frais ;
- commissions ;
- hors ligne ;
- erreurs ;
- fraude ;
- maintenance.

---

# 146. Indicateurs

Exemples :

- volume ;
- valeur ;
- taux de succès ;
- panier moyen ;
- temps moyen de paiement ;
- taux de refus ;
- taux de remboursement ;
- taux d’annulation ;
- disponibilité terminal ;
- taux de synchronisation ;
- usage NFC ;
- usage QR ;
- usage Mobile Money ;
- coût par transaction ;
- revenu par terminal.

---

# 147. Tests fonctionnels

- enrôlement ;
- connexion ;
- ouverture de caisse ;
- paiement carte ;
- paiement NFC ;
- paiement QR ;
- Mobile Money ;
- lien ;
- pourboire ;
- split ;
- préautorisation ;
- annulation ;
- remboursement ;
- reçu ;
- clôture ;
- règlement.

---

# 148. Tests carte

- puce ;
- sans contact ;
- bande ;
- PIN ;
- carte expirée ;
- carte bloquée ;
- carte étrangère ;
- réseau indisponible ;
- timeout ;
- reversal ;
- double présentation.

---

# 149. Tests QR et Mobile Money

- QR statique ;
- QR dynamique ;
- expiration ;
- montant erroné ;
- double scan ;
- opérateur indisponible ;
- timeout ;
- validation tardive ;
- annulation ;
- réconciliation.

---

# 150. Tests hors ligne

- activation ;
- limite ;
- queue ;
- redémarrage ;
- absence réseau ;
- synchronisation ;
- doublon ;
- refus après synchronisation ;
- stockage chiffré ;
- expiration ;
- compteur.

---

# 151. Tests périphériques

- lecteur ;
- NFC ;
- clavier ;
- imprimante ;
- caméra ;
- scanner ;
- batterie ;
- réseau ;
- SIM ;
- écran ;
- caisse.

---

# 152. Tests de sécurité

- root ;
- modification application ;
- certificat ;
- clé ;
- terminal volé ;
- accès technicien ;
- mode kiosque ;
- ports ;
- stockage ;
- capture ;
- logs ;
- saisie manuelle ;
- injection de clés ;
- effacement à distance.

---

# 153. Tests de résilience

- coupure réseau ;
- changement de SIM ;
- panne batterie ;
- redémarrage ;
- crash ;
- imprimante en panne ;
- périphérique déconnecté ;
- backend indisponible ;
- HSM indisponible ;
- partenaire indisponible ;
- reprise.

---

# 154. Tests de performance

- temps de démarrage ;
- temps d’autorisation ;
- temps d’impression ;
- temps de synchronisation ;
- liste de transactions ;
- catalogue ;
- mémoire ;
- batterie ;
- télémetrie ;
- volume journalier.

---

# 155. Règles métier

1. Chaque terminal possède un identifiant unique.
2. Chaque terminal est affecté à un commerçant.
3. Chaque paiement possède une référence unique.
4. Toute transaction financière passe par le ledger.
5. Aucun double paiement n’est autorisé.
6. Les données carte sensibles ne sont jamais stockées en clair.
7. Les frais sont affichés avant confirmation lorsque nécessaire.
8. Toute annulation dépend du statut de la transaction.
9. Tout remboursement est lié à une transaction, sauf exception approuvée.
10. Le mode hors ligne est limité.
11. Les transactions hors ligne sont chiffrées.
12. La synchronisation conserve l’ordre.
13. Un timeout n’est pas considéré immédiatement comme un échec définitif.
14. Les reversals sont gérés.
15. Les reçus sont liés à une transaction.
16. Les réimpressions sont marquées DUPLICATA.
17. Les employés disposent de permissions limitées.
18. Les terminaux compromis sont mis en quarantaine.
19. Les mises à jour sont signées.
20. Les certificats sont uniques.
21. Les clés ne sont jamais exposées en clair.
22. Les accès techniciens sont temporaires.
23. Les statistiques utilisent les données financières validées.
24. Les corrections financières sont auditées.
25. Les audits sont immuables.

---

# 156. Critères d’acceptation

L’Application TPE Mansa est validée lorsque :

- plusieurs modèles de terminaux sont supportables ;
- l’enrôlement fonctionne ;
- les certificats sont installés ;
- les employés peuvent se connecter ;
- les caisses peuvent être ouvertes ;
- l’accueil est configurable ;
- le montant peut être saisi ;
- le catalogue peut être utilisé ;
- les paiements par puce fonctionnent ;
- les paiements sans contact fonctionnent ;
- les limites sans contact sont appliquées ;
- la bande magnétique est contrôlée ;
- la saisie manuelle est restreinte ;
- le QR statique fonctionne ;
- le QR dynamique fonctionne ;
- Mobile Money est intégré ;
- le paiement Mansa fonctionne ;
- Tap to Pay est supportable ;
- le paiement par lien fonctionne ;
- les paiements à distance sont encadrés ;
- les pourboires sont configurables ;
- le split payment fonctionne ;
- les paiements partiels sont supportables ;
- les préautorisations fonctionnent ;
- les préautorisations peuvent être finalisées ;
- les annulations sont contrôlées ;
- les remboursements totaux fonctionnent ;
- les remboursements partiels fonctionnent ;
- les remboursements exceptionnels sont protégés ;
- les refus sont compréhensibles ;
- les timeouts sont vérifiés ;
- les reversals sont générés ;
- les reçus papier fonctionnent ;
- les reçus numériques fonctionnent ;
- la réimpression est contrôlée ;
- l’historique est disponible ;
- la recherche fonctionne ;
- les caisses peuvent être fermées ;
- la clôture journalière est disponible ;
- les règlements sont consultables ;
- le mode hors ligne est configurable ;
- les limites hors ligne sont appliquées ;
- la queue locale est chiffrée ;
- la synchronisation fonctionne ;
- les refus après synchronisation sont gérés ;
- le réseau faible est pris en charge ;
- la bascule réseau fonctionne ;
- le mode kiosque est actif ;
- le démarrage sécurisé fonctionne ;
- root et compromission sont détectés ;
- l’attestation fonctionne ;
- les certificats sont uniques ;
- les clés sont protégées ;
- le PIN est chiffré ;
- les exigences PCI applicables sont intégrées ;
- les données locales sont minimisées ;
- l’effacement à distance fonctionne ;
- les terminaux perdus peuvent être bloqués ;
- les règles antifraude fonctionnent ;
- la géolocalisation peut être contrôlée ;
- les périphériques sont supervisés ;
- les diagnostics sont disponibles ;
- la batterie est suivie ;
- l’imprimante est suivie ;
- les mises à jour sont signées ;
- le déploiement progressif est supporté ;
- le rollback est possible ;
- une Golden Image existe ;
- la supervision temps réel fonctionne ;
- les alertes sont configurables ;
- la télémetrie remonte ;
- la maintenance est gérée ;
- les accès techniciens sont temporaires ;
- les tests après maintenance sont obligatoires ;
- le support est accessible ;
- Jini est intégré sans contourner les droits ;
- les langues sont configurables ;
- l’accessibilité est prise en charge ;
- le mode restaurant est supportable ;
- le mode hôtel est supportable ;
- le mode station-service est supportable ;
- le mode livraison est supportable ;
- le mode transport est supportable ;
- le mode institutionnel est supportable ;
- l’intégration caisse-TPE est sécurisée ;
- le catalogue est synchronisable ;
- les remises sont gérées ;
- les taxes sont configurables ;
- la fidélité est intégrable ;
- les coupons sont supportables ;
- l’administration centrale est complète ;
- les feature flags sont disponibles ;
- les frais sont configurables ;
- les commissions sont configurables ;
- le multi-devises est supportable ;
- les API sont définies ;
- les webhooks sont définis ;
- les rôles et permissions sont définis ;
- les approbations critiques sont protégées ;
- les rapports sont disponibles ;
- les indicateurs sont calculés ;
- les tests couvrent les parcours fonctionnels, carte, QR, Mobile Money, hors ligne, périphériques, sécurité, résilience et performance ;
- les audits sont immuables.
