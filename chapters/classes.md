# Les Classes

En programmation orientée objet (POO), une classe est une structure qui permet de grouper ensemble un ensemble de propriétés (appelées attributs) et de fonctions (appelées méthodes) pour manipuler ces propriétés. Prenez la classe suivante qui définit une personne avec les propriétés "name" et "age" et la méthode "greet".

```Python
class Person:

      def __init__(self, name, age):
          self.name = name
          self.age = age

      def greet(self):
          print("Hello, my name is %s!" % self.name)
```

La plupart des classes ont besoin d'une méthode appelée constructeur ("\_\_init\_\_") pour intialiser les attributs de la classe. Dans le cas précédent le constructeur de la classe reçoit  le nom et l'âge de la personne et stocke cette information dans l'instance de la classe (référencée par le mot-clé *self*). Finalement, la méthode "greet" imprime le nom de la personne tel que stocké dans une instance de classe particulière (un objet).

Les instances de classe sont utilisées grâce à une instanciation d'objets. Voici comment nous instancions deux objets:

```Python
>>> a = Person("Peter", 20)
>>> b = Person("Anna", 19)

>>> a.greet()
Hello, my name is Peter!
>>> b.greet()
Hello, my name is Anna!

>>> print(a.age)  # Nous pouvons aussi accéder aux attributs d'un objet.
20
```

## Exercices avec des classes

Utilisez la documentation Python sur les classes à <https://docs.python.org/3/tutorial/classes.html> pour résoudre les exercices suivants.

1.  Implémentez une classe nommée "Rectangle" pour stocker les coordonnées d'un rectangle d'après le coin supérieur gauche (x1, y1) et le coin inférieur droit (x2, y2).

2.  Implémentez le constructeur de classe avec les paramètres (x1, y1, x2, y2) et stockez-les dans l'instance de classe en utilisant le mot-clé "self".

3.  Implémentez les méthodes "width()" et "height()" qui retournent, respectivement, la largeur et la hauteur d'un rectangle. Créez deux objets, instances de "Rectangle", pour tester les calculs.

4.  Implémentez la méthode "area" pour retourner l'aire du rectangle (width\*height).

5.  Implémentez la méthode "circumference" qui retourne le périmètre du rectangle (2\*width + 2\*height).

6.  Faites un print d'un des objets créés pour tester la classe. Implémentez la méthode "\_\_str\_\_" de manière que lorsque vous imprimez l'un des objets il imprime les coordonnées comme (x1, y1)(x2, y2).

## L'Héritage de classe

En programmation orientée objet, l'héritage est une des formes par lesquelles une sous-classe peut hériter des attributs et des méthodes d'une autre classe, lui permettant de réécrire certaines des fonctionnalités de la superclasse. Par exemple, à partir de la classe "Person" vue plus haut nous pouvons créer une sous-classe qui ne conserve que les personnes âgées de 10 ans:

```Python
class TenYearOldPerson(Person):

      def __init__(self, name):
          super().__init__(name, 10)

      def greet(self):
          print("I don't talk to strangers!!")
```

L'indication que la classe "TenYearOldPerson" est une sous-classe de "Person" est donnée à la première ligne. Ensuite, nous avons réécrit le constructeur de la sous-classe pour ne recevoir que le nom de la personne, mais nous appelons finalement le constructeur de la superclasse avec le nom de l'enfant de 10 ans et l'âge codé en dur de 10. Enfin, nous avons réimplémenté la méthode "greet".

## Exercices avec l'héritage

Utilisez la classe "Rectangle" telle qu'elle est implémentée plus haut pour effectuer les exercices suivants:

1.  Créez une class "Square" comme sous-classe de "Rectangle".

2.  Implement the "Square" constructor. The constructor should have only the x1, y1 coordinates and the size of the square. Notice which arguments you’ll have to use when you invoke the "Rectangle" constructor when you use "super".

2.  Implémentez le constructeur de "Square". Le constructeur ne doit contenir que les coordonnées x1, y1 et la taille du carré. Faites attention aux arguments que vous utilisez lorsque vous invoquez le constructeur de "Rectangle" lorsque vous utilisez "super".

3.  Instantiez deux objets "Square", invoquez la méthode "area" et imprimez les objets. Assurez-vous que tous les calculs retournent des nombres corrects et que les coordonnées des carrés sont cohérents avec la taille du carré utilisée comme argument.