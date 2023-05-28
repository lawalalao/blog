---
title: "Devenez Un Dompteur Du Cors  🧙‍♀️"
seoTitle: "Devenez un dompteur du CORS"
seoDescription: ""Débloquez le pouvoir du CORS : Guide pratique pour une intégration sans faille des ressources externes""
datePublished: Sun May 28 2023 10:30:02 GMT+0000 (Coordinated Universal Time)
cuid: cli7a4mbb000109lddz02gd6s
slug: devenez-un-dompteur-du-cors
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1685269695073/cd1cad22-f719-466b-89c3-7cffe169ec0f.png
tags: beginners, cors, cors-errors, wizard

---

Yeah, c'est enfin arrivé ! 😲 Vous avez bossé dur pour développer votre application web frontend, mais dès que vous tentez d'accéder à une ressource sur un autre serveur pour l'afficher dans votre appli, vous vous tapez l'erreur CORS de l'enfer. Mais no soucis, je vais vous remettre tout ça d'équerre en vous expliquant ce que c'est que le CORS, pourquoi vous vous tapez toujours ces erreurs CORS et quelques astuces pour les résoudre. Bien sûr, y'a sûrement d'autres alternatives, alors hésitez pas à les partager avec moi et tous les autres lecteurs... Let'ssss gooooo !

# Terminologie CORS

Avant d'entrer dans le vif du sujet, passons en revue quelques termes importants.

* L'origine est une url composée de trois parties :
    
    * **Schéma URI:** par exemple http:// ou https://
        
    * **Nom d'hôte**: comme [twitter.com](https://twitter.com)
        
    * **Numéro de port:** par exemple 80 pour HTTP et 443 pour HTTPS. Vous ne les verrez jamais dans votre barre d'adresse, car cela est pris en charge en background, mais essayez de coller **https://twitter.com:443** dans votre barre d'adresse et vous allez remarquer qu'il vous dirige automatiquement vers le site web attendu.
        
* Les **requêtes HTTP** sont des requêtes qu'une application web effectue pour accéder aux ressources d'une application. Il existe différents types de requêtes HTTP, notamment **GET** (qui vous permet d'obtenir des ressources), **DELETE** (qui vous permet de supprimer des ressources), etc. Vous trouverez ci-dessous un exemple de requête **GET :**,
    
    * lorsque vous utilisez twitter dans votre navigateur pour cliquer sur le profil d'une personne et que vous souhaitez voir ses tweets. L'application web envoie une requête HTTP au serveur à l'adresse [http://twitter-api.com](http://twitter-api.com) qui répond avec les tweets de cette personne pour que vous puissiez les voir.
        

![Diagram of a sample HTTP Get Request](https://cdn.hashnode.com/res/hashnode/image/upload/v1666753233263/qggiPXYKH.png?auto=compress,format&format=webp align="left")

* **Demande d'origine croisée** 🤣🤣😂 (Cross-Origin Request) c'est lorsqu'une demande est faite à partir d'une origine vers une autre origine. Exemple ? Vous recherchez des images de chats sur [https://flikr.com](https://flikr.com) et cette application interroge [https://image.com/api](https://image.com/api) pour demander que des photos de chats soient affichées pour vous.
    
    ![Diagram of a Sample Cross Origin Request](https://cdn.hashnode.com/res/hashnode/image/upload/v1666753827447/Ah3K4EEWW.png?auto=compress,format&format=webp align="left")
    
* Les **en-têtes HTTP (HTTP HEADERS)** sont des données qui décrivent la requête ou la réponse envoyée. Ils fournissent des informations supplémentaires, un peu comme la bio de votre profil Twitter. Des exemples d'en-têtes tels que **Host** et **access-control-allow-origin** sont présentés dans l'image ci-dessous.
    
    ![Diagram of an HTTP response with headers](https://cdn.hashnode.com/res/hashnode/image/upload/v1666753299656/T2e6UkWTE.png?auto=compress,format&format=webp align="left")
    

**Un proxy** est un serveur qui sert d'intermédiaire entre un client (votre navigateur) et un autre serveur.

# Qu'est-ce que CORS ?

[CORS](https://medium.com/@electra_chong/what-is-cors-what-is-it-used-for-308cafa4df1a) (Cross Origin Resource Sharing) est un ensemble de règles que tous les navigateurs mettent en place pour sécuriser les applications web contre les accès indésirables (+1 pour la sécurité 🥳). (+1 pour la sécurité 🥳) L'une des méthodes utilisées par les navigateurs consiste à vérifier la présence d'informations spécifiques dans une réponse HTTP, qui lui permettent de savoir que l'application web qui demande une ressource a reçu l'autorisation de le faire. C'est le comportement par défaut du navigateur, sauf s'il sait déjà qu'une application web a accès à une ressource.

![Meme of spongebob checking response headers](https://cdn.hashnode.com/res/hashnode/image/upload/v1666577217219/oVrab04kt.jpg?auto=compress,format&format=webp align="left")

## Comment fonctionne CORS ?

À un niveau élevé, selon le type de requête effectuée, CORS fonctionne de deux manières. Examinons les deux dans le contexte de l['obtention ou de la modification d'un tweet](https://blog.twitter.com/en_us/topics/product/2022/twitter-new-edit-tweet-feature-only-test) (oui, ça existe maintenant).

1. Lorsque votre application web veut récupérer un tweet SANS le modifier, le navigateur vérifie que la réponse contient un en-tête **access-control-allow-origin** qui correspond à l'origine de l'application twitter requérante (par exemple, [https://twitter.com](https://twitter.com)), ou un **\*** pour indiquer au navigateur que toutes les origines sur le web y ont accès. C'est le comportement typique des requêtes GET.
    
2. Lorsque votre application web souhaite **METTRE À JOUR** un tweet, plusieurs choses se produisent.
    
    * Le navigateur envoie une pré-requête, qui est une petite requête de type **OPTIONS**, qui donne au serveur des informations sur la requête que vous essayez d'envoyer pour mettre à jour votre tweet. L'application backend examine les **en-têtes** fournis dans la pré-requête afin de déterminer si la requête que vous souhaitez effectuer est autorisée. Certains des en-têtes ajoutés à la pré-requête sont [**Access-Control-Request-Method**](https://developer.mozilla.org/en-US/docs/Web/HTTP/Headers/Access-Control-Request-Method) et [**Access-Control-Request-Headers.**](https://developer.mozilla.org/en-US/docs/Web/HTTP/Headers/Access-Control-Request-Headers) Ils donnent au serveur des informations telles que la méthode de la requête, etc. Cette couche supplémentaire de protection est utile car les requêtes qui peuvent modifier les ressources sont plus susceptibles d'avoir des effets néfastes que les requêtes qui ne le peuvent pas.
        
    * Une fois que le serveur a reçu la demande (pré-requête), il répond et vous fait savoir s'il a accepté une demande ou pas selon les paramètres que vous lui avez donnés dans les en-têtes . Vous trouverez ci-dessous une explication simplifiée de la conversation entre le navigateur et le serveur backend.
        
        ![Conversation between browser and server, but make them both toddlers](https://cdn.hashnode.com/res/hashnode/image/upload/v1666772758378/xVPfKzFuc.png?auto=compress,format&format=webp align="left")
        

## Pourquoi obtenez-vous une erreur CORS ? 🙄

L'une des principales raisons des erreurs CORS dans le développement est que le serveur auquel vous envoyez une requête peut ne pas inclure l'en-tête **access-control-allow-origin** dans les réponses qu'il vous renvoie. Ou s'il le fait, il n'inclut pas l'URL de votre application frontend dans la liste des origines approuvées. Les solutions ci-dessous visent à remédier à ce problème. Vous pouvez trouver une longue liste d'autres causes d'erreurs CORS [ici](https://developer.mozilla.org/en-US/docs/Web/HTTP/CORS/Errors).

## Quelques moyens de résoudre les erreurs CORS

1. **Activer CORS sur le backend** : A quoi cela ressemble-t-il ? L'activation de CORS et l'ajout de l'origine de votre application frontend à la liste des origines approuvées pour l'API.
    
    * **Avantage** : vous pouvez résoudre le problème en interne en quelques lignes de code.
        
    * **Inconvénient** : Vous devez faire des mises à jour dans le backend, ce à quoi vous n'avez pas forcément accès.
        
    * **Exemple** : Voici comment j'ai procédé pour un projet récent sur lequel je travaillais en utilisant le framework Phoenix elixir pour mon backend. Tout d'abord, j'ai trouvé une bibliothèque CORS appelée **Corsica** qui ajouterait l'origine de mon front-end à la liste des origines approuvées. Ensuite, je l'ai ajoutée en tant que dépendance (une dépendance est un code tiers dont votre code a besoin pour fonctionner) à mon projet de backend. Dans elixir, vous ajoutez une nouvelle dépendance dans votre fichier mix.exs comme indiqué ci-dessous.
        
    * ```erb
            defp deps do 
            [
             ...
             {:corsica, "~> 1.1.3"} 
            ] 
            end
        ```
        
        Ensuite, j'ai ajouté l'origine de mes applications web frontend à la liste des origines approuvées en ajoutant Corsica, et en plaçant l'origine de mon frontend dans la liste des origines approuvées pour accéder aux ressources de mon backend.
        

```erb
plug Corsica, origins: ["http://localhost:3000"]
```

En fonction du backend que vous choisissez, vous pouvez définir l'URL d'origine en fonction de l'environnement dans lequel vous vous trouvez. Vous suivrez une approche similaire pour activer CORS sur le backend dans de nombreux frameworks backend.

1. Envoyez vos requêtes à un proxy qui ajoute les en-têtes attendus à la réponse. Le code pour cela se trouve dans votre application frontend. Mais qu'est-ce que cela signifie exactement ? Au lieu que votre application envoie des requêtes à https://twitter.com/, vous pouvez utiliser un proxy CORS comme [CORS anywhere](https://github.com/Rob--W/cors-Anywhere) qui est situé à <mark>https://cors-anywhere.herokuapp.com/</mark> comme ceci -&gt; <mark>https://cors-anywhere.herokuapp.com/https://twitter.com</mark>.
    

* **Avantage** : vous n'obtenez plus l'erreur CORS et vous avez désormais accès aux ressources que vous demandiez, car l'en-tête attendu a été ajouté par le proxy CORS.
    
* **Inconvénient** : La demande peut potentiellement prendre plus de temps à être satisfaite car vous serez à la merci de la vitesse à laquelle le proxy externe envoie, reçoit et met à jour la réponse pour inclure l'en-tête dont CORS a besoin pour être satisfait. De plus, vous devez faire confiance à 100% au proxy, car il peut lire et faire n'importe quoi avec la réponse que vous attendez en retour. Je déconseille fortement l'utilisation d'un proxy pour tout ce qui n'est pas des données triviales.
    
    ![Proxy.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1666753400946/Gn6dFPKHj.png?auto=compress,format&format=webp align="left")
    

1. **Envoyez vos requêtes à votre propre proxy** afin de réduire les lenteurs potentielles liées à l'attente d'un proxy externe qui ajouterait les en-têtes pour vous.
    

* **Avantage** : vous n'avez pas besoin d'apporter de modifications au back-end. Vous pouvez allouer autant de ressources que vous le souhaitez à votre proxy pour réduire les lenteurs.
    
* **Inconvénient** : Vous devrez gérer les ressources de votre proxy, mais il est probable que si vous hébergez une application back-end, cet inconvénient ne soit pas si important. Vous pouvez voir un exemple de comment faire [ici](https://minasami.com/2021/06/10/cors-errors-fix-with-reactjs.html).
    

1. **Désactiver temporairement CORS sur votre navigateur**
    
    * **Avantage** : vous pouvez développer et tester immédiatement les requêtes de votre navigateur vers des sources croisées.
        
    * **Inconvénient** : Cette méthode ne doit être utilisée que temporairement et ne fonctionne qu'en phase de développement.
        
        L'erreur CORS subsistera lorsque vous déployerez votre application en production. Selon le navigateur que vous utilisez, vous pouvez soit installer une extension pour contourner CORS, OU si vous utilisez Safari, vous pouvez manuellement désactiver CORS temporairement en activant le menu développeur et en cliquant sur l'option ci-dessous :
        
    
    ![Screen Shot 2022-10-24 at 8.54.26 PM.jpg](https://cdn.hashnode.com/res/hashnode/image/upload/v1666662869152/Kppb9yDRw.jpg?auto=compress,format&format=webp align="left")
    

# Récapitulatif

Pour faire court, **CORS** est un ensemble de règles que chaque navigateur a universellement mis en place pour assurer la sécurité d'une application web et de ses utilisateurs. Et comme la plupart des choses dans le monde du développement, il existe plusieurs méthodes pour corriger toute erreur CORS potentielle. Je sais qu'elles peuvent être un casse-tête, mais maintenant que vous savez de quoi il s'agit et que vous connaissez quelques méthodes pour les résoudre, c'est gagné !

Maintenant, allez, donnez à ces erreurs CORS une bonne correction 💪

![goku-jumping-goku.gif](https://cdn.hashnode.com/res/hashnode/image/upload/v1666663055388/0vdezSCDh.gif?auto=format,compress&gif-q=60&format=webm align="left")

### Vous voulez descendre dans le trou du lapin ? Voici quelques lectures complémentaires en anglais :

* [Que sont les mandataires CORS et quand sont-ils sûrs ?](https://httptoolkit.com/blog/cors-proxies/)
    
* [Proxy CORS Anywhere](https://github.com/Rob--W/cors-anywhere)
    
* [Voler des données sensibles avec une attaque CORS](https://www.whiteoaksecurity.com/blog/fun-with-cors/)
    

Alors vous aimé cet article ? n'hésitez pas à le partager autour de vous et abonnez-vous ... Surtout n'hésitez pas à partager avec moi et d'autres lecteurs d'autres moyens pour résoudre les erreurs CORS. Merci