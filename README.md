# CS421 Project 2

## Abstract:
In this project I trained a 'python2vec' machine learning model using the gensim Word2Vec implementation. The goal was to approximate the Code2Vec model presented in [this paper](https://doi.org/10.1145/3291636) without using path contexts derived from abstract syntax trees to 'vectorize' code. The training data was python code gathered from eight open-source repositories. The code was cleaned so that comments were removed and tokens lowercased.

## Results:
### Similarity of top 50 identifiers:
The similarity of the 50 most common identifiers in the data set was computed using the trained Word2Vec (Python2Vec) model. Results are available in `most_similar_identifiers.csv`. This table presents the ten pairs with the highest similarity, duplicate entries (c=b and b=c, etc.) have been removed:

Identifier | Most Similar | Similarity
-|-|-
c | b | 0.7712486
x | y | 0.734981
a | b | 0.72498536
df | result | 0.6224475
index | idx | 0.6162908
dataframe | series | 0.6149798
expected | result | 0.5809328
arr | result | 0.5689963
res | result | 0.55125296
int | dtype | 0.5473172

## Discussion:
The top three results are all pairs of single-character identifiers: a, b, c, x, and y. There is a significant margin between these pairs and subsequent data. There could be a number of causes for this. One is that these identifiers will frequently appear close to each other (a function which uses variable c likely also uses b). Another is that the meaning of the variables (excepting x and y) is often very similar, in most cases c and b could be swapped without effecting readability.

## Extensions:
As my first extension I wrote code to automatically download all of the source code files for scanning using GitPython in `scrape-repositories.ipynb`. As my second extension I completed the optional steps after 7 in the instructions and found the most frequent identifiers in the source code and then had the trained model compute the similarity of the top 50.