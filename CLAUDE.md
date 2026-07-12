# Sipelle Website


## Project Purpose
A flat html website that will be hosted on cloudflare works or pages. This website is in support of the phone app sippelle.




## Design System

The website must match the Sipelle app's look and feel. The app's design system is ported into `design-system/` (every file byte-identical to the app handoff except `WEB-NOTES.md`; upstream: `D:\GITHUB\sipelle\design\design_handoff_sipelle_app` — to change the design, edit upstream and re-copy, never edit the copies in place).

When building ANY page (the landing page included):

- Link `/design-system/styles.css` — all colors, typography, spacing, radii, and shadows come from its CSS custom properties. Never hardcode values or invent new tokens.
- Follow the brand rules in `design-system/readme.md`: soft watercolor identity — painted washes as backgrounds (ship as images, never flat white or CSS gradients), Playfair Display serif for display type, Caveat for handwritten accents, system sans for body, soft warm shadows, generous radii, no hard borders, no photography, no emoji.
- Read `design-system/WEB-NOTES.md` before styling: the token type scale is phone-scale (@2x, 768px mockups) — remap for desktop; fonts and icons are Google-Fonts/Lucide substitutions.
- Match the app visually: `design-system/reference/original-screens/` are the real app screens and `design-system/spec-sheet.html` renders every token and component — pages here should feel like they belong to the same product.
- Reuse the artwork in `design-system/assets/` (wordmarks, hero cocktail, drinks, category art, washes) rather than inventing new art.

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

## 4. Goal-Driven Execution

**Define success criteria. Loop until verified.**

Transform tasks into verifiable goals:
- "Add validation" → "Write tests for invalid inputs, then make them pass"
- "Fix the bug" → "Write a test that reproduces it, then make it pass"
- "Refactor X" → "Ensure tests pass before and after"

For multi-step tasks, state a brief plan:
```
1. [Step] → verify: [check]
2. [Step] → verify: [check]
3. [Step] → verify: [check]
```

## Execution Rules
Claude MUST start in Plan Mode.
Claude may modify existing .prd files without needing permission.


## Always Do First

- **Plan Mode** Always start in plan mode.

- **Invoke the `frontend-design` skill** before writing any frontend code, every session, no exceptions. Design source of truth: the "Design System" section above and `design-system/`.

- **agent teams** always invoke agent teams to do the work, you should use 3 team mates minimum, never do the work in the main context window. The main context window should only manage teams and agents.

- **Sequential Thinking** Use "Sequential Thinking" for complex decisions.

- **Never do a git commit** Unless expressly told my the user