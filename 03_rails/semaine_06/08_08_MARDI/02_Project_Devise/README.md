# Projet : The_Gossip_Project : Final Part
Encore The_Gossip_Project ??? Mais on ne finira jamais !! Aujourd'hui tu vas profiter des compétences que tu as acquises avec Devise pour faire une version Finale de The_Gossip_Project !

**Durée** : le reste de la journée

## Résumé
Voici ce qui t'es demandé : ton agence vient de t'annoncer qu'ils ont décroché un contrat à 200k€ pour The_Hacking_Project afin que tu leur fasses un site qui permettra à leurs matelots de poster des gossips de manière anonyme. La page d'accueil du site doit être :

- un warning qui dit : "Hey bro connecte-toi ou inscris-toi !" si la personne n'est pas logguée
- la liste de tous les gossips si la personne est login

La page d'inscription est simple : nous demandons `email`, `anonymous_username`, et `password` à la personne. Petit bonus : il faudra trouver un moyen de rendre le site exclusif pour éviter que des petits curieux viennent s'y inscrire et matter tous nos gossips (code promo, whitelist d'emails, fais comme tu veux 👊).

Une fois login/signup, l'utilisateur est redirigé vers la liste de tous les gossips. Dans cet `index`, tu pourras retrouver une liste de tous les gossips, avec la date d'ajout, le `username` de la personne qui a posté le gossip, et un lien pour supprimer le gossip si la personne qui a écrit le gossip est bien la personne qui est login.

Le site aura un petit header qui contient : 

- un lien pour créer un gossip
- un lien pour se logout, si la personne est login


Bien entendu, l'intégralité du site n'est accessible uniquement si la personne est login. Le site redirigera vers la page "Hey bro connecte-toi ou inscris-toi !" si la personne n'est pas logguée.

## Niveau de difficulté : je suis chaud-patate, j'ai envie de réfléchir 🔥
Au boulot ❤️

## Niveau de difficulté : t'as pas un pas à pas ?
Bien sûr !

### 1. Models & Architecture
Avant toute chose, il faut toujours penser à modéliser la base de données d'un site, et de penser l'architecture. Si tu as bien suivi, le site aura deux models :

- `corsair`, qui a comme attributs : un `email`, un `username`, un `password`. Devise s'occupe déjà de deux de ces attributs, tu devrais ajouter toi-même le troisième
- `gossip`, qui a comme attribut : un `content`

Bien entendu les classes `gossip` et `corsair` sont liées : un `corsair` peut avoir plusieurs `gossip`, mais un `gossip` n'a qu'un seul `corsair`.

La modélisation de ce site est assez simple, mais il est en général recommandé de commencer par les migrations, pour éviter de faire des migrations foireuses au milieu du projet (bien que l'on ne soit jamais à l'abri d'un "oh merde en fait le client veut rajotuer cette feature il faut supprimer cette colonne"). Donc ce que tu as vu hier avec le pas à pas des `Booking` et `Passenger` était absolument pas best practice (mais très bien pour s'entraîner à faire des migrations en milieu de projet).

Pour les users, bien entendu, il faut que tu passes par Devise.

Enfin, mon framwork préféré Tacit peut t'aider à ne pas te prendre la tête sur le CSS pour le moment, et avoir un truc qui ressemble à quelque chose.

⚠️ **Heroku** ⚠️ : pour éviter les mauvaises suprises en fin de projet, on te conseille de faire un premier push sur Heroku pour vérifier que tout marche convenablement ✌️

### 2. Le flow
Faisons un petit flow basique :

- si une personne arrive sur la page d'accueil, le site lui demande de s'inscrire/login s'il n'est pas connecté, ou bien lui renvoyer l'index des gossips s'il est connecté
- si un user se login / signup, le site va le rediriger vers la root (soit l'index des gossips)

Je t'invite à faire une base de ces views, en te servant de Devise, et en configurant tes controllers et views. Nous passerons après aux sujets un peu plus complexes.

### 3. Le header
Maintenant, créé le header pour qu'un qui est login puisse :

- y trouver un lien pour créer un `gossip`
- y trouver le lien pour se logout

Bien entendu, le header ne doit pas afficher ces liens si l'utilisateur n'est pas login.

### 4. anonymous_username
Maintenant, nous allons prendre en compte l'attribut `anonymous_username` : modifie le formulaire de sign_up afin d'obliger les personnes qui s'inscrivent de renseigner la case `anonymous_username`.

Une fois ceci fait, modifie la view de l'index des `gossip` pour afficher les gossip : chaque `gossip` doit afficher le `anonymous_username` de sont auteur, le `content`, puis la date de création.

### 5. Supprimer le gossip
Dans la liste des gossips, un utilisateur doit pouvoir supprimer les `gossip` qu'il a créés. Tu peux utiliser la variable `current_user` que Devise autorise pour ceci.

### 6. Exclusif !
Tu as quasiment fini, il ne te manque plus qu'à rajouter une touche d'exclusivité à ton inscription d'utilisateurs. Ceci est plus facile que ce que cela en a l'air. L'avantage de Rails est que comment c'est un langage assez utilisé, d'autres personnes se sont penchées sur le sujet. Voici deux solutions plutôt évidentes : 

- [Autoriser uniquement certaines adresses emails](https://stackoverflow.com/questions/28787615/add-invite-code-to-devise)
- [Donner un code d'accès type "GOSSIP_2017"](https://stackoverflow.com/questions/5167576/whitelisting-with-devise)

## Des tests
Mais mais mais, tu viens de faire ton premier site qui marche pour de vrai et que tu peux montrer sans honte à la terre entière !! Waow ! Avant de faire un push sur Heroku, on va faire quelques tests pour vérifier que tout marche bien.

La bonne pratique est de faire des tests de happy_path, c'est à dire de voir que ce qui devrait marcher marche bien.

### Test d'intégration
Les tests d'intégration testent que ce qui devrait être affiché soit bien affiché. Fais donc deux tests d'intégration pour la page d'accueil :

- si jamais l'utilisateur n'est pas login, le site le redirige vers la page de signup
- si jamais l'utilisateur est login, le site doit afficher l'index des `gossip`

### Controller tests
Les tests de controller vérifient que le controller fait bien son travail :

- une fois qu'un utilisateur s'inscrit ou se login, il doit être redirigé vers l'index des `gossip`

### Destroy
La page d'index des `gossip` doit afficher tous les gossips. Aussi, un utilisateur doit pouvoir détruire ses `gossip`, mais pas ceux des autres utilisateurs. Fais-donc un test pour vérifier cela. Tu peux t'aider des fixtures pour générer des `gossip` à la volée.

### Exclusif
Il est impossible de s'inscrire si la personne n'a pas le bon code / n'est pas whitelistée. Fais-donc un test pour vérifier ceci.

Aussi, vérifie qu'il est possible de s'inscrire avec le bon code / le bon whtelist.

### Autres ?
Les tests c'est le bien, tu peux donc en faire d'autres si tu veux !

## Push push push
Bravo ! Maintenant fais tourner le site parmi les corsaires et spammez-vous de gossips entre vous ⛵
