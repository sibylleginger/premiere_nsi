## Exercices boucles Python

**Exercice 1 :**  
On rappelle que l'on peut dupliquer plusieurs fois une chaîne de caractère avec l'opérateur **\***
Par exemple `'o'*11`


```python
print('o'*11)
```

Écrire un script qui affiche le motif ci-dessous :

```python
o
oo
ooo
oooo
ooooo
oooooo
ooooooo
oooooooo
ooooooooo
oooooooooo
```

**Exercice 2 :**
Écrire un script qui affiche le motif ci-dessous :

```
ooooooooo
oooooooo
ooooooo
oooooo
ooooo
oooo
ooo
oo
o
```

**Exercice 3:**  

Écrire un script qui affiche le motif ci-dessous :
    
```
         o
        oo
       ooo
      oooo
     ooooo
    oooooo
   ooooooo
  oooooooo
 ooooooooo
oooooooooo
```

**Exercice 4 :** Cet exercice se traite sur papier, sans machine. Voici un script :
```
x = 1
n = 5
while n > 1 :
    x = x * n
    n = n - 1
```

Quelle est la valeur finale de x ?

**Exercice 5 :** Cet exercice se traite sur papier, sans machine. Voici un script :
```
x = 0
for i in range(2) :
    x = x + i
    for j in range(3) :
        x = x + j
```

Quelle est la valeur finale de x ?

**Exercice 6 :**

Ecrire un programme qui demande à l'utilisateur de saisir le nombre d'équipes participant à un championnat, puis le programme affiche la liste des matchs aller et retour pour ce championnat.

Exemple pour 3 équipes, le programme doit afficher :<br>
```equipe 1 - equipe 2
equipe 1 - equipe 3
equipe 2 - equipe 1
equipe 2 - equipe 3
equipe 3 - equipe 1
equipe 3 - equipe 2
```

**Exercice 7 :**

Une chaine de caractère est tout simplement un texte mis entre guillemet ".

Si à la place de range on met une chaine de caractères à énumérer dans une boucle for, on va tout simplement prendre chaque lettre l'une après l'autre de cette chaine de caractères.

Prenons un exemple :


```python
nb_e = 0
for lettre in "Hello !":
    #si une lettre est égale à e, alors on augmente nb_e de 1
    if lettre == "e":
        nb_e+=1
print(nb_e)
```

    1
    

Ecrire un programme qui permet de compter le nombre de "e" dans un texte.

**Exercice 8 :**  La distance de la terre à la lune est de $384\ 400 km$  soit  $384\ 400\ 000\ 000mm$

On dispose d'une feuille de papier de $0,1mm$ d'épaisseur.  On la plie en 2 puis encore en 2 et ainsi de suite. 

1. quelle épaisseur obtiendrait-on si on pouvait la plier 10 fois?
2. Déterminer le nombre de fois qu'il faut la plier pour que l'épaisseur soit plus grande que la distance terre lune.?
