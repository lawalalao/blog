---
title: "Démystifier les architectures API : Un guide complet"
datePublished: Tue Jul 18 2023 14:54:56 GMT+0000 (Coordinated Universal Time)
cuid: clk8f1psy000009jr3i0j5ful
slug: demystifier-les-architectures-api-un-guide-complet
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1689692053295/5794b855-0844-4f77-b2f3-f0688a4a269e.avif
tags: development, apis, architecture, software-engineering

---

Dans le monde interconnecté d'aujourd'hui, les interfaces de programmation d'applications (API) jouent un rôle crucial en permettant une communication et un échange de données transparents entre divers systèmes logiciels. Cependant, avec la multitude d'architectures d'API disponibles, il est important de comprendre leurs forces, leurs faiblesses et leurs cas d'utilisation. Dans cet article, nous allons explorer sept architectures d'API populaires : REST, GraphQL, WebSockets, webhooks, SOAP, gRPC et MQTT, ainsi que leurs principales caractéristiques et leurs applications réelles.

## REST (Representational State Transfer) :

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1683882146370/f016ce62-8fc4-40fc-863e-d12ef8fb66a0.png?auto=compress,format&format=webp align="left")

REST est un style architectural largement adopté pour la création d'API, qui met l'accent sur la **simplicité, l'évolutivité et l'absence d'état**. Il fonctionne sur HTTP et utilise des méthodes HTTP standard (GET, POST, PUT, DELETE) pour effectuer des opérations sur les ressources. Les API REST suivent une approche orientée ressources, où chaque ressource est identifiée par une URL unique (Uniform Resource Locator). Cette architecture est connue pour sa facilité d'intégration, sa grande compatibilité et ses capacités de mise en cache, ce qui la rend adaptée à une grande variété d'applications, en particulier celles qui impliquent des opérations CRUD (Create, Read, Update, Delete).

<mark>Voici un petit exemple pour illustrer le fonctionnement de REST :</mark>

En supposant que nous ayons la même application de blog avec des entités "User" et "Post", une API REST suit une approche orientée ressources où chaque entité est représentée par une URL unique.

Pour récupérer le nom d'utilisateur et les titres des messages d'un utilisateur spécifique à l'aide de REST, un client doit généralement effectuer plusieurs requêtes auprès de différents points de terminaison (endpoints).

1. Tout d'abord, le client fait une demande pour récupérer les informations de l'utilisateur :
    
    ```http
    GET /users/123
    ```
    
    Le serveur réponds avec les détails de l'utilisateur
    
    ```json
    {
       "id": 123,
       "username": "john_doe",
       "email": "john.doe@example.com",
       ...
     }
    ```
    
    1. Ensuite, le client fera une autre demande pour récupérer les messages associés à l'utilisateur:
        
        ```http
         GET /users/123/posts
        ```
        
        Le serveur répond par une liste/tableau de messages:
        
        ```json
         [  
             {    "id": 1,    "title": "RESTful APIs 101",    ...  }, 
             {    "id": 2,"title": "Building Scalable Web Applications",...} 
          ]
        ```
        
    
    Le client reçoit les réponses séparément et combine les données selon ses besoins.
    
    REST nécessite plusieurs requêtes pour extraire des données connexes. Cela peut entraîner une extraction excessive ou insuffisante des données, car le client reçoit la représentation complète de la ressource sans avoir la possibilité de demander de manière sélective des champs spécifiques.
    
    Les API REST s'appuient sur des méthodes HTTP standard pour effectuer des opérations sur les ressources. Par exemple, la création d'un nouveau message implique l'envoi d'une requête **POST** au point de terminaison <mark>/posts</mark>, la mise à jour d'un message utilise une requête **PUT** ou **PATCH** au point de terminaison <mark>/posts/{postId}</mark>, et la suppression d'un message se fait avec une requête **DELETE** au même point de terminaison.
    

## GraphQL:

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1683889468736/c96f9542-e396-482a-b784-9fbe9e30314e.png?auto=compress,format&format=webp align="left")

GraphQL est un langage de requête et un moteur d'exécution d'API qui offre une approche souple et efficace de la recherche et de la manipulation de données. Contrairement à REST, qui nécessite plusieurs requêtes pour obtenir des données connexes, GraphQL permet aux clients de demander précisément les données dont ils ont besoin en une seule requête. Il permet aux clients de définir leurs besoins en matière de données à l'aide d'une syntaxe déclarative, ce qui accroît l'efficacité et minimise l'extraction excessive ou insuffisante de données. GraphQL est particulièrement utile pour les applications nécessitant des données complexes, les applications mobiles et les scénarios dans lesquels l'optimisation de la bande passante est cruciale.

1. **Par exemple** : Supposons que nous ayons une application de blog avec deux types d'entités : "User" et "Post". Chaque utilisateur peut être associé à plusieurs messages. Avec une API GraphQL, un client peut demander des données spécifiques à ces entités en une seule requête.
    
    Voici un exemple de requête GraphQL qui récupère le nom d'utilisateur et les titres des messages d'un utilisateur spécifique :
    

```json
    query {
      user(id: 123) {
        username
        posts {
          title
        }
      }
    }
```

Dans cette requête, le client spécifie qu'il souhaite récupérer les données d'un utilisateur dont l'ID est 123. Il précise également qu'il souhaite obtenir le nom d'utilisateur et les titres des messages associés à cet utilisateur.

Le serveur, qui met en œuvre l'API GraphQL, reçoit cette requête et la résout en conséquence. Il récupère les données demandées à partir de la source de données sous-jacente, telle qu'une base de données. Au lieu de renvoyer une structure de réponse fixe, **GraphQL permet au serveur de renvoyer les données dans la forme exacte demandée par le client**.

Le serveur traite la requête et répond avec les données demandées au format JSON :

```json
    {
      "data": {
        "user": {
          "username": "john_doe",
          "posts": [
            {
              "title": "GraphQL Introduction"
            },
            {
              "title": "Advanced GraphQL Techniques"
            }
          ]
        }
      }
    }
```

Le client reçoit une réponse contenant les données demandées, à savoir le nom de l'utilisateur et un tableau de titres d'articles. Cette approche élimine le problème de l'extraction excessive ou insuffisante des données, généralement associé aux API REST traditionnelles.

Avec GraphQL, les clients ont la possibilité de demander des champs spécifiques, des relations imbriquées et même d'effectuer des mutations (mises à jour) ou des abonnements (données en temps réel) au sein d'une seule requête. Cela réduit le nombre d'allers-retours entre le client et le serveur, améliore les performances et permet une récupération efficace des données.

## Websockets:

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1683886671020/22c36ba5-390f-4e5e-b946-1a36ee41b151.png?auto=compress,format&format=webp align="left")

1. Les WebSockets introduisent un canal de communication bidirectionnel et en duplex intégral entre un client et un serveur, permettant un flux de données en temps réel. Contrairement aux architectures traditionnelles requête-réponse basées sur le protocole HTTP, les WebSockets permettent au serveur et au client d'initier le transfert de données à tout moment, facilitant ainsi les mises à jour instantanées et les notifications push. Cette architecture est bien adaptée aux applications nécessitant une collaboration en temps réel, aux applications de chat, aux téléscripteurs boursiers et aux jeux multijoueurs.
    
    Exemple : Supposons que nous ayons une application de chat en temps réel où les utilisateurs peuvent envoyer et recevoir des messages. Avec les WebSockets, les clients peuvent établir un canal de communication bidirectionnel et persistant avec le serveur, ce qui permet des mises à jour en temps réel.
    
    **Connexion côté client** : Le client établit une connexion WebSocket en adressant au serveur une demande de prise de contact WebSocket :
    

```http
    GET /chat
```

**Connexion côté serveur** : Le serveur accepte la demande de prise de contact WebSocket et établit une connexion permanente avec le client.

**Communication en temps réel** : Une fois la connexion WebSocket établie, le client et le serveur peuvent s'envoyer des messages à tout moment, sans que le client ait besoin d'initier une demande. Cela permet une communication bidirectionnelle en temps réel.

<mark>Par exemple, lorsqu'un utilisateur envoie un message, le client peut envoyer un message WebSocket au serveur :</mark>

```json
    SEND: {
      "sender": "user123",
      "message": "Hello, everyone!"
    }
```

Le serveur reçoit le message WebSocket et le diffuse à tous les clients connectés, y compris l'expéditeur. Chaque client connecté reçoit le message instantanément, ce qui permet des mises à jour en temps réel dans leur interface de discussion.

De même, si un autre utilisateur envoie un message, le serveur le diffuse à tous les clients connectés, garantissant ainsi que tous les participants reçoivent le message en temps réel.

Les WebSockets sont idéales pour les applications qui nécessitent des mises à jour instantanées et une collaboration en temps réel, telles que les applications de chat, les notifications en direct, les jeux multijoueurs et les téléscripteurs financiers.

La connexion WebSocket reste ouverte jusqu'à ce que le client ou le serveur décide de la fermer. Cela permet une communication continue et efficace sans avoir à établir une nouvelle connexion pour chaque requête.

**Il est important de noter que les WebSockets ne remplacent pas les API REST ou GraphQL traditionnelles, mais les complètent en offrant des capacités en temps réel.**

## Webhooks:

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1683888339074/95a4774a-1b35-424d-83e0-3f6975b82f26.png?auto=compress,format&format=webp align="left")

Les webhooks sont un moyen pour les applications de recevoir des notifications automatiques ou des rappels lorsqu'un événement spécifique se produit. Au lieu d'interroger régulièrement une API pour obtenir des mises à jour, les webhooks permettent à l'API d'envoyer de manière proactive des données à une URL prédéfinie lorsqu'un événement intéressant se produit. Les développeurs peuvent définir leurs propres déclencheurs d'événements et spécifier comment l'application doit réagir. Les webhooks sont couramment utilisés pour intégrer des services externes, déclencher des actions basées sur des événements et construire des architectures basées sur les événements.

Prenons l'exemple d'un service d'abonnement à des articles d'un journal : nous souhaitons informer les abonnés de la publication d'un nouvel article.

**Configuration de l'abonnement** : Les abonnés fournissent au service de journal leur URL de rappel, généralement un point de terminaison sur leur serveur. Cette URL sera utilisée pour délivrer des notifications par webhook.

**Déclenchement de l'événement** : Lorsqu'un nouvel article est publié, le service du journal déclenche un événement et se prépare à envoyer une notification par webhook.

**Notification par webhook** : Le service du journal envoie une requête HTTP POST à l'URL de rappel de l'abonné, contenant des informations pertinentes sur l'article récemment publié. La charge utile peut se présenter sous différents formats, tels que JSON ou XML, en fonction de l'accord conclu entre le service d'actualités et l'abonné.

```json
 POST /webhook/callback
 Content-Type: application/json

 {
   "event": "article.published",
   "data": {
     "title": "New Blog Post",
     "author": "John Doe",
     "content": "Lorem ipsum dolor sit amet, consectetur adipiscing elit..."
   }
 }
```

**Traitement par le serveur de l'abonné** : Le serveur de l'abonné reçoit la notification du webhook au point de terminaison spécifié. Le serveur peut alors traiter la notification, extraire les données pertinentes et prendre les mesures appropriées, telles que la mise à jour d'une base de données locale, l'envoi d'une notification aux utilisateurs abonnés ou l'exécution de toute logique personnalisée requise.

En utilisant les webhooks, l'abonné n'a pas besoin d'interroger en permanence le service pour vérifier s'il y a de nouveaux articles. Au lieu de cela, le service envoie proactivement les données au serveur de l'abonné dès que l'événement (dans ce cas, la publication d'un nouvel article) se produit.

Les webhooks sont couramment utilisés pour intégrer des services externes, automatiser des flux de travail et construire des architectures axées sur les événements. Ils permettent de connecter des systèmes et d'effectuer des mises à jour en temps réel, ce qui réduit la nécessité d'une interrogation constante et améliore l'efficacité.

## SOAP (protocole d'accès simple aux objets)

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1683889374711/5c3dc793-08b7-4663-b94d-3331d9ecb455.png?auto=compress,format&format=webp align="left")

SOAP est un protocole permettant d'échanger des informations structurées par le biais de divers protocoles, notamment HTTP, SMTP, etc. Il utilise XML pour le formatage des messages et s'appuie sur le WSDL (Web Services Description Language) pour définir l'interface API. Les API SOAP suivent une approche plus rigide que REST et offrent des fonctionnalités avancées telles que la sécurité au niveau des messages et la gestion des transactions. Cette architecture est souvent utilisée dans les scénarios d'entreprise, où l'interopérabilité, le typage strict des données et les protocoles normalisés sont cruciaux.

**Prenons l'exemple d'un service météorologique basé sur SOAP qui fournit des informations sur la météo en fonction d'un lieu spécifique**.

**Construction d'une requête SOAP** : Le client construit une requête SOAP, généralement un document XML, en spécifiant l'opération et les paramètres requis. Par exemple, pour obtenir la météo d'un lieu spécifique, le client crée une requête SOAP comme celle-ci:

```xml
    <soap:Envelope xmlns:soap="http://www.w3.org/2003/05/soap-envelope">
      <soap:Body>
        <GetWeatherRequest xmlns="http://example.com/weatherservice">
          <Location>London</Location>
        </GetWeatherRequest>
      </soap:Body>
    </soap:Envelope>
```

**Envoi de la requête SOAP** : Le client envoie la requête SOAP à l'URL du point de terminaison SOAP du service météorologique en utilisant le protocole HTTP ou d'autres protocoles de transport. La demande est généralement envoyée sous la forme d'une requête HTTP POST, l'enveloppe SOAP constituant la charge utile de la demande.

**Réponse SOAP** : Le service météorologique reçoit la requête SOAP, la traite et génère une réponse SOAP. La réponse contient les données demandées ou le résultat de l'opération.

1. ```xml
    <soap:Envelope xmlns:soap="http://www.w3.org/2003/05/soap-envelope">
       <soap:Body>
         <GetWeatherResponse xmlns="http://example.com/weatherservice">
           <Weather>
             <Location>London</Location>
             <Temperature>22°C</Temperature>
             <Conditions>Sunny</Conditions>
           </Weather>
         </GetWeatherResponse>
       </soap:Body>
     </soap:Envelope>
    ```
    
    **Analyse de la réponse SOAP** : Le client reçoit la réponse SOAP et l'analyse pour en extraire les informations pertinentes. Dans le cas présent, la réponse contient les détails météorologiques pour le lieu demandé.
    
    SOAP fournit un moyen normalisé de définir la structure des demandes et des réponses à l'aide du WSDL (Web Services Description Language). Le WSDL définit les opérations, les formats de message et les points de terminaison disponibles pour un service SOAP, ce qui facilite la compréhension et l'interaction des clients avec le service.
    

### **gRPC (Google Remote Procedure Call):**

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1683891206077/7ded5e1b-dc0e-4859-9b02-ea73492e6b90.png?auto=compress,format&format=webp align="left")

1. gRPC est un cadre d'appel de procédure à distance (RPC) à haute performance et à code source ouvert développé par Google. Il permet aux applications écrites dans différents langages de communiquer de manière transparente et efficace. gRPC utilise Protocol Buffers comme langage de définition d'interface et fonctionne sur HTTP/2, offrant un flux bidirectionnel, un contrôle de flux et la prise en charge de divers mécanismes d'authentification. Il excelle dans les scénarios où la performance, la fiabilité et la communication agnostique sont essentielles, comme les architectures microservices, les systèmes distribués et la communication inter-services dans les environnements "cloud-native".
    
    Considérons un scénario dans lequel nous avons un service de gestion des utilisateurs basé sur gRPC avec deux opérations : "CreateUser" et "GetUser".
    
    Définition du protocole : Le fournisseur de services définit les opérations et les structures de données du service à l'aide de tampons de protocole. La définition du protocole spécifie les méthodes disponibles, les paramètres d'entrée et les types de retour.
    
    ```json
     syntax = "proto3";
    
     message CreateUserRequest {
       string name = 1;
       string email = 2;
     }
    
     message User {
       string id = 1;
       string name = 2;
       string email = 3;
     }
    
     service UserService {
       rpc CreateUser(CreateUserRequest) returns (User);
       rpc GetUser(GetUserRequest) returns (User);
     }
    ```
    
    **Génération de code** : En utilisant la définition du protocole, les générateurs de code créent des stubs client et serveur dans différents langages de programmation. Ces stubs fournissent une API simple que le client et le serveur peuvent utiliser pour interagir l'un avec l'autre.
    
    **Demande du client** : Le client invoque l'opération souhaitée en appelant la méthode correspondante sur le stub client généré. Par exemple, pour créer un nouvel utilisateur, le client appelle la fonction suivante :
    
    1. ```http
         user = userServiceStub.CreateUser(CreateUserRequest(name="John Doe", email="john.doe@example.com"))
        ```
        
        **Sérialisation des requêtes** : Le cadre gRPC sérialise le message de la demande, généralement dans un format binaire, conformément au schéma des tampons de protocole spécifié.
        
        **Communication sur le réseau** : La requête sérialisée est envoyée sur le réseau au serveur en utilisant HTTP/2 comme protocole de transport sous-jacent. gRPC exploite les avantages de HTTP/2, tels que le multiplexage et la compression des en-têtes, pour améliorer les performances et l'efficacité.
        
        **Traitement par le serveur** : Le serveur reçoit la demande, la désérialise et invoque la méthode correspondante sur le stub du serveur, en passant le message de demande désérialisé comme argument.
        
        **Réponse du serveur** : Le serveur traite la demande et génère une réponse, qui est ensuite sérialisée dans un format binaire.
        
        Désérialisation de la réponse : La réponse sérialisée est renvoyée au client, où elle est désérialisée dans le message de réponse correspondant.
        
        **Traitement par le client** : Le client reçoit la réponse et peut maintenant accéder au résultat ou aux données renvoyées par le serveur. Par exemple, le client peut accéder aux informations sur l'utilisateur renvoyées par la méthode "CreateUser".
        
    
    ## MQTT (Transport de télémétrie MQ)
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1683892153828/5fc1d3ba-610f-4672-945b-04126fb928c2.png?auto=compress,format&format=webp align="left")
    

MQTT est un protocole de messagerie léger conçu pour une communication efficace entre les appareils et les applications dans des conditions de réseau à faible bande passante, à forte latence ou peu fiables. Il suit un modèle de messagerie de type publication-abonnement, où les clients peuvent publier des messages vers des sujets ou s'abonner à des sujets pour recevoir des messages. MQTT est largement utilisé dans les scénarios de l'internet des objets (IoT), où des appareils aux ressources limitées doivent échanger des données de manière fiable et évolutive.

Considérons un scénario dans lequel nous avons un système de surveillance de la température qui recueille les relevés de température de divers capteurs et les envoie à un serveur central à l'aide de MQTT.

**Établissement de la connexion** : Le client MQTT, tel qu'un capteur ou un appareil, établit une connexion avec un courtier MQTT. Le courtier sert de plaque tournante pour l'acheminement et la distribution des messages.

**Abonnement à un sujet** : Le client s'abonne à un ou plusieurs sujets qui l'intéressent. Les sujets sont hiérarchiques et représentent différentes catégories ou canaux de distribution de messages. Par exemple, le client peut s'abonner au thème "capteurs/température".

**Publication de messages** : le client recueille périodiquement des relevés de température et les publie auprès du courtier MQTT, en spécifiant le sujet correspondant. La charge utile du message contient généralement la valeur de la température et des métadonnées supplémentaires.

**Distribution du message** : Le courtier MQTT reçoit le message publié et le distribue à tous les clients qui se sont abonnés au sujet correspondant. Dans ce cas, tous les clients abonnés à "sensors/temperature" recevront les relevés de température en temps réel.

**Réception du message :** Les clients abonnés à la rubrique "sensors/temperature" reçoivent les messages publiés et peuvent les traiter en conséquence. Par exemple, un client peut afficher les relevés de température sur un tableau de bord ou déclencher une action spécifique en fonction d'un seuil prédéfini.

# Conclusion :

Dans cet article, nous avons exploré six architectures d'API populaires : REST, GraphQL, WebSockets, webhooks, SOAP et gRPC, ainsi que le protocole MQTT. Chaque architecture a ses propres atouts et convient à différents cas d'utilisation. **REST** offre simplicité et compatibilité, **GraphQL** offre une flexibilité dans la collecte des données, **WebSockets** permet une communication bidirectionnelle en temps réel, **webhooks** permet une intégration pilotée par les événements, **SOAP** offre des fonctionnalités avancées et l'interopérabilité, **gRPC** excelle dans la performance et la communication indépendante du langage, et **MQTT** est idéal pour les scénarios IoT. Comprendre les caractéristiques et les applications de ces architectures permet aux développeurs de prendre des décisions éclairées lors de la conception et de la mise en œuvre des API pour leurs besoins spécifiques. En s'appuyant sur la bonne architecture, les entreprises peuvent construire des systèmes efficaces, évolutifs et robustes qui répondent aux exigences des applications modernes.