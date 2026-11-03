# OSEF Engineers — prototype GitHub Pages

Cette Pull Request propose un portail **statique public** d'information pour les parcours d'admission OSEF.

## Contenu du prototype
- Mission ADVISE / BUILD / OPERATE
- Deux parcours : Ingénieur OSEF et Responsable OSEF
- Admission en cinq étapes
- Mandat de responsable proposé pour 90 jours
- Liens vers les dépôts publics et mention explicite des ressources privées

## Publication (après validation de la PR)
Pour tester ce prototype dans le dépôt `.github`, aller dans **Settings → Pages → Build and deployment → Source: Deploy from a branch** ; choisir **main /docs** puis enregistrer.

Sur GitHub.com, le site de projet serait alors accessible sous `https://opensource-enterprise-factory.github.io/.github/` **si Pages est activé avec succès**. Ne pas considérer cette URL comme opérationnelle avant vérification du déploiement.

## Architecture cible à moyen terme
Créer un dépôt dédié nommé `opensource-enterprise-factory.github.io` pour héberger le portail officiel à la racine `https://opensource-enterprise-factory.github.io/`, puis transférer les fichiers du prototype et configurer Pages dans ce dépôt. La création de ce nouveau dépôt doit être effectuée par un administrateur habilité.

## Protection des données
GitHub Pages est un hébergement statique : ne pas y déposer de CV, contrats d'emploi, coordonnées privées, conflits d'intérêts, décisions d'admission ou registres de membres. Le dépôt et le site sont publiquement accessibles.

Pour collecter les candidatures, créer ultérieurement un formulaire privé hébergé par une solution dédiée, avec information sur les données collectées, finalité, accès restreints, durée de conservation et droits des candidats. Le formulaire ne doit pas déposer de réponses dans un dépôt public.

## Workflow de gouvernance recommandé
1. Candidat → formulaire privé (à sélectionner et déployer).
2. Administration & Juridique → registre privé et validation initiale.
3. Référent technique → revue d'une contribution GitHub.
4. Responsable habilité → décision d'admission.
5. Administrateur GitHub → attribution des permissions minimales.
6. Responsable de domaine → appel à candidature et mandat de 90 jours si souhaité.

Les workflows automatisés et l'activation de Pages ne sont **pas** inclus dans cette PR ; seule la vitrine est proposée.
