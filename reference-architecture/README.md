# Reference Architecture

This area will contain implementation-neutral designs derived only after the two source systems have been independently reviewed.

Initial three-plane model:

## Control Plane — Unity
- workflow state
- orchestration
- policy
- capabilities
- budgets
- approvals
- routing
- audit/event ledger

## Knowledge Plane — Brain
- approved durable knowledge
- decisions
- project memory
- provenance
- portable human-readable records

## Execution Plane — AI + Tools
- replaceable AI models
- provider adapters
- coding/execution tools
- filesystem/git/browser/tool capabilities

No execution-plane component should own authoritative workflow state or durable canonical memory.
