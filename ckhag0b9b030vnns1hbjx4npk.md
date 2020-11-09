## Cinq concepts clés à connaître avant de vous lancer dans le développement Javascript

Avant de commencer à parler de certaines des fonctionnalités de Javascript en tant que langage, ce ne serait pas une hérésie de dire que vous devez tous avoir déjà entendu parler de Javascript. Et il y a de bonnes raisons à cela. Selon l'enquête 2020 de  [Stack Overflow](https://insights.stackoverflow.com/survey/2020)  auprès des développeurs, Javascript est resté huit fois de suite le langage le plus populaire et le plus couramment utilisé. Même l’état  [d’octoverse de Github](https://octoverse.github.com/)  a classé Javascript comme le langage le plus utilisé et est resté cohérent à sa place depuis 2014. Eh bien, qu'est-ce qui rend Javascript si populaire après tout?

Le développement des technologies Web et des frameworks a en outre annoncé l'evolution de Javascript. La montée en puissance des frameworks Front-End de niche comme React et Angular a ouvert une nouvelle voie dans le développement Front-End et des frameworks comme  [NodeJS](https://nodejs.org/en/)  et  [Express](https://expressjs.com/)  sont la cerise sur le gâteau qui a encore stimulé la communauté Javascript. De nombreux développeurs recherchent maintenant des rôles dans le développement Javascript et il y a de bonnes raisons de le faire: en tant que langage, il offre des capacités pour développer des interfaces côté client et côté serveur.
Si vous avez commencé avec Javascript, il y a beaucoup de choses à apprendre avant de vous lancer dans les Frameworks et Bibliothèques. Mais ce n'est pas toujours le cas. Les gens ont tendance à se lancer immédiatement dans le développement avec Javascript, et ils renoncent à la nécessité de maîtriser les bases. Dans cet article, nous allons approfondir cinq des concepts Javascript que vous devez maîtriser avant de vous lancer dans le développement Javascript.

# 1. Fonctions fléchées(Arrow Functions)

La manière la plus désagréable d'écrire des fonctions en Javascript est la manière traditionnelle, où nous déclarons une fonction quelque part, la définissons plus tard, puis nous l'appelons. Mais que se passe-t-il si, nous avons besoin d'une fonction en ligne et nous devons les utiliser une seule fois. Pour écrire de telles fonctions anonymes et rendre nos fonctions plus lisibles, nous pouvons miser sur une nouvelle fonctionnalité que l'ES6 nous fournit: les fonctions fléchées.

Il y a maintenant plusieurs avantages à utiliser les fonctions fléchées dans votre code. Les plus évidents sont que cela rend votre code plus lisible, plus concis et que vous pouvez également écrire des fonctions régulières avec une syntaxe plus courte. Cela paraît bien?

```
/* Syntaxe standard javascript (ES5) */

var multiply = function(a, b) {
  return a * b;
};


 /* fonctions fléchées utilisant syntaxe ES6 */

 var multiply = (a, b) => { return a * b };
```
Comme vous pouvez le voir, vous pouvez facilement utiliser la fonction Flèche pour simplifier davantage la définition et l'utilisation de votre fonction. Si vous n'avez qu'un seul paramètre dans votre définition de fonction, vous pouvez le faire sans avoir besoin de crochets.

Pour les développeurs qui commencent tout juste à se familiariser avec la syntaxe ES6, cette transition peut sembler difficile. Mais vous pouvez simplement suivre deux étapes simples pour convertir votre fonction régulière en une fonction de flèche:


- Supprimez le mot-clé `function ()`.
     
- 
Ajoutez un => juste après le ()

Les fonctions fléchées sont uniquement appelables et non contraignantes, contrairement aux fonctions régulières. Cela signifie simplement que vous pouvez utiliser le nouveau mot-clé avec les fonctions régulières mais pas avec les fonctions fléchées. Avant de travailler avec les fonctions fléchées, n'oubliez pas qu'il s'agit de fonctions anonymes. Si vous souhaitez appeler une fonction de flèche, vous pouvez la définir dans une variable telle que `const`, `var` ou `let`.

# 2. Importation et exportation de modules

Imaginons un fichier que vous avez construit pour vos besoins, en utilisant Javascript. Ce fichier se compose de nombreuses fonctions que vous avez définies et que vous souhaitez maintenant également les utiliser dans d'autres fichiers. Maintenant, c'est en fait le meilleur moyen de développer de nouvelles applications, où vous divisez toute votre base de code en morceaux sains, puis les importez et les exportez comme vous le souhaitez.

Avec Javascript, tout ce processus est simplifié et vous pouvez accéder à vos fichiers en utilisant ces mots-clés simples: importation (`import`) et exportation (`export`). Écrivons un bloc de code dans notre fichier **math-operations.js** et exportons un module pour ajouter deux nombres.

```
const add = (x, y) => {
  return x + y;
}

export { add };
```
Mais comment allons-nous importer ce bloc de code dans un autre fichier? Eh bien, pour cette opération, nous utiliserons le mot-clé `import` et la meilleure partie est que vous n'avez pas besoin de réécrire le code. Cela semble assez facile?

```
import { add } from './math-operations.js';
```

Si vous avez des difficultés à comprendre le but de l'importation et de l'exportation de modules, vous pouvez le comprendre d'une manière légèrement différente. En Javascript, un module est simplement un objet, une variable ou une fonction que vous pouvez exporter à l'aide du mot-clé `export`. Vous pouvez exporter plusieurs modules, mais il ne devrait y avoir qu'une seule exportation par défaut.

Les importations sont effectuées à l'aide du mot-clé `import` et il est exécuté en plaçant, le nom exact entre accolades. N'oubliez pas de rechercher le chemin correct si vous importez localement, sinon vous pouvez utiliser un nom absolu pour récupérer vos `node_modules` pour le package exact.

Voyons un autre exemple d’exportation de notre package:

```
export const sqrt = Math.sqrt;
export function square(x) {
    return x * x;
}
export function diag(x, y) {
    return sqrt(square(x) + square(y));
}
```
On peut savoir importer les packages en les important simplement:

```
import { square, diag } from 'lib';
console.log(square(11)); // 121
console.log(diag(4, 3)); // 5

```

# 3. Promises (promesse) in Javascript

Eh bien, cela semble assez étrange, mais nous avons également ce concept de promesses en Javascript. Pour gérer plusieurs tâches, qui dépendent toutes de l'achèvement des unes des autres, nous pouvons utiliser plusieurs rappels et nous retrouver dans quelque chose que nous appelons un enfer de rappel. Pour résoudre ce problème, nous avons des promesses en Javascript, qui font une promesse asynchrone de faire quelque chose.


![0 UPFgfl7Vie5Yju4M.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1604704966630/ixrBsQnWp.png)

Une promesse `promise` peut être simplement comprise comme un objet qui consiste en un statut et une valeur. Promise sert de constructeur qui prend une fonction comme argument avec deux paramètres: résoudre et rejeter. Ces deux paramètres déterminent l'issue de la promesse.

Javascript est un langage à thread unique, et donc seul un seul morceau de code peut s'exécuter à un moment donné qui doit s'exécuter l'un après l'autre. Donc, avant les promesses, vous utilisiez probablement des événements, async () et des rappels pour contourner cette fonctionnalité JavaScript. Dans Promises, nous ne pouvons réussir ou échouer qu'une seule fois. voir https://lawaltech.hashnode.dev/comment-utiliser-async-await-en-javascript

```
const PostUp =[
    { text:"Post 1", text:"This is Post 1" },
    { text:"Post 2", text:"This is Post 2" }
];

// Getting PostUp takes 1 sec
function getPostUp(){
    setTimeout(() => {
        let output = '';
        PostUp.forEach((post) => {
            output += `${post.text} \n`
        })
        console.log(output);
    },1000)
}

// Creating a post takes 2 sec
function createPost(post){
    return new Promise((resolve, reject) => {
        setTimeout(() => {
            PostUp.push(post);

            const error = false;
            if (!error){
                resolve();
            } else {
                reject("Something went wrong!!");
            }
        },2000)
    })
}

createPost({ text:"Post 3", text:"This is Post 3" })
    .then(getPostUp)
    .catch(err => console.log(err));
```

Dans Promises, nous pouvons avoir trois statuts:

     
- 
**Le statut initial** est indiqué comme étant en attente qui n'est ni rempli ni rejeté.
     
- 
**Le statut Fulfilled** est indiqué comme étant accompli, ce qui signifie que l'opération a été exécutée avec succès.
     
- 
**L'état d'échec** est indiqué comme rejeté, ce qui signifie qu'une erreur a été renvoyée.

L'une des meilleures choses lorsque vous travaillez avec Promises est que cela vous permet d'utiliser `Promise.resolve` ou `Promise.reject` avec la valeur exacte que vous souhaitez représenter.

# 4. Déclaration de variable en Javascript

JavaScript est typé dynamiquement, ce qui signifie simplement que les types peuvent changer au moment de l'exécution. Déclarer des variables avec le mot-clé `var` nous permet d'écraser simplement le type de données de la variable sans enregistrer une erreur. Une nouvelle fonctionnalité de syntaxe ES6 nous permet de figer le type de données de la variable. voir mon article https://lawaltech.hashnode.dev/variables-javascript-var


![0 72IRmXQFi-75FcZR.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1604705274804/18_DxWqt3.png)


Le nouveau mot-clé `let` permet de déclarer les variables et si nous essayons d'utiliser le même nom de variable ailleurs, il lancera immédiatement une erreur. Vous pouvez également utiliser `strict` qui active un mode strict qui peut nous aider à détecter certaines erreurs de codage courantes comme accéder à une variable sans la déclarer.

```
"use strict";
let name = "Hello, World!";  
let number = 7;  
if (number > 4) {  
   let hello = "Hi! What's Up!";   
   console.log(hello) // retour: Hi! What's Up!
}  
console.log(hello) // Erreur: hello n'est pas defini

```
La seule chose que vous devez comprendre à propos du mot-clé `let` en Javascript, c'est qu'il suit les règles de portée standard. La portée de toute variable déclarée avec `let` est limitée uniquement à ce bloc de code.

Vous pouvez également utiliser le mot clé `const` pour déclarer uniquement des variables en lecture seule. Cela signifie qu'une fois qu'un mot clé `const` est utilisé, nous ne pouvons pas lui réaffecter la valeur. Essayer de réaffecter une variable avec `const` provoquera une erreur.

```
const xam = 'Hashnode';
const xam = 'not-hashnode';

// Donne une erreur: 'constant' xam 'a déjà été défini'

```

Si vous commencez par déclarer des variables, vous pouvez commencer par utiliser le mot clé `const` à cet effet. Vous pouvez plus tard refactoriser votre code et convertir `const` en let une fois que vous devez réaffecter la variable.

# 5. Map, Filter and Reduce (Cartographier, filtrer et réduire)

Map, Filter et Reduce est un concept important qui enveloppe votre esprit pour une fois, mais si vous avez bien compris vos bases, ce serait le concept le plus important de votre arsenal Javascript.

Map, Filter et Reduce sont utilisés pour la transformation `Array` et peuvent soit effectuer leurs opérations indépendamment, soit être enchaînés les uns aux autres. Explorons-les tous un par un.

Une **Map** est utilisée pour prendre une fonction et est ensuite appelée sur tous les autres éléments du tableau. Il peut créer un nouveau tableau à partir d'un tableau existant et appeler une fonction pour agir sur chaque élément du tableau. Ça a l'air plutôt cool, n'est-ce pas?

```
const array = [1, 2, 3, 4, 5, 6, 7, 8, 9, 10] 

const newArr = array.map((num) => num*num) 
//newArr = [1, 4, 9, 16, 25, 36, 49, 64, 81, 100]
```
La Map effectue une boucle sur tous les éléments du tableau, transforme chaque élément du tableau et le renvoie.

Un **Filter** prend chaque élément d'un tableau et applique une instruction conditionnelle pour filtrer les éléments du tableau. De cette façon, si nous voulons qu'une condition soit vérifiée dans la boucle, nous n'avons pas besoin de la parcourir entièrement. Nous pouvons simplement utiliser le filtre et extraire les éléments spécifiques correspondant à la condition.

```
const array = [1, 2, 3, 4, 5, 6, 7, 8, 9, 10] 

const newArr = array.filter((num) => num % 2 === 0)
//newArr = [2, 4, 6, 8, 10]
```
Une ***reduce** fait une boucle sur un tableau entier et le convertit en autre chose en utilisant une fonction de transformation. Ce «quelque chose d'autre» est référencé par vous qui est passé comme second argument et il peut être utilisé pour «réduire» le tableau entier en quelque chose de nouveau qui peut être un objet ou une variable. Contrairement à la carte et au filtre, la réduction prend quatre arguments:


    
- 
Accumulator (accumulateur)
    
- 
Current Value (valeur actuel)
    
- 
Current Index (l'index actuel)
    
- 
Source Array (source de l'array)

Voyons un exemple de reduce:

```
function sumOfNum(total, num) {
  return total + num;
}

const arr = [1, 2, 3, 4, 5, 6, 7, 8, 9, 10];

const newArr = arr.reduce(sumOfNum);

```
La raison pour laquelle de nombreux développeurs Javascript utilisent si souvent mapper, réduire et filtrer est qu'ils n'ont pas à parcourir un tableau entier maintenant et qu'ils peuvent être enchaînés les uns aux autres pour une transformation de tableau facile à mettre en œuvre.

# Conclusion

Avec cela, nous arrivons à la fin de certains des concepts les plus importants de Javascript. Il existe en outre des fonctionnalités avec Javascript en général et ES6 en particulier qui nécessitent plus de perspicacité et d'intuition mais dépassent le cadre de cet article. Javascript, en tant que langage, est assez complexe à comprendre au début et travailler autour de lui est assez difficile, même pour les développeurs seniors, si les bases ne sont pas bien faites.

Apprendre Javascript ne signifie pas que vous devez tout maîtriser avant de passer à un framework ou une bibliothèque avec laquelle travailler. Mais des compétences essentielles dans les bases sont tout à fait souhaitables et c'est ce qui a été abordé ici.


> Merci d'avoir lu et j’espère que l'article vous a été utile.
