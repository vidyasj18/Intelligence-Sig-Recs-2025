# Creating word Embeddings Part - A
Representing the words in the form of vectors. Have the unique vectors for each word.

## Installation steps 
- Fork this repository
- install Tensorflow
  '''
  !pip install -q tensorflow tensorflow-hub pandas numpy nltk
  
  '''
- Install datasets library - to directly use the dataset without downloading
  '''
  pip install datasets
  '''

## About the dataset
- The dataset used is https://huggingface.co/datasets/lucadiliello/newsqa - NewsQA
- This dataset has 4 columns which are - 'id', 'context', 'question', 'answers'
  
## Workflow

### Loading the dataset and splitting into training dataset
'''
from datasets import load_dataset
dataset = load_dataset("newsqa", split="train")
'''
### Converting the dataset to pandas dataframe
'''
import pandas as pd
df = pd.DataFrame(dataset)
'''
### Datapreprocessing
- we took starting 500 rows of 'context' from the dataset for the easier and faster building of the model
- All the text has been converted into lower case
- All the symbols, numbers and punctuations have been removed

### Word embedding methods 
There are 2 methods 
1. Using embedding layers using tensorflow and neural networks
2. Using word2vec

#### 1. Embedding Layers 
Done by importing TfidfVectorizer from sklearn.feature_extraction.text
''' 
layer = TfidfVectorizer(max_features=100)  
X_layer = layer.fit_transform(processed_texts)
'''
Converted the results to dataframe and saved to .csv file(present in the current folder itself under the name "layer_embeddings.csv" 
or "layer_word_embedding.csv") 

#### 2. Word2vec embeddings
Word2Vec learns relationships between words based on context (similar to how humans infer meaning).
The model will produce dense embeddings (vectors) for each word.

import word2vec and word_tokenize
''' 
from gensim.models import Word2Vec
from nltk.tokenize import word_tokenize

import nltk
'''
Download nltk and tokenize the sentences

Install genism
''' 
pip install gensim
'''

##### Training the word2vec model 
1. Using no skip-gram
- Create a model with all the parameters needed (sg = 0)
- Convert embeddings to dataframe
- embeddings have been saved to .csv(exists in present folder under the name of "word2vec_embeddings.csv")

2. Using skip-gram
- Create a model with all the parameters (sg = 1)
- Covert embeddings to dataframe
- embeddings have been saved to .csv(exists in present folder under the name of "word2vec_skipgram_embeddings.csv")



  
