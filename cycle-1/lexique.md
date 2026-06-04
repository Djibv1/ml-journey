# Lexique Python — Cycle 1

Mes notes au fil des modules Kaggle Learn (dans l'ordre où je les vois).
Chaque truc : déf avec mes mots + un exemple. J'ajoute en continu.

---

## Module 1 — Hello, Python

### Variable
Un nom auquel j'associe une valeur. En Python pas de `let`/`const` comme en JS,
juste l'affectation directe.

```python
nom = "Djilani"
age = 25
```

### Types primitifs
Les briques de base :

- `str` — chaîne de caractères : `"hello"`, `'a'`
- `int` — entier : `42`, `-7`, `0`
- `float` — nombre à virgule : `3.14`, `-2.5`
- `bool` — `True` ou `False` (majuscule obligatoire, pas comme JS)
- `None` — l'absence de valeur, genre le `null`/`undefined` du JS

### `print()`
Affiche dans la console. Plusieurs valeurs séparées par des virgules.

```python
print("Bonjour", nom, age)   # Bonjour Djilani 25
```

### `type()`
Te rend la **classe** de la valeur — pas une string comme `typeof` en JS.

```python
type(42)        # <class 'int'>
type("hello")   # <class 'str'>
```

### Commentaire
Ligne ignorée par Python, commence par `#`.

```python
# ceci est un commentaire
```

### Opérateurs arithmétiques
Les classiques, plus deux pièges (`//` et `**`) :

| Op   | Sens                                  | Exemple                 |
| ---- | ------------------------------------- | ----------------------- |
| `+`  | addition (ou concat de strings)       | `2 + 3` → `5`           |
| `-`  | soustraction                          | `5 - 2` → `3`           |
| `*`  | multiplication (ou répétition string) | `"ab" * 3` → `"ababab"` |
| `/`  | division (rend toujours un float)     | `7 / 2` → `3.5`         |
| `//` | division entière                      | `7 // 2` → `3`          |
| `%`  | modulo (le reste)                     | `7 % 2` → `1`           |
| `**` | puissance                             | `2 ** 3` → `8`          |

### Conversion de type (cast)
Forcer un type vers un autre.

```python
int("42")      # 42
str(42)        # "42"
float("3.14")  # 3.14
bool(0)        # False — 0 c'est falsy
bool(1)        # True
```

### f-string
Le format string moderne, genre les template strings du JS (les backticks).

```python
print(f"Bonjour {nom}, tu as {age} ans")
```

---

## Module 2 — Functions and Getting Help

### Fonction (`def`)
Bloc de code réutilisable avec un nom. Prend des paramètres, retourne une valeur.

```python
def square(n):
    return n ** 2

square(5)   # 25
```

### `return`
Renvoie une valeur depuis la fonction (vs `print` qui ne fait qu'afficher).
Une fonction sans `return` retourne implicitement `None`.

```python
def add(a, b):
    return a + b

result = add(2, 3)   # result = 5, réutilisable plus loin
```

### `print` vs `return` (le piège fondamental ⚠️)
- `print` = affichage humain, c'est un effet de bord
- `return` = une valeur que je peux réutiliser dans le code

Une fonction qui `print` mais ne `return` rien, je peux pas la chaîner ni la tester.
C'est LE truc à pas confondre au début.

### Argument
La valeur que je passe à une fonction au moment de l'appel.

```python
def greet(name):          # 'name' = le paramètre
    print(f"Salut {name}")

greet("Djilani")          # "Djilani" = l'argument
```

### Argument par défaut
Une valeur de repli si l'argument n'est pas fourni.

```python
def greet(name, lang="fr"):
    if lang == "fr":
        print(f"Salut {name}")
    else:
        print(f"Hi {name}")

greet("Djilani")          # "Salut Djilani"
greet("Djilani", "en")    # "Hi Djilani"
```

### Argument nommé (keyword argument)
Passer un argument en précisant son nom — plus clair, et l'ordre devient flexible.

```python
greet(lang="en", name="Djilani")
```

### Docstring
La doc d'une fonction, en triple guillemets juste après le `def`. Lue par `help()`.

```python
def square(n):
    """Retourne le carré de n.

    Examples:
        >>> square(3)
        9
    """
    return n ** 2
```

### `help()`
Affiche la doc d'une fonction, classe ou module.

```python
help(square)   # affiche la docstring
help(print)    # la doc du built-in print
```

### Composition de fonctions
Une fonction qui en appelle d'autres dedans, en passant le résultat de l'une à l'autre.

```python
def kilos_to_grams(k):
    return k * 1000

def grams_to_milligrams(g):
    return g * 1000

def kilos_to_milligrams(k):
    grams = kilos_to_grams(k)            # appelle la 1re
    return grams_to_milligrams(grams)    # passe le résultat à la 2e
```

---

## Module 3 — Booleans and Conditionals

### Booléen (`bool`)
Type à 2 valeurs possibles : `True` et `False` (majuscule obligatoire).

### Opérateurs de comparaison
Rendent un booléen.

| Op        | Sens       |
| --------- | ---------- |
| `==`      | égalité    |
| `!=`      | différence |
| `<` `>`   | strict     |
| `<=` `>=` | inclusif   |

### Opérateurs logiques
Combinent des booléens. En Python c'est des **mots-clés**, pas `&&`/`||` comme JS.

```python
True and False   # False
True or False    # True
not True         # False
```

### Short-circuit (court-circuit)
`and`/`or` évaluent paresseusement et te rendent la première valeur déterminante.
Pratique pour les valeurs par défaut.

```python
x = None
x or "default"   # "default"
x and "ok"       # None (rien à évaluer après)
```

### `if / elif / else`
Le branchement conditionnel.

```python
if score < 30:
    return "T1"
elif score <= 70:
    return "T2"
else:
    return "T3"
```

`elif` = "else if" en un mot. Les branches sont **mutuellement exclusives** :
l'évaluation s'arrête à la 1re vraie.

### Conditional expression (ternaire)
La conditionnelle sur une ligne. Attention, l'ordre est **inversé** par rapport au
`cond ? x : y` du JS.

```python
statut = "majeur" if age >= 18 else "mineur"
```

Format : `valeur_si_vrai if condition else valeur_si_faux`.

### Truthy / Falsy
Comment une valeur est évaluée dans un contexte booléen (un `if` par ex).

- **Falsy** (vaut `False`) : `False`, `None`, `0`, `0.0`, `""`, `[]`, `{}`, `()`
- **Truthy** (vaut `True`) : tout le reste — y compris `"0"`, `[0]`, les négatifs…

```python
if []:
    print("ne s'affiche pas")     # liste vide = falsy
if "0":
    print("s'affiche")            # string non vide = truthy même si c'est "0"
```

### `bool()`
Convertit une valeur en booléen selon les règles truthy/falsy.

```python
bool(0)        # False
bool("hello")  # True
bool([])       # False
```

---

## Module 4 — Lists

### Liste (`list`)
Collection ordonnée, **mutable** (modifiable), peut mélanger les types.

```python
themes = ['ai-llms', 'dev-code', 'design-ui']
mix = [1, "a", True, None]
```

### Indexing
Accès à un élément par sa position. Les indices commencent à **0**.

```python
themes[0]    # 'ai-llms' (le 1er)
themes[2]    # 'design-ui' (le 3e)
themes[-1]   # 'design-ui' (le dernier, indice négatif)
themes[-2]   # 'dev-code' (l'avant-dernier)
```

### Slicing
Extraire une sous-liste avec `liste[début:fin:pas]`.

```python
themes[0:2]    # ['ai-llms', 'dev-code'] (0 inclus → 2 exclu)
themes[:2]     # pareil (début par défaut = 0)
themes[1:]     # ['dev-code', 'design-ui'] (jusqu'à la fin)
themes[::-1]   # la liste inversée
themes[::2]    # 1 élément sur 2
```

### Mutations (modifier la liste en place)
Les listes sont mutables. Ces méthodes modifient la liste directement et rendent
souvent `None` (donc je les chaîne pas).

| Méthode               | Effet                                      | Exemple                  |
| --------------------- | ------------------------------------------ | ------------------------ |
| `.append(x)`          | ajoute x à la fin                          | `lst.append(4)`          |
| `.insert(i, x)`       | insère x à l'index i                       | `lst.insert(0, "new")`   |
| `.pop()`              | retire et rend le dernier                  | `last = lst.pop()`       |
| `.pop(i)`             | retire et rend l'élément à l'index i       | `x = lst.pop(2)`         |
| `.remove(x)`          | retire la 1re occurrence de x (par valeur) | `lst.remove("a")`        |
| `.sort()`             | trie en place (ascendant par défaut)       | `lst.sort()`             |
| `.sort(reverse=True)` | trie en place descendant                   | `lst.sort(reverse=True)` |
| `.reverse()`          | inverse l'ordre en place                   | `lst.reverse()`          |
| `.extend(autre)`      | ajoute tous les éléments de `autre`        | `lst.extend([4,5,6])`    |

### Built-ins utiles sur liste

| Fonction               | Effet                                                          |
| ---------------------- | -------------------------------------------------------------- |
| `len(lst)`             | le nombre d'éléments                                           |
| `sorted(lst)`          | rend une **nouvelle** liste triée (touche pas à l'originale)   |
| `sum(lst)`             | la somme des éléments numériques                               |
| `min(lst)`, `max(lst)` | le min / max (numérique, ou lexicographique pour des strings)  |
| `x in lst`             | `True` si x est dans la liste                                  |

À retenir : `lst.sort()` modifie en place et rend `None`. `sorted(lst)` ne touche
à rien et rend une nouvelle liste.

### Concaténation
Combiner 2 listes avec `+` (ça crée une nouvelle liste).

```python
[1, 2] + [3, 4]   # [1, 2, 3, 4]
```

Vs `extend` qui modifie en place :

```python
a = [1, 2]
a.extend([3, 4])   # a == [1, 2, 3, 4] (modifié)
```

### Tuple
Collection ordonnée mais **immutable** (non modifiable). Parenthèses au lieu de crochets.

```python
coords = (10, 20, 30)
coords[0]        # 10 (indexing OK)
coords[0] = 99   # ❌ TypeError, c'est immutable
```

Tuple vs list, quand utiliser quoi :
- **Tuple** : des valeurs fixes qui vont ensemble (coordonnées, dates, retour multiple d'une fonction)
- **List** : une collection que je vais modifier au fil du temps

### Unpacking (déstructuration)
Affecter plusieurs variables d'un coup depuis un tuple/liste.

```python
x, y, z = (10, 20, 30)
print(x)   # 10

a, b, c = [1, 2, 3]   # marche aussi avec les listes
```

### Swap (échange de variables)
Le cas d'usage emblématique de l'unpacking — pas besoin de variable temporaire.

```python
a, b = 5, 10
a, b = b, a   # swap en 1 ligne → a == 10, b == 5
```

### Mutabilité partagée (gros piège ⚠️)
Quand j'assigne une liste à une autre variable, les **2 pointent vers la même liste**.
Du coup modifier l'une modifie l'autre.

```python
a = [1, 2, 3]
b = a           # b = juste un autre nom pour la même liste
b.append(4)
print(a)        # [1, 2, 3, 4] ⚠️ modifié aussi !
```

Pour copier pour de vrai : `b = a.copy()` ou `b = a[:]` (slice complet).

---

## Module 5 — Loops and List Comprehensions

### Boucle `for`
Itère sur n'importe quel itérable (liste, tuple, string, range, dict...). Pas de
`for(i=0; i<n; i++)` à la C/JS — on itère sur des **éléments**, pas des indices.

```python
themes = ['ai-llms', 'dev-code', 'design-ui']
for t in themes:
    print(t)
```

Si vraiment je veux les indices : voir `enumerate` plus bas.

### `range()`
Génère une séquence de nombres. Quasi tjrs utilisé avec `for`.

```python
range(5)          # 0, 1, 2, 3, 4 (stop exclu)
range(2, 7)       # 2, 3, 4, 5, 6 (start inclus, stop exclu)
range(0, 10, 2)   # 0, 2, 4, 6, 8 (avec pas)

for i in range(3):
    print(i)      # 0, 1, 2
```

À retenir : `stop` est **exclu**. `range(5)` rend 5 nombres, de 0 à 4.

### `enumerate()`
Itère avec **index + valeur** d'un coup, pour pas recourir à `range(len(lst))`
(considéré non-pythonique).

```python
for i, t in enumerate(themes):
    print(f"{i}: {t}")
# 0: ai-llms
# 1: dev-code
# 2: design-ui

# Avec un index qui démarre à 1 :
for i, t in enumerate(themes, start=1):
    print(f"{i}. {t}")
```

### Boucle `while`
Tant que la condition est vraie. Important : **modifier la condition** dans le
corps de la boucle, sinon boucle infinie.

```python
guess = 0
secret = 7
while guess != secret:
    guess += 1
print(f"Trouvé en {guess} essais")
```

### List comprehension
Façon condensée de construire une liste depuis un itérable. Une ligne, lisible.
Format : `[expression for x in iterable]`.

```python
# Carrés de 1 à 5
carres = [n ** 2 for n in range(1, 6)]   # [1, 4, 9, 16, 25]

# Equivalent en for verbeux :
carres = []
for n in range(1, 6):
    carres.append(n ** 2)
```

### List comprehension avec condition (filtre)
Ajout d'un `if` à la fin pour filtrer.

```python
themes_ai = [t for t in themes if t.startswith("ai")]
nombres_pairs = [n for n in range(10) if n % 2 == 0]
```

### List comprehension avec transformation + condition
Combiner les deux : transformer ET filtrer.

```python
# Longueurs des thèmes qui commencent par "ai"
longueurs = [len(t) for t in themes if t.startswith("ai")]
```

### Nested list comprehension
Comp imbriquée — vraiment utile pour les grilles / produits cartésiens. Pas
forcément à utiliser tout le temps (lisibilité), mais à savoir lire.

```python
# Table de multiplication 3x3
table = [[i * j for j in range(1, 4)] for i in range(1, 4)]
# [[1, 2, 3], [2, 4, 6], [3, 6, 9]]
```

### `min` / `max` / `sum` / `any` / `all`
Built-ins sur itérables. Utiles partout.

| Fonction         | Sens                                          |
| ---------------- | --------------------------------------------- |
| `min(lst)`       | le plus petit                                 |
| `max(lst)`       | le plus grand                                 |
| `sum(lst)`       | la somme (sur des numériques)                 |
| `any(lst)`       | `True` si au moins 1 élément est truthy       |
| `all(lst)`       | `True` si TOUS les éléments sont truthy       |

```python
notes = [12, 15, 8, 16, 18]
all(n >= 10 for n in notes)   # False (8 < 10)
any(n >= 18 for n in notes)   # True (18)
sum(notes)                    # 69
```

À retenir : `any` et `all` consomment souvent une **expression génératrice**
(comme une list comp mais sans crochets). Pas besoin de creuser pour l'instant,
juste savoir que `(n > 10 for n in lst)` marche dans `any()`/`all()`.

---

## Module 6 — Strings and Dictionaries

### String — c'est aussi une séquence
Une string se comporte comme une liste de caractères : indexing, slicing, `in`,
`len()`, `for c in s` — tout marche pareil.

```python
mot = "python"
mot[0]       # 'p'
mot[-1]      # 'n'
mot[1:4]     # 'yth'
len(mot)     # 6
"th" in mot  # True
```

⚠️ Différence majeure avec une liste : une string est **immutable**. `mot[0] = 'P'`
plante (TypeError). Pour "modifier", on crée une nouvelle string.

### Méthodes de string utiles

| Méthode                  | Effet                                        | Exemple                                |
| ------------------------ | -------------------------------------------- | -------------------------------------- |
| `.upper()` / `.lower()`  | maj / min                                    | `"abc".upper()` → `"ABC"`              |
| `.strip()`               | retire les espaces (et `\n`) début/fin       | `"  hi  ".strip()` → `"hi"`            |
| `.split(sep)`            | découpe en liste sur `sep`                   | `"a,b,c".split(",")` → `["a","b","c"]` |
| `.split()` sans arg      | découpe sur tout whitespace (espaces, tabs, retours ligne) | `"hello world".split()` → `["hello", "world"]` |
| `.join(lst)`             | colle une liste de strings avec le séparateur | `",".join(["a","b","c"])` → `"a,b,c"` |
| `.startswith(x)`         | bool : commence par x                        | `"ai-llm".startswith("ai")` → `True`   |
| `.endswith(x)`           | bool : finit par x                           | `"file.md".endswith(".md")` → `True`   |
| `.replace(a, b)`         | remplace toutes les occurrences de a par b   | `"a-b-c".replace("-", "_")` → `"a_b_c"` |
| `.count(x)`              | nombre d'occurrences                         | `"abab".count("a")` → `2`              |
| `.find(x)`               | index de la 1re occurrence, ou `-1` si absent | `"hello".find("l")` → `2`              |

Toutes ces méthodes **rendent une nouvelle string**, l'originale est intouchée
(parce qu'une string c'est immutable).

### f-string formatting avancé
Déjà vu en module 1, mais ici on peut formater à l'intérieur.

```python
pi = 3.14159
f"{pi:.2f}"          # "3.14" (2 décimales)
f"{42:05d}"          # "00042" (entier paddé sur 5 caractères)
f"{0.85:.0%}"        # "85%" (pourcentage)
```

### Dictionnaire (`dict`)
Collection **clé → valeur** non ordonnée (enfin, ordonnée par insertion depuis Python 3.7,
mais on s'en sert pas pour l'ordre). Genre objet JS / hashmap.

```python
note = {
    "title": "machine learning",
    "theme": "ai-llms",
    "tier": "T2"
}
```

Clés : tjrs **immuables** (string, int, tuple). Pas de liste comme clé.

### Accès aux valeurs

```python
note["title"]               # "machine learning"
note["inconnu"]             # ❌ KeyError
note.get("inconnu")         # None (pas d'erreur)
note.get("inconnu", "N/A")  # "N/A" (valeur par défaut)
```

⚠️ Bracket `d[key]` plante si la clé existe pas. `.get(key, default)` est safe.

### Modification

```python
note["rating"] = 5         # ajoute une nouvelle clé
note["tier"] = "T3"        # écrase l'existant
del note["rating"]         # supprime la clé
```

### Tester la présence d'une clé

```python
"title" in note            # True (teste les CLÉS, pas les valeurs)
"machine learning" in note # False — c'est une valeur, pas une clé
```

### Itération sur un dict
3 façons : sur les clés (défaut), sur les valeurs, sur les paires.

```python
for k in note:              # itère sur les clés (équivalent .keys())
    print(k)

for v in note.values():     # juste les valeurs
    print(v)

for k, v in note.items():   # le combo — le plus utile
    print(f"{k} = {v}")
```

`.items()` = LA méthode qu'on utilise tout le temps en pratique.

### Comptage avec un dict (pattern classique)
Compter les occurrences de trucs dans une liste — pattern qu'on refait souvent.

```python
mots = ["python", "ml", "python", "data", "ml", "python"]
counts = {}
for m in mots:
    counts[m] = counts.get(m, 0) + 1
# {"python": 3, "ml": 2, "data": 1}
```

Le `.get(m, 0)` évite de devoir tester si la clé existe avant.

### Dict comprehension
Comme list comp mais avec `{clé: valeur for ...}`.

```python
# Longueur de chaque thème
longueurs = {t: len(t) for t in themes}
# {"ai-llms": 7, "dev-code": 8, "design-ui": 9}

# Filtrer un dict existant
notes_t2 = {k: v for k, v in note.items() if v == "T2"}
```

---

## Module 7 — Working with External Libraries

### `import`
Charger un module externe (ou de la stdlib). Une fois importé, j'accède à ses
fonctions/classes avec la notation `module.truc`.

```python
import math

math.pi          # 3.141592...
math.sqrt(16)    # 4.0
math.floor(3.7)  # 3
```

### `import X as Y` (alias)
Pour raccourcir. Les conventions canoniques en data/ML :

```python
import numpy as np       # numpy en np
import pandas as pd      # pandas en pd
import matplotlib.pyplot as plt
```

À respecter même si je trouve ça moche au début — c'est ce que tout le monde
écrit, faut s'aligner.

### `from X import Y`
Importer juste une fonction/classe précise du module, sans préfixe.

```python
from math import sqrt, pi
sqrt(16)     # 4.0 (plus besoin de math.sqrt)
pi           # 3.14...
```

⚠️ Piège : `from math import *` importe TOUT et pollue mon namespace. À éviter
sauf cas très spécifique.

### `dir()` et `help()` sur un module
Explorer un module sans aller sur la doc.

```python
import math
dir(math)   # liste tous les attributs/fonctions du module
help(math)  # affiche la doc du module entier
help(math.sqrt)  # doc d'une fonction précise
```

### Type confusion / duck typing
Quand une lib externe rend un objet qui **ressemble à une liste/dict** mais qui
n'en est pas un. Genre numpy rend des `ndarray` qui se comportent comme des
listes... sauf que pas vraiment.

```python
import numpy as np
arr = np.array([1, 2, 3])
type(arr)    # <class 'numpy.ndarray'> — pas list !
arr[0]       # 1 (indexing marche)
arr + arr    # array([2, 4, 6]) (addition vectorisée, pas concat liste !)
```

Règle : quand je code avec une lib externe, je `type()` les objets pour pas me
faire piéger. Surtout quand un message d'erreur parle d'un type que je connais pas.

---

## Complément — outils pour le test de sortie de bloc

Pas dans Kaggle module 7, mais nécessaires pour le mini-script 50 lignes
(lecture de fichiers, parcours de dossier).

### Lire un fichier — `with open(...)`
Le pattern canonique. `with` ferme le fichier automatiquement à la fin.

```python
with open("note.md", "r", encoding="utf-8") as f:
    contenu = f.read()        # tout le fichier en une string
```

3 méthodes de lecture utiles :

| Méthode               | Rend                                                  |
| --------------------- | ----------------------------------------------------- |
| `f.read()`            | toute la string                                       |
| `f.readlines()`       | liste de lignes (avec `\n` à la fin de chaque ligne)  |
| `f.read().splitlines()` | liste de lignes (sans le `\n`) — souvent + propre  |

Pour itérer ligne par ligne sans tout charger en mémoire :

```python
with open("note.md", encoding="utf-8") as f:
    for ligne in f:
        print(ligne.strip())   # strip pour virer le \n de fin
```

### Parcourir un dossier — `pathlib`
Plus moderne que `os.listdir`. À préférer.

```python
from pathlib import Path

dossier = Path("00-Inbox")
for fichier in dossier.iterdir():
    print(fichier.name)    # juste le nom
    print(fichier)         # le chemin complet

# Filtrer par extension :
for fichier in dossier.glob("*.md"):
    print(fichier.name)

# Récursif (sous-dossiers inclus) :
for fichier in dossier.rglob("*.md"):
    print(fichier)
```

### Trier un dict / une liste avec une clé custom
Utile pour trier les mots par fréquence.

```python
counts = {"python": 3, "ml": 2, "data": 1}

# Trier les clés du dict par leur valeur (fréquence), décroissant
tri = sorted(counts.items(), key=lambda kv: kv[1], reverse=True)
# [("python", 3), ("ml", 2), ("data", 1)]
```

Le `key=` prend une fonction qui dit "trie selon quoi". `lambda kv: kv[1]`
extrait le 2e élément de chaque paire (la valeur). On voit la lambda en
détail plus tard, pour l'instant retenir la syntaxe.

### Tester rapidement avec `print` partout
Pendant le test, pas honte de mettre des `print` à tous les coins pour voir
ce qui se passe — c'est mon `console.log` Python. Je virerai à la fin.

---

## À venir (sections vides pour plus tard)

### Cycle 1 — Bloc 1.4 (OOP minimal)

(Pas dans Kaggle Learn Python — session dédiée, indispensable pour `nn.Module` cycle 4 PyTorch.)

#### Classe vs instance
- **Classe** = le moule, le blueprint ("voici comment est faite une note")
- **Instance** = un objet concret créé depuis ce moule ("voici LA note 'ML basics'")

Une seule classe peut produire 100 instances avec des valeurs différentes. Comme un dict :
le type `dict` est unique, mais tu peux avoir plein de dicts différents.

#### `class` + `__init__` + `self`

```python
class Note:
    def __init__(self, title, theme, tier="T2"):
        # self = l'objet en construction. Équivalent du `this` JS,
        # MAIS doit être explicite en 1er param de chaque méthode.
        self.title = title
        self.theme = theme
        self.tier = tier
        self.rating = None             # valeur par défaut

    def set_rating(self, rating):      # méthode = fonction qui prend self
        self.rating = int(rating)

    def summary(self):
        rating_str = f"⭐{self.rating}" if self.rating is not None else "⭐?"
        return f"{self.title} [{self.theme} · {self.tier} · {rating_str}]"

# Instanciation : on appelle la classe comme une fonction
# (PAS de mot-clé `new` comme en JS)
n1 = Note("ML basics", "ai-llms")        # tier prend la valeur par défaut "T2"
n2 = Note("Numpy intro", "dev-code", "T3")
n1.set_rating(4)
print(n1.summary())                      # "ML basics [ai-llms · T2 · ⭐4]"
```

**À retenir** :
- `class Note:` — PascalCase par convention
- Pas de `new`, juste `Note(...)`
- `self` obligatoire en 1er param de chaque méthode (Python le passe automatiquement à l'appel — donc `n1.set_rating(4)` ne passe PAS explicitement `self`)
- `n1.summary()` AVEC les parenthèses pour APPELER la méthode. Sans, on récupère la référence à la méthode, pas son résultat.

#### Héritage : `class Child(Parent)`

Pour réutiliser tout ce qu'a le parent et ajouter du spécifique.

```python
class VideoNote(Note):                                   # (Note) entre parenthèses
    def __init__(self, title, theme, duration_sec, platform, tier="T2"):
        super().__init__(title, theme, tier)             # construit la partie Note
        self.duration_sec = duration_sec
        self.platform = platform

    def summary(self):                                   # override de la méthode
        base = super().summary()                         # réutilise la version Note
        minutes = self.duration_sec // 60
        seconds = self.duration_sec % 60
        return f"{base} ({self.platform} · {minutes}:{seconds:02d})"

v = VideoNote("Karpathy GPT", "ai-llms", 8500, "youtube")
v.set_rating(5)              # méthode héritée de Note, pas besoin de la redéfinir
print(v.summary())
# "Karpathy GPT [ai-llms · T2 · ⭐5] (youtube · 141:40)"
```

**À retenir** :
- `super().__init__(...)` construit la partie parente. Sans ça, les attributs du parent ne sont PAS initialisés.
- Override = redéfinir une méthode du parent dans l'enfant. Python prend la version la plus spécifique.
- `super().methode()` permet d'appeler la version du parent pour la réutiliser (DRY).
- N'override que ce qui change vraiment — `set_rating` reste hérité de `Note` sans rien retaper.

#### Lien direct avec PyTorch (cycle 4 teaser)
C'est le même pattern partout en deep learning :

```python
class MyModel(nn.Module):              # hérite de nn.Module
    def __init__(self):
        super().__init__()             # OBLIGATOIRE
        self.layer1 = nn.Linear(10, 5)

    def forward(self, x):              # override (méthode définie par nn.Module)
        return self.layer1(x)
```

Si tu reconnais `class`, `__init__`, `self`, `super().__init__()` et l'override de méthode,
tu as déjà 95% du vocabulaire OOP nécessaire pour cycle 4.

### Cycle 1 — Bloc 2 (NumPy)
_(à remplir : ndarray, broadcasting, axis, dot product, reshape, indexing avancé)_

### Cycle 1 — Bloc 3 (pandas)
_(à remplir : DataFrame, Series, filter/groupby/merge/join, read_csv, plot basique)_

### Cycle 1 — Bloc 4 (maths)
_(à remplir : vecteur, matrice, produit scalaire, dérivée, gradient au sens math vs numpy)_

---

**Dernière maj** : 2026-06-05 — bloc 1.4 OOP minimal rempli (class, __init__, self, héritage, super, override) + teaser PyTorch
