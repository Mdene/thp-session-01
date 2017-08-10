# Projet : Services et APIs
Les APIs c'est le bien. Au lieu de se faire chier à faire des scrappers ou à coder toi même ta base de données de films, il est très possible d'utiliser une API pour intéragir avec d'autres sites.

**Durée** : le reste de la journée

## Résumé
Tu vas faire deux sites :

- une mise en chauffe avec un site qui twitte à ta place
- un site qui va chercher des titres de films et te renvoyer le nom, la date de sortie, l'affiche, et le réalisateur

### 1. Twitter-bis
Ce projet est relativement rapide et te fais utiliser une gem dont nous nous sommes déjà servis. Le site est simple : il a une home avec un formulaire avec un _text-field_ à remplir, et une fois soumis, le site va tweeter ce qu'il y a marqué dans le formulaire.

#### A. Architecture
Elle sera plutôt simple : tu vas faire un service qui va initializer Twitter, et qui va envoyer un tweet, puis tu auras juste à lier le service à ton front.

#### B. Service
Tu te souviens comment créer un service ? 😉

Créé un service `SendTweet` qui va prendre un string à l'initializer, et qui va envoyer un tweet à partir de ce string.

Je te conseille de faire les méthodes suivantes :

- `initialize`, qui permet de faire passer le string en paramètre
- `log_in_to_twitter` qui permet de se login sur twitter avec tes credentials
- `send_tweet` qui envoie un tweet

Tu ne sais pas comment envoyer un tweet ? Ça tombe bien moi non plus ! Heureusement que la [doc existe](https://github.com/sferik/twitter) 🙃

Pour tester ton twitteur, tu peux le faire dans la console : lance (ou relance là, car il faut toujours la relancer pour que ça marche) et : `SendTweet.new("Bonjour monde!").perform`.

#### C. Le front
Easy, fais un controller `Home` avec une méthode `index`. La méthode `index` sera la root de ton application. Dans le view index, mets-y un formulaire qui a juste un _text-field_ et de quoi le soumettre.

La méthode `index` va récupérer le text-field de ton formulaire et le passer dans le service `SendTweet`. Tu n'as plus qu'à checker sur Tweeter et à toi la gloire 😎


### 2. Movie searcher
Cet exercice sera un peu moins pas à pas, car un skill très important pour les devs est d'aller lire les docs et tester plein de trucs.

Tu dois faire un site qui va te demander sur la page d'accueil de rentrer un nom de film en recherche. Si la recherche renvoie un ou plusieurs films, le site doit afficher les 20 premiers en mentionnant :

- le nom du film
- la date de sortie
- le réalisateur
- une image s'il y en a une

Si la recherche rentre broucouille, le site va renvoyer un truc du genre "yo la recherche n'a rien donné"

#### 1. Architecture
Le site aura un service `SearchMovie` qui prendra un string en paramètre, et qui va renvoyer une array qui contient plein de movies.
Cette classe `SearchMovie` sera liée à un controller `Movies` et une méthode `search`. La view `search.html.erb` devra afficher les résultats de la recherche.

#### 2. API ?
La meilleure API pour rechercher des films est [TheMovieDB](https://developers.themoviedb.org/4/getting-started). Cette API a même une [gem](https://github.com/ahmetabdi/themoviedb) qui fait tout le travail pour toi. Elle est pas belle la vie ? 😎

