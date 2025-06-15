# 🧠 LangGraph 기반 RAG 아키텍처 설계

이 문서는 LangGraph를 기반으로 구성한 RAG (Retrieval-Augmented Generation) 시스템의 구성 요소 및 데이터 흐름을 설명합니다.

---

## 📊 전체 구조 다이어그램

```mermaid
flowchart TD
    A[📁 문서 등록<br>필요 시 수동 추가] --> B[📚 DocumentLoader<br>텍스트 추출 및 분할]
    B --> C[🔢 Embedder<br>텍스트 → 벡터 임베딩]
    C --> D[💽 VectorStore<br>pgvector에 벡터 저장]

    E[❓ 사용자 쿼리 입력] --> F[🔢 Embedder<br>쿼리 임베딩]
    F --> G[🔍 Retriever<br>유사 벡터 검색]
    G --> H[📂 관련 문서 반환]

    H --> I[🧠 RAGPipeline<br>결과 통합 및 후처리]
    I --> J[🖥️ 결과 출력<br>콘솔, API, UI 등]

    subgraph "📦 백엔드 구성"
        B
        C
        D
        F
        G
        I
    end

    subgraph "👤 사용자 측"
        A
        E
        J
    end
