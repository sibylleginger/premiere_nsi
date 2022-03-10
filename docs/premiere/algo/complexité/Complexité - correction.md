###### NSI Spécialité NSI Première - J.J.Dides - nov. 2020 + S. Roux - janv. 2022

# Algorithmes : complexité, terminaison et correction

Rappelons avant de commencer ce qu’est un algorithme. Nous dirons que c’est un ensemble de règles permettant de résoudre un problème sur des données d’entrée.

Cet ensemble de règle définit avec précision un ensemble de séquences d’opérations qui se terminent en un temps fini. Pour résoudre un problème, il existe plusieurs méthodes menant chacune à un algorithme différent.

<div class="alert alert-info" role="alert" style="font-style: verdana;">

Pour chaque algorithme ont peut se poser trois question fondamentales que nous détaillerons dans ce Notebook :
* la question du coût que l’on peut subdiviser en deux sous-questions :
    * le coût en temps
    * le coût en espace (mémoire pour l’ordinateur)
* la question de la terminaison, à savoir si un algorithme se termine ou pas. On se posera cette question en particulier pour les boucles ``while``
* la question de la correction, c’est à dire savoir si l’algorithme résout effectivement le problème de départ. Nous travaillerons ces différentes questions sur des exemples "simples" qu’il faudra maîtriser.

</div>

## Complexité d'un algorithme

L'analyse de la complexité d'un algorithme est une évaluation de son efficacité : le plus souvent, on s'intéresse au temps nécessaire à son exécution. En effet, un programme doit être traité en un temps raisonnable : dès que son exécution devient trop longue, se pose la question d'un algorithme plus efficace ! L'une des principales quête de l'informaticien est la recherche de l'algorithme de plus faible complexité, dit **optimal**.

On compare, bien sur, la performance d'algorithmes indépendamment du langage et de l'environnement de programmation (compilateur, interpréteur ...) utilisés et de l'ordinateur sur lequel sera exécuté le code.   

### Temps de calcul T(n)   

En général, le traitement d'un certain volume de données requiert un temps d'exécution lié au volume de données.    
La complexité en temps sera exprimée par une fonction T(n), *T signifiant Time* et n étant la taille des données traitées.    
Il est ainsi possible d'estimer la performance d'un programme en fonction du volume de données à traiter en mesurant sa durée d'exécution. Plus ces données seront volumineuses, plus leur traitement sera long ...

> *Par exemple, si en doublant le volume n de données, le temps d'exécution d'un programme double et le temps d'exécution d'un autre programme est multiplié par 4, on considère que le premier programme est plus performant. On dit que sa complexité (temporelle) est meilleure !*

### <font color=green> &#9998; Etude de cas </font>
<p style="color : green">Commençons par considérer les 2 fonctions suivantes (elles incrémentent, en boucle, un compteur a) :</p>


```python
def p1(n) :
    a = 0
    for i in range(n) :
        a += 1
    return a

def p2(n) :
    a = 0
    for i in range(n) :
        for j in range(n) :
            a += 1
    return a
```

<p style="color : green">Essayons de comparer "à vu d'oeil" leur durée d'exécution pour n = 500 :</p>


```python
p1(500)
```


```python
p2(500)
```

<p style="color : green">
Pas de différence perceptible : on a l'impression que les 2 programmes se sont exécutés instantanément.</p>
<p style="color : green">
Maintenant testons une valeur plus élévée de n :
</p>


```python
p1(5000)

```


```python
p2(5000)

```

On observe maintenant une nette différence : p2 est beaucoup plus lente que p1.

Il est possible de **mesurer avec précision ce temps d'exécution**, en utilisant la fonction ``perf_counter`` du module ``time``.

>*``perf_counter()`` renvoie un temps en secondes : placée avant et après l'appel à la fonction testée, elle permet de mesurer le temps d'exécution de la fonction.*

Réalisons cette mesure dans une boucle qui fait varier n de 0 à 1000 et affiche la durée d'exécution de ``p1(n)`` pour chaque valeur en millisecondes :


```python
from time import perf_counter
# mesure du temps d'exécution d'une fonction p(n) pour n variant de 0 à 1000 par pas de 100
for n in range(0, 1100, 100) :
    debut = perf_counter()      # mesure du temps avant exécution de la fonction p(n)
    resultat = p2(n)
    fin = perf_counter()        # mesure du temps après exécution de la fonction p(n)
    temps = 1000*(fin - debut)  # calcul du temps d'exécution de p(n) en millisecondes
    print("pour n =", n, ", résultat = ", resultat, " en ", temps, "ms")
```

<p style="color : green">
A vous de mesurer, de la même manière, le temps d'exécution de la fonction p2(n).</p>

Traçons maintenant les **courbes d'évolution du temps d'exécution des fonctions en fonction du volume n de données traitées** ...

*Pour celà, on utilise le module de tracé de courbes *matplotlib*.  *   
*On stocke les valeurs de n dans une liste X, les valeurs du temps d'exécution de f(n) dans une liste Y et on trace la courbe d'évolution de Y en fonction de X. L'opération est réalisée pour p1 puis pour p2 :*


```python
# Tracé de T(n) pour p1
import matplotlib.pyplot as plt
X = []
Y = []
for n in range(0, 1100, 100) :
    debut = perf_counter()
    resultat = p1(n)
    fin = perf_counter()
    temps = 1000*(fin-debut)
    X.append(n)
    Y.append(temps)
plt.plot(X, Y)
```


```python
# Tracé de T(n) pour p2
X = []
Y = []
for n in range(0, 1100, 100) :
    debut = perf_counter()
    resultat = p2(n)
    fin = perf_counter()
    temps = 1000*(fin-debut)
    X.append(n)
    Y.append(temps)
plt.plot(X, Y)
```

Les différences de performance de p1 et p2 apparaissent nettement : non seulement les temps d'exécution obtenus pour p2 sont beaucoup plus importants (quelques dizaines de ms pour p2 contre quelques centièmes de ms pour p1), mais les 2 courbes T(n), des variations du temps d'exécution en fonction de la taille n des données traitées, ont un aspect bien différent ...

> On remarque que l'aspect des courbes est irrégulier et, si l'on renouvelle plusieurs fois l'exécution des tracés, que cette irrégularité varie d'une exécution à l'autre.
>
>En effet les temps mesurés à l'aide de la fonction ``perf_counter()`` concernent l'ensemble du système, qui partage ses ressources entre les différents processus en cours : on n'est jamais sur que les durées obtenues ne concernent que le processus d'exécution de nos programmes python !

Mais l'ordre de grandeur des durées obtenues et l'aspect général des courbes sont conservés !

Pour s'affranchir de ces incertitudes, nous allons opérer plus simplement.

### Nombre d'opérations élémentaires effectuées

On peut se contenter de compter simplement le **nombre d'opérations élémentaires** (affectation, calcul, comparaison ...) effectuées par un programme, en supposant que toutes les opération élémentaires ont un "coût" équivalent en temps.

Reévaluons ainsi la fonction p1 :


```python
def p1(n) :
    a = 0
    for i in range(n) :
        a += 1
    return a
```

<div class="alert alert-warning" role="alert" style="font-style: verdana;">
La fonction p1 effectue n fois l'instruction ``a+=1`` (une incrémentation).    
    
    
Donc, quand n augmente de 1, T(n) augmente de 1, quand n double, T(n) double, etc.
</div>

> Dans les cas de nos 2 fonctions simples, p1 et p2, le résultat des fonctions correspond au nombre exact d'instructions exécutées !

Traçons la courbe du nombre d'incrémentations exécutées par p1 en fonction de la valeur de n :


```python
X = []
Y = []
for n in range(0, 1100, 100) :
    resultat = p1(n)
    X.append(n)
    Y.append(resultat)
plt.plot(X, Y)
```

<div class="alert alert-danger" role="alert" style="font-style: verdana;">
    
Pour p1, la fonction T est bien **linéaire** de type **T(n) = n**.
</div>

Reexaminons maintenant la fonction p2 :


```python
def p2(n) :
    a = 0
    for i in range(n) :
        for j in range(n) :
            a += 1
    return a
```

<div class="alert alert-warning" role="alert" style="font-style: verdana;">  
La fonction p2 effectue n fois la boucle qui exécute n fois l'instruction ``a+=1`` : l'incrémentation ``a+=1`` est donc réalisée n x n = $n^2$ fois .    
    
Quand n est multiplié par 2, T(n) est multiplié par 4 ; quand n est multiplié par 10, T(n) est multiplié par 100 ; etc.
</div>

Traçons la courbe du nombre d'incrémentations exécutées par p2 en fonction de la valeur de n :


```python
# Tracé de T(n) pour p2
X = []
Y = []
for n in range(0, 1100, 100) :
    resultat = p2(n)
    X.append(n)
    Y.append(resultat)
plt.plot(X, Y)
```

<div class="alert alert-danger" role="alert" style="font-style: verdana;">
    
Pour p2, la fonction T est bien de type T(n) = $n^2$, dit **quadratique**.
</div>

### Ordre de grandeur O(*f(n)*)

Pour comparer des algorithmes, on se contente d'une simple estimation du nombre d'opérations réalisées, en ne considérant que son ordre de grandeur O.

> On dit qu'un algorithme est en O(f(n)) si, à partir d'une certaine valeur de n, sa fonction T(n) est toujours dominée par la foncion f."     

Dit plus simplement, la fonction f décrit la partie de T(n) dont la croissance est la plus rapide.

Et on choisira le plus souvent d'évaluer la complexité d'un algorithme dans le **pire des cas** (celui de la situation la plus défavorable).

> par exemple, pour la recherche séquentielle d'un élément dans un tableau, une situation favorable est celle ou l'élément est situé en début de tableau, une situation défavorable est celle ou l'élément est situé en fin de tableau, où pire, celle ou l'élément est absent du tableau.*

Par exemple : p1 est en O($n$) et p2 est en O($n^2$).
Prenons un troisième exemple :


```python
def p3(n) :
    a = 0
    for i in range(n) :
        a += 1
    for i in range(n) :
        a += 1
    for i in range(10) :
        a += 1
    return a
```

<p style="color: green">
    
Combien d'instructions ``a += 1`` sont effectuées lors de l'appel de p3(n) ?</p>


```python
# réponse ici
p3(n) effectue 2n+10 incrémentations *a+=1* : T(n) = 2n+10    
```

Traçons T(n) de p3 comme précédemment :


```python
# Tracé de T(n) pour p3
X = []
Y = []
for n in range(0, 1100, 100) :
    resultat = p3(n)
    X.append(n)
    Y.append(resultat)
plt.plot(X, Y)
```

<div class="alert alert-danger" role="alert" style="font-style: verdana;">
    
Pour p3, la fonction T(n) est d'ordre linéaire O($n$) : pour déterminer cet ordre, on a négligé les constantes 2 et 10 présentes dans T(n) = 2n+10 !
</div>

<div class="alert alert-info" role="alert" style="font-style: verdana;">
    
On peut ainsi catégoriser les différents ordres de grandeur :      
 - **constant** O($1$) : T(n) est indépendant de n (*cas de l'accès à un élement d'un tableau*)
 - **linéaire** O($n$) : si on augmente n de k, on augmente T(n) de k (*cas du parcours d'un tableau à la recherche d'un élement*)
 - **logarithmique** O($log(n)$) : si on multiplie n par 2, on augmente T(n) de 1 (*cas de la recherche dichotomique d'un élément dans un tableau*)
 - **quadratique** O($n^2$) : si on multiplie n par 2, 3 ,4 ..., on multiplie T(n) par 4, 9, 16 ... (*cas du parcours d'un tableau à 2 dimensions à la recherche d'un élément*)
 - **exponentiel** O($2^n$) : si on augmente n de 1, on multiplie T(n) par 2 (*cas du problème du sac à dos que l'on verra plus tard*)
 - etc.
</div>

Voyons ce que cela donne :


```python
# Calcul de T(n) pour différents ordres de grandeur et différentes valeurs de n
from math import log
N = [1,5,10,20,30,40,50,100]
print('O(n)', '\t', '1', '\t', 'log n', '\t', 'n', '\t', 'n**2', '\t', '2**n')
print('n')
for n in N :
    print(n, '\t', 1, '\t', int(log(n,2)), '\t', n, '\t', n**2, '\t', 2**n)
```

Traçons et comparons les fonctions T(n) pour les ordres de grandeur, constants, logarithmique et linéaire ...


```python
from math import log
X = [i for i in range(0,21)]
Y0 = [1 for i in range(0,21)]
Y1 = [i for i in range(0,21)]
Y2 = [log(i,2) for i in range(1,22)]
plt.axis([0,21,0,21])
plt.plot(X, Y0, X, Y1, X, Y2)
```

De tels algorithmes sont très efficace, ils sont de faible complexité : T(n) augmente lentement avec n !

Traçons et comparons les fonctions T(n) pour les ordres de grandeur, linéaire, quadratique et exponentiel ...


```python
X = [i for i in range(0,101)]
Y1 = [i for i in range(0,101)]
Y3 = [i**2 for i in range(0,101)]
Y4 = [2**i for i in range(0,101)]
plt.axis([0,101,0,101])
plt.plot(X, Y3,  X, Y1, X, Y4)
```

De tels algorithmes sont peu efficace, ils sont de forte complexité : T(n) augmente rapidement avec n !



Dans la suite du chapitre, différentes études de cas vont permettre de rechercher l'algorithme le plus efficace parmi plusieurs algorithmes résolvant tous un même problème (exemple : recherche dans un tableau, tris d'un tableau, etc.).

## <font color=green> &#9998; Application </font>

<div class="alert alert-danger" role="alert" style="font-style: verdana;">
    
Le problème : on s’intéresse à la recherche d’occurrence sur des valeurs (de type quelconque : nombre, booléens,chaine de caractère, liste...) dans une liste.
    
Nous noterons ``c`` l’élément recherché (cible) et la liste dans laquelle nous cherchons sera notée ``L``. Voici un algorithme en langage naturel qui résout ce problème :
</div>

![Algorigthme de recherche dans une liste](https://capytale2.ac-paris.fr/web/sites/default/files/2022/01-19/11-38-33/algo_recherche.png)

<font color=green> Écrire, ci-dessous, une implémentation en Python de cet algorithme sous la forme d’une fonction nommée ``recherche`` et la compléter par deux tests.</font>


```python
# fonction recherche ici
def recherche(L,c):
    present = False
    for i in range(len(L)) :
        if c == L[i] :
            present = True
    return present

# tests ici
assert recherche([1,2,3,4,5], 5) == True
assert recherche([2,5,8,2,1], 3) == False
```

<font color="green">
Intéressons-nous aux questions évoquées en introduction.
</font>
 
<br>
<br>

<font color="green">
    
1. **La complexité** : Quel l'ordre de grandeur de la complexité de la fonction ``recherche()``?
</font>


```python

```

<font color="green">
    
2. **La terminaison** : Cet algorithme se finira-t-il en un temps fini?
</font>


```python

```

<font color="green">
    
3. **La correction** : L’algorithme fait-il ce pourquoi il est conçu?
</font>


```python

```

## Terminaison et correction

Pour certains algorithmes, il peut être difficile de prouver que l’algorithme se termine et qu’il fait ce qui est attendu. Des "outils" théoriques vont nous aider.

Dans cette partie, nous allons découvrir comment **démontrer** qu’une boucle ``while`` se termine avec le **variant** de boucle, puis nous allons prouver qu’un algorithme est correct avec **l’invariant** de boucle.

### Terminaison et variant de boucle

Pour montrons que cet algorithme se termine, il va falloir prouver que la boucle ``while`` ne boucle pas indéfiniment. Pour cela nous allons utiliser un **variant de boucle**.

<div class="alert alert-danger" role="alert" style="font-style: verdana;">

**Définition** : variant de boucle    
Un variant de boucle est une expression :
* entière
* positive
* qui décroît strictement à chaque itération
</div>

<div class="alert alert-info" role="alert" style="font-style: verdana;">

**Variants usuels**
* i  pour une boucle du type for i in range(deb, fin, -1) 
* n−i  pour une boucle du type for i in range(n) 
* j−i  pour deux variables i  croissante et j  décroissante
* ...
</div>

Il n'y a pas de technique systématique.

## <font color=green> &#9998; Application </font>

<font color=green>Justifier la terminaison de l'algorithme ci-dessous de multiplication de deux entiers en identifiant un **variant de boucle.**</font>


```python
a = int(input("a : "))
b = int(input("b : "))
i = 0
m = 0
while i < b:
   m += a
   i += 1
print("a*b = ", m)
```


```python
# réponse ici
invariant : b-i
b-i est positif si b est positif et i augmente de 1 à chaque itération.
donc b-i va diminuer a chaque tour et va sera nul au bout d'un certains nombre d'itération, ce qui terminera la boucle.
```

### Correction et invariant de boucle

<div class="alert alert-danger" role="alert" style="font-style: verdana;">

**Définition** : invariant de boucle    
L’invariant de boucle est une formule logique qui :
* est vérifiée à l’initialisation de la boucle
* reste vraie à chaque itération de la boucle
</div>

<div class="alert alert-info" role="alert" style="font-style: verdana;">
    
Voici une méthode pour prouver la terminaison et la correction d’un algorithme ayant une boucle ``while``:
* Définir clairement lespréconditions– état des variables initial (avant la boucle)
* Déterminer la variant de boucle et prouver la terminaison de la boucle
* Définir un invariant de boucle
* Prouver que l’invariant est vrai au début de la boucle et à chaque itération
* Montrer qu’en sortie de boucle l’invariant est vrai et que combiné à la condition de sortie de boucle il permet de prouver que l’algorithme est correct
</div>

Pour vérifier qu'une expression est un invariant on utilise la preuve par récurrence.  

Dans notre exemple de multiplication, l'invariant est ``m = a*i``. En effet :
* à l'initialisation (avant la boucle) : ``m = 0`` et ``i = 0`` donc ``a*i = 0`` (donc ``m = a*i``)
* à chaque tour de boucle : m augmente de a (on notera la nouvelle valeur ``m' = m+a``) et i augmente de 1 (on notera ``i' = i+1``)
    * Si au début du tour de boucle on a ``m = a*i``, on veut vérifier qu'à la fin du tour ``m' = a*i'``
    * à la fin du tour ``m' = m+a`` &#10132; ``m' = a*i + a`` &#10132; ``m' = a*(i + 1)`` &#10132; ``m' = a*i'``

On a bien prouvé que l'invariant reste vrai à chaque tour de boucle, ainsi à la fin du programme i = b (car la boucle while s'arrête quand i = b) donc ``m = a*b``. L'algorithme calcule bien le produit de a par b.

## <font color=green> &#9998; Application </font>

<font color=green>On considère l'algorithme suivant :</font>

![Algorigthme de calcul de factorielle](https://capytale2.ac-paris.fr/web/sites/default/files/2022/01-19/11-38-33/algo_factorielle.png)


<font color=green>

1. Prouver que l'algorithme termine.
2. On  note $n!$ le  nombre  entier  défini  par $n! = n×(n−1)×(n−2)×...×3×2×1$ (on dira « n factorielle »)
    1. Calculer ``factorielle(4)`` et $4!$,  puis ``factorielle(7)`` et $7!$
    2. Selon vous, que fait ce programme ?
3. Montrer que $f=i!$ est un invariant de la boucle.
4. Prouver que cet algorithme est correct.
5. Quelle est la complexité de cet algorithme ?

</font>


```python

```
