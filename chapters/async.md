# La Programmation Asynchrone

Jusqu'ici nous avons fait de la *programmation synchrone*. L'exécution d'un programme synchrone est assez simple: le programme démarre à la première ligne, et ensuite chaque ligne est exécutée jusqu'à ce que le programme atteigne sa fin. Chaque fois qu'une fonction est appelée, le programme attend que la fonction retourne avant de continuer à la ligne suivante. 

En programmation asynchrone, l'exécution d'une fonction est habituellement non-bloquante. En d'autres termes, chaque fois que vous appelez une fonction celle-ci retourne immédiatement. Néanmoins cette fonction n'est pas nécessairement exécutée tout de suite. Il y a généralement un mécanisme (appelé le "scheduler") qui est responsable de l'exécution future de la fonction.

Le problème avec la programmation asynchrone est qu'un programme peut s'arrêter avant le démarrage de la moindre fonction asynchrone. Une solution habituelle à ce problème  est que les fonction asynchrones retournent des "futures" ou "promises". Ce sont des objets qui représentent l'état d'exécution d'une fonction asychrone. Enfin, les frameworks de programmation asynchrone ont typiquement des mécanismes pour bloquer ou attendre que ces fonctions asynchrones finissent leur travail, mécanismes basés sur ces objets "futures".

Depuis Python 3.6, le module "asyncio" combiné avec les mots-clés *async* et *await* nous permet d'implémenter ce qu'on appelle des *programmes multitâches coopératifs*. Dans ce type de programmation, une fonction coroutine cède le contrôle volontairement à une autre fonction coroutine lorsqu'elle est inactive ou qu'elle attend de nouvelles données.

Considérez la fonction asynchrone suivante qui met au carré un nombre et dort une seconde avant de retourner. Les fonctions asynchrones sont déclarées avec **async def**. Ignorez le mot-clé **await** pour l'instant:

```Python
import asyncio

async def square(x):
    print('Square', x)
    await asyncio.sleep(1)
    print('End square', x)
    return x * x

# Créez une boucle d'événements
loop = asyncio.get_event_loop()

# Exécutez une fonction asynchrone et attendez qu'elle arrive à son terme

results = loop.run_until_complete(square(1))
print(results)

# Fermez la boucle
loop.close()
```

La boucle d'événements (<https://docs.python.org/3/library/asyncio-eventloop.html>) est, entre autres, le mécanisme Python qui organise l'exécution des fonctions asynchrones. Nous utilisons la boucle pour faire tourner la fonction jusqu'à complétion. Elle est le mécanisme de synchronisation qui s'assure que l'expression print suivante ne soit pas exécutée tant que nous avons des résultats.

L'exemple précédent n'est pas un bon exemple de programmation asynchrone parce que nous n'avons pas besoin de tant de complexité pour n'exécuter qu'une seule fonction. Néanmoins, imaginez que vous ayez besoin d'exécuter la fonction `square(x)` trois fois, comme ceci:

```python
square(1)
square(2)
square(3)
```

Since the `square()` function has a sleep function inside, the total execution time of this program would be 3 seconds. However, given that the computer is going to be idle for a full second each time the function is executed, why can't we start the next call while the previous is sleeping? Here's how we do it:

Puisque la fonction `square()` contient une fonction sleep, l'exécution totale de ce programme devrait prendre 3 secondes. Néanmoins, puisque l'ordinateur va rester inactif pendant une seconde complète chaque fois que la fonction est exécutée, pourquoi ne pas démarrer l'appel suivant pendant que le précédent dort ? Voici comment faire:

```Python
# Exécutez la fonction async et attendez qu'elle se termine
results = loop.run_until_complete(asyncio.gather(
    square(1),
    square(2),
    square(3)
))
print(results)
```

Pour l'essentiel, nous utilisons ``asyncio.gather(*tasks)`` pour informer la boucle d'attendre que toutes les tâches soient finies. Puisque les coroutines démarreront à peu près au même moment, le programme devrait tourner seulement 1 seconde. La fonction **gather()** du module Asyncio n'exécutera pas nécessairement les coroutines dans l'ordre, bien qu'elle retournera une liste de résultats.

```Python
$ python3 python_async.py
Square 2
Square 1
Square 3
End square 2
End square 1
End square 3
[1, 4, 9]
```

Parfois on peut avoir besoin de résultats aussitôt qu'ils sont disponibles. Pour cel nous pouvons utiliser une seconde coroutine qui gère chacun des résultats en utilisant ``asyncio.as_completed()``:

```Python
(...)

async def when_done(tasks):
    for res in asyncio.as_completed(tasks):
        print('Result:', await res)

loop = asyncio.get_event_loop()
loop.run_until_complete(when_done([
    square(1),
    square(2),
    square(3)
]))
```

Cela imprimera quelque chose comme:

```Python
Square 2
Square 3
Square 1
End square 3
Result: 9
End square 1
Result: 1
End square 2
Result: 4
```

Finalement, les coroutines async peuvnt appeler **d'autres fonctions coroutines asynchrones** grâce au mot-clé **await**:

```Python
async def compute_square(x):
    await asyncio.sleep(1)
    return x * x

async def square(x):
    print('Square', x)
    res = await compute_square(x)
    print('End square', x)
    return res
```

## Exercices avec asyncio

1.  Implémentez une fonction coroutine asynchrone qui additionne deux variables et dort un nombre de secondes égal au résultat de l'addition. Utilisez la boucle asyncio pour appeler la fonciton avec deux nombres.

2.  Changez le programme précédent pour organiser l'exécution de deux appels à la fonction somme. 