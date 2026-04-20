# Flask App Component

```mermaid
flowchart TD
    A[Client] -->|GET /| B[Render index.html]
    A -->|POST /upload| C[upload_document()]
    C --> D[process_document()]
    D --> E[TextLoader / PyPDFLoader]
    D --> F[RecursiveCharacterTextSplitter]
    F --> G[Text chunks]
    C --> H[storage_service.upload_file()]
    C --> I[vector_store.add_documents()]
    A -->|POST /query| J[query()]
    J --> K[llm_service.get_response()]
    K --> A
    style A fill:#f9f,stroke:#333
    style B fill:#bbf,stroke:#333
    style C fill:#bfb,stroke:#333
    style D fill:#ffe4b5,stroke:#333
    style H fill:#fdd,stroke:#333
    style I fill:#ffd,stroke:#333
    style K fill:#cfc,stroke:#333
```