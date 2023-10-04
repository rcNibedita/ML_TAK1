
# ML_TAK1

This project aims to identify important features classifying the 'TAB1-bound' and 'apo' conformations of TAK1 obtained through MD simulation.

1. randomforest.ipynb:

This script is a part of Workflow1 and contains the code that uses random forest algorithm to:

a. Classify the 'TAB1-bound' and 'apo' TAK1 conformations from a dataset of their mixture by learning splitting rules using important features. 

b. Extract the important features and rank them according to their importance (MDI score).
The same script is invoked to perform multiple iterations of PhaseI (feature pre-selection) and Phase II (feature identification) classifications. 

2. MLP.ipynb:

This script is a part of Workflow2 and contains the code that uses multilayer perceptron (neural network) model to:

a. Classify the 'TAB1-bound' and 'apo' TAK1 conformations from the merged dataset by learning relation between the target output and a subset of input features (selected from Phase I RF classification) in the network architecture.

b. Score and rank each feature by computing the average of all connection weights between its input neuron and neurons of the subsequent hidden layer.
The same script is invoked to perform multiple iterations of classification with different MLP architectures (tuning number of hidden layers).

3. CompositeFeatureScore.ipynb: 

This script is used for composite scoring of features for each of the models: Random Forest and Multilayer Perceptron. 
This scoring performs a simple summation of model scores recieved by each feature across multiple iterations of model classification to generalize feature importance estimates. 

4. MI_rescoring.ipynb:

This script is also a part of Workflow2 and follows MLP classification. It uses mutual information (MI) classification algorithm to:

a. Classify the 'TAB1-bound' and 'apo' TAK1 conformations from the merged dataset using features (mixture of strong and poor conformational class discriminants) that were prioritized by various MLP architectures.

b. Rescore the features by computing the stregnth of association (MI) between the target (class) and input (feature) variables.

c. Extract the important features that recieve the highest MI scores.
