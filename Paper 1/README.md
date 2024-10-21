# Paper 1 - TIM-Net

Following is the **_modified_** implementation of **T**emporal-aware b**I**-direction **M**ulti-scale Network, termed **TIM-Net**. [[paper]](https://arxiv.org/abs/2211.08233)

## How to Run?

I have trained and tested the code on an _OSX-ARM_ Architecture in a `Python 3.8` _miniforge_-based environment.

### Setup Environment

`cd` to the `./Paper\ 1` directory. Create the environment from the `./requirements.txt` file using the following command:

```
conda create --name IPR_P1 --file requirements.txt
```

In case of any issues, the exact steps for environment creation are as follows:

```
conda create -n IPR_P1 python=3.8
conda activate IPR_P1
conda install cvxopt h5py keras librosa matplotlib numba numpy openpyxl pandas prettytable scikit-learn scipy tqdm
conda install -c apple tensorflow-deps
python -m pip install tensorflow-macos
pip install spafe speechpy
conda install ipykernel natsort
pip install python-speech-features
python -m pip install tensorflow-metal
```

### Add Dataset

The organised dataset can be saved to the `./Datasets` folder which can be used for MFCC generation as mentioned in `./preprocess.ipynb`. To skip pre-processing, you can directly download and save the pre-processed MFCCs in the `./MFCC` directory.

### Code Organisation

The code is organised in 3 files. Run them in the following order:

1. `preprocess.ipynb` - Used to convert the Raw Dataset to npy MFCCs used for training and testing the model. Copy the MFCCs to the MFCC directory.
2. `train.ipynb` - It contains the code for the model and the training/testing scripts.
3. `tsne.ipynb` - File used for generating the t-SNE visualisation for the penultimate layer of the trained model.

**Note**:

1. Set the hyperparameters as per the choice of the dataset mentioned in the markdown cells of all 3 files.
2. The [official Github repository](https://github.com/Jiaxin-Ye/TIM-Net_SER) included [updated results](https://github.com/Jiaxin-Ye/TIM-Net_SER?tab=readme-ov-file#-additional-experimental-results-update-for-cpac-and-gm-tcnet), after the paper publication. These addressed some overfitting concerns causing the accuracies to drop.
3. I have added additional custom model checkpointing constraints to minimize overfitting and increase training speed on my laptop. I also ran it for a smaller number of splits. In spite of all of these changes, we are still getting accuracies close to that mentioned in the repository in most cases.
4. Based on size, `IEMOCAP` was very large causing 1 epoch to run for a long time (> 1.5 min) on my local machine. Running the code locally for 10 splits would take around 1 week for training and hence a split size of 2 was used for training. The accuracy can be further improved by running more epochs (> 500) on larger number of split-folds (> 8) in a decent GPU environment.
5. Raw `CASIA` dataset was not available publicly and hence the author's pre-processed MFCCs were used as is.

### Outputs

The generated model will be saved in the `./Models` folder. The corresponding visualisations will be saved in the `./logs` folder. The split-wise accuracies are saved in the`./Results` folder in `.xlsx` format.

For reference, a combined analysis of the accuracies achieved are in `./Accuracy\ Analysis\ Summary.xlsx`.

## Acknowledgments

```bibtex
@inproceedings{TIMNET,
  title={Temporal Modeling Matters: A Novel Temporal Emotional Modeling Approach for Speech Emotion Recognition},
  author = {Ye, Jiaxin and Wen, Xincheng and Wei, Yujie and Xu, Yong and Liu, Kunhong and Shan, Hongming},
  booktitle = {ICASSP 2023-2023 IEEE International Conference on Acoustics, Speech and Signal Processing (ICASSP), Rhodes Island, Greece, June 4-10, 2023},
  pages={1--5},
  year = {2023}
}
```
