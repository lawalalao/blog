## API NodeJS CRUD avec MongoDB

Si vous avez été dans le monde du développement Web, les chances sont: vous avez déjà entendu parler de NodeJS et MongoDB. La page officielle de NodeJS le définit comme : Node.js® est un moteur d'exécution JavaScript basé sur le moteur JavaScript V8 de Chrome. En outre, MongoDB est l'une des bases de données NoSQL les plus populaires. comme promis dernièrement ,Dans cet article, nous allons développe une API  CRUD sur MongoDB en utilisant NodeJS avec des outils express & mangoose.

## Prérequis

Si vous voulez commencer, je suppose que vous avez déjà configuré un cluster MongoDB et que vous avez l'URL de connexion. Sinon, vous pouvez trouver comment le configurer dans mon  [article précédent,](https://lawaltech.hashnode.dev/premiers-pas-avec-mongodb)  il vous guidera étape par étape sur la configuration du cluster gratuit MongoDB. Je suppose également que vous avez des connaissances basiques avec NodeJS et express sinon vous pouvez le voir ici aussi  [https://lawaltech.hashnode.dev ](https://lawaltech.hashnode.dev/comment-demarrer-avec-nodejs-and-express) .

## Configurations

Pour commencer, la première chose que nous allons faire est de créer la structure de fichiers. Je vous suggère de créer un dossier racine `root`, puis à l'intérieur du dossier racine, de créer les sous-dossiers suivants:


![za.jpeg](https://cdn.hashnode.com/res/hashnode/image/upload/v1601993780711/NukQiUyod.jpeg)

## Installation des dépendances (packages)

Maintenant, pour commencer, nous devons d'abord créer un fichier server.js, puis installer quelques dépendances requises. Ainsi dans notre terminal,


```
cd my-project // dossier racine de mon projet
npm init -y


touch server.js
touch .env
mkdir controllers
mkdir models
mkdir routes

npm install express mongoose dotenv cors body-parser
``` 
Cela complétera notre structure de dossiers et l'installation des dépendances. Maintenant, la prochaine étape sera d'obtenir notre URI de connexion mongoDB et de le placer dans un fichier .env. Pour ce faire, ouvrez votre fichier .env et modifiez-le comme:


```
DB = "YOUR_CONNECTION_STRING_HERE" // données de connection

``` 

## Configuration du serveur et des routes

Maintenant, éditons notre fichier server.js afin de configurer les routes. Copiez et collez le code suivant dans votre fichier server.js:


```
const express = require("express");
const bodyParser = require("body-parser");
const cors = require("cors");
const mongoose = require("mongoose");

require("dotenv").config();

const app = express();

const routes = require("./app/routes");

var corsOptions = {
  origin: "http://localhost:8081",
};

app.use(cors(corsOptions));

app.use(bodyParser.json());

app.use(bodyParser.urlencoded({ extended: true }));

let DB = process.env.DB;

mongoose
  .connect(DB, { useNewUrlParser: true, useUnifiedTopology: true })
  .then(() => console.log("mongoDB connected Successfully"))
  .catch((err) => console.log(err));

app.use("/api/notes", routes);

const PORT = process.env.PORT || 8080;

app.listen(PORT, () => {
  console.log(`Server is running on port ${PORT}`);
});
``` 
Ce que nous faisons ici est:   
- 

importer les dépendances requises
    
- 
Importer des itinéraires (que nous n'avons pas encore créés mais le sera bientôt)
     
- 
Connexion à mongoDB

##  Créer des models

Puisque nous utilisons MongoDB et Mongoose, nous devons avoir des `models`. Dans cette application, nous n'aurons qu'un seul models `NotesModel` qui contiendra les champs de nos notes. Créez donc un fichier NotesModel.js dans le dossier models et collez le code suivant:


```
const mongoose = require("mongoose");

const NotesSchema = new mongoose.Schema(
  {
    title: String,
    description: String,
  },
  { timestamps: true }
);

const Note = mongoose.model("Note", NotesSchema);
module.exports = Note;
``` 
Donc, essentiellement, nous avons juste 2 champs `titre et description` des types chaînes de caractère pour garder les choses simples. Les `timestamps` ont également été définis sur true, ce qui enregistrera la date de création et de modification.

## Création d'un routeur et d'un contrôleur

Maintenant, le server.js est tout configuré, nous pouvons commencer à configurer notre contrôleur et notre routeur. Dans le dossier du contrôleur, créez un fichier `index.js` et collez le code suivant:


```
const NotesModel = require("../models/NotesModel");

exports.findAll = async (req, res) => {
  try {
    const notes = await NotesModel.find({});
    res.send(notes);
  } catch (error) {
    res.status(500).send({
      message: error.message || "Some error occured while retrieving Notes",
    });
  }
};

exports.create = async (req, res) => {
  const Note = req.body;

  try {
    let NoteDoc = new NotesModel(Note);
    await NoteDoc.save();
    res.send(Note);
  } catch (error) {
    res.status(500).send(error);
  }
};

exports.findOne = async (req, res) => {
  const id = req.params.id;

  try {
    let Note = await NotesModel.findById(id);
    res.send(Note);
  } catch (error) {
    res.status(500).send(error);
  }
};

exports.update = async (req, res) => {
  let { ...data } = req.body;
  const result = await NotesModel.findOneAndUpdate(
    { _id: req.params.id },
    data,
    {
      new: true,
    }
  );

  res.send(result);
};

exports.delete = async (req, res) => {
  try {
    let id = req.params.id;

    await NotesModel.findByIdAndDelete(req.params.id);

    res.status(200).send();
  } catch (error) {
    res.status(500).send(error);
  }
};
``` 
Cette partie contient la logique de création, lecture, mise à jour et suppression de données de ` / ` vers notre base de données. Maintenant, pour que cela fonctionne, nous devons l'apporter dans le fichier de routes et le mapper aux méthodes `/ chemins` appropriés. Pour ce faire, créez un fichier appelé `index.js` dans le dossier routes et collez le code suivant:


```
// importer le serveur
const express = require("express");

// importer la router Express
const router = express.Router();

// Import the Controller
const controller = require("../controllers");

// Crée une nouvelle Note
router.post("/", controller.create);

// reçoit/renvoi toutes les notes
router.get("/", controller.findAll);

// reçoit/renvoi une note par Id
router.get("/:id", controller.findOne);

// Modifie une Note existante
router.put("/:id", controller.update);

// Supprime la Note par Id
router.delete("/:id", controller.delete);

module.exports = router;
``` 
Maintenant que tout a été configuré, vous pouvez simplement exécuter:


```
node server.js
```
Le serveur démarrera et écoutera le port: 8080. Vous pouvez utiliser Postman pour tester les API.

Le projet complet se trouve sur mon répertoire  [github ](https://github.com/lawalalao/simpleAPIcrud) 




> 
Si vous aimez lire mes articles, pensez à vous abonner à la newsletter afin d'être averti chaque fois que je publie un nouvel article.