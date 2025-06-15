# RAG Pipeline 구조 설계

## 1. 목적
- 다양한 문서(PDF, Word, PPTX, TXT)를 벡터DB에 등록하고
- 사용자 쿼리에 적절한 문서를 찾아
- 결과를 사용자에게 제공하는 Retrieval-Augmented Generation 구조를 구현한다.

## 2. 주요 클래스 구성

### 📁 DocumentLoader
- 역할: 다양한 문서 포맷을 로드하여 텍스트로 변환

### 📁 Embedder
- 역할: E5, BGE 등의 모델을 이용해 텍스트 임베딩 생성

### 📁 VectorStore
- 역할: pgvector 기반 DB에 벡터 저장 및 유사도 검색

### 📁 Retriever
- 역할: 쿼리 임베딩 후 VectorStore에서 유사 문서 검색

### 📁 RAGPipeline
- 역할: 전체 흐름을 통합하고 사용자 요청에 응답 생성

## 3. 향후 확장 방향
- FAISS, Qdrant 등 다른 VectorDB 플러그인화
- LLM 후처리 및 LangChain 연동


my_rag_project/
├── loaders/
│   └── document_loader.py
├── embed/
│   └── embedder.py
├── vectorstore/
│   └── pgvector_store.py
├── retrieval/
│   └── retriever.py
├── pipeline/
│   └── rag_pipeline.py
├── main.py
