graph TD
    A[📝 load_query] --> B[🔢 embed_query]
    B --> C[✅ check_validity]
    C -->|유효| D[🔍 retrieve_docs]
    D --> E[📚 process_docs]
    E --> F[🧠 final_answer]
    C -->|무효| A  
