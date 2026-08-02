# 50 — Portail Partenaires et Développeurs Mansa : API, intégrations, webhooks, sandbox, clés, documentation et supervision

## 1. Objet du document

Ce document définit l’architecture officielle du **Portail Partenaires et Développeurs Mansa**.

Le portail permet aux partenaires autorisés d’intégrer les services Mansa dans leurs propres systèmes.

Il couvre :

- les banques ;
- les opérateurs Mobile Money ;
- les institutions publiques ;
- les établissements scolaires ;
- les universités ;
- les entreprises ;
- les plateformes numériques ;
- les commerçants avancés ;
- les fintechs partenaires ;
- les intégrateurs ;
- les fournisseurs techniques ;
- les développeurs ;
- les environnements de test ;
- les API ;
- les clés d’API ;
- OAuth ;
- les certificats ;
- les webhooks ;
- les événements ;
- la documentation ;
- les SDK ;
- les tests ;
- les journaux ;
- les quotas ;
- les versions ;
- les incidents ;
- les règlements ;
- les rapports ;
- le support ;
- les approbations ;
- la sécurité ;
- la conformité ;
- l’administration.

L’objectif est de fournir une plateforme permettant de :

- connecter des partenaires à Mansa ;
- tester une intégration sans toucher à la production ;
- gérer les accès et les permissions ;
- suivre les appels API ;
- recevoir des événements fiables ;
- diagnostiquer les erreurs ;
- gérer plusieurs applications partenaires ;
- protéger les données financières ;
- faire évoluer les API sans casser les intégrations ;
- industrialiser les partenariats à l’échelle nationale et régionale.

---

# 2. Principes fondamentaux

## 2.1 Aucun partenaire ne reçoit un accès global

Chaque partenaire doit disposer d’un périmètre limité selon :

- son contrat ;
- son pays ;
- ses produits ;
- ses organisations ;
- ses établissements ;
- ses opérations ;
- ses environnements ;
- ses permissions ;
- ses plafonds ;
- ses obligations réglementaires.

---

## 2.2 La sandbox est séparée de la production

Les environnements doivent être totalement séparés.

La sandbox ne doit jamais :

- utiliser de vrais soldes ;
- déclencher de vrais paiements ;
- envoyer de vrais règlements ;
- modifier le ledger de production ;
- utiliser de vraies clés de production ;
- donner accès aux données réelles des clients.

---

## 2.3 Les clés ne doivent jamais être visibles après création

Une clé secrète doit être :

- générée de manière sécurisée ;
- affichée une seule fois ;
- stockée sous forme protégée ;
- révocable ;
- rotative ;
- limitée à un environnement ;
- associée à des permissions ;
- surveillée.

---

## 2.4 Les intégrations doivent être versionnées

Chaque API doit disposer :

- d’une version ;
- d’un statut ;
- d’une documentation ;
- d’une date de publication ;
- d’une politique de compatibilité ;
- d’une date éventuelle de fin de support ;
- d’un historique des modifications.

---

## 2.5 Les webhooks doivent être fiables

Les webhooks doivent supporter :

- signature ;
- horodatage ;
- identifiant unique ;
- tentative multiple ;
- reprise ;
- ordre documenté ;
- idempotence ;
- journal ;
- rejeu contrôlé ;
- désactivation automatique en cas d’échec prolongé.

---

# 3. Types de partenaires

Le portail peut servir :

- banque partenaire ;
- opérateur Mobile Money ;
- réseau de cartes ;
- institution publique ;
- établissement scolaire ;
- université ;
- entreprise privée ;
- commerce ;
- plateforme e-commerce ;
- transporteur ;
- fournisseur de factures ;
- service d’eau ;
- service d’électricité ;
- assurance ;
- opérateur télécom ;
- intégrateur technique ;
- développeur indépendant approuvé ;
- partenaire régional.

---

# 4. Types d’intégration

Exemples :

- paiements ;
- transferts ;
- encaissements ;
- décaissements ;
- dépôts ;
- retraits ;
- Mobile Money ;
- cartes ;
- vérification de compte ;
- KYC ;
- KYB ;
- facturation ;
- services publics ;
- bourses ;
- scolarité ;
- amendes ;
- taxes ;
- règlements ;
- webhooks ;
- reporting ;
- réconciliation ;
- Hub ;
- identité ;
- notifications.

---

# 5. Technologie

Technologie recommandée pour le portail :

```text
Next.js
TypeScript
```

Composants possibles :

- portail web sécurisé ;
- documentation interactive ;
- OpenAPI ;
- OAuth 2.0 ;
- OIDC ;
- mTLS ;
- gestion de secrets ;
- API Gateway ;
- rate limiting ;
- webhooks ;
- journaux ;
- analytics ;
- sandbox ;
- SDK ;
- feature flags ;
- support intégré.

---

# 6. Architecture du projet

Structure recommandée :

```text
src/
├── auth/
├── organizations/
├── applications/
├── environments/
├── api-keys/
├── oauth-clients/
├── certificates/
├── permissions/
├── products/
├── api-catalog/
├── documentation/
├── playground/
├── webhooks/
├── events/
├── logs/
├── analytics/
├── quotas/
├── usage/
├── settlements/
├── reconciliation/
├── reports/
├── incidents/
├── support/
├── compliance/
├── approvals/
├── security/
└── settings/
```

---

# 7. Navigation principale

Navigation recommandée :

```text
Accueil
Applications
API
Webhooks
Journaux
Rapports
Support
```

Menu secondaire :

- Sandbox ;
- Production ;
- Clés ;
- Certificats ;
- OAuth ;
- Documentation ;
- SDK ;
- Quotas ;
- Règlements ;
- Équipe ;
- Sécurité ;
- Paramètres.

---

# 8. Onboarding partenaire

Le parcours peut inclure :

1. création du compte ;
2. vérification de l’e-mail ;
3. authentification renforcée ;
4. création de l’organisation ;
5. identification du représentant ;
6. KYB ;
7. bénéficiaires effectifs ;
8. documents ;
9. contrat ;
10. produits demandés ;
11. pays ;
12. volume estimé ;
13. revue conformité ;
14. accès sandbox ;
15. tests ;
16. validation technique ;
17. validation sécurité ;
18. approbation production.

---

# 9. Statuts partenaire

- DRAFT ;
- ONBOARDING ;
- KYB_PENDING ;
- COMPLIANCE_REVIEW ;
- TECHNICAL_REVIEW ;
- SANDBOX_ACTIVE ;
- PRODUCTION_REQUESTED ;
- PRODUCTION_APPROVED ;
- ACTIVE ;
- LIMITED ;
- SUSPENDED ;
- TERMINATED ;
- ARCHIVED.

---

# 10. Dossier partenaire

Il doit contenir :

- raison sociale ;
- nom commercial ;
- pays ;
- secteur ;
- contacts ;
- représentant ;
- documents ;
- bénéficiaires effectifs ;
- compte bancaire ;
- contrat ;
- produits ;
- environnements ;
- applications ;
- clés ;
- certificats ;
- permissions ;
- plafonds ;
- incidents ;
- audits ;
- statut.

---

# 11. Équipe partenaire

Une organisation peut inviter plusieurs utilisateurs.

Rôles possibles :

- OWNER ;
- ADMIN ;
- DEVELOPER ;
- SECURITY_MANAGER ;
- FINANCE_MANAGER ;
- COMPLIANCE_MANAGER ;
- SUPPORT_USER ;
- AUDITOR ;
- VIEWER.

---

# 12. Permissions d’équipe

Exemples :

```text
partner.organization.read
partner.organization.manage
partner.member.read
partner.member.manage
partner.application.read
partner.application.manage
partner.api_key.create
partner.api_key.revoke
partner.webhook.manage
partner.log.read
partner.report.read
partner.settlement.read
partner.production.request
partner.security.manage
partner.support.create
```

---

# 13. MFA obligatoire

Le MFA doit être obligatoire pour :

- propriétaires ;
- administrateurs ;
- responsables sécurité ;
- accès production ;
- rotation de clé ;
- modification de webhook ;
- export de données ;
- changement bancaire ;
- demande de mise en production.

---

# 14. Applications partenaires

Un partenaire peut créer plusieurs applications.

Exemples :

- application mobile ;
- site web ;
- backend ;
- ERP ;
- logiciel de caisse ;
- application publique ;
- portail institutionnel ;
- service de réconciliation ;
- outil de reporting.

---

# 15. Dossier d’application

Chaque application doit avoir :

- nom ;
- description ;
- organisation ;
- pays ;
- environnement ;
- produits activés ;
- redirect URIs ;
- webhooks ;
- clés ;
- certificats ;
- permissions ;
- quotas ;
- version ;
- statut ;
- contact technique.

---

# 16. Statuts d’une application

- DRAFT ;
- TESTING ;
- REVIEW_REQUIRED ;
- SANDBOX_ACTIVE ;
- PRODUCTION_PENDING ;
- ACTIVE ;
- LIMITED ;
- SUSPENDED ;
- REVOKED ;
- ARCHIVED.

---

# 17. Environnements

Les environnements peuvent être :

```text
SANDBOX
DEMO
CERTIFICATION
PREPRODUCTION
PRODUCTION
```

Chaque environnement doit avoir :

- URL distincte ;
- clés distinctes ;
- données distinctes ;
- limites distinctes ;
- journaux distincts ;
- configuration distincte.

---

# 18. Sandbox

La sandbox doit permettre :

- comptes simulés ;
- soldes fictifs ;
- cartes de test ;
- transactions simulées ;
- erreurs simulées ;
- webhooks simulés ;
- remboursements simulés ;
- litiges simulés ;
- règlements simulés ;
- scénarios de fraude ;
- scénarios réseau.

---

# 19. Données de test

Le portail peut générer :

- client fictif ;
- commerçant fictif ;
- agent fictif ;
- wallet fictif ;
- carte fictive ;
- paiement fictif ;
- transfert fictif ;
- facture fictive ;
- service public fictif ;
- webhook fictif.

---

# 20. Scénarios de test

Exemples :

- paiement réussi ;
- paiement refusé ;
- solde insuffisant ;
- OTP requis ;
- KYC incomplet ;
- transaction expirée ;
- doublon ;
- timeout ;
- remboursement ;
- annulation ;
- webhook échoué ;
- règlement bloqué ;
- fraude suspectée.

---

# 21. Passage en production

Le passage en production peut exiger :

- KYB validé ;
- contrat signé ;
- tests réussis ;
- revue de sécurité ;
- revue technique ;
- conformité ;
- webhooks validés ;
- mécanismes d’idempotence ;
- procédures d’incident ;
- contact d’urgence ;
- approbation Mansa.

---

# 22. Checklist de production

Elle doit vérifier :

- stockage des secrets ;
- chiffrement ;
- TLS ;
- mTLS si requis ;
- IP autorisées ;
- redirect URIs ;
- signature webhook ;
- idempotence ;
- timeouts ;
- reprise ;
- journalisation ;
- protection des données ;
- tests de charge ;
- gestion des erreurs ;
- support.

---

# 23. Clés API

Types possibles :

- clé publique ;
- clé secrète ;
- clé sandbox ;
- clé production ;
- clé limitée ;
- clé temporaire ;
- clé de serveur ;
- clé de test.

---

# 24. Propriétés d’une clé

Une clé doit contenir :

- identifiant ;
- application ;
- environnement ;
- date de création ;
- date d’expiration ;
- permissions ;
- IP autorisées ;
- dernière utilisation ;
- statut ;
- auteur ;
- date de révocation.

---

# 25. Rotation de clé

Le partenaire doit pouvoir :

- créer une nouvelle clé ;
- conserver temporairement l’ancienne ;
- définir une période de transition ;
- tester ;
- révoquer ;
- consulter l’usage ;
- recevoir une alerte.

---

# 26. Révocation de clé

Une clé doit pouvoir être révoquée :

- manuellement ;
- automatiquement à expiration ;
- après suspicion ;
- après inactivité ;
- après fin de contrat ;
- après incident ;
- après dépassement de politique.

---

# 27. OAuth 2.0 et OIDC

Le portail peut prendre en charge :

- Authorization Code ;
- PKCE ;
- Client Credentials ;
- Device Authorization lorsque pertinent ;
- refresh tokens ;
- scopes ;
- consentement ;
- révocation ;
- rotation de tokens.

---

# 28. Scopes OAuth

Exemples :

```text
payments.read
payments.create
payments.refund
transfers.read
transfers.create
accounts.read
customers.read
customers.verify
webhooks.manage
settlements.read
reports.read
public_services.read
public_services.pay
```

---

# 29. Redirect URIs

Les redirect URIs doivent être :

- déclarées ;
- validées ;
- exactes ;
- liées à un environnement ;
- protégées contre les jokers non contrôlés ;
- historisées.

---

# 30. Certificats

Le portail peut gérer :

- mTLS ;
- certificats clients ;
- certificats serveurs ;
- certificats de signature ;
- expiration ;
- rotation ;
- révocation ;
- chaîne de confiance.

---

# 31. Catalogue API

Le catalogue doit présenter :

- nom de l’API ;
- description ;
- version ;
- statut ;
- pays ;
- permissions ;
- limites ;
- documentation ;
- exemples ;
- erreurs ;
- changelog ;
- disponibilité.

---

# 32. Familles d’API

Exemples :

- Identity API ;
- Customer API ;
- Wallet API ;
- Payment API ;
- Transfer API ;
- Card API ;
- Cash Network API ;
- Merchant API ;
- Settlement API ;
- Public Services API ;
- Notification API ;
- Webhook API ;
- Reporting API ;
- Directory API.

---

# 33. Documentation

La documentation doit inclure :

- introduction ;
- authentification ;
- environnements ;
- headers ;
- idempotence ;
- pagination ;
- erreurs ;
- webhooks ;
- sécurité ;
- exemples ;
- SDK ;
- limites ;
- changelog ;
- migration.

---

# 34. Documentation interactive

Le partenaire peut :

- sélectionner un environnement ;
- saisir une clé de test ;
- exécuter une requête sandbox ;
- voir la réponse ;
- copier le code ;
- changer de langage ;
- tester un webhook ;
- consulter les erreurs.

Aucun secret ne doit être enregistré dans le navigateur au-delà de la session nécessaire.

---

# 35. Exemples de code

Langages possibles :

- JavaScript ;
- TypeScript ;
- Python ;
- Java ;
- Kotlin ;
- Swift ;
- PHP ;
- C# ;
- Go ;
- cURL.

---

# 36. SDK officiels

Mansa peut fournir :

- SDK JavaScript ;
- SDK TypeScript ;
- SDK Python ;
- SDK Java ;
- SDK Kotlin ;
- SDK Swift ;
- SDK PHP ;
- SDK .NET.

Chaque SDK doit être :

- versionné ;
- signé ;
- documenté ;
- testé ;
- publié officiellement ;
- maintenu selon une politique définie.

---

# 37. Versionnement API

Format recommandé :

```text
/v1/
/v2/
```

Les changements non compatibles doivent créer une nouvelle version majeure.

---

# 38. Changelog

Chaque changement doit préciser :

- date ;
- version ;
- API ;
- type ;
- impact ;
- migration ;
- date d’effet ;
- date de fin de support ;
- contact.

---

# 39. Dépréciation

Une API dépréciée doit afficher :

- statut ;
- raison ;
- version de remplacement ;
- guide de migration ;
- date limite ;
- alertes ;
- partenaires concernés.

---

# 40. Compatibilité

Les modifications compatibles peuvent inclure :

- nouveau champ optionnel ;
- nouvel endpoint ;
- nouveau statut documenté ;
- nouveau filtre optionnel.

Les partenaires ne doivent pas dépendre de l’ordre des champs JSON.

---

# 41. Idempotence

Les opérations sensibles doivent accepter :

```http
Idempotency-Key
```

Le système doit empêcher :

- double paiement ;
- double transfert ;
- double remboursement ;
- double dépôt ;
- double création de facture.

---

# 42. Identifiants de corrélation

Chaque requête doit pouvoir contenir ou recevoir :

```http
X-Correlation-Id
X-Request-Id
```

Ils doivent être utilisables dans :

- les journaux ;
- le support ;
- les incidents ;
- les audits ;
- les recherches.

---

# 43. Pagination

Les listes doivent utiliser une pagination documentée.

Méthodes possibles :

- curseur ;
- token ;
- pagination par page pour certains rapports.

---

# 44. Filtrage

Les endpoints peuvent supporter :

- date ;
- statut ;
- type ;
- pays ;
- devise ;
- référence ;
- client ;
- établissement ;
- partenaire ;
- montant.

---

# 45. Erreurs API

Format recommandé :

```json
{
  "code": "PAYMENT_INSUFFICIENT_FUNDS",
  "message": "Le solde disponible est insuffisant.",
  "requestId": "req_123",
  "details": {}
}
```

Les erreurs doivent être :

- stables ;
- documentées ;
- traduisibles ;
- sans secret ;
- actionnables.

---

# 46. Catégories d’erreurs

- authentification ;
- autorisation ;
- validation ;
- ressource absente ;
- conflit ;
- limite ;
- risque ;
- partenaire ;
- indisponibilité ;
- erreur interne ;
- maintenance.

---

# 47. Webhooks

Le partenaire doit pouvoir créer plusieurs endpoints de webhook.

Chaque endpoint doit contenir :

- URL ;
- événements ;
- environnement ;
- secret ;
- statut ;
- version ;
- tentatives ;
- dernière réponse ;
- taux de réussite.

---

# 48. Événements webhook

Exemples :

```text
payment.created
payment.authorized
payment.completed
payment.failed
payment.refunded
transfer.created
transfer.completed
transfer.failed
customer.kyc.updated
merchant.updated
cash_deposit.completed
cash_withdrawal.completed
settlement.created
settlement.paid
dispute.opened
dispute.closed
```

---

# 49. Signature webhook

Chaque webhook doit être signé.

Headers possibles :

```http
Mansa-Signature
Mansa-Event-Id
Mansa-Timestamp
```

Le partenaire doit vérifier :

- signature ;
- horodatage ;
- identifiant ;
- tolérance temporelle ;
- absence de rejeu.

---

# 50. Tentatives webhook

Exemple de stratégie :

```text
immédiate
1 minute
5 minutes
30 minutes
2 heures
12 heures
24 heures
```

La stratégie doit être configurable.

---

# 51. Rejeu de webhook

Le portail peut permettre de rejouer un événement :

- individuellement ;
- sur une période limitée ;
- après correction ;
- avec permission ;
- avec audit.

Le rejeu ne doit pas créer une nouvelle transaction financière.

---

# 52. Échec prolongé des webhooks

Après plusieurs échecs :

- alerte partenaire ;
- alerte Mansa ;
- réduction de fréquence ;
- désactivation temporaire ;
- ticket automatique ;
- procédure de réactivation.

---

# 53. Journaux API

Le partenaire doit pouvoir consulter :

- date ;
- endpoint ;
- méthode ;
- statut HTTP ;
- durée ;
- environnement ;
- application ;
- request ID ;
- réponse masquée ;
- erreur ;
- quota.

---

# 54. Données masquées dans les journaux

Ne jamais afficher en clair :

- secret API ;
- token ;
- PIN ;
- OTP ;
- CVV ;
- numéro complet de carte ;
- document ;
- mot de passe ;
- donnée biométrique ;
- clé privée.

---

# 55. Recherche dans les journaux

Filtres :

- période ;
- application ;
- endpoint ;
- statut ;
- request ID ;
- correlation ID ;
- code d’erreur ;
- environnement ;
- durée ;
- IP.

---

# 56. Durée de conservation

La durée des journaux doit dépendre :

- du pays ;
- du contrat ;
- du type de donnée ;
- de la conformité ;
- de la sécurité ;
- de la politique de rétention.

---

# 57. Quotas

Le système doit gérer :

- requêtes par seconde ;
- requêtes par minute ;
- requêtes par jour ;
- volume financier ;
- nombre d’opérations ;
- volume de webhooks ;
- nombre d’applications ;
- nombre de clés.

---

# 58. Rate limiting

En cas de dépassement, l’API doit retourner une réponse documentée.

Headers possibles :

```http
RateLimit-Limit
RateLimit-Remaining
RateLimit-Reset
Retry-After
```

---

# 59. Quotas personnalisés

Les quotas peuvent varier selon :

- partenaire ;
- contrat ;
- produit ;
- environnement ;
- pays ;
- risque ;
- volume ;
- niveau de service ;
- période.

---

# 60. Tableau de bord d’usage

Afficher :

- appels API ;
- taux de réussite ;
- erreurs ;
- latence ;
- webhooks ;
- volume ;
- quotas ;
- applications ;
- incidents ;
- disponibilité ;
- évolution.

---

# 61. Analytics partenaire

Indicateurs possibles :

- paiements créés ;
- paiements réussis ;
- transferts ;
- remboursements ;
- taux d’échec ;
- volume financier ;
- délais ;
- webhooks reçus ;
- règlements ;
- réconciliation.

---

# 62. Règlements partenaires

Le portail peut afficher :

- période ;
- volume brut ;
- frais ;
- commissions ;
- taxes ;
- remboursements ;
- réserves ;
- ajustements ;
- net ;
- date prévue ;
- statut ;
- référence bancaire.

---

# 63. Réconciliation

Le partenaire doit pouvoir :

- télécharger un rapport ;
- comparer les transactions ;
- identifier les écarts ;
- soumettre un écart ;
- suivre une résolution ;
- consulter les écritures liées ;
- voir le statut.

---

# 64. Fichiers de réconciliation

Formats possibles :

- CSV ;
- XLSX ;
- JSON ;
- API ;
- SFTP lorsque nécessaire.

---

# 65. Rapports

Rapports possibles :

- paiements ;
- transferts ;
- remboursements ;
- règlements ;
- commissions ;
- erreurs ;
- disponibilité ;
- webhooks ;
- quotas ;
- incidents ;
- réconciliation.

---

# 66. Exports

Les exports doivent être :

- autorisés ;
- chiffrés ;
- limités ;
- temporaires ;
- protégés par expiration ;
- auditables ;
- adaptés au pays.

---

# 67. Notifications

Le partenaire peut recevoir :

- clé bientôt expirée ;
- certificat bientôt expiré ;
- quota proche ;
- webhook en échec ;
- nouvelle version ;
- dépréciation ;
- incident ;
- maintenance ;
- règlement ;
- document requis ;
- accès production validé.

---

# 68. Centre d’incidents

Le portail doit présenter :

- service ;
- environnement ;
- statut ;
- impact ;
- début ;
- progression ;
- résolution ;
- historique ;
- recommandations.

---

# 69. Maintenance

Une maintenance doit préciser :

- API concernée ;
- environnement ;
- pays ;
- date ;
- durée ;
- impact ;
- alternative ;
- action partenaire ;
- statut.

---

# 70. Support développeur

Le partenaire doit pouvoir :

- consulter la documentation ;
- rechercher une erreur ;
- créer un ticket ;
- joindre un request ID ;
- joindre des journaux masqués ;
- suivre le ticket ;
- demander une revue technique ;
- signaler un incident critique.

---

# 71. Catégories de support

- authentification ;
- clé API ;
- OAuth ;
- webhook ;
- paiement ;
- transfert ;
- règlement ;
- réconciliation ;
- erreur technique ;
- sandbox ;
- production ;
- conformité ;
- sécurité.

---

# 72. SLA

Le niveau de service peut dépendre :

- du contrat ;
- de la criticité ;
- du produit ;
- de l’environnement ;
- du pays ;
- du plan partenaire.

---

# 73. Sécurité

Mesures principales :

- MFA ;
- RBAC ;
- ABAC ;
- OAuth ;
- mTLS ;
- chiffrement ;
- rotation de clé ;
- IP allowlist ;
- rate limiting ;
- détection d’anomalie ;
- audit ;
- gestion des secrets ;
- WAF ;
- protection DDoS.

---

# 74. IP allowlist

Le partenaire peut déclarer des IP autorisées pour :

- API production ;
- portail ;
- SFTP ;
- webhooks sortants ;
- accès administrateur.

Les changements doivent être audités.

---

# 75. Restrictions géographiques

Un accès peut être limité selon :

- pays ;
- région ;
- adresse IP ;
- environnement ;
- utilisateur ;
- produit ;
- horaire.

---

# 76. Alertes de sécurité

Exemples :

- clé utilisée depuis une IP inconnue ;
- hausse soudaine des appels ;
- erreurs d’authentification ;
- webhook modifié ;
- certificat expiré ;
- tentative de dépassement ;
- comportement automatisé inhabituel ;
- accès hors périmètre ;
- fuite suspectée.

---

# 77. Incident de clé compromise

Le workflow doit permettre :

1. signalement ;
2. révocation immédiate ;
3. création d’une nouvelle clé ;
4. analyse des appels ;
5. limitation temporaire ;
6. notification ;
7. rapport ;
8. clôture ;
9. rotation complète si nécessaire.

---

# 78. Conformité

Selon le produit, le partenaire doit respecter :

- KYC ;
- KYB ;
- AML ;
- sanctions ;
- PEP ;
- protection des données ;
- conservation ;
- consentement ;
- sécurité ;
- obligations contractuelles ;
- restrictions pays.

---

# 79. Accès aux données personnelles

L’accès doit être limité :

- aux données nécessaires ;
- aux finalités autorisées ;
- à une durée définie ;
- aux utilisateurs autorisés ;
- aux pays autorisés ;
- aux produits autorisés.

---

# 80. Consentement utilisateur

Lorsqu’un partenaire agit pour un utilisateur, le système peut exiger :

- consentement explicite ;
- scopes ;
- durée ;
- révocation ;
- preuve ;
- écran d’autorisation ;
- journal.

---

# 81. Révocation du consentement

L’utilisateur doit pouvoir révoquer un accès lorsque le modèle le prévoit.

La révocation doit entraîner :

- invalidation du token ;
- arrêt des appels ;
- notification du partenaire ;
- journalisation ;
- conservation limitée des preuves nécessaires.

---

# 82. Administration Mansa

Le portail Admin Web doit pouvoir gérer :

- partenaires ;
- organisations ;
- applications ;
- utilisateurs ;
- environnements ;
- produits ;
- clés ;
- certificats ;
- OAuth ;
- permissions ;
- quotas ;
- webhooks ;
- incidents ;
- règlements ;
- conformité ;
- rapports ;
- versions ;
- documentation ;
- mises en production.

---

# 83. Approbations

Peuvent nécessiter une approbation :

- création d’accès production ;
- augmentation de quota ;
- ajout d’un produit ;
- ajout d’un pays ;
- modification de permission ;
- export massif ;
- changement bancaire ;
- activation mTLS ;
- accès à une donnée sensible ;
- réactivation après incident.

---

# 84. Double validation

Peut être exigée pour :

- accès production critique ;
- accès aux paiements ;
- accès aux données personnelles ;
- augmentation majeure de plafond ;
- réactivation après compromission ;
- modification globale d’une API ;
- fin de support accélérée ;
- rotation d’un certificat racine.

---

# 85. Permissions Admin

Exemples :

```text
partner.read
partner.manage
partner.approve
partner.application.read
partner.application.manage
partner.production.approve
partner.key.read
partner.key.revoke
partner.certificate.manage
partner.permission.manage
partner.quota.manage
partner.webhook.read
partner.log.read
partner.settlement.read
partner.incident.manage
partner.audit.read
```

---

# 86. Actions critiques

Doivent être protégées :

- activation production ;
- révocation globale ;
- modification de scope ;
- création d’une clé privilégiée ;
- modification d’un certificat ;
- augmentation importante de quota ;
- accès à de nouvelles données ;
- modification d’un webhook sensible ;
- changement de compte de règlement ;
- réactivation après fraude.

---

# 87. API du portail

Exemples :

```http
POST   /partner/applications
GET    /partner/applications
GET    /partner/applications/{id}
PATCH  /partner/applications/{id}

POST   /partner/api-keys
GET    /partner/api-keys
POST   /partner/api-keys/{id}/rotate
POST   /partner/api-keys/{id}/revoke

POST   /partner/webhooks
GET    /partner/webhooks
PATCH  /partner/webhooks/{id}
POST   /partner/webhooks/{id}/test

GET    /partner/logs
GET    /partner/usage
GET    /partner/quotas
GET    /partner/reports
GET    /partner/settlements

POST   /partner/production-requests
POST   /partner/support/tickets
```

---

# 88. Modèles

- PartnerOrganization
- PartnerUser
- PartnerRole
- PartnerPermission
- PartnerApplication
- PartnerEnvironment
- PartnerProductAccess
- PartnerApiKey
- PartnerOAuthClient
- PartnerCertificate
- PartnerScope
- PartnerWebhookEndpoint
- PartnerWebhookSubscription
- PartnerWebhookDelivery
- PartnerApiRequestLog
- PartnerQuota
- PartnerUsageMetric
- PartnerSettlement
- PartnerReconciliation
- PartnerReport
- PartnerProductionRequest
- PartnerIncident
- PartnerSupportTicket
- PartnerSecurityEvent
- PartnerAudit

---

# 89. Analytics

Événements possibles :

```text
partner_onboarding_started
partner_sandbox_activated
partner_application_created
partner_api_key_created
partner_api_key_rotated
partner_api_key_revoked
partner_webhook_created
partner_webhook_tested
partner_api_request_completed
partner_quota_warning_created
partner_production_requested
partner_production_approved
partner_reconciliation_downloaded
partner_support_ticket_created
partner_security_alert_created
```

---

# 90. Données analytics interdites

Ne pas transmettre :

- secret API ;
- token ;
- clé privée ;
- mot de passe ;
- OTP ;
- PIN ;
- CVV ;
- document complet ;
- numéro complet de carte ;
- données biométriques ;
- contenu confidentiel ;
- payload sensible complet.

---

# 91. Tests

- tests d’onboarding ;
- tests KYB ;
- tests d’équipe ;
- tests de rôles ;
- tests de permissions ;
- tests de sandbox ;
- tests d’isolation des environnements ;
- tests de clés ;
- tests de rotation ;
- tests OAuth ;
- tests OIDC ;
- tests mTLS ;
- tests de certificats ;
- tests d’API ;
- tests d’idempotence ;
- tests de pagination ;
- tests d’erreurs ;
- tests de webhooks ;
- tests de signature ;
- tests de rejeu ;
- tests de quotas ;
- tests de rate limiting ;
- tests de journaux ;
- tests de masquage ;
- tests de production ;
- tests de règlements ;
- tests de réconciliation ;
- tests de sécurité ;
- tests multi-pays ;
- tests d’audit ;
- tests d’accessibilité ;
- tests de performance.

---

# 92. Règles métier

1. Chaque partenaire appartient à une organisation identifiée.
2. Chaque application possède son propre périmètre.
3. La sandbox est séparée de la production.
4. Les données sandbox sont fictives.
5. Les clés sont propres à un environnement.
6. Les secrets ne sont affichés qu’une fois.
7. Les clés peuvent être révoquées immédiatement.
8. Les permissions sont vérifiées côté backend.
9. Les scopes suivent le principe du moindre privilège.
10. Les webhooks sont signés.
11. Les webhooks possèdent un identifiant unique.
12. Les événements peuvent être rejoués sans recréer l’opération.
13. Les opérations sensibles utilisent l’idempotence.
14. Les erreurs sont documentées et stables.
15. Les journaux masquent les secrets.
16. Les quotas sont administrables.
17. Les API sont versionnées.
18. Les dépréciations sont annoncées.
19. Le passage en production exige une validation.
20. Les accès aux données personnelles sont limités.
21. Les consentements peuvent être révoqués.
22. Les changements critiques sont audités.
23. Les règlements sont calculés par le backend.
24. Les exports sensibles sont protégés.
25. Les actions critiques peuvent exiger une double validation.

---

# 93. Critères d’acceptation

Le Portail Partenaires et Développeurs est validé lorsque :

- les partenaires peuvent être onboardés ;
- les organisations peuvent gérer leurs équipes ;
- les applications peuvent être créées ;
- la sandbox est disponible ;
- les données de test sont générées ;
- les clés API sont sécurisées ;
- la rotation de clé fonctionne ;
- OAuth est pris en charge ;
- les certificats sont gérés ;
- le catalogue API est disponible ;
- la documentation est interactive ;
- les SDK peuvent être publiés ;
- les API sont versionnées ;
- l’idempotence est appliquée ;
- les erreurs sont documentées ;
- les webhooks sont signés ;
- les tentatives de webhook sont suivies ;
- le rejeu est contrôlé ;
- les journaux sont consultables ;
- les données sensibles sont masquées ;
- les quotas sont visibles ;
- le rate limiting fonctionne ;
- les rapports sont disponibles ;
- les règlements sont consultables ;
- la réconciliation est intégrée ;
- le support développeur est disponible ;
- le passage en production utilise un workflow ;
- les accès sensibles sont limités ;
- les actions critiques sont auditées ;
- les tests couvrent les parcours essentiels.
