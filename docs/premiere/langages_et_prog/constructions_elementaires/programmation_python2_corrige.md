# Programmation Python - 2

## Les instructions conditionnelles

Dans une suite d'instructions on est souvent amené à faire des choix.

**Si** une ou plusieurs conditions sont réalisées **Alors** on exécute une ou plusieurs instructions


La structure en Python: On indente (une tabulation) les instructions qui doivent s'exécuter si la condition est vérifiée

<pre>
if condition(s) :
    instruction1
    instruction2

</pre>

**Exemple :** Un pâtissier breton vend des petits kouign-amanns au tarif de 1,5 euros l’unité pour l’achat de 1 à 10 pièces et  1,35 euros l’unité pour l’achat de plus de 10 pièces. Le programme ci-dessous permet de calculer le prix de l’achat de  kouign-amann.


```python
n = int(input("Nombre de kouigns ? "))

if n < 9:
    p = 1.5 * n
if n > 10:
    if n < 15 :
        p = 1.35 * n
    else :
        p = 1 * n
    

print("Prix en euros :", p)
```

**Si.............Sinon.....**

<pre>
    if condition(s):
        instruction1
        instruction2
    else:
        instruction3
        
 </pre>

 Dans cette structure, si la ou les conditions sont vraies, les instructions 1 et 2 sont exécutées.
 Sinon c'est l'instruction3 qui est exécutée.
 
 **Voici un exemple**


```python
n = int(input("Nombre de kouigns ? "))

if n < 11:
    p = 1.5 * n
else:
    p = 1.35 * n
print("Prix en euros :", p)
```

**Si.......SinonSi......SinonSi........Sinon**

<pre>
    if condition1:
        instruction1
    elif condition2:
        instruction2
        instruction3
    elif condition3:
        instruction4
    else:
        instruction5
</pre>

Dans cette structure on teste plusieurs conditions

***Remarque : Une instruction conditionnelle if peut être suivie d’un ou plusieurs elif et d’un else.***

**Voici un exemple**




```python
a = 12

if a < 0 :
    print(a, " age incorrect")
elif a < 18:
    print(a, " mineur")
else:
    print(a," majeur")
    
```

***Remarque : on peut également mettre une ou plusieurs instructions if dans une autre***

**Voici un exemple**


```python
a = 12

if a > 0 :
    if a < 18 :
        print(a, " mineur")
    else :
        print(a, " majeur")
else :
    print(a, " age incorrect")
```

On peut également combiner les conditions dans le premier if :


```python
a = 12

if a > 0 and a < 18 :
    print(a, " mineur")
elif a >= 18 :
    print(a, " majeur")
else :
    print(a, " age incorrect")
```

### Exercice 1

Ecrire un programme qui demande un entier à l'utilisateur et affiche s'il est pair ou impair.


```python
a = int(input("un entier :"))
if a%2 == 0 :
    print("pair")
else :
    print("impair")
```

### Exercice 2

Ecrire un programme qui demande 2 nombres à l'utilisateur et affiche le plus grand.


```python
a=int(input("choisir un entier"))
b=int(input("choisir un autre entier"))

if a>b:
    print("le plus grand nombre est",a)
else:
    print("le plus grand nombre est",b)
```

### Exercice 3

Ecrire un programme qui demande 3 nombres à l'utilisateur et affiche le plus grand.


```python
# écrire ici
nb1 = int(input("Un premier nombre : "))
nb2 = int(input("Un deuxième nombre : "))
nb3 = int(input("Un troisième nombre : "))
if nb1 <= nb2 and nb3 <= nb2 : # si nb2 est supérieur ou égal aux deux autres
    print(nb2,"est le plus grand")
elif nb1 >= nb2 and nb1 >= nb3 : # sinon si nb2 est supérieur ou égal aux deux autre
    print(nb1,"est le plus grand")
else :   # sinon nb3 est supérieur ou égal aux deux autres
    print(nb3,"est le plus grand")
```

### Exercice 4

Ecrire un programme qui demande 2 entiers à l'utilisateur et les compare et affiche le résultat (Ex : "x plus grand que y").


```python
entier1 = int(input('entier1 : '))
entier2 = int(input('entier2 : '))
if entier1 > entier2 : 
    print("entier1 est supérieur à entier2")
elif entier2 > entier1 :
    print("entier2 est supérieur à entier1")
else : 
    print ("entier1 est égal à entier2")
```

    entier13
    entier23
    entier1 est égale a entier2
    

### Exercice 5

Pour le diplôme du baccalauréat, si on note m (0<=m<=20) la moyenne du candidat au premier groupe d'épreuves, on distingue six possibilités :
* "Refusé" si m < 8
* "Admis au second groupe" si 8 <= m < 10
* "Admis" si 10 <= m < 12
* "Admis mention assez bien" si 12 <= m < 14
* "Admis mention bien" si 14 <= m < 16
* "Admis mention très bien" sinon

Compléter le script Python ci-dessous pour qu'il affiche la situation d'un candidat en fonction de sa moyenne au premier groupe d'épreuves.


```python
m = int(input("moyenne du candidat "))
if m < 0 :
    print("note non valide")
elif 8 > m :
    print ("Refusé")
elif 8 <= m and m < 10 :
    print ("Admis au second groupe")
elif 10 <= m and m < 12 :
    print ("Admis")
elif 12 <= m and m < 14 :
    print ("Admis mention assez bien")
elif 14 <= m and m < 16 :
    print ("Admis mention bien")
elif m <= 20 :
    print ("Admis mention très bien")
else :
    print("note non valide")
```


```python

```


```python

```
