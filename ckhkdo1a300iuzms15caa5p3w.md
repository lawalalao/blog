## Créez une API REST avec Node.js: 
1-2:Module HTTP et Express

Bonjour à tous! Tout d'abord, un immense merci à tous ceux qui m'ont fait de beaux retour et de merveilleux commentaires dès le lancement de cette série d'articles. Je suis tellement heureux que vous soyez autant enthousiasmé par cette série que moi!

Ensuite, passons à la raison pour laquelle j'écris cet article. Un de mes lecteurs qui a lu la partie 1 de la série,  [concevez et planifiez votre API](creez-une-api-rest-avec-nodejs-concevez-et-planifiez-votre-api) , suggère que j'élabore un peu plus sur le module HTTP et pourquoi **nous devons inclure Express** ou tout autre framework Web à utiliser pour notre API. Et donc, voici un mini article non planifié de dernière minute (d'où la partie 1.2) que j'ai rédigé pour tous ceux qui sont curieux de connaître le sujet.

## Le module HTTP

Node.js dispose d'un module HTTP intégré qu'il utilise pour effectuer des requêtes HTTP et transférer des données du serveur vers le client. Voici un diagramme illustrant son fonctionnement.


![diagramme.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1604842535232/fc3fD2Gkj.png)

Selon sa  [documentation](https://nodejs.org/es/docs/guides/anatomy-of-an-http-transaction/) , un processus typique de la façon dont Node.js gère les transactions HTTP est le suivant:


- 
Instancier un serveur HTTP avec une fonction de gestionnaire de requêtes et faites-le écouter sur un port.
 

- 
Obtenir des en-têtes(headers), des URL, des méthodes et des données de corps (body) à partir des objets de requête.

- 
Envoyer des en-têtes, des codes d'état HTTP et des données de corps via des objets de réponse.

- 
Diriger les données des objets de demande et des objets de réponse.

- 
Gérer les erreurs dans les flux de demande et de réponse.

Dans le code, cela ressemble à:

```
//1.
const http = require('http');

//2.
http.createServer((request, response) => {
  const { headers, method, url } = request;
  let body = [];
  request.on('error', (err) => {
    console.error(err);
  }).on('data', (chunk) => {
    body.push(chunk);
  }).on('end', () => {
    body = Buffer.concat(body).toString();

//3.
    response.statusCode = 200;
    response.setHeader('Content-Type', 'application/json');
    const responseBody = { headers, method, url, body };

//4.
    response.write(JSON.stringify(responseBody));

//5.
    response.on('error', (err) => {
      console.error(err);
    });

    response.end();

  });
}).listen(8080);
```

Comme vous pouvez le voir dans le code ci-dessus, cela semble vraiment long et fastidieux à écrire. De plus, ce n'est qu'un exemple squelette. Pour gérer les requêtes avec différentes charges utiles (corps), routes et ajout de middleware, nous aurions à écrire du code plus long et plus fastidieux.

Et donc ... nous utilisons des frameworks Web comme Express pour nous faire **gagner beaucoup de temps** sur l'écriture de code répétitif, car cela facilite la mise en œuvre de routes et l'ajout de middleware. Il ajoute également **une couche de sécurité** à nos applications en éliminant les erreurs humaines (c'est-à-dire ne pas échapper à certains caractères) qui proviennent de la création manuelle d'un serveur avec Node.js.

Écrivons l'équivalent Express de notre code précédent:

```
const express=require('express');
const app=express();

// ajouter le middleware ici

app.get("/", function (req, res) {
  res.send(req.headers, req.originalUrl, req.method, req.body);
});

app.listen(3000, () =>
  console.log('Example app listening on port 3000!'),
);
```

C'est tellement plus concis! Et vous pouvez faire encore plus de choses avec Express, telles que:


- 
ajouter un middleware à tout moment entre l'instanciation de l'application et les routes ou même sur des routes individuelles

- 
ajout de gestionnaires de requêtes avec différentes méthodes HTTP sur différentes routes

- 
envoyer des réponses avec des formats analysés et lisibles

- 
définir les paramètres communs comme le port à utiliser pour la connexion et où rendre la réponse.

# Et voila pourquoi Express est notre héros!

Merci d'avoir lu. J'espère qu'il est maintenant clair pourquoi Express.js ou tout autre framework Web comme Sails.js ou Adonis.js est recommandé d'utiliser lors de la création d'un serveur avec Node. Quelques lectures supplémentaires pour vous si vous voulez en savoir plus sur le module HTTP dans Node ou Express:

 
- 
[Anatomie d'une transaction HTTP dans Node](https://nodejs.org/es/docs/guides/anatomy-of-an-http-transaction/) 
 
- 
[Introduction Express et Node par Mozilla](https://developer.mozilla.org/en-US/docs/Learn/Server-side/Express_Nodejs/Introduction) 
 
- 
[Serveur Node.js sans framework](https://developer.mozilla.org/en-US/docs/Learn/Server-side/Node_server_without_framework) 

>Restez à l'écoute pour la partie 2 de la série! . Passez une bonne journée et Merci!