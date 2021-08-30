# Neural_Network_Charity_Analysis
Module 19 Challenge for UT Bootcamp - Neural Networks


## Overview of Loan Prediction Risk Analysis
In the fictional scenario for this assignment, we are presented with a dataset of applicants for grants from a philantropic foundation called Alphabet Soup. The task was to create a model that predicts which organizations are worth supporting with grants and which are too high risk and should not receive a grant. In this assignment, we design and train a neural network as our model.

## Results
Based on the analysis, we answer these six questions posed in the homework.
- Data Preprocessing
  - *What variable(s) are considered the target(s) for your model?*  The target (response variable) is the column labeled "IS_SUCCESSFUL." A value of 1 indicates the investment in the organization yielded good results, and a value of 0 indicates the investment did not yield good results.
  - *What variable(s) are considered to be the features for your model?*  The features are the amount asked for by the organization, the type of application completed, the affiliation of the organization, its classification using a code provided by Alphabet Soup, the Use Case, the income amount, and any special considerations.
  - *What variable(s) are neither targets nor features for your model?*  The variables that were not considered (and removed from the inital dataset) are the organization's name and an identification number issued by Alphabet Soup.

- Compiling, Training, and Evaluating the Model
  - *How many neurons, layers, and activation functions did you select for your neural network model, and why?*  The original model (as shown in the code for Deliverable 2) had 10 neurons in layer 1 and 5 neurons in layer 2. The activation function for both hidden layers was the Rectified Linear Unit (ReLU) function. The activation function for the final output layer was the sigmoid function since we want to predict a binary outcome. 
  - *Were you able to achieve the target model performance?*  The target model performance was an accuracy of 75%. The optimization code (see the file entitled *AlphabetSoupCharity_Optimization.ipynb*) was only able to achieve an accuary level of 73%, which did not meet the target model performance. 
  - *What steps did you take to try and increase model performance?*  As seen in the Optimization code, the code was changed from the initial model (Deliverable 2) by adjusting three types of things:
    - The cutoff levels for making the "other" categories were lowered before performing the one-hot encoding. This made more levels to try within the `Classification` and the `Application Type` columns but could allow for more accuracy if fewer items were lumped together within Other that were actually not related. These changes did not substantially increase the accuracy.
    - The number of nodes within the neural network were increased. Several different combinations were tried for the number of neurons in layer 1 and layer 2. The code in the Optimization file shows the last combination tried (60 in layer 1 and 30 in layer 2). These changes did not substantially increase the accuracy.
    - The number of nodes were increased again, along with adding a third layer in the network and experimenting with different activation functions. The code in the Optimization file shows the last combination tried (100 neurons in layer 1, 50 in layer 2, 20 in layer 3, and the tanh activation function). These changes did not substantially increase the accuracy.


## Summary
The final accuracy of the neural network was about 73%. To get a better model, it is recommended that the categorical variables be further researched and refined so that it is better understood what those variables mean and whether or not they are useful. In particular, the `Income Amount` variable is categorical and has values such as 1-9999, 10000-24999, and 1M-5M. If this column could be converted to a numerical value, it would likely help as income is important in making decisions related to loans. The current values in the column such as 1M-5M indicate 1 million to 5 million, which is very different from 1-9999. Having these values be numerical in some way would help tremendously. It may also be worth trying to make a Random Forest model since so many variables in this dataset are categorical in nature.