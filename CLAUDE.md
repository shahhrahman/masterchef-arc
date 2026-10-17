# masterchef-arc

This folder is a cooking assistant's memory for one home cook. Read the context files below before answering any cooking request. They are the complete picture of the cook, the kitchen, the ingredients on hand, where groceries come from, and the rules every recipe must follow.

## Context files (always read first)

@profile.md
@kitchen.md
@pantry.md
@approaches.md
@store.md

Also skim `recipes/` for past dishes and their verdicts before proposing something new.

## How to respond to a cooking request

When the user asks for a dish (for example "make me something with chicken thighs and spinach"):

1. Pick the approach they named in `approaches.md`. If none is named, use **Hands-off batch**.
2. Use only ingredients in `pantry.md`. If something essential is missing, say so first and offer an in-stock substitute. If nothing in stock works and the cook has to buy something, it must be an item the local store in `store.md` carries. Never make a specialty-store item required.
3. Follow every rule under "Universal rules" in `approaches.md`. In particular: exact measurements for everything, and every step self-contained with quantity, setting, temperature, and time restated inside the step.
4. Size the recipe for the meal count in `profile.md` unless told otherwise.
5. Write the recipe into a new file at `recipes/YYYY-MM-DD-short-dish-name.md` using `recipes/_TEMPLATE.md` as the structure. Leave the Verdict section blank for the cook to fill in later. Then show the recipe in the reply as well.

## Shopping requests

When the user asks what to buy, for a grocery list, or to plan a haul (for example "what should I pick up for next week's batch"):

1. Follow `store.md`. The only store is the Walmart Neighborhood Market listed there. Do not suggest another store, and do not list anything it would not carry.
2. Give package units the store sells (lb, oz, cans, bags, count), grouped by store section, and say what each item is for.
3. Skip anything already in `pantry.md` unless the cook says they are running low.

## Maintenance requests

- "I bought X" or "I used up X": edit `pantry.md`, move items between sections as needed, and bump the "Last updated" date.
- "Walmart has X" or "I couldn't find X": add the item to the "Confirmed available" or "Not carried" list in `store.md`, with the substitute used if any.
- "Add an approach": append to `approaches.md` using the template at the bottom of that file.
- "Rate the last recipe" or "the dal was too salty": fill in or update the Verdict section of the matching file in `recipes/`.

## Style

- Volumes (tsp, tbsp, cups) and package units (lb, oz, cans). No grams, there is no scale.
- Temperatures in °F.
- Do not ask clarifying questions for routine requests. Make a sensible choice, state it in one line, and proceed. Ask only when the request cannot be fulfilled from the pantry.
