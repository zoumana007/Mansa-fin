# 12 — Système global de notifications et communications de Mansa

## 1. Objet du document

Ce document définit le système officiel de notifications et communications de Mansa.

Il couvre :

- notifications push ;
- notifications internes ;
- e-mails ;
- SMS ;
- WhatsApp lorsque autorisé ;
- messages de sécurité ;
- alertes transactionnelles ;
- notifications commerciales ;
- notifications administratives ;
- communications partenaires ;
- préférences utilisateur ;
- priorités ;
- modèles ;
- journalisation ;
- retry ;
- suivi de livraison ;
- confidentialité ;
- règles multi-pays ;
- règles multi-langues ;
- administration.

L’objectif est de garantir que chaque message envoyé par Mansa soit :

- utile ;
- compréhensible ;
- correctement priorisé ;
- sécurisé ;
- traduit ;
- traçable ;
- envoyé par le bon canal ;
- respectueux des préférences ;
- conforme aux obligations locales.

---

# 2. Principes fondamentaux

## 2.1 Une notification doit avoir un objectif clair

Chaque notification doit répondre à une raison précise :

- informer ;
- confirmer ;
- alerter ;
- demander une action ;
- rappeler ;
- accompagner ;
- promouvoir.

Les notifications sans utilité réelle sont interdites.

---

## 2.2 Les notifications critiques sont prioritaires

Les messages de sécurité, de fraude ou d’opération financière ne doivent pas être noyés parmi les notifications marketing.

Ordre de priorité recommandé :

1. sécurité critique ;
2. action financière requise ;
3. opération financière ;
4. conformité ;
5. service ;
6. rappel ;
7. information ;
8. promotion.

---

## 2.3 Une notification ne constitue pas la preuve unique

Une notification peut confirmer qu’une action a été traitée, mais la preuve officielle reste :

- le statut backend ;
- la transaction ;
- le reçu ;
- le document ;
- le journal d’audit.

Une notification ne doit jamais être considérée comme source de vérité indépendante.

---

## 2.4 Aucun faux succès

Le système ne doit jamais envoyer :

> Paiement réussi

 tant que le backend n’a pas confirmé définitivement le statut.

Les statuts intermédiaires doivent être explicites :

- en attente ;
- en cours ;
- à confirmer ;
- partiellement terminé ;
- retardé ;
- échoué.

---

## 2.5 Confidentialité par défaut

Le contenu affiché sur l’écran verrouillé doit être limité selon :

- sensibilité ;
- réglage utilisateur ;
- politique du pays ;
- type de message ;
- risque.

Une notification ne doit pas afficher inutilement :

- solde complet ;
- numéro de carte ;
- identité complète ;
- document ;
- code OTP ;
- détail confidentiel ;
- contenu privé d’une conversation.

---

# 3. Canaux supportés

Le système doit pouvoir utiliser :

- notification push ;
- centre de notifications interne ;
- e-mail ;
- SMS ;
- WhatsApp ou messagerie partenaire lorsque autorisé ;
- bannière in-app ;
- modal critique ;
- message dans Mansa Connect ;
- appel automatisé éventuel pour certains cas autorisés ;
- webhook pour partenaires ;
- notification portail Admin ;
- notification TPE.

Tous les canaux ne sont pas nécessaires pour chaque message.

---

# 4. Catégories de notifications

## 4.1 Sécurité

Exemples :

- nouvelle connexion ;
- nouvel appareil ;
- changement de mot de passe ;
- changement de PIN ;
- biométrie activée ;
- appareil révoqué ;
- tentative suspecte ;
- compte temporairement bloqué ;
- changement de numéro ;
- modification des paramètres sensibles.

---

## 4.2 Transactions

Exemples :

- transfert initié ;
- transfert reçu ;
- paiement réussi ;
- paiement refusé ;
- paiement en attente ;
- remboursement ;
- demande d’argent ;
- prélèvement ;
- paiement programmé ;
- conversion ;
- retrait ;
- dépôt ;
- opération Mobile Money.

---

## 4.3 Cartes

Exemples :

- carte commandée ;
- carte expédiée ;
- carte livrée ;
- carte activée ;
- carte bloquée ;
- carte débloquée ;
- PIN modifié ;
- paiement carte ;
- plafond atteint ;
- transaction suspecte ;
- carte expirant bientôt.

---

## 4.4 Commerce

Exemples :

- nouvelle vente ;
- remboursement ;
- stock faible ;
- stock épuisé ;
- nouvelle commande ;
- nouvelle réservation ;
- nouveau client ;
- avis reçu ;
- règlement disponible ;
- anomalie de caisse ;
- TPE hors ligne.

---

## 4.5 TPE

Exemples :

- terminal activé ;
- terminal désactivé ;
- mise à jour disponible ;
- synchronisation échouée ;
- paiement accepté ;
- paiement refusé ;
- imprimante indisponible ;
- clôture requise ;
- sécurité du terminal ;
- certificat expirant.

---

## 4.6 Mansa Connect

Exemples :

- nouveau message ;
- demande d’argent ;
- paiement reçu dans une conversation ;
- invitation de groupe ;
- message de sécurité ;
- fichier partagé ;
- réaction ;
- rappel de demande.

---

## 4.7 Budgets et coffres

Exemples :

- budget bientôt dépassé ;
- budget dépassé ;
- objectif atteint ;
- versement programmé réussi ;
- versement échoué ;
- coffre débloqué ;
- proposition Jini.

---

## 4.8 Fidélité et promotions

Exemples :

- points gagnés ;
- récompense disponible ;
- cashback reçu ;
- coupon expirant ;
- promotion proche ;
- offre personnalisée ;
- changement de niveau.

---

## 4.9 Services publics

Exemples :

- amende enregistrée ;
- paiement public reçu ;
- justificatif disponible ;
- dossier en attente ;
- carte étudiante disponible ;
- bourse versée ;
- document rejeté ;
- action administrative requise.

---

## 4.10 Support

Exemples :

- ticket créé ;
- réponse reçue ;
- document demandé ;
- dossier escaladé ;
- ticket résolu ;
- satisfaction demandée.

---

## 4.11 Administration

Exemples :

- validation requise ;
- action critique ;
- fraude détectée ;
- partenaire indisponible ;
- incident ;
- export terminé ;
- configuration modifiée ;
- seuil dépassé ;
- workflow bloqué.

---

## 4.12 Marketing

Exemples :

- nouvelle fonctionnalité ;
- campagne ;
- promotion ;
- offre partenaire ;
- parrainage ;
- contenu éducatif.

Les communications marketing doivent respecter les consentements.

---

# 5. Niveaux de priorité

Chaque notification doit avoir un niveau.

## 5.1 Critique

Exemples :

- fraude ;
- accès suspect ;
- carte compromise ;
- opération sensible ;
- action administrative urgente.

Peut utiliser plusieurs canaux.

## 5.2 Haute

Exemples :

- paiement reçu ;
- paiement refusé ;
- action KYC requise ;
- remboursement ;
- terminal bloqué.

## 5.3 Normale

Exemples :

- information de compte ;
- nouvelle réponse support ;
- mise à jour d’un service.

## 5.4 Faible

Exemples :

- conseil ;
- rappel non urgent ;
- contenu produit ;
- marketing.

---

# 6. Structure d’une notification

Chaque notification doit contenir :

- identifiant ;
- type ;
- catégorie ;
- priorité ;
- destinataire ;
- canal ;
- titre ;
- corps ;
- action principale ;
- action secondaire éventuelle ;
- ressource liée ;
- langue ;
- pays ;
- date de création ;
- date planifiée ;
- date d’expiration ;
- statut ;
- niveau de sensibilité ;
- modèle ;
- version ;
- métadonnées ;
- corrélation ;
- environnement.

---

# 7. Modèles de notification

Chaque modèle doit définir :

- identifiant stable ;
- catégorie ;
- canal ;
- langue ;
- titre ;
- corps ;
- variables ;
- liens ;
- priorité ;
- règles d’affichage ;
- pays ;
- version ;
- statut ;
- date d’effet ;
- fallback ;
- auteur ;
- approbateur.

Exemple :

```text
template: payment.completed.push
title: Paiement confirmé
body: Votre paiement de {amount} {currency} à {merchantName} est confirmé.
```

---

# 8. Variables

Les variables peuvent inclure :

- prénom ;
- nom ;
- montant ;
- devise ;
- commerçant ;
- date ;
- heure ;
- statut ;
- référence ;
- appareil ;
- ville ;
- limite ;
- délai ;
- lien d’action.

Les variables doivent être :

- typées ;
- validées ;
- échappées ;
- localisées ;
- non sensibles par défaut.

---

# 9. Centre de notifications interne

Toutes les notifications importantes doivent pouvoir apparaître dans un centre interne.

Fonctions :

- liste ;
- lecture ;
- non lue ;
- filtres ;
- catégories ;
- recherche ;
- date ;
- action ;
- suppression logique ;
- archivage ;
- priorité ;
- regroupement ;
- statut.

Une notification critique ne doit pas pouvoir disparaître avant traitement si une action est requise.

---

# 10. Regroupement

Les notifications répétitives peuvent être regroupées.

Exemples :

- plusieurs nouveaux messages ;
- plusieurs ventes ;
- plusieurs promotions ;
- plusieurs alertes stock ;
- plusieurs activités similaires.

Le regroupement ne doit pas masquer une alerte critique.

---

# 11. Préférences utilisateur

L’utilisateur doit pouvoir gérer :

- push ;
- e-mail ;
- SMS ;
- marketing ;
- rappels ;
- alertes budget ;
- Mansa Connect ;
- promotions ;
- recommandations ;
- fréquence ;
- plage silencieuse ;
- aperçu écran verrouillé.

Certaines notifications restent obligatoires :

- sécurité ;
- fraude ;
- opérations financières ;
- documents légaux ;
- modifications critiques ;
- obligations réglementaires.

---

# 12. Plages silencieuses

L’utilisateur peut définir :

- heures silencieuses ;
- jours ;
- fuseau ;
- exceptions ;
- catégories autorisées.

Les notifications critiques peuvent contourner les plages silencieuses selon les règles.

---

# 13. Consentement marketing

Le système doit enregistrer :

- consentement ;
- canal ;
- pays ;
- langue ;
- date ;
- source ;
- version ;
- retrait ;
- finalité.

Le retrait doit être pris en compte rapidement.

---

# 14. Push notifications

Le push doit gérer :

- token d’appareil ;
- plateforme ;
- application ;
- environnement ;
- langue ;
- statut ;
- expiration ;
- révocation ;
- dernière utilisation.

Un token invalide doit être désactivé.

---

# 15. Notifications écran verrouillé

Niveaux possibles :

- contenu complet ;
- contenu masqué ;
- titre générique ;
- aucune information.

Exemple sécurisé :

> Nouvelle activité sur votre compte.

au lieu de :

> Vous avez reçu 500 000 XOF de Mamadou Traoré.

---

# 16. E-mails

Les e-mails doivent inclure :

- objet ;
- préheader ;
- contenu HTML ;
- version texte ;
- CTA ;
- pied de page ;
- informations légales ;
- lien support ;
- désabonnement lorsque applicable ;
- version linguistique.

---

# 17. SMS

Les SMS doivent être réservés à des cas utiles :

- OTP ;
- sécurité ;
- statut important ;
- rappel critique ;
- opération lorsque le push échoue ;
- communication réglementaire.

Ils doivent rester courts et éviter les données sensibles.

---

# 18. OTP

Les OTP ne doivent pas être mélangés aux notifications marketing.

Règles :

- durée limitée ;
- usage unique ;
- nombre de tentatives limité ;
- non journalisé en clair ;
- aucun partage ;
- message explicite ;
- alerte anti-fraude.

Exemple :

> Votre code Mansa est 123456. Ne le partagez jamais.

---

# 19. WhatsApp et canaux tiers

L’utilisation dépend :

- du pays ;
- du consentement ;
- du partenaire ;
- des conditions ;
- des modèles approuvés ;
- de la conformité ;
- de la confidentialité.

Les données financières sensibles doivent être limitées.

---

# 20. Notifications TPE

Le TPE doit afficher :

- statut de paiement ;
- erreur ;
- impression ;
- connexion ;
- synchronisation ;
- mise à jour ;
- action requise ;
- sécurité.

Les notifications TPE doivent être :

- courtes ;
- lisibles ;
- orientées action ;
- adaptées au contexte professionnel.

---

# 21. Notifications Admin

Le portail Admin doit gérer :

- alertes fraude ;
- incidents ;
- validations ;
- seuils ;
- partenaires ;
- exports ;
- configuration ;
- support ;
- audit ;
- disponibilité.

Les notifications doivent respecter les permissions.

---

# 22. Notification multi-canaux

Une même notification peut utiliser plusieurs canaux selon :

- priorité ;
- risque ;
- préférence ;
- échec ;
- réglementation ;
- pays ;
- type d’utilisateur.

Exemple :

1. push ;
2. si échec, e-mail ;
3. si critique, SMS ;
4. centre interne toujours mis à jour.

---

# 23. Fallback de canal

Chaque modèle peut définir un ordre.

Exemple :

```text
push → e-mail → SMS
```

Le fallback doit être contrôlé pour éviter les doublons.

---

# 24. Déduplication

Le système doit empêcher :

- double push ;
- double SMS ;
- double e-mail ;
- répétition après retry ;
- doublon multi-appareil inutile ;
- répétition partenaire.

Une clé de déduplication peut être utilisée.

---

# 25. Idempotence

Chaque demande d’envoi doit posséder :

- identifiant ;
- clé d’idempotence ;
- type ;
- destinataire ;
- canal ;
- contenu ;
- statut ;
- tentative ;
- résultat.

---

# 26. Statuts d’envoi

Statuts possibles :

- créé ;
- planifié ;
- mis en file ;
- envoyé ;
- livré ;
- ouvert ;
- cliqué ;
- échoué ;
- expiré ;
- annulé ;
- ignoré ;
- bloqué.

Toutes les plateformes ne fournissent pas tous les statuts.

---

# 27. Retry

Le retry doit dépendre du type d’erreur.

Exemples :

- erreur temporaire : retry ;
- token invalide : désactivation ;
- numéro invalide : arrêt ;
- utilisateur désabonné : blocage ;
- modèle refusé : escalade ;
- partenaire indisponible : retry contrôlé.

---

# 28. File d’attente

Les notifications doivent passer par une file lorsque nécessaire.

Chaque tâche doit contenir :

- notification ;
- canal ;
- tentative ;
- prochaine exécution ;
- priorité ;
- statut ;
- erreur ;
- délai ;
- corrélation.

---

# 29. Planification

Le système doit permettre :

- envoi immédiat ;
- envoi différé ;
- récurrence ;
- fuseau ;
- fenêtre autorisée ;
- date d’expiration ;
- segmentation ;
- annulation.

---

# 30. Expiration

Certaines notifications deviennent inutiles.

Exemples :

- OTP ;
- demande d’argent ;
- devis ;
- promotion ;
- validation ;
- réservation ;
- rappel d’action.

Après expiration, elles ne doivent plus être envoyées.

---

# 31. Liens profonds

Les notifications peuvent ouvrir :

- transaction ;
- carte ;
- conversation ;
- ticket ;
- commerce ;
- coffre ;
- service public ;
- document ;
- écran de sécurité.

Les deep links doivent être validés et protégés.

---

# 32. Sécurité des liens

Les liens doivent éviter :

- redirection arbitraire ;
- usurpation ;
- exposition de token ;
- accès sans authentification ;
- fuite de données ;
- URL trop longue.

---

# 33. Multi-appareil

Un utilisateur peut avoir plusieurs appareils.

Le système doit définir :

- tous les appareils ;
- appareil actif ;
- appareil principal ;
- appareil révoqué ;
- push par appareil ;
- déduplication ;
- statut par appareil.

---

# 34. Notifications de groupe

Pour Mansa Connect, commerces ou équipes :

- mention ;
- groupe ;
- rôle ;
- établissement ;
- équipe ;
- administration.

Le système doit limiter le spam.

---

# 35. Anti-spam

Mesures :

- fréquence maximale ;
- limite par canal ;
- regroupement ;
- consentement ;
- segmentation ;
- plages silencieuses ;
- score de pertinence ;
- désabonnement ;
- protection contre abus.

---

# 36. Fréquence

Le système doit pouvoir définir :

- maximum horaire ;
- maximum quotidien ;
- maximum hebdomadaire ;
- fréquence marketing ;
- exceptions critiques.

---

# 37. Segmentation

Les communications peuvent cibler selon :

- pays ;
- langue ;
- type d’utilisateur ;
- niveau KYC ;
- abonnement ;
- activité ;
- commerce ;
- secteur ;
- application ;
- version ;
- appareil ;
- consentement ;
- risque.

Les segments doivent respecter la confidentialité.

---

# 38. Campagnes

Une campagne doit contenir :

- nom ;
- objectif ;
- audience ;
- contenu ;
- langue ;
- canal ;
- calendrier ;
- consentement ;
- pays ;
- statut ;
- métriques ;
- auteur ;
- approbateur.

---

# 39. A/B testing

Possible uniquement pour les notifications non critiques.

Interdit pour :

- sécurité ;
- fraude ;
- confirmation financière ;
- documents légaux ;
- erreurs critiques ;
- consentements.

---

# 40. Administration

Le portail Admin doit permettre :

- créer un modèle ;
- créer une campagne ;
- traduire ;
- prévisualiser ;
- tester ;
- planifier ;
- annuler ;
- publier ;
- suivre ;
- configurer les canaux ;
- gérer les préférences obligatoires ;
- consulter les erreurs ;
- relancer ;
- exporter ;
- auditer.

---

# 41. Permissions

Exemples :

```text
notification.read
notification.template.create
notification.template.update
notification.template.publish
notification.send
notification.campaign.create
notification.campaign.approve
notification.campaign.cancel
notification.security.send
notification.export
```

Les notifications de sécurité doivent être réservées à des rôles spécifiques.

---

# 42. API

Exemples :

```http
GET    /notifications
GET    /notifications/{id}
POST   /notifications/{id}/read
POST   /notifications/read-all

GET    /notification-preferences
PATCH  /notification-preferences

POST   /notification-templates
PATCH  /notification-templates/{id}
POST   /notification-templates/{id}/publish

POST   /notification-campaigns
POST   /notification-campaigns/{id}/schedule
POST   /notification-campaigns/{id}/cancel
```

---

# 43. Modèles

- Notification
- NotificationType
- NotificationCategory
- NotificationPriority
- NotificationChannel
- NotificationTemplate
- NotificationTemplateVersion
- NotificationRecipient
- NotificationDelivery
- NotificationAttempt
- NotificationPreference
- NotificationConsent
- NotificationCampaign
- NotificationSegment
- NotificationSchedule
- PushDeviceToken
- NotificationAudit
- NotificationDeduplicationKey

---

# 44. Règles métier

1. Une notification possède un type.
2. Une notification critique ne dépend pas du marketing.
3. Les notifications financières utilisent le statut backend réel.
4. Une opération en attente n’est jamais annoncée comme réussie.
5. Les préférences sont respectées.
6. Les obligations réglementaires restent envoyables.
7. Les données sensibles sont limitées.
8. Les OTP expirent.
9. Les doublons sont empêchés.
10. Les retries sont contrôlés.
11. Les tokens invalides sont désactivés.
12. Les modèles sont versionnés.
13. Les contenus sont traduits.
14. Les campagnes respectent les consentements.
15. Les liens profonds sont sécurisés.
16. Les notifications expirées ne sont pas envoyées.
17. Les canaux tiers respectent la conformité.
18. Les notifications critiques sont auditées.
19. Les rôles sont vérifiés.
20. Les messages marketing sont désactivables.
21. Les notifications peuvent être regroupées.
22. Les statuts d’envoi sont conservés.
23. Les erreurs techniques ne sont pas exposées directement.
24. Les environnements sont séparés.
25. Les tests n’envoient pas de vrais messages en production.

---

# 45. Analytics

Événements possibles :

```text
notification_created
notification_queued
notification_sent
notification_delivered
notification_opened
notification_clicked
notification_failed
notification_expired
notification_deduplicated
notification_preference_updated
notification_campaign_started
notification_campaign_completed
notification_security_alert_sent
notification_fallback_used
```

---

# 46. Tests

- tests de modèles ;
- tests de variables ;
- tests multi-langues ;
- tests multi-pays ;
- tests de préférences ;
- tests de consentement ;
- tests de priorité ;
- tests de retry ;
- tests de déduplication ;
- tests de fallback ;
- tests de push ;
- tests d’e-mail ;
- tests de SMS ;
- tests d’OTP ;
- tests de deep links ;
- tests de confidentialité ;
- tests de plages silencieuses ;
- tests de campagne ;
- tests de charge ;
- tests d’audit ;
- tests de permissions.

---

# 47. Critères d’acceptation

Le système de notifications est validé lorsque :

- les catégories sont définies ;
- les priorités sont appliquées ;
- les messages financiers utilisent le bon statut ;
- les préférences sont respectées ;
- les notifications critiques restent envoyables ;
- les contenus sensibles sont protégés ;
- les modèles sont versionnés ;
- les langues sont prises en charge ;
- les canaux sont configurables ;
- les doublons sont évités ;
- les retries fonctionnent ;
- les statuts d’envoi sont traçables ;
- les campagnes respectent les consentements ;
- les deep links sont sécurisés ;
- les notifications expirées sont bloquées ;
- le portail Admin permet la gestion ;
- les actions critiques sont auditées ;
- les tests couvrent les principaux canaux.
