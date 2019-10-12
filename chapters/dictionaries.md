# Les Dictionnaires

Dans ce chapitre nous allons travailler avec les dictionnaires Python. Les dictionnaires sont des structures de données qui indexent les valeurs par une clé donnée (paires clé-valeur). L'exemple suivant  montre un dictionnaire qui indexe les âges des étudiants par nom.

```Python
ages = {
    "Peter": 10,
    "Isabel": 11,
    "Anna": 9,
    "Thomas": 10,
    "Bob": 10,
    "Joseph": 11,
    "Maria": 12,
    "Gabriel": 10,
}

>>> print(ages["Peter"])
10
```

Il est possible d'itérer sur les contenus d'un dictionnaire en utilisant "items", comme ceci:

```Python
>>> for name, age in ages.items():
...     print(name, age)
...
Peter 10
Isabel 11
Anna 9
Thomas 10
Bob 10
Joseph 11
Maria 12
Gabriel 10
```

Néanmoins, les clés de dictionnaire ne doivent pas être nécessairement des chaînes de caractères mais peuvent être n'importe quel objet [immuable](https://docs.python.org/3/tutorial/datastructures.html#dictionaries):

```Python
d = {
    0: [0, 0, 0],
    1: [1, 1, 1],
    2: [2, 2, 2],
}

>>> d[2]
[2, 2, 2]
```

Et vous pouvez aussi utiliser d'autres dictionnaires comme valeurs:

```Python
students = {
    "Peter": {"age": 10, "address": "Lisbon"},
    "Isabel": {"age": 11, "address": "Sesimbra"},
    "Anna": {"age": 9, "address": "Lisbon"},
}

>>> students['Peter']
{'age': 10, 'address': 'Lisbon'}
>>> students['Peter']['address']
'Lisbon'
```

C'est très utile pour structurer une information hiérarchique.

## Exercices avec les dictionnaires

Utilisez la documentation Python à <https://docs.python.org/3/library/stdtypes.html#mapping-types-dict> pour résoudre les exercices suivants.

Prenez le dictionnaire Python suivant:

    ages = {
        "Peter": 10,
        "Isabel": 11,
        "Anna": 9,
        "Thomas": 10,
        "Bob": 10,
        "Joseph": 11,
        "Maria": 12,
        "Gabriel": 10,
    }

1.  Combien d'étudiants sont dans le dictionnaire? Etudiez la fonction "len".

2.  Implémentez une fonction qui reçoit le dictionnaire "ages" comme paramètre et retourne l'âge moyen des étudiants. Traversez tous les éléments du dictionnaire en utilisant la méthode "items" comme expliqué plus haut.

3.  Implémentez une fonction qui reçoit le dictionnaire "ages" comme paramètre et retourne le nom de l'étudiant le plus âgé.

4.  Implémentez une fonction qui reçoit le dictionnaire "ages" et une nombre "n" et retourne un nouveau dictionnaire dans lequel chaque étudiant est plus âgé de \(n\) ans. Par exemple, *new_ages(ages, 10)* retourne une copie de "ages" dans laquelle chaque étudiant est 10 ans plus âgé.

## Exercices avec des sous-dictionnaires

Prenez le dictionnaire suivant:

    students = {
        "Peter": {"age": 10, "address": "Lisbon"},
        "Isabel": {"age": 11, "address": "Sesimbra"},
        "Anna": {"age": 9, "address": "Lisbon"},
    }

1.  Combien d'étudiants sont-ils dans le dict "students"? Utilisez la fonction appropriée.

2.  Implémentez une fonction qui reçoit le dict "students" et retourne l'âge moyen.

3. Implémentez une fonction qui reçoit le dict "students" et une adresse, et retourne une liste avec les noms de tous les étudiants dont l'adresse correspond à l'adresse dans l'argument. Par exemple, invoquer "find_students(students, ’Lisbon’)" devrait retourner Peter et Anna.