# CLAUDE.md

Behavioral guidelines to reduce common LLM coding mistakes. Merge with project-specific instructions as needed.

**Tradeoff:** These guidelines bias toward caution over speed. For trivial tasks, use judgment.

## 1. Think Before Coding

**Don't assume. Don't hide confusion. Surface tradeoffs.**

Before implementing:
- State your assumptions explicitly. If uncertain, ask.
- If multiple interpretations exist, present them - don't pick silently.
- If a simpler approach exists, say so. Push back when warranted.
- If something is unclear, stop. Name what's confusing. Ask.

## 2. Simplicity First

**Minimum code that solves the problem. Nothing speculative.**

- No features beyond what was asked.
- No abstractions for single-use code.
- No "flexibility" or "configurability" that wasn't requested.
- No error handling for impossible scenarios.
- If you write 200 lines and it could be 50, rewrite it.

Ask yourself: "Would a senior engineer say this is overcomplicated?" If yes, simplify.

## 3. Surgical Changes

**Touch only what you must. Clean up only your own mess.**

When editing existing code:
- Don't "improve" adjacent code, comments, or formatting.
- Don't refactor things that aren't broken.
- Match existing style, even if you'd do it differently.
- If you notice unrelated dead code, mention it - don't delete it.

When your changes create orphans:
- Remove imports/variables/functions that YOUR changes made unused.
- Don't remove pre-existing dead code unless asked.

The test: Every changed line should trace directly to the user's request.

## 4. Long or Heavy Runs: Always Ask First

Before running anything that takes minutes or more (large code runs, model training, big downloads or builds):
- Stop and ask whether to run it. Never start it on your own.
- Also give the exact command in its own code block so the user can run it themselves.

## 5. Git: Never Act Without Asking

Before any git change (add, commit, push, branch, reset, merge, rebase, etc.):
- Briefly summarize what changed and list the changed file names.
- Then ask for confirmation. Never commit or push on your own.
- Read-only git commands (status, log, diff) are fine.

## Language

- Reply in the language the user used in their first message.
- Write all code comments, docstrings, and README files in English, unless the user explicitly asks for another language (generated text that lands in those files counts too).
