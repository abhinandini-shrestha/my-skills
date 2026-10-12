---
name: my-brand
description: Abhinandini Shrestha's personal brand. Use whenever creating, styling or reviewing any UI, web page, component, README, slide or graphic for Abhinandini's projects, so everything matches her portfolio's look and voice.
---

# Abhinandini's Brand

Clean, light, modern, with a calm blue → purple → pink gradient, generous whitespace,
thin headings, rounded shapes, and one playful developer touch: a terminal.
Copy exact values from `tokens.css` in this folder. Prefer Tailwind + shadcn/ui + motion (framer-motion).

## 1. Color

| Role | Value | Tailwind |
|---|---|---|
| Brand gradient (signature) | #3b82f6 → #8b5cf6 → #ec4899 | `from-blue-500 via-violet-500 to-pink-500` |
| Accent gradient (text highlights) | #2563eb → #9333ea | `from-blue-600 to-purple-600` |
| Primary solid | #2563eb | `blue-600` |
| Text | #111827 / dark: #ffffff | `gray-900` / `dark:text-white` |
| Muted text | #4b5563 / dark: #9ca3af | `gray-600` / `dark:text-gray-400` |
| Page background | #f9fafb / dark: #030712 | `gray-50` / `dark:bg-gray-950` |
| Surface (cards) | #ffffff / dark: #111827 | `bg-white` / `dark:bg-gray-900` |
| Success / "open to work" | #10b981 | `emerald-500`, text `emerald-700` |
| Terminal | bg #000, text #4ade80, prompt #60a5fa, headings #facc15 | `black`, `green-400`, `blue-400`, `yellow-400` |

Rules:
- The gradient is the signature. Use it sparingly: one word of a headline, a photo border, a header bar. Never as a full-page background.
- Hero backgrounds use the pale wash `from-blue-50 via-purple-50 to-pink-50` with two blurred orbs and a faint grid.
- Every color must work in dark mode. Always write the `dark:` variant.
- Body text meets WCAG AA contrast (4.5:1). Never light gray text on white.

## 2. Typography

- Font: the project's default sans (system / Inter-style). Monospace only for terminal and code.
- Headings are **light and tight**: `font-light tracking-tight`. Never heavy bold headlines.
- Scale:
  - Hero name: `text-5xl sm:text-6xl md:text-7xl font-light leading-[1.05]`
  - Section title: `text-4xl md:text-5xl font-light tracking-tight`, centered
  - Section subtitle: `text-lg text-gray-600 dark:text-gray-400`, centered, below the title
  - Card title: `text-xl font-semibold`
  - Body: `text-base leading-relaxed` (cards: `text-[15px]`)
  - Small label: `text-xs font-semibold uppercase tracking-widest text-muted-foreground`
- Highlight one key word in a headline with the accent gradient:
  `bg-gradient-to-r from-blue-600 to-purple-600 bg-clip-text text-transparent`

## 3. Layout & spacing

- Sections: `py-24 px-4`, content in `max-w-6xl mx-auto` (hero: `max-w-7xl`).
- Section header block: `text-center mb-16`.
- Grids: `grid grid-cols-1 md:grid-cols-2 lg:grid-cols-3 gap-8`.
- Two-column sections (photo + text): `lg:grid-cols-[2fr_3fr] gap-10 lg:gap-12 items-start`; the photo can be `lg:sticky lg:top-24`.
- Inside cards: `p-6 md:p-8`, sections separated by `space-y-5`.
- Mobile first: everything stacks below `lg`. Center text on mobile, left-align on desktop (`text-center lg:text-left`).

## 4. Components

**Buttons** (always `rounded-full`)
- Primary: `rounded-full px-6 bg-gray-900 text-white hover:bg-gray-800 dark:bg-white dark:text-gray-900 hover:scale-105 transition-all duration-300`
- Secondary: `variant="outline"` + `rounded-full px-6 border-2 hover:scale-105`
- Icon links: `p-2.5 rounded-full hover:bg-primary/10`, icon `h-5 w-5 text-muted-foreground group-hover:text-primary`
- Add a trailing arrow on the main CTA that nudges on hover (`group-hover:translate-x-1`).

**Cards**
- `bg-white dark:bg-gray-900 rounded-2xl p-8 border border-gray-100 dark:border-gray-800 shadow-sm hover:shadow-xl hover:-translate-y-1 transition-all duration-300`

**Icon tile** (top of feature cards)
- `w-16 h-16 rounded-xl bg-blue-600 flex items-center justify-center`, white lucide icon `h-8 w-8 strokeWidth={1.75}`, `group-hover:scale-110`.

**Checklists**: lucide `Check` in `text-blue-600 dark:text-blue-400`, `h-4 w-4`, text `text-sm text-gray-600`.

**Chips**
- Trait/focus chips: `rounded-full bg-muted px-3 py-1 text-xs font-medium`
- Glass chips on hero: `rounded-full bg-white/70 dark:bg-white/5 border border-gray-200 dark:border-gray-800 backdrop-blur px-3 py-1 text-sm`
- Skills: plain text `items.join(' · ')` with a bold fixed-width label column. Compact beats chip clouds.

**Status pill** ("Open to …"): `rounded-full border border-emerald-500/30 bg-emerald-500/10 text-emerald-700 dark:text-emerald-400 px-4 py-1.5 text-sm font-medium`, with a pinging emerald dot.

**Photo frame**: wrapper `rounded-2xl p-[3px] bg-gradient-to-br from-blue-600 via-purple-600 to-pink-500 shadow-xl`, image `rounded-[14px] object-cover aspect-[4/5]`.

**Terminal** (signature developer element)
- Card: `bg-black font-mono border-zinc-800 shadow-2xl`, title bar with red/yellow/green dots and a centered `name — zsh` title.
- Prompt `user@portfolio:~$` in `text-blue-400`; output `text-green-400`; section headers (`Usage:`) `text-yellow-400`; errors `text-red-400`.
- Welcome banner: the name in figlet **slant** font, then `Portfolio version 1.0.0 · tagline`.
- Supports `help`, `clear`, ↑/↓ history. Never autofocus on page load.

**Gradient header bar** (chat widgets, panels): `bg-gradient-to-r from-purple-600 to-blue-600 text-white`.

## 5. Motion

Use `motion/react`. Subtle and quick.
- Section entrance: `initial={{ opacity: 0, y: 30 }} whileInView={{ opacity: 1, y: 0 }} viewport={{ once: true, margin: '-100px' }} transition={{ duration: 0.6 }}`
- Grid items: stagger `delay: (index % 3) * 0.1`
- Side-by-side columns slide in from opposite sides (`x: -40` / `x: 40`).
- Hover: lift (`-translate-y-1`) or `scale-105`. Never bounce or shake.
- Background orbs rotate slowly (15–20s linear, infinite).
- Desktop-only parallax for the hero; disable scroll effects below `lg`.
- Respect `prefers-reduced-motion`.

## 6. Voice & content

- First person, warm and concise: "Hi, I'm Abhinandini…"
- Lead with real numbers: 6+ years, 15K+ docs/day, 30% faster review, high-volume ERP platform.
- No buzzwords ("cutting-edge", "passionate ninja", "rockstar"). No filler stats.
- **Never invent facts.** No placeholder people, fake companies, fake GitHub stats or certifications. If a fact is missing, write `[PLACEHOLDER]` and say so.
- Focus areas: Full-Stack · Data Engineering · AI / LLMs.

## 7. GitHub READMEs & graphics

- Header/footer: capsule-render waving banner, `color=0:3b82f6,50:8b5cf6,100:ec4899`, white text.
- Typing line: readme-typing-svg, `color=8B5CF6`, Fira Code.
- Badges: shields.io, `style=for-the-badge` for contact links and `flat-square` for tech stack.
- Include a `console` code block with the slant-font name banner to echo the portfolio terminal.

## 8. Accessibility checklist

- Real `<button>`, `<a href>`, and `<label>`; `aria-label` on every icon-only button or link.
- Decorative SVGs/icons: `aria-hidden="true"`.
- One `<h1>` per page (the name); headings in order.
- Touch targets ≥ 44px; visible focus states.
- Test light and dark mode and a 375px-wide phone before calling anything done.
- 
## 9. Choosing the context

First decide which kind of project this is, then apply the matching rules.
Sections 1–2 (color, type) and 8 (accessibility) apply to **both**.

### A. Showcase (portfolio, landing page, README, slides)
Use everything above: hero, orbs, grid background, big light headings,
first-person voice, terminal banner.

### B. Application (chat interface, LMS, dashboard, admin tool)
Same identity, but calmer and denser. The user is working, not browsing.

**Layout**
- App shell: left sidebar (`w-64`, collapsible) + top bar (`h-14`) + main content. Content `max-w-5xl` for reading views.
- Spacing tighter: page padding `p-4 md:p-6`, cards `p-4 md:p-5`, gaps `gap-4`.
- Type scale smaller: page title `text-2xl font-light tracking-tight`, section `text-lg font-semibold`, body `text-sm`/`text-base`.
- No hero, no orbs, no parallax, no grid background. Plain `bg-gray-50 dark:bg-gray-950`.

**Where the brand shows (keep it small)**
- The gradient appears in **one** place per screen: the logo mark, the active nav indicator, a thin top bar (`h-1`), or the primary send/submit button.
- Primary actions: `bg-blue-600 text-white rounded-full` (or `rounded-lg` for dense toolbars).
- Selected/active states: `bg-blue-50 text-blue-700 dark:bg-blue-950 dark:text-blue-300`.
- Progress bars, focus rings and links: `blue-600`.

**Chat interfaces**
- User bubbles: `bg-blue-600 text-white rounded-2xl rounded-br-md`.
- Assistant messages: no bubble or `bg-muted rounded-2xl rounded-bl-md`, full-width readable text, `leading-relaxed`.
- Assistant avatar: gradient circle (`from-purple-600 to-blue-600`) with a white icon.
- Input: `rounded-2xl` bar pinned to the bottom, send button with the gradient.
- Code blocks use the terminal palette (black bg, green/blue/yellow).
- Typing indicator: three bouncing dots. Auto-scroll to the newest message.

**LMS / dashboards**
- Course and lesson cards use the brand card style, but smaller (`rounded-xl p-5`).
- Icon tiles shrink to `w-10 h-10 rounded-lg`.
- Progress: `h-2 rounded-full bg-gray-200` track with a gradient fill.
- Tables: `text-sm`, zebra rows `even:bg-gray-50 dark:even:bg-gray-900/50`, sticky header.
- Status colors: emerald = complete, blue = in progress, gray = not started, red = overdue. Always pair color with a text label or icon.
- Every list needs empty, loading (skeletons) and error states.

**Motion in apps**
- Faster and smaller: `duration-150`–`200`, fades and 4–8px slides only.
- No entrance animations on content the user sees repeatedly.

**Voice in apps**
- Address the user ("Your courses", "Ask anything…"), not first person.
- Personal branding lives in the logo, colors, and a small "Built by Abhinandini Shrestha" footer link. It never appears in the product copy.

### C. Non-React or non-web projects
- Use `tokens.css` variables (or translate the hex values) for any framework.
- Native mobile, Figma, slides: use the same hex colors, gradient, radii and "light headings" rule.