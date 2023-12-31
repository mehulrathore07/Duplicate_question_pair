# Duplicate_question_pair

Over 100 million people visit Quora every month, so it's no surprise that many people ask similarly worded questions. Multiple questions with the same intent can cause seekers to spend more time finding the best answer to their question, and make writers feel they need to answer multiple versions of the same question. Quora values canonical questions because they provide a better experience to active seekers and writers, and offer more value to both of these groups in the long term. so main aim of project is that predicting whether pair of questions are similar or not. This could be useful to instantly provide answers to questions that have already been answered. Credits: Kaggle

# Problem Statement :
Identify which questions asked on Quora are duplicates of questions that have already been asked.

# Real world/Business Objectives and Constraints :
The cost of a mis-classification can be very high.
You would want a probability of a pair of questions to be duplicates so that you can choose any threshold of choice.
No strict latency concerns.
Interpretability is partially important.

# Data Overview:
Train.csv contains 5 columns : qid1, qid2, question1, question2, is_duplicate.
Total we have 404290 entries. 
Splitted data into train and test with 80% and 20%.

# Feature Extraction:
# Basic Features - Extracted some features before cleaning of data as below.
q1len = Length of q1
q2len = Length of q2
q1_n_words = Number of words in Question 1
q2_n_words = Number of words in Question 2
word_Common = (Number of common unique words in Question 1 and Question 2)
word_Total =(Total num of words in Question 1 + Total num of words in Question 2)
word_share = (word_common)/(word_Total)



# Advanced Features -
Did some preprocessing of texts and extracted some other features. i am giving some definitions which are used below. Token- You get a token by splitting sentence by space , Stop_Word - stop words as per NLTK, Word -A token that is not a stop_word.

cwc_min = common_word_count / (min(len(q1_words), len(q2_words))
cwc_max = common_word_count / (max(len(q1_words), len(q2_words))
csc_min = common_stop_count / (min(len(q1_stops), len(q2_stops))
csc_max = common_stop_count / (max(len(q1_stops), len(q2_stops))
ctc_min = common_token_count / (min(len(q1_tokens), len(q2_tokens))
ctc_max = common_token_count / (max(len(q1_tokens), len(q2_tokens))
last_word_eq = Check if Last word of both questions is equal or not (int(q1_tokens[-1] == q2_tokens[-1]))
first_word_eq = Check if First word of both questions is equal or not (int(q1_tokens[0] == q2_tokens[0]) )
abs_len_diff = abs(len(q1_tokens) - len(q2_tokens))
mean_len = (len(q1_tokens) + len(q2_tokens))/2
fuzz_ratio = How much percentage these two strings are similar, measured with edit distance.
fuzz_partial_ratio = if two strings are of noticeably different lengths, we are getting the score of the best matching lowest length substring.
token_sort_ratio = sorting the tokens in string and then scoring fuzz_ratio.
longest_substr_ratio = len(longest common substring) / (min(len(q1_tokens), len(q2_tokens))


# References:

https://www.kaggle.com/c/quora-question-pairs
https://www.kaggle.com/c/quora-question-pairs/discussion
