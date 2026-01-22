---
description: >-
  This doc explains the repeatable system I use to go from: idea → a working UI
  screen using Google AI Studio, visual references, and AI-assisted prompting.
---

# Google AI Studio UI Cookbook

**How I design and build UI fast using AI (the exact workflow)**\
This is about **controlling context** so AI produces usable, production-grade UI.

***

### Core Ethos

AI is a **context machine**, not a mind reader.

The quality of the UI you get is proportional to:

1. how clearly you know what you’re building
2. how strong your visual references are
3. how specific your prompt is

Most failures happen because people skip one of those.

***

### High-level workflow (TL;DR)

1. Get clear on what you’re building (screen, goal, sections)
2. Dictate the idea to a chatbot (speech > typing)
3. Use the chatbot to generate **Dribbble search queries**
4. Find a UI reference on Dribbble and screenshot it
5. Have AI write a **Google AI Studio–optimized prompt**
6. Generate the UI in Google AI Studio (with screenshots)
7. Download output and integrate into the repo using your editor

That’s the loop. Everything else is refinement.

***

### Step 1: Know what you’re building (the hardest step)

Before touching AI, answer these **in plain language**:

* What is this screen?
* What is the user trying to accomplish?
* What are the main sections?
* What data appears?
* What happens if there’s no data?

You do **not** need a full spec.\
You need a mental picture.

Bad:

> “I need a clean dashboard.”

Good:

> “Projects overview screen that shows student progress, groups items by status, and pushes the user to start the next project.”

***

### Step 2: <mark style="color:$primary;">**DICTATE**</mark> the idea into a chatbot

Open your chatbot of choice (ChatGPT, Claude, Gemini, Copilot, etc.).

**Use dictation.**\
Talking lets you ramble, add nuance, and capture intent more accurately than typing.

<div data-full-width="true"><figure><img src=".gitbook/assets/Screenshot 2026-01-17 at 9.40.56 PM.png" alt="dictate on chatGPT"><figcaption></figcaption></figure></div>

Describe:

* what you’re building
* what kind of product it is (learning platform, PWA, portfolio, etc.)
* the vibe (playful, serious, game-like, minimal)
* any constraints (desktop only, fast iteration, internal tool)

Then ask:

> “Give me Dribbble search queries to find screens like this.”

***

### Step 3: Find visual references on Dribbble

Go to [Dribbble](https://dribbble.com/) and run the queries.

When you find something good:

* screenshot the screen (or parts of it)
* optionally grab **two references**:
  * one for layout
  * one for components or style

This screenshot is **non-negotiable**.\
Without it, AI guesses. Guessing is how you get generic UI.

***

### Step 4: Let AI write the Google AI Studio prompt (AI → AI)

This is the leverage point.

Instead of writing the generator prompt yourself, you ask AI to do it **using your reference and constraints**.

Attach the screenshot and use a meta-prompt like this:

{% code overflow="wrap" %}
```
You are an expert prompt engineer for Google AI Studio.

I want you to write a single prompt that I can paste directly into Google AI Studio to generate a UI screen.

Context:
- App type: <learning platform / PWA / portfolio / etc>
- Tech stack: Next.js (App Router), TypeScript, Tailwind, shadcn/ui
- Output must be clean, production-ready code

Goal:
<describe what the screen should do>

Visual reference:
(Attached screenshot) Match the layout and component structure closely.

Brand & styling:
### Backgrounds
* **Primary background:** `#020617`
* **Secondary background:** `#0B0F18`
* **Card / panel surface:** `#111827`

### Borders
* **Border:** `#1F2937`
* **Subtle border:** `rgba(255,255,255,0.06)`

### Accents
* **Primary blue:** `#3B82F6`
* **Sky blue:** `#0EA5E9`
* **Cyan:** `#06B6D4`
* **Teal:** `#14B8A6`

### States
* **Success green:** `#10B981`
* **Error red:** `#EF4444`

### Text
* **Primary text:** `#FFFFFF`
* **Secondary text:** `#94A3B8`
* **Muted text:** `#64748B`

If you want one “signature” LiLO gradient for buttons/headers:
`linear-gradient(90deg, #3B82F6 0%, #0EA5E9 100%)`

Requirements:
- Include loading, empty, and error states
- Use reusable components where appropriate
- Provide a file list and full code for each file
- Avoid external image dependencies (use placeholders)
- Make it easy to drop into an existing repo

Write ONLY the final Google AI Studio prompt.
```
{% endcode %}

AI is unusually good at prompting other AI. Use that.

***

### Step 5: Generate in Google AI Studio

Go to **Google AI Studio**:

* paste the generated prompt
* attach the screenshot(s)
* run the generation

You should get a solid **V0/V1 UI**.

If it’s not what you want at all:

* do **not** manually patch everything
* tighten constraints and regenerate **from scractch**

Iteration via regeneration is faster than hand-editing.

***

### Step 6: Generate an Integration Prompt (UI → Repo Translation)

#### What you do:

1. Take **screenshots of the generated UI**
2. Go back to your chatbot of choice (ChatGPT, Claude, Gemini, etc.)
3. Show it:
   * the UI screenshots
   * the generated file structure/code (if relevant)
4. Ask it to write a **Cursor-optimized integration prompt**

This is a second “AI writes AI instructions” step — but now the target is **Cursor**, not AI Studio.

***

#### Why this step matters

* AI Studio is good at **generating UI**
* Cursor is good at **editing existing repos**
* Chatbots are good at **bridging intent between the two**

You are using AI as a **translation layer**, not a blind executor.

***

#### Copy/paste: Cursor Integration Prompt Generator

Use this prompt in ChatGPT (with screenshots attached):

```
You are helping me integrate a newly generated UI feature into an existing codebase using Cursor.

Context:
- I have just generated this UI using Google AI Studio.
- Screenshots of the UI are attached.
- This is a real production repository, not a sandbox.

Repository structure:
- Monorepo-style folder called "Launchpad"
- /backend → backend service
- /frontend → frontend app

Goals:
- Integrate the new UI cleanly
- Follow existing patterns and conventions
- Minimize unnecessary changes
- Do not refactor unrelated code

Instructions:
1. Write a single, clear Cursor prompt I can paste directly into Cursor.
2. The prompt should:
   - Specify which files to create or modify
   - Explain where the generated code should live
   - Describe how to wire routing, components, and data
   - Avoid touching files outside the frontend unless explicitly needed
3. Assume Cursor has access only to the Launchpad directory.

Output ONLY the final Cursor prompt.
```

***

### Step 7: Controlled Integration Using Launchpad (Cursor Safety Pattern)

This is a **deliberate containment strategy**.

#### Your setup

* You keep **frontend and backend repos inside a single parent folder**
* That parent folder is called **Launchpad**
* You open Cursor **at the Launchpad level**
* You do NOT let Cursor operate on:
  * your full filesystem
  * Downloads
  * unrelated projects

***

#### How integration actually happens

1. Download the ZIP generated by Google AI Studio
2.  Manually drag the extracted folder into:

    ```
    Launchpad/
      ├── backend/
      ├── frontend/
      └── ai-studio-output/   ← temporary
    ```
3. Open Cursor **from the Launchpad directory**
4. `@mention` the generated files or folder inside Cursor
5. Paste the **Cursor integration prompt** generated in Step 6
6. Let Cursor integrate selectively:
   * copy components
   * adjust imports
   * wire routes
   * align types

After integration, the `ai-studio-output` folder can be deleted.

***

#### Why this pattern is important

* Limits blast radius
* Prevents Cursor from “helpfully” touching unrelated files
* Keeps human-in-the-loop control
* Makes integrations auditable and reversible

This is **defensive AI-assisted development**, not reckless automation.

### Step 8: Download and integrate using your editor

Download the output or copy the code.

Then switch to your editor (Cursor, VS Code, etc.) and integrate it into the real repo.

Use an integration prompt like:

```
Integrate this generated UI into the existing repository.

Rules:
- Follow existing folder structure and naming conventions
- Do not introduce new patterns unless required
- Ensure imports resolve cleanly
- Make it compile on first run

Tasks:
1. Add the screen to the correct route
2. Wire navigation if needed
3. Replace mock data with existing types or APIs
4. Keep Tailwind and component patterns consistent
```

Google AI Studio is best at **generation**.\
Your editor + repo context is best at **integration**.

***

### Color systems matter more than people think

If you don’t specify colors:

* AI invents them
* your app drifts visually
* everything feels inconsistent

Always keep a **copy-paste color block** ready and include it in prompts.

***

### Why this system works

* Visual references anchor layout decisions
* Dictation captures intent better than typed prompts
* AI-generated prompts are more generator-friendly
* Regeneration replaces manual cleanup
* Clear separation between generation and integration

This is not magic. It’s controlled input.

***

### Team standard (recommended)

Any time someone uses AI Studio to build a screen:

* save the prompt
* save the reference screenshot
* link the final result or PR

Over time, this becomes a **prompt library**:

* dashboard recipe
* onboarding flow recipe
* PWA settings recipe
* portfolio landing recipe

That’s how individual speed turns into team velocity.
