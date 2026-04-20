# LLM Service Component

```mermaid
flowchart TD
    A[User question] --> B[LLMService.get_response()]
    B --> C[ChatOpenAI (gpt-3.5-turbo)]
    B --> D[ConversationBufferMemory]
    E[Retriever results] --> B
    C --> F[ConversationalRetrievalChain]
    F --> G[Answer text]
    G --> H[Flask /query response]
    style A fill:#f9f,stroke:#333
    style B fill:#bfb,stroke:#333
    style C fill:#bbf,stroke:#333
    style D fill:#ffe4b5,stroke:#333
    style E fill:#fdd,stroke:#333
    style F fill:#cfc,stroke:#333
    style G fill:#cff,stroke:#333
