## L'opérateur typeof en JavaScript

L'opérateur typeof renvoie une chaîne indiquant le type de valeur JavaScript.

Dans mon dernier article, j'ai parlé des variables en JavaScript et du fait que nous n'avons pas d'instructions particulières pour différents types de données comme `int` pour les valeurs entières en Java. Au lieu de cela, nous utilisons var / let / const pour la déclaration de variables pour tous les types de données. Ainsi, l'opérateur `typeof` nous aide à comprendre le type de valeurs que nous attribuons aux variables.

# Syntaxe:

Deux types d'utilisation de l'opérateur typeof: avec ou sans parenthèses.

     
- 
typeof operand
     
- 
typeof (operand)

Exemples:


```
console.log(typeof 10); // "nombre"
console.log(typeof true); // "booleen"
``` 

## 1. Boolean


```
console.log(typeof true); // "boolean"
console.log(typeof false); // "boolean"

//La fonction boolean() convertit n'importe quelle valeur en valeur booléenne
console.log(typeof Boolean(1)); // "boolean"

//Deux fois l'appel d'opérateur NOT logique sont égaux à la fonction booléenne
console.log(typeof !!('google')); // "boolean"
``` 

## 2. Number

```
console.log(typeof 11); // "number"
console.log(typeof (50)); // "number"
console.log(typeof 2.22); // "number"

console.log(typeof NaN); // "number"  meme si ce n'est pas un nombre

// utilisation de la syntaxe des parenthèses dans l'évaluation de l'expression
console.log(typeof (5 + 10)); // "number"

// La fonction number essaie d'analyser n'importe quelle valeur dans les nombres entiers d'argument même s'ils ne peuvent pas être analysés
console.log(typeof Number(5)); // "number" 
console.log(typeof Number('hey')); // "number"
```
## 3. String

```
console.log(typeof ''); // "string"
console.log(typeof 'apple'); // "string"

// ES6:  Template literal
console.log(typeof `${10+5} pens`); // "string"
```
Remarque: typeof typeof (opérande) sera toujours une chaîne.

```
console.log(typeof typeof 10); // "string"
console.log(typeof typeof {msg: 'hey'}); // "string"
```

> le premier typeof retournera toujours une chaîne comme "object", "boolean" ou "string". Ainsi, le typeof d'une chaîne sera une chaîne, c'est-à-dire typeof typeof (opérande) === "chaîne"

## 4. Symbols

```
console.log(typeof Symbol); // "symbol"
console.log(typeof Symbol('text message')); // "symbol"

``` 
## 5. Undefined

```
let str;
console.log(typeof str); // "undefined"
console.log(typeof undeclaredVariable); // "undefined"
```
À première vue, `undefined` peut sembler être une valeur vide mais `undefined` est un type spécifique en Javascript.

## 6. Null

```
console.log(typeof null); // "object"
```
En général, null représente 0 ou pointeur nul. Mais en JavaScript, les valeurs étaient représentées comme une balise de type et la balise de type pour les objets était 0. De plus, null avait 0 comme balise de type, d'où la valeur de retour typeof de typeof est "objet".

## 7. Function

```
console.log(typeof function() {}); // "function"
console.log(typeof class Animal() {}); // "function"

// Constructors
console.log(typeof Boolean); // "function"
console.log(typeof Number); // "function"
console.log(typeof String); // "function"

// Methods
console.log(typeof [1,2,3].map); // "function"
console.log(typeof 'cool'.charAt); // "function"
```

## 8. Object

```
console.log(typeof {}); // "object"
console.log(typeof {key: 'house'}); // "object"

// using new keyword
console.log(typeof new Date()); // "object"
console.log(typeof new String('str')); // "object"

// Reference types
console.log(typeof [1,2,3]); // "object"
```

### **Cas d'utilisation:**

Vous pouvez utiliser l'opérateur typeof dans les contrôles de validation ou pour des conditions telles que la condition if-else.

```
if(typeof argument === "string") {
 // do something
}

if(typeof formValue === "number") {
  // throw error
}
```

### **Remarque:**

Il existe des cas particuliers, le typage dynamique et la conversion de type en JavaScript qui décident du type final de la valeur. En utilisant typeof sur les types primitifs, vous pouvez facilement prédire les types, mais avec les objets, cela peut devenir déroutant si rapidement.

Vous pouvez en savoir plus sur la saisie dynamique sur [ Mozilla.](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Data_structures)  J'essaierai également de couvrir ces sujets dans mes prochains articles, mais cet article était spécifiquement axé sur les bases de l'opérateur typeof.

Références: En savoir plus sur l'opérateur typeof  [Mozilla](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/typeof#null) .


> Merci d'avoir lu! Bon codage!
