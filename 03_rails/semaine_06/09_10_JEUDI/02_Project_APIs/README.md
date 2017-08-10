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