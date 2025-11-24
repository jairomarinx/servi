```mermaid
erDiagram

    USER {
        string id PK
        string name
        string email
        string phone
        string password_hash
        string city
        string address
        float geo_lat
        float geo_lng
        datetime created_at
        datetime updated_at
    }

    CATEGORY {
        string id PK
        string parent_id FK
        string name
        string slug
        boolean is_active
    }

    PROVIDER {
        string id PK
        string user_id FK
        text bio
        boolean is_verified
        datetime created_at
        datetime updated_at
    }

    VERIFICATION_DOC {
        string id PK
        string provider_id FK
        string document_type
        string file_url
        string status
        text rejection_reason
        datetime created_at
    }

    SERVICE {
        string id PK
        string provider_id FK
        string category_id FK
        string title
        text description
        decimal list_price
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
        decimal agreed_price
        string status
        boolean is_urgent
        datetime scheduled_for
        datetime created_at
        datetime updated_at
    }

    REQUEST_LOG {
        string id PK
        string request_id FK
        string previous_status
        string new_status
        string changed_by_user_id FK
        datetime created_at
    }

    MESSAGE {
        string id PK
        string request_id FK
        string sender_id FK
        text content
        datetime read_at
        datetime created_at
    }

    RATING {
        string id PK
        string request_id FK
        string reviewer_id FK
        string target_user_id FK
        integer score
        text comment
        datetime created_at
    }

    USER ||--o{ PROVIDER : becomes
    CATEGORY ||--o{ CATEGORY : subcategory_of
    CATEGORY ||--o{ SERVICE : classifies

    PROVIDER ||--o{ VERIFICATION_DOC : uploads
    PROVIDER ||--o{ SERVICE : offers
    SERVICE ||--o{ SERVICE_PHOTO : has

    USER ||--o{ REQUEST : requests
    SERVICE ||--o{ REQUEST : generates

    REQUEST ||--o{ MESSAGE : contains
    REQUEST ||--o{ REQUEST_LOG : history
    REQUEST ||--o{ RATING : produces
