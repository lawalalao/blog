## les méthodes map(), filter() et reduction()

Ce sont quelques méthodes qui sont très utilisées dans le développement et les connaître est un must. Alors commençons!

# **Map**:
La méthode map() crée un nouveau tableau à partir d'un tableau existant et applique la fonction à chacun des éléments du premier tableau.

```
const numbers = [1, 2, 3, 4];
const doubled = numbers.map(item => item * 2);
console.log(doubled); // [2, 4, 6, 8]
```
# **Filter**:
La méthode filter() renvoie les valeurs basées sur l'instruction conditionnelle. Il vérifie la condition pour chaque élément du tableau et si la condition est vraie, elle la renvoie sinon.

```
const numbers = [4, 7, 12, 3];
const evens = numbers.filter(item => item % 2 === 0);
console.log(evens); // [4, 12]
```
```
const students = [
  { name: 'abc', attendance: 96 },
  { name: 'mno', attendance: 60 },
  { name: 'def', attendance: 89 },
  { name: 'jkl', attendance: 65 },
  { name: 'xyz', attendance: 40 }
];

const eligibleStudent = students.filter(student => student.attendance >= 75);
return eligibleStudent; // [ { name: 'abc', grade: 96 }, { name: 'def', grade: 89}]
```
# **Reduce**

La méthode reduce() réduit le tableau à une valeur unique, exécutant la fonction fournie sur chaque élément du tableau.

syntaxe:

```
array.reduce(function(total, currentValue, currentIndex, arr), initialValue)
```
Total (La valeur initiale ou la valeur précédemment renvoyée de la fonction) et la currentValue (valeur de l'élément courant) sont des paramètres obligatoires. InitialValue est facultatif, il définit la valeur initiale du tableau. Si aucune valeur initiale n'est fournie, le premier élément du tableau sera utilisé comme initial. L'appel de reduce() sur un tableau vide sans initialValue lancera une `TypeError`.

```
const cfa = [2900, 4185, 46565];
const sum = cfa.reduce((total, amount) => total + amount); 
console.log(sum)  //53650
```
```
var pilots = [
  {
    id: 10,
    name: "lito rodriguez",
    years: 14,
  },
  {
    id: 2,
    name: "Temmin 'Snap' Wexley",
    years: 30,
  },
  {
    id: 41,
    name: "lawal alao",
    years: 16,
  },
  {
    id: 99,
    name: "koffi kodjo",
    years: 22,
  }
];
const totalYears = pilots.reduce((acc, pilot) => acc + pilot.years, 0); 
console.log(totalYears) //82

```
C'est tout pour ce sujet. Si vous avez appris quelque chose, partagez-le avec vos amis dev. Merci.
Happy coding
