# Comment envoyer un e-mail en utilisant JS sans backend ?

Dans le monde d'aujourd'hui, la plupart des entreprises ont leur propre site Web. Dans certains cas, comme un formulaire soumis par l'utilisateur, un formulaire de contact, etc., nous pouvons avoir besoin d'envoyer un e-mail à partir de notre site Web et chaque site Web que nous développons n'a pas de backend dédié. Dans cet article nous allon ensemble voir comment envoyer un email en utilisant **SmtpJS et vanilla javascript.**

En ce qui concerne SmtpJS, il s'agit d'un script sans licence et sans restriction d'utilisation. Vous pouvez l'utiliser pour tout projet commercial ou non-commercial. Mais, si vous recevez un rapport de spam, votre compte sera bloqué.

## Assez d'introduction n'est ce pas ?. De quoi avez-vous besoin avant de commencer à coder ?

- Hôte SMTP : [smtp.gmail.com](smtp.gmail.com) (pour d'autres clients de messagerie, ce sera différent)

- Nom d'utilisateur SMTP : Votre adresse e-mail à partir de laquelle vous souhaitez envoyer des e-mails.

- Mot de passe SMTP : Votre mot de passe de messagerie

- Port SMTP : 587 (pour d'autres clients de messagerie, cela peut varier)
Maintenant, commençons le code.

Importez le script en utilisant le CDN ou en téléchargeant le fichier du script dans votre page index.html.


```
<script src="https://smtpjs.com/v3/smtp.js"></script>
```


- 
Ajoutez un bouton dans votre formulaire qui déclenchera la fonction sendEmail.


```
<input type = "button" onClick="sendEmail()"/>
```



- 
Créez une fonction qui envoie l'e-mail. Si vous souhaitez envoyer l'e-mail à plusieurs adresses e-mail, vous pouvez utiliser un tableau d'e-mails de destination dans la propriété "To".


```
<script type="text/javascript">
function sendEmail() {
Email.send({
    Host : "smtp.yourisp.com",
    Username : "username",
    Password : "password",
    To : 'them@website.com',
    From : "you@isp.com",
    Subject : "ceci est l'objet",
    Body : "Et ceci est le message"
}).then(
  message => alert(message)
);
}
</script>
```



- 
Si vous souhaitez envoyer des pièces jointes, vous pouvez utiliser la propriété "attachments".


```
<script type="text/javascript">
function sendEmail() {
Email.send({
    Host : "smtp.yourisp.com",
    Username : "username",
    Password : "password",
    To : 'them@website.com',
    From : "you@isp.com",
    Subject : "Ceci est un objet",
    Body : "Et ceci est le message"
    Attachments : [
    {
        name : "xyz.png",
        path : "https://xyz.com/xyz.png"
    }]
}).then(
  message => alert(message)
);
}
</script>
```


- 
Si vous craignez de fournir les informations d'identification SMTP dans le code, vous pouvez utiliser la fonction Encrypt your SMTP Credentials fournie sur le site officiel de [SmtpJS](https://smtpjs.com/).


![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1665066368017/VwH3eELAD.png align="left")


- Après avoir obtenu votre SecureToken, modifiez la fonction en ajoutant la propriété "SecureToken".


```
<script type="text/javascript">
function sendEmail() {
Email.send({
    SecureToken : "C973D7AD-F097-4B95-91F4-40ABC5567812",
    To : 'them@website.com',
    From : "you@isp.com",
    Subject : "Ceci est un objet",
    Body : "Et ceci est un message"
    Attachments : [
    {
        name : "xyz.png",
        path : "https://xyz.com/xyz.png"
    }]
}).then(
  message => alert(message)
);
}
</script>
```

- Vous avez terminé avec le code. Maintenant, exécutez le code et cliquez sur le bouton pour envoyer l'email. Vous verrez une alerte avec le message "OK" en cas de succès ou un message d'erreur en cas d'échec.

## Conclusion

Ainsi, en utilisant SmtpJS vous pouvez envoyer des emails sans aucun backend. Cela peut être utilisé dans n'importe quel framework ou bibliothèque javascript comme Angular, React etc.

Merci et n'hésitez pas à partager autour de vous.





