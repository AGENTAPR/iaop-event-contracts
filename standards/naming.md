# Event Naming Standard

Format: `<domain>.<past-tense-event>` — lowercase, dot-separated.

- Domain segment matches the owning bounded context
  (e.g. `recruitment`, `onboarding`, `agent`, `agency`, `learning`,
  `certification`, `eligibility`, `sales`, `portfolio`, `commission`,
  `compliance`, `performance`).
- Event segment is past tense (something that happened), never imperative.
- Examples: `agent.activated`, `portfolio.policy-issued`,
  `commission.calculated`.
- Breaking changes → new `eventVersion`; old version kept for consumers.
