---
title: "10 secrets pour améliorer votre Dockerfile"
datePublished: Thu Aug 31 2023 09:45:12 GMT+0000 (Coordinated Universal Time)
cuid: cllyzcvmo000209lgd7b12527
slug: 10-secrets-pour-ameliorer-votre-dockerfile
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1693474803021/0978b66b-6331-4c8e-a281-95d06e688024.webp
tags: docker, dockerfile, multi-stage-docker-file

---

Dockerfile est un outil puissant pour construire et déployer des applications dans des conteneurs Docker. Bien que de nombreux développeurs connaissent les bases de Dockerfile, il existe un certain nombre de fonctionnalités avancées et de bonnes pratiques qui ne sont peut-être pas aussi connues.

Dans cet article, nous allons explorer 10 choses que vous ne savez peut-être pas sur Dockerfile, y compris des trucs et astuces pour optimiser vos builds, utiliser des builds en plusieurs étapes, et plus encore. Que vous soyez novice en matière de Docker ou un professionnel chevronné, cet article vous aidera à faire passer vos compétences en matière de Dockerfile au niveau supérieur.

## Fichier .dockerignore

Vous pouvez utiliser un fichier **.dockerignore** pour exclure des fichiers et des répertoires de la copie dans le contexte de construction (build), ce qui peut aider à maintenir la taille de votre contexte de construction plus petite. Cela peut être utile s'il y a de gros fichiers ou répertoires que vous n'avez pas besoin d'inclure dans l'image, car cela réduira la quantité de données qui doivent être transférées au démon Docker pendant la construction.

plus d’informations : [*https://docs.docker.com/engine/reference/builder/#dockerignore-file*](https://docs.docker.com/engine/reference/builder/#dockerignore-file)

## Utiliser COPY plutôt que ADD

Les instructions <mark>COPY</mark> et <mark>ADD</mark> permettent toutes deux de copier des fichiers et des répertoires du contexte de construction (machine hôte) vers l'image. Cependant, il existe des différences importantes entre les deux.

ADD possède des fonctionnalités supplémentaires que COPY ne prend pas en charge, comme par exemple:

* **Extraction Tar** : la possibilité de décompresser automatiquement les fichiers compressés (.tar, .tar.gz, .tgz, .tar.bz2, .tbz2)
    
* **Invalidation du cache** : ADD invalide le cache de construction de Docker si le contenu du fichier dans le chemin change, alors que COPY ne le fait pas. Cela signifie que si vous apportez des modifications au fichier ou au répertoire source, l'utilisation de ADD déclenchera une reconstruction de l'image Docker, alors que COPY ne le fera pas.
    
* **Permissions** : Lors de l'utilisation de ADD, les permissions du fichier ou du répertoire source sont conservées, alors qu'avec COPY, les permissions du répertoire de destination sont fixées à **755** par défaut.
    
* **Prise en charge des URL de fichiers** : ADD prend en charge l'utilisation des paramètres d'URL de fichiers. Les URL de fichiers peuvent être utilisées pour copier des fichiers à partir d'emplacements distants, tels qu'un site web ou un dépôt Git. Mais la documentation officielle indique que l'instruction COPY est préférable. En effet, elle est plus transparente que l'instruction ADD qui peut avoir un comportement imprévisible.
    

*Plus d'informations:* [*https://docs.docker.com/develop/develop-images/dockerfile\_best-practices/#add-or-copy*](https://docs.docker.com/develop/develop-images/dockerfile_best-practices/#add-or-copy)

## Constructions en plusieurs étapes

Vous pouvez utiliser plusieurs instructions <mark>FROM</mark> dans un seul fichier Dockerfile pour créer une construction en plusieurs étapes, ce qui vous permet de construire votre application dans un environnement, puis de copier le résultat dans une image plus petite, prête pour la production.

Cela peut être utile pour réduire la taille de l'image finale, car vous pouvez exclure les artefacts de construction intermédiaires qui ne sont pas nécessaires à l'exécution de l'application.

```dockerfile
# Stage 1: Builder ton executable golang
FROM golang as buildStage
WORKDIR /app
COPY . .
RUN go build -o /go/bin/myapp

# Stage 2: lancer l'application
FROM alpine:latest
COPY --from=buildStage /go/bin/myapp /usr/local/bin/myapp
CMD ["myapp"]
```

*Plus d'informations:* [*https://docs.docker.com/build/building/multi-stage/*](https://docs.docker.com/build/building/multi-stage/)

## Multicouches et mise en cache

Les instructions <mark>RUN, COPY, ADD</mark> créent des calques. D'autres instructions créent des images intermédiaires temporaires et n'augmentent pas la taille de la compilation.

Ces couches sont mises en cache. Cela signifie que si vous apportez une modification à votre fichier Docker et que vous construisez à nouveau l'image, Docker ne reconstruira que les couches qui ont été modifiées. Cela peut faire gagner du temps, car les constructions suivantes seront plus rapides. Le cache est invalidé si le contenu d'une couche change, par exemple si un fichier est ajouté, modifié ou supprimé. Si vous souhaitez effectuer à nouveau la procédure complète, ajoutez l'option "**<mark>-nocache</mark>**" à la construction de docker.

Certaines des meilleures pratiques consistent à éviter les images multicouches. N'exécutez pas plusieurs commandes <mark>RUN</mark>. Reliez-les en utilisant ***&& (ex : RUN yum -disablerepo=\*, -enablerepo="myrepo" && yum update -y && yum install nmap)*** le résultat est une seule couche. (pour maintenir la lisibilité, écrivez les commandes sur des lignes différentes en utilisant && \\ à la fin de chaque ligne.

Dans la mesure du possible, utilisez des [constructions en plusieurs étapes](https://docs.docker.com/build/building/multi-stage/), et ne copiez que les artefacts dont vous avez besoin dans l'image finale. Cela vous permet d'inclure des outils et des informations de débogage dans vos étapes de construction intermédiaires sans augmenter la taille de l'image finale.

*Plus d'informations:* [*https://docs.docker.com/build/cache/*](https://docs.docker.com/build/cache/)

## Soyez un bon parent, utilisez ONBUILD

L'instruction **ONBUILD** est utilisée pour spécifier les commandes qui doivent être exécutées lorsqu'une image Docker construite à partir de votre image est utilisée comme image de base pour une autre image. Les commandes ONBUILD sont déclenchées lorsqu'une nouvelle image est construite à partir de votre image (après que la construction du Dockerfile parent soit terminée), vous permettant d'automatiser des tâches telles que la copie de fichiers et la définition de variables d'environnement.

Il est recommandé d'utiliser un autre tag (ex : myapp:1.2-onbuild) pour éviter un échec si le contexte de la nouvelle construction n'a pas la ressource ajoutée (en utilisant les instructions ADD/COPY) et laisser le choix à l'auteur.

*Plus d'informations :* [*https://docs.docker.com/develop/develop-images/dockerfile\_best-practices/#onbuild*](https://docs.docker.com/develop/develop-images/dockerfile_best-practices/#onbuild)

## Changer d'utilisateur

Par défaut, les conteneurs s'exécutent en tant que root, mais vous pouvez utiliser l'instruction USER pour spécifier un utilisateur différent pour vos conteneurs. Cela peut contribuer à renforcer la sécurité, car l'exécution des conteneurs en tant qu'utilisateurs non root peut réduire l'impact potentiel des failles de sécurité.

```dockerfile
FROM alpine:latest

# Créer un utilisateur et se connecter avec ce dernier
RUN adduser -D -u 1000 appuser
USER appuser

# Définir le répertoire de travail à /app
WORKDIR /app

# Copier le script dans le conteneur et le rendre exécutable
COPY script.sh .
RUN chmod +x script.sh

# Lancer le script
CMD ["./script.sh"]
```

*Plus d'informations:* [*https://docs.docker.com/engine/reference/builder/#user*](https://docs.docker.com/engine/reference/builder/#user)

## Vérifier l'état de santé de votre conteneur

Les contrôles de santé sont un moyen pour Docker de surveiller la santé d'un conteneur. L'instruction **HEALTHCHECK** est utilisée pour spécifier la commande que Docker doit utiliser pour vérifier la santé du conteneur. Les contrôles de santé peuvent être utilisés pour détecter si un conteneur a échoué, et Docker peut être configuré pour redémarrer automatiquement les conteneurs défaillants.

```dockerfile
...
# Définir la commande pour démarrer le serveur
CMD ["python", "app.py"]
# ajoutez un contrôle d'état de santé du serveur
HEALTHCHECK --interval=5s \\
            --timeout=5s \\
            CMD curl --fail <http://localhost:5000/health> || exit 1
```

L'instruction **HEALTHCHECK** vérifie que le serveur web python fonctionne correctement. Il effectue la vérification toutes les 5 secondes (--interval=5s) et nous voulons lui donner un maximum de 5 secondes pour répondre (--timeout=5s). L'instruction CMD spécifie la commande qui sera exécutée pour vérifier la santé du conteneur. Dans ce cas, il s'agit d'une commande curl qui tente de se connecter au point de terminaison /health du serveur web. Si le point d'accès ne répond pas dans le délai imparti ou s'il renvoie un code d'erreur, le contrôle de l'état de santé échoue et le conteneur est marqué comme étant en mauvais état.

*Plus d'informations:* [*https://docs.docker.com/engine/reference/builder/#healthcheck*](https://docs.docker.com/engine/reference/builder/#healthcheck)

## Utilisation du formulaire Shell ShellForms:

En plus de la forme exec, les Dockerfiles prennent également en charge une forme shell pour les commandes, ce qui vous permet d'utiliser des fonctionnalités spécifiques au shell, telles que la substitution de variables d'environnement et le chaînage de commandes. La forme shell est spécifiée en incluant la commande dans un script shell, tel que ***<mark>SHELL ["/bin/bash", "-c"</mark>***\].

Plus d'informations : [https://docs.docker.com/engine/reference/builder/#run](https://docs.docker.com/engine/reference/builder/#run)

## Instructions relatives aux métadonnées

Des instructions telles que **<mark>EXPOSE</mark>** et **<mark>LABEL</mark>** qui vous faciliteront la vie et celle des personnes qui travaillent avec vos images.

Si votre conteneur expose un port, soyez explicite à ce sujet et spécifiez ce qu'il expose en utilisant les instructions **<mark>EXPOSE</mark>**. Rappelez-vous que cette instruction n'a aucun impact sur le réseau. Il s'agit simplement de métadonnées.

**<mark>LABEL</mark>** Les étiquettes peuvent être utilisées à diverses fins, notamment pour identifier le but de l'image, l'auteur, etc. Les étiquettes peuvent être interrogées à l'aide de la commande ***<mark><s>docker inspect</s></mark>***<mark>.</mark>

```dockerfile
FROM ubuntu:latest
LABEL maintainer="Votre nom <votreemail@exemple.com>"
LABEL description="Voici un exemple simple de fichier Docker qui utilise les instructions LABEL et EXPOSE."
RUN apt-get update && \
    apt-get install -y nginx
EXPOSE 80
CMD ["nginx", "-g", "daemon off;"]
```

## Le fichier Docker, une fois construit, n'est qu'un fichier tar

Saviez-vous qu'une image Docker n'est en fait qu'un fichier **tar** ? C'est exact - toutes ces images Docker sophistiquées que vous avez créées et exécutées ne sont en réalité que des archives compressées de fichiers et de répertoires

Lorsque vous construisez une image Docker, Docker prend tous les fichiers et répertoires que vous spécifiez dans votre Dockerfile, les compresse dans un seul fichier tar, et ajoute ensuite quelques métadonnées.

C'est ce fichier tar compressé qui est poussé vers un registre Docker et qui est ensuite extrait par d'autres utilisateurs ou machines lorsqu'ils veulent exécuter l'image. De cette façon, votre image peut être stockée dans un objet stocké (comme S3) en tant que tar, mais ce n'est pas une bonne pratique ! :)

## Conclusion

Avec un minimum d'effort, vous pouvez retravailler vos dockerfiles pour :

* Améliorer la sécurité
    
* Améliorer la lisibilité
    
* Réduire le temps de construction, améliorant ainsi votre CI et votre productivité
    

Si vous avez aimé l'article, mettez un pouce, laissez un commentaire et partagez-le avec votre entourage :)

En Français simple merci de faire partie de notre communauté ! et n'oubliez pas de vous abonnez à ma newsletter pour faire partir des premiers à se procurer de mon manuel intitulé **<mark>l'architecture logicielle expliquée de manière simple</mark>**