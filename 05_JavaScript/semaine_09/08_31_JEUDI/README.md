# Jeudi
Aujourd'hui tu vas voir une techno très intéressante qui s'appelle l'AJAX. L'AJAX permet de faire des appel à ta base de données sans avoir besoin de recharger une nouvelle page.

Le projet est validant. [Voici le formulaire](https://goo.gl/forms/oHTVuqf5sMAiBEkg2)

## Ressources

- Tutorials Point ont fait [une très bonne introduction](https://www.tutorialspoint.com/ruby-on-rails/rails-and-ajax.htmRuby ) à AJAX que nous t'invitons à suivre
- LaunchSchool ont fait un [super tutoriel](https://launchschool.com/blog/the-detailed-guide-on-how-ajax-works-with-ruby-on-rails) pour apprendre les bases de l'AJAX. Nous t'invitons à le suivre
- RubyPlus ont fait [un autre tutorial](https://rubyplus.com/articles/4211-Using-Ajax-and-jQuery-in-Rails-5-Apps) sur l'AJAX. Tu n'es pas obligé de le suivre, mais nous t'invitons à au moins le lire


## Projet
Pour ce projet, nous allons te demander de faire un _Email Viewer_, c'est à dire une page `index` dans laquelle il y aura 2 colonnes :

- une colonne avec la liste des emails
- une colonne qui affiche le contenu de l'email sur lequel tu viens de cliquer

### Rails
Nous allons te demander de faire ceci dans une app rails `email-viewer`, que je t'invite à créer. Ensuite, créé un model `email`, avec comme attribut `object`, et `body` (on ne va pas trop se prendre la tête sur l'app Rails, le but est de te faire jouer avec AJAX après tout 😇). Mets dans ta base quelques emails.

Root ton projet à `email#index`, et commence à faire ton controller et ta view.

### Colonne liste
La colonne de la liste devra afficher juste l'objet de tous les emails.

### Colonne contenu
La colonne contenu devra ne rien afficher au loading de la page. Quand on clique sur un email dans la colonne liste, la colonne contenu devra afficher : 

- L'objet de l'email, en gros
- Le corps de l'email, en taille normale
- un lien pour supprimer l'email


La suppression d'email sera faite elle aussi avec de l'AJAX.

### Un peu plus d'AJAX
_Cette partie n'est pas obligatoire_
Pour t'entrainer encore plus, nous allons te demander de marquer les emails non lus. C'est à dire qu'un email non lu aura une marque spéciale dans la colonne liste (Gmail affiche le sujet en gras, Outlook change le fond en jaune). Libre à toi de choisir ce qui te semble le plus sympa (`background-color: yellow` si tu es en panne d'inspiration).

Bien entendu, quand un user clique sur un email non lu pour l'afficher, ce dernier passera lu, et la marque spéciale dans la colonne liste disparaitra.

Hint : ajouter un attribut booléen `read` dans ton model user t'aidera 😉

### Et voilà !
Tu n'as plus qu'à soumettre le projet via le formulaire : [par ici le lien](https://goo.gl/forms/oHTVuqf5sMAiBEkg2)