Denne README filen burde dekke det som trengs av kunnskap for å kjøre koden. Skal sendes med koden til foreleser
# README

## main.ipynb
Main running model
- Global variables: Some hyperparameters for the model and some other variables
### Data Preprocessing
- Loading file as Pandas Dataframe
- Impute 0s with linear regression
- Splitting data into 5 folds after given indexes
- Scaling each fold from given training data
  

### NN
- Designing the architecture of the Neural Network to have a input layer of 26 neurons, two hidden layers with 14 neurons and 10 neurons in the respective order, and a output neuron for classification
- Creating fully connected deep neural network
- ReLU as activation function on weights between layers
- Sigmoid as activation function on output layer to convert it to a binary value

### Training Loop
- Seeded for reproducibility
- Training the model seperatily on each fold, then saving the model in the `models` folder for later validation.
- Uses Binary Cross-Entropy Loss to adjust model weights
- Uses Adam to try to optimize our loss and search for the global minima
- Plotting loss vs. epoch to visualize how the model changes over time
- Predicting MCC scores on training data

### Testing the model on the test set
- Loading the previously trained models on the different folds, and runs a forward propagation on the test data, while calculating the:
  - f1 score
  - MCC (Matthews Correlation Coefficient)
  - Accuracy
  - Precision
  - Recall
  - Confusion Matrix
- Plotting all the scores on a bar plot for better visualization 
### Confusion matrix comparison
- Plotting Confusion Matrixes also for better visualization of number of TP, FP, TN and FN values.
- Plotting a mean confusion matrix score to have better overall confidence of model

## viz_data
Notebook used for extracting test and training data from the original_dataset/ReadBrownDwarf.mat file.
Notebook generates 4 csv files in the original_dataset/ folder: 
- idTE.npy
- idTR.npy
- labelTE.npy
- labelTR.npy

Due to a bug in the data, fold 2 in the index and labeling data had one extra data point for the training set and one less for the test data. This was solved by removing the last element in the training data, and adding it to the test data, for both the labeling and index.

## act_func_test
Notebook used for comparing different activation functions used in the deep network, to evaluate which yields the best results.
Network architecture is chosen as an arbitrary, but qualified guess to be 26x10x5x1
### Components
#### Training loss
Used to compare training loss vs #epochs
ReLU seems to decrease the losses fastest, but Hardtanh could find a more optimal solution, given enough epochs
#### Bar plot
Used to compare different performance indicators after the last epoch
Hardtanh and ReLU seems to have the best overall results, and looking at the MCC values, Hardtanh achieves the best score.
#### Confusion matrix
Used to compare true positive (TP), false negative (FN), false positive (FP) and true negative (TN).
The goal here would be to have the highest number of TP, since we want to find more brown dwarfs in space, while also avoiding FP, to avoid misclassifieng normal stars as brown dwards. Offcourse we also would want to achieve a high number of TN and FN, but considering the goal of the deep neural network: "creating a significant reliable sample of brown dwarfs", the sample that the network should deliver as an output should be reliable.



# TODO/Improvements
## Initialization
Begrunne vår initialisering
Se om ulike init. påvirker resultatet mye (ikke det viktigste)


## Activation Function
Dokumenter forskjellene og legg evt ved plot
Pass på å kjør ulike trening/test set for å forbedre resultatet
Tenk på en god måte å sammenligne disse resultatene på (snitt, varians, std. avvik...)
RELU
Logistisk
Tanh
Sigmoid, kan gå siden vi har få layers, men husk exploding gradient og vanishing gradient
Legge ved plots og skrive om på metode og resultater

## Feature Selection
Begrunne valg av features, plotte valgte (og ikke valgte features) for å se deres viktighet.
Prøvd å bruke PCA, men 
Skriv ut de featurene den velger, for å se at features som gir mening passer. 
Dokumentere at PCA gir like bra/muligens bedre resultat? Like bra er vel bra uansett siden den skal minimere kjøretid

## Dokumentering
Linke det vi bruker mot kilder, og få det ned i dokument. sikkert eksperimenelt og metode. Evt legg ved formler og algoritmer
