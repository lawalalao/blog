## Créez une API REST avec Node.js: Routes et contrôleurs

Bonjour les amis! Bienvenue dans le 3ème article de la série **Créez une API REST avec Node.js**. Dans cet article, nous allons continuer là où nous nous sommes arrêtés dans [ la conception et la planification de votre API](creez-une-api-rest-avec-nodejs-concevez-et-planifiez-votre-api)  et commencer à créer des routes et des contrôleurs pour notre T-API!

## Que sont les contrôleurs?

Les contrôleurs sont généralement des fonctions de rappel qui correspondent aux routeurs pour traiter les demandes. C'est un bon principe de conception de garder le code concis et lisible. Dans l'article précédent, j'ai discuté de ce qu'est une route. Un exemple d'itinéraire pourrait ressembler à ceci:

```
// Syntaxe
app.method('<path>', callbackFunction)

// Exemple
app.get("/", function (req, res) {
  res.json({message: "Hello world!"});
});
```
Au fur et à mesure que vous ajoutez d'autres routes à l'API, le script peut commencer à paraître long et désordonné comme:

(Ceci est juste une illustration. Pas besoin de lire ce long morceau de code)

```
app.post('/api/exercise/new-user', function(req, res) {
  let username = req.body.username;
  Person.findOne({username:username}, (err,findData)=>{
    if (findData == null){
      //no user currently, make new
      const person = new Person({username : username, exercise : []});
      person.save((err,data)=>{
        if(err){
          return res.json({error: err});
        }
        return res.json({"username":findData.username,"id":findData.shortId});
      });
    }else{
      //username taken, show their id
      return res.json({error:"This username is taken","id":findData.shortId});
    }
  });
}

app.post('/api/exercise/add', function(req,res){
  let id = req.body.userId;
  let descr = req.body.description;
  let duration = req.body.duration;
  let date = req.body.date;

  if(date != ''){
    date = new Date(req.body.date); //save as Date object
  }

  if(descr == ''|| duration == '' || id == ''){
    return res.json({error: 'missing values'});
  }

  //check if id exists in database
  Person.findOne({shortId:id}, (err,data)=>{
    if (data == null){
      return res.json({error: 'id not found'});
    }else{
      data.exercise = data.exercise.concat({desc : descr, duration: duration, date: date});
      //save
      data.save((err, data) => {
        if (err) return res.json({error: err});
      });
      return res.json({"username": data.username, "description": descr, "duration": duration,"id": id, "date": date});
    }
  });
}
```
Ainsi, un contrôleur peut réduire cet énorme morceau de code en:

```
app.post('/api/exercise/new-user', UserController.addUser); //nouvel utilisateur

app.post('/api/exercise/add', UserController.addExercise); //nouvel excercice
```

Là, c'est beaucoup plus simple à lire et c'est la beauté d'un contrôleur. Les fonctions sont conservées dans un autre fichier (c'est-à-dire controllers.js) pour que notre server.js ait l'air propre! Alors, commençons à implémenter nos routes et contrôleurs.

## Étape 1: créer des dossiers et des fichiers

Dans le répertoire racine de votre projet, créez 2 dossiers et nommez-les «routes» et «contrôleurs».

Ensuite, dans chaque dossier, créez un fichier `tea.js` pour notre route du thé et notre contrôleur de thé. C'est une convention de nommer le contrôleur de la même manière que la route qu'il gère. Votre répertoire doit ressembler à:


![LBhp-Q9p1.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1604843854267/LuccKmSBU.png)

## Étape 2: La première route et le premier contrôleur.

Impressionnant! Maintenant, ouvrez votre fichier routes / tea.js. Nous pouvons créer notre premier route comme suit:


- 
Créez un objet routeur express pour configurer nos routes

- 
Importez notre contrôleur de thé à partir de notre fichier controllers / tea.js que nous avons créé précédemment

- 
Créez notre première route avec la fonction de contrôleur comme rappel pour gérer la demande.

- 
Exportez la route à utiliser dans notre server.js


**Dans le code, cela ressemblera à:**

```
const express = require('express'); //import express

// 1.
const router  = express.Router(); 
// 2.
const teaController = require('../controllers/tea'); 
// 3.
router.post('/tea', teaController.newTea); 
// 4. 
module.exports = router; // export to use in server.js
```

Pour cet exemple, nous créons la route POST '/ tea' et définissons la fonction `teaController` `newTea` pour gérer la requête. À ce stade, nous n'avons pas encore créé la fonction newTea, mais nous allons le faire maintenant.

### Dans controllers / tea.js:

```
// nouvelleFonction thé pour la route du thé
const newTea = (req, res, next) => {
    res.json({message: "POST new tea"}); // fonction exemple pour le moment
};

module.exports = {newTea};
```

Dans notre contrôleur de thé, nous créons la fonction newTea pour gérer la requête POST '/ tea'. Pour l'instant, il imprimera un message. Ensuite, nous exportons cette fonction afin de pouvoir l'importer dans nos routes / tea.js, comme indiqué précédemment. Super, maintenant votre premier route et son contrôleur sont créés avec succès! Ajoutons les routes au serveur pour qu'il puisse y accéder.

Notre server.js du premier article est maintenant mis à jour avec 2 lignes:


- 
routes const = require ('./ routes / tea'); pour importer les routes / tea.js

- 
ʻApp.use ('/', routes); pour les utiliser via express.

### Maintenant, server.js devrait ressembler à:

```
const express = require ('express');
const routes = require('./routes/tea'); // import the routes

const app = express();

app.use(express.json());

app.use('/', routes); //to use the routes

const listener = app.listen(process.env.PORT || 3000, () => {
    console.log('Your app is listening on port ' + listener.address().port)
})
```
## Étape 3: Test avec POSTman

D'accord, c'est donc le moyen le plus simple d'écrire une route et son contrôleur! Mais maintenant, comment savons-nous que cela fonctionne? En programmation back-end, nous n'avons généralement pas d'interface utilisateur à tester sur le navigateur ...

C'est là qu'intervient POSTman. C'est un excellent outil gratuit pour tester les API. Pour commencer, téléchargez POSTman  [ici](https://www.postman.com/downloads/) .

Ensuite, nous exécutons notre server.js et l'exécutons sur le port 3000 avec le serveur server.js. Une fois que le serveur est en cours d'exécution, la console doit afficher:

```
Your app is listening on port 3000 //Votre application écoute sur le port 3000
```
De retour dans POSTman, entrez l'url comme `http://localhost:3000/tea`, définissez la méthode sur POST et cliquez sur Envoyer. Reportez-vous à l'image ci-dessous. 


![D2zkxII3i.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1604844540018/UjRbJ6GxT.png)

Comme le montre l'image ci-dessus, la réponse à la demande concernant le message comme prévu, ce qui signifie que cela fonctionne! Wow! Nous avons réussi notre première route et notre premier contrôleur!

Maintenant, nous devons juste ajouter tous les autres points de terminaison pour notre route `/tea` tels que GET et DELETE. Comme indiqué dans l'article précédent, nous avons également une route `/tea/:name` pour OBTENIR, CREER et SUPPRIMER un objet thé individuel. Commençons aussi par les ajouter!

>N'hésitez pas à vous arrêter à cette étape pour essayer de les écrire vous-même. C'est la même logique que la première que nous avons écrite.

 ## **Veuillez patienter, codage en cours ... **


![O1gFC1uPm.gif](https://cdn.hashnode.com/res/hashnode/image/upload/v1604844784391/GcS1Sf4n_.gif)

## Étape 4: créer tous les itinéraires et points de terminaison d'API.

Voici à quoi ressemble routes `/tea.js` à la fin de cette étape.

### Routes `/tea.js`

```
const express = require('express');
const router  = express.Router();
const teaController = require('../controllers/tea');

router.get('/tea', teaController.getAllTea);
router.post('/tea', teaController.newTea);
router.delete('/tea', teaController.deleteAllTea);

router.get('/tea/:name', teaController.getOneTea);
router.post('/tea/:name', teaController.newComment);
router.delete('/tea/:name', teaController.deleteOneTea);

module.exports = router;
```

Tout comme ce que nous avons fait pour notre route POST /tea, nous créons les routes GET et DELETE `/tea` de la même manière et ajoutons les fonctions de contrôleur `getAllTea` et `deleteAllTea` pour gérer la demande.

De même, nous créons les routes GET, POST et DELETE pour `/tea /:name`, avec leurs fonctions de contrôleur correspondantes `getOneTea`, `newComment` et `deleteOneTea`. Prenez votre temps pour lire le code pour le comprendre.

Jetons un coup d'œil aux fonctions du contrôleur pour chaque route. Pour l'instant, ils renverront tous simplement un message json décrivant ce qu'ils sont censés faire. Prenez votre temps pour lire et comprendre les fonctions.

### Controleur /tea.js

```
//GET '/tea'
const getAllTea = (req, res, next) => {
    res.json({message: "GET all tea"});
};

//POST '/tea'
const newTea = (req, res, next) => {
    res.json({message: "POST new tea"});
};

//DELETE '/tea'
const deleteAllTea = (req, res, next) => {
    res.json({message: "DELETE all tea"});
};

//GET '/tea/:name'
const getOneTea = (req, res, next) => {
    res.json({message: "GET 1 tea"});
};

//POST '/tea/:name'
const newComment = (req, res, next) => {
    res.json({message: "POST 1 tea comment"});
};

//DELETE '/tea/:name'
const deleteOneTea = (req, res, next) => {
    res.json({message: "DELETE 1 tea"});
};

//export controller functions
module.exports = {
    getAllTea, 
    newTea,
    deleteAllTea,
    getOneTea,
    newComment,
    deleteOneTea
};
```
## Tester ce que nous avons jusqu'à présent.

Maintenant que tous nos points de terminaison sont terminés, essayez de tester chacun d'eux dans POSTman et assurez-vous qu'il renvoie le message correct.

Remarque pour nos routes `/tea/:name`, nous pouvons fournir une chaîne aléatoire comme paramètre de nom. Pour mon exemple, j'utiliserai «green» comme chaîne de sorte que la route soit `http://localhost:3000/tea/green`.


![q0oaABZlT.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1604845074331/KN8oJxM3Q.png)

### Résumé du test et résultat attendu

<table style="width:100%">
  <tr>
    <th>URL</th>
    <th>Methodes HTTP</th>
    <th>Reponse Message</th>
  </tr>
  <tr>
    <td>http://localhost:3000/tea</td>
    <td>GET</td>
    <td>affiche tous les thés</td>
  </tr>
  <tr>
    <td>http://localhost:3000/tea</td>
    <td>POST</td>
    <td>Cree un nouveau thé</td>
  </tr>
<tr>
    <td>http://localhost:3000/tea</td>
    <td>DELETE</td>
    <td>supprime tous les thés</td>
  </tr>
<tr>
    <td>http://localhost:3000/tea/green</td>
    <td>GET</td>
    <td>Affiche un thé spécifique, en fonction du nom donne qui est green dans notre exemple</td>
  </tr>
<tr>
    <td>http://localhost:3000/tea/green</td>
    <td>POST</td>
    <td>Ajoute un commentaire à un thé spécifique, en fonction du nom donne qui est green dans notre exemple</td>
  </tr>
<tr>
    <td>http://localhost:3000/tea/green</td>
    <td>DELETE</td>
    <td>supprime un thé specifique en fonction du nom donné qui est green dans notre exemple</td>
  </tr>
</table>

Si vous avez réussi tous les tests, tant mieux! L'API est prête pour la partie 3: **intégration avec une base de données***.

# C'est tout pour le moment!

Nous continuerons ce projet d'API en construisant les fonctions du contrôleur et en l'intégrant à MongoDB Atlas dans le prochain article de la série! Merci d'avoir lu et s'il vous plaît laissez un like ou un partage si cela est utile. N'hésitez pas à poser des questions dans les commentaires ci-dessous. Si vous n'êtes pas sûr de certains concepts. Merci