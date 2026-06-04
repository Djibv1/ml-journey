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

## 2026-06-05

### Done

- Kaggle Learn Python — modules 5, 6, 7 enchaînés ✅ (loops + comprehensions, strings + dicts, external libraries)
- Bloc 1.4 OOP minimal couvert en session dédiée ✅ (`class`, `__init__`, `self`, héritage, `super()`, override de méthode)
- **Test de sortie bloc Python validé** : `word_counter_veille` en aveugle sur `lexique.md` → top 10 mots avec stopwords, lowercase, ponctuation strippée. 1er jet bricolé (chaîne de `!=`), refacto propre derrière (`set` de stopwords, `return` au lieu de `print`).
- **Bloc Python officiellement clos** (Kaggle 1-7 + OOP minimal + test de sortie)
- Lexique mis à jour : sections 5/6/7 + complément lecture fichier + bloc 1.4 OOP avec teaser PyTorch (`nn.Module`)

### Learned

- **Set de stopwords > liste** : lookup `in` est O(1) sur set, O(n) sur liste. Réflexe à prendre dès qu'on teste l'appartenance souvent.
- **`.strip(chars)`** retire les caractères passés en début ET fin (pas au milieu). Pratique pour virer ponctuation collée par `.split()`.
- **Classe vs instance** : 1 classe = N instances, avec attributs propres. Comme `dict` est un type, mais on peut avoir 100 dicts distincts.
- **`self` explicite** vs `this` implicite en JS — 1er param obligatoire de chaque méthode, mais Python le passe automatiquement à l'appel.
- **Pas de `new`** en Python : on appelle la classe comme une fonction (`Note(...)`).
- **`super().__init__(...)`** dans une classe enfant = construit la partie parente. Sans ça, les attributs hérités ne sont pas initialisés. **Le pattern PyTorch** : `class MyModel(nn.Module): def __init__(self): super().__init__()`.
- **Override** = redéfinir une méthode du parent dans l'enfant. Python prend la version la plus spécifique. On n'override que ce qui change.
- **`super().methode()`** = appeler la version du parent pour la réutiliser (DRY). Évite de tout retaper quand on enrichit juste.
- **`n.summary` vs `n.summary()`** : sans parenthèses = référence à la méthode (`<bound method...>`), avec parenthèses = on l'APPELLE et on récupère le retour.
- **`is not None`** plutôt que `if self.rating:` pour tester l'absence — sinon `rating = 0` (falsy) serait confondu avec "pas de rating".

### Blocked / à corriger

- Aucun blocage majeur côté bloc Python. Reste à pratiquer numpy/pandas pour ancrer les patterns en data.

### Méta — vitesse réelle vs prévue

- Prévu pour bloc Python : 2-3 semaines (sem 1-3 du cycle)
- Réel : 2 semaines
- Temps gagné réinjecté dans bloc 2 NumPy / maths (plus de marge pour ancrer broadcasting/axis).
