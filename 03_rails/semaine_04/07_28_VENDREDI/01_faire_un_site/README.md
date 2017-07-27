# Faire un site pas trop dégueu
Dans ce projet, tu vas refaire un site un peu plus complexe que ce que tu as fait jusqu'à présent. Ce sera l'occasion de mettre en pratique les notions vues cette semaine.

## Projet validant
Le projet est validant. Comme la semaine dernière, nous ne prendrons pas les projets avec un seul contributeur. Voici [le beau formulaire de complétion du projet](https://goo.gl/forms/TKYV1QfskCO73Vc62)

## Récap
The_Hacking_Project c'est des gens très sympas, il faut donc faire un site qui recense les corsaires. Ce site permettrait à qui le veut de pouvoir voir une liste de corsaires avec : 

- leur prénom
- leur age
- s'ils sont plutôt Kebab ou Hummus

Puis en allant sur la page d'édition des corsaires, il est possible de mettre à jour une petite bio, d'y renseigner leur pseudo slack et/ou Github, et/ou de supprimer le corsaire de la base. Bien entendu, nous allons faire en sorte que les paramêtres renseignés ressemblent à quelque chose, et afficher des messages d'erreur si un utilisateur rentre un prénom vide en prénom par exemple.

Puis parce que l'on veut la terre profiter de notre super site, nous allons le mettre en ligne sur Heroku 😻

# Le site, pas à pas
## Les bases
Pour bien débuter, il faut faire nos bases :

- crée donc un projet rails appelé thp-corsaires
- il va te falloir faire un `bundle install --without production` du Gemfile, mais il faut un Gemfile compatible Heroku. Voici un joli [exemple](https://github.com/TheHackingProject/thp-session-01/blob/master/03_rails/semaine_04/07_28_VENDREDI/01_faire_un_site/files/Gemfile).
 - Tu veux faire `bundle install` sans le `--without production` et PostGreSQL te balance des gros bugs de partout ? On peut solver ça en installant les [biliothèques de développement de PostGreSQL](https://stackoverflow.com/a/34399917)
- génère un controller static_pages avec une méthode : home
- home doit être sur root, modifie le fichier _routes.rb_
- lance les serveurs `rails server`, puis va sur [http://localhost:3000/](http://localhost:3000/) pour checker que tout va bien

Maintenant que l'on a un site qui marche, nous allons le push sur heroku, pour éviter les mauvaises surprises plus tard

- initialise git, crée un repo Github et ajoute ce repo en origin
- `heroku create`
- `git push heroku master`
- à toi la gloire !

⚠️ **Meilleures pratiques** ⚠️ : nous te conseillons de faire des commit à chaque sous-chapitre de ce tutoriel. Ainsi, si jamais tu veux tester quelque chose, au lieu de commenter la section, tu peux faire `git reset --hard` pour revenir au commit précédent. Très pratique quand tu as un truc qui merde 💩

## Un peu de mise en forme
Pour que notre site ressemble à quelque chose, nous allons faire un peu de mise en forme sur notre page principale.
### Installation de Bootstrap
Pour installer Bootstrap, il faut mettre Bootstrap dans le Gemfile :
```ruby
gem 'bootstrap-sass', '3.3.7'
```
Mettre à jour le bundle avec un petit `bundle install --without production`
Puis renseigner les lignes suivantes dans le fichier _app/assets/stylesheets/custom.scss_
```sass
@import "bootstrap-sprockets";
@import "bootstrap";
```
Enfin, relancer le serveur. Bootstrap devrait être installé.

### Un header
Un header pour tout le site c'est bien. Comme tu n'es pas (encore) un expert de Bootstrap, nous n'allons pas réinventer la roue, et reprendre le header du Rails Tutorial. Créé une partial `_header.html.erb` dans ton dossier `app/views/layouts` puis fais appel à elle dans ton fichier `app/views/layouts/application/html.erb`.

Voici un exemple de header que tu peux reprendre dans ton fichier `_header.html.erb` :
```erb
<header class="navbar navbar-fixed-top navbar-inverse">
  <div class="container">
    <nav>
      <ul class="nav navbar-nav navbar-right">
        <li><%= link_to "Accueil",   '#' %></li>
        <li><%= link_to "Index des corsaires",   '#' %></li>
        <li><%= link_to "Nouveau corsaire", '#' %></li>
      </ul>
    </nav>
  </div>
</header>
```

### Un body
Pour notre page d'accueil idem : nous n'allons pas réinventer la roue. Dans ton fichier `home.html.erb` colle le code suivant :
```erb
<div class="center jumbotron">
  <h1>Bienvenue !</h1>
  <h3>
    Ici, tu peux retrouver les corsaires 🎓
  </h3>
  <%= link_to "Enregistre-toi !", '#', class: "btn btn-lg btn-primary" %>
</div>
```
Tu peux ajouter du CSS dans le fichier `custom.scss` si tu veux mais ce n'est pas l'objet de ce projet : n'y passe pas trop de temps. Voici quand même une ligne à rentrer pour éviter que le header ne recouvre le début de ta page :
```scss
body {
	margin-top: 50px;
}
```

## Le CRUD basique
Maintenant que l'on a une base squelettique, on va pouvoir commencer à travailler dessus. Et rien de tel qu'un petit CRUD des families pour cela 💁
### Model - Controller
Tu vas devoir générer un model corsair. Les corsaires ont :

- un `first_name`, qui est un `string`
- un `age`, qui est un `integer`
- un `likeness` qui est un `string` (et sera soit égal à "kebab", soit égal à "hummus")
- un `bio` qui est un `string`
- un `slack_handle` qui est un `string`
- un `github_handle` qui est un `string`

Joli modèle ! Nous allons revenir sur les validations plus tard. C'est best practice de faire le model bien fait avant, mais le but est de construire un squelette progressif pour que tu puisses voir tes avancées.

Maintenant génère un controller avec toutes les méthodes de base.

### CRUD
Idem, nous allons construire un CRUD de base afin de pouvoir itérer dessus facilement. Voici les specs du CRUD :

#### 1. New
Quand un corsaire s'inscrit, il doit renseigner son `first_name`, et son `age`.

#### 2. Show
Le view show doit montrer le prénom du corsaire en `<h1>`, et son age en plus petit. Il doit y avoir un lien pour éditer le corsaire à partir de show.

#### 3. Edit
À partir de la view edit, on peut éditer le `age` du corsaire, ainsi que son `first_name`. On peut supprimer un corsaire à partir de la view edit.

#### 4. Index
L'index doit recenser tous les corsaires. Pour chaque corsaire, il doit afficher :

- Son prénom
- Son âge
- Un lien vers la view show

En fin de liste des corsaires, l'index doit proposer un lien pour inscrire un corsaire.

## Model pour les BGs
Tu viens de faire un magnifique CRUD, tu as une base pour maintenant faire les tâches plus funky 💋

Nous allons valider les attributs, afin d'éviter que nos corsaires rentrent des truc foireux :

- le `first_name` et le `age` sont obligatoires
- le `first_name` ne doit pas dépasser 20 caractères
- le `age` doit être compris entre 15 et 120 (au délà, on estime que c'est une erreur)
- le `slack_handle` et le `github_handle` ne doivent pas contenir d'espace

Afin de tester la validité de tes models, tu peux vérifier dans la console en appelant la méthode `.valid?` sur les corsaires que tu créés.

## Entrer plus de paramètres dans la view edit
Maintenant nous allons pouvoir changer plus d'attributs dans la view edit. Change le formulaire et les controller dans edit / update pour que l'on puisse prendre en compte les attributs suivants :

- `bio`
- `slack_handle`
- `github_handle`

Une fois ceci fait, tu peux afficher ces attributs dans la view show.

### if show
Question : si le corsaire n'a pas (encore) défini son `slack_handle`, c'est pas très cool d'afficher dans la vue show une phrase du genre :
```
Voici le pseudo slack de Jean-Raoul : nil
```
Pour remédier à ceci, on peut faire des if en erb, une fonction bien pratique :
```erb
<% if @corsair.slack_handle != nil %>
	<p>Voici le pseudo Slack de <%=@corsair.first_name%> : <%=@corsair.slack_handle%></p>
<% else %>
	<p><%=@corsair.first_name%> n'a pas encore renseigné son pseudo Slack !</p>
<% end %>
```

## Flash
C'est super bien d'afficher des messages d'erreur pour nos corsaires quand ils se plantent en remplissant le formulaire. Faisons-en donc.

### Create
Rentre d'abord le flash de success. Pour ceci, je t'invite à regarder le schéma 7.29 du Rails Tutorial pour savoir comment l'insérer dans le controller.

Puis avec le 7.31, tu peux voir comment le mettre dans notre view, ce qui va automatiquement insérer les flash en cas d'erreur. Pense bien à `render new` si `@corsair.save` ne marche pas.

### Update
Pour le flash de la méthode, il te faudra l'adapter malinement à partir de new et create.

## Kebab, or not Kebab
On l'avait un peu délaissé jusqu'à présent, mais maintenant on va s'attaquer à ces fameux kebabs. Dans le formulaire d'édition, mets un radio_button qui va prendre en compte le paramètre pour savoir si notre corsaire préfère les kebabs, ou le hummus.

Si le corsaire coche la case Kebab, son paramètre `likeness` doit être `kebab` ;  si le corsaire coche la case Hummus, son paramètre `likeness` doit être `hummus`

[La doc renseigne](http://guides.rubyonrails.org/form_helpers.html#helpers-for-generating-form-elements) comment faire des radios_buttons.

Bien entendu, change la view show pour montrer si le corsaire préfère les kebabs, ou le hummus.

## En ligne
Maintenant que tu as un truc qui ressemble à quelque chose, mettons-le en ligne !
```shell
$ git push heroku master
$ heroku run rails db:migrate
```
Bravo ! Il ne te reste plus qu'à remplir [le formulaire](https://goo.gl/forms/TKYV1QfskCO73Vc62).