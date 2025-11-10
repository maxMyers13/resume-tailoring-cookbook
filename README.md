---
icon: play
---

# Quickstart

<a href="https://chatgpt.com/g/g-p-690b22ce50d88191b98bf3e9a460697b-resume-rewrites/project" class="button primary" data-icon="arrow-up-right-from-square">Open the LiLO Resume Tailoring Project</a>

[Click here to start](https://chatgpt.com/g/g-p-690b22ce50d88191b98bf3e9a460697b-resume-rewrites/project)

#### Step 1: Upload the Job Description

{% code overflow="wrap" %}
```markdown
Job Description Analysis

Using the context in 'how_to_tailor_your_resume.md' and 'metricdiscoveryprompt.md', extract the following information from the job description below.

[Paste the full job description here]

Identify and list:

Must-have qualifications — essential skills, experiences, or credentials without which a candidate would not be considered.

Nice-to-have qualifications — secondary or bonus skills that strengthen a candidate’s fit.

Above-and-beyond or standout traits — signals of an exceptional applicant (leadership, impact scale, rare technical depth, etc.).

Core responsibilities — what the role is accountable for delivering.

Keywords / tools — specific terms or technologies that should be echoed in tailored resume bullets (rank these by importance).

Present your findings as a Tailoring Checklist, formatted with checkboxes (☐).

Before returning results, confirm that each category reflects LiLO’s definitions of must-have vs. nice-to-have (see context).
```
{% endcode %}

***

#### Step 2: Choose the Experience to Tailor

Pick 1 project or internship that fits this job:

{% code overflow="wrap" %}
```prompt
Experience Selection & Rewrite Setup
Using the Tailoring Checklist from Step 1 and the context files how_to_rewrite_a_resume.md, metricdiscoveryprompt.md, before_greater_than_after.md, and especially star_xyz_fusion.md, help me select and rewrite one experience for this role.

Role Type: (e.g., Backend Intern — Company — Dates)
My raw bullets / notes (paste exact text):
(Paste exact Bullets Here) - Required
Extra context (optional): links/specs, stack, scale, users, latency, data size, $$ impact.

Do this in order:

Targeting plan: From the Step-1 Checklist, list the top 3–5 items this experience can credibly hit. Quote them verbatim and rank by importance.

Gap queries (max 6): Ask only the smallest set of questions needed to surface missing details about scope, scale, tools, and outcomes. Use metricdiscoveryprompt.md for guidance.

Rewrite (3–4 bullets):
  • Follow the S + T → XYZ method from star_xyz_fusion.md.
  • Make sure each bullet:
   – Begins with a strong action verb.
   – Contains S + T to explain why the work mattered and XYZ to show what you did and what changed.
   – Includes a specific tool or system and one truthful metric (time saved, perf gain, users impacted, etc.).
   – Maps to at least one Checklist item from Step 1.
  • Avoid duplicate sentence shapes and generic phrasing (see how_to_rewrite_a_resume.md).

Traceability table: Return a table with columns: Checklist Item Hit | Final Bullet | Proof (Tool/Metric) | Why It Mattered.

Integrity check: Flag any metric that’s assumed or estimated as NEEDS CONFIRMATION so I can verify it.

After Step 2, pause for my answers (if you asked questions) or my confirmation before continuing.
```
{% endcode %}

***

#### Step 3: Fill in the Gaps (Q\&A)

* AI will ask you targeted questions.
* Be honest and specific. If you don’t have a metric, just describe the result qualitatively.

{% code overflow="wrap" %}
```prompt
Context Gap Q&A (Be Specific + Truthful)
Using the outputs from Step 2 — your targeting plan, ranked checklist items, and the initial draft bullets — ask up to 6 targeted questions to uncover any missing context before rewriting.

Ground your questions and later rewrites in these context files:
metricdiscoveryprompt.md, star_xyz_fusion.md, and how_to_rewrite_a_resume.md.

Question types to prioritize:

Scope: team size, number of users affected, data volume, traffic scale, deployment environment.

My role: what I personally built, designed, or owned vs. what the team handled.

Tools used: specific frameworks, languages, libraries, or versions.

Results: quantitative (latency, accuracy, adoption, cost/time savings) or qualitative if numbers are unknown.

Constraints: security, accessibility, performance, or reliability considerations.

Fabrication Rule:

Never invent or infer numbers, tools, or outcomes.

If data is missing, create an inline note in square brackets:
[TO-DO: clarify X metric] or [TO-DO: add context on reliability improvements].

Use these placeholders only where a fact must later be confirmed.

After asking your questions and receiving my answers, regenerate 3–4 bullets following the S + T → XYZ method from star_xyz_fusion.md.
Each bullet should include:

One verified metric or qualitative descriptor (if no metric).

One clear action verb + technical noun.

A mapping back to at least one Step-1 checklist item.

End your response with a short “Pending TO-DOs” list that summarizes any placeholders needing confirmation.

If the role is technical, consult metricdiscovery_swe.md; otherwise consult metricdiscovery_general.md. Ask at most 6 questions total, then summarize metrics as Baseline→After→Δ with timeframe and source; use [TO-DO: …] for any missing confirmations.
```
{% endcode %}

***

#### Step 4: Rewrite Your Bullets

* Copy the rewrite prompt.
* Get your improved bullets in STAR + XYZ format.
* Paste the new ones into your resume doc.

{% code overflow="wrap" %}
```
Final Resume Bullet Rewrite
Using all confirmed context from Steps 1–3 including the JD Tailoring Checklist, targeting plan, and verified Q&A responses  rewrite my selected experience into 3–4 polished bullets.

Reference the following context files:
star_xyz_fusion.md, how_to_rewrite_a_resume.md, and before_greater_than_after.md.

Instructions:

Follow the S + T → XYZ structure from star_xyz_fusion.md.

Keep every statement truthful and verifiable.

If any detail is uncertain, insert a clear placeholder in brackets, e.g. [TO-DO: confirm latency impact].

Each bullet must:
• Begin with a strong action verb.
• Include one technical noun (tool, framework, or system).
• Contain one metric or qualitative descriptor showing the result.
• Map explicitly to at least one checklist item from Step 1.

Use variation in sentence rhythm; avoid repetition of structure or verbs (see how_to_rewrite_a_resume.md).

If all context gaps were already filled in Step 3, proceed directly with the rewrite—no further questions needed.

Return:

Final bullets (3–4 lines).

A brief summary of alignment, which checklist items each bullet satisfies.

A short “Pending TO-DOs” list, if any placeholders remain.
```
{% endcode %}

***

#### Step 5: Quality Check

* Run the following checks when needed:

#### Context Check

_When to use:_ If someone who doesn’t know you (like a recruiter) would be confused by reading your bullets, you’ve got work to do.

{% code overflow="wrap" %}
```prompt
Using the S + T → XYZ method from star_xyz_fusion.md, review these bullets for clarity.
If the Situation or Task is unclear, add a single intro line or short clause that explains why the work mattered.
Do not change verified facts.

[Paste bullets here]
```
{% endcode %}

#### Metrics Check

_When to use:_ if your bullet describes what you did but doesn’t show the impact, scale and result.

{% code overflow="wrap" %}
```prompt
For each bullet, ensure there is one honest, verifiable measure of impact (time, scale, performance, users, revenue, etc.).
If a metric is missing, add a placeholder note in brackets e.g. [TO-DO: measure latency reduction] — and stop.

[Paste bullets here]
```
{% endcode %}

#### Tighten

_When to use:_ if your bullets all start to sound the same or rely on buzzwords instead of proof.

{% code overflow="wrap" %}
```prompt
Tighten these bullets. Remove filler, repeat nouns sparingly, keep one metric per bullet, make verbs concrete.
[Paste bullets]
```
{% endcode %}
