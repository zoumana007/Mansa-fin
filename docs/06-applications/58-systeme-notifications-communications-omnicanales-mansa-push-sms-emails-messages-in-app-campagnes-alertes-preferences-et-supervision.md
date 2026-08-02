# 58 — Système de notifications et communications omnicanales Mansa : push, SMS, e-mails, messages in-app, campagnes, alertes, préférences et supervision

## 1. Objet du document

Ce document définit l’architecture officielle du **Système de notifications et communications omnicanales Mansa**.

Ce système centralise toutes les communications envoyées par l’écosystème Mansa vers :

- les clients particuliers ;
- les commerçants ;
- les agents Cash Network ;
- les entreprises ;
- les employés ;
- les établissements scolaires ;
- les étudiants ;
- les parents ;
- les institutions publiques ;
- les agents publics ;
- les banques ;
- les opérateurs Mobile Money ;
- les partenaires financiers ;
- les développeurs ;
- les administrateurs internes ;
- les équipes support ;
- les équipes sécurité ;
- les équipes Finance.

Le système couvre notamment :

- les notifications push ;
- les SMS ;
- les e-mails ;
- les messages dans les applications ;
- les bannières ;
- les centres de notifications ;
- les messages transactionnels ;
- les alertes de sécurité ;
- les rappels ;
- les campagnes ;
- les communications réglementaires ;
- les notifications de support ;
- les notifications de paiement ;
- les notifications de carte ;
- les notifications d’agent ;
- les notifications TPE et DAB ;
- les notifications de bourse ;
- les notifications scolaires ;
- les notifications d’entreprise ;
- les notifications institutionnelles ;
- les webhooks partenaires ;
- les modèles ;
- les traductions ;
- les préférences ;
- les consentements ;
- les fournisseurs ;
- la délivrabilité ;
- les reprises ;
- les priorités ;
- les coûts ;
- les rapports ;
- les audits ;
- la sécurité ;
- le multi-pays ;
- le multi-langues ;
- le réseau faible.

L’objectif est de fournir un moteur unique capable de :

- envoyer le bon message ;
- au bon destinataire ;
- par le bon canal ;
- dans la bonne langue ;
- au bon moment ;
- avec le bon niveau de priorité ;
- sans exposer de données sensibles ;
- avec une traçabilité complète ;
- avec des fournisseurs de secours ;
- avec une gestion dynamique des règles ;
- avec une supervision centralisée.

---

# 2. Principes fondamentaux

## 2.1 Une seule plateforme de communication pour tout Mansa

Toutes les applications et tous les services Mansa doivent utiliser le même moteur central.

Ils ne doivent pas intégrer directement un fournisseur SMS, e-mail ou push sans passer par la plateforme de communication.

Cela permet de centraliser :

- les modèles ;
- les fournisseurs ;
- les coûts ;
- les langues ;
- les consentements ;
- les règles ;
- la sécurité ;
- les rapports ;
- les audits ;
- les reprises ;
- les incidents.

---

## 2.2 Aucun fournisseur ne doit être codé en dur

Le système doit permettre d’ajouter, modifier, activer, désactiver ou remplacer :

- un fournisseur SMS ;
- un fournisseur e-mail ;
- un fournisseur push ;
- un fournisseur de messagerie ;
- un fournisseur vocal ;
- un fournisseur local ;
- un fournisseur international ;
- un fournisseur de secours.

---

## 2.3 Les communications critiques ne dépendent pas d’un seul canal

Pour les messages sensibles, le système doit pouvoir utiliser plusieurs canaux.

Exemple :

```text
Notification push
→ si non délivrée : SMS
→ si SMS impossible : e-mail
→ message visible dans l’application
```

La stratégie doit être configurable.

---

## 2.4 Les préférences utilisateur doivent être respectées

Le système doit distinguer :

- communication obligatoire ;
- communication transactionnelle ;
- communication de sécurité ;
- communication opérationnelle ;
- communication de service ;
- communication commerciale ;
- campagne marketing.

Les communications obligatoires et de sécurité peuvent être exemptées de certaines préférences selon le cadre applicable.

---

## 2.5 Aucune donnée sensible inutile ne doit être envoyée

Les messages ne doivent pas contenir en clair :

- PIN ;
- OTP complet dans les journaux ;
- CVV ;
- numéro complet de carte ;
- mot de passe ;
- solde détaillé non nécessaire ;
- document complet ;
- clé privée ;
- secret API ;
- information médicale ;
- données biométriques ;
- identité complète inutile.

---

## 2.6 Toute communication doit être traçable

Chaque envoi doit enregistrer :

- événement source ;
- destinataire ;
- canal ;
- fournisseur ;
- modèle ;
- langue ;
- pays ;
- date ;
- heure ;
- priorité ;
- statut ;
- tentative ;
- coût ;
- résultat ;
- erreur ;
- corrélation ;
- consentement applicable.

---

# 3. Types de communications

Le système doit distinguer :

- transactionnelle ;
- sécurité ;
- authentification ;
- réglementaire ;
- opérationnelle ;
- support ;
- commerciale ;
- informative ;
- urgente ;
- maintenance ;
- incident ;
- rappel ;
- confirmation ;
- campagne.

---

# 4. Canaux

Canaux principaux :

- push mobile ;
- SMS ;
- e-mail ;
- message in-app ;
- bannière ;
- centre de notifications ;
- notification web ;
- message TPE ;
- message DAB ;
- webhook ;
- messagerie externe autorisée ;
- appel vocal automatisé ;
- impression de reçu ;
- USSD lorsque disponible.

---

# 5. Technologie

Technologies recommandées :

```text
NestJS
TypeScript
PostgreSQL
Redis
Message Queue
Event Bus
```

Composants associés :

- moteur de règles ;
- moteur de modèles ;
- gestion des traductions ;
- file d’attente ;
- retries ;
- idempotence ;
- fallback ;
- fournisseurs multiples ;
- observabilité ;
- reporting ;
- audit ;
- sécurité ;
- rate limiting ;
- scheduler.

---

# 6. Architecture du système

Structure recommandée :

```text
src/
├── events/
├── notifications/
├── messages/
├── channels/
├── push/
├── sms/
├── email/
├── in-app/
├── banners/
├── webhooks/
├── voice/
├── ussd/
├── providers/
├── routing/
├── fallback/
├── templates/
├── translations/
├── preferences/
├── consent/
├── campaigns/
├── scheduling/
├── queues/
├── retries/
├── delivery/
├── tracking/
├── costs/
├── suppression/
├── throttling/
├── reports/
├── approvals/
├── audit/
├── security/
└── settings/
```

---

# 7. Sources d’événements

Le système peut recevoir des événements depuis :

- application Client ;
- application Commerce ;
- application Agent ;
- application TPE ;
- application Admin Lite ;
- Hub ;
- site officiel ;
- portail Admin ;
- portail développeurs ;
- portail Institutions ;
- portail Banques ;
- portail Entreprises ;
- portail Écoles ;
- portail Support ;
- console Sécurité ;
- console Finance ;
- backend central ;
- ledger ;
- moteur de risque ;
- moteur KYC ;
- moteur KYB ;
- partenaires ;
- banques ;
- Mobile Money ;
- réseaux cartes ;
- DAB ;
- TPE ;
- tâches programmées.

---

# 8. Événement de notification

Chaque événement doit contenir :

- identifiant ;
- type ;
- source ;
- destinataire ;
- organisation éventuelle ;
- pays ;
- langue ;
- priorité ;
- canal préféré ;
- contexte ;
- référence métier ;
- date ;
- expiration ;
- politique ;
- données autorisées ;
- clé d’idempotence.

---

# 9. Exemples d’événements

```text
payment.completed
payment.failed
transfer.completed
transfer.failed
deposit.completed
withdrawal.completed
card.blocked
card.transaction.declined
account.login.new_device
security.alert
kyc.additional_information_required
merchant.settlement.completed
agent.liquidity.low
atm.cash_low
support.ticket.updated
school.invoice.due
scholarship.paid
company.salary.paid
public_service.reference.created
```

---

# 10. Priorités

Niveaux possibles :

- BULK ;
- LOW ;
- NORMAL ;
- HIGH ;
- URGENT ;
- CRITICAL.

---

# 11. Règles de priorité

La priorité peut dépendre :

- type d’événement ;
- impact ;
- montant ;
- sécurité ;
- délai ;
- pays ;
- client ;
- partenaire ;
- incident ;
- produit ;
- règlementation ;
- heure d’expiration.

---

# 12. Catégories de messages

Exemples :

- authentification ;
- paiement ;
- transfert ;
- carte ;
- Cash Network ;
- TPE ;
- DAB ;
- commerçant ;
- entreprise ;
- scolarité ;
- bourse ;
- institution ;
- banque ;
- support ;
- sécurité ;
- finance ;
- campagne ;
- maintenance.

---

# 13. Notification push

Le système doit gérer :

- iOS ;
- Android ;
- web push ;
- appareil ;
- token ;
- application ;
- environnement ;
- langue ;
- pays ;
- statut ;
- expiration ;
- priorité ;
- action profonde ;
- image autorisée ;
- badge ;
- son ;
- catégorie.

---

# 14. Tokens push

Chaque token doit être lié à :

- utilisateur ;
- appareil ;
- application ;
- plateforme ;
- environnement ;
- date de création ;
- dernière utilisation ;
- langue ;
- statut ;
- version ;
- révocation.

---

# 15. Statuts d’un token push

- ACTIVE ;
- EXPIRED ;
- INVALID ;
- REVOKED ;
- UNREGISTERED ;
- UNDER_REVIEW.

---

# 16. Liens profonds

Une notification peut ouvrir directement :

- une transaction ;
- une carte ;
- un ticket ;
- une facture ;
- une bourse ;
- un reçu ;
- une campagne ;
- un profil ;
- une alerte ;
- une demande ;
- un document.

Le lien profond doit respecter les permissions de l’utilisateur.

---

# 17. Notifications push sensibles

Le contenu visible sur écran verrouillé doit être limité.

Exemples :

- « Vous avez reçu un paiement » ;
- « Une opération nécessite votre attention » ;
- « Votre carte a été temporairement bloquée ».

Le détail doit être consulté après authentification.

---

# 18. SMS

Le module SMS doit gérer :

- expéditeur ;
- pays ;
- opérateur ;
- encodage ;
- longueur ;
- nombre de segments ;
- coût ;
- statut ;
- rapport de livraison ;
- fournisseur ;
- fallback ;
- expiration ;
- langue.

---

# 19. Cas d’usage SMS

Exemples :

- OTP ;
- transaction ;
- absence d’Internet ;
- rappel ;
- sécurité ;
- ticket support ;
- retrait ;
- dépôt ;
- bourse ;
- échéance ;
- notification réglementaire ;
- incident.

---

# 20. SMS en réseau faible

Le SMS doit pouvoir servir de canal principal ou de secours lorsque :

- le téléphone n’a pas Internet ;
- la notification push échoue ;
- l’application n’est pas installée ;
- le client utilise un téléphone simple ;
- le pays ou la zone possède une couverture limitée.

---

# 21. E-mails

Le module e-mail doit gérer :

- expéditeur ;
- domaine ;
- réputation ;
- modèle ;
- objet ;
- contenu ;
- HTML ;
- texte brut ;
- pièce jointe autorisée ;
- tracking ;
- bounce ;
- plainte ;
- désinscription ;
- fournisseur ;
- fallback ;
- langue ;
- pays.

---

# 22. Cas d’usage e-mail

Exemples :

- reçu ;
- relevé ;
- rapport ;
- contrat ;
- document ;
- invitation ;
- onboarding ;
- sécurité ;
- support ;
- notification entreprise ;
- communication partenaire ;
- campagne ;
- changement réglementaire.

---

# 23. Messages in-app

Le centre de notifications doit permettre :

- liste chronologique ;
- non-lu ;
- lu ;
- archivé ;
- supprimé côté utilisateur ;
- priorité ;
- catégorie ;
- lien profond ;
- filtre ;
- recherche ;
- expiration ;
- action ;
- contenu riche ;
- synchronisation multi-appareils.

---

# 24. Statuts d’un message in-app

- CREATED ;
- PUBLISHED ;
- DELIVERED ;
- READ ;
- ARCHIVED ;
- EXPIRED ;
- REVOKED.

---

# 25. Bannières

Le système peut afficher :

- bannière d’information ;
- bannière de maintenance ;
- bannière d’incident ;
- bannière réglementaire ;
- bannière commerciale ;
- bannière de sécurité ;
- bannière de mise à jour obligatoire.

---

# 26. Périmètre d’une bannière

Une bannière peut être limitée par :

- application ;
- pays ;
- ville ;
- langue ;
- rôle ;
- segment ;
- version ;
- OS ;
- produit ;
- partenaire ;
- organisation ;
- date ;
- heure ;
- environnement.

---

# 27. Messages TPE

Les terminaux peuvent recevoir :

- maintenance ;
- mise à jour ;
- panne ;
- certificat expirant ;
- formation ;
- changement de frais ;
- message urgent ;
- statut réseau ;
- campagne commerçant ;
- rappel de clôture.

---

# 28. Messages DAB

Les DAB peuvent afficher ou recevoir :

- maintenance ;
- indisponibilité ;
- coupures manquantes ;
- limite temporaire ;
- message institutionnel ;
- sécurité ;
- assistance ;
- langue ;
- incident.

---

# 29. Webhooks

Le système doit permettre d’envoyer des événements aux partenaires.

Chaque webhook doit contenir :

- type ;
- version ;
- identifiant ;
- horodatage ;
- ressource ;
- référence ;
- signature ;
- tentative ;
- statut ;
- clé d’idempotence.

---

# 30. Signature des webhooks

Les webhooks doivent utiliser :

```http
X-Mansa-Event
X-Mansa-Delivery
X-Mansa-Timestamp
X-Mansa-Signature
X-Mansa-Version
```

---

# 31. Réessai des webhooks

Stratégie possible :

```text
Tentative 1 : immédiate
Tentative 2 : +1 minute
Tentative 3 : +5 minutes
Tentative 4 : +30 minutes
Tentative 5 : +2 heures
Tentative 6 : +24 heures
```

La stratégie doit être configurable.

---

# 32. Appels vocaux automatisés

Le système peut utiliser un appel vocal pour :

- urgence ;
- sécurité ;
- OTP vocal ;
- rappel important ;
- incident ;
- client malvoyant ;
- échec répété des autres canaux.

---

# 33. USSD

Lorsque disponible, l’USSD peut servir à :

- confirmer une action ;
- consulter un statut ;
- recevoir un message ;
- obtenir un code ;
- lancer une procédure ;
- accéder à un service sans Internet.

---

# 34. Modèles de messages

Chaque modèle doit contenir :

- code ;
- nom ;
- catégorie ;
- canal ;
- langue ;
- pays ;
- sujet éventuel ;
- contenu ;
- variables ;
- statut ;
- version ;
- auteur ;
- approbateur ;
- date d’effet ;
- date d’expiration ;
- historique.

---

# 35. Variables de modèles

Exemples :

```text
{{first_name}}
{{transaction_amount}}
{{currency}}
{{transaction_reference}}
{{merchant_name}}
{{masked_card}}
{{support_ticket_number}}
{{due_date}}
{{institution_name}}
{{deep_link}}
```

Les variables doivent être limitées à une liste autorisée.

---

# 36. Validation des variables

Le système doit empêcher :

- variable inconnue ;
- secret ;
- numéro complet de carte ;
- PIN ;
- CVV ;
- mot de passe ;
- contenu non autorisé ;
- injection ;
- HTML dangereux ;
- lien non approuvé.

---

# 37. Versionnement des modèles

Chaque modification doit créer une nouvelle version.

Le système doit conserver :

- ancienne version ;
- nouvelle version ;
- auteur ;
- approbateur ;
- date ;
- motif ;
- périmètre ;
- statut ;
- résultats de test.

---

# 38. Statuts d’un modèle

- DRAFT ;
- REVIEW ;
- APPROVED ;
- SCHEDULED ;
- ACTIVE ;
- SUSPENDED ;
- EXPIRED ;
- REPLACED ;
- ARCHIVED.

---

# 39. Prévisualisation

Avant publication, l’administration doit pouvoir prévisualiser :

- push ;
- SMS ;
- e-mail ;
- in-app ;
- bannière ;
- TPE ;
- DAB ;
- mobile ;
- web ;
- langues ;
- tailles d’écran.

---

# 40. Tests de modèles

Le système doit permettre :

- envoi test ;
- destinataire interne ;
- environnement Démo ;
- environnement Recette ;
- contrôle des variables ;
- contrôle des liens ;
- contrôle du rendu ;
- vérification de la langue ;
- vérification de la longueur SMS.

---

# 41. Traductions

Chaque modèle doit pouvoir être traduit selon :

- langue ;
- pays ;
- variante locale ;
- canal ;
- ton ;
- contexte ;
- obligation réglementaire.

---

# 42. Langues

Le système doit être préparé pour :

- français ;
- bambara ;
- anglais ;
- arabe ;
- langues nationales ;
- langues des futurs pays.

---

# 43. Langue de communication

La langue peut être déterminée par :

- préférence utilisateur ;
- langue de l’application ;
- pays ;
- canal ;
- langue du service ;
- langue du contrat ;
- langue de secours.

---

# 44. Langue de secours

Exemple :

```text
Bambara
→ si modèle absent : français
→ si français absent : anglais
```

La chaîne de secours doit être configurable.

---

# 45. Préférences utilisateur

L’utilisateur peut gérer :

- push ;
- SMS ;
- e-mail ;
- in-app ;
- campagnes ;
- offres ;
- rappels ;
- relevés ;
- sécurité ;
- fréquence ;
- heures préférées ;
- langue.

---

# 46. Communications non désactivables

Certaines communications peuvent rester obligatoires :

- sécurité ;
- authentification ;
- confirmation de transaction ;
- changement contractuel ;
- incident important ;
- communication réglementaire ;
- blocage ;
- litige ;
- document obligatoire.

---

# 47. Consentement

Le système doit enregistrer :

- utilisateur ;
- type de consentement ;
- canal ;
- finalité ;
- version ;
- pays ;
- date ;
- heure ;
- source ;
- retrait ;
- preuve ;
- expiration éventuelle.

---

# 48. Retrait du consentement

Le retrait doit :

- prendre effet rapidement ;
- être historisé ;
- ne pas bloquer les communications obligatoires ;
- être synchronisé entre applications ;
- être transmis aux systèmes concernés.

---

# 49. Liste de suppression

Le système doit gérer :

- e-mail en bounce permanent ;
- numéro invalide ;
- plainte spam ;
- désinscription ;
- contact interdit ;
- canal révoqué ;
- utilisateur décédé selon source autorisée ;
- compte fermé ;
- blocage réglementaire.

---

# 50. Campagnes

Le moteur de campagne doit permettre :

- création ;
- ciblage ;
- modèle ;
- canal ;
- langue ;
- budget ;
- calendrier ;
- validation ;
- test ;
- envoi ;
- pause ;
- arrêt ;
- rapports ;
- analyse.

---

# 51. Types de campagnes

- onboarding ;
- activation ;
- réengagement ;
- promotion ;
- fidélité ;
- commerçant ;
- agent ;
- entreprise ;
- étudiant ;
- institution ;
- sécurité ;
- prévention fraude ;
- nouvelle fonctionnalité ;
- information réglementaire.

---

# 52. Segmentation

Une campagne peut cibler selon :

- pays ;
- région ;
- ville ;
- langue ;
- âge selon règles ;
- type de compte ;
- niveau KYC ;
- activité ;
- produit utilisé ;
- commerçant ;
- agent ;
- entreprise ;
- établissement ;
- historique ;
- fidélité ;
- appareil ;
- version d’application.

---

# 53. Exclusions de campagne

Le système doit pouvoir exclure :

- utilisateur désinscrit ;
- compte suspendu ;
- mineur selon règles ;
- utilisateur sensible ;
- utilisateur récemment contacté ;
- utilisateur sans consentement ;
- pays non autorisé ;
- canal indisponible ;
- liste de suppression ;
- segment fraude.

---

# 54. Fréquence maximale

Le système doit pouvoir limiter :

- nombre de messages par jour ;
- nombre par semaine ;
- nombre par campagne ;
- nombre par canal ;
- répétition du même message ;
- relance ;
- période de repos.

---

# 55. Programmation

Un envoi peut être :

- immédiat ;
- programmé ;
- récurrent ;
- déclenché par événement ;
- déclenché par condition ;
- retardé ;
- dépendant du fuseau horaire ;
- limité à des heures autorisées.

---

# 56. Heures silencieuses

Le système doit gérer des heures silencieuses selon :

- pays ;
- canal ;
- type de message ;
- préférence ;
- réglementation ;
- urgence ;
- fuseau horaire.

Les alertes critiques peuvent contourner les heures silencieuses selon règle.

---

# 57. Orchestration multicanale

Exemple :

```text
Événement : transfert terminé
1. Message in-app immédiat
2. Push immédiate
3. SMS uniquement si push non délivrée après 2 minutes
4. E-mail uniquement si montant supérieur au seuil configuré
```

---

# 58. Fallback

Le fallback peut dépendre :

- échec ;
- délai ;
- canal ;
- priorité ;
- pays ;
- coût ;
- consentement ;
- réseau ;
- type de téléphone ;
- disponibilité fournisseur.

---

# 59. Fournisseurs

Chaque fournisseur doit avoir :

- nom ;
- canal ;
- pays ;
- devises ;
- coût ;
- capacité ;
- SLA ;
- taux de succès ;
- identifiants sécurisés ;
- statut ;
- priorité ;
- calendrier ;
- limites ;
- incidents ;
- historique.

---

# 60. Statuts d’un fournisseur

- DRAFT ;
- TESTING ;
- ACTIVE ;
- DEGRADED ;
- SUSPENDED ;
- MAINTENANCE ;
- DISABLED ;
- TERMINATED.

---

# 61. Routage fournisseur

Le routage peut dépendre :

- pays ;
- opérateur ;
- canal ;
- coût ;
- qualité ;
- disponibilité ;
- priorité ;
- volume ;
- heure ;
- contrat ;
- taux de succès.

---

# 62. Fournisseur principal et secours

Le système doit pouvoir configurer :

- fournisseur principal ;
- fournisseur secondaire ;
- fournisseur local ;
- fournisseur international ;
- bascule automatique ;
- bascule manuelle ;
- retour automatique ;
- contrôle de santé.

---

# 63. Supervision des fournisseurs

Le système doit suivre :

- disponibilité ;
- latence ;
- taux de succès ;
- taux d’échec ;
- erreurs ;
- coût ;
- volume ;
- files ;
- incidents ;
- SLA ;
- qualité par pays ;
- qualité par opérateur.

---

# 64. Délivrabilité

Statuts possibles :

- CREATED ;
- QUEUED ;
- ACCEPTED ;
- SENT ;
- DELIVERED ;
- READ ;
- CLICKED ;
- FAILED ;
- REJECTED ;
- EXPIRED ;
- BOUNCED ;
- SUPPRESSED ;
- CANCELLED.

---

# 65. Rapports de livraison

Le système doit collecter :

- statut ;
- fournisseur ;
- heure d’envoi ;
- heure de livraison ;
- erreur ;
- opérateur ;
- pays ;
- canal ;
- coût ;
- tentative ;
- identifiant externe.

---

# 66. Reprises

Le système doit pouvoir relancer :

- erreur temporaire ;
- timeout ;
- fournisseur indisponible ;
- rate limit ;
- problème réseau ;
- erreur partenaire ;
- livraison inconnue.

---

# 67. Idempotence

Le même événement ne doit pas produire plusieurs notifications identiques non souhaitées.

Chaque demande doit pouvoir utiliser :

```http
Idempotency-Key
X-Request-Id
X-Correlation-Id
```

---

# 68. Déduplication

Le système doit détecter :

- même événement ;
- même utilisateur ;
- même modèle ;
- même référence ;
- même canal ;
- même période ;
- même campagne.

---

# 69. Files d’attente

Files possibles :

- critique ;
- sécurité ;
- transactionnelle ;
- opérationnelle ;
- support ;
- campagne ;
- bulk ;
- webhooks ;
- retry ;
- dead-letter.

---

# 70. Dead-letter queue

Les messages définitivement échoués doivent être placés dans une file dédiée avec :

- événement ;
- destinataire ;
- canal ;
- fournisseur ;
- tentatives ;
- erreurs ;
- date ;
- responsable ;
- action ;
- statut.

---

# 71. Quotas et throttling

Le système doit appliquer :

- quota par fournisseur ;
- quota par pays ;
- quota par utilisateur ;
- quota par application ;
- quota par campagne ;
- quota par partenaire ;
- limite par seconde ;
- limite par minute ;
- limite par jour.

---

# 72. Gestion des coûts

Le système doit suivre :

- coût par SMS ;
- coût par e-mail ;
- coût par push ;
- coût par appel ;
- coût par pays ;
- coût par fournisseur ;
- coût par campagne ;
- coût par produit ;
- coût par client ;
- coût par partenaire.

---

# 73. Budgets de communication

Un budget peut être défini par :

- pays ;
- équipe ;
- campagne ;
- produit ;
- partenaire ;
- canal ;
- mois ;
- année ;
- organisation.

---

# 74. Alertes de coût

Le système doit alerter en cas de :

- dépassement de budget ;
- coût unitaire inhabituel ;
- hausse soudaine ;
- fournisseur trop cher ;
- volume anormal ;
- boucle d’envoi ;
- campagne excessive ;
- retries trop nombreux.

---

# 75. Pièces jointes

Les e-mails ou messages peuvent inclure :

- reçu ;
- relevé ;
- facture ;
- rapport ;
- document ;
- contrat ;
- attestation.

Les pièces doivent être :

- chiffrées ;
- temporaires ;
- signées ;
- protégées ;
- limitées ;
- auditables.

---

# 76. Liens sécurisés

Les documents sensibles doivent de préférence être accessibles par un lien sécurisé avec :

- expiration ;
- authentification ;
- usage unique ;
- permission ;
- journalisation ;
- révocation.

---

# 77. OTP

Le système peut gérer :

- OTP SMS ;
- OTP e-mail ;
- OTP vocal ;
- OTP push ;
- code à usage unique ;
- durée de validité ;
- nombre de tentatives ;
- nouvelle émission ;
- verrouillage.

---

# 78. Protection des OTP

Les OTP doivent être :

- générés de manière sécurisée ;
- expirants ;
- non réutilisables ;
- masqués dans les journaux ;
- limités en tentatives ;
- liés à une action ;
- liés à un utilisateur ;
- protégés contre le brute force.

---

# 79. Notifications de sécurité

Exemples :

- nouvel appareil ;
- nouvelle connexion ;
- mot de passe modifié ;
- téléphone modifié ;
- carte bloquée ;
- bénéficiaire ajouté ;
- transfert suspect ;
- compte restreint ;
- session révoquée ;
- tentative échouée ;
- clé API modifiée.

---

# 80. Notifications financières

Exemples :

- paiement reçu ;
- paiement refusé ;
- transfert envoyé ;
- transfert reçu ;
- dépôt effectué ;
- retrait effectué ;
- remboursement ;
- commission ;
- règlement ;
- salaire ;
- bourse ;
- facture payée ;
- prélèvement.

---

# 81. Notifications Cash Network

Exemples :

- float faible ;
- demande de liquidité ;
- dépôt ;
- retrait ;
- caisse ouverte ;
- caisse fermée ;
- écart de caisse ;
- commission ;
- incident ;
- suspension.

---

# 82. Notifications commerçants

Exemples :

- paiement reçu ;
- remboursement ;
- règlement ;
- chargeback ;
- terminal hors ligne ;
- nouvelle commande ;
- stock faible ;
- facture ;
- rapport ;
- campagne.

---

# 83. Notifications entreprises

Exemples :

- salaire versé ;
- paie rejetée ;
- note de frais ;
- budget dépassé ;
- carte professionnelle bloquée ;
- fournisseur payé ;
- validation requise ;
- rapport disponible.

---

# 84. Notifications scolaires

Exemples :

- inscription ;
- facture ;
- échéance ;
- bourse ;
- carte disponible ;
- logement attribué ;
- document généré ;
- transport ;
- remboursement.

---

# 85. Notifications institutionnelles

Exemples :

- référence de paiement ;
- amende ;
- taxe ;
- reçu ;
- recours ;
- aide ;
- versement ;
- carte ;
- document officiel ;
- changement réglementaire.

---

# 86. Notifications partenaires

Exemples :

- webhook échoué ;
- certificat expirant ;
- règlement ;
- fichier rejeté ;
- écart ;
- incident ;
- maintenance ;
- changement d’API ;
- changement de frais ;
- dépassement de quota.

---

# 87. Notifications administratives

Exemples :

- validation requise ;
- incident ;
- export ;
- changement de rôle ;
- modification de paramètre ;
- action critique ;
- clôture ;
- rapport ;
- anomalie ;
- maintenance.

---

# 88. Administration centrale

L’administration peut gérer :

- fournisseurs ;
- canaux ;
- modèles ;
- traductions ;
- règles ;
- campagnes ;
- préférences ;
- consentements ;
- coûts ;
- budgets ;
- quotas ;
- horaires ;
- pays ;
- langues ;
- priorités ;
- fallback ;
- suppressions ;
- incidents ;
- rapports ;
- audits ;
- feature flags.

---

# 89. Rôles

Exemples :

```text
COMMUNICATION_ADMIN
NOTIFICATION_MANAGER
CAMPAIGN_MANAGER
TEMPLATE_MANAGER
TRANSLATION_MANAGER
DELIVERY_OPERATOR
COMMUNICATION_FINANCE_ANALYST
COMMUNICATION_SUPPORT_AGENT
COMMUNICATION_AUDITOR
VIEWER
```

---

# 90. Permissions

Exemples :

```text
communication.dashboard.read
communication.provider.read
communication.provider.manage
communication.template.read
communication.template.manage
communication.translation.manage
communication.campaign.create
communication.campaign.approve
communication.campaign.send
communication.preference.read
communication.consent.read
communication.delivery.read
communication.cost.read
communication.report.read
communication.audit.read
```

---

# 91. Approbations

Peuvent exiger une approbation :

- nouveau fournisseur ;
- modification d’un modèle critique ;
- campagne de masse ;
- communication réglementaire ;
- changement d’expéditeur ;
- activation d’un nouveau pays ;
- augmentation de quota ;
- modification d’un fallback ;
- communication d’incident ;
- export de destinataires.

---

# 92. Double validation

Peut être exigée pour :

- campagne nationale ;
- campagne contenant des données financières ;
- modèle OTP ;
- message réglementaire ;
- changement de fournisseur principal ;
- activation d’un canal externe ;
- export massif ;
- communication de crise ;
- modification d’un modèle de sécurité.

---

# 93. Séparation des rôles

Exemple :

```text
Responsable communication prépare
→ Responsable conformité vérifie
→ Administrateur autorisé approuve
→ Système programme l’envoi
```

---

# 94. API

Exemples :

```http
POST   /communications/events
POST   /communications/notifications
GET    /communications/notifications/{id}

GET    /communications/templates
POST   /communications/templates
POST   /communications/templates/{id}/test
POST   /communications/templates/{id}/publish

GET    /communications/preferences/{userId}
PATCH  /communications/preferences/{userId}

POST   /communications/campaigns
POST   /communications/campaigns/{id}/preview
POST   /communications/campaigns/{id}/approve
POST   /communications/campaigns/{id}/send
POST   /communications/campaigns/{id}/pause

GET    /communications/providers
GET    /communications/delivery
GET    /communications/reports
GET    /communications/audit
```

---

# 95. Webhooks internes

Événements possibles :

```text
communication.created
communication.queued
communication.sent
communication.delivered
communication.read
communication.failed
communication.suppressed
communication.provider.degraded
communication.provider.failed
communication.campaign.started
communication.campaign.paused
communication.campaign.completed
communication.budget.warning
communication.security.alert
```

---

# 96. Intégrations

Le système doit pouvoir se connecter à :

- Firebase Cloud Messaging ;
- Apple Push Notification service ;
- fournisseurs SMS ;
- fournisseurs e-mail ;
- téléphonie ;
- messageries autorisées ;
- applications Mansa ;
- backend central ;
- partenaires ;
- support ;
- sécurité ;
- finance ;
- observabilité ;
- analytics ;
- gestion du consentement ;
- feature flags.

Les fournisseurs précis doivent rester remplaçables.

---

# 97. Multi-pays

Chaque pays peut avoir :

- fournisseurs ;
- expéditeurs ;
- langues ;
- horaires ;
- coûts ;
- règles ;
- consentements ;
- obligations ;
- formats ;
- restrictions ;
- opérateurs ;
- canaux disponibles.

---

# 98. Multi-langues

Chaque communication doit pouvoir exister dans plusieurs langues.

Le système doit gérer :

- langue principale ;
- langue secondaire ;
- langue de secours ;
- variantes régionales ;
- direction du texte ;
- formats de date ;
- devise ;
- heure ;
- nom des institutions ;
- variables localisées.

---

# 99. Réseau faible

Le système doit prévoir :

- SMS de secours ;
- messages in-app synchronisés plus tard ;
- notifications légères ;
- contenu textuel ;
- faible taille ;
- reprise ;
- expiration ;
- suppression des médias ;
- priorité aux messages critiques.

---

# 100. Mode dégradé

En cas de panne :

- les communications critiques restent prioritaires ;
- les campagnes peuvent être suspendues ;
- les files bulk peuvent être ralenties ;
- les fournisseurs de secours peuvent être activés ;
- les messages peuvent être conservés ;
- les envois peuvent reprendre automatiquement ;
- les administrateurs doivent être alertés.

---

# 101. Sécurité

Mesures principales :

- chiffrement ;
- MFA ;
- RBAC ;
- ABAC ;
- gestion des secrets ;
- fournisseurs isolés ;
- signature des webhooks ;
- validation des modèles ;
- filtrage des variables ;
- protection des OTP ;
- rate limiting ;
- détection de boucle ;
- audit ;
- révocation ;
- surveillance.

---

# 102. Protection contre les abus

Le système doit détecter :

- envoi massif inhabituel ;
- boucle de notifications ;
- utilisation abusive d’OTP ;
- changement de modèle suspect ;
- campagne sans consentement ;
- fournisseur détourné ;
- export massif ;
- message contenant un secret ;
- usurpation d’expéditeur ;
- spam interne ;
- ciblage interdit.

---

# 103. Audit

Le journal doit contenir :

- utilisateur ;
- rôle ;
- canal ;
- fournisseur ;
- modèle ;
- campagne ;
- destinataire masqué ;
- action ;
- ancienne valeur ;
- nouvelle valeur ;
- date ;
- heure ;
- pays ;
- appareil ;
- IP ;
- motif ;
- approbateur ;
- résultat.

---

# 104. Immutabilité des audits

Les audits ne doivent pas être :

- modifiés ;
- supprimés ;
- réécrits ;
- désactivés ;
- masqués sans trace ;
- exportés sans permission.

---

# 105. Modèles principaux

- CommunicationEvent
- Notification
- NotificationRecipient
- NotificationChannel
- NotificationAttempt
- NotificationDelivery
- PushToken
- SmsMessage
- EmailMessage
- InAppMessage
- BannerMessage
- VoiceMessage
- UssdMessage
- WebhookDelivery
- CommunicationProvider
- ProviderRoute
- ProviderHealth
- MessageTemplate
- MessageTemplateVersion
- MessageTranslation
- CommunicationPreference
- CommunicationConsent
- SuppressionEntry
- CommunicationCampaign
- CampaignAudience
- CampaignDelivery
- CommunicationSchedule
- CommunicationBudget
- CommunicationCost
- CommunicationApproval
- CommunicationIncident
- CommunicationAudit

---

# 106. Analytics

Événements possibles :

```text
communication_notification_created
communication_notification_queued
communication_notification_sent
communication_notification_delivered
communication_notification_read
communication_notification_failed
communication_notification_clicked
communication_template_created
communication_template_published
communication_campaign_created
communication_campaign_started
communication_campaign_completed
communication_provider_degraded
communication_provider_fallback_used
communication_budget_warning_created
communication_security_alert_created
```

---

# 107. Données analytics interdites

Ne pas transmettre :

- PIN ;
- OTP ;
- CVV ;
- numéro complet de carte ;
- mot de passe ;
- clé privée ;
- secret API ;
- contenu complet sensible ;
- document complet ;
- identité complète inutile ;
- message privé complet ;
- données biométriques.

---

# 108. Tests

- tests d’événements ;
- tests d’idempotence ;
- tests de déduplication ;
- tests push ;
- tests iOS ;
- tests Android ;
- tests web push ;
- tests SMS ;
- tests e-mail ;
- tests in-app ;
- tests bannières ;
- tests TPE ;
- tests DAB ;
- tests webhooks ;
- tests voix ;
- tests USSD ;
- tests modèles ;
- tests variables ;
- tests sécurité HTML ;
- tests traductions ;
- tests langue de secours ;
- tests préférences ;
- tests consentements ;
- tests suppression ;
- tests campagnes ;
- tests segmentation ;
- tests exclusions ;
- tests programmation ;
- tests heures silencieuses ;
- tests fallback ;
- tests fournisseurs ;
- tests bascule ;
- tests rapports de livraison ;
- tests retries ;
- tests dead-letter ;
- tests throttling ;
- tests coûts ;
- tests budgets ;
- tests pièces jointes ;
- tests liens sécurisés ;
- tests OTP ;
- tests multi-pays ;
- tests multi-langues ;
- tests réseau faible ;
- tests mode dégradé ;
- tests sécurité ;
- tests audit ;
- tests performance ;
- tests accessibilité.

---

# 109. Règles métier

1. Toutes les communications passent par le moteur central.
2. Aucun fournisseur n’est codé en dur.
3. Chaque envoi possède un identifiant unique.
4. L’idempotence empêche les doublons non souhaités.
5. Les modèles sont versionnés.
6. Les modèles critiques sont approuvés.
7. Les variables sont filtrées.
8. Les secrets ne sont jamais envoyés.
9. Les préférences utilisateur sont respectées.
10. Les communications obligatoires restent disponibles.
11. Les consentements sont historisés.
12. Les retraits de consentement sont synchronisés.
13. Les campagnes utilisent une segmentation autorisée.
14. Les mineurs sont protégés selon les règles applicables.
15. Les heures silencieuses sont configurables.
16. Les messages critiques peuvent utiliser un fallback.
17. Les fournisseurs peuvent être remplacés.
18. Les échecs temporaires sont relancés.
19. Les échecs définitifs vont en dead-letter.
20. Les coûts sont suivis.
21. Les budgets peuvent bloquer ou suspendre une campagne.
22. Les webhooks sont signés.
23. Les OTP sont protégés.
24. Le demandeur ne valide pas seul une communication critique.
25. Les audits sont immuables.

---

# 110. Critères d’acceptation

Le Système de notifications et communications omnicanales Mansa est validé lorsque :

- toutes les applications peuvent envoyer des événements ;
- les événements sont idempotents ;
- les notifications push fonctionnent ;
- les SMS fonctionnent ;
- les e-mails fonctionnent ;
- les messages in-app fonctionnent ;
- les bannières sont administrables ;
- les TPE et DAB peuvent recevoir des messages ;
- les webhooks sont signés ;
- les appels vocaux sont intégrables ;
- l’USSD est pris en charge lorsque disponible ;
- les modèles sont versionnés ;
- les variables sont sécurisées ;
- les prévisualisations sont disponibles ;
- les traductions sont administrables ;
- la langue de secours fonctionne ;
- les préférences utilisateur sont synchronisées ;
- les consentements sont historisés ;
- les listes de suppression fonctionnent ;
- les campagnes sont administrables ;
- les segmentations sont contrôlées ;
- les exclusions sont appliquées ;
- les heures silencieuses sont respectées ;
- les stratégies multicanales fonctionnent ;
- le fallback est automatique ;
- les fournisseurs sont remplaçables ;
- les fournisseurs de secours fonctionnent ;
- la délivrabilité est suivie ;
- les retries sont configurables ;
- les doublons sont empêchés ;
- les dead-letter queues sont disponibles ;
- les quotas sont appliqués ;
- les coûts sont suivis ;
- les budgets sont configurables ;
- les alertes de coût fonctionnent ;
- les pièces jointes sont protégées ;
- les OTP sont sécurisés ;
- les communications de sécurité sont prioritaires ;
- le multi-pays fonctionne ;
- le multi-langues fonctionne ;
- le réseau faible est pris en charge ;
- le mode dégradé fonctionne ;
- les actions critiques utilisent une approbation ;
- les audits sont immuables ;
- les tests couvrent les parcours essentiels.
