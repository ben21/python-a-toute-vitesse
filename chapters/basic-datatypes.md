# Nombres et chaînes de caractères

Dans ce chapitre nous travaillerons avec les types de données les plus basiques, les nombres et les chaînes de caractères. Démarrez votre REPL Python et écrivez ce qui suit:

```Python
>>> a = 2
>>> type(a)
<class 'int'>
>>> b = 2.5
>>> type(b)
<class 'float'>
```

Pour l'essentiel, vous déclarez deux variables (nommées "a" et "b") qui vont contenir des nombres: la variable "a" est un nombre entier tandis que la variable "b" est un nombre réel. Nous pouvons maintenant utiliser nos variables ou n'importe quels autres nombres pour effectuer des calculs:

```Python
>>> a + b
4.5
>>> (a + b) * 2
9.0
>>> 2 + 2 + 4 - 2/3
7.333333333333333
```

Python gère également les chaînes de caractères. Les chaînes de caractères sont des suites de lettres (comme les mots) et peuvent être définies en utilisant des guillemets simples ou doubles:

```Python
>>> hi = "hello"
>>> hi
'hello'
>>> bye = 'goodbye'
>>> bye
'goodbye'
```

Vous pouvez additionner les chaînes de caractères pour les concaténer, mais vous ne pouvez pas mélanger différents types de données, tels que les chaînes de caractères et les nombres.

```Python
>>> hi + "world"
'helloworld'
>>> "Hello" + 3
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
TypeError: must be str, not int
```

Néanmoins, la multiplication fonctionne comme répétition:

```Python
>>> "Hello" * 3
'HelloHelloHello'
```

## Exercices avec les nombres

1.  Essayez les calculs mathématiques suivants et devinez ce qui se passe: \((3 / 2)\), \((3 // 2)\), \((3 \% 2)\), \((3**2)\).

    Suggestion: Ouvrez la documentation de référence de la bibliothèque Python à <https://docs.python.org/3/library/stdtypes.html#numeric-types-int-float-complex>.


2.  Calculez la moyenne des séquences de nombres suivantes: (2, 4), (4, 8, 9), (12, 14/6, 15)

3.  Le volume d'une sphère est donné par (4/3 * pi * r^3). Calculez le volume d'une sphère de radius 5. Suggestion: créez une variable nommée "pi" avec une valeur de 3.145.

4.  Utilisez l'opérateur modulo (%) pour voir lesquels the nombres suivants sont pairs: (1, 5, 20, 60/7).

    Suggestion: le reste de la division \(x/2\) est toujours zéro lorsque \(x\) est pair. 

5.  Trouvez des valeurs pour \(x\) et \(y\) telles que \(x < 1/3 < y\) retourne "True" sur la REPL Python. Suggestion: essayez \(0 < 1/3 < 1\) sur la REPL.

## Exercices avec des chaînes de caractères

En utilisant la documentation de Python sur les chaînes de caractères (<https://docs.python.org/3/library/stdtypes.html?#text-sequence-type-str>), effectuez les exercices suivants:

1.  Initialisez la chaîne "abc" dans une variable nommée "s":

    1.  Utilisez une fonction pour obtenir la longueur de la chaîne.

    2.  Ecrivez la séquence d'opérations nécessaire pour transformer la chaîne "abc" en "aaabbbccc". Sugestion: utilisez la concaténation de chaînes et les index de chaînes.

2.  Initialisez la chaîne "aaabbbccc" dans une variable nommée "s":

    1.  Utilisez une fonction qui vous permet de trouver la première occurrence de "b" dans la chaîne, et la première occurrence de "ccc".

    2.  Utilisez une fonction qui vous permet de remplacer toutes les occurrences de "a" par "x", et ensuite utilisez la même fonction pour remplacer seulement la première occurrence de "a" par "x".

3.  En commençant par la chaîne "aaa bbb ccc", de quelles suites d'opérations avez-vous besoin pour arriver aux chaînes suivantes ? Vous pouvez utiliser la fonciton "replace".

    1.  "AAA BBB CCC"

    2.  "AAA bbb CCC"
