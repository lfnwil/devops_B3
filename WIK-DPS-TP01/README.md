# WIK-DPS-TP01

API HTTP minimale developpee en TypeScript avec le module natif `node:http`.

## Fonctionnalites

- Demarrage sur le port defini dans le fichier `.env`.
- Route `GET /ping`.
- Retour des en-tetes HTTP recus au format JSON.
- Reponse `404` pour les autres routes.

## Prerequis

- [Node.js](https://nodejs.org/)
- npm

## Installation

Installer les dependances :

```sh
npm install
```

Creer un fichier `.env` a la racine du projet :

```env
PORT=3000
```

## Lancer l'API

Pour lancer le serveur :

```sh
npm start
```

Pour le lancer en mode developpement avec rechargement automatique :

```sh
npm run dev
```

Une fois le serveur demarre, l'API est disponible sur
`http://localhost:3000`.

## Tester l'endpoint

Envoyer une requete sur `/ping` :

```sh
curl -H "X-Test: wik-dps-tp01" http://localhost:3000/ping
```

Exemple de reponse :

```json
{
  "host": "localhost:3000",
  "user-agent": "curl/8.0.0",
  "accept": "*/*",
  "x-test": "wik-dps-tp01"
}
```

## Compiler le projet

Compiler le code TypeScript dans le dossier `dist` :

```sh
npm run build
```

## Structure

```text
.
|-- .env
|-- package.json
|-- server.ts
`-- tsconfig.json
```
