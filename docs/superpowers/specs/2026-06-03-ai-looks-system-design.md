# AI Looks System — Design Spec
**Date:** 2026-06-03  
**User:** 55-year-old male looking to improve appearance using AI agents

---

## Goal

A set of AI agents that help a 55-year-old man look and feel his best — covering grooming, skincare, hair, wardrobe (including personal color analysis), and fitness. A single master agent coordinates all specialists and delivers one unified action plan per session. A weekly check-in skill tracks progress over time.

---

## Architecture

One **Image Director** master agent receives the user's input (description or photo context) and orchestrates calls to specialist agents. It synthesises their outputs into a single prioritised action plan. Specialists are independent files — each has a single clear purpose and can also be used standalone.

```
image_director_agent
    ├── grooming_agent         (existing)
    ├── stylist_agent          (existing — expanded with color analysis)
    ├── haircut_agent          (new)
    ├── mature_skincare_agent  (new)
    └── fitness_agent          (new)

skills/
    └── weekly_checkin         (new)
```

---

## Agent Specs

### `agents/image_director_agent.md` (new)
- Accepts a user description (face shape, hair, build, skin tone, lifestyle, goals) or photo context
- Routes relevant details to each specialist agent
- Synthesises all outputs into one unified, prioritised action plan
- Sections: Immediate Wins (week 1), Short-term (month 1), Ongoing habits
- Always references which specialist agent each recommendation came from

### `agents/grooming_agent.md` (exists — no changes needed)
- Facial geometry mapping, beard architecture, skincare routines
- AM/PM routine design, active ingredient management
- Safety protocols (no retinoid + Vitamin C clash, barrier repair protocol)

### `agents/stylist_agent.md` (expand with color analysis)
- **Existing:** Body architecture, wardrobe curation, capsule building, occasion matrix
- **Add — Color Analysis section:**
  - Determines skin undertone (warm / cool / neutral) from description or photo
  - Maps user to a seasonal palette (e.g. Deep Autumn, True Winter)
  - Outputs: best colours, colours to avoid, exact hex-approximate shades for key wardrobe items
  - Integrates colour recommendations into outfit blueprints

### `agents/haircut_agent.md` (new)
- Specialises in hair for men 50+: thinning, greying, receding hairlines
- Recommends cuts that work with (not against) current hair texture and density
- Beard shaping advice coordinated with hairstyle
- Outputs a "barber brief" — exact instructions to hand to a barber
- Considers face shape (from grooming agent data) for cut recommendations

### `agents/mature_skincare_agent.md` (new)
- Skincare specifically for men's skin in the 50s
- Focus areas: wrinkles, loss of firmness, uneven tone, dryness, sun damage
- AM/PM routine with age-appropriate actives (retinoids, peptides, Vitamin C, SPF 50)
- Product tier recommendations: budget / mid-range / premium
- Flags when to see a dermatologist vs. handle at home
- Dovetails with `grooming_agent` — no ingredient conflicts

### `agents/fitness_agent.md` (new)
- Exercise and body composition advice for men over 50
- Primary goal: build a physique that makes clothes fit better and improves posture
- Covers: resistance training, mobility, posture correction
- Realistic schedules (3–4 days/week)
- Safety-first: joint-friendly programming, warm-up protocols
- Connects posture improvements to style impact (how clothes drape)

### `skills/weekly_checkin.md` (new)
- A structured weekly review routine
- Reviews progress across: skincare, fitness, grooming habits, wardrobe updates
- Asks 5–7 targeted questions about the past week
- Outputs: what's working, what to adjust, top 3 priorities for the coming week
- Tracks which agent recommendations have been acted on

---

## Response Standards (all agents)

- No generic filler ("confidence is your best accessory" etc.)
- Always include a **"Why This Works"** section explaining the science or logic
- Recommendations tied to specific age-group context (55-year-old male)
- Structured outputs: numbered steps for routines, blueprint format for outfits

---

## Out of Scope

- Medical diagnosis or prescription advice
- Cosmetic surgery recommendations
- Diet / nutrition planning (outside of general fitness context)
