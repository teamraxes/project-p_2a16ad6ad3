# Belbes Studio — Site Generation Prompt

**Project:** `p_2a16ad6ad3`
**Tariff:** landing
**Niche:** plumbing-supply

This prompt drives Claude Design's Pages generation, **after** the Design System is published. Attached files (paperclip): `composition.json`, `brief.json`, `creative_direction.json`. The DS already encodes typography/colors/components — this prompt focuses on layout grid, sitemap, и per-page content briefs.


---

## Grid Logic

*Component:* `cmp_full_bleed_editorial_pacing@1.0.0`

# Magazine-spread full-bleed hero rhythm

**Axis:** `grid_logic`
**Component ID:** `cmp_full_bleed_editorial_pacing`

## When this component is selected

См. `vector_centroid` (density=0.32 → sparse band) + `niche_affinity`.

## Pattern signals

- `full-bleed-hero` (3×)
- `low-density-editorial` (2×)
- `vertical-sidebar-nav` (1×)
- `asymmetric-vertical-nav` (1×)
- `magazine-pacing-rhythm` (1×)
- `full-bleed-aerial-hero` (1×)
- `3-col-sub-brand-section` (1×)
- `manifest-footer-display` (1×)
- `5-section-low-density` (1×)
- `full-bleed-interior-hero` (1×)

## Grid directives 

**Column structure:**
- Columns: **2**
- Breakpoints: [320, 768, 1024, 1440] (mobile / tablet / laptop / desktop)
- Hero layout: **full-bleed**

**Density profile (`sparse`):**
- Row rhythm: 24px baseline grid
- Gutter: 48px between columns
- Margin: 96px page padding
- Section count target: ~6 sections
- Rhythm: **accelerating**

**Section pacing details:**
- Accelerating — sections shorter as user scrolls deeper (editorial)

## Anti-patterns

- вертикальный sidebar nav требует серьёзного UX-investment; без продуманной реализации сбивает пользователей, ожидающих стандартную топ-навигацию
- tracklist layout works только для venue с реальной music programming; для cafe/restaurant без концепции = неуместно

---

## Sitemap


**Page strategy:** single  |  **Responsiveness:** single_responsive


**Rationale:** Landing tariff: one CTA-driven page concentrating all credibility (heritage, brand portfolio, two physical showrooms, contact) toward a single conversion goal — drive Oakland walk-in foot traffic to the Kohler Showroom at 415 40th Street.


- **/home** [landing, responsive]

    - `hero` — Anchor message — 'Specialty plumbing for the East Bay since 1980' — with primary CTA to visit the Kohler Showroom; rejects the category-default emergency-call hero pattern.

    - `brands` — Kohler, Grohe, A.O. Smith, Takagi — paired with the product category each brand covers (kitchen/bath fixtures, faucet/shower systems, tankless water heaters). Merges brief's required `brands` and `what_we_sell` into one section to respect landing's 5-section ceiling.

    - `showrooms` — Treat the Kohler Showroom and Bathroom Showroom as a physical destination — fixture vignettes from inside 415 40th Street, framed as 'come touch the premium brands' rather than a paragraph mention.

    - `family_history` — Forty-six years, same East Bay block, third-generation family ownership — heritage as visual structure (founding year, named generations) instead of buried About-page paragraph. Load-bearing trust signal vs. franchise rollups and big-box.

    - `contact` — Address, Mon–Fri 7:00–4:30 hours, phone 510-652-7437 (contractor-priority), and a low-key custom-request form. Phone-first secondary CTA respects how trade buyers actually transact.


---

## Brief Highlights


**Main message:** Specialty plumbing for the East Bay since 1980 — come touch the premium brands at our Oakland showroom.


**CTA goal:** visit_showroom


**Target audience:** East Bay Area contractors (quick price/availability checks) + new residential customers (Google searches for Kohler/Grohe in Oakland) — both need to feel they're talking to a real specialty supplier, not a chain.


**Key offers:**
- Kohler kitchen and bathroom fixtures (showroom-displayed)
- Grohe faucets and shower systems
- A.O. Smith and Takagi tankless water heaters
- Flexible piping, fittings, and standard plumbing supply


**Required sections:**
- hero
- brands
- showrooms
- family_history
- what_we_sell
- contact



## Image Briefs


### 1. role=hero_main

```json
{
  "role": "hero_main",
  "type": "photo",
  "default_dimensions": "1920x1080",
  "prompt_seed": "Editorial interior vignette inside an Oakland specialty plumbing showroom: a polished Kohler chrome and brass kitchen faucet on a honed soapstone counter, late-afternoon warm side light from an industrial-sash window, soft shadow on a cream plaster wall, a single neatly coiled copper supply line catching highlight in the foreground; restrained, magazine-quality, no people, no stock-photo smile, no plumbing-clipart props, no blue-and-white retail signage. Mood: trade-grounded heritage, third-generation specialty supplier — not a chain store.",
  "model": "google/gemini-3.1-flash-image-preview",
  "viewport_variants": [
    {
      "viewport": "desktop",
      "aspect_ratio": "16:9",
      "exact_dimensions": "1920x1080",
      "crop_intent": "subject_centered"
    },
    {
      "viewport": "tablet",
      "aspect_ratio": "4:3",
      "exact_dimensions": "1024x768",
      "crop_intent": "subject_centered"
    },
    {
      "viewport": "mobile",
      "aspect_ratio": "9:16",
      "exact_dimensions": "1080x1920",
      "crop_intent": "subject_centered"
    }
  ],
  "used_in_pages": [
    "home"
  ]
}
```



---

## Output Format

Generate a complete static multi-page website implementing the Design System и this site brief.

**Required pages:** /home.
**Required asset:** `assets/styles.css` (shared CSS with semantic tokens matching the published Design System).

Constraints:
- All HTML must be valid HTML5 with semantic landmarks (`<header>`, `<main>`, `<footer>`, `<nav>`).
- All inter-page links must be relative.
- Do NOT use Tailwind utility classes — write plain CSS only.
- Do NOT use Lorem ipsum — use real content driven by the brief.
- Hero must surface main_message in <30s scan.
