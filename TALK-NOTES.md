# Talk Notes — Shipping with AI Skills

Decision record for this talk. Kept so future-you (or a co-presenter) understands *why*
the deck is shaped the way it is — not just what's on each slide.

## North star

**The audience should leave feeling they understand what a skill is and have the
confidence to build their own.** This is an enablement talk, not a story talk. The
PR-review origin story is scaffolding to make the concept concrete.

## The spine (one sentence to remember)

> A skill is a reusable instruction file that teaches your agent **how** to do a task
> the way you'd want it done — and **when** to reach for it.

- **How** = instructions, format, guardrails.
- **When** = the `description`, the one thing the agent reads to decide to use it.
- The "when" is the piece that turns a prompt into a skill — most beginners miss it.

## Shape: example-driven pattern (not pure story)

Chosen "Shape B": the PR-review skill is the running specimen that makes the *general*
concept concrete, then we explicitly generalize so people can map it to their own task.
Pure story would teach *my* skill, not *the pattern* — and confidence to build comes
from seeing the anatomy abstracted at least once.

## Audience

AI Guild — engineer-majority, with a mixed tail (PMs, designers, analysts). Keep the
PR-review hero (lands with the majority + carries the emotional hook) **and** pair it
with a non-dev skill so the tail sees themselves. Cap the body at three specimens.

## The four-part anatomy (taught once, in Demo 1)

1. **Description** — WHEN + WHAT (the trigger the agent reads)
2. **Instructions** — HOW (step-by-step, the way you'd do it)
3. **Format** — SHAPE (what the output looks like)
4. **Guardrails** — SAFETY (rules that keep it on the rails)

### Spec alignment (Anthropic Agent Skills)

Checked against platform.claude.com Agent Skills → "Skill structure." The canonical
spec is: frontmatter (`name` + `description`) + `## Instructions` + `## Examples`, where
**`description` must include both *what* it does and *when* Claude should use it.**
So slide 3's Description card is labeled **WHEN + WHAT** to match the spec exactly.
**Format** and **Guardrails** are *not* named spec fields — they're practitioner
conventions (present in the real `submit-pr-review` skill). Slide 3 says this outright:
"description + instructions are the spec; format & guardrails are conventions that make
skills reliable." This keeps a spec-reader nodding while still teaching the practical anatomy.

## The three demos — three distinct jobs, decreasing depth

1. **`submit-pr-review` — DEEP (the anatomy specimen).** The hero. Raw SKILL.md, name
   the four parts, tell the teammate-adoption story. This is where the *pattern* is taught.

   **The real backstory (slide 4):** In my work environment we don't have automated
   Copilot PR reviews — so I set out to build my own. Then I found Matt Pocock's skills
   repo, took his, made it mine. Two weeks later my teammates got envious and wanted to
   see how I made it + how to use it. The recursive punchline: I stole-and-adapted exactly
   like I'm telling the audience to — then it happened *to* me. Frame the constraint as
   "we don't have access to automated Copilot reviews in my environment" — not a complaint
   about the org, not a policy workaround. The "output isn't perfect, ready to edit and send"
   expectation-setting line moved to the gif slide (slide 5).
2. **`grill-me` — GENERALIZE (same skeleton, zero code).** Fast. Don't re-teach anatomy.
   Meta-beat: *this talk was grilled into shape by this skill.* Proves the pattern travels.
3. **`teach` — CEILING (how far it scales).** Show real GitHub Pages output, not the file.
   "Skills scale way up — but you don't start here."

## write-a-skill — the on-ramp, not a fourth demo

Placed in the close, not the body. It's not a specimen to admire; it's the on-ramp:
"you don't even write the file by hand — there's a skill that interviews you and writes
it. So the barrier isn't skill, it's picking the one task."

## Homage — Matt Pocock

Credit line on the opening slide, linking https://github.com/mattpocock/skills
("Skills For Real Engineers"). His philosophy — *small, easy to adapt, composable,
make them your own* — is the direct inspiration for this repo and reinforces the talk's
north star (the Monday CTA is literally "make one your own"). Keep it on slide 1 only,
not the definition slide, so it credits without derailing the teaching flow.

## References — on the Q&A slide, not slide 2

Slide 2 (the definition) stays a single crisp idea — no links. References live on the
Q&A slide where people are writing things down. Lineage credited there:
**Anthropic Agent Skills** (the `SKILL.md` format spec, built for Claude Code) → **Matt
Pocock's repo** (built on it) → this talk's skills (inspired by Matt). Anthropic is the
root “spec,” though it's a format + conventions, not a formal standard.

## The format spec link (slide 3)

Slide 3 links to **agentskills.io/specification** — a formal, standalone spec for the
`SKILL.md` format (frontmatter `name`, `description`, `license`, `compatibility`,
`metadata`, `allowed-tools`; `scripts/references/assets/` dirs; progressive disclosure).
It is **not** Anthropic's own docs and carries no explicit affiliation statement, so it's
labeled neutrally — “The format spec: Agent Skills · agentskills.io” — not “the Anthropic
spec.” It's richer than Anthropic's overview and validates slide 3 better (`allowed-tools`
is a named field there). On the Q&A slide: agentskills.io = the full spec, Anthropic docs
= where the format came from. Say it that way on stage to stay accurate.

## Emotional arc

- **Open:** social proof + promise ("teammates adopted it in two weeks; by the end
  you'll know how to build your own"). Concrete surprise beats an abstract reframe cold.
- **Body:** definition → three demos (deep → generalize → ceiling).
- **Close:** the *earned* reframe — "none of these made me faster; they removed the
  friction" — lands only after they've watched it happen three times. Then the CTA.

## Call to action (do-it-Monday)

> Pick one thing you retype every week. Write down how you'd tell a new hire to do it.
> Save it as a `.md` file. That's a skill.

Close line: **"The repo link is in the chat. Try it once. That's all it takes."**

## Live-demo risk

Default to pre-recorded gifs — a stalled live LLM demo undercuts the "confidence"
message. Treat any live demo (Demo 2) as an optional bonus if wifi + room energy allow.

**Exception — Demo 1 is now LIVE (slide 5).** We run `submit-pr-review` against a real PR
on stage: `github.com/fpigeonjr/ai-guild-talk` PR #8. The PR has three seeded flaws
(no `localStorage` persistence = unmet AC → blocking; toggle click also advances the
slide = propagation bug → blocking; light-theme `--muted` fails WCAG contrast → important).
Dry-run confirmed the skill catches all three and lands on **Request Changes**. Watch beat:
the **approval gate** — it drafts, then waits; nothing posts until approved. **Before the
talk, run it COLD in the real harness once** — the dry-run was authored in the same
session, so it's not a fully independent signal. Fallback: the drafted review is saved (see
below) — read it aloud and move on if the live run stalls.

### Demo 1 fallback review (paste-ready if live fails)
The full drafted Request-Changes review from the dry-run is reproducible via
`submit-pr-review 8`; keep a copy in PRIVATE-NOTES or a scratch file the morning of.

**Demo 2 is also LIVE (slide 9).** Origin story: "I met with the UX team last week — they
wanted a theme picker, but we never got to specifics." There is deliberately NO theme issue
in the repo (deleted #2; its spec is stashed in PRIVATE-NOTES). On stage, run `grill-me` on
the fuzzy theme-picker ask; it asks one question at a time until the ask has edges (which
themes, switcher behavior, persistence). Then chain into `to-issues` to slice the sharpened
plan into grabbable tickets. DECIDED: use `to-issues` (dogfood both skills on stage), not a
quick `gh issue create`.

Gotchas to narrate / expect with `to-issues`:
- It DECOMPOSES into multiple tracer-bullet slices — expect ~2–3 issues (e.g. warm theme,
  high-contrast theme, switcher+persistence), NOT a single recreated #2. That's the point:
  grill-me sharpens → to-issues slices.
- Step 4 is a QUIZ gate: it shows the numbered breakdown and iterates until I approve before
  publishing anything. Narrate this as the SECOND human-in-the-loop gate (after
  submit-pr-review's approval gate). Callback to slide 2's guardrail beat.
- No domain glossary / ADRs in this repo, so it'll skip those; may briefly explore the repo.
After publishing, optionally compare what we derived vs. the stashed old #2.
Fallback if grilling stalls: talk through the branches from the stashed #2 spec.

## Time budget

~20 min + Q&A (50 min slot, stop when done). Only Demo 1 is deep; Demos 2–3 stay fast.

## TODO before the talk

- [ ] **Run `submit-pr-review` cold against PR #8 in the real harness** (de-risk the live demo)
- [ ] Record `assets/demo-grill-me.gif` (use a PM/design-flavored plan)
- [ ] GitHub Pages URLs for Demo 3: ________________________________________
- [ ] Confirm repo link for the chat (real internal repo/PR — see PRIVATE-NOTES.md, git-ignored)
- [ ] Verify the real `submit-pr-review` description text matches slide 6
