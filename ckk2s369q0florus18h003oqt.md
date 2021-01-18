## Saisie semi-automatique /suggestions d'entrées avec seulement du HTML5 | balise datalist

Parfois, vous souhaitez suggérer des options à un utilisateur lorsqu'il saisit quelque chose dans une entrée. Il existe peut-être des catégories de recherche ou des balises populaires que les gens recherchent. Vous pouvez, bien sûr, implémenter une fonctionnalité basée sur l'API, ou si vous souhaitez obtenir un moyen rapide pour qu'elle soit opérationnelle, pourquoi ne pas simplement utiliser la balise datalist?


> L'élément HTML `datalist` contient un ensemble d'éléments `option` qui représentent les options autorisées ou recommandées disponibles au choix dans d'autres contrôles. - MDN

Datalist agit comme un hybride entre une entrée normale et un champ de sélection où il permet aux utilisateurs de choisir une option suggérée, d'afficher des suggestions au fur et à mesure de la saisie ou d'ajouter leur propre option.

## Alors, comment ça marche?

Voyons comment ajouter la balise datalist à un ancien `input type = "text"` normal à titre d'exemple simple (et probablement le plus courant que vous utiliserez). datalist fonctionnera presque de la même manière qu'une balise de sélection prenant des options internes.

```
<input type="text" id="programming_language" list="languages"/>
<datalist id="languages">
 <option value="JavaScript"></option>
 <option value="Python"></option>
 <option value="Java"></option>
 <option value="HTML">stop being a troll</option>
</datalist>

```
La chose importante que vous verrez ici est que notre entrée prend une liste comme une option qui dirige vers l'id du datalist que vous souhaitez utiliser pour remplir l'entrée.


![giphy.gif](https://cdn.hashnode.com/res/hashnode/image/upload/v1610908712469/XxJ5ku6nN.gif)

Vous pouvez également ajouter des notes internes, donc dans cet exemple, vous verrez si quelqu'un commence à taper «Html» comme langage de programmation préféré, nous pouvons afficher une petite note lui disant d'arrêter de nous troller…

L'autre chose vraiment cool à propos de datalist est que ce n'est pas uniquement pour les entrées avec un type de texte. Vous pouvez l'utiliser pour ajouter des suggestions à pratiquement toutes les balises, y compris les balises de date et de couleur.

Voici un exemple d’utilisation avec un sélecteur de couleurs:

```
<label for="pick_color">Pick a color</label>
<input type="color" id="pick_color" list="colors"/>
<datalist id="colors">
 <option value="#155AF0"></option>
 <option value="#F107BA"></option>
 <option value="#2B2B2B"></option>
</datalist>
```


![giphy (1).gif](https://cdn.hashnode.com/res/hashnode/image/upload/v1610908847406/1ZRSorx9e.gif)

Je suis un grand fan de l'apprentissage par le piratage, alors lancez-vous directement dans ce CodePen pour l'essayer par vous-même:

https://codepen.io/lawalalao/pen/QWKYjRB

Exemple de balises datalist en action Quand l'utiliser? Étant donné que cela ajoutera des éléments DOM, je suggérerais de l'utiliser lorsque vous ne disposez pas d'une base de données complète de suggestions (peut-être moins de 50 ou plus est une bonne règle de base pour moi).

Merci d'avoir lu.