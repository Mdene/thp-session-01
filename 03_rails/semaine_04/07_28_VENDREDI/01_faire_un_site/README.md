# Faire un site pas trop dégueu
Dans ce projet, tu vas refaire un site un peu plus complexe que ce que tu as fait jusqu'à présent. Ce sera l'occasion de mettre en pratique lesn otions vues cette semaine.

## Projet validant
Le projet est validant.

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

- crée donc un nes projet rails appelé thp-corsaires
- il va te falloir faire un `bundle install` du Gemfile, mais il faut un Gemfile compatible Heroku. Voici un joli [exemple](/files/Gemfile)


# Windows does not include zoneinfo files, so bundle the tzinfo-data gem
gem 'tzinfo-data', platforms: [:mingw, :mswin, :x64_mingw, :jruby]
```
Un site avec un modèle :

- Crud entier
- validation
- jouer avec les formulaires
- installer bootstrap
- push sur heroku
- faire du test


Site qui recense les corsaires de THP. Ils vont y mettre, prénom, pseudo_slack, age (avec validation).
Il peuvent ajouter une phrase de présentation dans l'édition du profil. Ils peuvent delete à partir du profil. 
La home doit souhaiter la bienvenue, puis une navbar mentionne : ajouter un user, home, liste des users
On peut accéder à la liste des users à partir de la home
On peut ajouter un user à partir de la liste des users
faire le flash en cas d'inscription mauvaise
à la fin, ajouter une page : possibilité d'inscrire plusieurs users à la fois. Avec un préformulaire.

