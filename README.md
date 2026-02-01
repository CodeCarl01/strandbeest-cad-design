# 🦿 Strandbeest — Mécanisme de Jansen imprimé en 3D

**Conception, fabrication et tests d'un Strandbeest mécanique autonome — 0% électronique, 100% mécanique.**

Projet académique de 1ère année cycle ingénieur à Polytech Dijon. Un robot marcheur inspiré du mécanisme de Theo Jansen, entièrement conçu en CAO sous SolidWorks, fabriqué par impression 3D et propulsé par une corde élastique. Budget total : **15,82 €**.

![SolidWorks](https://img.shields.io/badge/SolidWorks-CAO-FF0000?style=flat-square&logo=dassaultsystemes&logoColor=white)
![3D Printing](https://img.shields.io/badge/Impression_3D-PLA_/_ABS-FF6F00?style=flat-square)
![Budget](https://img.shields.io/badge/Budget-15,82_€_/_100_€-4CAF50?style=flat-square)
![Status](https://img.shields.io/badge/Status-Fonctionnel-brightgreen?style=flat-square)

---

<!-- Ajouter ici une photo ou un GIF du Strandbeest en mouvement -->
<!-- ![Demo](docs/strandbeest-demo.gif) -->

## 📋 Sommaire

- [Le projet](#-le-projet)
- [Mécanisme de Jansen](#-mécanisme-de-jansen)
- [Conception CAO](#-conception-cao)
- [Fabrication](#-fabrication)
- [Résultats des tests](#-résultats-des-tests)
- [Bill of Materials](#-bill-of-materials)
- [Limites et améliorations](#-limites-et-améliorations)
- [Équipe](#-équipe)

---

## 🎯 Le projet

### Cahier des charges

| Critère | Exigence | Résultat |
|---|---|---|
| Parcourir 30 cm minimum | ✅ Requis | **65 cm** atteints (4,5 tours) |
| Temps sur 30 cm | ~10 secondes | ✅ Validé |
| Stabilité | Marche stable sur sol plat | ✅ Validé |
| Cycle complet sans blocage | ✅ Requis | ✅ Validé |
| Aucune électronique | ✅ Obligatoire | ✅ Respecté |
| Budget < 100 € | ✅ Obligatoire | **15,82 €** |

### Principe de fonctionnement

```
  Clé de remontage
       │
       ▼
┌─────────────────┐
│  Corde élastique │  ← Stockage d'énergie (25 J, rendement ~70%)
│    (sandow)      │
└────────┬────────┘
         │
         ▼
┌─────────────────┐
│  Système poulie  │  ← Transmission et renvoi d'angle
│  + engrenage     │
└────────┬────────┘
         │
         ▼
┌─────────────────┐
│  Axe principal   │  ← Rotation continue (couple max : 1 N.m)
│  (manivelle)     │
└────────┬────────┘
         │
         ▼
┌─────────────────┐
│  Pattes Jansen   │  ← 4 pattes articulées, mouvement de marche
│  (x4, déphasées) │
└─────────────────┘
```

---

## ⚙️ Mécanisme de Jansen

Le Strandbeest repose sur le mécanisme à barres inventé par Theo Jansen. Chaque patte est composée de tiges rigides reliées par des articulations qui convertissent un mouvement rotatif en une trajectoire de marche.

### Proportions de Jansen (originales → adaptées)

Les 13 longueurs de référence de Jansen ont été adaptées à notre échelle avec un coefficient multiplicateur de **55/38** (base `a` = 55 mm au lieu de 38 mm) :

```
Longueurs originales (mm)        Notre adaptation (mm)
a = 38.0                         a = 55.0 (base)
b = 41.5                         b = 60.1
c = 39.3                         c = 56.9
d = 40.1                         d = 58.0
e = 55.8                         e = 80.7
f = 39.4                         f = 57.0
g = 36.7                         g = 53.1
h = 65.7                         h = 95.1
i = 49.0                         i = 70.9
j = 50.0                         j = 72.4
k = 61.9                         k = 87.0 ⚠️ (modifié, voir ci-dessous)
l =  7.8                         l = 11.3
m = 15.0                         m = 21.7
```

### Modification du paramètre `k`

Lors de la simulation cinématique sous SolidWorks, le mécanisme se bloquait avec les cotes proportionnelles exactes. La valeur `k` (distance axe manivelle – point de pivot) a été augmentée de **57 mm à 87 mm** pour débloquer la cinématique.

**Impact sur la trajectoire :**

| Caractéristique | Modèle Jansen original | Notre adaptation |
|---|---|---|
| Forme de la trajectoire | En "D" (optimale) | Aplatie horizontalement |
| Foulée | Standard | Plus longue |
| Hauteur de levée du pied | Haute (franchit les obstacles) | Basse (rase le sol) |
| Stabilité sol plat | Excellente | Bonne |

Ce compromis a transformé le marcheur en un "glisseur" optimisé pour les surfaces lisses.

---

## 🖥️ Conception CAO

Toutes les pièces ont été modélisées sous **SolidWorks** :

- Modélisation paramétrique des 27 pièces distinctes
- Assemblage complet avec contraintes cinématiques
- Simulation du mécanisme de marche
- Export STL pour impression 3D

### Pièces principales (27 types, 130+ pièces au total)

| Catégorie | Pièces | Quantité |
|---|---|---|
| Pattes | Fémur C, Fémur F, Tibia, Métatarse inf./sup., Patelle | 64 |
| Liaisons | Bielle, Bielle terminale, Entretoise, Circlips | 94 |
| Châssis | Abdomen inf./sup., Pédicelle, Griffe inf./sup. | 12 |
| Transmission | Poulie, Roues (entrée/sortie/libre), Manivelle, Levier | 15 |
| Autres | Clé, Crochet | 2 |

---

## 🏭 Fabrication

### Matériaux et impression 3D

| Matériau | Quantité | Usage | Prix |
|---|---|---|---|
| PLA | 511,22 g | Structure principale, pattes, châssis | 11,75 € |
| ABS | 111,82 g | Pièces soumises à contrainte | 2,57 € |
| Corde élastique (sandow) | 1 m, Ø6 mm | Motorisation | 1,50 € |
| **Total** | | | **15,82 €** |

### Optimisations de coût

- Retrait de matière superflue sur chaque pièce pour réduire le temps et le coût d'impression
- Aucune vis, boulon ou élément de fixation externe — uniquement des liaisons imprimées (circlips, entretoises)
- Résultat : **84% sous le budget** maximum de 100 €

---

## 📊 Résultats des tests

### Distance parcourue vs. nombre de tours de clé

| Tours de clé | Distance (cm) |
|---|---|
| 1 | 10 |
| 2 | 30 |
| 3 | 40 |
| 4 | 53 |
| 4,5 | 65 |

### Performances mesurées

| Métrique | Valeur |
|---|---|
| Distance maximale | **65 cm** (4,5 tours) |
| Vitesse moyenne | **39,55 cm/s** (1,4 km/h) |
| Objectif 30 cm | ✅ Atteint dès 2 tours |
| Stabilité | ✅ Marche stable sur sol plat |
| Cycle complet | ✅ Sans blocage |

---

## ⚠️ Limites et améliorations

| Problème identifié | Cause | Amélioration proposée |
|---|---|---|
| Porte-poulies fragiles | PLA ne résiste pas au couple de la corde | Ajout de nervures (fait) / passage en ABS |
| Clé de remontage mal positionnée | Difficilement accessible | Remplacer par une clé de serrage externe |
| Usure du crochet et engrenage | Frottements PLA/PLA | Matériau plus résistant ou lubrification |
| Limite à 4,5 tours | Le crochet cède sous le couple | Renforcer le mécanisme de retenue |
| Dérapage sur sol lisse | Pieds trop fins | Ajouter des embouts en caoutchouc |

---

## 👥 Équipe

Projet réalisé dans le cadre du **Projet Fil Rouge — Ouverture** (1ère année cycle ingénieur, Polytech Dijon, 2025) :

| Membre | Rôle |
|---|---|
| Alexandre RAFFIN | Conception & fabrication |
| Raphaël MAUL | Conception & fabrication |
| Mamalinesso BAKAI | Conception & fabrication |
| Carl MENSAH | Conception & fabrication |

---

## 📁 Structure du repository

```
strandbeest-cad-design/
├── CAO/
│   ├── Pieces/             # Fichiers SolidWorks (.SLDPRT) de chaque pièce
│   ├── Assemblage/         # Assemblage complet (.SLDASM)
│   └── STL/                # Fichiers STL prêts pour impression 3D
├── docs/
│   ├── rapport-technique.pdf
│   └── screenshots/        # Captures CAO et photos du Strandbeest
├── tests/
│   └── resultats.md        # Données brutes des tests de performance
└── README.md
```

---

## 📜 Licence

Projet académique — Polytech Dijon, 2025.

---

*Inspiré par les créatures de plage de [Theo Jansen](https://www.strandbeest.com/) 🌊*