# Associations - The Project, part.2 : La Revanche des associations
## Récap
Dans ce dernier projet de la semaine, nous allons te demander de réaliser des models de sites, afin de t'entraîner aux base de données relationnelles.

## Durée estimée
- Le reste de la journée

## Le projet
### Plateforme de réservations de docteurs
#### Le pitch
Tu veux concurrencer Doctolib, donc tu te dis : et si je créais un site qui fait la même chose ? C'est ce que nous allons voir 👩‍⚕️

#### Les models
Pour ce premier exercice, nous allons t'aider et te donner les models à créer :

- un model `doctor`, qui a comme attributs :
  - un `first_name`, qui est un string
  - un `last_name`, qui est un string
  - un `specialty`, qui est un string
  - un `postal_code`, qui est un integer
- un model `patient`, qui a comme attributs :
  - un `first_name`, qui est un string
  - un `last_name`, qui est un string
- un model `appoitments`, qui a comme attributs :
  - un `date`, qui est un datetime

Un `appointment` ne peut avoir qu'un seul `doctor`, mais un `doctor` peut avoir plusieurs `appointment`. Un `appointment` ne peut avoir qu'un seul `patient`, mais un `patient` peut avoir plusieurs `appointment`. Enfin, un `doctor` peut avoir plusieurs `patient`, au travers des `appointments`, et vice versa.

Si tu as bien suivi, il se peut que ce soit un exemple utilisé par [la doc](http://guides.rubyonrails.org/association_basics.html#the-has-many-through-association). C'est une excellente introduction à ce chapitre. Je t'invite à créer les models, et de faire le migrations.

#### Tester
Pour tester, tu peux aller dans la console, créer des `doctor`, `patient`, et `appointment` à la volée, puis les lier avec la sémantique que tu as utilisée.

⚠️ Comment les `doctor` et les `patient` sont liés au format array, faire `doctor.patients.last_name` te renverra une erreur 😉

### Le Airbnb des promenades de chiens
#### Le pitch
En cours de Bizeuness Model, tu devais créer une entreprise, et conquérir le monde avec tes SWOTs. À l'époque tu t'étais dit que faire une pletaforme où des personnes pourraient promener les chiens, en échange de $€

#### Les models
À priori, les models seraient simples : il y aurait un model `dogsitter` et un model `dog`. Un `dogsitter` pourrait promener plusieurs `dog` à travers un `stroll` (promenade, en anglais) ; et un `dog` pourraient avoir plusieur `dogsitter` à travers un `stroll`.

Cela ressemble beaucoup à notre schéma de docteurs tout ceci ! C'est fait exprès, rien de tel pour s'entraîner que de refaire plusieurs exercices. Ça fait toujours un peu peur au début, mais à la fin c'est toujours les mêmes syntaxes. 

#### Tester
Comme la dernière fois, pour tester il te faudra aller en console pour faire des opérations.

### Youtube-like
#### Le pitch
Après avoir conquis le monde avec des applications de promenades, tu veux t'attaquer à un marché qui explose : les vidéos en ligne. Tu connais personnellement Charly et Féfé, deux stars montantes de Youtube, et ils pourraient faire un excellent produit d'appel pour ta plateforme.

Voici comment tu verrais la plateforme : il y aurait des `user`, qui peuvent mettre en ligne des `video`. Une `video` a un auteur : un `user`. Une vidéo appartient à une seule `category`, mais une `category` peut concerner plusieurs `video`. Enfin, un `user` peut s'inscrire à plusieurs `category`, et une `category` peut être suivie par plusieurs `user`.

Cela fait un peu mal à la tête, mais voici les trois model :

- `video`, qui n'a qu'un seul auteur, et une seule catégorie
- `user`, qui peut mettre en ligne plusieurs vidéos, et qui peut suivre plusieurs catégories
- `category`, qui peut concerner plusieurs vidéos, et qui être suivie par plusieurs utilisateurs


Si tu as bien suivi, il y aura un model en plus : celui entre les catégories et les utilisateurs. Nous te laissons choisir le nom. 

### Pimp des docteurs
Ta startup de docteurs marche à merveille, tellement que tu aimerais ajouter plusieurs tables :

- `city` : un docteur, un patient, et un rendez-vous appartiennent tous à une `city`. Une city peut avoir plusieurs docteurs, patients, et rendez-vous
- tu voudrais virer la ligne `specialty` de ta table `doctor` et la remplacer par un model à part entière : tu vas donc créer un model `specialty`. Un docteur aurait plusieurs `specialty` (DEAL_WITH_IT), et une `specialty` pourrait concerner plusieurs `doctor`