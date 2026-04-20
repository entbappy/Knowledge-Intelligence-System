# Storage Service Component

```mermaid
flowchart TD
    A[File upload] --> B[S3Storage.upload_file()]
    B --> C[Boto3 S3 client]
    C --> D[AWS S3 bucket]
    E[Stored file request] --> F[S3Storage.get_file()]
    F --> C
    style A fill:#f9f,stroke:#333
    style B fill:#bfb,stroke:#333
    style C fill:#bbf,stroke:#333
    style D fill:#ffe4b5,stroke:#333
    style E fill:#fdd,stroke:#333
    style F fill:#cfc,stroke:#333
```