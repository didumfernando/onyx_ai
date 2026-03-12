When building Onyx AI it started off as a basic RAG system (aka naive RAG). However given the complexity of questions that could potentially be asked in the field of computing our basic RAG system may face challenges. This is due to the fact that when we handle complex queries, we may require reasoning from multiple pieces of information that could be scattered. Therefore I decided to explore into multi-hop retrieval systems.

Let's break down what multi-hop retrieval is. Suppose for instance the user queries: "Who was the president of Singapore in 2024?". 

Given this query and say we feed it to the vector database, we potentially get a few matches but say we take the two nearest matching context passages that can solve this question:

"Person A stepped down as the president of singapore in 2021 following her long stint..." 

"Person B has been named the new president of singapore, replacing person A...."

Now in these two passages, it is not explicity stated who is the president of singapore in 2024 but if we were to choose it would be Person B given the fact that 1. Person A stepped down in 2021 and 2. Person B is named the new president after person A. This shows that we had **hop** 2 times before we reached the answer. To us humans this is simple logical thinking but thanks to multi-hop retrievals we can now easily solve questions despite not having explicit data.

<img width="1109" height="427" alt="image" src="https://github.com/user-attachments/assets/3ef11e05-cf89-4596-89c9-869722d9a333" /> **Credits to Sachin Khandewal**

