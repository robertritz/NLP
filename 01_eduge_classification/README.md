# Eduge News Classification

This is a classification task for the [Eduge](https://github.com/tugstugi/mongolian-nlp/blob/master/datasets/eduge.csv.gz) dataset of 70 thousand Mongolian online news articles with labeled news categories. This project uses Fast.ai. 

After training a language model using the Eduge dataset, a classifier accuracy of 93.5% is reached after 10 epochs. Training the classifier without the language model gives an accuracy of roughly 90.5% after 10 epochs.


#### Notebooks:

- **01 - Mongolian Language Model**: A language model is trained using the Eduge dataset. An accuracy of 33% is reached for the language model.
- **02 - Eduge Classifier**: Using the vocabulary and encoder (i.e. language model) from notebook 01, a classifier is trained to predict news category. An accuracy of 93.5% is reached after 10 epochs. 
- **03 - Eduge Classifier w_out Pretrained LM**: The purpose of this notebook is to show the difference in accuracy achieved in a classifer model with a pre-trained language model vs without. Below we can see that after several epochs the accuracy flattens out around 90-91%. 

#### Data:

Data is in the `data` folder. [Google Drive link.](https://drive.google.com/drive/folders/15zqDnt9YEuXydMkxnKsyNDNA_lDS4MH_?usp=sharing)
- `news.csv`: This is the Eduge news dataset as downloaded from the source. Used to train the language model and classifier.
- `eduge_clean.csv`: Not used in the notebooks. This is a cleaned verison of the Eduge dataset. A slightly better accuracy can be obtained with the cleaned data. For comparison reasons this dataset isn't used. 

#### Outputs:

Outputs are in the `models` folder. [Google Drive link.](https://drive.google.com/drive/folders/1SmPRDsZRNX7Mj_OPPkO3A4mZG648mEIm?usp=sharing)
- `mn_eduge_lm.pth`: The complete language model including encoder and decoder. 
- `mn_eduge_lm_encoder.pth`: The saved encoder from the learner. This is used to prep our learner in notebook 02.
- `mn_eduge_vocab.pkl`: The vocabulary to correspdong with the language model. This is also needed in notebook 02 to create our dataloaders object.
