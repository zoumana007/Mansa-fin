# 02 — Architecture fonctionnelle globale de Mansa

## 1. Objet du document

Ce document définit l’architecture fonctionnelle de l’écosystème Mansa.

Il décrit :

- les grands domaines fonctionnels ;
- les responsabilités de chaque application ;
- les interactions entre les applications ;
- les services communs ;
- les flux principaux ;
- les limites entre les produits ;
- les dépendances envers des partenaires ;
- les règles de séparation entre interface, logique métier, administration et infrastructure.

Il ne définit pas encore le code, les tables Prisma ni les endpoints détaillés. Ces éléments seront documentés séparément.

## 2. Principes d’architecture fonctionnelle

### 2.1 Un écosystème, plusieurs produits

Mansa n’est pas une application unique.

L’écosystème comprend plusieurs produits spécialisés :

1. Mansa Client ;
2. Mansa Commerce ;
3. Mansa TPE ;
4. Mansa Admin Lite ;
5. Mansa Annuaire / Hub ;
6. site public Mansa ;
7. site Mansa Professionnels ;
8. portail Admin Web ;
9. backend et API Gateway ;
10. services IA Jini ;
11. services partagés ;
12. infrastructure.

Chaque produit possède son propre périmètre, mais utilise des données et services communs.

### 2.2 Séparation des responsabilités

Chaque fonctionnalité doit être placée dans le produit qui en a la responsabilité principale.

Exemples :

- un particulier gère son argent dans Mansa Client ;
- un commerçant gère ses produits dans Mansa Commerce ;
- un employé encaisse dans Mansa TPE ;
- un administrateur configure les règles dans le portail Admin ;
- un utilisateur recherche un commerce dans Mansa Annuaire ;
- le backend applique les règles métier ;
- Jini assiste, explique et recommande, sans contourner les contrôles.

### 2.3 Le backend reste la source d’autorité

Les applications affichent et transmettent des actions.

Le backend :

- valide les données ;
- applique les permissions ;
- vérifie les plafonds ;
- calcule les frais ;
- contrôle les statuts ;
- déclenche les écritures financières ;
- journalise les opérations ;
- refuse les actions interdites ;
- garantit l’idempotence ;
- publie les événements.

Une application ne doit jamais décider seule qu’un paiement est définitivement réussi.

### 2.4 Administration centralisée

Les fonctions configurables doivent pouvoir être administrées depuis le portail Admin Web.

Exemples :

- disponibilité d’un module ;
- ordre d’affichage ;
- frais ;
- commissions ;
- plafonds ;
- pays ;
- devises ;
- partenaires ;
- rôles ;
- permissions ;
- modèles de reçus ;
- contenus ;
- promotions ;
- abonnements ;
- feature flags.

### 2.5 Multi-pays dès la conception

Chaque fonctionnalité doit pouvoir varier selon :

- pays ;
- réglementation ;
- devise ;
- langue ;
- banque partenaire ;
- opérateur Mobile Money ;
- disponibilité d’un service ;
- plafond ;
- frais ;
- conditions légales ;
- niveau KYC ou KYB.

# 3. Domaines fonctionnels principaux

L’écosystème est divisé en domaines.

## 3.1 Identité et accès

Ce domaine couvre :

- inscription ;
- connexion ;
- OTP ;
- mot de passe ;
- PIN ;
- biométrie ;
- passkeys ;
- récupération de compte ;
- appareils ;
- sessions ;
- rôles ;
- permissions ;
- consentements ;
- identité publique ;
- identité légale ;
- KYC ;
- KYB ;
- profils particuliers ;
- profils professionnels ;
- profils institutionnels.

Produits concernés :

- toutes les applications ;
- portail Admin ;
- backend ;
- Jini pour l’assistance non critique.

## 3.2 Comptes, wallets et soldes

Ce domaine couvre :

- wallet principal ;
- comptes secondaires ;
- comptes multi-devises ;
- comptes professionnels ;
- comptes d’épargne ;
- comptes jeunes ;
- comptes d’investissement ;
- soldes disponibles ;
- soldes bloqués ;
- mouvements ;
- limites ;
- rapprochements ;
- écritures comptables.

Le backend financier reste l’unique autorité sur les soldes.

## 3.3 Paiements et transferts

Ce domaine couvre :

- transfert entre utilisateurs ;
- paiement marchand ;
- paiement TPE ;
- QR ;
- NFC ;
- Mobile Money ;
- virement bancaire ;
- paiement international ;
- paiement programmé ;
- paiement récurrent ;
- demande d’argent ;
- paiement fractionné ;
- remboursement ;
- annulation ;
- litige ;
- rétrofacturation ;
- frais ;
- commissions ;
- taxes.

## 3.4 Cartes

Ce domaine couvre :

- carte physique ;
- carte virtuelle ;
- carte temporaire ;
- carte jetable ;
- carte professionnelle ;
- carte jeune ;
- carte étudiante ;
- plafonds ;
- blocage ;
- opposition ;
- remplacement ;
- PIN ;
- CVV ;
- wallets numériques ;
- paiements sans contact ;
- restrictions géographiques ;
- restrictions par commerçant.

L’émission réelle dépend d’un partenaire autorisé.

## 3.5 Commerce et entreprise

Ce domaine couvre :

- établissement ;
- entreprise ;
- employés ;
- rôles internes ;
- catalogue ;
- produits ;
- services ;
- variantes ;
- prix ;
- taxes ;
- stocks ;
- inventaires ;
- fournisseurs ;
- ventes ;
- caisse ;
- clients ;
- reçus ;
- factures ;
- retours ;
- remboursements ;
- promotions ;
- fidélité ;
- rendez-vous ;
- mini-site ;
- analytics professionnels.

## 3.6 TPE et encaissement

Ce domaine couvre :

- activation du terminal ;
- association à un commerce ;
- employés autorisés ;
- saisie d’un montant ;
- panier ;
- scan produit ;
- remises ;
- taxes ;
- pourboire ;
- paiement carte ;
- NFC ;
- QR ;
- Mobile Money ;
- Tap to Phone ;
- impression ;
- remboursement ;
- annulation ;
- clôture de caisse ;
- rapports ;
- synchronisation ;
- mode hors ligne limité.

## 3.7 Annuaire et découverte

Ce domaine couvre :

- recherche ;
- catégories ;
- géolocalisation ;
- carte ;
- commerces proches ;
- profils professionnels ;
- mini-sites ;
- horaires ;
- produits ;
- services ;
- promotions ;
- favoris ;
- avis ;
- modération ;
- rendez-vous ;
- réservations ;
- abonnements de visibilité ;
- établissements sponsorisés.

## 3.8 Messagerie Mansa Connect

Ce domaine couvre :

- conversations privées ;
- groupes ;
- messages texte ;
- fichiers ;
- photos ;
- reçus ;
- transactions ;
- demandes d’argent ;
- paiements dans une conversation ;
- partage de profil ;
- partage de QR ;
- notifications ;
- blocage ;
- signalement ;
- confidentialité ;
- sécurité ;
- historique financier lié à la conversation.

## 3.9 Épargne, budgets et gestion financière

Ce domaine couvre :

- coffres ;
- objectifs ;
- arrondis automatiques ;
- versements programmés ;
- budgets ;
- catégories ;
- prévisions ;
- abonnements détectés ;
- analyse des dépenses ;
- recommandations ;
- alertes ;
- rapports.

## 3.10 Fidélité et promotions

Ce domaine couvre :

- points ;
- cashback ;
- récompenses ;
- coupons ;
- cadeaux ;
- niveaux ;
- programmes marchands ;
- campagnes ;
- offres ciblées ;
- conditions d’éligibilité ;
- expiration ;
- remboursements de points ;
- statistiques.

## 3.11 Services publics et institutionnels

Ce domaine couvre :

- amendes ;
- taxes ;
- démarches ;
- paiements administratifs ;
- cartes étudiantes ;
- bourses ;
- frais scolaires ;
- documents publics ;
- identification des agents ;
- traçabilité ;
- validation ;
- contrôle anti-corruption ;
- rapprochement avec les organismes concernés.

L’activation dépend d’accords institutionnels.

## 3.12 Investissements

Ce domaine couvre :

- produits d’investissement ;
- projets ;
- souscriptions ;
- portefeuille ;
- performance ;
- rendement ;
- documents ;
- risques ;
- disponibilité selon le pays ;
- validation réglementaire ;
- limites ;
- historique.

Aucun produit d’investissement ne doit être activé sans partenaire et autorisation appropriés.

## 3.13 Support et litiges

Ce domaine couvre :

- centre d’aide ;
- tickets ;
- chat support ;
- appels éventuels ;
- pièces jointes ;
- litiges de paiement ;
- remboursements ;
- contestations ;
- fraude ;
- escalade ;
- SLA ;
- satisfaction ;
- audit.

## 3.14 Notifications et communications

Canaux :

- push ;
- e-mail ;
- SMS ;
- notifications internes ;
- WhatsApp lorsque autorisé ;
- messages administratifs ;
- bannières ;
- alertes de sécurité.

Les notifications critiques ne doivent pas pouvoir être totalement désactivées.

## 3.15 Documents

Ce domaine couvre :

- reçus ;
- factures ;
- contrats ;
- justificatifs ;
- documents KYC ;
- documents KYB ;
- attestations ;
- relevés ;
- exports ;
- garanties ;
- documents fiscaux ;
- documents institutionnels ;
- stockage ;
- signature ;
- expiration ;
- contrôle d’accès.

## 3.16 Analytics et reporting

Ce domaine couvre :

- événements d’usage ;
- métriques produit ;
- rapports financiers ;
- rapports commerçants ;
- tableaux de bord ;
- performances ;
- fraude ;
- support ;
- conversions ;
- rétention ;
- revenus ;
- commissions ;
- disponibilité technique.

Les analytics ne doivent jamais exposer de secrets, codes, mots de passe ou contenu privé non nécessaire.

## 3.17 Audit et conformité

Ce domaine couvre :

- journal d’audit ;
- historique des changements ;
- décisions administratives ;
- approbations ;
- accès sensibles ;
- export ;
- conservation ;
- règles AML ;
- contrôles KYC/KYB ;
- sanctions ;
- alertes ;
- preuves ;
- séparation des responsabilités.

# 4. Responsabilités des applications

## 4.1 Mansa Client

Responsable de l’expérience des particuliers.

Elle permet notamment :

- créer un compte ;
- gérer son profil ;
- consulter ses soldes ;
- envoyer et recevoir de l’argent ;
- gérer ses cartes ;
- utiliser QR et NFC ;
- utiliser Mansa Connect ;
- gérer budgets et coffres ;
- consulter ses documents ;
- accéder à Jini ;
- utiliser les services publics disponibles ;
- accéder aux investissements autorisés ;
- gérer ses paramètres et sa sécurité.

Elle ne gère pas :

- le stock complet d’un commerce ;
- la configuration globale de la plateforme ;
- l’administration des partenaires ;
- la gestion technique des TPE ;
- les règles centrales de fraude.

## 4.2 Mansa Commerce

Responsable de la gestion professionnelle.

Elle permet :

- créer et gérer un commerce ;
- gérer les établissements ;
- gérer les employés ;
- gérer les produits et services ;
- gérer les stocks ;
- consulter les ventes ;
- créer des promotions ;
- gérer les clients ;
- gérer la fidélité ;
- produire des factures et reçus ;
- traiter certains retours et remboursements ;
- administrer le profil Annuaire ;
- piloter les TPE associés.

Elle ne remplace pas le terminal d’encaissement dans les usages où un TPE dédié est nécessaire.

## 4.3 Mansa TPE

Responsable de l’encaissement opérationnel.

Elle doit rester :

- rapide ;
- lisible ;
- fiable ;
- sécurisée ;
- adaptée à un usage intensif ;
- compatible avec plusieurs terminaux ;
- utilisable par des employés aux droits limités.

Elle ne doit pas contenir toute la gestion stratégique du commerce.

## 4.4 Mansa Admin Lite

Responsable des tâches mobiles urgentes ou limitées.

Elle peut permettre :

- consulter une alerte ;
- approuver une action autorisée ;
- suspendre temporairement un compte ;
- suivre un incident ;
- répondre à un ticket ;
- consulter un tableau de bord simplifié.

Elle ne doit pas exposer toutes les fonctions sensibles du portail Admin.

## 4.5 Mansa Annuaire / Hub

Responsable de la découverte publique des professionnels.

Elle permet :

- rechercher ;
- filtrer ;
- localiser ;
- consulter ;
- contacter ;
- réserver ;
- payer ;
- enregistrer un favori ;
- consulter une promotion ;
- laisser un avis lorsque permis.

Elle ne gère pas directement les stocks internes, les employés ou la comptabilité du professionnel.

## 4.6 Site public Mansa

Responsable de :

- présenter Mansa ;
- expliquer les produits ;
- rassurer sur la sécurité ;
- publier les tarifs ;
- publier les chiffres ;
- présenter les partenaires ;
- fournir les liens de téléchargement ;
- publier les pages légales ;
- publier les actualités ;
- collecter des contacts et candidatures.

## 4.7 Site Mansa Professionnels

Responsable de :

- présenter les offres professionnelles ;
- expliquer les TPE ;
- expliquer Tap to Phone ;
- présenter les abonnements ;
- présenter les outils commerce ;
- collecter les demandes de démonstration ;
- collecter les demandes de devis ;
- accompagner l’inscription professionnelle ;
- publier la documentation commerciale.

## 4.8 Portail Admin Web

Responsable de l’administration centrale.

Il doit gérer :

- configuration ;
- utilisateurs ;
- professionnels ;
- partenaires ;
- paiements ;
- cartes ;
- TPE ;
- services publics ;
- investissements ;
- contenus ;
- abonnements ;
- commissions ;
- fraude ;
- support ;
- sécurité ;
- audit ;
- reporting ;
- feature flags ;
- environnements.

# 5. Services fonctionnels communs

## 5.1 Identité

Utilisé par toutes les applications.

## 5.2 Authentification

Utilisé par toutes les applications avec des politiques différentes selon le niveau de risque.

## 5.3 Permissions

Centralise :

- rôles ;
- droits ;
- ressources ;
- actions ;
- périmètres ;
- établissements ;
- pays ;
- environnements.

## 5.4 Paiement

Centralise :

- orchestration ;
- frais ;
- limites ;
- statuts ;
- idempotence ;
- partenaires ;
- rapprochement ;
- notifications ;
- audit.

## 5.5 Notifications

Centralise les préférences, modèles, canaux, priorités et historiques.

## 5.6 Documents

Centralise le stockage sécurisé et les droits d’accès.

## 5.7 Recherche

Permet la recherche globale dans :

- utilisateurs ;
- commerçants ;
- transactions ;
- conversations ;
- documents ;
- services ;
- produits ;
- administrations.

## 5.8 Configuration

Centralise :

- pays ;
- devises ;
- langues ;
- plafonds ;
- frais ;
- feature flags ;
- versions minimales ;
- règles produit.

## 5.9 Audit

Centralise les événements critiques et les preuves de modification.

## 5.10 Jini

Fournit des capacités IA contrôlées aux différentes applications.

# 6. Flux fonctionnels principaux

## 6.1 Inscription d’un particulier

1. L’utilisateur ouvre Mansa Client.
2. Il choisit son pays et sa langue.
3. Il fournit son téléphone ou son e-mail.
4. Le système vérifie l’identifiant.
5. L’utilisateur crée ses moyens d’accès.
6. Il accepte les conditions nécessaires.
7. Il commence ou complète son KYC.
8. Le backend crée son profil et ses ressources autorisées.
9. Les fonctions disponibles sont activées selon son pays et son niveau de vérification.
10. L’utilisateur accède à l’accueil.

## 6.2 Inscription d’un commerçant

1. Création ou association d’un compte utilisateur.
2. Saisie de l’entreprise.
3. Vérification KYB.
4. Création de l’établissement.
5. Choix de l’offre.
6. Configuration des produits et employés.
7. Demande ou association d’un TPE.
8. Publication éventuelle dans l’Annuaire.
9. Activation après contrôles requis.

## 6.3 Paiement entre utilisateurs

1. Sélection du destinataire.
2. Vérification de son identité affichable.
3. Saisie du montant.
4. Simulation des frais et du change.
5. Contrôles de solde, plafond et risque.
6. Authentification adaptée.
7. Création de la transaction.
8. Écriture financière.
9. Notification des parties.
10. Génération du reçu.
11. Mise à jour éventuelle dans Mansa Connect.

## 6.4 Paiement marchand

1. Le commerçant crée une demande d’encaissement.
2. Le client choisit le moyen de paiement.
3. Le backend vérifie les règles.
4. Le partenaire concerné est sollicité si nécessaire.
5. Le paiement est autorisé, refusé ou placé en attente.
6. Le ledger est mis à jour.
7. Le commerçant reçoit la confirmation.
8. Le client reçoit le reçu.
9. Les ventes, stocks et rapports sont mis à jour.

## 6.5 Remboursement

1. Le professionnel ou le support lance une demande.
2. Le système vérifie les droits.
3. Le montant remboursable est calculé.
4. Une approbation supplémentaire peut être exigée.
5. Une transaction de remboursement est créée.
6. Les soldes et rapports sont mis à jour.
7. Les parties sont notifiées.
8. L’opération est auditée.

## 6.6 Paiement d’un service public

1. L’utilisateur choisit le service.
2. Il fournit la référence demandée.
3. Le backend consulte ou vérifie l’organisme partenaire.
4. Le montant et les informations sont affichés.
5. L’utilisateur confirme.
6. Le paiement est exécuté.
7. Une preuve est générée.
8. L’organisme reçoit la confirmation.
9. L’opération reste traçable.

# 7. Séparation entre démonstration, recette et production

## 7.1 Démonstration

Permet de présenter les interfaces sans argent réel.

Les données doivent être clairement identifiées comme fictives.

## 7.2 Recette

Permet les tests avec partenaires, équipes et scénarios contrôlés.

## 7.3 Production

Utilise :

- données réelles ;
- partenaires réels ;
- secrets réels ;
- règles réglementaires ;
- surveillance renforcée ;
- audit complet.

Aucune donnée de démonstration ne doit être confondue avec une donnée de production.

# 8. Fonctionnalités dépendantes de partenaires

Dépendances principales :

- émission de cartes ;
- Visa ;
- Mastercard ;
- comptes bancaires ;
- virements ;
- Mobile Money ;
- Apple Wallet ;
- Google Wallet ;
- Tap to Phone ;
- SMS ;
- vérification d’identité ;
- services publics ;
- cartes étudiantes ;
- bourses ;
- investissements ;
- logistique de cartes ;
- points relais ;
- impression ou matériel TPE selon le modèle.

La documentation doit distinguer :

- interface prévue ;
- simulation ;
- intégration technique ;
- certification ;
- autorisation légale ;
- activation commerciale.

# 9. Gestion des événements

Les modules doivent communiquer par événements lorsque cela réduit le couplage.

Exemples :

- utilisateur créé ;
- KYC vérifié ;
- paiement autorisé ;
- paiement échoué ;
- remboursement terminé ;
- carte bloquée ;
- stock faible ;
- ticket créé ;
- fraude détectée ;
- document disponible ;
- objectif atteint ;
- campagne activée.

Les événements ne remplacent pas les validations synchrones nécessaires aux opérations critiques.

# 10. Gestion des états

Chaque entité importante doit posséder un cycle de vie explicite.

### Utilisateur

- invité ;
- inscrit ;
- vérification en cours ;
- actif ;
- limité ;
- suspendu ;
- bloqué ;
- fermé.

### Paiement

- brouillon ;
- initié ;
- en validation ;
- autorisé ;
- en traitement ;
- terminé ;
- refusé ;
- expiré ;
- annulé ;
- remboursé ;
- contesté.

### Commerce

- brouillon ;
- KYB en cours ;
- en revue ;
- validé ;
- actif ;
- limité ;
- suspendu ;
- fermé.

### Carte

- commandée ;
- fabriquée ;
- expédiée ;
- livrée ;
- activée ;
- verrouillée ;
- suspendue ;
- expirée ;
- remplacée ;
- opposée.

# 11. Règles de cohérence fonctionnelle

1. Une opération financière confirmée ne doit jamais être supprimée.
2. Une correction financière doit produire une écriture distincte.
3. Un statut visible dans une application doit correspondre au statut backend.
4. Une fonctionnalité désactivée par pays ne doit pas apparaître comme disponible.
5. Une permission refusée côté backend doit rester refusée même si l’interface est modifiée.
6. Les données sensibles ne doivent pas être dupliquées inutilement.
7. Les documents doivent respecter leur politique de conservation.
8. Les notifications ne constituent pas une preuve unique d’exécution.
9. Les rapports doivent être reconstruisibles à partir des données officielles.
10. Jini ne doit jamais contourner une règle métier ou une permission.
11. Les actions administratives critiques doivent être auditées.
12. Les intégrations partenaires doivent gérer les délais, erreurs et doublons.
13. Toute commande financière doit utiliser une clé d’idempotence lorsque nécessaire.
14. Les applications doivent gérer les statuts intermédiaires.
15. Une indisponibilité partenaire ne doit pas produire une fausse réussite.

# 12. Disponibilité fonctionnelle

Chaque module doit définir son comportement lorsque :

- Internet est lent ;
- Internet est absent ;
- le backend est indisponible ;
- un partenaire est indisponible ;
- une requête expire ;
- une transaction reste en attente ;
- une synchronisation échoue ;
- l’application est trop ancienne ;
- le service est en maintenance.

Les écrans doivent distinguer clairement :

- donnée réelle ;
- donnée en cache ;
- estimation ;
- opération en attente ;
- opération échouée ;
- opération définitivement confirmée.

# 13. Administration et paramétrage

Le portail Admin doit permettre de configurer les fonctionnalités sans modifier le code lorsque cela est raisonnable.

Chaque paramètre doit préciser :

- clé ;
- valeur ;
- type ;
- pays ;
- environnement ;
- module ;
- version ;
- auteur ;
- date ;
- justification ;
- approbation éventuelle ;
- historique.

Les paramètres critiques doivent être protégés par :

- permissions spécifiques ;
- réauthentification ;
- double validation ;
- audit ;
- notification ;
- possibilité de retour arrière lorsque adaptée.

# 14. Sécurité fonctionnelle

La sécurité fonctionnelle comprend :

- moindre privilège ;
- séparation des rôles ;
- authentification récente ;
- limites ;
- contrôle de risque ;
- blocage d’urgence ;
- journalisation ;
- approbation ;
- confirmation explicite ;
- masquage des secrets ;
- notifications de sécurité ;
- gestion des appareils ;
- révocation de session ;
- protection contre le spam ;
- protection contre les abus ;
- signalement.

# 15. Critères d’acceptation de l’architecture fonctionnelle

L’architecture fonctionnelle est considérée comme validée lorsque :

- chaque application possède un périmètre clair ;
- les responsabilités ne sont pas inutilement dupliquées ;
- le backend reste la source d’autorité ;
- les flux critiques sont identifiés ;
- les dépendances partenaires sont distinguées ;
- les services communs sont définis ;
- les cycles de vie principaux sont documentés ;
- les fonctions multi-pays sont prises en compte ;
- les règles d’administration sont définies ;
- les limites entre démonstration, recette et production sont claires ;
- les comportements en erreur sont prévus ;
- les fonctions IA restent sous contrôle ;
- les opérations critiques sont auditables.

# 16. Documents suivants liés

Cette architecture sera détaillée dans :

- architecture technique ;
- sécurité globale ;
- rôles et permissions ;
- modèle de données ;
- contrats API ;
- application Client ;
- application Commerce ;
- application TPE ;
- application Admin Lite ;
- application Annuaire / Hub ;
- sites web ;
- portail Admin ;
- IA Jini ;
- infrastructure ;
- tests ;
- déploiement.
