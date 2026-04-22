---
layout: post
title: A comparison between 'traditional' and hybrid (graph) RAG applications
date: 2026-04-15
---

I've recently come into some unscheduled downtime and have been trying to keep busy.
One of the things I've been exploring is LLMs and generative applications. So, I took a short course targeted at developers and while exploring the material, I stumbled upon a few tutorials showing a way to enhance RAG output using knowledge graphs.
I'm writing this post, and maybe a few others to follow, to document my process and notes as I try to replicate it.

Components and structure

RAG in this context stands for Retrieval Augmented Generation. 

It is a process of enhancing the output generated from a large language model by providing it with relevant context outside of its training data along with your query/prompt.

Typically you provide an llm with a snippet of text (query/prompt) that it completes (answers) based on its training data. In a RAG application, you also provide specific material (text, audio etc) that the llm references in addition to its training data when generating the response.

Ingestion
For a typical RAG application, the augmenting document is uploaded by a user and read by one of an ever increasing library. You then chunk it up and get a numerical/vector representation of each chunk called a vector embedding that you store in a vector store. This numerical representation allows you to search the data by similarity in an efficient way.

For a graph-RAG application however, you convert the document into a knowledge graph and generate vector embeddings from this graph. Alternatively, you can generate the vector embeddings the usual way as described above.

Querying
Next is finding the most relevant chunks to the query provided and supplying those to the llm for generation
most datastores come packaged with appropriate functionality to query the underlying data efficiently.