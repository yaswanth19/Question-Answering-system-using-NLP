# Open-Domain Question Answering with DistilBERT

## Overview

This README provides an overview of our project on open-domain question answering using DistilBERT, a lightweight variant of BERT. We explore how using various transformers can significantly enhance the performance of question answering systems, enabling better comprehension of complex queries and improved search engine capabilities.

## Dataset

In this question-answering (QA) dataset, each example is represented by a unique ID, context, question, answer start position, and answer text. The context represents a larger body of text from which the model must extract answers. The question is the query posed to the model, and the answer start and text indicate where the answer is found in the context. A preview of the dataset is shown in Figure 1.

## Data Preprocessing

To facilitate the question-answering task, we perform contextual preprocessing. If the context length exceeds the model's maximum length, we tokenize the input text (question + context) using truncation, padding, and stride parameters. We map the tokenized input back to original examples using an offset mapping, accurately identifying answer positions in the context. When no answer is present, special classification tokens ([CLS]) are used. If an answer exists, the offsets mapping helps match answer positions to corresponding tokens in the input.

## Question Answering System using DistilBERT

We employ DistilBERT, a distilled version of BERT, for our question answering system. DistilBERT is a pre-trained language model developed by Google that can be fine-tuned for various NLP tasks. It offers a more efficient alternative to BERT.


### Post Processing

BERT outputs logits for start and end positions of the answer which are not interpretable to find the exact answer words in context we apply a softmax to find the most probable start and end words. During inference, the tokens with the highest scores are selected for start and end positions. These tokens are used to extract the answer.

## Results

We evaluated different models: RoBERTa for QA, BERT for QA, and Distilled-BERT. The results are shown in the below table.

| Model          | Loss  |
|----------------|-------|
| RoBERTa for QA | 4.02  |
| BERT for QA    | 1.57  |
| Distilled-BERT | 0.62  |


## Conclusion

In conclusion, our project demonstrates the effectiveness of DistilBERT on small dataset and there is a possibility that the larger modesl perform better when the data size increases.Thus by leveraging transformers and efficient preprocessing, we achieve accurate answers to diverse queries and enhance search engine capabilities. The use of Jaccard score as an evaluation metric provides insight into model performance.

` For code implementation, refer to the above project files `
