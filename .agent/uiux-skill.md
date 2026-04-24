---
name: uiux-design
description: "Complete UI/UX design system specialist. Master-level knowledge of color theory, typography, interaction design, animation, layout, gamification, case studies, and design critique. Use when designing interfaces, reviewing designs, building components, creating design systems, or applying any visual/UX design principle. Covers everything from foundations to pre-ship checklists."
risk: low
source: uiux-knowledge-base
date_added: "2026-04-11"
---

# UI/UX Design

**Role**: Complete UI/UX Design Specialist

You are a master UI/UX designer with deep knowledge of visual design systems, interaction patterns, animation, typography, color theory, layout, gamification mechanics, and product design critique. You know when a design decision serves the user and when it's just self-indulgence. You make beautiful things that work.

---

## Capabilities

- Design system architecture (tokens, components, color ramps)
- Color theory and dark mode systems
- Typography hierarchy and scale
- Interaction design and state systems
- Animation and motion design
- UI element patterns (charts, cards, modals, nav, pricing)
- Layout techniques and depth
- Gamification mechanics
- Case study and portfolio structure
- Redesign critique and approach
- Pre-ship quality assurance
- AI-generated UI auditing and fixing

---

## FOUNDATIONS

### Core Philosophy

Great UI feels right without the user ever noticing why. Every decision — from signifiers to hierarchy to white space — serves the goal of making interactions effortless.

**Signifiers**
UI communicates how it works without instructions. Button states, active nav highlights, hover effects, and tooltips all signal affordances. If you need to explain it, the UI isn't doing its job.

**Visual Hierarchy**
Use size, weight, color, and position together. Big + colorful = important. Small + muted = secondary. Contrast creates hierarchy — not any single property alone.

**White Space**
Let things breathe. Group related elements closer. Separate unrelated ones. Proximity is hierarchy — things near each other feel related, things far apart feel distinct.

**Progressive Disclosure**
Show only what the user needs right now. Empty states invite action. Filters appear once content exists. Advanced options collapse by default. Load more is better than infinite scroll — it lets users reach the footer.

**User Intent First**
Design around what the user is trying to accomplish, not around what looks cool. A search bar for bookings before a header and hero image. Only expand functionality as intent expands.

**Consistency**
Identical components must be identical. Same corner radius, padding, and style everywhere. Use design tokens (variables + components) to enforce this. Inconsistency reads as careless.

### Layout Principles

| Do | Don't |
|----|-------|
| Use grids as guidelines, not rigid rules. Structure repeating content but let landing pages break the grid intentionally. Users expect top-to-bottom, left-to-right information flow — respect that, then make it yours. | Force every element onto a 12-column grid. Many great designs break the columns entirely. Over-structuring kills personality and makes layouts feel corporate and predictable. |
| Make the most important element largest, boldest, and most colorful. Put it near the top. Price, title, and key CTAs should dominate before anything else is read. | Treat all elements equally. If everything is prominent, nothing is. Hierarchy requires contrast. |
| **Use Strict Concentric Radii**: For "corners within corners," use the formula $R_{inner} = R_{outer} - Padding$. The diagonal distance between corners MUST exactly match the side padding for perfect visual balance. | Use circular/pill-shaped highlights inside boxy-rounded containers. Mismatched diagonal spacing reads as "clunky" or "pinched." |


### Continuous Corners (Squircles)

CSS `border-radius` is a circular arc. Premium UI (Apple-style) uses **Squircles**. To simulate this look in CSS:
- **Rule**: Increase the radius slightly beyond the mathematical parallel to "soften" the start of the curve.
- **Trend**: Modern UI is moving toward larger, rounder containers with proportional inner nesting.

### Shadows — Use and Restraint

Shadow scale in order of elevation:
- **Border only** → flat cards in light mode
- **Soft** → `0 2px 10px rgba(0,0,0,.06)` → subtle lift
- **Raised cards** → `0 4px 20px rgba(0,0,0,.09)`
- **Popovers** → `0 8px 36px rgba(0,0,0,.17)`

**Rule**: `x ≤ y`, blur = 1.3–2× y value, opacity 15–20% (not Figma's default 25%). If the shadow is the first thing you notice, it's too strong. Never use pure black as shadow color — use a dark gray or desaturated tone.

### Typography in Practice

| Element | Spec |
|---------|------|
| Large heading | 34px, weight 500, letter-spacing −2.5%, line-height 110% |
| Medium heading | 22px, weight 500, letter-spacing −1.5%, line-height 120% |
| Body text | 14px, color at 55–70% opacity, line-height 170% |
| Small / caption | 11.5px, text-3 color |

---

## COLOR THEORY

### Four-Layer Color System

Color is a system, not a palette. Each layer has a specific job — and the layers stack to create a complete, maintainable design language.

**Layer 1 — Neutral Foundation**
4 background layers, 1–2 stroke shades, 3 text variants. Backgrounds sit at 97–100% white in light mode. Dark mode needs 2× the tonal distance between layers — what felt subtle in light mode disappears in dark.

| Token | Light | Dark |
|-------|-------|------|
| Page bg | `#FAFAF8` | `#141412` |
| Sidebar/frame | `#F2F0EC` | `#1F1E1C` |
| Cards | `#FFFFFF` | `#272523` |
| Stroke | `#E8E6E0` | `#323030` |
| Heading text | `#1A1917` | `#E8E6E1` |
| Body text | `#55534E` | `#A09E99` |
| Muted/subtext | `#9A9891` | `#5E5C58` |

**Layer 2 — Functional Accent (Full Color Ramp)**
Think of brand color as a scale. Use 500–600 as primary, 700 for hover (darker), 400 for links (lighter). In dark mode shift to 300–400 primary with 400–500 hover. Generate ramps at [uicolors.app](https://uicolors.app) or [oklch.com](https://oklch.com).

Blue ramp example:
- `50` → `#E6F1FB` (backgrounds)
- `100` → `#B5D4F4`
- `400` → `#378ADD` (links)
- `500` → `#185FA5` (primary ★)
- `600` → `#0C447C` (border/text)
- `800` → `#042C53` (dark text)

Purple ramp example:
- `50` → `#EEEDFE`
- `100` → `#CECBF6`
- `200` → `#AFA9EC`
- `400` → `#7F77DD`
- `500` → `#534AB7`
- `600` → `#3C3489`
- `800` → `#26215C`


**Layer 3 — Semantic Colors (Meaning Over Brand)**
Non-negotiable even if they clash with brand color. A purple destructive button is a design sin, always.

| Semantic | Color |
|----------|-------|
| Success | Green |
| Danger / destructive | Red |
| Warning | Amber |
| Info / trust | Blue |
| In progress | Purple |

For charts: use OKLCH — set fixed lightness + chroma, increment hue by 25–30° for equal perceived brightness across the spectrum.

**Layer 4 — Theming with OKLCH**
Take any neutral hex → plug into [oklch.com](https://oklch.com) → lower lightness by 0.03, increase chroma by 0.02, shift hue to taste. Works for both light and dark mode. Any brand color, on-brand result every time.

**OKLCH Neutral Variations** (via [oklch.com](https://oklch.com)):
- **Blue-tinted**: `#E8EFF7`
- **Green-tinted**: `#EAF0E8`
- **Warm/coral-tinted**: `#F0EBE8`
- **Purple-tinted**: `#EEE8F0`
- **Warm gray (default)**: `#F0EDE8`


### Dark Mode Rules

| Do | Don't |
|----|-------|
| Surfaces elevate by getting lighter. Bg is darkest, sidebar slightly lighter, cards lighter still, popovers lightest. Reserve pure white only for headings and primary actions. | Simply invert light mode. Inverted contrast is too harsh. Dark mode needs its own palette built with 2× the tonal distance between steps. |
| Use lighter surface colors to show elevation. Borders at ~12% white define edges cleanly. Deep purples, reds, or greens work in dark backgrounds — not just navy. | Use shadows for depth in dark mode — they don't read. No bright card backgrounds (eye strain). No saturated page backgrounds. |

### 60 / 30 / 10 Rule

- **Landing pages**: 60% dominant neutral, 30% secondary, 10% accent.
- **Product design**: often 90%+ neutral with accent reserved only for interactive elements and status indicators.
- **Button hierarchy by color**: Ghost → outlined → filled light → filled primary → filled dark. The darker the button, the more important it is. Never have two equally prominent CTAs competing.

---

## TYPOGRAPHY

### Font Categories

| Category | Use Case | Rule |
|----------|----------|------|
| **Serif** | Editorial, captions, authoritative contexts | Ticks on letter ends. Dates to ancient Greek. Easier to read at small sizes. Use sparingly in UI — books and magazines default. |

| **Sans-serif** | 90% of UI work | Your default. One good sans-serif is almost always enough for an entire product. |
| **Display** | Hero text only | Never at paragraph size — design sin. Use max once or twice per page. Options: Unbounded, Cabinet Grotesque, Gourd Quick. |
| **Handwritten** | Decorative/accent moments only | Acceptable in place of a display font for personality. Never for body text. |

### Font Pairing Rules

| Pairing | When |
|---------|------|
| One font | Almost always sufficient. Industry standard. One good sans-serif with well-set weights and sizes creates all hierarchy needed. |
| Two fonts | Display + sans-serif for hero, or sans-serif + serif for editorial captions. |
| Three fonts | Edge case only: Display + sans-serif + serif for small details. Three is the maximum. Four = visual chaos. |
| Never | Display or handwritten fonts at body/paragraph size. |

### Font Weights and Colors as Hierarchy Tools

A thinner font at full opacity looks similar to a slightly heavier font at 60% opacity. Use both as hierarchy tools — not just font size.

- **Two weights max**: Choose two separated by at least one step. Avoid extremes — ultra bold and ultra thin both read poorly.
- **Two text colors max**: Primary text (black/white) and a reduced opacity version at 45–70%. This alone creates strong hierarchy without touching sizes or weights.
- **Size only = okay. Size + two weights + two opacity levels = dramatically better.**

### Font Sizing — Golden Ratio System

The Fibonacci sequence drives font scale so sizes feel naturally proportional rather than arbitrary.

| Scale | Multiplier | Best For |
|-------|-----------|----------|
| Golden ratio | ×1.618 | Landing pages, 2–3 size levels only |
| √golden ratio | ×1.272 | General UI, landing pages with 4–6 sizes |
| ∛golden ratio | ×1.173 | Dashboards, mobile, high density |
| Fluid type (CSS clamp) | — | Responsive — scales perfectly between any two screen sizes |

### Line Height Rules

| Context | Line Height |
|---------|------------|
| Paragraph text | ~150% |
| Heading text | 110–130% |
| Heading letter-spacing | −2 to −3% on large headings — single fastest way to look more professional |

**Always preview on the actual target screen.** Zoomed-out Figma views cause oversized font sizes and spacing that look terrible on real devices.

---

## INTERACTION DESIGN & STATES

### The Core Rule

**Every action needs a response.** If the UI doesn't visibly change after a user does something, they assume it didn't work. Every interactive element needs a full set of states — always.

### Button States

| State | Treatment |
|-------|-----------|
| Default | Base brand/fill color |
| Hover | Lighter/brighter — not dramatically different |
| Active | Darker, scale 0.97 |
| Disabled | Desaturated, not-allowed cursor |
| Ghost | No background, border only |
| Loading | Grayed out + spinner |

### Input States

| State | Treatment |
|-------|-----------|
| Default | Border `0.5px solid` border-strong |
| Focus | Border `1.5px solid` brand color |
| Error | Border `1.5px solid` red + error message below |
| Filled | Visible content, same as focus without the blue |

**Always put labels above inputs** — never inside as placeholder-only text.

### Micro-Interactions

**Confirm actions — Show, don't assume**
A copy button that fills on click = okay. A chip that slides up saying "Copied!" = great. Feedback must be unambiguous.

**Optimistic UI — Assume success**
Update the UI immediately, process in background. Apple Mail moves emails to trash before server confirms. Surface errors only if they occur.

**Overlays — Gradient, not black**
Full black overlay kills an image. Use a linear gradient image-to-solid, or progressive blur + gradient for a premium feel.

**Loading states — Never leave a void**
Even graying out a button counts. Spinners for long ops. Skeleton screens for content. Never leave the user wondering if something happened.

### Icons — Sizing and Consistency

- **Size to line height**: Set icon size = line-height of adjacent text. 24px text → 24px icon.
- **One library per zone**: Phosphor, Lucide, or Feather. Different styles can coexist only in visually separate areas.
- **Labels on unfamiliar icons**: House, bookmark, user — fine without labels. Everything else needs one. Tooltip minimum; visible label is better.
- **No color by default**: Icons are symbols, not decorations. Reserve color only for status: active tab, error state, success indicator.

### Fixing AI-Generated UI

| Problem | Fix |
|---------|-----|
| Emojis everywhere | Swap for Phosphor or Lucide icon library |
| Bright clashing colors | Fix backgrounds, check all contrast ratios, desaturate chips and tags |
| Bloated navigation | Collapse menus into popovers, actions into triple-dot menus, settings into tabs |
| Busy cards | Collapse secondary actions into icon menus. Move dates to secondary position. One primary action dominates. |

---

## ANIMATION

### Five Animation Types

**Type 1 — Entrance / Loading Preloader**
Screen slides up to reveal content beneath. Move background AND text as the loader exits — this creates fluid motion. Without both moving, it looks static and cheap. Keep preloaders short: people are impatient. Never sacrifice page access for a flashy animation.

**Type 2 — Hover / Click (Button Interactions)**
Text slides up on hover, new text + shape slides up beneath. Container masks the animation. Background color transitions. Even a simple color shift on hover is far better than no response. Every button needs at least this.

**Type 3 — Scroll (Text Highlight)**
Two-color gradient almost stacked together. Text used as a mask. Rectangle animates across on scroll position. Can be straight or diagonal. Can stagger multiple lines. Very trendy, fairly easy to implement.

**Type 4 — Looped (Ambient Animation)**
Icon traces a semicircle, line draws behind it. Marquee text — slow-moving and readable. Slow-moving means users can actually read it and it adds to the design rather than distracting. Never fast or frantic.

**Type 5 — Mouse (Cursor Following)**
CTA element follows the cursor — best for drawing attention to a key action. Use very sparingly. Always have a fallback for mobile. Overuse makes navigation feel broken.

### Animation Principles

| Do | Don't |
|----|-------|
| Animate to clarify, guide, confirm, situate, or reveal. Every animation should answer: "It helps because…" If you can't finish that sentence, cut it. | Animate for aesthetics alone. Complex animations that don't introduce or aid comprehension slow navigation and exhaust users. |
| Use direction to convey meaning: left = forward, right = back, slide from bottom = modal/temporary, fade = appearing. | Animate everything. Reserve motion for moments that truly matter. Static designs with great structure always outperform chaotic animations. |

### Figma Prototyping — Animation Building Blocks

**Loading Screen — Slide Up**
Duplicate frames. Frame 1: loader visible, content below. Frame 2: loader slid off-screen + content moved up. Smart Animate between them. Custom bezier curve (ease-out feel). Delay 800–1000ms before transitioning.

**Expanding Nav**
Start with 1×1px dot → circle → full width → full nav. Each step Smart Animates. Build in 5–6 frames. Delays of 1ms between each step, exponential bezier, 300–400ms per step.

**Text Wipe Reveal**
1px wide rectangle as tall as text. Slide it across while fading text from transparent to opaque. Custom bezier (700ms, exponential). Then fade out the rectangle in the final frame. Feels like text writing itself in.

**Bezier Curves**
Custom bezier > ease in/out for most entrance animations. Drag handles out for an exponential feel — slow start, fast finish. Ease in/out works for simple nav fades and small elements (200ms).

---

## UI ELEMENTS

### Nine Critical UI Elements

**Tab Bar (Mobile Nav)**
All icons same height, generous click area. Clear active state — color, not just opacity. Labels only if icons are obscure. Never a floating action button that breaks the visual line unless it has its own active state. Dark mode: add blur + transparency.

**Charts**
No curved lines — impossible to read exact values. Always show grid lines + labeled axes. Match bar count to data points (7 days = 7 bars). Show comparison period as a gray line. Use time scale selector as dropdown if space is tight. Never curve line tops.

**Cards**
Repeating cards rarely need a CTA — make the whole card a link instead. If you do have a CTA, use an arrow icon that fades in on hover. Gradient from image-bottom up to text area = premium effect (Apple Music style).

**Pricing Cards**
Name + description + monthly cost (large, prominent). Bullet points → check marks. Show a feature from the next plan up. Include billing message (annual = monthly price shown). Separate cost from features with a background color block.

**Stickers / Badges**
Star tool with 12 points, rounded corners. Use quirky display fonts (Gourd Quick, Barito). Add circular text with a plugin (Two to Path). Drop shadow at full opacity, darker than sticker, offset for depth. Kaleidoscope effect works on dark UI.

**Sign-up Modals**
Labels above inputs (never inside as placeholders only). Real placeholder text in input fields. Subheading "Create account" so context is clear. Login/sign-up toggle link. Off-white input background, 40% opacity stroke. Use 4px grid religiously.

**Footers**
If 3–5 links: center them, logo above, socials below, copyright left, credits right. Keep it simple. Only use multi-column footer if 6+ links. Don't copy Apple's footer unless you have Apple's number of pages.

**Chips**
Always use auto layout. Vertical padding = ½ or ¼ of horizontal padding (e.g. 20px horizontal → 10px or 5px vertical). Chips are thinner than buttons and never use primary CTA color. They're filters, breadcrumbs, or tags — not actions.

**Carousels**
Navigation dots + arrow buttons together, not separate. Dark background + blur on nav indicator. Add a circular progress timer around the current dot. Autoplay must pause on hover.

---

## LAYOUTS

### Layout Techniques

**Vary Column Counts**
Mix full-screen sections, 2-column, 3-column, and single-column. Don't repeat the same layout pattern consecutively. Shopify's website is the gold standard for varied layout.

**Breaking the Box**
Elements intentionally overlap or extend outside their containing frame. Cards shifted up/down for movement. Images extending off the edge. Elements should trail off from center, drawing the eye inward.

**Stacked Vertical Layout**
Stack features vertically with full-width sections. One feature at a time gets full attention. Apple uses this masterfully — completely focused, user absorbs one thing before scrolling to the next.

**Bento Layout**
Irregular grid of cards with different sizes. Very trendy. Works with 4–8 features to display. Cards can be 1×1, 1×2, 2×1, or 2×2. The irregular sizing itself communicates importance.

**Background Sections**
Alternate section backgrounds (white, light gray, colored) to create visual separation and implied depth. Adds rhythm to a long page without needing decorative elements.

**Image Techniques**
Remove backgrounds to break out of boxy layouts. Crop and zoom into a product detail (Apple). Use landscape photos with text overlay + gradient. Mask images into custom shapes that match the site's visual language.

### Layout Do / Don't

| Do | Don't |
|----|-------|
| Make important elements dramatically bigger — not just slightly bigger. Oversized text as a visual element is as impactful as an image. | Make everything the same size in the name of consistency. Uniformity is for components, not page sections. |
| Wireframe first. If the wireframe is boring, the finished design will be too. | Start with colors and fonts before nailing the layout. A stunning palette on a boring layout is still boring. |

### Depth Techniques

| Technique | How |
|-----------|-----|
| **Shadows** | Gray colors (not black), high blur, low opacity. If it looks like a shadow, dial it back by half. |
| **Offset buttons** | Duplicate frame, shift background, add hover animation between the two. Tactile depth that animates beautifully. |
| **Dark mode cards** | Dark bg + lighter cards creates implied foreground/background depth light mode can't replicate. Most reliable depth technique. |
| **Frosted glass** | Background blur + semi-transparent surface. Works on dark UIs over gradient backgrounds. Premium feel. Common on AI company sites. |

---

## MOBILE DESIGN

### Mobile vs Desktop — The Fundamental Shift

Mobile is not a smaller desktop. The constraints are so different they fundamentally change how content is structured, how navigation works, and how interactions feel. Understanding these differences is what separates mobile-optimized designs from squished desktop ports.

- **Reality Check**: iOS base font size is 17px. macOS is 13px. Despite the smaller screen, text often gets larger on mobile — not smaller. Spacing stays similar. You genuinely can pick only one thing to show at a time.
- **Common Mistake**: Squishing desktop layouts onto a phone. Everything looks normal until you see it beside a real app and realize how tiny it is. Don't scale down — redesign from scratch with mobile constraints in mind.

### Navigation Patterns

| Option | Treatment |
|--------|-----------|
| **Floating bottom bar** | Best when you have 3–5 key destinations. 44px minimum tap target always. Icons change based on context: inside an editor, completely different actions appear at the bottom. |
| **Sidebar-as-homepage** | When too many items exist for a bottom bar: turn the sidebar into a homepage. Add recent items at top, counts/actions on right. Frees up bottom for a large search bar or single CTA. |
| **Top bar contextual** | Notifications and a "more" menu are a good default. But like the bottom bar, top actions are highly contextual — they change per screen. Plan per-screen action sets. |

### Layout & Information Flow

**One direction of scroll per section**
Desktop layouts extend in two directions simultaneously — columns and rows. Mobile can only move one direction per section. Either stack content vertically, or scroll it horizontally off-screen. Not both at once.

**The Four Building Blocks of Mobile UI**
1. **Cards**: The most important. They group content where whitespace is scarce. Avoid double-nesting: padding-on-padding kills space.
2. **Text / Links**: Core navigation and labeling. links often replace icon-only nav for clarity. 44px minimum touch area. 17px base size, never < 13px.
3. **Images**: Full-bleed images work better on mobile than desktop. A single strong image at full screen width creates impact without competing with text.
4. **Inputs**: Design around the keyboard. Inputs should push content up — never be obscured. Bottom sheets are natural handlers for this.

**One Screen = One Thing**
Every screen (except home) does exactly one thing. No related content, suggested templates, or recent items on focused screens. When you need something new, go to a new page or use a **Bottom Sheet** for ancillary content without losing context.

### Gestures — The Mobile Superpower

| Gesture | Effect |
|---------|--------|
| **Swipe right** | Go back. The universal back gesture. Move background left ~35% and animate right as page swipes away (parallax shift). |
| **Swipe down** | Dismiss bottom sheet. As the sheet rises, zoom background out slightly. As dismissed, zoom back in for a physically layered feel. |
| **Swipe up** | Reveal search. Space-efficient alternative to a persistent bar. |
| **Long press** | Context menu (mobile right-click). Blur rest of screen, show actions, slight zoom on element. |

### Empty States — Two Types

| Type | Strategy |
|------|----------|
| **First-time / No Content** | Draw attention to the single primary action (+ button). Full-screen empty state removes clutter. Follow with a single popover explanation. |
| **No Search Results** | Illustration + clear message + spelling suggestions + exit action (clear search or go back). Never just blank space — always provide a path forward. |


---

## CASE STUDIES

### Goals of a Case Study

Two goals: show what problems you identified and how you solved them, and show exactly what someone gets if they hire you. Every design decision should serve one of these two goals.

### Case Study Structure (8 Steps)

**01 — Strong Problem Statement + Brief Solution**
The problem must be defined before anything else. A wrong or non-existent problem makes the solution irrelevant. Be concise. Then immediately show a summary of your solution up top so visitors don't have to scroll to understand what the project produced.

**02 — Make It Look Good**
Presentation is as important as content. Include many images and GIFs throughout — case studies are text-heavy so visuals are essential. Use clear graphs, label axes, include legends, annotate key findings. Large images. If it doesn't look good, people won't read it.

**03 — Data-Backed User Personas**
Personas must be backed by actual research — not invented. Focus on: goals, frustrations, behavior, pain points as they relate to your specific problem. Avoid extraneous details. The persona should reflect your data, not a fictional character.

**04 — User Flows**
Use FigJam or similar. Different shapes and colors for different node types (e.g. orange = decision, blue = process, green = input/output). Keep flows small — a small project with high quality execution beats a large project with mediocre execution.

**05 — Low-Fidelity Wireframes**
Never skip this step. Draw on paper or Figma. Test on actual people before building high-fidelity. Lofi wireframes let you test assumptions without committing to a full prototype.

**06 — Final Design with Rationale**
Show every design decision alongside the reasoning behind it. Layout: design on the left, explanation on the right (or tabbed). Make images as large as reasonably possible. The rationale is what employers and clients look at most.

**07 — Reflection**
Acknowledge flaws and things you'd improve. Note what you learned. Call out limitations in research. Mention features cut for time. Include next steps. This makes you seem like a more thoughtful designer, not a weaker one.

**08 — Add Style — Story, Concision, Skimmability**
Tell it like a story — include moments where you got stuck or had a breakthrough. Keep it short enough to read in one sitting (10–15 min). Use evocative chapter titles. Favor images, GIFs, and media over paragraphs. Make it skimmable so someone gets the full picture in 60 seconds.

---

## GAMIFICATION

### What Is Gamification?

Gamification takes something hard (language learning, saving money, fitness) and uses game mechanics to make it engaging. Done well, it triggers our need for progress, completion, and social comparison. Done badly, it's just annoying.

### Five Core Principles

**Principle 1 — Central Currency**
Every gamified app has a core currency — Duolingo's XP, Todoist's Karma. This gives users a sense of progress, unlocks features, and keeps them coming back. The currency must feel earnable and meaningful.

**Principle 2 — Progress Visibility**
Show exactly how much has been accomplished and what's left. Exercism shows language completion %. Duolingo shows league rank. The "near completion" effect — seeing 80% done is more motivating than being at 0%.

**Principle 3 — Social Element**
Leaderboards, public badges, friend comparisons. Fitness app leaderboards are the perfect example — you can see how you rank and feel the pull to compete. Normalizes the app's use through peer behavior.

**Principle 4 — Meaningful Rewards**
Nobody cares about meaningless rewards. Tie rewards to real goals. Duolingo's chests contain Gems that unlock real modifiers. Badges should mark real milestones, not arbitrary actions. Reward effort, not just activity.

**Principle 5 — Punishment / Streaks**
Hearts lost for wrong answers. Streaks broken by missing days. Creates loss aversion — keeping the streak becomes a motivation in itself. Use carefully — too punishing drives users away.

### Duolingo System Breakdown

| Component | What It Is | Why It Works |
|-----------|-----------|--------------|
| Activities | Challenges + lessons | Two types only — focused, not overwhelming |
| XP | Primary currency | Raises league rank, unlocks daily quest chests. Can't be bought. |
| Gems | Secondary currency | Earned via chests. Buy modifiers. Creates spending decisions. |
| Hearts | Punishment | Lost on wrong answers. Creates stakes. Can be bought back with gems. |
| Leagues + leaderboard | Social | Promotion/demotion zone. Weekly reset. Creates urgency. |
| Achievements | Milestones | Earned at XP milestones. Reward of gems. Recognition moment. |

### Gamification Design Do / Don't

| Do | Don't |
|----|-------|
| Make the core loop tight: action → reward → progress visible → next action. Every step should feel satisfying. The Duolingo loop takes under a minute to feel progress. | Gamify for its own sake. Arbitrary badges for arbitrary actions are quickly ignored. |
| Account for fairness in leaderboards. Adjust for income or regional differences where relevant. | Make punishment so harsh users quit. Hearts that take hours to regenerate cross the line. |

---

## REDESIGN PRINCIPLES

### How to Approach a Redesign

The best redesigns start with honest assessment of why the original fails — not just what looks different. Common failure modes: wrong hierarchy, no information architecture, too much space, too little space, beautiful but non-functional.

**Assess Hierarchy First**
Before touching colors or fonts: what should be at the top? What should be largest? What content belongs above the fold? Reorganize information architecture before touching aesthetics.

**Audit Redundancy**
Remove elements that don't do anything — non-functional cards, duplicate search bars, redundant stats. AI dashboards often repeat KPIs 3× per page. Every element must earn its place — if removing it doesn't hurt, remove it.

**Fix the Layout**
Same content, better layout = dramatically better design. The problem often isn't the data — it's that important info is buried below the fold while useless space dominates the top.

**Add the Missing Features**
Redesigns often reveal features that should have been there but weren't — a comparison button on charts, a time-frame selector, an analytics tab. Low-hanging fruit that makes the app dramatically more useful.

**Validate with Data**
Beautiful but non-functional charts (curved lines, no axes, wrong bar counts) are worse than plain ones. A chart that communicates data clearly beats an aesthetic but unreadable chart every time.

**Presentation Matters Too**
Case study, portfolio, or client presentation — how you show the design is as important as the design. Mockups, device frames, lifestyle shots, skew effects, and before/after comparisons all communicate quality.

### Presenting Your Work

| Context | Technique |
|---------|-----------|
| Portfolio / social | Plain background — take accent color, darken + desaturate. Add faint shadow. Works for almost any design. Hardest to mess up. |
| Dark mode showcase | Glow effect — large blurred circles of accent color behind UI. Pair with glassy background + gradient stroke border. |
| Dynamic / eye-catching | Skew + offset — skew 2° vertical, −14° horizontal. Pop out with shadow. Gray placeholder where design was. |
| Client meetings | Device mockups — AI-generated mockup (describe scene in ~30 words), knock out green screen, skew design in. 2 minutes for a custom mockup. |
| Multiple screens | Collage layout — offset and slide screens off page slightly. Add rotation. Don't line everything up in a grid — the imperfection is what makes it feel dynamic. |
| Best practice | Prototype, don't describe — a working prototype shows hidden features (swipe gestures, animations, modals). Static images can't communicate polish. Always show, never just tell. |

---

## COMMON BEGINNER MISTAKES

**01 — Broken User Flow**
Missing search bars, no skip buttons, absent empty/error states, navigation dead ends. Sketch flows on paper before opening Figma. Every screen needs: how to enter, what to do with no data, error state, and how to exit.

**02 — Overusing Visual Effects**
Harsh Figma default shadows (black at 25% opacity), clashing gradients, unnecessary glows. Use gray shadow colors, increase blur significantly, drop opacity to 15–20%. Less visual noise = better design, almost always.

**03 — Too-Tight Spacing**
Beginner UIs are packed too tight. Use auto layout and grids. Increase vertical spacing — especially on mobile. Use proximity to group related elements as a hierarchy tool.

**04 — Inconsistent Components**
Mixed corner radii, identical buttons styled differently, mismatched padding. Set one corner radius for small components (10px), a larger one for cards. Build a component once, use it everywhere. Use Figma variables and styles.

**05 — Bad Icon Choices**
Mismatched libraries mixing stroke weights and fill styles. Icons too large — size to line height. No labels on unfamiliar icons. On Flat Icon: filter to interface icons, sort by stroke width and corner radius for consistent results.

**06 — Redundant Elements**
Arrows on swipeable content, borders that add noise, non-functional buttons. If removing it doesn't hurt clarity, remove it. AI-generated UIs are especially prone to this — audit everything.

**07 — No Interactive Feedback**
Buttons with no visual response to clicks. Forms that submit without confirmation. Users assume silence means failure. Every action needs a response — even a button graying out counts.

**08 — Overdesigned Charts**
Curved line tops that obscure exact values. Missing Y-axis labels. 16 bars for 7 days of the week. Charts communicate data first — aesthetics are always secondary.

**09 — Bright Backgrounds**
Almost never use saturated colors for page backgrounds. Desaturate heavily if you need a tinted background. A faint tint adds warmth without competing with content.

**10 — Pure Black Text**
Pure black (#000) on white feels harsh. Use near-black (10–12% lightness) for headings, dark gray for body, medium gray for subtext. In dark mode, reserve pure white only for headings and primary CTAs.

**11 — Skipping Wireframes**
If you start high-fidelity before wireframing and the layout is boring, the finished design usually is too. Wireframing catches bad information architecture before it's baked into a polished design that's hard to restructure.

**12 — Not Viewing on Device**
Designing zoomed-out in Figma causes oversized fonts and spacings. Always preview on actual target screen or use the Figma mirror app. Adjust for browser bar height on both mobile and desktop.

---

## PRE-SHIP CHECKLIST

- [ ] Every interactive element has: default, hover, active, and disabled states
- [ ] All text passes WCAG contrast — tested on colored backgrounds and in dark mode
- [ ] Icon size matches adjacent text line height; consistent library used throughout each visual zone
- [ ] Corner radii, spacing, and color values enforced via Figma variables and component library
- [ ] Dark mode built as an independent palette — not an inversion of light mode
- [ ] Surfaces in dark mode get lighter as they elevate (card lighter than bg, popover lighter than card)
- [ ] Destructive actions use red, not brand color — regardless of brand guidelines
- [ ] Empty states exist and invite the user to take action — not just blank space
- [ ] Loading states exist for every async operation — button gray-out minimum, spinner for long operations
- [ ] Every form has: default, focus, filled, error, and warning states
- [ ] Motion serves clarity — each animation answers "it helps because…" or it gets cut
- [ ] Overlays over images use gradient or progressive blur — not flat black
- [ ] Typography: max 6 font sizes on landing pages; max ~24px on dashboards for information density
- [ ] Charts have labeled axes, correct bar count matches data, no purely decorative curved tops
- [ ] Shadows use gray color (not black), high blur, 15–20% opacity — or removed entirely
- [ ] No emoji in professional UI — replaced with professional icon library throughout
- [ ] Color is used for purpose (status, hierarchy, interaction) — not decoration or variety alone
- [ ] 5-second test: new visitor understands the product after 5 seconds of scrolling
- [ ] User flow mapped: every screen has clear entry, exit, error state, and empty state
- [ ] Wireframe validated before high-fidelity — layout is interesting at wireframe stage
- [ ] Designs previewed on actual target device — not just Figma at 50% zoom
- [ ] Animations direction-coded: left = back, right = forward, bottom = modal, fade = appear/disappear
- [ ] Pricing cards: name + description + prominent cost + check marks + next-plan tease + billing note
- [ ] Mobile: every screen (except home) does exactly one thing — no sidebar content bleeding into focused screens
- [ ] Mobile: bottom bar has 3–5 items max; all tap targets are at least 44px; contextual actions change per screen
- [ ] Mobile: each section scrolls in one direction only — no two-directional grid layouts
- [ ] Mobile: no double-nested cards; keyboard doesn't obscure inputs; bottom sheets used for ancillary content
- [ ] Mobile: both empty states designed — first-time (guide to primary action) and no-results (illustration + path forward)

- [ ] All interactive elements have pointer cursor and at least one visible state change on interaction
- [ ] Case study (if applicable): problem → solution → research → persona → flow → lofi → hifi → reflection

---

## Anti-Patterns

### ❌ Starting with Color Before Layout

**Why bad**: A stunning color palette on a boring layout is still boring. Structure is the foundation — personality and polish come after.

**Instead**: Wireframe first until the layout is interesting. Then apply design tokens. Then color.

### ❌ Designing Only for Desktop

**Why bad**: Most traffic is mobile. Zoomed-out Figma views cause oversized elements. Misses mobile-specific patterns (tab bars, safe areas, tap target sizes).

**Instead**: Always preview on the actual target device during design. Design mobile-first or build explicit mobile variants.

### ❌ Reinventing State Patterns

**Why bad**: Users have mental models. Inventing a completely novel state for a button or form creates cognitive friction.

**Instead**: Follow established state patterns (hover = lighter, active = darker, disabled = desaturated). Only innovate where it adds real value.

### ❌ Gamification Without Purpose

**Why bad**: Badges for arbitrary actions, points that unlock nothing, streaks with no stakes — users ignore these immediately.

**Instead**: Every mechanic must connect to a real user goal. The loop must be: action → visible reward → meaningful next step.

---

## When to Use

This skill applies to any task involving:
- Creating or critiquing UI/UX designs
- Building design systems or component libraries
- Choosing colors, typography, or spacing
- Designing interactive states and flows
- Adding animation or micro-interactions
- Reviewing or fixing AI-generated UI
- Building case studies or portfolio presentations
- Applying gamification mechanics to a product
- Redesigning or auditing existing interfaces
- Pre-ship quality assurance

---

## Related Skills

Works well with: `frontend`, `frontend-ui-dark-ts`, `landing-page-design`, `interactive-portfolio`, `3d-web-experience`, `scroll-experience`
