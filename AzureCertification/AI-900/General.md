# AI 900 topics

- An AI system's performance can degrade over time, so a robust monitoring and model tracking process needs to be established to reactively and proactively measure the model's performance and retrain it, as necessary, to modernize it.
- **Feature engineering** is applied first to generate additional features, and then **feature selection** is done to eliminate irrelevant, redundant, or highly correlated features.
- In Azure Machine Learning, scaling and normalization techniques are applied to facilitate feature engineering. 
- Automated machine learning, also referred to as automated ML or AutoML, is the process of automating the time consuming, iterative tasks of machine learning model development. It allows data scientists, analysts, and developers to build ML models with high scale, efficiency, and productivity all while sustaining model quality.
- During training, Azure Machine Learning creates a number of pipelines in parallel that try different algorithms and parameters for you. The service iterates through
ML algorithms paired with feature selections, where each iteration produces a model with a training score. The higher the score, the better the model is considered to "fit" your data. It will stop once it hits the exit criteria defined in the experiment.
- Accuracy is simply the proportion of correctly classified instances. It is usually the first metric you look at when evaluating a classifier. However, when the test data is unbalanced (where most of the instances belong to one of the classes), or you are more interested in the performance on either one of the classes, accuracy doesn't really capture the effectiveness of a classifier.
- Form Recognizer applies advanced machine learning to accurately extract text, key/ value pairs, and tables from documents.
- Real-time endpoints must be deployed to an Azure Kubernetes Service cluster and for Dev/Test - use Azure Container Service.
- Azure Machine Learning Designer enables you to include custom Python functions and R code.
- F1 score also known as balanced F-score or F-measure is used to evaluate a classification model.
- aucROC or area under the curve (AUC) is used to evaluate a classification model.
- MAE, RMSE and R2 are metris for regression.
- Azure Machine Learning designer lets you visually connect **datasets** and **modules** on an interactive canvas to create machine learning models.
- **Confidence** represents the level of certainty or probability assigned to a specific classification prediction made by a machine learning model. It indicates the model's belief in the accuracy of its prediction. 
- Object Deteciton has no further types to choose from. Classification has 2 classification types to choose - MultiClass & MultiLabel.
- Custom Vision service can be used only on graphic files, no video.
- Computer Vision can analyze an image and generate a human-readable phrase that describes its contents. 
- The Text Analytics API is a cloud-based service that provides advanced natural language processing over raw text, and includes four main functions: sentiment analysis, key phrase extraction, named entity recognition, and language detection.