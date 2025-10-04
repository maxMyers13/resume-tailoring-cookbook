---
description: For SWE internships and new‑grad roles. API‑doc style. Copy‑paste ready.
icon: terminal
layout:
  width: default
  title:
    visible: true
  description:
    visible: true
  tableOfContents:
    visible: true
  outline:
    visible: true
  pagination:
    visible: false
  metadata:
    visible: true
---

# Quickstart

### What this resource is:

This is a **prompt cookbook** for tailoring your résumé to Software Engineering internships and new grad roles.\
It gives you **ready-to-use ChatGPT prompts** that rewrite your bullets so they match the job description without fabricating.

Think of it as a **cheat sheet + power tool**:

* You provide the job description and your current résumé bullets.
* The prompts help you surface the right skills and metrics.
* You get stronger, clearer bullets in 10–15 minutes.

### Who this is for

* Students applying to **internships** or **new grad SWE roles**.
* People who already have a **resume** draft but need to **make it match each job posting**.

**What this is not:**

* This is not a resume template.
* This is not a generic rewrite service, this is about **tailoring**.

### How to use it

1. Open the role page that matches your target job&#x20;
   1. General SWE
   2. Fullstack
   3. Database&#x20;
   4. Frontend
   5. Data-Focused
2. Copy the **Core Tailor Prompt** from that page into ChatGPT.
3. Paste in the job description and the resume bullets for that role or project.
4. If the output feels generic, run the [**Fix Weak Bullets**](https://app.gitbook.com/o/rdYpRiHUNe7S7AfuclRd/s/Kmv3UJTYft9NarhONBrk/~/changes/8/appendix/fix-weak-bullets-gap-finder-prompts) prompts to add missing context.
5. Use the [**Before → After Gallery**](appendix/before-greater-than-after-gallery.md) in the Appendix to see examples of vague bullets turned into strong ones.

### Why it matters

Recruiters look for **evidence** that you match the job. A generic résumé leaves them guessing.\
A tailored résumé answers their questions directly — and gets you more interviews.

**Goal**\
Tailor your résumé to a specific job in about 15 minutes by pasting the right prompts into ChatGPT. This guide teaches you the **how** and gives you **copy‑paste** snippets that work.

**What you need before you start**

* The **job description** (JD) you are applying to.
* Your **master résumé** or the section you want to improve.
* 10 minutes to add missing context so ChatGPT has something real to work with.

#### 0.1 Core Setup Prompt

Paste this at the top of a fresh ChatGPT thread.

{% code overflow="wrap" %}
```prompt
You are a Resume Tailoring Assistant for SWE internships and new grad roles

Rules:
1) Evidence only. Use my actual experience and the job description. Do not invent tools, metrics, or responsibilities.
2) STAR + XYZ. Every bullet must include enough Situation/Task context and an Action with a Result. Prefer one metric per bullet.
3) No fluff. No subjective adjectives. No clichés. No em dashes. Use plain punctuation.
4) Student‑friendly vocabulary. Prioritize clarity. Use the target role’s keywords naturally.
5) If my input is missing context or metrics, ask targeted questions using a short checklist before writing.

Outputs:
- Tidy bullets in past tense for past roles, present tense for current roles.
- 1–3 bullets per role depending on relevance to the JD.
- Include a “TODO: metric” line whenever a result is missing.

When I say SWITCH ROLE I will give you a role label. Update vocabulary, ordering, and emphasis accordingly.
```
{% endcode %}

***

#### 0.2 Paste the JD

{% code overflow="wrap" %}
```prompt
JOB DESCRIPTION
[Paste the full JD here]
Please extract:
- Must‑have skills
- Nice‑to‑have skills
- Core responsibilities
- Keywords/tools I must echo in bullets (sorted by importance)
Return a short checklist for tailoring.
```
{% endcode %}

***

#### 0.3 Paste the Experience You Want Tailored

Start with 1 role or project at a time.

{% code overflow="wrap" %}
```prompt
EXPERIENCE TO TAILOR
Role: [e.g., Backend Intern, Company, Dates]
My raw bullets or notes:
- [paste your current bullets or notes]
- [paste specs, links, or short context if needed]

Please rewrite 2–3 bullets that align to the JD checklist. Use STAR + XYZ. Keep it truthful. If context is missing, ask me targeted questions first.
```
{% endcode %}

***

#### 0.4 Gap‑Finder (ask me what’s missing first)

{% code overflow="wrap" %}
```prompt
Before writing bullets, ask me at most 6 questions to fill context gaps:
- Scope: team size, users impacted, data size, traffic, environment.
- My specific contribution vs team.
- Tools actually used (versions if relevant).
- Any benchmarks or outcomes (latency, accuracy, cost, time saved, adoption).
- Constraints (security, performance, accessibility, reliability).
After questions, write the tailored bullets.
```
{% endcode %}

***

#### 0.5 Universal Micro‑Prompts

Use these anywhere, fast.

**STAR check**

```prompt
Run a STAR check on these bullets. Add one line of context at the start if the Situation/Task is unclear to a non‑technical recruiter.
[Paste bullets]
```

**Quantify check**

```prompt
Add one honest metric to each bullet. If unknown, add a TODO line that tells me exactly what to measure. Then stop.
[Paste bullets]
```

**Tighten**

```prompt
Tighten these bullets. Remove filler, repeat nouns sparingly, keep one metric per bullet, make verbs concrete.
[Paste bullets]
```

***

#### 0.6 Apply/De‑prioritize Filter

For students and new grads:

* **Hard stop**: graduation window mismatch, ineligible work authorization.
* **De‑prioritize**: you miss a must‑have that is truly fundamental to the role.
* **Soft apply**: missing a nice‑to‑have is fine if your bullets show you can learn quickly.

<a href="https://gitbookio.github.io/onboarding-template-images/gitbook-petstore.yaml" class="button primary" data-icon="arrow-up-right-from-square">View OpenAPI spec</a>
