## Pima diabetes classification
Le but de ce projet est de parvenir à mettre en place une classification binaire : 
- 0 (négatif)
- 1 (positif)
Dans le cas de diabètes chez la communauté Pima, on a alors dans notre projet 8 données d'entrée : 
- Pregnancies
- Glucose	
- Blood Pressure
- Skin Thickness
- Insulin	
- BMI	
- Diabetes Pedigree 
- Function
- Age
Et on a en sortie si la personne est malade ou pas. Le dataset est disponible sur Kaggle via ce [lien](https://www.kaggle.com/uciml/pima-indians-diabetes-database).

## Disposition du dépôt
* pima-notebook.ipynb : Contient la totalité du projet réalisé
* pima-diabetes.csv : Dataset disponible sur Kaggle
## Pré-requis logiciels 
Python 3.8 et +
Ainsi que les packages suivant : 
- Numpy
- Pandas
- Seaborn
- Scikit-learn
- Matplotlib
- Scipy
## Contenu du projet
1. Chargement des données
2. Analyse globale des données du dataset
3. Ensemble de visualisation des données et analyse de la corrélation entre les différentes variables
4. Application d'un ensemble d'algorithme de classification en analysant les performances en test sur les variables de bases: 
    - Random Forrest
    - Extremely randomized tree
    - Adaboost
    - KNN
    - SVM 
5. Normalisation des données d'entrées et on refait les tests avec les algorithmes
6. 

## Performances atteintes
### Avec les caractéristiques de base
|   Algorithme choisi    |   Précision en test (%)|  F1 score (%) |
|---      |:-:        |:-:        |
|  Random Forrest   |   76.62   |   76.42   |
|   Extremely randomized tree   |   76.62   |   76.17   |
|   Adaboost   |   73.59   |   72.8   |
|   KNN   |   75.32   |   74.69   |
|   SVM   |   75.76   |   74.62   |
### Avec normalisation des données 
Etant donné que les algorithmes basés sur des algorithmes d'arbres de décision sont insensibles à la normalisation des données j'ai retesté que les autres algorithmes : 
|   Algorithme choisi    |   Précision en test (%)|  F1 score (%) |
|---      |:-:        |:-:        |
|   KNN   |   75.76   |   74.98   |
|   SVM   |   74.89   |   74.08   |
### Avec restructuration des données
On a dans le dataset de départ une distribution comme suit : 
- 0 : 500
- 1 : 268
#### Down-sampling de la classe majoritaire
Avec ce down-sampling on a alors diminué du nombre d'échantillons de la classe majoritaire qu'on a pour restructurer le dataset comme suit : 
- 0 : 370
- 1 : 268

On retrouve les résultats suivant :

|   Algorithme choisi    |   Précision en test (%)|  F1 score (%) |
|---      |:-:        |:-:        |
|   KNN   |   69.27   |   68.83   |
|   SVM   |   64.58   |   64.24   |
|   Random Forrest   |   73.44   |   73.51   |

Comme on le pensait, le down-sampling aurait un effet néfaste vu le nombre déjà assez petit d'échantillons dans le dataset de base. 
#### Up-sampling de la classe minoritaire
Avec ce up-sampling on a alors augmenté en dupliquant aléatoirement des échantillons faisant partie de la classe minoritaire pour restructurer le dataset comme suit : 
- 0 : 500
- 1 : 400

On retrouve les résultats suivant :

|   Algorithme choisi    |   Précision en test (%)|  F1 score (%) |
|---      |:-:        |:-:        |
|   KNN   |   76.3   |   76.39   |
|   SVM   |   74.44   |   74.31   |
|   Random Forrest   |   83.7   |   83.74   |

On a alors avec cet up-sampling grandement amélioré les résultats du Random Forrest.