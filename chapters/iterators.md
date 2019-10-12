# Les Itérateurs

Comme nous l'avons vu précédemment, en Python nous utilisons la boucle "for" pour itérer sur les contenus des objets:

```Python
>>> for value in [0, 1, 2, 3, 4, 5]:
...     print(value)
...
0
1
4
9
16
25
```

Les objets qui peuvent être utilisés dans une boucle "for" sont appelés itérateurs. Partant de là, un itérateur est un objet qui suit le protocole d'itération.

La fonction intégrée "iter" peut-être utilisée pour construire des objets intérateurs, tandis que la fonction "next" peut être utilisée pour itérer graduellement sur leur contenu:

```Python
>>> my_iter = iter([1, 2, 3])
>>> my_iter
<list_iterator object at 0x10ed41cc0>
>>> next(my_iter)
1
>>> next(my_iter)
2
>>> next(my_iter)
3
>>> next(my_iter)
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
StopIteration
```

S'il n'y a plus d'élément, l'itérateur lève une exception "StopIteration".

## Les Classes Itérateurs

Les itérateurs peuvent être implémentés comme classes. Vous devez seulement implémenter les méthodes "\_\_next\_\_" et "\_\_iter\_\_". Voici un exemple de classe qui imite la fonction "range", retournant toutes les valeurs de "a" jusqu'à "b":

```Python
class MyRange:

    def __init__(self, a, b):
        self.a = a
        self.b = b

    def __iter__(self):
        return self

    def __next__(self):
        if self.a < self.b:
            value = self.a
            self.a += 1
            return value
        else:
            raise StopIteration
```

Pour l'essentiel, à chaque appel, la méthode "next" augmente la variable "a" d'une unité et retourne sa valeur. Lorsque celle-ci atteint la valeur de "b", la méthode lève une exception StopIteration.

```Python
>>> myrange = MyRange(1, 4)
>>> next(myrange)
1
>>> next(myrange)
2
>>> next(myrange)
3
>>> next(myrange)
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
StopIteration
```

Mais le plus important, c'est que vous pouvez utiliser la classe itérateur dans une boucle "for":

```Python
>>> for value in MyRange(1, 4):
...     print(value)
...
1
2
3
```

## Exercices avec les itérateurs

1.  Implémentez une classe itérateur qui retourne le carré de tous les nombres de "a" à "b".

2.  Implémentez une classe térateur qui retourne tous les nombres pairs de 1 à \(n\).

3.  Implémentez une classe itérateur qui retourne tous les nombres impairs de 1 à \(n\).

4.  Implémentez une classe itérateur qui retourne tous les nombres de \(n\) positif jusqu'à 0.

5.  Implémentez une classe intérateur qui retourne la suite de Fibonnaci depuis le premier élément jusqu'à \(n\). Vous pouvez vérifier la définition de la suite de Fibonnaci dans le chapitre sur les fonctions. Voici les premiers nombres de la suite: 0, 1, 1, 2, 3, 5, 8, 13, 21, 34, 55, 89, ...

6.  Implémentez une classe itérateur qui retourne toutes les paires consécutives de nombres de 0 à \(n\), telles que (0, 1), (1, 2), (2, 3)...