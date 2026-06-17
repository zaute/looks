# Copilot Instructions — AI Looks System

## What This Repository Is

A collection of AI agent prompt files for personal appearance optimization, targeted at a 55-year-old man. There are no build, test, or lint commands — all files are Markdown prompts and one static HTML dashboard.

## Architecture

```
image_director_agent        ← entry point; orchestrates all specialists
    ├── grooming_agent      (facial geometry, beard design, skincare routines)
    ├── stylist_agent       (wardrobe, capsule building, color analysis)
    ├── haircut_agent       (hair for men 50+, barber brief output)
    ├── mature_skincare_agent (age-specific AM/PM routines, actives)
    └── fitness_agent       (physique, posture, clothes-fit focus)

skills/
    └── weekly_checkin      (structured weekly progress review)

my-plan/                    ← user's personal output files (not templates)
site/index.html             ← static HTML dashboard displaying the plan
docs/superpowers/           ← design specs and implementation plans
```

`image_director_agent` is the master coordinator. It routes user input to relevant specialists and synthesises all outputs into one prioritised action plan (Immediate Wins / Short-term / Ongoing Habits). Each specialist agent is also fully usable standalone.

## Agent Authoring Conventions

**Every agent must include:**
- A `## Role & Persona` section defining the agent's specialist identity
- A `## Core Capabilities & Execution Steps` section with numbered steps
- A `## Strict Rules` section (hard limits, never-do items)
- A `## Response Formatting Guidelines` section
- A `**"Why This Works"**` subsection in all substantive responses — explaining the science or logic behind recommendations

**Never include generic filler** such as "Confidence is your best accessory." All recommendations must be specific, actionable, and tied to the user's profile.

**Target audience framing:** All agents are built around a 55-year-old male user. Recommendations must reflect this context (joint-safe programming, men's 50s skin physiology, greying/thinning hair strategies, etc.).

## Critical Cross-Agent Rules

These rules apply whenever `grooming_agent` and `mature_skincare_agent` are both active — `image_director_agent` runs an explicit ingredient conflict check (Step 4):

| Ingredient | Rule |
|-----------|------|
| Vitamin C (L-Ascorbic Acid) | **AM only** — always include when skin concerns are present |
| Retinoids | **PM only** — do not recommend as a Week 1 action; barrier must be stable first |
| AHA/BHA | **PM only** — must alternate with retinoid nights, never same night |
| Retinoids + AHAs/BHAs | **NEVER** combine in the same application |
| Retinoids + Vitamin C | **NEVER** apply simultaneously |

If the user reports burning, stinging, or peeling, immediately switch to Barrier Repair Protocol (ceramides, HA, Centella Asiatica — halt all actives for 1–2 weeks minimum).

## Output Format Conventions

- **Outfit blueprints** (stylist_agent): Silhouette Focus → Palette (hex approximates) → Blueprint (top/base/trousers/shoes/accents) → Fit Warning
- **Skincare routines** (grooming_agent, mature_skincare_agent): numbered AM/PM steps in sequence
- **Fitness programmes** (fitness_agent): Day-by-day, sets × reps, with style connection per block
- **Haircut recommendations** (haircut_agent): lead with reasoning, then Barber Brief in a copyable `code block`
- **Weekly check-in** (skills/weekly_checkin): 10 questions → 0–2 scoring per area → three-horizon summary
- **Master plan** (image_director_agent): tagged by source agent in brackets, three-horizon structure

## Specialist-Specific Logic Notes

**stylist_agent — Color Analysis:**  
Maps user to a seasonal palette via undertone (vein/jewellery/sun tests) + contrast level. Outputs: best colours with hex, accent colours, wardrobe neutrals, and colours to avoid. All outfit blueprints must reference the assigned palette.

**haircut_agent:**  
Never recommend a comb-over. Never recommend hair dye unless explicitly requested. Embrace grey. Every recommendation ends with a Barber Brief in exact copy-paste format.

**fitness_agent:**  
Priority stack: posture → upper body → core → lower body → cardio. Every exercise recommendation connects to a clothing/appearance outcome. Default to joint-safe alternatives (goblet squat over barbell squat, no behind-the-neck movements).

**mature_skincare_agent — Priority Stack:**  
SPF 50 → Sleep → Hydration → Retinoid → Vitamin C → Peptides → HA → Niacinamide. Lower numbers give faster visible returns and should be addressed first.

## my-plan/ Directory

Contains the user's actual personal outputs (e.g., `colour-palette.md`, `fitness-plan.md`, `skincare-shopping-list.md`). These are personalised files generated from agent interactions, not templates. Treat them as living documents that may be updated as the user's situation evolves.

## site/index.html

A single-file static HTML dashboard (dark theme, sidebar nav, CSS variables for the personal color palette). No framework, no build step. Edit directly. Color variables at the top of the `<style>` block correspond to the user's assigned seasonal palette.
