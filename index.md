# The Summary of *"Easy Victories  and Uphill Battles in Coreference Resolution"*
#####EMNLP 2013#####

The papers presents a learning-based, mention-synchronous coreference system which utilizes the simplest features to address various aspects regarding coreference resolution. Although only surface-level document characteristics and superficial syntactic infomation are used, surprisingly, the system is able to achieve high performance, which is referred to as *Easy Victories* in the paper title. However, on the other hand, the behaviors of the system in capturing semantic information is not satisfactory because of the complex structural property.Therefore, semantic inforamtion extraction is considered as *Uphill Battles*.

## Mention-Synchronous Framework 
The mention-synchronous framework indicates that we use features to decide whether single mentions are anaphorics and pairs of mentions or not. So, the initial job is to indentify the set of mentions from text annotated with parses as well as named entity tags.

Afterwards, in order to choose at most one antecedent for each mention or determine it is the beginning of a new cluster, a log-linear model is adopted. 

As is depicted in Figure 1, the mention-ranking architecture serves as the backbone of this coreference system.
![figure1](figure1.png)<center>Figure 1 The basic structure of coreference model</center >

We extracted *n* mentions from a document *x*. The i th mention has an association random variable a<sub>i</sub> taking values from {1,...,i-1,NEW}.This variable has i possible antecedence choices:link to one of the i-1 preceding mentions or just begin a new cluster. The sequence of a<sub>i</sub> can be regarded as a unique set of coreference chains,serving as the output of this system.
  
  
  
  
    
<img src="http://chart.googleapis.com/chart?cht=tx&chl=\Large x=\frac{-b\pm\sqrt{b^2-4ac}}{2a}" style="border:none;">

		
