# Lundi || Mardi
L'un de ces jours, tu vas te remettre dans le bain merveilleux de HTML / CSS en faisant la page vidéo d'une vidéo YouTube.

## Ressources
Les ressources sont ici à titre indicatif. Tu t'en serviras sûrement pour le projet et comme la meilleure façon de savoir coder est de s'entrainer, ne prends pas plus d'une heure pour tout appréhender. Survole donc ces lectures, tu t'en serviras en temps voulu 😉

- The Odin Project ont fait [un bon récap](https://www.theodinproject.com/courses/html5-and-css3/lessons/html5-basics) sur les bases de HTML / CSS
- W3Schools ont fait [un article](https://www.w3schools.com/html/html_images.asp) sur comment insérer des images
- Ils ont fait [un article aussi sur l'embed des vidéos YouTube](https://www.w3schools.com/html/html_youtube.asp)
- Cela peut toujours servir : [voici comment créer](https://www.w3schools.com/howto/howto_css_fixed_menu.asp) un header qui est _fixed_

## Projet
Dans ce projet, tu vas devoir recréer [la page d'une vidéo Youtube](https://www.youtube.com/watch?v=dQw4w9WgXcQ). C'est une excellente introduction à l'insertion de média, et cela va te redonner des bases solides en mise en page.

![youtube page](https://github.com/TheHackingProject/thp-session-01/blob/master/04_HTML_CSS/semaine_07/08_14_LUNDI%7C%7CMARDI/files/youtube.jpg)

Tu vas donc de voir insérer une vidéo qui est embed, ainsi que les images qui réprésentent les aperçus sur la barre latérale de YouTube. Il y a beaucoup d'élément qui sont fait avec du JavaScript, que tu n'as pas à faire (on verra JS la semaine prochaine). Dès qu'un élément réagit au click, c'est du JS.

Aussi, pas besoin de faire le site en mobile friendly. On verra lundi prochain comment le faire responsive. Pour le moment concentre-toi sur la mise en page.

### Les étapes
On va t'aider dans les étapes :

- fais un nouveaux projet rails `youtube` (tu as cru que tu allais esquiver Rails ? 😎)
- controller home, methode index, toussa toussa
- essaie de voir l'architecture de la page : quels seront les divs qui vont être ensemble, comment seront regroupés les principaux éléments
- fais les divs, positionne-les, donne-leur la bonne taille. 
  - Conseil : `background-color` sur un div est une arme redoutable pour savoir leur forme, taille, position
  - Conseil bis : l'inspecteur d'éléments est ton meilleur ami ✌️
- maintenant fais les éléments dans l'ordre suivant :
  - la vidéo principale, dans laquelle tu embed une vidéo de ton choix
  - la barre latérale, dans laquelle tu vas mettre les images des _thumbnails_ des vidéos, et le texte sur le côté (titre, auteur, etc)
  - le titre de la vidéo principale, la description
- Tu commences à avoir une page sympa. Tu peux maintenant mettre un commentaire ou deux pour la forme, et t'attaquer au header
- Si tu te sens très chaud, tu peux faire l'un de ces deux bonus-stage :
  - utilise un Youtube Downloader pour télécharger une vidéo de ton choix (courte, pour pas qu'elle pèse 500Mo), puis au lieu d'embed pour la vidéo principale une vidéo Youtube, arrange-toi pour héberger la vidéo et la jouer avec un lecteur média
  - quand tu _hover_ les _thumbnails_ des vidéos de la barre latérale, tu constates qu'il y a un petit gif qui donne un aperçu de la vidéo en cours. Arrange-toi pour que ce gif apparaisse dans ton site
- tu n'as plus qu'à push sur heroku ta merveille de site internet 🔥