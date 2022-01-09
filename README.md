# Neural_Network_Charity_Analysis
Module 19: Neural Networks and Deep Learning Models

## Overview of the analysis

With our knowledge of machine learning and neural networks, we use the features in the provided dataset to create a binary classifier that is capable of predicting whether applicants will be successful if funded by Alphabet Soup.

The dataset CSV contains more than 34,000 organizations that have received funding from Alphabet Soup over the years. Within this dataset are a number of columns that capture metadata about each organization, such as the following:

- EIN and NAME—Identification columns
- APPLICATION_TYPE—Alphabet Soup application type
- AFFILIATION—Affiliated sector of industry
- CLASSIFICATION—Government organization classification
- USE_CASE—Use case for funding
- ORGANIZATION—Organization type
- STATUS—Active status
- INCOME_AMT—Income classification
- SPECIAL_CONSIDERATIONS—Special consideration for application
- ASK_AMT—Funding amount requested
- IS_SUCCESSFUL—Was the money used effectively

The three steps for this assignment were to:
1) Deliverable 1: Preprocessing Data for a Neural Network Model
2) Deliverable 2: Compile, Train, and Evaluate the Model
3) Deliverable 3: Optimize the Model

These are the results gathered from the analysis.

## Results
### Data Preprocessing
We encoded all categorical variables which were chosen to be features of the models and standardised all numerical features.

#### What variable(s) are considered the target(s) for your model?

IS_SUCCESSFUL—Was the money used effectively. Since this is the aim of the machine learning program predictions.

#### What variable(s) are considered to be the features for your model?

- APPLICATION_TYPE
- AFFILIATION
- CLASSIFICATION
- USE_CASE
- ORGANIZATION
- STATUS
- INCOME_AMT
- SPECIAL_CONSIDERATIONS
- ASK_AMT

#### What variable(s) are neither targets nor features, and should be removed from the input data?

EIN (Employer Identification) and NAME as these values would be noise to the model and would skew the reslts.

### Compiling, Training, and Evaluating the Model
#### How many neurons, layers, and activation functions did you select for your neural network model, and why?

<img width="517" alt="original" src="https://user-images.githubusercontent.com/87828174/148668669-750477ce-dc42-4566-93ee-6e0eb13c8dfe.png">

- Input & 1st Hidden Layer: 80 Neurons and to speed up the training process we use RELU Activation Function
- 2nd Hidden Layer: 30 Neurons and to speed up the training process we use RELU Activation Function
- Output Layer: Since it is a binary classification we use 1 neuron and Sigmoid Activation Function

#### Were you able to achieve the target model performance?

<img width="574" alt="original-" src="https://user-images.githubusercontent.com/87828174/148668857-63585630-3525-4f08-9f5f-8fa1de33f376.png">

Since our accuracy was 72.618 %, **no** we **did not** meet out target performance of 75 %.

#### What steps did you take to try and increase model performance?
##### Attempt 1: Drop Noisy Variables

In the first attempt we dropped all noisy variables/ features which we believed would only confuse the model. The feature we dropped was SPECIAL_CONSIDERATIONS which due to encoding had been separated to SPECIAL_CONSIDERATIONS_N & SPECIAL_CONSIDERATIONS_Y. Both of these columns were dropped.

<img width="515" alt="1" src="https://user-images.githubusercontent.com/87828174/148668975-62b7cd29-050f-45b9-9b2a-e6469339424a.png">

<img width="564" alt="1-" src="https://user-images.githubusercontent.com/87828174/148668977-08984f55-ebae-443c-81cd-0fc8ce1d8789.png">

This did not improve the performance and resulted in a model accuracy of 72.502 %.

##### Attempt 2: Drop Noisy Variables, Additional neurons are added to hidden layers and Additional hidden layers are added

In the second attempt we dropped the same columns as before but this time increased the number of neurons and number of layers as follows.

- Hidden Layer 1 / Input Layer: Number of neurons was increased to 100
- Hidden Layer 2: Number of neurons was increased to 50
- A third hidden layer was added with 25 neurons
- The output layer remained the same as its a binary classification

<img width="515" alt="2" src="https://user-images.githubusercontent.com/87828174/148669047-7790a3f5-982a-432e-ade4-ac5cea036272.png">

<img width="576" alt="2-" src="https://user-images.githubusercontent.com/87828174/148669050-ac3572f7-7bd4-4c74-a351-c3b4118b200b.png">

This improved the accuracy from before to 72.537 % but was not able to match the original Deliverable 1/2 or target accuracy.

##### Attempt 3: Drop Noisy Variables, Additional neurons are added to hidden layers, Additional hidden layers are added and Activation Functions are changed

In the third attempt we dropped the same columns and had the same number of neurons and layers as attempt 2 but this time changed the activation functions. The first, second and third hidden layer were changed to Tanh activation functions instead of RELU. The output layer activation function remained Sigmoid due to it being a binary classification. 

<img width="516" alt="3" src="https://user-images.githubusercontent.com/87828174/148669171-03c69305-941d-4fd2-8cbe-5c23a87a18fd.png">

<img width="557" alt="3-" src="https://user-images.githubusercontent.com/87828174/148669175-8c53f3ae-6949-4938-b409-3ccba4a55658.png">

Although this improved the accuracy from the previous two attempts to 72.571 %, it did not meet the requirements of the optimization.

## Summary
The model did not meet the target of 75 % accuracy despite three attempts at optimization. Further optimizations could include changing the number of iterations the model runs for, increasing the number of layers or neurons although that would run the risk of overfitting to this dataset. Increasing the number of data points or meaningful features could also improve performance accuracy. 

The other option similar to a deep learning model is the Random Forest Classifier which could be used to combine multiple decision trees to reach a classified binary output and compare its performance to our machine learning model. The RF model would be more accurate and robust due to its large number of estimators. It also has a faster performance than a deep learning model.
