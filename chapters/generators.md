# Les Générateurs

Si vous avez lu le chapitre précédent, vous savez que les itérateurs sont des objets qui sont régulièrement utilisés dans les boucles "for". En d'autres mots, les itérateurs sont des objets qui implémentent le protocole d'itération. Un générateur Python est un moyen pratique d'implémenter un itérateur. Au lieu d'une classe, un générateur est une fonction qui retourne une valeur à chaque fois que le mot-clé "yield" est utilisé. Voici l'exemple d'un générateur qui compte les valeurs entre deux nombres:

```Python
def myrange(a, b):
    while a < b:
        yield a
        a += 1
```

Tout comme les itérateurs, les générateurs peuvent être utilisés dans une boucle "for":

```Python
>>> for value in myrange(1, 4):
...     print(value)
...
1
2
3
```

Sous le capot, les générateurs se comportent d'une manière semblable aux itérateurs:

```Python
>>> seq = myrange(1,3)
>>> next(seq)
1
>>> next(seq)
2
>>> next(seq)
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
StopIteration
```

La chose intéressante à propos des générateurs est le mot-clé "yield". Le mot-clé "yield" fonctionne de manière similaire au mot-clé "return", mais à la différence de "return", il permet à la fonction de reprendre son exécution. En d'autres mots, à chaque fois que la valeur suivante d'un générateur est demandée, Python réveille la fonction et reprend son exécution depuis la ligne commençant par "yield" comme si la fonction ne s'était jamais interrompue.

Les fonctions générateurs peuvent utiliser d'autres fonctions à l'intérieur d'elles-mêmes. Par exemple, il est très courant d'utiliser la fonction "range" pour itérer sur une suite de nombres.

```Python
def squares(n):
    for value in range(n):
        yield value * value
```

## Exercices avec les générateurs

1.  Implémentez un générateur appelé "squares" qui produit (yield) les carrés de tous les nombres de \(a\) à \(b\). Testez-la avec une boucle "for"" et imprimez chacune des valeurs produites.

2.  Créez un générateur qui produit tous les nombres pairs de 1 à \(n\).

3. Créez un autre générateur qui produit tous les nombres impairs de 1 à \(n\).

4.  Implémentez un générateur qui renvoie tous les nombres de \(n\) positif jusqu'à 0. 

5. Créez un générateur qui renvoie la suite de Fibonnaci en commençant par le premier élément jusqu'à \(n\). Les premiers nombres de la suite sont: 0, 1, 1, 2, 3, 5, 8, 13, 21, 34, 55, 89, ...

6.  Implémentez un générateur qui renvoie toutes les paires consécutives de nombres de 0 à \(n\),, sou sla forme (0, 1), (1, 2), (2, 3)...