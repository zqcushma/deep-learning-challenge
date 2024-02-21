Alphabet Soup Deep Learning Model Analysis Report

Overview of the Analysis

The purpose of this analysis is to develop a deep learning model using neural networks to predict the success of organizations funded by Alphabet Soup. The model is designed to classify whether the funding provided by Alphabet Soup was used effectively based on various metadata features associated with the organizations.

Data Preprocessing
Target and Features

    Target Variable(s): IS_SUCCESSFUL (Binary classification indicating the success of funding usage).
    Feature Variable(s): APPLICATION_TYPE, AFFILIATION, CLASSIFICATION, USE_CASE, ORGANIZATION, STATUS, INCOME_AMT, SPECIAL_CONSIDERATIONS, ASK_AMT, and others.
    Removed Variables: EIN and NAME were removed as identification columns, and other non-informative columns.

Results
The final, best performing mode, ended up being a two layer model with 9 neurons per layer. However, through the utilization of Keras Tuner, we were able to test a model with up to 6 hidden layers, with each layer having 9, 9, 3, 1, 7, and 9 respectively. As for the activation function, the 'tanh' function was chosen for the hidden layers in each of the models tested, and sigmoid was used for the output layer. The performance statistics are listed below, with the baseline set by a model constructed with precise random guessing: two layers of 80 and 30 neurons respectively. 
    Baseline Model Performance: Loss: 0.5616, Accuracy: 0.7266.
    Two Layer Performance: Loss: 0.5544, Accuracy: 0.7233.
    Six Layer Performance: Loss: 0.5604, Accuracy: 0.7207.

At the time of writing, the best model unfortunately only hit 72.6% at best. The target of 75% is currently out of reach with the current constraints given to Keras Tuner (10 neurons per layer, 6 max layers). Speaking of, Keras Tuner was the backbone of my optimization attempt. I utilized this to determine the number of layers, and when fitting the model later, I utilized early stopping in order to avoid overfitting or underfitting the data. 


In summary, the deep learning model achieved a reasonable accuracy for the given classification problem. Further optimization is very likely to involve increasing the search range of Keras Tuner, with other potential optimizations available in the preparation stage, primarily in the cutoffs for the bins. 