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
        string parent_id FK "Opcional para subcategorias"
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
        string document_type "DNI, Certificado, Pasado Judicial"
        string file_url
        string status "pending, approved, rejected"
        text rejection_reason
        datetime created_at
    }

    SERVICE {
        string id PK
        string provider_id FK
        string category_id FK
        string title
        text description
        decimal list_price "Precio base ofertado"
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
        decimal agreed_price "Precio final negociado"
        string status "pending, accepted, in_progress, completed, cancelled"
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
        datetime created_at "Fecha del cambio"
    }

    MESSAGE {
        string id PK
        string request_id FK
        string sender_id FK
        text content
        datetime read_at "Null si no leido"
        datetime created_at
    }

    RATING {
        string id PK
        string request_id FK
        string reviewer_id FK "Quien califica"
        string target_user_id FK "A quien califican"
        integer score
        text comment
        datetime created_at
    }

    %% Relaciones
    USER ||--o{ PROVIDER : "se convierte en"
    CATEGORY ||--o{ CATEGORY : "tiene subcategorias"
    CATEGORY ||--o{ SERVICE : "clasifica"
    
    PROVIDER ||--o{ VERIFICATION_DOC : "sube"
    PROVIDER ||--o{ SERVICE : "ofrece"
    SERVICE ||--o{ SERVICE_PHOTO : "tiene"
    
    USER ||--o{ REQUEST : "solicita (cliente)"
    SERVICE ||--o{ REQUEST : "genera (venta/preventa)"
    
    REQUEST ||--o{ MESSAGE : "contiene"
    REQUEST ||--o{ REQUEST_LOG : "tiene historial"
    REQUEST ||--o{ RATING : "produce"