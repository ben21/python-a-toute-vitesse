# L'itération et les boucles

Dans ce hapitre nous allons explorer les deux sujets de l'itération et des boucles. Les boucles sont utilisées en informatique pour automatiser les tâches répétitives.

En Python la forme la plus commune d'itération est la boucle "for". La boucle "for" vous permet d'itérer sur tous les éléments d'une liste de manière à ce que vous puissiez faire tout ce que vous voulez avec chaque élément. Par exemple, créons une liste et imprimons la valeur du carré de chacun des éléments.

```Python
>>> for value in [0, 1, 2, 3, 4, 5]:
...     print(value * value)
...
0
1
4
9
16
25
```

C'est assez simple mais très puissant \! La boucle "for" est la base de beaucoup de choses en programmation. Par exemple, vous connaissez déjà la fonction "sum(list)" qui somme tous les éléments d'une liste, mais voici un exemple utilisant la boucle "for":

```Python
>>> mylist = [1,5,7]
>>> sum = 0
>>> for value in mylist:
...     sum = sum + value
...
>>> print(sum)
13
```

Pour l'essentiel, vous créez la variable "sum" et vous continuez d'additionner chaque valeur selon l'ordre de la liste.

Parfois, au lieu des valeurs d'une liste, vous pourriez avoir besoin de travailler avec les index eux-mêmes, c'est-à-dire non pas avec les valeurs, mais avec les positions où elles sont dans la liste. Voici un exemple qui itère sur une liste et retourne les index et les valeurs pour chaque index:

```Python
>>> mylist = [1,5,7]
>>> for i in range(len(mylist)):
...     print("Index:", i, "Value:", mylist[i])
...
Index: 0 Value: 1
Index: 1 Value: 5
Index: 2 Value: 7
```

Vous pouvez voir que nous n'intérons pas sur la liste elle-même mais que nous itérons sur le "range" (l'intervalle) de la longueur de la liste. La fonction range retourne une liste spéciale:

```Python
>>> list(range(3))
[0, 1, 2]
```

Donc, quand vous utilisez "range" vous n'itérez pas sur "myList" mais sur une liste contenant plusieurs nombres que vous allez utiliser comme index pour accéder aux valeurs individuelles de "myList". Vous trouverez plus d'informations sur la fonction range dans la documentation Python à <https://docs.python.org/3/tutorial/controlflow.html#the-range-function>.

Il se peut que parfois vous ayez besoin des deux, index et valeurs. Vous pouvez alors utiliser la fonction "enumerate":

```Python
>>> mylist = [1,5,7]
>>> for i, value in enumerate(mylist):
...     print("Index:", i, "Value:", value)
...
Index: 0 Value: 1
Index: 1 Value: 5
Index: 2 Value: 7
```

Souvenez-vous que la première valeur d'une liste Python est toujours à l'index 0.

Finalement, nous avons aussi l'expression "while" qui nous permet de répéter une suite d'instructions tant qu'une condition spécifiée est vraie. Par exemple, l'exemple suivant démarre avec "n" à 10 et **tant que "n" est plus grand que 0**, il continue de soustraire 1 de "n". Lorsque "n" atteint 0, la condition "n \> 0" est fausse, et la boucle s'arrête.

```Python
>>> n = 10
>>> while n > 0:
...     print(n)
...     n = n-1
...
10
9
8
7
6
5
4
3
2
1
```

Remarquez qu'il n'imprime jamais 0...

## Exercices avec la boucle for

Pour cette section, il se pourrait que vous souhaitiez consulter la documentation Python à <https://docs.python.org/3/tutorial/controlflow.html#the-range-function>.

1.  Créez une fonction "ajouter" qui reçoit une liste comme paramètre et retourne la somme de tous les éléments de la liste. Utilisez la boucle "for" pour itérer à travers les éléments de la liste.

2.  Créez une fonction qui reçoit une liste comme paramètre et retourne la valeur maximum de la liste. Lorsque vous itérez à travers la liste vous voudrez garder la valeur maximum trouvée jusque-là afin de la comparer avec les éléments suivants de la liste.

3.  Modifiez la fonction précédente de manière qu'elle retourne une liste dont le premier élément est la valeur maximum et le second l'index de la valeur maximum de la liste. En plus de conserver la valeur maximum de la liste à chaque étape de la boucle, vous devrez conserver aussi la position où elle est apparue.

4.  Implémentez une fonction qui retourne en ordre inverse une liste reçue en paramètre. Vous pouvez créer une liste vide et ajouter les valeurs dans le sens inverse au fur et à mesure qu'elles sortent de la liste d'origine. Regardez ce que vous pouvez faire avec les listes à <https://docs.python.org/3/tutorial/datastructures.html#more-on-lists>.

5.  Créez une fonction "is\_sorted" qui reçoit une liste comme paramètre et retourne True si la liste est triée dans un ordre ascendant. Par exemple \[1, 2, 2, 3\] est triée alors que \[1, 2, 3, 2\] ne l'est pas. Suggestion: Vous devez comparer un nombre dans la liste avec le suivant. Vous pouvez utiliser les index, ou vous devez garder en mémoire le nombre précédent dans une variable pendant que vous itérez à travers la liste.

6.  Implémentez la fonction "is\_sorted\_dec" qui est similaire à la précédente mais cette fois-ci tous les éléments doivent être triés en ordre décroissant.

7.  Implémentez la fonction "has\_duplicates" qui vérifie si une liste a des valeurs dupliquées. Il se peut que vous ayez à utiliser deux boucles "for", dans lesquelles pour chaque valeur vous ayez à chercher des doublons dans le reste de la liste.

## Exercices avec l'expression while

1.  Implémentez une fonction qui reçoit un nombre comme paramètre et imprime, en ordre décroissant, quels nombres sont pairs et quels nombres sont impairs, jusqu'à atteindre 0.
    
        >>> even_odd(10)
        Even number: 10
        Odd number: 9
        Even number: 8
        Odd number: 7
        Even number: 6
        Odd number: 5
        Even number: 4
        Odd number: 3
        Even number: 2
        Odd number: 1
