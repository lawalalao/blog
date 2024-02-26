---
title: "Comment utiliser Google Gemini avec Node.js"
seoTitle: "comment utiliser Gemini avec Node.js"
datePublished: Mon Feb 26 2024 08:50:46 GMT+0000 (Coordinated Universal Time)
cuid: clt2p8d48000809lhb9qae5df
slug: comment-utiliser-google-gemini-avec-nodejs
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1708936289896/6e109326-576f-4837-ad07-0fd0e3f0d0e9.png
tags: javascript, nodejs, beginners, ia, generative-ai

---

L'IA générative a été un sujet brûlant dans la technologie au cours de l'année précédente. Tout le monde construit des projets intéressants en l'utilisant. Google possède sa propre IA générative, appelée Gemini.

Récemment, Google a lancé ses API pour les développeurs Gemini. Ces API sont accompagnées de plusieurs bibliothèques et librairies que les développeurs peuvent utiliser pour les incorporer dans leurs applications.

Dans cet article, nous allons créer une simple application Node.js et y intégrer Google Gemini. Nous utiliserons pour cela le [SDK Google Gemini](https://www.npmjs.com/package/@google/generative-ai).

Alors, sans plus attendre, COMMENÇONS !

# C'est quoi Gemini ?

![Google's Incredible New 'Gemini' SHOCKS The Entire AI Industry! - YouTube](https://i.ytimg.com/vi/wPA5RFtHRnM/maxresdefault.jpg align="left")

Google Gemini est un modèle d'IA puissant et polyvalent développé par Google AI. Gemini ne se contente pas de traiter du texte ; il est capable de comprendre et d'exploiter différents formats tels que le code, l'audio, les images et la vidéo. Cela ouvre des possibilités passionnantes pour vos projets Node.js.

## Configuration du projet :

1. **Créer un projet Node.js** :
    

Pour démarrer notre projet, nous devons mettre en place un environnement Node.js. Créons donc un projet Node. Exécutez la commande suivante dans le terminal.

```powershell
npm init
```

Cette commande initialise un projet Node.js

1. ### Installer les dépendances :
    

Nous allons maintenant installer les dépendances nécessaires à notre projet.

```powershell
npm install express body-parser @google/generative-ai dotenv
```

Cela installera les paquets suivants :

* **express** : un framework web populaire pour Node.js
    
* **body-parser** : middleware pour analyser les corps des requêtes
    
* **@google/generative-ai** : un paquetage pour accéder au modèle Gemini
    
* **dotenv** : charge les variables d'environnement à partir d'un fichier <mark>.env</mark>
    

1. ### Configurer les variables d'environnement :
    

Ensuite, nous allons créer un dossier <mark>.env</mark> pour stocker en toute sécurité nos informations sensibles telles que les informations d'identification de l'API.

```powershell
//.env
API_KEY = VOTRE_CLE_API
PORT=3000
```

1. ### Obtenir la clé API :
    

Avant d'utiliser Gemini, nous devons configurer les informations d'identification de l'API à partir de la Google Developers Console. Pour cela, nous devons nous connecter à notre compte Google et créer une clé API.

Une fois connecté, allez sur https://makersuite.google.com/app/apikey. Vous obtiendrez quelque chose comme ceci :  

![Image of Google AI Studio Console](https://res.cloudinary.com/practicaldev/image/fetch/s--0JJ9cIY7--/c_limit%2Cf_auto%2Cfl_progressive%2Cq_auto%2Cw_800/https://cdn.hashnode.com/res/hashnode/image/upload/v1707836987343/d339372d-195e-47f7-80a0-dc33fef00428.png align="left")

Nous cliquerons ensuite sur le bouton Créer une clé API. Cela générera une clé d'API unique que nous utiliserons pour authentifier les demandes adressées à l'API Google Generative AI.

> Pour tester votre API, vous pouvez exécuter la commande Curl suivante :
> 
> ```powershell
> curl \
>   -H 'Content-Type: application/json' \
>   -d '{"contents":[{"parts":[{"text":"Write a story about a magic backpack"}]}]}' \
>   -X POST https://generativelanguage.googleapis.com/v1beta/models/gemini-pro:generateContent?key=VOTRE_CLE_API
> ```
> 
> Remplacez VOTRE\_CLE\_API par la clé d'API que nous avons obtenue précédemment.

Après avoir obtenu la clé API, nous mettrons à jour notre fichier `.env`

1. ### Créer un serveur Express:
    

Maintenant, nous allons créer un fichier <mark>index.js</mark> dans le répertoire racine et mettre en place un serveur express de base. Voir le code suivant :

```javascript
const express = require("express");
const dotenv = require("dotenv");

dotenv.config();

const app = express();
const port = process.env.PORT;

app.get("/", (req, res) => {
  res.send("Hello World");
});

app.listen(port, () => {
  console.log(`Server running on port ${port}`);
});
```

Ici, nous utilisons le paquetage "<mark>dotenv</mark>" pour accéder au <mark>PORT</mark> du fichier <mark>.env.</mark>

Au début du projet, nous chargeons les variables d'environnement en utilisant <mark>dotenv.config()</mark> pour les rendre accessibles dans tout le fichier.

### 6\. Lancer le projet:

Dans cette étape, nous allons ajouter un script de démarrage au fichier <mark>package.json</mark> pour lancer facilement notre projet.

Ajoutez donc le script suivant au fichier <mark>package.json.</mark>

```json
"scripts": {
  "start": "node index.js"
}
```

Le fichier <mark>package.json</mark> doit ressembler à ceci :

[![package.json File](https://res.cloudinary.com/practicaldev/image/fetch/s--ypLZ6-6N--/c_limit%2Cf_auto%2Cfl_progressive%2Cq_auto%2Cw_800/https://cdn.hashnode.com/res/hashnode/image/upload/v1707982485800/c23cbb23-68c6-4f6b-942d-dad0dfe9c3fb.png align="left")](https://res.cloudinary.com/practicaldev/image/fetch/s--ypLZ6-6N--/c_limit%2Cf_auto%2Cfl_progressive%2Cq_auto%2Cw_800/https://cdn.hashnode.com/res/hashnode/image/upload/v1707982485800/c23cbb23-68c6-4f6b-942d-dad0dfe9c3fb.png)

Pour vérifier si tout fonctionne ou non, exécutons le projet à l'aide de la commande suivante :

```powershell
npm run start
```

Cela démarre le serveur Express. Si nous nous rendons à l'URL [http://localhost:3000/](http://localhost:3000/), nous obtiendrons ceci :

![Image of http://localhost:3000/](https://res.cloudinary.com/practicaldev/image/fetch/s--W2-VU0GM--/c_limit%2Cf_auto%2Cfl_progressive%2Cq_auto%2Cw_800/https://cdn.hashnode.com/res/hashnode/image/upload/v1707838639217/c4d08730-7534-4ad5-a0fd-5962d3eb7cc6.png align="left")

## Ajout de Google Gemini :

1. ### Configurer la route et le middleware :
    

Pour ajouter le Gemini à notre projet, nous allons créer une route <mark>/generate</mark> où nous communiquerons avec l'IA Gemini.

Pour cela, ajoutez le code suivant dans le fichier <mark>index.js</mark>.

```javascript
const bodyParser = require("body-parser");
const { generateResponse } = require("./controllers/index.js");

//middleware to parse the body content to JSON
app.use(bodyParser.json());

app.post("/generate", generateResponse);
```

Ici, nous utilisons un middleware <mark>body-parser</mark> pour analyser le contenu au format <mark>JSON</mark>.

1. **Configurez Google Generative AI** :
    

Maintenant, nous allons créer un dossier <mark>controller</mark> et à l'intérieur de celui-ci, nous allons créer un fichier <mark>index.js</mark>. Ici, nous allons créer une nouvelle fonction pour gérer la route déclarée dans le code ci-dessus.

```javascript
const { GoogleGenerativeAI } = require("@google/generative-ai");
const dotenv = require("dotenv");

dotenv.config();

// Configuration requise pour GoogleGenerativeAI
const configuration = new GoogleGenerativeAI(process.env.API_KEY);

// initialisation de modèle
const modelId = "gemini-pro";
const model = configuration.getGenerativeModel({ model: modelId });
```

Ici, nous créons un objet de configuration pour l'API en transmettant la clé API à partir des variables d'environnement.

Ensuite, nous initialisons le modèle en fournissant l'ID du modèle ("<mark>gemini-pro</mark>") à la méthode **<mark>getGenerativeMode</mark>**l de l'objet de configuration.

> #### Configurations du modèle :
> 
> Nous pouvons également configurer les paramètres du modèle à notre convenance
> 
> Ces valeurs de paramètres contrôlent la manière dont le modèle génère une réponse.
> 
> Exemple :
> 
> ```javascript
> const generationConfig = {
>   stopSequences: ["red"],
>   maxOutputTokens: 200,
>   temperature: 0.9,
>   topP: 0.1,
>   topK: 16,
> };
> 
> const model = configuration.getGenerativeModel({ model: modelId, generationConfig });
> ```
> 
> #### Paramètres de sécurité :
> 
> Nous pouvons utiliser les paramètres de sécurité pour éviter de recevoir des réponses nuisibles. Par défaut, les paramètres de sécurité sont configurés pour bloquer les contenus dont la probabilité d'être dangereux est moyenne ou élevée selon différents critères.
> 
> Voici un exemple :
> 
> ```javascript
> const { HarmBlockThreshold, HarmCategory } = require("@google/generative-ai");
> 
> const safetySettings = [
>   {
>     category: HarmCategory.HARM_CATEGORY_HARASSMENT,
>     threshold: HarmBlockThreshold.BLOCK_ONLY_HIGH,
>   },
>   {
>     category: HarmCategory.HARM_CATEGORY_HATE_SPEECH,
>     threshold: HarmBlockThreshold.BLOCK_MEDIUM_AND_ABOVE,
>   },
> ];
> 
> const model = genAI.getGenerativeModel({ model: "MODEL_NAME", safetySettings });
> ```
> 
> Grâce à ces paramètres de sécurité, nous pouvons renforcer la sécurité en réduisant la probabilité de génération de contenu nuisible.

1. ### Gérer l'historique des conversations :
    

Pour conserver l'historique de la conversation, nous avons créé un tableau historique et l'avons exporté depuis le fichier du contrôleur :

```javascript
export const history = [];
```

1. ### Mise en œuvre de la fonction de contrôleur :
    

Nous allons maintenant écrire une fonction contrôleur <mark>generateResponse</mark> pour gérer la route de génération <mark>(/generate</mark>) et générer une réponse aux demandes des utilisateurs.

```javascript
/**
 * Génère une réponse sur la base de demande de l'utilisateur.
 * @param {Object} req - L'objet de requête.
 * @param {Object} res - L'objet de reponse.
 * @returns {Promise} - Une promesse qui se résout lorsque la réponse est envoyée.
 */
export const generateResponse = async (req, res) => {
  try {
    const { prompt } = req.body;

    const result = await model.generateContent(prompt);
    const response = await result.response;
    const text = response.text();
    console.log(text);

    history.push(text);
    console.log(history);

    res.send({ response: text });
  } catch (err) {
    console.error(err);
    res.status(500).json({ message: "Internal server error" });
  }
};
```

Ici, nous prenons la demande dans le corps de la requête et générons une réponse basée sur cette demande à l'aide de la méthode <mark>model.generateContent.</mark>

Et pour garder une trace des réponses, nous poussons les réponses dans le tableau d'historique..

1. ### Vérifier l'historique des réponses:
    

Maintenant, nous allons créer une route pour vérifier l'historique de nos réponses. Ce point d'accès renvoie le tableau de l'historique.

Ajoutez le code simple au dossier <mark>./index.js</mark>.

```javascript
app.get("/generate", (req, res) => {
  res.send(history);
});
```

Et c'est fini !

1. ### Exécutez le projet :
    

Maintenant, nous devons vérifier si notre application fonctionne correctement ou non !

Exécutons notre projet en utilisant :

```powershell
npm run start
```

[![Terminal output](https://res.cloudinary.com/practicaldev/image/fetch/s--jX4RZRIz--/c_limit%2Cf_auto%2Cfl_progressive%2Cq_auto%2Cw_800/https://cdn.hashnode.com/res/hashnode/image/upload/v1707855196139/694e7c44-39c4-4ee7-8080-51e0a429c8ec.png align="left")](https://res.cloudinary.com/practicaldev/image/fetch/s--jX4RZRIz--/c_limit%2Cf_auto%2Cfl_progressive%2Cq_auto%2Cw_800/https://cdn.hashnode.com/res/hashnode/image/upload/v1707855196139/694e7c44-39c4-4ee7-8080-51e0a429c8ec.png)

Pas d'erreurs ! Dieu merci : ) Cela fonctionne correctement.

1. ### Vérifier la fonctionnalité
    

Ensuite, nous allons effectuer une requête Post à l'aide de Postman pour valider la fonction de notre contrôleur.

Nous enverrons une requête POST à [http://localhost:3000/generate](http://localhost:3000/generate) avec la charge utile JSON suivante :

```json
{
  "prompt": "Write 3 Javascript Tips for Beginners"
}
```

[![Postman Console Output](https://res.cloudinary.com/practicaldev/image/fetch/s--X8vY7idJ--/c_limit%2Cf_auto%2Cfl_progressive%2Cq_auto%2Cw_800/https://cdn.hashnode.com/res/hashnode/image/upload/v1707855502196/bb379294-e966-4fa1-b08d-057f852b8c1a.png align="left")](https://res.cloudinary.com/practicaldev/image/fetch/s--X8vY7idJ--/c_limit%2Cf_auto%2Cfl_progressive%2Cq_auto%2Cw_800/https://cdn.hashnode.com/res/hashnode/image/upload/v1707855502196/bb379294-e966-4fa1-b08d-057f852b8c1a.png)

Et nous avons reçu notre réponse :

```json
{
    "response": "1. **Use console.log() for Debugging:**\n   - console.log() is a useful tool for debugging your JavaScript code. It allows you to inspect the values of variables and expressions, and to see how your code is executing. This can be especially helpful when you encounter errors or unexpected behavior in your program.\n\n2. **Learn the Basics of Data Types:**\n   - JavaScript has several built-in data types, including strings, numbers, booleans, and objects. Understanding the properties and behaviors of each data type is crucial for writing effective code. For instance, strings can be manipulated using string methods, while numbers can be used in mathematical operations.\n\n3. **Use Strict Mode:**\n   - Strict mode is a way to opt-in to a restricted and secure subset of JavaScript. It helps you to write more secure and reliable code, as it throws errors for common mistakes that would otherwise go unnoticed in regular JavaScript mode. To enable strict mode, simply add \"use strict;\" at the beginning of your JavaScript file or module."
}
```

[![Postman Console Output](https://res.cloudinary.com/practicaldev/image/fetch/s--XFTkjxmC--/c_limit%2Cf_auto%2Cfl_progressive%2Cq_auto%2Cw_800/https://cdn.hashnode.com/res/hashnode/image/upload/v1707855825387/a186b78f-e6d9-4197-8b00-ce55766a2e16.png align="left")](https://res.cloudinary.com/practicaldev/image/fetch/s--XFTkjxmC--/c_limit%2Cf_auto%2Cfl_progressive%2Cq_auto%2Cw_800/https://cdn.hashnode.com/res/hashnode/image/upload/v1707855825387/a186b78f-e6d9-4197-8b00-ce55766a2e16.png)

Super ! Notre intégration Gemini fonctionne comme prévu !

De plus, nous pouvons accéder au point de terminaison de l'historique à l'adresse [http://localhost:3000/generate](http://localhost:3000/generate) pour consulter l'historique de la conversation.

Avec cela, nous avons intégré Gemini AI dans notre application Node.js. Dans les prochains articles, nous explorerons d'autres cas d'utilisation de Gemini AI.

D'ici là, Portez-vous bien.

## Conclusion

Si vous avez trouvé cet article utile, n'hésitez pas à le partager avec d'autres personnes qui pourraient en bénéficier. Vous pouvez également me suivre pour plus de contenu des sujets liés à la technologie.

Merci de m'avoir lu :)

![Merci ! - Dianego RH](https://www.dianego-rh.com/wp-content/uploads/2019/07/merci2.jpg align="left")