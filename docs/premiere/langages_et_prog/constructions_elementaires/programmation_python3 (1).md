# Programmation - Python 3

## Les boucles

<span style='font-size:22px; '>&#128203;</span>
Retenez ceci :

Une boucle permet de **répéter** un certain nombre de fois une ou plusieurs instructions.

Il y deux types de boucles:
* les boucles bornées
* les boucles non bornées

Dans **une boucle bornée**, on connaît à l'avance le nombre de répétitions à faire.<br>
On les écrits en langage courant de la manière suivante:

**Pour** i allant de $0$ à $n$ par pas de $1$ **faire** ceci ou cela.<br>
Cette boucle se répète $n+1$ fois, car de 0 à $n$,  il y a $n+1$ entiers (le pas ici est de $1$).

Dans **une boucle non bornée**, on ne connaît pas à l'avance le nombre de répétitions à faire.<br>
Celles-ci dépendent d'une condition.<br>
En langage courant cela s'écrit:

**Tant que** une ou plusieurs conditions sont vraies(ou fausses) **faire** ceci ou cela.<br>
Le nombre de répétitions dépend de conditions.


## Les boucles bornées en Python

**La syntaxe :**

```py
for i in range(debut,fin,pas):
    instructions
```
Cette boucle fait varier i entre debut et fin sans atteindre fin...<br>
1er tour : i = debut<br>
2ème tour : i = debut + pas<br>
3ème tour : i = debut + pas + pas<br>
etc..<br>
**Si l'ajout d'un pas est supérieur ou égal à fin, la boucle se termine.**


***Exemples***
```py
for i in range(0,10,1):
    instructions
```
i vaudra 0,1,2,3,4,5,6,7,8 et 9 (en tout 10 répétitions)

```py
for i in range(0,10,2):
    instructions
```
i vaudra ....? **à remplir**

```py
for i in range(-5,10,3):
    instructions
```
i vaudra ....?    **à remplir**

```py
for i in range(10,-1,-2):
    instructions
```
i vaudra ....?    **à remplir**

Quand on souhaite faire n répétitions, il suffit d'écrire:
```py
for i in range(n):
    instructions
```
Si on veut commencer à 1 et faire n répétitions, il suffit d'écrire :
```py
for i in range(1,n+1):
    instructions
```

En Python range(n) équivaut à range(0,n,1).

Dans l'exemple ci-dessous, on fait afficher les entiers de 0 à 9 :


```python
for i in range(10) :
    print(i)
```

Ecrire un programme qui affiche les entiers de 10 à 20 :


```python
#écrire ici
```

Dans l'exemple ci-dessous, on fait afficher une table de multiplication:


```python
for i in range(12):
    print(i," x 7 = ",7*i)
```

### Exercice 1


Ecrire un programme qui affiche la table de 5


```python
# code ici
```

### Exercice 2

Faire afficher avec une boucle `for` les 25 premiers nombres impairs<br>

Résultat attendu:
1 3 5 7 9 11 13 15 17 19 21 23 25 27 29 31 33 35 37 39 41 43 45 47 49 


```python
# code ici
```

### Exercice 3

$a\times b$ signifie $\underbrace{a+a+...+a}_{\text{b fois}}$

Ecrire un programme avec une boucle `for` qui affiche résultat de $a\times b$ où $a$ et $b$ sont des entiers naturels


```python
a =  123
b = 20

#écrire votre code ici

print(produit)
print(123*20)# pour vérifier
```

### Exercice 4

Écrire un programme qui calcule et affiche la somme des entiers jusqu'à l'entier n saisi par l'utilisateur.

Dans l'exemple d'affichage ci-dessous, l'utilisateur a entré la valeur 10 après le message incitatif.
```
Entrer un entier positif : 10
La somme des entiers de 0 à 10 est 55
```


```python
#écrire ici
```

### Exercice 5

Écrire un programme avec une boucle `for`, qui calcule la somme des entiers naturels pairs jusqu'à 100.<br>
$2+4+6+...+98+100$<br>
Résultat attendu : 2550


```python
# écrire ici
```

## Les boucles non bornées en Python

**Syntaxe**
```py

while condition:
    instructions
```
Le mot clé **while** est suivi d’une expression logique : le bloc d’instruction qui suit sera exécuté tant que cette expression logique sera vraie. Cette expression logique fixe une **condition d'arrêt** à l'exécution de la boucle.
Il faut bien sûr veiller à ce que la boucle s'arrête...<br>
C'est à dire que la condition doit à un certain moment être contredite...

**Exemples**<br>
Ce programme ne s'arrêtera jamais , car jamais i ne sera supérieur ou égal à 10.
```py
i = 0
while i < 10:
    print(i)
```

### Exercice 6
Modifier le programme ci-dessus afin d'afficher les entiers de 0 à 9 et que la boucle se termine.


```python
#écrire ici
```

### Exercice 7

Le programme ci-dessous calcule la somme des 10 premiers entiers<br>
$0+1 +2+3+4+5+6+7+8+9=45$


```python
i=0
somme=0
while i<10:
    somme = somme + i
    i = i + 1
print(somme)
```

Écrire un programme avec une boucle `while`, qui calcule la somme des 101 premiers entiers naturels (0 compris).<br>
$0 + 1 +2+...+100$<br>
Résultat attendu : 5050




```python
# code ici
```

### Exercice 8

1. Écrire un programme avec une boucle `while`, qui calcule le produit des 10 premiers entiers naturels non nuls.<br>
$ 1 \times 2\times 3...\times 10$<br>
Résultat attendu : 3628800


```python
# code avec boucle while ici
```

2. Modifier le programme ci-dessus afin de l'écrire avec une boucle `for`. Le résultat doit être identique.


```python
# code avec boucle for ici
```

### Exercice 9

1. Écrire un programme avec une boucle `while`, qui calcule la somme des entiers naturels **pairs** jusqu'à 100.<br>
$2+4+6+...+98+100$<br>
Résultat attendu : 2550


```python
# code avec boucle while ici
```

2. Modifier le programme ci-dessus afin de l'écrire avec une boucle `for`. Le résultat doit être identique.


```python
# code avec for while ici
```

### Exercice 10

Écrire un programme avec une boucle `while`, qui calcule la somme des entiers naturels impairs jusqu'à 100.<br>
$1+3+5+...+99$<br>
Résultat attendu : 2500


```python
# code ici
```
