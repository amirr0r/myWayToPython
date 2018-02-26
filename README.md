# What I didn't know about Python...

- **tuples**: immutables
- **listes** & **dictionnaires** : mutables (valeurs passées par pointeurs)
```python
def test(struct, key=0):
    struct[key] = 14
    return # pas obligé le return

tup = (1, 2, 'abc')
tab = [1, 2, 'abc']
dico = { "nickname":"apprenti programmeur", "age":12 }

#test(tup) # TypeError: 'tuple' object does not support item assignment
print 'tup:', tup # tup: (1, 2, 'abc')
test(tab)
print 'tab:', tab # tab: [14, 2, 'abc']
test(dico, "age")
print 'dico:', dico

del dico["nickname"]
print 'dico:', dico # dico: {'age': 14}
del tab[2]
print 'tab:', tab # tab: [14, 2]
# del tup[0] # TypeError: 'tuple' object doesn't support item deletion
```

/!\ **elif** et pas **else if**
/!\ Pas de **switch..case**
/!\ Pas de **do..while**

- **comprehension list**
```python
tab = range(1,10)
liste=[nb**2 for nb in tab if (nb**2)%2 == 0] 
print liste # [4, 16, 36, 64]

table_multiplication=[(str(x) +' x ' + str(y) + ' = ' + str(x * y)) for x in range(1, 5) for y in range(1, 5)]
print table_multiplication 
# ['1 x 1 = 1', '1 x 2 = 2', '1 x 3 = 3', '1 x 4 = 4', '2 x 1 = 2', '2 x 2 = 4', '2 x 3 = 6', '2 x 4 = 8', '3 x 1 = 3', '3 x 2 = 6', '3 x 3 = 9', '3 x 4 = 12', '4 x 1 = 4', '4 x 2 = 8', '4 x 3 = 12', '4 x 4 = 16']
```

/!\
- **un astérisque * devant le paramètre**: tuple
- **deux astérisques ** devant le paramètre**: dictionnaire
- **locals()**: dictionnaire avec les variables locales.
- **globals()**: dictionnaire avec les variables globales.

## Lambda, Map & filter

```python
ma_fonction = lambda x : x**2 
print ma_fonction(4) # 16
ma_fonction = lambda x,y : x**y 
print ma_fonction(4,2) # 16

liste = [1,3,7,9,12,25,27,45,52]
print map(lambda x : x**2, liste) # [1, 9, 49, 81, 144, 625, 729, 2025, 2704]

print filter(lambda x : x % 2 == 0, range(10)) # [0, 2, 4, 6, 8]
```

## Modules

Il existe **3 manières d'importer un module**(*module = librairie*).
```python
# 1
import os 
print os.system("ping localhost") 
# 2
from os import system 
print system("ping localhost") 
# 3
from os import system as shell 
print shell("ping localhost")
```

## Paquet

Un paquet (ou package) permet de regrouper un ensemble de modules et de les structurer dans une hiérarchie de répertoires.

Chaque répertoire doit contenir un fichier __init__.py qui sera automatiquement exécuté au chargement du package.

Dans ce dossier, créons le fichier suivant : __init__.py. Cela indique à Python qu’il s’agit d’un package. Ce fichier peut être vide, seule sa présence est importante.

### Exemple :

Notre nommerons notre package: **"utils"**. Toujours dans ce répertoire utils, on crée un répertoire nommé **outils** et dans ce dernier on place **un fichier calcul.py**.

```python
def puissance(nb) : 
    return nb**2
```

Créons un nouveau fichier, que nous appelons fichier.py.

```python
from outils.calcul import puissance 

nbr = input("Donnez un nombre? : ") 
nbr_puissance = calcul(nbr) 
print "Votre nombre au carré donne : %d " % nbr_puissance
```

## Fichiers

```python
open(fileName, mode) # open("fichier.txt",'a+')
```

- toutesleslignes = fichier.readlines()
- lalignesuivante = fichier.readline()
- for ligne in fichier:

L'expression **with**
```python
with open(’fichier.txt’,’r’) as mon_fichier : 
    for ligne in mon_fichier : 
        print ligne,
```
>*À la fin du bloc, le fichier est automatiquement fermé.*

/!\ Pour manipuler **les fichiers binaires**, nous utiliserons les méthodes `read()` et `write()`.

Autrement :
- `tell()` permet de connaître l’endroit où nous nous trouvons, elle retourne le nombre d’octets lus depuis le début du fichier.

- `seek()` permet de se déplacer dans le fichier, nous lui indiquons en paramètre la position (nombre d’octets) que nous désirons atteindre.

- `writelines()` permet d’écrire une liste dans un fichier. Elle accepte en paramètre la liste à écrire.

# Modules utiles

## 1. sys : interaction avec l’interpréteur

- `argv`: liste des arguments (argv[0] = nom du script)
- `sys.exit` : quitte l'interpréteur (0: correct, > 0 : erreur)
- `sys.getfilesystemencoding()`: encodage utilisé par le systeme de fichiers.
- `sys.getdefaultencoding()`: encodage par défaut
- `sys.path`:  liste des répertoires dans lesquels l’interpréteur recherche des modules lorsque la directive import est utilisée, ou lorsque des noms de fichiers sont utilisés sans leur chemin complet. path peut être modifiée à la volée dans un programme.
- `sys.platform`: os utilisé
- `sys.stdin`, `sys.stdout` et `sys.stderr`: entrée/sortie standard/erreur.

## 2. os : accéder aux différentes fonctions de notre os

- `os.system(<commande shell>)`: exécuter une commande shell 
- `os.environ`: environnement de l’utilisateur (*variables d’environnement*...)
- `os.getcwd()`: chemin du répertoire courant 
- `os.getgid()`: groupe du processus courant
- `os.getuid()`: utilisateur courant
- `os.getpid()`: processus courant
- `os.chroot(path)`: change répertoire root courant par path
- `os.listdir(path)`: liste du contenu du répertoire donné en argument
- `os.mkdir()`: crée un répertoire à l’emplacement indiqué par le paramètre
- `os.makedirs(path)`: permet de créer des répertoires récursivement
- `os.remove()`: supprime le fichier donné dans le chemin
- `os.removedirs(path)`: supprime les répertoires récursivement
- `os.rename(src,dst)`: renomme (src) en (dst) *fichier, répertoire*
- `os.rmdir(path)`: supprime le répertoire donné en argument
- `os.fork()`: duplique un processus (fork()) et retourne son PID
- `os.walk()`: le path en train d’être listé, les répertoires et les fichiers

## 3. re : expressions régulières


- `.`: n’importe quel caractère.
- `ˆ`: début d’une chaîne, sauf dans des crochets [] où ˆ signifie "qui n’est - pas".
- `$`: fin de chaîne.
- `{n}`: le caractère précédent est répété n fois.
- `{n,m}`: le caractère précédent est répété entre n et m fois.
- `*`: le caractère précédent peut être répété aucune ou plusieurs fois.
- `+`: le caractère précédent peut être répété une ou plusieurs fois.
- `?`: le caractère précédent peut être répété zéro ou une fois.
- `[]`: permet d’indiquer une plage de caractères.

Par exemple :
- abc* pourra nous retourner ab, abc, abcc, abccc...
- abc+ pourra nous retourner abc, abcc, abccc...
- abc? pourra nous retourner ab ou abc.
- ab{2} nous retournera abb.
- ab{2,4} pourra nous retourner abb, abbb, abbbb.
- a.b pourra nous retourner acb, azb, agb...
- [abc] nous retournera une des lettres a, b ou c.
- [a-z] nous retournera une lettre minuscule.
- [a-z]{3} nous retournera trois lettres minuscules, par exemple abc, gfd, bht, vch...
- [a-fA-F0-9]{8} nous retournera un nombre hexadécimal 32 bits.
- [ˆa-z] nous retournera tout sauf des lettres minuscules.

D’autres caractères spéciaux nous seront aussi utiles:
- `\w`: tout caractère alphabétique, identique à [a-zA-Z].
- `\W`: tout ce qui n’est pas un caractères alphabétique.
- `\d`: tout caractère numérique, identique à [0-9].
- `\D`: tout caractère qui n’est pas numérique.
- `\s`: désigne un caractère espace.
- `\S`: désigne un caractère non espace.

```python
regex = re.compile('[a-z]+')
result=regex.match('mon texte')
```

>RegexObject: on retrouve les méthodes search(), match(), split(), sub()...
En plaçant **un r** avant le délimiteur qui ouvre notre chaîne, tous les caractères antislash qu’elle contient sont échappés

- `match()`: s’arrête à la première occurrence valide trouvée
- `search()`: savoir si une occurrence se retrouve au moins une fois dans une chaîne
- `findall()`: permet de trouver toutes les occurrences valides
- `sub()`: remplacer une expression par une autre

Les méthodes acceptent **des drapeaux** pour déterminer comment doit se comporter la recherche, le découpage et le remplacement.

- `re.I ou re.IGNORECASE`: ne pas tenir compte des majuscules et minuscules.
- `re.M ou re.MULTILINE`: déterminer que le caractère `ˆ` symbolise le début de la ligne et également le début de chaque ligne de la chaîne multiligne.
- `re.L ou re.LOCALE`: modifie le comportement des symboles \w \W \b \B \s en accord avec la locale.
- `re.U ou re.UNICODE`: permet que les symboles \w \W \b \B \d \D \s \S s’accordent avec les propriétés du caractère unicode.
- `re.X ou re.VERBOSE`: permet d’écrire des motifs d’expressions régulières plus lisibles, les espaces sont ignorés et nous pouvons mettre des commentaires en fin de ligne.
- `re.S ou re.DOTALL`: permet de définir que le caractère . signifie tous les caractères y compris les retours chariot.
- `re.DEBUG`: affiche des informations de débogage sur l’expression compilée.
