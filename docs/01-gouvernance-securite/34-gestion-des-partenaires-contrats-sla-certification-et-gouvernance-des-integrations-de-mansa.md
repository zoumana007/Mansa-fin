# 34 — Gestion des partenaires, contrats, SLA, certification et gouvernance des intégrations de Mansa

## 1. Objet du document

Ce document définit l’architecture officielle de gestion des partenaires de Mansa.

Il couvre :

- les banques ;
- les opérateurs Mobile Money ;
- les réseaux cartes ;
- les processeurs de paiement ;
- les fournisseurs KYC/KYB ;
- les prestataires AML ;
- les fournisseurs SMS, e-mail et Push ;
- les fournisseurs cloud ;
- les prestataires de sécurité ;
- les fabricants de cartes ;
- les fabricants et distributeurs de TPE ;
- les partenaires gouvernementaux ;
- les établissements publics ;
- les commerçants stratégiques ;
- les assureurs ;
- les fournisseurs de données ;
- les intégrateurs ;
- les partenaires API ;
- les contrats ;
- les SLA ;
- les certifications ;
- les habilitations ;
- les environnements ;
- les incidents ;
- les coûts ;
- les performances ;
- les renouvellements ;
- les audits ;
- la réversibilité ;
- la résiliation.

L’objectif est de garantir que chaque partenaire de Mansa soit :

- identifié ;
- évalué ;
- approuvé ;
- contractualisé ;
- sécurisé ;
- intégré de manière contrôlée ;
- surveillé ;
- auditable ;
- remplaçable lorsque possible ;
- conforme aux exigences du pays ;
- suivi pendant toute la durée de la relation.

---

# 2. Principes fondamentaux

## 2.1 Aucun partenaire critique sans évaluation préalable

Avant toute intégration en production, Mansa doit évaluer :

- l’identité du partenaire ;
- sa capacité juridique ;
- sa situation financière ;
- ses licences ;
- ses agréments ;
- sa sécurité ;
- sa conformité ;
- sa disponibilité ;
- son historique ;
- ses sous-traitants ;
- ses pays d’activité ;
- ses capacités techniques ;
- ses coûts ;
- son plan de continuité.

---

## 2.2 Aucun échange de données sans contrat adapté

Un partenaire ne doit recevoir des données que si les documents nécessaires existent.

Selon le cas :

- contrat principal ;
- annexe technique ;
- accord de confidentialité ;
- accord de traitement des données ;
- SLA ;
- annexe sécurité ;
- annexe tarifaire ;
- annexe pays ;
- mandat ;
- certification ;
- autorisation réglementaire.

---

## 2.3 Les responsabilités doivent être explicites

Pour chaque service, le contrat doit préciser qui est responsable de :

- l’authentification ;
- l’autorisation ;
- la sécurité ;
- la disponibilité ;
- les données ;
- les fraudes ;
- les remboursements ;
- les rapprochements ;
- les incidents ;
- les réclamations ;
- les notifications ;
- les déclarations ;
- les pertes ;
- les audits ;
- la conservation.

---

## 2.4 Les performances doivent être mesurées

Les engagements d’un partenaire doivent être suivis avec des indicateurs objectifs.

Exemples :

- disponibilité ;
- latence ;
- taux de succès ;
- taux de refus ;
- taux d’erreur ;
- délai de confirmation ;
- délai de règlement ;
- délai de support ;
- délai de résolution ;
- délai de rapprochement.

---

## 2.5 La dépendance doit être maîtrisée

Mansa doit éviter qu’un partenaire unique devienne impossible à remplacer.

Il faut prévoir lorsque possible :

- une interface standard ;
- un second fournisseur ;
- un plan de sortie ;
- une exportation des données ;
- une période de transition ;
- une documentation ;
- un environnement de test ;
- des contrats de réversibilité.

---

# 3. Catégories de partenaires

## 3.1 Partenaires bancaires

Ils peuvent fournir :

- comptes de cantonnement ;
- comptes de règlement ;
- virements ;
- IBAN ou équivalent ;
- émission de cartes ;
- BIN sponsorship ;
- accès au réseau bancaire ;
- trésorerie ;
- change ;
- rapprochement.

---

## 3.2 Opérateurs Mobile Money

Ils peuvent fournir :

- cash-in ;
- cash-out ;
- transfert ;
- paiement ;
- collecte ;
- décaissement ;
- wallet externe ;
- confirmation ;
- règlement.

---

## 3.3 Réseaux cartes

Exemples :

- Visa ;
- Mastercard ;
- réseaux locaux ou régionaux.

Ils peuvent couvrir :

- autorisation ;
- compensation ;
- règlement ;
- tokenisation ;
- 3-D Secure ;
- cartes virtuelles ;
- wallets mobiles ;
- chargebacks ;
- certification.

---

## 3.4 Processeurs de paiement

Ils peuvent gérer :

- émission ;
- acquisition ;
- autorisation ;
- personnalisation ;
- tokenisation ;
- prévention fraude ;
- settlement ;
- reporting.

---

## 3.5 Partenaires KYC/KYB

Ils peuvent fournir :

- OCR ;
- vérification documentaire ;
- selfie ;
- preuve de vie ;
- comparaison faciale ;
- vérification d’entreprise ;
- bénéficiaires effectifs ;
- contrôle de registre.

---

## 3.6 Partenaires AML

Ils peuvent fournir :

- sanctions ;
- PEP ;
- adverse media ;
- listes de surveillance ;
- screening continu ;
- scoring ;
- surveillance.

---

## 3.7 Fournisseurs de communication

Catégories :

- SMS ;
- e-mail ;
- Push ;
- WhatsApp lorsque autorisé ;
- appels vocaux ;
- courrier.

---

## 3.8 Fournisseurs techniques

Exemples :

- cloud ;
- stockage ;
- CDN ;
- monitoring ;
- cybersécurité ;
- sauvegarde ;
- gestion des secrets ;
- cartographie ;
- IA ;
- OCR ;
- signature électronique.

---

## 3.9 Partenaires matériels

Exemples :

- fabricants de cartes ;
- imprimeurs ;
- fabricants de puces ;
- fabricants de TPE ;
- distributeurs ;
- mainteneurs ;
- transporteurs ;
- centres de personnalisation.

---

## 3.10 Partenaires gouvernementaux et institutionnels

Exemples :

- ministères ;
- collectivités ;
- universités ;
- écoles ;
- police ;
- douanes ;
- impôts ;
- bourses ;
- organismes sociaux ;
- entreprises publiques.

---

# 4. Cycle de vie d’un partenaire

Étapes officielles :

1. identification ;
2. qualification ;
3. évaluation ;
4. sélection ;
5. négociation ;
6. approbation ;
7. contractualisation ;
8. intégration technique ;
9. certification ;
10. recette ;
11. mise en production ;
12. surveillance ;
13. revue périodique ;
14. renouvellement ;
15. suspension ;
16. résiliation ;
17. sortie ;
18. archivage.

---

# 5. Fiche partenaire

Chaque partenaire doit avoir une fiche contenant :

- identifiant ;
- raison sociale ;
- nom commercial ;
- pays ;
- adresse ;
- registre ;
- numéro fiscal ;
- licence ;
- agrément ;
- catégorie ;
- services ;
- contacts ;
- responsable Mansa ;
- niveau de criticité ;
- niveau de risque ;
- environnements ;
- contrats ;
- sous-traitants ;
- certifications ;
- incidents ;
- performances ;
- coûts ;
- date de revue ;
- statut.

---

# 6. Statuts partenaire

Valeurs possibles :

- PROSPECT ;
- UNDER_REVIEW ;
- QUALIFIED ;
- NEGOTIATION ;
- APPROVAL_PENDING ;
- APPROVED ;
- INTEGRATION ;
- CERTIFICATION ;
- PILOT ;
- ACTIVE ;
- LIMITED ;
- SUSPENDED ;
- TERMINATION_PENDING ;
- TERMINATED ;
- ARCHIVED ;
- REJECTED.

---

# 7. Qualification

La qualification doit vérifier :

- adéquation au besoin ;
- pays couverts ;
- services couverts ;
- capacité technique ;
- disponibilité ;
- capacité financière ;
- conformité ;
- réputation ;
- délais ;
- coûts ;
- support ;
- scalabilité.

---

# 8. Due diligence

La due diligence peut inclure :

- identité juridique ;
- dirigeants ;
- bénéficiaires effectifs ;
- structure capitalistique ;
- sanctions ;
- PEP ;
- litiges ;
- incidents ;
- audit financier ;
- certifications ;
- sécurité ;
- continuité ;
- assurances ;
- sous-traitants ;
- licences ;
- autorisations.

---

# 9. Niveau de criticité

## 9.1 Critique

Une panne bloque :

- les paiements ;
- les soldes ;
- les cartes ;
- les retraits ;
- les règlements ;
- la conformité ;
- l’accès principal.

## 9.2 Élevé

Une panne dégrade fortement :

- l’onboarding ;
- les notifications de sécurité ;
- les TPE ;
- le support ;
- le rapprochement.

## 9.3 Modéré

Une panne affecte un service secondaire.

## 9.4 Faible

Une panne a peu d’impact immédiat.

---

# 10. Score de risque partenaire

Facteurs possibles :

- pays ;
- service ;
- données ;
- accès ;
- criticité ;
- stabilité financière ;
- sécurité ;
- historique ;
- dépendance ;
- sous-traitance ;
- conformité ;
- capacité de reprise ;
- concentration ;
- incidents.

---

# 11. Catégories de risque

- LOW ;
- MEDIUM ;
- HIGH ;
- CRITICAL ;
- PROHIBITED.

Le score doit être :

- versionné ;
- explicable ;
- daté ;
- approuvé ;
- revu périodiquement.

---

# 12. Sélection

La sélection doit comparer :

- fonctionnalités ;
- intégration ;
- sécurité ;
- conformité ;
- coûts ;
- SLA ;
- couverture pays ;
- expérience ;
- certifications ;
- support ;
- évolutivité ;
- réversibilité.

---

# 13. Appel d’offres

Pour les partenaires importants, Mansa peut utiliser :

- cahier des charges ;
- grille d’évaluation ;
- démonstration ;
- questionnaire sécurité ;
- questionnaire conformité ;
- test technique ;
- test financier ;
- phase pilote ;
- validation juridique.

---

# 14. Matrice de décision

Exemple de critères :

- sécurité ;
- conformité ;
- performance ;
- disponibilité ;
- coût ;
- couverture ;
- intégration ;
- support ;
- expérience ;
- continuité ;
- réversibilité.

Chaque critère peut avoir un poids.

---

# 15. Contrat principal

Le contrat doit préciser :

- parties ;
- objet ;
- durée ;
- territoire ;
- services ;
- responsabilités ;
- coûts ;
- données ;
- sécurité ;
- conformité ;
- SLA ;
- support ;
- audit ;
- incidents ;
- sous-traitance ;
- propriété intellectuelle ;
- confidentialité ;
- résiliation ;
- réversibilité ;
- droit applicable.

---

# 16. Annexes contractuelles

Annexes possibles :

- annexe technique ;
- annexe sécurité ;
- annexe données ;
- annexe SLA ;
- annexe tarifaire ;
- annexe pays ;
- annexe support ;
- annexe de réversibilité ;
- plan de continuité ;
- matrice de responsabilités ;
- catalogue de services ;
- procédure d’incident.

---

# 17. Matrice RACI

Pour chaque processus, préciser qui est :

- Responsible ;
- Accountable ;
- Consulted ;
- Informed.

Processus concernés :

- intégration ;
- incident ;
- rapprochement ;
- fraude ;
- chargeback ;
- support ;
- changement ;
- certification ;
- migration ;
- résiliation.

---

# 18. SLA

Le SLA doit définir des engagements mesurables.

Exemples :

- disponibilité mensuelle ;
- latence maximale ;
- taux de succès ;
- temps de prise en charge ;
- temps de résolution ;
- délai de règlement ;
- délai de transmission de fichier ;
- délai de correction ;
- fenêtre de maintenance.

---

# 19. Disponibilité

Exemple :

```text
Disponibilité mensuelle : 99,9 %
```

La méthode de calcul doit préciser :

- période ;
- exclusions ;
- maintenance ;
- incidents externes ;
- source de mesure ;
- fuseau ;
- arrondi ;
- seuil.

---

# 20. Latence

Les engagements peuvent utiliser :

- moyenne ;
- p95 ;
- p99 ;
- délai maximal ;
- temps de webhook ;
- temps de confirmation ;
- temps de réponse API.

---

# 21. Taux de succès

Le SLA doit distinguer :

- succès technique ;
- succès métier ;
- refus légitime ;
- timeout ;
- statut inconnu ;
- erreur partenaire ;
- erreur Mansa ;
- erreur utilisateur.

---

# 22. Incidents

Niveaux possibles :

- P1 critique ;
- P2 majeur ;
- P3 modéré ;
- P4 mineur.

Chaque niveau doit avoir :

- délai de prise en charge ;
- fréquence de communication ;
- délai cible de résolution ;
- équipe ;
- escalade ;
- rapport final.

---

# 23. Exemple de SLA incident

```text
P1 :
- prise en charge : 15 minutes ;
- communication : toutes les 30 minutes ;
- résolution cible : 2 heures.
```

Les valeurs définitives dépendent du contrat.

---

# 24. Maintenance

Le partenaire doit préciser :

- fenêtres planifiées ;
- préavis ;
- durée ;
- impact ;
- services concernés ;
- solution de contournement ;
- notification ;
- maintenance urgente.

---

# 25. Pénalités SLA

Les pénalités peuvent prendre la forme de :

- avoir ;
- remboursement ;
- crédit de service ;
- réduction ;
- pénalité financière ;
- plan correctif ;
- droit de résiliation.

---

# 26. Plafond de pénalité

Le contrat doit préciser :

- plafond mensuel ;
- plafond annuel ;
- cumul ;
- exclusions ;
- procédure de réclamation ;
- justificatifs ;
- délai de paiement.

---

# 27. Performance réelle

Mansa doit mesurer indépendamment :

- disponibilité ;
- latence ;
- erreurs ;
- statuts inconnus ;
- retries ;
- incidents ;
- taux de règlement ;
- divergences ;
- tickets ;
- délais.

---

# 28. Service Level Indicator

Exemples :

```text
partner_availability_rate
partner_api_latency_p95
partner_success_rate
partner_webhook_delay
partner_reconciliation_delay
partner_incident_resolution_time
```

---

# 29. Service Level Objective

Chaque SLI peut avoir un objectif interne plus strict que le SLA contractuel.

---

# 30. Error Budget

Un partenaire peut disposer d’un budget d’erreur.

Lorsque ce budget est consommé :

- revue ;
- plan d’action ;
- limitation ;
- bascule ;
- suspension de changement ;
- pénalité ;
- escalade.

---

# 31. Certification technique

Avant production, le partenaire peut devoir valider :

- authentification ;
- chiffrement ;
- certificats ;
- API ;
- webhooks ;
- idempotence ;
- erreurs ;
- charge ;
- sécurité ;
- rapprochement ;
- reprise ;
- conformité.

---

# 32. Certification réseau carte

Elle peut inclure :

- certification processeur ;
- certification TPE ;
- EMV ;
- sans contact ;
- 3-D Secure ;
- tokenisation ;
- personnalisation ;
- gestion des clés ;
- sécurité PIN ;
- conformité PCI.

---

# 33. Certification TPE

Elle peut inclure :

- matériel ;
- firmware ;
- application ;
- NFC ;
- puce ;
- imprimante ;
- sécurité ;
- clés ;
- mises à jour ;
- réseau ;
- mode hors ligne ;
- gestion distante.

---

# 34. Certification sécurité

Le partenaire peut devoir fournir :

- rapport d’audit ;
- test d’intrusion ;
- politique sécurité ;
- certifications ;
- gestion des vulnérabilités ;
- plan d’incident ;
- plan de continuité ;
- preuve de chiffrement ;
- gestion des accès.

---

# 35. Certifications possibles

Selon le service :

- PCI DSS ;
- ISO 27001 ;
- SOC 2 ;
- EMVCo ;
- certifications réseau carte ;
- certifications locales ;
- homologations publiques ;
- certifications de signature ;
- certifications cloud.

La liste doit rester configurable.

---

# 36. Validité des certifications

Chaque certification doit contenir :

- nom ;
- organisme ;
- périmètre ;
- numéro ;
- date de début ;
- date d’expiration ;
- document ;
- statut ;
- restrictions ;
- date de contrôle.

---

# 37. Expiration de certification

Avant expiration, le système doit :

- alerter ;
- demander un renouvellement ;
- vérifier la nouvelle preuve ;
- limiter si nécessaire ;
- suspendre si obligatoire ;
- auditer la décision.

---

# 38. Environnements partenaire

Chaque partenaire doit avoir des environnements clairement séparés :

- Sandbox ;
- Test ;
- Recette ;
- Préproduction ;
- Production.

---

# 39. Données par environnement

Les environnements hors production doivent utiliser :

- données fictives ;
- références de test ;
- cartes de test ;
- faux utilisateurs ;
- faux montants ;
- webhooks de test ;
- secrets distincts.

---

# 40. Passage en production

Le passage en production doit exiger :

- contrat actif ;
- sécurité validée ;
- conformité validée ;
- tests réussis ;
- certification réussie ;
- SLA validé ;
- support opérationnel ;
- secrets production ;
- rapprochement testé ;
- rollback ;
- approbation.

---

# 41. Checklist de production

Exemples :

- endpoint production ;
- DNS ;
- certificats ;
- clé API ;
- IP autorisées ;
- mTLS ;
- webhooks ;
- timeout ;
- retry ;
- circuit breaker ;
- monitoring ;
- alertes ;
- contacts ;
- runbook ;
- plan de reprise.

---

# 42. Pilote

Avant généralisation, Mansa peut lancer un pilote limité par :

- nombre d’utilisateurs ;
- nombre de commerçants ;
- zone ;
- montant ;
- pays ;
- type de transaction ;
- durée ;
- canal.

---

# 43. Critères de sortie du pilote

Le pilote est validé lorsque :

- taux de succès atteint ;
- incidents maîtrisés ;
- support prêt ;
- rapprochement exact ;
- conformité validée ;
- coûts confirmés ;
- performances acceptables ;
- utilisateurs satisfaits ;
- sécurité validée.

---

# 44. Gouvernance opérationnelle

Chaque partenaire critique doit avoir :

- responsable Mansa ;
- responsable partenaire ;
- contact technique ;
- contact opérationnel ;
- contact sécurité ;
- contact conformité ;
- contact finance ;
- contact incident ;
- comité de suivi.

---

# 45. Comité partenaire

Le comité peut suivre :

- volumes ;
- incidents ;
- SLA ;
- coûts ;
- changements ;
- roadmap ;
- sécurité ;
- conformité ;
- rapprochement ;
- support ;
- actions.

---

# 46. Fréquence des revues

Exemples :

- hebdomadaire pendant l’intégration ;
- mensuelle en production ;
- trimestrielle pour la performance ;
- annuelle pour la due diligence ;
- immédiate après incident critique.

---

# 47. Revue périodique

Elle doit vérifier :

- contrat ;
- certification ;
- performance ;
- risque ;
- sécurité ;
- sous-traitants ;
- coûts ;
- incidents ;
- continuité ;
- satisfaction ;
- plan de sortie ;
- conformité.

---

# 48. Changements partenaire

Un changement peut concerner :

- API ;
- certificat ;
- endpoint ;
- tarif ;
- contrat ;
- sous-traitant ;
- région ;
- sécurité ;
- processus ;
- version ;
- produit ;
- réglementation.

---

# 49. Notification de changement

Le contrat doit prévoir un délai de notification avant :

- changement incompatible ;
- retrait d’API ;
- modification tarifaire ;
- changement de sous-traitant ;
- changement d’hébergement ;
- modification de sécurité ;
- arrêt de service.

---

# 50. Change Management

Chaque changement doit contenir :

- description ;
- impact ;
- urgence ;
- version ;
- environnement ;
- plan de test ;
- date ;
- rollback ;
- approbation ;
- communication.

---

# 51. Dépréciation d’API

Le partenaire doit fournir :

- date d’annonce ;
- ancienne version ;
- nouvelle version ;
- documentation ;
- période de coexistence ;
- date de retrait ;
- support ;
- environnement de test.

---

# 52. Incidents partenaire

Un incident partenaire doit créer :

- identifiant ;
- partenaire ;
- service ;
- gravité ;
- début ;
- impact ;
- statut ;
- communications ;
- actions ;
- résolution ;
- perte ;
- SLA ;
- rapport final.

---

# 53. Communication d’incident

Le partenaire doit fournir :

- heure de détection ;
- service concerné ;
- impact ;
- cause probable ;
- mesure temporaire ;
- prochaine mise à jour ;
- heure estimée de résolution.

---

# 54. Escalade

Niveaux d’escalade possibles :

1. support technique ;
2. responsable opérationnel ;
3. responsable de compte ;
4. direction technique ;
5. direction générale ;
6. juridique ou conformité.

---

# 55. Post-mortem

Après un incident majeur, le partenaire doit fournir :

- chronologie ;
- cause racine ;
- impact ;
- détection ;
- réponse ;
- résolution ;
- actions correctives ;
- échéances ;
- responsables ;
- prévention.

---

# 56. Sécurité des partenaires

Chaque partenaire doit appliquer :

- chiffrement ;
- contrôle d’accès ;
- MFA ;
- journalisation ;
- séparation des environnements ;
- rotation des secrets ;
- gestion des vulnérabilités ;
- réponse à incident ;
- sauvegardes ;
- continuité.

---

# 57. Accès partenaire à Mansa

Un partenaire peut recevoir :

- API key ;
- certificat ;
- compte de service ;
- accès portail ;
- accès limité ;
- environnement dédié.

L’accès doit être :

- limité ;
- expirant ;
- révocable ;
- audité ;
- rattaché à une organisation.

---

# 58. Accès de support partenaire

L’accès exceptionnel doit contenir :

- demande ;
- motif ;
- périmètre ;
- durée ;
- approbateur ;
- supervision ;
- journalisation ;
- révocation.

---

# 59. Sous-traitants du partenaire

Le partenaire doit déclarer :

- nom ;
- service ;
- pays ;
- données ;
- criticité ;
- contrat ;
- certification ;
- date d’entrée ;
- date de sortie.

---

# 60. Changement de sous-traitant

Selon le contrat, Mansa peut :

- être informée ;
- s’opposer ;
- demander des garanties ;
- limiter ;
- résilier ;
- exiger une nouvelle revue.

---

# 61. Données partagées

Chaque intégration doit documenter :

- champs ;
- finalité ;
- fréquence ;
- direction ;
- pays ;
- durée ;
- sécurité ;
- conservation ;
- suppression ;
- sous-traitants ;
- base de traitement.

---

# 62. Minimisation

Le partenaire ne reçoit que les données nécessaires.

Exemples :

- token plutôt que numéro complet ;
- identifiant plutôt que document ;
- montant et référence plutôt que profil complet ;
- résultat KYC plutôt que toutes les pièces.

---

# 63. Localisation des données

Le contrat doit préciser :

- pays d’hébergement ;
- régions ;
- réplication ;
- sauvegardes ;
- support ;
- transferts ;
- sous-traitants ;
- accès internationaux.

---

# 64. Notification de violation

Le partenaire doit notifier Mansa selon un délai contractuel.

La notification doit contenir :

- date ;
- nature ;
- données ;
- personnes ;
- pays ;
- cause ;
- mesures ;
- impact ;
- plan ;
- contacts.

---

# 65. Audit partenaire

Mansa doit pouvoir :

- demander des preuves ;
- consulter des rapports ;
- réaliser un audit ;
- mandater un tiers ;
- demander un plan correctif ;
- vérifier la résolution.

---

# 66. Questionnaire de contrôle

Il peut couvrir :

- gouvernance ;
- sécurité ;
- données ;
- continuité ;
- incidents ;
- conformité ;
- sous-traitants ;
- accès ;
- sauvegardes ;
- certifications ;
- personnel ;
- développement.

---

# 67. Non-conformité

Une non-conformité doit avoir :

- description ;
- gravité ;
- preuve ;
- responsable ;
- plan correctif ;
- échéance ;
- statut ;
- validation ;
- escalade.

---

# 68. Plan correctif

Étapes possibles :

1. analyse ;
2. action immédiate ;
3. correction ;
4. test ;
5. preuve ;
6. validation ;
7. clôture ;
8. suivi.

---

# 69. Suspension partenaire

La suspension peut concerner :

- toutes les opérations ;
- un produit ;
- un pays ;
- un endpoint ;
- un canal ;
- un environnement ;
- de nouveaux utilisateurs ;
- des montants élevés.

---

# 70. Motifs de suspension

Exemples :

- incident critique ;
- certification expirée ;
- faille ;
- fraude ;
- violation contractuelle ;
- rapprochement incorrect ;
- indisponibilité prolongée ;
- autorisation réglementaire retirée ;
- défaut de paiement ;
- sous-traitant non déclaré.

---

# 71. Mode dégradé

En cas de problème partenaire, Mansa peut :

- basculer vers un autre fournisseur ;
- mettre en attente ;
- limiter les montants ;
- désactiver un canal ;
- autoriser seulement la consultation ;
- informer les utilisateurs ;
- déclencher un rapprochement renforcé.

---

# 72. Stratégie de fallback

Pour chaque partenaire critique, définir :

- fournisseur secondaire ;
- processus manuel ;
- mode dégradé ;
- délai ;
- capacité ;
- coût ;
- limites ;
- activation ;
- retour à la normale.

---

# 73. Concentration

Mansa doit surveiller :

- part du volume ;
- part du revenu ;
- part des données ;
- nombre de services ;
- nombre de pays ;
- dépendance technique ;
- dépendance réglementaire.

---

# 74. Risque de concentration

Une trop forte dépendance peut déclencher :

- plan de diversification ;
- second fournisseur ;
- négociation ;
- architecture multi-connecteur ;
- limite de volume ;
- plan de sortie.

---

# 75. Tarification partenaire

La fiche tarifaire doit contenir :

- frais fixes ;
- frais variables ;
- minimum ;
- paliers ;
- devise ;
- taxes ;
- frais d’installation ;
- frais de certification ;
- frais de support ;
- pénalités ;
- indexation ;
- date d’effet.

---

# 76. Vérification des factures

Les factures partenaires doivent être comparées avec :

- volumes internes ;
- transactions ;
- tarifs ;
- SLA ;
- avoirs ;
- pénalités ;
- taxes ;
- devises ;
- périodes ;
- environnements.

---

# 77. Règlements partenaires

Le système doit suivre :

- facture ;
- échéance ;
- validation ;
- devise ;
- taux ;
- paiement ;
- statut ;
- litige ;
- avoir ;
- retenue ;
- pénalité.

---

# 78. Réconciliation partenaire

Le rapprochement doit comparer :

- opérations Mansa ;
- opérations partenaire ;
- montants ;
- statuts ;
- frais ;
- commissions ;
- règlements ;
- références ;
- dates ;
- devises.

---

# 79. Divergence

Une divergence peut être :

- opération manquante ;
- opération dupliquée ;
- montant différent ;
- statut différent ;
- frais incorrect ;
- règlement manquant ;
- devise incorrecte ;
- date incorrecte.

---

# 80. Litige partenaire

Un litige doit contenir :

- référence ;
- contrat ;
- période ;
- service ;
- montant ;
- motif ;
- preuve ;
- responsable ;
- statut ;
- réponse ;
- résolution ;
- impact.

---

# 81. Renouvellement

Le renouvellement doit vérifier :

- performance ;
- incidents ;
- coûts ;
- besoin ;
- risque ;
- conformité ;
- certifications ;
- satisfaction ;
- alternatives ;
- clauses ;
- durée.

---

# 82. Alertes d’expiration

Le système doit alerter avant :

- contrat ;
- certification ;
- assurance ;
- licence ;
- certificat technique ;
- clé ;
- agrément ;
- SLA ;
- mandat.

---

# 83. Résiliation

La résiliation doit suivre un workflow :

1. décision ;
2. validation ;
3. notification ;
4. plan de transition ;
5. arrêt des nouveaux flux ;
6. migration ;
7. rapprochement final ;
8. révocation des accès ;
9. restitution ou suppression des données ;
10. archivage ;
11. clôture.

---

# 84. Plan de sortie

Il doit prévoir :

- export des données ;
- format ;
- délai ;
- assistance ;
- migration ;
- continuité ;
- coûts ;
- destruction ;
- certificats ;
- équipements ;
- comptes ;
- secrets ;
- documentation.

---

# 85. Réversibilité

Le partenaire doit permettre lorsque nécessaire :

- récupération des données ;
- récupération des historiques ;
- transfert des configurations ;
- assistance au changement ;
- maintien temporaire ;
- compatibilité ;
- documentation.

---

# 86. Restitution du matériel

Pour les TPE ou cartes :

- inventaire ;
- collecte ;
- effacement ;
- désactivation ;
- vérification ;
- transport ;
- destruction ;
- certificat.

---

# 87. Suppression des données

Après résiliation, le partenaire doit :

- supprimer ;
- anonymiser ;
- archiver uniquement si autorisé ;
- fournir une preuve ;
- respecter les legal holds ;
- traiter les sauvegardes selon la politique.

---

# 88. Administration

Le portail Admin doit permettre :

- créer une fiche partenaire ;
- qualifier ;
- évaluer ;
- gérer le risque ;
- suivre les contrats ;
- suivre les SLA ;
- suivre les certifications ;
- suivre les incidents ;
- suivre les coûts ;
- suivre les audits ;
- suivre les changements ;
- suspendre ;
- résilier ;
- consulter l’historique.

---

# 89. Permissions

Exemples :

```text
partner.read
partner.create
partner.update
partner.approve
partner.risk.read
partner.risk.manage
partner.contract.read
partner.contract.manage
partner.sla.read
partner.sla.manage
partner.certification.read
partner.certification.manage
partner.incident.read
partner.incident.manage
partner.audit.read
partner.audit.manage
partner.suspend
partner.terminate
partner.cost.read
partner.cost.manage
partner.access.manage
```

---

# 90. Actions critiques

Doivent être particulièrement protégées :

- activation en production ;
- approbation d’un partenaire critique ;
- modification du SLA ;
- ajout de secrets ;
- accès production ;
- suspension ;
- résiliation ;
- modification tarifaire ;
- changement de sous-traitant ;
- suppression d’une preuve ;
- validation d’une non-conformité critique.

---

# 91. Double validation

Peut être exigée pour :

- partenaire bancaire ;
- réseau carte ;
- partenaire État ;
- fournisseur KYC principal ;
- activation production ;
- changement majeur de contrat ;
- dérogation sécurité ;
- suspension ;
- résiliation ;
- accès d’urgence ;
- renouvellement d’un partenaire critique.

---

# 92. API

Exemples :

```http
GET    /partners
POST   /partners
GET    /partners/{id}
PATCH  /partners/{id}

POST   /partners/{id}/qualify
POST   /partners/{id}/approve
POST   /partners/{id}/activate
POST   /partners/{id}/suspend
POST   /partners/{id}/terminate

GET    /partners/{id}/contracts
GET    /partners/{id}/sla
GET    /partners/{id}/certifications
GET    /partners/{id}/incidents
GET    /partners/{id}/performance
GET    /partners/{id}/costs
GET    /partners/{id}/audits

POST   /partners/{id}/reviews
POST   /partners/{id}/corrective-actions
```

---

# 93. Modèles

- Partner
- PartnerCategory
- PartnerContact
- PartnerCountry
- PartnerCapability
- PartnerRiskAssessment
- PartnerDueDiligence
- PartnerApproval
- PartnerContract
- PartnerContractVersion
- PartnerSla
- PartnerSli
- PartnerSlo
- PartnerCertification
- PartnerEnvironment
- PartnerCredentialReference
- PartnerIncident
- PartnerPerformanceMetric
- PartnerAudit
- PartnerFinding
- PartnerCorrectiveAction
- PartnerCost
- PartnerInvoice
- PartnerReconciliation
- PartnerChange
- PartnerTermination
- PartnerExitPlan
- PartnerSubprocessor
- PartnerAccess
- PartnerReview

---

# 94. Règles métier

1. Tout partenaire possède une fiche officielle.
2. Tout partenaire critique passe par une due diligence.
3. Tout partenaire possède un niveau de risque.
4. Aucun partenaire critique n’accède à la production sans approbation.
5. Les contrats sont versionnés.
6. Les SLA sont mesurables.
7. Les performances sont surveillées indépendamment.
8. Les certifications ont une date d’expiration.
9. Les accès sont individuels ou liés à un compte de service.
10. Les secrets sont séparés par environnement.
11. Les environnements sont isolés.
12. Les données partagées sont minimisées.
13. Les sous-traitants sont déclarés.
14. Les changements majeurs sont notifiés.
15. Les incidents sont enregistrés.
16. Les incidents critiques produisent un post-mortem.
17. Les non-conformités ont un plan correctif.
18. Les factures sont rapprochées des volumes.
19. Les contrats sont revus avant renouvellement.
20. Les partenaires critiques ont un plan de continuité.
21. Les risques de concentration sont surveillés.
22. Les suspensions sont proportionnées.
23. Les résiliations incluent un plan de sortie.
24. Les accès sont révoqués après fin de contrat.
25. Les données sont restituées ou supprimées selon la politique.

---

# 95. Analytics

Événements possibles :

```text
partner_created
partner_due_diligence_started
partner_due_diligence_completed
partner_risk_assessed
partner_approved
partner_contract_signed
partner_certification_started
partner_certification_completed
partner_activated
partner_sla_breached
partner_incident_created
partner_incident_resolved
partner_corrective_action_created
partner_audit_completed
partner_certification_expiring
partner_contract_expiring
partner_suspended
partner_reactivated
partner_terminated
partner_exit_completed
```

---

# 96. Tests

- tests de création partenaire ;
- tests de qualification ;
- tests de due diligence ;
- tests de scoring ;
- tests d’approbation ;
- tests de contrats ;
- tests de versions ;
- tests SLA ;
- tests SLI ;
- tests de pénalités ;
- tests de certification ;
- tests d’expiration ;
- tests d’environnement ;
- tests d’accès ;
- tests de sous-traitants ;
- tests d’incident ;
- tests d’escalade ;
- tests de post-mortem ;
- tests de coûts ;
- tests de rapprochement ;
- tests de suspension ;
- tests de résiliation ;
- tests de réversibilité ;
- tests de permissions ;
- tests de double validation ;
- tests d’audit.

---

# 97. Critères d’acceptation

La gestion des partenaires est validée lorsque :

- tous les partenaires sont inventoriés ;
- les catégories sont définies ;
- les partenaires critiques sont évalués ;
- les risques sont documentés ;
- les contrats sont versionnés ;
- les SLA sont mesurables ;
- les performances sont suivies ;
- les certifications sont enregistrées ;
- les expirations génèrent des alertes ;
- les environnements sont séparés ;
- les accès sont protégés ;
- les sous-traitants sont documentés ;
- les incidents sont tracés ;
- les plans correctifs sont suivis ;
- les coûts sont rapprochés ;
- les partenaires sont revus périodiquement ;
- les suspensions sont contrôlées ;
- les résiliations disposent d’un plan de sortie ;
- les données sont restituées ou supprimées ;
- les actions critiques sont auditées ;
- les tests couvrent les principaux scénarios.