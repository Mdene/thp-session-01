# Members Only - The_Hacking_Project version
## Récap
Le projet de The Odin Project n'était pas ouf ouf car compliqué. Voici donc une version un peu moins galère.

## Durée estimée
- Le reste de la journée

## Ressources
### Préparations
Tu vas créer un site où seuls les utilisateurs peuvent y voir le contenu. C'est topeu-secret. Pour ceci, nous allons créer des fonctions basiques de login, puis restreindre l'accès à certaines fonctionnalités du site.

- Le site aura un model User, avec mots de passe, emails
- Les utilisateurs devront se login pour accéder à une page de contenu ultra-secret
- Plus quelques fonctionnalités pour ceux qui veulent aller plus loin 😉

### En avant
#### 1. Création

- Crée une nouvelle application Rails avec `rails new members-2`
- Mets à jour le Gemfile pour [notre Gemfile classique](https://github.com/TheHackingProject/thp-session-01/blob/master/03_rails/semaine_04/07_28_VENDREDI/01_faire_un_site/files/Gemfile), puis bundle
- Push sur Heroku pour voir si ça marche

#### 2. Le model

- Crée un model `User`
  - il y aura un attribut `email`, unique, avec une présence obligatoire
  - il y aura un password, que l'on va gérer avec has_secure_password. Si jamais ta mémoire te trahit, [voici le lien du chapitre du bouquin de Hartl qui en parlait](https://www.railstutorial.org/book/modeling_users#sec-adding_a_secure_password)
- Mets à jour le fichier `seeds.rb` pour y rentrer un utilisateur qui te servira pour aller sur ton app

#### 3. CRUD
Pour le model User, fais un petit CRUD, afin de ne pas perdre la main ✌️

Tu peux t'inspirer du [projet de The_Hacking_Gossip](https://trello.com/c/puGvB8nC/61-thehackinggossip)

### Static Pages
#### 1. La home
Notre site va contenir une page d'accueil, qui va proposer en lien notre page top secrète.

#### 2. La page secrète
La page secrète doit annoncer la réponse à la question de l'univers.

### Login ?
Nous n'allons pas aller plus loin que [le chapitre](https://www.railstutorial.org/book/basic_login) de basic login pour cette partie. Pas de cookies permanent, juste la notion de login.

#### 1. La base
Nous allons donc créer le login. Pour cela, il faut créer le controller des sessions, puis faire les views correspondantes. Crée le controller des sessions, avec comme méthodes `new`, `create`, `edit`.

Fais la view pour la méthode `new`.

#### 2. Le login
Nous allons nous attaquer à la méthode `create`. Si l'utilisateur arrive à s'autentifier, login ce dernier. Sinon, `render new`.

Pour le login, n'utilise pas les cookies permanents, mais juste la `session` : plus simple.

#### 3. Header
Le header du site doit afficher le lien pour se login si jamais l'utilisateur n'est pas login. Si ce dernier, le header doit afficher le lien pour se logout. Bien entendu, le lien pour se logout doit être relié à la méthode destroy de notre controller de session.

### Restriction d'accès
Notre page avec la réponse de l'univers ne doit être accessible que pour les personnes enregistrées sur le site. Si une personne n'est pas login et essaie d'accéder à cette page, le site doit la rediriger ver la page de login, avec un message d'erreur lui disant qu'il faut qu'elle se login.

### Version des champions
Cette partie est pour ceux qui s'ennuient.

#### 1. Login, niveau BG
Le login par session c'est faible? Fais un login avec des cookies permanents.

#### 2. Restriction, niveau BG
Actuellement, tous les utilisateurs peuvent aller éditer les pages de tout le monde. Fais en sorte que les pages d'édition de profil ne peuvent être accédées que par les utilisateurs concernés (et qui doivent être login bien entendu). On me dit dans mon oreillette que la variable `current_user` te sera utile 😉


model user, login, logout liens
session, cookies pour les champions
restreindre l'accès à la page 42, restreindre l'accès à l'edit pour les champions