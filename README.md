## Pima diabetes classification
The goal of this project is to achieve a binary classification: 
- 0 (negative)
- 1 (positive)
In the case of diabetes in the Pima community, we have in our project 8 input data: 
- Pregnancies
- Glucose	
- Blood Pressure
- Skin Thickness
- Insulin	
- BMI	
- Diabetes Pedigree 
- Function
- Age
And we have in output if the person is sick or not. The dataset is available on Kaggle via this [link](https://www.kaggle.com/uciml/pima-indians-diabetes-database).

## Repository layout
* pima-notebook.ipynb : Contains the whole project
* pima-diabetes.csv : Dataset available on Kaggle
## Software requirements 
Python 3.8 and more
As well as the following packages : 
- Numpy
- Pandas
- Seaborn
- Scikit-learn
- Matplotlib
- Scipy
## Content of the project
1. Data loading
2. Global analysis of the dataset
3. Data visualization set and analysis of the correlation between the different variables
4. Application of a set of classification algorithms by analyzing the test performance on the basic variables: 
    - Random Forest
    - Extremely randomized tree
    - Adaboost
    - LGBM
    - Naive Bayes
    - KNN
    - SVM 
5. Normalization of the input data and retesting with the algorithms
6. We proceed to a resampling of our data to allow a rebalancing of the classes and we test once again the algorithms and we analyze the impact of this resampling (down-sampling and up-sampling)

## Performance achieved
### With the basic characteristics
|   Algorithms    |   Accuracy (%)|  F1 score (%) |
|---      |:-:        |:-:        |
|  Random Forest   |   76.62   |   74.18   |
|   Extremely randomized tree   |   76.62   |   73.7   |
|   Adaboost   |   73.59   |   69.79   |
|   LGBM   |   74.89   |   72.43   |
|   Naive Bayes   |   75.76   |   73.53   |
|   KNN   |   75.32   |   71.96   |
|   SVM   |   75.76   |   71.53   |
### With data normalization 
Since the algorithms based on decision tree algorithms are insensitive to data normalization, I tested the other algorithms : 

|   Algorithms    |   Accuracy (%)|  F1 score (%) |
|---      |:-:        |:-:        |
|   KNN   |   75.76   |   72.17   |
|   SVM   |   74.89   |   71.17   |
### With data restructuring
We have in the starting dataset a distribution as follows: 
- 0 : 500
- 1 : 268
#### Down-sampling of the majority class
With this down-sampling we have then decreased the number of samples of the majority class that we have to restructure the dataset as follows: 
- 0 : 370
- 1 : 268

We find the following results:

|   Algorithms    |   Accuracy (%)|  F1 score (%) |
|---      |:-:        |:-:        |
|   KNN   |   69.27   |   67.48   |
|   SVM   |   64.58   |   62.8    |
|   Random Forest   |   73.44   |   72.73   |

As expected, down-sampling would have a detrimental effect given the already small number of samples in the base dataset. 
#### Up-sampling of the minority class
With this up-sampling we then increased by randomly duplicating samples belonging to the minority class to restructure the dataset as follows: 
- 0 : 500
- 1 : 500

We find the following results:

|   Algorithms    |   Accuracy (%)|  F1 score (%) |
|---      |:-:        |:-:        |
|   KNN   |   85.67   |   85.66   |
|   SVM   |   76      |   75.93   |
|   Random Forest   |   88    |   88   |
|   Naive Bayes   |   75.67    |   75.55   |
|   Extremely randomized tree   |   89.33    |   89.26   |

We can see the beneficial effect of this up-sampling, we see excellent results with the Random Forest and the Extremely randomized tree