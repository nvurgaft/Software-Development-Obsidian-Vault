Retrieval-augmented generation (RAG) is a technique that enables [[large language models|large language models]] (LLMs) to retrieve and incorporate new information from external data sources. With RAG, LLMs first refer to a specified set of documents, then respond to user queries. These documents supplement information from the LLM's pre-existing training data. This allows LLMs to use domain-specific and/or updated information that is not available in the training data. For example, this helps LLM-based chatbots access internal company data or generate responses based on authoritative sources.

RAG improves large language models (LLMs) by incorporating information retrieval before generating responses. Unlike LLMs that rely on static training data, RAG pulls relevant text from databases, uploaded documents, or web sources.

RAG also reduces the need to retrain LLMs with new data, saving on computational and financial costs. Beyond efficiency gains, RAG also allows LLMs to include sources in their responses, so users can verify the cited sources. This provides greater transparency, as users can cross-check retrieved content to ensure accuracy and relevance.

Source: https://en.wikipedia.org/wiki/Retrieval-augmented_generation

### Known Issues

These are several known phenomena is AI models that necessitate the use of RAG 

1. Hallucinations - The AI may some times generate fabricated, inaccurate data or information that is unsupported  by it's training data. The response may sound convincing but they are incorrect.
2. Outdated Knowledge - The training data collected may be old and not up to data with new relevant data, a model trained with data from a past timeframe will be unaware of new trends, discoveries and occurrences. Adding DAG functionality will allow it to retrieve new data.
3. Limited domain expertise - LLM models my lack certain depth needed in a specific domain to answer related questions, thus the model may answer in a limited and inaccurate fashion leading to errors and even deliberate inaccuracies when the model tries to fill the gaps on it's own.

### Components in RAG

* Generators - AI models that accept and return natural human language responses based on training data.
* Vector databases - These store vector embeddings that allow retrieval of data based on similarity to other data. These are optimized for AI systems.
* Retrievers - Algorithms that match queries that documents.

### How RAG works

RAG combines two core processes: **retrieval** and **generation**. Together, they create a feedback loop that enhances the quality and relevance of AI-generated content.

- **Retrieval**: When a query is received, the system uses a retriever to search a knowledge base for relevant documents. These are often stored in a [[Vector Database]] like Pinecone or FAISS, which enables fast similarity searches using embeddings. The retriever converts the query into a vector and finds the closest matches.
- **Generation**: The retrieved documents are passed to a generator, typically an LLM, which uses them to produce a response. The model incorporates the external context into its output, making it more accurate and informative.

### RAG poisoning

RAG systems may retrieve factually correct but misleading sources, leading to errors in interpretation. In some cases, an LLM may extract statements from a source without considering its context, resulting in an incorrect conclusion. Additionally, when faced with conflicting information, RAG models may struggle to determine which source is accurate. The worst case outcome of this limitation is that the model may combine details from multiple sources producing responses that merge outdated and updated information in a misleading manner.

Source: https://github.com/resources/articles/software-development-with-retrieval-augmentation-generation-rag