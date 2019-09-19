---
layout: post
title:  "Text Generation from Knowledge Graphs with Graph Transformers"
date:   2019-09-19 19:21:59
author: Sungwon Lyu
categories: studies
tags: deep-learning natural-language-processing knowledge-graph
---
## WHY? 
Though knowledge graph can capture the essence of corpus, generating sentences based on the graph is difficult task. This paper tried to generate texts(paper abstracts) from KG in science(AI) domain. 

## Graph Extraction
![image](/assets/images/graphwriter1.png){: .centered-product}
Grph extration is a task to extract a graph from text corpus. This paper used SciIE system to extract a graph from 40k science paper titles and abstracts. Note that this paper used entity type information instead of entity itself(for example, event detection is used as task1). Also, the system provided co-reference annotations and 7 kinds of relations. 

## WHAT?
![image](/assets/images/graphwriter2.png){: .centered-product width="50%"}
This paper encodes graph information by reconstructing bipatite graphs and applying Graph Attention Network(GAT). A graph is represented with V and E where V is a list of entities, relations, and a global node and E is an adjacency matrix.
![image](/assets/images/graphwriter3.png){: .centered-product width="75%"}
Titles are encoded with BiRNN. Encoded graphs and titles are attended while the decoder generate words or copy from the input. 

## So?
![image](/assets/images/graphwriter4.png){: .head-image}
GraphWriter tends to generate more natural(in BLEU score) abstracts compared to other benchmarks.

## Review
Although the domain is restricted to specific area and human evaluation is not that great, it is meaningful to generate descent texts using the knowledge graph. Especially, adopting copying mechanism was clever. 

[Koncel-Kedziorski, Rik, et al. "Text Generation from Knowledge Graphs with Graph Transformers." arXiv preprint arXiv:1904.02342 (2019).](https://arxiv.org/abs/1904.02342)

