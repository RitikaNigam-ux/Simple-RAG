# RAG-based Chatbot with Ollama
This project demonstrates a Retrieval-Augmented Generation (RAG) chatbot built using the Ollama API. The system embeds text chunks from a dataset, stores them in a vector database, retrieves the most relevant chunks based on a user query, and generates a response using a language model. The project utilizes two key Ollama models: one for embeddings (semantic representation of text) and another for generating responses based on retrieved context.

**Project Overview**

**Key Steps:**
1. Embedding Text Chunks: Text from a dataset is embedded using an embedding model.
2. Storing in Vector Database: The text chunks along with their embeddings are stored in a vector database.
3. Query Processing: Upon receiving a user query, the system computes the cosine similarity between the query's embedding and the embeddings in the database.
4. Response Generation: The top relevant text chunks are retrieved and used as context for generating a response using a language model.

**Models Used:**
Embedding Model: hf.co/CompendiumLabs/bge-base-en-v1.5-gguf – Used to convert text into vector embeddings.
Language Model: hf.co/bartowski/Llama-3.2-1B-Instruct-GGUF – Used to generate a response based on the retrieved context.

**How It Works**
1. Dataset Preparation: The system first loads a text dataset (cat-facts.txt), where each line represents a text chunk (e.g., a cat fact). Each chunk will be embedded to generate its semantic representation.
2. Embedding and Vector Database: The embedding model is used to convert each text chunk into a vector. These vectors are then stored in the VECTOR_DB (vector database), which is a list of tuples: (text_chunk, embedding).
3. Retrieving Relevant Information: When a user asks a question, the system:
 -->Embeds the query using the same embedding model.
 -->Compares the query embedding to the embeddings in the vector database using cosine similarity.
 -->Retrieves the top n most similar text chunks from the database.
4. Generating Response: The retrieved text chunks are fed to the language model as context, and a response is generated based on the context. The system does not generate new information but relies only on the provided context.
5. Interactive Chat: The chatbot interacts with the user and generates real-time responses. The system streams the response as it is being generated.
