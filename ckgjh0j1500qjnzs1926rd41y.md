## Variables Javascript: var

Les variables représentent un emplacement mémoire où les données peuvent être stockées. Fondamentalement, ce sont des noms de boîtes dans lesquelles nous pouvons mettre des valeurs de données.

Mais pour utiliser les variables, nous devons les déclarer, puis lui affecter une valeur de données.

En Javascript, les variables sont déclarées avec les mots-clés `var`, `let` et `const`.

**Remarque:** en Java et dans de nombreux autres langages, les variables sont déclarées avec différents mots-clés comme `int` pour le type entier des valeurs de données ou `char` pour les caractères. Mais en JavaScript, nous avons des mots-clés généraux pour tous les types de valeurs de données, qu'elles soient entières, décimales, booléennes ou chaînes.

ES6 a introduit les mots clés `let` et `const`, mais `var` était la seule option avant 2015. 

Dans cet article, nous allons discuter spécifiquement de `var`.

## Le var:

     
- 
Le `var` déclare une variable à portée fonction ou à portée globale en Javascript.
     
- 
Il ne crée pas de portée "bloc".
     
- 
La même variable peut être déclarée plusieurs fois.
     
- 
Les variables déclarées avec `var` sont levées et initialisées avec une valeur indéfinie.

# 1. Syntaxe


```
var x = 5;
console.log('valeur de x est: ', x); // valeur de x est : 5

var str = "je suis une chaine";
console.log(str);  // je suis une chaine

var myFunction = function() {
   console.log('hey');
}
console.log(myFunction);  // ƒ () {console.log('hey');}

``` 
**Contraintes de dénomination des variables Javascript**: Le nom ne doit contenir que des lettres, des chiffres ou les symboles `$` et `_`, et le premier caractère ne doit pas être un chiffre.

## 2. Portée (Scope):

`var` déclare une variable à portée fonction ou à portée globale mais ne peut pas créer de portée de bloc.

### 2.1 Portée globale (global scope):

```
var value = 10;
function logger() {
  console.log(value); //10
}
console.log(value); //10

``` 
La variable `value` est dans la portée globale, nous pouvons donc y accéder n'importe où dans cette portée, qu'elle soit à l'intérieur d'une fonction ou après 10000 lignes.

### 2.2 Portée fonction (function scope):


```
function mood() {
  var happy = true;
  console.log(happy);  // true
}
console.log(happy);  // ReferenceError: happy is not defined (happy n'est pas defini)

``` 
La variable `value` est dans la portée de la fonction, nous ne pouvons donc y accéder que dans la fonction `mood` mais pas en dehors de celle-ci. Cela nous donnera une erreur de référence.

### 2.3 Portée de bloc (bloc scope):


```
var a = 10;
if (a > 10) {
  var name = 'hashnode';
}
function logger() {
  console.log(name);
}
logger(); // hashnode
console.log(name); // hashnode

``` 
Ici, la variable `name` ne crée pas de portée de bloc, mais à la place, elle est visible partout comme une variable dans la portée globale. Donc, nous ne pouvons pas déclarer de variables privées dans ce champ du bloc `if`, c'est-à-dire que la portée du bloc n'est pas possible.

Avant 2015, lorsque `var` était la seule option pour déclarer des variables, nous pouvions utiliser le modèle IIFE pour obtenir la portée des blocs.

**IIFE**: Immediately Invoked Function Expressions (expressions de fonction immédiatement appelées). Il décrit une expression de fonction qui peut être appelée immédiatement et qui possède ses propres variables privées.


```
(function() {
  var greeting = "Good Morning!";
  console.log(greeting ); // Good Morning!
})();
``` 
Dans cette syntaxe, la fonction est entourée de parenthèses puis immédiatement appelée à l'aide de ().

**Solution:** Pour créer un bloc dans notre exemple ci-dessus, nous pouvons définir la condition `if` dans IIFE comme ci-dessous:


```
var a = 10;
(function() {
  if (a > 10) {
    var name = 'hashnode';
  }
})();
console.log(name); // ReferenceError: name is not defined (name n'est pas defini)

``` 

## 3. Redéclaration:

Les variables déclarées avec `var` peuvent être déclarées à nouveau. Javascript ne renvoie pas d'erreur.

```
var browser = 'Mozilla';
var browser = 'Chrome';
console.log(browser); //Chrome
```
La dernière valeur attribuée remplace la dernière valeur.

## 4. Levage (Hoisting)

Les déclarations de variables sont traitées en premier avant l'exécution de tout code. Ainsi, déclarer une variable n'importe où dans le code équivaut à la déclarer en haut. Ce comportement est appelé "levage", car il semble que la déclaration de variable est déplacée vers le haut de la portée:  fonction ou global.


```
test = 10;
var test;
// En termes simples, le code ci-dessus est traité comme ci-dessous
var test;
test = 10;
``` 
Avec `var`, nous pouvons d'abord attribuer une valeur, puis déclarer la variable, elle ne générera pas d'erreur en raison du levage (hoisting).

Mais, il est hissé vers le haut avec une valeur `indéfinie`.


```
console.log(band); // undefined
// ---some code
band = 'coldplay';
console.log(band); //coldplay
// ---some code
var band;
``` 
La variable `band` est traitée avant la première console en raison du levage mais seule la déclaration est levée et non l'affectation. Ainsi, sa valeur **n'est pas définie **initialement. C'est comme attribuer la valeur **non définie** à la variable `band`.


> Les déclarations sont hissées mais pas l'affectation.


# Exemple divers:

```
for(var i = 0; i < 5; i++) {
    console.log(i); 
}
console.log(i); // 5
```


> La portée de bloc n'est pas non plus créée en cas de boucle `for`:

pour toutes questions n'hesitez pas a m'ecrire sur  [@twitter](https://twitter.com/AdechinaAlao) 
