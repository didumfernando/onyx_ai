During the intial production of Onyx AI it was built upon a classic RAG (Retrieval-Augmented Generation) model where classic RAG follows a linear process. Intially, users will type in a question or query (e.g what is a linked list?). Once this query is received, the system retrieves a fixed set of passages from the PDFs given to the model beforehand that matches the query's question. This is done by fetching the top-k relevant chunks (usually via vector search). Then it assembles the context by arrange the passages into a prompt context and lastly produces an answer referencing the retrieved passages. The model hence generates an answer based on the single retrieval.

<img width="1023" height="246" alt="create me a illustration for the workflow of classic RAG given this_ - visual selection" src="https://github.com/user-attachments/assets/cec1e748-39cc-4b03-ae23-6d9ecfaa0faf" />

However, through testing different questions that are not as direct we noticed that classic RAG hits a deadend. Through experimentation we noticed the classic RAG failed due to 2 main reasons:

1. Underspecified queries: Where the user's wordings in the question they posed were very general which meant that they were not the best retrieval queries. (e.g. Why is a linked list better than a list?)

2. Brittle chunking: Relevant context is split across chunks or blocked by uncessary jargon in some of the PDFs

To solve these issues and improve our model we considered exploring an "Agentic RAG" approach. A classic RAG, simply put runs one log query and constructs the answer from whatever is retrieved, regardless of whether it answers the question directly or not. However, "Agentic RAGs" tend to act like a debug loop. User queries, the evidence is retrieved and insepcted, gaps are noticed, query is refined based on the gaps or a second system is used to check and this is done repeately until it has reached a time/cost budget.

"Agentic RAG" is beneficial in this sense as it can repair retrieval. When the intial retrieval from the system is weak, the system is able to either rewrite queries, switch sources or take in more information before answering. This helps to address issues where the question is underspecified or ambigious, evidence provided (PDFs in this case) is spread across mutliple documents and lastly first retrieval returns partial information.
