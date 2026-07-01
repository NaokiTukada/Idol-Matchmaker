---
name: fastapi-endpoint
description: >-
  Scaffolds new FastAPI endpoints following the 3-layer architecture (Router /
  Service / Schema). Use when adding API endpoints, routers, services, or
  implementing FastAPI backend features.
---

# FastAPI Endpoint

## Task Progress

```
- [ ] Step 1: Define Request/Response models in schemas/
- [ ] Step 2: Implement business logic in services/
- [ ] Step 3: Add thin HTTP handler in routers/
- [ ] Step 4: Register router in main.py or router aggregator
- [ ] Step 5: Add pytest tests
```

## Step 1: schemas/

Define Pydantic models for request and response.

- Do not put business logic in schemas
- Use axis keys from README: `relationship`, `performance`, `visual`, `character`, `age_attribute`, `behavior`

## Step 2: services/

Implement business logic. Delegate score/distance calculation to `services/scoring/` Strategy.

- Do not call HTTP-layer concerns from services
- Do not duplicate matching logic outside the scoring Strategy

## Step 3: routers/

Thin HTTP handler: validate input, call service, return response.

- Do not write business logic or distance calculation in routers
- Do not access master data directly from routers

## Step 4: Router registration

Include the new router in `main.py` or the project's router aggregator.

- Do not create orphan routers that are never mounted

## Step 5: Tests

Add pytest tests covering the service layer and endpoint.

- Do not skip tests for endpoints with scoring logic
