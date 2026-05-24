---
type: project
status: active
started: 2026-05-22
deadline: 2026-07-10
tags: [ai/ml, dev-perso/learning]
---

# Cycle 1 — Python + numpy/pandas + maths minimaliste

**Sortie** : Python fluide, manipulation de données, intuition algèbre linéaire & dérivée, 1 projet livré

**Légende ressources** : 📄 article/doc · 🎬 vidéo · 📚 livre · 💻 repo · 🎓 cours · ⭐ indispensable · 🌐 inspiration

**📘 Cours sur les outils** : à chaque fois que je rencontre un outil/concept (Python, venv, Jupyter, Colab, Kaggle, NumPy, etc.), une fiche sourcée est créée dans [cours-outils.md](cours-outils.md).

---

## Critères de complétion (cocher pour clore le cycle)

- [ ] Script Python ~50 lignes manipulant des données, **écrit sans Google ni LLM**
- [ ] Exercices NumPy Keith Galli refaits **en aveugle**
- [ ] JSON/CSV chargé en pandas + 5 transformations classiques (filter, groupby, merge, join, plot) **sans Google**
- [ ] Capable d'expliquer à voix haute : vecteur, matrice, produit scalaire, dérivée, gradient
- [ ] Projet final livré : repo GitHub public + README + 5 visualisations minimum

---

## 1. Python fondamentaux

### 1.1 Syntaxe & contrôle

- [x] Variables, types primitifs (`str`, `int`, `float`, `bool`, `None`)
- [ ] Opérateurs (arithmétiques, comparaison, logiques, `in`, `is`)
- [ ] Indentation = bloc (pas de `{}` — piège classique venant de JS)
- [x] `if / elif / else`
- [ ] `for ... in` (pas de C-style `for i=0;i<n;i++`) + `while`
- [ ] `try / except / finally`
- [ ] f-strings : `f"hello {name}"`

### 1.2 Structures de données

- [ ] Listes : create, append, slice (`a[1:5]`, `a[::-1]`), `len`, `sorted`
- [ ] Tuples (immutables, unpacking : `a, b = (1, 2)`)
- [ ] Dicts : create, update, iterate (`for k, v in d.items()`)
- [ ] Sets (unicité, opérations ensemblistes)
- [ ] **List comprehensions** : `[x*2 for x in arr if x > 0]` — incontournable Python
- [ ] Dict/set comprehensions

### 1.3 Fonctions & modules

- [ ] `def`, arguments positionnels/nommés, `*args`/`**kwargs`
- [ ] Type hints (`def f(x: int) -> str:` — optionnel mais lisible)
- [ ] `import`, `from ... import`, modules locaux
- [x] Différence `print()` vs `return`
- [ ] Lambdas pour usage simple

### 1.4 OOP minimaliste

- [ ] `class`, `__init__`, méthodes
- [ ] `self` (pas `this`)
- [ ] Héritage simple (pour comprendre PyTorch plus tard : `class MyModel(nn.Module)`)

### 1.5 Différences vs TypeScript/Node

- [ ] Mutabilité par défaut (pas de `const`)
- [ ] Pas de types statiques au runtime (mais type hints + `mypy` possible)
- [ ] Indentation significative
- [ ] `None` vs `null`/`undefined`
- [ ] `pip` vs `npm` (et venv vs node_modules)
- [ ] Pas de fonction `arrow` à la JS — `lambda` est limité
- [ ] **Capture** : `30-Concepts/python-vs-js-key-diffs.md` (note atomique)

### 🧪 Questions de vérif bloc 1 (à voix haute, sans Google)

À répondre **avant** de cocher le bloc complet. Si j'hésite > 5 sec, je reviens. C'est plus rigoureux que les checkboxes.

- [ ] Quelle est la différence entre `return` et `print` dans une fonction ? Donner un cas concret où l'un casse et l'autre marche.
- [ ] Donner 2 exemples de composition de fonctions (une fonction qui en appelle une autre).
- [ ] Quand utiliser `elif` plutôt que plusieurs `if` séparés ?
- [ ] C'est quoi une list comprehension ? Écrire en pensée `[x*2 for x in [1,2,3] if x > 1]` et donner le résultat.
- [ ] Différence entre `list` et `tuple` en Python ?
- [ ] Pourquoi un nom de variable avec un accent (`âge`) est une mauvaise pratique même si Python l'accepte ?

**Ressources bloc 1** :

- 🎓 ⭐ **[Kaggle Learn — Python](https://www.kaggle.com/learn/python)**
- 📄 ⭐ [Tuto officiel Python §3-9](https://docs.python.org/3/tutorial/introduction.html)
- 📄 ⭐ [learnxinyminutes — Python](https://learnxinyminutes.com/docs/python/)
- 🎬 freeCodeCamp Python crash course (backup si tuto officiel trop sec)
- 🌐 Nodes roadmap.sh/python couverts : `basic-syntax`, `operators`, `variables-and-data-types`, `conditionals`, `loops`, `functions`, `exceptions`, `lists`, `tuples`, `dictionaries`, `sets`, `list-comprehensions`, `modules`, `classes`, `inheritance`, `methods`, `type-casting`, `working-with-strings`

**Skippé cycle 1** (à voir plus tard) : decorators (cycle 3), context managers (cycle 2), async/threading/GIL (cycle 4 si besoin), regex (cycle 4), static typing strict + pydantic (cycle 2-3), frameworks web (cycle 4 pour API), package managers avancés (poetry/uv — `pip` suffit cycle 1).

---

## 2. NumPy

### 2.1 ndarray

- [ ] Créer un array : `np.array([1,2,3])`, `np.zeros`, `np.ones`, `np.arange`, `np.linspace`
- [ ] `.shape`, `.dtype`, `.ndim`
- [ ] Conversion list → array et inverse

### 2.2 Indexing & slicing

- [ ] Indexing 1D (comme listes)
- [ ] Indexing 2D : `a[i, j]` et `a[i][j]` (les deux marchent, le premier est canonique)
- [ ] Slicing par axe : `a[:, 0]` (colonne 0), `a[1, :]` (ligne 1)
- [ ] Boolean indexing : `a[a > 0]`
- [ ] Fancy indexing : `a[[0, 2, 4]]`

### 2.3 Broadcasting

- [ ] Règle de broadcasting (shapes compatibles axe par axe)
- [ ] `a + 1`, `a + b` (shapes différentes)
- [ ] Section commentée dans le notebook : 3 exemples + 1 contre-exemple qui plante

### 2.4 Opérations vectorisées

- [ ] Arithmétique element-wise
- [ ] Reductions par axe : `np.sum(a, axis=0)`, `mean`, `max`, `min`, `std`
- [ ] Pourquoi vectoriser au lieu de loops Python (perf 10-100x)

### 2.5 Linear algebra basics

- [ ] Dot product : `a @ b` (préférer à `np.dot`)
- [ ] Transpose : `a.T`
- [ ] `np.linalg.norm` (longueur de vecteur)
- [ ] Déterminant 2×2 à la main puis `np.linalg.det`
- [ ] Inverse matrice : `np.linalg.inv`

**Ressources bloc 2** :

- 🎬 ⭐ [freeCodeCamp NumPy (Keith Galli)](https://youtu.be/QUT1VHiLmmI) + refaire les 2 challenges en aveugle
- 📄 [NumPy quickstart officiel](https://numpy.org/doc/stable/user/quickstart.html)
- 📄 [Broadcasting officiel](https://numpy.org/doc/stable/user/basics.broadcasting.html)
- 🌐 Nodes roadmap.sh/machine-learning couverts : `numpy`, `scalars-vectors-tensors`, `matrix--matrix-operations`

---

## 3. Pandas

### 3.1 DataFrame & Series

- [ ] `pd.DataFrame.from_records`, `pd.read_csv`, `pd.read_json`
- [ ] Series vs DataFrame
- [ ] `.head()`, `.info()`, `.describe()`
- [ ] Sélection colonnes : `df['col']`, `df[['c1', 'c2']]`
- [ ] Sélection lignes : `df.loc[index]`, `df.iloc[0]`

### 3.2 Manipulation

- [ ] Filtering : `df[df['tier'] == 'T2']`
- [ ] `groupby` + agg (`sum`, `mean`, `count`)
- [ ] `merge`, `join`, `concat`
- [ ] `apply` (lambda sur colonne)
- [ ] `value_counts` (tableau de fréquences)

### 3.3 Time series & viz intégrée

- [ ] Parser dates : `pd.to_datetime`
- [ ] Indexer par date, `resample` (regroupement par jour/mois)
- [ ] `.plot()` intégré (matplotlib backend)

### 3.4 Mini-projet de calibration ⭐

**But** : manipuler un dataset Kaggle public avant d'attaquer le gros projet sem 6-7. Révèle les trous tôt, calibre le rythme.

- [ ] Choisir un dataset Kaggle simple : **Titanic** (https://www.kaggle.com/c/titanic) ou **Wine Quality** (https://archive.ics.uci.edu/dataset/186/wine+quality)
- [ ] Notebook séparé `cycle-1-week-4-mini-project.ipynb`
- [ ] Charger en pandas, faire 5 transformations (filter, groupby, sort, merge si possible, plot)
- [ ] Tirer 3 insights écrits en commentaire markdown du notebook
- [ ] Push sur GitHub avec mini-README

**Pas l'objectif** : prédire/modéliser. Juste manipuler et explorer.

**Ressources bloc 3** :

- 🎓 ⭐ **[Kaggle Learn — Pandas](https://www.kaggle.com/learn/pandas)** (6 modules) À enchaîner avec Kaggle Learn Python du bloc 1 — synergie maximale, même plateforme.
- 📄 ⭐ [10 minutes to pandas (officiel)](https://pandas.pydata.org/docs/user_guide/10min.html)
- 🎬 Keith Galli pandas playlist
- 📄 [Cheat sheet pandas](https://pandas.pydata.org/Pandas_Cheat_Sheet.pdf)
- 🌐 Nodes roadmap.sh/machine-learning couverts : `pandas`, `csv`, `json`, `data-loading`

---

## 4. Maths minimalistes

### 4.1 Algèbre linéaire intuitive

- [ ] 🎬 ⭐ **3Blue1Brown — Essence of Linear Algebra** (15 ép courts)
      https://www.youtube.com/playlist?list=PLZHQObOWTQDPD3MizzM2xVFitgF8hE_ab
- [ ] Concepts à retenir : vecteur, base, matrice = transformation linéaire, déterminant = facteur d'aire, produit scalaire = projection, valeurs propres = directions invariantes

### 4.2 Calcul différentiel intuitif

- [ ] 🎬 ⭐ **3Blue1Brown — Essence of Calculus, ép. 1-3 seulement**
      https://www.youtube.com/playlist?list=PLZHQObOWTQDMsr9K-rj53DwVRMYO3t5Yr
- [ ] Concepts à retenir : dérivée = pente locale, chain rule (composition), gradient = dérivée multi-dim

### 4.3 Probas basiques + Bayes

- [ ] Proba élémentaire, distribution, espérance, variance (lecture rapide)
- [ ] 🎬 3Blue1Brown — Bayes Theorem (vidéo unique)
- [ ] Pourquoi Bayes matters en ML : eval avec incertitude, calibration

### 4.4 Formalisme texte (en bonus)

- [ ] 📚 [Mathematics for ML, Deisenroth et al.](https://mml-book.github.io/) — **chapitre 2 sections 2.1-2.4 seulement** (vecteurs, espaces vectoriels, dépendance linéaire, base/rang)
- [ ] Skip les démonstrations, retenir intuitions et notations

### 4.5 Notes atomiques `30-Concepts/` ⭐

Créer 5 notes courtes (~250 mots) :

- [ ] `30-Concepts/vecteur.md`
- [ ] `30-Concepts/matrice.md`
- [ ] `30-Concepts/produit-scalaire.md`
- [ ] `30-Concepts/derivee.md`
- [ ] `30-Concepts/gradient.md`

**Garde-fou** : si MML book trop sec → couper, 3Blue1Brown suffit.

**Ressources bloc 4** :

- 🎬 ⭐ 3Blue1Brown chaîne entière (canonique maths intuitives)
- 📚 Mathematics for ML — PDF gratuit
- 🌐 Nodes roadmap.sh/machine-learning couverts : `linear-algebra`, `calculus`, `derivatives-partial-derivatives`, `chain-rule-of-derivation`, `gradient-jacobian-hessian`, `probability`, `basics-of-probability`, `bayes-theorem`

---

## 5. Projet final — "Que dit mon vault de moi ?" (démarrage **sem 3**)

**Concept** : analyse exploratoire de mon vault Obsidian, en notebook + repo GitHub public.

**Démarrage progressif** (anti-scope creep) — au lieu de tout sem 6-7 :

- **Sem 3** (après NumPy) : `project/00-scan-minimal.ipynb` — juste un `os.walk` qui compte les `.md` du vault. Aucune dépendance sur pandas encore. J'ai mon premier squelette.
- **Sem 4** (pendant pandas) : `project/01-load-frontmatter.ipynb` — parser les frontmatters, construire un premier DataFrame. J'utilise pandas en pratique sur mes vraies données.
- **Sem 5** (pendant maths) : 1 viz minimal (distribution par thème). Met le pied dans matplotlib avant le crunch.
- **Sem 6-7** : polissage, 4 viz restantes, README, push public. Plus du scope creep, du fignolage.

### 5.1 Pipeline

- [ ] Scanner récursivement `c:\Users\djila\Desktop\SecondBrain` (exclure `50-Journal/`, `10-Moi/`, `_archive/`)
- [ ] Parser frontmatter YAML de chaque note Markdown
- [ ] Construire DataFrame pandas : `path`, `theme`, `tier`, `tags`, `date_captured`, `length_words`
- [ ] Charger en complément `00-Inbox/_telegram-queue.archive.jsonl` pour stats d'ingestion

### 5.2 Analyses obligatoires (5 viz minimum, matplotlib)

- [ ] Distribution notes par thème (bar chart)
- [ ] Cadence d'ingestion mensuelle (time series)
- [ ] Distribution T1/T2/T3 pour les notes veille
- [ ] Top 20 tags les plus utilisés
- [ ] Co-occurrence de tags (matrice simplifiée)

### 5.3 Bonus si temps

- [ ] Longueur moyenne notes par thème (boxplot)
- [ ] Évolution mensuelle par thème (heatmap)
- [ ] Notes orphelines (sans backlinks)

### 5.4 Livrable public

- [ ] Repo GitHub `vault-analytics` (ou autre nom)
- [ ] README sérieux : ce que j'ai fait, ce que j'ai appris, **les limites** (cruciales — capital crédibilité)
- [ ] Screenshots des 5 viz dans le README
- [ ] Instructions pour cloner + relancer

**Critères de coupure** :

- 5 viz minimum, même si moches → coupe à la deadline
- Pas de Next.js / dashboard interactif → notebook only
- Si parser frontmatter > 2h galère → fallback `python-frontmatter` lib ou regex grossier

---

## 6. Challenge final — "sans Google ni LLM" (fin sem 7) ⭐

Validation explicite du critère de complétion #1 (les autres se valident dans le projet).

**Setup** :

- 1 heure chronométrée, environnement isolé
- Pas d'internet (ou seulement la doc officielle Python/numpy/pandas en local)
- Pas d'autocomplétion IA, pas de ChatGPT/Claude, pas de Stack Overflow
- Juste un éditeur + Python

**Sujet** (à choisir en fin sem 6) :

- Option A : écrire un script `analyze.py` de ~40-60 lignes qui prend un dossier de fichiers `.md` en argument et sort le top 10 des tags les plus utilisés en frontmatter. Doit gérer cas d'erreur basiques.
- Option B : écrire un script qui charge un CSV en pandas, calcule 3 stats descriptives, affiche un bar chart matplotlib. Le tout sans regarder.

**Verdict** :

- Si je fais le script qui tourne sans aide → critère "sans Google" coché, cycle 1 complet
- Si je bloque sur la syntaxe → flag dans la rétro "ce qui doit être revu en cycle 2 démarrage"
- Pas d'échec, juste un diagnostic honnête

---

## Calendrier suggéré (à ajuster en sem 1 selon cadence réelle)

| Semaine | Bloc                                                                                               |
| ------- | -------------------------------------------------------------------------------------------------- |
| 1       | 0 + 1.1 + 1.2 + Kaggle Learn Python (démarrer)                                                     |
| 2       | 1.3 + 1.4 + 1.5 + finir Kaggle Learn Python + questions de vérif bloc 1                            |
| 3       | 2 (NumPy complet) + **projet/00-scan-minimal.ipynb**                                               |
| 4       | 3.1-3.3 + Kaggle Learn Pandas + 3.4 mini-projet calibration + **projet/01-load-frontmatter.ipynb** |
| 5       | 4 (maths) + **1 viz minimal sur le projet**                                                        |
| 6       | 5.1 + 5.2 (polissage projet, 4 viz restantes)                                                      |
| 7       | 5.3 + 5.4 + section 6 challenge final + rétro                                                      |

---

## Rituel d'exécution

- **Bilan hebdo** : 10 min vendredi soir → cocher ce qui est fait, noter les blocages
- **Capture notes** : tout concept revu 2+ fois → note atomique dans `30-Concepts/` (cf. CLAUDE.md)
- **Rétro fin de cycle** : 1h en fin de cycle → écrire `40-Projets/ml-roadmap/cycle-1/retro.md`

---

## Cycle 2 (préview) — NN from scratch

Cycle 2 (après inversion F6 dans le spec parent) = **NN from scratch** avec Karpathy zero-to-hero ép. 1 (micrograd). Réinvestit immédiatement les maths du cycle 1 (chain rule, gradient).

Ressources déjà identifiées :

- 🎬 ⭐ [Karpathy — "The spelled-out intro to neural networks and backpropagation: building micrograd"](https://www.youtube.com/watch?v=VMj-3S1tku0)
- 💻 [Repo micrograd officiel](https://github.com/karpathy/micrograd)
- 🎓 CS50 AI semaine 5 (Neural Networks) en complément
- Projet candidat : mini-NN scorant la qualité d'une note du vault, **sans framework** (numpy pur)

ML classique (scikit-learn + _Hands-On ML_ Géron) = **cycle 3** maintenant.

À confirmer en rétro cycle 1.
