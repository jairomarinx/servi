# Servi  
Entity Relationship Diagram

Below is the proposed database structure for the initial Servi marketplace.  
This ERD uses Mermaid and is fully supported by GitHub.

```mermaid
erDiagram

    USER {
        string id PK
        string name
        string email
        string phone
        string password_hash
        datetime created_at
        datetime updated_at
    }

    PROVIDER {
        string id PK
        string user_id FK
        text bio
        boolean is_verified
        datetime created_at
        datetime updated_at
    }

    SERVICE {
        string id PK
        string provider_id FK
        string title
        text description
        decimal price
        string category
        boolean is_active
        datetime created_at
        datetime updated_at
    }

    SERVICE_PHOTO {
        string id PK
        string service_id FK
        string url
        datetime created_at
    }

    REQUEST {
        string id PK
        string customer_id FK
        string service_id FK
        string status
        datetime scheduled_for
        datetime created_at
        datetime updated_at
    }

    MESSAGE {
        string id PK
        string request_id FK
        string sender_id FK
        text content
        datetime created_at
    }

    RATING {
        string id PK
        string request_id FK
        string provider_id FK
        integer score
        text comment
        datetime created_at
    }


    USER ||--o{ PROVIDER : owns
    PROVIDER ||--o{ SERVICE : offers
    SERVICE ||--o{ SERVICE_PHOTO : has
    USER ||--o{ REQUEST : creates
    SERVICE ||--o{ REQUEST : requested_for
    REQUEST ||--o{ MESSAGE : contains
    PROVIDER ||--o{ RATING : receives
    REQUEST ||--o{ RATING : produces
