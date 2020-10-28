## Comment ajouter plusieurs classes aux composants React

Parfois, dans nos composants React, nous devons ajouter plusieurs classes en fonction de certaines conditions. Comme dans le composant Button, nous pouvons ajouter différentes classes `primaires` et `secondaires` en fonction d'une valeur de `props`.

En React, il existe deux façons d'y parvenir:

     
- 
template literals
     
- 
bibliothèque de noms de classe(classnames library)

# 1. template literals:

Nous pouvons définir l'opérateur ternaire dans les templates literals pour évaluer conditionnellement le nom de la classe.


```
import React from "react";

const Button = ({fill, isDisabled}) => {
  return (
    <button
    className={`
      default
      ${fill ? 'primary' : 'secondary'}
      ${isDisabled ? 'disabled' : 'enabled'}
    `}
    >
    {props.children}
    </button>
  );
}

export default Button;
``` 
# 2. bibliothèque de noms de classe

     
- 
C'est une bibliothèque très légère (~ 17 Ko) pour utiliser plusieurs classes.
    
- 
 Nous pouvons passer des chaînes ou des objets comme arguments dans la fonction className.
     
- 
L'objet argument a une clé comme nom et une valeur comme condition. Si la condition est fausse, c'est-à-dire que la valeur est fausse, cette clé n'est pas incluse dans la sortie.


```
import classNames from 'classnames';

classNames('default', 'primary')    /* seul les chaines (string) */

classNames('default', {primary: props.fill}) /* chaine et objet  */

classNames({default: true, primary: props.fill}) /* seul les objets */

``` 
**Exemple ci-dessus avec la bibliothèque de noms de classes:**


```
import React from "react";
import classNames from "classnames";

const Button = ({fill, isDisabled, size}) => {
  return (
    <button
    className={classNames({
      default: true,
      primary: fill,
      secondary: !fill,
      disabled: isDisabled,
    })}
    >
    {props.children}
    </button>
  );
}

export default Button;
``` 


> Merci! Les commentaires sont très appréciés :) Nous pouvons discuter sur  [Twitter](https://twitter.com/AdechinaAlao)  
