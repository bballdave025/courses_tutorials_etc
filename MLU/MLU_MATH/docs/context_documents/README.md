# Context Documents

This directory contains **continuation-ready context documents** (Lab
Notebook / LN files) for the **Machine Learning University — Mathematics
(mlumath)** course.

These are **not** polished study notes. They are:

- structured snapshots of learning progress,
- continuation-ready checkpoints,
- mathematical intuition and derivation notes,
- implementation ideas inspired by the course,
- "lab notebook" entries for active learning.

------------------------------------------------------------------------

# Purpose

Each document is designed to answer:

> **If I resumed studying this course in a fresh chat or after several
> months away, what would I need to know?**

These documents preserve:

- lecture progress
- mathematical intuition
- notation decisions
- terminology
- derivations
- important conceptual insights
- implementation ideas
- project ideas inspired by the course
- active questions
- immediate next study tasks

Think of these as **checkpoint files for understanding**, not summaries.

------------------------------------------------------------------------

# Documentation Hierarchy

```text
README.md
    ↓
Course Structure
    ↓
Lab Notebook / Context Documents
    ↓
Experiment Notes
    ↓
Related Repositories / Projects
```

Examples of related projects include:

- JabberVec
- Latent Forge
- no_code_jupyter_nb
- dwb-ip-notes

------------------------------------------------------------------------

# Context Document Header Template

Use **double-brace placeholders** (`{{...}}`) rather than angle
brackets.

```text
*BEGIN: Context Document Header*

# CONTEXT DOCUMENT — Continuation

## Course

**Name:**
Machine Learning University — Mathematics

**Short marker:**
mlumath

**Lecture(s):**
{{Lecture numbers}}

**Primary topic(s):**
{{Topic list}}

---

## Continuation Metadata

**Prepared at:**
{{ssssssssss_YYYY-mm-ddTHH:MM:SS±ZZZZ}}

Generated via:

date +'%s_%Y-%m-%dT%H:%M:%S%z'

(Boston, MA time)

**Continued from chat:**
{{Exact chat title}}

**Also involving:**
- {{Related discussion}}
- {{Related project}}
- *(or: no other subjects specified)*

---

## Author / Source

**User (GitHub):**
@bballdave025

---

## Intent for This Context

{{Describe what future Dave and ChatGPT should immediately continue
without re-deriving.}}

---

## Usage Instructions

- Treat this document as authoritative learning state.
- Continue with minimal re-derivation.
- Preserve notation preferences whenever practical.
- Preserve intuition before optimization.

*ENDOF: Context Document Header*
```

------------------------------------------------------------------------

# Pre-Context-Document Prompt (PCDP)

Before pasting a context document into a fresh chat, you may send a
short PCDP establishing the current lecture, immediate goals, and
expected continuation.

```text
## Current Work

Course:
Machine Learning University — Mathematics

Current lecture(s):
{{Lecture}}

Current objective:
{{Immediate study goal}}

---

## Upcoming Context Document

The next message will be a CONTEXT DOCUMENT for:

Machine Learning University — Mathematics

This continues discussion begun in:

"{{Previous chat title}}"

---

## Timing

Preparation:
{{YYYY-MM-DDTHH:MM:SS±ZZ:ZZ}}

(Optional) New chat:
{{YYYY-MM-DDTHH:MM:SS±ZZ:ZZ}}

---

## Immediate Focus

Help me:

{{Concrete ADHD-friendly next study task}}

*End of PCDP*
```

------------------------------------------------------------------------

# Naming Convention

```text
LN_mlumath_YYYY-MM-DD_{{optional-tag}}_-_{{short-slug}}.md
```

Examples:

```text
LN_mlumath_2026-07-05_ctx01_-_lecture01_linear_algebra_review.md
LN_mlumath_2026-07-05_-_contravariance_covariance_intuition.md
LN_mlumath_2026-07-08_-_lecture02_matrix_factorization.md
```

`LN` = Lab Notebook.

The optional tag is usually omitted unless it adds useful context.

Examples:

- ctx01
- parked
- review
- project-idea

Choose the slug to describe the primary mathematical or conceptual topic
rather than simply the lecture number whenever practical.

------------------------------------------------------------------------

# What Belongs in a Context Document?

A context document should capture the **current learning state**, not
merely what was covered.

Typical sections include:

- Current lecture progress
- Key mathematical ideas
- Notation decisions
- Intuition developed
- Connections to previous mathematics
- Connections to physics
- Connections to machine learning
- Questions answered
- Questions still open
- Project ideas
- Immediate next lecture or exercise
- Important equations
- References worth revisiting

Include derivations, diagrams, code snippets, Einstein notation,
alternative explanations, or implementation notes whenever they reduce
future re-derivation.

------------------------------------------------------------------------

# Scope

These documents are intended to bridge study across:

- multiple ChatGPT conversations,
- multiple study sessions,
- multiple devices,
- interruptions lasting days or months.

They are written primarily for future Dave, who should be able to resume
thinking immediately rather than reconstructing previous understanding.

------------------------------------------------------------------------

# Retrieval Tip

1. Sort by filename.
2. Open the newest `LN_mlumath_*`.
3. Resume from **Immediate Next Steps**.

------------------------------------------------------------------------

*End of README*
