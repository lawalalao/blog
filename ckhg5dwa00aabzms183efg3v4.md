## Créez une API REST avec Node.js: concevez et planifiez votre API

Bonjour à tous! Bienvenue dans le premier article de cette série passionnante intitulée **Créez une API REST avec Node.js**. Dans cette série, je vous montrerai étape par étape la façon dont vous pouvez planifier, concevoir et créer votre propre API REST à l'aide de Node.js!..

### Avant de commencer...

Quelques prérequis que vous devez suivre:


- 
Connaissances débutantes à intermédiaires en JavaScript

- 
Compréhension de base de ce que sont les API REST

- 
Compréhension de base de la programmation back-end et de Node.js

### Quelques outils que nous utiliserons:


- 
Visual Studio Code ou tout éditeur de texte

- 
POSTman

- 
Node.js et express

- 
Atlas MongoDB

Pour l'instant, **il vous suffit d'avoir un éditeur de texte installé sur votre ordinateur**. Je vais vous expliquer comment installer le reste de cette série.

## Étape 1: Planification de notre T-API

Pour ce tutoriel, nous allons créer une API simple pour le thé (si aléatoire que je sais). Je l'appelle T-API parce que cela ressemble à "Thé API".

Pour planifier une API, nous devons d'abord comprendre ce que nous voulons qu'elle fasse. Nous pouvons rédiger des user stories pour nous aider à déterminer ce dont nous avons besoin dans la conception de notre API.
Nos témoignages d'utilisateurs T-API


- 
Je peux créer un nouvel objet thé et l'ajouter à la base de données

- 
Je peux obtenir tout le thé de la base de données


- 

Je peux supprimer tout le thé de la base de données

- 
Je peux obtenir un seul thé en interrogeant son nom


- 
Je peux publier un commentaire sur un seul thé


- 
Je peux supprimer un seul thé de la base de données

## Notre objet à thé

Sur la base de nos user stories et de la manière dont nous souhaitons utiliser l'API, nous pouvons rédiger un exemple d'objet thé que l'API peut renvoyer. Cela nous aide à décider quelles propriétés inclure dans l'objet au début de la phase de création de cette API. Ainsi, pour T-API, un objet thé pourrait ressembler à:

```
{
    "name": "Thé Lawal",
    "image": "url image",
    "description": "Le thé lawal est un thé parfumé à l'arôme de fleurs de jasmin.",
    "keywords": "aromatic, togo, sweet",
    "origin":"Togo",
    "brew time": 2,
    "temperature": 80,
    "comments": []
}
```
## Étape 2: Conception de la structure pour T-API

La façon de concevoir une API est de visualiser ses itinéraires et ses méthodes de requête.

Maintenant que nous avons compris ce que nous voulons que T-API fasse pour nous, nous pouvons proposer un design comme celui-ci:
<table style="width:100%">
  <tr>
    <th>Routes</th>
    <th>Methodes HTTP</th>
    <th>Description</th>
  </tr>
  <tr>
    <td>/the</td>
    <td>GET</td>
    <td>affiche tous les thés</td>
  </tr>
  <tr>
    <td>/the</td>
    <td>POST</td>
    <td>Cree un nouveau thé</td>
  </tr>
<tr>
    <td>/the</td>
    <td>DELETE</td>
    <td>supprime tous les thés</td>
  </tr>
<tr>
    <td>/tea/:name</td>
    <td>GET</td>
    <td>Affiche un thé spécifique, en fonction du nom donne</td>
  </tr>
<tr>
    <td>/tea/:name</td>
    <td>POST</td>
    <td>Ajoute un commentaire à un thé spécifique, en fonction du nom donne</td>
  </tr>
<tr>
    <td>/tea/:name</td>
    <td>DELETE</td>
    <td>supprime un thé specifique en fonction du nom donné</td>
  </tr>
</table>

D'accord, nous avons planifié et conçu notre T-API, commençons par configurer le projet!

## Étape 3: Installez Node.js et npm

Téléchargez Node.js (avec npm) sur: nodejs.org/en/download

Une fois installé, pour vérifier s'il est bel et bien installe, accédez à votre invite de commande et tapez:

```
node -v
npm -v
```
## Étape 4: Initialiser le projet

Créez un nouveau fichier projet et dans le répertoire racine, initialisez `npm` en exécutant le code suivant dans la ligne de commande:

```
npm init
```
Répondez aux questions qui suivent et un fichier `package.json` sera créé.

## Étape 5: Installez express

Installons `express` et sauvegardons-le dans notre package.json en exécutant:

```
npm install --save express
```
## Étape 6: créer un serveur

Maintenant, nous allons créer un fichier server.js dans le répertoire racine de notre projet pour prendre en charge le back-end. Tout d'abord, nous devons créer une application `Express` avec:

```
const express = require("express");
const app = express();
```
puis ajouter ce code:

```
app.use(express.json());// analyse les demandes entrantes avec des charges utiles JSON
```
Puis, en dessous, notre auditeur demande à notre serveur d'écouter une requête.

```
const listener = app.listen(process.env.PORT || 3000, () => {
    console.log('App is listening on port ' + listener.address().port)
})
```
Par défaut, nous voulons écouter sur le port 3000. Cependant, dans les cas où le numéro de port est désigné à partir d'une variable d'environnement, l'application écoutera sur `process.env.PORT`.

### Faites un essai!
Alors maintenant que notre `server.js` est configuré, essayons d'exécuter le serveur en entrant:

```
node server.js
```

dans la ligne de commande. Si cela fonctionne, vous devriez voir que la console affiche un message vous indiquant sur quel port elle écoute.


![3aeDW2WBB.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1604802409980/9OxD7xi0j.png)

## C'est tout pour le moment!

Merci d'avoir lu le premier article de la série. Techniquement, je peux écrire sur la construction d'une API REST en 1 article, mais ce sera trop long et je vais omettre beaucoup de détails importants qui peuvent dérouter les débutants en code.



# Glossaire

Voici quelques mots potentiellement inconnus que j'ai utilisés dans cet article. N'hésitez pas à lire lentement et à lire les articles suggérés pour plus de détails.

### Histoires d'utilisateurs ou USER STORIES

Selon  [Wikipedia](https://en.wikipedia.org/wiki/User_story) , une user story est une description informelle en langage naturel d'une ou de plusieurs fonctionnalités d'un système logiciel. Les user stories sont souvent rédigées du point de vue d'un utilisateur final ou d'un utilisateur d'un système.

### itinéraires ou ROUTES

Les itinéraires sont représentés sous forme d'URI dans les API REST. Par exemple, la route d'index pour une API est «/». D'autres routes seront construites dessus telles que '/ names' pour une route qui renvoie tous les noms ou '/ pages' pour celle qui renvoie toutes les pages. Pour en savoir plus sur le routage de base,  [cliquez ici](https://expressjs.com/en/starter/basic-routing.html) .

### méthodes de requête ou HTTP methods

Les méthodes de requête font référence aux méthodes HTTP qui spécifient l'action souhaitée que le navigateur souhaite effectuer avec le serveur.

### Express

Express est un framework Web pour Node.js pour permettre un routage facile et robuste pour le développement back-end. Il sera utilisé pour créer nos routes et gérer nos requêtes HTTP et tout middleware pour notre API. Vous pouvez en lire plus dans sa documentation  [ici](https://expressjs.com/) .

### middleware

![f1tkx-LGQ.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1604802926701/HezWxGKI_.png)

Un middleware fait essentiellement référence au logiciel qui se situe entre les demandes côté client et la ressource côté serveur. Il gère les données, fournit la gestion des API, les services de messagerie ainsi que l'authentification. Pour plus d'informations, lisez  [ici](https://en.wikipedia.org/wiki/Middleware) .

**J'espère que cet article a été utile pour vous. Assurez-vous d'aimer, partagez  et restez à l'écoute pour la partie suivante où nous commencerons à créer nos `routes` et à configurer notre base de données dans Mongo Atlas! En attendant, posez vos questions dans les commentaires ci-dessous et lisez les cadres / concepts / technologies de cet article pour accélérer votre apprentissage. Jusqu'à la prochaine fois, Merci!**
