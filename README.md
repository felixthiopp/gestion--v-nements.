
# Gestion d'Événements - Application Web

## Description
Cette application permet de gérer des événements en ligne. Elle offre les fonctionnalités suivantes :
- Inscription et authentification des utilisateurs.
- Création, lecture, mise à jour et suppression (CRUD) d'événements.
- Interface utilisateur simple avec des champs de formulaire pour interagir avec les événements.

## Fonctionnalités
- **Inscription** : Les utilisateurs peuvent s'inscrire en fournissant un email et un mot de passe.
- **Connexion** : Les utilisateurs peuvent se connecter pour obtenir un token d'authentification.
- **Création d'événements** : Les utilisateurs peuvent créer des événements en spécifiant un titre, une description et une date.
- **Affichage des événements** : Les utilisateurs peuvent consulter tous les événements créés.
- **Mise à jour des événements** : Les utilisateurs peuvent modifier les détails d'un événement existant.
- **Suppression des événements** : Les utilisateurs peuvent supprimer un événement.

## Technologies utilisées
- **Back-end** : Node.js, Express, Mongoose
- **Base de données** : MongoDB (NoSQL)
- **Front-end** : HTML, JavaScript
- **Authentification** : JSON Web Token (JWT)
- **CORS** : Permet l'accès depuis d'autres origines
- **Bibliothèque de gestion des variables d'environnement** : dotenv

## Prérequis
Avant de commencer, vous aurez besoin de :
- Node.js installé sur votre machine.
- MongoDB en fonctionnement sur `localhost:27017` ou un serveur MongoDB distant.

## Installation
1. Clonez ce repository.
   ```bash
   git clone https://github.com/votre-utilisateur/gestion-evenements.git
   ```

2. Accédez au dossier du projet.
   ```bash
   cd gestion-evenements
   ```

3. Installez les dépendances.
   ```bash
   npm install
   ```

4. Configurez votre fichier `.env` avec les informations suivantes :
   ```bash
   MONGO_URI=mongodb://localhost:27017/eventapp
   JWT_SECRET=une_cle_secrete
   ```

5. Lancez le serveur.
   ```bash
   node server.js
   ```

Le serveur sera disponible à l'adresse `http://localhost:5000`.

## Utilisation de l'Application

### 1. Inscription d'un utilisateur
Pour vous inscrire, envoyez une requête `POST` à `http://localhost:5000/api/auth/register` avec le corps suivant :

```json
{
  "email": "test@example.com",
  "password": "123456"
}
```

### 2. Connexion
Pour vous connecter, envoyez une requête `POST` à `http://localhost:5000/api/auth/login` avec le corps suivant :

```json
{
  "email": "test@example.com",
  "password": "123456"
}
```

Vous recevrez un token JWT dans la réponse. Ce token doit être utilisé pour l'authentification dans les requêtes suivantes.

### 3. Création d'un événement
Envoyez une requête `POST` à `http://localhost:5000/api/events` avec le corps suivant :

```json
{
  "title": "Titre de l'événement",
  "description": "Description de l'événement",
  "date": "2025-05-01"
}
```

### 4. Récupération des événements
Envoyez une requête `GET` à `http://localhost:5000/api/events` avec le token JWT dans les en-têtes de la requête :

```bash
Authorization: Bearer <votre_token>
```

### 5. Mise à jour d'un événement
Envoyez une requête `PUT` à `http://localhost:5000/api/events/{id}` avec le corps suivant :

```json
{
  "title": "Nouveau titre",
  "description": "Nouvelle description",
  "date": "2025-05-02"
}
```

### 6. Suppression d'un événement
Envoyez une requête `DELETE` à `http://localhost:5000/api/events/{id}` pour supprimer l'événement.

## Structure du projet
```
/gestion-evenements
|-- /models
|   |-- Event.js         # Modèle pour l'événement
|   |-- User.js          # Modèle pour l'utilisateur
|
|-- /routes
|   |-- authRoutes.js    # Routes pour l'inscription et la connexion
|   |-- eventRoutes.js   # Routes pour la gestion des événements
|
|-- server.js           # Point d'entrée du serveur Node.js
|-- .env                # Fichier pour les variables d'environnement
|-- package.json        # Dépendances du projet
```

## Notes
- Assurez-vous que MongoDB est en cours d'exécution avant de démarrer l'application.
- Pour sécuriser l'application, n'oubliez pas de ne jamais exposer vos clés secrètes dans un environnement public.
  

