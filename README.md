Denne README filen burde dekke det som trengs av kunnskap for å kjøre koden. Skal sendes med koden til foreleser
# italy_dl_padova

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


## Dokumentering
Linke det vi bruker mot kilder, og få det ned i dokument. sikkert eksperimenelt og metode. Evt legg ved formler og algoritmer


