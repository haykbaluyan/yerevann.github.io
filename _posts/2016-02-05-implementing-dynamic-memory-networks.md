---
layout: post
title: Implementing Dynamic memory networks
tags:
- Recurrent neural networks
- Natural language processing
- draft
---

The Allen Institute for Artificial Intelligence has organized a 4 month [contest](https://www.kaggle.com/c/the-allen-ai-science-challenge) in Kaggle on question answering. The aim is to create a system which can correctly answer the questions from the 8th grade science exams of US schools (biology, chemistry, physics etc.). DeepHack Lab organized a [scientific school + hackathon](http://qa.deephack.me/) devoted to this contest in Moscow. Our team decided to use this opportunity to explore the deep learning techniques on question answering (although they seem to be far behind traditional systems). We tried to implement the Dynamic memory networks described [in a paper by A. Kumar et al.](http://arxiv.org/abs/1506.07285). Here we report some preliminary results. In the next blog post we will describe the techniques we used to get to top 5% in the contest.

<!--more-->

## Contents
{:.no_toc}
* TOC
{:toc}

## bAbI tasks

The questions of this contest are quite hard, they not only require lots of knowledge in natural sciences, but also abilities to make inferences, generalize the concepts, apply the general ideas to the examples and so on. The methods based on deep learning do not seem to be mature enough to handle all of these difficulties. On the other hand these questions have 4 answer candidates. That's why, as was noted by [Dr. Vorontsov](https://www.youtube.com/watch?v=lM2-Mi-2egM), simple search engine indexed on lots of documents will perform better as a question answering system than any "intelligent" system. 

But there is already some work on creating question answering / reasoning systems using neural approaches. As another lecturer of the DeepHack event, [Tomas Mikolov](https://www.youtube.com/watch?v=gi4Zf59_IcU), told us, we should start from easy, even synthetic questions and try to gradually increase the difficulty. This roadmap towards building intelligent question answering systems is described in [a paper](http://arxiv.org/abs/1502.05698) by Facebook researchers Weston, Bordes, Chopra, Rush, Merriënboer and Mikolov, where the authors introduce a benchmark of toy questions called [bAbI tasks](http://fb.ai/babi) which test several basic reasoning capabilities of a QA system. 

Questions in the bAbI dataset are grouped into 20 types, each of them has 1000 samples for training and another 1000 samples for testing. A system is said to have passed a given task, if it correctly answers at least 95% of the questions in the test set. There is also a version with 10K samples, but as Mikolov told during the lecture, deep learning is not necessarily about large datasets, and in this setting it is more interesting to see if the systems can learn answering questions by looking at a few training samples. 

|![some of the bAbI tasks](/public/2016-02-06/babi1.png "some of the bAbI tasks") |
| --- |
|![some of the bAbI tasks](/public/2016-02-06/babi2.png "some of the bAbI tasks") |
| --- |
| Some of the bAbI tasks. More examples can be found in the [paper](http://arxiv.org/pdf/1502.05698v10.pdf). | 


## Memory networks

bAbI tasks were first evaluated on an LSTM-based system, which achieve 50% performance on average and do not pass any task. Then the authors of the paper try [Memory Networks](http://arxiv.org/abs/1410.3916) by Weston et al. It is a recurrent network which has a long-term memory component where it can learn to write some data (the input sentences) and read them later. 

bAbI tasks include not only the answers to the questions but also the numbers of those sentences which help answer the question. This information is taken into account when training MemNN, they not only get the correct answers but also an information about which input sentences affect the answer. Under this so called _strongly supervised_ setting "plain" Memory networks pass 7 of the 20 tasks. Then the authors apply some modifications to them and pass 16 tasks.

We are mostly interested in _weakly supervised_ setting, because the additional information on important sentences is not available in many real scenarios. This was investigated in a paper by Sukhbaatar, Szlam, Weston and Fergus (from New York University and Facebook AI Research) where they introduce [End-to-end memory networks](http://arxiv.org/abs/1503.08895) (MemN2N). They investigate many different configurations of these systems and the best version passes 9 tasks out of 20. Facebook's MemN2N repository on GitHub lists [some implementations of MemN2N](https://github.com/facebook/MemNN).

## Dynamic memory networks



## Next steps

Overfitting.

Answer choices.

Evaluate on MCTest.




All related files are in our [Github repository](https://github.com/YerevaNN/char-rnn-constitution).