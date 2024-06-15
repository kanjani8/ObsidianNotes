## 검색 증강 생성

최신 자연어 처리 기술로, 대규모 언어 모델(LLM)과 정보 검색 시스템을 결합한 것

RAG는 질의에 대한 답변을 생성할 때, 단순히 사전 훈련된 지식에 의존하지 않고, 외부 데이터 소스로부터 관련 정보를 검색하여 이를 답변 생성에 반영한다.

어떤 한 Question에 대해 Search할 때 더 잘 대답하기 위해  그와 관련된 Context를 LLM에 함께 보내는 것.

https://python.langchain.com/v0.2/docs/tutorials/rag/

![[Pasted image 20240616010822.png]]The most common full sequence from raw data to answer looks like:

### Indexing[​](https://python.langchain.com/v0.2/docs/tutorials/rag/#indexing "Direct link to Indexing")

1. **Load**: First we need to load our data. This is done with [DocumentLoaders](https://python.langchain.com/v0.2/docs/concepts/#document-loaders).
2. **Split**: [Text splitters](https://python.langchain.com/v0.2/docs/concepts/#text-splitters) break large `Documents` into smaller chunks. This is useful both for indexing data and for passing it in to a model, since large chunks are harder to search over and won't fit in a model's finite context window.
3. **Store**: We need somewhere to store and index our splits, so that they can later be searched over. This is often done using a [VectorStore](https://python.langchain.com/v0.2/docs/concepts/#vectorstores) and [Embeddings](https://python.langchain.com/v0.2/docs/concepts/#embedding-models) model.