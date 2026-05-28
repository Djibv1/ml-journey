# Maths progressif — guide juste-à-temps

> **Principe** : pour chaque cycle, les concepts math précis dont j'ai besoin + une ressource ciblée (1-2h max). Je ne fais le bloc math que si je sens le concept m'échapper. Si je le maîtrise déjà → skip.

---

## Cycle 1 — bloc 4 (sem 5) — Algèbre linéaire + calcul

**Concepts dont j'ai besoin** :

- ✅ Vecteur en 2D/3D (intuition géométrique)
- ✅ Matrice = transformation linéaire (rotation, étirement)
- ✅ Produit scalaire = projection / similarité entre 2 vecteurs
- ✅ Dérivée = pente locale d'une courbe
- ✅ Chain rule = dériver une composition de fonctions

**Ressources prévues (déjà dans le roadmap)** :

- 🎬 ⭐ 3Blue1Brown — _Essence of Linear Algebra_ (15 ép)
- 🎬 ⭐ 3Blue1Brown — _Essence of Calculus_ ép 1-3

**Trous potentiels à combler en parallèle (si je sens 3B1B m'échapper)** :

| Si je bloque sur...                               | Ressource Khan Academy fr                                                          |
| ------------------------------------------------- | ---------------------------------------------------------------------------------- |
| Notation vectorielle `(x, y, z)`, calcul de norme | [Vecteurs ](https://fr.khanacademy.org/math/be-tle-math/be-vecteurs)               |
| Coordonnées et repère orthonormé                  | [Géométrie repérée ](https://fr.khanacademy.org/math/be-2eme-math)                 |
| Dérivée d'une fonction simple (intuition)         | [Dérivée ](https://fr.khanacademy.org/math/be-1ere-math/x213a6fc6f6c9e122:derivee) |

**Antidote pratique** : après chaque vidéo 3B1B importante, ouvrir un notebook et **refaire en NumPy** ce que je viens de voir. Ex : 3B1B parle de produit scalaire → `np.dot([1,2,3], [4,5,6])` à la main puis vérifier. La pratique NumPy = exercice math caché.

---

## Cycle 2 — NN from scratch (Karpathy micrograd)

**Concepts dont j'ai besoin** :

- ✅ Chain rule (déjà acquis cycle 1)
- ✅ Dérivée partielle (extension multi-variable de la dérivée — juste intuition)
- ✅ Gradient = vecteur des dérivées partielles
- ✅ Fonction de coût (loss) : MSE = moyenne des carrés des erreurs
- ✅ Descente de gradient = "je suis la pente vers le bas"

**Ressource principale** : Karpathy zero-to-hero ép. 1 (micrograd). Il explique tout en codant, en partant de zéro. Pas de prérequis math formel, juste la chain rule.

**Trous potentiels** :

| Si je bloque sur...         | Ressource Khan Academy fr                                                                   |
| --------------------------- | ------------------------------------------------------------------------------------------- |
| Dérivée partielle (`∂f/∂x`) | [Calcul différentiel multivariable](https://fr.khanacademy.org/math/multivariable-calculus) |
| Notation gradient `∇f`      | Idem (chapitre dérivées partielles)                                                         |
| Somme de carrés / MSE       | [Statistiques](https://fr.khanacademy.org/math/be-1ere-math)                                |

**Antidote pratique** : Karpathy fait tout en code Python. Si je suis le code et que je peux le re-coder à la main, c'est suffisant. La compréhension émerge de la pratique, pas du formalisme.

---

## Cycle 3 — ML classique (scikit-learn + Géron)

**Concepts dont j'ai besoin** :

- ✅ Équation de droite : `y = ax + b` (pente + ordonnée à l'origine)
- ✅ Régression linéaire = "trouver la meilleure droite qui passe par mes points"
- ✅ Moyenne, variance, écart-type (basiques stats)
- ✅ Loi normale (intuition : courbe en cloche)
- ✅ Probabilité conditionnelle (intuition Bayes vu cycle 1)
- ✅ Logarithme (juste intuition : "ça compresse les grandes valeurs")

**Ressource principale** : _Hands-On ML_ (Géron) chap 1-4 + Andrew Ng ML Specialization YT.

**Trous potentiels** :

| Si je bloque sur...                     | Ressource Khan Academy fr                                                                   |
| --------------------------------------- | ------------------------------------------------------------------------------------------- |
| Équation de droite, pente               | [Fonctions affines ](https://fr.khanacademy.org/math/be-3eme-math)                          |
| Logarithme et exponentielle (intuition) | [Logarithme népérien ](https://fr.khanacademy.org/math/be-1ere-math)                        |
| Probabilités conditionnelles            | [Probabilités](https://fr.khanacademy.org/math/be-1ere-math/x213a6fc6f6c9e122:probabilites) |

**Antidote pratique** : scikit-learn cache le math. Je peux entraîner une régression linéaire **sans** comprendre la formule mathématique de la minimisation. Mais si je veux comprendre cycle 3 en profondeur, 1-2h sur l'équation de droite et le log m'aideront.

---

## Cycle 4 — PyTorch sérieux

**Concepts dont j'ai besoin** :

- Pas de NOUVEAU math majeur. Réinvestissement des cycles 1-3.
- Notation tensorielle (extension matrice → N-dim) — accessible via NumPy.

**Si trou identifié** : c'est probablement une lacune d'un cycle précédent. Je reviens combler là où c'est le trou racine.

---

## Cycle 5 — Transformers + attention

**Concepts dont j'ai besoin** :

- ✅ Softmax (intuition : transforme N scores en N probabilités qui somment à 1)
- ✅ Exponentielle (déjà vu cycle 3)
- ✅ Produit matriciel (déjà vu cycle 1+2)
- ✅ Notation `∑` (sigma) — lire ne pas écrire
- ✅ Dot-product attention (`Q · K^T / √d`) — beaucoup de notation, peu de math nouvelle

**Ressources principales** : paper _"Attention is all you need"_ (lu lentement, 3-4 sessions) + Karpathy "Building GPT".

**Trous lycée potentiels** :

| Si je bloque sur...                 | Ressource                                                  | Temps  |
| ----------------------------------- | ---------------------------------------------------------- | ------ |
| Notation Σ (somme)                  | Tuto rapide en ligne (5 min)                               | 5 min  |
| Softmax (intuition de la formule)   | Article "Softmax explained" ou vidéo 3B1B sur les NN ép. 4 | 30 min |
| Lire un paper math (notation dense) | "How to read a paper" — Andrej Karpathy guide rapide       | 30 min |

**Antidote pratique** : ne pas lire le paper _seul_ la 1re fois. Lire en parallèle d'une vidéo Karpathy qui implémente le truc en PyTorch. La formule devient claire quand on voit le code.

---

## Cycle 6 — LLMs en prod (RAG, eval)

**Concepts dont j'ai besoin** :

- Quasi zéro maths nouvelles
- Similarité cosinus = produit scalaire normalisé (déjà vu cycle 1+5)
- Métriques eval (précision, rappel, F1) = stats basiques (vu cycle 3)

**Aucun trou math attendu.** Si trou ici → c'est de l'ingénierie, pas du math.

---

## Cycle 7 — Fine-tuning + petits modèles open source

**Concepts dont j'ai besoin** :

- Idem cycle 6 : quasi zéro maths nouvelles
- LoRA = approximation matricielle de rang faible (intuition vue cycle 1 : valeurs propres et compression)

**Si je veux creuser** : décomposition SVD (singular value decomposition) — mais c'est optionnel. Khan Academy ne couvre pas bien, je verrai par la doc Hugging Face directement.

---

## Cycle 8 — Fork conscient

### (a) ML engineer / MLOps

- Stats inférentielles plus poussées (intervalles de confiance, tests d'hypothèse)
- Optimisation au-delà de la descente de gradient simple
- → Khan Academy fr Tle + plateforme dédiée (à choisir au démarrage)

### (b) Produit/distrib

- **Zéro nouveau math**. Marketing, distribution, UX.

**Le seul cycle où le math monte vraiment** = cycle 8a (ML eng). Si je choisis (b), je n'ai plus de prérequis math au-delà du cycle 5.

---

## Règle de fraîcheur

Ce fichier est **mis à jour à chaque démarrage de cycle** : je note ce que j'ai vraiment eu besoin de combler vs ce qui était surestimé. Vérité terrain > prévision.

**Dernier update** : 2026-05-25 — création initiale.
