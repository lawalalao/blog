## Qu'est-ce que Prime React? Comment l'utiliser dans create-react-app?

Prime React est une bibliothèque React, similaire aux bibliothèques populaires comme Material UI, React Bootstrap, etc. Mais c'est devenu l'une de mes bibliothèques React préférées car elle me donne beaucoup de variété pour utiliser le composant en fonction de mes besoins. Aussi, si vous avez besoin de créer une application qui nécessite beaucoup de personnalisation des éléments, Prime React n'est que le meilleur choix. Mais, nous ne ferons aucune personnalisation pour le moment.
Si vous avez besoin d'en savoir plus sur la bibliothèque et sa communauté, vous pouvez aller  [ici](https://primefaces.org/primereact/showcase/#/ ) . Ils ont également des tonnes d'exemples et ils ont également une collection Bit.dev si vous êtes intéressé à le voir, vous pouvez aller  [ici](https://bit.dev/primefaces) .

Commençons maintenant.

# Commencer

Comme toute autre bibliothèque React, il est très simple de configurer le projet. Tout d'abord, nous devons créer une application React, puis


```
npx create-react-app myprimeapp
``` 
ensuite

```
npm install primereact primeicons classname react-transition-group
```
Vous pourriez utiliser yarn


```
yarn add primereact primeicons classnames react-transition-group
``` 
Après avoir installé le package, vous devez importer son CSS dans votre `index.js` , tout comme bootstrap. Prime react propose de nombreux thèmes, mais nous n'aurons normalement pas besoin d'un autre thème, jusqu'à ce que vous souhaitiez être très pointilleux sur les couleurs.

Accédez à votre fichier `index.js` et placez ces importations en haut du fichier:


```
import 'primereact/resources/themes/saga-blue/theme.css';
import 'primereact/resources/primereact.min.css';
import 'primeicons/primeicons.css';
``` 
Après avoir importé les styles CSS, nous pouvons ajouter un élément à la page pour voir comment cela fonctionne. Prime React a une liste de composants qui peuvent être utilisés, le point le plus fort de cette bibliothèque est qu'elle contient de très bons composants pour la visualisation des données. Il intègre des graphiques et des composants graphiques qui peuvent être utilisés pour créer très rapidement des tableaux de bord d'analyse. Dans leur documentation, ils spécifient la liste des bibliothèques tierces qu'ils utilisent pour construire leur bibliothèque. Ils utilisent les dépendances suivantes dans leur bibliothèque.


   
- 
 Charts : Charts.js 2.1.x
    
- 
GMap : Google Maps
    
- 
Editor : Quill.js
    
- 
FullCalendar : FullCalendar 4.0 Alpha.2+

Ils utilisent également des animations, des bibliothèques CSS telles que "react-transition-group" et "classnames". Nous les avons déjà ajoutés lors de l'étape d'installation.

# Composants de Prime React

 créons une petite application todo, avec prime react afin que nous puissions en savoir plus sur cette bibliothèque. Tout d'abord, nous devons importer un composant de carte, l'un des éléments les plus importants de nombreuses applications Web étant les cartes.

Vous pouvez suivre votre propre structure de projet ou vous pouvez créer un dossier nommé `components` à l'intérieur de votre dossier src. Dans le dossier `components`, créez un dossier nommé `TodoInfoCard` et à l'intérieur, ajoutez un fichier nommé `TodoInfoCard`.js.

![react1.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1603205619310/GXDODytfC.png)

Pour un si petit, vous n'aurez peut-être pas besoin d'ajouter un dossier et des fichiers, mais il est bon de garder notre structure propre.

À l'intérieur du TodoInfoCard.js:


```
import React from "react";
import { Card } from "primereact/card";
class TodoInfoCard extends React.Component {
  render() {
    return <Card>Content</Card>;
  }
}

export default TodoInfoCard;
``` 
Après avoir créé le composant, ajoutez ce qui suit dans votre fichier **App.js**:


```
import TodoInfoCard from "./components/TodoInfoCard/TodoInfoCard";
import { Card } from "primereact/card";

import "./app.css";

class App extends React.Component {
render() {
  return (
    <div className="App">
      <TodoInfoCard />
    </div>
  );
 }
}
export default App;
``` 
Après avoir ajouté la carte, vous pouvez voir une carte s'étendant sur toute la largeur de l'écran, comme ci-dessous:


![react2.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1603205594399/cOCwJh0ZO.png)

Maintenant, ajoutons du style, nous pouvons donner à toute la carte une couleur de fond sombre avec une belle ombre. Nous voulons également que le texte soit gras et blanc.

Accédez à votre fichier **app.css** afin que nous puissions ajouter nos classes personnalisées.

Comme il s'agit d'une toute petite application, la conception de notre composant ne prendrait pas beaucoup de temps, mais si nous avons beaucoup de composants dynamiques qui doivent avoir des styles différents, l'app.css deviendrait encombrant. Afin d'éviter une telle situation, je préfère utiliser la bibliothèque CSS Tailwind. Pour l'instant, nous ne l'utiliserons pas, mais j'écrirai bientôt un article à ce sujet.

fichier app.css

```
.customCard {
  width: 560px;
  background-color: #2b2d42;
  font-weight: bold;
  color: white;
  -webkit-box-shadow: 14px 17px 25px -23px rgba(0, 0, 0, 1);
  -moz-box-shadow: 14px 17px 25px -23px rgba(0, 0, 0, 1);
  box-shadow: 14px 17px 25px -23px rgba(0, 0, 0, 1);
}

.cardHeader {
  text-align: left;
  padding: 10px 0px 0px 10px;
  color: white;
  font-size: 20px;
}

.cardContentClass {
  display: flex;
  justify-content: space-between;
  align-items: center;
}

.content {
  width: 360px;
  text-align: left;
  white-space: nowrap;
  overflow: hidden;
  text-overflow: ellipsis;
}
```
Maintenant, ajoutez les styles dans votre fichier, accédez à app.js et ajoutez classNames au composant comme ceci:


``` 
import React from "react";
import { Card } from "primereact/card";
class TodoInfoCard extends React.Component {
  render() {
    return (
      <Card className="customCard">
        <div className="cardContentClass">
          <div>Checkbox</div>
          <div className="content">Need To Add A State to the Function</div>
          <div>Status</div>
        </div>
      </Card>
    );
  }
}

export default TodoInfoCard;

```
Après avoir ajouté le style au composant, si vous voyez votre navigateur, cela ressemblerait à ceci:


![react3.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1603205862961/MSXxYuxye.png)

Afin de rendre ce composant plus dynamique, nous devons envoyer les props afin de pouvoir gérer l'état de notre composant App.

Nous pouvons convertir le TodoInfoCard.js en:


```
import React from "react";
import { Card } from "primereact/card";
class TodoInfoCard extends React.Component {
  render() {
    return <Card className="customCard">{this.props.children}</Card>;
  }
}

export default TodoInfoCard;
``` 
nous avons juste besoin de demander aux proprietes enfants, donc nous avons plus de flexibilité sur le contenu à l'intérieur. Maintenant, ajoutez ce code à votre App.js,


```
import React from "react";
import TodoInfoCard from "./components/TodoInfoCard/TodoInfoCard";
import "./styles.css";

class App extends React.Component {
  render() {
    return (
      <div className="App">
        <TodoInfoCard>
          <div className="cardContentClass">
            <div>Checkbox</div>
            <div className="content">Need To Add A State to the Function</div>
            <div>Status</div>
          </div>
        </TodoInfoCard>
      </div>
    );
  }
}
export default App;
``` 

La sortie doit rester la même car nous envoyons le même composant.

Ce sera tout pour cette configuration initiale. Je continuerai d'ajouter l'état et de nombreux autres composants de Prime React à cette application dans mon prochain article. Faites-moi savoir ce que vous pensez de cette bibliothèque.