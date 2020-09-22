## Secret Git : faites un commit avec une date passée.


Vous avez toujours voulu effectuer un `commit`  dans un repo git avec une date passée? Voici comment procéder.

Si vous travaillez sur un projet et avez manqué un commit hier ou si vous avez accompli la tâche mais que GitHub pour Windows vous a renfloué.. Eh bien, ce petit hack peut résoudre votre problème.

Pré-étape. Récupérez toutes les données du référentiel distant `remote repositery`vers le référentiel local `local repositery`.

Pour la même chose, nous utilisons les commutateurs `--amend` et `--date`. La commande exacte est la suivante:

`$ git commit --amend --date="YYYY-MM-DD HH:MM:SS"`

Simple, n'est-ce pas!

Cela devrait résoudre votre problème . Si vous avez des questions ou des suggestions, veuillez me contacter dans la section Commentaires ci-dessous.

