# Énoncé du projet Python : Simulation d'une usine de fabrication de jouets (avec explications internes)

---

## Introduction

Dans le cadre de votre cours de programmation Python, vous devez développer un projet simulant une usine de fabrication de jouets (par exemple, des voitures miniatures). L'objectif est de créer un programme qui modélise une chaîne de production où les jouets passent par différentes étapes (stations) avant d'être finalisés. Vous devrez gérer des goulets d'étranglement, des erreurs de production (produits défectueux), et des pannes imprévues des stations, tout en produisant un rapport final pour analyser les performances.

---

## Objectifs

1. Structurer un programme complexe en utilisant la **programmation orientée objet (POO)**, avec des classes bien définies et des responsabilités claires.
2. Implémenter et utiliser des structures de données comme les **files d'attente (queue)** et les **piles (stack)**, en comprenant leur fonctionnement interne (FIFO vs LIFO).
3. Exploiter des outils de la bibliothèque standard Python, notamment **`itertools`** (pour générer des séquences), **`logging`** (pour tracer les événements), et les fonctions fonctionnelles (**`map`**, **`filter`**, **`reduce`**).
4. Utiliser des **expressions régulières (regex)** pour valider et analyser des données, en comprenant comment les motifs fonctionnent.
5. Implémenter une **récursivité** simple pour gérer des processus répétitifs, en comprenant la pile d'appels.
6. Simuler des événements aléatoires (par exemple, pannes, défauts) et comprendre comment les intégrer dans une simulation.

---

## Contexte du projet

Vous devez simuler une usine qui fabrique des jouets. Chaque jouet passe par les étapes suivantes, dans l'ordre :
1. **Assemblage** : Les pièces du jouet sont assemblées.
2. **Peinture** : Le jouet est peint.
3. **Contrôle qualité** : Le jouet est inspecté pour détecter d'éventuels défauts.
4. **Emballage** : Les jouets validés sont emballés et prêts à être expédiés.

Chaque étape est représentée par une **station** qui peut traiter un produit à la fois. Les stations ont des temps de traitement variables, ce qui peut créer des goulets d'étranglement (par exemple, si la peinture est plus lente que l'assemblage, une file d'attente se forme). De plus, certaines stations peuvent tomber en panne de manière aléatoire, bloquant temporairement le traitement. Enfin, certains jouets peuvent être détectés comme défectueux au contrôle qualité et devront être retraités.

---

## Structure générale du programme

Votre programme sera structuré autour de plusieurs classes principales, chacune avec des responsabilités spécifiques. Voici un aperçu des classes et de leur rôle, avec des explications détaillées sur leur fonctionnement interne dans les sections suivantes :
- **Classe `Produit`** : Représente un jouet fabriqué, avec un identifiant unique, un statut, un temps total de production, et un suivi des étapes effectuées.
- **Classe `Station`** : Représente une étape de production, avec une file d'attente pour gérer les produits en attente, un temps de traitement variable, et la possibilité de tomber en panne.
- **Classe `PileDefauts`** : Gère une pile de produits défectueux, avec un mécanisme pour les renvoyer à une étape précédente.
- **Classe `Usine`** : Orchestre toute la simulation, en gérant les stations, la pile des défauts, et les produits finis, et produit un rapport final.
