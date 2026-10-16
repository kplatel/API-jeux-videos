# API Jeux Vidéo 🎮

API REST développée avec Symfony pour consulter et gérer des informations sur des jeux vidéo : catégories, éditeurs, jeux, utilisateurs et newsletter.

## Technologies

- PHP / Symfony
- Doctrine ORM
- Authentification JWT avec LexikJWTAuthenticationBundle
- DataFixtures pour les données de test
- NelmioApiDocBundle pour la documentation Swagger

## Fonctionnalités

- CRUD des jeux vidéo, catégories et éditeurs.
- Gestion des relations entre les entités.
- Validation des données avec les Asserts.
- Authentification JWT.
- Seuls les utilisateurs `ROLE_ADMIN` peuvent créer, modifier ou supprimer des jeux, catégories et éditeurs.
- CRUD des utilisateurs.
- Gestion des exceptions avec des réponses JSON.
- Pagination des listes avec mise en cache.
- Ajout d’une jaquette (`coverImage`) pour chaque jeu vidéo.
- Inscription à la newsletter via le champ `subscriptionToNewsletter`.
- Envoi d’un e-mail aux abonnés avec les jeux sortant dans les 7 prochains jours.
- Planification de l’envoi de la newsletter chaque lundi à 8h30.
- Documentation de l’API avec Swagger ou Postman.

## Installation

### 1. Cloner le projet

```bash
git clone <URL_DU_DEPOT>
cd <NOM_DU_PROJET>
```

### 2. Installer les dépendances

```bash
composer install
```

### 3. Configurer la base de données

Créer un fichier `.env.local` avec vos informations :

```dotenv
DATABASE_URL="mysql://utilisateur:mot_de_passe@127.0.0.1:3306/api_jeux_video"
```

### 4. Créer la base de données et les tables

```bash
php bin/console doctrine:database:create
php bin/console doctrine:migrations:migrate
```

### 5. Générer les clés JWT

```bash
php bin/console lexik:jwt:generate-keypair
```

### 6. Charger les données de test

```bash
php bin/console doctrine:fixtures:load
```

### 7. Lancer le serveur

```bash
symfony serve
```

## Documentation

La documentation de l’API est disponible via Swagger ou NelmioApiDocBundle. Elle permet de voir les routes disponibles, les paramètres attendus et de tester les requêtes.

## Exemple d’utilisation

- `GET /api/video-games` : récupérer la liste paginée des jeux vidéo.
- `GET /api/video-games/{id}` : récupérer un jeu vidéo.
- `POST /api/video-games` : ajouter un jeu vidéo, réservé aux administrateurs.
- `PUT /api/video-games/{id}` : modifier un jeu vidéo, réservé aux administrateurs.
- `DELETE /api/video-games/{id}` : supprimer un jeu vidéo, réservé aux administrateurs.

## Objectif du projet

Mettre en pratique la création d’une API REST avec Symfony : entités et relations, migrations, validation, sécurité JWT, pagination, cache, gestion d’erreurs et documentation.
