## Introduction aux expressions régulières ou expressions rationnelles en JavaScript

Dans cette nouvelle serie d'articles, nous allons nous intéresser aux expressions régulières encore appelées expressions rationnelles ou en abrégé « Regex ».
Avant de découvrir ce que sont les expressions régulières, vous devez bien comprendre que les expressions régulières ne sont pas un élément du langage JavaScript en soi mais constituent en fait un autre langage en soi.

Comme de nombreux autres langages, le JavaScript supporte l’utilisation des expressions régulières et nous fournit des outils pour utiliser toute leur puissance.

Nous allons donc découvrir ce que sont les expressions régulières, comment les construire et comment les utiliser intelligemment en JavaScript.

# Présentation des expressions régulières

Les expressions régulières sont des schémas ou des motifs utilisés pour effectuer des recherches et des remplacements dans des chaines de caractères.
Ces schémas ou motifs sont tout simplement des séquences de caractères dont certains vont disposer de significations spéciales et qui vont nous servir de schéma de recherche. Concrètement, les expressions régulières vont nous permettre de vérifier la présence de certains caractères ou suites de caractères dans une expression.

En JavaScript, les expressions régulières sont avant tout des objets appartenant à l’objet global constructeur `RegExp`. Nous allons donc pouvoir utiliser les propriétés et méthodes de ce constructeur avec nos expressions régulières.

Notez déjà que nous n’allons pas être obligés d’instancier ce constructeur pour créer des expressions régulières ni pour utiliser des méthodes avec celles-ci.

Nous allons également pouvoir passer nos expressions régulières en argument de certaines méthodes de l’objet String pour effectuer des recherches ou des remplacements dans une chaine de caractère.

# Création d’une première expressions régulière et syntaxe des Regex

Nous disposons de deux façons de créer nos expressions régulières en JavaScript : on peut soit déclarer nos expressions régulières de manière littérale, en utilisant des slashs comme caractères d’encadrement, soit appeler le constructeur `RegExp()`.

De manière générale, on préfèrera comme souvent utiliser une écriture littérale tant que possible pour des raisons de performance.

```
/*on definit ici deux masques de recherche c'est a dire 2 expressions regulieres de 2 facons differentes*/

let masque1 = /lawal/;
let masque2 = new RegExp('lawal');
```
Dans le code ci-dessus, on définit deux expressions régulières en utilisant les deux méthodes décrites précédemment. On les enferme dans des variables masque1 et masque2. Notez que les termes « masque de recherche », « schéma de recherche » et « motif de recherche » seront utilisés indifféremment et pour décrire nos expressions régulières par la suite.

Dans cet exemple, nos deux expressions régulières disposent du même motif qui est le motif simple /lawal/. Ce motif va nous permettre de tester la présence de « lawal » c’est-à-dire d’un « l » suivi d’un «a » suivi d’un « w » suivi d’un « a » suivi d’un autre « l » dans une chaine de caractères.

Dans ce cas-là, notre masque n’est pas très puissant et le recours aux expressions régulières n’est pas forcément nécessaire. Cependant, nous allons également pouvoir construire des motifs complexes grâce aux expressions régulières qui vont nous permettre d’effectuer des tests de validation très puissants.

Pour créer des motifs de recherche complexes, nous allons utiliser ces caractères spéciaux, c’est-à-dire des caractères qui vont disposer d’une signification spéciale dans le contexte des expressions régulières. Ces caractères au sens spécial vont pouvoir être classés dans différents groupes en fonction de ce qu’ils apportent à notre schéma.

Dans la suite de cette serie, nous allons étudier chacun d’entre eux pour créer des motifs de plus en plus complexes qui vont pouvoir être utilisés de manière pratique avec certaines méthodes des objets `String` ou `RegExp` pour par exemple vérifier la validité d’un champ de formulaire ou la présence d’une certaine séquence de caractères ou d’un certain type de séquences dans une chaine.