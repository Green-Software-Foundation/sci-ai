# Claude Code Context for SCI-AI Repository

## Repository Overview
This is **NOT a code repository** - it's a technical specification repository for measuring carbon emissions of AI systems. The main deliverable is a specification document, not software.

## Key Files & Their Purpose

### Primary Files
- **`SPEC.md`** - The main specification document. Most changes to this repository will be modifications to this file.
- **`FAQ.md`** - Critical companion document containing rationale for how the specification is structured. Essential reading before making any changes to SPEC.md.
- **`README.md`** - Project overview and scope

### Supporting Directories
- **`discussion-docs/`** - Documentation from specification discussions (not for final spec)
- **`ANCILLIARY.md`** - Older version of FAQ (likely to be removed)

## Workflow & Change Process

### Change Management Rules
1. **Always reference FAQ.md** when making changes to SPEC.md
2. **If your SPEC.md change contradicts or invalidates something in FAQ.md**, the PR must include updates to both files
3. **For substantial SPEC.md changes without existing FAQ coverage**, add corresponding FAQ entries

### Standard Workflow
1. Discuss via GitHub issues
2. Once agreed, create pull request
3. Review PR in weekly calls
4. Implement agreed changes

## Important Notes
- This specification is for measuring carbon emissions of AI systems (both classical AI and generative AI)
- Target audience: AI practitioners, developers, data scientists, engineers, decision-makers
- Goal: Provide methodology for calculating Software Carbon Intensity (SCI) scores for AI systems
- Status: Pre-draft standard (not yet approved by Green Software Foundation)

## When Making Changes
- **Read SPEC.md** to understand current specification
- **Read FAQ.md** to understand rationale behind current structure
- **Check if changes affect FAQ accuracy** and update accordingly
- **Consider if new FAQ entries are needed** for substantial changes