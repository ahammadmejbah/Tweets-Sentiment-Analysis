<h1><code>Tweets Sentiment Analysis</code></h1>

***

# Working Process

<ol>
      <li>Representing <code>text as numerical data</code></li>
      <li>Reading a <code>text-based dataset</code> into pandas</li>
      <li><code>Vectorizing</code> our dataset</li>
      <li><code>Building and evaluating</code> a model</li>
      <li><code>Comparing</code> models</li>
      <li>Examining a model for <code>further insight</code></li>
      <li>Practicing this workflow on <code>another dataset</code></li>
      <li>Tuning the <code>vectorizer (discussion)</code></li>
</ol>


# Working Goals:
      
Throughout this notebook, we will mention an elevated overview of the fundamentals of natural language processing, which essentially entails combining machine learning techniques with text and using math and statistics to get that text in a format that the machine learning algorithms can understand. This notebook will be divided into three sections: the first section will provide an introduction to natural language processing, the second section will discuss natural language processing in more detail, and the third section will.


 From the [scikit-learn documentation](http://scikit-learn.org/stable/modules/feature_extraction.html#text-feature-extraction):

<h3>Features and samples are defined as follows:</h3>
<ol>
<li>Each individual token occurrence frequency (normalized or not) is treated as a <code>feature</code>.</li>
<li>The vector of all the token frequencies for a given document is considered a multivariate <code>sample</code>.</li>
</ol>

A <b><code>corpus of documents</code></b> can thus be represented by a matrix with <code>one row per document</code>and <b><code> one column per token</code></b> (e.g. word) occurring in the corpus.

We call <b><code>vectorization</code></b>  the general process of turning a collection of text documents into numerical feature vectors. This specific strategy (tokenization, counting and normalization) is called the <b><code>Bag of Words</code></b> or <b><code>Bag of n-grams</code></b> representation. Documents are described by word occurrences while completely ignoring the relative position information of the words in the document.



# Text Pre-processing approaches:

<ol>
      <li> Our main issue with our data is that it is all in text format (strings). The classification algorithms that we usally use need some sort of numerical feature vector in order to perform the classification task. There are actually many methods to convert a corpus to a vector format. The simplest is the bag-of-words approach, where each unique word in a text will be represented by one number.</li>
      <li>In this section we'll convert the raw messages (sequence of characters) into vectors (sequences of numbers).</li>
      
      <li> As a first step, let's write a function that will split a message into its individual words and return a list. We'll also remove very common words, ('the', 'a', etc..). To do this we will take advantage of the NLTK library. It's pretty much the standard library in Python for processing text and has a lot of useful features. We'll only use some of the basic ones here.</li>

      <li> Let's create a function that will process the string in the message column, then we can just use **apply()** in pandas do process all the text in the DataFrame.</li>

      <li> First removing punctuation. We can just take advantage of Python's built-in **string** library to get a quick list of all the possible punctuation</li>
      
 </ol>
 
 

 ``` python
 
import string
from nltk.corpus import stopwords

def text_process(mess):
    """
    Takes in a string of text, then performs the following:
    1. Remove all punctuation
    2. Remove all stopwords
    3. Returns a list of the cleaned text
    """
    STOPWORDS = stopwords.words('english') + ['u', 'ü', 'ur', '4', '2', 'im', 'dont', 'doin', 'ure']
    # Check characters to see if they are in punctuation
    nopunc = [char for char in mess if char not in string.punctuation]

    # Join the characters again to form the string.
    nopunc = ''.join(nopunc)
    
    # Now just remove any stopwords
    return ' '.join([word for word in nopunc.split() if word.lower() not in STOPWORDS])
 
 ```
