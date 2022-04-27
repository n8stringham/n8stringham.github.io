# An Entity Recognizer for Literary Texts

[Try out the system](https://huggingface.co/nates/LER-roberta)

Named Entity Recognition is a fundamental task in NLP and serves as a key feature for many downstream tasks. However, Most NER systems have been trained on text from specific domains such as news articles. While this might seem like a general domain, it turns out that these systems often struggle when used in a domain where they entity types and distributions are substantially different. One such domain is Literature.

### Task Description
This system is designed to extract 6 types of entities from literary text 
- people (PER)
- facilities (FAC)
- geo-political entities (GPE)
- locations (LOC)
- vehicles (VEH)
- organizations (ORG)

We use the [LitBank](https://github.com/dbamman/litbank) dataset for training, development, and evaluation which consists of entities from 100 English Literature books from [Project Gutenberg](https://www.gutenberg.org/)


### What Makes Literature Different?
- Different distribution across entity types (more PER, FAC, LOC)
- Longer entities (Rich literary descriptions of entities)
- common nominals as well as named entities
- figurative language (personification, metaphor, metonymy)

### System Description
My system, `LER-RoBERTa`, is a fine-tuned version of the pre-trained RoBERTa model from Hugging Face. Specifically, it uses the `roberta-base` checkpoint for its weights and a token classification head. The model is fine-tuned on the token level BIO tags from [LitBank](https://github.com/dbamman/litbank).

The system takes in a sentence, tokenizes it, passes it through RoBERTa's series of transformer layers and then through a final classification layer which returns a probability distribution over the 13 possible BIO tags for each token. The system then chooses the tag with highest probability for each token as the label. Tokens with appropriate labels are then combined to produce full entity predictions.

I performed hyperparameter selection using a grid search over the learning rate and epochs, selecting the model that had the highest accuracy on the dev set. 

The final model was trained for 3 epochs with a learning rate of 5e-5 and weight decay of 0.01 


### Summary
The fine-tuned model is available on the [Hugging Face model hub](https://huggingface.co/nates/LER-roberta) so feel free to try it out there!

While entity recognition may seem like a relatively solved task in NLP, there is a long tail of domains and entity types that systems still struggle to extract.

You can view the [slides](https://n8stringham.github.io/slides/ler-slides.pdf)

This project was completed as part of CS6390 - Information Extraction from Text at the University of Utah in Spring 2022.
