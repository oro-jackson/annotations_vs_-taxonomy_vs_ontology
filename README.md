# Annotation vs Taxonomy vs Ontology: Retrieval Impact Study

> A notebook-first benchmark showing what structured knowledge actually buys in retrieval: **annotation** for governance, **taxonomy** for structured recall, and **ontology** for grounded LLM expansion.

## Why this repo exists

Search and RAG teams often ask the same question:

> If we tag documents with entities, organize those entities into a hierarchy, and connect them with domain relationships, which layer actually improves retrieval quality?

This repository turns that question into a controlled benchmark.

It compares:

* **Annotation**: flat entity tags linked to MeSH concepts.
* **Taxonomy**: MeSH `is-a` hierarchy / ancestor expansion.
* **Ontology**: typed MeSH relations such as pharmacological action and see-also links.
* **Dense retrieval**: semantic retrieval using GTE embeddings.
* **LLM query expansion**: Qwen-based query expansion, including ontology-grounded expansion.
* **Hybrid retrieval**: fusion of semantic retrieval and ontology-grounded LLM expansion.

The main artifact is:

```text
annotation_vs_taxonomy_ontology.ipynb
```

## Key findings

1. **Annotation is table stakes, not a search engine.**
   Flat entity tagging gives governance and analytics value, but concept-overlap retrieval is far weaker than semantic retrieval.

2. **Taxonomy is the first real structured-retrieval win.**
   Adding `is-a` hierarchy improves standalone structured Recall@10 by roughly **14%** over flat annotation.

3. **More structure is not automatically better.**
   Naive ontology expansion can over-broaden queries and give back some of taxonomy's gains.

4. **A strong embedder is hard to beat on raw Recall@10.**
   Dense GTE remains the best standalone retriever on raw top-10 recall.

5. **Ontology is most valuable as an LLM grounding layer.**
   Ontology-grounded LLM expansion plus dense retrieval gives the strongest overall ranking quality.


