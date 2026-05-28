# Lexique Python — Cycle 1

> **Principe** : tout ce que j'ai appris, défini en quelques lignes avec un exemple minimal. Organisé par module Kaggle Learn (ordre dans lequel je l'ai vu). Vivant : j'ajoute à chaque nouveau module / exo / découverte.
>
> **Format de chaque entrée** : Nom du concept · Définition en 1 ligne · Exemple Python en bloc code.

---

## Module 1 — Hello, Python

### Variable

Un nom auquel j'associe une valeur. En Python pas de `let`/`const`, juste l'affectation directe.

```python
nom = "Djilani"
age = 25
```

### Types primitifs

Les briques de base du langage.

- `str` (string, chaîne de caractères) : `"hello"`, `'a'`
- `int` (entier) : `42`, `-7`, `0`
- `float` (nombre à virgule) : `3.14`, `-2.5`
- `bool` (booléen) : `True` ou `False` (avec majuscule)
- `None` (absence de valeur, équivalent du `null`/`undefined` JS) : `None`

### `print()`

Affiche dans la console. Peut afficher plusieurs valeurs séparées par virgules.

```python
print("Bonjour", nom, age)  # Bonjour Djilani 25
```

### `type()`

Retourne la **classe** de la valeur (pas une string comme `typeof` en JS).

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

| Opérateur | Sens                                  | Exemple                 |
| --------- | ------------------------------------- | ----------------------- |
| `+`       | addition (ou concat de strings)       | `2 + 3` → `5`           |
| `-`       | soustraction                          | `5 - 2` → `3`           |
| `*`       | multiplication (ou répétition string) | `"ab" * 3` → `"ababab"` |
| `/`       | division (résultat float)             | `7 / 2` → `3.5`         |
| `//`      | division entière (int floor)          | `7 // 2` → `3`          |
| `%`       | modulo (reste)                        | `7 % 2` → `1`           |
| `**`      | puissance                             | `2 ** 3` → `8`          |

### Conversion de type (cast)

Forcer un type vers un autre.

```python
int("42")      # 42
str(42)        # "42"
float("3.14")  # 3.14
bool(0)        # False
bool(1)        # True
```

### f-string

Format string moderne, équivalent des template strings JS.

```python
nom = "Djilani"
print(f"Bonjour {nom}, tu as {age} ans")
```

---

## Module 2 — Functions and Getting Help

### Fonction (`def`)

Bloc de code réutilisable avec un nom. Peut prendre des paramètres et retourner une valeur.

```python
def square(n):
    return n ** 2

square(5)  # 25
```

### `return`

Renvoie une valeur depuis la fonction (vs `print` qui affiche). Une fonction sans `return` retourne implicitement `None`.

```python
def add(a, b):
    return a + b

result = add(2, 3)  # result = 5, utilisable plus loin
```

### `print` vs `return` (piège fondamental)

- `print` = affichage humain (effet de bord)
- `return` = valeur réutilisable dans le code
  Une fonction qui `print` mais ne `return` rien ne peut pas être chaînée ni testée.

### Argument

Valeur passée à une fonction au moment de l'appel.

```python
def greet(name):  # 'name' est un paramètre
    print(f"Salut {name}")

greet("Djilani")  # "Djilani" est l'argument
```

### Argument par défaut

Valeur par défaut si l'argument n'est pas fourni.

```python
def greet(name, lang="fr"):
    if lang == "fr":
        print(f"Salut {name}")
    else:
        print(f"Hi {name}")

greet("Djilani")           # "Salut Djilani"
greet("Djilani", "en")     # "Hi Djilani"
```

### Argument nommé (keyword argument)

Passer un argument en précisant son nom — clarté + ordre flexible.

```python
greet(lang="en", name="Djilani")
```

### Docstring

Documentation d'une fonction, écrite en triple guillemets juste après `def`. Lue par `help()`.

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

Affiche la documentation d'une fonction, classe ou module.

```python
help(square)   # affiche la docstring
help(print)    # doc du built-in print
```

### Composition de fonctions

Une fonction qui en appelle d'autres en interne.

```python
def kilos_to_grams(k):
    return k * 1000

def grams_to_milligrams(g):
    return g * 1000

def kilos_to_milligrams(k):
    grams = kilos_to_grams(k)        # appel la 1re
    return grams_to_milligrams(grams)  # passe le résultat à la 2e
```

---

## Module 3 — Booleans and Conditionals

### Booléen (`bool`)

Type avec 2 valeurs uniques : `True` et `False` (majuscule obligatoire).

### Opérateurs de comparaison

Retournent un booléen.
| Opérateur | Sens |
|---|---|
| `==` | égalité |
| `!=` | différence |
| `<` `>` | strict |
| `<=` `>=` | inclusif |

### Opérateurs logiques

Combinent des booléens. **Mots-clés Python**, pas `&&`/`\|\|` comme JS.

```python
True and False   # False
True or False    # True
not True         # False
```

### Short-circuit (court-circuit)

`and`/`or` évaluent paresseusement, retournent la première valeur déterminante.

```python
x = None
x or "default"   # "default" (utile pour valeurs par défaut)
x and "ok"       # None (rien à évaluer après)
```

### `if / elif / else`

Branchement conditionnel.

```python
if score < 30:
    return "T1"
elif score <= 70:
    return "T2"
else:
    return "T3"
```

**`elif`** = "else if" en un mot. Les branches sont **mutuellement exclusives** : l'évaluation s'arrête à la 1re vraie.

### Conditional expression (ternaire)

Expression conditionnelle sur une ligne. Ordre INVERSÉ par rapport au `cond ? x : y` JS.

```python
statut = "majeur" if age >= 18 else "mineur"
```

Format : `valeur_si_vrai if condition else valeur_si_faux`.

### Truthy / Falsy

Une valeur évaluée comme un booléen dans un contexte conditionnel.

**Falsy** (évalue à `False`) : `False`, `None`, `0`, `0.0`, `""`, `[]`, `{}`, `()`
**Truthy** (évalue à `True`) : tout le reste (y compris `"0"`, `[0]`, négatifs, etc.)

```python
if []:
    print("ne s'affichera pas")
if "0":
    print("s'affiche bien — string non vide = truthy")
```

### `bool()`

Convertit une valeur en booléen selon les règles truthy/falsy.

```python
bool(0)       # False
bool("hello") # True
bool([])      # False
```

---

## Module 4 — Lists

### Liste (`list`)

Collection ordonnée, **mutable** (modifiable), peut contenir des éléments hétérogènes.

```python
themes = ['ai-llms', 'dev-code', 'design-ui']
mix = [1, "a", True, None]
```

### Indexing

Accès à un élément par sa position. **Indices commencent à 0**.

```python
themes[0]   # 'ai-llms' (1er)
themes[2]   # 'design-ui' (3e)
themes[-1]  # 'design-ui' (dernier, indice négatif)
themes[-2]  # 'dev-code' (avant-dernier)
```

### Slicing

Extraire une **sous-liste** avec syntaxe `liste[début:fin:pas]`.

```python
themes[0:2]   # ['ai-llms', 'dev-code'] (de 0 inclus à 2 exclus)
themes[:2]    # idem (début par défaut = 0)
themes[1:]    # ['dev-code', 'design-ui'] (jusqu'à la fin)
themes[::-1]  # liste inversée
themes[::2]   # 1 élément sur 2
```

### Mutations (modifier la liste)

Les listes sont **mutables**. Ces méthodes modifient la liste en place et retournent généralement `None`.

| Méthode               | Effet                                      | Exemple                  |
| --------------------- | ------------------------------------------ | ------------------------ |
| `.append(x)`          | ajoute x à la fin                          | `lst.append(4)`          |
| `.insert(i, x)`       | insère x à l'index i                       | `lst.insert(0, "new")`   |
| `.pop()`              | retire et retourne le dernier              | `last = lst.pop()`       |
| `.pop(i)`             | retire et retourne l'élément à l'index i   | `x = lst.pop(2)`         |
| `.remove(x)`          | retire la 1re occurrence de x (par valeur) | `lst.remove("a")`        |
| `.sort()`             | trie en place (ascendant par défaut)       | `lst.sort()`             |
| `.sort(reverse=True)` | trie en place descendant                   | `lst.sort(reverse=True)` |
| `.reverse()`          | inverse l'ordre en place                   | `lst.reverse()`          |
| `.extend(autre)`      | ajoute tous les éléments de `autre`        | `lst.extend([4,5,6])`    |

### Built-ins utiles sur liste

| Fonction               | Effet                                                               |
| ---------------------- | ------------------------------------------------------------------- |
| `len(lst)`             | nombre d'éléments                                                   |
| `sorted(lst)`          | retourne une **nouvelle** liste triée (sans modifier l'originale)   |
| `sum(lst)`             | somme des éléments numériques                                       |
| `min(lst)`, `max(lst)` | minimum / maximum (ordre numérique ou lexicographique pour strings) |
| `x in lst`             | True si x est dans la liste                                         |

**Différence clé** : `lst.sort()` modifie en place et retourne `None`. `sorted(lst)` ne modifie pas et retourne une nouvelle liste.

### Concaténation

Combiner 2 listes avec `+` (crée une nouvelle liste).

```python
[1, 2] + [3, 4]   # [1, 2, 3, 4]
```

Vs `extend` qui modifie en place :

```python
a = [1, 2]
a.extend([3, 4])   # a == [1, 2, 3, 4] (modifié)
```

### Tuple

Collection ordonnée, **immutable** (non modifiable). Parenthèses au lieu de crochets.

```python
coords = (10, 20, 30)
coords[0]   # 10 (indexing OK)
coords[0] = 99   # ❌ TypeError, immutable
```

**Quand utiliser tuple vs list ?**

- **Tuple** : valeurs fixes qui vont ensemble (coordonnées, dates, retours multiples de fonction)
- **List** : collection qu'on va modifier au fil du temps

### Unpacking (déstructuration)

Affecter plusieurs variables à partir d'un tuple/liste.

```python
x, y, z = (10, 20, 30)
print(x)  # 10

# Marche aussi avec listes
a, b, c = [1, 2, 3]
```

### Swap (échange de variables)

Cas d'usage emblématique du tuple unpacking — pas besoin de variable temporaire.

```python
a, b = 5, 10
a, b = b, a   # swap en 1 ligne
# a == 10, b == 5
```

### Mutabilité partagée (piège ⚠️)

Quand j'assigne une liste à une autre variable, **les 2 pointent vers la même liste**. Modifier l'une modifie l'autre.

```python
a = [1, 2, 3]
b = a           # b est juste un autre nom pour la même liste
b.append(4)
print(a)        # [1, 2, 3, 4] ⚠️ modifié aussi
```

Pour copier vraiment : `b = a.copy()` ou `b = a[:]` (slice complet).

---

## Modules à venir (vide pour l'instant)

À chaque nouveau module Kaggle Learn ou nouveau cycle, j'ajoute ici une nouvelle section. Pas de copy-paste depuis Kaggle — j'écris la définition avec mes propres mots après avoir compris.

### Module 5 — Loops and List Comprehensions

_(vide, sera rempli quand je l'aurai vu)_

### Module 6 — Strings and Dictionaries

_(vide)_

### Module 7 — Working with External Libraries

_(vide)_

### Cycle 1 — Bloc 2 (NumPy)

_(à remplir au bloc 2 : ndarray, broadcasting, axis, dot product en numpy, etc.)_

### Cycle 1 — Bloc 3 (pandas)

_(à remplir au bloc 3)_

### Cycle 1 — Bloc 4 (maths)

_(à remplir au bloc 4 : vecteur, matrice, dérivée, gradient au sens math vs au sens numpy)_

---

## Règles de tenue

- **1 entrée par concept** : nom, définition 1-2 lignes, exemple Python minimal
- **Pas de copy-paste de Kaggle** — j'écris avec mes mots après avoir compris (sinon je relis sans retenir)
- **Ordre par module Kaggle**, mais à l'intérieur d'un module : ordre d'apparition logique (pas alphabétique)
- **Si je trouve une erreur** : je corrige immédiatement, je ne laisse pas un truc faux ici

**Dernière maj** : 2026-05-26 — création initiale (modules 1-4)
