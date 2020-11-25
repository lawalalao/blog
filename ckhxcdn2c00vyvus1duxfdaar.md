## Créer une API REST avec Node.js: télécharger un fichier image

Bonjour à tous! Bienvenue à nouveau dans la 5ème partie de la série d'API REST **Créer une API REST avec Node.js**. Nous sommes si près de terminer cette API. Ne perdons plus de temps et commençons!

Si vous êtes nouveau dans cette série, veuillez consulter les articles précédents à suivre:


1. 
 [Conception et planification de l'API](https://lawaltech.hashnode.dev/creez-une-api-rest-avec-nodejs-concevez-et-planifiez-votre-api?guid=aeb98ca9-707d-467e-8e44-7c8efdc24ec2&deviceId=8bffedad-d849-4d38-9356-4b5b673b80aa) 

2. 
 [Routes et contrôleurs](https://lawaltech.hashnode.dev/creez-une-api-rest-avec-nodejs-routes-et-controleurs) 

3. 
 [Intégration de MongoDB Atlas](https://lawaltech.hashnode.dev/creer-une-api-rest-avec-nodejs-integration-de-mongodb-atlas) 

4. 
 [Finalisation des contrôleurs](https://lawaltech.hashnode.dev/creer-une-api-rest-avec-nodejs-finaliser-les-controleurs) 

Dans l'article précédent, nous avons enfin toutes nos fonctions de contrôleur terminées et fonctionnelles. Notre API peut GET, POST et SUPPRIMER nos objets de thé qui se composent de:

<table style="width:100%">
  <tr>
    <th>Proprietes</th>
    <th>Description</th>
    <th>Types</th>
  </tr>
<tr>
    <th>name</th>
    <th>tea name</th>
    <th>String</th>
  </tr>
<tr>
    <th>image</th>
    <th>image url</th>
     <th>String</th>
  </tr>
<tr>
    <th>description</th>
    <th> description</th>
     <th>String</th>
  </tr>
<tr>
    <th>keywords</th>
    <th>	words associated with the tea</th>
    <th>String</th>
  </tr>
<tr>
    <th>origin	</th>
    <th>	country where the tea is first made</th>
    <th>String</th>
  </tr>
<tr>
    <th>brew_time	</th>
    <th>	time to brew in minutes</th>
    <th>Number</th>
  </tr>
<tr>
    <th>temperature	</th>
    <th>	best temperature in Celsius to drink</th>
    <th>number</th>
  </tr>
<tr>
    <th>comments		</th>
    <th>	any comments posted about the tea</th>
    <th>Array of string</th>
  </tr>
</table>

Cependant, dans l'article précédent, j'ai défini la propriété image sur "factice". Dans cet article, nous travaillerons à le configurer correctement.

# Étape 1: Installez multer et importez

Pour les images, nous ne fournissons pas seulement une chaîne de texte comme "nom" mais un fichier, un fichier image pour être exact. Et notre propriété image est une chaîne qui sera le chemin de notre fichier image téléchargé.

Taper simplement "/myImage.png" dans notre req.body.image ne fonctionnera pas car ce chemin n'existe pas. Nous devons télécharger notre image avec  [multer](https://www.npmjs.com/package/multer) , un middleware node.js utile pour télécharger des fichiers.

Installez multer en exécutant:

```
npm install --save multer
```
Puis importons multer dans notre fichier controllers /tea.js:
```
const multer = require('multer');
```

# Étape 2: créer un stockage

Toujours dans notre fichier controllers /tea.js, nous ajoutons le code suivant pour créer un stockage où seront stockées nos images téléchargées.

Nous utilisons multer.diskStorage() et incluons ses 2 propriétés:


- 
destination: le chemin où les images seront stockées. Nous allons le définir comme «./uploads».

- 
filename: détermine le nom qui serait enregistré dans le stockage. Nous pouvons simplement le garder comme son nom d'origine.

Voici à quoi cela devrait ressembler:

```
const storage = multer.diskStorage({
    destination: function (req, file, cb) {
        cb(null, './uploads');
      },
    filename: function (req, file, cb) {
        cb(null, file.originalname);
    }
});
```
N'oubliez pas de créer un dossier «**uploads**» dans votre répertoire racine afin qu'il existe réellement pour l'image à y stocker.

# Étape 3: fonction de téléchargement d'image

Sous notre stockage `const`, nous pouvons initialiser multer avec `multer()` et passer le stockage dans sa propriété de stockage. Ensuite, nous avons une méthode `.single()` qui garantit que multer n'acceptera qu'un seul fichier et le stockera sous le nom `req.file`.

Le code sera:

```
const uploadImg = multer({storage: storage}).single('image');
```
Dans notre fonction `newTea`, nous devons changer notre propriété image en `req.file.path` au lieu de `req.body.image` car nous voulons que l'image soit le chemin de notre fichier image, et non une chaîne de `req.body.image`.

```
const newTea = new Tea({
     name:req.body.name,
     image: req.file.path,  //update this
     description: req.body.description,
     keywords: req.body.keywords,
     origin: req.body.origin,
     brew_time: req.body.brew_time,
     temperature: req.body.temperature,
})
```

Il ne nous reste plus qu'à exporter `uploadImg` pour l'utiliser dans nos routes `/tea.js` et l'inclure comme middleware. Incluez donc cette fonction dans notre module.exports en bas, avec le reste.

```
module.exports = {
    getAllTea,
    uploadImg,  //include the new guy
    newTea,
    deleteAllTea,
    getOneTea,
    newComment,
    deleteOneTea
};
```
Dirigez-vous maintenant vers notre fichier routes `/tea.js`, trouvez la route POST`/tea` et ajoutez uploadImg avant newTea.

```
router.post('/tea', teaController.uploadImg /*insert this guy*/ , teaController.newTea);
```

# Testons-le!

Essayons de POSTER un nouveau thé avec POSTman. Assurez-vous que la méthode est définie sur POST et que l'URL est correcte. Fournissez des valeurs pour chaque propriété. Pour l'image, définissez-le sur «fichier» au lieu de texte, puis téléchargez une image.


![13.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1606269728827/WqG59Vl1r.png)

POSTman devrait renvoyer nos nouvelles données d'objet thé avec notre propriété d'image enregistrée comme chemin vers notre image.


![14.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1606269746323/WSYtf5qKn.png)

Si nous voyons notre dossier «uploads», l'image que nous avons téléchargée devrait s'y trouver. Cela signifie que ça marche! Nous pouvons télécharger des images sur notre objet thé.


![15.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1606269827959/bBUibW2Gg.png)

# Et pour GET?

Il est inutile de pouvoir POSTER si vous ne pouvez pas OBTENIR l'image correctement?

Essayons d'obtenir l'image en entrant **http://localhost:3000/uploads/green.png** comme URL dans POSTman et définissons la méthode sur GET. Vous devriez voir cette erreur renvoyée:


![16.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1606269892794/5QjHA19qy.png)

# Pourquoi cela est-il ainsi?

Notre dossier «uploads» n'est pas accessible publiquement et par conséquent le serveur ne peut pas OBTENIR notre image. Pour résoudre ce problème, nous devons faire de notre dossier uploads un fichier statique.

Accédez à server.js et ajoutez cette ligne de code:

```
app.use('/uploads', express.static('./uploads'));
```

Maintenant, réessayons ce test sur POSTman et il devrait renvoyer l'image correctement.


![17.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1606269968438/N2G71SB9V.png)

# Toutes mes félicitations!

Notre API est maintenant pleinement opérationnelle et construite! Il ne reste plus qu'à ajouter de la sécurité et à la déployer pour l'utiliser! Ce sera dans notre prochaine et dernière partie de la série. Merci d'avoir lu et suivi cette série, j'espère qu'elle vous a été utile. Restez à l'écoute pour la dernière partie. En attendant, posez vos questions ou préoccupations dans les commentaires et reportez-vous aux ressources ci-dessous. Merci!

## Lectures complémentaires


-  [A props de Multer](https://www.npmjs.com/package/multer) 
