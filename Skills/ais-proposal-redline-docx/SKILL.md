---
name: ais-proposal-redline-docx
description: >-
  Modify existing AIS proposal Word drafts by merging red-draft content into
  pink DOCX forms while preserving formatting, reviewer comments, tracked
  changes, and comment-response traceability. Use when asked to revise an
  existing reviewed proposal document instead of generating a new DOCX from
  scratch.
license: Proprietary
compatibility: Requires Python 3.10+ and uv (https://docs.astral.sh/uv/)
metadata:
  author: ais-internal
  version: "1.0"
---

# AIS Proposal Redline DOCX

Use this skill for pink-to-red proposal revision when the reviewed DOCX is the
source of truth. The goal is to preserve the existing form, tables, styles,
comments, and page discipline while applying targeted content changes and
documenting how reviewer feedback was addressed.

Use `ais-proposal-docx` instead when the user wants to generate a new proposal
document from structured JSON.

## Principles

- Treat the pink DOCX as the source of truth.
- Make text-only edits unless a bounded table insertion is explicitly needed.
- Preserve existing comments; do not accept, delete, or resolve them by default.
- Add concise response comments that state what changed and how it addressed the
  reviewer feedback.
- Enable tracked revisions and validate structurally, then visually QA the final
  DOCX in Word or through a render workflow before delivery.
- Do not invent metrics, past performance claims, or compliance assertions. Mark
  unsupported claims for user confirmation.

## Available Scripts

- `scripts/extract_review_context.py` - extracts comments, anchors, paragraphs,
  table counts, and tracked-change state from a DOCX.
- `scripts/build_merge_plan.py` - creates a merge-plan skeleton from extracted
  review context.
- `scripts/apply_merge_plan.py` - applies targeted paragraph/table operations
  and response comments to the existing DOCX.
- `scripts/validate_redline_docx.py` - validates the resulting DOCX for package
  health, comments, response comments, and tracked-change indicators.

## Workflow

### 1. Extract reviewer context

```bash
uv run Skills/ais-proposal-redline-docx/scripts/extract_review_context.py \
  --input pink.docx \
  --output review-context.json
```

Read the extracted comments in context before drafting changes. Use paragraph
indices from this file as anchors for merge-plan operations.

### 2. Build a merge plan

```bash
uv run Skills/ais-proposal-redline-docx/scripts/build_merge_plan.py \
  --review-context review-context.json \
  --source-docx pink.docx \
  --output-docx redline.docx \
  --output merge-plan.json
```

Fill `operations` with only the needed changes. Fill every applicable
`comment_replies[].reply` with a specific response. Leave uncertain items as
`needs_confirmation` rather than forcing unsupported content.

Supported operation types:

- `replace_paragraph_text`
- `insert_paragraph_after`
- `insert_table_after`

See `examples/merge-plan.sample.json`.

### 3. Apply the merge plan

```bash
uv run Skills/ais-proposal-redline-docx/scripts/apply_merge_plan.py \
  --input pink.docx \
  --plan merge-plan.json \
  --output redline.docx
```

The script preserves the DOCX package, edits the targeted body XML, enables
tracked revisions in document settings, and adds response comments for reviewer
comments with non-empty replies.

### 4. Validate the redline DOCX

```bash
uv run Skills/ais-proposal-redline-docx/scripts/validate_redline_docx.py \
  --input redline.docx \
  --require-track-revisions \
  --fail-generic-replies
```

Use `--expect-reviewer-comments` and `--expect-resolution-comments` when counts
are known. A passing structural validation does not replace visual QA.

### 5. Visual QA

Open or render the DOCX and verify:

- page limits are still met
- formatting, tables, headers, footers, and cover-page fields did not drift
- comments are preserved and response comments are visible
- tracked insertions/deletions are understandable
- no generic comment responses remain

## Reference Materials

- [Merge Strategy](references/MERGE-STRATEGY.md)
- [Comment Replies](references/COMMENT-REPLIES.md)
- [Tracked Changes](references/TRACKED-CHANGES.md)
