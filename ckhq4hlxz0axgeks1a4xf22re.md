## Créer une API REST avec Node.js: intégration de MongoDB Atlas

Bonjour à tous! Bienvenue à nouveau dans la serie **Créer une API REST avec Node.js**.

Si vous êtes nouveau dans cette série, veuillez consulter les articles précédents à suivre:


- 
 [Conception et planification de l'API](https://lawaltech.hashnode.dev/creez-une-api-rest-avec-nodejs-concevez-et-planifiez-votre-api) 

- 
 [Le module HTTP et Express](https://lawaltech.hashnode.dev/creez-une-api-rest-avec-nodejs-1-2module-http-et-express) 

- 
 [Routes et contrôleurs]((https://lawaltech.hashnode.dev/creer-une-api-rest-avec-nodejs-integration-de-mongodb-atlas) 

Reprenant là où nous nous étions arrêtés dans le 2ème article, nous allons maintenant intégrer notre API à une base de données. Pour cette API, nous utilisons MongoDB Atlas: une base de données cloud entièrement gérée.

# Étape 1: configurer MongoDB

Accédez à [ leur site Web](https://www.mongodb.com/cloud/atlas)  pour créer un compte MongoDB ou connectez-vous. Suivez les étapes ci-dessous pour configurer MongoDB.

## 1. Créer un cluster.

Lorsque vous créez un compte pour la première fois, il vous sera demandé de créer un cluster. Choisissez le cluster partagé, alias le «GRATUIT».


![1.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1605648875180/IcLXlrATH.png)

Sélectionnez maintenant la région la plus proche de l'endroit où vous vous trouvez actuellement. Je sélectionne la Virginie du Nord car c'est le plus proche de là où je suis.


![2.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1605648948870/NSn1vF9c2.png)

Laissez le reste des paramètres par défaut et cliquez sur «Créer un cluster».

## 2. Adresse IP de la liste blanche.

Après avoir créé le cluster, vous devriez voir quelque chose comme l'image ci-dessous. Cliquez sur 'Accès réseau' dans le panneau de gauche.


![3.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1605649022567/f9ukfCtyk.png)

Vous verrez une page où vous pouvez ajouter une adresse IP à la liste blanche. Cela signifie que seules les adresses IP de la liste blanche peuvent accéder à cette base de données.

Cliquez sur «Ajouter une adresse IP». Une fenêtre contextuelle apparaîtra, puis cliquez sur «Autoriser l'accès de n'importe où» pour vous assurer que tout appareil peut accéder à la base de données. Enfin, cliquez sur «Confirmer». Voir l'image ci-dessous pour visualiser.


![4.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1605649183656/m2q1jwI4l.png)

## 3. Créer un utilisateur

Cliquez maintenant sur «Accès à la base de données» dans le panneau de gauche. Nous créerons notre utilisateur en cliquant sur «Ajouter un nouvel utilisateur de base de données».


![5.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1605649254525/peRz7wv_7.png)

Ceci est une étape très importante. Nous utiliserons l'authentification par mot de passe pour connecter notre API à notre base de données. Remplissez votre nom d'utilisateur et votre mot de passe avec tout ce que vous voulez, assurez-vous de vous en souvenir ou prenez-en note. Cliquez ensuite sur «Ajouter un utilisateur».


![6.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1605649301304/3m21p8ToL.png)

## 4. Connectez le cluster.

Maintenant, dirigez-vous vers «Clusters» et cliquez sur le bouton «CONNEXION». Enfin, cliquez sur «Connecter votre application». Jetez un œil à l'image ci-dessous pour voir les étapes.


![7.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1605649355708/sfouwI0O_.png)

Ensuite, assurez-vous que le pilote est Node.js et que la version est la dernière (voir l'image ci-dessous). Copiez l'extrait de code fourni. Nous allons l'utiliser pour connecter notre API à ce cluster de base de données. Fermons la fenêtre pop-up et dirigons-nous vers notre API.


![8.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1605649399876/jqihxGdok.png)

# Étape 2: connectez l'API à MongoDB

Dans notre projet, installez mongoose en exécutant:

```
npm install --save mongoose
```
## Qu'est-ce que moongoose?

Mongoose est une bibliothèque de modélisation de données d'objets (ODM) pour MongoDB. Cela nous permet de créer efficacement des schémas que notre MongoDB peut utiliser avec facilité. Pour plus d'informations, consultez la  [documentation de la mongoose.](https://mongoosejs.com/docs/)

Après avoir installé mongoose, ajoutez ce qui suit à notre fichier server.js:

```
 //importer mongoose
const mongoose = require('mongoose');

//etablir la connection database
mongoose.connect(
    'mongodb+srv://<username>:<password>@cluster0.eetsx.mongodb.net/<dbname>',
    { useFindAndModify: false, useUnifiedTopology: true, useNewUrlParser: true, useCreateIndex: true},
    (err) => {
        if (err) return console.log("Error: ", err);
        console.log("MongoDB Connection -- Ready state is:", mongoose.connection.readyState);
    }
);
```

Dans ce code, nous avons effectué les opérations suivantes:


- 
Importez mongoose.


- 
Utilisez **mongoose.connect ()** pour établir une connexion à la base de données. Entrez l'URL copiée d'avant comme premier argument.

- 
Remplacez `<username>`, `<password>` et `<dbname>` de l'URL selon le cas. Pour mon API, `<dbname>` est du thé.

- 
Dans le 2ème argument, nous entrons certaines options pour lesquelles nous devons définir des valeurs. Ceci afin que nous n'obtenions pas d'avertissements d'obsolescence et que mongoose puisse se connecter à MongoDB. Plus de détails  [ici.](https://mongoosejs.com/docs/connections.html) 

- 
Enfin, nous avons une fonction de gestion des erreurs.

## Pour des raisons de sécurité

Si vous ajoutez ce projet à un référentiel public, il est préférable que personne ne puisse voir l'URI MongoDB puisque nous y avons inclus notre mot de passe, une information sensible. Par conséquent, nous pouvons créer un fichier .env dans notre répertoire racine et écrire notre URI à l'intérieur comme:

```
MONGODB_URI='mongodb+srv://<username><password>@cluster0.eetsx.mongodb.net/tea```

De retour à server.js, remplacez l'URI dans mongoose.connect () par process.env.MONGODB_URI afin que nous puissions masquer ces informations sensibles. Assurez-vous que .env est inclus dans votre .gitignore afin de ne pas le pousser vers un dépôt public pour que tout le monde puisse voir votre mot de passe. Cela gaspillerait le point de créer un fichier .env. Voici à quoi devrait ressembler la méthode de connexion finale de mongoose:

```
mongoose.connect(
    process.env.MONGODB_URI,
    { useFindAndModify: false,useUnifiedTopology: true, useNewUrlParser: true, useCreateIndex: true},
    (err) => {
        if (err) return console.log("Error: ", err);
        console.log("MongoDB Connection -- Ready state is:", mongoose.connection.readyState);
    }
);
```

Ensuite, installez le package  [dotenv npm](https://www.npmjs.com/package/dotenv )  afin que nous puissions utiliser notre fichier .env dans notre projet:

```
npm install dotenv
```

Ajoutez cette ligne en haut de **server.js** qui initialise le dotenv:

```
require('dotenv').config();
```
# Étape 3: Créez le modèle de thé

Nous sommes maintenant prêts à ajouter des objets de données de thé dans notre base de données MongoDB Atlas.

Commencez par créer un dossier «models». Ensuite, créez un fichier tea.js dans le dossier. C'est là que sera notre modèle de thé. Voici à quoi devrait ressembler votre répertoire à ce stade:


![9.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1605650090256/_jINUj-MZ.png)

Maintenant, créons un nouveau schéma dans notre fichier models / tea.js. Exportez ensuite le module à utiliser dans notre contrôleur de thé.

### Qu'est-ce qu'un schéma?

Un schéma définit la forme du document qui correspond à une collection MongoDB. Nous convertissons ensuite ce schéma en un modèle, avec lequel nous pouvons ensuite travailler pour le manipuler avec notre API.

Notre schéma de thé sera basé sur l'objet thé que nous avions prévu plus tôt dans le  [premier article](https://lawaltech.hashnode.dev/creez-une-api-rest-avec-nodejs-concevez-et-planifiez-votre-api) :

```
// exemple d'objet the
{
    "name": "Jasmine Tea",
    "image": "an image file url",
    "description": "Jasmine tea (茉莉花茶) is tea scented with the aroma of jasmine blossoms.",
    "keywords": "aromatic, china, sweet",
    "origin":"China",
    "brew_time": 2,
    "temperature": 80,
    "comments": ["text": "I am a comment", "date": Date String]
}
```
Nous pouvons créer notre schéma de thé comme suit:

```
//Syntaxe
property: {type: SchemaType (i.e. String, Date, Number), 
                  other options (i.e. default, required)}

//Exemples
name: {type: String, required: true}
description: String   //short for {type: String}
```


> N'hésitez pas à vous arrêter à cette étape pour essayer d'écrire le schéma vous-même. C'est le même format que les exemples.


![O1gFC1uPm.gif](https://cdn.hashnode.com/res/hashnode/image/upload/v1605650271713/p8JZxK4VP.gif)

Voici notre schéma de thé (dans models / tea.js):

```
const mongoose = require("mongoose"); //importer mongoose

// tea schema
const TeaSchema = new mongoose.Schema({
    name: {type:String, required:true},
    image: String,
    description: String,
    keywords: String,
    origin: String,
    brew_time: Number,
    temperature: Number,
    comments: [{ text: String, date: {type:String, default: new Date()} }]
});

const Tea = mongoose.model('Tea', TeaSchema); //convertir en modèle nommé Tea
module.exports = Tea; //exportation pour l'utilisation du contrôleur
```
Ainsi, comme indiqué dans le code ci-dessus, nous avons créé notre schéma de thé, l'avons converti en modèle à l'aide de `mongoose.model ()` et enfin exporté en tant que modèle 'Tea' pour que les fonctions de contrôleur puissent le manipuler (c'est-à-dire créer, lire, mettre à jour et supprimer Les données).

# C'est tout pour le moment!

Dans cet article, nous avons configuré avec succès MongoDB Atlas et utilisons mongoose pour aider à intégrer notre API à MongoDB. Ajoutons quelques fonctions à nos controllers / tea.js pour utiliser notre modèle Tea pour notre API dans la prochaine partie de cette série.

Merci d'avoir lu et s'il vous plaît laissez un like ou un partage si cela est utile. N'hésitez pas à poser des questions dans les commentaires ci-dessous. Si vous n'êtes pas sûr de certains concepts, veuillez consulter quelques-unes des ressources de lecture ci-dessous.
 À votre santé!