## Comment utiliser Async / Await en JavaScript

Le but de cet article est de vous apprendre à travailler avec les promises en utilisant async / await. Pourquoi voudriez-vous utiliser async / await, cependant? L'avantage le plus significatif est qu'il rend le code plus lisible et plus propre en supprimant les chaînes  promises.
Par conséquent, voyons ce qu'est async / await et comment l'utiliser.

# La promise habituelle

Voyons un exemple de promise en JavaScript:


```
fetch("https://api.app/v1/users/cp"); // faux URL
.then(response => response.json());
.then(console.log);
``` 
Cela vous semble probablement familier. Maintenant, voyons le même code réécrit avec async / await.


```
async function getData() {
    const response = await fetch("https://api.app/v1/users/cp/avatar"); // faux URL
    const data = response.json();

    console.log(data);
}
``` 
lequel préfères-tu? À mon avis, il est plus clair de comprendre ce qui se passe dans le code lors de l'utilisation de async / await.

# Qu'est-ce que async / await

Async / Await est construit au-dessus des promises et nous permet de mieux écrire du code asynchrone. C'est une nouvelle façon d'écrire du code asynchrone, en plus des promises et des callbacks.

La puissance d'Async / Await est qu'elle rend le code plus organisé et plus propre. Cela le rend également plus "synchrone".

Il existe deux mots-clés particuliers:


- `async`

- `await`

Nous utilisons le mot-clé `async` au début de la fonction. Lorsque vous utilisez le mot-clé `async`, cela signifie que la fonction renvoie toujours une promise. De plus, si nous voulons utiliser le mot-clé `await` dans une fonction, cette fonction doit toujours commencer par le mot-clé `async`. Le code ci-dessous renvoie une promise lorsque nous appelons la fonction `greeting`. L'objet de promise contient un état (rempli ou rejeté) et un résultat (dans ce cas, une chaîne).


```
async function greeting(name) {
    return `Hello, ${name}!`;
}
``` 

Deuxièmement, nous pouvons utiliser le mot-clé `await` pour attendre qu'une promisese réalise et renvoyer le résultat.


```
async function greeting(name) {
    return greet = await Promise.resolve(`Hello, ${name}!`);
}

greeting("lawal").then(console.log); // Retourne "Hello, lawal!"

``` 
L'exemple ci-dessus peut ne pas être utile, mais imaginez quand vous effectuez un appel d'API - voir l'exemple ci-dessus, dans la première section de l'article.

# Autres avantages

## Meilleure gestion des erreurs

Tout d'abord, nous pouvons gérer le code synchrone et le code asynchrone dans la même construction. Deuxièmement, s'il y a une erreur lors de la résolution de la promise, le contrôle passe au bloc `catch` pour gérer l'erreur.

Vous pouvez même encapsuler plusieurs promises dans le même bloc `try`, et le code détecte les erreurs de toutes les promises, pas seulement d'une. Il vous indique également où l'erreur s'est produite et dans quelle promise.


```
async function getUserInfo() {
    try {
        const response = await fetch("https://api.app/v1/users/cp/avatar"); // faux URL
        const data = response.json();

        console.log(data);
    } catch (err) {
        console.log(err);
    }
}
``` 
Dans l'extrait de code ci-dessus, le code saute au bloc catch en cas d'erreur.

## Meilleur code

Async / await nous permet d'écrire un code clair et meilleur. Cela permet de comprendre plus facilement et plus rapidement ce qui se passe dans le code, car il ressemble plus à du code synchrone.

Même dans les extraits de code courts tels que ceux de la section "La promise habituelle" (voir plus haut), nous pouvons voir à quel point le code est propre.

## Conditionnels

Un autre avantage de l'utilisation de async / await est qu'il est facile et propre a utiliser avec les conditions. Les extraits de code ci-dessous sont basiques et ne gèrent pas les erreurs. Leur seul objectif est de montrer la différence entre les promises et async / wait lors de l'utilisation de conditions.


```
const getUserInformation = () => {
    return getUser()
    .then(user => {
      if (user.profile) {
        return getUserProfile(user.id)
        .then(userProfile) {
          console.log(userProfile);
          return userProfile;
        }
      } else {
        console.log(user);
        return user;
      }
    });
};
``` 
L'extrait de code ci-dessus illustre l'utilisation de conditions dans une promise. Même si le code n'est pas complexe, il est difficile de le lire. Imaginez maintenant à quel point le code serait complexe si nous avions plus d'instructions `if` et plus de requêtes.

Ci-dessous, vous pouvez voir le code réécrit en utilisant async / await. N'est-ce pas mieux? Il est plus facile de lire le code et de comprendre ce qui se passe.


```
const getUserInformation = async () => {
  const user = await getUser();

  if (user.profile) {
    const userProfile = await getUserProfile(user.id);

    console.log(userProfile);
    return userProfile;
  } else {
    console.log(user);
    return user;
  }
};
``` 
Par conséquent, vous pouvez améliorer votre code en convertissant les promises en async / await. Vous pouvez voir qu'ils améliorent considérablement la lisibilité du code.

# Conclusion

En conclusion, récapitulons ce que vous avez appris:

     
- 
En ajoutant async à votre en-tête de méthode, vous retournez toujours une promise. En plus de cela, il vous permet d'utiliser le mot clé `await`. Par conséquent, vous pouvez attendre qu'une promise soit résolue.
     
- 
Rend le code plus explicite, plus facile à comprendre et plus concis.
     
- 
En utilisant le mot-clé `await`, vous empêchez le code de s'exécuter jusqu'à ce que la promise soit résolue ou rejetée.
     
- 
Lorsque la promesse ne peut être réglée, elle génère une exception.