# 105 — Fidélité, cashback et récompenses Mansa

## 1. Objet du document

Ce document définit le cahier des charges du module **Fidélité, cashback et récompenses Mansa**.

Le module permet aux commerçants, entreprises et partenaires Mansa de créer des programmes de fidélité configurables, tout en donnant aux utilisateurs un espace unique pour cumuler, consulter et utiliser des avantages liés à leurs paiements et interactions autorisées.

Le module ne doit jamais masquer la nature financière réelle d’une récompense. Toute valeur monétaire, remise, cashback, point convertible ou avantage financé par un partenaire doit être comptabilisé, tracé et présenté de manière explicite.

---

## 2. Objectifs

- augmenter la rétention des utilisateurs ;
- augmenter la fréquence d’achat ;
- permettre aux commerçants de lancer des programmes simples sans développement spécifique ;
- proposer du cashback, des points, des coupons, des statuts et des avantages ;
- gérer des campagnes ciblées par segment ;
- mesurer précisément le coût et la performance des campagnes ;
- empêcher la fraude, le double usage et l’auto-récompense abusive ;
- rendre les récompenses compatibles avec paiements carte, wallet, QR, TPE et Mobile Money lorsque le flux le permet ;
- permettre des règles différentes selon pays, devise, marchand, produit et canal ;
- fournir une piste d’audit complète.

---

## 3. Positionnement dans l’écosystème Mansa

Le module s’intègre avec :

- Identity et comptes utilisateurs ;
- KYC/KYB ;
- Wallet et Ledger ;
- paiements ;
- cartes ;
- QR ;
- TPE ;
- commerçants ;
- Mobile Money ;
- abonnements ;
- notifications ;
- moteur de risque ;
- analytics ;
- administration ;
- support ;
- partenaires externes.

---

## 4. Principes non négociables

1. Une récompense monétaire ne doit jamais être créée sans source de financement identifiée.
2. Les règles actives sont versionnées.
3. Toute attribution et toute utilisation sont idempotentes.
4. Aucun client ne peut modifier lui-même son solde de points ou de cashback.
5. Les montants financiers utilisent des unités monétaires entières ou des types décimaux sûrs, jamais des flottants binaires.
6. Les expirations sont calculées de manière déterministe et auditable.
7. Toute correction manuelle exige une permission adaptée et un audit.
8. Les campagnes doivent pouvoir être suspendues immédiatement.
9. Les règles anti-abus s’appliquent avant attribution définitive lorsque requis.
10. Les conditions visibles par l’utilisateur doivent correspondre aux règles réellement exécutées.

---

## 5. Concepts principaux

Le module manipule au minimum :

- `LoyaltyProgram` ;
- `LoyaltyMembership` ;
- `RewardRule` ;
- `RewardRuleVersion` ;
- `RewardEvent` ;
- `RewardGrant` ;
- `RewardBalance` ;
- `RewardLedgerEntry` ;
- `CashbackGrant` ;
- `PointsGrant` ;
- `Coupon` ;
- `CouponRedemption` ;
- `RewardTier` ;
- `TierProgress` ;
- `Campaign` ;
- `CampaignBudget` ;
- `RewardFundingSource` ;
- `RewardReversal` ;
- `RewardExpiration` ;
- `RewardAdjustment`.

---

## 6. Types de programmes

Le système doit supporter au minimum :

```text
POINTS
CASHBACK
COUPONS
DISCOUNTS
TIERED_STATUS
PARTNER_REWARDS
MISSIONS
HYBRID
```

Un programme hybride peut combiner plusieurs mécanismes.

---

## 7. Portée d’un programme

Un programme peut être limité à :

- un commerçant ;
- un groupe de commerçants ;
- une marque ;
- une catégorie ;
- un pays ;
- une ville ;
- un canal ;
- un moyen de paiement ;
- une application Mansa ;
- un segment utilisateur ;
- une période ;
- un produit donné.

---

## 8. Cycle de vie d’un programme

```text
DRAFT
REVIEW
SCHEDULED
ACTIVE
PAUSED
ENDED
ARCHIVED
CANCELLED
```

Les transitions sensibles sont auditables.

---

## 9. Adhésion

Selon le programme, l’adhésion peut être :

- automatique ;
- volontaire avec consentement ;
- conditionnée à un achat ;
- limitée à un segment ;
- réservée aux utilisateurs vérifiés ;
- réservée aux clients d’un partenaire.

Le système conserve la date d’adhésion, la source et le statut.

---

## 10. Règles d’éligibilité

Une règle peut inclure :

- montant minimum ;
- montant maximum ;
- commerçant ;
- catégorie commerçant ;
- canal ;
- type de paiement ;
- devise ;
- période horaire ;
- jour de semaine ;
- pays ;
- segment utilisateur ;
- statut KYC ;
- nouveau client ;
- première transaction ;
- nombre d’achats ;
- panier moyen ;
- produit ;
- campagne ;
- présence d’un coupon ;
- exclusion de transactions remboursées ou annulées.

---

## 11. Moteur de règles

Le moteur doit supporter :

- conditions AND/OR ;
- seuils ;
- multiplicateurs ;
- plafonds ;
- fenêtres temporelles ;
- exclusions ;
- priorités ;
- règles cumulables ou exclusives ;
- activation différée ;
- expiration ;
- simulation avant publication.

---

## 12. Versionnement

Toute règle publiée conserve :

- identifiant stable ;
- version ;
- auteur ;
- date de création ;
- date d’effet ;
- justification ;
- statut ;
- conditions ;
- formule ;
- plafonds ;
- budget ;
- historique des modifications.

Une récompense attribuée référence la version exacte utilisée.

---

## 13. Points

Les points doivent pouvoir être attribués selon :

- montant dépensé ;
- achat qualifiant ;
- fréquence ;
- mission ;
- parrainage autorisé ;
- campagne ;
- événement promotionnel.

Exemple :

```text
1 point par tranche de 1 000 FCFA éligibles
```

La formule doit être configurable et sans ambiguïté d’arrondi.

---

## 14. Solde de points

Le solde est dérivé d’un journal immuable de mouvements.

Types de mouvements :

```text
EARN
REDEEM
EXPIRE
REVERSE
ADJUST
TRANSFER_IN
TRANSFER_OUT
LOCK
UNLOCK
```

Le transfert de points entre utilisateurs est désactivé par défaut et ne peut être activé que si une politique métier l’autorise.

---

## 15. Cashback

Le cashback peut être :

- fixe ;
- proportionnel ;
- progressif ;
- plafonné ;
- réservé à une période ;
- réservé à un commerçant ;
- financé par Mansa ;
- financé par un marchand ;
- cofinancé.

Exemple :

```text
5 % de cashback
plafond = 5 000 FCFA / utilisateur / mois
```

---

## 16. États du cashback

```text
PENDING
CONFIRMED
AVAILABLE
REDEEMED
REVERSED
EXPIRED
BLOCKED
```

Un cashback peut rester en attente jusqu’à expiration de la fenêtre de remboursement ou jusqu’à confirmation définitive du paiement.

---

## 17. Financement

Chaque avantage monétaire doit référencer une `RewardFundingSource`.

Sources possibles :

```text
MANSA_MARKETING
MERCHANT
PARTNER
CO_FUNDED
PROMOTIONAL_BUDGET
OTHER_APPROVED_SOURCE
```

Aucune campagne ne peut dépasser son budget autorisé sauf configuration explicitement approuvée.

---

## 18. Budget de campagne

Le système suit :

- budget total ;
- budget consommé ;
- budget réservé ;
- budget disponible ;
- coût estimé des récompenses en attente ;
- plafond quotidien ;
- plafond par utilisateur ;
- seuil d’alerte ;
- date d’épuisement estimée.

---

## 19. Réservation de budget

Pour certaines campagnes, le budget est réservé lors du paiement puis confirmé après finalisation.

Le moteur doit éviter qu’une concurrence de transactions dépasse le budget disponible.

---

## 20. Coupons

Un coupon possède au minimum :

- code ou identifiant ;
- campagne ;
- titulaire éventuel ;
- valeur ;
- type d’avantage ;
- date de début ;
- date d’expiration ;
- nombre maximal d’utilisations ;
- restrictions ;
- statut.

---

## 21. Types de coupons

```text
FIXED_DISCOUNT
PERCENTAGE_DISCOUNT
FREE_ITEM
FREE_SERVICE
BONUS_POINTS
BONUS_CASHBACK
PARTNER_BENEFIT
```

---

## 22. Utilisation d’un coupon

L’utilisation doit être atomique : validation, réservation, consommation et référence à la transaction.

Le système protège contre :

- double usage ;
- réutilisation concurrente ;
- coupon expiré ;
- coupon d’un autre utilisateur ;
- coupon hors marchand éligible ;
- coupon copié lorsqu’il est nominatif.

---

## 23. Statuts et niveaux

Le système peut gérer des niveaux comme :

```text
STANDARD
SILVER
GOLD
PLATINUM
```

Les noms sont configurables par programme.

---

## 24. Progression de niveau

Critères possibles :

- dépenses cumulées ;
- nombre d’achats ;
- points gagnés ;
- ancienneté ;
- engagement ;
- combinaison pondérée.

La période de calcul peut être glissante, annuelle ou fixe.

---

## 25. Avantages de niveau

Exemples :

- multiplicateur de points ;
- cashback supérieur ;
- coupons exclusifs ;
- support prioritaire ;
- frais réduits si la politique produit l’autorise ;
- offres partenaires.

Toute réduction de frais financiers doit rester compatible avec la tarification et les obligations réglementaires.

---

## 26. Missions

Une mission peut récompenser un comportement autorisé :

- effectuer plusieurs achats chez des commerçants distincts ;
- découvrir un nouveau service ;
- compléter un profil ;
- effectuer un premier paiement QR ;
- utiliser une fonctionnalité spécifique.

Les missions ne doivent pas encourager des comportements financiers risqués ou artificiels.

---

## 27. Parrainage

Si activé, le parrainage doit inclure :

- lien ou code unique ;
- critères d’éligibilité du parrain ;
- critères d’éligibilité du filleul ;
- événement déclencheur ;
- période de validation ;
- limites ;
- règles anti-auto-parrainage ;
- détection multi-comptes.

---

## 28. Récompense différée

Une récompense peut être différée pour :

- délai de remboursement ;
- règlement marchand ;
- validation KYC ;
- analyse de risque ;
- confirmation partenaire.

Le motif de l’attente est enregistré.

---

## 29. Annulation et remboursement

Lorsqu’une transaction est annulée ou remboursée :

- les récompenses non disponibles sont annulées ;
- les récompenses disponibles peuvent être reprises selon la politique ;
- si le solde est insuffisant, un solde de récupération ou une dette de récompense contrôlée peut être créée ;
- aucune modification n’efface l’historique.

---

## 30. Expiration

Les points ou coupons peuvent expirer selon :

- date fixe ;
- durée après attribution ;
- durée après dernière activité ;
- règles du partenaire.

Le système doit notifier l’utilisateur avant expiration lorsque cette notification est activée.

---

## 31. Calcul FIFO d’expiration

Lorsque des points ont plusieurs dates d’expiration, le moteur consomme par défaut les unités expirant le plus tôt, sauf politique différente explicitement définie.

---

## 32. Anti-fraude et anti-abus

Le module doit détecter :

- auto-paiement marchand ;
- transactions artificielles ;
- achats suivis de remboursements répétés ;
- multi-comptes ;
- abus de parrainage ;
- exploitation de coupons ;
- création massive de comptes ;
- vélocité anormale ;
- réutilisation de terminal ;
- collusion agent-commerçant-client.

---

## 33. Intégration avec le moteur de risque

Avant attribution ou utilisation, le module peut demander une décision au moteur de risque.

Décisions possibles :

```text
ALLOW
DELAY
REVIEW
BLOCK_REWARD
BLOCK_CAMPAIGN_PARTICIPATION
```

Le risque ne doit pas modifier silencieusement les règles commerciales : toute dérogation est tracée.

---

## 34. Segmentation

Les campagnes peuvent cibler des segments calculés par le module analytics, à condition que l’utilisation des données soit autorisée.

Exemples :

- nouveaux utilisateurs ;
- utilisateurs inactifs ;
- clients fréquents ;
- forte valeur ;
- catégorie d’achat ;
- zone géographique ;
- type de compte.

Les segments sensibles interdits par politique ne doivent pas être utilisés.

---

## 35. Personnalisation

La personnalisation peut sélectionner l’offre la plus pertinente parmi un ensemble autorisé, mais ne doit pas créer automatiquement des conditions financières non approuvées.

---

## 36. Catalogue de récompenses

Le catalogue peut contenir :

- cashback ;
- coupon ;
- bon marchand ;
- service ;
- avantage partenaire ;
- réduction ;
- produit promotionnel.

Chaque entrée possède disponibilité, coût en points, période et restrictions.

---

## 37. Conversion points → récompense

La conversion doit utiliser un taux explicite et versionné.

Exemple :

```text
1 000 points = coupon de 2 000 FCFA
```

Un changement de taux n’affecte pas rétroactivement une conversion déjà confirmée.

---

## 38. Valeur financière

Si des points ont une valeur financière comptable, cette valeur est suivie séparément du nombre de points afin de permettre rapprochement, provision et reporting.

---

## 39. Comptabilité et Ledger

Les mouvements monétaires de cashback doivent s’intégrer au Ledger Mansa.

Le journal de fidélité ne remplace pas le grand livre financier.

Toute opération monétaire possède une référence croisée vers l’écriture financière correspondante.

---

## 40. Réconciliation

Le système doit pouvoir rapprocher :

- récompenses attribuées ;
- paiements éligibles ;
- budgets consommés ;
- écritures Ledger ;
- factures partenaires ;
- remboursements ;
- expirations.

---

## 41. Facturation commerçant

Lorsqu’un marchand finance la campagne, le système peut produire :

- relevé des récompenses ;
- coût brut ;
- taxes applicables ;
- frais de service ;
- période ;
- détail transactionnel autorisé ;
- montant à régler.

---

## 42. Multi-devise

Un programme doit préciser sa devise de financement et les règles applicables aux transactions dans d’autres devises.

Toute conversion utilise une source de taux identifiable et une politique d’arrondi documentée.

---

## 43. Multi-pays

Les programmes sont isolés par pays lorsque les règles fiscales, réglementaires, commerciales ou monétaires diffèrent.

Une campagne globale peut générer des déclinaisons locales.

---

## 44. Expérience Client

L’application Client doit afficher :

- solde de points ;
- cashback disponible ;
- cashback en attente ;
- coupons ;
- niveau ;
- progression ;
- historique ;
- récompenses disponibles ;
- expirations prochaines ;
- conditions principales.

---

## 45. Expérience Commerçant

L’application Commerçant ou le portail professionnel doit permettre selon permissions :

- consulter les campagnes ;
- voir les coûts ;
- voir les résultats ;
- créer un brouillon de campagne ;
- choisir des règles autorisées ;
- suivre le budget ;
- exporter les données ;
- suspendre une campagne si autorisé.

---

## 46. TPE

Le TPE peut afficher :

- points gagnés ;
- coupon appliqué ;
- avantage utilisé ;
- confirmation de récompense.

Le TPE ne doit jamais être la source de vérité du solde.

---

## 47. Mode hors ligne

En mode hors ligne, aucune récompense à forte valeur ne doit être attribuée définitivement sans validation serveur.

Le terminal peut afficher une estimation ou une récompense `PENDING` selon la politique.

---

## 48. Notifications

Événements notifiables :

- récompense gagnée ;
- cashback disponible ;
- coupon reçu ;
- coupon bientôt expiré ;
- points bientôt expirés ;
- changement de niveau ;
- campagne personnalisée autorisée ;
- récompense annulée avec motif adapté.

---

## 49. Préférences utilisateur

L’utilisateur peut gérer les communications promotionnelles selon les règles applicables.

Le refus de marketing ne doit pas empêcher l’affichage d’informations transactionnelles nécessaires sur une récompense déjà acquise.

---

## 50. Administration

L’Admin doit permettre :

- créer programmes et campagnes ;
- gérer règles ;
- gérer budgets ;
- gérer catalogue ;
- gérer niveaux ;
- gérer partenaires ;
- suspendre ;
- simuler ;
- consulter audits ;
- effectuer des corrections contrôlées ;
- exporter les rapports.

---

## 51. RBAC

Rôles indicatifs :

```text
LOYALTY_VIEWER
LOYALTY_OPERATOR
LOYALTY_CAMPAIGN_MANAGER
LOYALTY_FINANCE
LOYALTY_RISK
LOYALTY_ADMIN
LOYALTY_AUDITOR
```

Les permissions critiques sont séparées.

---

## 52. Double validation

Une double validation peut être requise pour :

- campagne dépassant un budget ;
- modification d’un taux de cashback ;
- correction massive ;
- crédit manuel important ;
- changement de financement ;
- suppression logique d’une campagne active.

---

## 53. Ajustement manuel

Tout ajustement manuel requiert :

- utilisateur ou compte concerné ;
- type ;
- valeur ;
- motif ;
- auteur ;
- approbateur si requis ;
- référence support ou incident ;
- date ;
- trace d’audit.

---

## 54. API principales

Exemples d’API :

```text
GET /loyalty/me
GET /loyalty/me/balance
GET /loyalty/me/history
GET /loyalty/me/coupons
GET /loyalty/me/rewards
POST /loyalty/rewards/:id/redeem
POST /loyalty/coupons/:code/validate
POST /loyalty/coupons/:code/redeem
GET /admin/loyalty/programs
POST /admin/loyalty/programs
POST /admin/loyalty/campaigns
POST /admin/loyalty/campaigns/:id/publish
POST /admin/loyalty/campaigns/:id/pause
POST /internal/loyalty/evaluate
POST /internal/loyalty/reverse
```

Toutes les API sensibles exigent authentification, autorisation, idempotence et corrélation.

---

## 55. Événements internes

Exemples :

```text
payment.completed
payment.refunded
payment.reversed
loyalty.reward.granted
loyalty.reward.available
loyalty.reward.redeemed
loyalty.reward.reversed
loyalty.reward.expired
loyalty.tier.changed
loyalty.campaign.budget.low
loyalty.campaign.budget.exhausted
```

---

## 56. Idempotence

La clé d’attribution doit empêcher qu’un même événement financier produise plusieurs fois la même récompense.

Exemple :

```text
rewardKey = programId + ruleVersionId + sourceTransactionId + beneficiaryId
```

La structure exacte peut différer, mais l’unicité fonctionnelle doit être garantie.

---

## 57. Concurrence

Les opérations de budget, coupon et solde doivent être protégées contre les accès concurrents.

Le système doit gérer les doubles clics, retries réseau, webhooks dupliqués et traitements parallèles.

---

## 58. Performance

Objectifs indicatifs :

- évaluation d’éligibilité synchrone rapide ;
- lecture du solde à faible latence ;
- attribution asynchrone possible lorsque l’expérience paiement ne dépend pas du résultat immédiat ;
- batch d’expiration scalable ;
- campagnes supportant des volumes élevés.

Les SLO précis sont définis dans le volume plateforme.

---

## 59. Cache

Le cache peut accélérer règles et catalogues, mais ne doit pas devenir la source de vérité pour :

- budget ;
- coupon consommable ;
- solde définitif ;
- écritures financières.

---

## 60. Stockage

Les données minimales doivent permettre :

- reconstitution du solde ;
- preuve d’attribution ;
- preuve d’utilisation ;
- rapprochement ;
- audit ;
- analyse de campagne.

---

## 61. Rétention

Les durées de conservation sont définies par catégorie de donnée, pays et obligation légale.

Les données marketing non nécessaires doivent pouvoir être supprimées ou anonymisées selon les politiques applicables sans détruire les preuves financières obligatoires.

---

## 62. Analytics

Indicateurs :

- membres actifs ;
- taux d’adhésion ;
- points émis ;
- points utilisés ;
- taux d’expiration ;
- cashback attribué ;
- coût par campagne ;
- taux de conversion ;
- panier moyen ;
- fréquence d’achat ;
- rétention ;
- revenu incrémental estimé ;
- abus détectés.

---

## 63. Mesure incrémentale

Le module doit distinguer corrélation et causalité.

Lorsque possible, les campagnes peuvent utiliser groupes de contrôle ou tests A/B conformes aux règles de données afin d’estimer l’impact réel.

---

## 64. Exports

Formats possibles :

- CSV ;
- XLSX si supporté par le portail ;
- API ;
- rapports PDF générés côté reporting.

Les exports respectent permissions, filtrage et masquage.

---

## 65. Audit

Doivent être audités :

- création de programme ;
- publication de règle ;
- modification de budget ;
- suspension ;
- ajustement manuel ;
- changement de taux ;
- changement de financement ;
- export sensible ;
- action administrative de support.

---

## 66. Observabilité

Métriques :

- temps d’évaluation ;
- erreurs ;
- récompenses/minute ;
- montant cashback ;
- budget restant ;
- échecs de réconciliation ;
- doublons bloqués ;
- coupons refusés ;
- files en attente ;
- expirations traitées.

---

## 67. Alertes

Alertes possibles :

- budget presque épuisé ;
- budget dépassé ;
- taux d’attribution anormal ;
- hausse de fraude ;
- erreur de Ledger ;
- taux d’échec élevé ;
- file bloquée ;
- divergence de réconciliation.

---

## 68. Sécurité

Le module applique :

- authentification ;
- RBAC/ABAC ;
- chiffrement ;
- secrets hors dépôt ;
- journalisation ;
- validation stricte ;
- limitation de débit ;
- protection contre rejeu ;
- séparation des environnements.

---

## 69. Confidentialité

La segmentation et la personnalisation utilisent uniquement les données autorisées.

Les données sensibles non nécessaires ne doivent pas être copiées dans le domaine fidélité.

---

## 70. Tests unitaires

Couvrir au minimum :

- calcul points ;
- arrondis ;
- cashback ;
- plafonds ;
- expiration ;
- priorité de règles ;
- coupon ;
- niveau ;
- réversion ;
- budget.

---

## 71. Tests d’intégration

Scénarios :

- paiement → récompense ;
- remboursement → réversion ;
- campagne → budget ;
- coupon → paiement ;
- cashback → Ledger ;
- risque → blocage ;
- notification ;
- expiration.

---

## 72. Tests de concurrence

Tester :

- double utilisation de coupon ;
- double attribution ;
- épuisement simultané d’un budget ;
- deux rédemptions simultanées ;
- webhooks dupliqués.

---

## 73. Tests de sécurité

Inclure :

- élévation de privilège ;
- IDOR ;
- modification de solde ;
- injection ;
- replay ;
- brute force de coupons ;
- exposition de données ;
- abus de rôle marchand.

---

## 74. Tests de résilience

Simuler :

- Ledger indisponible ;
- moteur de risque indisponible ;
- notifications indisponibles ;
- timeout partenaire ;
- worker d’expiration interrompu ;
- retry après panne.

---

## 75. Données de test

Les environnements non production utilisent des données synthétiques ou anonymisées.

Aucun secret ou identifiant réel de partenaire ne doit être ajouté au dépôt.

---

## 76. Migration

Toute migration d’un programme existant doit préserver :

- soldes ;
- historique ;
- dates d’expiration ;
- coupons ;
- niveaux ;
- références financières ;
- consentements requis.

---

## 77. Déploiement progressif

Le module doit supporter :

- feature flags ;
- activation par pays ;
- activation par marchand ;
- activation par segment ;
- mode shadow ;
- campagne pilote ;
- rollback contrôlé.

---

## 78. Mode shadow

Une nouvelle règle peut calculer une récompense théorique sans attribution réelle afin de mesurer son coût et son impact avant activation.

---

## 79. Gouvernance

Chaque programme important possède :

- propriétaire métier ;
- responsable finance ;
- responsable risque ;
- périmètre ;
- budget ;
- date de revue ;
- règles ;
- mécanisme de suspension.

---

## 80. Critères d’acceptation

Le module est considéré prêt lorsque :

- les programmes peuvent être créés, versionnés, activés et suspendus ;
- points, cashback, coupons et niveaux sont supportés ;
- les attributions sont idempotentes ;
- les remboursements produisent les réversions attendues ;
- les budgets ne peuvent pas être dépassés par concurrence non contrôlée ;
- les écritures monétaires sont rapprochées avec le Ledger ;
- les règles anti-abus sont actives ;
- l’Admin dispose des permissions et audits requis ;
- les applications affichent des soldes et conditions cohérents ;
- les tests unitaires, intégration, concurrence, sécurité et résilience passent ;
- aucun secret n’est présent dans le dépôt.
