**Embedding** is a technique used in machine learning and natural language processing (NLP) to ==convert words into numbers==. Computers understand numbers, not words, so we need to translate text into a numerical format that a machine learning model can work with.

Imagine each word in a sentence being transformed into a unique sequence of numbers. This process allows the model to "understand" the text by working with these numerical representations instead of the raw text.

### What is Vectorization?

**Vectorization** is the process of converting text documents into vectors. A vector is essentially a list of numbers, and each document is represented as a vector. This transformation helps the machine learning model to process and analyze the text more effectively.

For example, if we have three documents, ==vectorization will create a unique vector for each document==. These vectors capture important information about the documents' contents, making it easier for the model to distinguish between them.

### Embedding Documents

To further enhance the understanding, we can **embed each document** using a model like OpenAI's embedding model. Here's how it works:

1. **Splitting Documents**: First, we split the documents into smaller chunks or individual words.
    
2. **Embedding with OpenAI's Model**: We then use OpenAI's embedding model to convert these chunks or words into vectors. This model generates vectors with at least 1000 dimensions. A dimension can be thought of as an individual feature or attribute in the vector.
    
    - **1000 Dimensions**: Think of a vector as a long list of 1000 numbers. Each number represents a specific aspect of the word or chunk of text. Having more dimensions allows the model to capture more detailed information about the text. 