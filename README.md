# Telugu Text Generation using N-Gram Language Models

## Introduction

This project explores Telugu text generation using classical Natural Language Processing (NLP) techniques. Since most NLP resources and language models are heavily focused on English and a few other major languages, this work aims to experiment with language modeling for Telugu, a relatively low-resource language.

The model was trained on a collection of Telugu newspaper articles from Andhrajyothi and uses N-gram language models to learn word patterns and generate text. Different N-gram models were compared to understand how increasing context affects text generation quality and model performance.

---

## Dataset

The dataset contains 10,821 Telugu newspaper articles collected from Andhrajyothi. The articles cover a variety of topics such as politics, administration, business, sports, and current affairs.

After preprocessing, the corpus contained roughly 1.79 million words with a vocabulary of about 198,000 unique words.

---

## Preprocessing

Before training the language models, several preprocessing steps were applied to the raw articles.

First, unnecessary content such as XML tags, English characters, numbers, punctuation symbols, and extra whitespace was removed from the documents.

The cleaned text was then tokenized using the Indic NLP Library to split each article into individual Telugu words.

A manually prepared Telugu stopword list was used to remove frequently occurring words that add little semantic value. Examples include words such as "ఈ", "ఆ", "ఒక", "అని", and "లో".

Finally, a simple rule-based stemming approach was applied by removing common Telugu suffixes. This helped reduce vocabulary size and group related word forms together.

---

## Language Models

Four different language models were implemented and evaluated:

* Unigram
* Bigram
* Trigram
* Quadgram

The unigram model considers only individual word frequencies.

The bigram model predicts a word using the immediately preceding word as context.

The trigram model uses the previous two words, while the quadgram model uses the previous three words to make predictions.

To avoid zero probabilities for unseen word combinations, Laplace (Add-One) smoothing was used during probability estimation.

---

## Text Generation

Text generation starts with a user-provided seed word or sequence of words.

Using the learned N-gram probabilities, the model repeatedly predicts the most likely next word and gradually constructs a sentence.

For example, starting with a seed word such as "విద్యుత్తు", the model generates a continuation based on patterns observed in the training corpus.

---

## Evaluation

The models were evaluated using perplexity, which is a standard metric for language models.

Perplexity measures how well a model can predict a sequence of words. Lower perplexity generally indicates better predictive performance.

Among all the models tested, the bigram model achieved the best result with a perplexity of 55.95.

---

## Observations

A few interesting patterns were observed during experimentation.

The unigram model was too simple and often produced text without meaningful context.

The bigram model provided a good balance between contextual information and data availability, resulting in the best overall performance.

Although trigram and quadgram models had access to more context, they suffered from data sparsity because many word combinations appeared very rarely in the dataset. As a result, their performance was not as strong as expected.

The generated text was able to capture common Telugu news-writing patterns, although repetition occasionally appeared due to the nature of N-gram based generation.

---

## Technologies Used

Python was used for implementation along with the Indic NLP Library for Telugu tokenization. The experiments were performed in Jupyter Notebook.

---

## Project Structure

```text
telugu-text-generation/
│
├── telugu_text_generation.ipynb
├── dataset/
└── README.md
```

---

## Future Work

Some possible improvements include:

* Better Telugu stemming techniques
* More advanced smoothing methods
* Proper train-test data splitting
* Neural language models such as LSTM or GRU
* Transformer-based Telugu text generation

---

## Conclusion

This project was an attempt to apply classical NLP techniques to Telugu text generation and language modeling. Through the implementation of unigram, bigram, trigram, and quadgram models, it was possible to study how context influences prediction quality and how challenges such as vocabulary sparsity affect regional language processing. The experiments showed that, for this dataset, the bigram model provided the most effective balance between simplicity and performance.
