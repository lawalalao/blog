## Créer une API REST avec Node.js: Finaliser les contrôleurs

Bonjour à tous! Bienvenue à nouveau dans notre serie **Créer une API REST avec Node.js**. Dans l'article précédent, nous avons intégré notre API à MongoDB et configuré notre modèle Mongoose. Nous sommes maintenant prêts à supprimer les fonctions factices de notre contrôleur et à ajouter des fonctions réelles pour manipuler notre modèle.

# Important à savoir: l'objet de requête

Selon la documentation  [Express](https://expressjs.com/en/api.html#req) ,

l'objet de requête ou «req» représente la requête HTTP et a des propriétés pour la chaîne de requête de requête, les paramètres, le corps, les en-têtes HTTP, etc.

Lorsque nous faisons une requête POST, nous envoyons un `req.body` contenant les paires clé-valeur de données au serveur. Par défaut, c'est un objet vide (c'est-à-dire {}).

Si nous voulons créer un nouvel objet thé et l'ajouter à notre base de données MongoDB, nous devrions POSTER notre objet thé avec leurs clés et valeurs fournies dans req.body. Nous verrons comment faire cela plus tard.

Par contre, lorsque nous effectuons une requête GET, nous fournissons la valeur de req.params. {Params_name} pour demander au serveur d'aller récupérer les données qui correspondent à ces paramètres. Par défaut, c'est un objet vide (c'est-à-dire {}).

![1.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1606045584531/p1eWU8dPi.png)

Par exemple, dans l'image ci-dessus, si la route est / tea /: name, la propriété "name" est req.params.name, qui a la valeur "green". Par conséquent, nous demandons au serveur d'obtenir l'objet `tea` avec celui dont la propriété name est «green».

**résumer**

L'article d'aujourd'hui peut être un peu long. Après tout, nous avons un total de 6 fonctions de contrôleur à faire. Petit rappel de notre T-API (Tea API) et de ses endpoints:

<table style="width:100%">
  <tr>
    <th>Fonction controlleurs</th>
    <th>Routes</th>
    <th>Methodes HTTP</th>
    <th>Description</th>
  </tr>
  <tr>
     <td>newTea</td>
    <td>/tea</td>
    <td>GET</td>
    <td>affiche tous les thés</td>
  </tr>
  <tr>
     <td>newTea</td>
    <td>/tea</td>
    <td>POST</td>
    <td>Cree un nouveau thé</td>
  </tr>
<tr>
    <td>newTea</td>
    <td>/tea</td>
    <td>DELETE</td>
    <td>supprime tous les thés</td>
  </tr>
<tr>
    <td>getOneTea</td>
    <td>/tea/:name</td>
    <td>GET</td>
    <td>Affiche un thé spécifique, en fonction du nom donne</td>
  </tr>
<tr>
     <td>newTeaComment</td>
    <td>/tea/:name</td>
    <td>POST</td>
    <td>Ajoute un commentaire à un thé spécifique, en fonction du nom donne</td>
  </tr>
<tr>
    <td>deleteOneTea</td>
    <td>/tea/:name</td>
    <td>DELETE</td>
    <td>supprime un thé specifique en fonction du nom donné</td>
  </tr>
</table>


Importons notre modèle de thé que nous avons créé à partir de l'article précédent dans les controllers /tea.js pour commencer:

```
//import tea model
const Tea = require('../models/tea');
```
nouveauThé
Dans cette fonction, nous allons créer un nouvel objet thé en fournissant ses paires clé-valeur à req.body, puis l'enregistrer dans la base de données. Voici comment nous pouvons l'implémenter:


- 
Tout d'abord, nous devons nous assurer de ne pas POSTER accidentellement un thé avec un nom identique. Donc, notre fonction newTea devrait vérifier si le nom du nouveau thé de req.body.name existe déjà dans la base de données. Si c'est le cas, n'ajoutez pas ce thé.

- 
Si ce n'est pas le cas, créez un nouvel objet thé avec les paires clé-valeur de req.body.

- 
Enregistrez le nouvel objet thé dans la base de données.

Pour vérifier si un nom de thé existe déjà dans la base de données, nous pouvons utiliser une méthode de requête mangouste appelée findOne (), qui renvoie un objet de la base de données qui correspond à la condition fournie. Plus de détails peuvent être trouvés dans leur  [documentation](https://mongoosejs.com/docs/api.html#model_Model.findOne) .

```
//POST tea
const newTea = (req, res) => {
    //check if the tea name already exists in db
    Tea.findOne({name:req.body.name},(data)=>{

        //if tea not in db, add it
        if(data===null){
            //create a new tea object using the Tea model and req.body
            const newTea = new Tea({
                name:req.body.name,
                image: req.body.image, // placeholder for now
                description: req.body.description,
                keywords: req.body.keywords,
                origin: req.body.origin,
                brew_time: req.body.brew_time,
                temperature: req.body.temperature,
            })

            // save this object to database
            newTea.save((err, data)=>{
                if(err) return res.json({Error: err});
                return res.json(data);
            })
        //if tea is in db, return a message to inform it exists            
        }else{
            return res.json({message:"Tea already exists"});
        }
    })    
};
```

Test dans POSTman


1. 
Assurez-vous que la méthode est définie sur POST et que l'URL est correcte.

2. 
Cliquez sur l'onglet 'Body' pour accéder à la req.body.

3. 
Cliquez sur le bouton radio des données du formulaire ci-dessous.

4. 
Fournissez des paires clé-valeur de test pour le corps de demande `req.body`. Voir l'exemple ci-dessous.


![2.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1606046335743/pJ1I9hzOx.png)

Comme vous pouvez le voir, POSTman revient avec les données que nous avons publiées, ce qui signifie que notre fonction newTea fonctionne. Si vous enregistrez MongoDB, vous verrez qu'il est bien dans notre base de données.


![3.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1606046357487/R2qfEbSUz.png)

# getAllTea

Pour obtenir tout le thé, notre fonction récupérera et retournera toutes les données de notre base de données en utilisant la méthode find () intégrée à mongoose. Nous fournissons {} comme condition de correspondance afin que toutes les données soient renvoyées.

```
//GET all teas
const getAllTea = (req, res) => {
    Tea.find({}, (err, data)=>{
        if (err){
            return res.json({Error: err});
        }
        return res.json(data);
    })
};
```

# Test avec POSTman

Assurez-vous que nous avons défini la méthode sur GET cette fois et que l'URL reste la même qu'auparavant. Nous devrions mettre tout notre thé dans notre base de données. Pour le moment, il ne devrait renvoyer qu'un seul thé (thé noir) de notre demande newTea POST avant.


![4.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1606046529798/VJfUrhIJL.png)

J'ai ajouté un autre objet de thé (c'est-à-dire du thé vert) en utilisant newTea, et j'ai à nouveau fait la demande getAll. Maintenant, je devrais récupérer 2 objets de thé.


![5.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1606046542129/pOhZRY5Kw.png)

# deleteAllTea

Cette fonction supprimera toutes les données de la base de données. Nous pouvons simplement le faire avec deleteMany () et fournir le paramètre de condition avec {} puisque nous supprimons tout sans condition.

```
//DELETE teas
const deleteAllTea = (req, res) => {
    Tea.deleteMany({}, err => {
        if(err) {
          return res.json({message: "Complete delete failed"});
        }
        return res.json({message: "Complete delete successful"});
    })
};
```
# Tester avec POSTman

Nous définissons la méthode de demande sur DELETE et nous devrions voir le message de retour indiquant que toutes les données sont supprimées.


![6.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1606046656643/8-hhGFmpU.png)

Maintenant, si nous essayons d'obtenir tout notre thé. Nous devrions voir un tableau vide renvoyé. Ça marche! Toutes les données ont été supprimées.


![7.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1606046663060/-bqWceopb.png)

# getOneTea

Cette fonction récupérera et ne retournera qu'un seul thé, étant donné son nom comme condition correspondante. Nous pouvons utiliser `findOne()` pour cela. Comme mentionné précédemment à propos des objets de requête, le serveur récupérera l'objet thé avec le nom de `req.params.name`.

```
const getOneTea = (req, res) => {
    let name = req.params.name; //get the tea name

    //find the specific tea with that name
    Tea.findOne({name:name}, (err, data) => {
    if(err || !data) {
        return res.json({message: "Tea doesn't exist."});
    }
    else return res.json(data); //return the tea object if found
    });
};
```

# Tester avec POSTman

J'ai rajouté nos 2 thés que nous avons supprimés, donc notre base de données devrait maintenant contenir des objets de thé vert et noir. Nous définissons l'URL sur http://localhost:3000/tea/black%20tea où black%20tea (thé noir) est le nom du thé que nous voulons obtenir. On devrait nous rendre notre objet de thé noir.


![8.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1606046812464/jwQOdkFoH.png)

Si nous demandons un thé dont le nom n'est pas dans la base de données, comme "rouge", nous obtiendrons le message qu'il n'existe pas.


![9.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1606046823033/mV11jaGBO.png)

# newTeaComment

Dans cette fonction, le serveur POST un commentaire sur la propriété comments d'un objet tea spécifié, qui est un tableau. Il est implémenté comme suit:


- 
Pour savoir sur quel thé publier le commentaire, le serveur obtiendra le nom du thé à partir de req.params.name, tout comme getOneTea.

- 
Ensuite, il prend le commentaire fourni dans req.body.comment pour créer un objet de commentaire et pousser cet objet de commentaire vers la base de données, sous la propriété comment de l'objet de thé spécifié.

- 
Enregistrez les modifications

```
//POST 1 tea comment
const newComment = (req, res) => {
  let name = req.params.name; //get the tea to add the comment in
  let newComment = req.body.comment; //get the comment
  //create a comment object to push
  const comment = {
      text: newComment,
      date: new Date()
  }
  //find the tea object
  Tea.findOne({name:name}, (err, data) => {
      if(err || !data || !newComment) {
          return res.json({message: "Tea doesn't exist."});
      }
      else {
          //add comment to comments array of the tea object
          data.comments.push(comment);
          //save changes to db
          data.save(err => {
              if (err) { 
              return res.json({message: "Comment failed to add.", error:err});
              }
              return res.json(data);
          })  
      } 
  })
};
```

# Tester avec POSTman

Tout comme nous créons le test pour newTea, nous pouvons créer un test req.body.comment en fournissant un "commentaire" sous l'onglet Corps de POSTman. Cette fois, cliquez sur le bouton radio «brut» et assurez-vous que la liste déroulante est JSON. J'ai ajouté 2 commentaires et gardez l'url comme http://localhost:3000/tea/black% 20 pour ajouter des commentaires à l'objet thé noir.

Les données renvoyées montrent que notre objet thé noir a 2 commentaires sous sa propriété 'comments'. Ça marche!


![10.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1606046997427/mtpewfqfX.png)

# deleteOneTea

D'accord, notre dernière fonction de contrôleur! Cette fonction fonctionne de manière similaire à getOneTea, mais au lieu d'utiliser findOne, nous utilisons deleteOne pour supprimer le thé dont le nom correspond à req.params.name.

```
//DELETE 1 tea
const deleteOneTea = (req, res) => {
    let name = req.params.name; // get the name of tea to delete

    Tea.deleteOne({name:name}, (err, data) => {
    if(err || !data) {
        return res.json({message: "Tea doesn't exist."});
    }
    else return res.json({message: "Tea deleted."}); //deleted if found
    });
};
```

Tester avec POSTman
Nous définissons la méthode de requête sur DELETE et avons `` thé noir '' comme nom du thé à supprimer de la base de données en définissant l'URL sur http: // localhost: 3000 / tea / black% 20tea (toujours le même qu'avant) .


![11.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1606047068413/JW81MdPDJ.png)

Nous pouvons vérifier que la suppression fonctionne avec getAllTea, et voir que seul le thé vert est retourné car le thé noir a été supprimé.


![12.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1606047098381/-YtjMwDHU.png)

# Toutes mes félicitations!

Nous avons construit nos fonctions de contrôleur T-API! S'il réussit tous les tests avec POSTman, nous savons que cela fonctionne donc tout ce qu'il reste à faire est de prendre soin de la propriété image, car il ne s'agit pour l'instant que d'une chaîne factice. Le téléchargement d'un fichier image pour la propriété image de notre objet thé est un peu plus compliqué que de simplement fournir une chaîne comme pour 'nom'. Nous aborderons cela dans la partie suivante, puis nous sommes prêts à déployer notre API!

Merci d'avoir lu et s'il vous plaît laissez un like ou un partage si cela est utile. N'hésitez pas à poser des questions dans les commentaires ci-dessous.  cheer!