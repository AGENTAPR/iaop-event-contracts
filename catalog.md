# IAOP Event Catalog

Machine-readable catalog: `catalog.json`. All events are **DRAFT** until
producer and consumer contracts are agreed.

| Event Type | Producer | Privacy | Status |
|---|---|---|---|
| `recruitment.candidate-registered` | iaop-recruitment-service | confidential | DRAFT |
| `recruitment.approved` | iaop-recruitment-service | internal | DRAFT |
| `onboarding.started` | iaop-onboarding-service | internal | DRAFT |
| `onboarding.completed` | iaop-onboarding-service | internal | DRAFT |
| `onboarding.rejected` | iaop-onboarding-service | confidential | DRAFT |
| `agent.created` | iaop-agent-service | internal | DRAFT |
| `agent.activated` | iaop-agent-service | internal | DRAFT |
| `agent.suspended` | iaop-agent-service | confidential | DRAFT |
| `agent.terminated` | iaop-agent-service | confidential | DRAFT |
| `agency.agent-assigned` | iaop-agency-service | internal | DRAFT |
| `agency.agent-transferred` | iaop-agency-service | internal | DRAFT |
| `learning.training-completed` | iaop-learning-service | internal | DRAFT |
| `learning.assessment-passed` | iaop-learning-service | internal | DRAFT |
| `certification.credential-verified` | iaop-certification-service | confidential | DRAFT |
| `certification.credential-expired` | iaop-certification-service | confidential | DRAFT |
| `eligibility.changed` | iaop-eligibility-service | internal | DRAFT |
| `eligibility.revoked` | iaop-eligibility-service | confidential | DRAFT |
| `sales.proposal-submitted` | iaop-sales-service | confidential | DRAFT |
| `portfolio.policy-issued` | iaop-portfolio-service | confidential | DRAFT |
| `portfolio.policy-lapsed` | iaop-portfolio-service | confidential | DRAFT |
| `commission.calculated` | iaop-commission-service | confidential | DRAFT |
| `commission.reversed` | iaop-commission-service | confidential | DRAFT |
| `compliance.restriction-applied` | iaop-compliance-service | confidential | DRAFT |
| `compliance.restriction-removed` | iaop-compliance-service | confidential | DRAFT |
| `integration.operation-dispatched` | iaop-integration-service | internal | DRAFT |
| `integration.operation-completed` | iaop-integration-service | internal | DRAFT |
| `integration.operation-failed` | iaop-integration-service | internal | DRAFT |
| `integration.callback-received` | iaop-integration-service | internal | DRAFT |

---

## Kafka Topic Governance

All topics follow the naming convention: `iaop.{family}.{event_type}` or canonical topic prefix `iaop.{event_type}`.

| Topic Name | Producer Service | Partition Key | Retention | Ordering Guarantees | Security |
| :--- | :--- | :--- | :--- | :--- | :--- |
| `iaop.agent.created` | `iaop-agent-service` | `aggregate_id` (agentId) | 7 days | In-order per agent | Internal |
| `iaop.agent.activated` | `iaop-agent-service` | `aggregate_id` (agentId) | 7 days | In-order per agent | Internal |
| `iaop.agent.suspended` | `iaop-agent-service` | `aggregate_id` (agentId) | 30 days | In-order per agent | Confidential |
| `iaop.agent.terminated` | `iaop-agent-service` | `aggregate_id` (agentId) | 30 days | In-order per agent | Confidential |
| `iaop.agency.agent-assigned` | `iaop-agency-service` | `aggregate_id` (unitId/agentId) | 7 days | In-order per unit | Internal |
| `iaop.agency.agent-transferred` | `iaop-agency-service` | `aggregate_id` (agentId) | 7 days | In-order per agent | Internal |
| `iaop.integration.operation-dispatched` | `iaop-integration-service` | `aggregate_id` (operationId) | 3 days | In-order per operation | Internal |
| `iaop.integration.operation-completed` | `iaop-integration-service` | `aggregate_id` (operationId) | 7 days | In-order per operation | Internal |
| `iaop.integration.operation-failed` | `iaop-integration-service` | `aggregate_id` (operationId) | 14 days | In-order per operation | Internal |
| `iaop.integration.callback-received` | `iaop-integration-service` | `aggregate_id` (callbackId) | 7 days | In-order per callback | Internal |
| `iaop.recruitment.candidate-registered` | `iaop-recruitment-service` | `aggregate_id` (candidateId) | 7 days | In-order per candidate | Confidential |
| `iaop.onboarding.completed` | `iaop-onboarding-service` | `aggregate_id` (candidateId) | 7 days | In-order per candidate | Internal |
| `iaop.sales.proposal-submitted` | `iaop-sales-service` | `aggregate_id` (proposalId) | 30 days | In-order per proposal | Confidential |

