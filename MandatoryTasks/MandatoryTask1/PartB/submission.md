# Developing a translational model for cross language communication
This model helps in converting a text from English language to french

## Installation steps
- Fork this repository
- Install Transformers from tensorflow

  ```
  !pip install transformers datasets sacrebleu sentencepiece tensorflow --quiet
  ```
  
## Workflow
- Import tensorflow, numpy and load_dataset
- From transformers import necessities

```
  from transformers import (
    AutoTokenizer,
    TFAutoModelForSeq2SeqLM,
    DataCollatorForSeq2Seq,
    create_optimizer
)
```

### Load the dataset
- Use en-fr auto-download dataset from huggingface

```
dataset = load_dataset("opus_books", "en-fr")
```

### Datapreprocessing
- Split the dataset into train and test dataset took a range of 3000 for the easier and faster building of the model
- All the text has been converted into lower case
- All the symbols, numbers and punctuations have been removed

### Tokanizing - converting text into numbers

#### English tokanizer - converts english words to numbers

```
tokenizer_en = keras.preprocessing.text.Tokenizer(filters='')
tokenizer_en.fit_on_texts(en_texts)
input_tensor = tokenizer_en.texts_to_sequences(en_texts)
```

#### French tokanizer

```
tokenizer_fr = keras.preprocessing.text.Tokenizer(filters='')
tokenizer_fr.fit_on_texts(fr_texts)
target_tensor = tokenizer_fr.texts_to_sequences(fr_texts)
```


- Padding the sequences to make it the same length by adding 0 when the length of the sequence is smaller than the padding length taken
```
input_tensor = keras.utils.pad_sequences(input_tensor, padding='post')
target_tensor = keras.utils.pad_sequences(target_tensor, padding='post')
```

- creating a training dataset from the target_tensor and input_tensor from tokanizers
- Number of steps per epoch are defined by batch_size and buffer_size taken

```
batch_size = 64
buffer_size = len(input_tensor)
steps_per_epoch = buffer_size//batch_size

dataset_tf = (
    tf.data.Dataset.from_tensor_slices((input_tensor, target_tensor))
    .shuffle(buffer_size)
    .batch(batch_size, drop_remainder=True)
)
```

- Building seq2seq model using encoder-decoder architecture by taking the right parameters
- Training the model(Model) from the encoder and decoder input data
- Encoder and decoder inferences done by putting in Model function
- Create reverse word mappings - numbers to words
- Build a function to translate english to french
  

### Some examples tried on the built model

Input

```
English: the former was divided between admiration of the brilliancy which exercise
had given to her complexion, and doubt as to the occasion's justifying her coming so far alone.
the latter was thinking only of his breakfast.
```


Output

```
Translated to French: la rue tait un d heure, il tait un d te de la v te de la table et les 
yeux du plus de la c te de la vie et les yeux de la vie et les yeux de la famille.
English: how dared they kill him!
```


