# MSMARCO
A Family of datasets built using technology and Data from Microsoft's Bing.

> MS MARCO: A Human Generated MAchine Reading COmprehension Dataset
> Paper URL : https://arxiv.org/abs/1611.09268

MS MARCO(Microsoft Machine Reading Comprehension) is a large scale dataset focused on machine reading comprehension, question answering, and passage ranking, Keyphrase Extraction, and Conversational Search Studies, or what the community thinks would be useful. 

First released at [NIPS 2016](https://arxiv.org/pdf/1611.09268.pdf), the current dataset has 1,010,916 unique real queries that were generated by sampling and anonymizing Bing usage logs. The dataset started off focusing on QnA but has since evolved to focus on any problem related to search. For task specifics please explore some of the tasks that have been built out of the dataset. If you think there is a relevant task we have missed please open an issue explaining your ideas?  

For more information about [TREC 2019 Deep Learning](https://github.com/microsoft/TREC-2019-Deep-Learning)

For more information about [Q&A](https://github.com/microsoft/MSMARCO-Question-Answering)

For more information about [Ranking](https://github.com/microsoft/MSMARCO-Passage-Ranking)

For more information about [Keyphrase Extraction](https://github.com/microsoft/MSMARCO-OpenKP)

For more information about [Conversational Search](https://github.com/microsoft/MSMARCO-Conversational-Search)

For more information about [Polite Crawling](https://github.com/microsoft/MSMARCO-Optimal-Freshness-Crawl-Under-Politeness-Constraints)


## Dataset Generation, Data Format, And Statistics
The MSMARCO dataset was generated by leveraging the Question Answering capabilities of Bing. For each query, Bing retrieved the 10 most relevant context passages. These passages are generated independelty of any query. Passages are generated by scanning over full documents and extrating all possible passages. Only the top N passages are kept in an index. What this means is it is possible that context passages have high overlaps in their ngrams. Using this passage index, for each query the top 10 most relevant passages were retrieved. All unique passages were unioned to produce the Passage ranking dataset. 

What is the difference between MSMARCO and other MRC datasets? We believe the advantages that are special to MSMARCO are:
- Real questions: All questions have been sample from real anonymized bing queries.
- Real Documents: Most Url's that we have source the passages from contain the full web documents. These can be used as extra contextual information to improve systems or be used to compete in our expert task.
- Human Generated Answers: All questions have an answer written by a human. If there was no answer in the passages the judge read they have written 'No Answer Present.'
- Human Generated Well-Formed: Some questions contain extra human evaluation to create well formed answers that could be used by intelligent agents like Cortana, Siri, Google Assistant, and Alexa.
- Dataset Size: At over 1 million queries the dataset is large enough to train the most complex systems and also sample the data for specific applications.
 
## Download the Dataset
To Download the MSMARCO Dataset please navigate to [msmarco.org](http://www.msmarco.org/dataset.aspx) and agree to our Terms and Conditions. If there is some data you think we are missing and would be useful please open an issue. 

### Tasks
In an effort to produce a dataset that can continue to be challanging and rewarding we have broken down the MSMARCO dataset into tasks of varying difficulty.

##### Question Answering
Given a query q and a set of passages P = p1, p2, p3,... p10 a successful Machine Reading Comprehension system is expected to read and understand both the questions and passages. Then, the system must accuratley decide if the passages provide addequate information to answer the query since not all queries have an answer. If there is not enough information, the system should response 'No Answer Present.'. If there is enough information the system should create a quality answer. The target of the answer a should be as close as possible to the human generated refrence answers RA= ra1,ra2,...,ram. Evaluation will be done using ROUGE-L, BLEU-1, and a F1 score computed by measuring how well a system can know to answer questions or not. Questions that have the do not have an answer will not be used to calculate ROUGE-L or BLEU-1.

##### Natural Language Generation
Given a query q and a set of passages P = p1, p2, p3,... p10 a successful Machine Reading Comprehension system is expected to read and understand both the questions and passages. For this task all queries have an answer so systems do not need to understand No Answer Queries. Using the relevant passages a successful system should produce a candidate answer that should be as close as possible to the human generated well formed refrence answers RA= wfra1,wfra2,...,wfram. Evaluation will be done using ROUGE-L and BLEU-1.

##### Passage RerankingTask
Given a query q and a the 1000 most relevant passages P = p1, p2, p3,... p1000, as retrieved by BM25 a succeful system is expected to rerank the most relevant passage as high as possible. For this task not all 1000 relevant items have a human labeled relevant passage. Evaluation will be done using [MRR](https://en.wikipedia.org/wiki/Mean_reciprocal_rank)

##### End2End Passage Ranking Task
Given a query q and a corpus of passages P = p1, p2, p3,... pn, a succeful system is expected to provide 10 passages with the goal of providing the most relevant results. Evaluation will be done using [MRR](https://en.wikipedia.org/wiki/Mean_reciprocal_rank)

##### KeyPhrase Extraction
Given a document D represented as text and cleanbody text a successful system is expected to provide 5 potential document keyphrases ranked by importance.

##### Conversational Search
Given a sequence of queries Q = q1,...,qn-1 predict query qn

##### V1 MSMARCO Dataset
The first iteration of the MSMARCO dataset was 100,000 queries and ran from Dec 2016-March 2018. The full data can be found below
[Train](https://msmarco.blob.core.windows.net/msmsarcov1/train_v1.1.json.gz), [Dev](https://msmarco.blob.core.windows.net/msmsarcov1/dev_v1.1.json.gz), [Eval](https://msmarco.blob.core.windows.net/msmsarcov1/test_hidden_v1.1.json), [Evaluation Scripts](https://msmarco.blob.core.windows.net/msmsarcov1/ms_marco_eval_old.tar.gz)

### Feedback
MS MARCO has been designed not as a dataset to be beat but an effort to establish a large community of researchers working on Machine Comprehension. If you have any thoughts on things we can do better, ideas for how to use datasets or general question please dont hesitate to [reach out and ask](mailto:ms-marco@microsoft.com?subject=MS MARCO Feedback).

## Author
Daniel Campos, Microsoft (dacamp@microsoft.com)

## License
This project is licensed under the MIT License - see the [LICENSE.md](LICENSE.md) file for details
