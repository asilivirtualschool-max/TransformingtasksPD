# Designing Worthwhile Tasks with AI

Five certificated, self-paced professional development courses for teachers, plus an interactive prompt builder. Thirty hours across twenty modules, portfolio-assessed, with no examination and no lesson observation.

**Live site:** https://asilivirtualschool-max.github.io/worthwhile-tasks/

| Course | Hours | Strategy | Techniques |
|---|---|---|---|
| **PD 1 — Intellectual Challenge** | 6 | Foundation | Level and kind of thinking · fluency and fluency plus · reading the challenge · conditions for challenge |
| **PD 2 — From Closed to Open** | 6 | Closed → open | Different perspectives · many solutions · many pathways · many entry points |
| **PD 3 — From Tell to Ask** | 6 | Tell → ask | Explore before explain · Socratic questioning · student voice · use dialogue |
| **PD 4 — From Procedure to Problem Solving** | 6 | Procedure → problem solving | Students determine the problem · insufficient information · no steps · irrelevant information |
| **PD 5 — The Prompt Builder** | 6 | MAP → AIM → CRUCIBLE → OCEAN | The Fuel · The Engine · The Crucible · The Polish — with a live builder |

Take PD 1 first — the others assume it. PD 2, 3 and 4 each end with a commitment to action: teach something, and bring back what happened. PD 5 is the practical companion — how to ask a model for the task the others taught you to want — and its workspace, `prompt-builder.html`, is usable on its own.

## How it works

Each course is a single page with six panels — an introduction, four modules, and a portfolio workspace.

- **Progress and answers save to the browser.** No account, no server, nothing uploaded anywhere. `localStorage` only.
- **Self-test questions give feedback on wrong answers**, not just the right one. Open questions have a model answer you can reveal.
- **The portfolio workspace** collects the three assessed pieces per course and exports them as a plain text file.
- **Print or save as PDF** expands every panel, so a whole course prints as a readable document.
- **AI briefs** are given as copy-and-paste prompts throughout, with the reasoning for each constraint.

## Structure

```
index.html                               landing page
programme.html                           the ten-day programme and the 30-day clinic
pd1-intellectual-challenge.html          PD 1
pd2-closed-to-open.html                  PD 2
pd3-tell-to-ask.html                     PD 3
pd4-procedure-to-problem-solving.html    PD 4
pd5-prompt-builder.html                  PD 5
prompt-builder.html                      the interactive workspace (standalone app)
assets/site.css                          shared site styling
.nojekyll                                serve files as-is, no Jekyll processing
ATTRIBUTION.md                           source, credit and the licensing question
```

Each course is scoped under its own CSS prefix (`.wt1-course` … `.wt5-course`) and uses a separate `localStorage` key, so any two can sit on the same page without colliding and neither can leak styles into a host page.

## Publishing to GitHub Pages

1. Create a repository named `worthwhile-tasks` under `asilivirtualschool-max`.
2. Push the contents of this folder to the `main` branch.
3. Settings → Pages → Source: `main`, folder `/ (root)`.

The `.nojekyll` file is required — without it GitHub ignores files and folders beginning with an underscore and can interfere with the raw HTML.

## Before this is used commercially

See `ATTRIBUTION.md`. The Transforming Tasks framework belongs to the South Australian Department for Education. Confirm the licensing position in writing before selling access to these courses.

## The Prompt Builder

`prompt-builder.html` is a standalone single-page app — its own chalkboard styling, no dependency on `assets/site.css`, and no build step. It walks the four stages, assembles the prompt live, and has the four Transforming Tasks differentiation strategies (with subject exemplar links) and the twenty formative assessment check-ins built in. Nothing is stored or sent anywhere; the Copy button puts the finished prompt on the clipboard.

It is linked from PD 5 and from the site navigation, and it works perfectly well as a link on its own — it is the most shareable single artefact in the repository.
