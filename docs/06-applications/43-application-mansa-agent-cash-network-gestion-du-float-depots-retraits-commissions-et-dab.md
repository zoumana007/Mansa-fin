# 43 — Application Mansa Agent, Cash Network, gestion du float, dépôts, retraits, commissions et DAB

## 1. Objet du document

Ce document définit l’architecture officielle de l’application **Mansa Agent** et du réseau **Mansa Cash Network**.

Il couvre :

- les agents ;
- les points de service ;
- les agences Mansa ;
- les commerces partenaires ;
- les dépôts ;
- les retraits ;
- le float ;
- la caisse physique ;
- les commissions ;
- les frais ;
- les réapprovisionnements ;
- les transferts entre agents ;
- les demandes de liquidité ;
- l’ouverture et la fermeture de caisse ;
- les reçus ;
- les incidents ;
- les contrôles anti-fraude ;
- le fonctionnement sans Internet côté client ;
- les distributeurs automatiques Mansa ;
- la gestion des billets ;
- la maintenance ;
- l’administration ;
- les rapports ;
- les rapprochements ;
- les extensions nationales et régionales.

L’objectif est de construire un réseau de distribution capable de :

- transformer les espèces en argent numérique ;
- transformer l’argent numérique en espèces ;
- rémunérer automatiquement les agents ;
- fonctionner avec des clients faiblement connectés ;
- sécuriser les dépôts et retraits ;
- suivre les liquidités ;
- gérer les distributeurs ;
- rester entièrement administrable ;
- évoluer d’un premier point de service vers un réseau national.

---

# 2. Principes fondamentaux

## 2.1 Le réseau doit démarrer simplement

Mansa peut commencer avec :

- un seul distributeur ;
- quelques agents pilotes ;
- une zone limitée ;
- une agence partenaire ;
- un superviseur ;
- des plafonds prudents ;
- un modèle de commission simple.

L’architecture doit toutefois être prête à gérer :

- des centaines d’agents ;
- plusieurs milliers de points ;
- plusieurs banques ;
- plusieurs opérateurs ;
- plusieurs pays ;
- plusieurs devises.

---

## 2.2 Aucun frais ne doit être codé en dur

Tous les frais et toutes les commissions doivent être administrables.

L’administration doit pouvoir :

- créer ;
- modifier ;
- activer ;
- désactiver ;
- programmer ;
- remplacer ;
- limiter ;
- tester ;
- historiser.

---

## 2.3 Les agents ne travaillent pas gratuitement

Chaque opération doit pouvoir rémunérer :

- l’agent ;
- Mansa ;
- la banque partenaire ;
- le gestionnaire du DAB ;
- un opérateur Mobile Money ;
- un superviseur ;
- un partenaire externe.

La rémunération doit être calculée automatiquement.

---

## 2.4 Le float est séparé du compte personnel

Chaque agent possède :

- un compte personnel ;
- un compte professionnel éventuel ;
- un compte de float ;
- une caisse déclarée ;
- un portefeuille de commissions.

Ces comptes ne doivent pas être confondus.

---

## 2.5 Le dépôt ne demande pas de confirmation client

Pour un dépôt :

- le client remet les espèces ;
- l’agent initie l’opération ;
- le backend effectue les contrôles ;
- le wallet client est crédité ;
- le client reçoit une notification, un SMS ou un reçu ;
- aucune confirmation PIN ou biométrique du client n’est exigée.

---

## 2.6 Le retrait exige une autorisation client

Pour un retrait :

- le solde client est vérifié ;
- l’agent doit disposer des espèces nécessaires ;
- le client s’authentifie ;
- le backend valide ;
- le wallet est débité ;
- le float agent est crédité ;
- l’agent remet les espèces.

---

# 3. Composition du Mansa Cash Network

Le réseau peut inclure :

- boutiques partenaires ;
- supermarchés ;
- stations-service ;
- pharmacies ;
- commerçants agréés ;
- agences bancaires partenaires ;
- agences Mansa ;
- points mobiles ;
- agents individuels ;
- distributeurs automatiques ;
- superviseurs de zone ;
- centres de rééquilibrage.

---

# 4. Types d’agents

## 4.1 Agent standard

Peut effectuer :

- dépôts ;
- retraits ;
- réception de paiements ;
- création de reçus ;
- consultation du float ;
- demande de liquidité.

## 4.2 Agent premium

Peut disposer :

- de plafonds plus élevés ;
- de commissions différentes ;
- de plusieurs employés ;
- de plusieurs caisses ;
- de services supplémentaires ;
- de transferts entre agents.

## 4.3 Agence partenaire

Peut effectuer :

- réapprovisionnement ;
- dépôt important ;
- retrait important ;
- gestion de plusieurs agents ;
- contrôle de caisse ;
- récupération de fonds ;
- rapprochement local.

## 4.4 Agence Mansa

Peut assurer :

- onboarding ;
- support ;
- KYC ;
- gestion de liquidité ;
- gestion de DAB ;
- traitement d’incidents ;
- formation ;
- audit ;
- rééquilibrage.

## 4.5 Superviseur

Peut suivre :

- agents d’une zone ;
- demandes de float ;
- incidents ;
- écarts de caisse ;
- disponibilité des liquidités ;
- performances ;
- risques ;
- conformité.

---

# 5. Statuts d’un agent

Valeurs possibles :

- PROSPECT ;
- ONBOARDING ;
- KYC_PENDING ;
- KYB_PENDING ;
- TRAINING_REQUIRED ;
- APPROVAL_PENDING ;
- ACTIVE ;
- LIMITED ;
- SUSPENDED ;
- BLOCKED ;
- TERMINATED ;
- ARCHIVED.

---

# 6. Onboarding agent

Le parcours peut inclure :

1. identification ;
2. vérification du téléphone ;
3. KYC ;
4. KYB si nécessaire ;
5. adresse ;
6. localisation ;
7. type de commerce ;
8. compte bancaire ;
9. contrat ;
10. formation ;
11. dépôt de garantie éventuel ;
12. activation de l’appareil ;
13. attribution des plafonds ;
14. activation du float.

---

# 7. Dossier agent

Le dossier doit contenir :

- identité ;
- entreprise ;
- point de service ;
- contacts ;
- documents ;
- banque partenaire ;
- compte de règlement ;
- appareil ;
- localisation ;
- horaires ;
- statut ;
- niveau ;
- plafonds ;
- commissions ;
- incidents ;
- audits ;
- formation ;
- superviseur.

---

# 8. Application Mansa Agent

Technologie recommandée :

```text
React Native
TypeScript
```

Selon le matériel, certaines versions peuvent utiliser :

- Android natif ;
- Kotlin ;
- terminal Android sécurisé ;
- imprimante intégrée ;
- lecteur NFC ;
- lecteur puce ;
- scanner QR.

---

# 9. Architecture de l’application

Structure possible :

```text
src/
├── auth/
├── onboarding/
├── dashboard/
├── deposits/
├── withdrawals/
├── customers/
├── float/
├── cash-register/
├── commissions/
├── replenishment/
├── liquidity/
├── receipts/
├── incidents/
├── devices/
├── employees/
├── reports/
├── settings/
├── security/
├── sync/
└── support/
```

---

# 10. Navigation principale

Navigation recommandée :

```text
Accueil
Dépôt
Retrait
Caisse
Activité
```

Menu secondaire :

- Float ;
- Commissions ;
- Réapprovisionnement ;
- Agents ;
- Reçus ;
- Incidents ;
- Paramètres ;
- Support.

---

# 11. Tableau de bord agent

Afficher en temps réel :

- float disponible ;
- float réservé ;
- espèces déclarées ;
- dépôts du jour ;
- retraits du jour ;
- commissions du jour ;
- commissions en attente ;
- solde de caisse ;
- alertes de liquidité ;
- opérations en attente ;
- statut du point de vente.

---

# 12. Widgets du tableau de bord

Exemples :

- niveau de float ;
- couverture estimée des retraits ;
- montant de caisse ;
- commissions de la semaine ;
- objectif mensuel ;
- dernier incident ;
- demande de liquidité ;
- prochain contrôle ;
- statut réseau.

---

# 13. Identification du client

L’agent peut rechercher un client par :

- numéro de téléphone ;
- QR ;
- identifiant Mansa ;
- carte Mansa ;
- code de transaction ;
- scan de document lorsque autorisé.

---

# 14. Protection des données client

L’agent ne doit voir que :

- nom partiellement masqué ;
- téléphone masqué ;
- photo si nécessaire ;
- statut du compte ;
- niveau d’éligibilité ;
- devise ;
- alertes utiles.

Il ne doit pas voir :

- solde complet sauf nécessité ;
- historique total ;
- documents ;
- PIN ;
- OTP ;
- secrets ;
- informations non nécessaires.

---

# 15. Dépôt d’espèces

## 15.1 Parcours

1. L’agent sélectionne Dépôt.
2. Il identifie le client.
3. Il saisit le montant.
4. Il vérifie les espèces reçues.
5. Le backend vérifie :
   - le float ;
   - les plafonds ;
   - le statut agent ;
   - le statut client ;
   - les règles pays ;
   - la fraude ;
   - les frais.
6. Le wallet client est crédité.
7. Le float agent est débité.
8. La caisse physique est augmentée.
9. Le reçu est généré.
10. Le client est notifié.

## 15.2 Exemple comptable

Avant :

```text
Client : 5 000 XOF
Float agent : 500 000 XOF
Caisse agent : 300 000 XOF
```

Dépôt :

```text
20 000 XOF
```

Après :

```text
Client : 25 000 XOF
Float agent : 480 000 XOF
Caisse agent : 320 000 XOF
```

## 15.3 Aucune confirmation client

Le dépôt ne doit pas exiger :

- PIN ;
- biométrie ;
- OTP ;
- validation dans l’application Client.

Le client doit seulement recevoir une preuve après l’opération.

---

# 16. Dépôt par carte

L’agent peut accepter un dépôt par carte si :

- le terminal est certifié ;
- le service est activé ;
- le pays l’autorise ;
- le partenaire carte est disponible ;
- les frais sont calculés.

---

# 17. Dépôt Mobile Money

Le client peut transférer depuis Mobile Money vers son wallet Mansa via l’agent.

Le système doit distinguer :

- dépôt espèces ;
- dépôt Mobile Money ;
- dépôt carte ;
- dépôt bancaire.

---

# 18. Retrait d’espèces

## 18.1 Parcours

1. L’agent sélectionne Retrait.
2. Il identifie le client.
3. Il saisit le montant.
4. Le backend vérifie :
   - le solde client ;
   - les plafonds ;
   - le statut client ;
   - le statut agent ;
   - la disponibilité de caisse ;
   - le risque ;
   - les frais.
5. Le client s’authentifie.
6. Le backend autorise.
7. Le wallet client est débité.
8. Le float agent est crédité.
9. La caisse agent est diminuée.
10. L’agent remet les espèces.
11. Les reçus sont générés.

## 18.2 Exemple comptable

Avant :

```text
Client : 100 000 XOF
Float agent : 400 000 XOF
Caisse agent : 250 000 XOF
```

Retrait :

```text
30 000 XOF
```

Après :

```text
Client : 70 000 XOF
Float agent : 430 000 XOF
Caisse agent : 220 000 XOF
```

Les frais et commissions sont comptabilisés séparément.

---

# 19. Authentification du retrait

Méthodes possibles :

- PIN sur le terminal ;
- OTP SMS ;
- USSD ;
- carte Mansa + PIN ;
- QR sécurisé ;
- code de retrait ;
- confirmation biométrique ;
- validation sur appareil reconnu.

---

# 20. Retrait sans Internet client

Le client n’a pas besoin de connexion Internet si :

- le terminal de l’agent est connecté ;
- l’authentification est réalisée par un canal disponible ;
- le backend autorise l’opération.

Canaux possibles :

- SMS ;
- USSD ;
- carte + PIN ;
- code pré-généré ;
- vérification contrôlée.

---

# 21. Règle de remise des espèces

L’agent ne doit jamais remettre les espèces lorsque le statut est :

- CREATED ;
- AUTHENTICATION_REQUIRED ;
- PROCESSING ;
- UNKNOWN ;
- FAILED ;
- EXPIRED ;
- CANCELLED ;
- UNDER_REVIEW.

La remise est permise uniquement après autorisation explicite du backend.

---

# 22. Statuts d’opération

- CREATED ;
- VALIDATING ;
- AUTHENTICATION_REQUIRED ;
- AUTHORIZED ;
- PROCESSING ;
- COMPLETED ;
- FAILED ;
- EXPIRED ;
- CANCELLED ;
- REVERSED ;
- UNDER_REVIEW.

---

# 23. Gestion du float

Chaque agent dispose de :

- float disponible ;
- float réservé ;
- float total ;
- limite minimale ;
- limite maximale ;
- seuil d’alerte ;
- historique ;
- position par devise ;
- position par partenaire ;
- statut.

---

# 24. Séparation du float

Le float doit être distinct :

- du compte personnel ;
- du wallet commerçant ;
- des commissions ;
- de la caisse physique ;
- des fonds en attente ;
- des réserves.

---

# 25. Réapprovisionnement du float

Méthodes :

- virement bancaire ;
- dépôt agence partenaire ;
- transfert Mobile Money ;
- transfert superviseur ;
- transfert entre agents ;
- dépôt Mansa ;
- règlement automatique.

---

# 26. Réapprovisionnement par banque

Le système doit gérer :

- référence ;
- banque ;
- montant ;
- devise ;
- statut ;
- preuve ;
- rapprochement ;
- délai ;
- frais éventuels.

---

# 27. Transfert entre agents

Il peut être autorisé selon :

- même pays ;
- même zone ;
- même devise ;
- même superviseur ;
- plafond ;
- niveau agent ;
- risque ;
- disponibilité.

---

# 28. Demande de liquidité

Un agent peut demander :

- float électronique ;
- espèces ;
- coupures spécifiques ;
- intervention ;
- transfert d’un autre agent ;
- livraison par superviseur.

---

# 29. Statuts d’une demande de liquidité

- CREATED ;
- PENDING ;
- APPROVED ;
- ASSIGNED ;
- IN_TRANSIT ;
- DELIVERED ;
- REJECTED ;
- CANCELLED ;
- CLOSED.

---

# 30. Rééquilibrage

Le système doit aider à identifier :

- agents avec trop d’espèces ;
- agents avec trop peu d’espèces ;
- agents avec trop de float ;
- agents proches ;
- zones sous-desservies ;
- risques de rupture.

---

# 31. Caisse physique

Chaque agent doit déclarer sa caisse.

Elle peut inclure :

- espèces disponibles ;
- coupures ;
- caisse théorique ;
- caisse réelle ;
- écart ;
- ouverture ;
- fermeture ;
- mouvements ;
- justificatifs.

---

# 32. Ouverture de caisse

L’agent doit enregistrer :

- date ;
- heure ;
- montant initial ;
- coupures ;
- appareil ;
- employé ;
- point de vente ;
- photo éventuelle ;
- validation éventuelle.

---

# 33. Fermeture de caisse

À la fermeture :

- calcul du total théorique ;
- saisie du total réel ;
- comparaison ;
- écart ;
- justification ;
- signature ;
- rapport ;
- escalade si nécessaire.

---

# 34. Écart de caisse

Types :

- excédent ;
- manque ;
- erreur de saisie ;
- opération non synchronisée ;
- faux billet ;
- incident ;
- vol ;
- litige.

---

# 35. Commissions agent

Le tableau de bord doit afficher :

- commissions du jour ;
- commissions de la semaine ;
- commissions du mois ;
- commissions en attente ;
- commissions validées ;
- commissions versées ;
- bonus ;
- pénalités ;
- détail par opération.

---

# 36. Calcul des commissions

Méthodes :

- montant fixe ;
- pourcentage ;
- combinaison fixe + pourcentage ;
- palier ;
- seuil ;
- minimum ;
- maximum ;
- bonus de volume ;
- bonus promotionnel.

---

# 37. Modèles de dépôt

Exemples configurables :

- dépôt gratuit, agent payé par Mansa ;
- dépôt payant, frais partagés ;
- dépôt gratuit pendant une campagne ;
- dépôt gratuit jusqu’à un plafond ;
- dépôt payant selon zone ;
- dépôt subventionné par un partenaire.

---

# 38. Modèles de retrait

Exemples :

- frais fixe ;
- pourcentage ;
- frais par palier ;
- gratuité premium ;
- réduction promotionnelle ;
- tarif par agent ;
- tarif par région ;
- tarif par DAB.

---

# 39. Répartition des frais

Une opération peut répartir les revenus entre :

- agent ;
- Mansa ;
- banque ;
- Mobile Money ;
- superviseur ;
- partenaire ;
- gestionnaire DAB ;
- taxes.

---

# 40. Paramètres tarifaires

Les règles peuvent dépendre :

- du pays ;
- de la région ;
- de la ville ;
- du quartier ;
- du type d’agent ;
- du niveau d’agent ;
- du type de transaction ;
- du montant ;
- du client ;
- du moyen de paiement ;
- du jour ;
- de l’heure ;
- des jours fériés ;
- d’une campagne ;
- d’un partenaire.

---

# 41. Historisation des frais

Chaque modification doit enregistrer :

- administrateur ;
- date ;
- heure ;
- ancienne valeur ;
- nouvelle valeur ;
- motif ;
- date d’effet ;
- périmètre ;
- approbation ;
- version.

---

# 42. Reçus

Les reçus doivent inclure :

- référence ;
- identifiant unique ;
- agent ;
- point de service ;
- client masqué ;
- type ;
- montant ;
- frais ;
- commission visible si applicable ;
- total ;
- devise ;
- date ;
- statut ;
- QR de vérification ;
- support.

---

# 43. Impression

L’application Agent peut utiliser :

- imprimante intégrée ;
- imprimante Bluetooth ;
- imprimante réseau ;
- reçu numérique ;
- SMS ;
- e-mail.

---

# 44. Historique agent

Filtres :

- dépôt ;
- retrait ;
- commission ;
- réapprovisionnement ;
- caisse ;
- incident ;
- client ;
- date ;
- montant ;
- statut ;
- employé ;
- point de vente.

---

# 45. Employés d’un agent

Un agent peut créer des comptes employés avec :

- rôle ;
- PIN ;
- appareil ;
- horaires ;
- plafonds ;
- permissions ;
- caisse ;
- historique ;
- statut.

---

# 46. Rôles employés

Exemples :

- caissier ;
- responsable ;
- superviseur local ;
- comptable ;
- support ;
- propriétaire.

---

# 47. Séparation des responsabilités

Un employé ne doit pas nécessairement pouvoir :

- modifier les frais ;
- changer les coordonnées bancaires ;
- approuver un écart ;
- transférer du float ;
- clôturer un incident ;
- ajouter un autre administrateur.

---

# 48. Sécurité de l’agent

Le système doit vérifier :

- identité ;
- appareil ;
- terminal ;
- localisation ;
- statut ;
- horaires ;
- float ;
- caisse ;
- plafonds ;
- règles de risque ;
- fraude ;
- version application.

---

# 49. Appareil enregistré

Chaque appareil doit avoir :

- identifiant ;
- modèle ;
- OS ;
- version ;
- certificat ;
- agent ;
- point de vente ;
- date d’activation ;
- dernière activité ;
- statut ;
- révocation.

---

# 50. Localisation

La localisation peut être utilisée pour :

- vérifier le point de vente ;
- détecter un déplacement anormal ;
- confirmer une intervention ;
- trouver l’agent ;
- analyser les zones.

Elle doit rester configurable selon la politique.

---

# 51. Règles anti-fraude

Exemples :

- dépôts fractionnés ;
- retraits répétés ;
- écarts de caisse ;
- agent très actif soudainement ;
- appareil inconnu ;
- déplacement impossible ;
- opérations nocturnes ;
- montant inhabituel ;
- collusion ;
- faux dépôts ;
- annulations répétées.

---

# 52. Incident agent

Types :

- panne application ;
- panne terminal ;
- manque d’espèces ;
- manque de float ;
- erreur client ;
- fraude ;
- faux billet ;
- vol ;
- réseau indisponible ;
- impression ;
- écart de caisse ;
- agression ;
- DAB indisponible.

---

# 53. Signalement d’incident

Le dossier peut contenir :

- référence ;
- agent ;
- point ;
- type ;
- date ;
- opération ;
- description ;
- photo ;
- vidéo ;
- pièce jointe ;
- géolocalisation ;
- gravité ;
- statut ;
- responsable.

---

# 54. Bouton d’urgence

L’application peut proposer un bouton d’urgence permettant :

- suspension temporaire ;
- verrouillage de caisse ;
- alerte superviseur ;
- signalement de vol ;
- arrêt des retraits ;
- révocation de session ;
- appel au support.

---

# 55. Mode dégradé

En cas d’incident :

- dépôts désactivés ;
- retraits désactivés ;
- consultation seulement ;
- plafond réduit ;
- un seul canal ;
- opérations en attente ;
- reçus différés ;
- agent suspendu temporairement.

---

# 56. Synchronisation

L’application doit gérer :

- reprise ;
- idempotence ;
- files locales ;
- statuts ;
- conflits ;
- opérations en attente ;
- reçus ;
- journaux ;
- configuration.

Aucune opération financière ne doit être dupliquée.

---

# 57. Mode hors ligne agent

Le mode hors ligne doit rester très limité.

Il peut permettre :

- consultation de procédures ;
- consultation d’historique local ;
- préparation d’une opération ;
- saisie de caisse ;
- création d’un incident.

Il ne doit pas confirmer librement un dépôt ou un retrait non autorisé par le backend.

---

# 58. Distributeur automatique Mansa

Le DAB est directement connecté à Mansa.

Il peut proposer :

- retrait avec carte ;
- retrait sans carte ;
- retrait QR ;
- retrait par code ;
- consultation du solde ;
- mini-relevé ;
- changement de PIN ;
- dépôt d’espèces ;
- impression ;
- assistance.

---

# 59. Modèles de DAB

Exemples :

- DAB retrait uniquement ;
- DAB dépôt et retrait ;
- kiosque compact ;
- distributeur mobile ;
- terminal bancaire partenaire ;
- recycleur de billets.

---

# 60. Gestion des billets

Le système doit suivre :

- coupures ;
- nombre de billets ;
- valeur totale ;
- cassettes ;
- billets rejetés ;
- billets suspects ;
- billets déposés ;
- billets distribués ;
- seuils ;
- historique.

---

# 61. Cassettes

Chaque cassette doit avoir :

- identifiant ;
- coupure ;
- capacité ;
- quantité ;
- statut ;
- seuil ;
- dernière recharge ;
- dernier retrait ;
- maintenance.

---

# 62. Alertes DAB

Exemples :

- caisse faible ;
- cassette vide ;
- cassette bloquée ;
- imprimante vide ;
- lecteur défectueux ;
- réseau perdu ;
- porte ouverte ;
- température anormale ;
- billet bloqué ;
- tentative d’effraction ;
- certificat expiré.

---

# 63. Maintenance DAB

Le système doit gérer :

- maintenance préventive ;
- maintenance corrective ;
- ticket ;
- technicien ;
- pièce ;
- date ;
- durée ;
- cause ;
- réparation ;
- remise en service ;
- preuve.

---

# 64. Réapprovisionnement DAB

Le workflow doit inclure :

- ordre ;
- montant ;
- coupures ;
- équipe ;
- transport ;
- double contrôle ;
- ouverture ;
- chargement ;
- fermeture ;
- rapprochement ;
- signature ;
- audit.

---

# 65. Sécurité DAB

Mesures :

- chiffrement ;
- certificat ;
- gestion des clés ;
- surveillance ;
- anti-skimming ;
- alarme ;
- géolocalisation ;
- journal technique ;
- caméra si autorisée ;
- verrouillage ;
- effacement sécurisé.

---

# 66. Administration centrale

L’administration doit gérer :

- agents ;
- points de service ;
- employés ;
- appareils ;
- DAB ;
- plafonds ;
- frais ;
- commissions ;
- horaires ;
- zones ;
- campagnes ;
- risques ;
- liquidité ;
- rééquilibrage ;
- incidents ;
- audits ;
- rapports ;
- maintenance.

---

# 67. Carte de supervision

Le portail Admin peut afficher :

- agents actifs ;
- agents hors ligne ;
- DAB actifs ;
- DAB en panne ;
- zones sans liquidité ;
- zones avec excès d’espèces ;
- incidents ;
- demandes ;
- volumes ;
- fraude ;
- maintenance.

---

# 68. Gestion dynamique

L’administration doit pouvoir modifier sans mise à jour de l’application :

- frais ;
- commissions ;
- plafonds ;
- rôles ;
- services ;
- horaires ;
- zones ;
- moyens d’authentification ;
- promotions ;
- partenaires ;
- règles anti-fraude ;
- statuts ;
- disponibilités.

---

# 69. Rapports

Rapports possibles :

- dépôts ;
- retraits ;
- commissions ;
- float ;
- caisse ;
- écarts ;
- liquidité ;
- performance agent ;
- performance zone ;
- DAB ;
- maintenance ;
- incidents ;
- fraude ;
- rapprochement ;
- rentabilité.

---

# 70. Rapprochement

Le système doit comparer :

- opérations Agent ;
- wallet client ;
- float agent ;
- caisse déclarée ;
- ledger ;
- banque ;
- Mobile Money ;
- DAB ;
- commissions ;
- règlements.

---

# 71. Divergences

Exemples :

- dépôt sans crédit ;
- crédit sans espèces déclarées ;
- retrait débité sans remise ;
- float incorrect ;
- caisse incorrecte ;
- commission incorrecte ;
- doublon ;
- opération manquante ;
- écart DAB ;
- billet non comptabilisé.

---

# 72. Comptes ledger

Comptes possibles :

- float agent ;
- caisse agent ;
- wallet client ;
- commissions agent ;
- revenu Mansa ;
- part banque ;
- part partenaire ;
- taxe ;
- suspense ;
- DAB espèces ;
- DAB dépôt ;
- DAB retrait.

---

# 73. API

Exemples :

```http
POST   /agents
GET    /agents
GET    /agents/{id}
PATCH  /agents/{id}

POST   /agents/{id}/activate
POST   /agents/{id}/suspend

POST   /agent/deposits
POST   /agent/withdrawals
GET    /agent/transactions

GET    /agent/float
POST   /agent/float/replenishments
POST   /agent/float/transfers
POST   /agent/liquidity-requests

POST   /agent/cash-register/open
POST   /agent/cash-register/close
POST   /agent/cash-register/declarations

GET    /agent/commissions
GET    /agent/receipts
POST   /agent/incidents

GET    /atms
POST   /atms
GET    /atms/{id}
POST   /atms/{id}/maintenance
POST   /atms/{id}/cash-replenishment
```

---

# 74. Permissions

Exemples :

```text
agent.deposit.create
agent.withdrawal.create
agent.transaction.read
agent.float.read
agent.float.replenish
agent.float.transfer
agent.cash_register.open
agent.cash_register.close
agent.cash_register.declare
agent.commission.read
agent.receipt.read
agent.incident.create
agent.employee.manage
agent.device.manage
agent.report.read
atm.read
atm.manage
atm.maintenance.manage
atm.cash.manage
cash_network.admin
```

---

# 75. Actions critiques

Doivent être protégées :

- activation agent ;
- suspension agent ;
- transfert de float ;
- correction de caisse ;
- modification de commission ;
- modification de frais ;
- augmentation de plafond ;
- remise en service DAB ;
- recharge DAB ;
- correction financière ;
- suppression d’une preuve.

---

# 76. Double validation

Peut être exigée pour :

- gros transfert de float ;
- correction d’un écart ;
- recharge importante de DAB ;
- modification globale de commission ;
- activation de retrait hors ligne ;
- réactivation après fraude ;
- annulation d’une opération validée ;
- changement de banque partenaire.

---

# 77. Modèles

- CashAgent
- CashAgentType
- CashAgentLevel
- CashAgentLocation
- CashAgentEmployee
- CashAgentDevice
- CashAgentFloatAccount
- CashAgentFloatMovement
- CashAgentCashRegister
- CashAgentCashDeclaration
- CashAgentCommission
- CashAgentFeeRule
- CashAgentLiquidityRequest
- CashAgentRebalancing
- CashDeposit
- CashWithdrawal
- CashReceipt
- CashIncident
- Atm
- AtmCassette
- AtmCashPosition
- AtmTransaction
- AtmAlert
- AtmMaintenance
- AtmCashReplenishment
- CashNetworkAudit

---

# 78. Analytics

Événements possibles :

```text
agent_onboarding_started
agent_activated
agent_deposit_started
agent_deposit_completed
agent_withdrawal_started
agent_withdrawal_completed
agent_float_replenished
agent_float_transferred
agent_cash_register_opened
agent_cash_register_closed
agent_cash_variance_detected
agent_commission_earned
agent_liquidity_requested
agent_incident_created
atm_transaction_completed
atm_cash_low
atm_alert_created
atm_maintenance_started
atm_replenishment_completed
```

---

# 79. Tests

- tests d’onboarding agent ;
- tests KYC/KYB ;
- tests de dépôt ;
- tests de dépôt sans confirmation client ;
- tests de retrait ;
- tests d’authentification ;
- tests sans Internet client ;
- tests de float ;
- tests de caisse ;
- tests de commissions ;
- tests de frais dynamiques ;
- tests de réapprovisionnement ;
- tests de transfert agent ;
- tests de liquidité ;
- tests de reçus ;
- tests d’incidents ;
- tests de fraude ;
- tests d’appareil ;
- tests DAB ;
- tests de cassette ;
- tests de maintenance ;
- tests de rapprochement ;
- tests multi-pays ;
- tests multi-devises ;
- tests de permissions ;
- tests de double validation ;
- tests d’audit.

---

# 80. Règles métier

1. Chaque agent possède un compte de float séparé.
2. Le float ne doit pas être mélangé au compte personnel.
3. Chaque agent déclare sa caisse.
4. Un dépôt ne demande pas de confirmation client.
5. Un retrait exige une authentification client.
6. Les espèces ne sont remises qu’après autorisation du backend.
7. Les frais sont administrables.
8. Les commissions sont administrables.
9. Les agents sont rémunérés automatiquement.
10. Les commissions peuvent être fixes, variables ou mixtes.
11. Les règles peuvent varier par zone, agent et période.
12. Toute modification tarifaire est historisée.
13. Toute opération possède une référence unique.
14. Les opérations validées sont immuables.
15. Toute correction utilise un workflow.
16. Les employés possèdent des permissions limitées.
17. Les appareils sont enregistrés.
18. Les écarts de caisse sont tracés.
19. Les transferts de float sont contrôlés.
20. Les demandes de liquidité sont suivies.
21. Le mode hors ligne agent reste limité.
22. Les DAB sont supervisés à distance.
23. Les cassettes sont inventoriées.
24. Les rapprochements sont automatisés.
25. Les actions critiques sont auditées.

---

# 81. Critères d’acceptation

L’application Mansa Agent et le Cash Network sont validés lorsque :

- les agents peuvent être onboardés ;
- les points de service sont administrables ;
- les appareils sont enregistrés ;
- les dépôts fonctionnent sans confirmation client ;
- les retraits exigent une authentification ;
- les opérations fonctionnent avec un client hors ligne ;
- le float est séparé ;
- la caisse est déclarée ;
- les commissions sont calculées ;
- les frais sont entièrement configurables ;
- les agents peuvent se réapprovisionner ;
- les transferts entre agents sont contrôlés ;
- les demandes de liquidité sont suivies ;
- les reçus sont disponibles ;
- les incidents sont traçables ;
- les règles anti-fraude sont appliquées ;
- les DAB sont administrables ;
- les cassettes sont suivies ;
- la maintenance est gérée ;
- les rapprochements sont automatisés ;
- les rapports sont disponibles ;
- les actions critiques sont protégées ;
- les tests couvrent les scénarios essentiels.
