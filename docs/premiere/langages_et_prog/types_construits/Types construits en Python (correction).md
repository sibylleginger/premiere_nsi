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
    return (2*x, 2*y)

print(date)
print(double(3,4))
```

<div class="alert alert-info" role="alert" style="font-style: verdana;">

<u>Remarque</u> :
Le tuple vide est noté (). Un tuple avec un seul élément doit avoir une virgule après l'élément pour le distinguer d'une simple expression entre parenthèses : ``(10,)`` et non pas ``(10)`` qui est l'entier 10.
</div>

Pour extraire les éléments d'un tuple, on peut utiliser l'**affectation multiple** :


```python
x, y = position             # x vaut 100 et y vaut 200
jour, mois, année = date    # jour = 18, mois = 'juillet', année 2020
valeur, couleur = carte     # valeur = 7, couleur = 'pique'
p, q = fraction             # p = 18, q = 7

print(jour)
print(y)
print(couleur)
```

Le nombre de variables à gauche de l'affectation doit correspondre au nombre d'éléments du tuple, sinon une erreur se produit :


```python
x, y = (1, 2, 3)
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

# créer un tuple n, appeler la fonction avec n, et afficher le résultat.
n = (1,2,3)
print(somme(n))
```

    6
    

Un tuple peut contenir un tuple comme élément. L'affectation multiple peut alors récupérer ce tuple, ou bien ses éléments :


```python
personne = ("Lovelace", "Ada", (10, 'decembre', 1815), 'Londres')

nom, prenom, date, lieu = personne
print(date)

# ou alors
nom, prenom, (jour, mois, an), lieu = personne
print(mois)
```

Un tuple est **immuable** : une fois construit, on ne peut pas modifier son contenu. En particulier, si on construit un tuple avec des variables, ce sont les valeurs de ces variables qui sont utilisées, et le tuple ne sera pas modifié si on change les valeurs de ces variables :


```python
a = 18
b = 20
t = (a, b)
print(t)

a = 50
print(t)
```

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
    print('indice', i, -> premiers[i])
```

<div class="alert alert-info" role="alert" style="font-style: verdana;">

<u>Remarque</u> : Un tableau vide est noté [].
</div>

Si l'on tente d'accéder à un élément avec un indice en dehors du tableau, on obtient une erreur :


```python
premiers[20]
```

On peut **parcourir** les éléments d'un tableau comme indiqué ci-dessus, avec une boucle et un indice qui va de 0 à sa longeur – 1 (``for i in range (len(t))``).

Si l'on n'a pas besoin de la valeur de l'indice, on peut aussi énumérer les éléments directement avec l'instruction ``for e in t``. Dans ce cas, la variable de boucle ``e`` prend les valeurs des éléments du tableau :


```python
for n in premiers:  # n vaut les éléments successifs du tableau.
    print(n, 'est un nombre premier')
```

Comme pour les chaînes de caractères, on peut créer de nouveaux tableaux à partir de tableaux existants par **concaténation** (opérateur ``+``) et par répétition (opérateur ``*``):


```python
pairs = [2, 4, 6, 8, 10]
impairs = [1, 3, 5, 7, 9]
nombres = pairs + impairs
couleurs = ['trefle', 'pique'] + ['coeur', 'carreau']
zeros = [0] * 100           # tableau de 100 éléments, qui valent tous 0
cycle = [1, 2, 3]* 10       # 10 fois la séquence 1, 2, 3

print(nombres)
print(cycle)
```

<div class="alert alert-info" role="alert" style="font-style: verdana;">

<u>Remarque</u> : on peut également utiliser la notation indexée, l'énumération, la concaténation et la répétition avec les **tuples**
</div>
    
Contrairement aux tuples, les tableaux sont des types mutables : on peut modifier leur contenu. Pour modifier un élément de tableau, on utilise la notation indexée à gauche d'une **affectation** :


```python
t = [1, 2, 3]
for i in range(len(t)):
    t[i] = t[i] * 2     # double la valeur du i-éme élément
print(t)
```

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
liste = [1,2,3,4]

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

    [1, 2, 3, 4, 5]
    [1, 2, 6, 3, 4, 5]
    6
    [1, 2, 3, 4, 5]
    [1, 2, 3, 4]
    []
    

La méthode **``append(x)``** ajoute la valeur ``x`` à la fin de la liste

La méthode **``insert(i,x)``** ajoute la valeur ``x`` à l'indice ``i`` de la liste

La méthode **``pop(i)``** supprime l'élément d'indice i de la liste et le retourne

La méthode **``remove(x)``** supprime la première occurence de x dans la liste, lève une erreur si l'élément n'est pas présent

La méthode **``clear()``** vide le contenu de la liste

En Python on manipulera donc des listes et non des tableaux, mais les tableaux sont utilisés dans d'autres langages comme Java ou C/C++, il est donc important de connaître leurs différences.

## 4. Les chaînes de caractères

Les chaines de caractères ont été introduites au chapitre 2 comme un type de base. Elles ont cependant certaines caractéristiques en commun avec les tableaux :
* on peut obtenir la longueur d'une chaîne ch par la fonction Python ``len(ch)``
* on peut accéder aux caractères de la chaîne avec la notation indexée ``ch[1]``. Cependant les chaines sont immuables: on ne peut pas modifier leur contenu. L'affectation ``ch[i] = "X"`` provoque une erreur
* on peut parcourir les caractères d'une chaîne par ``for car in ch:``

On peut créer un tableau à partir d'une chaîne de caractères ``chaine`` en « découpant » celle-ci avec la méthode ``chaine.split(separateur)``, qui prend en argument une autre chaine de caractères ``separateur`` et retourne un tableau contenant les éléments de chaine initialement séparés par separateur.

A l'inverse, la méthode ``join`` crée une chaîne de caractères en « collant » ensemble les éléments d'un tableau de chaînes avec un séparateur :


```python
phrase = "Il fait beau"

mots = phrase.split(' ')    # mots = ['Il', 'fait', 'beau']
mots[1] = 'fera'            # mots = ['Il', 'fera', 'beau']
phrase = ' '.join(mots)     # phrase = "Il fera beau"
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
    print(cle + ":" + valeur)
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



## Exercices niveau 1

### Exercice 1 :

On représente une personne par un tuple ``(nom, date)`` où ``nom`` est lui-même un tuple formé du prénom et du nom, et ``date`` est la date de naissance représentée par un tuple ``(j, m, a)`` où ``j`` est le jour du mois, ``m`` le numéro du mois (de 1 à 12) et ``a`` l'année.

Écrire une fonction qui prend une personne en paramètre et retourne un tuple formé du nom de famille et de l'année de naissance. Testez votre fonction en créant la personne de votre choix.


```python
def nom_naissance(personne) :
    nom, date = personne
    prenom, nom_famille = nom
    j, m, a = date
    return (nom_famille, a)

harry = (("Harry", "Cover"),(31,12,2000))
print(nom_naissance(harry))
```

    ('Cover', 2000)
    

### Exercice 2 :

Écrire une fonction ``est_ordonne`` qui prend en paramètre une liste de nombres et retourne ``True`` si ses éléments sont ordonnés par ordre croissant.


```python
def est_ordonne(liste) :
    est_ordonne = True
    for i in range(len(liste)-1) :
        if liste[i] > liste[i+1] :
            est_ordonne = False
    return est_ordonne

liste = [1,2,3,4,5]
liste2 = [1,3,2,1]
print(est_ordonne(liste))
print(est_ordonne(liste2))
```

    True
    False
    

### Exercice 3 :

Écrire une fonction ``palindrome`` qui prend en paramètre une chaîne de caractères et retourne ``True`` si c'est un palindrome, c'est-à-dire s'il peut se lire dans les deux sens, comme le mot ``"ressasser"``.


```python
def palindrome(mot) :
    i = 0
    j = len(mot)-1
    est_palindrome = True
    while i < j and est_palindrome :
        if mot[i] != mot[j] :
            est_palindrome = False
        i += 1
        j -= 1
    return est_palindrome

print(palindrome("ressasser"))
print(palindrome("kayak"))
print(palindrome("aa"))
print(palindrome("bonjour"))
```

    True
    True
    True
    False
    

### Exercice 4 :

On définit une carte comme un tuple ``(valeur, couleur)``. ``valeur`` est un entier de 1 à 13 inclus, où 11 représente le Valet, 1 la Dame et 13 le Roi. ``couleur`` est une chaîne de caractères parmi « Pique », « Coeur », « Carreau », « Trèfle ».

1. Écrire une fonction ``carte_valide`` qui prend un tuple en paramètre et retourne un booléen qui indique s'il représente une carte valide ou non.
2. Écrire une fonction ``nom_carte`` qui prend un tuple représentant une carte en paramètre et retourne une chaîne de caractères avec le nom de la carte, par exemple  ``nom_carte(1,"Trèfle")`` doit retourner ``"As de Trèfle"``.
3. Écrire une fonction ``paquet52`` qui retourne une liste contenant toutes les cartes d'un jeu de 52 cartes.
4. Écrire une fonction ``piocher`` qui prend un paramètre ``paquet`` représentant une liste de cartes et enlève la première carte du paquet et la retourne.
5. Écrire une fonction ``ajouter_paquet`` qui prend en paramètres une liste de cartes et une carte, et ajoute la carte à la fin du paquet.
6. À l'aide de la fonction ``randint(a,b)`` de la bibliothèque random, écrire une fonction ``piocher_hasard`` qui prend un paramètre ``paquet`` représentant une liste de cartes et retourne une carte tirée au hasard dans le paquet (l'enlever de la liste).


```python
from random import randint

def carte_valide(carte) :
    if len(carte) == 2 :
        valeur, couleur = carte
        if valeur >= 1 and valeur <= 13 :
            if couleur in ["Pique", "Coeur", "Carreau", "Trèfle"] :
                return True
    return False

def nom_carte(carte) :
    valeur, couleur = carte
    if valeur == 11 :
        nom_carte = "Valet"
    elif valeur == 12 :
        nom_carte = "Dame"
    elif valeur == 13 :
        nom_carte = "Roi"
    elif valeur == 1 :
        nom_carte = "As"
    else :
        nom_carte = str(valeur)
    return f"{nom_carte} de {couleur}"

def paquet52() :
    paquet = []
    for i in range(1,14) :
        paquet.append((i, "Pique"))
        paquet.append((i, "Coeur"))
        paquet.append((i, "Carreau"))
        paquet.append((i, "Trèfle"))
    return paquet

def piocher(paquet) :
    return paquet.pop(0)

def ajouter_paquet(paquet, carte) :
    paquet.append(carte)

def piocher_hasard(paquet) :
    i = randint(0,len(paquet)-1)
    return paquet.pop(i)



paquet_cartes = paquet52()

print("Pioche premiere carte :")
premiere_carte = piocher(paquet_cartes)
print(carte_valide(premiere_carte))
print(nom_carte(premiere_carte))

print("\nNombre cartes dans le paquet :")
print(len(paquet_cartes))

print("\nAjout au paquet :")
ajouter_paquet(paquet_cartes, premiere_carte)
print(paquet_cartes)

print("\nPioche carte au hasard :")
carte_hasard = piocher_hasard(paquet_cartes)
print(carte_valide(carte_hasard))
print(nom_carte(carte_hasard))

print("\nPaquet :")
print(paquet_cartes)

```

    Pioche premiere carte :
    True
    As de Pique
    
    Nombre cartes dans le paquet :
    51
    
    Ajout au paquet :
    [(1, 'Coeur'), (1, 'Carreau'), (1, 'Trèfle'), (2, 'Pique'), (2, 'Coeur'), (2, 'Carreau'), (2, 'Trèfle'), (3, 'Pique'), (3, 'Coeur'), (3, 'Carreau'), (3, 'Trèfle'), (4, 'Pique'), (4, 'Coeur'), (4, 'Carreau'), (4, 'Trèfle'), (5, 'Pique'), (5, 'Coeur'), (5, 'Carreau'), (5, 'Trèfle'), (6, 'Pique'), (6, 'Coeur'), (6, 'Carreau'), (6, 'Trèfle'), (7, 'Pique'), (7, 'Coeur'), (7, 'Carreau'), (7, 'Trèfle'), (8, 'Pique'), (8, 'Coeur'), (8, 'Carreau'), (8, 'Trèfle'), (9, 'Pique'), (9, 'Coeur'), (9, 'Carreau'), (9, 'Trèfle'), (10, 'Pique'), (10, 'Coeur'), (10, 'Carreau'), (10, 'Trèfle'), (11, 'Pique'), (11, 'Coeur'), (11, 'Carreau'), (11, 'Trèfle'), (12, 'Pique'), (12, 'Coeur'), (12, 'Carreau'), (12, 'Trèfle'), (13, 'Pique'), (13, 'Coeur'), (13, 'Carreau'), (13, 'Trèfle'), (1, 'Pique')]
    
    Pioche carte au hasard :
    True
    Dame de Coeur
    
    Paquet :
    [(1, 'Coeur'), (1, 'Carreau'), (1, 'Trèfle'), (2, 'Pique'), (2, 'Coeur'), (2, 'Carreau'), (2, 'Trèfle'), (3, 'Pique'), (3, 'Coeur'), (3, 'Carreau'), (3, 'Trèfle'), (4, 'Pique'), (4, 'Coeur'), (4, 'Carreau'), (4, 'Trèfle'), (5, 'Pique'), (5, 'Coeur'), (5, 'Carreau'), (5, 'Trèfle'), (6, 'Pique'), (6, 'Coeur'), (6, 'Carreau'), (6, 'Trèfle'), (7, 'Pique'), (7, 'Coeur'), (7, 'Carreau'), (7, 'Trèfle'), (8, 'Pique'), (8, 'Coeur'), (8, 'Carreau'), (8, 'Trèfle'), (9, 'Pique'), (9, 'Coeur'), (9, 'Carreau'), (9, 'Trèfle'), (10, 'Pique'), (10, 'Coeur'), (10, 'Carreau'), (10, 'Trèfle'), (11, 'Pique'), (11, 'Coeur'), (11, 'Carreau'), (11, 'Trèfle'), (12, 'Pique'), (12, 'Carreau'), (12, 'Trèfle'), (13, 'Pique'), (13, 'Coeur'), (13, 'Carreau'), (13, 'Trèfle'), (1, 'Pique')]
    

A vous de jouer, copiez vos fonction dans le code ci-dessous et essayez de créer un jeu de carte (la bataille par exemple, mais vous pouvez inventer votre propre jeu).
* Quelles vont être les différentes données nécessaires pour votre programme ?
    .........
* Quelle structure de données utiliser pour représenter les joueurs et leurs cartes ?
    .........
* Quelles fonctions en plus vont être utiles pour votre jeu ?
    .........
* A vous de choisir les règles, les différentes possibilités, le déroulement du jeu (nombre joueurs, rejouer, points...)
    .........


```python
# fonctions




# programme principal (construction des données puis déroulement du jeu)



```
