# 42.5 — Complément Application Client Mansa : Cash Network, dépôts, retraits, localisation et reçus

## 1. Objet du document

Ce document complète le document 42 consacré à l’application Client Mansa.

Il ajoute les fonctionnalités visibles côté client liées au Mansa Cash Network :

- recherche d’agents ;
- recherche de distributeurs automatiques Mansa ;
- dépôts d’espèces ;
- retraits d’espèces ;
- fonctionnement sans Internet côté client ;
- authentification des retraits ;
- reçus ;
- historique ;
- localisation ;
- notifications ;
- frais affichés ;
- sécurité ;
- intégration au backend.

Ce document ne décrit pas encore l’application Mansa Agent ni l’administration complète du réseau. Ces éléments seront détaillés dans le document 43.

---

# 2. Principes fondamentaux

## 2.1 Aucun contrôle de confirmation côté client pour un dépôt

Lors d’un dépôt d’espèces chez un agent :

- le client remet les espèces ;
- l’agent initie l’opération ;
- le backend vérifie le float, les limites, le statut du compte et les règles de risque ;
- le wallet du client est crédité ;
- aucune confirmation PIN, biométrique ou applicative n’est demandée au client ;
- le client reçoit une preuve après exécution.

---

## 2.2 Authentification obligatoire pour un retrait

Lors d’un retrait d’espèces :

- le débit du wallet doit être autorisé par le client ;
- l’authentification doit être adaptée au canal et au risque ;
- l’agent ne remet les espèces qu’après confirmation du serveur.

Méthodes possibles :

- PIN sur le terminal ;
- OTP par SMS ;
- USSD lorsque disponible ;
- carte Mansa + PIN ;
- QR sécurisé ;
- code de retrait ;
- biométrie ;
- autre méthode configurée par l’administration.

---

## 2.3 Le téléphone du client peut être hors ligne

Le terminal de l’agent reste connecté.

Le client peut recevoir :

- un SMS ;
- un reçu papier ;
- un reçu numérique ultérieurement ;
- une notification dès le retour de la connexion.

---

## 2.4 Les frais viennent du backend

L’application Client ne calcule pas elle-même :

- les frais ;
- les commissions ;
- la rémunération de l’agent ;
- les parts de Mansa ;
- les parts de la banque ;
- les parts partenaires.

Elle affiche uniquement les valeurs renvoyées par le moteur central de tarification.

---

# 3. Accès au Mansa Cash Network

L’application Client doit intégrer une entrée dédiée :

```text
Cash Network
```

Cette entrée peut apparaître dans :

- l’accueil ;
- les raccourcis ;
- l’onglet Paiements ;
- le Hub ;
- la recherche ;
- le profil ;
- l’assistant Jini.

---

# 4. Écran Cash Network

L’écran doit proposer :

- déposer des espèces ;
- retirer des espèces ;
- trouver un agent ;
- trouver un DAB Mansa ;
- voir les opérations récentes ;
- consulter les reçus ;
- consulter les frais ;
- accéder au support.

---

# 5. Trouver un agent

L’utilisateur doit pouvoir rechercher un agent par :

- proximité ;
- ville ;
- quartier ;
- région ;
- nom ;
- catégorie ;
- disponibilité ;
- horaires ;
- services disponibles.

---

# 6. Filtres agent

Exemples :

- dépôt disponible ;
- retrait disponible ;
- dépôt par carte ;
- dépôt Mobile Money ;
- retrait avec carte Mansa ;
- retrait QR ;
- retrait par code ;
- imprimante disponible ;
- ouvert maintenant ;
- accessible ;
- agent vérifié ;
- agence Mansa ;
- commerce partenaire.

---

# 7. Carte interactive

La carte doit pouvoir afficher :

- agents ;
- agences Mansa ;
- distributeurs Mansa ;
- distance ;
- itinéraire ;
- statut ;
- horaires ;
- services ;
- coordonnées de contact.

L’utilisateur doit pouvoir choisir :

- position précise ;
- position approximative ;
- ville manuelle ;
- aucune géolocalisation.

---

# 8. Fiche d’un agent

La fiche peut afficher :

- nom commercial ;
- type d’agent ;
- badge vérifié ;
- adresse ;
- horaires ;
- distance ;
- services ;
- frais indicatifs lorsque publiés ;
- téléphone ;
- itinéraire ;
- statut ouvert ou fermé ;
- disponibilité déclarée des espèces lorsque autorisée ;
- bouton signaler un problème.

Les données financières internes de l’agent ne doivent pas être exposées.

---

# 9. Trouver un distributeur Mansa

L’utilisateur doit pouvoir filtrer les DAB selon :

- retrait par carte ;
- retrait sans carte ;
- retrait par QR ;
- retrait par code ;
- dépôt d’espèces ;
- consultation de solde ;
- mini-relevé ;
- changement de PIN ;
- disponibilité ;
- accessibilité ;
- horaires.

---

# 10. Fiche DAB

Elle peut afficher :

- emplacement ;
- adresse ;
- distance ;
- itinéraire ;
- services disponibles ;
- statut opérationnel ;
- indisponibilité temporaire ;
- horaires d’accès ;
- frais applicables ;
- moyens d’authentification acceptés.

L’application ne doit pas exposer :

- le nombre exact de billets ;
- la valeur totale en caisse ;
- les détails internes des cassettes ;
- les informations techniques sensibles.

---

# 11. Dépôt d’espèces chez un agent

## 11.1 Parcours client

1. Le client se rend chez un agent.
2. Il remet les espèces à l’agent.
3. Il communique son identité Mansa par :
   - numéro de téléphone ;
   - QR ;
   - identifiant Mansa ;
   - carte Mansa.
4. L’agent saisit le montant.
5. Le backend effectue les contrôles.
6. Le wallet du client est crédité.
7. Le client reçoit une preuve.
8. L’opération apparaît dans l’historique.

---

## 11.2 Aucune confirmation dans l’application

Le client ne doit pas être obligé de :

- saisir son PIN ;
- utiliser sa biométrie ;
- confirmer dans l’application ;
- disposer d’une connexion Internet.

Le dépôt constitue un crédit du compte client après remise d’espèces à l’agent.

---

## 11.3 Écran de suivi du dépôt

Lorsque l’application est connectée, elle peut afficher :

- montant reçu ;
- agent ;
- date ;
- heure ;
- référence ;
- frais éventuels ;
- statut ;
- reçu ;
- bouton d’assistance.

---

## 11.4 Statuts du dépôt

- CREATED ;
- PROCESSING ;
- COMPLETED ;
- FAILED ;
- CANCELLED ;
- UNDER_REVIEW.

Le statut `COMPLETED` ne doit apparaître qu’après confirmation du backend.

---

# 12. Retrait chez un agent

## 12.1 Parcours client

1. Le client demande un retrait.
2. L’agent sélectionne Retrait.
3. Le montant est saisi.
4. Le backend vérifie :
   - le solde du client ;
   - les limites ;
   - le statut du compte ;
   - le niveau KYC ;
   - le risque ;
   - la capacité opérationnelle de l’agent.
5. Le client s’authentifie.
6. Le backend valide le débit.
7. L’agent reçoit l’autorisation de remise.
8. L’agent remet les espèces.
9. Le client et l’agent reçoivent un reçu.

---

## 12.2 Écran avant retrait

Lorsque le client utilise son application, afficher :

- montant ;
- agent ou DAB ;
- frais ;
- total débité ;
- devise ;
- méthode d’authentification ;
- durée de validité ;
- avertissement de sécurité ;
- bouton d’annulation.

---

## 12.3 Authentification possible sans Internet mobile

Le client peut autoriser le retrait par :

- PIN sur le terminal de l’agent ;
- OTP par SMS ;
- USSD ;
- carte Mansa + PIN ;
- code sécurisé généré préalablement ;
- autre canal approuvé.

---

## 12.4 Statuts du retrait

- CREATED ;
- AUTHENTICATION_REQUIRED ;
- AUTHORIZED ;
- CASH_DISPENSING ;
- COMPLETED ;
- FAILED ;
- EXPIRED ;
- CANCELLED ;
- UNDER_REVIEW.

---

# 13. Retrait par QR

Le client peut générer ou scanner un QR de retrait.

Le QR doit être :

- signé ;
- temporaire ;
- lié au montant ;
- lié au client ;
- lié à l’environnement ;
- révocable ;
- inutilisable après expiration ;
- protégé contre le rejeu.

---

# 14. Retrait par code sécurisé

Le client peut générer un code de retrait contenant :

- référence ;
- montant ;
- durée de validité ;
- canal ;
- agent ou DAB éventuel ;
- statut ;
- nombre de tentatives ;
- annulation.

Le code ne doit pas être affiché longtemps à l’écran.

---

# 15. Dépôt au DAB

Lorsque le modèle le permet, le client peut :

1. s’identifier ;
2. sélectionner Dépôt ;
3. insérer les billets ;
4. consulter le montant détecté ;
5. confirmer sur le DAB ;
6. recevoir un reçu ;
7. voir l’opération dans l’application.

Les billets suspects ou non reconnus doivent suivre un traitement séparé.

---

# 16. Retrait au DAB

Méthodes possibles :

- carte Mansa + PIN ;
- QR sécurisé ;
- code de retrait ;
- authentification mobile lorsque disponible.

L’application doit afficher :

- montant ;
- frais ;
- DAB ;
- date ;
- statut ;
- reçu ;
- procédure si les billets ne sont pas délivrés.

---

# 17. Fonctionnement sans Internet

## 17.1 Client hors ligne

Le client peut recevoir :

- un SMS de confirmation ;
- un OTP ;
- un reçu papier ;
- un code USSD ;
- une notification différée.

---

## 17.2 Synchronisation ultérieure

À la reconnexion, l’application doit :

- actualiser le solde ;
- récupérer les nouvelles opérations ;
- récupérer les reçus ;
- éviter les doublons ;
- conserver les références ;
- informer le client des opérations effectuées hors connexion.

---

# 18. Notifications Cash Network

Types :

- dépôt reçu ;
- retrait demandé ;
- retrait autorisé ;
- retrait terminé ;
- retrait expiré ;
- opération échouée ;
- reçu disponible ;
- agent indisponible ;
- DAB indisponible ;
- frais modifiés ;
- incident ;
- opération en révision.

---

# 19. SMS

Le SMS peut être utilisé pour :

- confirmer un dépôt ;
- envoyer un OTP ;
- confirmer un retrait ;
- alerter sur une opération ;
- communiquer une référence ;
- signaler un échec ;
- informer d’un remboursement.

Le SMS ne doit pas contenir de secret complet.

---

# 20. Reçus Cash Network

Le reçu doit contenir :

- identifiant unique ;
- référence publique ;
- type d’opération ;
- montant ;
- frais ;
- total ;
- devise ;
- date ;
- heure ;
- statut ;
- agent ou DAB ;
- point de service ;
- méthode ;
- QR de vérification éventuel ;
- coordonnées du support ;
- mention de contestation.

---

# 21. Partage du reçu

Le client doit pouvoir :

- télécharger ;
- partager ;
- imprimer ;
- envoyer par e-mail ;
- retrouver dans l’historique.

Les données sensibles doivent être masquées.

---

# 22. Historique Cash Network

Nouveaux types d’opérations :

- CASH_DEPOSIT_AGENT ;
- CASH_WITHDRAWAL_AGENT ;
- CASH_DEPOSIT_ATM ;
- CASH_WITHDRAWAL_ATM ;
- CASH_WITHDRAWAL_QR ;
- CASH_WITHDRAWAL_CODE ;
- CASH_DEPOSIT_CARD ;
- CASH_DEPOSIT_MOBILE_MONEY.

---

# 23. Filtres d’historique

Le client peut filtrer par :

- dépôt ;
- retrait ;
- agent ;
- DAB ;
- date ;
- montant ;
- statut ;
- ville ;
- méthode ;
- référence.

---

# 24. Détail d’une opération

Afficher :

- référence ;
- type ;
- montant ;
- frais ;
- total ;
- agent ou DAB ;
- localisation ;
- date ;
- statut ;
- méthode d’authentification sans exposer le secret ;
- reçu ;
- assistance ;
- contestation.

---

# 25. Frais affichés côté client

Avant un retrait, le client doit voir :

- montant demandé ;
- frais ;
- taxes éventuelles ;
- total débité ;
- montant remis ;
- devise ;
- conditions de l’opération.

Pour un dépôt :

- dépôt gratuit ou payant ;
- frais éventuels ;
- montant crédité ;
- montant remis en espèces.

---

# 26. Frais dynamiques

L’application doit accepter des frais variables selon :

- pays ;
- région ;
- ville ;
- type d’agent ;
- type d’opération ;
- montant ;
- jour ;
- heure ;
- campagne ;
- niveau du client ;
- moyen d’authentification ;
- partenaire.

Aucune valeur ne doit être codée en dur dans l’application.

---

# 27. Promotions

L’application peut afficher :

- dépôt gratuit ;
- retrait à tarif réduit ;
- bonus temporaire ;
- campagne locale ;
- promotion partenaire ;
- promotion par segment.

Elle doit afficher :

- période ;
- conditions ;
- zone ;
- plafond ;
- éligibilité.

---

# 28. Sécurité côté client

L’application doit :

- vérifier le statut de la session ;
- protéger les codes ;
- masquer les secrets ;
- bloquer les captures d’écran lorsque nécessaire ;
- limiter les tentatives ;
- révoquer les codes expirés ;
- détecter les appareils compromis ;
- afficher des avertissements contre la fraude.

---

# 29. Avertissements contre la fraude

Exemples :

- ne jamais communiquer son PIN à l’agent ;
- vérifier le nom et le montant ;
- ne jamais remettre de frais non affichés ;
- attendre le reçu ;
- ne pas quitter le point avant confirmation ;
- signaler immédiatement une opération inconnue.

---

# 30. Contestation

Le client doit pouvoir signaler :

- dépôt non crédité ;
- montant incorrect ;
- retrait débité sans espèces ;
- retrait partiel ;
- frais incorrects ;
- faux agent ;
- reçu absent ;
- opération inconnue ;
- comportement suspect.

---

# 31. Dossier de contestation

Le formulaire peut préremplir :

- référence ;
- agent ou DAB ;
- montant ;
- date ;
- heure ;
- localisation ;
- statut ;
- appareil ;
- version de l’application.

---

# 32. Paramètres Cash Network

L’utilisateur peut gérer :

- notifications Cash Network ;
- réception par SMS ;
- reçu numérique par défaut ;
- affichage des agents proches ;
- géolocalisation ;
- alertes de sécurité ;
- langue des reçus ;
- partage des reçus.

Les notifications de sécurité essentielles ne doivent pas être désactivables.

---

# 33. Jini et Cash Network

Jini peut :

- trouver un agent ;
- trouver un DAB ;
- expliquer un dépôt ;
- expliquer un retrait ;
- retrouver un reçu ;
- expliquer les frais ;
- guider une contestation ;
- signaler un incident.

Jini ne doit pas :

- confirmer seul un retrait ;
- révéler un code ;
- modifier un statut financier ;
- garantir la disponibilité physique des espèces.

---

# 34. Accessibilité

Les écrans Cash Network doivent prévoir :

- gros boutons ;
- texte lisible ;
- lecteur d’écran ;
- contraste ;
- itinéraire simple ;
- langage clair ;
- recours aux SMS ;
- alternatives sans géolocalisation ;
- alternatives sans smartphone connecté.

---

# 35. Connexion faible

Mesures :

- carte légère ;
- liste textuelle alternative ;
- cache des points récents ;
- chargement progressif ;
- reprise automatique ;
- affichage des dernières données connues ;
- SMS de confirmation ;
- limitation des images.

---

# 36. API côté Client

Exemples :

```http
GET    /cash-network/agents
GET    /cash-network/agents/{id}
GET    /cash-network/atms
GET    /cash-network/atms/{id}
GET    /cash-network/fees/preview
GET    /cash-network/transactions
GET    /cash-network/transactions/{id}
GET    /cash-network/receipts/{id}
POST   /cash-network/withdrawal-codes
POST   /cash-network/withdrawal-codes/{id}/cancel
POST   /cash-network/disputes
```

L’application Client ne crée pas directement une écriture ledger.

---

# 37. Analytics

Événements possibles :

```text
client_cash_network_opened
client_agent_search_started
client_agent_search_completed
client_atm_search_completed
client_cash_deposit_received
client_cash_withdrawal_started
client_cash_withdrawal_authenticated
client_cash_withdrawal_completed
client_withdrawal_code_created
client_withdrawal_code_cancelled
client_cash_receipt_opened
client_cash_dispute_created
```

---

# 38. Données analytics interdites

Ne pas transmettre :

- PIN ;
- OTP ;
- code de retrait complet ;
- numéro complet de carte ;
- secret ;
- coordonnées précises non nécessaires ;
- données biométriques ;
- informations internes de caisse de l’agent.

---

# 39. Tests

- tests de recherche agent ;
- tests de recherche DAB ;
- tests de géolocalisation ;
- tests sans géolocalisation ;
- tests de dépôt sans confirmation client ;
- tests de retrait avec authentification ;
- tests PIN terminal ;
- tests OTP SMS ;
- tests USSD ;
- tests carte + PIN ;
- tests QR ;
- tests code sécurisé ;
- tests hors ligne ;
- tests de synchronisation ;
- tests de frais dynamiques ;
- tests de reçus ;
- tests de contestation ;
- tests de sécurité ;
- tests d’accessibilité ;
- tests multi-pays ;
- tests multi-langues.

---

# 40. Règles métier

1. Un dépôt chez un agent ne demande pas de confirmation dans l’application Client.
2. Un dépôt ne doit être affiché comme terminé qu’après confirmation du backend.
3. Un retrait exige une authentification du client.
4. L’agent ne remet les espèces qu’après autorisation du serveur.
5. Le téléphone du client peut être hors ligne.
6. Les SMS peuvent servir à l’authentification et à la confirmation.
7. Les reçus sont générés par le backend.
8. Les frais sont récupérés depuis le moteur de tarification.
9. Aucun frais n’est codé en dur.
10. Les méthodes disponibles dépendent du pays et du partenaire.
11. Les QR et codes sont temporaires et protégés contre le rejeu.
12. L’historique est synchronisé de manière idempotente.
13. Les données internes de l’agent ne sont pas exposées.
14. La localisation reste facultative.
15. Une alternative par ville ou quartier est toujours proposée.
16. Les contestations sont reliées à l’opération d’origine.
17. Les notifications de sécurité essentielles restent actives.
18. Jini reste soumis aux permissions.
19. L’application ne modifie jamais directement le ledger.
20. Toutes les actions sensibles sont auditables côté backend.

---

# 41. Critères d’acceptation

Le complément Cash Network de l’application Client est validé lorsque :

- l’utilisateur peut trouver un agent ;
- l’utilisateur peut trouver un DAB ;
- la recherche fonctionne avec ou sans géolocalisation ;
- les services disponibles sont visibles ;
- le dépôt fonctionne sans confirmation dans l’application ;
- le retrait exige une authentification ;
- le retrait fonctionne même si le téléphone n’a pas Internet ;
- les SMS et reçus sont disponibles ;
- les statuts sont fidèles au backend ;
- les frais sont affichés avant l’opération ;
- les frais sont dynamiques ;
- les reçus sont consultables ;
- l’historique distingue les opérations Cash Network ;
- les QR et codes expirent correctement ;
- les contestations sont accessibles ;
- les données sensibles sont protégées ;
- les écrans restent accessibles sur réseau faible ;
- les langues sont prises en charge ;
- les tests couvrent les parcours critiques.
