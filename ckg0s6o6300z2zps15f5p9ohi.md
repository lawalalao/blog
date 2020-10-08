## Premiers pas avec MongoDB

MongoDB est une base de données NoSQL, à usage général, basée sur des documents . Basé sur un document, cela signifie qu'il stocke les données dans des documents de type JSON. Dans cet article, nous allons configurer un cluster MongoDB de type gratuit sur le cloud MongoDB et nous connecter à notre application NodeJS & Express.

## Lancement du cluster MongoDB

Donc, pour commencer, allons à la page d'accueil  [MongoDB](https://www.mongodb.com/)  et cliquez sur le bouton Démarrer gratuitement au centre de l'écran.


![z1M2Gni7Q.jpeg](https://cdn.hashnode.com/res/hashnode/image/upload/v1601990331856/zRHDLeswM.jpeg)

Une fois que vous avez cliqué sur Démarrer gratuitement, un formulaire similaire à celui-ci vous sera présenté:


![0lmaOj4dG.jpeg](https://cdn.hashnode.com/res/hashnode/image/upload/v1601990394759/fQgxYIU76.jpeg)

Remplissez les champs requis et fournissez une adresse e-mail valide et cliquez sur «Commencer gratuitement». Ensuite, vous serez connecté à Mongo Cloud Console et vous serez invité à créer un cluster. Ce sera quelque chose de similaire à ceci:


![a.jpeg](https://cdn.hashnode.com/res/hashnode/image/upload/v1601990460210/9XMJTF5kc.jpeg)

Maintenant, renommez simplement votre cluster et cliquez sur "Créer un cluster". Cela lancera le processus de lancement du cluster. Après environ 5 minutes, le cluster sera prêt et vous serez autorisé à créer un utilisateur.

## Création d'un utilisateur de base de données


![b.jpeg](https://cdn.hashnode.com/res/hashnode/image/upload/v1601990552701/LtBFtRXrw.jpeg)

Maintenant, dans le menu de navigation de gauche, cliquez sur "Accès à la base de données". Vous aurez quelque chose de similaire à ça..


![c.jpeg](https://cdn.hashnode.com/res/hashnode/image/upload/v1601990594081/rkiS-gI8W.jpeg)

Maintenant, cliquez sur "Ajouter un nouvel utilisateur de base de données". Vous serez invité avec quelque chose de similaire à.


![d.jpeg](https://cdn.hashnode.com/res/hashnode/image/upload/v1601990635532/EskNSShGi.jpeg)

Entrez le nom d'utilisateur et le mot de passe dans le champ respectif et cliquez sur Ajouter un utilisateur.

## Adresse IP de WhiteListing

Une fois que l'utilisateur de la base de données a été créé, vous devez ajouter à la liste blanche l'adresse IP par laquelle la base de données est accessible. Pour ce faire, retournez aux clusters à partir de la barre de navigation gauche et cliquez sur CONNECT dans la zone SANDBOX..


![e.jpeg](https://cdn.hashnode.com/res/hashnode/image/upload/v1601990747757/HLeUv_JBd.jpeg)

Maintenant, choisissez Autoriser l'accès de n'importe où et enregistrez. Cliquez ensuite sur Choisir une méthode de connexion.

## Obtenir la chaîne de connexion

Maintenant, après avoir cliqué sur Choisir la méthode de connexion, les options suivantes vous seront présentées


![fg.jpeg](https://cdn.hashnode.com/res/hashnode/image/upload/v1601990795113/q8JpWzHqX.jpeg)

Choisissez `Connecter votre application` et vous recevrez les informations suivantes


![g.jpeg](https://cdn.hashnode.com/res/hashnode/image/upload/v1601990836876/edLGSD1JR.jpeg)

Copiez la chaîne de connexion en cliquant sur Copier et collez-la dans un fichier NotePad ou bloc note. Cela ressemblerait à quelque chose comme:


```
mongodb+srv://dmr:<password>@mytestcluster.f5kbx.mongodb.net/<dbname>?retryWrites=true&w=majority
``` 
Remplacez le `<password>` par le mot de passe que vous avez utilisé lors de la création de l'utilisateur et le `<dbname>` également par le nom de votre cluster. Dans mon cas, j'utiliserais `testdb`.

## Connexion avec notre application express

Maintenant, avec notre chaîne de connexion, nous pouvons directement établir la connexion avec notre base de données en utilisant MongoDB Compass mais nous aimerions connecter notre application Express avec MongoDB. Créez donc un dossier appelé MongoTest et via le terminal, accédez au dossier.

Étant donné que vous êtes dans le dossier Mongotest, tapez les commandes suivantes:

```
npm init -y
npm i express mongoose --save
touch index.js
```

Nous initialisons le fichier `package.json` et installons les packages Express et Mongoose. Maintenant, éditons notre fichier `Index.js`. Ce serait quelque chose de similaire à:


```
const express = require("express");
const mongoose = require("mongoose");

const app = express();

let db =
  "mongodb+srv://dmr:<Password>@mytestcluster.f5kbx.mongodb.net/testdb?retryWrites=true&w=majority";

mongoose
  .connect(db, { useNewUrlParser: true, useUnifiedTopology: true })
  .then(() => console.log("mongoDB connected Successfully"))
  .catch((err) => console.log(err));

app.listen(3000, console.log("Server running on port 3000"));
``` 
N'oubliez pas de remplacer la section`password` par le mot de passe que vous avez défini pour l'utilisateur. Maintenant, tapez simplement:


```
node index.js

``` 
Si vous avez tout fait correctement, vous verrez dans votre terminal le message `MongoDB connectée avec succès`.

    
> 
 Merci d'avoir lu. Dans le prochain article, nous allons creer une API CRUD en utilisant MongoDb, NodeJS et Express..