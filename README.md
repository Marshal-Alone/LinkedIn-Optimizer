# LinkedIn Skills & Growth Automation: The Complete Setup, Guide & Case Study

[![MIT License](https://img.shields.io/badge/License-MIT-22C55E.svg)](LICENSE)
[![Python 3.10+](https://img.shields.io/badge/Python-3.10%2B-blue.svg)](https://www.python.org/)
[![Platform Windows | Linux | macOS](https://img.shields.io/badge/Platform-Windows%20%7C%20Linux%20%7C%20macOS-lightgrey.svg)]()
[![Antigravity Compatible](https://img.shields.io/badge/Antigravity-Compatible-0776D0)](https://antigravity.google)
[![Claude Code & Codex](https://img.shields.io/badge/Claude_Code%20%7C%20Codex-Ready-D97757)]()

A battle-tested, open-source guide and toolkit featuring **12 AI skills** for LinkedIn marketing, post writing, profile optimization, and content operations. Built to enforce **2026 feed algorithm heuristics**, eliminate AI slop, and follow a strict **human-approval-before-publish** workflow.

---

## Table of Contents

1. [Overview](#overview)
2. [Quickstart & Windows Setup Guide](#quickstart--windows-setup-guide)
3. [Cost Breakdown: Paid Services vs. Free Alternatives](#cost-breakdown-paid-services-vs-free-alternatives)
4. [Environment Configuration (.env)](#environment-configuration-env)
5. [How to Use This (Day-to-Day Guide)](#how-to-use-this-day-to-day-guide)
6. [The Core Pattern (Approval Loop)](#the-core-pattern-approval-loop)
7. [Real-World Case Study & Walkthrough](#real-world-case-study--walkthrough)
   - [Phase 1: Building the Story Bank](#phase-1-building-the-story-bank)
   - [Phase 2: Writing a 2026 Algorithm-Optimized Post](#phase-2-writing-a-2026-algorithm-optimized-post)
   - [Phase 3: The 2026 Profile Optimization Blueprint](#phase-3-the-2026-profile-optimization-blueprint)
8. [The 12 Skills Catalog](#the-12-skills-catalog)
9. [Apify Read Layer (Optional)](#apify-read-layer-optional)
10. [Verification & Test Suite](#verification--test-suite)

---

## Overview

Most AI-generated LinkedIn content fails because:
1. It is packed with unmistakable AI vocabulary (*"delve", "testament", "landscape", "in today's fast-paced world"*).
2. It uses obsolete feed strategies (e.g., opening with generic questions, hashtag stuffing, external links in the body).
3. It posts blindly without human review.

This repository fixes that by pairing **12 single-purpose agent skills** with **20 proven 2026 hook formulas (F1–F20)**, a personal **Story Bank**, and an approval-first publishing pipeline.

---

## Quickstart & Windows Setup Guide

### 1. Prerequisites
* **Python 3.10+** (Python 3.12 recommended)
* Git

### 2. Clone and Install Dependencies
```bash
git clone https://github.com/your-username/linkedin-skills.git
cd linkedin-skills
pip install -r requirements-dev.txt
```

### 3. Windows Compatibility Fix (Crucial!)
On Windows, standard git clones checkout `.claude/skills` as one-line plain text pointer files instead of directory symlinks unless Developer Mode is enabled. Without fixing this, agents cannot resolve the skill paths.

Run this simple command in **Command Prompt (cmd)** from the repository root to create **Windows Directory Junctions** (requires **no admin privileges**):

```cmd
rmdir .claude\skills /s /q && mkdir .claude\skills && for /d %s in (skills\*) do mklink /J .claude\skills\%~nxs %cd%\%s
```

If you prefer **PowerShell**:
```powershell
Remove-Item -Recurse -Force .claude\skills
New-Item -ItemType Directory -Path .claude\skills -Force
Get-ChildItem -Directory skills | ForEach-Object {
    cmd /c "mklink /J .claude\skills\$($_.Name) $($_.FullName)"
}
```

---

## Cost Breakdown: Paid Services vs. Free Alternatives

The repository is 100% open-source (MIT). The upstream author includes optional commercial hooks, but **you can run the entire system for $0**:

| Layer | Upstream Service | Cost | $0 Free Alternative (Used Here) |
|---|---|---|---|
| **Brain / LLM** | Claude Pro / Max ($20/mo) | $20/month | **Google AI Pro (Gemini 3.8 Flash / Pro)** or **Groq API** (Llama 3.3 70B) in Antigravity or via Python. |
| **Publishing** | Publora API | 15 free posts/mo, then $19+/mo | **Tier 0 Manual Copy-Paste** ($0) or the **Publora Free Tier** (15 posts/month). |
| **Web Scraping** | Apify Actors | $5/month free credit | Manual copy-pasting of LinkedIn post URLs/text ($0). |
| **Graphics** | Pixfaro API | $0.004–$0.16/image | Google Imagen 3 via `google-genai` ($0) or local Python PIL/Pillow quote cards. |

---

## Environment Configuration (.env)

Copy the template to create your `.env`:
```bash
cp .env.example .env
```

If you use Publora, Apify, or Pixfaro, configure your keys:

```env
# 1. Publora Auto-publishing (Optional: 15 free posts/month)
# Sign up: https://app.publora.com/signup
PUBLORA_API_KEY=sk_your_publora_key_here
LINKEDIN_PLATFORM_ID=linkedin-your_channel_id_here

# 2. Apify URL Scraper (Optional: $5 free credit/month)
# Sign up: https://console.apify.com/sign-up
APIFY_TOKEN=apify_api_your_token_here

# 3. Pixfaro Branded Visuals (Optional)
PIXFARO_TOKEN=pf_live_your_token_here
```

Verify your configuration live with:
```bash
python scripts/check_config.py
```

---

## How to Use This (Day-to-Day Guide)

You don't need to launch a background server or memorize complex CLI commands. This repository turns **your AI assistant** (Antigravity, Claude Code, Cursor, or Codex) into your personal LinkedIn content engine. 

Simply open this repository in your AI coding environment and talk to it in plain English.

### 📋 Ready-to-Use Prompts

Here are the canonical prompts to trigger the skills directly:

#### 1. Writing a High-Performing Post
```text
"Write me a LinkedIn post about why setting up an AWS CI/CD pipeline taught me more than solving 100 LeetCode problems. Make it viral using a 2026 hook formula."
```
*What happens:* The agent loads `linkedin-post-writer`, consults your `story-bank.md`, applies **Formula F7 (Number-First Build Log)**, checks 2026 slop density, and formats the post.

#### 2. Commenting on Someone Else's Post
```text
"Comment on this post: https://www.linkedin.com/posts/... — I want to add a thoughtful take from a backend perspective."
```
*What happens:* The agent fetches the post text via Apify (or asks you to paste it), scores the draft for 2026 comment depth (introducing new nouns, 200–350 chars), and prepares a comment.

#### 3. Sweeping and Replying to Comment Threads
```text
"Reply to comments on this post: https://www.linkedin.com/posts/..."
```
*What happens:* The agent sweeps all top-level comments and replies, filters out low-value spam, and drafts batched replies.

#### 4. Auditing and Humanizing an Existing Draft
```text
"Audit this post draft for AI tells, cliches, and algorithm issues: [paste your draft]"
```
*What happens:* The agent scans against the 2026 vocabulary blacklist (*delve, robust, seamless, tapestry*), caps em dashes, breaks stacked triads, and calculates AI emoji density.

#### 5. Building Your Personal Story Bank
```text
"Interview me to build my Story Bank for LinkedIn content."
```
*What happens:* The agent asks 5 targeted questions about your career timeline, concrete numbers, shipped projects, turning points, and scars, saving them to `references/story-bank.md`.

#### 6. Reverse-Engineering Viral Posts
```text
"What hook formula does this post use? https://www.linkedin.com/posts/... Give me a blank template."
```
*What happens:* The agent analyzes the structural hook and outputs a fill-in-the-blank template for your own niche.

#### 7. Planning Your Content Week
```text
"Create a 7-day LinkedIn content plan. I am a fresher Java backend developer targeting tech leads and recruiters."
```
*What happens:* The agent outputs a strategic 7-day calendar with daily formats, hook types, and posting windows.

#### 8. Optimizing Your LinkedIn Profile
```text
"Optimize my LinkedIn profile for inbound leads: [paste your About section or resume]"
```
*What happens:* The agent audits your 9 profile components and delivers a 220-char headline, a 7-step About section with a <265-char mobile hook, and featured item recommendations.

---

### 🚦 The Approval & Publishing Flow

Whenever the agent finishes drafting, it displays an **Approval Card** and halts:

```
────────────────────────────────────────────────────────────────
📋 POST APPROVAL CARD
Formula: F7 Number-First Technical Build Log
Length:  1,120 chars (optimal 900-1,300 range)
Account: Your LinkedIn Channel
Draft:   [Preview of the post text]
────────────────────────────────────────────────────────────────
```

You have complete control:
* **To publish immediately:** Type `post` or `publish`.
* **To schedule for later:** Type `schedule for tomorrow at 9:00 AM`.
* **To request edits:** Type your feedback (e.g., *"make the opening punchier"* or *"mention Jenkins multibranch pipelines"*).
* **To cancel a scheduled post:** Type `cancel scheduled post [postGroupId]`.

---

## The Core Pattern (Approval Loop)

Every action follows three non-negotiable steps:

```
[ 1. Input ]   ──> User supplies an idea, topic, or target LinkedIn URL
                         │
                         ▼
[ 2. Draft ]   ──> Agent checks Story Bank + applies 2026 rules + generates draft
                         │
                         ▼
[ 3. Action ]  ──> Agent displays an Approval Card and WAITS
                         │
                         ├─ User requests changes ──> Agent iterates draft
                         └─ User says "post" ───────> Agent publishes via Publora API
```

---

## Real-World Case Study & Walkthrough

Here is the exact step-by-step workflow demonstrated in this project:

### Phase 1: Building the Story Bank
The **Story Bank** (`references/story-bank.md`) is your career memory file. Instead of asking for numbers and dates on every draft, the skills read this file.

* **Subject Profile:** Marshal Alone, 2026 B.Tech Computer Science graduate from RTMNU Nagpur (8.0 CGPA).
* **Skills:** Core Java, OOP, Collections, SQL, Node.js, Express.js, MongoDB, REST APIs.
* **DevOps Practice on AWS:** EC2 setup with Maven, SonarQube, JaCoCo, Nexus, and Jenkins CI/CD.
* **Real Project Receipts:**
  - `Mail-E`: Campus recruitment notification app using Node.js, Telegram Bot API, and a local Android Wi-Fi SMS gateway with `Promise.allSettled()` and `AbortSignal` timeouts.
  - `FarmRent`: Farmer machinery sharing platform selected at the state-level NIRMAN Hackathon.
  - `ApplicationTracker`: Chrome extension extracting job portal metadata into a custom dashboard.

---

### Phase 2: Writing a 2026 Algorithm-Optimized Post

Using `linkedin-post-writer`, we selected **Formula F7 (Number-First Technical Build Log)**:
* **2026 Rule Check:** Line 1 starts with a number (+34% median likes); hook completes under 210 characters; no generic questions as openers (-34% penalty); zero AI tells.

#### The Draft:
```text
5 AWS servers configured from scratch taught me more about backend engineering than any classroom tutorial.

While studying Core Java and Collections at QSpiders Wakad, I noticed a huge gap in how freshers prepare.

Most of us spend weeks writing loops and solving syntax exercises. But production systems don't live in an IDE console.

Last week, I set up a complete build and delivery pipeline on EC2:
- Maven to build and manage dependencies
- SonarQube to catch code smells before they hit staging
- JaCoCo to track line and branch test coverage
- Nexus to store verified build artifacts
- Jenkins to automate the whole flow

When you configure SonarQube quality gates yourself, you stop writing code just to "make it run". You start caring about clean architecture, exception boundaries, and maintainability.

I'm graduating in 2026 (B.Tech CSE, 8.0 CGPA) with hands-on practice in Java, SQL, and Node.js. 

I don't just want to write backend logic.. I want to build reliable software that is ready for production pipelines.

For senior Java engineers and hiring managers: what is the one deployment or testing habit you wish every fresher understood on day one?

P.S. Currently diving deep into Jenkins multibranch pipelines and Advanced Java.
```

#### The Approval Card:
* **Formula:** F7 (Number-First Technical Build Log)
* **Goal:** High-value engagement from Tech Leads & Recruiters
* **Length:** 1,120 chars (optimal 900–1,300 sweet spot)
* **Status:** Ready for one-word confirmation (`post`) to trigger Publora.

---

### Phase 3: The 2026 Profile Optimization Blueprint

Using `linkedin-profile-optimizer`, we audited and rewrote the candidate's profile to maximize recruiter inbound discovery:

#### 1. Headline (Budget: 220 chars max)
* **Formula:** `[What You Do] | [Who You Help / Tech Focus] | [Proof / Target Role]`
* **Optimized Version (196 chars):**
  ```text
  Java Backend & Full Stack Developer | Building Production-Ready Web Apps & REST APIs | Core Java, SQL, Node.js, AWS & Jenkins CI/CD | 2026 CSE Graduate (8.0 CGPA) seeking Entry-Level Backend Roles
  ```

#### 2. About Section (7-Step Framework)
* **Rule:** The first 2 lines must hook before the **265-character mobile cutoff**.
* **Hook (157 chars):**
  > *"Most freshers write code that only runs in an IDE console. I build backend systems designed for automated testing, code quality gates, and production pipelines."*
* **Full Body:** Highlights B.Tech CGPA (8.0/10), QSpiders Wakad training, `Mail-E`, `FarmRent`, AWS EC2 pipeline details, clean keyword section, and low-friction contact CTA (`marshal3869@gmail.com`).

#### 3. Featured Section Strategy
1. **Item 1:** Direct link to `Mail-E` GitHub repository with 1200x627 cover image.
2. **Item 2:** NIRMAN State-Level Hackathon certificate and architecture slides.
3. **Item 3:** Downloadable PDF Resume.

#### 4. Skills Strategy
* **Top 3 Pinned Skills:** `Java`, `SQL`, `REST APIs`
* **Additional Keywords:** `Core Java`, `Spring Framework`, `Jenkins`, `AWS`, `Maven`, `SonarQube`, `Node.js`, `Express.js`, `Git`, `Linux`, `MongoDB`.

---

## The 12 Skills Catalog

| Skill Name | Purpose |
|---|---|
| [`linkedin-post-writer`](skills/linkedin-post-writer) | Drafts viral posts with 20 hook formulas (F1–F20) and founder angles. |
| [`linkedin-humanizer`](skills/linkedin-humanizer) | Strips AI tells, scores emoji density, and audits drafts against slop filters. |
| [`linkedin-profile-optimizer`](skills/linkedin-profile-optimizer) | Audits and rewrites all 9 LinkedIn profile sections for inbound leads. |
| [`linkedin-content-planner`](skills/linkedin-content-planner) | Generates a 7-day post schedule across general or founder pillars. |
| [`linkedin-interviewer`](skills/linkedin-interviewer) | Interviews you to build and update your personal `references/story-bank.md`. |
| [`linkedin-comment-drafter`](skills/linkedin-comment-drafter) | Drafts high-depth comments on any post URL. |
| [`linkedin-reply-handler`](skills/linkedin-reply-handler) | Sweeps threads and drafts batched replies. |
| [`linkedin-hook-extractor`](skills/linkedin-hook-extractor) | Reverse-engineers viral posts into reusable templates. |
| [`linkedin-engager-analytics`](skills/linkedin-engager-analytics) | Pulls commenters and likers, segmenting by ICP fit. |
| [`linkedin-thread-monitor`](skills/linkedin-thread-monitor) | Tracks your comment threads for the 6–24h follow-up window. |
| [`linkedin-repurposer`](skills/linkedin-repurposer) | Converts tweets, blogs, and YouTube videos into native LinkedIn posts. |
| [`linkedin-employee-advocacy`](skills/linkedin-employee-advocacy) | Plans team-wide employee advocacy roadmaps. |

---

## Apify Read Layer (Optional)

If you connect `APIFY_TOKEN`, the skills can read post bodies, comment threads, and engagers without cookies:

| Use case | Actor | Cost |
|---|---|---|
| Post body by URL | `apimaestro/linkedin-post-detail` | $1 / 1,000 |
| Comments + replies on a post | `apimaestro/linkedin-post-comments-replies-engagements-scraper-no-cookies` | $5 / 1,000 |
| Your own recent comments | `apimaestro/linkedin-profile-comments` | $5 / 1,000 |
| Likers + commenters on any post | `scraping_solutions/linkedin-posts-engagers-likers-and-commenters-no-cookies` | $5 / 1,000 |

*(Without Apify, the skills simply ask you to paste the text directly into the chat — 100% free).*

---

## Verification & Test Suite

Verify your entire repository anytime:

```bash
# 1. Run live credential diagnostics
python scripts/check_config.py

# 2. Run the full platform self-test
python scripts/selftest.py

# 3. Run all unit tests
python -m unittest discover -s tests
```

---

## License

This project is licensed under the [MIT License](LICENSE).
