# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

This is a single-file HTML prototype for **Barbearia Leão de Judá**, a barbershop appointment booking mobile app. The entire application lives in `leao_de_juda_identidade_visual.html` and can be opened directly in any modern browser — no build step, no dependencies, no server required.

## Architecture

The file is structured in three sections (all inline):

1. **CSS** — CSS custom properties define the design tokens (brand colors, typography). The layout simulates a 375px-wide iPhone frame with an inner 351px viewport. Screen visibility is controlled by toggling a `.active` class.

2. **HTML** — Each app screen is a `<div id="s-*">` container:
   - `s-land`, `s-login`, `s-otp`, `s-register` — onboarding flow
   - `s-home` — main dashboard
   - `s-sched1` → `s-sched4` → `s-success` — 4-step booking flow
   - `s-hist`, `s-assin`, `s-profile` — secondary screens

3. **JavaScript** — Vanilla JS at the bottom of `<body>`. Key globals:
   - `go(id)` — navigates between screens by toggling `.active`
   - `selSvc`, `selPrc`, `selDur`, `selDt`, `selHr` — booking state
   - `pickSvc()`, `pickDate()`, `pickTime()` — update state + UI highlights
   - `doVerify()` — accepts OTP `1234` as the demo code

## Design Tokens (dark theme)

```css
--brand: #BB9629        /* dourado — cor primária da identidade */
--brand-dark: #9A7A1F   /* dourado escuro (hover/active) */
--brand-light: #1C1808  /* tint escuro para estados selecionados */
--brand-red: #B53E2B    /* vermelho da logo (acento secundário) */
--brand-gold-light: #E5D5A1  /* dourado claro (highlight) */
--bg: #0A0A0A           /* fundo do app */
--surface: #141414      /* cards e headers */
--surface2: #1F1F1F     /* inputs e chips */
--border: #2A2A2A
--text: #F0EAD6         /* off-white quente, combina com o dourado */
--text2: #A09880
--green: #27AE60
```

Fonts: **Poppins** (headings/bold), **Inter** (body) — loaded from Google Fonts.

## Logos

- `img/Logo 1.svg` — brasão/ícone isolado, tudo em `#BB9629`. Ideal para fundos escuros.
- `img/Logo 2.svg` — logo completa com texto, usa `#BB9629`, `black` e `#B53E2B`. Para fundos claros.

## Regra de contraste

Todo texto/ícone sobre fundos `--brand` (dourado) usa `color: #0a0a0a` (escuro), nunca `#fff`.

## Services & Pricing

| Service | Price | Duration |
|---|---|---|
| Corte navalhado | R$ 45 | 45 min |
| Manutenção da barba | R$ 35 | 30 min |
| Corte + Barba | R$ 70 | 1h 15min |
| Limpeza de pele | R$ 60 | 1h |
| Sombrancelha | R$ 20 | 15 min |

Subscription plans: **Básico R$ 89/mês**, **Premium R$ 149/mês**.
