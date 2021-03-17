# ULMFiT Language Model for Mongolian

The paper outlines a three step process to achieve excellent results:
1. General Language Model - Pre-train a language model using a relatively large general corpus.
2. Language Model Fine Tuning - Perform transfer learning on the general language model using your problem specific dataset.
3. Classifier Training - Using the fine tuned language model train a text classifier. Excellent results can be found with only 100 training examples.

The benefits of ULMFiT (from my perspective):
1. The pre-trained language model is not prohibitively expensive to train and does not require massive amounts of data.
2. Affordable hardware can be used for all stages. 
3. Fine-tuning and classification can take as little as an hour and doesn't require large amounts of labeled data.


## Output
Result is a language model suitable for transfer learning on a variety of tasks. See the folder for more details. 

[Download pretrained model](https://drive.google.com/drive/folders/1uXqhw6gLCyewZ1L7WMLO3pkgL--xd8yx?usp=sharing) (Google Drive Folder). Folder contains:
- `mn_20_news_lm.pth`: Language model 
