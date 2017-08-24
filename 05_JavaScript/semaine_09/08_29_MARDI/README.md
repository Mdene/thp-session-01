# Mardi
Aujourd'hui, tu vas découvrir l'univers merveilleux des callbakcs.

## Ressources
La grande différence entre JavaScript et un langage séquentiel type ruby, est que JavaScript n'exécute pas les fonctions ligne après ligne, mais il exécute tout en même temps. C'est en effet très pratique pour le front : notre site va en même temps attendre que l'utilisateur clique sur `Send credentials`, et il va aussi attendre qu'il clique sur `tab 2`, en même temps. Et transposer ça en séquentiel aurait été bien galère.

Mais alors comment incrémenter une variable, et jouer avec la variable incrémentée ? 🤔 Voici tout l'intérêt des callbacks : ils permettent de donner de l'ordre d'exécution à JavaScript. Bien que ce soit un concept assez avancé, c'est indisensable pour bien comprendre JavaScript.

Le truc qui peut être un peu déroutant avec les callbacks, c'est que c'est un système que fait passer des fonctions en tant que paramètres de fonction.

J'ai pas mal recherché d'articles à ce sujet, et j'ai trouvé [cet article](https://medium.freecodecamp.org/javascript-callbacks-explained-using-minions-da272f4d9bcd) qui expliquait les callbacks en faisant une référence un peu bizarre avec les minions. C'est pour moi le meilleur article qui explique les callbacks. Puis nos amis de The Odin Project ont fait [un article](https://www.theodinproject.com/courses/javascript-and-jquery/lessons/callbacks-living-in-an-event-driven-world) qui explique les callbacks qui est très bien une fois que l'on a compris grossomodo comment ils marchent.


## Projet
Pour ce projet, nous allons reprendre le projet de The Odin Project sur les callbacks, que tu peux retrouver [ici](https://www.theodinproject.com/courses/javascript-and-jquery/lessons/callbacks)