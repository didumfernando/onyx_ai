During the intial production of Onyx AI it was built upon a classic RAG (Retrieval-Augmented Generation) model where classic RAG follows a linear process. Intially, users will type in a question or query (e.g what is a linked list?). Once this query is received, the system retrieves a fixed set of passages from the PDFs given to the model beforehand that matches the query's question. This is done by fetching the top-k relevant chunks (usually via vector search). Then it assembles the context by arrange the passages into a prompt context and lastly produces an answer referencing the retrieved passages. The model hence generates an answer based on the single retrieval.

However, through testing different questions that are not as direct we noticed that classic RAG hits a deadend. Through experimentation we noticed the classic RAG failed due to 2 main reasons:
1. Underspecified queries: Where the user's wordings in the question they posed were very general which meant that they were not the best retrieval queries.

2. Brittle chunking: Relevant context is split across chunks or blocked by uncessary jargon in some of the PDFs
