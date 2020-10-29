## Créez une page d'accueil en moins de 100 lignes de code (y compris CSS)

Récemment, je me suis amuse a créer une page d'accueil rapide  pour mon prochain domaine [lawal.com](https://naughty-wozniak-12aa6b.netlify.app/)  qui servirait pour votre portfolio. J'ai pensé que certains d'entre vous pourraient le trouver utile, alors j'ai décidé de faire un tutoriel à ce sujet.

# HTML

Commencez par créer un nouveau fichier `index.html` et lancez un boiler-plate en tapant "!" et en appuyant sur «Tab». Tapez le nom de votre site dans les balises de titre. Il sera affiché dans l'onglet du navigateur.


```
<!DOCTYPE html>
<html lang="en">
<head>
   <meta charset="UTF-8">
   <meta name="viewport" content="width=device-width, initial-scale=1.0">
   <title>Ma superbe page d'accueil</title>
</head>
<body>

</body>
</html>
``` 
Créez ensuite des `divs` qui envelopperont la page et centreront le contenu. Ajoutez un titre qui présentera le site et un paragraphe description du site. J'ai également utilisé des éléments `span` sur les séparateurs pour les styliser plus tard.

```
<div class="page-wrapper">
      <div class="content-wrapper">
        <h1>Hi, I'm lawal alao</h1>
        <p>
          FrontEnd <span class="divider"> | </span> BackEnd
          <span class="divider"> | </span> trainer
        </p>
      </div>
 </div>
```
Ensuite, créez un nouveau dossier Icônes. Vous pouvez trouver des icônes impressionnantes sur  [Font Awesome](https://fontawesome.com/) . Visitez leur site et entrez l'email pour recevoir le pack. Décompressez-le et ajoutez-le au dossier `Icons`. Enfin, lien vers le fichier `all.css` dans le pack.

```
<link rel="stylesheet" href="icons/font-awesome/css/all.css" />
```
Ajoutez vos icônes à l'intérieur des liens et utilisez la syntaxe Font Awesome appropriée pour les icônes spécifiques que vous allez utiliser (voir leurs  [documents](https://fontawesome.com/how-to-use/on-the-web/referencing-icons/basic-use) )

```
<a href="https://twitter.com/lawalalao">
  <i class="icon fab fa-twitter fa-2x"></i>
</a>
<a href="https://github.com/lawalalao">
   <i class="icon fab fa-github fa-2x"></i>
</a>
<a href="https://www.linkedin.com/in/lawalalao/">
   <i class="icon fab fa-linkedin-in fa-2x"></i>
</a>
<a href="https://lawaltech.hashnode.com">
   <i class="icon fas fa-book fa-2x"></i>
</a>
<a href="mailto:lawalalaoad@gmail.com">
   <i class="icon fas fa-envelope fa-2x"></i>
</a>
```

C'est tout pour le balisage. Si vous avez suivi, cela devrait maintenant ressembler à ceci. Les icônes sont bleues, en raison de la couleur par défaut des balises «a». Ça a l'air vintage!.

![Screen Shot 2020-10-28 at 1.15.25 PM.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1603887380564/reDAegH1y.png)
# CSS

Rendons tout plus joli!

Commencez par créer un nouveau dossier pour les styles, ajoutez-y un nouveau fichier `main.css` et créez un lien vers celui-ci dans la section d'en-tête **header** `index.html`.

```
<link rel="stylesheet" href="styles/main.css" />
```
Après cela, importez les polices que vous allez utiliser. J'ai décidé d'aller avec  [Comfortaa](https://fonts.google.com/specimen/Comfortaa?query=comfortaa)  et  [Source Sans Pro](https://fonts.google.com/specimen/Source+Sans+Pro?query=source+sa) . Visitez  [Google Fonts](https://fonts.google.com/)  et choisissez celles que vous voulez et importez-les par-dessus le fichier `main.cs`.



```
@import url("https://fonts.googleapis.com/css2?family=Comfortaa:wght@700&family=Source+Sans+Pro:wght@900&display=swap");
```

Réinitialisez ensuite simplement les styles par défaut, définissez la couleur d'arrière-plan de votre page d'accueil et centrez les éléments à l'aide de CSS GRID.

```
* {
  margin: 0;
  text-decoration: none;
}

html,
body {
  height: 100%;
  display: grid;
  place-items: center;
  background-color: black;
}

.page-wrapper {
  display: grid;
  place-items: center;
  text-align: center;
}
```
Stylisez maintenant le texte. Définissez la couleur des polices, la famille de polices, ajustez l'espacement des lettres et ajoutez une marge si nécessaire pour une belle apparence.

```
h1 {
  color: white;
  font-family: "Source Sans Pro", sans-serif;
  font-size: 5em;
  letter-spacing: -0.04em;
}

p {
  color: rgb(98, 0, 255);
  font-family: "Comfortaa", cursive;
  font-size: 1.5em;
  margin: 15px 0;
}

.divider {
  color: white;
}
```

Enfin, vous devez styliser les icônes. En fonction de votre couleur d'arrière-plan, définissez la couleur des icônes et leur taille. Pour l'interactivité, vous pouvez ajouter un changement de curseur et un changement de couleur d'arrière-plan d'icône au survol.

```
.icon {
  color: white;
  padding: 15px;
  border-radius: 50%;
}

.icon:hover {
  cursor: pointer;
  background-color: rgb(22, 22, 22);
  color:red;

}
```

Assurez-vous également de créer votre favicon pour votre site. Vous le verrez dans l'onglet du navigateur avant le titre de la page. Pour cela, je recommanderais  [favicon.io](https://favicon.io/) . Ajoutez-le à votre répertoire d'icônes et créez un lien vers celui-ci dans l'en-tête `index.html`.

```
<link rel="icon" href="icons/favicon.ico" />
```

Bien joué! Le résultat final devrait ressembler à ceci:


![Screen Shot 2020-10-28 at 1.14.42 PM.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1603887433651/kC2rJ-b2A.png)


Avant le déploiement, assurez-vous de tester différents paramètres dans le fichier main.css. Le design est toujours subjectif, mais je recommanderais quelque chose dans les lignes de grand contraste:


![Screen Shot 2020-10-28 at 2.20.53 PM.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1603891290719/vVf_Pecjz.png)



![Screen Shot 2020-10-28 at 2.19.20 PM.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1603891300786/-amy4WYke.png)

Toutes mes félicitations! Vous venez de créer une page d'accueil simple sans frameworks CSS ou JavaScript sophistiqués et en moins de 100 lignes de code.

Le code source est disponible sur  [GitHub](https://github.com/lawalalao/landing-page) . Donnez-moi un ⭐ si vous avez aimé 🎉🥳