# pysparkexplainableai.github.io
Checking pyspark feasibility for XAI

## Explainable Artificial Intelligence 

As a beginner, trying out initial projects to get hands on experience. Initially, do read about Interpretable machine learning.
This link [https://github.com/jphall663/awesome-machine-learning-interpretability](url).


### Step 1 :  Try out 

My first tryout on XAI project to get hands-on-experience to have an idea about what are the capabilities of it in XAI_tryout_1_for_xgboost_using_pandas.ipynb

### Step 2 : Checking feasibility shap.TreeExplainer for RandomForestClassifier in pyspark ml libraries

I have tried out the feasibility in pyspark for pyspark_ml_random forest model in XAI_in_pyspark_ml_random_forest_with_shap_tree_explainability.ipynb

Tried out the shap.TreeExplainer(rfModel)  for   pyspark.ml.classification import RandomForestClassifier

SHAP didn't support pyspark ml models. Reason was 'check_additivity requires us to run predictions which is not supported with spark, ignoring.' It was hard to debug.

### Step 3 : Checking feasibility Dalex library for RandomForestClassifier in pyspark ml libraries

I have tried out the feasibility in pyspark for pyspark_ml_random forest model in XAI_dalex_DIY.ipynb

Here it is recommending to use dalex, because from library to library like keras, scikit-learn, xgboost might have different interfaces and different arguments. Therefore, in dalex if we specify common parameters like model, X,y , we will be able to observe the functionality in the resulting object. 

Pyspark didn't support Dalex , because of numpy limitation. 
 'residual_function' returns an Error when executed:
An error occurred while calling z:org.apache.spark.ml.python.MLSerDe.loads.
: net.razorvine.pickle.PickleException: expected zero arguments for construction of ClassDict (for numpy.dtype). This happens when an unsupported/unregistered class is being unpickled that requires construction arguments. Fix it by registering a custom IObjectConstructor for this class.

### In conclusion method recommended for pyspark ML libraries

Since the algorithm is same, train the same model (say Random forest model ) in keras/ scikit-learn for the same data and try to interpret it.
