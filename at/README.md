# Answer Triggering

Answer triggering is a question answering task that given a question, it finds sentences within a provided document that contain the answer context.
In answer triggering, the provided document may or may not contain sentences including the answer text, which is not the case for answer sentence selection where at least one sentence in the provided document always includes the answer context.
Thus, answer triggering is more challenging because it cannot be approached by simply ranking candidate sentences.

## Data for Analysis

JSON files, `selqa-at-(train|dev|test).json` are provided for analysis: 

* `question`: the question.
* `article`: the Wikipedia article related to this question.
* `section`: the section in the Wikipedia article related to this question.
* `topic`: the topic of this question, where the topics are *MUSIC*, *TV*, *TRAVEL*, *ART*, *SPORT*, *COUNTRY*, *MOVIES*, *HISTORICAL EVENTS*, *SCIENCE*, *FOOD*.
* `q_types`: the types of this question, where the types are *what*, *why*, *when*, *who*, *where*, and *how*.  If empty, none of the predefined types are found in this question.
* `is_paraphrase`: *True* if this question is a paragraph of some other question; otherwise, *False*.
* `candidate_list`: the list of 5 candidate sections:
  * `article`: the title of the candidate article.
  * `section`: the section of the candidate article.
  * `candidates`: the list of sentences in this candidate section.
  * `answers`: the indices of the candidates containing the answer context of this question (can be empty).

## Data for Experiments

TSV files, `selqa-at-(train|dev|test).tsv`, are provided for experiments, where each column gives:

* `0`: a question where all tokens are separated.
* `1`: a candidate of the question where all tokens are separated.
* `2`: the label where `0` implies no answer to the question is found in this candidate and `1` implies the answer is found. 