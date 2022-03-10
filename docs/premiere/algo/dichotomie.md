# Recherche par dichotomie


<div class="alert alert-danger">

**Le problème :**
    
On s’intéresse à la **recherche d’occurrence** sur des valeurs de type quelconque : nombre, booléen, chaîne de caractère, liste ect. dans une liste.
Nous noterons ``c`` l’élément recherché (cible) et la liste dans laquelle nous cherchons sera notée ``L``.
    </div>

## Parcours séquentiel

Voici un algorithme en langage naturel qui résout ce problème :

```
Algorithme recherche(L,c)
    """
    Entrée: Une liste L de n éléments et c un élément à rechercher dans L
    Sortie: Un booléen qui indique si l’élément c est dans la liste L.
    """"
    present ← Faux
    pour i allant de 0 à n−1 faire
        si c est égal à l'élément d'indice i de L alors
            present ← Vrai
    retourner present
```

<div class="alert alert-success">

Écrire, ci-dessous, une implémentation en Python de cet algorithme sous la forme d’une fonction nommée ``recherche()`` et ajouter deux tests pour vérifier qu'elle fonctionne.
</div>


```python
# fonction recherche() ici
```

<div class="alert alert-success">

Quelle est la complexité de cette fonction ?
</div>


```python

```

<div class="alert alert-success">

Avez-vous une idée d'une autre manière de rechercher une valeur dans une liste ?
    </div>


```python

```

## Recherche dichotomique

<div class="alert alert-success">

**Expérience :**
Par groupe de 2, un élève choisit un nombre entier entre 1 et 20. L’autre élève doit trouver le nombre choisit en posant le moins de questions possible. Les seules réponses possibles sont :
* “oui c’est le nombre recherché”,
* “non, c’est plus”,
* “non, c’est moins”.

Trouver la stratégie la plus efficace.
    </div>


```python
notez votre stratégie ici :
```

<div class="alert alert-danger">

**Le problème:**

Rechercher un élément dans un liste triée.
Nous avons vu précédemment qu’un parcours séquentiel de la liste peut résoudre ce problème. Avec cet algorithme, la complexité est linéaire, l’objectif est de faire mieux.
    </div>

<div class="alert alert-info">

Principe de la recherche dichotomique :
* comparer l’élément avec la valeur du milieu de la liste
* si les valeurs sont égales, la tâche est accomplie
* sinon on recommence dans la moitié de la liste pertinente (selon si la valeur est supérieure ou inférieure).
    </div>

Voici l’algorithme présenté en langage naturel :

````
Algorithme recherche_dichotomique(L,c)
    '''
    Entrée: Une liste L de n éléments triée par ordre croissant et c un élément à rechercher dans L
    Sortie: Un booléen qui indique si l’élément c est dans la liste L.
    present ← Faux
    debut ← 0
    fin ← n−1
    tant que . . . . . . . . . . . . . . . ET . . . . . . . . . . . . . . . faire
        milieu ← (debut + fin) // 2
        si l'élément d'indice milieu dans L est égal à c alors
            present ← Vrai
        sinon si c supérieur à l'élément d'indice milieu dans L alors
            . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . .
        sinon
            . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . .
    retourner present
````

<div class="alert alert-success">

**Exemple**

Rechercher l’élément 23 dans la liste triée ``[2,5,7,11,13,17,19,23,29]`` 

Complétez les valeurs des variables de l'algorithme dans les tableaux ci-dessous pour comprendre le déroulement :
    </div>

| | | | | | | | | | |
|:---:|:---:|:---:|:---:|:---:|:---:|:---:|:---:|:---:|:---:|
| valeurs | 2 | 5 | 7 | 11 | 13 | 17 | 19 | 23 | 29 |
| indices | 0 | 1 | 2 | 3 | 4 | 5 | 6 | 7 | 8 |
| variables | d | | | | m | | | | f |

| | | | | | | | | | |
|:---:|:---:|:---:|:---:|:---:|:---:|:---:|:---:|:---:|:---:|
| valeurs | 2 | 5 | 7 | 11 | 13 | 17 | 19 | 23 | 29 |
| indices | 0 | 1 | 2 | 3 | 4 | 5 | 6 | 7 | 8 |
| variables | | | | | | | | |  |

| | | | | | | | | | |
|:---:|:---:|:---:|:---:|:---:|:---:|:---:|:---:|:---:|:---:|
| valeurs | 2 | 5 | 7 | 11 | 13 | 17 | 19 | 23 | 29 |
| indices | 0 | 1 | 2 | 3 | 4 | 5 | 6 | 7 | 8 |
| variables | | | | | | | | |  |

| | | | | | | | | | |
|:---:|:---:|:---:|:---:|:---:|:---:|:---:|:---:|:---:|:---:|
| valeurs | 2 | 5 | 7 | 11 | 13 | 17 | 19 | 23 | 29 |
| indices | 0 | 1 | 2 | 3 | 4 | 5 | 6 | 7 | 8 |
| variables | | | | | | | | |  |

<div class="alert alert-danger">

La **recherche dichotomique** fera ... tours de boucles VS la **recherche séquentielle** fera ... tours de boucles.
    </div>

<div class="alert alert-success">

**Exemple**

Rechercher l’élément 8 dans la liste triée : ``[2,5,7,11,13,17,19,23,29]`` 

Complétez les valeurs des variables de l'algorithme dans les tableaux ci-dessous pour comprendre le déroulement :
    </div>

| | | | | | | | | | |
|:---:|:---:|:---:|:---:|:---:|:---:|:---:|:---:|:---:|:---:|
| valeurs | 2 | 5 | 7 | 11 | 13 | 17 | 19 | 23 | 29 |
| indices | 0 | 1 | 2 | 3 | 4 | 5 | 6 | 7 | 8 |
| variables | d | | | | m | | | | f |

| | | | | | | | | | |
|:---:|:---:|:---:|:---:|:---:|:---:|:---:|:---:|:---:|:---:|
| valeurs | 2 | 5 | 7 | 11 | 13 | 17 | 19 | 23 | 29 |
| indices | 0 | 1 | 2 | 3 | 4 | 5 | 6 | 7 | 8 |
| variables |  |  | |  | | | | |  |

| | | | | | | | | | |
|:---:|:---:|:---:|:---:|:---:|:---:|:---:|:---:|:---:|:---:|
| valeurs | 2 | 5 | 7 | 11 | 13 | 17 | 19 | 23 | 29 |
| indices | 0 | 1 | 2 | 3 | 4 | 5 | 6 | 7 | 8 |
| variables | | |  |  |  | | | |  |

| | | | | | | | | | |
|:---:|:---:|:---:|:---:|:---:|:---:|:---:|:---:|:---:|:---:|
| valeurs | 2 | 5 | 7 | 11 | 13 | 17 | 19 | 23 | 29 |
| indices | 0 | 1 | 2 | 3 | 4 | 5 | 6 | 7 | 8 |
| variables | | | |  | | | | |  |

<div class="alert alert-danger">

La **recherche dichotomique** fera ... tours de boucles VS la **recherche séquentielle** fera ... tours de boucles.
    </div>

Avec l'aide des 2 déroulements analysés, compléter l'algorithme donné plus haut.
* Quelles sont les conditions d'arrêts du programme ?
* Que se passe-t-il dans les différents cas (si ``c`` est inférieur/supérieur à l'élément d'indice ``milieu``) ?

### Implémentation en Python

<div class="alert alert-success">

Écrire, ci-dessous, une implémentation en Python de cet algorithme sous la forme d’une fonction nommée ``recherche_dicho()``.

Ajouter trois tests pour vérifier qu'elle fonctionne :
* un cas où la valeur recherchée est en début de liste
* un cas où la valeur recherchée est en fin de liste
* un cas où la valeur recherchée n'est pas dans la liste
</div>


```python
# fonction recherche_dicho() ici



# tests ici


```

<div class="alert alert-success">

Cet algorithme termine-t-il dans tous les cas ? Donner un variant de boucle.


```python

```

<div class="alert alert-success">

L’algorithme fait-il ce pourquoi il est conçu ?


```python

```

<div class="alert alert-success">

Quel est le temps d’exécution au pire des cas? Quel est la classe de complexité de cet algorithme?


```python

```

## Synthèse

Qu'avez-vous retenu/appris dans ce notebook ? Faites votre propre synthèse !


```python

```
