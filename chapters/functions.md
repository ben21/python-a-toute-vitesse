# Modules et fonctions

Dans ce chapitre nous allons parler des modules et fonctions. Une fonction est un bloc de code qui est utilisé pour accomplir une action. Un module est un fichier Python contenant des variables, des fonctions et bien d'autres choses encore.

Lancez votre REPL Python. Utilisons le module "math" qui donne accès aux fonctions mathématiques:

```Python
>>> import math
>>> math.cos(0.0)
1.0
>>> math.radians(275)
4.799655442984406
```

Les fonctions sont des suites d'instructions qui sont exécutées lorsque la fonction est invoquée. Ce qui suit définit la fonction "do\_hello" qui imprime deux messages lorsqu'elle est invoquée:

```Python
>>> def do_hello():
...     print("Hello")
...     print("World")
...
>>> do_hello()
Hello
World
```

Assurez-vous de bien insérer un tab avant chacune des deux expression dans la fonction précédente. Les tabs et les espaces ont une signification en Python et définissent qu'un bloc de code est d'une certaine manière dépendant de l'instruction précédente. Par exemple, les expressions print sont "à l'intérieur" de la fonction "do\_hello" et pour cette raison doivent avoir un tab.

Les fonctions peuvent également recevoir des paramètres et retourner une valeur (en utilisant le mot-clé "return"):

```Python
>>> def add_one(val):
...     print("Function got value", val)
...     return val + 1
...
>>> value = add_one(1)
Function got value 1
>>> value
2
```

## Exercices avec le module math


Utilisez la documentation Python concernant le module math (<https://docs.python.org/3/library/math.html>) pour résoudre les exercices suivants:

1.  Trouvez le plus grand commun diviseur des paires de nombres suivantes: (15, 21), (152, 200), (1988, 9765).

2.  Calculez le logarithme en base 2 des nombres suivants: 0, 1, 2, 6, 9, 15.

3.  Utilisez la fonction "input" pour demander un nombre à l'utilisateur et montrez le résultat du sinus, du cosinus et de la tangeante du nombre. Assurez-vous que vous convertissez l'input de l'utilisateur de chaîne à nombre (utilisez la fonction int() ou float()).

## Exercices avec les fonctions

1.  Implémentez la fonction "add2" qui reçoit deux nombres comme arguments et retourne la somme des deux nombres. Ensuite implémentez la fonction "add3" qui reçoit et additionne 3 paramètres.

2.  Implémentez une fonction qui retourne le plus grand de deux nombres donnés en paramètres. utilisez l'expression "if" pour comparer les deux nombres: <https://docs.python.org/3/tutorial/controlflow.html#if-statements>.

3.  Implémentez une fonction nommée "is\_divisible" qui reçoit deux paramètres (nommés "a" et "b") et retourne vrai si "a" peut être divisé par "b" ou faux autrement. Un nombre est divisible par un autre lorsque le reste de la division est zéro. Utilisez l'opérateur modulo (%).

4.  Créez une fonction nommée "moyenne" qui calcule la valeur moyenne d'une liste passée en paramètre d ela fonction. Utilisez les fonctions "sum" et "len".

## Les fonctions récursives

En programmation, une fonction récursive est simplement une fonction qui s'appelle elle-même. Par exemple, prenez la fonction factorielle.

\begin{equation}
f(x)=\begin{cases}
    1, & \text{if $x=0$}.\\
    x \times f(x-1), & \text{otherwise}.
\end{cases}
\end{equation}

Prenons comme cas concret la factorielle de 5:

\begin{equation}
\begin{split}
5! &= 5 \times 4! \\
    &= 5 \times 4 \times 3! \\
    &= 5 \times 4 \times 3 \times 2! \\
    &= 5 \times 4 \times 3 \times 2 \times 1 \\
    &= 120
\end{split}
\end{equation}

Pour l'essentiel, la factorielle de 5 est 5 fois la factorielle de 4, etc. Finalement, la factorielle de 1 (ou de zéro) est 1, ce qui rompt la récursion. En Python nous pourrions écrire la fonction récursive suivante:

```Python
def factorial(x):
    if x == 0:
        return 1
    else:
        return x * factorial(x-1)
```

L'astuce avec les fonctions récursives est qu'il doit y avoir un cas "de base" où la récursion s'arrête et un cas récursif qui itère vers le cas de base. Dans la cas de la factorielle nous savons que la factorielle de zero est un, et la factorielle d'un nombre plus grand que zero va dépendre de la factorielle du nombre précédent jusqu'à ce celui-ci atteigne zéro.

## Exercices avec les fonctions récursives

1.  Implémentez la fonction factorielle et testez-là avec plusieurs valeurs. Verifiez avec une calculette.

2.  Implémentez une fonction récursive pour calculer la somme des \(n\) premiers nombres entiers (où \(n\) est un paramètre de fonction). Commencez par réfléchir au cas de base (la somme des 0 premiers entiers est égale à combien?) et ensuite réfléchissez au cas résursif.

3.  La suite de Fibonnaci est une suite de nombres dans laquelle chaque nombre de la suite correspond à la somme des deux nombres précédents. Etant donnée la définition récursive suivante, implémentez \(fib(n)\).

    \begin{equation}
    fib(n)=\begin{cases}
        0, & \text{if $n=0$}.\\
        1, & \text{if $n=1$}.\\
        fib(n-1) + fib(n-2), & \text{otherwise}.
    \end{cases}
    \end{equation}

    Vérifiez vos résultats pour les premiers nombres de la suite: 0, 1, 1, 2, 3, 5, 8, 13, 21, 34, 55, 89, ...