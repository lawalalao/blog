## Créez une API REST avec Node.js: déploiement sur Heroku (Finale)

Bonjour à tous! Bienvenue à nouveau dans cette serie Créez une API REST avec Node.js- la finale. Nous terminons enfin cette API. Ça a été une longue série et nous sommes enfin là!

Si vous êtes nouveau dans cette série, veuillez consulter les articles précédents à suivre:

1. 
 [Conception et planification de l'API](https://lawaltech.hashnode.dev/creez-une-api-rest-avec-nodejs-concevez-et-planifiez-votre-api?guid=aeb98ca9-707d-467e-8e44-7c8efdc24ec2&deviceId=8bffedad-d849-4d38-9356-4b5b673b80aa) 

2. 
 [Routes et contrôleurs](https://lawaltech.hashnode.dev/creez-une-api-rest-avec-nodejs-routes-et-controleurs) 

3. 
 [Intégration de MongoDB Atlas](https://lawaltech.hashnode.dev/creer-une-api-rest-avec-nodejs-integration-de-mongodb-atlas) 

4. 
 [Finalisation des contrôleurs](https://lawaltech.hashnode.dev/creer-une-api-rest-avec-nodejs-finaliser-les-controleurs) 

5. 
 [télécharger un fichier image](https://lawaltech.hashnode.dev/creer-une-api-rest-avec-nodejs-telecharger-un-fichier-image) 

Aujourd'hui, nous allons préparer l'API pour le déploiement! Pour ce faire, nous devons d'abord ajouter un peu de sécurité et de compression.

## Étape 1: Sécurité

Nous utilisons  **helmet** pour assurer la sécurité de notre application. 

Pour l'installer, exécutez:

```
npm install --save helmet
```
Incluez ensuite les éléments suivants dans server.js:

```
// ajoutez cette ligne sous les autres instructions d'importation
const helmet = require('helmet');

// ajoutez cette ligne sous const app = express ();
app.use(helmet());
```

Une autre fonctionnalité de sécurité que nous pouvons ajouter est la protection des itinéraires **route**. C'est parce que nous ne voulons pas que chaque utilisateur ait accès pour créer un nouveau thé ou pour supprimer tout le thé dans notre API. Ce serait tragique!

Pour cette API, j'ai implémenté une autorisation d'en-tête API de base pour restreindre l'accès à certaines routes, mais cela sort du cadre de cette série, car je veux qu'elle soit aussi conviviale que possible pour les débutants. Un article séparé sur les méthodes d'authentification API à venir.

# Étape 2: Compression

Nous pouvons compresser les requêtes HTTP pour réduire considérablement le temps nécessaire au client pour obtenir et charger la page à partir du serveur. Pour ce faire, nous pouvons utiliser  `compression`.

Installez-le avec:

```
npm install compression
```

Ajoutez ensuite ce qui suit avant les routes dans server.js:

```
// ajoutez cette ligne en dessous de helmet 
const compression = require('compression');

// ajoutez en dessous de app.use(helmet())
app.use(compression()); //Compressez toutes les routes
```

## Étape 3: Préparation pour heroku

Pour cette API, je la déploie sur  [heroku](https://www.heroku.com/) . Il s'agit d'une plate-forme basée sur le cloud pour créer, fournir et surveiller des applications Web telles que cette API. Mais il existe de nombreuses options comme:


- 
AWS

- 
DigitalOcean

- 
Google Cloud

- 
Firebase

- 
Microsoft Azure

- ...

### 1. Github

Tout d'abord, assurez-vous d'avoir votre API dans un référentiel Github. En effet, heroku est intégré à git, ce qui facilite les changements futurs.

### 2. package.json

Vérifiez la version de votre node en exécutant:

```
node --version
```
La console affichera la version de votre nodejs. Copiez-le, et incluez-le dans la clé "moteurs" pour l'ajouter à votre package.json:

```
"engines": {
    "node": "14.13.0"
  },
```
Et assurez-vous que votre package.json a la configuration suivante pour les clés "main" et "scripts".

```
"main": "server.js",
"scripts": {
    "start": "node server.js",
    "test": "echo \"Error: no test specified\" && exit 1"  //optional
  },
```

### 3. Procfile et index.html

Créez un nom de fichier 'Procfile' dans le répertoire racine et ajoutez

```
web:node server.js
```

Il s'agit de demander à heroku d'exécuter la commande 'node server.js' dès qu'elle démarre l'application.

Si vous le souhaitez, créez un `index.html` afin que l'API ait au moins un visage lors de son premier chargement. J'en fais un simple avec un élément de titre et de paragraphe.

```
<h1>Welcome to T-API</h1>
<p>The Tea API for all Tea Lovers~</p>
```

N'oubliez pas d'ajouter sa route dans server.js pour que index.html soit statique, ce qui permet à l'API d'y accéder au démarrage du serveur.

```
// ajoutez ceci ci-dessous app.use ("/", routes) pour faire de index.html un fichier statique
app.route ('/')
  .get(function (req, res) {
    res.sendFile(process.cwd() + '/index.html');
});
```

### 4. MongoDB

Nous y sommes presque! Enfin, nous ajoutons 2 autres options dans notre méthode `mongoose.connect()` dans notre fichier server.js:

```
server: { 
   socketOptions: { keepAlive: 300000, connectTimeoutMS: 30000 } 
}, 
replset: {
   socketOptions: { keepAlive: 300000, connectTimeoutMS : 30000 } 
}
```
Cela empêche heroku de renvoyer une erreur de délai d'expiration 503, juste au cas où. Voici la version finale de la méthode mongoose.connect () dans notre fichier server.js:

```
mongoose.connect(
  process.env.MONGODB_URI,
  {
    useFindAndModify: false,
    useUnifiedTopology: true,
    useNewUrlParser: true,
    useCreateIndex: true,
    server: { socketOptions: { keepAlive: 300000, connectTimeoutMS: 30000 } },
    replset: { socketOptions: { keepAlive: 300000, connectTimeoutMS: 30000 } },
  },
  function (err) {
    if (err) return console.log("Error: ", err);
    console.log(
      "MongoDB Connection -- Ready state is:",
      mongoose.connection.readyState
    );
  }
);
```
Génial! Nous avons préparé ce dont nous avons besoin pour déployer notre application sur heroku.

## Étape 4: Heroku

Créez un compte gratuitement sur heroku.com.

Ensuite, téléchargez la CLI heroku ici et suivez leurs instructions sur cette  [page](https://devcenter.heroku.com/articles/heroku-cli)  pour l'installer.

Une fois que vous avez installé la CLI, vous pouvez maintenant utiliser les commandes heroku sur votre invite de commande pour déployer l'API. Dirigez-vous vers le répertoire racine du projet et exécutez:

```
heroku create <app-name>
```
Ensuite, faisons le dernier push:

```
Ensuite, faisons le dernier effort:
```
super! Nous avons déployé l'API! Mais comme les variables d'environnement ne sont pas déployées, nous devons d'abord configurer notre process.env.MONGODB_URI avant de démarrer l'application.

Configurez en exécutant la commande dans votre invite de commande:

```
heroku config:set MONGODB_URI="<your url here>"
```

Terminé!
Enfin, exécutez ce qui suit pour vous assurer qu'une instance de l'application s'exécute toujours:

```
heroku ps:scale web=1
```
visitons le site avec

```
heroku open
```

L'index.html se chargera comme page d'entrée comme indiqué ci-dessous. C'est juste une page blanche vide avec des mots pour le moment. Assurez-vous de rendre le fichier statique afin qu'il soit accessible par le serveur pour le rendu. Dans server.js:

```
//Index page d'entree par defaut
app.route("/").get(function (req, res) {
  res.sendFile(process.cwd() + "/index.html");
});
```

![1.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1606404645679/7k2VIUHcT.png)

Pour le moment, nous n'avons pas d'interface conviviale pour tester notre API sur le navigateur. Mais nous pouvons simplement ajouter nos routes dans l'URL manuellement. 

Bien sûr, je suis allé de l'avant pour remplir (POST) certains objets de thé en premier ou l'URL retournera un objet vide. Comme le montre l'image ci-dessus, l'URL renvoie correctement l'objet thé que j'ai créé précédemment et par conséquent, l'API fonctionne! Yay!

# Toutes mes félicitations!

Nous avons enfin fini de créer une API REST fonctionnelle avec Node.js, MongoDB et Express! J'espère que cette série vous a été très utile pour comprendre les routes, les contrôleurs, les bases de données et le fonctionnement des API. J'écrirai et publierai bientôt un article sur la création d'un front-end d'une API, alors restez à l'écoute.

Merci d'avoir lu et suivi cette série. Je suis très reconnaissant d'avoir reçu vos paroles généreuses et vos commentaires. Nous terminerons cette série sur une bonne note. Tout commentaire ou question, comme d'habitude, n'hésitez pas à les partager ci-dessous. J'espère que vous aimez le thé et les API maintenant. À votre santé!

Reportez-vous au référentiel Github si vous avez besoin de voir le code source: https://github.com/lawalalao/t-api
