# Canonical Accessibility Testing and Remediation Framework

Manual and Automatable Test Resource for LLM Training.
This is the knowledgebase of tests used in projects by Double FW Ltd
All test Scripts are without context but are free to be used as reference and exploration for AI test management systems.

## Overview

This repository contains a structured accessibility testing, remediation, and design-system alignment framework designed to support:

- accessibility engineering
- inclusive design systems
- automated accessibility testing
- manual accessibility QA
- AI-assisted remediation workflows
- component-level accessibility governance
- WCAG conformance operations
- design token accessibility enforcement
- accessibility knowledge retrieval systems
- large-scale accessibility programme management

The framework combines:

- a canonical accessibility test inventory
- exact WCAG Success Criterion mappings
- POUR principle mappings
- design token dependencies
- component relationships
- automated-to-manual testing orchestration
- AXE rule mappings
- remediation prompt libraries
- structured remediation guidance for both humans and LLM systems

The repository is intended for use by:

- Accessibility Engineers
- QA Teams
- UX Designers
- Design System Teams
- Front-End Engineers
- Accessibility Programme Managers
- Responsible AI Teams
- Automated Accessibility Tooling Teams
- AI/LLM Accessibility Workflow Developers

---

# Repository Purpose

Traditional accessibility tooling often focuses on isolated rule failures rather than complete user experience outcomes.

This framework extends accessibility testing into a broader operational model that supports:

- behavioural accessibility validation
- inclusive interaction design
- semantic integrity
- component-level accessibility governance
- accessibility-aware design tokens
- AI-assisted remediation pipelines
- structured accessibility QA orchestration

The repository treats accessibility as:

- a system capability
- a design capability
- an engineering capability
- a governance capability
- a measurable operational process

---

# Repository Structure

## Canonical Test Library

Defines the canonical accessibility test inventory.

The tests are written as:

- user-behaviour-focused expectations
- accessibility requirements
- supported user outcomes

Example areas include:

- colour independence
- focus visibility
- semantic structure
- form labelling
- motion reduction
- landmark usage
- resize and reflow behaviour
- media accessibility
- navigation clarity
- assistive technology compatibility

The inventory defines accessibility expectations in behavioural and interactional terms rather than purely technical implementation terms.

---

## WCAG and POUR Alignment

Maps each canonical test to:

- exact WCAG Success Criterion IDs
- POUR principles

This enables:

- audit traceability
- reporting alignment
- standards compliance mapping
- governance integration
- legal and procurement support

Example mappings include:

- Text Contrast Minimum → WCAG 1.4.3
- Skip Link Presence → WCAG 2.4.1
- Page Title Present → WCAG 2.4.2
- Primary Page Language Declared → WCAG 3.1.1

---

## Component and Design Token Mapping

The repository maps accessibility requirements directly to:

- components
- patterns
- design tokens

This allows accessibility to be integrated directly into:

- design systems
- component libraries
- atomic design workflows
- token governance systems

Examples include:

| Accessibility Concern | Token Dependencies |
|---|---|
| Text contrast | `color.foreground`, `color.background` |
| Focus visibility | `focus.ring.*`, `outline.*` |
| Motion reduction | `motion.duration.*`, `motion.reduced.*` |
| Form labelling | `content.label`, `typography.label` |
| Landmarks | `layout.landmarks.*` |

This architecture enables accessibility enforcement to happen upstream during:

- design token definition
- component construction
- design system governance
- build-time validation

rather than only during post-build remediation.

---

# Automated Accessibility Tool Integration

## Supported Automated Testing Ecosystem

The repository is designed to work alongside multiple automated accessibility testing tools including:

1. IBM Equal Access Accessibility Checker
2. Alfa by Siteimprove
3. QualWeb
4. AccessLint
5. AXE-based tooling

The documents explicitly describe the strengths and limitations of each automated system and position them as complementary rather than standalone solutions.

---

# Recommended Testing Strategy

## Use Automation for Structural and Rule-Based Validation

Automated tools are strongest when validating:

- ARIA syntax
- accessible name presence
- semantic structure
- landmark usage
- colour contrast
- table structure
- language declarations
- form label presence
- heading hierarchy
- duplicate IDs
- static WCAG rule conformance

The repository specifically recommends combining:

- IBM Equal Access
- Alfa
- QualWeb
- AccessLint

for overlapping structural coverage.

---

# Use Manual Testing for Behavioural Accessibility

The framework explicitly identifies that automation cannot conclusively validate:

- meaning quality
- label usefulness
- interaction predictability
- task completion quality
- focus lifecycle quality
- route-change orientation
- motion tolerability
- real-world usability
- screen reader comprehension
- workflow continuity

Manual testing is therefore treated as essential rather than optional.

---

# Recommended Automated + Manual Workflow

## Phase 1 — Automated Static Analysis

Run all supported automated tools in CI/CD pipelines:

- IBM Equal Access
- Alfa
- QualWeb
- AccessLint
- AXE integrations

Use automation to identify:

- missing labels
- missing accessible names
- semantic failures
- ARIA misuse
- contrast failures
- missing landmarks
- invalid structure
- missing alt text
- keyboard accessibility indicators

---

## Phase 2 — Canonical Test Alignment

Map automated findings against the canonical inventory.

This prevents teams from treating isolated tool failures as the full accessibility picture.

Instead, findings are grouped into broader behavioural concerns such as:

- “Focus State Not Conveyed by Colour Alone”
- “Interactive Elements Have Accessible Names”
- “Layout Reflows Without Horizontal Dependency”
- “Motion Respects Reduced Motion Preference”

---

## Phase 3 — Manual Validation

Perform manual testing for:

- screen reader workflows
- keyboard-only journeys
- magnification usage
- motion sensitivity
- cognitive clarity
- route-change predictability
- modal lifecycle behaviour
- interaction sequencing
- task completion

The repository explicitly positions manual testing as the conclusive validation layer.

---

# AXE Integration Guidance

The repository includes detailed AXE remediation mappings and rule descriptions.

Examples include:

- `image-alt`
- `button-name`
- `label`
- `link-name`
- `document-title`
- `skip-link`
- `color-contrast`

These mappings provide:

- remediation intent
- user-focused interpretation
- implementation guidance
- accessibility rationale
- manual verification expectations

---

# How to Use This Repository with AXE

## Recommended AXE Workflow

### 1. Run AXE Automatically

Use AXE during:

- local development
- CI/CD pipelines
- Storybook validation
- component testing
- regression testing

---

### 2. Map AXE Findings to Canonical Tests

Do not treat AXE rules as isolated engineering defects.

Instead:

- map the AXE rule
- identify the related canonical behavioural test
- identify affected components
- identify affected design tokens
- identify associated WCAG and POUR mappings

Example:

| AXE Rule | Canonical Concern |
|---|---|
| `color-contrast` | Text Contrast Minimum |
| `button-name` | Interactive Elements Have Accessible Names |
| `label` | Visible Labels Exist for Form Inputs |

---

### 3. Validate Behaviour Manually

The repository repeatedly states that automated detection alone is insufficient for conclusive accessibility validation.

Always perform:

- keyboard testing
- screen reader testing
- zoom/reflow testing
- motion testing
- real task testing

---

# AI and LLM Remediation Workflows

The repository includes structured remediation guidance for both:

- humans
- LLM systems

Each canonical test includes:

- an LLM remediation prompt
- a human remediation brief

The remediation workflow is designed to support:

- AI-assisted accessibility fixing
- accessibility copilots
- structured remediation generation
- accessibility-aware code review
- design remediation guidance
- accessibility QA support systems

---

# Design System Integration

The repository is heavily aligned to atomic and token-based design systems.

Accessibility dependencies are mapped directly to:

- atoms
- molecules
- organisms
- templates
- content tokens
- semantic tokens
- layout tokens
- motion tokens
- focus tokens

This allows teams to:

- prevent accessibility defects upstream
- centralise accessibility governance
- create reusable accessibility-safe components
- standardise remediation behaviour
- scale accessibility across products

---

# Recommended Operational Model

The repository is most effective when integrated into:

- design systems
- CI/CD pipelines
- component libraries
- QA governance
- accessibility operations
- AI remediation tooling
- design review workflows
- engineering quality gates

Accessibility should not be treated as:

- a final audit phase
- isolated WCAG checks
- a single-tool process
- a compliance-only activity

Instead, this repository supports accessibility as a continuous operational capability.

---

# Intended Outcomes

The framework aims to enable:

- earlier accessibility detection
- reduced remediation costs
- improved consistency
- scalable accessibility governance
- reusable accessibility patterns
- structured accessibility QA
- AI-assisted accessibility operations
- component-level accessibility enforcement
- stronger alignment between design and engineering
- measurable accessibility maturity

---

# Important Principle

The repository consistently treats automated accessibility tooling as necessary but insufficient.

Automation is highly effective for:

- structural validation
- rule-based detection
- semantic exposure checks
- static conformance analysis

However, accessibility quality ultimately depends on:

- human behaviour
- comprehension
- predictability
- usability
- workflow continuity
- assistive technology experience
- cognitive clarity

The framework therefore combines:

- automated evaluation
- behavioural validation
- manual QA
- component governance
- AI-assisted remediation
- design-system enforcement

into a unified accessibility operations model.
