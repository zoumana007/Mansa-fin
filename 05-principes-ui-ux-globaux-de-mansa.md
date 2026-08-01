# 05 — Principes UI/UX globaux de Mansa

## 1. Objet du document

Ce document définit les règles officielles d’expérience utilisateur et d’interface de Mansa.

Il complète le Design System en précisant :

- comment organiser les écrans ;
- comment guider l’utilisateur ;
- comment réduire les erreurs ;
- comment présenter les opérations financières ;
- comment gérer les parcours sensibles ;
- comment adapter l’expérience aux différents produits ;
- comment concevoir pour les utilisateurs peu familiers avec la technologie ;
- comment maintenir une expérience cohérente entre mobile, web et TPE.

---

## 2. Principes UX fondamentaux

### 2.1 Une action importante doit être évidente

L’utilisateur doit comprendre rapidement :

- où il se trouve ;
- ce qu’il peut faire ;
- ce qui est attendu ;
- ce qui est déjà terminé ;
- ce qui bloque ;
- ce qui est risqué.

Les actions principales doivent être visuellement prioritaires.

### 2.2 Réduire le nombre d’étapes

Les parcours fréquents doivent être courts.

Exemples :

- envoyer de l’argent ;
- scanner un QR ;
- consulter une carte ;
- bloquer une carte ;
- payer une facture ;
- rembourser un client.

Une étape supplémentaire n’est justifiée que si elle améliore la sécurité, la compréhension ou la conformité.

### 2.3 Afficher le statut réel

Le système doit distinguer clairement :

- brouillon ;
- en cours ;
- en attente ;
- confirmé ;
- échoué ;
- annulé ;
- remboursé ;
- contesté.

Aucune animation ou notification ne doit faire croire qu’une opération est réussie avant confirmation officielle.

### 2.4 Prévenir les erreurs avant qu’elles arrivent

L’interface doit aider l’utilisateur à éviter :

- mauvais destinataire ;
- mauvais montant ;
- mauvaise devise ;
- mauvaise carte ;
- doublon ;
- paiement à un commerçant inconnu ;
- dépassement de plafond ;
- oubli de frais ;
- mauvaise action administrative.

### 2.5 Expliquer les conséquences

Avant une action critique, l’utilisateur doit voir :

- ce qui va se passer ;
- ce qui sera débité ;
- ce qui sera crédité ;
- les frais ;
- le délai ;
- les limites ;
- la possibilité ou non d’annuler ;
- l’impact sur son compte.

---

# 3. Architecture de l’information

## 3.1 Hiérarchie

Chaque écran doit suivre une hiérarchie claire :

1. contexte ;
2. information principale ;
3. action principale ;
4. actions secondaires ;
5. détails ;
6. aide.

## 3.2 Navigation

La navigation doit être stable.

Les changements de structure importants doivent être :

- justifiés ;
- testés ;
- documentés ;
- éventuellement introduits progressivement.

## 3.3 Recherche

La recherche doit être disponible lorsque le volume d’informations le justifie.

Elle peut couvrir :

- utilisateurs ;
- transactions ;
- commerces ;
- produits ;
- documents ;
- messages ;
- services publics ;
- paramètres.

## 3.4 Filtres

Les filtres doivent :

- être compréhensibles ;
- être réinitialisables ;
- afficher leur état actif ;
- être mémorisables si utile ;
- fonctionner avec la pagination.

---

# 4. Parcours utilisateurs

## 4.1 Parcours critique

Un parcours critique doit prévoir :

- prérequis ;
- étapes ;
- validations ;
- erreurs ;
- reprises ;
- annulation ;
- support ;
- audit ;
- analytics ;
- accessibilité.

## 4.2 Progression

Les parcours longs doivent afficher :

- nombre d’étapes ;
- étape actuelle ;
- étapes terminées ;
- possibilité de reprendre plus tard ;
- sauvegarde automatique si nécessaire.

## 4.3 Reprise

L’utilisateur doit pouvoir reprendre après :

- interruption réseau ;
- fermeture de l’application ;
- expiration de session ;
- erreur partenaire ;
- redémarrage du terminal ;
- validation administrative en attente.

---

# 5. Accueil et tableau de bord

L’accueil doit :

- montrer l’essentiel ;
- donner accès aux actions fréquentes ;
- afficher les alertes importantes ;
- rester personnalisable ;
- éviter la surcharge ;
- fonctionner en connexion lente.

Les widgets doivent être organisés par priorité :

1. sécurité ;
2. argent ;
3. actions ;
4. activité ;
5. recommandations ;
6. contenus secondaires.

---

# 6. Formulaires

## 6.1 Champs

Chaque champ doit avoir :

- label visible ;
- format attendu ;
- exemple si nécessaire ;
- validation ;
- message d’erreur ;
- aide contextuelle ;
- comportement clavier adapté.

## 6.2 Validation

La validation doit se faire :

- pendant la saisie pour les erreurs simples ;
- au changement de champ ;
- à la soumission ;
- côté backend pour toute règle officielle.

## 6.3 Erreurs

Une erreur doit préciser :

- le problème ;
- le champ concerné ;
- la solution ;
- si l’utilisateur peut recommencer.

## 6.4 Données sensibles

Les champs sensibles doivent prévoir :

- masquage ;
- affichage temporaire ;
- protection contre les captures si nécessaire ;
- expiration ;
- effacement ;
- absence de journalisation.

---

# 7. Opérations financières

## 7.1 Saisie du montant

L’écran doit afficher :

- montant ;
- devise ;
- compte débité ;
- solde disponible ;
- frais ;
- taux de change ;
- montant reçu ;
- plafond applicable.

## 7.2 Choix du destinataire

Afficher :

- nom ;
- identifiant Mansa ;
- photo si autorisée ;
- statut vérifié ;
- pays ;
- avertissement en cas de risque.

## 7.3 Confirmation

La confirmation doit résumer :

- destinataire ;
- montant ;
- devise ;
- frais ;
- compte ;
- délai ;
- motif ;
- pièces jointes ;
- méthode d’authentification.

## 7.4 Résultat

Après l’action :

- statut réel ;
- référence ;
- reçu ;
- prochaine action ;
- possibilité de support ;
- possibilité de partager.

---

# 8. Sécurité UX

La sécurité doit être visible sans rendre l’application anxiogène.

Exemples :

- appareil inconnu ;
- connexion inhabituelle ;
- tentative de fraude ;
- carte bloquée ;
- modification sensible ;
- plafond dépassé.

Les alertes doivent être hiérarchisées :

- critique ;
- urgente ;
- importante ;
- informative.

---

# 9. Gestion des erreurs

## 9.1 Erreur récupérable

Exemple :

- connexion temporaire ;
- partenaire lent ;
- code expiré.

Le système doit proposer :

- réessayer ;
- revenir ;
- changer de méthode ;
- contacter le support.

## 9.2 Erreur non récupérable

Exemple :

- compte suspendu ;
- opération interdite ;
- document rejeté.

Le système doit expliquer :

- la cause générale ;
- la prochaine étape ;
- le canal de support ;
- le délai éventuel.

## 9.3 Erreur inconnue

Afficher :

- message simple ;
- identifiant de corrélation ;
- bouton réessayer ;
- accès au support.

---

# 10. Notifications UX

Une notification doit préciser :

- ce qui s’est passé ;
- pour quel compte ;
- montant si utile ;
- statut ;
- action possible ;
- niveau de priorité.

Les notifications sensibles ne doivent pas afficher trop d’informations sur l’écran verrouillé sans consentement.

---

# 11. Messagerie Mansa Connect

L’expérience doit être naturelle.

Le chat doit distinguer :

- message classique ;
- paiement ;
- demande d’argent ;
- reçu ;
- document ;
- alerte ;
- message système.

Les objets financiers doivent rester interactifs et afficher leur statut réel.

---

# 12. Commerce et TPE

## 12.1 Commerce

Priorités UX :

- rapidité ;
- gestion claire ;
- visibilité des ventes ;
- accès aux stocks ;
- actions sur les employés ;
- filtres ;
- rapports.

## 12.2 TPE

Priorités :

- très peu d’étapes ;
- gros boutons ;
- contraste ;
- montant central ;
- confirmation explicite ;
- reprise après erreur ;
- accès rapide au remboursement ;
- limitation des erreurs employé.

---

# 13. Portail Admin

Le portail Admin doit privilégier :

- densité maîtrisée ;
- raccourcis ;
- recherche globale ;
- filtres avancés ;
- colonnes configurables ;
- actions en masse ;
- double confirmation ;
- historique ;
- audit ;
- permissions.

Les actions critiques doivent demander :

- motif ;
- confirmation ;
- réauthentification ;
- approbation éventuelle.

---

# 14. États vides

Un état vide doit :

- expliquer ;
- rassurer ;
- proposer une action ;
- rester simple.

Exemples :

- aucun compte ;
- aucune transaction ;
- aucun commerce ;
- aucun ticket ;
- aucun résultat.

---

# 15. Chargement

Le chargement doit utiliser :

- skeleton ;
- progression ;
- message ;
- estimation si utile ;
- possibilité d’annuler pour les tâches longues.

Éviter les écrans blancs.

---

# 16. Hors ligne

L’utilisateur doit savoir :

- qu’il est hors ligne ;
- quelles données sont en cache ;
- quelles actions sont disponibles ;
- quelles actions attendent ;
- quelles actions sont interdites ;
- quand la synchronisation reprendra.

---

# 17. Personnalisation

La personnalisation doit rester contrôlée.

L’utilisateur peut modifier :

- thème ;
- ordre ;
- widgets ;
- langue ;
- raccourcis ;
- densité ;
- animations.

L’administration peut définir :

- éléments obligatoires ;
- limites ;
- variantes par pays ;
- fonctionnalités disponibles.

---

# 18. Accessibilité UX

Chaque parcours doit être testable avec :

- lecteur d’écran ;
- clavier ;
- fort contraste ;
- zoom ;
- tailles de texte ;
- réduction des animations.

Les actions critiques ne doivent pas dépendre uniquement :

- d’une couleur ;
- d’un geste ;
- d’un son ;
- d’une animation.

---

# 19. Langage

Le ton Mansa doit être :

- clair ;
- direct ;
- respectueux ;
- rassurant ;
- professionnel ;
- non paternaliste.

Éviter :

- jargon bancaire ;
- termes techniques ;
- phrases trop longues ;
- messages accusateurs.

---

# 20. Microcopy

Exemples de bonnes pratiques :

- « Votre paiement est en cours de traitement. »
- « Vérifiez le nom du destinataire avant de confirmer. »
- « Cette action ne peut pas être annulée. »
- « Votre connexion a expiré. Reconnectez-vous pour continuer. »

---

# 21. Critères d’acceptation

Les principes UI/UX sont validés lorsque :

- les parcours critiques sont courts ;
- les statuts sont clairs ;
- les erreurs sont compréhensibles ;
- les actions risquées sont confirmées ;
- la sécurité est visible ;
- l’accessibilité est intégrée ;
- le mode hors ligne est explicite ;
- le TPE est optimisé pour l’encaissement ;
- le portail Admin est efficace ;
- les notifications respectent la confidentialité ;
- les textes sont simples ;
- les opérations financières affichent tous les éléments nécessaires.
