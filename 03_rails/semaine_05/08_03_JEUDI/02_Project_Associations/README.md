# Associations - le projet
## Récap
Ce projet te fera jouer avec de la manipulation d'associations entre utilisateurs.

## Durée estimée
- Le reste de la journée

## Projet : The_Gossip_Project, Part.2 : La Revanche des Gossips
Tu es chaud des gossips, we know it 😎

Dans ce projet, tu vas faire une version de The_Gossip_Project qui a plus de gueule. Il y aura deux models : le model Corsair, et le model Gossip. Un corsair peut écrire plusieurs gossips, mais un gossip n'a qu'un seul auteur.

La homepage du Gossip Project sera la liste de tous les gossips. Sur le header, tu pourras trouver un lien pour créer un gossip.

Le formulaire de création de gossip aura 2 champs :

- un champ `corsair_username`
- un champ `content`

Bien entendu, si quelqu'un rentre un gossip d'un corsair avec un `corsair_username` qui n'existe pas dans la base, le formulaire devrai renvoyer une erreur.

### Les models
Tu vas créer deux models :

- Corsair, qui a comme attribut
  - `username`, qui est un string, et qui a une présence obligatoire
- Gossips, qui a comme attribut
  - `content`, qui est un string, et qui a une présence obligatoire

Les deux model sont liés avec une relation `has_many / belongs_to`. Ainsi `Corsair.first.gossips` devra retourner une array, et `Gossip.first.corsair` devra retourner un objet corsair.

Je t'invite à checker [la doc](http://guides.rubyonrails.org/association_basics.html) pour savoir comment faire cette relation dans Rails. Pour la tester, tu peux lancer la console, créer des Corsair et Gossips à la volée (n'oublie pas de faire `.save` sinon les données ne sont pas sauvegardées), et de voir ce que `Corsair.first.gossips` et `Gossip.first.corsair` te renvoient.

Aussi, s'il est possible d'avoir un corsair qui n'a pas publié de gossips, un gossip ne peut pas ne pas avoir d'auteur.


### Les views
Pour cette version un peu simple du site, nous aurons deux views : la home, qui affiche tous les gossips, et le formulaire de création d'un gossip

#### 1. La maison
La page d'accueil du site doit afficher tous les gossips. Si tu as bien suivi, c'est la méthode `index` du `gossips_controller` 😉

Juste avant la liste des Gossips, je t'invite à mettre un lien pour inviter les utilisateurs à créer leurs gossips. Un header peut faire l'affaire par exemple !

#### 2. Création de gossips
Le formulaire de création de Gossips doit demander deux paramètres :

- l'auteur du gossip
- le contenu du gossip

Hum, ça doit être des méthodes `new` / `create` du `gossips_controller` ça ! Mais alors, comment vérifier que l'auteur du gossip existe bien 🤔 C'est bien là l'intérêt des bases de données relationnelles, on peut écrire un truc du genre :

```ruby
if Corsair.find_by username: LES_PARAMS_DES_FAMILLES
	# C'est de la 💣 bébé
else
	# aïe error 😨
end
```

Jouer avec des formulaires et des params est l'un des parties les plus intéressantes de Rails donc je te laisse trouver ton bonheur ❤️

### J'ai fini, quoi d'autre ?
Tu peux faire un formulaire de création de corsair, pimper un peu le site !

Aussi, tu peux compléter ton fichier `seeds.rb`, mettre plein de Gossips, et puis utiliser la gem de pagination pour n'afficher que les 30 premiers.

Enfin, tu peux classer les gossips pour que les derniers créés apparaissent en premier dans l'index.

## Balance-moi du lourd 📬
Si tu es chaud, tu peux faire le `Project 2: Private Events` de [The Odin Project](https://www.theodinproject.com/courses/ruby-on-rails/lessons/associations).