# Entity Relationship Diagram - servi.cam
> Last updated: 2026-04-09
> Status: MVP draft

## users (auth - managed by Laravel)
| Field | Type | Notes |
|-------|------|-------|
| id | BIGINT UNSIGNED PK | |
| email | VARCHAR(255) | unique |
| password | VARCHAR(255) | |
| email_verified_at | TIMESTAMP NULL | |
| remember_token | VARCHAR(100) NULL | |
| created_at | TIMESTAMP | |
| updated_at | TIMESTAMP | |

## persons (business data)
| Field | Type | Notes |
|-------|------|-------|
| id | BIGINT UNSIGNED PK | |
| user_id | BIGINT UNSIGNED FK | → users.id |
| first_name | VARCHAR(100) | |
| last_name | VARCHAR(100) | |
| phone | VARCHAR(20) | |
| avatar | VARCHAR(255) NULL | |
| bio | TEXT NULL | |
| national_id | VARCHAR(50) NULL | passport, DNI, cedula, etc |
| national_id_verified | BOOLEAN | default false |
| trust_score | DECIMAL(3,2) | 0.00 to 1.00 |
| city | VARCHAR(100) | |
| latitude | DECIMAL(10,8) NULL | |
| longitude | DECIMAL(11,8) NULL | |
| created_at | TIMESTAMP | |
| updated_at | TIMESTAMP | |

## clients
| Field | Type | Notes |
|-------|------|-------|
| id | BIGINT UNSIGNED PK | |
| person_id | BIGINT UNSIGNED FK | → persons.id |
| rating | DECIMAL(3,2) NULL | 0.00 to 5.00 |
| is_active | BOOLEAN | default true |
| created_at | TIMESTAMP | |
| updated_at | TIMESTAMP | |

## providers
| Field | Type | Notes |
|-------|------|-------|
| id | BIGINT UNSIGNED PK | |
| person_id | BIGINT UNSIGNED FK | → persons.id |
| rating | DECIMAL(3,2) NULL | 0.00 to 5.00 |
| jobs_done | INT | default 0 |
| is_active | BOOLEAN | default true |
| created_at | TIMESTAMP | |
| updated_at | TIMESTAMP | |

## categories
| Field | Type | Notes |
|-------|------|-------|
| id | BIGINT UNSIGNED PK | |
| parent_id | BIGINT UNSIGNED NULL FK | → categories.id |
| name | VARCHAR(100) | |
| slug | VARCHAR(100) | unique |
| icon | VARCHAR(100) NULL | |

## skills
| Field | Type | Notes |
|-------|------|-------|
| id | BIGINT UNSIGNED PK | |
| category_id | BIGINT UNSIGNED FK | → categories.id |
| name | VARCHAR(100) | |
| slug | VARCHAR(100) | unique |

## services
| Field | Type | Notes |
|-------|------|-------|
| id | BIGINT UNSIGNED PK | |
| provider_id | BIGINT UNSIGNED FK | → providers.id |
| title | VARCHAR(150) | |
| description | TEXT | |
| price | DECIMAL(10,2) | |
| price_type | ENUM | fixed, hourly, negotiable |
| modality | ENUM | local, remote |
| radius_km | INT NULL | |
| is_active | BOOLEAN | default true |
| created_at | TIMESTAMP | |
| updated_at | TIMESTAMP | |

## service_categories (pivot)
| Field | Type | Notes |
|-------|------|-------|
| service_id | BIGINT UNSIGNED FK | → services.id |
| category_id | BIGINT UNSIGNED FK | → categories.id |

## service_skills (pivot)
| Field | Type | Notes |
|-------|------|-------|
| service_id | BIGINT UNSIGNED FK | → services.id |
| skill_id | BIGINT UNSIGNED FK | → skills.id |

## person_skills (pivot)
| Field | Type | Notes |
|-------|------|-------|
| person_id | BIGINT UNSIGNED FK | → persons.id |
| skill_id | BIGINT UNSIGNED FK | → skills.id |

## service_requests
| Field | Type | Notes |
|-------|------|-------|
| id | BIGINT UNSIGNED PK | |
| client_id | BIGINT UNSIGNED FK | → clients.id |
| category_id | BIGINT UNSIGNED FK | → categories.id |
| title | VARCHAR(150) | |
| description | TEXT | |
| budget | DECIMAL(10,2) NULL | |
| urgency | ENUM | low, medium, high, urgent |
| modality | ENUM | local, remote |
| latitude | DECIMAL(10,8) NULL | |
| longitude | DECIMAL(11,8) NULL | |
| status | ENUM | open, matched, in_progress, closed |
| created_at | TIMESTAMP | |
| updated_at | TIMESTAMP | |

## proposals
| Field | Type | Notes |
|-------|------|-------|
| id | BIGINT UNSIGNED PK | |
| service_request_id | BIGINT UNSIGNED FK | → service_requests.id |
| provider_id | BIGINT UNSIGNED FK | → providers.id |
| price_proposed | DECIMAL(10,2) | |
| message | TEXT | |
| eta_hours | INT NULL | |
| status | ENUM | pending, accepted, rejected |
| created_at | TIMESTAMP | |
| updated_at | TIMESTAMP | |

## bookings
| Field | Type | Notes |
|-------|------|-------|
| id | BIGINT UNSIGNED PK | |
| client_id | BIGINT UNSIGNED FK | → clients.id |
| service_id | BIGINT UNSIGNED FK | → services.id |
| proposal_id | BIGINT UNSIGNED NULL FK | → proposals.id |
| scheduled_at | TIMESTAMP | |
| status | ENUM | pending, confirmed, in_progress, completed, cancelled |
| total_price | DECIMAL(10,2) | |
| payment_status | ENUM | pending, paid, refunded |
| created_at | TIMESTAMP | |
| updated_at | TIMESTAMP | |

## reviews
| Field | Type | Notes |
|-------|------|-------|
| id | BIGINT UNSIGNED PK | |
| booking_id | BIGINT UNSIGNED FK | → bookings.id |
| reviewer_id | BIGINT UNSIGNED FK | → users.id |
| reviewed_id | BIGINT UNSIGNED FK | → users.id |
| rating | TINYINT | 1 to 5 |
| comment | TEXT NULL | |
| created_at | TIMESTAMP | |
