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

Here's my solutions to www.learnpython.org challenges

## Learn the Basics

[**1. Hello, World!**](https://learnpython.org/en/Hello%2C_World%21)

```python
print("Hello, World!")
```

[**2. Variables and Types**](https://learnpython.org/en/Variables_and_Types)

```python
mystring = "hello"
myfloat = 10.0
myint = 20

if mystring == "hello":
    print("String: %s" % mystring)
if isinstance(myfloat, float) and myfloat == 10.0:
    print("Float: %f" % myfloat)
if isinstance(myint, int) and myint == 20:
    print("Integer: %d" % myint)
```

[**3. Lists**](https://learnpython.org/en/Lists)

```python
numbers = []
strings = []
names = ["John", "Eric", "Jessica"]

# write your code here
second_name = names[1]

numbers.append(1)
numbers.append(2)
numbers.append(3)

strings.append("hello")
strings.append("world")

# this code should write out the filled arrays and the second name in the names list (Eric).
print(numbers)
print(strings)
print("The second name on the names list is %s" % second_name)
```

[**4. Basic Operators**](https://learnpython.org/en/Basic_Operators)

```python
x = object()
y = object()

# TODO: change this code
x_list = [x] * 10
y_list = [y] * 10
big_list = x_list + y_list

print("x_list contains %d objects" % len(x_list))
print("y_list contains %d objects" % len(y_list))
print("big_list contains %d objects" % len(big_list))

# testing code
if x_list.count(x) == 10 and y_list.count(y) == 10:
    print("Almost there...")
if big_list.count(x) == 10 and big_list.count(y) == 10:
    print("Great!")
```

[**5. String Formatting**](https://learnpython.org/en/String_Formatting)

```python
#%s - String (or any object with a string representation, like numbers)
#%d - Integers
#%f - Floating point numbers
#%.<number of digits>f - Floating point numbers with a fixed amount of digits to the right of the dot.
#%x/%X - Integers in hex representation (lowercase/uppercase)

data = ("John", "Doe", 53.44)
format_string = "Hello %s %s. Your current balance is $%s."

print(format_string % data)
```

[**6. Basic String Operations**](https://learnpython.org/en/Basic_String_Operations)

```python
s = "Strings are awesome!"
# Length should be 20
print("Length of s = %d" % len(s))

# First occurrence of "a" should be at index 8
print("The first occurrence of the letter a = %d" % s.index("a"))

# Number of a's should be 2
print("a occurs %d times" % s.count("a"))

# Slicing the string into bits
print("The first five characters are '%s'" % s[:5]) # Start to 5
print("The next five characters are '%s'" % s[5:10]) # 5 to 10
print("The thirteenth character is '%s'" % s[12]) # Just number 12
print("The characters with odd index are '%s'" %s[1::2]) #(0-based indexing)
print("The last five characters are '%s'" % s[-5:]) # 5th-from-last to end

# Convert everything to uppercase
print("String in uppercase: %s" % s.upper())

# Convert everything to lowercase
print("String in lowercase: %s" % s.lower())

# Check how a string starts
if s.startswith("Str"):
    print("String starts with 'Str'. Good!")

# Check how a string ends
if s.endswith("ome!"):
    print("String ends with 'ome!'. Good!")

# Split the string into three separate strings,
# each containing only a word
print("Split the words of the string: %s" % s.split(" "))

```

[**7. Conditions**](https://learnpython.org/en/Conditions)

```python
# change this code
number = 16
second_number = 0
first_array = [1, 15, 2]
second_array = [1,2]

if number > 15:
    print("1")

if first_array:
    print("2")

if len(second_array) == 2:
    print("3")

if len(first_array) + len(second_array) == 5:
    print("4")

if first_array and first_array[0] == 1:
    print("5")

if not second_number:
    print("6")
```

[**8. Loops**](https://learnpython.org/en/Loops)

```python
numbers = [
    951, 402, 984, 651, 360, 69, 408, 319, 601, 485, 980, 507, 725, 547, 544,
    615, 83, 165, 141, 501, 263, 617, 865, 575, 219, 390, 984, 592, 236, 105, 942, 941,
    386, 462, 47, 418, 907, 344, 236, 375, 823, 566, 597, 978, 328, 615, 953, 345,
    399, 162, 758, 219, 918, 237, 412, 566, 826, 248, 866, 950, 626, 949, 687, 217,
    815, 67, 104, 58, 512, 24, 892, 894, 767, 553, 81, 379, 843, 831, 445, 742, 717,
    958, 609, 842, 451, 688, 753, 854, 685, 93, 857, 440, 380, 126, 721, 328, 753, 470,
    743, 527
]

# your code goes here
for number in numbers:
    if (number == 237):
        break
    if (number % 2 == 0):
        print(number)
```

[**9. Functions**](https://learnpython.org/en/Functions)

```python
# Modify this function to return a list of strings as defined above
def list_benefits():
    return ["More organized code", "More readable code", "Easier code reuse", "Allowing programmers to share and connect code together"]

# Modify this function to concatenate to each benefit - " is a benefit of functions!"
def build_sentence(benefit):
    return benefit + " is a benefit of functions!"

def name_the_benefits_of_functions():
    list_of_benefits = list_benefits()
    for benefit in list_of_benefits:
        print(build_sentence(benefit))

name_the_benefits_of_functions()
```

[**10. Classes and Objects**](https://learnpython.org/en/Classes_and_Objects)

```python
# define the Vehicle class
class Vehicle:
    name = ""
    kind = "car"
    color = ""
    value = 100.00
    def description(self):
        desc_str = "%s is a %s %s worth $%.2f." % (self.name, self.color, self.kind, self.value)
        return desc_str
# your code goes here
car1 = Vehicle()
car2 = Vehicle()

car1.name = "Fer"
car1.kind = "convertible"
car1.color = "red"
car1.value = 60000.00

car2.name = "Jump"
car2.kind = "van"
car2.color = "blue"
car2.value = 10000.00
# test code
print(car1.description())
print(car2.description())
```

[**11. Dictionaries**](https://learnpython.org/en/Dictionaries)

```python
phonebook = {
    "John" : 938477566,
    "Jack" : 938377264,
    "Jill" : 947662781
}

# write your code here
phonebook["Jake"] = 938273443

del phonebook["Jill"]
# testing code
if "Jake" in phonebook:
    print("Jake is listed in the phonebook.")
if "Jill" not in phonebook:
    print("Jill is not listed in the phonebook.")
```

[**12. Modules and Packages**](https://learnpython.org/en/Modules_and_Packages)

```python
import re

# Your code goes here
match_functions = []
substr = "find"
for functionName in dir(re):
    if substr in functionName:
        match_functions.append(functionName)

print(sorted(match_functions))
```


## Data Science Tutorials

[**1. Numpy Arrays**](https://learnpython.org/en/Numpy_Arrays)

```python
weight_kg = [81.65, 97.52, 95.25, 92.98, 86.18, 88.45]

import numpy as np

# Create a numpy array np_weight_kg from weight_kg
np_weight_kg = np.array(weight_kg)
# Create np_weight_lbs from np_weight_kg
np_weight_lbs = np_weight_kg * 2.2
# Print out np_weight_lbs
print(np_weight_lbs)
# [ 179.63   214.544  209.55   204.556  189.596  194.59 ]
```

[**2. Pandas Basics**](https://learnpython.org/en/Pandas_Basics)
>No real exercices here, just some tests.

```python
dict = {"country": ["Brazil", "Russia", "India", "China", "South Africa"],
       "capital": ["Brasilia", "Moscow", "New Dehli", "Beijing", "Pretoria"],
       "area": [8.516, 17.10, 3.286, 9.597, 1.221],
       "population": [200.4, 143.5, 1252, 1357, 52.98] }

import pandas as pd
brics = pd.DataFrame(dict)
print(brics)
#      area    capital       country  population
# 0   8.516   Brasilia        Brazil      200.40
# 1  17.100     Moscow        Russia      143.50
# 2   3.286  New Dehli         India     1252.00
# 3   9.597    Beijing         China     1357.00
# 4   1.221   Pretoria  South Africa       52.98
# Set the index for brics
brics.index = ["BR", "RU", "IN", "CH", "SA"]

# Print out brics with new index values
print(brics)
#      area    capital       country  population
#BR   8.516   Brasilia        Brazil      200.40
#RU  17.100     Moscow        Russia      143.50
#IN   3.286  New Dehli         India     1252.00
#CH   9.597    Beijing         China     1357.00
#SA   1.221   Pretoria  South Africa       52.98
# Import the cars.csv data: cars
cars = pd.read_csv('cars.csv')

# Print out cars
print(cars)
#     Unnamed: 0  cars_per_cap        country drives_right
#   0         US           809  United States         True
#   1        AUS           731      Australia        False
#   2        JAP           588          Japan        False
#   3         IN            18          India        False
#   4         RU           200         Russia         True
#   5        MOR            70        Morocco         True
#   6         EG            45          Egypt         True
cars = pd.read_csv('cars.csv', index_col = 0)

# Print out country column as Pandas Series
print(cars['cars_per_cap'])
#    US     809
#    AUS    731
#    JAP    588
#    IN      18
#    RU     200
#    MOR     70
#    EG      45

# Print out country column as Pandas DataFrame
print(cars[['cars_per_cap']])
#    Name: cars_per_cap, dtype: int64
#         cars_per_cap
#    US            809
#    AUS           731
#    JAP           588
#    IN             18
#    RU            200
#    MOR            70
#    EG             45

# Print out DataFrame with country and drives_right columns
print(cars[['cars_per_cap', 'country']])
#         cars_per_cap        country
#    US            809  United States
#    AUS           731      Australia
#    JAP           588          Japan
#    IN             18          India
#    RU            200         Russia
#    MOR            70        Morocco
#    EG             45          Egypt

# Print out first 4 observations
print(cars[0:4])
#     cars_per_cap        country drives_right
#US            809  United States         True
#AUS           731      Australia        False
#JAP           588          Japan        False
#IN             18          India        False

# Print out fifth, sixth, and seventh observation
print(cars[4:6])
#     cars_per_cap  country drives_right
#RU            200   Russia         True
#MOR            70  Morocco         True
```

`loc` is label-based, which means that you have to specify rows and columns based on their row and column labels. `iloc` is integer index based, so you have to specify rows and columns by their integer index like you did in the previous exercise.

```python
# Print out observation for Japan
print(cars.iloc[2])
#  cars_per_cap      588
#  country         Japan
#  drives_right    False
#  Name: JAP, dtype: object

# Print out observations for Australia and Egypt
print(cars.loc[['AUS', 'EG']])
#       cars_per_cap    country drives_right
#  AUS           731  Australia        False
#  EG             45      Egypt         True
```

## Advanced Tutorials

[**1. Generators**](https://learnpython.org/en/Generators)

```python
# fill in this function
def fib():
  a, b = 1, 1
  while True:
    a, b = b, a + b
    yield a
  

# testing code
import types
if type(fib()) == types.GeneratorType:
    print("Good, The fib function is a generator.")

    counter = 0
    for n in fib():
        print(n)
        counter += 1
        if counter == 10:
            break
```

[**2. List Comprehensions**](https://learnpython.org/en/List_Comprehensions)

```python
numbers = [34.6, -203.4, 44.9, 68.3, -12.2, 44.6, 12.7]
newlist = [nb for nb in numbers if nb > 0]
print(newlist) 
# [34.6, 44.9, 68.3, 44.6, 12.7]
```

[**3. Multiple Function Arguments**](https://learnpython.org/en/Multiple_Function_Arguments)

```python
def foo(first, second, third, *therest):
    print("First: %s" % first)
    print("Second: %s" % second)
    print("Third: %s" % third)
    print("And all the rest... %s" % list(therest))

foo(1, 2, 3, 4, 5, 6)
# First: 1
# Second: 2
# Third: 3
# And all the rest... [4, 5, 6]

def bar(first, second, third, **options):
    if options.get("action") == "sum":
        print("The sum is: %d" %(first + second + third))

    if options.get("number") == "first":
        return first

result = bar(1, 2, 3, action = "sum", number = "first")
print("Result: %d" %(result))
# The sum is: 6
# Result: 1
# edit the functions prototype and implementation
def foo(a, b, c, *extraArgs):
    return len(extraArgs)

def bar(a, b, c, **options):
    return options.get("magicnumber") == 7


# test code
if foo(1,2,3,4) == 1:
    print("Good.")
if foo(1,2,3,4,5) == 2:
    print("Better.")
if bar(1,2,3,magicnumber = 6) == False:
    print("Great.")
if bar(1,2,3,magicnumber = 7) == True:
    print("Awesome!")
```

[**4. Regular Expressions**](https://learnpython.org/en/Regular_Expressions)

```python
# Exercise: make a regular expression that will match an email
import re
def test_email(your_pattern):
    pattern = re.compile(your_pattern)
    emails = ["john@example.com", "python-list@python.org", "wha.t.`1an?ug{}ly@email.com"]
    for email in emails:
        if not re.match(pattern, email):
            print("You failed to match %s" % (email))
        elif not your_pattern:
            print("Forgot to enter a pattern!")
        else:
            print("Pass")
# Your pattern here!
pattern = r"\"?([-a-zA-Z0-9.`?{}]+@\w+\.\w+)\"?"
test_email(pattern)
```

[**5. Exception Handling**](https://learnpython.org/en/Exception_Handling)

```python
print(a) # NameError: name 'a' is not defined
try:
    print(a)
except NameError:
    print('Fail')
# Fail
# Handle all the exceptions!
#Setup
actor = {"name": "John Cleese", "rank": "awesome"}

#Function to modify, should return the last name of the actor - think back to previous lessons for how to get it
def get_last_name():
    try:
        return actor["last_name"]
    except KeyError:
        try:
            actor_identity = actor["name"].split()
            lastname = actor_identity[1]
            return lastname
        except Exception as e:
            return 'Fail'

#Test code
get_last_name()
print("All exceptions caught! Good job!")
print("The actor's last name is %s" % get_last_name())

# All exceptions caught! Good job!
# The actor's last name is Cleese
```

[**6. Sets**](https://learnpython.org/en/Sets)

```python
a = set(["Jake", "John", "Eric"])
print(a) # {'Eric', 'John', 'Jake'}
b = set(["John", "Jill"])
print(b) # {'John', 'Jill'}

print(a.intersection(b)) # {'John'}
print(b.intersection(a)) # {'John'}

print(a.difference(b)) # {'Eric', 'Jake'}
print(b.difference(a)) # {'Jill'}

print(a.symmetric_difference(b)) # {'Eric', 'Jake', 'Jill'}
print(b.symmetric_difference(a)) # {'Eric', 'Jake', 'Jill'}

print(a.union(b)) # {'Eric', 'John', 'Jake', 'Jill'}
print(b.union(a)) # {'Eric', 'John', 'Jake', 'Jill'}
```

[**7. Serialization**](https://learnpython.org/en/Serialization)

```python
import json

# fix this function, so it adds the given name
# and salary pair to salaries_json, and return it
def add_employee(salaries_json, name, salary):
    salaries = json.loads(salaries_json)
    salaries[name] = salary

    return json.dumps(salaries)

# test code
salaries = '{"Alfred" : 300, "Jane" : 400 }'
new_salaries = add_employee(salaries, "Me", 800)
decoded_salaries = json.loads(new_salaries)
print(decoded_salaries["Alfred"]) # 300
print(decoded_salaries["Jane"]) # 400
print(decoded_salaries["Me"]) # 800
```

[**8. Partial functions**](https://learnpython.org/en/Partial_functions)

```python
# So easy, JS help me check nodeschool.io
#Following is the exercise, function provided:
from functools import partial
def func(u,v,w,x):
    return u*4 + v*3 + w*2 + x
#Enter your code here to create and print with your partial function
four = partial(func, 5)
three = partial(four, 10)
dbl = partial(three, 5)
add = partial(dbl, 0)

print(add()) # 60
```

[**9. Code Introspection**](https://learnpython.org/en/Code_Introspection)

```python
#Code introspection is the ability to examine classes, functions and keywords to know what they are, what they do and what they know.
#Python provides several functions and utilities for code introspection.

# help()
# dir() 
# hasattr() 
# id() 
# type() 
# repr() 
# callable() 
# issubclass() 
# isinstance() 
# __doc__ 
# __name__
class Vehicle:
    name = ""
    kind = "car"
    color = ""
    value = 100.00
    def description(self):
        desc_str = "%s is a %s %s worth $%.2f." % (self.name, self.color, self.kind, self.value)
        return desc_str

# Print a list of all attributes of the Vehicle class.
# Your code goes here
print(dir(Vehicle()))
# ['__class__', '__delattr__', '__dict__', '__dir__', '__doc__', '__eq__', '__format__', '__ge__', '__getattribute__', '__gt__', '__hash__', '__init__', '__le__', '__lt__', '__module__', '__ne__', '__new__', '__reduce__', '__reduce_ex__', '__repr__', '__setattr__', '__sizeof__', '__str__', '__subclasshook__', '__weakref__', 'color', 'description', 'kind', 'name', 'value']
```

[**10. Closures**](https://learnpython.org/en/Closures)

```python
# your code goes here
def multiplier_of(nb):
    def multiplier_by(n):
        return nb * n
    return multiplier_by
     
multiplywith5 = multiplier_of(5)
print(multiplywith5(9))
```

[**11. Decorators**](https://learnpython.org/en/Decorators)

```python

```
