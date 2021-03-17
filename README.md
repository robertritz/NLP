# NLP
 
Collection of NLP projects, mostly relating to Mongolian. Datasets and model outputs are not pushed to Github because of file size. The notebooks assume that you have the data extracted to a data folder. 


### Eduge Classification
Folder: `01_eduge_classification`

This is a classification task for the [Eduge](https://github.com/tugstugi/mongolian-nlp/blob/master/datasets/eduge.csv.gz) dataset of 70 thousand Mongolian online news articles with labeled news categories. This project uses Fast.ai. A shortened process is used:

1. Training [ULMFiT](https://arxiv.org/abs/1801.06146) language model on Eduge dataset
2. Train classifier

After training a language model using the Eduge dataset, a classifier accuracy of 93.5% is reached after 10 epochs. Training the classifier without the language model gives an accuracy of roughly 90.5% after 10 epochs.

### ULMFiT Mongolian Language Model
Folder: `02_mongolian_language_model`

This is a project to create a general language model using the [ULMFiT](https://arxiv.org/abs/1801.06146) method proposed by the Fast.ai co-authors Jeremy Howard and Sebastian Ruder. See the folder for more details and link to the completed model.

Result is a general language model that can be used for transfer learning on a variety of tasks. Notebook show the complete three stage process:
1. Pre-training language model
2. Fine tuning model on target dataset
3. Training the classifier
