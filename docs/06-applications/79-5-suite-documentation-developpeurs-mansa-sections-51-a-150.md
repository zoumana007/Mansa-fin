# 79.5 — Suite de la Documentation Développeurs Mansa : sections 51 à 150

# 51. Gestion du compte développeur

Le compte développeur doit permettre :

- création de profil ;
- vérification de l’e-mail ;
- vérification du téléphone ;
- gestion du mot de passe ;
- activation MFA ;
- gestion des appareils ;
- gestion des sessions ;
- gestion des organisations ;
- gestion des invitations ;
- gestion des préférences ;
- fermeture du compte.

---

# 52. Organisation développeur

Un compte développeur peut appartenir à :

- une entreprise ;
- une startup ;
- une banque ;
- une institution ;
- une école ;
- une équipe interne ;
- un partenaire technique ;
- une agence d’intégration.

Chaque organisation doit posséder :

- identifiant ;
- nom ;
- pays ;
- secteur ;
- site web ;
- logo ;
- représentant ;
- statut KYB ;
- environnement autorisé ;
- membres ;
- applications ;
- clés ;
- contrats ;
- historique.

---

# 53. Statuts d’une organisation

- DRAFT ;
- PENDING_VERIFICATION ;
- VERIFIED ;
- ACTIVE ;
- SUSPENDED ;
- RESTRICTED ;
- REJECTED ;
- CLOSED.

---

# 54. Gestion des membres

L’organisation doit pouvoir :

- inviter un membre ;
- supprimer un membre ;
- suspendre un membre ;
- modifier son rôle ;
- limiter ses accès ;
- consulter son historique ;
- révoquer ses sessions.

---

# 55. Rôles d’organisation

Exemples :

```text
ORGANIZATION_OWNER
ORGANIZATION_ADMIN
DEVELOPER
TECHNICAL_MANAGER
SECURITY_MANAGER
BILLING_MANAGER
SUPPORT_MANAGER
AUDITOR
VIEWER
```

---

# 56. Création d’une application développeur

Chaque intégration doit être représentée par une application.

Une application possède :

- identifiant ;
- nom ;
- description ;
- organisation ;
- environnement ;
- logo ;
- URL ;
- type ;
- pays ;
- produits activés ;
- permissions ;
- statut ;
- date de création ;
- propriétaire technique.

---

# 57. Types d’applications

- WEB ;
- MOBILE ;
- BACKEND ;
- ECOMMERCE ;
- ERP ;
- TPE ;
- INSTITUTION ;
- EDUCATION ;
- BANKING ;
- INTERNAL ;
- PARTNER_CONNECTOR ;
- TEST.

---

# 58. Statuts d’une application

- DRAFT ;
- SANDBOX_ACTIVE ;
- PENDING_REVIEW ;
- PRODUCTION_APPROVED ;
- ACTIVE ;
- SUSPENDED ;
- REVOKED ;
- ARCHIVED.

---

# 59. Passage en Production

Le passage en Production doit exiger :

- organisation vérifiée ;
- application complète ;
- cas d’usage déclaré ;
- politique de confidentialité ;
- conditions d’utilisation ;
- URL de production ;
- webhooks configurés ;
- tests Sandbox réussis ;
- revue sécurité ;
- revue conformité ;
- limites définies ;
- contrat accepté ;
- validation Mansa.

---

# 60. Checklist Production

La checklist doit vérifier :

- authentification ;
- signatures ;
- idempotence ;
- gestion des erreurs ;
- sécurité des secrets ;
- stockage des données ;
- webhooks ;
- retries ;
- timeouts ;
- journalisation ;
- conformité ;
- support ;
- monitoring ;
- capacité ;
- procédure d’incident.

---

# 61. Scopes API

Exemples :

```text
payments.read
payments.write
payments.refund
transfers.read
transfers.write
customers.read
customers.write
invoices.read
invoices.write
webhooks.manage
reports.read
cards.read
cards.tokenize
merchant.read
merchant.write
```

---

# 62. Principe du moindre privilège

Une application ne doit recevoir que les permissions nécessaires à son fonctionnement.

Les scopes sensibles doivent :

- être demandés explicitement ;
- être justifiés ;
- être validés ;
- être auditables ;
- pouvoir être révoqués ;
- avoir éventuellement une expiration.

---

# 63. Rotation des clés

Le portail doit permettre :

- créer une nouvelle clé ;
- conserver temporairement l’ancienne ;
- tester la nouvelle ;
- révoquer l’ancienne ;
- programmer une rotation ;
- recevoir une alerte d’expiration ;
- consulter l’historique.

---

# 64. Révocation d’une clé

La révocation doit être :

- immédiate ;
- confirmée ;
- journalisée ;
- notifiée ;
- irréversible pour la clé concernée.

---

# 65. Restrictions IP

Une clé peut être limitée à :

- une adresse IP ;
- plusieurs adresses ;
- une plage ;
- un réseau privé ;
- un environnement ;
- une région.

---

# 66. Restrictions de domaine

Les applications web peuvent déclarer :

- domaines autorisés ;
- sous-domaines ;
- URLs de redirection ;
- URLs de callback ;
- origines autorisées.

---

# 67. OAuth 2.0

Lorsque OAuth est activé, la documentation doit couvrir :

- authorization code ;
- PKCE ;
- client credentials ;
- refresh token ;
- scopes ;
- consentement ;
- révocation ;
- expiration ;
- redirection ;
- erreurs.

---

# 68. Consentement OAuth

L’écran de consentement doit afficher :

- nom de l’application ;
- organisation ;
- permissions demandées ;
- durée ;
- données accessibles ;
- bouton Autoriser ;
- bouton Refuser ;
- lien vers les conditions ;
- lien vers la confidentialité.

---

# 69. Refresh Tokens

Les refresh tokens doivent être :

- protégés ;
- rotatifs ;
- révocables ;
- limités ;
- liés à un client ;
- liés à un environnement ;
- journalisés.

---

# 70. Authentification mutuelle

Pour certains partenaires, Mansa peut exiger :

- mTLS ;
- certificat client ;
- certificat serveur ;
- rotation ;
- révocation ;
- liste blanche ;
- validation d’identité.

---

# 71. Signature des requêtes

La documentation doit expliquer :

- algorithme ;
- ordre des champs ;
- timestamp ;
- nonce ;
- corps ;
- secret ;
- encodage ;
- validation ;
- erreurs ;
- exemple.

---

# 72. Protection contre le rejeu

Les requêtes sensibles doivent utiliser :

- timestamp ;
- nonce ;
- fenêtre de validité ;
- signature ;
- identifiant unique ;
- contrôle d’idempotence.

---

# 73. Horodatage

La documentation doit préciser :

- format UTC ;
- fuseau ;
- précision ;
- tolérance ;
- synchronisation de l’horloge ;
- erreurs associées.

---

# 74. Identifiants

Chaque objet doit avoir :

- identifiant Mansa ;
- éventuelle référence externe ;
- type ;
- date ;
- environnement ;
- statut.

---

# 75. Références externes

Le partenaire peut fournir une référence externe pour :

- paiement ;
- transfert ;
- facture ;
- client ;
- commande ;
- remboursement ;
- règlement.

Elle doit être unique dans le périmètre défini.

---

# 76. Version des API

Exemples :

```text
/v1/payments
/v1/transfers
/v2/payments
```

La version doit être visible dans :

- URL ;
- documentation ;
- SDK ;
- changelog ;
- erreurs ;
- logs.

---

# 77. Compatibilité descendante

Une version mineure ne doit pas casser les intégrations existantes.

Les changements incompatibles doivent passer par :

- nouvelle version ;
- période de migration ;
- documentation ;
- avertissement ;
- date de fin de support.

---

# 78. Politique de dépréciation

La politique doit définir :

- durée minimale ;
- communication ;
- bannière ;
- e-mail ;
- changelog ;
- date limite ;
- solution de remplacement ;
- support de migration.

---

# 79. API de paiement — création

Exemple :

```http
POST /v1/payments
```

Le corps peut contenir :

- amount ;
- currency ;
- description ;
- customer ;
- merchantReference ;
- paymentMethod ;
- returnUrl ;
- metadata ;
- idempotencyKey.

---

# 80. API de paiement — réponse

La réponse peut contenir :

- paymentId ;
- status ;
- amount ;
- currency ;
- fees ;
- paymentUrl ;
- qrCode ;
- expiresAt ;
- createdAt ;
- merchantReference.

---

# 81. Moyens de paiement API

Les moyens possibles peuvent inclure :

- MANSA_WALLET ;
- CARD ;
- MOBILE_MONEY ;
- QR ;
- BANK_TRANSFER ;
- PAYMENT_LINK ;
- TPE ;
- CASH_AGENT ;
- OTHER_SUPPORTED_METHOD.

---

# 82. Statuts d’un paiement

- CREATED ;
- REQUIRES_ACTION ;
- PENDING ;
- AUTHORIZED ;
- PROCESSING ;
- COMPLETED ;
- FAILED ;
- CANCELLED ;
- EXPIRED ;
- REVERSED ;
- REFUNDED ;
- PARTIALLY_REFUNDED.

---

# 83. Confirmation de paiement

La confirmation peut être :

- synchrone ;
- asynchrone ;
- via redirection ;
- via webhook ;
- via consultation du statut ;
- via SDK mobile.

---

# 84. API de remboursement

Exemple :

```http
POST /v1/payments/{paymentId}/refunds
```

Le corps peut contenir :

- amount ;
- reason ;
- merchantReference ;
- metadata ;
- idempotencyKey.

---

# 85. Statuts de remboursement

- CREATED ;
- PENDING ;
- PROCESSING ;
- COMPLETED ;
- FAILED ;
- CANCELLED ;
- REVIEW_REQUIRED.

---

# 86. API de transfert

Exemple :

```http
POST /v1/transfers
```

Le corps peut contenir :

- source ;
- destination ;
- amount ;
- currency ;
- reason ;
- beneficiary ;
- reference ;
- metadata ;
- idempotencyKey.

---

# 87. Types de transfert

- MANSA_TO_MANSA ;
- BANK_TRANSFER ;
- MOBILE_MONEY_TRANSFER ;
- INTERNATIONAL_TRANSFER ;
- MASS_TRANSFER ;
- SALARY_PAYMENT ;
- INSTITUTIONAL_PAYMENT.

---

# 88. API de bénéficiaires

Elle doit permettre :

- créer ;
- consulter ;
- modifier ;
- désactiver ;
- vérifier ;
- lister.

---

# 89. Vérification du bénéficiaire

L’API peut retourner :

- nom masqué ;
- institution ;
- opérateur ;
- statut ;
- devise ;
- pays ;
- validation ;
- avertissement.

---

# 90. API de facturation

Elle doit permettre :

- créer une facture ;
- ajouter des lignes ;
- envoyer ;
- consulter ;
- annuler ;
- payer ;
- générer un avoir ;
- télécharger.

---

# 91. Statuts d’une facture

- DRAFT ;
- OPEN ;
- SENT ;
- VIEWED ;
- PARTIALLY_PAID ;
- PAID ;
- OVERDUE ;
- CANCELLED ;
- REFUNDED.

---

# 92. API de liens de paiement

Elle doit permettre :

- créer ;
- consulter ;
- modifier avant activation ;
- désactiver ;
- expirer ;
- lister ;
- suivre les paiements.

---

# 93. Paramètres d’un lien de paiement

- montant fixe ou libre ;
- devise ;
- description ;
- expiration ;
- nombre d’utilisations ;
- branding ;
- moyens autorisés ;
- redirection ;
- metadata ;
- référence externe.

---

# 94. API QR

Elle doit permettre :

- générer un QR ;
- résoudre un QR ;
- vérifier un QR ;
- expirer un QR ;
- consulter le statut ;
- associer une transaction.

---

# 95. QR sécurisé

Le QR doit pouvoir contenir :

- identifiant ;
- signature ;
- expiration ;
- montant ;
- devise ;
- commerçant ;
- contexte ;
- version.

---

# 96. API Mobile Money

Elle doit permettre :

- initier une demande ;
- consulter le statut ;
- annuler si possible ;
- recevoir la confirmation ;
- rembourser selon partenaire ;
- lister les opérateurs.

---

# 97. Gestion des opérateurs

L’API doit pouvoir retourner :

- opérateur ;
- pays ;
- devise ;
- disponibilité ;
- limites ;
- frais ;
- délais ;
- statut.

---

# 98. API Cartes

Selon les droits, elle peut permettre :

- tokeniser ;
- autoriser ;
- capturer ;
- annuler ;
- rembourser ;
- consulter ;
- gérer une préautorisation.

---

# 99. Tokenisation

La documentation doit expliquer :

- création du token ;
- usage ;
- durée ;
- portée ;
- carte liée ;
- sécurité ;
- suppression ;
- restrictions.

---

# 100. API Clients

Elle doit permettre :

- créer un profil ;
- consulter ;
- modifier ;
- rechercher ;
- désactiver ;
- associer des moyens de paiement ;
- gérer les consentements.

---

# 101. Données client

Les champs doivent être classés en :

- obligatoires ;
- facultatifs ;
- sensibles ;
- interdits sans consentement ;
- dépendants du pays ;
- dépendants du produit.

---

# 102. API Commerce

Elle peut couvrir :

- commerces ;
- points de vente ;
- produits ;
- stocks ;
- commandes ;
- factures ;
- employés ;
- règlements ;
- rapports.

---

# 103. API de rapports

Elle doit permettre :

- demander un rapport ;
- consulter son statut ;
- télécharger ;
- programmer ;
- filtrer ;
- choisir un format.

---

# 104. Rapports asynchrones

Les rapports volumineux doivent être générés de manière asynchrone.

Statuts :

- REQUESTED ;
- PROCESSING ;
- READY ;
- FAILED ;
- EXPIRED.

---

# 105. API de fichiers

Elle peut permettre :

- téléverser ;
- télécharger ;
- lier à un objet ;
- consulter ;
- supprimer selon droits ;
- vérifier le statut antivirus.

---

# 106. Contrôle des fichiers

Les fichiers doivent être contrôlés selon :

- type ;
- taille ;
- extension ;
- malware ;
- contenu ;
- chiffrement ;
- durée ;
- propriétaire ;
- pays.

---

# 107. Webhooks — livraison

Chaque livraison doit contenir :

- eventId ;
- eventType ;
- createdAt ;
- data ;
- signature ;
- version ;
- attempt ;
- environment.

---

# 108. Retries Webhooks

Les retries doivent être documentés selon :

- nombre de tentatives ;
- délai ;
- backoff ;
- erreurs concernées ;
- expiration ;
- passage en Dead Letter Queue.

---

# 109. Codes attendus pour les webhooks

Le partenaire doit répondre avec un code HTTP de succès dans le délai défini.

Les réponses suivantes doivent être documentées :

- 200 ;
- 201 ;
- 202 ;
- 204 ;
- 400 ;
- 401 ;
- 403 ;
- 404 ;
- 429 ;
- 500 ;
- 503.

---

# 110. Rejeu manuel d’un webhook

Le portail doit permettre :

- sélectionner un événement ;
- rejouer ;
- choisir l’URL ;
- confirmer ;
- consulter la réponse ;
- journaliser l’action.

---

# 111. Vérification de signature Webhook

Exemple général :

```text
signature = HMAC_SHA256(
  webhook_secret,
  timestamp + "." + raw_body
)
```

La documentation doit fournir des exemples dans plusieurs langages.

---

# 112. Protection contre les faux webhooks

Le partenaire doit vérifier :

- signature ;
- timestamp ;
- environnement ;
- eventId ;
- certificat éventuel ;
- origine ;
- répétition ;
- version.

---

# 113. Ordre des événements

La documentation doit préciser que les événements peuvent être reçus dans un ordre différent.

Le partenaire doit utiliser :

- statut ;
- date ;
- version ;
- identifiant ;
- idempotence ;
- récupération API.

---

# 114. Duplication des événements

Un webhook peut être livré plusieurs fois.

Le partenaire doit dédupliquer par :

- eventId ;
- référence ;
- statut ;
- idempotence.

---

# 115. Console Webhook

Le portail doit permettre :

- consulter les événements ;
- filtrer ;
- voir le payload ;
- voir la réponse ;
- rejouer ;
- désactiver une URL ;
- renouveler le secret ;
- tester.

---

# 116. Simulateur Webhook

Le Sandbox doit permettre de simuler :

- paiement réussi ;
- paiement échoué ;
- remboursement ;
- transfert ;
- expiration ;
- litige ;
- règlement ;
- erreur partenaire.

---

# 117. Explorer API

La documentation doit proposer un explorateur permettant :

- sélectionner un endpoint ;
- saisir les paramètres ;
- utiliser une clé Sandbox ;
- envoyer ;
- voir la requête ;
- voir la réponse ;
- copier le code ;
- sauvegarder un exemple.

---

# 118. Exécution sécurisée dans le navigateur

L’explorateur ne doit jamais exposer :

- secrets Production ;
- clés privées ;
- données réelles sensibles ;
- certificats ;
- accès administrateur.

---

# 119. Collection Postman

Une collection peut être fournie avec :

- environnements ;
- variables ;
- authentification ;
- exemples ;
- tests ;
- dossiers ;
- version ;
- documentation.

---

# 120. Collection Bruno ou Insomnia

Des collections supplémentaires peuvent être proposées selon la demande et la stratégie.

---

# 121. CLI Mansa

Une CLI peut permettre :

- connexion ;
- création d’application ;
- gestion des clés ;
- tests ;
- consultation d’événements ;
- écoute de webhooks ;
- déploiement de configuration ;
- génération de types.

---

# 122. Commandes CLI possibles

```bash
mansa login
mansa apps list
mansa keys create
mansa webhooks listen
mansa events replay
mansa openapi download
mansa sdk generate
```

---

# 123. SDK JavaScript et TypeScript

Le SDK doit proposer :

- client typé ;
- gestion automatique de l’authentification ;
- idempotence ;
- retries contrôlés ;
- erreurs typées ;
- pagination ;
- webhooks ;
- documentation ;
- exemples.

---

# 124. SDK Mobile

Les SDK mobile peuvent faciliter :

- paiement ;
- QR ;
- redirection ;
- authentification ;
- retour d’état ;
- tokenisation ;
- gestion des erreurs ;
- reprise de session.

---

# 125. SDK Backend

Les SDK backend doivent privilégier :

- sécurité ;
- typage ;
- compatibilité ;
- logs ;
- timeouts ;
- retries ;
- webhooks ;
- idempotence.

---

# 126. Versionnement des SDK

Chaque SDK doit posséder :

- version ;
- changelog ;
- compatibilité API ;
- date ;
- statut ;
- dépendances ;
- fin de support ;
- exemples.

---

# 127. Signature des packages SDK

Les packages doivent être :

- publiés officiellement ;
- signés lorsque possible ;
- vérifiables ;
- accompagnés de hash ;
- protégés contre l’usurpation ;
- liés au dépôt officiel.

---

# 128. Dépôts SDK

Chaque SDK peut posséder :

- dépôt Git ;
- documentation ;
- exemples ;
- tests ;
- issues ;
- releases ;
- licence ;
- politique de contribution.

---

# 129. Génération automatique des SDK

Les SDK peuvent être partiellement générés depuis :

- OpenAPI ;
- schémas ;
- contrats ;
- modèles ;
- versions.

Ils doivent ensuite être :

- relus ;
- testés ;
- documentés ;
- validés.

---

# 130. Exemples complets

La documentation doit proposer des projets complets pour :

- paiement simple ;
- paiement e-commerce ;
- QR ;
- Mobile Money ;
- remboursement ;
- facture ;
- webhook ;
- application mobile ;
- intégration ERP ;
- marketplace.

---

# 131. Tutoriels

Exemples de tutoriels :

- accepter son premier paiement ;
- créer un lien de paiement ;
- recevoir un webhook ;
- intégrer Mobile Money ;
- sécuriser les clés ;
- gérer les remboursements ;
- migrer de v1 à v2 ;
- passer en Production ;
- intégrer Mansa dans une marketplace.

---

# 132. Guides d’architecture

La documentation doit proposer :

- architecture e-commerce ;
- architecture mobile ;
- architecture marketplace ;
- architecture institutionnelle ;
- architecture multi-commerçants ;
- architecture événementielle ;
- architecture haute disponibilité ;
- architecture de reprise.

---

# 133. Guide de gestion des erreurs

Il doit expliquer :

- erreurs permanentes ;
- erreurs temporaires ;
- retries ;
- timeout ;
- idempotence ;
- conflit ;
- authentification ;
- quota ;
- indisponibilité ;
- réconciliation.

---

# 134. Guide des timeouts

Le guide doit préciser :

- durée recommandée ;
- vérification du statut ;
- stratégie de retry ;
- protection contre le doublon ;
- journalisation ;
- alerte ;
- comportement utilisateur.

---

# 135. Guide d’idempotence

Il doit expliquer :

- génération de clé ;
- stockage ;
- durée ;
- réutilisation ;
- erreur de conflit ;
- résultats identiques ;
- cas limites.

---

# 136. Guide de sécurité

Il doit couvrir :

- stockage des secrets ;
- rotation ;
- moindre privilège ;
- mTLS ;
- signature ;
- IP allowlist ;
- logs ;
- chiffrement ;
- dépendances ;
- incidents ;
- audits.

---

# 137. Guide de conformité

Il doit expliquer :

- données personnelles ;
- conservation ;
- consentement ;
- KYC ;
- KYB ;
- AML/CFT ;
- pays ;
- sous-traitants ;
- transferts ;
- audits ;
- responsabilités.

---

# 138. Guide de mise en Production

Étapes :

1. terminer l’intégration Sandbox ;
2. exécuter les tests ;
3. configurer les webhooks ;
4. sécuriser les secrets ;
5. soumettre la demande ;
6. passer la revue ;
7. signer les contrats ;
8. recevoir les accès ;
9. effectuer les tests Production contrôlés ;
10. activer progressivement.

---

# 139. Certification d’intégration

Certaines intégrations peuvent nécessiter :

- tests automatiques ;
- tests fonctionnels ;
- tests sécurité ;
- preuve de webhook ;
- preuve d’idempotence ;
- test de remboursement ;
- test de timeout ;
- test de reprise ;
- validation Mansa.

---

# 140. Score de préparation

Le portail peut afficher un score basé sur :

- clés sécurisées ;
- webhooks configurés ;
- tests réussis ;
- politique de confidentialité ;
- contacts ;
- monitoring ;
- alertes ;
- conformité ;
- support ;
- documentation.

---

# 141. Journal d’activité développeur

Le portail doit enregistrer :

- connexion ;
- création d’application ;
- création de clé ;
- rotation ;
- révocation ;
- changement de scope ;
- ajout de webhook ;
- rejeu ;
- passage Production ;
- téléchargement SDK ;
- export ;
- support.

---

# 142. Alertes développeur

Exemples :

- clé expirante ;
- clé compromise ;
- quota proche ;
- taux d’erreur élevé ;
- webhook en échec ;
- nouvelle version ;
- dépréciation ;
- maintenance ;
- incident ;
- action de sécurité.

---

# 143. Notifications

Canaux possibles :

- e-mail ;
- SMS ;
- portail ;
- webhook ;
- application ;
- Slack ou Teams via intégration éventuelle.

---

# 144. Préférences de notifications

Le développeur peut configurer :

- sécurité ;
- incidents ;
- changelog ;
- dépréciations ;
- quota ;
- facturation ;
- support ;
- webhooks ;
- marketing technique.

Les alertes critiques doivent rester obligatoires.

---

# 145. Support technique avancé

Le support doit permettre :

- ticket ;
- chat ;
- partage de logs filtrés ;
- référence de requête ;
- incident ;
- priorité ;
- SLA ;
- environnement ;
- application ;
- endpoint ;
- erreur ;
- pièce jointe.

---

# 146. Ticket technique

Le ticket doit contenir :

- organisation ;
- application ;
- environnement ;
- endpoint ;
- date ;
- heure ;
- correlationId ;
- requestId ;
- code erreur ;
- description ;
- impact ;
- reproduction ;
- pièce jointe ;
- niveau d’urgence.

---

# 147. Statuts du ticket

- CREATED ;
- TRIAGED ;
- ASSIGNED ;
- IN_PROGRESS ;
- WAITING_DEVELOPER ;
- ESCALATED ;
- RESOLVED ;
- CLOSED ;
- REOPENED.

---

# 148. SLA développeur

Le SLA peut dépendre :

- offre ;
- environnement ;
- criticité ;
- partenaire ;
- pays ;
- produit ;
- incident ;
- heure ;
- contrat.

---

# 149. Tests

Les tests doivent couvrir :

- création de compte ;
- organisation ;
- application ;
- clé API ;
- scopes ;
- rotation ;
- révocation ;
- OAuth ;
- mTLS ;
- signature ;
- paiement ;
- transfert ;
- remboursement ;
- facture ;
- QR ;
- Mobile Money ;
- webhooks ;
- retries ;
- duplication ;
- ordre ;
- Sandbox ;
- SDK ;
- CLI ;
- documentation ;
- changelog ;
- dépréciation ;
- passage Production ;
- permissions ;
- support ;
- sécurité ;
- accessibilité ;
- performance ;
- audit.

---

# 150. Critères d’acceptation finaux

La Documentation Développeurs Mansa est validée lorsque :

- les comptes développeurs sont gérés ;
- les organisations sont supportées ;
- les membres et rôles sont gérés ;
- les applications développeurs sont créables ;
- les statuts sont administrables ;
- le passage en Production est contrôlé ;
- la checklist Production est disponible ;
- les scopes API sont définis ;
- le moindre privilège est appliqué ;
- les clés peuvent être créées ;
- les clés peuvent être rotatives ;
- les clés peuvent être révoquées ;
- les restrictions IP sont disponibles ;
- les domaines autorisés sont gérés ;
- OAuth est documenté ;
- PKCE est supportable ;
- les refresh tokens sont protégés ;
- mTLS est supportable ;
- les signatures de requêtes sont documentées ;
- la protection contre le rejeu est intégrée ;
- les horodatages sont normalisés ;
- les identifiants sont définis ;
- les références externes sont supportées ;
- les versions API sont gérées ;
- la compatibilité descendante est encadrée ;
- la politique de dépréciation est définie ;
- l’API Paiement est documentée ;
- les statuts de paiement sont définis ;
- l’API Remboursement est documentée ;
- l’API Transfert est documentée ;
- les bénéficiaires sont gérés ;
- les factures sont gérées ;
- les liens de paiement sont gérés ;
- les QR sont gérés ;
- Mobile Money est documenté ;
- les cartes et la tokenisation sont documentées ;
- l’API Clients est documentée ;
- l’API Commerce est documentée ;
- les rapports asynchrones sont supportés ;
- les fichiers sont contrôlés ;
- les webhooks sont signés ;
- les retries sont documentés ;
- les doublons sont gérés ;
- l’ordre des événements est pris en compte ;
- le rejeu manuel fonctionne ;
- le simulateur Webhook est disponible ;
- l’Explorer API fonctionne ;
- les secrets Production ne sont pas exposés ;
- les collections API sont disponibles ;
- une CLI est supportable ;
- les SDK sont versionnés ;
- les SDK sont testés ;
- les packages officiels sont vérifiables ;
- les dépôts SDK sont identifiés ;
- les exemples complets sont disponibles ;
- les tutoriels sont disponibles ;
- les guides d’architecture sont disponibles ;
- les guides d’erreurs sont disponibles ;
- les guides de timeout sont disponibles ;
- le guide d’idempotence est disponible ;
- le guide de sécurité est disponible ;
- le guide de conformité est disponible ;
- le guide de Production est disponible ;
- la certification d’intégration est définie ;
- le score de préparation est disponible ;
- les journaux d’activité sont disponibles ;
- les alertes développeur sont configurables ;
- les notifications critiques restent obligatoires ;
- le support technique est disponible ;
- les SLA sont définis ;
- les rôles et permissions sont appliqués ;
- les contenus sont versionnés ;
- les approbations critiques sont protégées ;
- les audits sont complets ;
- les audits sont immuables ;
- les tests couvrent les fonctions, la sécurité, les intégrations, la performance, la résilience et l’accessibilité.
