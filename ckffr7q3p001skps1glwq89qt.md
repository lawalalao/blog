## Fonctions en JavaScript

# Fonction

Les fonctions sont l'un des éléments fondamentaux de JavaScript. Une fonction JavaScript est un bloc de code conçu pour effectuer une tâche particulière. Une fonction JavaScript est exécutée lorsque "quelque chose" l'invoque (l'appelle).

# Pourquoi des fonctions?

     
- 
Vous pouvez réutiliser le code: définissez le code une fois et utilisez-le plusieurs fois.
     
- 
Vous pouvez utiliser le même code plusieurs fois avec des arguments différents, pour produire des résultats différents.

Une fonction est définie en utilisant le mot-clé `function` suivi du nom de la fonction et des parenthèses (), pour contenir les entrées **(paramètre1, paramètre2)** le cas échéant.

Une fonction peut avoir zéro ou plusieurs paramètres séparés par des virgules.


```
// creation d'une fonction

function myFun(a, b) {
  return a * b;   // la fonction retourne la multiplication de a et b
}
``` 

Les fonctions peuvent être paramétrées et non paramétrées, ce qui signifie qu'elles peuvent ou non accepter des entrées.

# Les fonctions sont aussi des objets.

Les fonctions sont également conservées en tant qu'objets. Cependant, ils sont spéciaux car ils sont invocables (appelables).

Le `typeof` renvoie une fonction pour les fonctions, cependant, les fonctions peuvent toujours recevoir des paires `key-value` (clé-valeur), tout comme les objets.


```
function hello(){
 console.log("hello")
}
hello.a = 1
hello.b = 2

// fonctionne correctement

typeof(hello) // "fonction"

``` 
 # fonction Return

Lorsque JavaScript atteint une instruction `return`, la fonction s'arrête de s'exécuter.

Si la fonction a été appelée à partir d'une instruction, JavaScript "retournera" pour exécuter le code après l'instruction d'appel.


```
var x = myFunction(4, 3);   // La fonction est appelée, la valeur de retour se terminera par x

function myFunction(a, b) {
  return a * b;             // la fonction retourne la multiplication de a et b
}

//le resultat de x sera : 12

``` 
# Déclarations de fonction

Une déclaration de fonction, en revanche, est une instruction qui définit une variable nommée avec une valeur de type `function`.

Les fonctions déclarées ne sont pas exécutées immédiatement. Ils sont "enregistrés pour une utilisation ultérieure", et seront exécutés plus tard, lorsqu'ils seront appelés.


```
function myFunction(a, b) {
  return a * b;
}
``` 
# Expression de fonction

Une fonction JavaScript peut également être définie à l'aide d'une expression.Une expression de fonction peut être stockée dans une variable:


```
var x = function (a, b) {return a * b};
``` 

Une fois qu'une expression de fonction a été stockée dans une variable, la variable peut être utilisée comme fonction. Les fonctions stockées dans des variables n'ont pas besoin de noms de fonction. Ils sont toujours appelés en utilisant le nom de la variable.

# Fonctions fléchées ou Arrow Function

La fonction fléchée ou la fonction de flèche est une notation abrégée pour définir une fonction anonyme en JavaScript.

Les fonctions fléchées en JavaScript existaient depuis un certain temps maintenant et je ne saurais trop insister sur la commodité d'un développeur d'utiliser les fonctions fléchées lors du codage. La fonction fléchée est quelque chose que tout développeur Web doit savoir.

La meilleure façon de savoir à quoi ressemble une fonction de flèche est de la comparer avec une fonction JavaScript traditionnelle.


```
//fonction JavaScript traditionnelle
var myFunction = function(parameter){
    return result;
}
//fonction fléchée en JS
var myFunction = (parameter) => { return result; }
``` 
# Les fonctions Arrow sont-elles utiles?

Eh bien, cela dépend. En termes de fonctionnalité et de facilité d'utilisation, les fonctions Arrow sont les meilleures. Mais en ce qui concerne la lisibilité et la compréhension, vous pourriez trouver cette notation fléchée un peu gênante. S'il y a beaucoup de fonctions imbriquées, garder une trace de toutes les fonctions serait fastidieux car il n'y a pas de mots-clés comme `function` et `return` utilisés dans les fonctions fléchées.


> 
J'espère que cela a été utile! Faites-moi savoir dans la section des commentaires.Et merci de partage l'article.