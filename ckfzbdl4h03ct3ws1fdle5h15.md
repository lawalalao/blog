## Comment démarrer avec NodeJS & Express

Salut , récemment j'ai commencé a faire du backend avec Node js / Express Js... Dans cet article je vous montre comment mettre en place et exécuter un serveur web Express JS.. 

# Étape 1 - Installez NodeJS

Si NodeJS n'est pas déjà installé, vous pouvez le faire en vous rendant sur ce lien  [https://nodejs.org/en/download/](https://nodejs.org/en/)

# Étape 2 - Configurez votre projet

Ensuite, nous devons configurer un projet Node JS de base. Vous pouvez le faire en utilisant Node Package Manager (NPM): 

```
cd myproject
npm init
``` 
Vous pouvez modifier la configuration selon vos goûts..

# Étape 3 - Installez vos dépendances

Dans ce cas, nous avons juste besoin d'express js. Il existe différentes manières d'installer des modules, je vous recommande d'utiliser l'indicateur `--save` pour stocker le module dans votre projet.


```
npm install --save express
``` 

# Étape 4 - Codez et exécutez votre serveur Web

Commençons par créer un fichier index.js et importons le module express:


```
const express = require('express');
``` 
Ensuite, créez une application `app` - ce sera votre instance de serveur Web:


```
const app = express();
``` 
Maintenant, vous pouvez faire toutes sortes de choses avec la variable `app`. Vous pouvez créer des itinéraires, modifier les paramètres, etc. Outre la route `hello world` obligatoire, ces configurations sont hors de portée de ce tutoriel. N'hésitez pas à laisser des commentaires sur ce que nous devrions couvrir ensuite.

Voici le code Hello World:


```
app.get('/', (req, res) => {
  res.send("Hello World!");
});
``` 
Alors qu'est-ce que ça fait? Tout d'abord, nous spécifions une méthode `HTTP`. `GET` est celui utilisé par défaut pour ouvrir les pages Web, d'où app.get (...). Le premier argument est le chemin. Nous spécifions `/` car c'est la page d'accueil ouverte. Cela peut être quelque chose comme `/ ma-page` ou des chemins plus compliqués. Le deuxième argument est une fonction de rappel. Cette fonction est exécutée une fois que quelqu'un demande cette page `/ route Web`. Il y a deux arguments pour cette fonction de rappel,`req` avec les informations de demande du visiteur et `res` avec les informations de réponse que vous renvoyez. Dans ce cas, nous renvoyons `(res.send (...);)` le texte "Hello World!". Cela peut contenir toutes sortes de choses - des images au HTML.

Il ne nous reste plus qu'à exécuter le serveur sur le port par défaut de HTTP:


```
app.listen(80, () => {
  console.log('Running the web server!');
});
``` 
Eh voila! Si vous exécutez maintenant ce script en utilisant `node index.js` dans votre terminal tout en étant dans le répertoire de votre projet, vous devriez voir la page Web de travail sur localhost!

# Bonus - Configuration de SSL / TLS (: https: https :)

Afin d'activer HTTPS, nous devons ajouter quelques lignes de code à la fin. En particulier, nous devons créer une instance HTTPS de `app`, configurer nos certificats SSL / TLS utilisés pour crypter le trafic et exécuter la deuxième instance sur le port 443 (https par défaut).

Dans le cas du code suivant, vous devez télécharger un certificat (server.crt) et une clé (server.key) dans le répertoire de votre projet. Vous pouvez obtenir des certificats SSL aujourd'hui gratuitement, soit en utilisant un service proxy tel que  [cloudflare.com](https://www.cloudflare.com/)  ou  [gentlent.com](https://www.gentlent.com/) , soit en en obtenant un auprès d'une autorité de certification telle que  [zerossl.com](https://zerossl.com/)  (le plus simple) ou  [letsencrypt.org](https://letsencrypt.org/) .

Commencez par importer les modules Node requis en haut:


```
const https = require('https');
const fs = require('fs');
``` 
Après cela, ajoutez le code suivant en bas pour exécuter un serveur HTTPS:


```
https.createServer({
    cert: fs.readFileSync(__dirname + '/server.crt'),
    key: fs.readFileSync(__dirname + '/server.key'),
}, app).listen(port);
``` 
Maintenant, HTTPS devrait être opérationnel. Maintenant, commencez à jouer avec votre code et commencez à apprendre à créer quelque chose de génial!

Faites-nous savoir si cela a fonctionné pour vous et merci de partager l'article avec vos amis.. Prochainement je vous montrerai comment créer une API CRUD(create, read, update, delete) simple avec la base de données MongoDb 