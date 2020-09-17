## Démarrer avec Vue JS

VueJS est un framework Javascript moderne qui facilite la gestion du flux de données, simplement en incluant des attributs dans vos balises HTML.

Dans ce guide, nous allons créer une application de liste de tâches simple pour être opérationnelle avec VueJS.

## Configuration et installation

Il existe deux façons de configurer Vue: via un projet NodeJS, ou en incluant un script à l'intérieur de votre fichier HTML. Puisque nous ne faisons que commencer, nous utiliserons un script dans notre fichier index.html.

 Vous pouvez configurer votre fichier index.html comme ceci.


```
<!DOCTYPE  html>
<html lang="en">
  <head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Todooey - A Simple Todo List App</title>
    <link rel="stylesheet" href="style.css">
    <script src="https://unpkg.com/vue"></script>
  </head>
  <body>
    <div id="app">
    </div>
  </body>
</html>

``` 
Pour utiliser Vue dans notre application, nous devons créer une nouvelle instance de Vue. Nous pouvons le faire en utilisant une autre balise  `script` avant la balise de fermeture du `body`.


```
<script>
  new Vue( {
    el: '#app',
  });
</script>

``` 
maintenant nous pouvons utiliser Vue dans notre application.

## Créons notre application.

Avant d'ajouter la fonctionnalité à notre application avec Vue, nous allons créer la structure HTML / CSS de base avec du contenu statique.

À l'intérieur de notre fichier HTML, nous allons créer l'entrée 'ajouter` de `Todo,` ainsi que la liste des taches `Todo` ainsi que chaque élément.


```
<div class="container">
  <h1 class="">My Todo List</h1>
  <div class="card">
    <div class="flex">
      <input placeholder="Add new todo" />
        <button>Add</button>
    </div>
  </div>
  <div class="card">
    <div class="card-inner">
      <h2>Todo</h2>
      <ul class="list">
        <li class="list-item">
          <div class="list-item-toggle"></div><span>Wash the car</span>
          <div class="list-item-delete">X</div>
        </li>
      </ul>
    </div>
  </div>
</div>

``` 

Ensuite ajoutons un peu de style a notre application grâce au fichier `style.css`


```
html,
body {
  margin: 0;
  padding: 0;
  background: #faffff;
  font-size: 16px;
}

* {
  box-sizing: border-box;
  font-family: -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, Oxygen,
        Ubuntu, Cantarell, 'Open Sans', 'Helvetica Neue', sans-serif;
  color: #3d4855;
}

h1,
h2,
h3,
h4,
h5,
h6 {
  margin-top: 0;
}

.container {
  padding: 24px 0;
  max-width: 700px;
  width: 100%;
  margin: 0 auto;
}

.card {
  border-radius: 4px;
  box-shadow: 1px 1px 40px -10px #31505f30, 0px 1px 2px 0px #31505f30;
  background: white;
  margin-bottom: 24px;
}

.card-inner {
  padding: 16px 24px;
}

.flex {
  display: flex;
  align-items: center;
  justify-content: space-between;
}

input {
  border-radius: 4px;
  background: transparent;
  border: none;
  width: 100%;
  padding: 14px;
  font-size: 16px;
  border: 1px solid transparent;
  height: 100%;
  display: block;
  outline: none;
}

button {
  background: #4fc08d;
  padding: 10px 22px;
  border: none;
  color: white;
  border-radius: 4px;
  margin: 8px;
  font-size: 16px;
  cursor: pointer;
  box-shadow: 1px 1px 15px -2px #212c4430;
  transition: 0.15s;
}

button:hover {
  background: #42aa7b;
}

button:disabled {
  background: #e8e8e8;
  color: #555;
  box-shadow: none;
}

.list {
  list-style: none;
  margin: 0;
  padding: 0;
}

.list-item {
  padding: 12px 16px 12px 16px;
  border: 1px solid #e8e8e8;
  cursor: pointer;
  display: flex;
  align-items: center;
  justify-content: flex-start;
  margin-bottom: 6px;
  border-radius: 4px;
}

.list-item:first-child {
  border-top: 1px solid #e8e8e8;
}

.list-item-toggle {
  border: 1px solid #e8e8e8;
  border-radius: 999px;
  height: 21px;
  width: 21px;
  margin-right: 16px;
}

.list-item-delete {
  margin-left: auto;
  color: tomato;
  margin-top: -2px;
  font-weight: bold;
  text-decoration: none !important;
}

.list-item.completed {
  border: 1px solid #4fc08d;
}

.list-item.completed span {
  text-decoration: line-through;
}

.list-item.completed .list-item-toggle {
  background: #4fc08d;
  border: #4fc08d;
``` 
## Utilisation de Vue pour ajouter des fonctionnalités

Génial! Maintenant que notre application est stylée, nous pouvons commencer à utiliser `Vue` pour créer une liste de tâches dynamique.

## Affichage de notre liste de tâches `Todo` .

Pour afficher notre liste de tâches, nous profiterons du flux de données bidirectionnel de `Vue`. À l'intérieur de notre balise de script, nous utiliserons l'objet de données de `Vue` pour créer un tableau qui contiendra tous nos éléments `todo`.


```
<script>
  new Vue( {
    el: '#app',
    data: {
      items: [
         {
           id: 1,
           name: 'Clean the fridge'
         },
         {
           id: 2,
           name: 'Walk the dogs'
         },
      ]
    }
  });
</script>

``` 

Chaque élément de `todo` a un nom et un ID, qui seront utilisés pour supprimer des éléments de la listes plus tard.

Maintenant que nous avons nos données, nous pouvons les afficher dans notre liste en utilisant l'attribut `v-for`, qui est essentiellement une boucle `forEach` utilisée par Vue.


```
<ul class="list">
  <li class="list-item" v-for="item in reversedItems">
    ...
    <span>{{ item.name }}</span>
    ...
  </li>
</ul>

``` 
L'utilisation de l'attribut `v-for` nous permet d'accéder à la propriété `item`. Nous pouvons afficher le nom en utilisant la syntaxe du double accolade: `{{item.name}}`.

## Ajouter des éléments Todo.

Maintenant que nos éléments s'affichent correctement, nous pouvons travailler sur l'ajout de nouveaux éléments à la liste. En utilisant la propriété `methods` de Vue, nous pouvons créer une méthode qui ajoute un nouveau todo à la liste.

Tout d'abord, créons une nouvelle propriété à l'intérieur de notre objet de données `data`, appelée `newItem`.


```
<script>
  new Vue( {
    el: '#app',
    data: {
      newItem: '',
      items: [...]
    }
  });

</script>

``` 
Ce sera la valeur que nous entrons dans l'entrée `Add Todo`.

Afin de nous assurer que ce que nous tapons dans notre entrée met à jour la valeur `newItem`, nous pouvons tirer parti du flux de données bidirectionnel de Vue, en utilisant l'attribut `v-model`. Cela signifie que quelle que soit la valeur que nous entrons;l'entrée sera conservée dans l'objet de données `data`.

```
<input v-model="newItem" placeholder="Add new todo"  />

```
Puisque nous avons maintenant notre valeur `newItem` stockée, nous pouvons créer une méthode pour ajouter cet élément à la liste.

Sous l'objet de données `data`, nous allons créer un nouvel objet `methods` avec une fonction, `addItem`.


```
<script>
  new Vue( {
    el: '#app',
    data: {...},
    methods: {
      addItem: function() {
        this.items.push({
          id: this.items.length + 1,
          name: this.newItem,
          completed: false,
        });
        this.newItem = '';
      },
    },
  });
</script>

``` 

Fondamentalement, lorsque cette fonction est appelée, nous prenons la valeur `newItem` et la poussons vers le tableau `items`. Nous effaçons la valeur `newItem`, ce qui efface notre entrée Ajouter `Todo`.

Maintenant, tout ce que nous devons faire est d'appeler la fonction lorsque nous cliquons sur le bouton Ajouter. Nous pouvons utiliser l'attribut `v-on`, ou le symbole `@` pour faire court.


```
<button @click="addItem">Add</button>

``` 

Maintenant, `Vue` saura appeler la fonction `addItem` lorsque ce bouton sera cliqué.

En plus, nous pouvons également désactiver le bouton s'il n'y a pas de valeur dans l'entrée, en utilisant l'attribut: `disabled`. Cela indique à `Vue` d'appliquer l'attribut désactivé uniquement si l'expression à l'intérieur des quotes est vraie.


```
<button @click="addItem" :disabled="newItem.length === 0">Add</button>
``` 

## Marquer les éléments comme terminés.

La dernière chose que nous devons faire est d'ajouter la possibilité de marquer nos éléments comme terminés.

Pour ce faire, nous allons ajouter une nouvelle propriété à chaque élément de notre tableau: la propriété `completed`.


```
<script>
new Vue({
  el: '#app',
  data: {
    items: [{
      id: 1,
      name: 'Clean the fridge',
      completed: true,
    },
    {
      id: 2,
      name: 'Walk the dogs',
      completed: false,
    }]
  }
});
</script>

``` 

Vue nous fournit à nouveau un attribut pour changer dynamiquement la classe d'un élément, en fonction des données de l'instance Vue.

Nous pouvons donc accéder à notre élément de liste et ajouter l'attribut: `class`.


```
<li class="list-item" :class="{completed: item.completed}" v-for="item in reversedItems">
  ...
</li>
``` 

Cela indique à Vue qu'il doit appliquer la classe terminée au `<li>` uniquement si l'élément est terminé (ce que nous pouvons dire en accédant à la propriété `item.completed`.

Maintenant, nos éléments terminés devraient avoir un contour vert. Cependant, nous devons toujours être en mesure de les marquer comme terminés s'ils ne le sont pas.

Pour ce faire, nous allons créer une autre méthode, appelée `toggleComplete`.


```

<script>
  new Vue( {
    el: '#app',
    data: {...},
    methods: {
      addItem: function() {...},
      toggleComplete: function (item) {
        item.completed = !item.completed;
      }
    },
  });
</script>

``` 
Une fois que nous avons notre méthode, nous pouvons l'appeler en utilisant l'attribut `@click` fourni par Vue.


```
<li class="list-item" :class="{completed: item.completed}" v-for="item in reversedItems">
  <div class="list-item-toggle" @click="toggleComplete(item)"></div>
  ...
</li>
``` 

Une fois de plus, nous pouvons passer l'objet `item` comme `prop` à la fonction, car Vue nous permet d'y accéder via l'attribut `v-for`.

Maintenant, nous pouvons basculer chaque élément à faire entre complet et incomplet.

## Suppression d'éléments Todo

La dernière chose que nous devons faire est de nous permettre de supprimer les éléments à faire. Encore une fois, nous utiliserons une méthode pour y parvenir.


```
<script>
  new Vue( {
    el: '#app',
    data: {...},
    methods: {
      addItem: function() {...},
      toggleComplete: function (item) {...},
      removeItem: function (itemID) {
        this.items = this.items.filter((item) => newItem.id!== itemID);
      } 
    },
  });
</script>

``` 
Dans cette fonction, nous accédons au prop `itemID` (qui est passé via l'élément delete) et définissons la propriété `items` sur un nouveau tableau, sans l'élément que nous venons de supprimer.

Maintenant, nous pouvons appeler la fonction à partir de notre élément de suppression.



```
<li class="list-item" :class="{completed: item.completed}" v-for="item in reversedItems">
  ...
  <div class="list-item-delete" @click="removeItem(item.id)">X</div>
</li>
``` 
Maintenant, nous pouvons supprimer avec succès nos taches à faire!

## Dernièrs ajouts.

Donc c'est tout! Nous venons de créer une application de liste de tâches `todo` fonctionnelle en utilisant Vue. Nous avons appris à appeler des méthodes, accéder aux données et mettre à jour les données, le tout sans aucune manipulation du `DOM JS`.

Vous pouvez trouver le code complet de cette application sur  [Github](https://github.com/lawalalao/Vue-todo) .

Si vous avez aimé ce tutoriel, j'apprécierais que vous  [m'achetiez un café](https://www.patreon.com/lawalalao) ! Ou suivez-moi sur  [Twitter](https://twitter.com/AdechinaAlao)  ✌.





