# TP Python implémentation fonctions de conversion

On cherche à écrire 2 fonctions qui assurent
* la conversion d’un nombre entier décimal en binaire : ``dec2bin()``
* la conversion d’un nombre entier binaire en décimal : ``bin2dec()``

En Python, le type int est affiché en base 10 (exemple 42). Pour permettre son affichage en binaire, on peut construire la chaine de caractère correspondante (exemple ‘101010’). Même chose en hexadécimal (exemple ‘2A’).

<div class="alert alert-info">
Pour parcourir une chaine de caractère, on peut utiliser une boucle for car in chaine :
dans laquelle car prendra successivement la valeur de chacun des caractères de chaine, et qui se répètera autant de fois qu’il y a de caractères dans la chaine.
    </div>

Voici les algorithmes et spécifications de nos 2 fonctions :

````python
def dec2bin(dec):
    """
    convertit un nombre entier décimal en nombre binaire
    # entrée : dec, un nombre entier décimal
    # sortie : bin, une chaine de caractères ‘0’ et ‘1’, la suite de chiffres du nombre binaire correspondant à dec
    """
    bin = ""
    tant que (dec non nul) répéter :
        reste = reste de la division entière de dec par 2
        concaténer str(reste) + bin
        dec = quotient de la division entière de dec par 2
    retourner bin
    

def bin2dec(bin):
    """
    convertit un nombre entier binaire en nombre décimal
    # entrée : bin, une chaine de caractères ‘0’ et ‘1’, la suite de chiffres d’un nombre binaire
    # sortie : dec, un nombre entier décimal, correspondant à bin
    """
    dec = 0
    pour chaque bit de bin répéter :
        dec = dec * 2 + int(bit)
    retourner dec
    
````

<div class="alert alert-success">
A partir de leur spécification et des algorithmes, implémenter les 2 fonctions, les tester sur quelques exemples et tracer, sur un exemple simple, l’exécution des boucles (un print à chaque tour pour afficher le déroulement).
    </div>


```python
# fonctions ici
```


```python

```
