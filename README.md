# 🧩 Projet Algo 2024 — Détection d’inclusions de polygones

[![Language](https://img.shields.io/badge/langage-Python-blue.svg)](https://www.python.org/)
[![Status](https://img.shields.io/badge/statut-Terminé-success.svg)]()
[![Université](https://img.shields.io/badge/École-ENSIMAG-orange.svg)]()
[![Date](https://img.shields.io/badge/Mars-2024-lightgrey.svg)]()

**Auteurs** : Antonio Mattar & Jayson Marest  
**Objectif** : Implémenter et comparer différents algorithmes permettant de détecter les inclusions entre polygones — déterminer si un polygone est contenu dans un autre.

---

## 📘 Introduction

Ce projet vise à concevoir plusieurs **algorithmes géométriques** capables d’identifier les relations d’inclusion entre polygones.  
Pour chaque polygone d’un ensemble, on cherche à déterminer s’il est inclus dans un autre, et à identifier son **plus petit parent**.

👉 Ce problème est typique en **géométrie computationnelle**, **cartographie**, **traitement d’images** et **analyse spatiale**.

---

## ⚙️ Structure du projet

```bash
📂 projet-algo-2024/
├── ray_casting.py              # Détection de point dans polygone (ray casting)
├── aire_polygone.py            # Calcul d’aire par la formule des lacets (Gauss)
├── gen_test.py                 # Génération automatique de polygones de test
├── naif.py                     # Algorithmes naïfs (brut et avec quadrant)
├── tri_aire.py                 # Algorithmes de tri par aire
├── algorithmes_non_concluants.py # Tentatives abandonnées (triangulation, grille, etc.)
├── mesures/                    # Résultats de performance
└── projet_algo_2024-final.pdf  # Rapport complet du projet
```

---

## 🧠 Algorithmes implémentés

### 🌀 1. Algorithmes naïfs
- **Naïf basique** : teste toutes les inclusions possibles entre polygones.  
  🔹 Complexité : `O(m²n)`  
- **Naïf à test de quadrant** : ajoute une vérification préalable du *quadrant* (plus petit carré englobant).

### ⚖️ 2. Algorithmes de tri par aire
- **Tri par aire décroissante** : ignore les polygones plus petits, réduction du nombre de comparaisons.  
- **Tri par aire fusion** : fusionne les polygones de même aire.  
- **Tri par aire croissante et arbre** : construit un arbre hiérarchique des inclusions.  
- **Tri par aire décroissante avec quadrant** : combinaison optimisée (meilleur résultat).

### 🚫 3. Algorithmes non concluants
- **Triangulation (Delaunay / monotone)** : complexe à implémenter malgré une complexité théorique intéressante.  
- **Sans détection de point** : approche expérimentale basée sur le comptage d’intersections.  
- **Quadrillage spatial** : prometteur mais difficile à synchroniser entre polygones.

---

## 🧩 Dépendances

Aucune dépendance externe obligatoire.  
Pour les expérimentations supplémentaires :

```bash
pip install numpy scipy matplotlib
```

Le module `geo` (fourni par l’énoncé ENSIMAG) est utilisé pour :
- le calcul des aires,
- la gestion des quadrants,
- la vérification d’inclusion de points.

---

## 🧪 Génération de tests

Le script [`gen_test.py`](./gen_test.py) permet de générer automatiquement plusieurs types de polygones :

- 🔷 Carrés simples ou imbriqués  
- 🔺 Polygones réguliers (3 à 5 côtés)  
- 🧬 Fractales de carrés  
- 🌀 Polygones aléatoires imbriqués  

Les jeux de tests servent à comparer les performances et à valider empiriquement la complexité des algorithmes.

---

## 📊 Résultats et performances

| Algorithme                              | Test 0 | Test 1 | Test 2 | Observation |
|-----------------------------------------|:-------:|:-------:|:-------:|--------------|
| Naïf basique                            | 5040 ms | ❌ | ❌ | Trop lent |
| Naïf avec quadrant                      | 3040 ms | 33 ms | ❌ | Bonne amélioration |
| Tri par aire décroissante               | 4040 ms | ❌ | ❌ | Légère optimisation |
| Tri par aire fusion                     | 4040 ms | ❌ | ❌ | Peu de gain |
| Tri par aire croissante et arbre        | 3040 ms | ❌ | ❌ | Structure hiérarchique utile |
| **Tri par aire décroissante + quadrant**| **3040 ms** | **17 ms** | **7041 ms** | ✅ Meilleur compromis |

---

## 🧾 Utilisation

Exécution des algorithmes :

```bash
python3 naif.py
python3 tri_aire.py
```

Les résultats et mesures sont enregistrés dans le dossier [`mesures/`](./mesures).

---

## 📚 Références

1. [🎥 Ray-casting algorithm – YouTube](https://www.youtube.com/watch?v=w4Dosp2U74Y)  
2. [📄 Cours de triangulation — G-SCOP Grenoble-INP](https://pagesperso.g-scop.grenoble-inp.fr/~lazarusf/Enseignement/triangulation.pdf)  
3. [🧮 RosettaCode – Ray casting algorithm](https://rosettacode.org/wiki/Ray-casting_algorithm)  
4. [📚 Wikipedia – Polygon triangulation](https://en.wikipedia.org/wiki/Polygon_triangulation)

---

## 🧩 Conclusion

Ce projet a permis d’explorer plusieurs stratégies algorithmiques de détection d’inclusions polygonales.  
Les résultats montrent que **la combinaison du tri par aire décroissante et des quadrants** est la plus efficace, tout en restant simple à implémenter.

> 💡 *“La géométrie computationnelle, c’est l’art d’optimiser le bon sens.”*

---

### 🏫 ENSIMAG — Projet Algorithmique 2024  
Made with ❤️ by **Antonio Mattar** & **Jayson Marest**
