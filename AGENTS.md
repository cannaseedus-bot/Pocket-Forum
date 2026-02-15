# AGENTS.md

## Purpose
This repository contains a forum dataset and UI logic where post/topic continuity matters.

## Content Preservation Rules (High Priority)
- Do **not** remove, rewrite, or replace existing forum topics/posts by default.
- Changes to topics/posts must be **additive-first**:
  - add new records, or
  - append related metadata/comments, or
  - introduce new seed data without deleting old data.
- Editing existing topics/posts is allowed **only** when:
  - fixing a clear factual/data error,
  - fixing broken formatting/syntax,
  - repairing malformed JSON/JSONL or runtime-breaking issues,
  - or when explicitly requested by the user.
- When an existing post must be edited for a fix, keep the edit minimal and preserve original meaning.

## Implementation Guidance
- Prefer merge/append patterns over reassignment/replacement when handling `DEMO_POSTS`, JSONL datasets, or comment datasets.
- If adding seed posts, ensure ID-based deduplication rather than replacing arrays wholesale.
- Preserve backward compatibility for existing categories, filters, and rendering behavior.

## Validation Expectations
- After topic/post-related edits, run lightweight checks (e.g., script parse checks and basic rendering smoke checks) to ensure no existing content path broke.
- In summaries/PR notes, explicitly state whether existing topics/posts were preserved.
