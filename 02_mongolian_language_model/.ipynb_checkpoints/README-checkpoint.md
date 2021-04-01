# ULMFiT Language Model for Mongolian
This project generates a language model suitable for fine-tuning and training a classifier. The ULMFiT method proposed by the Fast.ai co-authors Jeremy Howard and Sebastian Ruder is used ([paper](https://arxiv.org/abs/1801.06146)). This method has three steps:
1. General Language Model - Pre-train a language model using a relatively large general corpus.
2. Language Model Fine Tuning - Perform transfer learning on the general language model using your problem specific dataset.
3. Classifier Training - Using the fine tuned language model train a text classifier. Excellent results can be found with only 100 training examples.

You can used the linked model and vocabulary below to fine-tine on your own data and then build a text classifier.

The benefits of ULMFiT (from my perspective):
1. The pre-trained language model is not prohibitively expensive to train and does not require massive amounts of data. State of the art results can be achieved with a corpus of 100 million words.
2. Affordable hardware can be used for all stages. 
3. Fine-tuning and classification can take as little as an hour (or even minutes) and doesn't require large amounts of labeled data. The authors found great results with as few as 100 labeled examples. 

#### Libraries:
Notebooks used the following versions:
- Fast.ai version: 2.2.7
- Fastcore version: 1.3.19
- torchtext version: 0.8.0 (There was a dependency error with the fast.ai and fastcore versions above on Google Colab, so I installed torchtext 0.8.0)
- sentencepiece version: 0.1.95

#### Notebooks:
- **01 - Large News Corpus Data Prep**: Loads all files from original dataset into a Pandas dataframe and randomly samples 20% of the dataset. Output is the data used to train the LM in notebook 02.
- **02 - Large MGL News Language Model**: Trains the language model using a sentence piece tokenizer with the 20% sample from the large news corpus. Training took approximately 30 hours on a Quadro P4000. A perplexity of *32.7* is reached after 10 epochs. 
- **03 - Fine Tune Language Model**: The language model is fine-tuned on the Eduge dataset for 10 epochs.
- **04 - Train Classifier**: The classifier is trained on the Eduge dataset. An accuracy of 93.5% is reached. 

#### Data:
Data is in the data folder. [Google Drive link.](https://drive.google.com/drive/folders/1iG_qAJHJcB6V9wFJDGO00BuMvrW942lZ?usp=sharing)
- `news`: Folder containing the original Mongolian Large News Corpus.
- `20_news.txt`: 20% sample from the Mongolian Large News Corpus
- `40_news.txt`: 40% sample from the Mongolian Large News Corpus. Not used in the language model due to memory issues.

#### Outputs:
Result is a language model suitable for transfer learning on a variety of tasks. There are two folders containing completed models. One is SentencePiece Encoded and the other uses the default spaCy Encoder. 

[Pretrained language model](https://drive.google.com/drive/folders/1uXqhw6gLCyewZ1L7WMLO3pkgL--xd8yx?usp=sharing) (Google Drive Folder). Folder contains two model folders. Choose the model that corresponds to the encoder you want to use (SentencePiece or spaCy). spaCy is the default encoder, so use that if you aren't sure.
- `mn_20_news_lm.pth`: Language model used to create your learner in the Fast.ai library for fine tuning.
- `mn_20_news_vocab.pkl`: Vocabulary for the pre-trained language model. Imported alongside the model above when creating your learner.
- `spm.model`: Sentence piece model. Can be used to set up your tokenizer for your dataloader. **This seems to be optional as I was able to fine-tune without the sentence piece tokenizer when I tried.**
- `spm.vocab`: Vocabulary for the sentence piece tokenizer.

[Eduge classifer.](https://drive.google.com/file/d/1-0AovxFFmpvVT1LTw_j5awPQTgAtF6k4/view?usp=sharing) Can be used for classifying news stories with the Fast.ai library. 
- `eduge_classifier.pkl`: Pickled model. 

#### Notes:
Since I used a large news corpus and trained the language model on it instead of a more "general" dataset like a Wikipedia corpus, I didn't see an increase in my test case, Eduge classification, of 93.5% accuracy. It's also possible that this is the top end of the accuracy possibility without other augmentations or a different architecture.

The sentence piece tokenizer (spt) is really really fast, and is definitely faster than the default tokenizer. It also seems that you can train a language model with the spt then fine tune with the default tokenizer. Although it would make sense to use the same tokenizer the whole way through. 

I'll be using this pre-trained model for testing other classification tasks soon.
