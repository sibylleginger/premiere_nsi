# Types construits en Python

## 1. Types simples et types construits (ou structurés)

Tous les langages de programmation de haut niveau permettent de composer les types de base (nombres, chaînes de caractères, booléens) afin de créer des types plus complexes permettant de représenter des collections de valeurs. On appelle ces types des types construits ou types structurés. Ces types permettent de construire une collection à partir de ses éléments, de l'affecter à une variable, de la passer en paramètre à une fonction, de la retourner comme valeur d'une fonction, d'extraire ses éléments ou de modifier son contenu.

Ce chapitre introduit trois types structurés de Python: les tuples, les tableaux (plus précisément des listes spécifiques à Python) et les dictionnaires. Il revient également sur les chaînes de caractères, introduites au chapitre 2 comme un type de base, mais qui sont réalité un type construit.

## 2. Les tuples

Un tuple est constitué d'une collection ordonnée d'éléments. Il correspond à un p-uplet en mathématiques. Un tuple avec deux éléments est une paire, avec trois éléments un triplet, etc. Les tuples sont notés entre **parenthèses** en listant les éléments séparés par des virgules:
* si ``x`` et ``y`` sont deux nombres, le tuple ``(x, y)`` peut représenter un point
* le tuple ``(10, 'juillet', 2020)`` peut représenter une date
* si ``p`` et ``q`` sont des entiers, ``(p, q)`` peut représenter la fraction p/q.

Un tuple peut être affecté à une variable et une fonction peut retourner un tuple :


```python
position = (100, 200)
date = (18, 'juillet', 2020)
carte = (7, 'pique')
fraction = (10, 7)

def double(x, y):
    """ 
    entrées : x et y deux entiers
    sortie : Retourne 2x et 2y (dans un tuple)
    """
    return 2*x, 2*y

print(date)
print(double(3,4))
```

    (18, 'juillet', 2020)
    (6, 8)
    

<div class="alert alert-info" role="alert" style="font-style: verdana;">

<u>Remarque</u> :
Le tuple vide est noté (). Un tuple avec un seul élément doit avoir une virgule après l'élément pour le distinguer d'une simple expression entre parenthèses : ``(10,)`` et non pas ``(10)`` qui est l'entier 10.
</div>

Pour extraire les éléments d'un tuple, on peut utiliser l'**affectation multiple** :


```python
x, y = position             # x vaut 100 y vaut 200
jour, mois, année = date    # jour = ??, mois = ??, année = ??
valeur, couleur = carte     # valeur = ??, couleur = ??
p, q = fraction             # p = ??, q = ??

print(jour)
print(y)
print(couleur)
```

    18
    200
    pique
    

Le nombre de variables à gauche de l'affectation doit correspondre au nombre d'éléments du tuple, sinon une erreur se produit :


```python
x, y, z = (1, 2, 3)
```

<div class="alert alert-info" role="alert" style="font-style: verdana;">

<u>Remarque</u> : L'affectation multiple permet d'échanger les valeurs de deux variables: ``a, b`` = ``b, a`` (les parenthèse sont optionnelles)
</div>

On peut également accéder à la valeur d’un élément grâce à la **notation indexée** ``t[i]``, où ``i`` est appelé l’indice de l’élément ``t[i]`` (voir partie sur les tableaux).

Une fonction peut prendre un tuple en paramètre:


```python
def somme(p) :
    """
    entrée : p un tuple de 3 entiers
    """
    x, y, z = p
    return x+y+z
a=(23,3,43)
t=somme(a)
print(somme(a))
# créer un tuple n, appeler la fonction avec n, et afficher le résultat.
```

    69
    

Un tuple peut contenir un tuple comme élément. L'affectation multiple peut alors récupérer ce tuple, ou bien ses éléments :


```python
personne = ("Lovelace", "Ada", (10, 'decembre', 1815), 'Londres')

nom, prenom, date, lieu = personne
print(date)

# ou alors
nom, prenom, (jour, mois, an), lieu = personne
print(mois)
```

    (10, 'decembre', 1815)
    decembre
    

Un tuple est **immuable** : une fois construit, on ne peut pas modifier son contenu. En particulier, si on construit un tuple avec des variables, ce sont les valeurs de ces variables qui sont utilisées, et le tuple ne sera pas modifié si on change les valeurs de ces variables :


```python
a = 18
b = 20
t = (a, b)
print(t)

a = 50
print(t)
t = (1,2)
t = 'bonjour'
print(t)
```

    (18, 20)
    (18, 20)
    

    Traceback (most recent call last):
      File "<input>", line 8, in <module>
    TypeError: 'tuple' object does not support item assignment
    

## 3. Les tableaux

Un tableau est une collection ordonnée d'éléments de même type. Contrairement aux tuples, les tableaux sont **mutables**, c'est-à-dire que le contenu d'un tableau peut changer après sa création. Un tableau peut servir par exemple à représenter une suite de nombres, ou la suite des mots d'un texte. Un tableau est noté entre **crochets**.

<div class="alert alert-info" role="alert" style="font-style: verdana;">

<u>Remarque</u> : Les termes « mutable » et « immutable » issus de l'anglais, sont souvent utilisés au lieu de « muable » et « immuable ».
</div>

L'accès aux éléments d'un tableau se fait par la **notation indexée** ``t[i]``, où ``i`` est appelé l'**indice** de l'élément ``t[i]`` (le ``i+1``ème élément du tableau).<br>
Le premier élément du tableau est à l'indice 0 et le nombre d'éléments d'un tableau est donné par ``len(t)``. Le dernier élément est donc à l’indice ``len(t)-1``


```python
premiers = [1, 2, 3, 5, 7, 11, 13, 17, 19, 23]
print('le cinquième nombre premier est', premiers[4]) # 1er indice = 0
for i in range(len(premiers)): # i va de 0 à len(premiers)-1
    print('indice', i, '->', premiers[i])
```

    le cinquième nombre premier est 7
    indice 0 -> 1
    indice 1 -> 2
    indice 2 -> 3
    indice 3 -> 5
    indice 4 -> 7
    indice 5 -> 11
    indice 6 -> 13
    indice 7 -> 17
    indice 8 -> 19
    indice 9 -> 23
    

<div class="alert alert-info" role="alert" style="font-style: verdana;">

<u>Remarque</u> : Un tableau vide est noté [].
</div>

Si l'on tente d'accéder à un élément avec un indice en dehors du tableau, on obtient une erreur :


```python
premiers[20]
```

    Traceback (most recent call last):
      File "<input>", line 1, in <module>
    IndexError: list index out of range
    

On peut **parcourir** les éléments d'un tableau comme indiqué ci-dessus, avec une boucle et un indice qui va de 0 à sa longeur – 1 (``for i in range (len(t))``).

On peut parcourir un tableau pour rechercher une valeur, faire des calculs sur ses éléments...

Si l'on n'a pas besoin de la valeur de l'indice, on peut aussi énumérer les éléments directement avec l'instruction ``for e in t``. Dans ce cas, la variable de boucle ``e`` prend les valeurs des éléments du tableau :


```python
for element in premiers:  # n vaut les éléments successifs du tableau.
    print(element, 'est un nombre premier')

for i in range(len(premiers)) : # i vaut les indices successifs du tableau
    print(premiers[i])
```

    1 est un nombre premier
    2 est un nombre premier
    5 est un nombre premier
    9 est un nombre premier
    2 est un nombre premier
    1
    2
    3
    5
    7
    11
    13
    17
    19
    23
    

Comme pour les chaînes de caractères, on peut créer de nouveaux tableaux à partir de tableaux existants par **concaténation** (opérateur ``+``) et par répétition (opérateur ``*``):


```python
pairs = [2, 4, 6, 8, 10]
impairs = [1, 3, 5, 7, 9]
nombres = pairs + impairs
couleurs = ['trefle', 'pique'] + ['coeur', 'carreau']
zeros = [0] * 100           # tableau de 100 éléments, qui valent tous 0
cycle = [1, 2, 3]* 10       # 10 fois la séquence 1, 2, 3

print(nombres)
print(couleurs)
print(cycle)
```

    [2, 4, 6, 8, 10, 1, 3, 5, 7, 9]
    ['trefle', 'pique', 'coeur', 'carreau']
    [1, 2, 3, 1, 2, 3, 1, 2, 3, 1, 2, 3, 1, 2, 3, 1, 2, 3, 1, 2, 3, 1, 2, 3, 1, 2, 3, 1, 2, 3]
    

<div class="alert alert-info" role="alert" style="font-style: verdana;">

<u>Remarque</u> : on peut également utiliser la notation indexée, l'énumération, la concaténation et la répétition avec les **tuples**
</div>
    
Contrairement aux tuples, les tableaux sont des types mutables : on peut modifier leur contenu. Pour modifier un élément de tableau, on utilise la notation indexée à gauche d'une **affectation** :


```python
t = [1, 2, 3]
for i in range(len(t)):
    print(t)
    t[i] = t[i] * 2     # double la valeur du i-éme élément
print(t)
```

    [1, 2, 3]
    [[1, 2, 3, 1, 2, 3], 2, 3]
    [[1, 2, 3, 1, 2, 3], [[1, 2, 3, 1, 2, 3], 2, 3, [1, 2, 3, 1, 2, 3], 2, 3], 3]
    [[1, 2, 3, 1, 2, 3], [[1, 2, 3, 1, 2, 3], 2, 3, [1, 2, 3, 1, 2, 3], 2, 3], [[1, 2, 3, 1, 2, 3], [[1, 2, 3, 1, 2, 3], 2, 3, [1, 2, 3, 1, 2, 3], 2, 3], 3, [1, 2, 3, 1, 2, 3], [[1, 2, 3, 1, 2, 3], 2, 3, [1, 2, 3, 1, 2, 3], 2, 3], 3]]
    

Les éléments d'un tableau doivent être d'un **même type** et doivent avoir une **taille statique** (on ne peut pas modifier sa taille), même si Python n'impose pas cette contrainte.

Ce type peut être un type de base, comme dans les exemples ci-dessus, mais aussi un type construit, comme un tuple ou un tableau, ce qui permet de représenter des données complexes.

Par exemple, un tableau peut contenir un ensemble de coordonnées (x, y), ou l'ensemble des cartes d'un jeu de carte, ou une main d'un joueur. Inversement, un tuple peut contenir des tableaux comme élément. Par exemple on peut représenter le joueur d'un jeu de cartes par un tuple constitué de son nom, du tableau de ses cartes, et de son score :


```python
# tableau de tuples
cartes = [("as", "pique"), (10, "trefle"), ("valet", "trefle"), (18, "coeur"), (5, "pique")]
#tuple avec le tableau cartes comme second élément
joueur = ("Joe", cartes, 120)

print(joueur)
```

### 3.1. Remarque : les listes

Dans le langage Python, il n’y a pas de type construit ayant la même structure que les tableaux. Ainsi on utilisera un type construit appelé **liste** (list).

Ce type se comporte comme un tableau mais a la particularité de pouvoir ajouter et retirer des éléments de sa liste, alors que dans beaucoup de langages de programmation ce type n’existe pas et la taille d'un tableau est fixée à sa création.
On dit qu'une liste a une **taille dynamique**.

Pour ajouter et retirer des éléments d'une liste, on utilise des **méthodes**. Une méthode est une fonction associée à un type d'objet. On l'appelle en utilisant la notation pointée ``objet.methode(parametres)``. Les méthodes qui permettent de modifier le contenu d'une liste sont les suivantes :


```python
liste = [1,5,2,3,4]

liste.append(5)
print(liste)

liste.insert(2, 6)
print(liste)

p = liste.pop(2)
print(p)
print(liste)

liste.remove(5)
print(liste)

liste.clear()
print(liste)
```

    [1, 5, 2, 3, 4, 5]
    [5, 3]
    [1, 5, 6, 2, 3, 4, 5]
    6
    [1, 5, 2, 3, 4, 5]
    [1, 2, 3, 4, 5]
    []
    

La méthode **``append``** ajoute l'élément en paramètre à la fin de la liste

La méthode **``insert(i,v)``** ajoute l'élément v à l'indice i

La méthode **``pop(i)``** supprime l'élément d'indice i de la liste et le retourne

La méthode **``remove(v)``** supprime l'élément de valeur v de la liste (1ere occurrence) et erreur si l'élément n'est pas dans la liste

La méthode **``clear``** supprime tous les éléments de la liste (liste vide)

En Python on manipulera donc des listes et non des tableaux, mais les tableaux sont utilisés dans d'autres langages comme Java ou C/C++, il est donc important de connaître leurs différences.

### 3.2. Liste donnée en compréhension

Plutôt que de remplir un tableau par énumération de ces éléments dans une boucle, on peut définir des listes en compréhension, c'est-à-dire des listes dont le contenu est défini par filtrage du contenu d'une autre liste.

#### a. Boucle classique

On commence par créer une liste vide, puis, on ajoute grâce à une boucle les éléments un à un à la liste grâce à la méthode append().

Voici par exemple comment créer une liste contenant les puissances de 2 de $2^0$ à $2^{12}$ 


```python
L = []
for i in range(13):
    L.append(2**i)

print(L)
```

#### b. Ecriture en compréhension

Cette construction syntaxique offre des avantages de lisibilité et de concision et se rapproche de la notation utilisée en mathématiques :

$S=\{2^{n} | n\in {\mathbb{N*}}, n<13\}$


```python
L = [2**n for n in range(13)]
print(L)
```

On peut même ajouter des conditions, exemple ici on crée une liste des puissance de 2 des puissance paires (il est également possible d'ajouter l'instruction ``else``).


```python
L = [2**n for n in range(13) if n % 2 == 0]
print(L)
```

### 3.3. Listes à deux dimensions: les matrices

Pour représenter un tableau à 2 dimension, on peut utiliser une liste de liste.

\begin{pmatrix} 1 & 2 & 3\\ 4 & 5 & 6\\ 7 & 8 & 9 \end{pmatrix}


```python
M = [[1, 2, 3],
     [4, 5, 6],
     [7, 8, 9]]
print(M)
```

#### a. Accès aux éléments

On accède alors aux éléments en précisant l'index de ligne et le colonne: ``M[i_ligne][i_colonne]``.

Par exemple pour accéder au troisième élément de la première ligne.


```python
print(M[0][2])

#Accés au deuxième élément de la troisième ligne.
print("??")
```

#### b. Accès aux lignes et colonnes

L'accés à une ligne est aisé, par exemple pour la deuxième ligne.


```python
M[1]
```

On peut donc utiliser une boucle pour parcourir les lignes :


```python
for ligne in M :
    print(ligne)

print('ou alors')

for i in range(len(M)) :
    print("??")
```

L'accés aux colonnes est plus délicat, on peut utiliser une liste en compréhension ou une boucle, par exemple pour accéder à la première colonne.


```python
colonne1 = [ligne[0] for ligne in M]
print(colonne1)

colonne2 = []
for ligne in M :
    #??
print(colonne2)
```

#### c. Itérations sur les valeurs

Comme il s'agit d'une structure imbriquée, nous devons utiliser deux boucles imbriquées.

On peut par exemple itérer sur les valeurs des lignes.


```python
for ligne in M:
    for val in ligne:
        print(val)

print("ou avec les indices")

for i in range(len(M)) :
    for j in range(len(M[0])) :
        print("??")
```

## 4. Les chaînes de caractères

Les chaines de caractères ont été introduites au chapitre 2 comme un type de base. Elles ont cependant certaines caractéristiques en commun avec les tableaux :
* on peut obtenir la longueur d'une chaîne ch par la fonction Python ``len(ch)``
* on peut accéder aux caractères de la chaîne avec la notation indexée ``ch[1]``. Cependant les chaines sont immuables: on ne peut pas modifier leur contenu. L'affectation ``ch[i] = "X"`` provoque une erreur
* on peut parcourir les caractères d'une chaîne par ``for car in ch:``

On peut créer un tableau à partir d'une chaîne de caractères ``chaine`` en « découpant » celle-ci :
* avec la fonction ``list(chaine)`` (constructeur) qui retourne une liste contenant les caractères de ``chaine``.
* avec la méthode ``chaine.split(separateur)``, qui prend en argument une autre chaine de caractères ``separateur`` et retourne un tableau contenant les éléments de chaine initialement séparés par separateur.

A l'inverse, la méthode ``join`` crée une chaîne de caractères en « collant » ensemble les éléments d'un tableau de chaînes avec un séparateur :


```python
phrase = "Il fait beau"

lettres = list(phrase)      # lettres = ?
mots = phrase.split(' ')    # mots = ?
mots[1] = 'fera'            # mots = ?
phrase = ' '.join(mots)     # phrase = ?
```

<div class="alert alert-info" role="alert" style="font-style: verdana;">

<u>Remarque</u> : split en anglais peut signifier « séparer » ou « scinder ».
</div>

## 5. Les dictionnaires

Un **dictionnaire** est une table associative qui fait correspondre des **clés** à des **valeurs** de type quelconque.

Les clés doivent être d'un type immuable, donc soit des nombres, soit des chaînes de caractères, soit des tuples à condition que ceux-ci ne contiennent que des éléments eux-mêmes immuables.

Dans la majorité des cas, les clés sont des chaînes de caractères, ce qui explique le nom de dictionnaire, qui associe à chaque mot sa définition.

Un dictionnaire est noté entre **accolades** {...}. Chaque entrée est notée par sa clé, suivi de sa valeur séparées par un ``:``.


```python
# Un dictionnaire au sens usuel du terme
langages = {
    "Python": "Langage très populaire au début du 21e siècle",
    "Javascript": "Langage popularisé par l'avènement du Web",
}

#Ici les clés sont des villes et les valeurs des listes de températures
temperatures = {
    "Paris": [(10, 20), (11, 21), (8, 17), (6, 18), (7, 15), (18, 14), (12, 17)],
    "Montreal": [(0, 5), (-2, 4), (-5, -1), (-2, 6), (2, 4), (3, 7), (1, 10)]
}

#Ici les clés sont des tuples (nom, prénom) et les valeurs sont des tuples (date et lieu de naissance)
personnes = {
    ("Lovelace", "Ada"): (10, 'decembre', 1815, 'Londres'),
    ("von Neumann", "John"): (28, 'decembre', 1983, 'Budapest'),
    ("Turing", "Alan"): (23, 'juin', 1912, 'Londres')
}
```

<div class="alert alert-info" role="alert" style="font-style: verdana;">

<u>Remarque</u> : Un dictionnaire vide est noté {}
</div>

L'accès à une entrée d'un dictionnaire utilise la notation indexée, comme pour les tableaux, mais ici l'indice doit être la clé :


```python
print(langage["Python"])
temp_paris = temperatures["Paris"]
personnes[("Lovelace", "Ada")]
```

Si l'entrée n'existe pas, on obtient une erreur.


```python
langages["Ada"]
```

On peut tester la présence ou l'absence d'une clé avec l'opérateur ``in``:


```python
if "Paris" in temperatures:
    print(temperatures["Paris"])

if "Python" not in langages:
    print("Il manque Python !")
```

On peut parcourir les clés d'un dictionnaire de la même façon qu'un tableau, afin d'accéder aux valeurs :


```python
for lang in langages: # lang vaut successivement les clés du dictionnaire
    print(lang,':', langages[lang])
```

Les dictionnaires sont des types **mutables** : on peut ajouter des entrées, changer leur valeur, et les retirer.


```python
#ajout d'une entrée
langages["Ada"] = "Langage nommé en hommage à Ada Lovelace"
print(langages)

#modification d'une entrée existante
langages["Python"] = "Langage populaire pour l'enseignement"
print(langages)

#retrait d'une entrée.'del' est une instruction: pas de parenthèses
del langages["Javascript"]
print(langages)
```

Enfin, on peut récupérer le contenu d'un dictionnaire avec les méthodes ``keys`` (clés), ``values`` (valeurs) et ``items`` (paires clés/valeurs):


```python
dico = {"a" 18, "b": 20, "c" : 30}
cles = dico.keys()      # retourne la liste ["a", "b", "c"]
valeurs = dico.values() # retourne la liste [10, 20, 30]
items = dico. items()   # retourne la liste de tuples [("a", 10). ...]
# ces listes peuvent être parcourues avec for ... in:'
# Exemple affichage des éléments d'un dictionnaire :
for cle, valeur in dico.items():
    print(cle + ":" + str(valeur))
```

## Valeurs et références

Lorsque l'on affecte une valeur d'un type construit à une variable, on affecte en réalité une **référence** à cette valeur. Lorsque l'on affecte cette variable à une autre variable, les deux référencent alors la même valeur. On dit que les deux variables sont des **pointeurs** vers la même valeur.

Les pointeurs peuvent être source de confusion et d'erreurs lorsqu'ils référencent des valeurs mutables, car la modification du contenu de cette valeur par une variable affecte la valeur de l'autre variable.

Dans l'exemple suivant, après la ligne 2, les variables a et b référencent le même tableau. Lorsque l'on change la valeur de l'élément ``a[1]`` (ligne 3), on constate que la valeur référencée par ``b`` a également changé (ligne 4).


```python
L = [9, 2]
M = L
L[0] = "w"
print(M)
```

**Pour mieux comprendre :** https://www.youtube.com/watch?v=_jN8PWnqNks&ab_channel=ProfesseurKarr%C3%A9

Si l'on veut que ``M`` désigne une copie de ``L``, on peut utiliser la méthode ``copy()`` des liste (qui est aussi disponible pour les dictionnaires) :


```python
a = ["x", "y", "z"]

#copier le tableau a
b = a.copy()
a[1] = "w"

print(b)
```

## Pour résumer

| Quel type construit ? | Modifiable (Mutable) | Taille | Indicé (par quoi) | Caractère d’initialisation |
|:------------|:-------|:--------|:-------|:---------|
| Tuple | Non | Statique | Oui (un nombre) | ( ) |
| Liste | Oui | Dynamique | Oui (un nombre) | [ ] | 
| Dictionnaire | Oui | Dynamique | Oui (par clé) | { } |


**Opération sur les listes**

| Opération | Résultat |
|:----------|:---------|
| ``tab.append(x)`` | Ajoute l’élément x à la fin du tableau tab |
| ``tab[i] = x`` | Modifie le tableau et affecte la valeur x à la case d’indice i (qui doit auparavant exister) |
| ``tab.insert( i , v)``| Insère l’élément x dans le tableau tab, de façon à ce que l’élément ait l’indice i et décale les éléments suivants |
| ``tab.remove(x)`` | Supprime du tableau tab le premier élément dont la valeur est égale à x |
| ``tab.pop()`` | Supprime le dernier élément du tableau tab, et renvoie sa valeur |
| ``tab.pop(i)`` | Supprime du tableau tab l’élément à la position i et renvoie sa valeur |


**Opération sur les tuples et les liste**

| Opération | Résultat |
|:----------|:---------|
| ``x in s`` | Renvoie True si un élément de s est égal à x, False sinon|
|``x not in s``|Renvoie True si aucun élément de s n’est égal à x, False sinon|
|``len (s)``|Renvoie le nombre d’éléments de s|
|``s == s1``|Renvoie True si s et s1 sont de même type, ont la même longueur, et ont des éléments égaux 2 à 2|
|``s[i]``|Renvoie l’élément d’indice i de s. le premier élément a pour indice 0|
|``s[ i : j]``|Renvoie une partie de s de l’indice i à j non inclus|
|``s[ i : j : pas]``|Renvoie une partie de s de l’indice i à j non inclus, avec un pas|
|``s.index(x)``|Renvoie l’indice de la première apparition de x dans s|
|``s.count(x)``|Renvoie le nombre d’apparitions de x dans s|
|``s + t``|Renvoie une nouvelle séquence (tableau ou tuple), concaténation de s et t (qui doivent avoir le même type)|

**Opération sur les dictionnaires**

| Opération | Résultat |
|:----------|:---------|
|``dict[cle1]``|Renvoie la valeur associée à la clé  : cle1|
|``len(dict)``|renvoie le nombre d’éléments du dictionnaire dict|
|``dict1 == dict2``|renvoie True si dict1 et dict2 sont égaux (mêmes éléments)|
|``x in dict.values()``|Renvoie True si une valeur du dictionnaire dict est égale à x, False sinon|
|``x not in dict.values()``|Renvoie True si aucune valeur du dictionnaire dict n’est égale à x, False sinon|
|``x in dict.keys()``|Renvoie True si une clé du dictionnaire dict est égale à x, False sinon|
|``dict[cle1] = v``|Modifie la valeur v associée à la clé cle1 ou l’ajoute si elle n’existe pas déjà|
|``dict.pop(cle1)``|Enlève du dictionnaire la clé cle1 et renvoie sa valeur associée|


```python

```



## Exercices

### Exercice 1 :

On représente une personne par un tuple ``(nom, date)`` où ``nom`` est lui-même un tuple formé du prénom et du nom, et ``date`` est la date de naissance représentée par un tuple ``(j, m, a)`` où ``j`` est le jour du mois, ``m`` le numéro du mois (de 1 à 12) et ``a`` l'année.

Écrire une fonction qui prend une personne en paramètre et retourne un tuple formé du nom de famille et de l'année de naissance. Testez votre fonction en créant la personne de votre choix.


```python

```

### Exercice 2 :

On définit une carte comme un tuple ``(valeur, couleur)``. ``valeur`` est un entier de 2 à 14 inclus, où 11 représente le Valet, 12 la Dame, 13 le Roi et 14 l'As. ``couleur`` est une chaîne de caractères parmi « Pique », « Coeur », « Carreau », « Trèfle ».

1. Écrire une fonction ``carte_valide`` qui prend un tuple en paramètre et retourne un booléen qui indique s'il représente une carte valide ou non.


2. Écrire une fonction ``nom_carte`` qui prend un tuple représentant une carte en paramètre et retourne une chaîne de caractères avec le nom de la carte, par exemple  ``nom_carte(14,"Trèfle")`` doit retourner ``"As de Trèfle"``.


3. Écrire un programme qui crée une liste contenant toutes les cartes d'un jeu de 52 cartes.


```python
def carte_valide(carte) :
    valeur, couleur = carte
    if valeur >= 2 and valeur <= 14 :
        if couleur in ['Pique', 'Coeur', 'Trèfle', 'Carreau'] :
            return True
    return False

carte = (45,'bonjour')

print(carte_valide(carte))
```

    True
    

### Exercice 3 :

1. Écrire (sans utiliser la fonction Python ``sum``) une fonction qui prend en paramètre une liste de nombres et retourne le total de ses éléments.

2. L'adapter pour écrire une fonction ``moyenne`` qui calcule la moyenne des éléments de la liste.


```python
def somme(liste) :
    total = 0
    for nombre in liste :
        #ajout de la valeur au total
        total = total + nombre
    total = total / len(liste)
    return total
        
nombres = [4,5,2,7]
print(sum(nombres))
```

    18
    

### Exercice 4 :

Écrire (sans utiliser ``min``) une fonction qui prend en paramètre une liste et retourne son plus petit élément.


```python
def mini(liste) :
    valeur_mini = liste[0]
    #code


nombres = [4,5,2,7]
print(mini(nombres))
```

### Exercice 5 :

Écrire une fonction ``recherche`` qui prend en paramètres une liste t et une valeur v, et retourne ``True`` si v est dans la liste t et ``False`` sinon.


```python

```

### Exercice 6 :

Écrire une fonction ``palindrome`` qui prend en paramètre une chaîne de caractères et retourne ``True`` si c'est un palindrome, c'est-à-dire s'il peut se lire dans les deux sens, comme le mot ``"ressasser"``.


```python

```

## Pour les plus rapides

### Exercice 7 :

Pour cet exercice vous pouvez réutiliser le code de l'exercice 1.

1. Écrire une fonction ``piocher`` qui prend un paramètre ``paquet`` représentant une liste de cartes et enlève la première carte du paquet et la retourne.


2. Écrire une fonction ``ajouter_carte`` qui prend en paramètres une liste de cartes et une carte, et ajoute la carte à la fin du paquet. Attention à bien vérifier que la carte est valide!


3. À l'aide de la fonction ``random()`` de la bibliothèque random, écrire une fonction ``piocher_hasard`` qui prend un paramètre ``paquet`` représentant une liste de cartes et retourne une carte tirée au hasard dans le paquet (l'enlever de la liste).


```python

```

### Exercice 8 :

1. Écrire une fonction ``inverse_liste`` qui prend en paramètre une liste et retourne une liste avec les mêmes éléments en ordre inverse.


2. Écrire une fonction ``inverse_chaine`` qui fait la même chose pour une chaîne de caractères. Peut-on utiliser la fonction ``inverse_liste`` ?


```python

```

### Exercice 9 :

1. Écrire une fonction ``melanger`` qui prend une liste en paramètre et retourne une liste avec les mêmes éléments dans un ordre aléatoire.
    **Indication** : on utilisera la méthode ``pop`` des listes et la fonction ``randint`` de la bibliothèque ``random``.


2. Appliquer cette fonction au tableau des 52 cartes de l'exercice 4.


```python

```

### Exercice 10 :

Dans le jeu de la Bataille, à chaque tour de jeu, chaque joueur pose une carte sur la table puis on établit celle qui l'emporte: un 3 bat un 2, un Valet bat un 10, un As bat un Roi...
Dans cet exercice, vous pouvez réutiliser le code des exercices 4 et 6.

1. Écrire une fonction ``duel`` qui prend deux tuples représentant deux cartes en paramètre et retourne 0 en cas d'égalité, 1 si la première carte gagne, 2 si c'est la seconde.


2. À l'aide des fonctions ``piocher`` ou ``piocher_hasard``, écrire une fonction ``jouer`` qui prend en paramètre une liste de cartes. Cette fonction tire deux cartes du paquet et les met en duel. En cas d'égalité, elle tire deux nouvelles cartes jusqu'à ce qu'un joueur gagne. La fonction retourne un tuple formé du numéro du gagnant et du nombre de duels.


3. Ecrire un programme qui simule une partie de bataille avec un paquet de 52 cartes mélangé et 2 joueurs. La partie se termine quand il n'y a plus le carte dans le paquet. Afficher à chaque manche le gagnant et le nombre de duels. A la fin de la partie afficher le joueur ayant remporté le plus de manches.


```python

```

### Exercice 11 :

Le jeu de la Belote ressemble à la Bataille, mais la couleur (Pique, Coeur, etc.) compte. À chaque manche, une certaine couleur est appelée « atout » et bat toutes les autres couleurs.

1. Écrire une fonction ``manche_simple`` qui prend en paramètres l'atout courant et un dictionnaire de la forme ``("joueur": carte)`` qui indique la carte jouée par chaque joueur. Cette fonction doit retourner le nom du joueur qui remporte cette manche, sachant qu'une carte de la couleur de l'atout bat systématiquement une carte d'une autre couleur. Par exemple, si l'atout est Trèfle, un 2 de Trèfle bat un Roi de Carreau, et un 7 de Coeur bat un 6 de Pique. En cas d'égalité, l'un des joueurs ex-aequo l'emporte.


2. Écrire une fonction ``manche_belote`` qui fait la même chose que ``manche_simple``, sauf que pour la couleur atout, l'ordre de victoire change : le Valet (11) devient la carte la plus forte, suivie du 9; les autres cartes, de l'As (14) au 2, gardent le même ordre.


```python

```
