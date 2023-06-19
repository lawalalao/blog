---
title: "L'art du code review"
seoTitle: "L'art du code review"
seoDescription: ""Découvrez mes conseils essentiels pour devenir un excellent relecteur de code et améliorer la qualité de vos projets de développement ! 💻✨ #développement"
datePublished: Mon Jun 19 2023 14:14:40 GMT+0000 (Coordinated Universal Time)
cuid: clj2xu8ht00080akyaihbeu3u
slug: lart-du-code-review
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1687183985315/4c959bd7-5a66-4435-b52d-e244622ee27f.png
tags: code-review, developer, best-practices

---

Bonjour ! Je m'appelle Lawal ALAO, et en tant qu'ingénieur logiciel, j'ai consacré les 5 dernières années au développement d'une solution logistique aka chapchap.tg générant un nombre important de livraisons. Parallèlement, j'ai eu le privilège d'accompagner des étudiants d'EPITECH dans leur parcours et également collaborer à plus de 8 projets en tant que Lead technique.. Au cours de ce parcours, j'ai eu l'occasion de travailler avec plus de 20 ingénieurs front-end, back-end, DevOps de différents niveaux d'expérience, en leur transmettant mes connaissances et en apprenant d'eux ce que je ne savais pas. Aujourd'hui, je souhaite partager mon expérience en tant que relecteur de code et vous donner quelques conseils pour devenir un bon lecteur.

Je suis connu pour mes relectures de code notoires au sein des équipes, que certaines personnes ont détestées, voire détestées encore plus. Au final, c'est un plaisir de voir les personnes qui méprisaient mes relectures revenir me remercier pour le temps passé à améliorer nos compétences mutuelles. Indéniablement, mes compétences en relecture ont encore une longue route à parcourir, mais les retours positifs que j'ai reçus au fil du temps m'ont encouragé à rédiger cet article. Je souhaite explorer ce qui a fait que les gens ont aimé ou détesté mes relectures et comment vous pouvez en tirer des enseignements pour devenir un meilleur relecteur au sein de votre équipe.

# Le code review fait partie du développement

Laissez-moi vous dire que les code reviews, c'est pas du chiqué ! Non, non, c'est pas moins important que le codage en lui-même, en fait, ça pourrait même être encore plus crucial. C'est comme une pépite d'or gratuite que vous pouvez obtenir en retour. Imaginez, une petite faille dans votre logique, repérée lors de la révision, peut vous éviter un sacré stress et épargner à votre client de sérieux dégâts financiers.

Les code reviews, c'est un peu comme avoir un super-héros à vos côtés, prêt à repérer les erreurs et à vous faire économiser du temps et de l'argent. Alors, plutôt que de laisser les bugs se faufiler et causer des ravages, optez pour les code reviews et mettez toutes les chances de votre côté.

Maintenant, vous vous demandez peut-être pourquoi je vous parle de tout ça avec tant d'enthousiasme. Eh bien, c'est simple : je suis un véritable passionné de code et de code reviews et je veux vous aider à en tirer le meilleur parti. Alors, restez à l'écoute car je vais vous donner des conseils géniaux pour devenir un as de la révision de code.

![Image of a man behind computers](https://redd.one/blog/the-art-of-code-review/man-computer-TL4PR3KX.svg align="left")

On est tous dans le même bateau, alors assurons-nous que toute l'équipe danse sur la même musique en ce qui concerne la revue de code. Développeurs, chefs de projet, scrum masters, product owners et clients, tout le monde doit être sur la même longueur d'onde. C'est ça qui nous permettra de créer une symphonie logicielle harmonieuse et de livrer un produit de qualité. Alors, tous ensemble, jouons la même partition et assurons le succès de nos revues de code !

<mark>La revue du code n'est pas une activité volontaire, mais un devoir légitime qui doit être pris en compte, respecté et payé.</mark>

  
Plongeons sans peur dans les méandres du code que nous révisons ! Ouvrons les fichiers sources, explorons les changements et comprenons en profondeur leur nature. Avec de multiples demandes de tirage derrière nous, nous serons plus rapides dans cette tâche, ce qui nous permettra d'analyser les fonctionnalités en détail. Ne négligeons rien lors de la revue, car cela pourrait se retourner contre nous et générer encore plus de travail qu'il n'en aurait fallu pour comprendre les changements.

Voici quelques arguments percutants pour expliquer comment la revue de code contribue à un produit :

* Elle garantit une qualité de code irréprochable, et donc une qualité de produit optimale.
    
* Elle réduit la dette technique à l'avenir, ce qui diminue les coûts de maintenance.
    
* Elle favorise le partage des connaissances entre les développeurs, ce qui conduit à une collaboration plus efficace et élimine le risque de dépendance unique.
    

Alors, plongeons ensemble dans le code et donnons le meilleur de nous-mêmes pour créer des produits d'exception !

# Un évaluateur poli, un émetteur sensé

Gardons toujours une politesse exemplaire lors de nos revues de code. Nous sommes tous des êtres humains, accomplissant notre travail et cherchant à le faire de notre mieux. Même si cela peut sembler évident, il est important de se rappeler que nous pouvons en apprendre beaucoup sur nos collègues en faisant preuve de compréhension et de respect.

Par exemple, demander une revue de code à 17 heures le vendredi, juste avant les vacances tant attendues d'un collègue, peut en dire long sur notre sens de l'empathie. Soyons conscients des circonstances et évitons de placer les autres dans des situations inconfortables.

Alors, restons toujours courtois, respectueux et soucieux du bien-être de nos collègues. Cela contribuera à créer une atmosphère de travail positive et favorisera des échanges constructifs lors de nos revues de code.

![Image of a woman and a man pair programming](https://redd.one/blog/the-art-of-code-review/pair-programming-J32AE7GR.svg align="left")

L'une des parties les plus délicates d'une évaluation de code est lorsque nos suggestions sont mal interprétées et perçues comme une attaque personnelle. On peut comprendre que personne n'aime passer une semaine entière à travailler sur une fonctionnalité pour se voir dire qu'il faut tout revoir. Cela peut être douloureux tant pour celui qui émet les suggestions que pour celui qui les évalue. Mais, gardons notre calme et ne réagissons pas de cette manière.

Dans ma pratique, j'ai identifié deux principales raisons à de telles situations, que je vais vous expliquer ci-dessous.

### *Raison n° 1 : Un départ précipité*

Il arrive souvent que des personnes se lancent tête baissée dans le développement sans prendre le temps de réfléchir en amont aux changements nécessaires. **Je suis fermement convaincu qu'une journée de réflexion permet d'économiser une semaine de travail.**

Prendre le temps de planifier et de réfléchir en profondeur aux modifications à apporter peut faire toute la différence. Cela nous permet de clarifier nos objectifs, d'anticiper les obstacles potentiels et de concevoir une approche solide dès le départ.

Alors, résistons à l'envie de foncer tête baissée et accordons-nous une pause pour réfléchir. Cela nous permettra d'économiser du temps et de l'énergie, et nous évitera bien des tracas en cours de route.

<mark>N'ayez pas peur de demander et de discuter ! Cela vous permettra soit de confirmer votre approche, soit de vous épargner une semaine de travail dans une mauvaise direction.</mark>

Si cela peut être plus facile au sein d'une équipe, les personnes qui travaillent en solo peuvent parfois éprouver des difficultés à faire évaluer leurs idées. Mais n'oublions pas que de nombreuses personnes sont là pour nous aider. Nous ne sommes pas seuls.

Voici quelques-unes de mes communautés d'ingénieurs préférées, où vous pouvez trouver du soutien et des conseils :

* [Reactiflux](https://discord.com/invite/yNcseDS)
    
* [Nodeiflux](https://discord.com/invite/y5ksVAS)
    
    Ces communautés regorgent de professionnels talentueux et passionnés qui se feront un plaisir de partager leurs connaissances et de vous aider à évaluer vos idées.
    

Alors, ne restez pas isolé. Rejoignez ces communautés, posez vos questions et bénéficiez de l'expertise collective pour améliorer vos idées et votre code. Ensemble, nous pouvons accomplir de grandes choses !

### *Raison n° 2 : La manière dont vous vous exprimez*

La frontière entre "c'est affreux, refaites-le" et une explication pertinente des raisons pour lesquelles il y a une meilleure façon de faire est trop petite. N'oublions pas que le rôle de l'évaluateur est d'apporter un regard neuf. Faire preuve de compréhension envers les changements nécessaires et faire preuve de compassion lorsqu'il faut retravailler quelque chose sont essentiels pour maintenir une relation de travail saine entre l'émetteur et le réviseur.

Il est important de choisir nos mots avec soin lors de la revue de code. Au lieu de critiquer de manière abrupte, nous pouvons fournir des explications claires et des suggestions constructives. Adopter une approche empathique et comprendre que chacun fait de son mieux contribuera à maintenir une atmosphère positive et à préserver les relations professionnelles.

Alors, soyons conscients de notre langage et de notre ton. Faisons preuve de compassion et de compréhension mutuelle dans nos échanges. Cela favorisera une collaboration harmonieuse et nous permettra de progresser ensemble vers l'excellence.

*<mark>La revue de code est une conversation, pas une liste d'instructions à suivre aveuglément.</mark>*

Il est bon d'inclure des explications techniques et des liens vers des articles ou des ressources utiles lorsque l'on demande une modification. En effet, une demande de changement ne doit pas être considérée comme votre seul désir, mais comme une mesure nécessaire qui profite à tout le monde. Si le moment était critique, il est utile de donner un coup de main à votre collègue ou, peut-être, de faire un programme en binôme pour atteindre l'objectif commun, qui est de fusionner un code de qualité. Transformer le fait désagréable de devoir refaire son travail en une occasion d'apprendre est un excellent retournement de situation !

### Évaluer la logique,pas les points-virgules

Il fut un temps où j'évaluais l'absence de virgules et de points-virgules dans mes évaluations. C'est une honte (lol je rigole). C'est redondant et ne contribue à rien en vrai, mais c'est un bon exemple de la façon dont une dette technique est payée en faisant perdre du temps à tout le monde. Nous n'avions pas d'auto-formatage du code, et les gens ignoraient souvent les avertissements d'ESLint dans la console (c'est le moment d'en apprendre plus). Eh, ces temps sombres.

![Image of two women near a big typewriter](https://redd.one/blog/the-art-of-code-review/typewriter-YWBAEYNN.svg align="left")

<mark>L'automatisation réduit le nombre de vérifications inutiles et vous permet de vous concentrer sur la logique qui sous-tend les modifications, plutôt que sur les erreurs de syntaxe et les fautes de frappe.</mark>

L'utilisation d'outils comme [Prettier](https://prettier.io/) et l'intégration de vérifications de linter dans votre CI peuvent filtrer les fautes de frappe et les problèmes de syntaxe dès la première partie automatisée d'une demande d'extraction. Cela permet également de garder une base de code unifiée sans trop y penser. Le temps gagné en automatisant la routine peut être utilisé à bon escient pour vérifier la logique réelle derrière les changements.

### Gérer les changements importants (PULL REQUEST)

Le développement d'un produit de grande envergure peut donner lieu à des demandes de modifications importantes. Plus la portée d'un changement est importante, plus il est difficile d'évaluer son impact. Personne n'a envie de passer une journée entière à examiner une seule demande de modification tout en ayant un tas d'autres tâches à terminer.

![Image of a man behind a computer, and a Git commit tree](https://redd.one/blog/the-art-of-code-review/version-control-GJIGQRDJ.svg align="left")

<mark>Planifiez votre travail en petites parties, réalisables et significatives. Répétez et tirez des leçons de votre planification.</mark>

Cependant, la portée d'une fonctionnalité n'est pas le seul facteur qui affecte la taille d'une demande de modifications. Il y a aussi la profondeur technique, qui peut vous amener à modifier des centaines de fichiers simplement pour ajuster la teinte de cette petite icône.

<mark>Ayez une vision claire de vos changements avant de les effectuer. Réfléchissez bien et discutez avec vos collègues en cas de doute.</mark>

`Que faire si une fonctionnalité est petite et a un plan de développement clair en tête, mais qu'elle nécessite quand même de changer la moitié de la base de code entière ? Comment gérer cela ?`

Je peux vous recommander une approche que nous avons utilisée dans notre équipe sur un projet d'un des ministères, pour ce type de demandes et que nous avons appelée **revue de code intermédiaire**. Elle vise à réduire le nombre de modifications qu'un réviseur ou lead technique doit évaluer, ce qui se traduit par de courtes sessions de révision itératives. En tant que demandeur, cela signifie une règle pour créer une demande de modification, quel que soit l'état des changements, au plus tard le lendemain matin du premier commit. Pour un réviseur, il s'agit d'une règle qui consiste à toujours résoudre les demandes assignées au plus tard le lendemain matin. Bien sûr, toute communication nécessaire peut également avoir lieu afin que les choses soient révisées plus tôt ou plus tard.

Pour éradiquer les différences importantes dans votre système de contrôle de version, essayez d'émettre des demandes à partir d'une branche de fonctionnalités enfant vers une seule branche de fonctionnalités parent. De cette façon, chaque itération de révision se termine par la fusion des modifications dans la branche mère. Une fois le travail effectué, vous pouvez souvent fusionner la branche mère dans votre branche sans aucune revue de code préalable.

NB:Veuillez prendre toutes mes suggestions avec un regard cusieux. Je comprends qu'une même approche puisse fonctionner différemment selon les équipes, et c'est très bien ainsi. Il n'y a pas de mal à savoir comment font les autres - au pire, vous pouvez apprendre de leurs erreurs.

# Conclusion

En tant que développeur, la revue de code est une activité essentielle pour garantir la qualité du produit final. C'est un moyen de détecter les erreurs, d'améliorer la logique et de favoriser la collaboration au sein de l'équipe. En partageant mes conseils pour devenir un bon relecteur de code, j'espère avoir suscité chez vous l'enthousiasme et la volonté d'investir du temps et de l'effort dans cette pratique.

J'ai souligné l'importance de la politesse et de la compréhension mutuelle lors des revues de code, car nous sommes tous des êtres humains qui cherchent à faire de notre mieux. Je vous ai également encouragé à prendre le temps de réfléchir avant de vous lancer dans le développement, afin d'éviter des erreurs coûteuses en temps et en ressources.

La communication est un aspect crucial de la revue de code, et il est essentiel d'exprimer nos suggestions de manière claire, constructive et empathique. De plus, l'automatisation des vérifications de syntaxe et de formatage permet de se concentrer sur la logique des modifications, plutôt que sur les détails superficiels.

Enfin, j'ai abordé la gestion des demandes de modifications importantes, en recommandant une approche de revue de code intermédiaire pour faciliter le processus et réduire la charge de travail pour les réviseurs.

Ensemble, en tant qu'équipe, nous pouvons utiliser la revue de code comme un outil précieux pour améliorer la qualité de notre code, partager des connaissances et créer des produits exceptionnels. Alors, plongeons dans les méandres du code avec curiosité, respect et désir d'apprendre, et créons ensemble une symphonie logicielle harmonieuse.