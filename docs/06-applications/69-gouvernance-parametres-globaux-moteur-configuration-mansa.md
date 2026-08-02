# 69 — Gouvernance, paramètres globaux et moteur de configuration Mansa

## 1. Objet du document

Ce document définit l'architecture officielle du **moteur de gouvernance et de configuration centralisée de Mansa**.

L'objectif est que **100 % des paramètres métier, techniques, financiers, réglementaires et fonctionnels** puissent être administrés sans modifier le code source.

Le moteur doit permettre :

- l'activation ou la désactivation de fonctionnalités ;
- la configuration des règles métier ;
- la gestion des pays ;
- la gestion des devises ;
- la gestion des commissions ;
- la gestion des plafonds ;
- la gestion des rôles ;
- la gestion des produits ;
- la gestion des partenaires ;
- la gestion des applications ;
- la gestion des API ;
- la gestion des services ;
- la gestion des workflows ;
- la gestion des notifications ;
- la gestion des campagnes ;
- la gestion des risques ;
- la gestion des paramètres de sécurité ;
- la gestion des paramètres IA ;
- la gestion des intégrations.

---

# 2. Principes

Le moteur doit être :

- centralisé ;
- sécurisé ;
- versionné ;
- auditable ;
- multi-pays ;
- multi-langues ;
- multi-devises ;
- hautement disponible ;
- extensible ;
- compatible avec tous les modules Mansa.

---

# 3. Paramètres globaux

Configuration de :

- nom commercial ;
- logo ;
- identité visuelle ;
- couleurs ;
- domaines ;
- URLs ;
- fuseaux horaires ;
- langues ;
- formats de date ;
- formats numériques ;
- formats monétaires ;
- unités de mesure.

---

# 4. Gestion des pays

Chaque pays possède sa configuration propre :

- devise ;
- langue ;
- fuseau horaire ;
- réglementation ;
- KYC ;
- KYB ;
- plafonds ;
- frais ;
- partenaires bancaires ;
- Mobile Money ;
- taxes ;
- services disponibles.

---

# 5. Activation des modules

Activation indépendante de :

- Cartes ;
- Wallet ;
- Mobile Money ;
- QR Payment ;
- NFC ;
- TPE ;
- GAB/DAB ;
- Agents ;
- Commerçants ;
- Bourses ;
- Paiement État ;
- Paiement scolaire ;
- Marketplace ;
- Jini IA ;
- Cashback ;
- Fidélité ;
- Coffres ;
- Cartes virtuelles ;
- Cartes jetables.

---

# 6. Paramètres financiers

Configuration de :

- frais ;
- commissions ;
- TVA ;
- minimum ;
- maximum ;
- arrondis ;
- partage des revenus ;
- remises ;
- promotions.

---

# 7. Paramètres de sécurité

Configuration de :

- MFA ;
- biométrie ;
- PIN ;
- durée des sessions ;
- verrouillage ;
- appareils autorisés ;
- géolocalisation ;
- chiffrement ;
- HSM ;
- clés ;
- certificats ;
- signatures.

---

# 8. Paramètres des utilisateurs

Gestion de :

- types de comptes ;
- limites ;
- KYC ;
- statut ;
- suspension ;
- clôture ;
- préférences ;
- langues ;
- notifications.

---

# 9. Paramètres des cartes

Configuration de :

- Visa ;
- Mastercard ;
- cartes virtuelles ;
- cartes physiques ;
- cartes premium ;
- cartes temporaires ;
- cartes jetables ;
- plafonds ;
- PIN ;
- activation.

---

# 10. Paramètres GAB/DAB

Configuration de :

- types de machines ;
- retrait ;
- dépôt ;
- consultation ;
- limites ;
- billets ;
- cassettes ;
- maintenance ;
- sécurité ;
- supervision.

---

# 11. Paramètres TPE

Gestion de :

- modèles ;
- firmware ;
- NFC ;
- QR ;
- imprimante ;
- mode hors ligne ;
- mises à jour ;
- terminaux.

---

# 12. Paramètres Mobile Money

Configuration de :

- opérateurs ;
- frais ;
- limites ;
- disponibilité ;
- délais ;
- commissions.

---

# 13. Paramètres IA

Gestion de Jini :

- modèles IA ;
- prompts ;
- langues ;
- restrictions ;
- historique ;
- confidentialité ;
- niveau d'autonomie.

---

# 14. Paramètres API

Configuration de :

- clés API ;
- quotas ;
- webhooks ;
- environnements ;
- Sandbox ;
- versions ;
- authentification.

---

# 15. Paramètres Notifications

Gestion de :

- SMS ;
- Email ;
- Push ;
- WhatsApp (si activé) ;
- modèles ;
- langues ;
- priorités ;
- horaires.

---

# 16. Paramètres Workflow

Configuration de :

- validations ;
- approbations ;
- escalades ;
- rappels ;
- délais ;
- SLA.

---

# 17. Paramètres de conformité

Gestion de :

- AML ;
- CFT ;
- sanctions ;
- PEP ;
- gel des avoirs ;
- conservation ;
- audit.

---

# 18. Journal des modifications

Toute modification doit enregistrer :

- utilisateur ;
- ancienne valeur ;
- nouvelle valeur ;
- date ;
- heure ;
- justification ;
- approbateur ;
- pays concerné.

---

# 19. Versionnement

Chaque changement de configuration est versionné et peut être restauré.

---

# 20. Critères d'acceptation

Le moteur est validé lorsque :

- toutes les configurations sont centralisées ;
- aucun changement fonctionnel ne nécessite une recompilation ;
- toutes les modifications sont historisées ;
- les paramètres sont multi-pays ;
- les paramètres sont sécurisés ;
- les restaurations fonctionnent ;
- les permissions sont respectées ;
- les audits sont complets.
