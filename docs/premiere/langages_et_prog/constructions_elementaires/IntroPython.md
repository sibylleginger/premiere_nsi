##### Spécialité NSI Première - J.J.Dides sept.2020

# Introduction à la programmation en langage python

## Notion de variable

Un programme informatique traite des données qu'il range dans la mémoire de l'ordinateur. On peut considérer cette mémoire comme une suite de cases dans lesquelles sont rangées les données, chacune de ces cases possèdant une adresse qui permet au processeur de retrouver les données.

Qu'est-ce qu'une variable ?
C'est une information temporaire que l'on stocke dans une case de la mémoire. 
On dit qu'elle est "variable", car sa valeur peut changer pendant l'exécution du du programme.

Une variable ...
 - a une valeur, l'information stockée (par exemple le nombre entier 5)
 - a un nom, qui permet de la reconnaître (plus facile à manipuler que l'adresse de la case dans la mémoire).
 - a un type (par exemple "nombre entier"), qui détermine la taille de la case à réserver en mémoire pour stocker la donnée.
 
Notre premier programme contient 3 instructions qui définissent 3 variables, nommées a, b et c et qui, respectivement, "contiennent" le nombre entier (integer : int) 5, le nombre réel (ou flottant : float) 3.5 et la suite (ou chaine : string str) de caractères "bonjour" :


```python
a = 5
b = 3.5
c= "bonjour"
```

Remarquer la syntaxe : 
- le point (version anglo-saxonne de la virgule) indique que la variable b sera de type flottant.
- les *""*  indiquent que la variable c est de type chaine de caractère.

Pour retouver le contenu d'une variable, il suffit de l'appeler par son nom :


```python
a
```

Pour verifier le type d'une variable :


```python
type(a)
```

*Procéder de même pour les variables b et c ...*


```python

```


```python

```


```python

```


```python

```

### L'affectation

L'instruction a=5 a un sens bien particulier : elle crée une variable nommée a, lui affecte la valeur 5 et le type int, nombre entier.   
Le signe = est l'opérateur d'affectation.  
Observons le petit programme suivant :


```python
a = 5
a = a + 1
```

Que contient, à l'issue de l'exécution de ces 2 instructions, la variable a ?


```python
a
```

On voit bien ici la particularité de l'opérateur =  d'affectation ...   
Il n'a rien avoir avec l'opérateur égale = utilisé en maths (en maths, a serait évidemment différent de a+1).

L'instruction a=a+1 récupère en mémoire la valeur initiale de a, y rajoute 1, et range le résultat dans a.   
Dans cette affectation, le membre de gauche a reçoit le membre de droite a+1, ce qui nécessite d'évaluer la valeur du membre de droite avant de l'affecter au membre de gauche.

*Pour vous persuader que le contenu de a est bien variable, exécuter les instructions suivantes et vérifier le contenu de la variable a après chaque opération ...*


```python
a = a * 2
```


```python
a
```


```python
a = a / 3
```


```python
a
```


```python
a = a - 1
```


```python
a
```

### Quelques autres opérateurs

Vous aurez reconnu les opérateurs multiplication \*, division / et soustraction - ...  
*Voici quelques autres opérateurs à tester et à identifier ...*


```python
a = 7
```


```python
a // 2
```


```python
a % 2
```


```python
a ** 2
```


```python
49 ** 0.5
```

Vous aurez reconnu les opérateurs division entière //, reste de la divion entière % et élévation à la puissance **.   

Peut être avez vous remarqué, au cours de ces opérations, des conversions automatiques de type ...  
*Tester les opérations suivantes et vérifier les types obtenus :*


```python
a = 5
```


```python
type(a)
```


```python
b = a / 2
```


```python
type(b)
```


```python
c = a + 0.25
```


```python
type(c)
```

## Les fonctions

Imaginons que nous voulions réaliser une opération pour laquelle il n'existe pas d'opérateur prédéfini ...   
Par exemple, on souhaite pouvoir élever un nombre au carré : il va donc falloir créer une fonction adaptée ...

La notion de fonction en informatique est comparable à la notion de fonction en mathématiques.  

![](fonction.png)

Ecrivons une fonction carre(x) qui élèvera x au carré et retournera le résultat :


```python
def carre(x) :
    return x * x
```

carre() est le nom de la fonction. x est son paramètre d'entrée. x\*x est la valeur retournée par la fonction ...  
Bien noter la syntaxe de la définition de fonction : 
- au début, le mot clé **def**, suivi du nom de la fonction et des **:**, 
- le décalage de 4 espaces, appelé **indentation**, et qui délimite la suite (ou bloc) d'instructions exécuté par la fonction
- à la fin, le mot clé **return** 


Pour utiliser la fonction, il suffit de l'appeler par son nom, en fournissant, entre paranthèses, un paramètre d'entrée :


```python
carre(2)
```


```python
x = 2
y = carre(x)
y
```


```python
x = 3
y = carre(x)
y
```

De plus, les fonctions sont réutilisables : si nous avons défini une fonction capable de calculer un carré, par exemple, nous pouvons l'utiliser un peu partout dans notre programme sans avoir à la réécrire à chaque fois (on parle de factorisation du code).  

*Ecrire une fonction cube(x) qui retourne x au cube*   
*Ecrire une fonction polynome1(x) qui retourne 2x+3*   
*Ecrire une fonction polynome2(x, a, b) qui retourne ax+b (il est possible de passer plusieurs paramètres à une fonction, séparés par des virgules)*


```python

```


```python

```


```python

```


```python

```


```python

```


```python

```

## Les variables de type chaine de caractères

Attardons nous sur quelques particularités du type chaine de caractère (qui seront étuciées en détail prochainement) ... 

Nous avons déjà vu que, à l'affectation, on utilise les "" pour signifier qu'une variable est de type chaine de caractères.


```python
nom = "Victor"
```

On peut affecter une telle variable par une saisie au clavier. On utilise pour cela la fonction prédéfinie input().   
Cette fonction affiche un message ("Quel est ton nom ?") et attends une saisie clavier.   
Puis, le contenu de cette saisie est affecté, sous forme de chaine de caractère à la variable nom :


```python
nom = input("Quel est ton nom ? : ")

```


```python
message = "Bonjour " + nom + ' !'
print(message)
```

On peut constater, à l'issue de l'exécution de cette dernière cellule, que
 - une chaine de caractère a bien été affectée à la variable nom par la fonction input()
 - la fonction prédéfinie print() permet d'afficher le contenu d'une variable
 - l'opérateur +, appliqué à une variable de type chaine, a pour effet de juxtaposer/ enchainer/ concaténer 2 chaines : on voit ici l'importance du type de la variable qui va déterminer l'effet de l'opérateur +
 
 Essayons ceci :


```python
a = 5
message = "Nombre de personnes : " + a
print(message)
```

On obtient un message d'erreur car il semble impossible de concaténer ou d'additionner une chaine et un nombre !  
Essayons alors ceci :


```python
a = 5
message = "Nombre de personnes : " + str(a)
print(message)
```

La fonction prédéfinie str() convertit le type de la variable a d'entier vers chaine. La concaténation devient alors possible ...  

Réciproquement, essayons ceci :


```python
a = input("Choisissez un nombre : ")
print("Voici son carré : ", a*a)
```

Encore une erreur ! La fonction prédéfinie input() retourne une chaine, dont on ne peut calculer le carré !  
Essayons alors ceci :


```python
a = input("Choisissez un nombre : ")
a = int(a)
print("Voici son carré : ", a*a)
```

La fonction prédéfinie int() convertit le type de la variable a de chaine vers entier. Le produit a*a devient alors possible ... 

## Les expressions logiques (ou booléennes)

Une expression logique n'a que 2 états possibles : vrai (True, 1) ou faux (False, 0). On parle aussi de variable de **type booléen**.   

Dans une expression logique, on utilise les opérateurs égale (==), différent de (!=), <, >, <=, >=, etc.

Par exemple, si ...


```python
a = 5
b = 4
c = b + 1
```

*... évaluer les expressions logiques suivantes :*


```python
a == b
```


```python
b < c
```


```python
b > c
```


```python
c == a
```


```python
a != b
```

On peut aussi combiner ces expressions logiques élémentaires avec les opérateurs Non (Not), Ou (Or) et Et (And) pour obtenir une expression logique plus élaborée.

*Ainsi, évaluer les expressions logiques suivantes :*


```python
not a == b
```


```python
a == b and a == c
```


```python
a == b or a == c
```

On peut regrouper, dans des **tables de vérité**, l'ensemble des résultats des opérateurs logiques ET et OU obtenus pour toutes les combinaisons possibles de 2 opérandes logiques a et b  :

![](tables_verite.png)

## Les boucles

Une boucle permet d'exécuter plusieurs fois une même suite d'instructions ...

Dans une boucle (ici, **répéter tant que**), le mot clé **while** est suivi d’une expression logique : le bloc d’instruction qui suit sera exécuté tant que cette expression logique sera vraie. Cette expression logique fixe une **condition d'arrêt** à l'exécution de la boucle. 

Par exemple, la boucle suivante affiche (l'instruction print(i) permet l'affichage du contenu de la variable i) les entiers successifs de 1 à 9 :


```python
i = 1
while i < 10:
    print(i)
    i = i + 1
```

Tant que l'expression logique (i<10) est vraie, les 2 instructions suivantes sont répétées ...  La condition d'arrêt est donc (i>=10).  
Pour que la boucle se termine, la variable i, appelée compteur de boucle, doit être modifiée à chaque tour de boucle (i=i+1), afin que la condition d'arrêt soit atteinte après 9 tours de boucle.

Bien noter la syntaxe d'une boucle : le mot clé **while**, suivi de l'expression logique qui définit la condition d'arrêt, les **\:** et l'**indentation** (décalage horizontal de 4 espaces) qui permet de délimiter les bloc d'instructions à exécuter dans la boucle ...

Programmons maintenant l'affichage de la table de multiplication par 2 :


```python
# la table de multiplication
a = 2
i = 1
while i <= 10:
    print(a * i)
    i = i + 1
```

Afin d'obtenir une trace de l'exécution de notre boucle, demandons, à chaque tour de boucle, l'affichage des contenus des différentes variables : 


```python
a = 2
i = 1
while i <= 10:
    print("Tour de boucle n°", i, ": i=", i, ", expression logique (i<=10) :", i<=10, ", affichage :", a, "x", i, "=",a * i)
    i = i + 1
print("Arrêt de la boucle : ","i=", i, ", expression logique (i<=10) :", i<=10)
```

On voit bien que la boucle s'exécute pour toutes les valeurs entières de i, de 1 à 10, et s'arrête dès que l'expression logique (i<=10) devient fausse ...

*Modifier ce programme* 
 - *pour afficher la table de multiplication de votre choix,* 
 - *pour étendre la table à 12 éléments.*


```python

```


```python

```

Programmons maintenant le calcul des 10 premières puissances de 2 :


```python
# les 10 premières puissances de 2
a = 2
i = 1
b = 1
while i <= 10:
    b = b * a
    print(b)
    i = i + 1
```

Afin d'obtenir une trace de l'exécution de notre boucle, demandons, à cahque tour de boucle, l'affichage des contenus des différentes variables : 


```python
a = 2
i = 1
b = 1
while i <= 10:
    b = b * a
    print("Tour de boucle n°", i, ": i=", i, ", expression logique (i<=10) :", i<=10, ", valeur affichéee b :", b)
    i = i + 1
print("Arrêt de la boucle : ","i=", i, ", expression logique (i<=10) :", i<=10)
```

On voit bien que la boucle s'exécute pour toutes les valeurs entières de i, de 1 à 10, et s'arrête dès que l'expression logique (i<=10) devient fausse ...

*Modifier ce programme pour afficher*
 - *les 12 premières puissances de 2,*
 - *pour afficher les 10 premières puissances de 3, de 10 ...*


```python

```


```python

```

##### Exercice : La légende de Sissa							 

Un roi indien, voulant remercier le brahmane Sissa qui avait inventé le jeu d'échecs, lui proposa la récompense de son choix. Sissa prit alors la parole : « Que votre Majesté daigne me donner un grain de blé pour la première case de l'échiquier, deux pour la seconde, quatre pour la troisième, et ainsi de suite, en doublant le nombre de grains jusqu'à la soixante-quatrième case ». 

*Écrire un programme qui affiche le nombre de grains à déposer sur chacune des 64 cases du jeu, ainsi que le nombre total de grains de riz sur l'échiquier.*


```python

```

## Les tests

Un test permet de n'exécuter une instruction que quand une expression logique est vérifiée ...

Supposons que l’on souhaite afficher le résultat d’un examen ("Admis" ou "Recalé") en fonction de la note obtenue (10 et plus, ou moins de 10), saisie au clavier. Voici le programme correspondant ;  
(*Tester ce programme en l'exécutant avec différentes notes ;  modifier le seuil d'admission ...*) :


```python
note = input("Note sur 20 : ")
note = int(note)
if note >= 10 :
    print("Admis")
if note < 10 :
    print("Recalé !")
```


```python

```

Bien noter la syntaxe d'un test : le mot clé **if**, suivi d'une expression logique (la condition), les : et l'**indentation** (décalage horizontal de 4 espaces) qui permet de délimiter les bloc d'instructions à exécuter si la condition est vérifiée ..

Trace d'exécution :   
Si la première expression logique (note>=10) est vraie alors l'instruction qui suit (afficher "Admis") est exécutée, et on passe à la suite du programme ; si elle est fausse alors on passe directement à la suite du programme …
Si la seconde expression logique (note<10) est vraie alors l'instruction qui suit (afficher "Recalé") est exécutée et le programme se termine; si elle est fausse alors le programme se termine directement.

Une seconde manière d'écrire les tests :


```python
note = input("Note sur 20 : ")
note = int(note)
if note >= 10 :
    print("Admis")
else :
    print("Recalé !")
```

Trace d'exécution :   
Les 2 expressions logiques (note>=10) et (note<10) étant exclusives, cette seconde écriture est plus efficace (1 seul test, au lieu de 2) : si l'expression (note>=10) est vraie alors l'instruction Afficher "Admis" est exécutée, sinon on exécute l'instruction Afficher "Recalé".

Une troisième manière d'écrire des tests :


```python
note = input("Note sur 20 : ")
note = int(note)
if note >= 16:
    print('Très Bien')
elif note >= 14:
    print('Bien')
elif note >= 12:
    print('Assez Bien')
elif note>=10:
    print('Passable')
else:
  print('Recalé !')
```

Trace d'exécution :  
Lorsque l’on veut tester plus de 2 conditions, toutes exclusives, on utilise elif (SinonSi) :
Si la condition 1 est vraie alors l'instruction 1 est exécutée et le programme se termine ; si la condition 1 est fausse alors on teste la condition 2 … 
Si la condition 2 est vraie alors l'instruction 2 est exécutée et le programme se termine ; si la condition 2 est fausse alors on teste la condition 3 …  et ainsi de suite …
La dernière instructions (Afficher "Recalé") est donc exécutée si toutes les conditions précédentes sont fausses ... 

*Rajouter une sixième condition : si note entre 8 et 10, afficher "rattrapable"*


```python

```

##### Exercice Mineur Majeur				
*Ecrire un programme qui affiche si un sujet, qui a saisi au clavier son âge, est majeur ou mineur …*   
*Rajouter au programme l'affichage "Vous serez majeur dans ... / Vous êtes majeur depuis ... ans"*


```python

```


```python

```

##### Exercice Année bissextile 						
*Ecrire un programme qui affiche si une année, saisie au clavier est bissextile ou pas …*

Info : une année bissextile est divisible par 4 (ex. 2012), mais une année multiple de 100 (ex. 2100) n'est pas bissextile à moins d'être aussi multiple de 400 (ex. 2000).

Rappel : L'opérateur % calcule le reste d'une division entière. Par exemple, 15%4 vaut 3.   
Ainsi l'expression logique a%4 == 0 est vraie si et seulement si la variable a contient un multiple de 4.


```python

```


```python
    
```
