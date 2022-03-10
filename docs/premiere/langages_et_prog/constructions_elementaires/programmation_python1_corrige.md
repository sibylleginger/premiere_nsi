# Programmation - Python- 1

## Les variables

En informatique on utilise des données qui peuvent être des nombres, des chaînes de caractères (mots ou phrases), des booléens (Vrai ou Faux), des tableaux, etc.

Pour pouvoir les utiliser il faut les stocker dans des variables. Une variable est une petite information (une donnée) temporaire que l'on stocke dans une case de la mémoire. On dit qu'elle est "variable" car c'est une valeur qui peut changer pendant le déroulement du programme. Une variable est constituée de 2 choses :

* une valeur : c'est la donnée qu'elle stocke (par exemple le nombre 5)
* un nom : c'est ce qui permet de la reconnaître. Nous n'aurons pas à retenir l'adresse de mémoire, nous allons juste indiquer des noms de variables à la place.

Dans certains langages (C, Java . . . ), le type d'une variable doit être déclaré avant son affectation et il ne peut pas changer, on parle de typage statique.
Python est un langage à typage dynamique, c'est-à-dire que le type d'une variable peut changer après réaffectation.

**Noms des variables et bonnes pratiques :**
Dès qu'un algorithme se complexifie, il peut utiliser de nombreuses variables.  Pour éviter les conflits de noms et rendre le code compréhensibles, il y a de bonnes pratiques :

* Le nom s'écrit en minuscule et on utilise le tiret bas _  s'il est en plusieurs mots (nom_variable)
* On donne aux variables un nom significatif. Par exemple, une variable indiquant le nom d'un joueur s'appellera nom_joueur plutôt que j.
* Les mots réservés du language sont interdits.

En Python, on donne un nom à une variable et on utilise le signe = pour l'affectation :
Lors de l’exécution d’une instruction d’affectation, il y a d’abord évaluation de l’expression puis la valeur obtenue est attribuée à la variable.

Une expression est une combinaison de valeurs explicites, de variables, d’opérateurs et de fonctions qui est évaluée pour donner lieu à une valeur.

Dans le code ci-dessous, on a créé des variables dans lesquelles on a mis des valeurs

***Remarque: un # devant une ligne permet d'écrire un commentaire***


```python
# nombre1 et nombre2 contiennent des nombres entiers
nombre1 = 5
nombre2 = -7
# nombre3 contient un nombre à virgule
nombre3 = 25.12
# phrase contient une chaîne de caractère
# Les chaînes de caractères se déclarent entre quotes ".." ou '...'
phrase = "Hello World"
#test contient un booléen.
test = True

```

On peut faire afficher le contenu d'une variable avec la fonction : print(nom_de_la_variable)

***À faire : Afficher les contenus des variable***


```python
print(nombre1)
print(test)
```


```python
#affiche le mot phrase
print("phrase")

#affiche la variable phrase (si elle existe)
print(phrase)
```

On peut accèder au type de la variable avec l'instruction : **type(nom_de_la_variable)**

* 'int' si c'est un nombre entier
* 'float' si c'est un nombre flottant(à virgule)
* 'str' (string) si c'est une chaîne de caractères
* bool si c'est un booléen

***À faire : Afficher les types des variables***


```python
# à faire ici
print(type(nombre1))
print(type(nombre3))
print(type(phrase))
print(type(test))
```

## Opérations sur les variables

### L'addition +

* On peut additionner des nombres
* On peut additionner des chaînes de caractères

***À faire : Afficher les résultats des additions et le type du résultat obtenu***
* a + b
* a + c
* mot1 + mot2

***Remarque: l'addition de chaînes de caractères se nomme concaténation***


```python
a = 3
b = 7
c = 5.12
mot1 = "Hello"
mot2 = " World !"
# à faire ici
print(a + b)
print(type(a + b))

print(a + c)
print(type(a + c))

print(mot1 + mot2)
print(type(mot1 + mot2))
```

    10
    <class 'int'>
    8.120000000000001
    <class 'float'>
    Hello World !
    <class 'str'>
    

**Attention**

Que se passe-t-il si on essaie d'additionner deux variables de types différents ? Un nombre entier et un flottant ? Un nombre et une chaîne de caractères ?



```python
print(a + mot1)
```

### Messages d'erreur

Il est important de comprendre les messages d'erreur. Ils décrivent très souvent la source exacte du problème, en anglais : il faut les lire et essayer de comprendre leur signification.

Un message d'erreur vous donnera aussi toujours le numéro de la ligne qui a causé le souci. Ce numéro n'est pas toujours exact : l'ordinateur peut n'être dérangé qu'après votre erreur. Il vous faudra parfois regarder avant l'emplacement indiqué.


### La soustraction -

On ne peut soustraire que des nombres

***À faire : afficher les résultats des soustractions et le type du résultat obtenu***
* a - b
* b - a
* a - c


```python
a = 3
b = 7
c = 5.12

# à faire ici
print(a - b)
print(type(a - b))

print(b - a)
print(type(b - a))

print(a - c)
print(type(a - c))
```

### La multiplication *

* On peut multiplier deux nombres
* On peut multiplier une chaîne de caractères par un entier positif 

***À faire : Afficher les résultats des multiplications et le type du résultat obtenu***
* a*b
* a*c
* mot1*3


```python
a = 3
b = 7
c = 5.12
mot1 = "Hello"

# à faire ici
print(a * b)
print(type(a * b))

print(a * c)
print(type(a * c))

print(mot1 * 3)
print(type(mot1 * 3))
```

### La division /

On ne peut diviser que des nombres

***À faire : Afficher les résultats des divisions et le type du résultat obtenu***
* a/b
* a/c



```python
a = 4
b = 2
c = 6.32

# à faire ici
print(a/b)
print(type(a/b))

print(a/c)
print(type(a/c))
```

    2.0
    <class 'float'>
    0.6329113924050632
    <class 'float'>
    

### La division euclidienne // , %

![division](data:image/png;base64,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)


* L'instruction **a//b** donne le quotient
* L'instruction **a%b** donne le reste

***À faire : Afficher le quotient et le reste de la division euclidienne de 25 par 7, afficher également leurs types***


```python
a = 25
b = 7
# à faire ici

print(a//b)
print(type(a//b))

print(a%b)
print(type(a%b))
```

## La puissance **

Pour calculer $2^8$ on utilise l'instruction 2**8

***À faire : Afficher les différents résultats et leurs types***
* $a^8$
* $a^b$
* $b^{-4}$


```python
a = 5
b = 2.5

# à faire ici
print(a ** 8)
print(type(a ** 8))

print(a ** b)
print(type(a ** b))

print(b ** -4)
print(type(b ** -4))
```

    390625
    <class 'int'>
    55.90169943749474
    <class 'float'>
    0.0256
    <class 'float'>
    

## Comparaisons de variables

Les opérateurs de comparaisons sont :
* $<$  inférieur
* $<=$   inférieur ou égal
* $>$  supérieur
* $>=$ supérieur ou égal
* $==$ est égal à
* $!=$ est différents de

**Attention ne pas confondre l'opérateur == avec le signe = qui correspond à l'affectation!**

***Le résultat d'une comparaison est toujours un booléen***
* True si la comparaison est vraie
* False si la comparaison est Fausse

**Remarque : on ne peut comparer que des objets comparables**

***À faire : Commenter chaque instruction ci-dessous***


```python
a = 5
b = 18 
c = 12.3
mot1="Hello"
mot2="World"
#
print(a > b)
# False

print(b//a == 3)
#True

print(b%a == 3)
#True

print(a - b > 2)
#False

print(type(c) == float)
#True

print(mot1 != mot2)
#True

print(mot1 < mot2)
#True, la comparaison se fait alphabétiquement, Hello se trouve bien avant World.

print(mot1 > 2)
#Erreur, impossible de comparer une chaine de caractères et un entier
```

    False
    True
    True
    False
    True
    True
    False
    

## Combiner des comparaisons

Les opérateur **and** et **or** permettent de combiner des comparaisons.

Pour qu'une combinaison avec **and** soit vraie il faut que les comparaisons soient toutes vraies.

Pour qu'une combinaison avec **or** soit vraie il faut qu'au moins l'une des comparaisons soit vraie.

**Voici des exemples**


```python
a = 12
b = 5
c = 7

print(a>b and a>c)
# Vrai et Vrai ==> Vrai

print(a>b or a<c)
# Vrai ou Faux ==> Vrai

print(c < b and a>c)
# Faux et Vrai ==> Faux

print(b+c == a  and b < c and a//b == 2)
# Vrai et Vrai et Vrai ==> Vrai

print(a<0 or a+b > 10 or c <0)
# Faux ou Vrai ou Faux ==> Vrai
```

    True
    True
    False
    True
    True
    

## Entrées sorties

La fonction print() permet d'afficher un message à l'écran.

Pour récupérer les données saisies par l'utilisateur , on utilise la fonction input() et on affecte la donnée entrée dans une variable afin de stocker sa valeur.
Un message sous forme de chaîne de caractères (c'est-à-dire encadré par des apostrophes ou des guillemets) peut être écrit entre les parenthèses de input().


```python
nom = input("Quel est votre nom ?")
# Affichage d'un message
print("Bonjour")
# Affichage de la valeur contenue dans la variable nom
print(nom)
```

**Attention !**
La fonction input() récupère forcément des valeurs de type string (str), ce qui peut être gênant dans de nombreux programmes. En utilisant les fonctions int() ou float(), on force le changement de type.


```python
age = int(input("Quel est votre âge ?"))   # quel est le type de age ?
print(age)
```

## Exercices

### Ex 1:

Afficher le résultat de cette opération :

$a + \dfrac{2\times b -3}{c}$


```python
a = 30
b = 8
c = 7

print(a + ((2*b - 3)/c))
```

    31.857142857142858
    

### Ex 2:

Demander 2 entiers à l'utilisateur et afficher le quotient et le reste de la division euclidienne.


```python
a = int(input("Un premier entier : "))
b = int(input("Un deuxième entier : "))
print(a//b) #quotient (division entière)
print(a%b) #reste

```

    0.5833333333333334
    0
    

### Ex 3:

On considère un triangle dont les cotés mesurent : (54, 72, 90)

Afficher le résultat de la comparaison qui permet d'affirmer que ce triangle est rectangle.


```python
a = 54
b = 72
c = 90

print(a**2 + b**2 == c**2)
```

    True
    

### Ex 4 :

L'utilisateur entre deux valeurs. Voici un exemple d'affichage de console Python, où l'utilisateur a entré les valeurs 12 et 15.

```python
Entrer un nombre : 12
Entrer un autre nombre : 15
Leur somme est 27
Leur difference est -3
Leur produit est 180
```

Ecrire le programme correspondant.


```python
#écrire le programme ici
nb1 = int(input("Entrer un nombre : "))
nb2 = int(input("Entrer un autre nombre : "))
somme = nb1 + nb2
print("Leur somme est",somme)
diff = nb1 - nb2
print("Leur différence est",diff)
produit = nb1 * nb2
print("Leur produit est",produit)
```

    Entrer un nombre : 12
    Entrer un autre nombre : 15
    Leur somme est 27
    Leur différence est -3
    Leur produit est 180
    

## Autres opérations

Pour certaines opérations comme la racine carrée, l'exponentielle, le logarithme, le cosinus etc.

**Il faut importer la bibliothèque maths**

comme le montre l'exemple ci-dessous :


```python
from math import* # importe toute la bibliothèque maths

a= 81
print(sqrt(81)) # pour la racine carrée

print(cos(pi/4)) # le cosinus de 45°
```

Le coeur du langage Python est constitué d'une grammaire, de mots clefs et d'une bibliothèque de base rassemblant des instructions qui sont toujours disponibles : comme max, print, abs etc…
Par ailleurs, des bibliothèques ou modules, constituent des boîtes outils d'instructions que le programmeur peut réutiliser en important le module. La distribution standard de Python est livrée avec un ensemble de modules constituant sa bibliothèque standard.

Lorsqu'on a besoin d'utiliser une fonction de bibliothèque, on commence par explorer la bibliothèque standard dont les modules sont listés et documentés sur le site officiel https://www.python.org/. Une fois qu'on a déterminé le module qui nous intéresse, par exemple math, on dispose de plusieurs façons d'importer des instructions :

Si on a besoin juste d'une instruction comme sqrt, pour la fonction racine carrée, on peut écrire avant de l'appeler :


```python
from math import sqrt

print(sqrt(121))
```

Si on a besoin de plusieurs instructions, mais en nombre limité, comme sqrt, cos et sin, on peut écrire avant de les appeler :



```python
from math import sqrt, cos, sin
```

Si on a besoin de beaucoup d'instructions du module, on peut utiliser le joker * et écrire avant de les appeler (importe tout le module) :


```python
from math import *
```

Cette méthode peut sembler pratique mais elle est dangereuse si on importe plusieurs modules, qui contiennent des instructions avec les mêmes noms. Pour cloisonner les espaces de nommage, on préférera la méthode suivante.

Une autre méthode consiste à importer juste le module, puis on peut accéder à chacune des fonctions ou constantes qu'il contient en les préfixant du nom du module en notation pointée :


```python
import math
racine3 = math.sqrt(3)
```

Cette méthode alourdit la syntaxe mais permet un meilleur cloisonnement des noms utilisés par les différents modules utilisés dans un même programme.


```python

```


```python

```
