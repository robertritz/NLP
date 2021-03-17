# NLP
 
Collection of NLP projects, mostly relating to Mongolian. Datasets and model outputs are not pushed to Github because of file size. The notebooks assume that you have the data extracted to a data folder. 


### Eduge Classification
Folder: `01_eduge_classification`

This is a classification task for the [Eduge](https://github.com/tugstugi/mongolian-nlp/blob/master/datasets/eduge.csv.gz) dataset of 70 thousand Mongolian online news articles with labeled news categories. This project uses Fast.ai. A shortened process is used:

1. Training [ULMFiT](https://arxiv.org/abs/1801.06146) language model on Eduge dataset
2. Train classifier

After training a language model using the Eduge dataset, a classifier accuracy of 93.5% is reached after 10 epochs. Training the classifier without the language model gives an accuracy of roughly 90.5% after 10 epochs.

### ULMFiT Mongolian Language Model (In Progress)
Folder: `02_mongolian_language_model`

This is a project to create a general language model using the [ULMFiT](https://arxiv.org/abs/1801.06146) method proposed by the Fast.ai co-authors Jeremy Howard and Sebastian Ruder. The paper outlines a three step process to achieve excellent results:
1. General Language Model - Pre-train a language model using a relatively large general corpus.
2. Language Model Fine Tuning - Perform transfer learning on the general language model using your problem specific dataset.
3. Classifier Training - Using the fine tuned language model train a text classifier. Excellent results can be found with only 100 training examples.

The benefits of ULMFiT (from my perspective):
1. The pre-trained language model is not prohibitively expensive to train and does not require massive amounts of data.
2. Affordable hardware can be used for all stages. 
3. Fine-tuning and classification can take as little as an hour and doesn't require large amounts of labeled data.
