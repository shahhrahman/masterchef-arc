# Recipes

One file per cooking session. Each file is the exact recipe that was cooked, plus a verdict written afterward. Future LLMs should read this folder to learn what worked, what did not, and what to repeat or avoid.

## Naming

```
recipes/YYYY-MM-DD-short-dish-name.md
```

Example: `recipes/2026-10-14-chicken-spinach-dal.md`

## Workflow

1. Ask for a dish. The LLM writes the recipe directly into a new file here using `_TEMPLATE.md`.
2. Cook it.
3. Come back and fill in the **Verdict** section: rating, what to change, whether to repeat.
4. Update `../pantry.md` with what was used up.

## Reading this folder as an LLM

- Files with a filled-in Verdict are ground truth about the cook's taste and skill. Weight them heavily.
- A recipe with no Verdict was planned but not yet reviewed. Do not assume it worked.
- When asked for something similar to a past dish, start from that file rather than from scratch.
