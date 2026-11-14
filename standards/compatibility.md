# Event Compatibility Policy

- **Backward compatible (minor):** add optional payload fields, add new event types.
- **Breaking (major):** remove/rename fields, change field types, change semantics
  → requires `eventVersion` increment and consumer migration window.
- Consumers MUST tolerate unknown fields (forward compatibility).
- Producers MUST NOT reuse `eventId` values; UUIDv7 recommended.
- Schema validation runs in CI on every change to `main`.
