## Les meilleures bibliothèques React que vous devez connaître en 2021

Tout d'abord je profite pour vous souhaiter une bone et heureuse annee 2021. 
La dernière fois, nous avons regardé un peu de certaines fonctionnalités intégrées de React. Comme promis, il est maintenant temps d’examiner certains outils optionnels. Tout comme avec Vue et Angular, les composants jouent un grand rôle ici et, comme d'habitude, vous pouvez créer les vôtres ou utiliser certains de ceux fabriqués par la communauté en croissance rapide. Jetons un coup d'œil aux bibliothèques React que vous devriez vérifier en ce debut de 2021.

## Frameworks basés sur React.

Si vous envisagez de travailler avec React, vous devrez probablement choisir entre deux frameworks de démarrage, Gatsby.js et Next.js. React en lui-même ne fonctionne que du côté client et ne fournit pas de rendu côté serveur, tandis que ces deux éléments se construisent sur React et fournissent SSR / SSG. Les deux suivent également l'architecture JAMStack et vous fournissent un passe-partout qui permet d'accélérer et de simplifier le processus de développement. C'est assez sur les similitudes et regardons en quoi consiste le choix:

 
- 
**[gatsby.js](https://www.gatsbyjs.com/)**  : génère du HTML via un générateur côté serveur pendant la phase de construction, cela signifie que vous n'avez pas besoin d'un serveur Node.js pour gérer le rendu et que les fichiers HTML sont prêts juste après la construction. La récupération des données est gérée via GraphQL qui a ses avantages (vous ne récupérez que ce dont vous avez besoin, ce qui économise des ressources et du temps) mais vous lie également à GraphQL que tout le monde n'aime pas ou ne veut pas utiliser. Les principales utilisations de Gatsby.js incluent Figma.com, le site officiel de React et l'état (state) de Javascript.

 
- 
**[next.js](https://nextjs.org/)** : rend les pages via le rendu côté serveur, cela nécessite un serveur Node.js pour exécuter les applications et gérer le rendu HTML dynamique. Si vous n'aimez pas cela, Next.js prend également en charge SSG depuis la version 9.3. Ce que vous utilisez pour la récupération de données dépend de vous, vous pouvez même utiliser GraphQL. Les principales utilisations de Next.js incluent TikTok, Hulu et Twitch mobile.

![1.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1609700962775/OU-pihdNf.png)

## Gestion d'état:

La gestion de l'état est la partie la plus cruciale de toute application React moderne. La plupart du temps, il s'agit du plus grand défi auquel tous les développeurs sont confrontés lorsqu'ils travaillent sur leur projet frontend, en particulier lorsqu'il s'agit d'applications commerciales de grande taille et complexes. La gestion de l'état est une tâche si complexe qu'une gestion appropriée nécessite l'utilisation de bibliothèques externes, car à un moment donné, React lui-même ne sera plus en mesure de fournir une solution satisfaisante.

 
- 
**[Redux](https://redux.js.org/)**  :un conteneur d'état prévisible et autonome pour les applications JavaScript qui vous aide à écrire des applications qui se comportent de manière cohérente et s'exécutent dans différents environnements. Être une bibliothèque autonome signifie que vous pouvez utiliser Redux même si vous n'avez pas encore de configuration d'interface utilisateur. Redux peut être utilisé avec n'importe quel framework d'interface utilisateur, c'est-à-dire React, où vous pouvez décrire votre interface utilisateur en fonction de votre état et permettre à Redux de garder une trace de l'état de vos composants et de les mettre à jour en conséquence en réponse aux actions de l'interface utilisateur. Redux est certainement le choix le plus populaire en matière de gestion des états avec React avec près de 5 millions de téléchargements hebdomadaires sur NPM.

 
- 
**[MobX](https://mobx.js.org/README.html)** : une solution de gestion d'état simple et évolutive. Il est plus facile à apprendre et à utiliser que Redux et se concentre sur le développement d'applications plus simples avec moins de code standard. L'objectif principal est de réduire le nombre de bogues en cartographiant les relations entre l'état et les dérivés tout en maintenant l'intégrité référentielle. Un autre avantage est qu'il peut être utilisé côté client ou côté serveur et, en tant que bibliothèque JavaScript, vous permet de conserver les utilitaires existants de JS.

![state.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1609700975261/lwfvM1if5.png)

## Formulaires.

Les formulaires sont présents dans la plupart des applications Web et mobiles. Contrairement à Angular et Vue, qui vous permettent tous deux de valider les formulaires prêts à l'emploi, React vous oblige à les gérer tous vous-même. Heureusement, certaines bibliothèques sont pret pour vous aider.


- 
**[Formik](https://formik.org/)** : est la bibliothèque de formulaires la plus populaire pour React (et React Native). Formik regorge de dizaines de micro-fonctionnalités telles que différents types de validation, la gestion des erreurs d'API, l'enregistrement automatique des données de formulaires et bien d'autres. C'est le résultat des années d'expérience de la communauté React en termes d'interface utilisateur, de sécurité, d'accessibilité, etc. Avec Formik, vous pouvez vous concentrer sur le développement de votre produit au lieu de vous battre avec tous les aspects des formulaires. C'est une solution bien testée et hautement optimisée, qui vous laissera moins de risques d'erreurs inattendues et de cas extrêmes dans vos formulaires.


- 
 **[React Hook Forms](https://react-hook-form.com/)** : une bibliothèque de formulaires légère pour React, vous permettant d'obtenir des résultats étonnants avec une quantité minimale de code, ce qui la rend très axée sur les performances. React Hook Forms est optimisé pour supprimer tous les rendus inutiles de vos composants en offrant au développeur un moyen d'isoler les rendus de composants, améliorant ainsi les performances de votre application mobile ou Web. C'est un excellent moyen de doter vos applications de formulaires hautement performants, flexibles, faciles à utiliser et à gérer.


![forms.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1609701252229/g8BZvarpS.png)

## Tests.
Le développement piloté par les tests (TDD) est désormais l'une des principales approches du développement d'applications. Il devient de plus en plus populaire car il réduit les risques de bogues majeurs à l’avenir. Un inconvénient évident du développement piloté par les tests est qu'il faut généralement plus de temps pour mettre un produit sur le marché qu'en utilisant une approche de développement pilotée par le comportement. Heureusement, il existe des bibliothèques React utiles qui peuvent rendre l'écriture de tests beaucoup plus facile.


- 
 **[Enzyme](https://enzymejs.github.io/enzyme/)** : un utilitaire de test JS qui facilite le test de vos composants React. Vous pouvez manipuler, parcourir et simuler à certains égards le runtime en fonction de la sortie. Enzyme a été créé en interne chez AirBnB et publié en tant que projet open source en 2015. L'outil vise à être aussi simple que possible en fournissant une API intuitive inspirée de l'API de jQuery pour la manipulation et la traversée DOM.


- 
 **[React Testing Library](https://testing-library.com/docs/react-testing-library/intro/)** : un outil qui vous permet de tester les composants React sans vous fier aux détails de leur implémentation. Cette approche permet de se concentrer sur l'accessibilité car elle vous met essentiellement dans la peau de l'utilisateur final de l'application React. Le principe directeur ici est que plus vos tests ressemblent à la façon dont votre logiciel est censé être utilisé, plus leur exécution peut vous donner confiance. Elle est beaucoup plus légère et plus facile à utiliser qu’enzyme (qui a en revanche beaucoup plus de fonctions) et est l’application de test recommandée selon la documentation de React.


![test.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1609701405864/H46cbz_S1.png)

## UI.

Si cela fonctionne pour les composants React prêts à l'emploi, il y a un tas de bibliothèques utiles créées par la communauté à découvrir. Leur utilisation peut vous aider de différentes manières en fournissant des solutions pratiques et réutilisables, qui ont vraiment un impact sur le temps et les efforts de développement.

 
- 
**[React Bootstrap](https://react-bootstrap.github.io/)** : un kit d'interface utilisateur qui remplace le JavaScript de Bootstrap par du code React. Sans doute le meilleur moyen de commencer rapidement à créer une interface utilisateur car elle contient des milliers de thèmes et de ressources prêts à l'emploi. Pas étonnant qu'il soit parmi les bibliothèques de composants les plus populaires avec plus de 700 000 téléchargements hebdomadaires sur NPM.

 
- 
**[Material UI](https://material-ui.com/)**: un ensemble de composants créés par Google sur la base de leurs célèbres protocoles de conception de matériaux. Les composants sont de nature autonome et n'injectent que les styles dont ils ont besoin pour afficher. Il fournit également de nombreux widgets d'interface utilisateur accessibles et configurables et des modèles de site prêts à l'emploi. Cela augmente considérablement les performances, d'autant plus que la bibliothèque est régulièrement mise à jour et bénéficie d'un très bon support de la communauté avec plus de 60 000 étoiles sur GitHub et est probablement la bibliothèque de composants la plus populaire avec plus de 1,6 millions de téléchargements hebdomadaires sur NPM.

 
- 
**[Rebass](https://rebassjs.org/)** : une minuscule bibliothèque de composants qui a du punch. Rebass ne contient que 8 composants et ne pèse que 4 Ko, mais peut être utilisé pour créer un ensemble robuste d'éléments d'interface utilisateur à thème. Il est basé sur la bibliothèque Styled System et vise à fournir un démarrage rapide pour votre processus de développement. C'est vraiment pratique si vous ne voulez pas trop vous fier aux bibliothèques de composants de la communauté ou si vous avez l'intention de créer votre propre interface utilisateur personnalisée.

 
- 
**[Semantic UI React](https://react.semantic-ui.com/)** : l'intégration officielle de React pour l'interface utilisateur sémantique. Cela offre toutes les fonctions supplémentaires du re-scripté basé sur jQuery en code React. Livré avec des tonnes de composants prédéfinis spécialement conçus pour faciliter le travail et la production de code sémantique.

 
- 
**[Ant Design](https://ant.design/)** : un système de conception pour les produits de niveau entreprise. Basé sur le projet Ant Design, il vous fournit plus de 60 composants de haute qualité conçus à partir d'un langage de conception développé par les créateurs. Les composants sont personnalisables et incluent la prise en charge de dizaines de langues. L'accent est mis sur la création d'interfaces utilisateur riches et interactives pour les applications de bureau internes (pas de souci, il existe également Ant Design Mobile pour les applications mobiles).


![ui.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1609701668835/Kc_sKTizs.png)


**De toute évidence, ce ne sont que quelques bibliothèques populaires, il y en a une myriade d'autres et tout le monde trouvera facilement des bibliothèques utiles. La plupart d'entre eux ne sont pas compliqués et prennent un peu de temps à etre maîtriser, ce qui est du temps bien investi étant donné qu'ils accélèrent et simplifient généralement le processus de développement. Créer tout vous-même a ses avantages, mais dans l'ensemble, la communauté React en croissance rapide et déjà importante est probablement le plus grand avantage de son utilisation.**