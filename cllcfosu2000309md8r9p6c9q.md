---
title: "De Zéro à Ingénieur DevOps - Feuille de route DevOps adaptée à votre parcours spécifique."
datePublished: Tue Aug 15 2023 15:03:40 GMT+0000 (Coordinated Universal Time)
cuid: cllcfosu2000309md8r9p6c9q
slug: de-zero-a-ingenieur-devops-feuille-de-route-devops-adaptee-a-votre-parcours-specifique
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1692111749304/fd824ed5-fe42-46ae-b0ea-0af4ca240603.jpeg
tags: docker, devops, beginners, it, networkengineering

---

En tant que professionnel du DevOps, parfois on oublie à quel point il peut être difficile à un débutant d'entrer dans le monde du DevOps. C'est pourquoi j'ai décidé de créer cet article pour établir un parcours que je suivrais si je devais repartir de zéro avec les connaissances que j'ai acquises, quel serait le chemin le plus efficace pour y parvenir ?

En somme, quelles sont les étapes pour devenir ingénieur DevOps, ce que vous devez apprendre et dans quel ordre. ✅

Je réalise une vidéo actuellement sur la feuille de route DevOps (abonnez-vous en attendant la vidéo pour ne rien rater [https://youtube.com/@alaolawal](https://youtube.com/@alaolawal2125)), expliquant quels concepts et outils font partie de DevOps, et spécialement je vous montre comment vous pouvez devenir un ingénieur DevOps, si vous partez de zéro.

Et en plus je voulais la rendre plus individuelle pour les personnes ayant les parcours les plus courants de transition vers DevOps et, sur la base d'un sondage, j'ai choisi 5 des parcours les plus courants qui sont :

* Administrateurs système
    
* Développeurs de logiciels
    
* Ingénieurs en automatisation de tests
    
* Ingénieurs réseau
    

et les personnes n'ayant aucune ou très peu de connaissances en informatique. Si vous avez l'un de ces parcours, cet article vous sera très utile, car il vous montrera VOTRE chemin individuel vers le DevOps. Alors commençons ! 🙌

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1692003177822/4f6235df-9e95-4254-b30d-976d8e4407a4.gif align="center")

## Qu'est-ce que DevOps ?

Si vous ne savez pas ce qu'est DevOps. Vous pouvez d'abord regarder ma prochaine vidéo 😁😁 mais je vous l'explique plus bas 👇🏾👇🏾 :

Abonnez vous pour ne rien rater [https://youtube.com/@alaolawal](https://youtube.com/@alaolawal2125)

<mark>DevOps est une approche de développement logiciel et de gestion des opérations qui vise à améliorer la collaboration entre les équipes de développement (Dev) et les équipes d'exploitation (Ops). L'objectif principal de DevOps rendre tout le monde content.</mark>

## Qu'est-ce que l'ensemble des compétences DevOps ?

Maintenant, tout d'abord pour comprendre comment devenir un professionnel du DevOps, définissons exactement l'ensemble des compétences nécessaires pour cela. 🤔

**1 - Les bases du développement logiciel**

Comme vous travaillez en étroite collaboration avec l'équipe de développement pour améliorer et automatiser les tâches pour eux, vous devez comprendre les concepts de :

* Comment les développeurs travaillent et
    
* Quels flux de travail ils utilisent
    
* Comment ils collaborent au développement de fonctionnalités
    
* Les processus modernes comme agile et scrum
    
* Le flux de travail Git qu'ils utilisent
    
* Comprendre de manière générale ce que couvre le cycle de développement d'un logiciel, de l'idée au code, jusqu'à la mise à disposition aux utilisateurs finaux.
    

Il est important de souligner que vous n'avez pas besoin d'être un développeur de logiciels ou celui qui met en œuvre ces processus agiles et scrum. Vous devez **comprendr**e comment ces choses fonctionnent à un niveau élevé, de manière conceptuelle.

**2 - Déploiement de logiciels**

L'étape suivante est le déploiement du logiciel. Une fois la fonctionnalité développée, elle doit être mise à la disposition des utilisateurs finaux, ce qui signifie que vous avez besoin d'un environnement dans lequel votre application fonctionnera et sera disponible pour les utilisateurs finaux.

**2.1 - Systèmes d'exploitation et bases de Linux**

En tant qu'ingénieur DevOps, vous devez savoir comment

* Provisionner et préparer ces environnements et
    
* Comment les maintenir.
    

Et pour cela, vous devez connaître **l'administration générale des serveurs**, comme la création de machines virtuelles, principalement avec le système d'exploitation Linux, l'installation de logiciels, l'application de correctifs, la configuration du réseau sur site et sur le cloud.

**2.2 - Conteneurs avec Docker**

Dans le cadre des concepts d'infrastructure plus modernes, vous devez comprendre comment travailler avec des conteneurs et la technologie de conteneur la plus populaire, à savoir **Docker**.

**2.3 - Orchestration de conteneurs avec Kubernetes**

Et pour les projets avec des dizaines ou des centaines de conteneurs Docker, vous devez savoir comment travailler avec des plateformes d'orchestration de conteneurs comme Kubernetes, qui est la plus populaire de nos jours.

Et encore une fois, tous ces outils peuvent être utilisés soit on premise, soit on cloud.

**2.4 - Cloud - Apprendre 1 des fournisseurs de cloud les plus populaires**

Si vous travaillez sur un cloud comme AWS, qui est la plateforme cloud la plus populaire et la plus utilisée à l'heure actuelle, vous devez également connaître les services spécifiques d'AWS et savoir comment gérer l'ensemble de l'infrastructure de déploiement sur AWS.

![AWS Market Share](https://res.cloudinary.com/practicaldev/image/fetch/s--gWxw-4Jw--/c_limit%2Cf_auto%2Cfl_progressive%2Cq_auto%2Cw_880/https://dev-to-uploads.s3.amazonaws.com/uploads/articles/i857btnc2o084voq7ksu.jpeg align="left")

**3 - CI/CD - Intégration continue et déploiement continu**

Les pipelines d'intégration continue et de déploiement continu relient tous ces éléments et constituent en quelque sorte le cœur des processus DevOps.

Comment relier le développement et le déploiement de logiciels ? En d'autres termes, lorsqu'un logiciel est développé, comment déployer les fonctionnalités développées ?

Il ne s'agit pas seulement de les déployer dans l'environnement de déploiement, nous ne nous contentons pas de les prendre et de les mettre en place. Pourquoi ? Parce que les humains font des erreurs, soit par manque de connaissances dans un domaine, soit par accident. Le code déployé doit donc passer par plusieurs de ces contrôles avant d'être autorisé dans l'environnement final, et c'est à cela que sert le pipeline DevOps CI/CD :

**tester le code, l'empaqueter et et le déployer jusqu'à l'environnement final pour le livrer aux utilisateurs finaux**.

![CI/CD Pipeline](https://res.cloudinary.com/practicaldev/image/fetch/s--JZaJrMiW--/c_limit%2Cf_auto%2Cfl_progressive%2Cq_auto%2Cw_880/https://dev-to-uploads.s3.amazonaws.com/uploads/articles/1man7zjvnefnbw0h74tf.png align="left")

**Qu'est-ce que ces gardiens ?**

Eh bien, tester la qualité du code, tester la logique du code, tester qu'il n'a pas cassé le code existant, vérifier les problèmes de sécurité, tester qu'il fonctionne comme il est censé le faire, etc. Les outils permettant de mettre en œuvre l'ensemble des pipelines CI/CD avec tous ces gardiens sont donc un ensemble de compétences très important.

Connaître les outils de CI/CD comme Jenkins, Gitlab CI/CD, GitHub Actions, Circle CI et ainsi de suite. Et surtout, il est très important de savoir comment intégrer cet outil avec toutes les autres technologies pour tester les choses, déployer le code, etc.

**4 - Surveillance et observabilité**

Encore une fois, nous sommes des êtres humains et nous pouvons supposer que même avec les mesures les plus prudentes et de nombreux tests approfondis, nous ne pouvons pas toujours tester à 100 % chaque aspect du déploiement et qu'un problème peut se glisser dans la production. 🤷🏻‍♂️ C'est pourquoi nous avons des bogues en production et ce n'est pas grave tant que nous avons un plan pour gérer un bogue ou un problème lorsqu'il apparaît en production.

Une fois encore, une partie des compétences DevOps consiste à créer un processus de gestion des problèmes découverts en production au lieu d'adopter un mode panique. **Qu'est-ce que cet ensemble de compétences comprend ?** Eh bien, c'est ce qu'on appelle la "**surveillance et l'observabilité**".

Ainsi, lors de la dernière étape du déploiement continu, après avoir déployé les modifications du code, nous ne nous contentons pas de dire : "Hé, nous avons fini, c'est déployé, alors maintenant passons à la tâche suivante", mais nous observons et surveillons de près ce qui se passe. Si un utilisateur rencontre une erreur, si quelque chose se bloque ou ne fonctionne pas, nous savons que nous devons corriger cela de manière proactive. Ainsi, pendant quelques heures ou dans les jours qui suivent le déploiement, nous observons activement si un problème quelconque apparaît dans la production.

**5 - Automatisation (ma partie préférée)**

Et enfin la dernière pièce manquante pour vraiment conquérir DevOps, c'est d'automatiser tout ça. 👏 En gros, vous automatisez la plupart de votre propre travail et celui des autres ingénieurs, en automatisant surtout dans les domaines où la même tâche doit être répétée.

Laissez-moi vous donner quelques exemples, pour chaque nouveau code publié :

vous devez toujours tester votre application, vous devez toujours vérifier la sécurité, vous devez toujours empaqueter et déployer les modifications apportées à l'application. Ces tâches doivent être exécutées automatiquement, c'est pourquoi vous vous assurez d'exécuter les tests automatisés que les développeurs ou les ingénieurs de test écrivent, vous avez des contrôles de sécurité automatisés, des contrôles de qualité et vous avez des scripts ou un code d'automatisation qui déploie ce code dans l'environnement final :

![CI/CD automates all human tasks](https://res.cloudinary.com/practicaldev/image/fetch/s--k_omrfXi--/c_limit%2Cf_auto%2Cfl_progressive%2Cq_auto%2Cw_880/https://dev-to-uploads.s3.amazonaws.com/uploads/articles/45m2yyq169ivlvs0h26p.png align="left")

Ainsi, vous ne déployez pas l'application localement à partir de votre propre machine, mais le pipeline CI/CD la déploie automatiquement.

Une autre question est celle de la surveillance. Il est évident que vous ne voulez pas être assis devant un ordinateur et observer et attendre de voir si quelque chose se brise dans l'application, au lieu de cela vous voulez déployer des outils qui surveillent l'application et vous informent si quelque chose ne va pas ou si quelque chose se produit :

![Monitoring tools](https://res.cloudinary.com/practicaldev/image/fetch/s--hhmyRs_E--/c_limit%2Cf_auto%2Cfl_progressive%2Cq_auto%2Cw_880/https://dev-to-uploads.s3.amazonaws.com/uploads/articles/lc81eaf2q2b7no1uf0nl.png align="left")

Les outils de surveillance et d'observabilité font donc également partie de la panoplie DevOps.

**5.1 - L'infrastructure en tant que code**

Mais dans DevOps, nous ne nous arrêtons pas là avec l'automatisation, nous automatisons également des choses qui ne se répètent pas à chaque déploiement de changement de code, mais qui s'avèrent toujours incroyablement efficaces.

Ainsi, par exemple, le provisionnement de l'infrastructure ou la mise en place d'un cluster Kubernetes n'est pas quelque chose que vous faites très souvent, mais nous l'automatisons tout de même dans DevOps. Pourquoi ? Parce que nous voulons être en mesure de répliquer facilement nos environnements de déploiement s'ils sont corrompus ou si nous avons besoin de plusieurs environnements de staging, comme DEV, TEST et PRODUCTION :

![Infrastructure as Code](https://res.cloudinary.com/practicaldev/image/fetch/s--f4Givkzb--/c_limit%2Cf_auto%2Cfl_progressive%2Cq_auto%2Cw_880/https://dev-to-uploads.s3.amazonaws.com/uploads/articles/l05apgz703f9jvot80za.png align="left")

D'une manière générale, le fait que tout soit codé plutôt que d'avoir des scripts manuels qu'une personne de l'équipe exécute et dont personne n'est au courant présente de nombreux avantages :

tout d'abord:

* encourager la collaboration au sein d'une équipe sur la configuration de l'infrastructure
    
* Documenter les changements apportés à l'infrastructure
    
* Transparence de l'état de l'infrastructure et
    
* L'accessibilité à ces informations dans un endroit centralisé plutôt que dispersées sur les machines locales des gens sous la forme de quelques scripts.
    
    Il s'agit d'un concept d'infrastructure en tant que code qui s'inscrit dans le mouvement général d'automatisation de tous les flux de travail afin de les rendre plus efficaces.
    

Les outils les plus populaires dans ce domaine sont **Terraform** pour le provisionnement de l'infrastructure et **Ansible** pour la gestion de la configuration.

**5.2 Compétences en matière de scripts**

Bien qu'il ne soit pas nécessaire de programmer l'application en tant qu'ingénieur DevOps (nous y reviendrons plus loin dans l'article), vous aurez besoin de compétences en matière de script ou de programmation de base pour automatiser divers processus DevOps.

Il peut s'agir d'un simple script shell ou, mieux encore, d'un langage de programmation à part entière comme Python. Cependant, il n'est pas nécessaire d'être capable de développer des applications web avec Python comme un développeur de logiciels. Il suffit de savoir écrire des scripts d'automatisation avec Python et c'est en fait beaucoup plus facile à apprendre.

Quelques exemples seraient l'écriture d'un script shell pour effectuer une tâche dans un job Jenkins dans un pipeline CI/CD ou l'écriture d'un petit script utilitaire pour vider le cache, démarrer les builds et les déploiements, connecter différents outils, etc.

Il existe de nombreux langages de programmation, mais je recommanderais de commencer par Python. Python est largement utilisé, facile à apprendre et utilisé pour de nombreux cas d'utilisation différents, en particulier dans DevOps. Et la bonne chose est que les concepts de programmation restent les mêmes, donc quand vous apprenez bien un langage, vous pouvez facilement en apprendre de nouveaux assez rapidement.

**6 - Contrôle de version avec Git**

Vous écrivez toute la logique d'automatisation mentionnée ci-dessus sous forme de code. Et tout comme les développeurs gèrent le code de l'application avec un outil de contrôle de version, comme Git, vous devez également gérer ce code d'automatisation et les fichiers de configuration avec un outil de contrôle de version.

![Pause-breathe-love GIFs - Get the best GIF on GIPHY](https://media3.giphy.com/media/v1.Y2lkPTc5MGI3NjExNTJid3FodW0wZ3FkYnBxMmFtMzZvZTYwaWo3b2JqenRocTRlbXpnciZlcD12MV9naWZzX3NlYXJjaCZjdD1n/iL4LnlSZq6J20/giphy.gif align="left")

Il s'agit donc des processus fondamentaux et des outils respectifs qui font partie de DevOps. Tous les autres outils DevOps que vous pouvez rencontrer - et il en existe des centaines - ne font qu'optimiser ou améliorer différentes parties de ce flux de travail.

**Quel est VOTRE point zéro ou point de départ ?**

🤔 Donc, avoir ces compétences DevOps est l'objectif final et vous partez de zéro, mais beaucoup d'entre vous sont en transition vers DevOps ou commencent leur voyage DevOps en ayant des antécédents différents. Le point de départ est donc différent pour chacun d'entre vous et, comme je l'ai mentionné au début, vous pouvez être administrateur système, ingénieur logiciel, ingénieur QA, etc. ou ne pas avoir de formation informatique du tout et vouloir faire la transition vers DevOps :

![Different starting points when transitioning into DevOps](https://res.cloudinary.com/practicaldev/image/fetch/s--3FHpUhZr--/c_limit%2Cf_auto%2Cfl_progressive%2Cq_auto%2Cw_880/https://dev-to-uploads.s3.amazonaws.com/uploads/articles/smz5dg5qts03fal3t2yl.png align="left")

Donc maintenant, je veux vous montrer comment vous pouvez faire la transition vers DevOps et essentiellement apprendre tous ces outils que je viens de mentionner en partant de votre contexte spécifique. ✅

### **Débuter en tant qu'administrateur de systèmes 🧑🏽‍💻**

Si vous êtes administrateur de systèmes, vous savez comment administrer des serveurs et d'autres systèmes. Vous avez donc déjà des compétences dans les domaines suivants:

* mettre en place une infrastructure la configuration et la préparation au déploiement
    
* Travailler avec des systèmes d'exploitation, installer et exécuter des logiciels la sécurité, la configuration du réseau, etc. vous sont déjà familières.
    
* Parmi les autres tâches de l'administrateur de systèmes, citons la surveillance des systèmes, la santé, la sauvegarde et la reprise après sinistre, l'installation et l'application de correctifs sur les serveurs, etc.
    

Dans le cadre de projets plus modestes, vous pouvez également être amené à administrer des bases de données, des réseaux ou des systèmes de sécurité.

Toutes ces compétences sont très utiles, si vous voulez devenir un ingénieur DevOps. 👍 Vous avez donc déjà beaucoup de compétences que vous pouvez utiliser dans le volet déploiement et opérations de DevOps :

![Skills in deployment and operations part of DevOps](https://res.cloudinary.com/practicaldev/image/fetch/s--5d3hcvi2--/c_limit%2Cf_auto%2Cfl_progressive%2Cq_auto%2Cw_880/https://dev-to-uploads.s3.amazonaws.com/uploads/articles/747h16shxun522d5483k.png align="left")

Cela comprend les activités du jour 0 telles que la configuration initiale de l'infrastructure, mais aussi les tâches du jour 1 telles que la maintenance et l'exploitation de cette infrastructure.

De nombreux administrateurs de systèmes connaissent également l'écriture de scripts, ce qui sera utile pour la partie automatisation de DevOps. En tant qu'administrateur système, vous disposez donc déjà d'une très bonne base pour vous lancer dans le DevOps. Cependant, la grande partie manquante pour commencer dans le DevOps est l'apprentissage des bases du développement logiciel

* comprendre les flux de travail git
    
* Comment les développeurs travaillent, etc.
    

Il est très important de noter que même si certains ingénieurs DevOps savent programmer, ce n'est pas une compétence essentielle dans le DevOps, car en tant qu'ingénieur DevOps, votre tâche principale n'est pas de développer, mais de créer des processus automatisés pour livrer le logiciel développé aux utilisateurs finaux de manière efficace et avec le moins de bugs et de problèmes possible :

![Process to deliver app to end users](https://res.cloudinary.com/practicaldev/image/fetch/s--EvN4A7NV--/c_limit%2Cf_auto%2Cfl_progressive%2Cq_auto%2Cw_880/https://dev-to-uploads.s3.amazonaws.com/uploads/articles/bdh5g2nm1m6ine66o65k.png align="left")

Mais pour être en mesure d'apporter des modifications à l'application, il faut bien sûr comprendre comment cette application a été construite, développée et comment elle fonctionne.

### Débuter en tant que développeur de logiciels 👩‍💻 (mon cas)

Si vous êtes développeur de logiciels, vous avez déjà un bon bagage, car vous connaissez déjà une partie importante de DevOps, à savoir les processus de développement de logiciels et leur fonctionnement.

Mais il vous manque très probablement des compétences en matière de gestion des serveurs. Vous devez donc commencer par vous familiariser avec

* les machines virtuelles la création et la configuration de serveurs
    
* la configuration de l'infrastructure, la sécurité, la mise en réseau, etc.
    

Et comme la plupart des applications modernes fonctionnent sur le cloud, vous devez également apprendre à faire tout cela sur l'infrastructure du cloud.

Voilà donc votre point de départ pour apprendre le DevOps en tant que développeur de logiciels.

Et une fois que vous avez cette base, vous pouvez la développer en apprenant comment les conteneurs fonctionnent au-dessus des machines virtuelles et comment exécuter des applications dans des conteneurs et comment exécuter des conteneurs sur une plate-forme comme Kubernetes, etc.

Et bien sûr, vos compétences en programmation seront d'une grande aide pour écrire des scripts automatisés pour diverses parties des processus de développement et de déploiement d'applications. 👍

### Débuter en tant qu'automaticien de test Engineer👨🏼‍💻

Le métier d'ingénieur en automatisation de tests est un autre parcours courant des personnes qui se lancent dans le DevOps. Vous avez peut-être un peu plus de retard à rattraper et plus de compétences à acquérir que les développeurs ou les administrateurs de systèmes, mais vous pouvez certainement réutiliser bon nombre de vos compétences dans DevOps.

En tant qu'ingénieur de test, vous savez très probablement comment les développeurs de logiciels travaillent, comme les processus agiles, les flux de travail Jira, etc. Et dans le cadre de vos connaissances en automatisation des tests, vous comprenez les différentes portées de test comme

* Les tests au niveau du code tester l'ensemble de l'application à un niveau plus abstrait
    
* Tester l'intégration de l'application avec d'autres services, etc.
    

Vous comprenez également comment tester les différents aspects d'une application et cette connaissance est vraiment utile pour mettre en place un pipeline CI/CD automatisé, parce que pour automatiser le pipeline et rationaliser la livraison de vos changements d'application jusqu'à l'environnement de production, vous avez besoin de tests automatisés étendus :

![Extensive testing for multi-stage deployments](https://res.cloudinary.com/practicaldev/image/fetch/s--I7fx3bUU--/c_limit%2Cf_auto%2Cfl_progressive%2Cq_auto%2Cw_880/https://dev-to-uploads.s3.amazonaws.com/uploads/articles/eqse9nnxq57nedys68rp.png align="left")

En effet, dès que vous avez besoin d'un élément humain, vous brisez le pipeline automatisé et ajoutez un goulot d'étranglement :

![Manual process breaks automated pipeline](https://res.cloudinary.com/practicaldev/image/fetch/s--isp8uDIv--/c_limit%2Cf_auto%2Cfl_progressive%2Cq_auto%2Cw_880/https://dev-to-uploads.s3.amazonaws.com/uploads/articles/0b43uxkm1d3z1wixb920.png align="left")

Et puisque vous savez comment écrire des tests automatisés dans divers langages de programmation, vos compétences dans divers cadres de test sont certainement utiles ici pour écrire des scripts et coder certaines parties automatisées des processus DevOps. Ou disons que ce ne sera pas complètement nouveau pour vous. 👍

### Commencer en tant qu'ingénieur réseau 🧑🏻‍💻

La dernière mention honorable d'une formation permettant d'accéder à DevOps est l'ingénierie réseau. C'est probablement la formation la plus éloignée de DevOps par rapport aux trois autres que je viens de mentionner, mais vous avez tout de même des compétences que vous pouvez apporter à DevOps en tant qu'ingénieur réseau.

En tant qu'ingénieur réseau, vous savez comment configurer les appareils et les réseaux entre les appareils. Vous possédez donc des connaissances précieuses en matière de configuration de réseaux pour l'infrastructure sur site.

Transition vers le métier d'ingénieur réseau cloud Mais comme la plupart des entreprises déplacent leur infrastructure vers le cloud, de nombreux ingénieurs réseau passent à l'ingénierie réseau cloud :

![Moving to cloud](https://res.cloudinary.com/practicaldev/image/fetch/s--NLc-jnIy--/c_limit%2Cf_auto%2Cfl_progressive%2Cq_auto%2Cw_880/https://dev-to-uploads.s3.amazonaws.com/uploads/articles/nbvyeleoan8ddqtdrfan.png align="left")

Ils font donc tout cela sur des plateformes cloud. Et au lieu de configurer des routes, des commutateurs et des réseaux sur l'infrastructure sur site, ils configurent des routes virtuelles, des commutateurs virtuels et des réseaux virtuels sur l'infrastructure en nuage.

Avec des connaissances en matière de réseaux et de réseaux virtuels, vous avez un avantage pour comprendre les réseaux dans les machines virtuelles et les conteneurs, qui représentent une grande partie de la façon dont les applications modernes fonctionnent. Il vous sera donc plus facile de comprendre les réseaux Docker et Kubernetes, par exemple, et ce sont généralement des parties assez difficiles à gérer et à dépanner ou à sécuriser, lorsque vous configurez et maintenez les environnements de déploiement avec Kubernetes et les conteneurs sur eux.

Vous pouvez donc certainement utiliser vos connaissances et votre expertise dans ce domaine. Certains ingénieurs réseau connaissent même l'écriture de scripts en bash ou en python par exemple, ce qui est une autre compétence utile lorsqu'il s'agit de la partie automatisation de DevOps.

# DevOps Bootcamp en tenant compte de ces différents contextes 💡

Maintenant, c'est tous ces background que j'ai effectivement pris en compte lors de la création de mon cours sur Udemy (**DEVOPS : De débutant à expert)**.

<mark>Nous avons donc ajouté le module Linux Basics, où vous apprenez tout sur les systèmes d'exploitation et Linux ainsi que sur la mise en réseau, les scripts Bash, etc. Tout est parti de zéro</mark> alors inscrivez vous pour ne rien rater [https://forms.gle/vhMJqXjSgJPvuzxZ7](https://forms.gle/vhMJqXjSgJPvuzxZ7)

![Linux Module for Software Developers and Testers](https://res.cloudinary.com/practicaldev/image/fetch/s--_Jjv0esE--/c_limit%2Cf_auto%2Cfl_progressive%2Cq_auto%2Cw_880/https://dev-to-uploads.s3.amazonaws.com/uploads/articles/9m4p6jwsjkofm2pyzo1e.png align="left")

Donc, si vous êtes un développeur de logiciels ou un ingénieur en automatisation de tests, cela vous donnera les connaissances préalables et la base pour apprendre des choses comme le provisionnement des serveurs de déploiement, la configuration des serveurs et la préparation du déploiement, etc. ainsi que la façon d'administrer certains outils DevOps comme Jenkins et le cluster Kubernetes et ainsi de suite.

Il est évident qu'en tant qu'administrateur système, vous sauterez cette partie, mais vous devrez plutôt apprendre Git et comment travailler avec les flux de travail Git, afin de l'utiliser pour écrire l'infrastructure en tant que code, par exemple. Vous devrez également vous familiariser avec les outils de construction et d'empaquetage afin d'empaqueter les applications écrites dans différents langages.

Comme vous le voyez, il y a des prérequis que vous devez avoir dans le DevOps et les différentes formations apportent divers prérequis avec elles et nous avons inclus ces prérequis pour ceux qui les manquent, mais une fois que ces prérequis sont remplis, le chemin est à peu près le même pour tout le monde, parce que les outils comme Kubernetes, Terraform, EKS, même Docker sont assez nouveaux pour beaucoup de professionnels et il n'y a pas de profession qui était spécifiquement dédiée à ces outils auparavant. Tout le monde doit donc les apprendre, quelle que soit sa formation en informatique :

![DevOps Bootcamp](https://res.cloudinary.com/practicaldev/image/fetch/s--qOqO6uK9--/c_limit%2Cf_auto%2Cfl_progressive%2Cq_auto%2Cw_880/https://dev-to-uploads.s3.amazonaws.com/uploads/articles/isu66suzfjm4pea6vjs1.png align="left")

## Commencer avec peu ou pas d'expérience en informatique 🙉

Enfin, je reçois également de nombreuses questions sur le fait de commencer mon cours; DevOps avec très peu ou pas d'expérience en informatique. Ce qui signifie qu'il y a probablement beaucoup d'entre vous qui liseront cet article ou qui lisent mes posts, qui pensent à se lancer dans DevOps en faisant une reconversion sans beaucoup de connaissances informatiques préalables et qui veulent savoir quel est le chemin vers DevOps.

Il s'agit d'une question très délicate, car DevOps n'est PAS vraiment la profession d'entrée de gamme dans ce domaine. Ce n'est pas la première chose que l'on apprend quand on veut entrer dans le domaine de l'informatique. Pourquoi cela ? 🤷🏻‍♂️ Parce que DevOps concerne:

<mark>l'automatisation des processus et du développement et du déploiement de logiciels que les gens font manuellement depuis très longtemps.</mark>

Cela signifie qu'avant d'automatiser des processus et des tâches qui sont effectués manuellement, vous devez d'abord comprendre ce que sont ces processus et ces tâches. Si vous ne les comprenez pas, vous ne saurez pas ce que vous automatisez ni pourquoi vous avez besoin de DevOps.

**1 - Comprendre le cycle de vie complet du développement logiciel**

Donc, si vous êtes complètement nouveau dans l'informatique et que vous savez déjà que vous voulez éventuellement devenir un ingénieur DevOps, alors vous devriez commencer par comprendre le cycle de vie complet du développement logiciel. Et la bonne nouvelle, c'est que c'est plus facile qu'il n'y paraît. Vous n'avez pas besoin d'aller apprendre le développement logiciel pendant des mois pour cela et vous n'avez certainement pas besoin de devenir un expert en gestion d'infrastructure et en configuration de serveurs.

Si vous apprenez les bonnes choses, vous pouvez le faire en relativement peu de temps : Trouvez des projets d'exemple, où vous créez une application super simple et apprenez à la déployer sur un serveur virtuel, donc apprenez les étapes du développement, de l'emballage, peut-être même du test automatique et ensuite du déploiement d'une application d'exemple sur un serveur Linux sur une plateforme en nuage.

Il s'agit en fait d'une très bonne connaissance de base sur laquelle on peut s'appuyer pour apprendre DevOps. Dans ce processus:

* Vous apprendrez les bases de la création d'une application
    
* Vous apprendrez à créer une machine virtuelle avec un serveur Linux sur une plateforme cloud facile à utiliser et à y héberger votre application.
    

Cela vous permettra d'acquérir des compétences de base pour chaque partie du processus de développement logiciel, mais surtout de comprendre le flux de travail complet de ce processus. 👀

Vous n'avez pas besoin d'outils sophistiqués pour cela, ni de Jenkins, ni de cadre de programmation sophistiqué, ni même de Git. Encore une fois, il s'agit de comprendre les concepts de base et ensuite vous pouvez commencer à apprendre des outils DevOps comme Jenkins, Docker, Kubernetes et ainsi de suite. Parce que cette phase ne consiste pas à apprendre les outils, mais à comprendre les concepts et le flux de travail complet.

**2 - Comment les équipes de développement logiciel collaborent**

Après cela, regardez quelques tutoriels sur les méthodes agiles et scrum et sur la façon dont les équipes de développement logiciel collaborent et travaillent dans les projets de développement logiciel.

**3 - Pré-requis DevOps et 4 - Compétences DevOps**

Et ces compétences seront en fait suffisantes pour commencer mon cours DEVOPS, parce que Linux, Git et tous ces outils de base que vous apprenez réellement dans mon cours à partir de zéro. 🚀 Mais encore une fois, vous devez comprendre ces flux de travail d'abord afin de comprendre, pourquoi nous utilisons Git, pourquoi nous avons besoin de Jenkins, pourquoi nous apprenons Linux et les scripts, etc.

Et en raison de nombreuses demandes pour mon cours de la part de débutants en informatique 🙈, J'ai en fait également décidé de créer un cours complet sur les prérequis du cours. Donc si ça vous intéresse, vous pouvez d'ores et déjà vous inscrire pour être informé de la sortie du cours 🔔 : [https://forms.gle/PqTsPSGEbbUrzHod9](https://forms.gle/PqTsPSGEbbUrzHod9)

Comme je l'ai dit, vous pouvez bien sûr apprendre cela tout seul en suivant ces étapes et en élaborant un parcours d'apprentissage par vous-même ou vous pouvez utiliser mon cours sur les prérequis lorsqu'il sera disponible.

# **Résumé - Feuille de route DevOps En résumé, il y a 4 phases :**

**1 - Obtenir les bons pré-requis**

Tout d'abord, il s'agit de mettre en place les prérequis nécessaires. En fonction de votre formation et de vos connaissances préalables, vous devez d'abord vous assurer d'acquérir toutes les connaissances préalables manquantes.

Ainsi, en tant qu'administrateur système ou ingénieur réseau, apprenez les processus de développement de logiciels. En tant que développeur, apprenez les bases de l'infrastructure, des serveurs virtuels, etc. Bien entendu, si vous n'avez aucune formation en informatique, vous devez d'abord acquérir toutes ces connaissances préalables, de l'administration des serveurs au développement. L'entrée est donc plus difficile, mais c'est possible si vous savez quoi apprendre. D'ailleurs vous n'avez pas à vous en faire car j'aborde les prérequis sur le cours DEVOPS et également je ferai un cours entièrement gratuit sur les prerequis.

**2 - Cloud, Docker, Kubernetes**

La deuxième étape consiste à apprendre le cloud, Docker et Kubernetes. Après avoir appris les prérequis, vous pouvez déjà commencer avec des compétences DevOps importantes pour travailler avec des conteneurs et des outils d'orchestration de conteneurs. Il s'agit donc essentiellement d'apprendre Docker et Kubernetes pour aider vos équipes à déployer et à exécuter efficacement l'application. Kubernetes est un outil très complexe, il faudra donc un certain temps pour le maîtriser et le rendre prêt pour la production.

Et comme la plupart des applications modernes et des clusters Kubernetes s'exécutent sur le cloud, vous devez apprendre l'infrastructure cloud, comment travailler avec l'infrastructure cloud, comment la configurer, comment la mettre à l'échelle, etc.

**3 - L'automatisation**

La troisième étape est l'automatisation. Une fois que vous avez maîtrisé les compétences et les technologies ci-dessus, il est temps d'apprendre à optimiser et à automatiser les processus existants. En tant que professionnel du DevOps, les compétences en matière d'automatisation sont parmi les plus importantes.

Au cœur du DevOps, apprendre à construire des pipelines CI/CD est une compétence essentielle.

Enfin, vous apprendrez à automatiser des parties des processus DevOps complets, une par une, en utilisant les concepts et les outils de ce que l'on appelle **X as code, y compris Infrastructure as Code, Configuration as Code, Security as Code, Policy as Code** et ainsi de suite, ce qui signifie essentiellement automatiser tout ce qui est sous forme de code.

**4 - Aller de l'avant et continuer à apprendre.**

Continuez à apprendre 🙌 Le numéro quatre consiste à partir de là. DevOps et le monde de la technologie en général évolue et de nouveaux outils sont développés en permanence. Ainsi, en tant que professionnel DevOps, vous devriez apprendre à évaluer et à tester de nombreux nouveaux outils, toujours dans le même but d'optimiser et d'automatiser les processus existants et de les rendre efficaces.

# BONNE CHANCE À VOUS