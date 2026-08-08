# Mansa Access & Mobility Engine — accès, mobilité, flotte et usages privés

## 1. Objet

Ce document définit le moteur transversal `Mansa Access & Mobility Engine` destiné aux usages d’accès, mobilité, transport, station-service, parking, flotte, campus, entreprise et sites privés ou publics.

Le moteur ne remplace pas les modules métier existants. Il fournit une couche commune permettant d’identifier une personne, un véhicule ou un support, d’évaluer des règles, d’autoriser ou refuser un service, de déclencher éventuellement un paiement ou un débit, de commander un équipement physique et de conserver une preuve complète et auditable.

Principe général :

`Identifiant → contexte → règles → autorisation/paiement → équipement → preuve d’usage → rapprochement/audit`

Le moteur doit être multi-tenant, multi-pays, multi-fournisseurs, configurable et utilisable aussi bien par l’État que par des entreprises privées.

## 2. Cas d’usage couverts

Le moteur couvre notamment :

- parking d’entreprise ;
- parking public ou privé ;
- contrôle d’accès à un site industriel ;
- accès employé ou visiteur ;
- accès campus, école ou université ;
- transport collectif ;
- abonnement transport ;
- carte ou badge étudiant ;
- carte ou badge salarié ;
- badge flotte ;
- station-service pour flottes ;
- restriction carburant par véhicule ;
- péage privé ou concessionné ;
- accès résidentiel ;
- accès événementiel ;
- restauration d’entreprise ou universitaire ;
- contrôle d’accès à des équipements partagés ;
- services de mobilité liés à un compte Mansa.

## 3. Principe de réutilisation

Le système doit éviter de recréer un moteur différent pour chaque secteur.

Une même brique peut être réutilisée pour :

- un péage de l’État ;
- le parking d’une entreprise ;
- une station-service gérant des véhicules professionnels ;
- une université utilisant des cartes étudiantes ;
- un transporteur exploitant des abonnements ;
- un site industriel contrôlant l’accès des employés et véhicules.

Chaque organisation configure uniquement ses propres règles, supports, tarifs, équipements et politiques.

## 4. Multi-tenant et isolation

Chaque organisation possède son propre espace logique.

Concepts minimaux :

```text
AccessOrganization
AccessSite
AccessZone
AccessPoint
AccessDevice
Credential
CredentialAssignment
AccessPolicy
AccessRule
Entitlement
Subscription
Vehicle
FleetAccount
UsageEvent
AuthorizationDecision
PaymentInstruction
DeviceCommand
AccessAuditEvent
```

Les données, règles, équipements et historiques d’une organisation ne doivent jamais être accessibles à une autre organisation sans autorisation explicite.

## 5. Types d’identifiants

Le moteur doit supporter plusieurs moyens d’identification derrière des adaptateurs :

```text
UHF_RFID_TAG
HF_RFID_CARD
NFC_CARD
NFC_MOBILE
EMV_CARD_REFERENCE
QR_STATIC
QR_DYNAMIC
BARCODE
LICENSE_PLATE
MANSA_ACCOUNT
MANSA_CARD
EMPLOYEE_BADGE
STUDENT_CARD
VISITOR_PASS
DEVICE_TOKEN
OTHER
```

Un support ne doit jamais contenir en clair des secrets financiers ou des données personnelles inutiles.

## 6. Carte et badge multiservice

Mansa doit pouvoir gérer une carte ou un badge multiservice associé à une personne ou une organisation.

Usages possibles :

- identité visuelle ;
- contrôle d’accès ;
- transport ;
- restauration ;
- bibliothèque ;
- parking ;
- paiement ;
- avantages salarié ;
- campus ;
- services internes ;
- programmes publics autorisés.

Le fait qu’un support soit physiquement unique ne signifie pas que tous les services sont automatiquement activés. Chaque droit est indépendant et révocable.

## 7. Cycle de vie d’un support

États minimaux :

```text
PENDING
ACTIVE
SUSPENDED
BLOCKED
LOST
STOLEN
EXPIRED
REVOKED
REPLACED
```

Toute activation, suspension, remplacement ou réaffectation doit être auditée.

Un support remplacé ne doit jamais perdre son historique.

## 8. Association support-personne-véhicule

Un support peut être associé selon le cas à :

- une personne ;
- un employé ;
- un étudiant ;
- un visiteur ;
- un véhicule ;
- une flotte ;
- une organisation ;
- un compte de paiement ;
- un abonnement ;
- un ensemble de droits.

Les associations doivent être versionnées dans le temps.

## 9. Moteur de politiques

Chaque décision doit passer par un moteur de règles configurable.

Exemples :

- accès autorisé uniquement du lundi au vendredi ;
- badge valable uniquement sur un site ;
- véhicule autorisé uniquement sur certains parkings ;
- étudiant autorisé sur une ligne de transport donnée ;
- employé autorisé dans certaines zones ;
- véhicule de flotte limité à 50 000 FCFA de carburant par semaine ;
- véhicule autorisé uniquement pour du diesel ;
- nombre maximum de passages par jour ;
- plafond mensuel ;
- interdiction temporaire ;
- accès gratuit ou payant selon profil ;
- autorisation conditionnée à un abonnement actif.

## 10. Décision d’autorisation

Chaque demande produit une décision explicite :

```text
ALLOW
DENY
REQUIRE_PAYMENT
REQUIRE_SECOND_FACTOR
REQUIRE_OPERATOR
OFFLINE_ALLOW_LIMITED
OFFLINE_DENY
```

La décision doit conserver :

- identifiant de la demande ;
- règle appliquée ;
- version de règle ;
- horodatage ;
- support ;
- personne ou véhicule concerné ;
- équipement ;
- contexte ;
- résultat ;
- motif ;
- éventuelle transaction associée.

## 11. Parking et contrôle de barrière

Pour un parking, la chaîne recommandée est :

`badge/RFID/plaque/QR → lecteur → contrôleur local → Access Engine → autorisation ou paiement → relais OPEN → barrière → capteur de passage → clôture`

Le système doit gérer :

- entrée ;
- sortie ;
- durée ;
- abonnement ;
- tarif horaire ;
- gratuité ;
- validation commerçant ;
- flotte ;
- visiteurs ;
- ouverture manuelle auditée ;
- anti-passback lorsque requis.

## 12. Station-service et gestion de flotte

Le moteur peut être utilisé dans une station-service pour servir des entreprises disposant d’une flotte.

Exemple :

1. identification du véhicule par badge, RFID, QR ou plaque ;
2. identification du compte flotte ;
3. vérification des règles ;
4. sélection ou validation du carburant ;
5. contrôle du plafond ;
6. autorisation ;
7. délivrance du carburant par système compatible ou validation opérateur ;
8. enregistrement du volume, prix et montant ;
9. débit immédiat ou facturation selon contrat ;
10. rapprochement et reçu.

## 13. Règles carburant

Une entreprise doit pouvoir configurer :

- type de carburant autorisé ;
- montant maximum par opération ;
- litres maximum ;
- plafond journalier ;
- plafond hebdomadaire ;
- plafond mensuel ;
- stations autorisées ;
- jours et heures autorisés ;
- véhicule autorisé ;
- conducteur autorisé si nécessaire ;
- kilométrage ou compteur optionnel ;
- besoin d’une approbation ;
- mode de paiement ou de facturation.

## 14. Compte flotte

Un `FleetAccount` peut regrouper plusieurs véhicules et plusieurs supports.

Il doit permettre :

- budget global ;
- budget par véhicule ;
- budget par conducteur ;
- catégories de dépenses ;
- plafonds ;
- alertes ;
- suspension immédiate ;
- exports ;
- facturation centralisée ;
- rapprochement ;
- analytique par véhicule, site et période.

## 15. Transport public et privé

Le moteur doit pouvoir supporter un système de validation transport.

Supports possibles :

- carte transport ;
- carte étudiante ;
- carte employé ;
- NFC mobile ;
- QR ;
- compte Mansa ;
- carte bancaire sans contact lorsque l’architecture d’acceptation le permet.

Le moteur doit permettre :

- ticket unitaire ;
- carnet ;
- abonnement journalier ;
- hebdomadaire ;
- mensuel ;
- annuel ;
- tarif étudiant ;
- tarif salarié ;
- tarif social ;
- gratuité ;
- correspondances ;
- zones ;
- plafonnement tarifaire si activé.

## 16. Validation transport hors ligne

Les valideurs doivent pouvoir fonctionner temporairement sans Internet.

Le mode offline doit reposer sur :

- listes locales signées ;
- droits à durée limitée ;
- compteurs anti-rejeu ;
- horodatage ;
- limites configurables ;
- journal local append-only ;
- synchronisation ultérieure ;
- idempotence ;
- détection de doublons.

Aucun système offline ne doit permettre un débit financier multiple pour le même événement.

## 17. Entreprises et employés

Une entreprise doit pouvoir administrer :

- employés ;
- badges ;
- véhicules ;
- visiteurs ;
- sites ;
- zones ;
- horaires ;
- abonnements ;
- budgets ;
- dépenses autorisées ;
- révocations ;
- exports ;
- historique d’accès.

Les rôles RH, sécurité, finance et exploitation doivent pouvoir être séparés.

## 18. Universités et écoles

Le moteur doit compléter le portail Écoles et Universités existant.

Une carte étudiante peut être utilisée pour :

- identifier l’étudiant ;
- entrer sur le campus ;
- transport ;
- bibliothèque ;
- restauration ;
- logement ;
- examens lorsque autorisé ;
- services universitaires ;
- paiements ou avantages liés à l’établissement.

Chaque établissement choisit les fonctions activées.

## 19. Paiement et facturation

Une autorisation peut être :

```text
FREE
PREPAID
PAY_PER_USE
POSTPAID
SUBSCRIPTION
CORPORATE_BILLED
GOVERNMENT_FUNDED
SPONSORED
MIXED
```

Les paiements doivent passer par les modules financiers Mansa existants, sans recréer un ledger parallèle.

## 20. Moyens de paiement

Selon le contexte et les canaux activés :

- wallet Mansa ;
- carte Mansa ;
- carte bancaire via acquéreur ;
- Mobile Money ;
- compte bancaire ;
- abonnement prépayé ;
- compte entreprise ;
- facturation différée ;
- QR ;
- espèces uniquement dans les parcours explicitement prévus et contrôlés.

## 21. Équipements physiques

Le moteur doit rester multi-fournisseurs.

Exemples :

- lecteurs UHF RFID ;
- lecteurs NFC ;
- lecteurs QR ;
- caméras ANPR ;
- barrières ;
- portiques ;
- tourniquets ;
- serrures électroniques ;
- valideurs transport ;
- contrôleurs industriels ;
- automates ;
- terminaux Android ;
- TPE ;
- distributeurs ou contrôleurs de pompe lorsque le fournisseur expose une interface compatible.

Aucun fabricant ne doit être codé en dur dans la logique métier.

## 22. Couche adaptateurs matériels

Interface logique recommandée :

```text
AccessDeviceAdapter
CredentialReaderAdapter
BarrierAdapter
TurnstileAdapter
FuelControllerAdapter
PlateRecognitionAdapter
PaymentTerminalAdapter
SensorAdapter
```

Chaque adaptateur doit documenter :

- protocole ;
- authentification ;
- commandes ;
- événements ;
- erreurs ;
- retries ;
- timeout ;
- état de santé ;
- capacités offline.

## 23. Relais et interfaces industrielles

Pour les équipements simples, le moteur peut piloter un contrôleur local capable de fournir :

- contact sec ;
- relais OPEN/CLOSE ;
- GPIO industriel ;
- RS-485 ;
- Ethernet ;
- API locale ;
- Modbus ou protocole documenté ;
- autre interface standardisée.

La commande physique ne doit pas être envoyée directement par une application mobile non sécurisée.

## 24. Fonctionnement local

Un `Local Access Controller` peut conserver temporairement :

- configuration de voie ou point d’accès ;
- règles essentielles ;
- clés ou certificats nécessaires ;
- listes autorisées et bloquées ;
- plafonds offline ;
- état des équipements ;
- journal d’événements.

La durée et les capacités offline sont configurables par organisation et par risque.

## 25. Synchronisation

Lors du retour réseau :

- les événements sont envoyés dans l’ordre logique ;
- chaque événement possède une clé d’idempotence ;
- les doublons sont ignorés sans perdre la preuve ;
- les conflits sont signalés ;
- les débits ne sont jamais rejoués aveuglément ;
- les journaux locaux sont conservés jusqu’à accusé de réception durable.

## 26. Anti-fraude

Le moteur doit permettre de détecter :

- support cloné ou utilisé simultanément ;
- usage impossible géographiquement ;
- badge bloqué ;
- véhicule différent du véhicule associé ;
- passages excessifs ;
- ouverture sans décision valide ;
- contournement d’une barrière ;
- consommation carburant anormale ;
- dépassement de plafond ;
- modification anormale de règles ;
- activité opérateur inhabituelle.

## 27. Ouvertures et actions manuelles

Toute action manuelle sensible doit être auditée.

Exemples :

- ouverture de barrière ;
- validation exceptionnelle ;
- déblocage ;
- dépassement de plafond ;
- modification temporaire de droit ;
- autorisation opérateur.

Le journal doit contenir l’opérateur, le motif, l’heure, l’équipement et l’objet concerné.

## 28. Rapprochement physique-numérique

Lorsque des capteurs sont disponibles, Mansa doit rapprocher :

- identifiant détecté ;
- personne ou véhicule attendu ;
- décision ;
- paiement ou droit ;
- commande envoyée ;
- réponse équipement ;
- passage physique ;
- sortie éventuelle ;
- clôture de l’événement.

Cette exigence est essentielle pour les péages, parkings, stations-service et sites sensibles.

## 29. Administration et configuration

Chaque organisation doit pouvoir configurer depuis son portail habilité :

- sites ;
- zones ;
- équipements ;
- supports ;
- rôles ;
- tarifs ;
- abonnements ;
- horaires ;
- plafonds ;
- moyens de paiement ;
- règles offline ;
- alertes ;
- branding ;
- intégrations.

Les paramètres métier ne doivent pas nécessiter une modification du code pour les cas standards.

## 30. Marque blanche

Le produit doit être personnalisable pour :

- entreprise ;
- université ;
- transporteur ;
- station-service ;
- concessionnaire ;
- administration ;
- collectivité.

Éléments configurables :

- nom commercial ;
- logo ;
- couleurs ;
- supports physiques ;
- écrans ;
- reçus ;
- signalétique ;
- emails/SMS ;
- mention facultative `Propulsé par Mansa`.

Les identifiants techniques internes peuvent rester stables même lorsque le nom commercial change.

## 31. API et événements

API minimales :

```text
POST /access/authorize
POST /access/events
POST /access/device-commands
POST /credentials/activate
POST /credentials/suspend
POST /credentials/replace
POST /entitlements
POST /subscriptions
GET  /access/sites
GET  /access/events
GET  /fleet/accounts
GET  /fleet/vehicles
```

Webhooks possibles :

```text
access.allowed
access.denied
access.completed
credential.blocked
credential.replaced
subscription.expiring
fleet.limit_reached
device.offline
device.tamper_detected
manual_override.created
```

## 32. Audit

Doivent être auditables :

- création et modification des règles ;
- activation des supports ;
- révocations ;
- décisions ;
- paiements ;
- commandes matériels ;
- ouvertures manuelles ;
- changements de plafonds ;
- changements de branding ;
- imports ;
- exports ;
- opérations administrateur.

## 33. Sécurité

Exigences minimales :

- authentification forte pour les administrateurs ;
- RBAC/ABAC selon besoin ;
- chiffrement en transit ;
- secrets hors dépôt ;
- rotation de clés ;
- signatures des configurations offline ;
- protection anti-rejeu ;
- rate limiting ;
- journalisation ;
- révocation immédiate ;
- isolation stricte multi-tenant ;
- minimisation des données.

## 34. Données personnelles

Le moteur doit stocker uniquement les données nécessaires au service.

Une organisation peut définir des durées de conservation selon sa base légale et ses obligations.

Les données de déplacement ou d’accès ne doivent pas devenir un profilage général sans finalité légitime, information et contrôles appropriés.

## 35. Observabilité

Métriques recommandées :

- taux d’autorisation ;
- taux de refus ;
- latence de décision ;
- taux de fonctionnement offline ;
- équipements hors ligne ;
- erreurs de lecture ;
- commandes non confirmées ;
- événements non synchronisés ;
- transactions en échec ;
- anomalies fraude ;
- ouvertures manuelles.

## 36. Niveaux de déploiement

Le produit doit supporter plusieurs niveaux d’équipement :

### Niveau 1 — léger

- smartphone ou terminal Android ;
- QR/NFC ;
- validation opérateur ;
- faible coût.

### Niveau 2 — semi-automatisé

- lecteur dédié ;
- contrôleur local ;
- barrière ou tourniquet ;
- opérateur disponible pour exceptions.

### Niveau 3 — automatisé

- identification automatique ;
- contrôle local ;
- capteurs ;
- commande équipement ;
- supervision distante ;
- fonctionnement offline sécurisé.

Le client ne doit pas être obligé d’acheter immédiatement le niveau maximal.

## 37. Modèles commerciaux

Deux modèles minimum doivent être possibles :

- matériel acheté directement par le client auprès des fournisseurs compatibles, Mansa fournissant logiciel/intégration ;
- matériel fourni, intégré ou revendu par Mansa dans une offre clé en main.

La tarification logicielle peut être basée sur :

- abonnement par organisation ;
- site ;
- point d’accès ;
- terminal ;
- véhicule ;
- utilisateur actif ;
- événement ;
- transaction ;
- combinaison contractuelle.

## 38. Relation avec le module péage État

Le module péage État reste une spécialisation du moteur et conserve obligatoirement ses décisions de référence :

- solution A : péage automatique classique avec barrière ;
- solution B : télépéage UHF RFID avec barrière ;
- évolution free-flow optionnelle ultérieure ;
- espèces billets et pièces FCFA selon équipement ;
- EMV multi-réseaux selon acquéreur, notamment Visa et Mastercard lorsque disponibles contractuellement ;
- NFC, carte Mansa, wallet Mansa, QR et Mobile Money selon canaux activés ;
- Mobile Money configurable nationalement, par réseau, poste ou voie, avec date d’effet et audit ;
- fonctionnement local sécurisé sans double débit ;
- matériel multi-fournisseurs derrière adaptateurs ;
- voie automatique complète, voie semi-automatique et poste numérisé faible coût ;
- déploiement progressif ;
- matériel acheté par l’État/concessionnaire ou fourni/intégré/revendu par Mansa ;
- marque blanche État/concessionnaire avec mention facultative `Propulsé par Mansa` ;
- rapprochement véhicule, catégorie, tarif, paiement, ouverture et passage physique ;
- toute ouverture manuelle auditée.

Ces exigences ne doivent pas être affaiblies par la généralisation du moteur.

## 39. Hors périmètre

Ce moteur ne remplace pas :

- un système RH complet ;
- un ERP ;
- un logiciel de transport réglementaire complet ;
- un système universitaire complet ;
- le logiciel embarqué propriétaire d’une pompe à carburant ;
- un système de sûreté physique complet ;
- les règles légales de contrôle d’accès ou de transport.

Il orchestre les identités, droits, paiements, équipements et preuves nécessaires à l’expérience Mansa.

## 40. Critères d’acceptation

Le module est considéré correctement implémenté lorsque :

1. une organisation peut créer plusieurs sites et points d’accès ;
2. plusieurs types de supports peuvent être enregistrés ;
3. un support peut être associé à une personne, un véhicule ou une flotte ;
4. les règles sont configurables et versionnées ;
5. une autorisation produit une décision auditable ;
6. un équipement peut être commandé via un adaptateur ;
7. le système fonctionne temporairement hors ligne selon limites ;
8. la synchronisation ne crée pas de double débit ;
9. les ouvertures manuelles sont tracées ;
10. parking, transport, entreprise et flotte peuvent utiliser le même moteur sans partager leurs données ;
11. le module financier Mansa reste la source de vérité des paiements ;
12. le branding peut être modifié sans changer la logique métier ;
13. aucun fournisseur matériel unique n’est imposé dans le domaine métier ;
14. les exigences du péage État restent intégralement compatibles.
