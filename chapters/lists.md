# Les listes

Les listes de Python sont des structures de données qui groupent des suites d'éléments. Les listes peuvent avoir des éléments de différents types et vous pouvez aussi mélanger des types différents au sein de la même liste, bien que la plupart du temps tous les éléments sont du même type.

Les listes sont créées en utilisant des crochets et les éléments sont séparés par des virgules. On peut accéder aux éléments d'une liste par leurs positions respectives. 0 est l'index du premier élément. 

```Python
>>> l = [1, 2, 3, 4, 5]
>>> l[0]
1
>>> l[1]
2
```

Pouvez-vous accéder au numéro 4 de la liste précédente ?

Parfois vous voulez juste une petite portion d'une liste, une sous-liste. Les sous-listes peuvent être récupérées en utilisant une technique appelée *slicing*, qui consiste à définir les index de début et de fin.

```Python
>>> l = ['a', 'b', 'c', 'd', 'e']
>>> l[1:3]
['b', 'c']
```

Finalement, il est aussi possible de faire de l'arithmétique avec les listes, comme ajouter deux listes ensemble ou répéter the contenus d'une liste.

```Python
>>> [1,2] + [3,4]
[1, 2, 3, 4]
>>> [1,2] * 2
[1, 2, 1, 2]
```

## Exercices avec des listes

Créez une liste nommée "l" avec les valeurs suivantes ([1, 4, 9, 10, 23]). En utilisant la documentation de Python sur les listes (<https://docs.python.org/3.5/tutorial/introduction.html#lists>) effectuez les exercices suivants:

1.  En utilisant le slicing de liste obtenez les sous-listes \[4, 9\] et \[10, 23\].

2.  Ajoutez ("append" en anglais) la valeur 90 à la fin de la liste "l". Vérifiez la différence entre la concaténation et la méthode "append".

3.  Calculez la valeur moyennne de toutes les valeurs de la liste. Vous pouvez également utiliser les fonctions "sum" et "len".

4.  Supprimez la sous-liste [4, 9].

## Les compréhensions de liste

Une compréhension de liste est une manière concise d'écrire une liste. Elle consiste en des crochets contenant une expression suivie du mot-clé "for". Le résultat sera une liste dont les résultats correspondent à l'expression. Voici comment créer une liste avec les nombres d'une autre liste, mais carrés.

```Python
>>> [x*x for x in [0, 1, 2, 3]]
[0, 1, 4, 9]
```

Du fait de sa flexibilité, les compréhensions de liste utilisent généralement la fonction "range" qui retourne un intervalle ("range en anglais"):

```Python
>>> [x*x for x in range(4)]
[0, 1, 4, 9]
```

Parfois vous pourriez vouloir filtrer les éléments selon une condition donnée. Le mot-clé "if" peut être utilisé dans ces cas-là:

```Python
>>> [x for x in range(10) if x % 2 == 0]
[0, 2, 4, 6, 8]
```

L'exemple ci-dessus retourne toutes les valeurs paires dans un intervalle 0..10. Vous pouvez trouve plus d'informations sur lescompréhensions de liste à <https://docs.python.org/3/tutorial/datastructures.html#list-comprehensions>.

## Exercices avec des compréhensions de liste

1.  En utilisant des compréhensions de liste, créez une liste avec les carrés des dix premiers nombres.

2.  En utilisant des compréhensions de liste, créez une liste avec les cubes des 20 premiers nombres.

3.  Créez une compréhension de liste avec tous les nombres pairs de 0 à 20, et une autre avec tous les nombres impairs.

4.  Créez une liste avec les carrés des nombres pairs de 0 à 20, et faites la somme des éléments de la liste en utilisant la fonction "sum". Le résultat devrait être 1140. D'abord créez la liste en utilisant des compréhensions de listes, vérifiez le résultat, et ensuite appliquez la somme à la liste de compréhension.

5.  Créez une compréhension de liste qui retourne une liste contenant les carrés de tous les nombres pairs de 0 à 20, mais ignore les nombres qui sont divisibles par 3. En d'autres mots, chaque nombre devrait être divisible par 2 et ne pas être divisible par 3. Recherchez le mot-clé "and" dans la documentation Python. La liste résultante est \[4, 16, 64, 100, 196, 256\].