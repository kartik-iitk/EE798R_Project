# Phase 2 - TIM-Net

## How to Run?

I have trained and tested the code on an _OSX-ARM_ Architecture in a `Python 3.8` _miniforge_-based environment.

### Setup Environment

`cd` to the `./Phase\ 2` directory. Use the environment created for Phase 1 directly or otherwise please refer the setup instructions for Phase 1.

### Add Dataset

Directly download and save the pre-processed MFCCs in the `./MFCC` directory. For more information on data pre-processing, please refer to Phase 1's README.

### Code Organisation

All the code for the model and the training/testing scripts is available in `./train.ipynb`

**Note**:

1. Set the hyperparameters as per the choice of the dataset mentioned in the markdown cells the Jupyter Notebook.
2. The changes implemented in Phase 2 are on top of the changes made during Phase 1. For more more information regarding the previous changes, please refer the README of Phase 1.

### Outputs

The generated model will be saved in the `./Models` folder. The corresponding visualisations will be saved in the `./logs` folder. The split-wise accuracies are saved in the`./Results` folder in `.xlsx` format.

For reference, a combined analysis of the accuracies achieved are in `./Results/Phase\ 2\ -\ Accuracy\ Analysis\ Summary.xlsx`.

### Report

The report corresponding to my implementation of Phase 2 is available in `./kartik_210493_report.pdf`.
