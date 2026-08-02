# 67 — Gestion des versions, mises à jour et parc d’appareils Mansa : applications mobiles, web, TPE, DAB, terminaux agents, compatibilité, distribution, supervision, sécurité et administration centralisée

## 1. Objet du document

Ce document définit l’architecture officielle de la **Gestion des versions, des mises à jour et du parc d’appareils Mansa**.

Ce dispositif doit permettre à Mansa de contrôler l’ensemble des logiciels, versions, terminaux et équipements utilisés dans son écosystème.

Il couvre notamment :

- l’application Client ;
- l’application Commerce ;
- l’application Agent ;
- l’application TPE ;
- l’application Admin Lite ;
- les applications internes ;
- le site web ;
- les portails web ;
- les applications iOS ;
- les applications Android ;
- les WebView embarquées ;
- les TPE Android ;
- les DAB ;
- les terminaux agents ;
- les tablettes institutionnelles ;
- les appareils administrateurs ;
- les imprimantes ;
- les scanners ;
- les lecteurs NFC ;
- les lecteurs de cartes ;
- les appareils biométriques ;
- les versions backend ;
- les versions API ;
- les firmwares ;
- les configurations ;
- les certificats ;
- les clés ;
- les feature flags ;
- les campagnes de mise à jour ;
- les mises à jour obligatoires ;
- les rollbacks ;
- les appareils perdus ;
- les appareils volés ;
- les appareils compromis ;
- les appareils hors ligne ;
- les appareils en fin de support ;
- les inventaires ;
- les audits.

L’objectif est de fournir une plateforme capable de :

- connaître tous les appareils actifs ;
- savoir quelle version est installée ;
- contrôler la compatibilité ;
- déployer progressivement une mise à jour ;
- bloquer une version dangereuse ;
- imposer une version minimale ;
- restaurer une version précédente ;
- surveiller la santé du parc ;
- sécuriser les appareils ;
- gérer plusieurs pays ;
- gérer plusieurs types de terminaux ;
- éviter les appareils non autorisés ;
- garantir la traçabilité complète des changements.

---

# 2. Principes fondamentaux

## 2.1 Aucun appareil critique ne doit être inconnu

Tout appareil utilisé pour des opérations sensibles doit être enregistré avec :

- un identifiant unique ;
- un type ;
- un propriétaire ;
- une organisation ;
- un pays ;
- une localisation éventuelle ;
- une version ;
- un statut ;
- un certificat ;
- une date d’enrôlement ;
- une dernière activité ;
- un historique.

---

## 2.2 Chaque version doit être traçable

Chaque version doit être reliée à :

- un commit ;
- un build ;
- une pipeline ;
- un artefact ;
- une signature ;
- une date ;
- un environnement ;
- une application ;
- un responsable ;
- une campagne ;
- un résultat de test ;
- un statut.

---

## 2.3 Une mise à jour critique doit être contrôlable à distance

Mansa doit pouvoir :

- publier ;
- suspendre ;
- reprendre ;
- ralentir ;
- arrêter ;
- annuler ;
- forcer ;
- retirer ;
- restaurer ;
- surveiller une campagne.

---

## 2.4 Aucun appareil compromis ne doit continuer à opérer librement

Un appareil compromis peut être :

- suspendu ;
- limité ;
- verrouillé ;
- déconnecté ;
- révoqué ;
- mis en quarantaine ;
- effacé à distance lorsque techniquement permis ;
- interdit d’accès aux opérations financières.

---

## 2.5 Les versions anciennes doivent rester compatibles pendant une période contrôlée

La compatibilité doit être gérée pour :

- anciennes applications mobiles ;
- anciens TPE ;
- anciens DAB ;
- anciens SDK ;
- anciennes API partenaires ;
- anciens systèmes d’exploitation ;
- appareils temporairement hors ligne.

---

## 2.6 Une mise à jour ne doit pas bloquer inutilement l’activité

Les mises à jour doivent prendre en compte :

- horaires ;
- pays ;
- activité ;
- batterie ;
- réseau ;
- stockage ;
- opération en cours ;
- caisse ouverte ;
- maintenance ;
- criticité ;
- disponibilité d’un rollback.

---

# 3. Périmètre

Le dispositif couvre :

- versions applicatives ;
- versions backend ;
- versions API ;
- versions firmware ;
- versions de configuration ;
- versions de modèles IA ;
- versions de règles ;
- appareils mobiles ;
- terminaux TPE ;
- DAB ;
- tablettes ;
- postes administrateurs ;
- périphériques ;
- certificats ;
- identités techniques ;
- campagnes ;
- compatibilité ;
- distribution ;
- sécurité ;
- inventaire ;
- monitoring ;
- support ;
- maintenance ;
- fin de vie.

---

# 4. Architecture logique

Structure recommandée :

```text
device-and-release-management/
├── applications/
├── releases/
├── builds/
├── artifacts/
├── compatibility/
├── campaigns/
├── mobile-devices/
├── merchant-terminals/
├── agent-terminals/
├── atm-devices/
├── admin-devices/
├── firmware/
├── configurations/
├── certificates/
├── enrollment/
├── compliance/
├── security/
├── remote-actions/
├── telemetry/
├── maintenance/
├── end-of-life/
├── reports/
├── audit/
└── administration/
```

---

# 5. Types de versions

Le système doit gérer :

- version majeure ;
- version mineure ;
- patch ;
- hotfix ;
- build interne ;
- bêta ;
- release candidate ;
- version stable ;
- version pilote ;
- version retirée ;
- firmware ;
- configuration ;
- API ;
- base de données ;
- SDK.

---

# 6. Convention de version

Exemple :

```text
MAJOR.MINOR.PATCH
```

Exemple :

```text
3.12.4
```

Signification :

- MAJOR : changement majeur ou incompatibilité ;
- MINOR : nouvelle fonctionnalité compatible ;
- PATCH : correction compatible.

---

# 7. Numéro de build

Chaque livraison doit posséder un numéro de build distinct.

Exemple :

```text
Version publique : 3.12.4
Build interne : 31204027
```

---

# 8. Statuts d’une version

- DRAFT ;
- BUILDING ;
- TESTING ;
- QA_APPROVED ;
- SECURITY_APPROVED ;
- RELEASE_CANDIDATE ;
- PILOT ;
- ACTIVE ;
- LIMITED ;
- SUSPENDED ;
- BLOCKED ;
- DEPRECATED ;
- RETIRED ;
- ROLLED_BACK.

---

# 9. Fiche d’une version

Chaque version doit contenir :

- identifiant ;
- application ;
- plateforme ;
- version ;
- build ;
- date ;
- commit ;
- branche ;
- artefact ;
- hash ;
- signature ;
- environnement ;
- changements ;
- correctifs ;
- risques ;
- migrations ;
- compatibilité ;
- version minimale backend ;
- version maximale backend ;
- résultat des tests ;
- responsable ;
- statut.

---

# 10. Changelog

Le changelog doit préciser :

- nouveautés ;
- corrections ;
- sécurité ;
- performance ;
- fonctionnalités retirées ;
- changements de compatibilité ;
- migrations ;
- impacts ;
- limitations connues.

---

# 11. Types d’applications

Le système doit distinguer :

- Client Mobile ;
- Commerce Mobile ;
- Agent Mobile ;
- TPE Android ;
- Admin Lite ;
- Web Admin ;
- Web Public ;
- Portail Développeurs ;
- Portail Entreprises ;
- Portail Institutions ;
- logiciel DAB ;
- logiciel de maintenance ;
- applications internes.

---

# 12. Plateformes

- Android ;
- iOS ;
- Web ;
- Android TPE ;
- Linux embarqué ;
- Windows embarqué ;
- firmware propriétaire ;
- navigateur ;
- WebView ;
- serveur.

---

# 13. Compatibilité système d’exploitation

Chaque version doit préciser :

- version minimale OS ;
- version recommandée ;
- version maximale testée ;
- architecture CPU ;
- mémoire minimale ;
- stockage minimal ;
- dépendances ;
- permissions ;
- périphériques requis.

---

# 14. Compatibilité backend

Le backend doit pouvoir définir :

- version mobile minimale ;
- version mobile recommandée ;
- version TPE minimale ;
- version DAB minimale ;
- période de tolérance ;
- API compatibles ;
- fonctionnalités désactivées ;
- message de mise à jour.

---

# 15. Matrice de compatibilité

Exemple :

```text
App Client 3.12.x
→ API v4
→ Backend 8.x
→ Android 10+
→ iOS 16+
```

```text
TPE 5.6.x
→ API Terminal v3
→ Firmware 2.1+
→ Android 11+
```

---

# 16. Version minimale

La version minimale est la plus ancienne version encore autorisée.

Un appareil sous cette version peut être :

- averti ;
- limité ;
- bloqué ;
- redirigé vers une mise à jour ;
- autorisé uniquement en lecture ;
- autorisé uniquement aux opérations essentielles.

---

# 17. Version recommandée

La version recommandée est la version stable conseillée.

L’utilisateur peut recevoir :

- notification ;
- bannière ;
- message ;
- rappel ;
- avantage promotionnel éventuel ;
- assistance.

---

# 18. Mise à jour obligatoire

Elle peut être imposée en cas de :

- faille critique ;
- incompatibilité ;
- erreur financière ;
- changement réglementaire ;
- changement API ;
- certificat expirant ;
- corruption possible ;
- nouvelle exigence de sécurité ;
- fin de support.

---

# 19. Mise à jour facultative

Elle peut concerner :

- amélioration visuelle ;
- nouvelle fonctionnalité ;
- optimisation ;
- contenu ;
- correction non critique ;
- performance.

---

# 20. Mise à jour silencieuse

Elle peut être autorisée uniquement sur les appareils gérés lorsque :

- l’appareil appartient à Mansa ou à un partenaire autorisé ;
- la politique le permet ;
- l’artefact est signé ;
- l’opération est tracée ;
- le risque est contrôlé ;
- un rollback existe.

---

# 21. Mise à jour avec confirmation

Elle peut être utilisée pour :

- applications Client ;
- appareils personnels ;
- changements importants ;
- autorisations nouvelles ;
- consommation de données importante ;
- redémarrage nécessaire.

---

# 22. Campagne de mise à jour

Une campagne doit contenir :

- application ;
- version source ;
- version cible ;
- pays ;
- appareils ;
- pourcentage ;
- date ;
- heure ;
- durée ;
- réseau requis ;
- batterie minimale ;
- espace minimal ;
- criticité ;
- rollback ;
- statut ;
- responsable.

---

# 23. Statuts d’une campagne

- DRAFT ;
- PLANNED ;
- APPROVED ;
- SCHEDULED ;
- RUNNING ;
- PAUSED ;
- PARTIAL ;
- COMPLETED ;
- FAILED ;
- CANCELLED ;
- ROLLED_BACK.

---

# 24. Déploiement progressif

Exemple :

```text
1 % des appareils
→ 5 %
→ 10 %
→ 25 %
→ 50 %
→ 100 %
```

Chaque étape doit être validée par :

- taux de succès ;
- crash ;
- erreurs ;
- performance ;
- retours ;
- incidents ;
- compatibilité ;
- métriques métier.

---

# 25. Déploiement pilote

Le pilote peut cibler :

- équipe interne ;
- appareils de test ;
- pays pilote ;
- ville pilote ;
- partenaires pilotes ;
- agents sélectionnés ;
- commerçants sélectionnés ;
- DAB de test ;
- TPE de démonstration.

---

# 26. Déploiement Canary

La version est distribuée à un petit segment avant généralisation.

Le système doit surveiller :

- crash ;
- taux de paiement ;
- refus ;
- latence ;
- synchronisation ;
- batterie ;
- réseau ;
- support ;
- anomalies.

---

# 27. Déploiement par pays

Une campagne peut être définie par :

- pays ;
- région ;
- ville ;
- langue ;
- partenaire ;
- opérateur ;
- réseau ;
- fuseau ;
- réglementation ;
- disponibilité des stores.

---

# 28. Déploiement par segment

Exemples :

- nouveaux utilisateurs ;
- utilisateurs fidèles ;
- employés ;
- agents premium ;
- commerçants pilotes ;
- TPE d’un modèle précis ;
- DAB d’une série ;
- appareils à faible risque.

---

# 29. Déploiement par modèle d’appareil

Le système doit pouvoir cibler :

- fabricant ;
- modèle ;
- OS ;
- version firmware ;
- mémoire ;
- stockage ;
- périphérique ;
- numéro de série ;
- architecture.

---

# 30. Critères avant installation

Avant installation, vérifier :

- batterie ;
- alimentation ;
- réseau ;
- stockage ;
- intégrité de l’artefact ;
- signature ;
- version actuelle ;
- compatibilité ;
- opération en cours ;
- caisse ouverte ;
- maintenance ;
- autorisation.

---

# 31. Interdiction de mise à jour pendant une opération

Une mise à jour ne doit pas démarrer pendant :

- paiement ;
- retrait ;
- dépôt ;
- remboursement ;
- clôture ;
- impression ;
- synchronisation critique ;
- distribution de billets ;
- maintenance matérielle ;
- migration locale.

---

# 32. Plage horaire

Les mises à jour peuvent être planifiées selon :

- nuit ;
- heure creuse ;
- fermeture du commerce ;
- fermeture de caisse ;
- maintenance ;
- faible trafic ;
- pays ;
- jour férié ;
- fuseau.

---

# 33. Téléchargement

Le téléchargement doit gérer :

- reprise ;
- pause ;
- faible réseau ;
- checksum ;
- signature ;
- expiration ;
- cache ;
- limite de données ;
- source secondaire ;
- CDN.

---

# 34. Installation

L’installation doit vérifier :

- intégrité ;
- signature ;
- espace ;
- compatibilité ;
- permissions ;
- batterie ;
- état de l’appareil ;
- version source ;
- migration ;
- redémarrage.

---

# 35. Échec d’installation

En cas d’échec :

- conserver l’ancienne version ;
- journaliser ;
- envoyer l’erreur ;
- retenter selon règle ;
- bloquer après seuil ;
- alerter le support ;
- proposer une intervention ;
- éviter une boucle infinie.

---

# 36. Rollback

Le rollback peut restaurer :

- version applicative ;
- firmware ;
- configuration ;
- feature flag ;
- certificat ;
- modèle ;
- politique ;
- API ;
- WebView.

---

# 37. Conditions de rollback

Exemples :

- crash élevé ;
- paiement en échec ;
- synchronisation bloquée ;
- batterie anormalement consommée ;
- corruption locale ;
- problème périphérique ;
- problème de signature ;
- incompatibilité ;
- incident sécurité ;
- hausse des tickets.

---

# 38. Rollback automatique

Il peut être autorisé si :

- seuil dépassé ;
- version précédente disponible ;
- migration réversible ;
- appareil accessible ;
- aucune opération en cours ;
- politique approuvée.

---

# 39. Rollback manuel

Il doit préciser :

- appareil ou segment ;
- version cible ;
- motif ;
- responsable ;
- approbateur ;
- date ;
- résultat ;
- preuve ;
- surveillance.

---

# 40. Versions de configuration

Certaines modifications peuvent être distribuées sans nouvelle application.

Exemples :

- paramètres ;
- limites ;
- endpoints ;
- langues ;
- menus ;
- feature flags ;
- horaires ;
- règles d’affichage ;
- fournisseurs ;
- reçus ;
- formulaires.

---

# 41. Configuration distante

La configuration distante doit être :

- signée ;
- versionnée ;
- limitée ;
- validée ;
- ciblée ;
- réversible ;
- auditée ;
- compatible.

---

# 42. Configuration locale

Chaque appareil peut conserver :

- version de configuration ;
- date ;
- hash ;
- source ;
- statut ;
- date de dernière synchronisation ;
- version de secours.

---

# 43. Feature flags

Les fonctionnalités peuvent être activées par :

- pays ;
- appareil ;
- version ;
- utilisateur ;
- organisation ;
- commerçant ;
- agent ;
- pourcentage ;
- environnement ;
- modèle.

---

# 44. Feature flag d’urgence

Il peut permettre de :

- désactiver un paiement ;
- désactiver un partenaire ;
- couper une fonction ;
- passer en lecture seule ;
- bloquer une version ;
- masquer un écran ;
- activer un fallback ;
- limiter un plafond.

---

# 45. Inventaire des appareils

Chaque appareil doit être enregistré avec :

- device ID ;
- numéro de série ;
- IMEI si autorisé ;
- modèle ;
- fabricant ;
- OS ;
- firmware ;
- application ;
- version ;
- propriétaire ;
- organisation ;
- pays ;
- statut ;
- certificat ;
- dernière connexion ;
- dernière localisation si autorisée ;
- niveau de conformité.

---

# 46. Types d’appareils

- téléphone personnel ;
- téléphone professionnel ;
- tablette ;
- TPE ;
- DAB ;
- terminal agent ;
- poste administrateur ;
- scanner ;
- imprimante ;
- lecteur biométrique ;
- kiosque ;
- serveur local ;
- appareil de maintenance.

---

# 47. Statuts d’un appareil

- PENDING_ENROLLMENT ;
- ACTIVE ;
- INACTIVE ;
- OFFLINE ;
- DEGRADED ;
- NON_COMPLIANT ;
- QUARANTINED ;
- SUSPENDED ;
- BLOCKED ;
- LOST ;
- STOLEN ;
- RETIRED ;
- DECOMMISSIONED.

---

# 48. Enrôlement

L’enrôlement doit permettre :

- identification ;
- vérification ;
- attribution ;
- certificat ;
- configuration ;
- installation ;
- test ;
- activation ;
- association à une organisation ;
- audit.

---

# 49. Enrôlement d’un TPE

Le processus doit vérifier :

- numéro de série ;
- modèle ;
- firmware ;
- commerçant ;
- point de vente ;
- pays ;
- application ;
- certificat ;
- clé ;
- périphériques ;
- connectivité ;
- test transactionnel ;
- activation.

---

# 50. Enrôlement d’un DAB

Le processus doit vérifier :

- constructeur ;
- modèle ;
- série ;
- localisation ;
- opérateur ;
- cassettes ;
- lecteurs ;
- imprimante ;
- clavier sécurisé ;
- réseau ;
- certificats ;
- clés ;
- logiciel ;
- test de distribution ;
- activation.

---

# 51. Enrôlement d’un appareil Agent

Le processus doit vérifier :

- identité de l’agent ;
- organisation ;
- appareil ;
- numéro de série ;
- SIM éventuelle ;
- localisation si activée ;
- certificat ;
- PIN appareil ;
- biométrie ;
- application ;
- droits ;
- test de connexion.

---

# 52. Enrôlement d’un appareil administrateur

Il doit imposer :

- MFA ;
- appareil approuvé ;
- chiffrement ;
- verrouillage ;
- OS à jour ;
- antivirus ou protections adaptées ;
- certificat ;
- durée d’accès ;
- rôle ;
- audit.

---

# 53. Device Binding

Un compte sensible peut être lié à un ou plusieurs appareils autorisés.

Le système doit gérer :

- appareil principal ;
- appareil secondaire ;
- changement ;
- révocation ;
- récupération ;
- notification ;
- délai de sécurité ;
- validation renforcée.

---

# 54. Attestation de l’appareil

Le système peut vérifier :

- intégrité ;
- root ;
- jailbreak ;
- bootloader ;
- signature ;
- application officielle ;
- environnement ;
- émulateur ;
- hook ;
- débogage ;
- version OS.

---

# 55. Root et jailbreak

Un appareil rooté ou jailbreaké peut être :

- averti ;
- limité ;
- bloqué ;
- interdit d’opérations sensibles ;
- soumis à une vérification supplémentaire ;
- placé en quarantaine.

---

# 56. Émulateurs

Les émulateurs doivent être :

- autorisés en Développement ;
- autorisés en Test ;
- limités en Démo ;
- interdits en Production pour les fonctions sensibles sauf exception approuvée.

---

# 57. Conformité d’un appareil

La conformité peut vérifier :

- version minimale ;
- OS supporté ;
- chiffrement ;
- verrouillage ;
- certificat ;
- root ;
- jailbreak ;
- antivirus ;
- stockage ;
- heure ;
- réseau ;
- configuration ;
- application officielle.

---

# 58. Score de conformité

Le système peut attribuer :

- COMPLIANT ;
- WARNING ;
- LIMITED ;
- NON_COMPLIANT ;
- CRITICAL.

---

# 59. Quarantaine

Un appareil peut être mis en quarantaine en cas de :

- version dangereuse ;
- certificat invalide ;
- root ;
- jailbreak ;
- activité suspecte ;
- perte ;
- vol ;
- compromission ;
- malware ;
- échec d’attestation ;
- configuration non conforme.

---

# 60. Actions en quarantaine

L’appareil peut uniquement :

- contacter le support ;
- télécharger une mise à jour ;
- renouveler un certificat ;
- afficher un message ;
- envoyer des diagnostics ;
- être réactivé après validation.

---

# 61. Appareil perdu

Le processus doit permettre :

- déclaration ;
- suspension ;
- révocation des sessions ;
- révocation du certificat ;
- blocage ;
- notification ;
- effacement distant si possible ;
- transfert vers un nouvel appareil ;
- audit.

---

# 62. Appareil volé

En plus du blocage :

- alerte fraude ;
- géolocalisation si autorisée ;
- verrouillage distant ;
- rotation des secrets ;
- enquête ;
- conservation des preuves ;
- notification des responsables.

---

# 63. Appareil compromis

Le système doit pouvoir :

- couper l’accès ;
- révoquer les clés ;
- forcer une reconnexion ;
- bloquer les transactions ;
- capturer les éléments techniques nécessaires ;
- ouvrir un incident ;
- déclencher une investigation ;
- imposer un remplacement.

---

# 64. Certificats d’appareil

Chaque appareil critique peut disposer d’un certificat propre.

Le certificat doit avoir :

- identifiant ;
- appareil ;
- date d’émission ;
- date d’expiration ;
- autorité ;
- statut ;
- clé associée ;
- usage ;
- historique ;
- révocation.

---

# 65. Rotation des certificats

La rotation doit être :

- automatique lorsque possible ;
- planifiée ;
- surveillée ;
- progressive ;
- compatible avec le hors ligne ;
- auditée ;
- réversible.

---

# 66. Révocation des certificats

Elle doit être immédiate en cas de :

- vol ;
- perte ;
- compromission ;
- fin de contrat ;
- retrait du parc ;
- erreur ;
- certificat dupliqué ;
- appareil remplacé.

---

# 67. Clés d’appareil

Les clés doivent être :

- uniques ;
- protégées ;
- non exportables lorsque possible ;
- stockées dans un composant sécurisé ;
- renouvelables ;
- révocables ;
- auditées.

---

# 68. Gestion du parc TPE

L’administration doit voir :

- nombre total ;
- actifs ;
- inactifs ;
- hors ligne ;
- versions ;
- modèles ;
- commerçants ;
- pays ;
- état réseau ;
- imprimante ;
- NFC ;
- batterie ;
- campagnes ;
- incidents.

---

# 69. Gestion du parc DAB

L’administration doit voir :

- DAB actifs ;
- hors ligne ;
- maintenance ;
- version ;
- firmware ;
- constructeur ;
- cassettes ;
- billets ;
- périphériques ;
- localisation ;
- réseau ;
- incidents ;
- dernière transaction.

---

# 70. Gestion du parc Agent

L’administration doit voir :

- appareils actifs ;
- agents ;
- versions ;
- conformité ;
- dernière connexion ;
- pays ;
- localisation si activée ;
- incidents ;
- caisse ;
- mise à jour ;
- statut.

---

# 71. Gestion du parc mobile Client

Le système doit produire des statistiques agrégées sur :

- version ;
- OS ;
- modèle ;
- crash ;
- mise à jour ;
- pays ;
- langue ;
- compatibilité ;
- taux d’adoption.

Il ne doit pas exposer inutilement des identifiants personnels.

---

# 72. Télémetrie

Les appareils peuvent transmettre :

- état ;
- version ;
- OS ;
- batterie ;
- stockage ;
- réseau ;
- température si disponible ;
- crash ;
- erreur ;
- périphériques ;
- dernière synchronisation ;
- conformité.

---

# 73. Données interdites dans la télémetrie

Ne pas transmettre :

- PIN ;
- mot de passe ;
- OTP ;
- CVV ;
- numéro complet de carte ;
- clé privée ;
- contenu complet des transactions ;
- biométrie ;
- documents ;
- données inutiles.

---

# 74. Fréquence de télémetrie

Elle peut dépendre :

- type d’appareil ;
- criticité ;
- réseau ;
- batterie ;
- activité ;
- pays ;
- incident ;
- mode hors ligne ;
- coût.

---

# 75. Appareils hors ligne

Le système doit suivre :

- dernière connexion ;
- durée hors ligne ;
- dernière version ;
- opérations en attente ;
- certificat ;
- configuration ;
- risque ;
- action prévue.

---

# 76. Seuil hors ligne

Exemples :

- téléphone Client : seuil souple ;
- TPE : seuil court ;
- DAB : seuil critique ;
- terminal Agent : seuil opérationnel ;
- poste Admin : seuil de sécurité.

---

# 77. Synchronisation après reconnexion

L’appareil doit :

- s’authentifier ;
- vérifier le certificat ;
- vérifier la version ;
- télécharger la configuration ;
- envoyer la télémetrie ;
- synchroniser les opérations ;
- résoudre les conflits ;
- vérifier les mises à jour ;
- confirmer son état.

---

# 78. Gestion des conflits

Les conflits peuvent concerner :

- configuration ;
- opération locale ;
- version ;
- horloge ;
- droits ;
- caisse ;
- inventaire ;
- état du terminal.

Ils doivent être résolus selon des règles définies.

---

# 79. Horloge de l’appareil

Le système doit détecter :

- heure incorrecte ;
- fuseau incorrect ;
- date future ;
- date passée ;
- dérive importante ;
- synchronisation désactivée.

Une horloge incorrecte peut limiter les opérations sensibles.

---

# 80. Stockage insuffisant

Le système doit :

- détecter ;
- alerter ;
- proposer un nettoyage ;
- différer la mise à jour ;
- limiter les logs ;
- empêcher une installation incomplète ;
- signaler au support.

---

# 81. Batterie insuffisante

Une mise à jour peut exiger :

- niveau minimal ;
- branchement ;
- alimentation stable ;
- absence d’opération ;
- délai suffisant.

---

# 82. Réseau insuffisant

Le téléchargement peut exiger :

- Wi-Fi ;
- réseau stable ;
- débit minimal ;
- absence de roaming ;
- accord utilisateur ;
- reprise automatique.

---

# 83. Maintenance matérielle

Le système doit gérer :

- maintenance prévue ;
- maintenance urgente ;
- diagnostic ;
- remplacement ;
- réparation ;
- pièce ;
- technicien ;
- rapport ;
- résultat ;
- remise en service.

---

# 84. Statuts de maintenance

- REQUESTED ;
- PLANNED ;
- ASSIGNED ;
- IN_PROGRESS ;
- WAITING_PART ;
- COMPLETED ;
- FAILED ;
- CANCELLED ;
- VERIFIED.

---

# 85. Fiche de maintenance

Elle doit contenir :

- appareil ;
- problème ;
- date ;
- technicien ;
- site ;
- pièces ;
- diagnostic ;
- action ;
- version ;
- test ;
- résultat ;
- coût ;
- preuve.

---

# 86. Diagnostic distant

Le support peut consulter :

- version ;
- logs techniques masqués ;
- réseau ;
- batterie ;
- stockage ;
- périphériques ;
- certificat ;
- dernière erreur ;
- état de synchronisation.

---

# 87. Actions distantes

Actions possibles :

- redémarrer l’application ;
- relancer la synchronisation ;
- vider un cache non critique ;
- renouveler la configuration ;
- mettre à jour ;
- verrouiller ;
- suspendre ;
- révoquer ;
- redémarrer l’appareil ;
- lancer un diagnostic ;
- mettre en quarantaine.

---

# 88. Protection des actions distantes

Une action distante sensible doit exiger :

- rôle ;
- justification ;
- appareil ciblé ;
- confirmation ;
- approbation selon criticité ;
- journal ;
- résultat ;
- preuve.

---

# 89. Effacement distant

L’effacement distant peut être utilisé uniquement pour les appareils gérés et selon les politiques autorisées.

Il doit :

- être approuvé ;
- être ciblé ;
- éviter d’effacer des données personnelles non concernées ;
- être journalisé ;
- produire un statut ;
- conserver la preuve.

---

# 90. Mode kiosque

Les TPE, DAB et terminaux dédiés peuvent fonctionner en mode kiosque.

Le mode kiosque doit :

- limiter les applications ;
- bloquer les réglages ;
- empêcher les installations non autorisées ;
- contrôler les ports ;
- protéger les notifications ;
- surveiller les sorties ;
- permettre une administration distante.

---

# 91. Applications autorisées

Chaque appareil géré peut avoir une liste :

- autorisée ;
- interdite ;
- obligatoire ;
- facultative ;
- limitée.

---

# 92. Détection d’application non autorisée

Le système peut :

- alerter ;
- bloquer ;
- désinstaller ;
- mettre en quarantaine ;
- limiter l’accès ;
- ouvrir un incident.

---

# 93. Permissions système

Les permissions doivent être limitées à celles nécessaires :

- caméra ;
- NFC ;
- Bluetooth ;
- localisation ;
- stockage ;
- téléphone ;
- biométrie ;
- notifications ;
- microphone ;
- réseau.

---

# 94. Changement de permissions

Toute nouvelle permission doit être :

- justifiée ;
- documentée ;
- testée ;
- communiquée ;
- validée ;
- limitée ;
- compatible avec les stores.

---

# 95. Distribution mobile

Les applications peuvent être distribuées par :

- App Store ;
- Google Play ;
- distribution interne ;
- TestFlight ;
- piste de test ;
- MDM ;
- APK signé contrôlé ;
- store privé ;
- canal partenaire.

---

# 96. Distribution TPE

Elle peut utiliser :

- MDM ;
- store privé ;
- gestion constructeur ;
- serveur Mansa ;
- plateforme partenaire ;
- installation locale contrôlée ;
- campagne distante.

---

# 97. Distribution DAB

Elle doit utiliser :

- package signé ;
- canal sécurisé ;
- validation constructeur ;
- campagne ;
- fenêtre de maintenance ;
- contrôle d’intégrité ;
- rollback ;
- supervision.

---

# 98. Signature des applications

Chaque artefact doit être signé avec :

- certificat ;
- clé sécurisée ;
- identité ;
- horodatage ;
- hash ;
- chaîne de confiance ;
- environnement.

---

# 99. Protection des clés de signature

Les clés doivent être :

- stockées dans HSM ou coffre sécurisé ;
- limitées ;
- rotatives ;
- auditées ;
- non disponibles sur un poste personnel ;
- protégées par approbation ;
- sauvegardées selon politique.

---

# 100. Révocation d’un artefact

Une version peut être révoquée en cas de :

- malware ;
- mauvaise signature ;
- faille ;
- corruption ;
- erreur critique ;
- publication accidentelle ;
- compromission de clé.

---

# 101. Blocage d’une version

Le backend peut bloquer :

- version précise ;
- plage de versions ;
- build ;
- plateforme ;
- pays ;
- modèle d’appareil ;
- segment ;
- environnement.

---

# 102. Message de blocage

Il doit expliquer :

- que la version n’est plus autorisée ;
- pourquoi de manière simple ;
- comment mettre à jour ;
- quoi faire en cas d’échec ;
- comment contacter le support.

---

# 103. Fin de support

Chaque version doit posséder :

- date de publication ;
- date de fin de support ;
- date d’avertissement ;
- date de blocage ;
- version de remplacement ;
- plan de migration ;
- communication.

---

# 104. Fin de vie d’un appareil

Un appareil peut être retiré pour :

- ancienneté ;
- incompatibilité ;
- sécurité ;
- panne ;
- absence de pièces ;
- performance insuffisante ;
- constructeur non supporté ;
- fin de contrat.

---

# 105. Décommissionnement

Le processus doit inclure :

- retrait du parc ;
- révocation des certificats ;
- effacement ;
- récupération des clés ;
- suppression des accès ;
- mise à jour de l’inventaire ;
- archivage ;
- preuve ;
- destruction ou recyclage.

---

# 106. Recyclage

Le recyclage doit respecter :

- effacement sécurisé ;
- protection des données ;
- inventaire ;
- preuve ;
- partenaire autorisé ;
- destruction des supports ;
- conformité environnementale.

---

# 107. Appareil remplacé

Le remplacement doit gérer :

- ancien appareil ;
- nouvel appareil ;
- transfert de propriété ;
- configuration ;
- certificats ;
- application ;
- données autorisées ;
- test ;
- activation ;
- désactivation de l’ancien.

---

# 108. Stock d’appareils

L’administration peut gérer :

- appareils disponibles ;
- attribués ;
- en transit ;
- en réparation ;
- en réserve ;
- perdus ;
- volés ;
- retirés ;
- recyclés.

---

# 109. Affectation

Une affectation doit contenir :

- appareil ;
- utilisateur ;
- organisation ;
- site ;
- date ;
- responsable ;
- contrat ;
- accessoires ;
- état ;
- preuve de remise.

---

# 110. Retour d’appareil

Le retour doit vérifier :

- identité ;
- état ;
- accessoires ;
- données ;
- certificat ;
- verrouillage ;
- réparation ;
- réaffectation ;
- effacement ;
- archivage.

---

# 111. Garantie

Le système peut suivre :

- constructeur ;
- date d’achat ;
- garantie ;
- expiration ;
- fournisseur ;
- contrat ;
- panne ;
- remplacement ;
- historique.

---

# 112. Gestion des périphériques

Le système doit suivre :

- imprimante ;
- scanner ;
- lecteur de carte ;
- NFC ;
- clavier PIN ;
- caméra ;
- capteur ;
- cassette ;
- modem ;
- batterie ;
- écran.

---

# 113. État des périphériques

- AVAILABLE ;
- DEGRADED ;
- FAILED ;
- DISCONNECTED ;
- MAINTENANCE ;
- REPLACED ;
- UNKNOWN.

---

# 114. Compatibilité périphérique

Chaque version doit préciser les périphériques compatibles.

Exemples :

- modèle d’imprimante ;
- driver ;
- version NFC ;
- lecteur de carte ;
- scanner ;
- clavier sécurisé ;
- cassette DAB.

---

# 115. Gestion des drivers

Les drivers doivent être :

- signés ;
- versionnés ;
- testés ;
- compatibles ;
- remplaçables ;
- distribués avec contrôle ;
- retirables ;
- audités.

---

# 116. Mises à jour firmware

Elles doivent être :

- signées ;
- testées ;
- ciblées ;
- progressives ;
- compatibles ;
- planifiées ;
- réversibles lorsque possible ;
- surveillées.

---

# 117. Firmware critique

Un firmware critique concerne notamment :

- lecteur de carte ;
- clavier PIN ;
- distributeur de billets ;
- NFC ;
- modem ;
- imprimante ;
- contrôleur sécurisé.

---

# 118. Test après mise à jour

Après mise à jour, l’appareil doit vérifier :

- démarrage ;
- application ;
- certificat ;
- réseau ;
- périphériques ;
- stockage ;
- version ;
- synchronisation ;
- transaction de test ;
- télémetrie.

---

# 119. Mise à jour échouée sur TPE

Le terminal doit :

- conserver une version de secours ;
- éviter la corruption ;
- afficher un statut ;
- remonter l’erreur ;
- permettre un diagnostic ;
- continuer en mode sûr si possible ;
- demander une intervention si nécessaire.

---

# 120. Mise à jour échouée sur DAB

Le DAB doit :

- arrêter les opérations financières si l’état est incertain ;
- conserver les journaux ;
- basculer vers une image de secours ;
- alerter ;
- verrouiller les périphériques si nécessaire ;
- demander une intervention ;
- empêcher une distribution incorrecte.

---

# 121. Golden Image

Une image de référence peut être maintenue pour :

- TPE ;
- DAB ;
- tablettes ;
- postes administrateurs.

Elle contient :

- OS ;
- application ;
- drivers ;
- configuration ;
- certificats initiaux ;
- politiques ;
- outils de diagnostic.

---

# 122. Reprovisionnement complet

Un appareil peut être réinstallé depuis la Golden Image lorsque :

- compromis ;
- corrompu ;
- remplacé ;
- réaffecté ;
- trop ancien ;
- non conforme ;
- réparé.

---

# 123. Support à distance

Le support doit pouvoir :

- consulter l’inventaire ;
- voir la version ;
- vérifier la conformité ;
- lancer un diagnostic ;
- guider l’utilisateur ;
- déclencher une mise à jour ;
- créer un ticket ;
- escalader ;
- planifier une intervention.

---

# 124. Liaison avec les incidents

Chaque incident peut être relié à :

- appareil ;
- version ;
- build ;
- modèle ;
- campagne ;
- périphérique ;
- pays ;
- partenaire ;
- utilisateur ;
- ticket.

---

# 125. Détection d’anomalie par version

Le système doit comparer :

- crash ;
- erreurs ;
- latence ;
- batterie ;
- transactions ;
- refus ;
- tickets ;
- synchronisation ;
- performance ;
- sécurité.

---

# 126. Taux d’adoption

La plateforme doit calculer :

- adoption globale ;
- adoption par pays ;
- adoption par application ;
- adoption par appareil ;
- adoption par segment ;
- adoption par jour ;
- appareils bloqués ;
- appareils non joignables.

---

# 127. Indicateurs de campagne

Exemples :

- ciblés ;
- notifiés ;
- téléchargés ;
- installés ;
- réussis ;
- échoués ;
- en attente ;
- annulés ;
- rollbacks ;
- durée moyenne ;
- erreurs par modèle.

---

# 128. Tableau de bord versions

Il doit afficher :

- versions actives ;
- versions anciennes ;
- versions bloquées ;
- adoption ;
- crash ;
- anomalies ;
- campagnes ;
- compatibilité ;
- fin de support ;
- risques.

---

# 129. Tableau de bord parc

Il doit afficher :

- nombre total ;
- actifs ;
- hors ligne ;
- non conformes ;
- perdus ;
- volés ;
- en maintenance ;
- en fin de vie ;
- versions ;
- pays ;
- modèles ;
- propriétaires.

---

# 130. Alertes

Exemples :

- appareil hors ligne ;
- version trop ancienne ;
- certificat expirant ;
- stockage faible ;
- batterie faible ;
- root détecté ;
- jailbreak détecté ;
- mise à jour échouée ;
- firmware incompatible ;
- campagne anormale ;
- appareil compromis ;
- périphérique défaillant.

---

# 131. Règles d’alerte

Chaque alerte doit avoir :

- seuil ;
- sévérité ;
- appareil ;
- version ;
- pays ;
- propriétaire ;
- canal ;
- runbook ;
- délai ;
- escalade ;
- statut.

---

# 132. Multi-pays

Chaque pays peut avoir :

- versions autorisées ;
- calendrier ;
- langues ;
- stores ;
- appareils ;
- partenaires ;
- règles ;
- certificats ;
- firmware ;
- plage horaire ;
- support ;
- politique de blocage.

---

# 133. Multi-organisation

Le système doit séparer les appareils de :

- Mansa ;
- banques ;
- commerçants ;
- agents ;
- institutions ;
- écoles ;
- entreprises ;
- prestataires ;
- mainteneurs.

---

# 134. Propriété de l’appareil

Types :

- MANSA_OWNED ;
- PARTNER_OWNED ;
- MERCHANT_OWNED ;
- AGENT_OWNED ;
- USER_OWNED ;
- LEASED ;
- RENTED ;
- DEMO ;
- TEST.

---

# 135. Politique BYOD

Pour les appareils personnels, la politique doit préciser :

- fonctions autorisées ;
- données stockées ;
- sécurité ;
- séparation ;
- révocation ;
- confidentialité ;
- effacement limité ;
- compatibilité ;
- responsabilité.

---

# 136. Politique COPE

Les appareils appartenant à Mansa mais autorisés pour un usage personnel doivent avoir :

- profil professionnel ;
- profil personnel ;
- séparation ;
- contrôle ;
- effacement professionnel ;
- inventaire ;
- conformité ;
- support.

---

# 137. Politique entièrement gérée

Pour les TPE, DAB et appareils sensibles :

- aucune application libre ;
- mode kiosque ;
- configuration imposée ;
- mises à jour contrôlées ;
- accès administrateur interdit ;
- télémetrie obligatoire ;
- certificat obligatoire ;
- action distante autorisée.

---

# 138. Administration centrale

L’administration doit pouvoir gérer :

- applications ;
- versions ;
- builds ;
- artefacts ;
- compatibilité ;
- campagnes ;
- appareils ;
- propriétaires ;
- certificats ;
- clés ;
- firmware ;
- configuration ;
- feature flags ;
- conformité ;
- sécurité ;
- maintenance ;
- stock ;
- fin de vie ;
- alertes ;
- rapports ;
- audits.

---

# 139. Rôles

Exemples :

```text
RELEASE_ADMIN
RELEASE_MANAGER
MOBILE_RELEASE_MANAGER
WEB_RELEASE_MANAGER
TERMINAL_RELEASE_MANAGER
ATM_RELEASE_MANAGER
DEVICE_FLEET_ADMIN
DEVICE_SECURITY_ADMIN
FIRMWARE_MANAGER
CONFIGURATION_MANAGER
MAINTENANCE_MANAGER
SUPPORT_OPERATOR
INVENTORY_MANAGER
AUDITOR
VIEWER
```

---

# 140. Permissions

Exemples :

```text
release.version.read
release.version.create
release.version.approve
release.version.block
release.campaign.create
release.campaign.approve
release.campaign.pause
release.rollback.execute

device.read
device.enroll
device.assign
device.suspend
device.quarantine
device.revoke
device.remote_action.execute
device.maintenance.manage
device.inventory.manage

firmware.read
firmware.publish
firmware.approve
certificate.rotate
configuration.publish
audit.read
```

---

# 141. Approbations

Peuvent nécessiter une approbation :

- publication Production ;
- mise à jour obligatoire ;
- blocage global ;
- rollback ;
- effacement distant ;
- révocation massive ;
- firmware critique ;
- certificat ;
- campagne nationale ;
- fin de support ;
- décommissionnement massif.

---

# 142. Double validation

Peut être exigée pour :

- signature Production ;
- déploiement DAB ;
- firmware du clavier PIN ;
- blocage de tous les TPE ;
- rollback global ;
- effacement de parc ;
- révocation de certificats ;
- changement de version minimale ;
- mise à jour imposée à l’échelle nationale.

---

# 143. Séparation des rôles

Exemple :

```text
Équipe technique construit
→ QA valide
→ Sécurité approuve
→ Release Manager autorise
→ Plateforme distribue
→ Opérations surveillent
```

---

# 144. API

Exemples :

```http
GET    /releases/applications
GET    /releases/versions
POST   /releases/versions
POST   /releases/versions/{id}/approve
POST   /releases/versions/{id}/block

GET    /releases/campaigns
POST   /releases/campaigns
POST   /releases/campaigns/{id}/start
POST   /releases/campaigns/{id}/pause
POST   /releases/campaigns/{id}/rollback

GET    /devices
POST   /devices/enroll
PATCH  /devices/{id}
POST   /devices/{id}/suspend
POST   /devices/{id}/quarantine
POST   /devices/{id}/revoke

POST   /devices/{id}/actions
GET    /devices/{id}/telemetry
GET    /devices/{id}/maintenance

GET    /firmware
POST   /firmware
POST   /firmware/{id}/publish

GET    /compatibility
GET    /reports
GET    /audit
```

---

# 145. Webhooks internes

Événements possibles :

```text
release.version.created
release.version.approved
release.version.published
release.version.blocked
release.campaign.started
release.campaign.paused
release.campaign.completed
release.campaign.failed
release.rollback.started
release.rollback.completed

device.enrolled
device.activated
device.offline
device.non_compliant
device.quarantined
device.lost
device.stolen
device.revoked
device.maintenance.requested
device.maintenance.completed

firmware.published
certificate.expiring
certificate.revoked
configuration.updated
security.alert
```

---

# 146. Modèles principaux

- ApplicationProduct
- ApplicationVersion
- BuildArtifact
- ReleaseChannel
- CompatibilityRule
- ReleaseCampaign
- CampaignTarget
- CampaignExecution
- RollbackExecution
- Device
- DeviceOwner
- DeviceAssignment
- DeviceEnrollment
- DeviceCertificate
- DeviceKey
- DeviceAttestation
- DeviceComplianceRule
- DeviceComplianceResult
- DeviceTelemetry
- DeviceRemoteAction
- DeviceIncident
- DeviceMaintenance
- DevicePeripheral
- FirmwareVersion
- DeviceConfiguration
- FeatureFlagAssignment
- DeviceInventoryMovement
- DeviceEndOfLife
- ReleaseApproval
- DeviceApproval
- ReleaseAudit

---

# 147. Analytics

Événements possibles :

```text
release_dashboard_opened
release_version_created
release_version_approved
release_campaign_started
release_campaign_paused
release_campaign_completed
release_campaign_failed
release_rollback_executed

device_dashboard_opened
device_enrolled
device_quarantined
device_update_started
device_update_completed
device_update_failed
device_certificate_rotated
device_remote_action_executed
device_maintenance_completed
device_end_of_life_started
```

---

# 148. Données analytics interdites

Ne pas transmettre :

- clés privées ;
- certificats privés ;
- PIN ;
- OTP ;
- données cartes ;
- mots de passe ;
- contenu des transactions ;
- documents ;
- biométrie ;
- secrets ;
- logs sensibles complets ;
- localisation précise non nécessaire.

---

# 149. Audit

Le journal doit contenir :

- utilisateur ;
- rôle ;
- application ;
- version ;
- appareil ;
- campagne ;
- action ;
- pays ;
- organisation ;
- date ;
- heure ;
- ancienne valeur ;
- nouvelle valeur ;
- motif ;
- approbateur ;
- résultat ;
- preuve.

---

# 150. Immutabilité des audits

Les audits doivent être protégés contre :

- modification ;
- suppression ;
- réécriture ;
- remplacement ;
- désactivation ;
- changement de résultat ;
- export non autorisé.

---

# 151. Reporting

Rapports possibles :

- adoption par version ;
- appareils par statut ;
- parc par pays ;
- parc par organisation ;
- conformité ;
- appareils hors ligne ;
- mises à jour échouées ;
- rollbacks ;
- certificats expirants ;
- firmware ;
- maintenance ;
- appareils perdus ;
- appareils volés ;
- fin de support ;
- fin de vie ;
- coûts du parc.

---

# 152. Indicateurs

Exemples :

- taux d’adoption ;
- taux de succès de mise à jour ;
- taux d’échec ;
- temps moyen d’installation ;
- taux de rollback ;
- nombre d’appareils non conformes ;
- nombre d’appareils hors ligne ;
- âge moyen du parc ;
- taux de maintenance ;
- taux de remplacement ;
- délai moyen de remise en service.

---

# 153. Tests

- tests de versionnement ;
- tests de build ;
- tests de signature ;
- tests de changelog ;
- tests de compatibilité ;
- tests de version minimale ;
- tests de mise à jour facultative ;
- tests de mise à jour obligatoire ;
- tests de campagne ;
- tests de canary ;
- tests de pilote ;
- tests par pays ;
- tests par segment ;
- tests de téléchargement ;
- tests de reprise ;
- tests d’installation ;
- tests d’échec ;
- tests de rollback ;
- tests de configuration distante ;
- tests de feature flags ;
- tests d’inventaire ;
- tests d’enrôlement ;
- tests Device Binding ;
- tests d’attestation ;
- tests root ;
- tests jailbreak ;
- tests émulateur ;
- tests de conformité ;
- tests de quarantaine ;
- tests appareil perdu ;
- tests appareil volé ;
- tests appareil compromis ;
- tests certificats ;
- tests rotation ;
- tests révocation ;
- tests clés ;
- tests parc TPE ;
- tests parc DAB ;
- tests parc Agent ;
- tests télémetrie ;
- tests hors ligne ;
- tests synchronisation ;
- tests horloge ;
- tests stockage ;
- tests batterie ;
- tests réseau ;
- tests maintenance ;
- tests diagnostic ;
- tests actions distantes ;
- tests effacement distant ;
- tests kiosque ;
- tests applications interdites ;
- tests permissions ;
- tests distribution mobile ;
- tests distribution TPE ;
- tests distribution DAB ;
- tests clé de signature ;
- tests blocage version ;
- tests fin de support ;
- tests fin de vie ;
- tests décommissionnement ;
- tests affectation ;
- tests retour ;
- tests périphériques ;
- tests drivers ;
- tests firmware ;
- tests Golden Image ;
- tests multi-pays ;
- tests multi-organisation ;
- tests BYOD ;
- tests approbations ;
- tests audit ;
- tests performance ;
- tests haute disponibilité.

---

# 154. Règles métier

1. Tout appareil critique est enregistré.
2. Toute version est traçable.
3. Tout artefact Production est signé.
4. Les versions minimales sont administrables.
5. Les mises à jour critiques peuvent être obligatoires.
6. Les campagnes sont progressives.
7. Les mises à jour ne démarrent pas pendant une opération critique.
8. Les échecs d’installation sont journalisés.
9. Les rollbacks sont prévus.
10. Les configurations distantes sont versionnées.
11. Les appareils compromis sont isolés.
12. Les certificats d’appareils sont révocables.
13. Les appareils rootés peuvent être bloqués.
14. Les émulateurs Production sont limités.
15. Les appareils non conformes peuvent être mis en quarantaine.
16. Les appareils perdus ou volés sont révoqués.
17. Les actions distantes sont auditées.
18. Les TPE et DAB utilisent des packages signés.
19. Les clés de signature sont protégées.
20. Les versions anciennes ont une date de fin de support.
21. Les appareils retirés sont effacés.
22. Les périphériques sont inventoriés.
23. Les campagnes sont surveillées.
24. Le demandeur ne valide pas seul une action critique.
25. Les audits sont immuables.

---

# 155. Critères d’acceptation

La Gestion des versions, des mises à jour et du parc d’appareils Mansa est validée lorsque :

- toutes les applications possèdent un versionnement ;
- les builds sont identifiables ;
- les artefacts sont signés ;
- les changelogs sont disponibles ;
- les statuts de version sont gérés ;
- la compatibilité OS est définie ;
- la compatibilité backend est définie ;
- les versions minimales sont administrables ;
- les mises à jour recommandées sont gérées ;
- les mises à jour obligatoires sont gérées ;
- les campagnes sont planifiables ;
- le déploiement progressif fonctionne ;
- les pilotes sont supportés ;
- le canary est supporté ;
- le ciblage par pays fonctionne ;
- le ciblage par segment fonctionne ;
- le ciblage par modèle fonctionne ;
- les prérequis sont vérifiés ;
- aucune mise à jour ne démarre pendant une opération critique ;
- les plages horaires sont configurables ;
- le téléchargement reprend après interruption ;
- les signatures sont vérifiées ;
- les échecs d’installation sont gérés ;
- le rollback est disponible ;
- les versions de configuration sont gérées ;
- les feature flags sont compatibles avec les appareils ;
- l’inventaire est centralisé ;
- les appareils possèdent un identifiant unique ;
- les statuts d’appareil sont gérés ;
- l’enrôlement TPE fonctionne ;
- l’enrôlement DAB fonctionne ;
- l’enrôlement Agent fonctionne ;
- l’enrôlement Admin fonctionne ;
- le Device Binding fonctionne ;
- l’attestation est disponible ;
- les appareils rootés sont détectés ;
- les appareils jailbreakés sont détectés ;
- les émulateurs sont contrôlés ;
- la conformité est mesurée ;
- la quarantaine fonctionne ;
- les appareils perdus sont gérés ;
- les appareils volés sont gérés ;
- les appareils compromis sont bloqués ;
- les certificats d’appareil sont gérés ;
- la rotation des certificats fonctionne ;
- la révocation fonctionne ;
- les clés d’appareil sont protégées ;
- le parc TPE est supervisé ;
- le parc DAB est supervisé ;
- le parc Agent est supervisé ;
- la télémetrie est disponible ;
- les données sensibles ne sont pas transmises ;
- les appareils hors ligne sont détectés ;
- la synchronisation après reconnexion fonctionne ;
- les conflits sont gérés ;
- l’horloge incorrecte est détectée ;
- le stockage faible est détecté ;
- la batterie faible est détectée ;
- le réseau faible est pris en compte ;
- les maintenances sont gérées ;
- les diagnostics distants sont disponibles ;
- les actions distantes sont protégées ;
- l’effacement distant est encadré ;
- le mode kiosque est disponible ;
- les applications autorisées sont contrôlées ;
- les permissions système sont maîtrisées ;
- la distribution mobile est gérée ;
- la distribution TPE est gérée ;
- la distribution DAB est gérée ;
- les clés de signature sont protégées ;
- les artefacts peuvent être révoqués ;
- les versions peuvent être bloquées ;
- les messages de blocage sont clairs ;
- les dates de fin de support sont gérées ;
- la fin de vie des appareils est gérée ;
- le décommissionnement est sécurisé ;
- le recyclage est contrôlé ;
- le remplacement d’appareil est géré ;
- le stock d’appareils est suivi ;
- les affectations sont tracées ;
- les retours sont gérés ;
- les garanties sont suivies ;
- les périphériques sont supervisés ;
- les drivers sont versionnés ;
- les firmwares sont signés ;
- les tests post-mise à jour sont exécutés ;
- les TPE possèdent une version de secours ;
- les DAB peuvent revenir à une image sûre ;
- une Golden Image est disponible ;
- le support à distance est intégré ;
- les incidents sont liés aux versions ;
- les anomalies par version sont détectées ;
- les taux d’adoption sont calculés ;
- les tableaux de bord sont disponibles ;
- les alertes sont configurables ;
- le multi-pays est pris en charge ;
- le multi-organisation est pris en charge ;
- les politiques BYOD sont définies ;
- les appareils entièrement gérés sont contrôlés ;
- les rôles et permissions sont appliqués ;
- les approbations critiques sont protégées ;
- les audits sont immuables ;
- les tests couvrent les parcours essentiels.
