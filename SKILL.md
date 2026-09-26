---
name: permit-packet-gap-finder
description: Checks a local-government permit or planning packet against a stated completeness checklist and lists missing, expired, or inconsistent items. Use when intake staff or a clerk must decide whether an application can move to review, not when a decision on the merits is required.
license: MIT
compatibility: Claude, Codex, Cursor, OpenCode, Lovable
allowed-tools: read
inputs:
  - name: source
    type: text
    required: true
    description: Checklist plus notes or extracted text from the application packet
outputs:
  - name: artifact_markdown
    type: markdown
    description: Completeness findings
  - name: artifact_json
    type: json
    description: Structured gap list
side_effects: none
touches:
  - user_input
permissions:
  network: deny
  files: deny
  workspace: read
  secrets: deny
---

# Permit Packet Gap Finder

## When to use
Use at intake, before routing to planning, building, fire, or public works.

## Workflow
1. Read only the provided source.
2. Separate the checklist from the applicant materials.
3. For each required item: present, missing, expired, or inconsistent.
4. Do not approve, deny, or invent local code citations.
5. End with a single intake status: ready for review, hold for applicant, or needs supervisor.

## Input
A completeness checklist and the packet text or clerk notes.

## Output
Markdown findings plus JSON items with status and evidence quotes.

## Guidelines
- If the jurisdiction or permit type is unnamed, say so.
- Quote the source; do not browse the web.
- This skill does not submit filings or notify applicants.
