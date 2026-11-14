# IAOP Event Schema Standard

## Format

- Canonical schema format: **JSON Schema (draft 2020-12)**.
- One schema per event type, versioned by the `eventType` name suffix
  (`<domain>.<event>.v<N>` is expressed as `eventVersion: N` plus the
  `eventType` string).

## Envelope

All integration events use the canonical envelope defined in
`schemas/envelope.schema.json`:

| Field | Type | Required | Notes |
|---|---|---|---|
| eventId | UUID | yes | Unique per event occurrence |
| eventType | string | yes | `<domain>.<past-tense-event>` e.g. `agent.activated` |
| eventVersion | integer | yes | Schema version, starts at 1 |
| source | string | yes | Producing service name |
| aggregateId | UUID | no | Aggregate the event belongs to |
| aggregateVersion | integer | no | Optimistic-concurrency version |
| occurredAt | date-time | yes | RFC 3339 UTC instant |
| correlationId | UUID | no | Propagated request/trace correlation |
| causationId | UUID | no | Event/message that caused this one |
| payload | object | yes | Event-specific data (see event schema) |

## Rules

- Domain events are internal; **integration events are a separate,
  versioned contract**. Never publish internal domain objects.
- Prefer stable identifiers and references over embedded PII.
- Payload privacy classification: `public` | `internal` | `confidential`.
  Default is `internal`; PII minimization is mandatory.
- Backward compatibility: adding optional fields is compatible;
  removing/renaming fields or tightening types requires a version bump.
- All events in `events/` are **DRAFT** until producer and consumer agree;
  promotion to production contract is recorded in `catalog.json`.
