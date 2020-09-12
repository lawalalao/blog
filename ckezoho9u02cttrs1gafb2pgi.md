## Pourquoi  opté pour React Native plutôt que Flutter

Le développement d'applications mobiles ces derniers temps a pris de nombreux visages. Un certain nombre de méthodes peuvent être utilisées pour développer une application. Bien que les applications puissent être développées de manière native pour prendre en charge la plate-forme d'utilisation, il est devenu une pratique courante pour les développeurs d'utiliser des cadres pour développer des applications multiplateformes permettant de maintenir une base de code unique pour Android et iOS.

Avant de parler des frameworks multiplateformes, je vais parler du développement natif. Android et iOS sont les systèmes d'exploitation mobiles dominants à l'heure actuelle et ont des méthodes de mise en œuvre différentes. Alors que le développement Android peut être réalisé en utilisant les langages Java ou Kotlin, le développement iOS peut être réalisé en utilisant Swift ou Objective-C. Le développement doit être effectué à l'aide d'EDI spécifiques à la plate-forme (à savoir Android Studio pour Android et Xcode pour iOS).

Le développement natif offre l'utilisation d'un certain nombre de fonctionnalités au niveau du système d'exploitation qui peuvent être utilisées par les développeurs pour effectuer facilement des tâches essentielles. Certaines de ces fonctionnalités peuvent s'avérer inaccessibles lors du développement d'applications avec l'utilisation de frameworks multiplateformes. Mais le souci de maintenir deux bases de code distinctes a conduit les développeurs à privilégier les frameworks au développement natif lorsque l'exigence spécifie la prise en charge des deux plates-formes principales.

## multiplateformes

Le principal avantage de l'utilisation de frameworks multiplateformes est la commodité de développer des applications pour Android et iOS tout en conservant une base de code unique. Tous les écrans, éléments, fonctions, itinéraires de navigation, animations, etc. pertinents peuvent être définis en utilisant les langages spécifiés par les frameworks. Les deux principaux acteurs des frameworks multiplateformes sont React Native (développé par Facebook) et Flutter (développé par Google). Bien que ces deux cadres offrent le même résultat final, les spécificités de la mise en œuvre classent l'utilisabilité de chacun, en fonction des exigences et des cas d'utilisation.

## React Native vs Flutter

React Native et Flutter se sont avérés être les frameworks de développement mobile les plus populaires car ils permettent tous deux de compiler le code de manière native. Bien que le codage soit effectué à l'aide d'un langage spécifié par le framework, ils ont la possibilité de convertir les codes en une forme native en fonction de la version de chaque plate-forme.

En considérant l'utilisation des deux plates-formes, on peut voir que des applications populaires telles que Facebook Ads Manager, Instagram, Uber Eats, AirBnB et Discord ont été développées à l'aide de React Native. Google Ads, Google Assistant, Alibaba, Stadia et eBay sont quelques-unes des applications Flutter populaires. Maintenant, vous avez peut-être une idée de la qualité des applications développées par les deux frameworks. Pour discuter des facteurs qui m'ont aidé à prendre la décision de sélectionner un framework pour développer une application mobile, je vais faire une petite comparaison des deux frameworks concernés.

## Préférence de langage

Le langage de base utilisé pour développer des applications React Native est JavaScript. Flutter a son propre langage développé par Google, à savoir Dart. Dart est un langage qui, en comparaison, se révèle ressembler à Java et JavaScript. C'est un facteur majeur lors du choix du cadre de développement d'une application. Parmi les deux options de langue disponibles, Js est le langage le plus populaire car il a été adopté par de nombreux développeurs qui travaillent sur des solutions Web. `Dart`, d'autre part, a une courbe d'apprentissage impliquée car la langue est relativement nouvelle. Bien qu'il offre la possibilité de créer une application mobile entièrement fonctionnelle, Dart et Flutter doivent encore être largement adoptés par la communauté des développeurs. Selon une  [enquête](https://www.jetbrains.com/lp/devecosystem-2020/)  menée par JetBrains au cours du premier trimestre 2020, JavaScript s'est avéré être le plus populaire des deux langages avec un pourcentage d'utilisation de 70%. Cependant, Dart, avec sa durée de vie limitée et son utilisation dans le développement d'applications mobiles de moins de 2 ans, n'a réussi à rassembler qu'une base d'utilisateurs de 9% des développeurs qui ont participé à l'enquête. Cependant, le taux d'adaptation pour Dart et Flutter a connu une augmentation rapide depuis sa création il y a 2 ans et continue sa croissance en popularité.

## Préférences du développeur

Compte tenu de la saturation du marché des deux frameworks, on peut voir que React Native a un avantage dans ce domaine car il a eu un temps de maturité plus long que Flutter. Les développeurs ont eu la chance de s'adapter à React Native et sont plus largement utilisés par les développeurs tant en entreprise qu'en freelance. Cependant, selon un rapport de Statista, Flutter a montré une forte demande d'intérêt en 2020, portant sa popularité à 39% par rapport aux 30% observés en 2019. React Native a cependant maintenu sa popularité de 42% au fil du temps. des 2 dernières années.


![0.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1599835182823/M0lhsT1KG.png)



> Image: Cross-platform mobile frameworks used by software developers worldwide (Source:  [statista.com)](https://fr.statista.com/) 

Bien que RN ait la demande la plus élevée parmi la communauté des développeurs à ce jour, on peut remarquer que Flutter a une croissance rapide de l'adaptation, montrant le potentiel de prendre le relais en tant que cadre privilégié dans les années à venir.
Performance

Étant donné que les deux frameworks compilent le code de manière native, les performances des applications développées sont à un niveau considérablement élevé par rapport aux autres frameworks multiplateformes disponibles. Cependant, une différence notable peut être observée dans les applications développées à l'aide de Flutter, ce qui lui donne un avantage sur React Native. La raison principale en est que React Native utilise une combinaison de variations de JavaScript et de code natif pour appeler divers composants du système d'exploitation afin de gérer différentes interactions avec l'application. Flutter, en revanche, ne nécessite la combinaison d'aucun composant du système d'exploitation pour gérer les interactions. Sa construction légère permet aux utilisateurs de profiter d'animations transparentes sans compromis sur les performances.

## Communauté

Celui-ci est assez évident. React Native est là depuis bien plus longtemps que Flutter. Par conséquent, une plus grande communauté de développeurs s'est rassemblée autour d'elle. Avoir cette grande communauté facilite la vie d'un développeur lorsqu'il est confronté à des problèmes lors du codage, car la communauté aura des solutions à la plupart des problèmes qui se présenteront. Mais comme l'ont montré les statistiques intéressantes, la communauté Flutter se développe également, ouvrant la voie à la construction d'une communauté plus mature similaire à React Native.

## Pourquoi React Native?

Je travaille actuellement sur un projet qui nécessite une application d'authentification mobile basée sur push pour [ WSO2 Identity Server](https://wso2.com/identity-and-access-management/) . L'application doit être disponible pour Android et iOS, ce qui nécessite une approche de développement multiplateforme.

Compte tenu de tous les facteurs ci-dessus, il a été décidé que le développement se poursuivrait avec React Native. Pour justifier cette décision, le développement natif a été exclu car le maintien de deux bases de code serait une surcharge inutile. Étant donné que React Native est le cadre multiplateforme le plus saturé du secteur, le fait d'avoir une plus grande communauté de support en fait le choix logique pour le développement initial. De plus, le langage de développement étant JavaScript, permet à d'autres développeurs qui sont déjà familiarisés avec Js et React de maintenir le code sans avoir une exigence supplémentaire pour apprendre Dart.

Mais si Flutter s'avère atteindre le niveau que React Native a déjà atteint, cela pourrait être considéré comme une voie d'expansion pour le produit en discussion à l'avenir. Pour l'instant, Flutter est un excellent framework à utiliser pour développer des applications. Mais nous avons opté pour React Native car c'est le framework le plus familier de la communauté des développeurs.

