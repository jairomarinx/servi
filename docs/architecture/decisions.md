# Architecture Decision Records - servi.cam

## ADR-001: Split users and persons tables
- Date: 2026-04-09
- Decision: users table for Laravel auth only, persons for business data
- Reason: Separation of concerns. Allows changing auth without touching business data.
- Status: Accepted

## ADR-002: A person can be both client and provider simultaneously
- Date: 2026-04-09
- Decision: One person can have both a clients record and a providers record active
- Reason: Real world use case. A plumber can also hire an electrician.
- Status: Accepted

## ADR-003: categories with parent_id not full tag graph
- Date: 2026-04-09
- Decision: Simple self-referencing parent_id in categories
- Reason: MVP simplicity. 90% of value with 10% of complexity.
- Deferred: Full closure table deferred to v2
- Status: Accepted

## ADR-004: national_id instead of cedula
- Date: 2026-04-09
- Decision: national_id VARCHAR(50) nullable to support any country format
- Reason: Global launch target
- Status: Accepted

## ADR-005: Focus on local services
- Date: 2026-04-09
- Decision: Primary focus on in-person local services in mid-sized cities
- Reason: Freelancer and Upwork dominate remote. Local is uncontested in Colombia.
- Status: Accepted
