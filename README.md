# masterchef-arc

Context files for LLM-assisted cooking. Paste or attach these before asking for a recipe so the model knows the cook, the kitchen, the ingredients on hand, where groceries come from, and the rules every recipe must follow.

## Files

| File | What it holds | How often it changes |
|------|---------------|----------------------|
| `profile.md` | Who is cooking: body stats, eating pattern, meal count | Rarely |
| `kitchen.md` | Appliances and measuring tools available | Rarely |
| `pantry.md` | Every ingredient currently in the kitchen | Often (after each grocery run or cook) |
| `approaches.md` | Universal recipe rules, plus named cooking modes (time, effort, batch size) | Occasionally (when a new mode is added) |
| `store.md` | The one grocery store within walking distance, and what can realistically be bought there | Rarely (the lists at the bottom grow as you shop) |
| `recipes/` | One file per cooking session: the recipe as cooked, plus a verdict afterward | Every cook |
| `CLAUDE.md` | Auto-loaded by Claude Code. Pulls in the files above and tells the model how to respond | Rarely |

## How to ask for a recipe

**With Claude Code:** open a session in this folder and just ask. `CLAUDE.md` loads the context automatically.

**With any other LLM:** paste or attach the five context files, then a one-liner like:

```
Make me a dish with chicken thighs and spinach using the "Hands-off batch" approach.
```

The model should:

1. Use only ingredients listed in `pantry.md` unless told otherwise. If a dish needs something missing, say so up front and offer a swap.
2. Follow every rule under "Universal rules" in `approaches.md`.
3. Follow the constraints of the named approach (pot, batch size, hands-on time).
4. Size the recipe for the meal count in `profile.md` unless the request says otherwise.
5. Suggest buying only what the store in `store.md` carries. No specialty-store trips.

## Instructions for the LLM reading this

- Treat `pantry.md` as the source of truth for what exists. Do not assume common staples (onion, garlic, tomatoes, butter) unless they are listed.
- Exact measurements for every ingredient, including salt, water, and oil. The cook does not cook by feel.
- Every step must be self-contained: restate the quantity, temperature, pressure setting, and time inside the step. The cook should never scroll back to the ingredient list.
- Anything the cook is told to buy must be available at the store in `store.md`. Assume a standard American supermarket, not an Indian or Asian grocer.
- If something in these files is ambiguous or missing, ask one short question before writing the recipe.
