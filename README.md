# Les mathématiques au service du cœur : du médicament au stent… et à l'IA

**Bilel Charfi**, enseignant-chercheur en mathématiques appliquées, ESPRIT (Tunis) · bilel.charfi@esprit.tn
Fête de la Science 2026 (Youth for Science Foundation), intervention en lycée.

> *« Derrière chaque battement réparé, il y a une équation. »*

Ce dépôt accompagne la présentation donnée en lycée. Tu y trouveras la présentation, un rapport détaillé, les vraies données utilisées et tout le code Python qui recalcule chaque nombre et chaque figure.

---

## Ce que tu trouveras ici

| Fichier | Contenu |
|---|---|
| [`presentation.pptx`](presentation.pptx) | La présentation PowerPoint avec ses animations vidéo (48 diapositives) — à télécharger |
| [`presentation.pdf`](presentation.pdf) | La même présentation en PDF, lisible directement dans le navigateur (images fixes à la place des vidéos) |
| [`rapport_technique.pdf`](rapport_technique.pdf) | Le rapport détaillé : démonstrations, calculs, figures, références |
| [`maths_au_service_du_coeur.ipynb`](maths_au_service_du_coeur.ipynb) | Le notebook Python qui refait tous les calculs et toutes les figures |
| [`data/theoph.csv`](data/) | Les vraies mesures de concentration d'un médicament (théophylline), avec leur source |

## L'histoire en trois questions

1. **Le médicament.** Un comprimé : combien de temps agit-il ? On part de vraies mesures dans le sang, on observe une régularité (la concentration est divisée par 2 environ toutes les 7 h), on la traduit en équation (`C′ = −k C`), on la résout (`C(t) = C₀ e^(−kt)`) et on démontre que c'est la seule solution.
2. **L'artère.** Pourquoi une artère un peu plus étroite laisse-t-elle passer beaucoup moins de sang ? Parce que le débit dépend du rayon **à la puissance 4** (loi de Poiseuille) : rayon divisé par 2, débit divisé par 16.
3. **Le stent.** Comment un petit grillage passe-t-il de 0,8 mm à 3,0 mm de diamètre sans casser ? En ouvrant des losanges, comme un accordéon. La trigonométrie prédit qu'il raccourcit en s'ouvrant.

Et ensuite ? Le chapitre « ouverture » montre ce qui se passe quand on élargit le regard : un modèle à deux phases (absorption + élimination), la variabilité entre 12 patients, et une comparaison avec l'apprentissage automatique (*machine learning*).

## Résultats clés (vraies données)

- Patient 11 : `k ≈ 0,095 h⁻¹`, demi-vie ≈ **7,3 h** (la notice du médicament indique 6,1 à 12,8 h chez l'adulte).
- 12 patients : demi-vie de 6,7 h à 14,4 h (moyenne 8,4 h) : chaque patient est différent.
- Prédire la courbe d'un patient **jamais vu**, à partir de sa dose et de son poids (validation croisée) :

| Méthode | Erreur moyenne |
|---|---|
| Modèle mathématique à deux phases (paramètres de population) | **1,41 mg/L** |
| Forêt aléatoire (*machine learning*) | 1,54 mg/L |
| Réseau de neurones, 2 × 16 neurones (*deep learning*) | 1,70 mg/L |
| k plus proches voisins (*machine learning*) | 2,60 mg/L |

Avec seulement 12 patients, le modèle qui contient une connaissance scientifique fait mieux que les algorithmes « boîte noire ». Avec beaucoup plus de données, ou en combinant les deux approches, l'apprentissage automatique devient très puissant : c'est tout l'enjeu de la recherche actuelle.

## Refaire les calculs soi-même

**Sans rien installer :** ouvre le notebook directement sur GitHub (les figures s'affichent), ou dans Google Colab : [![Ouvrir dans Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/CharfiBilel/maths-au-service-du-coeur/blob/main/maths_au_service_du_coeur.ipynb). Dans Colab, téléverse aussi `data/theoph.csv` dans un dossier `data/`.

**Sur ton ordinateur** (Python 3, gratuit : https://www.python.org) :

```bash
pip install -r requirements.txt
jupyter notebook maths_au_service_du_coeur.ipynb
```

Puis *Run All*. Les figures s'affichent dans le notebook et sont aussi enregistrées dans `figures/`. Le notebook vérifie ses propres calculs (`assert`).

## Ce qui est réel, ce qui est simplifié

- **Réel :** les mesures de théophylline (`data/theoph.csv`), la plage de demi-vie de la notice, la fréquence cardiaque au repos (60 à 100 battements par minute), les diamètres du stent (0,8 → 3,0 mm, d'après un brevet).
- **Simplifié pour les calculs :** départ à 100 mg/L, `k = 0,1 h⁻¹` et seuil de 25 mg/L dans les questions 2 et 3 ; un stent fait de 6 losanges de côté 1 mm ; une artère vue comme un tube rigide.
- **Images :** les illustrations du cœur, du sang et du stent ont été générées par IA (Google Gemini). Les graphiques et les animations mathématiques sont calculés par le code.

## Références principales

1. Boeckmann A. J., Sheiner L. B., Beal S. L. (1994). *NONMEM Users Guide, Part V*. NONMEM Project Group, UCSF. Jeu de données « Theoph » du logiciel R.
2. Notice de la théophylline, section « Clinical Pharmacology » (demi-vie chez l'adulte).
3. Poiseuille J. L. M. (1840-1841). Recherches expérimentales sur le mouvement des liquides dans les tubes de très petits diamètres. *Comptes rendus de l'Académie des sciences*.
4. Brevet US 9 510 960, « Deformable lumen support devices and methods of use » ; FDA (2021), Svelte DES, dossier P210014.
5. Raissi M., Perdikaris P., Karniadakis G. E. (2019). Physics-informed neural networks. *Journal of Computational Physics*, 378, 686-707.

La liste complète est dans le rapport.

## Licence

Textes, figures et présentation : [CC BY 4.0](https://creativecommons.org/licenses/by/4.0/deed.fr) (réutilisation libre en citant l'auteur). Code : licence MIT (voir `LICENSE`). Les données `theoph.csv` restent sous les conditions de leur source.

**Pour citer :** Charfi B. (2026). *Les mathématiques au service du cœur : du médicament au stent… et à l'IA*. ESPRIT, Fête de la Science 2026. https://github.com/CharfiBilel/maths-au-service-du-coeur
