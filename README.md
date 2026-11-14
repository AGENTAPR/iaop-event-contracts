# iaop-event-contracts

Versioned integration events, event envelopes, and schemas.

## Purpose

iaop-event-contracts is part of the **Insurance Agent Operating Platform (IAOP)**, an enterprise
insurance agent lifecycle platform. It owns the **Event Contracts** bounded context
(or platform capability) within the IAOP microservices landscape.

## Bounded Context / Ownership

- **Bounded context:** Event Contracts
- **Owner:** AGENTAPR
- **Category:** contracts

## Technical Stack

AsyncAPI / JSON Schema

## Architecture Principles

- Domain-Driven Design (DDD) with explicit bounded contexts
- Hexagonal architecture (ports and adapters)
- Event-driven integration via versioned contracts
- PostgreSQL as the system of record where applicable
- Identity and access via Keycloak
- Workflow orchestration via Flowable BPM where applicable

## Responsibilities

- Versioned integration event definitions
- Event envelope and metadata schemas
- Cross-service event contract governance

## Non-Responsibilities

- Synchronous API contracts
- Service implementation
- Message broker configuration

## Related Repositories

- [iaop-architecture](https://github.com/AGENTAPR/iaop-architecture) - DDD strategic design, bounded context maps, ADRs
- [iaop-api-contracts](https://github.com/AGENTAPR/iaop-api-contracts) - Versioned OpenAPI contracts
- [iaop-event-contracts](https://github.com/AGENTAPR/iaop-event-contracts) - Versioned integration events
- [iaop-workflow-service](https://github.com/AGENTAPR/iaop-workflow-service) - Flowable BPM orchestration
- [iaop-local-dev](https://github.com/AGENTAPR/iaop-local-dev) - Local development environment

## Status

**INITIALIZED - NOT IMPLEMENTED**

This repository has been bootstrapped with baseline documentation and configuration only.
No business logic or service implementation exists yet.

## Development Conventions

- Default branch: `main`
- Development branch: `development` — all changes are committed and pushed here
- Squash merges preferred; merge commits and rebases disabled
- Pull requests required before merging into `main`
- Topics: iaop, insurance, insurance-agents, enterprise-architecture, event-driven-architecture, api-contracts, documentation, asyncapi

## Contract Layout

- `schemas/envelope.schema.json` - canonical integration event envelope
- `events/<domain>/<event>.schema.json` - per-event payload schemas (DRAFT)
- `catalog.json` / `catalog.md` - event registry with producer/consumer/privacy
- `standards/` - schema, naming, and compatibility policies
- `tools/validate.py` - CI validation (JSON Schema + catalog consistency)
