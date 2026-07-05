# Data model and entity relationship diagram

GitHub renders Mermaid natively inside markdown files, so the entity relationship diagram lives here as Mermaid rather than as a static image.

## Key entities

| Entity | Purpose |
|---|---|
| User | A consultant, SME, or reviewer, scoped to one or more engagements |
| Engagement | A single client project, the unit of data isolation |
| Document | An ingested source file, scoped to one engagement |
| Embedding chunk | A vector-embedded slice of a document |
| Chapter | A section of the report, generated and versioned independently |
| Version | A snapshot of a chapter at a point in time |
| Validation flag | An issue raised by the AI validation agent against a chapter |
| Citation | A link from a chapter to a specific source document |
| Reviewer approval | A logged sign-off required before a chapter can be finalized |

## Diagram

```mermaid
erDiagram
    USER ||--o{ ENGAGEMENT : works_on
    ENGAGEMENT ||--o{ DOCUMENT : contains
    DOCUMENT ||--o{ EMBEDDING_CHUNK : split_into
    ENGAGEMENT ||--o{ CHAPTER : produces
    CHAPTER ||--o{ VERSION : has
    CHAPTER ||--o{ VALIDATION_FLAG : receives
    CHAPTER ||--o{ CITATION : cites
    CITATION }o--|| DOCUMENT : points_to
    CHAPTER ||--o{ REVIEWER_APPROVAL : requires
    USER ||--o{ REVIEWER_APPROVAL : grants

    ENGAGEMENT {
        uuid id PK
        string client_name
        timestamp started_at
    }
    CHAPTER {
        uuid id PK
        uuid engagement_id FK
        string status
        timestamp updated_at
    }
    VALIDATION_FLAG {
        uuid id PK
        uuid chapter_id FK
        string issue_type
        string status
    }
```
