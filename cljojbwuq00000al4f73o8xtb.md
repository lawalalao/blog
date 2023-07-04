---
title: "Mastodon vs. Twitter : Une alternative décentralisée avec une API puissante"
datePublished: Tue Jul 04 2023 16:59:27 GMT+0000 (Coordinated Universal Time)
cuid: cljojbwuq00000al4f73o8xtb
slug: mastodon-vs-twitter-une-alternative-decentralisee-avec-une-api-puissante
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1688489435695/22232cac-d4be-42b6-9566-e1500d43c70c.png
tags: twitter, python, apis, developer, mastodon

---

Depuis que Elon Musk a introduit des limites strictes sur l'utilisation de l'API Twitter, ainsi que le nombre de tweets par utilisateurs en une journée, de nombreux utilisateurs ont cherché des alternatives pour continuer à interagir avec les réseaux sociaux en toute liberté et moi dans le même cas de manière automatisée. Mastodon, une plateforme de médias sociaux décentralisée, offre une solution prometteuse avec son API robuste. Dans cet article, nous explorerons l'API Mastodon et apprendrons comment créer une application automatisée pour suivre l'arrivée de nouveaux membres d'une communauté ou d'un pays spécifique.

Nous discuterons également des raisons pour lesquelles Mastodon est un choix intéressant, de ses similitudes avec Twitter, des ressources pour mieux utiliser le réseau, et de ses limites.

1. ## Pourquoi choisir Mastodon :
    
    Mastodon se distingue de Twitter et d'autres réseaux sociaux centralisés par sa structure décentralisée. Par exemple, au lieu d'un seul serveur contrôlé par Twitter, Mastodon est composé de multiples instances indépendantes qui peuvent interagir entre elles. Cette décentralisation offre plusieurs avantages, tels qu'une modération plus communautaire, une plus grande confidentialité des données et une absence de publicité intrusive. Les utilisateurs peuvent choisir leur instance en fonction de leurs préférences et rejoindre des communautés spécifiques.
    
2. ## Ressemblances avec Twitter :
    
    ![What is Mastodon? All you need to know to switch from Twitter | Stuff](https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcTd54y1itW6GjH0sw_HPCCOkmk0K6ZcKy1QUj86WHvwtfm8xfj1hyRpyeVaPJ4C4nwZvK8&usqp=CAU align="left")
    
    Mastodon partage certaines similitudes avec Twitter, ce qui en fait une transition plus facile pour les utilisateurs habitués à cette plateforme. Par exemple:
    
    * les toots de Mastodon sont similaires aux tweets de Twitter.
        
    * Les utilisateurs peuvent utiliser des hashtags, mentionner d'autres utilisateurs et créer des listes.
        
    
    De plus, Mastodon offre des fonctionnalités supplémentaires, comme la possibilité de personnaliser l'apparence de son instance et d'interagir avec d'autres instances décentralisées.
    
3. ## Explorer Mastodon en tant que néophyte :
    
    Pour les utilisateurs novices qui souhaitent découvrir Mastodon, il existe plusieurs ressources utiles à explorer. Par exemple, le [guide officiel](https://mastodon.help/) de Mastodon fournit des informations détaillées sur la plateforme et ses fonctionnalités. Les forums de discussion et les communautés en ligne, tels que le subreddit de reddit, Mastodon, offrent un soutien précieux et permettent de poser des questions aux utilisateurs expérimentés. En outre, certains utilisateurs partagent des tutoriels et des conseils sur leurs comptes .
    
4. ## Les limites de Mastodon :
    
    ![GIF sans limites limitless - GIF animé sur GIFER](https://i.gifer.com/7BNg.gif align="left")
    
    Bien que Mastodon offre de nombreux avantages, il est important de comprendre ses limites. Par exemple, chaque instance Mastodon peut avoir ses propres **règles de modération et politiques de contenu**. Il est donc essentiel de choisir une instance qui correspond à ses valeurs et à ses préférences. De plus, Mastodon peut présenter une courbe d'apprentissage pour les utilisateurs habitués à d'autres réseaux sociaux. Enfin, comme toute plateforme, il peut également être sujette à des problèmes techniques ou des temps d'arrêt occasionnels (vous connaissez la fameuse erreur 500).
    
5. ## Création d'une application Mastodon :
    
    Maintenant, explorons comment créer notre propre application Mastodon pour automatiser le repost de messages contenant des hashtags spécifiques.
    
    * **Installation des dépendances** : Pour commencer, nous devons installer les bibliothèques nécessaires pour interagir avec l'API Mastodon. Dans notre exemple, nous allons utiliser Python donc vous pouvez installer la bibliothèque "[Mastodon.py](http://Mastodon.py)" en utilisant pip et Magalodon si vous décidez Javascript donc npm ou yarn.
        
    
    ```python
    pip install Mastodon.py
    ```
    
6. **Création de l'application et génération des identifiants** :
    
    Connectez-vous à votre compte Mastodon et accédez aux paramètres de votre compte. Recherchez la section "Applications" et créez une nouvelle application en fournissant un nom et une description. Cela générera les identifiants nécessaires pour accéder à l'API Mastodon.
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1688413081491/88970dee-14c0-4bad-96a9-7df0b81aa7da.png align="center")
    

```python
from mastodon import Mastodon

Mastodon.create_app(
    'MyBot',
    api_base_url='https://mastodon.instance.com',
    to_file='mybot_clientcred.secret'
)
```

1. **Authentification et autorisation** : Maintenant, nous devons nous authentifier auprès de l'API Mastodon en utilisant les identifiants de notre application et obtenir un jeton d'accès. Ce jeton sera utilisé pour toutes les requêtes ultérieures.
    

```python
from mastodon import Mastodon

mastodon = Mastodon(
    client_id='mybot_clientcred.secret',
    api_base_url='https://mastodon.instance.com'
)

mastodon.log_in(
    'username',
    'password',
    to_file='myusercred.secret'
)
```

**Interagir avec l'API Mastodon** : Maintenant que nous sommes authentifiés, nous pouvons interagir avec l'API Mastodon pour rechercher des messages contenant des hashtags spécifiques et les repost automatiquement.

```python
from mastodon import Mastodon

mastodon = Mastodon(
    access_token='myusercred.secret',
    api_base_url='https://mastodon.instance.com'
)

def repost_hashtag(hashtag):
    results = mastodon.timeline_hashtag(hashtag)

    for toot in results:
        # Repost the toot using the desired method
        # ...

repost_hashtag('mastodon`)
```

# **Conclusion :**

L'utilisation de l'API Mastodon offre une alternative décentralisée et puissante pour interagir avec les réseaux sociaux. Mastodon, avec ses similitudes avec Twitter et ses fonctionnalités uniques, offre une expérience différente pour les utilisateurs. En comprenant ses limites et en explorant les ressources disponibles, vous pouvez tirer le meilleur parti du réseau. En créant notre propre application, nous pouvons automatiser des tâches telles que le repost de messages pour suivre l'arrivée de nouveaux membres d'une communauté spécifique en faisant un focus sur les hashtags,les pays à l'inscription etc ... N'hésitez pas à me faire un retour si vous rencontrez de problèmes sur les librairies car OUI vous aurez à réecrire une partie de ces librairies. Merci et bonne lecture.