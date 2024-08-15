
### What is Embedding?

**Embedding** is a technique used in machine learning and natural language processing (NLP) to ==convert words into numbers==. This process allows computers to understand and work with text data.

- **Words to Numbers**: Each word in a sentence is transformed into a unique sequence of numbers.
- **Purpose**: This numerical representation makes it possible for machine learning models to process and analyze text.

### What is Vectorization?

**Vectorization** is the process of converting text documents into vectors. A vector is essentially a list of numbers that represents a document.

- **Vectors for Documents**: Each document is represented as a unique vector.
- **Purpose**: These vectors capture important information about the documents, enabling the model to distinguish between them.

### Embedding Documents

To make this more practical, we can embed each document using OpenAI's embedding model. Here's the process:

1. **Splitting Documents**: Split the documents into smaller chunks or individual words.
    
2. **Embedding with OpenAI's Model**: Convert these chunks or words into vectors using OpenAI's embedding model, which generates vectors with at least 1000 dimensions.
    
    - **1000 Dimensions**: Each vector is a long list of 1000 numbers, where each number represents a specific feature (특징) or attribute connected to the word.

### Example Process

Let's consider the sentence "I love programming":

1. **Splitting**: Split into individual words: "I", "love", "programming".
2. **Embedding**:
    - "I" might be converted into a vector like [0.5, 0.1, 0.4, ...] (1000 numbers in total).
    - "love" might be converted into a vector like [0.3, 0.7, 0.8, ...] (1000 numbers).
    - "programming" might be converted into a vector like [0.9, 0.2, 0.5, ...] (1000 numbers).

### How It Connects to Words

Each dimension in the vector represents a specific feature or characteristic of the word. The numbers in the vector indicate how strongly each feature is connected to the word.

### Using Embeddings in Retrieval-Augmented Generation (RAG)

In RAG, the raw vectors are used to search for documents in the same vector space:

- **Search**: By comparing vectors, we can find documents that are similar or related to each other based on their numerical representations.

### Try Word to Vector

You can explore how words are converted to vectors using this tool: [Word2Vec](https://turbomaze.github.io/word2vecjson/)

### Good Explanation About How LLM Works


https://www.youtube.com/watch?v=2eWuYf-aZE4