---
  title: "Haystack"
  description: "Production-ready NLP framework for building search pipelines, RAG systems, and LLM applications. Modular pipeline architecture with 100+ integrations (OpenAI, Cohere, Weaviate, Elasticsearch, Pinecone). Best for enterprise search, document Q&A, and complex multi-step RAG pipelines."
  skillName: "haystack"
  skillVersion: "1.0.0"
  skillAuthor: "Orchestra Research"
  skillLicense: "MIT"
  skillTags: ["RAG", "Haystack", "NLP", "Search Pipelines", "Document QA", "Enterprise Search", "Pipeline Architecture", "Deepset", "Production"]
  skillDeps: ["haystack-ai", "transformers", "sentence-transformers"]
  ---

  | | |
  |---|---|
  | **Version** | 1.0.0 |
  | **Author** | Orchestra Research |
  | **License** | MIT |
  | **Tags** | `RAG` `Haystack` `NLP` `Search Pipelines` `Document QA` `Enterprise Search` |
  | **Dependencies** | `haystack-ai` `transformers` `sentence-transformers` |


  # Haystack — Production NLP & RAG Pipelines

  deepset's modular framework for building search systems and RAG applications at production scale.

  ## When to use Haystack

  **Use Haystack when:**
  - Building production-grade search or Q&A systems
  - Complex multi-step pipelines (retrieve → rerank → generate)
  - Enterprise document Q&A over large corpora
  - Need extensive integrations (100+ document stores, LLMs, embedders)
  - Evaluation-driven RAG development

  **Metrics**:
  - **18,000+ GitHub stars**
  - **100+ integrations** (OpenAI, Cohere, Hugging Face, Elasticsearch, Weaviate, Pinecone)
  - **Production-battle-tested** at enterprise scale
  - Apache 2.0 license

  ## Quick start

  ```bash
  pip install haystack-ai
  # With OpenAI
  pip install haystack-ai openai
  # With local models
  pip install haystack-ai transformers sentence-transformers
  ```

  ### Basic RAG pipeline

  ```python
  from haystack import Pipeline, Document
  from haystack.document_stores.in_memory import InMemoryDocumentStore
  from haystack.components.retrievers import InMemoryBM25Retriever
  from haystack.components.generators import OpenAIGenerator
  from haystack.components.builders import PromptBuilder

  # 1. Set up document store
  store = InMemoryDocumentStore()
  store.write_documents([
      Document(content="Flash Attention reduces memory from O(N²) to O(N) by using tiling and recomputation."),
      Document(content="GRPO uses group-relative policy optimization for RL training of LLMs."),
      Document(content="LoRA adds low-rank matrices to frozen weights, reducing trainable parameters by 10,000x."),
  ])

  # 2. Build pipeline
  template = """Answer the question based on the context.
  Context: {% for doc in documents %}{{ doc.content }}{% endfor %}
  Question: {{ question }}"""

  pipeline = Pipeline()
  pipeline.add_component("retriever", InMemoryBM25Retriever(document_store=store))
  pipeline.add_component("prompt_builder", PromptBuilder(template=template))
  pipeline.add_component("llm", OpenAIGenerator(model="gpt-4o-mini"))

  pipeline.connect("retriever", "prompt_builder.documents")
  pipeline.connect("prompt_builder", "llm")

  # 3. Run
  result = pipeline.run({
      "retriever": {"query": "How does Flash Attention save memory?"},
      "prompt_builder": {"question": "How does Flash Attention save memory?"}
  })
  print(result["llm"]["replies"][0])
  ```

  ### Semantic search with embeddings

  ```python
  from haystack.components.embedders import SentenceTransformersDocumentEmbedder, SentenceTransformersTextEmbedder
  from haystack.components.retrievers.in_memory import InMemoryEmbeddingRetriever
  from haystack.document_stores.in_memory import InMemoryDocumentStore

  # Indexing pipeline
  indexing = Pipeline()
  indexing.add_component("embedder", SentenceTransformersDocumentEmbedder(
      model="sentence-transformers/all-MiniLM-L6-v2"
  ))
  indexing.add_component("writer", DocumentWriter(document_store=store))
  indexing.connect("embedder", "writer")

  indexing.run({"embedder": {"documents": documents}})

  # Query pipeline
  query_pipeline = Pipeline()
  query_pipeline.add_component("text_embedder", SentenceTransformersTextEmbedder(
      model="sentence-transformers/all-MiniLM-L6-v2"
  ))
  query_pipeline.add_component("retriever", InMemoryEmbeddingRetriever(document_store=store, top_k=5))
  query_pipeline.connect("text_embedder.embedding", "retriever.query_embedding")

  results = query_pipeline.run({"text_embedder": {"text": "attention mechanism memory optimization"}})
  ```

  ### Advanced: Hybrid retrieval + reranking

  ```python
  from haystack.components.rankers import TransformersSimilarityRanker
  from haystack.components.joiners import DocumentJoiner

  pipeline = Pipeline()
  pipeline.add_component("bm25_retriever", InMemoryBM25Retriever(document_store=store, top_k=10))
  pipeline.add_component("embedding_retriever", InMemoryEmbeddingRetriever(document_store=store, top_k=10))
  pipeline.add_component("joiner", DocumentJoiner(join_mode="reciprocal_rank_fusion"))
  pipeline.add_component("reranker", TransformersSimilarityRanker(model="cross-encoder/ms-marco-MiniLM-L-6-v2", top_k=5))
  pipeline.add_component("llm", OpenAIGenerator(model="gpt-4o"))

  pipeline.connect("bm25_retriever", "joiner")
  pipeline.connect("embedding_retriever", "joiner")
  pipeline.connect("joiner", "reranker")
  # ... connect to prompt builder and llm
  ```

  ### Pipeline evaluation

  ```python
  from haystack.evaluation import EvaluationRunResult
  from haystack.components.evaluators import ContextRelevanceEvaluator, FaithfulnessEvaluator

  evaluator = Pipeline()
  evaluator.add_component("context_relevance", ContextRelevanceEvaluator(api="openai"))
  evaluator.add_component("faithfulness", FaithfulnessEvaluator(api="openai"))

  results = evaluator.run({
      "context_relevance": {"questions": questions, "contexts": retrieved_docs},
      "faithfulness": {"questions": questions, "contexts": retrieved_docs, "responses": answers}
  })
  ```

  ## Serialization & deployment

  ```python
  import yaml

  # Save pipeline as YAML
  with open("pipeline.yaml", "w") as f:
      pipeline.dump(f)

  # Load and run
  with open("pipeline.yaml") as f:
      pipeline = Pipeline.load(f)

  # REST API with Hayhooks
  # pip install hayhooks
  # hayhooks run pipeline.yaml
  ```

  ## Common pitfalls

  - **Slow first run**: Embedding models download on first use (~500MB); cache with `HF_HOME`
  - **Pipeline connection errors**: Check component input/output socket names exactly
  - **BM25 vs semantic**: BM25 better for keyword search; embeddings better for conceptual
  - **Memory on large corpora**: Use Elasticsearch/Weaviate instead of InMemoryDocumentStore

  ## References
  - [Haystack GitHub](https://github.com/deepset-ai/haystack)
  - [Documentation](https://docs.haystack.deepset.ai/)
  - [Integrations Hub](https://haystack.deepset.ai/integrations)
  - [Tutorials](https://haystack.deepset.ai/tutorials)
  