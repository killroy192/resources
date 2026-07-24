Use with [spec skill](./SKILL.md). Section titles must match exactly.

# Specification

## Business Goal

Explain why this work matters to users or the product. Focus on outcomes rather than implementation.

Structure:

Problem / pain description
Proposed solution

## Current Behavior

Provide a factual description of the current behavior based on the existing system or codebase. Split by layer (frontend, backend/API, data, etc.) where appropriate. Do not describe desired behavior.

Expected Behavior
Describe the expected user-visible and system-visible behavior after the work is complete.

### User Flow

Describe the expected user journey.

### Edge Cases

List important edge cases and how they should behave.

### Error Handling

Describe expected behavior for failures, validation errors, unavailable services, permission issues, and other error scenarios.

## Out Of Scope

List explicit exclusions to prevent scope creep.

## Technical Scope

Provide a high-level overview of the technical work, including affected layers and types of changes (UI, API, data model, integrations, etc.).

Do not include implementation steps, code, pseudocode, algorithms, diffs, or design decisions.

## Non-functional Requirements and Constraints

List factual requirements and constraints, including where applicable:

- Technology stack
- Existing architectural patterns
- Compatibility requirements
- Data limitations
- Performance
- Scalability
- Reliability
- Security
- Accessibility
- Testing expectations
- Existing tests that must continue to pass
- Only include facts or explicitly stated requirements—not personal recommendations.

## Acceptance Criteria

Create independently testable acceptance criteria (AC-1, AC-2, ...).

Present them as a table with the following columns:

ID | Acceptance Criterion | Verifiable By

"Verifiable By" should contain values such as Manual Test, Automated Test, API Check, UI Check, or Integration Test.

## Assumptions

List assumptions made while writing the specification. Clearly distinguish assumptions from constraints.