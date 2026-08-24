# Governance

## Purpose

This repository is a neutral architectural record. It exists to compare, challenge and document Unity/CITADEL, James's Second Brain, and any future combined/reference architecture.

## Source-of-truth boundaries

1. Gareth's Unity/CITADEL repository is authoritative for Unity/CITADEL code and implementation state.
2. James's Second Brain repository is authoritative for Second Brain code and implementation state.
3. This repository is authoritative for reviews, architectural comparisons, agreed principles, decisions and reference specifications created here.

## Read-only review principle

Source projects are reviewed read-only unless their owner explicitly authorises changes in their own repository.

## Separation principle

Unity/CITADEL and Second Brain remain independent systems. The goal is interoperability and architectural learning, not forced merger.

## Change discipline

Architectural conclusions should be recorded as decisions. Significant changes should identify:
- source evidence,
- assumptions,
- affected workstream,
- compatibility impact,
- approval status.

## Public repository and security boundary

This repository is public. All committed material must therefore be suitable for public disclosure.

Never commit credentials, API keys, tokens, `.env` files, private personal memory, family/legal/health material, financial or broker/account details, trading evidence, private logs, secrets, or unrelated private evidence.

Material derived from a private source repository or runtime may be included only when deliberately sanitised and when the resulting record is architectural rather than a disclosure of private implementation data.
