# 17 — Gestion des versions, compatibilité et mises à jour de Mansa

## 1. Objet du document

Ce document définit la manière dont Mansa doit gérer :

- les versions des applications ;
- les versions du backend ;
- les versions des API ;
- les versions des contrats ;
- les versions des événements ;
- les versions de base de données ;
- les compatibilités entre composants ;
- les mises à jour facultatives ;
- les mises à jour recommandées ;
- les mises à jour obligatoires ;
- les versions bloquées ;
- les déploiements progressifs ;
- les retours arrière ;
- les migrations ;
- les fins de support.

L’objectif est d’éviter qu’une ancienne application, un TPE non mis à jour ou une API incompatible provoque :

- des erreurs ;
- des pertes de fonctionnalités ;
- des incohérences financières ;
- des failles de sécurité ;
- des écrans inutilisables ;
- des opérations impossibles à reprendre.

---

# 2. Principes fondamentaux

## 2.1 Chaque composant possède une version identifiable

Les composants concernés incluent :

- Mansa Client ;
- Mansa Commerce ;
- Mansa TPE ;
- Mansa Admin Lite ;
- Mansa Annuaire ;
- site public ;
- site Professionnels ;
- portail Admin ;
- API Gateway ;
- services backend ;
- packages partagés ;
- contrats API ;
- événements ;
- schéma Prisma ;
- migrations ;
- configurations ;
- modèles de documents ;
- services Jini.

Chaque version doit être identifiable dans :

- les logs ;
- les audits ;
- les requêtes ;
- les rapports ;
- les incidents ;
- les déploiements.

---

## 2.2 Compatibilité avant suppression

Une fonctionnalité ou un contrat ne doit pas être supprimé immédiatement lorsqu’une nouvelle version est publiée.

Une période de compatibilité doit permettre :

- la mise à jour des applications ;
- la migration des TPE ;
- l’adaptation des partenaires ;
- la transition des données ;
- la surveillance ;
- le rollback.

---

## 2.3 Le backend doit connaître la version du client

Chaque requête provenant d’une application doit pouvoir transmettre :

- nom de l’application ;
- version ;
- numéro de build ;
- plateforme ;
- système d’exploitation ;
- modèle d’appareil ;
- environnement ;
- pays ;
- identifiant du terminal si applicable.

Exemple :

```http
X-Mansa-App: client-mobile
X-Mansa-Version: 2.4.1
X-Mansa-Build: 24107
X-Mansa-Platform: ios
```

---

## 2.4 Une version incompatible doit être bloquée proprement

Le système ne doit pas laisser une ancienne version continuer jusqu’à provoquer une erreur incompréhensible.

Il doit afficher :

- la raison ;
- le niveau d’urgence ;
- l’action à effectuer ;
- le lien de mise à jour ;
- les fonctionnalités encore disponibles ;
- l’accès éventuel au support.

---

# 3. Types de versions

## 3.1 Version produit

Exemple :

```text
2.4.1
```

Format recommandé :

```text
MAJOR.MINOR.PATCH
```

- `MAJOR` : changement incompatible important ;
- `MINOR` : nouvelle fonctionnalité compatible ;
- `PATCH` : correction compatible.

## 3.2 Numéro de build

Exemple :

```text
24107
```

Il permet de distinguer plusieurs compilations de la même version publique.

## 3.3 Version API

Exemple :

```text
/api/v1/
```

## 3.4 Version de contrat

Les DTO, événements et webhooks doivent avoir leur propre version.

## 3.5 Version de schéma

Le schéma de base de données doit être relié à :

- migration ;
- commit ;
- déploiement ;
- date ;
- environnement.

## 3.6 Version de configuration

Chaque bundle de configuration doit posséder une version.

---

# 4. Statuts d’une version

Une version peut être :

- en développement ;
- alpha ;
- bêta ;
- interne ;
- pilote ;
- en recette ;
- candidate ;
- publiée ;
- recommandée ;
- obligatoire ;
- limitée ;
- suspendue ;
- bloquée ;
- obsolète ;
- non supportée ;
- retirée.

---

# 5. Canaux de diffusion

Canaux possibles :

- développement interne ;
- test automatisé ;
- équipe Mansa ;
- bêta privée ;
- pilote partenaire ;
- pilote pays ;
- TestFlight ;
- Google Play testing ;
- production progressive ;
- production générale ;
- parc TPE contrôlé.

Chaque canal doit être séparé.

---

# 6. Politique de mise à jour

## 6.1 Mise à jour facultative

Utilisée pour :

- amélioration visuelle ;
- optimisation ;
- nouvelle fonction non critique ;
- correction mineure.

L’utilisateur peut continuer sans mettre à jour.

## 6.2 Mise à jour recommandée

Utilisée lorsque :

- une correction importante est disponible ;
- les performances sont améliorées ;
- une fonctionnalité utile nécessite la nouvelle version ;
- l’ancienne version reste temporairement compatible.

## 6.3 Mise à jour obligatoire

Utilisée lorsque :

- une faille de sécurité existe ;
- une ancienne API est retirée ;
- une règle réglementaire change ;
- un partenaire impose une nouvelle version ;
- une opération financière n’est plus sûre ;
- le schéma de données local devient incompatible.

## 6.4 Version bloquée

Une version peut être bloquée immédiatement si elle :

- produit des doublons ;
- affiche de faux statuts ;
- compromet des données ;
- contourne une permission ;
- contient une faille critique ;
- provoque des erreurs financières ;
- utilise un certificat compromis.

---

# 7. Configuration par version

Chaque application doit disposer d’une configuration indiquant :

- version minimale supportée ;
- version minimale recommandée ;
- dernière version publiée ;
- versions bloquées ;
- plateformes concernées ;
- pays concernés ;
- date d’effet ;
- message ;
- lien de mise à jour ;
- mode de blocage ;
- fonctionnalités désactivées.

Exemple :

```json
{
  "application": "client-mobile",
  "platform": "ios",
  "minimumSupportedVersion": "2.2.0",
  "recommendedVersion": "2.4.0",
  "latestVersion": "2.4.1",
  "blockedVersions": ["2.3.2"]
}
```

---

# 8. Écran de mise à jour

L’écran doit distinguer :

- mise à jour facultative ;
- recommandée ;
- obligatoire ;
- version bloquée ;
- maintenance ;
- incompatibilité pays ;
- incompatibilité appareil.

Il doit afficher :

- titre clair ;
- raison générale ;
- version disponible ;
- bouton de mise à jour ;
- bouton continuer lorsque autorisé ;
- accès au support ;
- informations hors ligne éventuelles.

---

# 9. Mode dégradé

Une ancienne version peut conserver un accès limité.

Exemples :

- consultation du solde ;
- consultation de l’historique ;
- téléchargement de documents ;
- accès au support ;
- blocage d’une carte ;
- déconnexion.

Les opérations risquées peuvent être désactivées :

- transfert ;
- paiement ;
- changement de sécurité ;
- création de carte ;
- remboursement ;
- action administrative.

---

# 10. Compatibilité API

Une API doit définir :

- versions supportées ;
- date de publication ;
- date de dépréciation ;
- date de retrait ;
- applications concernées ;
- partenaires concernés ;
- guide de migration.

Une ancienne version ne doit pas être supprimée sans :

- mesure de son utilisation ;
- notification ;
- période de transition ;
- plan de rollback ;
- validation des consommateurs.

---

# 11. Dépréciation

Lorsqu’un endpoint est déprécié, le système doit pouvoir retourner :

```http
Deprecation: true
Sunset: Wed, 31 Dec 2026 23:59:59 GMT
```

La documentation doit préciser :

- endpoint remplacé ;
- nouvelle version ;
- différences ;
- date limite ;
- exemples ;
- risques.

---

# 12. Contrats partagés

Les contrats doivent être compatibles avec plusieurs versions lorsque nécessaire.

Bonnes pratiques :

- ajouter des champs optionnels ;
- éviter de renommer brutalement ;
- conserver les enums existants ;
- prévoir une valeur `UNKNOWN` ;
- versionner les changements incompatibles ;
- ne pas changer le sens d’un champ existant.

---

# 13. Version des événements

Chaque événement doit contenir :

- type ;
- version ;
- date ;
- producteur ;
- identifiant ;
- schéma ;
- corrélation.

Exemple :

```json
{
  "type": "payment.completed",
  "version": 2,
  "eventId": "evt_123"
}
```

Un consommateur doit pouvoir :

- accepter plusieurs versions ;
- ignorer les champs inconnus ;
- rejeter proprement une version incompatible ;
- utiliser un adaptateur.

---

# 14. Version des webhooks

Les webhooks partenaires doivent être versionnés.

Exemple :

```text
/webhooks/v1/mobile-money
```

Chaque partenaire doit connaître :

- version ;
- schéma ;
- signature ;
- date de retrait ;
- changements ;
- environnement.

---

# 15. Compatibilité mobile

Le backend doit gérer les différences entre versions mobiles.

Exemples :

- champ non supporté ;
- fonctionnalité masquée ;
- navigation ancienne ;
- nouveau statut ;
- nouvelle authentification ;
- nouveau type de carte ;
- nouveau document.

Le backend ne doit pas envoyer un statut que l’ancienne application interprète de manière dangereuse.

---

# 16. Compatibilité TPE

Les TPE nécessitent une politique spécifique.

Chaque terminal doit enregistrer :

- modèle ;
- constructeur ;
- version Android ;
- version Mansa TPE ;
- version SDK paiement ;
- version firmware ;
- version certificat ;
- date de dernière mise à jour ;
- statut de conformité.

---

# 17. Mises à jour TPE

Les mises à jour peuvent être :

- silencieuses ;
- planifiées ;
- obligatoires ;
- progressives ;
- déclenchées par établissement ;
- limitées à un modèle ;
- suspendues en cas d’incident.

Le terminal doit vérifier :

- batterie ;
- connexion ;
- espace disponible ;
- session de caisse ;
- paiement en cours ;
- intégrité du paquet ;
- signature ;
- compatibilité matérielle.

---

# 18. Mise à jour sûre du TPE

Une mise à jour ne doit jamais interrompre :

- un paiement ;
- un remboursement ;
- une impression critique ;
- une clôture ;
- une synchronisation financière.

Le TPE doit attendre une fenêtre sûre.

---

# 19. Rollback TPE

Le système doit prévoir :

- version précédente ;
- paquet signé ;
- conditions de rollback ;
- conservation des données ;
- compatibilité du stockage ;
- audit ;
- remontée d’incident.

---

# 20. Base de données locale

Les applications mobiles et TPE peuvent utiliser une base locale.

Chaque base doit avoir :

- version de schéma ;
- migrations ;
- sauvegarde temporaire ;
- stratégie de rollback ;
- nettoyage ;
- validation d’intégrité.

Une migration locale échouée doit :

- éviter la perte silencieuse ;
- conserver les données critiques ;
- proposer une reprise ;
- remonter un diagnostic.

---

# 21. Migrations backend

Chaque migration doit être :

- versionnée ;
- testée ;
- reproductible ;
- traçable ;
- liée à un commit ;
- compatible avec le déploiement ;
- accompagnée d’un plan de retour.

---

# 22. Déploiement sans interruption

Pour les changements importants, utiliser une stratégie compatible avec l’ancienne et la nouvelle version.

Exemple :

1. ajout d’un nouveau champ ;
2. déploiement backend compatible ;
3. migration des données ;
4. mise à jour des applications ;
5. mesure de l’usage ancien ;
6. retrait de l’ancien champ.

---

# 23. Stratégie Expand and Contract

## 23.1 Expand

Ajouter la nouvelle structure sans supprimer l’ancienne.

## 23.2 Migrate

Migrer les données et consommateurs.

## 23.3 Contract

Supprimer l’ancienne structure une fois qu’elle n’est plus utilisée.

Cette méthode doit être privilégiée pour les changements critiques.

---

# 24. Compatibilité Prisma

Une modification Prisma doit être classée :

- additive ;
- compatible ;
- potentiellement destructive ;
- destructive ;
- nécessitant migration de données ;
- nécessitant arrêt contrôlé.

Les commandes destructives doivent être bloquées en production sans procédure spéciale.

---

# 25. Packages partagés

Chaque package partagé doit suivre une politique de version.

Exemples :

- contracts ;
- SDK ;
- UI ;
- design tokens ;
- auth ;
- permissions ;
- analytics ;
- internationalisation.

Une mise à jour d’un package doit préciser :

- compatibilité ;
- applications concernées ;
- changement cassant ;
- migration ;
- tests ;
- date.

---

# 26. Design System

Les composants du Design System doivent être versionnés.

Un changement visuel cassant doit inclure :

- anciennes propriétés ;
- nouvelles propriétés ;
- guide de migration ;
- période de compatibilité ;
- captures ;
- tests visuels.

---

# 27. Versions de documents

Les documents suivants doivent être versionnés :

- CGU ;
- politique de confidentialité ;
- conditions cartes ;
- conditions commerçants ;
- tarifs ;
- contrats partenaires ;
- reçus ;
- factures ;
- documents institutionnels.

Une ancienne version signée ou acceptée doit rester consultable.

---

# 28. Versions de Jini

Chaque configuration Jini doit identifier :

- modèle ;
- version ;
- prompt système ;
- outils ;
- règles ;
- politiques ;
- date d’effet ;
- pays ;
- langue ;
- environnement.

Une réponse ou une action importante doit pouvoir être reliée à la version utilisée.

---

# 29. Versions de règles métier

Les règles importantes doivent être versionnées.

Exemples :

- frais ;
- plafonds ;
- fraude ;
- KYC ;
- remboursements ;
- commissions ;
- taxes ;
- conversion ;
- éligibilité.

Une transaction doit conserver la version de règle appliquée.

---

# 30. Déploiement progressif

Une version peut être publiée progressivement :

- équipe interne ;
- testeurs ;
- 1 % ;
- 5 % ;
- 20 % ;
- 50 % ;
- 100 %.

Le déploiement doit surveiller :

- crashs ;
- erreurs ;
- latence ;
- paiements échoués ;
- tickets support ;
- désinstallations ;
- blocages ;
- consommation batterie ;
- performance.

---

# 31. Rollback d’application

Un rollback doit être possible lorsque les plateformes le permettent.

Sinon, le backend doit pouvoir :

- désactiver la fonctionnalité ;
- activer un mode compatible ;
- bloquer la version ;
- restaurer une ancienne API ;
- afficher un message ;
- limiter les opérations.

---

# 32. Compatibilité des appareils

Chaque application doit définir :

- version minimale Android ;
- version minimale iOS ;
- architectures supportées ;
- mémoire minimale ;
- stockage minimal ;
- capacités NFC ;
- biométrie ;
- caméra ;
- WebView ;
- services Google ou équivalent.

---

# 33. Appareils non compatibles

L’utilisateur doit recevoir une information claire :

- système trop ancien ;
- appareil non sécurisé ;
- NFC indisponible ;
- biométrie non supportée ;
- mémoire insuffisante ;
- constructeur non certifié ;
- terminal non compatible.

---

# 34. Fin de support d’un système

Une fin de support doit être annoncée progressivement.

Étapes possibles :

1. information ;
2. recommandation ;
3. limitation ;
4. blocage des nouvelles fonctions ;
5. mise à jour obligatoire ;
6. fin de support.

---

# 35. Administration

Le portail Admin doit permettre :

- consulter les versions actives ;
- définir la version minimale ;
- bloquer une version ;
- recommander une version ;
- programmer une obligation ;
- cibler un pays ;
- cibler une plateforme ;
- cibler un modèle de TPE ;
- activer un mode dégradé ;
- consulter l’adoption ;
- lancer un rollback ;
- consulter l’historique.

---

# 36. Tableau de bord des versions

Il doit afficher :

- nombre d’utilisateurs par version ;
- appareils ;
- pays ;
- plateformes ;
- erreurs ;
- crashs ;
- adoption ;
- versions bloquées ;
- versions obsolètes ;
- versions TPE ;
- partenaires encore sur une ancienne API.

---

# 37. Permissions

Exemples :

```text
version.read
version.create
version.publish
version.recommend
version.force_update
version.block
version.rollback
version.deprecate
version.api.sunset
version.tpe.schedule
version.production.manage
```

---

# 38. Actions critiques

Doivent être particulièrement protégées :

- blocage d’une version ;
- mise à jour obligatoire ;
- retrait d’une API ;
- rollback production ;
- migration destructive ;
- mise à jour de firmware TPE ;
- retrait d’un contrat ;
- baisse de version minimale.

---

# 39. Double validation

Une double validation peut être exigée pour :

- blocage global ;
- fin de support ;
- mise à jour obligatoire immédiate ;
- retrait API ;
- migration destructive ;
- firmware TPE ;
- changement réglementaire ;
- faille de sécurité.

---

# 40. Notifications

Les utilisateurs doivent pouvoir être informés par :

- bannière ;
- modal ;
- push ;
- e-mail ;
- SMS si nécessaire ;
- notification TPE ;
- portail Admin ;
- site public.

---

# 41. API

Exemples :

```http
GET    /versions
GET    /versions/applications/{app}
POST   /versions
PATCH  /versions/{id}

POST   /versions/{id}/publish
POST   /versions/{id}/recommend
POST   /versions/{id}/force
POST   /versions/{id}/block
POST   /versions/{id}/rollback

GET    /versions/check
GET    /versions/adoption
GET    /versions/compatibility
```

---

# 42. Vérification de version

Exemple de requête :

```json
{
  "application": "client-mobile",
  "version": "2.3.1",
  "build": 23105,
  "platform": "ios",
  "country": "ML"
}
```

Réponse :

```json
{
  "status": "UPDATE_RECOMMENDED",
  "latestVersion": "2.4.1",
  "minimumVersion": "2.2.0",
  "canContinue": true
}
```

---

# 43. Modèles

- ApplicationVersion
- ApplicationBuild
- VersionStatus
- VersionPolicy
- VersionCompatibilityRule
- MinimumSupportedVersion
- BlockedVersion
- VersionDeployment
- VersionRollout
- VersionRollback
- ApiVersion
- ContractVersion
- EventSchemaVersion
- DatabaseSchemaVersion
- MigrationVersion
- FirmwareVersion
- TpeVersionStatus
- VersionAudit

---

# 44. Audit

Chaque action doit enregistrer :

- version ;
- application ;
- plateforme ;
- ancienne règle ;
- nouvelle règle ;
- auteur ;
- approbateur ;
- pays ;
- environnement ;
- justification ;
- date d’effet ;
- rollback éventuel.

---

# 45. Alertes

Une alerte doit être déclenchée si :

- une ancienne version provoque trop d’erreurs ;
- une version bloquée continue à appeler l’API ;
- une migration échoue ;
- un TPE reste obsolète ;
- une API dépréciée reste très utilisée ;
- une version obligatoire n’est pas adoptée ;
- un paquet n’est pas signé ;
- une incompatibilité est détectée ;
- le rollback échoue.

---

# 46. Analytics

Événements possibles :

```text
version_detected
version_update_available
version_update_recommended
version_update_required
version_blocked
version_adoption_started
version_adoption_completed
version_api_deprecated
version_api_retired
version_tpe_update_started
version_tpe_update_completed
version_tpe_update_failed
version_rollback_started
version_rollback_completed
compatibility_error_detected
```

---

# 47. Tests

- tests de version minimale ;
- tests de version bloquée ;
- tests de mise à jour facultative ;
- tests de mise à jour obligatoire ;
- tests de mode dégradé ;
- tests de compatibilité API ;
- tests de contrats ;
- tests d’événements ;
- tests de migration ;
- tests de rollback ;
- tests TPE ;
- tests de firmware ;
- tests multi-pays ;
- tests multi-plateformes ;
- tests hors ligne ;
- tests de permissions ;
- tests de double validation ;
- tests d’audit.

---

# 48. Règles métier

1. Chaque composant possède une version.
2. Le backend connaît la version du client.
3. Une version incompatible est bloquée proprement.
4. Une version bloquée ne peut pas effectuer d’opération sensible.
5. Les API sont versionnées.
6. Les contrats incompatibles changent de version.
7. Les événements ont une version de schéma.
8. Les migrations sont tracées.
9. Les migrations destructives sont protégées.
10. Les anciennes versions restent compatibles pendant la transition.
11. Les TPE sont mis à jour dans une fenêtre sûre.
12. Les paquets sont signés.
13. Les rollbacks sont préparés.
14. Les versions obligatoires sont justifiées.
15. Les fins de support sont annoncées.
16. Les documents historiques conservent leur version.
17. Les règles métier appliquées sont historisées.
18. Jini conserve la version de configuration utilisée.
19. Les actions critiques sont auditées.
20. Les plateformes et pays sont séparés.
21. Les déploiements progressifs sont surveillés.
22. Les versions obsolètes sont mesurées.
23. Une ancienne application ne doit pas interpréter dangereusement un nouveau statut.
24. Les fonctionnalités peuvent être désactivées sans mise à jour.
25. Les tests couvrent les transitions.

---

# 49. Critères d’acceptation

La gestion des versions est validée lorsque :

- toutes les applications transmettent leur version ;
- le backend vérifie la compatibilité ;
- les mises à jour facultatives et obligatoires sont distinguées ;
- les versions dangereuses peuvent être bloquées ;
- les API sont versionnées ;
- les dépréciations sont planifiées ;
- les contrats restent compatibles ;
- les événements sont versionnés ;
- les migrations sont traçables ;
- les TPE peuvent être mis à jour progressivement ;
- les rollbacks sont prévus ;
- les appareils incompatibles sont identifiés ;
- les fins de support sont administrables ;
- l’adoption des versions est mesurée ;
- les changements critiques sont audités ;
- les tests couvrent les principales incompatibilités.
