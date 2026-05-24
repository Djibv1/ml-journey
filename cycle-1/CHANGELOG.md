# Changelog

Format : [keep-a-changelog](https://keepachangelog.com/). Entrée par semaine min, narratif (pas juste liste de fichiers).

---

## [Sem 1] 2026-05-22 → 2026-05-28

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
