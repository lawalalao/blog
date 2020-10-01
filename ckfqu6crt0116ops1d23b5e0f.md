## Comment déployer une application React sur Firebase?

## Les étapes pour déployer l'application sur Firebase:

Dans un article précédent j'ai fait la liste de quelques hébergement gratuits dont Firebase  pour vos applications web et mobile. Dans cet article je vous montre comment déployer une application React sur Firebase.

Suivez ces étapes pour déployer avec succès une application React sur le service d'hébergement Firebase.


```
npm install -g firebase-tools
``` 

```
PS C:\Users\lawal\Documents\React-September> npm install -g firebase-tools

C:\Users\lawal\AppData\Roaming\npm\firebase -> C:\Users\lawal\AppData\Roaming\npm\node_modules\firebase-tools\lib\bin\firebase.js

+ firebase-tools@8.10.0
updated 1 package in 32.755s
``` 
Avant cette etape veuillez creer un compte sur  [Firebase](firebase.com) 

```
firebase login
``` 

```
PS C:\Users\lawal\Documents\React-September\Venue Website Udemy\sep-venue-app> firebase login

Already logged in as <yourfirebaseaccount@gmail.com>
``` 

```
firebase init
``` 


```
PS C:\Users\lawal\Documents\React-September\Venue Website Udemy\sep-venue-app> firebase init

Vous êtes sur le point d'initialiser un projet Firebase dans ce répertoire:

C:\Users\lawal\Documents\React-September\Venue Website Udemy\sep-venue-app

? Are you ready to proceed? Yes
? Which Firebase CLI features do you want to set up for this folder? Press Space to select features, then Enter to confirm your choices. 
 ( ) Database: Deploy Firebase Realtime Database Rules
 ( ) Firestore: Deploy rules and create indexes for Firestore
 ( ) Functions: Configure and deploy Cloud Functions
>(*) Hosting: Configure and deploy Firebase Hosting sites
 ( ) Storage: Deploy Cloud Storage security rules
 ( ) Emulators: Set up local emulators for Firebase features

Tout d'abord, associons ce répertoire de projet à un projet Firebase.
Vous pouvez créer plusieurs alias de projet en exécutant firebase use --add,
mais pour l'instant, nous allons simplement configurer un projet par défaut.

i  .firebaserc already has a default project, using bhiyaoo-4b9fe.

=== Hosting Setup

Votre répertoire public est le dossier (relatif à votre répertoire de projet) qui
contiendra les ressources d'hébergement à télécharger avec Firebase deploy. Si vous
ayez un dossier build pour vos fichiers, utilisez ce repertoire pour le deploiement.

? What do you want to use as your public directory? build
? What do you want to use as your public directory? build
? Configure as a single-page app (rewrite all urls to /index.html)? Yes
? File build/index.html already exists. Overwrite? (y/N) No

i  Writing configuration info to firebase.json...

+  Firebase initialization complete!
``` 

```
firebase deploy
``` 

```
PS C:\Users\lawal\Documents\React-September\Venue Website Udemy\sep-venue-app> firebase deploy

=== Deploying to 'bhiyaoo-4b9fe'...

i  deploying hosting
i  hosting[bhiyaoo-4b9fe]: beginning deploy...
i  hosting[bhiyaoo-4b9fe]: found 20 files in build
+  hosting[bhiyaoo-4b9fe]: file upload complete
i  hosting[bhiyaoo-4b9fe]: finalizing version...
+  hosting[bhiyaoo-4b9fe]: version finalized
i  hosting[bhiyaoo-4b9fe]: releasing new version...
+  hosting[bhiyaoo-4b9fe]: release complete

+  Deploy complete!

Project Console: <firebase console link here>
Hosting URL: https://bhiyaoo-4b9fe.web.app
``` 

L'application sera hébergée sur l'URL fournie par Firebase Hosting.


Continuez à héberger! 🎇


> Si vous avez aime cet article veuillez le partager avec votre entourage pour qu'ils en beneficient aussi et @ suivez moi sur Twitter.. 


