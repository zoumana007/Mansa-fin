# 42 — Application Client Mansa : architecture, navigation, fonctionnalités, sécurité et expérience utilisateur

## 1. Objet du document

Ce document définit l’architecture officielle de l’application Client Mansa.

Il couvre :

- l’inscription ;
- la connexion ;
- l’authentification ;
- le KYC ;
- le profil ;
- le wallet ;
- les soldes ;
- les paiements ;
- les transferts ;
- les bénéficiaires ;
- les cartes ;
- les retraits ;
- les dépôts ;
- les reçus ;
- les budgets ;
- les coffres ;
- les abonnements ;
- les notifications ;
- le support ;
- Jini ;
- l’annuaire ;
- les services publics ;
- les paramètres ;
- la sécurité ;
- le mode hors ligne ;
- l’accessibilité ;
- les analytics ;
- les tests ;
- le multi-pays ;
- le multi-langues.

L’objectif est de fournir une application :

- moderne ;
- rapide ;
- claire ;
- sécurisée ;
- accessible ;
- personnalisable ;
- compatible avec des connexions faibles ;
- adaptée au Mali et à l’Afrique ;
- prête pour plusieurs pays ;
- capable de regrouper tous les services financiers de Mansa.

---

# 2. Principes fondamentaux

## 2.1 L’application ne décide pas des règles financières

L’application Client ne doit pas calculer seule :

- les frais officiels ;
- les plafonds ;
- les taux ;
- les droits ;
- les décisions KYC ;
- les décisions fraude ;
- les soldes officiels ;
- les statuts définitifs.

Elle affiche les décisions du backend.

---

## 2.2 La sécurité doit rester invisible autant que possible

La sécurité doit protéger l’utilisateur sans rendre l’application difficile à utiliser.

Elle doit combiner :

- appareil reconnu ;
- biométrie ;
- PIN ;
- OTP ;
- passkey ;
- analyse de risque ;
- confirmations adaptées.

---

## 2.3 L’utilisateur doit toujours comprendre son argent

Chaque opération doit montrer :

- montant ;
- frais ;
- devise ;
- destinataire ;
- délai ;
- statut ;
- référence ;
- reçu ;
- recours éventuel.

---

## 2.4 Aucun statut trompeur

Une opération ne doit jamais être affichée comme réussie tant que le backend ne l’a pas confirmée.

Statuts possibles :

- en préparation ;
- en attente ;
- en cours ;
- réussie ;
- échouée ;
- annulée ;
- remboursée ;
- partiellement remboursée ;
- vérification requise.

---

## 2.5 L’application doit fonctionner avec une connexion faible

Elle doit prévoir :

- cache ;
- reprise ;
- compression ;
- images optimisées ;
- faible consommation ;
- synchronisation ;
- messages clairs ;
- mode dégradé.

---

# 3. Technologie

Technologie principale recommandée :

```text
React Native
TypeScript
```

Composants possibles :

- React Navigation ;
- gestion d’état ;
- stockage sécurisé ;
- client API ;
- notifications Push ;
- biométrie native ;
- analytics ;
- crash reporting ;
- feature flags ;
- i18n.

---

# 4. Plateformes

L’application doit être disponible sur :

- Android ;
- iOS.

Une priorité peut être donnée à Android pour le marché malien, sans négliger iOS.

---

# 5. Architecture de l’application

Structure recommandée :

```text
src/
├── app/
├── navigation/
├── screens/
├── features/
│   ├── auth/
│   ├── onboarding/
│   ├── kyc/
│   ├── home/
│   ├── wallet/
│   ├── payments/
│   ├── transfers/
│   ├── cards/
│   ├── budgets/
│   ├── vaults/
│   ├── subscriptions/
│   ├── directory/
│   ├── public-services/
│   ├── support/
│   ├── jini/
│   └── settings/
├── components/
├── services/
├── store/
├── hooks/
├── theme/
├── localization/
├── security/
├── analytics/
├── storage/
└── utils/
```

---

# 6. Navigation principale

Navigation recommandée :

```text
Accueil
Paiements
Cartes
Hub
Profil
```

Les éléments peuvent évoluer selon :

- pays ;
- version ;
- fonctionnalité ;
- type de compte ;
- niveau KYC ;
- segment ;
- feature flag.

---

# 7. Accueil

L’écran d’accueil doit afficher :

- solde principal ;
- devise ;
- dernières opérations ;
- raccourcis ;
- cartes ;
- alertes ;
- objectifs ;
- dépenses ;
- promotions ;
- services ;
- notifications ;
- accès à Jini.

---

# 8. Solde

Le solde doit pouvoir être :

- visible ;
- masqué ;
- actualisé ;
- affiché par devise ;
- séparé par wallet ;
- distingué entre disponible et comptable si nécessaire.

---

# 9. Masquage du solde

L’utilisateur doit pouvoir masquer les montants.

Exemple :

```text
•••••• XOF
```

Le choix doit être mémorisé localement de manière sécurisée.

---

# 10. Raccourcis

Exemples :

- envoyer ;
- recevoir ;
- payer ;
- recharger ;
- retirer ;
- scanner ;
- carte ;
- facture ;
- coffre ;
- support.

Les raccourcis doivent être configurables.

---

# 11. Inscription

Le parcours peut demander :

- pays ;
- numéro de téléphone ;
- OTP ;
- identité ;
- code secret ;
- consentements ;
- langue ;
- appareil ;
- invitation éventuelle.

---

# 12. États d’inscription

- démarrée ;
- téléphone vérifié ;
- identité incomplète ;
- KYC en cours ;
- compte limité ;
- compte actif ;
- compte rejeté ;
- complément requis.

---

# 13. Connexion

Méthodes possibles :

- téléphone + PIN ;
- e-mail + mot de passe ;
- biométrie ;
- passkey ;
- appareil reconnu ;
- récupération sécurisée.

---

# 14. PIN

Le PIN doit être :

- localement protégé ;
- non journalisé ;
- limité en tentatives ;
- modifiable ;
- récupérable via un parcours renforcé ;
- distinct du PIN de carte.

---

# 15. Biométrie

L’application peut utiliser :

- Face ID ;
- Touch ID ;
- biométrie Android.

La donnée biométrique brute reste gérée par le système d’exploitation.

---

# 16. Gestion des appareils

L’utilisateur doit pouvoir consulter :

- appareil actuel ;
- appareils reconnus ;
- date de connexion ;
- ville approximative ;
- dernière activité ;
- statut ;
- révocation.

---

# 17. Nouvelle connexion

Lors d’une connexion inhabituelle, l’application peut demander :

- OTP ;
- confirmation sur appareil reconnu ;
- biométrie ;
- selfie ;
- vérification renforcée.

---

# 18. Récupération de compte

Le parcours doit prévenir :

- usurpation ;
- SIM swap ;
- récupération frauduleuse ;
- accès à un ancien numéro ;
- changement d’appareil suspect.

Il peut inclure :

- OTP ;
- document ;
- selfie ;
- preuve de vie ;
- délai de sécurité ;
- support.

---

# 19. KYC

Le parcours KYC doit être simple et progressif.

Étapes possibles :

1. informations personnelles ;
2. document ;
3. photo ;
4. preuve de vie ;
5. adresse ;
6. profession ;
7. source des fonds ;
8. validation.

---

# 20. Capture de document

L’application doit guider l’utilisateur :

- cadrage ;
- lumière ;
- netteté ;
- recto ;
- verso ;
- absence de reflet ;
- document complet ;
- format accepté.

---

# 21. Selfie

L’écran doit expliquer :

- pourquoi ;
- comment ;
- durée ;
- traitement ;
- protection ;
- possibilité de recommencer.

---

# 22. Suivi KYC

L’utilisateur doit voir :

- statut ;
- étape ;
- document reçu ;
- délai indicatif ;
- complément demandé ;
- motif compréhensible ;
- action suivante.

---

# 23. Profil

Le profil doit contenir :

- identité ;
- téléphone ;
- e-mail ;
- adresse ;
- pays ;
- langue ;
- profession ;
- niveau KYC ;
- préférences ;
- sécurité ;
- documents ;
- appareils.

---

# 24. Modification du profil

Les modifications simples peuvent être immédiates.

Les modifications sensibles peuvent exiger :

- OTP ;
- biométrie ;
- document ;
- délai ;
- revue ;
- confirmation.

---

# 25. Wallets

L’utilisateur peut posséder :

- wallet principal ;
- wallet secondaire ;
- wallet devise ;
- wallet professionnel ;
- wallet service public ;
- wallet épargne.

La disponibilité dépend du pays et du produit.

---

# 26. Paiement

Méthodes possibles :

- QR code ;
- lien ;
- TPE ;
- numéro ;
- identifiant ;
- commerce ;
- facture ;
- service public ;
- NFC lorsque disponible.

---

# 27. Écran de paiement

Avant confirmation, afficher :

- destinataire ;
- logo ;
- montant ;
- devise ;
- frais ;
- total ;
- source ;
- délai ;
- note ;
- référence ;
- bouton de confirmation.

---

# 28. Confirmation de paiement

La confirmation peut utiliser :

- PIN ;
- biométrie ;
- OTP ;
- passkey ;
- validation appareil.

Le niveau dépend du risque.

---

# 29. Reçu

Le reçu doit contenir :

- référence ;
- date ;
- montant ;
- frais ;
- devise ;
- destinataire ;
- émetteur ;
- statut ;
- mode de paiement ;
- QR de vérification éventuel.

---

# 30. Partage du reçu

L’utilisateur doit pouvoir :

- télécharger ;
- partager ;
- envoyer ;
- imprimer ;
- retrouver plus tard.

Les données sensibles doivent être masquées.

---

# 31. Transfert

Types possibles :

- Mansa vers Mansa ;
- Mansa vers banque ;
- banque vers Mansa ;
- Mansa vers Mobile Money ;
- Mobile Money vers Mansa ;
- transfert international ;
- transfert programmé.

---

# 32. Bénéficiaires

Un bénéficiaire peut être ajouté par :

- téléphone ;
- QR ;
- IBAN ;
- compte ;
- Mobile Money ;
- contact ;
- identifiant Mansa.

---

# 33. Vérification du bénéficiaire

L’application doit afficher :

- nom vérifié ;
- banque ;
- opérateur ;
- pays ;
- devise ;
- statut ;
- avertissement éventuel.

---

# 34. Nouveau bénéficiaire

Pour un nouveau bénéficiaire, une protection peut imposer :

- délai ;
- OTP ;
- biométrie ;
- limite temporaire ;
- confirmation supplémentaire ;
- notification.

---

# 35. Transfert programmé

L’utilisateur peut programmer :

- date ;
- fréquence ;
- montant ;
- bénéficiaire ;
- durée ;
- nombre d’occurrences ;
- rappel ;
- annulation.

---

# 36. Demande d’argent

L’utilisateur peut créer :

- demande simple ;
- lien ;
- QR ;
- partage ;
- montant fixe ;
- montant libre ;
- date d’expiration.

---

# 37. Paiement partagé

Fonctions possibles :

- diviser une dépense ;
- demander une part ;
- répartir également ;
- répartir manuellement ;
- suivre qui a payé ;
- relancer ;
- clôturer.

---

# 38. Groupe de paiement

Un groupe peut contenir :

- membres ;
- dépense ;
- parts ;
- statuts ;
- échéance ;
- messages ;
- justificatif.

---

# 39. Cartes

L’application doit gérer :

- carte physique ;
- carte virtuelle ;
- carte temporaire ;
- carte jetable ;
- carte enfant ;
- carte employé ;
- carte étudiante ;
- carte de fidélité.

---

# 40. Écran carte

Il peut afficher :

- visuel ;
- statut ;
- réseau ;
- type ;
- quatre derniers chiffres ;
- solde associé ;
- plafonds ;
- actions ;
- historique ;
- paramètres.

---

# 41. Données de carte

Les données sensibles doivent être protégées.

L’affichage du numéro complet peut exiger :

- biométrie ;
- PIN ;
- session récente ;
- masquage automatique ;
- délai court.

---

# 42. Actions carte

- activer ;
- geler ;
- dégeler ;
- changer plafond ;
- consulter PIN ;
- remplacer ;
- signaler perte ;
- gérer paiements en ligne ;
- gérer sans contact ;
- gérer retraits ;
- gérer pays.

---

# 43. Carte virtuelle

Elle peut être :

- permanente ;
- temporaire ;
- liée à un budget ;
- limitée à un marchand ;
- limitée à un montant ;
- limitée à une durée.

---

# 44. Carte jetable

Une carte jetable peut changer après chaque paiement en ligne réussi.

Elle dépend :

- du partenaire carte ;
- du réseau ;
- du pays ;
- du niveau KYC ;
- de la politique de risque.

---

# 45. Apple Wallet et Google Wallet

L’application peut permettre :

- ajout de carte ;
- vérification ;
- provisioning ;
- suspension ;
- retrait ;
- synchronisation de statut.

---

# 46. Dépôt d’argent

Méthodes possibles :

- carte bancaire ;
- virement ;
- Mobile Money ;
- agent ;
- dépôt partenaire ;
- salaire ;
- remboursement ;
- transfert interne.

---

# 47. Retrait

Méthodes possibles :

- Mobile Money ;
- banque ;
- agent ;
- distributeur ;
- TPE autorisé ;
- code de retrait.

---

# 48. Code de retrait

Un code de retrait doit être :

- temporaire ;
- limité ;
- unique ;
- annulable ;
- protégé ;
- lié à un montant ;
- traçable.

---

# 49. Historique

L’historique doit permettre :

- recherche ;
- filtre ;
- tri ;
- catégorie ;
- date ;
- montant ;
- statut ;
- devise ;
- partenaire ;
- export.

---

# 50. Détail transaction

L’écran doit afficher :

- référence ;
- montant ;
- frais ;
- total ;
- date ;
- statut ;
- origine ;
- destination ;
- catégorie ;
- reçu ;
- assistance ;
- contestation.

---

# 51. Contestation

L’utilisateur doit pouvoir signaler :

- transaction inconnue ;
- double débit ;
- montant incorrect ;
- retrait non reçu ;
- service non reçu ;
- remboursement manquant ;
- frais contesté.

---

# 52. Budgets

L’utilisateur peut créer des budgets par :

- catégorie ;
- semaine ;
- mois ;
- période ;
- carte ;
- wallet ;
- objectif ;
- montant.

---

# 53. Catégorisation

Exemples :

- alimentation ;
- transport ;
- logement ;
- loisirs ;
- santé ;
- études ;
- famille ;
- factures ;
- commerce ;
- autre.

---

# 54. Détection d’abonnements

L’application peut identifier :

- paiements récurrents ;
- abonnements ;
- échéances ;
- hausse de prix ;
- doublons ;
- services inutilisés.

---

# 55. Gestion des abonnements

L’utilisateur peut :

- consulter ;
- catégoriser ;
- recevoir un rappel ;
- masquer ;
- signaler ;
- lancer une résiliation assistée lorsque disponible.

---

# 56. Coffres

Un coffre permet de mettre de l’argent de côté.

Types possibles :

- urgence ;
- voyage ;
- études ;
- logement ;
- achat ;
- projet ;
- famille ;
- investissement futur.

---

# 57. Alimentation d’un coffre

Méthodes :

- manuelle ;
- automatique ;
- arrondi ;
- pourcentage ;
- montant périodique ;
- transfert entrant ;
- règle personnalisée.

---

# 58. Retrait d’un coffre

Selon le type :

- immédiat ;
- avec délai ;
- avec confirmation ;
- avec pénalité ;
- limité ;
- bloqué jusqu’à une date.

---

# 59. Objectifs

Un objectif doit afficher :

- montant cible ;
- montant actuel ;
- progression ;
- date ;
- rythme ;
- suggestion ;
- historique ;
- prochain versement.

---

# 60. Analyse des dépenses

L’application peut afficher :

- total mensuel ;
- catégories ;
- évolution ;
- comparaison ;
- dépenses inhabituelles ;
- revenus ;
- épargne ;
- abonnements ;
- prévisions.

---

# 61. Insights

Exemples :

- dépenses en hausse ;
- frais évitables ;
- abonnement doublé ;
- budget dépassé ;
- objectif en retard ;
- solde faible ;
- dépense inhabituelle.

---

# 62. Jini

Jini doit être accessible depuis :

- accueil ;
- transaction ;
- support ;
- budget ;
- carte ;
- profil ;
- centre d’aide.

---

# 63. Cas d’usage Jini

Jini peut :

- expliquer une transaction ;
- rechercher une opération ;
- aider à envoyer de l’argent ;
- expliquer les frais ;
- guider le KYC ;
- proposer un budget ;
- résumer les dépenses ;
- orienter vers le support.

---

# 64. Limites de Jini

Jini ne doit pas seul :

- exécuter un paiement sans confirmation ;
- modifier un solde ;
- débloquer un compte ;
- supprimer un bénéficiaire sensible ;
- afficher un secret ;
- prendre une décision réglementaire.

---

# 65. Hub / Annuaire

L’application peut intégrer :

- commerces ;
- services ;
- professionnels ;
- restaurants ;
- boutiques ;
- artisans ;
- transports ;
- écoles ;
- services publics ;
- promotions.

---

# 66. Recherche

Filtres possibles :

- proximité ;
- catégorie ;
- note ;
- prix ;
- ouvert ;
- livraison ;
- paiement Mansa ;
- promotion ;
- vérifié ;
- pays ;
- ville.

---

# 67. Fiche commerce

Elle peut afficher :

- nom ;
- photos ;
- description ;
- adresse ;
- horaires ;
- contact ;
- produits ;
- promotions ;
- avis ;
- moyens de paiement ;
- itinéraire ;
- bouton payer.

---

# 68. Géolocalisation

L’utilisateur doit pouvoir choisir :

- position précise ;
- position approximative ;
- ville manuelle ;
- aucune localisation.

---

# 69. Services publics

L’application peut permettre de payer :

- amendes ;
- taxes ;
- frais scolaires ;
- université ;
- documents administratifs ;
- eau ;
- électricité ;
- services municipaux.

---

# 70. Dossier public

Un service public doit afficher :

- institution ;
- référence ;
- montant ;
- motif ;
- date ;
- statut ;
- reçu officiel ;
- recours ;
- audit visible lorsque pertinent.

---

# 71. Bourses

L’application peut afficher :

- éligibilité ;
- statut ;
- montant ;
- date ;
- versement ;
- historique ;
- notification ;
- recours.

---

# 72. Carte étudiante

La carte étudiante numérique peut contenir :

- identité ;
- établissement ;
- année ;
- statut ;
- QR ;
- photo ;
- services ;
- paiements ;
- avantages.

---

# 73. Notifications

Types :

- paiement ;
- transfert ;
- carte ;
- sécurité ;
- KYC ;
- promotion ;
- budget ;
- coffre ;
- service public ;
- support ;
- système.

---

# 74. Centre de notifications

Fonctions :

- lire ;
- marquer ;
- filtrer ;
- archiver ;
- supprimer lorsque autorisé ;
- accéder à l’action ;
- gérer les préférences.

---

# 75. Notifications de sécurité

Elles ne doivent pas pouvoir être désactivées lorsqu’elles sont essentielles.

Exemples :

- nouvelle connexion ;
- changement de PIN ;
- nouveau bénéficiaire ;
- carte gelée ;
- paiement suspect ;
- récupération de compte.

---

# 76. Support

L’utilisateur doit pouvoir :

- consulter le centre d’aide ;
- parler à Jini ;
- créer un ticket ;
- joindre une preuve ;
- suivre le statut ;
- répondre ;
- contester ;
- demander un rappel ;
- évaluer la réponse.

---

# 77. Création de ticket

Le formulaire peut préremplir :

- utilisateur ;
- transaction ;
- appareil ;
- version ;
- pays ;
- catégorie ;
- référence ;
- logs techniques limités.

---

# 78. Paramètres

Catégories :

- profil ;
- sécurité ;
- confidentialité ;
- notifications ;
- langue ;
- apparence ;
- appareils ;
- documents ;
- limites ;
- pays ;
- aide ;
- légal ;
- fermeture du compte.

---

# 79. Apparence

Options possibles :

- clair ;
- sombre ;
- système ;
- taille de texte ;
- contraste ;
- animations réduites.

---

# 80. Langues

L’application doit être préparée pour :

- français ;
- bambara ;
- anglais ;
- autres langues selon pays.

Les textes ne doivent pas être codés en dur.

---

# 81. Accessibilité

L’application doit prendre en charge :

- lecteur d’écran ;
- contraste ;
- taille de texte ;
- navigation claire ;
- boutons suffisamment grands ;
- retour haptique ;
- réduction des animations ;
- langage simple.

---

# 82. Connexion faible

Mesures :

- chargement progressif ;
- skeletons ;
- cache ;
- reprise ;
- compression ;
- réduction d’images ;
- affichage de l’état réseau ;
- mise en attente contrôlée.

---

# 83. Mode hors ligne

Le mode hors ligne peut permettre :

- consultation de données mises en cache ;
- accès aux reçus récents ;
- préparation d’une opération ;
- consultation du profil ;
- centre d’aide local.

Il ne doit pas confirmer une opération financière non envoyée.

---

# 84. Synchronisation

À la reconnexion :

- vérifier la session ;
- actualiser les statuts ;
- envoyer les actions autorisées ;
- éviter les doublons ;
- appliquer l’idempotence ;
- informer l’utilisateur.

---

# 85. Stockage local

Le stockage local doit distinguer :

- données publiques ;
- cache ;
- préférences ;
- tokens ;
- secrets ;
- données temporaires.

Les secrets doivent utiliser un stockage sécurisé.

---

# 86. Données interdites en local

Ne pas stocker en clair :

- mot de passe ;
- PIN ;
- CVV ;
- OTP ;
- numéro complet de carte ;
- document complet ;
- clé privée ;
- secret partenaire.

---

# 87. Sécurité de l’application

Mesures possibles :

- détection root ;
- détection jailbreak ;
- protection capture d’écran sur certains écrans ;
- obfuscation ;
- certificate pinning lorsque pertinent ;
- anti-tampering ;
- intégrité appareil ;
- verrouillage automatique.

---

# 88. Sessions

La session doit gérer :

- expiration ;
- inactivité ;
- refresh ;
- révocation ;
- appareil ;
- risque ;
- fermeture distante ;
- reconnexion.

---

# 89. Verrouillage automatique

L’application peut se verrouiller après :

- inactivité ;
- passage en arrière-plan ;
- changement d’appareil ;
- risque ;
- action sensible.

---

# 90. Captures d’écran

Elles peuvent être bloquées sur :

- PIN ;
- données carte ;
- documents KYC ;
- secrets ;
- récupération de compte.

---

# 91. Deep Links

Les liens profonds doivent être sécurisés.

Ils peuvent ouvrir :

- paiement ;
- demande ;
- commerce ;
- promotion ;
- ticket ;
- KYC ;
- reçu ;
- carte.

Ils ne doivent pas exécuter automatiquement une action financière.

---

# 92. QR codes

Le scanner doit vérifier :

- format ;
- signature ;
- expiration ;
- destinataire ;
- montant ;
- pays ;
- environnement ;
- risque.

---

# 93. États d’écran

Chaque écran doit gérer :

- chargement ;
- succès ;
- vide ;
- erreur ;
- hors ligne ;
- accès refusé ;
- fonctionnalité indisponible ;
- maintenance ;
- complément requis.

---

# 94. Messages d’erreur

Ils doivent être :

- compréhensibles ;
- actionnables ;
- sans détail technique ;
- liés à un code stable ;
- traduits ;
- adaptés au contexte.

---

# 95. Maintenance

L’application doit pouvoir afficher :

- maintenance globale ;
- maintenance d’un service ;
- maintenance d’un partenaire ;
- indisponibilité d’un pays ;
- durée estimée ;
- alternative ;
- statut.

---

# 96. Feature Flags

Fonctions activables :

- carte virtuelle ;
- paiement QR ;
- NFC ;
- coffre ;
- budget ;
- Jini ;
- Hub ;
- service public ;
- transfert international ;
- carte étudiante.

---

# 97. Mises à jour

L’application doit distinguer :

- mise à jour facultative ;
- mise à jour recommandée ;
- mise à jour obligatoire ;
- version bloquée ;
- version vulnérable.

---

# 98. Compatibilité backend

L’application doit envoyer :

- version application ;
- version OS ;
- type appareil ;
- version API ;
- pays ;
- environnement ;
- capacités.

---

# 99. Analytics

Événements possibles :

```text
client_app_opened
client_registration_started
client_registration_completed
client_login_completed
client_kyc_started
client_kyc_completed
client_payment_started
client_payment_completed
client_transfer_started
client_transfer_completed
client_card_opened
client_card_frozen
client_budget_created
client_vault_created
client_support_ticket_created
client_jini_opened
client_directory_search_completed
client_public_service_payment_completed
```

---

# 100. Données analytics interdites

Ne pas transmettre :

- PIN ;
- OTP ;
- CVV ;
- numéro complet de carte ;
- mot de passe ;
- document complet ;
- contenu sensible non nécessaire ;
- données biométriques brutes.

---

# 101. Crash reporting

Un crash doit enregistrer :

- version ;
- appareil ;
- OS ;
- écran ;
- contexte technique ;
- stack filtrée ;
- date ;
- corrélation éventuelle.

Il ne doit pas inclure de données financières sensibles.

---

# 102. Performance

Objectifs :

- ouverture rapide ;
- navigation fluide ;
- faible consommation mémoire ;
- faible consommation batterie ;
- faible consommation de données ;
- réponse claire sur réseau faible.

---

# 103. Tests unitaires

Ils doivent couvrir :

- formats ;
- validations ;
- calculs d’affichage ;
- stores ;
- hooks ;
- permissions ;
- navigation ;
- transformations.

---

# 104. Tests d’intégration

Ils doivent couvrir :

- API ;
- stockage ;
- authentification ;
- KYC ;
- paiement ;
- transfert ;
- cartes ;
- notifications ;
- support ;
- Jini.

---

# 105. Tests end-to-end

Parcours principaux :

1. inscription ;
2. KYC ;
3. connexion ;
4. dépôt ;
5. paiement ;
6. transfert ;
7. carte ;
8. remboursement ;
9. support ;
10. clôture.

---

# 106. Tests appareils

Tester :

- Android faible ;
- Android récent ;
- iPhone ancien compatible ;
- iPhone récent ;
- petits écrans ;
- grands écrans ;
- faible mémoire ;
- réseau lent ;
- hors ligne.

---

# 107. Tests de sécurité

- stockage sécurisé ;
- biométrie ;
- session ;
- deep links ;
- QR ;
- root ;
- jailbreak ;
- capture d’écran ;
- logs ;
- permissions ;
- appareil compromis.

---

# 108. Tests d’accessibilité

- lecteur d’écran ;
- contraste ;
- taille de texte ;
- navigation ;
- labels ;
- focus ;
- animations réduites ;
- zones tactiles.

---

# 109. Permissions mobiles

L’application peut demander :

- caméra ;
- notifications ;
- localisation ;
- contacts ;
- biométrie ;
- fichiers.

Chaque permission doit être :

- justifiée ;
- demandée au bon moment ;
- refusée sans bloquer inutilement ;
- expliquée ;
- révocable.

---

# 110. Déploiement mobile

Le processus doit inclure :

- build ;
- signature ;
- tests ;
- scan ;
- environnement ;
- distribution interne ;
- bêta ;
- store ;
- rollout progressif ;
- monitoring ;
- rollback par version ou feature flag.

---

# 111. App Store et Play Store

Chaque publication doit contenir :

- version ;
- notes ;
- captures ;
- politique ;
- permissions ;
- classification ;
- pays ;
- langues ;
- support ;
- confidentialité.

---

# 112. Bêta interne

La bêta peut concerner :

- équipe ;
- testeurs ;
- banque partenaire ;
- commerçants pilotes ;
- institutions ;
- utilisateurs volontaires.

---

# 113. Rollout progressif

Exemple :

```text
1 %
5 %
10 %
25 %
50 %
100 %
```

La progression dépend :

- crashs ;
- erreurs ;
- paiements ;
- performance ;
- support ;
- fraude ;
- avis.

---

# 114. Administration

Le portail Admin doit permettre de gérer :

- versions ;
- feature flags ;
- maintenance ;
- messages ;
- pays ;
- langues ;
- campagnes ;
- limites ;
- stores ;
- compatibilité ;
- analytics ;
- incidents ;
- versions bloquées.

---

# 115. Permissions

Exemples :

```text
client.configuration.read
client.configuration.manage
client.feature.read
client.feature.manage
client.version.read
client.version.manage
client.maintenance.manage
client.notification.manage
client.analytics.read
client.release.approve
client.audit.read
```

---

# 116. Actions critiques

Doivent être protégées :

- blocage d’une version ;
- activation d’une fonction financière ;
- modification globale de navigation ;
- changement d’API ;
- activation d’un pays ;
- message de sécurité ;
- mise à jour obligatoire ;
- activation d’un partenaire ;
- modification d’un plafond visible.

---

# 117. Double validation

Peut être exigée pour :

- publication production ;
- mise à jour obligatoire ;
- activation carte ;
- activation paiement ;
- nouveau pays ;
- nouveau partenaire financier ;
- changement de sécurité ;
- désactivation globale ;
- modification de KYC.

---

# 118. Modèles

- ClientApplication
- ClientApplicationVersion
- ClientDevice
- ClientSession
- ClientPreference
- ClientNavigationConfiguration
- ClientFeatureFlag
- ClientHomeConfiguration
- ClientQuickAction
- ClientNotificationPreference
- ClientOfflineState
- ClientSecurityState
- ClientRelease
- ClientStorePublication
- ClientCrashReport
- ClientAnalyticsEvent
- ClientAudit

---

# 119. Règles métier

1. L’application ne calcule pas le solde officiel.
2. Toute opération financière est confirmée par le backend.
3. Les statuts sont affichés fidèlement.
4. Les frais sont visibles avant validation.
5. Les données sensibles sont masquées.
6. Le PIN applicatif est distinct du PIN carte.
7. Les tokens sont stockés de manière sécurisée.
8. Les appareils sont gérables par l’utilisateur.
9. Les connexions inhabituelles déclenchent une vérification.
10. Le KYC est progressif.
11. Les paiements exigent une confirmation.
12. Les bénéficiaires sont vérifiés.
13. Les reçus restent accessibles.
14. Les remboursements référencent la transaction d’origine.
15. Les cartes peuvent être gelées immédiatement.
16. Les budgets et coffres sont configurables.
17. Jini reste soumis aux permissions.
18. Le mode hors ligne ne confirme pas de paiement.
19. La synchronisation est idempotente.
20. Les textes sont traduisibles.
21. L’accessibilité est intégrée.
22. Les permissions mobiles sont demandées au bon moment.
23. Les analytics excluent les secrets.
24. Les versions peuvent être bloquées.
25. Les actions critiques sont auditables.

---

# 120. Critères d’acceptation

L’application Client est validée lorsque :

- l’inscription fonctionne ;
- la connexion est sécurisée ;
- les appareils sont gérés ;
- le KYC est complet ;
- l’accueil affiche les données essentielles ;
- les soldes sont correctement présentés ;
- les paiements sont confirmés par le backend ;
- les transferts sont sécurisés ;
- les bénéficiaires sont vérifiés ;
- les cartes sont administrables ;
- les reçus sont disponibles ;
- les contestations sont accessibles ;
- les budgets et coffres fonctionnent ;
- les abonnements sont détectables ;
- Jini est intégré ;
- le Hub est accessible ;
- les services publics sont disponibles selon le pays ;
- les notifications sont gérées ;
- le support est intégré ;
- le mode réseau faible est pris en charge ;
- les données locales sont protégées ;
- les langues sont configurables ;
- l’accessibilité est testée ;
- les versions sont administrables ;
- les tests couvrent les parcours critiques.
