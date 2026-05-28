# Changelog

Format : [keep-a-changelog](https://keepachangelog.com/). Entrée par semaine min, narratif (pas juste liste de fichiers).

---

## 2026-05-25

### Added

- Setup environnement Python local (Python 3.12, venv, jupyter, numpy, pandas, matplotlib)
- Repo `ml-journey` initialisé public sur GitHub + README + requirements.txt + .gitignore
- Notebook `01-python-bootstrap.ipynb` créé avec premiers exos Python (variables, types, fonctions, conditionals, composition de fonctions)
- Fichier `cours-outils.md` ajouté : fiches sourcées (Python, pip+venv, Jupyter+.ipynb, Colab, Kaggle)

### Learned

- **Python syntaxe de base** : `def`, `print`, `type()`, opérateurs, f-strings — confortable car proche de TS sur les concepts
- **List comprehensions** Python = équivalent fonctionnel des `.map().filter()` JS en plus concis : `[x*2 for x in arr if x > 0]`
- **`type(x)`** retourne une classe Python (ex `<class 'bool'>`), pas un string comme `typeof x` en JS
- **Convention nommage variables** : pas d'accents (`âge` est légal Python mais mauvaise pratique — interop, encodages, outils tiers)
- **`return` vs `print`** : `print` = affichage humain (effet de bord), `return` = valeur réutilisable (la fonction "rend" un résultat). Différence fondamentale qui m'a échappé sur un exo
- **`if/elif/else`** > plusieurs `if` séparés : branches mutuellement exclusives, évaluation s'arrête à la 1re vraie, plus lisible
- **Composition de fonctions** : une fonction qui en appelle une autre. Pattern : `def f(x): y = g(x); return h(y)`. Pas "passer les fonctions en paramètre" (ça c'est higher-order, plus avancé)
- **Format `.ipynb`** : c'est du JSON. Dictionnaire racine avec `cells`, `metadata`, `nbformat`. Ouvrir un notebook avec un éditeur de texte pour vérifier
- **`venv`** : pas commité dans Git, jetable, recréé à chaque machine. Convention nom : `.venv` à la racine du projet
- **`pip freeze > requirements.txt`** : fige les versions pour reproductibilité

### Done (exercices et notebooks)

- Exo 1 — Variables/types : ✅
- Exo A — `seconds_to_minutes` : ✅
- Exo B — `square` + docstring + `help()` : ✅
- Exo C — Composition de fonctions : ✅ 2e tentative correcte

### Blocked / à reprendre cycle 2 démarrage

- Refaire exo `tier` avec `return` + `elif`
- Recoder FizzBuzz

## 2026-05-25

### Done

- Kaggle Learn Python — module 3 (Booleans and Conditionals) ✅
- Exos refaits à la main dans `01-python-bootstrap.ipynb` : `tier` propre (return + elif). Reste à faire FizzBuzz, `mention(score)`, ternaire imbriqué

### Learned

- **Conditional expressions (ternaire)** : `valeur if condition else autre` — équivalent du `cond ? x : y` JS mais ordre inversé (valeur d'abord, pas condition)
- **Booléens** : `bool([])` = False, `bool("")` = False, `bool(0)` = False — truthy/falsy similaire à JS mais sans surprises (pas de `[] == false` weird)
- **`and` / `or` short-circuit** : `x or y` retourne `x` si truthy, sinon `y` (utile pour valeurs par défaut)

## 2026-05-26

### Done

- Kaggle Learn Python — modules 3 + 4 ✅
- Lexique `cycle-1/lexique.md` créé : 4 premiers modules définis, structure vivante
- Exos refaits : tier+return+elif, mention(score), ternaire imbriqué, indexing/slicing, mutations, swap, combinaison
- Guide `cycle-1/maths-progressif.md` créé : concepts math par cycle + ressources Khan Academy fr en fallback

### Learned

- **Ternaire Python** : `valeur if condition else autre` — ordre INVERSÉ par rapport au JS (`cond ? x : y`)
- **`sort()` vs `sorted()`** : `.sort()` modifie en place et retourne None, `sorted()` crée une nouvelle liste
- **`pop(i)` vs `remove(x)`** : `pop` retire par index, `remove` par valeur (1re occurrence)
- **Tuple unpacking** : `a, b = b, a` swap en une ligne sans variable temporaire
- **Mutabilité partagée** : `b = a` ne copie pas, les 2 pointent vers la même liste. Pour copier vraiment : `b = a.copy()` ou `b = a[:]`
- **Slicing avancé** : `a[::-1]` inverse, `a[::2]` 1 sur 2, `a[-3:]` les 3 derniers

### Blocked / à corriger

- `print` vs `return` : habitude à prendre
