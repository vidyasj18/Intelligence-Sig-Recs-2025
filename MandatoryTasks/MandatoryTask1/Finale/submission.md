# Designing a Machine Learning System
This model gives answer in the french language when question is asked in english language.Using pretrained QA model.
This combines all 3 parts A,B and C together to provide desired output.

## Installation steps
- Fork this repository
- Install Libraries
  
```
!pip install tensorflow numpy
```

## Workflow

- Import necessary libraries like tf, tokanizer,pad_sequences,sequential etc.
- I considered 1 example containing context, answers_en,answers_fr,questions similar to NewsQA dataset

### Datapreprocessing
- All the text(context,questions and answers in en and fr) has been converted into lower case
- All the symbols, numbers and punctuations have been removed

### Tokanization - Part A
- Done by TfidfVectorizer imported from sklearn.feature_extraction.text
- Tokanization is done using creating layers using tensorflow

### QA Model is created - Part C
- By using Transformers and pyTorch
- Pre Trained QA model BERT is used to find answer from the question given in dataset

### Translation Model is built - Part B
- Translates text from English to French
- Done using encoder-decoder architecture
- Inference models are used

### Integration of French Translational model with QA model

```
def ask_question(question, context):
    english_answer = get_answer_english(question, context)
    french_answer = translate_to_french(english_answer)
    return english_answer, french_answer
```

### User can give input the english question present in the NewsQA dataset and get the answer in french

```
user_q = input("Enter your question in English: ")
eng_ans, fr_ans = ask_question(user_q, context)
print(f"English Answer: {eng_ans}")
print(f"French Answer: {fr_ans}")
```

### Input
```
Who created Python?
```

### Output
```
Answer (English): guido van rossum
Answer (French): van rossum
```

  
