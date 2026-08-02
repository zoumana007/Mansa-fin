# Carte complète des produits, applications, interfaces, modules et API Mansa

## 1. Rôle du document

Ce document constitue l’inventaire fonctionnel officiel de Mansa.

Il sert à :

- recenser toutes les applications ;
- recenser toutes les interfaces web ;
- recenser tous les utilisateurs ;
- recenser tous les modules ;
- recenser les grandes familles d’API ;
- identifier les dépendances entre produits ;
- éviter l’oubli d’une fonctionnalité pendant le développement ;
- guider Codex, les développeurs, les designers et les équipes produit ;
- vérifier la couverture du projet avant chaque mise en production.

Il ne remplace pas les spécifications détaillées de chaque module. Il sert de carte générale et de liste de contrôle.

Le dépôt officiel unique du projet est `mansa-fin`.

---

## 2. Produits officiels de Mansa

L’écosystème comprend cinq applications mobiles principales, trois interfaces web et un socle technique commun.

### Applications mobiles

1. Mansa Client  
2. Mansa Commerce  
3. Mansa TPE  
4. Mansa Admin Lite  
5. Mansa Annuaire / Hub  

### Interfaces web

6. Site public officiel Mansa  
7. Site Mansa Professionnels  
8. Portail Mansa Admin Web  

### Socle commun

9. Backend et API Gateway  
10. Services IA Jini  
11. Packages partagés  
12. Base de données et modèles Prisma  
13. Infrastructure, sécurité, CI/CD et observabilité  

---

# 3. Application mobile Mansa Client

## 3.1 Utilisateurs concernés

- particuliers ;
- étudiants ;
- jeunes utilisateurs ;
- parents et responsables légaux ;
- salariés ;
- bénéficiaires d’aides ;
- clients de commerçants ;
- utilisateurs de services publics ;
- investisseurs autorisés ;
- membres de familles, groupes et associations.

## 3.2 Onboarding et création de compte

- sélection du pays ;
- langue ;
- numéro de téléphone ;
- e-mail ;
- OTP ;
- création du PIN ;
- mot de passe lorsque nécessaire ;
- acceptation des conditions ;
- consentements ;
- création de l’identifiant Mansa ;
- import facultatif des contacts ;
- configuration initiale ;
- invitation par parrainage ;
- détection d’un compte existant ;
- reprise d’un onboarding interrompu ;
- mode démonstration lorsque activé.

## 3.3 Authentification et sécurité

- connexion par téléphone ;
- connexion par e-mail ;
- PIN ;
- biométrie ;
- OTP ;
- passkeys ;
- double authentification ;
- appareil de confiance ;
- approbation d’un nouvel appareil ;
- récupération de compte ;
- réinitialisation du PIN ;
- réinitialisation du mot de passe ;
- changement de téléphone ;
- changement d’e-mail ;
- gestion des sessions ;
- fermeture de toutes les sessions ;
- bouton d’urgence ;
- verrouillage temporaire ;
- détection d’activité suspecte ;
- centre de sécurité ;
- codes de récupération ;
- contacts de récupération.

## 3.4 KYC et identité

- identité légale ;
- identité publique ;
- nom affiché ;
- identifiant unique Mansa ;
- documents d’identité ;
- selfie ;
- preuve de vie ;
- adresse ;
- nationalité ;
- date de naissance ;
- niveau KYC ;
- revue manuelle ;
- rejet et reprise ;
- expiration des documents ;
- mise à jour des informations ;
- statut vérifié ;
- badges ;
- historique des modifications ;
- protection contre l’usurpation.

## 3.5 Profil utilisateur

- photo ;
- nom public ;
- identifiant Mansa ;
- biographie ;
- pays ;
- ville facultative ;
- QR personnel ;
- lien de profil ;
- badge ;
- confidentialité ;
- visibilité ;
- favoris ;
- contacts ;
- blocage ;
- signalement ;
- statut en ligne ;
- préférences de communication ;
- export des données ;
- fermeture du compte.

## 3.6 Accueil et tableau de bord

- solde global ;
- solde disponible ;
- comptes ;
- cartes ;
- actions rapides ;
- transactions récentes ;
- alertes ;
- widgets ;
- Mansa Connect ;
- Jini ;
- promotions ;
- services publics ;
- fidélité ;
- investissements ;
- objectifs ;
- budgets ;
- coffres ;
- abonnements ;
- documents ;
- recherche universelle ;
- personnalisation de l’ordre ;
- mode compact ;
- mode faible connexion ;
- mode hors ligne limité.

## 3.7 Comptes et wallets

- compte principal ;
- compte d’épargne ;
- compte professionnel associé ;
- compte enfant ;
- compte étudiant ;
- compte investissement ;
- compte multi-devises ;
- comptes XOF, EUR, USD et autres devises autorisées ;
- soldes ;
- solde bloqué ;
- solde disponible ;
- historique ;
- renommage ;
- compte favori ;
- compte par défaut ;
- coordonnées bancaires ;
- RIB ou IBAN lorsque disponible ;
- relevés ;
- export ;
- limites ;
- blocage ;
- gel ;
- clôture.

## 3.8 Transactions

- historique complet ;
- recherche ;
- filtres ;
- catégories ;
- statuts ;
- reçu ;
- justificatif ;
- note ;
- pièce jointe ;
- favori ;
- remboursement ;
- contestation ;
- signalement ;
- export PDF ;
- export CSV ;
- export Excel ;
- regroupement par période ;
- regroupement par commerçant ;
- regroupement par catégorie ;
- transactions programmées ;
- transactions récurrentes ;
- abonnements détectés ;
- score de risque ;
- audit.

## 3.9 Envoi d’argent

- utilisateur Mansa ;
- identifiant Mansa ;
- contact téléphonique ;
- bénéficiaire enregistré ;
- compte bancaire ;
- Mobile Money ;
- QR ;
- NFC ;
- commerçant ;
- organisme public ;
- conversation Mansa Connect ;
- paiement programmé ;
- paiement récurrent ;
- conversion de devise ;
- paiement international ;
- note ;
- pièce jointe ;
- validation biométrique ;
- contrôle de plafond ;
- contrôle de fraude ;
- reçu ;
- notification ;
- annulation lorsque autorisée.

## 3.10 Demande d’argent

- demande individuelle ;
- demande de groupe ;
- demande depuis une conversation ;
- demande par QR ;
- demande par NFC ;
- paiement partiel ;
- date limite ;
- expiration ;
- rappels ;
- refus ;
- annulation ;
- renouvellement ;
- partage de facture ;
- division égale ;
- division personnalisée ;
- suivi des participants ;
- historique ;
- notifications.

## 3.11 Mansa Connect

- conversation privée ;
- conversation de groupe ;
- conversation commerçant ;
- conversation entreprise ;
- conversation institutionnelle ;
- conversation support ;
- conversation Jini ;
- texte ;
- emoji ;
- images ;
- vidéos ;
- audio ;
- documents ;
- PDF ;
- localisation ;
- contacts ;
- reçus ;
- QR ;
- cartes financières interactives ;
- envoi d’argent dans le chat ;
- demande d’argent dans le chat ;
- paiements fractionnés ;
- groupes financiers ;
- cagnottes ;
- dépenses partagées ;
- réactions ;
- réponses ;
- transfert de message ;
- modification limitée ;
- suppression ;
- messages éphémères ;
- verrouillage d’une conversation ;
- recherche ;
- statut de lecture ;
- indicateur de saisie ;
- appels audio et vidéo lorsque activés ;
- blocage ;
- signalement ;
- anti-spam ;
- synchronisation multi-appareils.

## 3.12 Cartes

- carte physique standard ;
- carte premium ;
- carte metal ;
- carte jeune ;
- carte étudiant ;
- carte professionnelle ;
- carte entreprise ;
- carte multi-devises ;
- carte virtuelle permanente ;
- carte virtuelle temporaire ;
- carte virtuelle jetable ;
- carte limitée à un commerçant ;
- carte limitée à un montant ;
- carte limitée à un pays ;
- carte événementielle ;
- activation ;
- blocage ;
- déblocage ;
- opposition ;
- remplacement ;
- perte ;
- vol ;
- personnalisation ;
- design ;
- plafonds ;
- paiements en ligne ;
- paiements internationaux ;
- retraits ;
- sans contact ;
- CVV dynamique ;
- consultation sécurisée du PIN ;
- Apple Wallet ;
- Google Wallet ;
- appareils associés ;
- historique ;
- alertes ;
- contrôle parental.

## 3.13 QR Code

- QR profil ;
- QR paiement ;
- QR demande d’argent ;
- QR conversation ;
- QR commerçant ;
- QR facture ;
- QR produit ;
- QR temporaire ;
- QR à usage unique ;
- QR dynamique ;
- QR événement ;
- QR de groupe ;
- QR de cagnotte ;
- QR signé ;
- expiration ;
- historique ;
- détection du type de QR ;
- protection contre la falsification ;
- confirmation obligatoire avant paiement.

## 3.14 NFC

- paiement NFC ;
- partage de profil ;
- ouverture de conversation ;
- demande d’argent ;
- partage de bénéficiaire ;
- carte multiservices ;
- carte étudiante ;
- badge entreprise ;
- contrôle d’accès ;
- cantine ;
- bibliothèque ;
- parking ;
- pointage ;
- transport futur ;
- avantages salariés ;
- fidélité ;
- validation côté serveur ;
- révocation ;
- historique ;
- anti-clonage lorsque le matériel le permet.

## 3.15 Mobile Money

- liaison d’un compte Mobile Money ;
- dépôt ;
- retrait ;
- transfert ;
- recharge ;
- paiement ;
- historique ;
- frais ;
- limites ;
- statut ;
- réconciliation ;
- gestion multi-opérateurs ;
- intégration Orange Money et autres partenaires autorisés ;
- notifications ;
- erreurs partenaires ;
- reprise après interruption.

## 3.16 Coffres et épargne

- coffre libre ;
- coffre objectif ;
- coffre urgence ;
- coffre études ;
- coffre voyage ;
- coffre logement ;
- coffre santé ;
- coffre enfant ;
- coffre projet ;
- coffre investissement ;
- montant cible ;
- date cible ;
- versement manuel ;
- versement automatique ;
- arrondi intelligent ;
- contribution depuis le salaire ;
- verrouillage ;
- délai de retrait ;
- récompense ;
- prévision Jini ;
- statistiques ;
- historique ;
- notifications.

## 3.17 Budgets

- budget global ;
- budget mensuel ;
- budget hebdomadaire ;
- budget annuel ;
- budget par catégorie ;
- budget voyage ;
- budget étudiant ;
- budget famille ;
- budget projet ;
- seuils ;
- alertes ;
- prévisions ;
- recommandations Jini ;
- catégorisation automatique ;
- correction manuelle ;
- dépenses récurrentes ;
- graphiques ;
- comparaisons ;
- export ;
- modèles administrables.

## 3.18 Abonnements

- détection automatique ;
- liste des abonnements ;
- prochaine échéance ;
- variation de prix ;
- alerte ;
- historique ;
- catégorie ;
- moyen de paiement ;
- suspension de carte ;
- aide à la résiliation lorsque le partenaire le permet ;
- analyse Jini ;
- abonnements oubliés ;
- regroupement des coûts.

## 3.19 Fidélité et récompenses

- points ;
- cashback ;
- coupons ;
- bons d’achat ;
- offres personnalisées ;
- niveaux ;
- badges ;
- récompenses commerçants ;
- récompenses partenaires ;
- historique ;
- expiration ;
- transfert éventuel ;
- règles par pays ;
- campagnes ;
- portefeuille de fidélité universel.

## 3.20 Centre familial et comptes jeunes

- création d’un profil jeune ;
- parent ou responsable ;
- plafond ;
- catégories autorisées ;
- commerçants interdits ;
- notifications ;
- carte jeune ;
- argent de poche ;
- objectifs ;
- épargne ;
- validation parentale ;
- contrôle des dépenses ;
- confidentialité adaptée ;
- retrait du contrôle à la majorité selon la réglementation.

## 3.21 Cagnottes et groupes financiers

- cagnotte privée ;
- cagnotte publique ;
- objectif ;
- échéance ;
- participants ;
- lien ;
- QR ;
- contribution ;
- remboursement ;
- retrait ;
- administrateurs ;
- règles de dépense ;
- historique ;
- pièces justificatives ;
- alertes ;
- partage dans Mansa Connect.

## 3.22 Tontines

- création ;
- membres ;
- calendrier ;
- cotisation ;
- ordre de bénéficiaires ;
- rappels ;
- pénalités configurables ;
- historique ;
- validation ;
- transparence ;
- reçus ;
- litiges ;
- règles locales ;
- administration ;
- audit.

## 3.23 Investissements

Lorsque les autorisations et partenaires nécessaires sont disponibles :

- catalogue de produits ;
- projets ;
- levées de fonds ;
- profil de risque ;
- questionnaire ;
- portefeuille ;
- souscription ;
- versement ;
- rendement ;
- retrait ;
- documents ;
- avertissements ;
- suivi ;
- historique ;
- fiscalité ;
- reporting ;
- alertes ;
- validation réglementaire.

## 3.24 Services publics

- amendes ;
- taxes ;
- factures publiques ;
- scolarité ;
- bourses ;
- aides ;
- documents administratifs ;
- cartes étudiantes ;
- paiements ;
- reçus ;
- suivi de dossier ;
- notifications ;
- vérification d’une référence ;
- QR public ;
- identification d’un agent ;
- traçabilité anti-corruption ;
- contestation ;
- remboursement selon les règles.

## 3.25 Documents et coffre-fort numérique

- reçus ;
- factures ;
- relevés ;
- contrats ;
- garanties ;
- documents KYC ;
- carte d’identité ;
- passeport ;
- permis ;
- diplômes ;
- assurances ;
- export ;
- partage sécurisé ;
- expiration ;
- rappel ;
- signature électronique future ;
- classement ;
- recherche ;
- chiffrement ;
- suppression selon les obligations légales.

## 3.26 Notifications

- push ;
- SMS ;
- e-mail ;
- notification interne ;
- sécurité ;
- paiement ;
- carte ;
- transfert ;
- messagerie ;
- demande d’argent ;
- budget ;
- coffre ;
- abonnement ;
- fidélité ;
- service public ;
- investissement ;
- document ;
- maintenance ;
- promotion ;
- préférences par catégorie ;
- alertes critiques non désactivables.

## 3.27 Assistant IA Jini

- support ;
- recherche universelle ;
- explication des dépenses ;
- résumé financier ;
- conseils d’épargne ;
- prévisions budgétaires ;
- détection d’abonnement ;
- anomalie ;
- catégorisation ;
- assistance à la navigation ;
- aide aux formulaires ;
- recommandations ;
- voix ;
- contexte utilisateur contrôlé ;
- historique ;
- consentement ;
- limitations ;
- aucun transfert ou blocage critique autonome sans confirmation.

---

# 4. Application mobile Mansa Commerce

## 4.1 Onboarding professionnel

- création d’entreprise ;
- KYB ;
- documents ;
- représentant légal ;
- secteur ;
- établissements ;
- coordonnées ;
- compte de règlement ;
- fiscalité ;
- abonnement ;
- validation ;
- équipe ;
- permissions ;
- configuration guidée.

## 4.2 Tableau de bord

- chiffre d’affaires ;
- ventes ;
- panier moyen ;
- remboursements ;
- clients ;
- produits ;
- stocks ;
- alertes ;
- performances ;
- établissements ;
- employés ;
- commissions ;
- abonnements ;
- promotions ;
- rendez-vous ;
- statistiques ;
- recommandations Jini.

## 4.3 Établissements

- plusieurs boutiques ;
- agences ;
- restaurants ;
- pharmacies ;
- salons ;
- hôtels ;
- écoles ;
- entreprises ;
- points de vente ;
- adresses ;
- horaires ;
- employés ;
- terminaux ;
- catalogue ;
- stocks ;
- compte de règlement ;
- taxes ;
- paramètres distincts.

## 4.4 Employés et permissions

- création d’employé ;
- invitation ;
- rôles ;
- caissier ;
- vendeur ;
- manager ;
- comptable ;
- administrateur ;
- permissions détaillées ;
- horaires ;
- pointage ;
- établissements autorisés ;
- limites de remboursement ;
- validation hiérarchique ;
- désactivation ;
- audit.

## 4.5 Catalogue

- produits ;
- services ;
- variantes ;
- options ;
- prix ;
- taxes ;
- photos ;
- vidéos ;
- catégories ;
- collections ;
- disponibilité ;
- produits composés ;
- produits au poids ;
- services sur rendez-vous ;
- import ;
- export ;
- archivage ;
- synchronisation TPE ;
- synchronisation mini-site.

## 4.6 Stocks et inventaires

- stock par établissement ;
- mouvements ;
- entrées ;
- sorties ;
- transfert ;
- inventaire ;
- correction ;
- casse ;
- perte ;
- seuil minimum ;
- alerte ;
- fournisseur ;
- coût d’achat ;
- lot ;
- numéro de série ;
- date d’expiration ;
- traçabilité ;
- export ;
- historique.

## 4.7 Fournisseurs

- fiches ;
- contacts ;
- commandes ;
- factures ;
- livraisons ;
- dettes ;
- paiements ;
- historique ;
- notation interne ;
- documents ;
- produits associés.

## 4.8 Ventes et caisse

- panier ;
- scan ;
- recherche produit ;
- quantité ;
- remise ;
- taxe ;
- pourboire ;
- paiement fractionné ;
- plusieurs moyens de paiement ;
- reçu ;
- facture ;
- client ;
- vendeur ;
- caisse ;
- ouverture ;
- fermeture ;
- différence de caisse ;
- annulation ;
- remboursement ;
- audit.

## 4.9 Clients et CRM

- profil client ;
- historique ;
- notes ;
- segments ;
- fidélité ;
- préférences ;
- consentements ;
- campagnes ;
- anniversaires ;
- recommandations ;
- relances ;
- litiges ;
- support ;
- données exportables.

## 4.10 Factures et documents

- devis ;
- facture ;
- avoir ;
- bon de commande ;
- bon de livraison ;
- reçu ;
- garantie ;
- contrat ;
- modèles ;
- logo ;
- couleurs ;
- taxes ;
- numérotation ;
- PDF ;
- e-mail ;
- impression ;
- signature ;
- archive ;
- export comptable.

## 4.11 Retours, échanges et remboursements

- retour complet ;
- retour partiel ;
- échange ;
- avoir ;
- remboursement ;
- contrôle de délai ;
- motif ;
- preuve ;
- état du produit ;
- approbation ;
- remise en stock ;
- historique ;
- notification client ;
- litige.

## 4.12 Promotions

- pourcentage ;
- montant fixe ;
- lot ;
- deuxième produit ;
- code promo ;
- QR promo ;
- période ;
- quantité ;
- segment client ;
- établissement ;
- canal ;
- limite d’utilisation ;
- cumul ;
- approbation ;
- statistiques.

## 4.13 Fidélité

- points ;
- niveaux ;
- cashback ;
- coupons ;
- récompenses ;
- parrainage ;
- anniversaire ;
- règles ;
- expiration ;
- campagnes ;
- synchronisation Mansa Client ;
- reporting.

## 4.14 Rendez-vous et réservations

- calendrier ;
- services ;
- employés ;
- horaires ;
- ressources ;
- créneaux ;
- acompte ;
- annulation ;
- rappel ;
- liste d’attente ;
- réservation depuis le Hub ;
- confirmation ;
- historique ;
- absence ;
- statistiques.

## 4.15 Mini-site professionnel

- domaine ou sous-domaine ;
- logo ;
- bannière ;
- couleurs ;
- description ;
- horaires ;
- équipe ;
- produits ;
- services ;
- prix ;
- promotions ;
- avis ;
- galerie ;
- contact ;
- WhatsApp ;
- rendez-vous ;
- réservation ;
- paiement ;
- SEO ;
- analytics ;
- contenu administrable.

## 4.16 Étiquettes et codes

- code-barres ;
- QR produit ;
- étiquette prix ;
- étiquette rayon ;
- étiquette logistique ;
- origine ;
- recyclage ;
- mentions légales ;
- lot ;
- expiration ;
- modèle ;
- impression ;
- format ;
- imprimante ;
- génération en masse.

## 4.17 Imprimantes

- imprimante intégrée au TPE ;
- Bluetooth ;
- Wi-Fi ;
- USB ;
- réseau ;
- format ticket ;
- format A4 ;
- test ;
- statut ;
- file d’impression ;
- réimpression ;
- modèles ;
- logo ;
- QR ;
- duplication.

## 4.18 Analytics professionnels

- ventes ;
- revenus ;
- marge ;
- taxes ;
- panier moyen ;
- produits ;
- catégories ;
- employés ;
- établissements ;
- clients ;
- promotions ;
- remboursements ;
- stocks ;
- prévisions ;
- export ;
- comparaison ;
- tableaux personnalisés.

---

# 5. Application Mansa TPE

## 5.1 Terminal et activation

- identification du terminal ;
- association à l’entreprise ;
- association à l’établissement ;
- environnement Démo ;
- environnement Recette ;
- environnement Production ;
- activation ;
- clé ;
- certificat ;
- version ;
- contrôle d’intégrité ;
- blocage ;
- mise à jour.

## 5.2 Encaissement

- saisie libre ;
- catalogue ;
- scan ;
- panier ;
- remise ;
- taxe ;
- pourboire ;
- référence ;
- client ;
- paiement ;
- confirmation ;
- reçu ;
- impression ;
- nouvelle vente.

## 5.3 Moyens de paiement

- carte ;
- puce ;
- sans contact ;
- NFC ;
- QR ;
- Mobile Money ;
- Tap to Phone ;
- lien de paiement ;
- espèces enregistrées ;
- paiement mixte ;
- paiement fractionné ;
- paiement à plusieurs personnes.

## 5.4 Gestion du panier

- ajout ;
- suppression ;
- quantité ;
- produit déjà scanné ;
- fusion ;
- variante ;
- option ;
- remise ;
- annulation ;
- note ;
- client ;
- sauvegarde temporaire.

## 5.5 Reçus

- reçu numérique ;
- reçu imprimé ;
- SMS ;
- e-mail ;
- QR ;
- réimpression ;
- duplication ;
- personnalisation ;
- numéro unique ;
- taxes ;
- détails des moyens de paiement.

## 5.6 Remboursement

- total ;
- partiel ;
- validation manager ;
- recherche de transaction ;
- contrôle de délai ;
- motif ;
- nouvelle écriture ;
- reçu ;
- audit ;
- synchronisation Commerce.

## 5.7 Mode hors ligne

- catalogue local ;
- panier ;
- file d’attente ;
- restrictions ;
- plafond hors ligne ;
- contrôle de durée ;
- synchronisation ;
- résolution des conflits ;
- refus des opérations sensibles non supportées ;
- indication claire à l’employé.

## 5.8 Rapports de caisse

- ouverture ;
- fermeture ;
- total ;
- moyen de paiement ;
- remboursement ;
- différence ;
- employé ;
- établissement ;
- terminal ;
- export ;
- impression ;
- signature.

---

# 6. Application Mansa Admin Lite

- connexion forte ;
- alertes ;
- incidents ;
- validations autorisées ;
- revue KYC limitée ;
- revue KYB limitée ;
- blocage d’urgence ;
- carte ;
- compte ;
- utilisateur ;
- commerçant ;
- TPE ;
- fraude ;
- support ;
- approbation ;
- tableau de bord ;
- notifications critiques ;
- consultation de journaux ;
- restrictions strictes selon le rôle ;
- aucune fonction non autorisée par le portail central.

---

# 7. Application Mansa Annuaire / Hub

- recherche de commerce ;
- recherche de service ;
- catégories ;
- carte ;
- géolocalisation ;
- itinéraire ;
- proximité ;
- filtres ;
- horaires ;
- ouvert maintenant ;
- profil professionnel ;
- galerie ;
- produits ;
- services ;
- prix ;
- promotions ;
- fidélité ;
- avis ;
- réponses ;
- favoris ;
- partage ;
- appel ;
- e-mail ;
- WhatsApp ;
- mini-site ;
- réservation ;
- rendez-vous ;
- paiement ;
- QR ;
- établissements à la une ;
- abonnements professionnels ;
- profils sponsorisés ;
- modération ;
- signalement ;
- statistiques ;
- recommandations Jini.

---

# 8. Site public officiel Mansa

- accueil ;
- vision ;
- mission ;
- produits ;
- application Client ;
- cartes ;
- paiements ;
- Mansa Connect ;
- sécurité ;
- Jini ;
- services publics ;
- investissements ;
- commerçants ;
- partenaires ;
- tarifs ;
- pays ;
- chiffres clés ;
- nombre d’utilisateurs ;
- volume de transactions ;
- impact ;
- actualités ;
- blog ;
- presse ;
- carrière ;
- téléchargements ;
- FAQ ;
- aide ;
- contact ;
- pages légales ;
- confidentialité ;
- cookies ;
- accessibilité ;
- statut des services ;
- CMS ;
- SEO ;
- analytics ;
- animations premium ;
- démonstrations 3D ;
- responsive ;
- performances.

---

# 9. Site Mansa Professionnels

- accueil professionnel ;
- solutions commerçants ;
- solutions entreprises ;
- TPE ;
- Tap to Phone ;
- paiements ;
- commerce ;
- stocks ;
- catalogue ;
- facturation ;
- fidélité ;
- promotions ;
- mini-site ;
- Hub ;
- rendez-vous ;
- abonnements ;
- tarifs ;
- secteurs ;
- études de cas ;
- démonstration ;
- demande de devis ;
- inscription ;
- partenaires ;
- banques ;
- institutions ;
- développeurs ;
- API ;
- documentation commerciale ;
- support ;
- contact ;
- CMS ;
- SEO ;
- analytics ;
- animations premium.

---

# 10. Portail Mansa Admin Web

## 10.1 Administration centrale

- dashboard ;
- utilisateurs ;
- commerçants ;
- entreprises ;
- employés ;
- agents ;
- rôles ;
- permissions ;
- sessions ;
- appareils ;
- KYC ;
- KYB ;
- wallets ;
- comptes ;
- soldes ;
- ledger ;
- transactions ;
- transferts ;
- paiements ;
- cartes ;
- programmes cartes ;
- BIN ;
- TPE ;
- imprimantes ;
- Mobile Money ;
- remboursements ;
- litiges ;
- fraude ;
- support ;
- notifications ;
- abonnements ;
- commissions ;
- taxes ;
- fidélité ;
- promotions ;
- catalogue ;
- stocks ;
- clients ;
- Annuaire ;
- rendez-vous ;
- CMS ;
- partenaires ;
- banques ;
- pays ;
- devises ;
- langues ;
- services publics ;
- investissements ;
- Jini ;
- analytics ;
- audit ;
- incidents ;
- monitoring ;
- feature flags ;
- environnements ;
- exports ;
- configuration générale.

## 10.2 Administration no-code

- activation d’un module ;
- désactivation ;
- ordre d’affichage ;
- rôles ;
- pays ;
- devises ;
- abonnements ;
- limites ;
- frais ;
- commissions ;
- taxes ;
- textes ;
- catégories ;
- modèles ;
- couleurs ;
- bannières ;
- campagnes ;
- règles de risque ;
- workflows ;
- double validation ;
- publication différée ;
- historique ;
- restauration de configuration.

---

# 11. Backend et services communs

## 11.1 Modules backend

- auth ;
- sessions ;
- devices ;
- users ;
- profiles ;
- identity ;
- KYC ;
- KYB ;
- roles ;
- permissions ;
- RBAC ;
- ABAC ;
- audit ;
- wallets ;
- accounts ;
- balances ;
- ledger ;
- transactions ;
- transfers ;
- payments ;
- payment requests ;
- cards ;
- card programs ;
- card network ;
- NFC ;
- QR ;
- Mobile Money ;
- merchants ;
- establishments ;
- employees ;
- terminals ;
- catalogue ;
- inventory ;
- suppliers ;
- sales ;
- invoices ;
- receipts ;
- returns ;
- refunds ;
- disputes ;
- customers ;
- loyalty ;
- promotions ;
- campaigns ;
- appointments ;
- Annuaire ;
- reviews ;
- messaging ;
- notifications ;
- documents ;
- support ;
- fraud ;
- risk ;
- analytics ;
- investments ;
- services publics ;
- taxes ;
- amendes ;
- bourses ;
- cartes étudiantes ;
- Jini ;
- CMS ;
- subscriptions ;
- billing ;
- commissions ;
- partners ;
- webhooks ;
- files ;
- search ;
- geolocation ;
- feature flags ;
- configuration ;
- tasks ;
- events ;
- idempotency ;
- correlation ;
- health ;
- monitoring.

---

# 12. Familles d’API

- `/auth` ;
- `/sessions` ;
- `/devices` ;
- `/users` ;
- `/profiles` ;
- `/identity` ;
- `/kyc` ;
- `/kyb` ;
- `/roles` ;
- `/permissions` ;
- `/wallets` ;
- `/accounts` ;
- `/balances` ;
- `/ledger` ;
- `/transactions` ;
- `/transfers` ;
- `/payments` ;
- `/payment-requests` ;
- `/cards` ;
- `/card-programs` ;
- `/qr` ;
- `/nfc` ;
- `/mobile-money` ;
- `/merchants` ;
- `/establishments` ;
- `/employees` ;
- `/terminals` ;
- `/catalog` ;
- `/inventory` ;
- `/suppliers` ;
- `/sales` ;
- `/invoices` ;
- `/receipts` ;
- `/returns` ;
- `/refunds` ;
- `/disputes` ;
- `/customers` ;
- `/loyalty` ;
- `/promotions` ;
- `/appointments` ;
- `/directory` ;
- `/reviews` ;
- `/chat` ;
- `/notifications` ;
- `/documents` ;
- `/support` ;
- `/fraud` ;
- `/analytics` ;
- `/investments` ;
- `/public-services` ;
- `/fines` ;
- `/taxes` ;
- `/scholarships` ;
- `/student-cards` ;
- `/jini` ;
- `/cms` ;
- `/subscriptions` ;
- `/billing` ;
- `/commissions` ;
- `/partners` ;
- `/webhooks` ;
- `/files` ;
- `/search` ;
- `/geolocation` ;
- `/feature-flags` ;
- `/configuration` ;
- `/audit` ;
- `/health`.

Chaque endpoint devra préciser :

- authentification ;
- permissions ;
- corps de requête ;
- paramètres ;
- réponse ;
- erreurs ;
- idempotence ;
- limitation de débit ;
- audit ;
- corrélation ;
- version ;
- dépendance partenaire éventuelle.

---

# 13. Packages partagés

- contrats API ;
- types TypeScript ;
- SDK ;
- client HTTP ;
- erreurs ;
- validation ;
- sécurité ;
- authentification ;
- permissions ;
- paiements ;
- cartes ;
- notifications ;
- analytics ;
- configuration ;
- feature flags ;
- design system ;
- composants UI ;
- thèmes ;
- icônes ;
- hooks ;
- utilitaires ;
- formatage monétaire ;
- dates ;
- internationalisation ;
- traductions ;
- tests ;
- mocks.

---

# 14. Données et Prisma

Les familles principales de modèles devront couvrir :

- utilisateurs ;
- profils ;
- identités ;
- documents ;
- sessions ;
- appareils ;
- rôles ;
- permissions ;
- organisations ;
- commerçants ;
- établissements ;
- employés ;
- wallets ;
- comptes ;
- soldes ;
- ledger ;
- transactions ;
- paiements ;
- demandes ;
- cartes ;
- programmes ;
- QR ;
- NFC ;
- Mobile Money ;
- terminaux ;
- produits ;
- stocks ;
- fournisseurs ;
- clients ;
- ventes ;
- factures ;
- reçus ;
- retours ;
- remboursements ;
- litiges ;
- fidélité ;
- promotions ;
- rendez-vous ;
- Annuaire ;
- avis ;
- conversations ;
- messages ;
- notifications ;
- documents ;
- support ;
- fraude ;
- risque ;
- services publics ;
- investissements ;
- abonnements ;
- commissions ;
- taxes ;
- audit ;
- configuration ;
- partenaires ;
- webhooks ;
- événements ;
- tâches.

---

# 15. Infrastructure

- monorepo ;
- PNPM ;
- Turborepo ;
- NestJS ;
- React Native ;
- Kotlin Android pour le TPE lorsque nécessaire ;
- Next.js ;
- TypeScript ;
- PostgreSQL ;
- Prisma ;
- Redis ;
- stockage objet ;
- file de messages ;
- tâches asynchrones ;
- Docker ;
- CI ;
- lint ;
- formatage ;
- tests ;
- build ;
- déploiement ;
- secrets externes ;
- monitoring ;
- logs ;
- traces ;
- métriques ;
- alertes ;
- sauvegardes ;
- restauration ;
- haute disponibilité ;
- environnements Démo, Recette et Production.

---

# 16. Sécurité et conformité

- authentification forte ;
- MFA ;
- biométrie locale ;
- passkeys ;
- JWT ou mécanisme équivalent sécurisé ;
- rotation des jetons ;
- révocation ;
- chiffrement en transit ;
- chiffrement au repos ;
- coffre de secrets ;
- RBAC ;
- ABAC ;
- double validation ;
- audit immuable ;
- limitation de débit ;
- protection OWASP ;
- validation des entrées ;
- anti-fraude ;
- AML ;
- KYC ;
- KYB ;
- sanctions ;
- appareils compromis ;
- détection de root ;
- gestion d’incident ;
- sauvegarde ;
- plan de reprise ;
- confidentialité ;
- conservation ;
- export ;
- suppression ;
- consentement ;
- séparation des environnements.

---

# 17. Règle anti-oubli

Chaque module détaillé devra obligatoirement préciser :

1. objectif ;  
2. utilisateurs ;  
3. écrans ;  
4. parcours ;  
5. actions ;  
6. permissions ;  
7. règles métier ;  
8. données ;  
9. contrats API ;  
10. administration ;  
11. notifications ;  
12. sécurité ;  
13. audit ;  
14. analytics ;  
15. états vides ;  
16. chargement ;  
17. erreurs ;  
18. hors ligne ;  
19. accessibilité ;  
20. performances ;  
21. dépendances partenaires ;  
22. critères d’acceptation ;  
23. tests unitaires ;  
24. tests d’intégration ;  
25. tests end-to-end ;  
26. statut de la fonctionnalité.
