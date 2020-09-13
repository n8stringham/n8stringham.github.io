# Learning Word Embeddings for a Latin Corpus

This project was completed in order to fulfill the senior thesis requirement for my undergraduate degree in Mathematics from Pomona College. The project involved a yearlong independent study of a chosen research topic, three presentations, and a final write up. I was advised throughout by [Mike Izbicki](https://www.cmc.edu/academic/faculty/profile/michael-izbicki).

### Presentation
* Slides [pdf](LatinEmbeddings/NateStringham_Presentations-final.pdf)

### Project Components
* Survey of embedding methods
* Construction of historical Latin corpus and sub-corpora
* Training of word2vec embedding models on Latin corpus
* Construction of evaluation set
* Evaluation of model quality

### Background
In order to process natural language data and apply computational techniques to it one must first generate an adequate representation. One way to achieve this is by representing each word in the corpus as a vector of arbitrary length. Together these vectors form a space and the goal is to construct them in such a way that semantically similar words have similar vector representations. We know that our model is good if the distances between vectors reflect the semantic relationship of the words they represent.

The use of embeddings to model natural language data is a critical component for many tasks in NLP; however, the vast majority of research has focused on generating embeddings for English. In this project we apply word2vec to generate an embedding model for Latin. We chose Latin because of its distinct linguistic properties as well as its low-resource and historical characteristics. In the project we perform all the steps necessary to create a word embedding model from corpus selection/creation to training, to evaluation.


