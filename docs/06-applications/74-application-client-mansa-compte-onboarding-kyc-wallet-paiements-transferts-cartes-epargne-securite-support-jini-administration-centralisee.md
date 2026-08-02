# 74 — Application Client Mansa : compte, onboarding, KYC, wallet, paiements, transferts, cartes, épargne, sécurité, support, Jini et administration centralisée

## 1. Objet du document

Ce document définit le cahier des charges complet de l’**Application Client Mansa**.

L’application Client constitue l’interface principale utilisée par les particuliers pour accéder aux services financiers Mansa.

Elle doit permettre notamment :

- la création d’un compte ;
- la connexion ;
- la vérification d’identité ;
- la gestion du wallet ;
- la consultation du solde ;
- la consultation de l’historique ;
- les transferts ;
- les paiements ;
- les dépôts ;
- les retraits ;
- le paiement par QR Code ;
- le paiement NFC ;
- la gestion des cartes ;
- la gestion des bénéficiaires ;
- la gestion des factures ;
- les paiements récurrents ;
- les coffres d’épargne ;
- les budgets ;
- le partage des dépenses ;
- les abonnements ;
- la fidélité ;
- le cashback ;
- la consultation des GAB, DAB, Agents et commerçants proches ;
- la gestion des notifications ;
- l’assistance ;
- l’utilisation de Jini ;
- la gestion du profil ;
- la gestion des appareils ;
- la sécurité du compte ;
- la confidentialité ;
- l’accessibilité ;
- le fonctionnement avec un réseau faible ;
- l’administration centralisée des fonctionnalités.

L’application doit être conçue comme une interface :

- moderne ;
- simple ;
- rapide ;
- sécurisée ;
- modifiable depuis l’administration ;
- multi-pays ;
- multi-langues ;
- multi-devises ;
- compatible Android et iOS ;
- adaptée aux appareils modestes ;
- adaptée aux réseaux faibles ;
- accessible aux utilisateurs peu familiarisés avec les services bancaires.

---

# 2. Principes fondamentaux

## 2.1 L’argent de l’utilisateur doit toujours rester compréhensible

L’utilisateur doit pouvoir comprendre à tout moment :

- combien il possède ;
- combien est disponible ;
- combien est réservé ;
- quelles opérations ont été effectuées ;
- quels frais ont été appliqués ;
- pourquoi une opération est en attente ;
- pourquoi une opération a échoué ;
- comment signaler un problème.

## 2.2 Aucun frais ne doit être caché

Avant chaque opération payante, l’application doit afficher :

- le montant envoyé ;
- le montant reçu ;
- les frais ;
- le taux de conversion éventuel ;
- le montant total débité ;
- le bénéficiaire ;
- la date prévue ;
- le délai éventuel.

## 2.3 Les fonctions doivent être configurables

L’administration doit pouvoir :

- activer ou désactiver une fonction ;
- modifier les plafonds ;
- modifier les frais ;
- modifier les textes ;
- modifier les images ;
- modifier l’ordre des modules ;
- activer une fonction par pays ;
- activer une fonction par segment ;
- activer une fonction par version ;
- activer une fonction par niveau KYC ;
- programmer une date d’activation.

## 2.4 Une action critique doit toujours être confirmée

Doivent notamment être confirmés :

- transfert ;
- paiement ;
- retrait ;
- dépôt tiers ;
- ajout de bénéficiaire ;
- changement de numéro ;
- changement de PIN ;
- création de carte ;
- changement de limite ;
- fermeture de compte ;
- suppression d’un appareil ;
- activation d’un paiement récurrent.

## 2.5 Le client doit pouvoir comprendre un échec

Les messages doivent éviter les codes techniques seuls.

Exemple :

```text
Le paiement n’a pas été effectué.
Aucun montant n’a été débité.
Réessaie dans quelques instants.
```

Lorsque nécessaire, afficher également :

- référence ;
- date ;
- montant ;
- bouton Réessayer ;
- bouton Signaler un problème ;
- bouton Contacter le support.

---

# 3. Plateformes

L’application doit être disponible sur :

- Android ;
- iOS.

Une version web légère peut éventuellement être prévue pour certains usages, mais elle ne doit pas remplacer l’application mobile principale.

---

# 4. Architecture de l’application

Structure recommandée :

```text
client-mobile/
├── onboarding/
├── authentication/
├── kyc/
├── home/
├── wallet/
├── transactions/
├── transfers/
├── payments/
├── qr/
├── cash/
├── cards/
├── beneficiaries/
├── bills/
├── subscriptions/
├── savings/
├── budgets/
├── loyalty/
├── nearby/
├── notifications/
├── support/
├── jini/
├── profile/
├── security/
├── settings/
├── offline/
├── analytics/
└── shared/
```

---

# 5. Navigation principale

Navigation recommandée :

1. Accueil.
2. Payer.
3. Transférer.
4. Cartes.
5. Plus.

Une navigation alternative peut être configurée par l’administration.

---

# 6. Onglet Accueil

L’accueil peut afficher :

- salutation ;
- nom du client ;
- photo ou avatar ;
- solde ;
- bouton masquer le solde ;
- devise ;
- actions rapides ;
- dernières transactions ;
- raccourcis ;
- cartes ;
- coffres ;
- alertes ;
- promotions ;
- état KYC ;
- messages importants ;
- accès Jini ;
- accès support.

---

# 7. Actions rapides

Exemples :

- Envoyer ;
- Recevoir ;
- Payer ;
- Déposer ;
- Retirer ;
- Scanner ;
- Recharger ;
- Factures ;
- Ajouter de l’argent ;
- Carte virtuelle.

L’ordre doit être modifiable depuis l’administration.

---

# 8. Splash Screen

Le Splash Screen peut contenir :

- logo Mansa ;
- animation légère ;
- couleur de marque ;
- vérification de version ;
- vérification de session ;
- vérification de sécurité ;
- chargement de configuration ;
- choix du parcours suivant.

---

# 9. Écran de maintenance

Lorsque le service est indisponible, l’application doit afficher :

- message ;
- services affectés ;
- heure estimée de retour ;
- fonctions encore disponibles ;
- bouton Actualiser ;
- bouton Contacter le support.

---

# 10. Mise à jour obligatoire

L’application doit pouvoir afficher :

- version actuelle ;
- version minimale ;
- raison ;
- bouton Mettre à jour ;
- lien vers le store ;
- assistance ;
- possibilité limitée d’accès si autorisée.

---

# 11. Onboarding

L’onboarding peut présenter :

- envoyer de l’argent ;
- payer ;
- utiliser une carte ;
- déposer et retirer ;
- épargner ;
- gérer son budget ;
- utiliser Jini ;
- bénéficier de la sécurité Mansa.

---

# 12. Onboarding administrable

L’administration doit pouvoir modifier :

- images ;
- vidéos ;
- titres ;
- textes ;
- nombre d’écrans ;
- ordre ;
- pays ;
- langue ;
- boutons ;
- liens ;
- date de publication.

---

# 13. Choix du pays

Lors de l’inscription, l’utilisateur doit sélectionner ou confirmer :

- pays ;
- indicatif téléphonique ;
- devise principale ;
- langue ;
- réglementation applicable ;
- services disponibles.

---

# 14. Choix de la langue

Langues initiales possibles :

- français ;
- bambara ;
- anglais ;
- arabe.

D’autres langues doivent pouvoir être ajoutées.

---

# 15. Création de compte

Le parcours doit pouvoir utiliser :

- numéro de téléphone ;
- e-mail éventuel ;
- nom ;
- prénom ;
- date de naissance ;
- pays ;
- consentements ;
- code OTP ;
- PIN ou mot de passe ;
- appareil.

---

# 16. Vérification du numéro

Le numéro peut être vérifié par :

- SMS OTP ;
- appel vocal ;
- notification opérateur ;
- autre mécanisme autorisé.

---

# 17. OTP

L’OTP doit posséder :

- durée limitée ;
- nombre d’essais limité ;
- possibilité de renvoi contrôlée ;
- liaison avec l’opération ;
- protection contre les abus ;
- masquage dans les journaux.

---

# 18. Détection d’un compte existant

Si le numéro existe déjà, proposer :

- connexion ;
- récupération du compte ;
- changement de numéro ;
- contact support.

---

# 19. Conditions générales

L’utilisateur doit pouvoir :

- consulter les conditions ;
- consulter la politique de confidentialité ;
- accepter ;
- refuser ;
- télécharger ou recevoir une copie ;
- consulter la version acceptée.

---

# 20. Consentements

Les consentements doivent être séparés lorsque nécessaire :

- conditions générales ;
- données personnelles ;
- marketing ;
- géolocalisation ;
- biométrie ;
- partage partenaire ;
- analyse personnalisée ;
- notifications commerciales.

---

# 21. Création du PIN

Le PIN doit respecter une politique configurable :

- longueur ;
- chiffres interdits ;
- séquences interdites ;
- nombre d’essais ;
- expiration éventuelle ;
- blocage ;
- récupération.

---

# 22. Mot de passe

Lorsque le mot de passe est utilisé, il doit pouvoir imposer :

- longueur minimale ;
- caractères ;
- détection des mots de passe compromis ;
- historique ;
- nombre d’essais ;
- verrouillage temporaire.

---

# 23. Biométrie

L’utilisateur peut activer :

- Face ID ;
- Touch ID ;
- empreinte Android ;
- autre mécanisme natif sécurisé.

La biométrie ne remplace pas la possibilité de récupérer le compte.

---

# 24. Connexion

La connexion peut utiliser :

- numéro et PIN ;
- e-mail et mot de passe ;
- biométrie ;
- passkey ;
- appareil approuvé ;
- authentification renforcée.

---

# 25. Appareil reconnu

L’application doit identifier :

- appareil principal ;
- appareil secondaire ;
- nouvel appareil ;
- appareil bloqué ;
- appareil compromis ;
- dernière connexion ;
- version ;
- système.

---

# 26. Connexion sur un nouvel appareil

Le parcours peut exiger :

- numéro ;
- OTP ;
- PIN ;
- biométrie ;
- vérification KYC ;
- délai de sécurité ;
- notification sur l’ancien appareil ;
- confirmation support en cas de risque.

---

# 27. Déconnexion

L’utilisateur doit pouvoir :

- se déconnecter ;
- déconnecter tous les appareils ;
- supprimer un appareil ;
- révoquer une session ;
- voir les sessions actives.

---

# 28. Récupération du compte

La récupération peut utiliser :

- téléphone ;
- e-mail ;
- document d’identité ;
- selfie ;
- questions sécurisées ;
- ancien appareil ;
- assistance ;
- délai de sécurité.

---

# 29. Compte compromis

L’utilisateur doit pouvoir :

- bloquer son compte ;
- bloquer ses cartes ;
- déconnecter les appareils ;
- signaler un vol ;
- contacter le support ;
- suivre le dossier.

---

# 30. KYC

Le parcours KYC doit être configurable par pays et niveau de compte.

Il peut demander :

- identité ;
- date de naissance ;
- sexe si requis ;
- nationalité ;
- adresse ;
- profession ;
- source de revenus ;
- pièce d’identité ;
- photo ;
- selfie ;
- preuve de résidence ;
- déclaration ;
- vérification biométrique.

---

# 31. Niveaux KYC

Exemple :

- KYC_LEVEL_0 ;
- KYC_LEVEL_1 ;
- KYC_LEVEL_2 ;
- KYC_LEVEL_3.

Chaque niveau peut définir :

- limites ;
- services ;
- documents ;
- durée ;
- pays ;
- risques ;
- contrôles.

---

# 32. KYC progressif

L’utilisateur peut commencer avec un accès limité puis compléter progressivement son profil.

```text
Compte créé
→ services limités
→ pièce vérifiée
→ limites augmentées
→ justificatifs supplémentaires
→ accès complet
```

---

# 33. Capture de document

La capture doit aider l’utilisateur à :

- cadrer le document ;
- éviter les reflets ;
- vérifier la netteté ;
- prendre le recto ;
- prendre le verso ;
- recommencer ;
- confirmer.

---

# 34. Contrôle du document

Le système peut vérifier :

- type ;
- pays ;
- numéro ;
- date de naissance ;
- expiration ;
- authenticité ;
- cohérence ;
- photo ;
- nom ;
- fraude éventuelle.

---

# 35. Selfie

Le parcours selfie peut vérifier :

- présence réelle ;
- clignement ;
- mouvement ;
- correspondance avec le document ;
- absence de capture d’écran ;
- qualité.

---

# 36. Statuts KYC

- NOT_STARTED ;
- IN_PROGRESS ;
- SUBMITTED ;
- AUTOMATIC_REVIEW ;
- MANUAL_REVIEW ;
- ADDITIONAL_INFORMATION_REQUIRED ;
- APPROVED ;
- REJECTED ;
- EXPIRED ;
- SUSPENDED.

---

# 37. KYC en attente

L’écran doit afficher :

- statut ;
- date de soumission ;
- délai estimé ;
- documents reçus ;
- éventuelle action requise ;
- bouton support.

---

# 38. KYC rejeté

Le refus doit afficher, lorsque autorisé :

- motif compréhensible ;
- document concerné ;
- possibilité de recommencer ;
- possibilité de recours ;
- contact support.

---

# 39. KYC expirant

L’utilisateur doit recevoir des rappels avant expiration.

L’administration doit configurer :

- délai ;
- fréquence ;
- services limités ;
- date de blocage ;
- documents requis.

---

# 40. Création du wallet

Après validation requise, le système crée :

- wallet principal ;
- compte ledger associé ;
- devise ;
- limites ;
- statut ;
- identifiant ;
- éventuel alias.

---

# 41. Wallets multiples

L’utilisateur peut éventuellement posséder :

- wallet FCFA ;
- wallet EUR ;
- wallet USD ;
- wallet devise locale ;
- wallet professionnel séparé ;
- wallet voyage.

La disponibilité dépend du pays et des partenaires.

---

# 42. Solde

L’application doit distinguer :

- solde disponible ;
- solde comptable ;
- montant réservé ;
- montant en attente ;
- montant dans les coffres ;
- crédit éventuel ;
- devise.

---

# 43. Masquage du solde

L’utilisateur doit pouvoir masquer :

- solde ;
- montant des transactions ;
- valeur des cartes ;
- montant des coffres.

Ce choix doit pouvoir être mémorisé localement.

---

# 44. Actualisation du solde

L’utilisateur doit pouvoir :

- tirer pour actualiser ;
- voir la dernière mise à jour ;
- comprendre si les données sont en cache ;
- voir une alerte en cas de réseau faible.

---

# 45. Historique des transactions

L’historique doit permettre :

- liste ;
- recherche ;
- filtres ;
- tri ;
- période ;
- catégorie ;
- montant ;
- statut ;
- type ;
- bénéficiaire ;
- devise ;
- export.

---

# 46. Catégories d’opérations

Exemples :

- transfert envoyé ;
- transfert reçu ;
- paiement ;
- retrait ;
- dépôt ;
- facture ;
- recharge ;
- carte ;
- remboursement ;
- frais ;
- cashback ;
- salaire ;
- bourse ;
- commission ;
- épargne.

---

# 47. Statuts de transaction

- CREATED ;
- PENDING ;
- PROCESSING ;
- COMPLETED ;
- FAILED ;
- CANCELLED ;
- REVERSED ;
- REFUNDED ;
- PARTIALLY_REFUNDED ;
- DISPUTED ;
- REVIEW_REQUIRED.

---

# 48. Détail d’une transaction

Le détail doit afficher :

- type ;
- montant ;
- frais ;
- devise ;
- bénéficiaire ou marchand ;
- date ;
- heure ;
- statut ;
- référence ;
- canal ;
- localisation éventuelle ;
- reçu ;
- bouton Signaler ;
- bouton Partager ;
- bouton Répéter.

---

# 49. Reçu numérique

Le reçu peut être :

- affiché ;
- téléchargé ;
- partagé ;
- envoyé par e-mail ;
- envoyé par SMS ;
- enregistré dans les documents.

Il doit masquer les données sensibles.

---

# 50. Recherche de transaction

La recherche peut utiliser :

- nom ;
- montant ;
- référence ;
- date ;
- marchand ;
- catégorie ;
- numéro ;
- mot-clé.

---

# 51. Export de l’historique

Formats possibles :

- PDF ;
- CSV ;
- relevé mensuel ;
- relevé annuel ;
- période personnalisée.

Une authentification renforcée peut être demandée.

---

# 52. Transfert Mansa à Mansa

Le transfert peut être effectué par :

- numéro de téléphone ;
- nom d’utilisateur ;
- QR ;
- contact ;
- bénéficiaire enregistré ;
- lien ;
- identifiant Mansa.

---

# 53. Vérification du bénéficiaire

Avant confirmation, afficher :

- prénom ;
- nom partiellement masqué ;
- photo ou avatar éventuel ;
- numéro partiellement masqué ;
- statut vérifié ;
- avertissement contre les erreurs.

---

# 54. Parcours de transfert

1. choisir le bénéficiaire ;
2. saisir le montant ;
3. choisir la devise ;
4. ajouter un message ;
5. afficher les frais ;
6. afficher le total ;
7. confirmer ;
8. s’authentifier ;
9. traiter ;
10. afficher le résultat ;
11. générer le reçu ;
12. notifier.

---

# 55. Message de transfert

L’utilisateur peut ajouter :

- texte ;
- emoji ;
- catégorie ;
- référence ;
- motif.

Le message ne doit pas devenir un canal de contenu interdit ou de harcèlement.

---

# 56. Transfert programmé

L’utilisateur peut programmer :

- date ;
- heure ;
- fréquence ;
- bénéficiaire ;
- montant ;
- durée ;
- nombre d’exécutions ;
- notification.

---

# 57. Transfert récurrent

Fréquences possibles :

- quotidien ;
- hebdomadaire ;
- mensuel ;
- personnalisé.

L’utilisateur doit pouvoir :

- suspendre ;
- modifier ;
- annuler ;
- consulter les prochaines dates.

---

# 58. Transfert vers banque

Le parcours peut demander :

- banque ;
- nom ;
- numéro de compte ;
- IBAN ou RIB ;
- motif ;
- montant ;
- frais ;
- délai ;
- authentification.

---

# 59. Transfert vers Mobile Money

Le parcours doit permettre :

- opérateur ;
- numéro ;
- nom vérifié si disponible ;
- montant ;
- frais ;
- délai ;
- référence ;
- confirmation.

---

# 60. Transfert international

Lorsque disponible, afficher :

- pays ;
- devise ;
- taux ;
- frais ;
- montant reçu ;
- délai ;
- exigences KYC ;
- motif ;
- partenaire.

---

# 61. Annulation d’un transfert

Un transfert peut être annulé uniquement selon son statut.

- PENDING : annulation possible ;
- COMPLETED : annulation impossible, remboursement éventuel ;
- PROCESSING : demande de rappel éventuelle ;
- FAILED : aucun débit définitif.

---

# 62. Demande d’argent

L’utilisateur peut demander de l’argent à :

- un contact ;
- un utilisateur Mansa ;
- un groupe ;
- un tiers par lien ;
- un client ou proche.

---

# 63. Lien de paiement personnel

Le lien peut contenir :

- montant fixe ou libre ;
- motif ;
- expiration ;
- nombre d’utilisations ;
- bénéficiaire ;
- image éventuelle ;
- QR.

---

# 64. Réception d’argent

L’utilisateur doit voir :

- expéditeur ;
- montant ;
- date ;
- message ;
- référence ;
- éventuel statut de sécurité ;
- option remercier ;
- option renvoyer.

---

# 65. Paiement QR

L’application doit pouvoir :

- scanner un QR ;
- afficher son QR ;
- générer un QR ;
- payer un commerçant ;
- payer un particulier ;
- payer une facture ;
- payer une institution.

---

# 66. Types de QR

- QR statique ;
- QR dynamique ;
- QR marchand ;
- QR personnel ;
- QR facture ;
- QR Agent ;
- QR GAB ;
- QR institutionnel ;
- QR de retrait.

---

# 67. Scanner QR

Le scanner doit permettre :

- caméra ;
- flash ;
- import d’image ;
- reconnaissance ;
- vérification ;
- affichage du bénéficiaire ;
- signalement d’un QR suspect.

---

# 68. Paiement QR dynamique

Le QR peut contenir :

- commerçant ;
- point de vente ;
- montant ;
- devise ;
- référence ;
- caisse ;
- expiration ;
- signature ;
- terminal.

---

# 69. Paiement QR statique

L’utilisateur doit saisir ou confirmer :

- montant ;
- motif ;
- devise ;
- pourboire éventuel ;
- frais ;
- bénéficiaire.

---

# 70. Confirmation du paiement

L’écran doit afficher :

- commerçant ;
- logo ;
- point de vente ;
- montant ;
- frais ;
- récompense éventuelle ;
- total ;
- moyen de paiement ;
- bouton Confirmer.

---

# 71. Paiement NFC

Le paiement NFC peut permettre :

- Tap to Pay ;
- paiement avec téléphone ;
- carte tokenisée ;
- authentification selon montant ;
- confirmation ;
- notification.

La disponibilité dépend du matériel et des partenaires.

---

# 72. Paiement à distance

L’utilisateur peut payer via :

- lien ;
- QR ;
- notification ;
- demande commerçant ;
- facture ;
- panier ;
- abonnement.

---

# 73. Pourboire

Le paiement peut proposer :

- aucun ;
- montant libre ;
- pourcentage ;
- valeurs prédéfinies.

La fonction doit être administrable.

---

# 74. Paiement partagé

Une addition peut être divisée :

- à parts égales ;
- par montant ;
- par article ;
- par pourcentage ;
- avec un payeur principal ;
- entre utilisateurs Mansa et non-Mansa.

---

# 75. Groupe de dépense

L’utilisateur peut créer un groupe pour :

- restaurant ;
- voyage ;
- colocation ;
- cadeau ;
- événement ;
- famille ;
- projet.

---

# 76. Répartition d’une dépense

Le système doit gérer :

- participants ;
- montants ;
- avances ;
- remboursements ;
- solde de chacun ;
- rappels ;
- statut ;
- clôture.

---

# 77. Paiement fractionné

Lorsque disponible, afficher clairement :

- montant total ;
- apport ;
- échéances ;
- frais ;
- taux ;
- dates ;
- conditions ;
- retard ;
- coût total.

---

# 78. Paiement de factures

Catégories possibles :

- eau ;
- électricité ;
- téléphone ;
- Internet ;
- télévision ;
- école ;
- assurance ;
- impôts ;
- taxes ;
- amendes ;
- loyer ;
- services.

---

# 79. Ajout d’un fournisseur

L’utilisateur peut :

- choisir un fournisseur ;
- saisir la référence ;
- scanner une facture ;
- enregistrer le compte ;
- choisir un nom personnalisé ;
- activer des rappels.

---

# 80. Facture détectée

Le système peut afficher :

- fournisseur ;
- montant ;
- échéance ;
- référence ;
- frais ;
- statut ;
- bouton Payer.

---

# 81. Paiement automatique de facture

L’utilisateur doit définir :

- fournisseur ;
- plafond ;
- fréquence ;
- compte débité ;
- notification avant paiement ;
- condition d’arrêt ;
- authentification initiale.

---

# 82. Recharge téléphonique

L’utilisateur peut recharger :

- son numéro ;
- un contact ;
- un numéro saisi ;
- plusieurs numéros ;
- un forfait ;
- du crédit simple.

---

# 83. Recharge Mobile Money

Selon les intégrations, l’utilisateur peut :

- créditer un compte Mobile Money ;
- retirer depuis Mobile Money vers Mansa ;
- choisir l’opérateur ;
- voir les frais ;
- suivre le statut.

---

# 84. Ajouter de l’argent

Les moyens possibles :

- Agent ;
- Mobile Money ;
- carte bancaire ;
- transfert bancaire ;
- dépôt GAB ;
- salaire ;
- bourse ;
- virement ;
- code promotionnel.

---

# 85. Dépôt chez un Agent

L’application doit afficher :

- Agents proches ;
- horaires ;
- disponibilité ;
- distance ;
- frais ;
- statut ;
- itinéraire ;
- limite.

Le dépôt n’exige pas forcément une confirmation du client dans l’application lorsque l’Agent identifie correctement le compte et remet un reçu.

---

# 86. Notification de dépôt Agent

Le client reçoit :

- nom ou identifiant Agent ;
- montant ;
- frais ;
- date ;
- heure ;
- nouveau solde ;
- référence ;
- bouton Signaler.

---

# 87. Retrait chez un Agent

Le retrait peut utiliser :

- QR ;
- code ;
- numéro ;
- application ;
- validation biométrique ;
- OTP ;
- authentification forte.

---

# 88. Code de retrait Agent

Le code doit contenir :

- montant ;
- durée ;
- Agent ou zone éventuelle ;
- bénéficiaire ;
- référence ;
- nombre d’essais ;
- statut.

---

# 89. Retrait GAB/DAB

L’application doit permettre :

- localiser la machine ;
- vérifier les services ;
- générer un code ;
- générer un QR ;
- choisir le montant ;
- consulter les frais ;
- suivre l’opération ;
- signaler un problème.

---

# 90. Dépôt GAB

L’utilisateur peut :

- choisir une machine ;
- consulter sa disponibilité ;
- voir les limites ;
- générer un QR d’identification ;
- suivre le dépôt ;
- recevoir le reçu ;
- signaler un billet bloqué.

---

# 91. Carte physique

L’utilisateur peut :

- commander ;
- personnaliser selon les options ;
- suivre la livraison ;
- activer ;
- définir le PIN ;
- bloquer ;
- débloquer ;
- modifier les limites ;
- consulter les transactions ;
- remplacer ;
- mettre en opposition.

---

# 92. Commande de carte

Le parcours peut demander :

- type de carte ;
- design ;
- nom affiché ;
- adresse ;
- mode de livraison ;
- frais ;
- délai ;
- conditions ;
- confirmation.

---

# 93. Nom sur la carte

Le nom du client peut être :

- imprimé ;
- gravé ;
- absent selon le programme ;
- limité en longueur ;
- validé selon l’identité KYC.

---

# 94. Design de carte

L’administration peut proposer :

- design standard ;
- design premium ;
- design pays ;
- design événementiel ;
- design entreprise ;
- design étudiant ;
- design personnalisable limité.

---

# 95. Suivi de livraison

Statuts possibles :

- ORDERED ;
- IN_PRODUCTION ;
- PERSONALIZED ;
- SHIPPED ;
- IN_TRANSIT ;
- AVAILABLE_FOR_PICKUP ;
- DELIVERED ;
- FAILED ;
- RETURNED.

---

# 96. Activation de la carte

L’activation peut utiliser :

- derniers chiffres ;
- code reçu ;
- scan ;
- NFC ;
- OTP ;
- authentification ;
- premier paiement avec PIN.

---

# 97. Carte virtuelle

L’utilisateur peut créer une carte virtuelle avec :

- numéro tokenisé ;
- expiration ;
- CVV dynamique éventuel ;
- limite ;
- usage ;
- blocage ;
- suppression ;
- marchand autorisé.

---

# 98. Carte jetable

Une carte jetable peut changer après chaque utilisation réussie.

L’administration doit pouvoir définir :

- disponibilité ;
- pays ;
- abonnement ;
- montant maximum ;
- commerçants exclus ;
- nombre d’utilisations.

---

# 99. Carte temporaire

L’utilisateur peut définir :

- date d’expiration ;
- limite ;
- devise ;
- marchand ;
- pays ;
- nombre d’utilisations.

---

# 100. Carte enfant ou proche

Lorsque la réglementation et le produit le permettent, l’utilisateur peut gérer une carte liée avec :

- plafond ;
- catégories autorisées ;
- horaires ;
- géographie ;
- notifications ;
- blocage ;
- argent de poche.

---

# 101. Paramètres carte

L’utilisateur peut activer ou désactiver :

- paiement en ligne ;
- paiement sans contact ;
- retrait ;
- paiement international ;
- paiement par bande magnétique ;
- paiement récurrent ;
- certaines catégories ;
- pays.

---

# 102. Limites carte

Limites possibles :

- paiement par opération ;
- paiement journalier ;
- retrait par opération ;
- retrait journalier ;
- paiement en ligne ;
- paiement international ;
- sans contact.

---

# 103. Blocage temporaire

Le blocage temporaire doit être immédiat.

L’utilisateur peut ensuite :

- débloquer ;
- signaler une perte ;
- signaler un vol ;
- commander un remplacement.

---

# 104. Opposition définitive

L’opposition doit expliquer :

- caractère définitif ;
- impact ;
- opérations déjà autorisées ;
- remplacement ;
- frais éventuels ;
- délai ;
- assistance.

---

# 105. PIN carte

L’utilisateur peut :

- consulter une aide ;
- changer le PIN ;
- débloquer selon procédure ;
- trouver un GAB compatible ;
- signaler un oubli.

Le PIN ne doit jamais être stocké ni affiché en clair.

---

# 106. Apple Wallet et Google Wallet

Lorsque disponible, l’utilisateur peut :

- ajouter la carte ;
- vérifier l’éligibilité ;
- s’authentifier ;
- voir le statut ;
- supprimer le token ;
- gérer les appareils.

---

# 107. Abonnements détectés

L’application peut détecter les paiements récurrents et afficher :

- marchand ;
- montant ;
- fréquence ;
- prochaine date ;
- carte utilisée ;
- évolution du prix ;
- statut ;
- bouton gérer.

---

# 108. Résiliation assistée

Jini ou le support peut aider à :

- trouver la procédure ;
- préparer un message ;
- ouvrir le site du fournisseur ;
- rappeler l’échéance ;
- bloquer un paiement futur lorsque légalement et techniquement possible.

---

# 109. Coffres d’épargne

L’utilisateur peut créer un coffre pour :

- voyage ;
- voiture ;
- maison ;
- études ;
- urgence ;
- projet ;
- mariage ;
- achat ;
- objectif libre.

---

# 110. Création d’un coffre

Données :

- nom ;
- image ;
- objectif ;
- montant cible ;
- date cible ;
- contribution initiale ;
- règles automatiques ;
- visibilité ;
- participants éventuels.

---

# 111. Alimentation automatique d’un coffre

Règles possibles :

- montant fixe périodique ;
- arrondi des paiements ;
- pourcentage des revenus ;
- pourcentage des dépenses ;
- cashback ;
- transfert manuel ;
- jour choisi.

---

# 112. Coffre partagé

Le coffre partagé peut gérer :

- créateur ;
- participants ;
- droits ;
- contributions ;
- objectif ;
- retrait ;
- approbation ;
- historique ;
- notifications.

---

# 113. Retrait d’un coffre

Le retrait peut être :

- libre ;
- limité ;
- soumis à délai ;
- soumis à frais ;
- soumis à validation ;
- lié à une date.

Tout doit être présenté avant confirmation.

---

# 114. Budgets

L’utilisateur peut créer un budget par :

- catégorie ;
- période ;
- marchand ;
- carte ;
- projet ;
- groupe ;
- pays.

---

# 115. Catégories de budget

Exemples :

- alimentation ;
- transport ;
- logement ;
- loisirs ;
- santé ;
- études ;
- famille ;
- abonnements ;
- voyages ;
- autres.

---

# 116. Alertes budget

L’application peut alerter à :

- 50 % ;
- 75 % ;
- 90 % ;
- 100 % ;
- dépassement ;
- rythme anormal ;
- dépense importante.

---

# 117. Analyse des dépenses

L’utilisateur peut consulter :

- total ;
- évolution ;
- catégories ;
- marchands ;
- périodes ;
- moyenne ;
- comparaison ;
- abonnements ;
- dépenses inhabituelles.

---

# 118. Prévisions

Jini peut proposer :

- estimation de fin de mois ;
- risque de dépassement ;
- capacité d’épargne ;
- charges à venir ;
- abonnements ;
- factures attendues.

Les prévisions doivent être présentées comme des estimations.

---

# 119. Objectifs financiers

L’utilisateur peut définir :

- objectif ;
- montant ;
- date ;
- priorité ;
- contribution ;
- progression ;
- rappels.

---

# 120. Fidélité

L’espace fidélité peut afficher :

- points ;
- niveau ;
- avantages ;
- historique ;
- partenaires ;
- récompenses ;
- expiration ;
- conditions.

---

# 121. Cashback

Le cashback peut dépendre :

- marchand ;
- catégorie ;
- campagne ;
- carte ;
- pays ;
- montant ;
- date ;
- limite ;
- abonnement.

---

# 122. Promotions

L’application peut afficher :

- offres ;
- réduction ;
- durée ;
- partenaires ;
- distance ;
- conditions ;
- bouton utiliser ;
- suivi.

---

# 123. Carte des partenaires

Une carte peut afficher :

- Agents ;
- commerçants ;
- GAB ;
- DAB ;
- agences ;
- promotions ;
- services publics ;
- établissements scolaires.

---

# 124. Recherche à proximité

Filtres :

- ouvert maintenant ;
- dépôt ;
- retrait ;
- TPE ;
- paiement QR ;
- GAB ;
- DAB ;
- dépôt GAB ;
- accessibilité ;
- promotion ;
- distance.

---

# 125. Fiche d’un Agent

Elle peut afficher :

- nom commercial ;
- identifiant vérifié ;
- adresse ;
- distance ;
- horaires ;
- services ;
- limites ;
- frais ;
- disponibilité déclarée ;
- note éventuelle ;
- itinéraire.

Le montant de cash exact ne doit pas être exposé publiquement.

---

# 126. Fiche d’un GAB/DAB

Elle peut afficher :

- type ;
- statut ;
- retrait ;
- dépôt ;
- cartes acceptées ;
- accessibilité ;
- horaires ;
- langues ;
- frais ;
- itinéraire ;
- dernière mise à jour.

---

# 127. Notifications

Types :

- transaction ;
- sécurité ;
- carte ;
- KYC ;
- promotion ;
- budget ;
- facture ;
- abonnement ;
- support ;
- maintenance ;
- information réglementaire.

---

# 128. Centre de notifications

Il doit permettre :

- liste ;
- lecture ;
- recherche ;
- filtres ;
- suppression locale ;
- action directe ;
- statut lu ou non lu ;
- lien vers l’opération.

---

# 129. Préférences de notifications

L’utilisateur peut configurer :

- push ;
- SMS ;
- e-mail ;
- catégories ;
- plages horaires ;
- langue ;
- marketing ;
- alertes obligatoires.

Les alertes de sécurité critiques ne doivent pas être totalement désactivables.

---

# 130. Support

Le support doit être accessible depuis :

- accueil ;
- profil ;
- transaction ;
- carte ;
- KYC ;
- GAB/DAB ;
- Agent ;
- erreur ;
- Jini.

---

# 131. Canaux de support

- FAQ ;
- base de connaissances ;
- Jini ;
- chat ;
- ticket ;
- téléphone ;
- e-mail ;
- rappel ;
- agence ;
- Agent autorisé pour certaines aides.

---

# 132. Création d’un ticket

Le ticket peut contenir :

- catégorie ;
- transaction ;
- description ;
- capture ;
- document ;
- urgence ;
- canal ;
- langue ;
- disponibilité.

---

# 133. Ticket lié à une transaction

L’application doit préremplir :

- référence ;
- montant ;
- date ;
- statut ;
- canal ;
- partenaire ;
- appareil.

---

# 134. Suivi du ticket

Statuts :

- CREATED ;
- OPEN ;
- ASSIGNED ;
- IN_PROGRESS ;
- WAITING_CUSTOMER ;
- RESOLVED ;
- CLOSED ;
- REOPENED.

---

# 135. Litige

L’utilisateur peut signaler :

- paiement inconnu ;
- débit sans service ;
- transfert non reçu ;
- retrait non distribué ;
- dépôt non crédité ;
- double débit ;
- fraude carte ;
- mauvaise facture ;
- remboursement non reçu.

---

# 136. Preuves

L’utilisateur peut ajouter :

- capture ;
- photo ;
- reçu ;
- facture ;
- message ;
- document ;
- vidéo limitée si autorisée.

---

# 137. Remboursement

Le suivi doit afficher :

- montant ;
- commerçant ;
- date de demande ;
- statut ;
- délai estimé ;
- référence ;
- méthode de remboursement.

---

# 138. Jini

Jini doit être intégré comme assistant financier et support.

Il peut :

- expliquer une transaction ;
- aider à effectuer un transfert ;
- trouver une fonctionnalité ;
- rechercher un Agent ;
- rechercher un GAB ;
- expliquer les frais ;
- aider à gérer le budget ;
- identifier un abonnement ;
- préparer une demande support ;
- répondre depuis la documentation.

---

# 139. Limites de Jini

Jini ne doit pas :

- révéler un secret ;
- afficher un PIN ;
- modifier un compte sans confirmation ;
- effectuer un paiement seul ;
- contourner les limites ;
- donner accès à un autre compte ;
- inventer un statut ;
- promettre un remboursement ;
- masquer les frais ;
- remplacer une validation obligatoire.

---

# 140. Actions Jini avec confirmation

Jini peut préparer :

- transfert ;
- paiement ;
- blocage carte ;
- création coffre ;
- budget ;
- ticket ;
- recherche ;
- ajout bénéficiaire.

L’utilisateur doit confirmer l’action finale.

---

# 141. Profil

Le profil doit afficher :

- photo ;
- nom ;
- identifiant ;
- téléphone ;
- e-mail ;
- pays ;
- langue ;
- niveau KYC ;
- statut ;
- adresse ;
- profession éventuelle ;
- documents ;
- paramètres.

---

# 142. Modification du profil

Les champs sensibles peuvent nécessiter :

- OTP ;
- PIN ;
- biométrie ;
- délai ;
- nouveau KYC ;
- validation support.

---

# 143. Changement de numéro

Le processus doit vérifier :

- ancien numéro ;
- nouveau numéro ;
- OTP ;
- identité ;
- appareils ;
- cartes ;
- risque ;
- délai ;
- notification.

---

# 144. Changement d’e-mail

Le processus doit vérifier :

- e-mail actuel ;
- nouvel e-mail ;
- code ;
- authentification ;
- notification.

---

# 145. Adresse

L’utilisateur peut :

- saisir ;
- sélectionner sur une carte ;
- ajouter plusieurs adresses ;
- choisir une adresse de livraison ;
- fournir une preuve si nécessaire.

---

# 146. Documents personnels

L’espace documents peut contenir :

- pièce KYC ;
- relevés ;
- reçus ;
- attestations ;
- RIB ;
- documents fiscaux ;
- contrats ;
- justificatifs.

---

# 147. RIB ou coordonnées de compte

L’utilisateur peut :

- consulter ;
- copier ;
- partager ;
- télécharger ;
- envoyer ;
- générer un QR ;
- voir la banque partenaire éventuelle.

---

# 148. Paramètres généraux

- langue ;
- pays ;
- devise d’affichage ;
- thème ;
- notifications ;
- confidentialité ;
- accessibilité ;
- sécurité ;
- appareils ;
- données ;
- documents ;
- support.

---

# 149. Apparence

L’application peut proposer :

- thème système ;
- thème clair ;
- thème sombre ;
- taille de texte ;
- contraste ;
- réduction des animations.

---

# 150. Accessibilité

Fonctions :

- lecteur d’écran ;
- navigation clavier lorsque applicable ;
- taille du texte ;
- contraste ;
- libellés ;
- vibrations ;
- lecture audio ;
- simplification ;
- sous-titres ;
- gestes alternatifs.

---

# 151. Confidentialité

L’utilisateur doit pouvoir consulter :

- données collectées ;
- finalités ;
- partenaires ;
- consentements ;
- historique ;
- téléchargements ;
- demandes ;
- suppression éventuelle ;
- durée de conservation.

---

# 152. Téléchargement des données

L’utilisateur peut demander une copie de :

- profil ;
- transactions ;
- consentements ;
- appareils ;
- tickets ;
- documents ;
- paramètres.

---

# 153. Fermeture du compte

Le parcours doit vérifier :

- solde ;
- opérations en attente ;
- cartes ;
- litiges ;
- crédits ;
- abonnements ;
- coffres ;
- obligations ;
- identité ;
- motif ;
- délai.

---

# 154. Compte dormant

Un compte inactif peut recevoir :

- rappel ;
- confirmation de sécurité ;
- information sur les frais éventuels ;
- procédure de réactivation ;
- avertissement réglementaire.

---

# 155. Compte suspendu

L’écran doit afficher :

- accès disponible ;
- opérations bloquées ;
- raison générale lorsque possible ;
- action requise ;
- contact support ;
- documents à fournir ;
- recours éventuel.

---

# 156. Compte gelé

Le gel peut empêcher :

- transfert ;
- paiement ;
- retrait ;
- carte ;
- dépôt tiers ;
- conversion.

La consultation et le support peuvent rester disponibles.

---

# 157. Sécurité

L’espace Sécurité doit gérer :

- PIN ;
- mot de passe ;
- biométrie ;
- passkeys ;
- appareils ;
- sessions ;
- limites ;
- alertes ;
- cartes ;
- connexion ;
- récupération.

---

# 158. Centre de sécurité

Il peut afficher un score ou une checklist :

- biométrie activée ;
- appareil vérifié ;
- e-mail vérifié ;
- PIN robuste ;
- notifications activées ;
- aucun appareil inconnu ;
- KYC à jour.

---

# 159. Alertes de sécurité

Exemples :

- nouvelle connexion ;
- nouvel appareil ;
- changement PIN ;
- ajout bénéficiaire ;
- changement de numéro ;
- carte ajoutée à un wallet ;
- transaction inhabituelle ;
- compte bloqué ;
- récupération demandée.

---

# 160. Appareils connectés

Pour chaque appareil :

- nom ;
- modèle ;
- OS ;
- localisation approximative ;
- dernière activité ;
- statut ;
- bouton Révoquer ;
- appareil actuel.

---

# 161. Protection contre les captures

Les écrans contenant des informations sensibles peuvent limiter les captures selon la plateforme.

Cela ne remplace pas les autres contrôles de sécurité.

---

# 162. Masquage automatique

L’application doit se masquer dans le sélecteur d’applications lorsque cela est possible et approprié.

---

# 163. Verrouillage automatique

L’utilisateur doit être redemandé après :

- durée d’inactivité ;
- passage en arrière-plan ;
- changement sensible ;
- risque détecté ;
- redémarrage.

---

# 164. Détection root et jailbreak

L’application peut :

- avertir ;
- limiter ;
- demander une vérification ;
- bloquer les fonctions sensibles ;
- refuser l’accès selon la politique.

---

# 165. Détection d’émulateur

Les émulateurs peuvent être autorisés en Démo et Test, mais limités en Production.

---

# 166. Protection réseau

L’application doit vérifier :

- certificat ;
- domaine ;
- chiffrement ;
- proxy suspect ;
- interception ;
- version TLS ;
- intégrité de la réponse.

---

# 167. Réseau faible

L’application doit :

- afficher l’état ;
- réduire les données ;
- compresser les médias ;
- reprendre les chargements ;
- éviter les doubles opérations ;
- conserver les brouillons ;
- afficher la dernière donnée connue ;
- distinguer les données non actualisées.

---

# 168. Mode hors ligne

Le mode hors ligne peut permettre :

- consultation limitée de données en cache ;
- lecture des reçus ;
- préparation d’une opération ;
- consultation des contacts ;
- affichage de QR non financier autorisé ;
- accès aux documents.

Les opérations financières réelles doivent attendre une connexion, sauf mécanisme spécifique validé.

---

# 169. Synchronisation

Après reconnexion :

- vérifier la session ;
- vérifier les opérations ;
- synchroniser les brouillons ;
- actualiser les soldes ;
- récupérer les notifications ;
- résoudre les conflits ;
- confirmer les statuts.

---

# 170. Prévention du double paiement

L’application doit utiliser :

- clé d’idempotence ;
- bouton temporairement bloqué ;
- référence unique ;
- confirmation serveur ;
- écran de traitement ;
- vérification de statut avant réessai.

---

# 171. Écran de traitement

Pendant une opération :

- animation ;
- message clair ;
- interdiction de quitter si nécessaire ;
- référence ;
- délai ;
- bouton Masquer sans annuler ;
- reprise automatique.

---

# 172. Timeout

En cas de timeout :

- ne pas afficher immédiatement Échec si le statut est inconnu ;
- afficher Vérification en cours ;
- interroger le backend ;
- éviter un nouvel envoi ;
- notifier le résultat final.

---

# 173. Deep Links

L’application peut ouvrir directement :

- transaction ;
- paiement ;
- facture ;
- ticket ;
- carte ;
- KYC ;
- promotion ;
- demande d’argent ;
- notification.

---

# 174. Liens universels

Les liens doivent être :

- vérifiés ;
- signés lorsque nécessaire ;
- expirants pour les actions sensibles ;
- résistants au phishing ;
- redirigés vers le store si l’application manque.

---

# 175. Widgets

L’application peut proposer des widgets avec :

- solde masqué ;
- action rapide ;
- QR ;
- coffre ;
- dépense du mois ;
- raccourci support.

Aucune donnée sensible ne doit être exposée sans contrôle.

---

# 176. Analytics produit

Événements possibles :

```text
client_app_opened
client_signup_started
client_signup_completed
client_kyc_started
client_kyc_submitted
client_home_opened
client_transfer_started
client_transfer_completed
client_payment_started
client_payment_completed
client_card_created
client_cash_withdrawal_code_created
client_support_ticket_created
client_jini_opened
```

---

# 177. Données analytics interdites

Ne pas transmettre :

- PIN ;
- mot de passe ;
- OTP ;
- CVV ;
- PAN complet ;
- document complet ;
- biométrie brute ;
- message privé complet ;
- solde sans nécessité ;
- secret ;
- clé ;
- données de tiers non nécessaires.

---

# 178. Crash Reporting

Les rapports de crash doivent contenir :

- version ;
- OS ;
- modèle ;
- écran ;
- erreur ;
- trace technique ;
- contexte non sensible ;
- date ;
- identifiant anonyme ou pseudonymisé.

---

# 179. Performance

Objectifs à définir pour :

- démarrage ;
- connexion ;
- affichage du solde ;
- ouverture historique ;
- scan QR ;
- confirmation paiement ;
- chargement carte ;
- faible réseau ;
- consommation batterie ;
- mémoire.

---

# 180. Notifications push

Les notifications transactionnelles doivent inclure :

- montant ;
- type ;
- statut ;
- référence courte ;
- accès au détail.

Le contenu sur écran verrouillé doit respecter le choix de confidentialité.

---

# 181. Masquage des notifications

L’utilisateur peut choisir :

- tout afficher ;
- masquer les montants ;
- masquer le contenu ;
- afficher uniquement « Nouvelle activité ».

---

# 182. Administration de l’application

L’administration doit pouvoir gérer :

- version minimale ;
- version recommandée ;
- modules ;
- navigation ;
- actions rapides ;
- textes ;
- images ;
- couleurs autorisées ;
- onboarding ;
- campagnes ;
- promotions ;
- pays ;
- langues ;
- frais ;
- limites ;
- cartes ;
- QR ;
- Agents ;
- GAB/DAB ;
- support ;
- Jini ;
- alertes ;
- maintenance ;
- feature flags.

---

# 183. Segmentation

Les contenus peuvent être ciblés selon :

- pays ;
- ville ;
- langue ;
- âge ;
- niveau KYC ;
- ancienneté ;
- produit ;
- appareil ;
- version ;
- comportement ;
- segment ;
- risque.

---

# 184. Campagnes in-app

Formats :

- bannière ;
- modal ;
- carte ;
- notification ;
- écran plein ;
- tooltip ;
- message Jini ;
- offre personnalisée.

---

# 185. Priorité des messages

Niveaux :

- INFORMATION ;
- PROMOTION ;
- WARNING ;
- IMPORTANT ;
- SECURITY ;
- CRITICAL.

---

# 186. Expérimentation

Les tests A/B doivent être limités aux éléments non critiques.

Ils ne doivent pas modifier secrètement :

- frais ;
- règles financières ;
- sécurité ;
- droits ;
- résultat d’une transaction ;
- conformité.

---

# 187. API principales

Exemples :

```http
POST   /client/auth/register
POST   /client/auth/login
POST   /client/auth/otp/verify
POST   /client/auth/recover

GET    /client/profile
PATCH  /client/profile
GET    /client/devices
DELETE /client/devices/{id}

GET    /client/kyc
POST   /client/kyc
POST   /client/kyc/documents
POST   /client/kyc/selfie

GET    /client/wallets
GET    /client/wallets/{id}/balance
GET    /client/transactions
GET    /client/transactions/{id}

POST   /client/transfers
POST   /client/payment-requests
POST   /client/payments
POST   /client/qr/resolve

POST   /client/cash/withdrawal-codes
GET    /client/cash/agents
GET    /client/atms

GET    /client/cards
POST   /client/cards
POST   /client/cards/{id}/freeze
POST   /client/cards/{id}/unfreeze
POST   /client/cards/{id}/replace

GET    /client/bills
POST   /client/bills/pay
GET    /client/subscriptions

GET    /client/savings
POST   /client/savings
POST   /client/budgets

GET    /client/notifications
POST   /client/support/tickets
POST   /client/jini/messages
```

---

# 188. Webhooks internes

Événements possibles :

```text
client.registered
client.login.succeeded
client.login.failed
client.device.added
client.device.revoked
client.kyc.submitted
client.kyc.approved
client.kyc.rejected

client.wallet.created
client.transfer.created
client.transfer.completed
client.payment.completed
client.payment.failed
client.cash.withdrawal_code.created
client.cash.deposit.completed

client.card.ordered
client.card.activated
client.card.frozen
client.card.replaced

client.savings.created
client.budget.limit_reached
client.support.ticket_created
client.security.alert_created
```

---

# 189. Modèles principaux

- ClientProfile
- ClientPreference
- ClientDevice
- ClientSession
- ClientConsent
- ClientKYCProfile
- ClientWallet
- ClientTransaction
- ClientBeneficiary
- ClientTransfer
- PaymentRequest
- ClientPayment
- QRPaymentSession
- CashWithdrawalCode
- ClientCard
- CardDelivery
- CardControl
- BillAccount
- BillPayment
- RecurringPayment
- SubscriptionDetection
- SavingsVault
- SavingsRule
- Budget
- BudgetAlert
- ExpenseCategory
- LoyaltyAccount
- CashbackReward
- NearbyLocation
- ClientNotification
- SupportTicket
- SecurityAlert
- ClientAudit

---

# 190. Rôles internes associés

Exemples :

```text
CLIENT_SUPPORT_OPERATOR
CLIENT_KYC_REVIEWER
CLIENT_FRAUD_ANALYST
CLIENT_CARD_OPERATOR
CLIENT_PAYMENT_OPERATOR
CLIENT_COMPLAINT_MANAGER
CLIENT_CONTENT_MANAGER
CLIENT_SECURITY_ADMIN
CLIENT_PRODUCT_ADMIN
AUDITOR
VIEWER
```

---

# 191. Permissions administratives

Exemples :

```text
client.read
client.profile.read
client.profile.update
client.kyc.read
client.kyc.review
client.wallet.read
client.wallet.freeze
client.transaction.read
client.payment.investigate
client.card.manage
client.device.revoke
client.support.manage
client.content.manage
client.configuration.publish
client.audit.read
```

---

# 192. Approbations

Peuvent nécessiter une approbation :

- gel du wallet ;
- dégel du wallet ;
- modification manuelle KYC ;
- remboursement important ;
- correction financière ;
- réactivation d’un compte compromis ;
- modification de limite exceptionnelle ;
- fermeture forcée ;
- suppression de document ;
- modification nationale des frais.

---

# 193. Double validation

Doit être exigée pour :

- écriture financière manuelle ;
- correction de solde ;
- dégel réglementaire ;
- remboursement important ;
- changement de bénéficiaire d’un transfert terminé ;
- suppression d’une preuve ;
- réactivation après fraude critique ;
- changement massif de limites ;
- blocage massif de comptes.

---

# 194. Audit

Le journal doit contenir :

- client ;
- appareil ;
- session ;
- action ;
- ressource ;
- pays ;
- date ;
- heure ;
- ancienne valeur ;
- nouvelle valeur ;
- canal ;
- résultat ;
- risque ;
- approbateur éventuel ;
- référence.

---

# 195. Tests d’onboarding

- lancement initial ;
- choix pays ;
- choix langue ;
- inscription ;
- OTP ;
- compte existant ;
- consentements ;
- PIN ;
- biométrie ;
- erreur réseau ;
- reprise.

---

# 196. Tests d’authentification

- connexion correcte ;
- PIN incorrect ;
- mot de passe incorrect ;
- nouvel appareil ;
- appareil compromis ;
- récupération ;
- déconnexion ;
- révocation ;
- session expirée ;
- MFA ;
- biométrie.

---

# 197. Tests KYC

- capture document ;
- document flou ;
- document expiré ;
- mauvais pays ;
- selfie ;
- liveness ;
- revue manuelle ;
- rejet ;
- recours ;
- expiration ;
- mise à jour.

---

# 198. Tests Wallet

- création ;
- solde ;
- réservation ;
- devise ;
- gel ;
- dégel ;
- actualisation ;
- affichage cache ;
- historique ;
- export.

---

# 199. Tests Transfert

- Mansa à Mansa ;
- banque ;
- Mobile Money ;
- international ;
- bénéficiaire ;
- frais ;
- limite ;
- annulation ;
- timeout ;
- idempotence ;
- transfert récurrent.

---

# 200. Tests Paiement

- QR statique ;
- QR dynamique ;
- NFC ;
- lien ;
- facture ;
- commerçant ;
- pourboire ;
- split ;
- échec ;
- remboursement ;
- double clic ;
- réseau faible.

---

# 201. Tests Cash

- dépôt Agent ;
- retrait Agent ;
- code ;
- expiration ;
- GAB ;
- DAB ;
- dépôt GAB ;
- retrait sans carte ;
- billet non distribué ;
- notification ;
- litige.

---

# 202. Tests Cartes

- commande ;
- livraison ;
- activation ;
- PIN ;
- blocage ;
- opposition ;
- remplacement ;
- virtuelle ;
- jetable ;
- temporaire ;
- Wallet mobile ;
- limites ;
- international.

---

# 203. Tests Épargne et budgets

- création coffre ;
- alimentation ;
- règle automatique ;
- retrait ;
- coffre partagé ;
- budget ;
- alerte ;
- prévision ;
- suppression ;
- historique.

---

# 204. Tests Support et Jini

- FAQ ;
- ticket ;
- pièce jointe ;
- transaction liée ;
- litige ;
- Jini ;
- permissions ;
- confirmation ;
- escalade ;
- reprise conversation.

---

# 205. Tests de sécurité

- root ;
- jailbreak ;
- émulateur ;
- interception ;
- certificat ;
- session ;
- PIN ;
- OTP ;
- biométrie ;
- appareil ;
- capture ;
- deep link ;
- lien malveillant ;
- données locales ;
- logs.

---

# 206. Tests de performance

- démarrage à froid ;
- démarrage à chaud ;
- réseau 2G ou faible ;
- liste longue ;
- historique ;
- scan QR ;
- paiement ;
- synchronisation ;
- consommation mémoire ;
- consommation batterie.

---

# 207. Tests d’accessibilité

- lecteur d’écran ;
- contraste ;
- taille de texte ;
- navigation ;
- libellés ;
- ordre de focus ;
- erreurs ;
- boutons ;
- audio ;
- réduction des animations.

---

# 208. Règles métier

1. Toute opération financière passe par le ledger.
2. Les frais sont affichés avant confirmation.
3. Le solde disponible est distingué du solde comptable.
4. Toute opération possède une référence.
5. Les opérations sont idempotentes.
6. Le client peut masquer son solde.
7. Le KYC détermine les limites.
8. Les fonctions sont activables par pays.
9. Les fonctions sont activables par segment.
10. Les actions critiques exigent une confirmation.
11. Le nouvel appareil exige une vérification.
12. Les OTP expirent.
13. Le PIN n’est jamais stocké en clair.
14. Les cartes peuvent être bloquées immédiatement.
15. Le paiement QR vérifie le bénéficiaire.
16. Un timeout n’est pas traité comme un échec définitif sans vérification.
17. Le dépôt Agent ne nécessite pas systématiquement une confirmation dans l’application Client.
18. Le retrait exige une authentification.
19. Les codes de retrait expirent.
20. Les alertes de sécurité critiques restent obligatoires.
21. Jini ne réalise pas seul une transaction.
22. Les données sensibles sont exclues des analytics.
23. Les fonctionnalités hors ligne restent limitées.
24. Toute correction financière est auditée.
25. Les audits sont immuables.

---

# 209. Critères d’acceptation

L’Application Client Mansa est validée lorsque :

- Android et iOS sont supportés ;
- le Splash Screen fonctionne ;
- la maintenance est gérée ;
- les versions minimales sont contrôlées ;
- l’onboarding est administrable ;
- le pays est sélectionnable ;
- la langue est modifiable ;
- l’inscription fonctionne ;
- l’OTP fonctionne ;
- les comptes existants sont détectés ;
- les consentements sont versionnés ;
- le PIN est sécurisé ;
- la biométrie fonctionne ;
- la connexion fonctionne ;
- les appareils sont reconnus ;
- les nouveaux appareils sont vérifiés ;
- la récupération fonctionne ;
- les comptes compromis peuvent être bloqués ;
- le KYC est configurable ;
- les niveaux KYC sont gérés ;
- la capture documentaire fonctionne ;
- le selfie est contrôlé ;
- les statuts KYC sont affichés ;
- les rejets KYC sont gérés ;
- les expirations KYC sont gérées ;
- le wallet est créé ;
- les wallets multiples sont supportables ;
- les soldes sont correctement distingués ;
- le solde peut être masqué ;
- l’historique est disponible ;
- la recherche transactionnelle fonctionne ;
- les reçus sont disponibles ;
- l’export fonctionne ;
- les transferts Mansa fonctionnent ;
- les bénéficiaires sont vérifiés ;
- les frais sont affichés ;
- les transferts programmés fonctionnent ;
- les transferts bancaires sont supportables ;
- Mobile Money est supportable ;
- les transferts internationaux sont supportables ;
- les demandes d’argent fonctionnent ;
- les liens de paiement fonctionnent ;
- le QR statique fonctionne ;
- le QR dynamique fonctionne ;
- le scanner fonctionne ;
- le paiement NFC est supportable ;
- les paiements à distance fonctionnent ;
- le pourboire est configurable ;
- le partage de dépense fonctionne ;
- les groupes de dépenses fonctionnent ;
- les factures peuvent être payées ;
- les paiements automatiques sont contrôlés ;
- les recharges fonctionnent ;
- l’ajout d’argent fonctionne ;
- les Agents proches sont visibles ;
- le dépôt Agent est notifié ;
- le retrait Agent est sécurisé ;
- les GAB/DAB sont visibles ;
- les codes de retrait GAB sont générables ;
- le dépôt GAB est supportable ;
- les cartes physiques sont commandables ;
- les designs sont administrables ;
- le suivi de livraison fonctionne ;
- l’activation fonctionne ;
- les cartes virtuelles fonctionnent ;
- les cartes jetables sont supportables ;
- les cartes temporaires sont supportables ;
- les contrôles carte sont disponibles ;
- les limites carte sont configurables ;
- le blocage temporaire est immédiat ;
- l’opposition est définitive ;
- les Wallets Apple et Google sont supportables ;
- les abonnements sont détectables ;
- les coffres sont disponibles ;
- les règles d’épargne fonctionnent ;
- les coffres partagés sont supportables ;
- les budgets sont disponibles ;
- les alertes budgets fonctionnent ;
- l’analyse des dépenses est disponible ;
- les prévisions sont présentées comme estimations ;
- la fidélité est disponible ;
- le cashback est configurable ;
- les promotions sont administrables ;
- la carte des partenaires fonctionne ;
- les Agents et GAB possèdent une fiche ;
- les notifications sont centralisées ;
- les préférences sont disponibles ;
- le support est accessible ;
- les tickets sont créables ;
- les litiges sont gérés ;
- les remboursements sont suivis ;
- Jini est intégré ;
- Jini respecte les permissions ;
- les actions Jini exigent une confirmation ;
- le profil est modifiable ;
- le changement de numéro est sécurisé ;
- les documents sont accessibles ;
- le RIB peut être partagé ;
- les paramètres sont disponibles ;
- l’accessibilité est prise en charge ;
- la confidentialité est administrable ;
- les données peuvent être téléchargées ;
- la fermeture de compte est contrôlée ;
- les comptes suspendus sont gérés ;
- les comptes gelés sont gérés ;
- le Centre de sécurité est disponible ;
- les alertes de sécurité sont disponibles ;
- les appareils peuvent être révoqués ;
- le verrouillage automatique fonctionne ;
- root et jailbreak sont détectables ;
- le réseau faible est pris en charge ;
- le mode hors ligne est limité ;
- la synchronisation fonctionne ;
- les doubles opérations sont empêchées ;
- les timeouts sont vérifiés ;
- les deep links sont sécurisés ;
- les analytics sont définis ;
- les données sensibles sont exclues ;
- les crashes sont remontés ;
- les performances sont mesurées ;
- les contenus de notifications peuvent être masqués ;
- l’administration peut modifier les modules ;
- la segmentation fonctionne ;
- les campagnes in-app sont disponibles ;
- les expérimentations ne modifient pas les règles critiques ;
- les API sont définies ;
- les webhooks sont définis ;
- les rôles et permissions sont définis ;
- les approbations critiques sont protégées ;
- les audits sont immuables ;
- les tests couvrent les parcours fonctionnels, financiers, sécuritaires, hors ligne et d’accessibilité.
