# Les Coroutines

Les coroutines de Python sont semblables aux générateurs, mais à la place de produire des données, les coroutines sont surtout utilisées pour consommer des données. En d'autres mots, les coroutines sont des fonctions qui reprennent leur activité chaque fois qu'une valeur est envoyée en utilisant la méthode `send`.

La particularité des coroutines est leur usage du mot-clé `yield` du côté droit d'une expression d'assignation. Voici un exemple d'une coroutine qui imprime les valeurs qui lui sont envoyées:

```Python
def coroutine():
    print('My coroutine')
    while True:
        val = yield
        print('Got', val)

>>> co = coroutine()
>>> next(co)
My coroutine
>>> co.send(1)
Got 1
>>> co.send(2)
Got 2
>>> co.send(3)
Got 3
```

L'appel initial à `next` est requis pour faire démarrer la coroutine. Vous pouvez voir qu'elle exécute l'expression print. Lorsque la fonction atteint l'expression `yield`, elle va attendre d'être relancée. Ensuite, à chaque fois qu'une valeur est envoyée (avec `send`), la fonction coroutine reprend depuis le `yield`, copie la valeur dans **val** et l'imprime.  

Les coroutines peuvent être refermées avec la méthode `close()`.

```Python
>>> co.close()
>>> co.send(4)
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
StopIteration
```

## Exercices avec les coroutines

1.  Créez une coroutine nommée "square" qui imprime le carré de toute valeur qui lui est envoyée.

2.  Implémentez la coroutine "minimize" qui retient et imprime la valeur minimale envoyée à la fonction.

## Les Pipelines

Les coroutines peuvent être utilisées pour implémenter des pipelines de données dans lesquelles une coroutine va envoyer des données à la coroutine suivante dans le pipeline. Les couroutines insèrent des données dans le pipeline en utilisant la méthode `send()`.

![](images/coroutine_pipeline.png)

Voici un exemple d'une petites pipeline dans laquelle les valeurs envoyées à la coroutine "producer" sont mises au carré et envoyée à la coroutine "consumer" pour être imprimées:

```Python
def producer(consumer):
    print("Producer ready")
    while True:
        val = yield
        consumer.send(val * val)

def consumer():
    print("Consumer ready")
    while True:
        val = yield
        print('Consumer got', val)
```

Comme plus haut, les coroutines doivent être "initialisées" avec `next` avant qu'aucune valeur ne puisse être envoyée.

```Python
>>> cons = consumer()
>>> prod = producer(cons)
>>> next(prod)
Producer ready
>>> next(cons)
Consumer ready

>>> prod.send(1)
Consumer got 1
>>> prod.send(2)
Consumer got 4
>>> prod.send(3)
Consumer got 9
```

Aussi, avec les coroutines, les données peuvent être envoyées vers de multiple destinations. L'exemple suivant implémente deux consommateurs dont le premier imprime seulement les nombres compris entre 0 et 10 et le second imprime seulement les nombre de 10 à 20:

```Python
def producer(consumers):
    print("Producer ready")
    try:
        while True:
            val = yield
            for consumer in consumers:
                consumer.send(val * val)
    except GeneratorExit:
        for consumer in consumers:
            consumer.close()

def consumer(name, low, high):
    print("%s ready" % name)
    try:
        while True:
            val = yield
            if low < val < high:
                print('%s got' % name, val)
    except GeneratorExit:
        print("%s closed" % name)
```

Comme plus haut, les coroutines doivent être "initialisées" avant qu'une valeur puisse être envoyée.

```Python
>>> con1 = consumer('Consumer 1', 00, 10)
>>> con2 = consumer('Consumer 2', 10, 20)
>>> prod = producer([con1, con2])

>>> next(prod)
Producer ready
>>> next(con1)
Consumer 1 ready
>>> next(con2)
Consumer 2 ready

>>> prod.send(1)
Consumer 1 got 1
>>> prod.send(2)
Consumer 1 got 4
>>> prod.send(3)
Consumer 1 got 9
>>> prod.send(4)
Consumer 2 got 16

>>> prod.close()
Consumer 1 closed
Consumer 2 closed
```

Les données sont envoyées à tous les consommateurs, mais seulement le second exécute l'expression print. Remarquez l'utilisation de l'exception `GeneratorExit`. Il peut parfois être utile d'intercepter l'exception et d'informer les coroutines en aval que la pipeline n'est plus utile.

![](images/consumers_pipeline.png)

## Exercices avec des pipelines de coroutines

1.  Implémentez une pipeline producteur-consommateur dans laquelle toutes les valeurs mises au carré par le producteur sont envoyées à deux consommateurs. L'un devrait stocker et imprimer la valeur minimum jusque là, et l'autre la valeur maximum.

2.  Implémentez une pipeline producteur-consommateur dans laquelle les valeurs mises au carré par le producteur sont envoyés à deux consommateurs, un à la fois. La première valeur devrait être envoyée au consommateur 1, la seconde valeur au consommateur 2, la troisièmme valeur à nouveau au consommateur 1, et ainsi de suite. Fermer le producteur devrait forcer les consommateurs à imprimer une liste contenant les nombres que chacun d'eux a obtenu.