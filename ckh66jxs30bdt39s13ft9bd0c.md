## Configuration d'une application React pour déploiement sur Heroku

Il y a quelques années, si vous aviez une application web, il était difficile de la déployer. Aujourd'hui, la situation est un peu différente. Il existe de nombreuses options bonnes et bon marché à utiliser, et l'une d'entre elles est Heroku. Il est simple de déployer votre application Web et de la rendre disponible gratuitement grâce à son intégration facile à GitHub. Pour ce faire, il vous suffit de suivre les étapes décrites ci-dessous.

# Application

Le but est de faire Heroku le serveur de l'application. Mais vous devez d'abord effectuer certaines étapes de configuration de l'application. Je suppose que vous avez créé votre application React à l'aide du package `create-react-app`. Cela signifie que vous avez déjà défini des tâches `npm`. Il s'agit notamment de démarrer une application et de la construire pour la production. Si vous exécutez la tâche de construction, vous obtenez une application intégrée dans le dossier de construction. Et c'est ce que vous devez servir à partir du serveur.

# Étape 1: configuration d'ExpressJS

Pour heberger mes fichiers, j'utilise le serveur ExpressJS. Bien qu'il existe de nombreuses autres solutions, j'aime Express pour sa simplicité. En outre, il est simple de l'utiliser comme API. Pour l'installer, exécutez la commande CLI suivante.

```
npm install express --save
```
Maintenant, nous devons ajouter un script qui démarre le serveur. Ce serveur doit servir les fichiers statiques du dossier de construction. Pour cela, créez le fichier server.js à la racine de votre projet et ajoutez le code suivant.

```
const express = require("express");
const app = express();

app.use(express.static('build'))

app.listen(process.env.PORT || 3002, () => {
    console.log(`listening on port ${process.env.PORT || 3002}`)
});
```

Il y a deux petites choses à laquelles il faut faire attention ici. Si vous essayez de l'exécuter localement, il le sert sur le port 3002. Vous pouvez le remplacer par n'importe quel port disponible. Il essaie d'abord de définir la valeur du port à partir de la variable process.env.PORT. C'est la variable d'environnement définie par Heroku. La dernière partie du nom de la variable doit être en majuscules. Il y a quelques articles StackOverflow sur les problèmes liés à l'utilisation de minuscules.

# Étape 2: tâche de post-installation

Lors de la configuration d'Heroku pour l'application Node,  l'installation est déclenchée automatiquement. Pour exécuter la tâche de construction, vous devez effectuer une petite configuration et il est préférable de la placer dans la tâche de post-installation. Vous devez mettre à jour le fichier package.json pour contenir cette tâche, comme dans le code ci-dessous.

```
"scripts": {
  "start": "react-scripts start",
  "build": "react-scripts build",
  "test": "react-scripts test",
  "eject": "react-scripts eject",
  "postinstall": "npm run build"
},
```
La raison pour laquelle cela est en post-installation est que cette tâche peut prendre du temps. Et Heroku a un certain temps maximum autorisé pour l'execution du script, et si la tâche de construction prend beaucoup de temps, cela peut entraîner un délai d'expiration.

# Étape 3: Procfile

La dernière étape de la configuration de l'application consiste à créer le fichier Procfile. Je n'entrerai pas dans les détails sur ce qu'est ce fichier. Considérez-le comme un script en cours d'exécution pour Heroku. Il y a suffisamment d'articles à ce sujet. Ce fichier doit être dans le dossier racine de votre projet et doit être nommé exactement Procfile. Pas de point au début ni d'extension à la fin. Il doit contenir le code suivant.

```
web: node server.js
```

À ce moment, votre application est prête pour le déploiement. Il y a quelques étapes supplémentaires à configurer dans la console Web Heroku, mais vous êtes prêt à commencer pour le deploiement de votre application.