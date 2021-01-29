## Gérer l’état de son application React

Depuis la nuit des temps, chaque homme sur terre, plus ou moins, a été confronté à cette même problématique : gérer l’état de son application React. Au début ça n’a pas vraiment été un problème, du moins jusqu’à la sortie de React en mai 2013. Ensuite la question a commencé à vraiment se poser.
Dans un premier temps, React fournissait une méthode très simple de gestion d’état avec le setState. Très vite le partage et la transmission des états entre les composants sont devenus problématiques. Et c’est pour répondre à cette problématique que des membres actifs de la communauté ont développé des outils de gestion d’état global à une application : Redux, Mobx, etc. C’est là que les dérives ont commencé et que de petites applications se retrouvaient à embarquer la terre entière afin de gérer l’état d’un simple champ texte.
Aujourd’hui en 2020, nous avons tout un tas de choses simples, comme des patterns couplés simplement à l’API native de React, qui permettent de gérer convenablement et simplement les états dans une application.

## Un état de composition

Dans un premier temps, pour gérer convenablement les états, il faut organiser son application de manière judicieuse. Pour éviter d’avoir un sac de noeuds global à une application, il faut découper celle ci. En utilisant un subtil mélange de  [DDD](https://css-tricks.com/domain-driven-design-with-react/?utm_campaign=React%20Ninjas%20Newsletter&utm_medium=email&utm_source=Revue%20newsletter)  et de séparation en composants, nous pouvons organiser sereinement une application.


> The software development approach called Domain-Driven Design, or DDD, exists to help us more readily succeed at achieving high-quality software model designs. When implemented correctly, DDD helps us reach the point where **our design is exactly how the software works.**.

L’idée du DDD est de regrouper le code par domaine fonctionnel et de le faire grandir au fur et à mesure de l’évolution de l’application. Grace à cela, et de façon naturelle, nous allons créer des clusters d’état. Il n’y aura plus qu’à les matérialiser dans le composant.
Il faut ensuite découper au fur et à mesure des besoins. Par exemple, lorsque le composant est trop gros, ou que vous rencontrez des problèmes de performance, ou encore qu’une partie est réutilisable, c’est qu’il est tant de découper. Et pas avant.

# Consommer local, privilégier le circuit court

Une fois que nous travaillons sur un composant, une simple question suffit pour noter s’il est nécessaire d’y ajouter un état.


> If you’re not sure whether some state is local, ask yourself: “If this component was rendered twice, should this interaction reflect in the other copy?” Whenever the answer is “no”, you found some local state.

Dan Abramov indique dans son super article  [Writing Resilient Components](https://overreacted.io/writing-resilient-components/)  qu’il suffit de se poser la question “**si le composant était rendu plusieurs fois faudrait-il que l’interaction soit reflétée sur les deux composants ?”**, alors si la réponse est non c’est que vous avez trouvé un état local.

Et pour cela rien de plus simple :

```
function Example() {
  const [value, setValue] = useState('');
  const updateInput = event => setValue(event.target.value);
  return (
    <div>
      <p>Votre nom : </p>
      <input
          value={username}
          onChange={updateInput}
          name="username"
          type="text"
        />
    </div>
  );
}
```
Avec cela vous allez pouvoir déjà répondre à un très grand nombre de cas. Ce sera souvent des petits états, tels que la valeur d’un input, l’état d’une popin ou les données d’un tableau. Cependant ces valeurs peuvent avoir une utilité pour d’autres composants.

# Prendre du recul.

Dans le cas d’un champ de saisie, il est fort probable qu’il fasse partie d’un formulaire, et de ce fait, il sera sans doute dans un ensemble de données qui seront transférées ou traitées. Dans ce cas, l’ensemble des sous composants du formulaire, avec ou sans états, recevront l’état du formulaire et les fonctions nécessaires pour mettre à jour ces dernières. Dans une connexion directe, la transmission de props est clairement la plus adaptée.

```
LoginFormContainer = () => {
  const [username, setUsername] = useState('');
  const [password, setPassword] = useState('');

  const submitForm = login(username, password);
  const handleChange = ({name, value}) => {
    if(name === "useName"){
      setUsername(value);
    } else {
      setPassword(value);
    }
  }
  
  return (
    <form onSubmit={submitForm}>
      <userInputs username={userName} password={password} onChange={handleChange}
      <br />
      <button>Submit</button>
    </form>
  );
}
```

> Prop drilling at its most basic level is simply explicitly passing values throughout the view of your application.

Kent C Dodds, a écrit un  [article très complet](https://kentcdodds.com/blog/prop-drilling/)  sur le sujet.

La transmission de props est la plus naturelle et la plus rapide à effectuer, mais également la plus simple. Elle possède également la qualité d’être la plus explicite et donc de simplifier la lecture de code.

Il y aura, cependant, un moment de rupture, ou les props seront transmises de père en fils sur trop de générations et où ça va devenir un vrai cauchemar. A ce moment là, on passe à la phase suivante.

# Entrez dans la matrice

Ici commencent les choses plus sérieuses. Avant de passer au Framework de gestion d’état, nous pouvons utiliser l’API Context.
Couplée avec les Hooks, et un petit pattern simple, nous allons pouvoir couvrir un très grand nombre de cas.

```
//creation d'un provider.
export const UserContext = createContext(null);	

const UserProvider = ({ children }) => {
  const [user, setUser] = React.useState({});
  const [error, setError] = React.useState(null);
  const login = async (login, password) => {
    const { status, data } = await axios('/login', { login, password });
    if (status === 200) {
      setUser(data);
    } else {
      setError('Connexion impossible');
    }
  };
  return <UserContext.Provider value={{ user, error, login }}>{children}</UserContext.Provider>;
};
```
```
//utilisation du provider

const LoginFormContainer = () => {
  const [username, setUsername] = React.useState('');
  const [password, setPassword] = React.useState('');
  const { login } = React.useContext(UserContext);

  const submitForm = login(username, password);
  const handleChange = ({ name, value }) => {
    if (name === 'useName') {
      setUsername(value);
    } else {
      setPassword(value);
    }
  };

  return (
    <div>
      <User user={user} />
      <errorMessage message={message} />
      <form onSubmit={submitForm}>
        <userInputs username={userName} password={password} onChange={handleChange} />
        <br />
        <button>Submit</button>
      </form>
    </div>
  );
};

const User = () => {
  const { user } = React.useContext(UserContext);
  return user && <User name={user.name} profil={user.profil} />;
};

const ErrorMessage = () => {
  const { message } = React.useContext(UserContext);
  return message && <Alert message={message} title="Une erreur est survenue" />;
};
```

Le but ici est d’extraire la grande majorité de la gestion des états, mais également la logique de tout un groupe de composants. Ici, les atomes et molécules de l’organisme vont pouvoir importer les méthodes et propriétés dont il a besoin pour fonctionner dans le petit écosystème. Ce qui aura pour effet bénéfique de simplifier leur code et donc leur lecture.

Cependant, attention, les autres règles s’appliquent toujours ! Il faut garder les états au plus près de leur utilisation. Si vous mettez un provider en place, ce n’est pas une raison pour tout y mettre. On continue avec des états locaux, et des transmissions de propriétés quand cela est convenable.

De plus il faut rester vigilant quant à ce qui est exposé par le provider.
Enfin, les providers se gèrent comme des composants : on commence simple et on applique du code splitting au besoin. Il faut se souvenir que lorsqu’on modifie une des composante du provider, l’ensemble des consommateurs seront rerendus.

```
// une fois decoupe
const UserPage = () => (
  <UserProvider>
    <ErrorMessage />
    <UserInfo />
    <LoginFormContainer />
  </UserProvider>
);
```
## C’est pas ma guerre.

Bien que cet ensemble permette de couvrir un très grand nombre de cas, les frameworks de gestion d’état ont quand même une utilité. Je ne vais pas trop en parler ici, car ce n’était pas le but de mon article. Cependant vous pourrez en trouver une utilité pour :


- 
L’utilisation des middlewares

- 
Une gestion plus optimisée

- 
Des outils plus avancés (pour le store, les dev tools, etc)
etc.

Globalement si vous ne savez pas pour quelle raison vous devriez utiliser de tels framework, c’est que vous ne devez pas. De même on ne met pas un tel outil sur un projet simple en se basant sur ce qu’il pourrait devenir. Il faut se baser sur l’instant présent. Restons simple.

# Bref

Tout ça pour dire, vous avez un bon nombre de clés en main. Maintenant le principe fondamental est de garder au plus près votre état du code qui l’utilise. Pour écrire cet article je me suis beaucoup basé sur des conseils de Kent C Dodds, dont je vous invite à suivre le  [blog](https://kentcdodds.com/blog/) . Je lui laisse donc le mot de la fin.


> Keep state as local as possible and use context only when prop drilling really becomes a problem. Doing things this way will make it easier for you to maintain state interactions.

Merci d'avoir lu.. je suis disponible sur  [twitter ](https://twitter.com/AdechinaAlao) . Vous pouvez me laissez des commentaires et questions.. je vous repondrai dans moins de 24 heures.