# Projet : La production
Ce projet vise à te faire un peu transpirer sur la mise en production de tes sites en utilisant l'asset pipeline. Tu devras faire des applications utilisant l'asset pipeline et arriver à les push sur Heroku

**Durée** : le reste de la journée

## Résumé
Voici une liste des sites que tu vas devoir push sur Heroku :

- un site qui utilise du CSS
- un site qui a des images
- un site qui utilise du JavaScript
- un site qui utilise jQuery
- un site qui utilise Bootstrap

### 1. Hello CSS
Tu te souviens de ton projet Google ? Voici ta mission : créé une application `rails-google` qui affiche en page d'accueil ce que tu avais fait lors de ton projet Google. Pas besoin d'y passer trois plombes sur le CSS : on en fera plein la semaine prochaine et là le but de l'exercice est de s'entraîner à push sur Heroku plein de projets différents. Si jamais tu as tout supprimé, tu peux reprendre le CSS d'un autre corsaire. Ne mets pas les images pour le moment.

Une fois que tu as un HTML / CSS de prêt, push le projet sur Heroku.

### 2. Des images ?
Google sans son logo, c'est pas très BG. Met l'image dans l'asset pipeline et arrive à push le projet sur Heroku.

### 3. Bonjour JavaScript
Tu te souviens de la version JavaScript du projet Google ? Ta mission : créé une application `rails-js` qui reprend ton projet avec le JavaScript.

Puis tu vas devoir push le projet sur Heroku. Idem, si tu n'as plus ce projet, essaie juste avec un `alert("kikou JavaScript marche !)`. Le but est d'arriver à push sur Heroku plein de projets différents.

### 4. jQuery maintenant
Tu te souviens du projet de jQuery ? Créé une application `rails-jquery` qui doit inclure du HTML, du CSS, du JavaScript, et du jQuery. Puis push le projet sur Heroku.

### 5. Bootstrap
#### 5.1. Bootstrap avec JS
On va passer aux choses sérieuses. Fais un nouveau projet `rails-bootstrap`, et insères-y Bootstrap. Maintenant, tu dois arriver à mettre en ligne un site qui contient Bootstrap, ainsi que la partie JavaScript de Bootstrap. 

Par exemple tu dois avoir en ligne [cette navbar](http://getbootstrap.com/components/#navbar-default) mentionnée dans la doc.

#### 5.2 Custom CSS et JavaScript
Maintenant, tu vas ajouter un peu de JavaScript et de CSS que tu auras défini. Idem, des trucs simples comme `background-color: black;` et `alert("yeah JS marche")` feront l'affaire. Le but est d'arriver à push le site sur Heroku.

### 6. Emails
Si tu est arrivé jusqu'ici, tu auras bien appris sur des push d'Heroku. Maintenant nous allons faire un truc sympa : nous allons pimper ton projet Devise et arriver à faire les emails en production.

Si tu n'as pas commencé / fini le projet de hier, c'est une excellente occasion pour se pencher dessus : Devise est très importante.

Si tu es dans les temps, ta mission est d'arriver à faire en sorte que le site passe en production, et que tu arrives à envoyer des emails quand l'utilisateur mentionne "J'ai oublié mon mot de passe". Tu peux utiliser SendGrid ; j'ai trouvé [ce tutoriel](https://2017doneright.com/email-verification-devise-in-rails-using-sendgrid-gmail-and-heroku-a0ca930c5373) qui a l'air très décent 😊