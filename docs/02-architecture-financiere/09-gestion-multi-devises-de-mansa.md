# 09 — Gestion multi-devises de Mansa

## 1. Objet du document

Ce document définit la gestion officielle des devises dans Mansa.

Il couvre :

- les devises disponibles ;
- les comptes multi-devises ;
- les conversions ;
- les taux de change ;
- les frais ;
- les arrondis ;
- les soldes ;
- les cartes ;
- les paiements ;
- les transferts ;
- les remboursements ;
- les écritures comptables ;
- les partenaires ;
- les rapports ;
- les règles par pays.

L’objectif est de permettre à Mansa de gérer plusieurs devises de manière fiable, compréhensible et auditable.

---

# 2. Principes fondamentaux

## 2.1 Une devise doit toujours être explicite

Chaque montant doit être associé à :

- un code de devise ;
- une précision ;
- un format ;
- une valeur entière minimale ;
- un contexte ;
- une date de valorisation si conversion.

Aucun montant financier ne doit être stocké ou transmis sans devise.

## 2.2 Pas de calcul financier en nombres flottants

Les montants doivent être traités avec :

- unités mineures ;
- entiers ;
- décimaux précis ;
- bibliothèques adaptées.

Exemples :

- `125000 XOF`
- `125050 EUR cents`
- `100000 USD cents`

Les calculs avec `float` ou `double` sont interdits pour les opérations financières critiques.

## 2.3 Devise du compte

Chaque compte possède une devise principale.

Un compte en XOF ne doit pas être confondu avec un compte en EUR.

## 2.4 Taux officiel et taux appliqué

Le système doit distinguer :

- taux de marché ;
- taux partenaire ;
- marge Mansa ;
- frais fixes ;
- frais variables ;
- taux final appliqué ;
- date et heure du taux.

## 2.5 Confirmation avant conversion

Avant toute conversion, l’utilisateur doit voir :

- montant débité ;
- devise débitée ;
- taux ;
- frais ;
- montant reçu ;
- devise reçue ;
- durée de validité du taux ;
- délai ;
- statut estimatif ou garanti.

---

# 3. Entité devise

Chaque devise doit contenir :

```text
code ISO 4217
nom
symbole
nombre de décimales
position du symbole
séparateur décimal
séparateur de milliers
statut
pays associés
précision
montant minimum
montant maximum
méthode d’arrondi
```

Exemples :

```text
XOF
EUR
USD
GBP
MAD
GHS
NGN
```

Une devise ne doit pas être activée uniquement parce qu’elle existe dans la norme ISO.

---

# 4. Statuts d’une devise

Une devise peut être :

- brouillon ;
- configurée ;
- en test ;
- active ;
- limitée ;
- suspendue ;
- retirée.

Une devise retirée doit rester identifiable dans les historiques.

---

# 5. Comptes multi-devises

Un utilisateur peut posséder :

- un compte principal ;
- plusieurs sous-comptes ;
- un wallet par devise ;
- des comptes professionnels par devise ;
- des comptes de règlement ;
- des comptes d’investissement.

Chaque compte doit afficher :

- devise ;
- solde disponible ;
- solde bloqué ;
- solde comptable ;
- valeur estimée dans une devise de référence ;
- dernière mise à jour.

---

# 6. Devise de référence utilisateur

L’utilisateur peut choisir une devise d’affichage principale.

Cette devise sert uniquement à :

- afficher une estimation globale ;
- convertir les graphiques ;
- comparer les soldes ;
- calculer une valeur approximative.

Elle ne modifie pas la devise réelle des comptes.

---

# 7. Conversion de devises

## 7.1 Parcours

1. Sélection du compte source.
2. Sélection du compte destination.
3. Saisie du montant.
4. Calcul du taux.
5. Affichage des frais.
6. Affichage du montant reçu.
7. Confirmation.
8. Authentification.
9. Création des écritures.
10. Mise à jour des soldes.
11. Génération du reçu.

## 7.2 Conversion interne

Lorsque les deux devises sont gérées directement par Mansa, la conversion peut être exécutée dans le ledger interne selon les règles autorisées.

## 7.3 Conversion partenaire

Lorsque la conversion dépend d’une banque ou d’un prestataire, Mansa doit gérer :

- devis ;
- délai ;
- expiration ;
- confirmation ;
- webhook ;
- échec ;
- retry ;
- rapprochement.

---

# 8. Devis de change

Chaque devis doit contenir :

- identifiant ;
- devise source ;
- devise destination ;
- montant source ;
- montant destination ;
- taux brut ;
- marge ;
- frais ;
- taux final ;
- date de création ;
- date d’expiration ;
- partenaire ;
- statut.

Statuts :

- créé ;
- valide ;
- accepté ;
- expiré ;
- annulé ;
- exécuté ;
- échoué.

---

# 9. Taux de change

Sources possibles :

- banque partenaire ;
- prestataire de change ;
- taux interne autorisé ;
- source de marché ;
- taux institutionnel ;
- taux réglementaire.

Chaque taux doit indiquer :

- source ;
- date ;
- heure ;
- paire ;
- valeur ;
- sens ;
- durée de validité ;
- environnement ;
- statut.

---

# 10. Paires de devises

Chaque paire doit être configurée.

Exemples :

```text
XOF/EUR
EUR/XOF
XOF/USD
USD/XOF
EUR/USD
```

Une paire peut être :

- directe ;
- indirecte ;
- calculée via une devise intermédiaire ;
- inactive ;
- limitée.

Les conversions triangulaires doivent être tracées.

---

# 11. Frais de change

Les frais peuvent inclure :

- marge sur taux ;
- frais fixes ;
- frais proportionnels ;
- frais partenaire ;
- taxe ;
- frais de canal ;
- frais d’urgence ;
- frais promotionnels.

Le détail doit être visible avant validation.

---

# 12. Arrondis

Chaque devise définit ses règles d’arrondi.

Méthodes possibles :

- arrondi mathématique ;
- arrondi inférieur ;
- arrondi supérieur ;
- arrondi bancaire ;
- règle partenaire.

L’arrondi doit être cohérent dans :

- paiement ;
- transfert ;
- remboursement ;
- frais ;
- taxes ;
- rapports ;
- ledger.

Les différences d’arrondi doivent être comptabilisées.

---

# 13. Paiements multi-devises

Un paiement peut impliquer :

- devise du client ;
- devise de la carte ;
- devise du commerçant ;
- devise de règlement ;
- devise du partenaire.

Le système doit distinguer chaque étape.

Exemple :

```text
Compte client : EUR
Prix commerçant : XOF
Règlement commerçant : XOF
Conversion : EUR → XOF
```

---

# 14. Paiements par carte

Pour un paiement carte, afficher lorsque disponible :

- devise du commerçant ;
- devise de la carte ;
- taux ;
- frais ;
- conversion dynamique éventuelle ;
- montant final.

La conversion dynamique proposée par un commerçant ou un acquéreur doit être clairement distinguée du taux Mansa.

---

# 15. Transferts internationaux

Un transfert international doit gérer :

- pays source ;
- pays destination ;
- devise source ;
- devise destination ;
- taux ;
- frais ;
- partenaires ;
- délai ;
- limites ;
- conformité ;
- bénéficiaire ;
- motif ;
- preuve.

Le montant reçu doit être affiché avant confirmation lorsque possible.

---

# 16. Remboursements

Un remboursement doit préciser :

- devise d’origine ;
- montant d’origine ;
- devise remboursée ;
- taux utilisé ;
- frais non remboursables éventuels ;
- différence de change ;
- date ;
- partenaire.

La politique doit indiquer si le taux utilisé est :

- taux d’origine ;
- taux du jour ;
- taux partenaire ;
- règle contractuelle.

---

# 17. Annulations

Une annulation avant règlement peut utiliser le taux initial.

Une annulation après règlement peut devenir un remboursement et générer une différence de change.

---

# 18. Ledger multi-devises

Chaque écriture doit contenir :

- compte ;
- devise ;
- montant ;
- sens ;
- référence ;
- transaction ;
- date ;
- statut ;
- conversion éventuelle ;
- taux ;
- paire ;
- frais ;
- compte de contrepartie.

Une écriture ne doit pas mélanger plusieurs devises dans une seule ligne.

---

# 19. Comptes techniques

Le système peut utiliser :

- compte de conversion ;
- compte de marge ;
- compte de frais ;
- compte d’arrondi ;
- compte de suspense ;
- compte partenaire ;
- compte de règlement ;
- compte de différence de change.

Chaque compte technique doit être auditable.

---

# 20. Rapprochement

Le rapprochement doit vérifier :

- taux ;
- montants ;
- frais ;
- règlements ;
- écarts ;
- devises ;
- dates ;
- références ;
- statuts.

Les écarts doivent être classés :

- arrondi ;
- taux ;
- frais ;
- doublon ;
- retard ;
- erreur partenaire ;
- erreur interne.

---

# 21. Cartes multi-devises

Une carte peut être associée à :

- une devise unique ;
- plusieurs comptes ;
- un portefeuille multi-devises ;
- une priorité de débit.

Règles possibles :

1. débiter la même devise ;
2. utiliser le compte principal ;
3. convertir automatiquement ;
4. refuser si la devise n’est pas disponible.

L’utilisateur doit connaître la logique appliquée.

---

# 22. Priorité de débit

L’utilisateur peut éventuellement définir :

- compte principal ;
- ordre des devises ;
- conversion automatique ;
- plafond de conversion ;
- blocage d’une devise.

Certaines règles peuvent être imposées par le programme de carte.

---

# 23. Multi-devises pour les commerçants

Un commerçant peut :

- afficher plusieurs devises ;
- accepter plusieurs devises ;
- régler dans une devise unique ;
- recevoir dans la devise du paiement ;
- convertir automatiquement ;
- définir une devise par établissement.

Les prix officiels doivent conserver leur devise d’origine.

---

# 24. Factures et reçus

Une facture multi-devises doit afficher :

- devise de facturation ;
- montant ;
- taux éventuel ;
- devise de paiement ;
- date du taux ;
- frais ;
- taxes ;
- total final.

Le reçu doit conserver la conversion appliquée.

---

# 25. Budgets et analytics

Les budgets sont définis dans une devise.

Pour une vue globale :

- chaque montant est converti ;
- la date du taux est indiquée ;
- la valeur est estimative ;
- les historiques peuvent utiliser le taux du jour ou le taux historique selon le rapport.

La méthode doit être documentée.

---

# 26. Investissements

Les investissements doivent afficher :

- devise du produit ;
- devise du compte ;
- valeur d’achat ;
- valeur actuelle ;
- taux ;
- frais ;
- performance locale ;
- performance convertie.

Les rendements convertis restent estimatifs tant qu’ils ne sont pas réalisés.

---

# 27. Services publics

Un service public peut imposer une devise.

Si l’utilisateur paie depuis une autre devise :

- une conversion est proposée ;
- les frais sont affichés ;
- la preuve indique la devise officielle du service.

---

# 28. Administration

Le portail Admin doit permettre :

- activer une devise ;
- suspendre une devise ;
- définir les pays ;
- configurer les paires ;
- gérer les taux ;
- gérer les sources ;
- définir les marges ;
- définir les frais ;
- définir les arrondis ;
- gérer les limites ;
- consulter les écarts ;
- consulter les conversions ;
- exporter les rapports.

---

# 29. Permissions

Permissions possibles :

```text
currency.read
currency.create
currency.update
currency.activate
currency.suspend
exchange_rate.read
exchange_rate.publish
exchange_margin.update
conversion.read
conversion.create
conversion.override
currency_report.export
```

Les modifications de taux ou de marge peuvent exiger une double validation.

---

# 30. API

Exemples :

```http
GET    /currencies
GET    /currencies/{code}
POST   /currencies
PATCH  /currencies/{code}

GET    /exchange-rates
POST   /exchange-rates
GET    /exchange-rates/quote

POST   /conversions
GET    /conversions/{id}
GET    /conversions

GET    /currency-pairs
POST   /currency-pairs
PATCH  /currency-pairs/{id}
```

---

# 31. Modèles

- Currency
- CurrencyCountry
- CurrencyPair
- ExchangeRate
- ExchangeRateSource
- ExchangeQuote
- Conversion
- ConversionFee
- ConversionMargin
- CurrencyAccount
- CurrencyLimit
- CurrencyRoundingRule
- CurrencySettlement
- CurrencyReconciliation
- CurrencyAudit

---

# 32. Règles métier

1. Tout montant possède une devise.
2. Les calculs financiers n’utilisent pas de flottants.
3. Une devise inactive ne peut pas être utilisée.
4. Une paire inactive ne peut pas être convertie.
5. Un devis expiré ne peut pas être exécuté.
6. Les frais sont affichés avant confirmation.
7. Le taux appliqué est conservé.
8. Les écritures restent séparées par devise.
9. Les différences de change sont comptabilisées.
10. Les remboursements suivent une politique définie.
11. Les arrondis sont cohérents.
12. Les taux sont versionnés.
13. Les modifications critiques sont auditées.
14. Les partenaires doivent être actifs.
15. Une conversion échouée ne doit pas produire de faux solde.
16. Les valeurs globales converties sont identifiées comme estimatives.
17. Le backend reste l’autorité.
18. Les limites sont appliquées par devise.
19. Les taxes respectent leur devise officielle.
20. Les historiques conservent les valeurs d’origine.

---

# 33. Analytics

Événements possibles :

```text
currency_account_created
currency_enabled
currency_disabled
exchange_quote_created
exchange_quote_accepted
exchange_quote_expired
conversion_started
conversion_completed
conversion_failed
exchange_margin_updated
currency_limit_exceeded
currency_reconciliation_difference_detected
```

---

# 34. Tests

- tests de précision ;
- tests d’arrondi ;
- tests de conversion ;
- tests de devis expirés ;
- tests de frais ;
- tests multi-paires ;
- tests de remboursement ;
- tests de cartes multi-devises ;
- tests de rapprochement ;
- tests de taux ;
- tests de limites ;
- tests de permissions ;
- tests d’idempotence ;
- tests de forte charge ;
- tests de cohérence ledger.

---

# 35. Critères d’acceptation

La gestion multi-devises est validée lorsque :

- chaque montant possède une devise ;
- les calculs sont précis ;
- les comptes multi-devises fonctionnent ;
- les devises sont configurables ;
- les paires sont contrôlées ;
- les taux sont historisés ;
- les frais sont transparents ;
- les arrondis sont cohérents ;
- les conversions produisent des écritures équilibrées ;
- les remboursements respectent la politique ;
- les cartes utilisent la bonne priorité de débit ;
- les commerçants peuvent gérer plusieurs devises ;
- les rapprochements détectent les écarts ;
- les permissions sont appliquées ;
- toutes les modifications sont auditées.
