## Récap
Là tu es en train de te dire : c'est cool Rails, mais comment je fais pour y mettre le code de mon scrapper de l'infini ? Remplir les controller et y mettre des méthodes `scrap_mairies` n'est pas très clean, donc nous allons voir un truc cool qui s'appelle les _services_. Les services sont une feature de Rails (pour changer) qui permettent d'y mettre du PORO (Plain Old Ruby Objects), c'est à dire du code Ruby, que tu pourras appeler où tu veux dans Rails. Plutôt cool, non ?

## Durée estimée
1h, en comptant le petit exercice

## Ressources
Nous allons commencer par un petit tuto fait maison pour que tu fasses ton premier service. Fais une app `rails-service`, puis créé un dossier `services` à l'intérieur du dossier `app`. Dans ce dossier tu peux y mettre tous les services, et les appeler en créant des objets.

Chaque fichier du dossier `services` invoque une seule `class` (tu te souviens du tic-tac-toe ? 😉), que tu pourras appeler librement dans ton application rails. Testons. Créé un fichier `say_hello.rb` dans le dossier `services`, puis colles-y les lignes suivantes :
```ruby
class SayHello
  def perform
    p "bonjour"
  end
end
```

Sauvegarde ton fichier, puis lance ta console, ou relance-la si elle est déjà lancée. Dans la console, rentre, `SayHello.new.perform`. La console devrait t'afficher "bonjour".

```
Dans le cas où la console te renvoie une erreur genre `NameError: uninitialized constant SayHello`, il se peut que tu doives relancer spring avec `$ bin/spring stop`
```

Voyons-voir ce que cela a fait. Rails a appelé la classe SayHello, a créé une nouvelle instance de la classe, puis lui a demandé d'éxécuter la méthode `perform`. C'est la convention à utiliser pour les services : il faut créer une classe par fichier, qui fait un truc précis (dire bonjour, encaisser un user, chercher un film sur une API), pour pouvoir appeler la méthode `perform` qui exécute tout ce que la classe doit réaliser.

Tu auras remarqué que l'on a appelé le fichier `say_hello.rb` et la classe `SayHello`. C'est (encore) une convention de Rails. Le nom du fichier doit être le snake_case du nom de la classe.

Tu peux appeler tes services où tu veux. Par exemple dans tes controllers, avec la syntaxe `SayHello.new.perform`. Les services permettent d'avoir du code propre et bien rangé, et de ne pas remplir les controllers.

## Quelques articles

- NetGuru ont fait un [bon article](https://www.netguru.co/blog/service-objects-in-rails-will-help) qui explique les services
- Rob Race a fait aussi [un bon article](https://hackernoon.com/service-objects-in-ruby-on-rails-and-you-79ca8a1c946e) sur les services