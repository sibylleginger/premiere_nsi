###### NSI Spécialité NSI Première - J.J.Dides - sept. 2020

# Les types construits en Python

# 4- Les tableaux : des listes de listes en Python

##  L'exemple du jeu de bataille navale

Reprenons l'exemple du jeu de la bataille navale : la grille de jeu est un ensemble de cases, organisées en 10 lignes de 10 colonnes, pouvant prendre 2 états "vide" ou "occupé par un navire" en début de partie (et même "touché" ou "à l'eau" en cours de partie, si l'on souhaite mémoriser les coups joués) ...

![](grilleBatNav.png)

Pour représenter cette grille de jeu on peut donc utiliser un tableau (ou matrice) de caractères tels que "." pour case vide et "o" pour case occupée ...

![](grilleBatNav2.png)

## Construire une liste de listes

Essayons de représenter une ligne du tableau en Python : on peut utiliser une liste de caractères *Ligne*, définissable par énumération :    


```python
Ligne =  ["." , "." , "." ,"." ,"." ,"." ,"." ,"." ,"." ,"."]

```

On peut aussi créer une telle liste par ajouts successifs : on utilise pour celà une boucle for j in range(10) ou j est le n° de colonne, variant de 0 à 10 :


```python
Ligne = []
for j in range(10) :
    Ligne += ["."]
    
```

ou encore, définir la liste Ligne en compréhension :


```python
Ligne = ["." for j in range(10)]

```


```python
Ligne

```

Pour créer une tableau de 10 lignes, on peut utiliser une seconde boucle, for i in range(10), où i est le numéro de ligne, variant de 1 à 10 et créer, par ajouts successifs, une liste *Tableau* de lignes *Ligne* :


```python
Tableau = []
for i in range(10) :
    Tableau += [Ligne]
    
```

ou bien, définir la liste *Tableau* en compréhension :


```python
Tableau = [Ligne for i in range(10)]

```


```python
Tableau

```

On obtient une liste de 10 listes de 10 caractères : **une liste de liste** !!!      

## Imbriquer des boucles ....

... que l'on aurait pu créer directement en utilisant 2 **boucles imbriquées**, ou i est le n° des lignes et j le n° des colonnes :


```python
Tableau = []
for i in range(10) :            # on crée i=10 lignes
    Ligne = []
    for j in range(10) :        # de j=10 colonnes
        Ligne += ["."]
    Tableau += [Ligne]
    
```

ou encore, en définissant la Tableau en compréhension :


```python
Tableau = [["." for j in range(10)] for i in range(10)]

```


```python
Tableau

```

**Exercice** : créer un tableau 3 lignes x 3 colonnes pour obtenir une grille de **Morpion**


```python

```

**Exercice** : écrire une fonction new_tab(nl, nc, car) qui crée un tableau de caractères car, de dimensions nl lignes x nc colonnes, rempli du caractère car ...


```python
def new_tab(nc, nl, car) :
    T = [[car for j in range(nc)] for i in range(nl)]
    return T

```


```python
new_tab(4,4,'X')

```

## Indexer chaque case du tableau 

Une ligne du tableau Tableau[i] peut être indexée par son rang i ...     
Et une case du tableau, par le rang i de sa ligne et le rang j de sa colonne : Tableau[i][j]

![](grilleBatNav3.png)


```python
Tableau[8][7]

```

Plaçons un navire en ligne 8, colonne 7 ...


```python
Tableau[8][7]= 'o'
Tableau

```

**Exercice** : placer un bateau sur la ligne 1 occupant les colonnes 6,7 et 8


```python
Tableau[1][6], Tableau[1][7],Tableau[1][8] = "o","o","o"
Tableau

```

### Exercice : convertir les coordonnées d'une grille de jeu     

A un couple coord (i,j) - n° de ligne i , n° de colonne j dans Tableau - correspond, à l’affichage, une chaine de caractère case, de type ‘A1’ ou ‘J10’.     
Dans le jeu de bataille navale, le joueur choisit une case en saisissant, par exemple "E6" ...     
Dans la liste de listes Tableau, l’élément Tableau[0][0] est référencé, à l’affichage, par ‘A1’, et  Grille[9][9] est référencé par ‘J10’.      

![](grilleBatNav4.png)

Ecrire une fonction qui convertit une cordonnée de type "E6" en 2 entiers, i le n° de ligne et j le n° de colonne du Tableau (voir schéma ci-dessous). La fonction retourne le tuple (i,j). Attention les 10 index i et j commencent à 0 et se terminent à 9 ...


```python
def case2coord(case) :
    # convertit une référence de case type "A1" en coordonnées (i,j) dans un tableau
    return ord(case[0])-65, int(case[1:])-1

```


```python
case2coord("E6")

```

Ecrire une fonction qui convertit une cordonnée de type (i,j), i n° de ligne et j n° de colonne du Tableau (voir schéma ci-dessus). La fonction retourne une chaine de 2 caractères de type "E6" ...


```python
def coord2case(i,j) :
    # convertit des coordonnées (i,j) dans un tableau en une référence de case type "A1" 
    return (chr(65+i) + str(j+1))

```


```python
coord2case(4,5)

```

### Exercice : Positionner une flotte de navires sur une grille vide    

Au jeu de bataille navale, le nombre et la taille des navires varient en fonction des règles choisies : une flotte peut par exemple comporter 1 cuirassé (4 cases), 2 croiseurs (3 cases), 3 torpilleurs (2 cases), 4 sous-marins (1 cases). En début du jeu, chaque joueur place ses bateaux sur sa grille.   

![](navires.png)

Afin de définir la position des navires d'une flotte sur la grille de jeu *Tableau*, on peut utiliser un dictionnaire *Flotte* dont les clés sont les couples (i,j) des coordonnées dans la grille des cases occupées par un navire et les valeurs sont les noms des navires.     
Nous avons, lors du cours sur les dictionnaires, déjà créé une telle structure (vous pouvez y modifier la position et la composition de votre flotte comme bon vous semble ...) :      


```python
Flotte = {  (3,3):'cuirasse', (4,3):'cuirasse', (5,3):'cuirasse', (6,3):'cuirasse',
            (1,6):'croiseur1', (1,7):'croiseur1', (1,8):'croiseur1',
            (8,5):'croiseur2', (8,6):'croiseur2', (8,7):'croiseur2',
            (1,1):'torpilleur1', (2,1):'torpilleur1',
            (3,5):'torpilleur2', (3,6):'torpilleur2',
            (6,7):'torpilleur3', (6,8):'torpilleur3',
            (1,3):'sousmarin1', (4,8):'sousmarin2', (5,5):'sousmarin3', (7,1):'sousmarin4'  }

```

Voici une fonction qui affiche un tableau de jeu en mode texte :


```python
# affichage de la grille, en mode console
def affiche(tableau) :
    # affichage en-tête colonne
    print('     ',end='')
    for j in range(10) :
        print(j+1,end=' ')
    print('\n')
    # affichage en-tête ligne
    for i in range(10) :
        print(chr(65+i),end='    ')
    # affichage contenu ligne
        for j in range(10) :
            print(tableau[i][j],end=' ')
        print()
        
```


```python
affiche(Tableau)

```

Ecrire une fonction qui permet de positionner la flotte sur la grille de jeu en modifiant le tableau *Tableau* en conséquence...     
En paramètre d'entrée, le dictionnaire *Flotte* précise les coordonnées et le nom de chaque navire.      
La fonction crée et retourne un tableau vide et y positionne tous les navires décrits dans le dictionnaire *Flotte*.     
Afficher ensuite ce tableau à l'aide de la fonction affiche ...


```python
def positionne(Flotte) :
    # création d'une grille de jeu 10x10 vide
    Tableau = new_tab(10,10,'.')
    # positionnement de la flotte sur la grille
    # . pour case vide, O pour case occupée par un vaisseau
    for position in Flotte :
        Tableau[position[0]][position[1]] = 'o'
    return Tableau

```


```python
Tableau = positionne(Flotte)
affiche(Tableau)

```

### Exercice : tirer dans une grille
Voici une fonction *choix_case()* qui invite le joueur à la saisie d'une référence de case (de type "A1" dans ["A1" .. "J10"]), vérifie la validité de la saisie et retourne les coordonnées de la case dans le tableau de jeu (de type (i,j) ...


```python
# création d'un ensemble de libellés de case possibles, de 'A1' à 'J10'
cases_possibles = set()
for i in range(10) :
    for j in range(10) :
        coord = chr(65+i) + str(j+1)
        cases_possibles.add(coord)

```


```python
# choix d'une case, en vue d'un tir
# retour d'un couple d'entiers, les coordonnées (i,j) d'1 case, i et j dans [0..9]
def choix_case() :
    # choix et vérification du libellé d'une case
    choix = input("Choisissez une case (de A1 à J10) :")
    while not choix in cases_possibles :
        choix = input("Choisissez une case (de A1 à J10) :")
    # conversion de la référence de la case choisie de type 'A1','B2' ... en coordonnées (i,j) de type (0,0),(1,1) ...
    return choix

```

Ecrire une fonction *tir(case)* qui annonce le résultat d'un tir et modifie le tableau *Tableau* en conséquence ...     
En entrée, *case* est le libéllé de la case visée dans la grille de jeu (exemple "A1").    
La fonction doit afficher un message : "A l'eau !" ou "Touché !", en fonction de l'occupation de la case visée.    
La fonction doit modifier le contenu de la case du tableau : "*" si à l'eau, "X" si touché.


```python
# analyse de l'impact d'un tir sur une case de la grille de jeu
# affiche le résultat du tir (raté ou touché)
# et met à jour Tableau[i][j] ("*" pour tir raté, "X" pour vaisseau touché)
def tir(case) :
    (i,j) = case2coord(case)    # coordonnées de case dans Tableau
    if (i,j) in Flotte :
        print("Tir en", case,":",Flotte[(i,j)], "Touché !")
        Tableau[i][j] = 'X'
    else :
        print("Tir en", case,": A l'eau !")
        Tableau[i][j] = '*'

```

Tester votre fonction en effectuant quelques tirs ...


```python
case = choix_case()        # choix d'une case de la grille de jeu
tir(case)                  # évaluation du tir sur la case choisie
print()
affiche(Tableau)           # afficahge actualisé de la grille de jeu

```

### Projet : un jeu complet de bataille navale     
Programmer maintenant un jeu complet de bataille navale contre l'ordinateur ...     
Commencer par écrire l'algorithme de la boucle principale de jeu et spécifier les fonctions nécessaires (elles ont quasiment toutes été déjà écrites !).

### Projet : générer aléatoirement une flotte et une grille de jeu     
Prévoir et écrire une fonction qui permet de générer aléatoirement une flotte (les navires ne doivent ni se croiser, ni se toucher, et bien sur contenir dans les limites de la grille de jeu !) ...

## Projet Poèmes combinatoires

## Projet Puissance 4
