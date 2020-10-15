## Créez une page coming soon avec un compte à rebours JavaScript

Dans ce tutoriel, vous apprendrez à développer  page coming soon avec un compte à rebours JavaScript. Cette page peut être utilisée pour afficher le temps restant avant un grand événement, le lancement d'un site Web ou la sortie d'un produit..

Alors commençons par créer un nouveau fichier HTML avec la structure suivante:


```
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <meta http-equiv="X-UA-Compatible" content="ie=edge">
    <link rel="stylesheet" href="main.css">
    
    <title>Coming Soon Page</title>
</head>
<body>
    <section class="landing">
        <div class="landing-inner">
        <p>c'est notre coming soon</p>
        <h1 class="comingsoon">Coming Soon</h1>
        <div class="countdown"></div>

        <br>
        

        <footer id="footer"><p>&copy; 2019  Created by: lawal alao </p></footer>
        
       
    </section>

    <script src="script.js"></script>
    
       
</body>
</html>


``` 
Ensuite, créez un fichier script.js et  commencez par définir des variables pour chacune des unités du temps;


```
(() => {
  const sec = 1000,
    min = sec * 60,
    hour = min * 60,
    day = hour * 24;  
})();
``` 

Alors que nous construisons un compte à rebours, nous devrons spécifier une date / heure de fin en utilisant le format suivant:


```
const end = new Date("Jul 01, 2021 12:00:00").getTime();
``` 

Pour calculer le temps restant, nous utiliserons `setInterval` pour récupérer l'heure actuelle toutes les 1000 millisecondes. On peut alors calculer le temps restant en le soustrayant de la date de fin et mettre à jour le texte HTML:


``` 
const int = setInterval(() => {
  const current = new Date().getTime();
  const remaining = end - current;
  document.getElementById("days").innerText = Math.floor(remaining / day);
  document.getElementById("hours").innerText = Math.floor( (remaining % day) / hour );
  document.getElementById("minutes").innerText = Math.floor( (remaining % hour) / min );
  document.getElementById("seconds").innerText = Math.floor( (remaining % min) / sec );   
}, 1000);
``` 

Actuellement, lorsque le compte à rebours expire, la minuterie continue de fonctionner en indiquant le temps écoulé depuis la date de fin. Au lieu de cela, nous allons mettre tous les chiffres à 0 et mettre à jour le texte pour indiquer que la date de fin a été atteinte. Pour ce faire, ajoutez ce qui suit à la fin de la méthode `setInterval`:


```
if (remaining < 0) {
  document.querySelector("h1").innerText = "bingo!";
  document.querySelector("p").innerHTML = "le grand jour est enfin la__Voir <a href=https://www.website.com>website<a/> Pour plus d'informations.";
  const digit = document.querySelectorAll("span");
  digit.forEach((digit) => {
    digit.innerText = "0";
  });
  clearInterval(int);
}
``` 
Fonctionnellement maintenant, cela termine le compte à rebours pour le CSS.

Ainsi, le compte à rebours est aligné au centre, à la fois horizontalement et verticalement pour afficher le corps a été réglé `display:fex;`. Une image d'arrière-plan qui provient de  [Iwaria](https://iwaria.com) la banque d'images africaine, configuré pour afficher en plein écran à l'aide de la propriété CSS `cover`;


```

html {
  height: 100%;
  overflow: hidden;
}
body {
  background: url("https://iwaria.s3.amazonaws.com/prod/1920x1920/1591830107908.1154.jpeg") no-repeat center center fixed;
  color: #fff;
  font-family: sans-serif;
  text-align: center;
  min-height: 100%;
  display: flex;
  justify-content: center;
  align-items: center;
}

``` 
Pour la typographie, nous ajouterons une ombre de texte `text-shadow` car elle facilite la lecture lorsqu'elle est superposée sur une image d'arrière-plan, nous augmenterons également les tailles de police et remplacerons la couleur par défaut du lien bleu;


```
h1 {
  font-size: 4rem;
  text-shadow: 1px 1px 5px #000;  
  margin: 0;
}
p {
  font-size: 1.2rem;  
  text-shadow: 1px 1px 2px #000;
}
a {
  color: #fff;
}
``` 
Enfin, les chiffres et le texte dans le compte à rebours. Comme il y a quatre éléments, nous utiliserons `flex: 25%` pour les répartir uniformément sur l'axe horizontal. Nous allons donc ajouter les nombres qui se démarquent de la couleur d'arrière-plan (tirée de l'image d'arrière-plan):


```
#countdown {
  max-width: 600px;
}
#countdown ul {
  margin: 5% 0 0 0;
  padding: 0;
  display: flex;
  gap: 5%;
}
#countdown ul li {
  flex: 25%;
  padding: 5%;
  margin: 0;
  list-style: none;
  background: #001f2f;
  border-radius: 5px;
}
#countdown ul li span {
  display: block;
  font-size: 3rem;
}
```

retrouvez tout le code  [ici](https://github.com/lawalalao/coming_soon)  et n’hésitez pas a  [m’écrire](https://twitter.com/AdechinaAlao)  si vous avez besoin d'explications.
> si vous avez aime n’hésitez pas de partager avec vos amis..
