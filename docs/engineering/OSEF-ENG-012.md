# OSEF-ENG-012 — Twelve-Factor Engineering Standard

**Statut : proposition de standard transversal (v0.1) — pilote, en attente d'adoption par la gouvernance OSEF.**  
**Périmètre :** applications et API, blueprints de déploiement, plateformes à composants persistants, labs, services proposés aux ESN et cloud providers.

## Objectif
Prouver qu'une technologie Open Source peut être **déployée, configurée, sécurisée, exploitée, maintenue et transmise**. Les douze facteurs sont un cadre de revue, pas une certification ni une garantie de production.

Référence primaire : [The Twelve-Factor App](https://12factor.net/).

## Obligations des ingénieurs
1. Lire le standard avant de contribuer à un projet pilote.
2. Renseigner la matrice `docs/engineering/TWELVE-FACTOR-COMPLIANCE.md` du dépôt, pour les facteurs concernés par la PR.
3. Fournir la **preuve vérifiable** (test, commande et résultat, fichier, rapport, capture anonymisée) ; ne jamais cocher une preuve non exécutée.
4. Distinguer **Conforme (C)**, **Non conforme (NC)**, **Non applicable (NA)** ; justifier chaque NA. Les NC doivent ouvrir une issue corrective avec propriétaire et échéance proposée.
5. Faire relire par un pair ; tout risque important, modification de production ou dérogation nécessite l'avis du responsable Engineering & Delivery et du référent sécurité si concerné.
6. Ne jamais publier secrets, données clients ni journaux sensibles ; ne jamais modifier manuellement un environnement administré en contournant la PR.

## Les 12 facteurs : grille de référence OSEF
| # | Facteur | Contrôle OSEF et preuve attendue |
|---|---|---|
| 01 | Codebase | Code, manifests et IaC versionnés ; lien commit/PR |
| 02 | Dependencies | Dépendances déclarées, versions ou digests identifiés ; SBOM si approprié |
| 03 | Config | Séparation configuration/code, secret manager ; exemple sans secrets |
| 04 | Backing services | DB, cache, stockage, queue déclarés et remplaçables/configurables selon architecture |
| 05 | Build, release, run | Étapes distinctes, artefacts traçables, versions et procédure de promotion |
| 06 | Processes | Processus applicatifs sans état local persistant ; composants stateful explicitement qualifiés |
| 07 | Port binding | Interfaces et ports explicites, limites d'exposition vérifiées |
| 08 | Concurrency | Scalabilité/concurrence testée ou limitation de capacité explicitée |
| 09 | Disposability | Démarrage, arrêt gracieux, redémarrage et reprise testés |
| 10 | Dev/prod parity | Écarts lab/préproduction/production listés ; pas de parité présumée |
| 11 | Logs | Flux et collecte de logs ; masquage des secrets et données personnelles |
| 12 | Admin processes | Migrations, maintenance, sauvegardes, procédures d'administration exécutables et traçables |

## Adaptations obligatoires
- **Applications/API** : appliquer le facteur dans son sens original quand pertinent.
- **Stacks intégrées (Nextcloud, ONLYOFFICE, BlueMind, Tazama, PostgreSQL, etc.)** : ne pas réécrire des logiciels tiers pour forcer le stateless ; spécifier stockage, services stateful, sauvegardes, restore, upgrade/rollback et responsabilités.
- **Labs** : être reproductible et séparer démo/métier/meetup ; ne pas prétendre à une validation de production.
- **Cloud/ESN** : documenter les responsabilités provider / client / OSEF, isolation client, mises à jour, réversibilité et niveaux de service **uniquement s'ils sont contractés**.

## Contrôle par Pull Request
- Modèle de PR : matrice à jour, preuves et risques explicités.
- CI : vérifie la présence/structure de la matrice et quelques règles mécaniques ; **elle ne démontre pas la conformité architecturale**.
- Revue humaine : évalue les preuves, l'applicabilité et les risques.
- À généraliser seulement après retour pilote : configuration de rulesets (reviews + statut de check obligatoire) par administrateur.

## Dérogations
Voir [EXCEPTIONS.md](./EXCEPTIONS.md). Aucun "NA" sans raison technique. Risques non acceptables (secret publié, exposition involontaire, données client) => correction avant fusion, sans simple dérogation documentaire.

## Gouvernance et indicateurs proposés
- Owner du standard : Engineering & Delivery (à désigner).
- Revue de version et d'exceptions : mensuelle au démarrage.
- Mesures : % PR avec matrice, % PR avec revue, NC ouvertes/traitées, exceptions expirées, preuves de restore/rollback.
- Cibles proposées : 100 % des PR nouvelles des dépôts pilotes avec matrice et revue ; 0 exception non tracée.
- Statut réel : **aucun taux de conformité ni adoption collective attesté à ce stade**.

**Références :** https://12factor.net/ ; https://docs.github.com/en/repositories/configuring-branches-and-merges-in-your-repository/managing-rulesets/about-rulesets
