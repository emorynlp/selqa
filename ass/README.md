# Answer Sentence Selection

Answer sentence selection is a question answering task that given a question, it selects sentences within a provided document that contain the answer context.

* `question`: the question.
* `article`: the Wikipedia article related to this question.
* `section`: the section in the Wikipedia article related to this question.
* `candidates`: the list of sentences in the related section.
* `answers`: the indices of the candidates containing the answer context of this question.
* `is_paraphrase`: `True` if this question is a paragraph of some other question; otherwise, `False`.
* `topic`: the topic of this question, where the topics are *MUSIC*, *TV*, *TRAVEL*, *ART*, *SPORT*, *COUNTRY*, *MOVIES*, *HISTORICAL EVENTS*, *SCIENCE*, *FOOD*.
* `q_types`: the types of this question, where the types are *what*, *why*, *when*, *who*, *where*, and *how*.  If empty, none of the predefined types are found in this question.








The package contains three splits: train, development and test sets.
For each `[split]`, the following files can be found:

- *SelQA-ass-[split].txt* - a tab separated text file that contains samples for `[split]` set. Each line can be extracted to three elements:
  * `Question text`
  * `Sentence text`
  * `Label`

 where `Label` denotes whether this `Sentence text` provides the answer for the `Question text` (can be `0` or `1`).
  
- *SelQA-ass-[split]_raw.pickle* - a pickle file that contains raw data based on which the *SelQA-ass-[split].txt* has been created. Each pickle is a list of dictionaries, where each dictionary is a single question entity. In the dictionary, the following elements can be found:
  * `question` - question text
  * `is_paraphrase` - whether the `question` is a paraphrase of other question
  * `type` - genera of the `question` (generas: `set(['MUSIC', 'TV', 'TRAVEL', 'ART', 'SPORT', 'COUNTRY', 'MOVIES', 'HISTORICAL EVENTS', 'SCIENCE', 'FOOD'])`)
  * `article` - name of the Wikipedia article the `question` is about
  * `section` - name of the Wikipedia section the `question` is about
  * `sentences` - set of sentences (simply sentences of the given `section`) for this `question`
  * `candidates` - set of sentence indexes that provide the answer for given `question`.

- *SelQA-ass-[split]_analysis.pickle* - a pickle file contains useful information that might be used for analysis such as question length, section length etc. Each pickle is a list of dictionaries, where each dictionary is a single question entity. In the dictionary, the following elements can be found:
  * `question` - question text
  * `is_paraphrase` - whether the `question` is a paraphrase of other question
  * `genera` - genera of the `question`
  * `q_len` - question length (a number of word tokens in a `question`)
  * `s_len` - section length (a number of `sentences` in a `section`)
  * `q_types` - set of question types (types: `set(['what', 'why', 'when', 'who', 'where', 'how'])`. If empty, none of recognized types are found in the question.)

- *SelQA-ass-[split]_dep.txt* - a text file that contains raw dependency trees of all samples in each `[split]`. __Note__: First question's tree is followed by the trees of its sentences, which is follwed by the second question's tree, which is followed by the trees of its sentences etc...  
 We used [NLP4J](https://github.com/emorynlp/nlp4j) to parse the data.



## Answer Triggering


The package contains three splits: train, development and test sets.
For each `[split]`, the following files can be found:

- *SelQA-at-[split].txt* - a tab separated text file that contains samples for `[split]` set. Each line can be extracted to three elements:
  * `Question text`
  * `Sentence text`
  * `Label`

 where `Label` denotes whether this `Sentence text` provides the answer for the `Question text` (can be `0` or `1`).
  
- *SelQA-at-[split]_raw.pickle* - a pickle file that contains raw data based on which the *SelQA-ass-[split].txt* has been created. Each pickle is a list of dictionaries, where each dictionary is a single question entity. In the dictionary, the following elements can be found:
  * `question` - question text
  * `is_paraphrase` - whether the `question` is a paraphrase of other question
  * `type` - genera of the `question` (generas: `set(['MUSIC', 'TV', 'TRAVEL', 'ART', 'SPORT', 'COUNTRY', 'MOVIES', 'HISTORICAL EVENTS', 'SCIENCE', 'FOOD'])`)
  * `article` - name of the Wikipedia article the `question` is about
  * `section` - name of the Wikipedia section the `question` is about
  * `sections` - list of section entities (five for each question, this is what makes this task Answer Triggering)

 Each entity of `sections` contains the following elements:
  * `article` - name of the Wikipedia article this `section` entity is from
  * `section` - name of the Wikipedia section of this `section` entity
  * `sentences` - set of sentences of this `section` entity
  * `candidates` - set of sentence indexes that provide the answer for given `question` in this `section` entity

 Please note that this is Answer Triggering data set. It implies that the answer is not necessarily present among all the candidates from all five sections. Thus, some question will have all `candidates` empty for all five entities in `sections` list. In fact, the majority of questions (~60%) does not have corresponding candidates among all its sentences (more details on that in the paper).


- *SelQA-at-[split]_analysis.pickle* - a pickle file contains useful information that might be used for analysis such as question length, sections length etc. Each pickle is a list of dictionaries, where each dictionary is a single question entity. In the dictionary, the following elements can be found:
  * `question` - question text
  * `is_paraphrase` - whether the `question` is a paraphrase of other question
  * `is_answer` - whether the `question` has at least a single candidate among all its candidates
  * `genera` - genera of the `question`
  * `q_len` - question length (a number of word tokens in a `question`)
  * `s_len` - sections length (a total amount of all sentences in all five `sections`)
  * `q_types` - set of question types (types: `set(['what', 'why', 'when', 'who', 'where', 'how'])`. If empty, none of recognized types are found in the question.)

- *SelQA-at-[split]_dep.txt* - a text file that contains raw dependency trees of all samples in each `[split]`. __Note__: First question's tree is followed by the trees of its sentences, which is follwed by the second question's tree, which is followed by the trees of its sentences etc...  
 We used [NLP4J](https://github.com/emorynlp/nlp4j) to parse the data.


## Contact

* [Tomasz Jurczyk](https://github.com/tjurczyk)
* [Jinho D. Choi](https://github.com/jdchoi77)