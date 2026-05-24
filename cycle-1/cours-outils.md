# Cours sur les outils — Cycle 1

> **Principe** : chaque outil ou concept que j'utilise dans le cycle a sa fiche ici. Définition fraîche, sourcée officiellement. Si une info devient périmée, je remplace par un fetch récent.
>
> **Format de fiche** : 1) Définition officielle citée, 2) À quoi ça sert concrètement, 3) Quand l'utiliser dans le parcours, 4) Sources.

---

## 🐍 Python

**Définition officielle** (Python.org, 2026-05-25) :

> "Python est un langage de programmation interprété, orienté objet, de haut niveau, avec une sémantique dynamique."

**Caractéristiques clés** :

- Structures de données haut-niveau intégrées, typage dynamique
- Syntaxe lisible, focus sur la clarté du code
- Architecture modulaire (packages réutilisables)
- Libre, gratuit, multi-plateformes

**Pourquoi les devs l'utilisent** (toujours selon Python.org) :

1. Pas de compilation → cycle edit-test-debug rapide
2. Debug par exceptions et stack traces (pas de segfault opaque)
3. Productivité élevée rapportée par les programmeurs
4. Capacités d'introspection (le debugger lui-même est écrit en Python)

**Dans le cycle** : c'est mon langage principal pour tout le ML. Je l'apprends bloc 1.

**Source** : https://www.python.org/about/

---

## 📦 pip + venv

### pip

**Définition** : le package manager officiel de Python. `pip install nom-paquet` télécharger depuis [PyPI](https://pypi.org) et installe.

### venv

**Définition officielle** (docs.python.org, Python 3.14.5) :

> "Le module `venv` permet de créer des 'environnements virtuels' légers, chacun avec son propre ensemble indépendant de paquets Python installés. Un environnement virtuel est créé au-dessus d'une installation Python existante, appelée le Python 'de base' de l'environnement virtuel, et est par défaut isolé des paquets de l'environnement de base."

**Problème résolu** : sans venv, tous mes projets partagent les mêmes paquets installés. Conflits de versions garantis (projet A veut numpy 1.x, projet B veut numpy 2.x → impossible). Avec venv, **chaque projet a sa bulle**.

**Caractéristiques** :

- Isolé des autres venvs et du système
- Dans un dossier (convention : `.venv` ou `venv`)
- **Pas commité dans Git** (d'où l'entrée `.venv/` dans `.gitignore`)
- Jetable : je le supprime et le recrées sans souci
- Non-portable : à recréer à chaque nouvelle machine

**Commandes essentielles (Windows PowerShell)** :

```powershell
# Créer
python -m venv .venv

# Activer
.venv\Scripts\Activate.ps1

# Installer
pip install numpy pandas matplotlib

# Figer les versions
pip freeze > requirements.txt

# Désactiver
deactivate
```

**Dans mon cycle** : j'utilise `.venv` dans `ml-roadmap/`. À chaque nouveau projet Python, j'en crées un. C'est la convention pro.

**Sources** :

- venv : https://docs.python.org/3/library/venv.html
- pip : https://pip.pypa.io/en/stable/
- PyPI : https://pypi.org

---

## 📓 Jupyter + format .ipynb

### Jupyter

**Définition officielle** (docs.jupyter.org) :

> "Jupyter est un grand projet parapluie qui couvre de nombreuses offres logicielles et outils centrés sur la fourniture d'outils (et de standards) pour le calcul interactif avec des notebooks computationnels."

### Notebook (.ipynb)

**Définition officielle** :

> "Un notebook est un document partageable qui combine du code, des descriptions en langage naturel, des données, des visualisations riches (modèles 3D, graphiques, figures), et des contrôles interactifs."

**Format technique** (spec officielle nbformat) :

- C'est **un fichier JSON**. Ouvrir un `.ipynb` avec un éditeur de texte, pour voir la structure.
- Dictionnaire racine avec 4 clés : `metadata`, `nbformat`, `nbformat_minor`, `cells`
- Chaque cellule a un type (markdown, code, raw) + son contenu + ses outputs (pour les code cells)
- Version actuelle : v4, rétrocompatible

**À quoi ça sert concrètement** :

- Mélanger exécution + commentaires markdown + visualisations dans un seul document
- Voir le résultat immédiatement sous chaque cellule (REPL persistant)
- Partageable : un `.ipynb` sur GitHub s'affiche en HTML rendu directement

### JupyterLab vs Jupyter Notebook

- **Notebook (classique)** : interface simplifiée, légère
- **JupyterLab** : interface riche, multi-notebooks en onglets, console système intégrée

**Dans mon cycle** : je code presque tout en notebook. VSCode me fournit un éditeur de notebook intégré (alternative à Jupyter Lab/Notebook web). Les fichiers `01-python-bootstrap.ipynb` que je crée sont au format Jupyter.

**Sources** :

- Jupyter : https://docs.jupyter.org/en/latest/
- Format spec : https://nbformat.readthedocs.io/en/latest/format_description.html

---

## ☁️ Google Colab

**Définition officielle** (Google Colab FAQ) :

> "Google Colab est un service hébergé de Jupyter Notebook qui ne nécessite aucune installation et offre un accès gratuit à des ressources informatiques, dont des GPU et des TPU."

**Ce que ça offre (gratuit)** :

- Notebooks hébergés dans le cloud (stockés sur mon Google Drive)
- Accès **GPU/TPU** gratuit (limité, fluctuant)
- Zéro installation : tout dans le navigateur
- Partageable comme un Google Doc

**Limites du tier gratuit** :

- _"Les ressources Colab ne sont pas garanties ni illimitées, les limites d'usage peuvent fluctuer."_
- Runtime max **12h**, dépend de la dispo et de l'usage
- Timeout après inactivité
- Pas de mining crypto, hosting de fichiers, P2P, cracking de mots de passe
- Mémoire VM standard (priorisée pour la prog interactive)

**Utilisations dans mon cycle** :

- **Sem 1-3** : si setup Python local pose souci, bascule total Colab (Kaggle Learn et mes notebooks d'apprentissage)
- **Cycle 4** : quand j'aurais besoin de GPU pour PyTorch, Colab gratuit suffit
- **Cycle 5** : entraînement mini-LM = GPU obligatoire, Colab Free ou Pro

**Source** : https://research.google.com/colaboratory/faq.html

---

## 🏆 Kaggle + Kaggle Learn

### Kaggle (plateforme)

- **Acquis par Google en 2017**, fait partie de Google Cloud
- Plateforme de data science / ML, communauté mondiale active
- Gratuit pour la plupart des fonctionnalités

**5 piliers** :

1. **Competitions** : compétitions de modélisation, parfois avec prix
2. **Datasets** : grand catalogue de datasets publics téléchargeables
3. **Notebooks** : Jupyter notebooks cloud (concurrent direct de Colab)
4. **Models** : hub de modèles pré-entraînés (concurrent de Hugging Face)
5. **Learn** : cours gratuits courts avec exercices auto-évalués

### Kaggle Learn (utilisé en cycle 1)

- Modules courts (1-5h chacun), structurés
- Tutorial lisible + exercices interactifs (Check → corrige/passe)
- Badge à la fin de chaque cours (capital portfolio léger)

**Pour mon cycle 1** : je fais

- **Python** (https://www.kaggle.com/learn/python) — 7 modules, ~5h
- **Pandas** (https://www.kaggle.com/learn/pandas) — 6 modules, ~4h
- Plus tard cycle 2 : **Intro to ML** + **Intermediate ML**

**Sources** :

- Kaggle Docs : https://www.kaggle.com/docs
- Kaggle Learn : https://www.kaggle.com/learn

---

## 🔧 Outils annexes utilisés

### Git + GitHub

- **Git** : système de versionning local
- **GitHub** : hébergement de repos Git + collaboration + portfolio public
- `requirements.txt` : produit par `pip freeze`, liste figée des versions de paquets pour reproductibilité.

### VSCode + extension Python

-L'extension Python ajoute : autocomplete, debugger, linting, support `.ipynb` natif.

---

## 📋 Outils à venir dans les cycles suivants

Ces fiches seront ajoutées à mesure que je découvre des outils.

| Outil                         | Cycle d'introduction  | Fiche à fetcher quand ?      |
| ----------------------------- | --------------------- | ---------------------------- |
| **NumPy**                     | Cycle 1, bloc 2       | À l'arrivée bloc 2 (sem 2-3) |
| **pandas**                    | Cycle 1, bloc 3       | À l'arrivée bloc 3 (sem 4)   |
| **matplotlib / seaborn**      | Cycle 1, bloc 5       | À l'arrivée projet (sem 6)   |
| **scikit-learn**              | Cycle 2               | Démarrage cycle 2            |
| **Hands-On ML (Géron)**       | Cycle 2               | Démarrage cycle 2            |
| **PyTorch**                   | Cycle 4               | Démarrage cycle 4            |
| **Flask / FastAPI + Docker**  | Cycle 4 (MLOps light) | Démarrage cycle 4            |
| **Hugging Face Hub**          | Cycle 5-6             | Démarrage cycle 5            |
| **Vector DB (Chroma/Qdrant)** | Cycle 6               | Démarrage cycle 6            |
| **LoRA / Ollama / LM Studio** | Cycle 7               | Démarrage cycle 7            |

## 🔄 Règle de fraîcheur

Toute fiche de ce fichier est **datée** et **sourcée**. Si une info est utilisée et qu'elle date de plus de **3 mois**, je re-fetch et je remplace.
