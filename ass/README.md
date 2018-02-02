# Answer Sentence Selection

Answer sentence selection is a question answering task that given a question, it selects sentences within a provided document that contain the answer context.

## Data for Analysis

JSON files, `selqa-ass-(train|dev|test).json` are provided for analysis: 

* `question`: the question.
* `article`: the Wikipedia article related to this question.
* `section`: the section in the Wikipedia article related to this question.
* `topic`: the topic of this question, where the topics are *MUSIC*, *TV*, *TRAVEL*, *ART*, *SPORT*, *COUNTRY*, *MOVIES*, *HISTORICAL EVENTS*, *SCIENCE*, *FOOD*.
* `q_types`: the types of this question, where the types are *what*, *why*, *when*, *who*, *where*, and *how*.  If empty, none of the predefined types are found in this question.
* `is_paraphrase`: *True* if this question is a paragraph of some other question; otherwise, *False*.
* `candidates`: the list of sentences in the related section.
* `answers`: the indices of the candidates containing the answer context of this question.

## Data for Experiments

TSV files, `selqa-ass-(train|dev|test).tsv`, are provided for experiments, where each column gives:

* `0`: a question where all tokens are separated.
* `1`: a candidate of the question where all tokens are separated.
* `2`: the label where `0` implies no answer to the question is found in this candidate and `1` implies the answer is found.
