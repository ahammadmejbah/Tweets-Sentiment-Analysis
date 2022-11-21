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
