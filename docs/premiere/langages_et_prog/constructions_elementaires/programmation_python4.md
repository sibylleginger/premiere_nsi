# Programmation Python - 4

## Les fonctions


Une fonction permet de délocaliser une partie de code (bloc d'instructions), de lui donner un nom et éventuellement de la réutiliser.<br>
La notion de fonction en informatique est comparable à la notion de fonction en mathématiques. 

**Syntaxe**

En général, une fonction reçoit des données en **paramètres** (mais ce n'est pas toujours le cas), qui permettent de transmettre des valeurs au bloc d'instructions. A l'intérieur de la fonction, les paramètres sont traités comme des variables.<br>

Une fonction peut **retourner une valeur**. L'instruction `return` définit la valeur retournée par la fonction et interrompt son exécution. Cette valeur est ensuite récupérée là où la fonction a été appelée.

![](fonction.png)

En Python, pour déclarer une fonction on utilise la syntaxe ci-dessous avec le mot clé `def` :

```py
def ma_fonction(parametre1,parametre2,...):
    resultat = 3
    instructions
    return resultat
```
Pour exécuter une fonction, il faut **l'appeler**.

```py
print(ma_fonction(a,b,...))
# affiche le résultat de la fonction
```

**Exemple**


```python
def plus_grand2(a,b):
    """
    paramètres : a et b, 2 nombres (int ou float)
    sortie : le plus grand de 2 nombres passés en paramètres
    """
    if a > b:
        return a
    # pas besoin de else, car return termine la fonction
    return b


b = 12
c = 2
a = plus_grand2(b,c)
plus_grand2(2,11)
print(a)
help(plus_grand2)
```

    12
    Help on function plus_grand2 in module __main__:
    
    plus_grand2(a, b)
        paramètres : a et b, 2 nombres (int ou float)
        sortie : le plus grand de 2 nombres passés en paramètres
    
    


```python
def affiche_ok() :
    print("ok")
    return

def affiche_entier(x) :
    print(x)
    return

def augmentation(x) :
    x = x + 1
    return x

print(affiche_ok())
```

    ok
    None
    

### Variables locales et variables globales

Lorsqu'une fonction utilise des variables (comme les paramètres par ex), celles-ci sont normalement propres à la fonction et ne sont pas accessibles à l'extrérieur de celle-ci. On dit qu'il s'agit de **variables locales**, par opposition aux **variables globales** qui sont utilisées dans le programme principal.


```python
def f() :
    a = 5
    return a

a = 10
print(f()) # affiche 5
print(a)   # affiche 10

```

    5
    10
    

Dans l'exemple ci-dessus, la variable `a` de la ligne 1 du programme principal n'est pas la même que celle dans la fonction, bien qu'elle ait le même nom.


```python
def f(a) :
    a = a + 1
    return a

a = 10
print(f(a))  # affiche 11
a = f(a)
print(a)     # affiche 10
```

    11
    10
    

Cependant, si l'on référence dans une fonction une variable qui n'a pas été affectée dans la fonction, Python regarde s'il exite une variable globale de ce nom. Si oui, il utilise sa valeur au lieu de provoquer une erreur de type «variable indéfinie». Dans l'exemple suivant, la variable message référencée dans la fonction ``affiche``, est la variable globale message.


```python
def affiche() :
    print(message)

message = "bonjour"
affiche()
```

    hello
    

Cette règle du langage Python est une source potentielle d'erreurs, car il suffit d'ajouter une affectation pour créer une variable locale et «cacher» la variable globale de même nom.

Il est possible d'accéder à une variable globale et de modifier sa valeur dans une fonction, en utilisant le mot-clé ``global``.

Mais modifier ainsi une variable globale depuis une fonction s'appelle un **effet de bord** et est considéré comme une mauvaise pratique, on évitera donc de l'utiliser. Si une fonction doit utiliser une variable du programme principal :
* Pour accéder à sa valeur → passage de la valeur en paramètre
* Pour modifier sa valeur → modifier sa valeur dans le programme principal en lui affectant la valeur de l’appel de fonction


```python
#modifier le code afin de ne plus avoir d'effets de bord
def f_augmente(a) :
    if a%2 == 0 :
        a = a + 1
    return a

a = 10
print(f_augmente(a))
```

    11
    

### Spécifier pour expliquer et tester pour valider

Avant d'écrire le code d'une fonction, il faut d'abord spécifier ce qu'elle doit faire.
La spécification (ou documentation) est un texte en français qui va décrire l'utilisation et le fonctionnement de la fonction.
La spécification doit déterminer les conditions d'entrées des paramètres (pré-conditions), et les conditions de sortie (post-conditions).

Le langage Python permet d'associer à chaque fonction une spécification, appelée docstring, sous la forme d'une chaîne de caractères juste après la ligne de définition de la fonction. Cette chaîne de caractères est conventionnellement délimitée par trois guillemets `''' spécification '''`, ce qui permet de l'écrire sur plusieurs lignes.

Cette spécification peut servir si d'autres personnes vont devoir utiliser votre code, afin qu'il soit compréhensible et utilisable facilement. Mais c'est également important pour la phase de test du code.

Une fois que la fonction est terminée, il faut impérativement la tester, avec des cas et des valeurs différentes afin de vérifier que les conditions (d'entrées et de sorties) sont bien garanties et respectées.


## Exercices niveau 1

Pour chaque fonction, ne pas oublier sa spécification et la tester avec différentes valeurs possibles :

* Écrire une fonction plus_petit qui prend en paramètres deux nombres et qui renvoie le plus petit.
* Écrire une fonction somme2 qui prend en paramètres deux nombres et qui renvoie leur somme.


```python
def plus_petit2(a,b):
    if a < b:
        return a 
    return b
a = 2
b = 9
print(plus_petit2(a,b))
print(plus_petit2(a,b))
print(plus_petit2(1111111,2949938282))
print(plus_petit2(a,b))
```

    2
    2
    1111111
    2
    


```python
def somme2(a,b):
    return a+b

a=2
b=3
print(somme2(a,b)+2)
```

    7
    

## Exercices niveau 2

* Écrire une fonction est_pair qui prend en paramètre un entier n et qui renvoie True si il est pair et False sinon.
* Écrire une fonction est_impair qui prend en paramètre un entier n et qui renvoie True si il est impair et False sinon.
* Écrire une fonction est_diviseur qui prend en paramètre un entier n et un entier a et qui renvoie True a est un diviseur de n et False sinon.
* Écrire une fonction table_multiplication qui prend en paramètre un entier n et qui **affiche** la table de multiplication de n jusqu'à 10.


```python
def est_pair(n):
    '''
    entrée : n entier
    sortie : True si n est pair, False sinon
    '''
    if n%2 == 0:
        return True
    else :
        return False

est_pair(3)
```




    False




```python
def est_impair(n):
    '''
    entrée : n entier
    sortie : True si n est impair, False sinon
    '''
    if n%2 != 0 :
        return True
    return False
print(est_impair(3))
```

    True
    


```python
# code ici
def est_pair(n) :
    return n%2==0
print(est_pair(7))
```

    False
    


```python
def est_impair2(n) :
    return not est_pair(n)

print(est_impair2(3))
```

    True
    


```python
def est_diviseur(n,a):
    '''
    entrée : n entier, a entier
    sortie : True si n est divisible par a et False sinon
    '''
    if n%a==0:
        return True
    if n%a!=0:
        return False
    
n=3
a=3
print(est_diviseur(n,a))

```

    True
    


```python
#fonction table_multiplication qui prend en paramètre un entier n
#affiche la table de multiplication de n jusqu'à 10
def table_multiplication(n):
    for i in range(1,10+1):
        print(n,"x",i,"=",i*n)
    return
table_multiplication(10)

```

    10 x 1 = 10
    10 x 2 = 20
    10 x 3 = 30
    10 x 4 = 40
    10 x 5 = 50
    10 x 6 = 60
    10 x 7 = 70
    10 x 8 = 80
    10 x 9 = 90
    10 x 10 = 100
    


```python

```

## Exercices niveau 3

### Ex1

Voici une fonction qui prend en paramètre un entier naturel et qui renvoie la somme de ses chiffres:<br>

```py
def somme_chiffre(n):
    s = 0
    while n > 0:
        s = s + n%10
        n = n//10
    return s
```

Un nombre Harshad, ou nombre de Niven, ou nombre multinumérique est un entier naturel qui est divisible par la somme de ses chiffres.

**Par exemple** : 777 est l'un de ces nombres<br>
$7+7+7=21$ et $\dfrac{777}{21}=37$

Écrire une fonction ``est_harshad`` qui prend en paramère un entier naturel et qui retourne vrai ou faux selon si l'entier est un nombre de Harshad ou non.


```python

```
