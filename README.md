Download Link: https://assignmentchef.com/product/solved-comp551-assignment-3-sentiment-classification
<br>
In this assignment, we will design a sentiment classifier for classifying the sentiment of the reviews. This is a Natural Language Processing (NLP) task where the input is a natural language text and output is the sentiment label. We will consider two different review datasets: yelp reviews for restaurants and IMDB reviews for movies.

yelp dataset

The Yelp dataset consists of 7000 reviews in the training set, 1000 reviews in the validation set, and 2000 reviews in the test set. This is a 5 class problem where each review is classified into one of the five ratings with rating-5 being the best score and rating-1 being the worst score.

IMDB dataset

IMDB dataset consists of 15000 reviews in training set, 10000 reviews in validation set, and 25000 reviews in test set. This is a 2 class problem with class 1 being positive sentiment and class 0 being negative sentiment.

<ol>

 <li>Most of the algorithms described in the class expects input as a vector. However, thereviews are natural language text of varying number of words. So the first step would be to convert this varying length movie review to a fixed length vector representation. We will consider two different ways of vectorizing the natural language text: binary bag-of-words representation and frequency bag-of-words representation (as explained in the end of the assignment). Convert both the datasets into both these representations and turn in the converted datasets. Instruction for dataset format is given in the end of the assignment (do not include the dataset in the printed report).</li>

 <li>For this question, we will focus on the yelp dataset with binary bag-of-words representation. We will use the F1-measure as the evaluation metric for the entire assignment. As a baseline, report the performance of the random classifier (a classifier which classifies a review into an uniformly random class) and the majority-class classifier (a classifier which computes the majority class in the training set and classifies all test instances as that majority class). Now train Naive Bayes, Decision Trees, and Linear SVM for this task. You should do a thorough hyper-parameter tuning by using the given validation set. In the report, you should mention the list of hyper-parameters you considered for each classifier, the range of the individual hyper-parameters and the best value for this hyper-parameters chosen based on the validation set performance<a href="#_ftn1" name="_ftnref1"><sup>[1]</sup></a>. Report training, validation, and test F1-measure for all the classifiers (with best hyper-parameter configuration). Comment about the performance of different classifiers. Note that you should use the appropriate naive Bayes classifier for binary input features (also called Bernoulli naive Bayes)’.</li>

 <li>Repeat question 2 but with frequency bag-of-words representation. Compare the performance with the binary bag-of-words based classifiers. Do you see a huge improvement? Note that you should use Gaussian Naive Bayes in this scenario since the input is a real vector.</li>

 <li>Now repeat questions 2 and 3 but with IMDB dataset. Note that the IMDB dataset is abalanced dataset. Hence majority-class classifier doesn’t make sense for this dataset, and you can omit it for this question. Do your observations about the relative performance of the classifiers change as you change the dataset? Comment about it.</li>

</ol>

<h2>Instruction for binary bag-of-words representation</h2>

<ol>

 <li>First step is to construct the word vocabulary for a dataset. Given a dataset, wewill only consider the training set and enumerate all unique words in the training set reviews<a href="#_ftn2" name="_ftnref2"><sup>[2]</sup></a>. To do this, we should do a bit of pre-processing to the raw text. For this assignment, we will do only 2 pre-processing steps: removal of punctuation, and lower-casing the words. For example, <em>(How old are you?) </em>would become <em>(how old are you)</em>.</li>

 <li>Once you have the vocabulary, count the frequency of each word in the training setand sort the words in the vocabulary based on frequency (in descending order). Now pick top 10,000 words in the vocabulary and ignore the rest of the words. These 10,000 words will form the feature set for our classification process.</li>

 <li>For any example to be classified, generate a 10,000 dimensional feature vector as follows: for each of the top 10,000 words, there is one corresponding dimension in the feature vector that is 1 if the example contains the word, and 0 otherwise. Make sure to use the same pre-processing steps as before for validation and test reviews.</li>

</ol>

<h2>Instruction for frequency bag-of-words representation</h2>

<ol>

 <li>Follow steps 1-2 of the instructions for the binary bag-of-words.</li>

 <li>Now, for each of the 10,000 words, the corresponding feature is the frequency of occurrence of that word in the given review. You can calculate this by summing the occurrences of words in a review into a histogram, and than divide by the sum of occurrences of all 10,000 words so that the vector for each example sums to 1.</li>

</ol>

<a href="#_ftnref1" name="_ftn1">[1]</a> Note that it is a good practise to discuss about your hyper-parameter tuning in any report or paper. Whenever you report the performance of an algorithm with hyper-parameters, you should mention all the hyper-parameters, the range of values you considered for each hyper-parameter and the final values you chose for the hyper-parameters to compute the test performance.

<a href="#_ftnref2" name="_ftn2">[2]</a> Think why should we not include validation and test set in the vocabulary construction process. <sup>3</sup>You can igmore words that are not in the vocabulary.