---
title: "Scraping Web avec Bright Data, Node.js, et Puppeteer"
datePublished: Tue Sep 12 2023 19:22:05 GMT+0000 (Coordinated Universal Time)
cuid: clmgp8yxl000a08mo4ojvdoo7
slug: scraping-web-avec-bright-data-nodejs-et-puppeteer
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1694546399695/695cdf05-5d0d-42f6-9594-7dbb96e61129.png
tags: developer, beginners, webscraping

---

Le scraping web est devenu un outil essentiel pour les entreprises et les chercheurs qui ont besoin d'extraire des données de sites web à grande échelle. Parmi les différents outils disponibles, [Bright Data](https://brightdata.com/) s'impose comme une solution puissante et polyvalente.

Dans cet article complet, nous allons explorer comment exploiter les capacités de Bright Data pour racler efficacement les sites Web à l'aide de Node.js. Que vous soyez un développeur chevronné ou un novice, cet article vous apportera les connaissances et les techniques nécessaires pour devenir un scrapeur de sites Web compétent.

## Introduction au Web Scraping

Le web scraping est le processus d'extraction automatique de données structurées à partir de sites web. Il s'agit d'utiliser des outils logiciels pour accéder à des pages web et en extraire des informations spécifiques, transformant ainsi des données non structurées en un format structuré qui peut être analysé et utilisé à diverses fins. Le web scraping est incroyablement populaire en raison de sa capacité à collecter rapidement et efficacement de grandes quantités de données.

## Les domaines d'applications du Web Scraping

Le web scraping a de nombreuses applications dans différents secteurs et industries :

* Intelligence économique : Les entreprises peuvent extraire des données des sites Web de leurs concurrents, des avis de clients et des plateformes de médias sociaux afin de mieux comprendre les tendances du marché, les préférences des consommateurs et les stratégies des concurrents.
    
* Génération de leads : Le web scraping permet aux entreprises d'extraire des informations de contact à partir de sites web et d'annuaires à des fins de vente et de marketing, telles que la génération de leads et la construction de listes de prospects.
    
* Surveillance des prix : Les plateformes de commerce électronique peuvent récupérer les sites web de leurs concurrents pour suivre les prix des produits, surveiller les remises et ajuster leurs stratégies de prix en conséquence.
    
* Agrégation de contenu : Les agrégateurs d'actualités et les plateformes de contenu peuvent récupérer des informations provenant de diverses sources afin d'élaborer et de présenter un contenu pertinent à leurs utilisateurs.
    
* Recherche et analyse : Les chercheurs et les universitaires peuvent collecter des données à partir de sites web afin d'analyser les tendances, de procéder à une analyse des sentiments et d'obtenir des informations précieuses pour leurs études.
    
* Immobilier et planification des voyages (ma préférée): Le web scraping peut aider à collecter des données sur les annonces immobilières, les prix de location, les disponibilités hôtelières et les tarifs des vols, ce qui permet aux utilisateurs de prendre des décisions en connaissance de cause.
    

## Considérations juridiques

Bien que le web scraping offre de nombreux avantages, il est essentiel de comprendre les considérations juridiques et les limites éthiques qui y sont associées. La légalité du web scraping varie d'une juridiction à l'autre et dépend de facteurs tels que les conditions de service du site web, les données récupérées et l'utilisation prévue des informations extraites.

* Conditions d'utilisation du site web : Les sites web peuvent avoir des conditions d'utilisation qui interdisent explicitement le web scraping ou imposent des restrictions sur l'utilisation de leurs données. Il est essentiel d'examiner ces conditions et de s'y conformer pour éviter des répercussions juridiques.
    
* Droits d'auteur et propriété intellectuelle : Le web scraping doit respecter les lois sur les droits d'auteur et les droits de propriété intellectuelle. Il est conseillé de ne récupérer que des données accessibles au public et d'éviter de récupérer des informations privées ou protégées par le droit d'auteur.
    
* Données personnelles et vie privée : Le web scraping doit respecter les réglementations en matière de protection de la vie privée, en particulier lorsqu'il s'agit d'informations personnelles identifiables (PII). Veillez à vous conformer aux lois sur la protection des données et à respecter la vie privée des individus.
    
* x@Robots.txt et Crawl-Delay : Le fichier robots.txt d'un site web fournit des directives aux robots d'indexation et peut restreindre ou limiter les activités de scraping. Respectez les directives mentionnées dans le fichier robots.txt afin d'éviter tout problème juridique.
    

## Les défis du Web Scraping

Le web scraping présente plusieurs défis que les développeurs doivent relever :

* Structure et variabilité des sites web : Les sites web ont souvent des structures différentes, ce qui nécessite d'adapter les techniques de scraping pour gérer les différentes mises en page et les formats de données.
    
* Contenu dynamique : De nombreux sites web modernes utilisent JavaScript et AJAX pour charger des données de manière dynamique. Le scraping de ces sites nécessite des outils capables de rendre JavaScript et d'interagir avec le DOM (Document Object Model) de manière efficace.
    
* Blocage d'IP et mesures anti-scraping : Les sites web utilisent diverses mesures anti-scraping pour protéger leurs données, telles que le blocage d'IP, les captchas et la limitation de débit. Pour relever ces défis, il faut des techniques et des outils avancés comme Bright Data.
    
* Évolutivité et performances : L'extraction efficace de grands volumes de données nécessite une utilisation optimale des ressources, un traitement parallèle et une gestion efficace des requêtes réseau.
    

# Présentation de Bright Data

[Bright Data](https://brightdata.com/) est l'un des principaux fournisseurs de solutions de collecte de données web et de proxy, offrant un ensemble complet d'outils et de services pour permettre aux entreprises et aux chercheurs de recueillir des informations précieuses à partir du web à grande échelle.

Bright Data se distingue par ses fonctionnalités robustes et ses capacités avancées qui améliorent la collecte des données, garantissent une extraction fiable des données et encouragent les pratiques éthiques.

L'un des principaux avantages de Bright Data est son intégration transparente avec Puppeteer, une puissante bibliothèque Node.js pour l'automatisation des navigateurs. Cette intégration permet aux utilisateurs de naviguer sur les sites web, d'interagir avec les pages web et d'extraire du contenu dynamique dont le rendu dépend fortement de JavaScript. En combinant Puppeteer avec le réseau de proxy de Bright Data, les développeurs peuvent gérer des scénarios de scraping complexes, y compris le contenu chargé en AJAX et les applications à page unique.

Bright Data propose une API complète et des kits de développement logiciel (SDK) pour différents langages de programmation, notamment Node.js. Ces SDK simplifient l'intégration de Bright Data dans les flux de travail de scraping existants, en permettant aux utilisateurs de configurer les paramètres du proxy, de gérer les requêtes et de traiter efficacement les scénarios d'erreur.

L'utilisation de Bright Data pour le scraping web offre plusieurs avantages, notamment la protection de l'anonymat et de la vie privée, l'évolutivité et la fiabilité. Les capacités étendues du réseau de proxy et de rotation des adresses IP permettent aux utilisateurs d'étendre leurs activités de scraping sans limitations de performances ni perturbations. Le ciblage par géolocalisation permet de recueillir des données spécifiques à une région ou de simuler le comportement de navigation dans différents pays ou villes. Les capacités de traitement du contenu dynamique de Bright Data garantissent l'extraction de données à partir de pages rendues en JavaScript, d'éléments chargés en AJAX et d'applications à page unique.

La conformité aux réglementations légales et aux pratiques éthiques de scraping est une priorité pour Bright Data. Les utilisateurs peuvent garantir l'adhésion aux conditions de service des sites web, respecter les directives <mark>robots.txt</mark> et se conformer aux lois sur la protection des données et de la vie privée lorsqu'ils utilisent Bright Data pour le scraping web.

Bright Data trouve des applications dans divers secteurs et cas d'utilisation, notamment les études de marché, l'analyse de la concurrence, la génération de prospects, la surveillance des prix, l'agrégation de contenu et la recherche universitaire.

Les capacités de Bright Data permettent aux utilisateurs d'extraire des données précieuses du web de manière efficace et éthique, facilitant ainsi la prise de décision éclairée et l'obtention d'un avantage concurrentiel dans le monde d'aujourd'hui axé sur les données.

## Obtenir votre clé API

Pour obtenir votre API, suivez les étapes ci-dessous :

1. Visitez le site Web de Bright Data et accédez à la page de tarification.
    
2. Sur cette page, sélectionnez le plan qui correspond le mieux à vos besoins et cliquez sur le bouton "Get Started" ou "Contact Sales".
    
3. Remplissez les informations requises dans le formulaire d'inscription, y compris votre nom, votre adresse électronique, le nom de votre entreprise et tout autre détail supplémentaire demandé.
    
4. Une fois le formulaire d'inscription envoyé, l'équipe de Bright Data examinera votre demande. Elle pourra vous contacter pour obtenir de plus amples informations ou pour discuter de vos besoins spécifiques.
    
5. Une fois votre demande approuvée, vous recevrez un courrier électronique de Bright Data contenant des instructions sur la marche à suivre. Cet e-mail contiendra votre clé API ou vous indiquera comment en générer une.
    
6. Suivez les instructions fournies dans le courrier électronique pour obtenir votre clé d'API Bright Data. Cette clé est un identifiant unique qui vous permet de vous authentifier et d'accéder aux services de Bright Data via l'API.
    

Notez que le processus peut varier en fonction de vos besoins spécifiques et que vous devrez peut-être contacter l'équipe de Bright Data pour discuter de la tarification, des limites d'utilisation et des fonctionnalités ou services supplémentaires dont vous avez besoin.

## Configuration de Node.js

La configuration de Node.js est la première étape vers l'utilisation de la puissance de Bright Data pour le web scraping. Node.js est un environnement d'exécution JavaScript populaire qui permet aux développeurs d'exécuter du code JavaScript en dehors d'un navigateur Web. Il offre un vaste écosystème de bibliothèques et d'outils, ce qui en fait un choix idéal pour créer des applications de web scraping évolutives et efficaces.

En supposant que Node.js soit déjà installé sur votre machine, créez un nouveau répertoire de projet et exécutez les commandes suivantes :

```js
npm init -y 
```

Cela configurera votre fichier **package.json**, dans lequel se trouveront vos dépendances.

Ensuite, nous allons exécuter la commande suivante pour installer le SDK Bright Data pour Node.js :

```js
npm install @brightdata/sdk
```

Cette commande télécharge et installe le <mark>SDK Bright Data à partir du registre npm.</mark>

## Configuration de Bright Data et de Puppeteer

Pour commencer à utiliser Bright Data dans votre projet Node.js, vous devez initialiser le SDK Bright Data et le configurer avec les détails de votre compte Bright Data. Procédez comme suit :

Dans votre projet racine, ouvrez le fichier de point d'entrée (par exemple, "index.js") dans un éditeur de code et importez le SDK de Bright Data en ajoutant la ligne suivante au début de votre fichier :

```js
const BrightData = require('@brightdata/sdk');
```

Initialisez le SDK Bright Data avec les détails de votre compte. Ajoutez l'extrait de code suivant :

```js
const brightDataClient = new BrightData.Client('VOTRE_CLÉ_API');
```

Remplacez " VOTRE\_CLÉ\_API " par votre clé d'API Bright Data, que vous pouvez obtenir sur le tableau de bord de votre compte Bright Data.

Une fois le SDK Bright Data initialisé, vous pouvez maintenant tirer parti de ses capacités pour le scraping Web. Utilisez les fonctions et méthodes du SDK pour configurer les proxys, gérer les sessions et effectuer des requêtes Web via le réseau de proxys de Bright Data.

Par exemple, pour effectuer une requête Web à l'aide de Bright Data, vous pouvez utiliser l'extrait de code suivant :

```js
const response = await brightDataClient.request('https://www.example.com');
console.log(response.body);
```

Ce code envoie une requête GET à l'URL spécifiée en utilisant le réseau proxy de Bright Data. L'objet réponse contient le corps de la réponse, que vous pouvez traiter et extraire les données souhaitées.

Pour gérer le contenu dynamique et interagir avec les pages Web, vous pouvez utiliser **<mark>Puppeteer</mark>** en combinaison avec Bright Data. Voici un exemple d'utilisation de Puppeteer avec Bright Data pour le scraping web :

```js
const puppeteer = require('puppeteer');
const BrightData = require('@brightdata/sdk');

(async () => {
  // Initialiser le SDK Bright Data avec votre clé API
  const brightDataClient = new BrightData.Client('VOTRE_CLÉ_API');

  const browser = await puppeteer.launch({
    args: [`--proxy-server=${brightDataClient.getProxyUrl()}`]
  });

  const page = await browser.newPage();

  // Configurer la session Bright Data à l'aide du SDK Bright Data
  await page.authenticate({
    username: brightDataClient.getProxyUsername(),
    password: brightDataClient.getProxyPassword()
  });

  await page.goto('https://www.example.com/products');

  // Attendre le chargement de la liste des produits
  await page.waitForSelector('.product');

  // Extraire les noms et les prix des produits
  const productList = await page.$$('.product');
  const products = [];

  for (const product of productList) {
    const name = await product.$eval('.product-name', (element) => element.textContent);
    const price = await product.$eval('.product-price', (element) => element.textContent);

    products.push({ name, price });
  }

  console.log(products);

  await browser.close();
})();
```

Tout d'abord, nous initialisons le SDK de Bright Data avec votre clé d'API. Nous lançons une instance de navigateur Puppeteer et la configurons pour qu'elle utilise le proxy de Bright Data en lui transmettant l'URL du serveur proxy obtenue auprès du SDK de Bright Data. Nous authentifions la page à l'aide des informations d'identification du proxy de Bright Data récupérées auprès du SDK. Ensuite, nous naviguons jusqu'à l'URL cible où se trouve la liste des produits.

Nous utilisons **<mark>page.waitForSelector()</mark>** pour attendre que la liste des produits se charge sur la page. Une fois les produits chargés, nous utilisons **<mark>page.$$()</mark>** pour récupérer tous les éléments correspondant au sélecteur **<mark>.product</mark>**. Ensuite, nous parcourons en boucle chaque élément de produit et utilisons **<mark>element.$eval()</mark>** pour extraire le nom et le prix en sélectionnant les éléments respectifs au sein de l'élément de produit.

Nous stockons les données extraites dans le tableau des produits et les enregistrons enfin dans la console.

N'oubliez pas de remplacer "VOTRE\_CLÉ\_API" par votre clé d'API Bright Data. En outre, ajustez les sélecteurs et la logique de récupération en fonction de la structure et du balisage du site Web cible que vous souhaitez récupérer.

Et voilà votre introduction à Bright Data. J'espère que cet article vous a été utile. N'hésitez pas à me faire part de vos questions ou commentaires ci-dessous.

# Conclusion

Le scraping web, lorsqu'il est effectué de manière responsable et dans les limites de la loi, ouvre un monde de possibilités pour les entreprises, les chercheurs et les particuliers.

En combinant la puissance de Node.js et de Bright Data, vous pouvez libérer tout le potentiel du web scraping, ce qui vous permettra d'obtenir des informations précieuses et de prendre des décisions éclairées sur la base de la richesse des données disponibles sur le web.

Découvrez [Bright Data](https://brightdata.com/) dès aujourd'hui !