# Building a Question and Answer Model - Part - C
Model is created which answers to the question one asked. This works on the a defined set of questions present in the dataset.

## Installation steps
- Fork this repository
- Installing required libraries

```
pip install transformers datasets tensorflow evaluate
```

## Workflow

- Import necessities like tensorflow,pandas, load_dataset, re and TFAutoModelForQuestionAnswering, AutoTokenizer from Transformers
- install datasets using pip install datasets

### Dataset
- Dataset directly used from huggingface https://huggingface.co/datasets/lucadiliello/newsqa - NewsQA
- This dataset has 4 columns which are - 'id', 'context', 'question', 'answers'

### Load the dataset
- dataset has context in the form of numpy array so we need to convert it into dictionary format
- Drop the missing data rows

### Tokanization

```
from transformers import AutoTokenizer

MODEL = "deepset/roberta-base-squad2"
tokenizer = AutoTokenizer.from_pretrained(MODEL)

max_length = 300
doc_stride = 100
```

- Apply tokanization to dataset
- Convert hugging face dataset to tensorflow dataset to proceed ahead

### Loading pretrained model 
- tried doing with tensorflow by installing Transformers but i was getting error
and was not able to move forward. That is why installed pyTorch ahead to continue building the model

```
pip install torch torchvision torchaudio --index-url https://download.pytorch.org/whl/cpu
```

- Model is trained using pretrained models
```
from transformers import AutoTokenizer, AutoModelForQuestionAnswering

MODEL = "bert-large-uncased-whole-word-masking-finetuned-squad"

tokenizer = AutoTokenizer.from_pretrained(MODEL)
model = AutoModelForQuestionAnswering.from_pretrained(MODEL)
```

### Testing on some example

Input 
```
context = "Vidya is learning NLP using Hugging Face Transformers."
question = "What is Vidya learning?"
```

Output
```
Answer: nlp
```

