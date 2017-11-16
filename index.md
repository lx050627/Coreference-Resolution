# The Summary of *"Easy Victories  and Uphill Battles in Coreference Resolution"*
#### EMNLP 2013

The papers presents a learning-based, mention-synchronous coreference system which utilizes the simplest features to address various aspects regarding coreference resolution. Although only surface-level document characteristics and superficial syntactic infomation are used, surprisingly, the system is able to achieve high performance, which is referred to as *Easy Victories* in the paper title. However, on the other hand, the behaviors of the system in capturing semantic information is not satisfactory because of the complex structural property.Therefore, semantic inforamtion extraction is considered as *Uphill Battles*.

## Mention-Synchronous Framework
### Coreference Model
The mention-synchronous framework indicates that we use features to decide whether single mentions are anaphorics and pairs of mentions or not. So, the initial job is to indentify the set of mentions from text annotated with parses as well as named entity tags.

Afterwards, in order to choose at most one antecedent for each mention or determine it is the beginning of a new cluster, a log-linear model is adopted. 

As is depicted in Figure 1, the mention-ranking architecture serves as the backbone of this coreference system.
![figure1](figure1.png)<center>Figure 1 The basic structure of coreference model</center >

We extracted *n* mentions from a document *x*. The i th mention has an association random variable a<sub>i</sub> taking values from {1,...,i-1,NEW}.This variable has i possible antecedence choices:link to one of the i-1 preceding mentions or just begin a new cluster. The sequence of a<sub>i</sub> can be regarded as a unique set of coreference chains, serving as the output of this system.

The system adopts a log-linear model of the condtional distribution P(a|x) as follows:
![formula1](formula1.png)
where **f**(i,a<sub>i</sub>,x) is a feature function that examines the coreference decision a<sub>i</sub> for mention *i* with document context *x*.

### Inference with Model
The inference process is efficient. We can obtain the result by maximizing logP(a|x), which decomposes linearly over each mention.
  
### Learning of Model
We optimize the conditional log-likelihood augmented with a parameterized loss function.C<sup>\*</sup> represents a gold clustering defined over gold mentions.Given *t* training examples of the form (x<sub>k</sub>,&nbsp;C<sup>\*</sup><sub>k</sub>),the likelihood function can be written as follows:
![formula2](formula2.png)
where <img src="formula3.png" width = "200" height = "30" align=center /> withl(a,C<sup>\*</sup>) being a loss function. This final parameterized loss function is a weighted sum of the counts of three error types（false anaphor error, false new error, wrong link eror).

## Easy Victories from Surface Features
The surface feature set only includes the following properties of mentions and mention pairs: 
 
* Mention type（nominal, proper, or pronominal)
* The complete string of a mention
* The semantic head of a mention
* The first word and last word of each mention
* The word immediately preceding and the word immediately following a mention
* Mention length
* Two distance measures between mentions

In addition, the features consist of two conjunctions of each feature.
Even though these features seem rather superficial and simple, they are adequate enough to yield a satisfying coreference result. The underlying reason is that they can capture implicitly the linguistic phenomena without the assitance of heuristic-driven features. Notably, these kinds of data-driven features are also able to model more patterns in the data by achieving finer level of granularity.  

To provide more insights into data-driven features and heuristic-driven features, the paper exhibits the results of ablation experiments.It is found that none of heuristic-driven features make substantial contribution on top of the data-driven features. To sum up, these simple features can help us gain victories on syntax-related subtask.

## Uphill Battles on Semantics
   The features which are effective in capturing syntactic phenomena can not handle semantic phenomena well. Even a combination of serveral shallow semantic features cannot succeed in modelling semantics.

