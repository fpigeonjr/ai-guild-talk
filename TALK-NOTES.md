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

1. **Description** — WHEN (the trigger the agent reads)
2. **Instructions** — HOW (step-by-step, the way you'd do it)
3. **Format** — SHAPE (what the output looks like)
4. **Guardrails** — SAFETY (rules that keep it on the rails)

## The three demos — three distinct jobs, decreasing depth

1. **`submit-pr-review` — DEEP (the anatomy specimen).** The hero. Raw SKILL.md, name
   the four parts, tell the teammate-adoption story. This is where the *pattern* is taught.
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

## Time budget

~20 min + Q&A. Only Demo 1 is deep; Demos 2–3 stay fast.

## TODO before the talk

- [ ] Record `assets/demo-pr-review.gif`
- [ ] Record `assets/demo-grill-me.gif` (use a PM/design-flavored plan)
- [ ] GitHub Pages URLs for Demo 3: ________________________________________
- [ ] Confirm repo link for the chat: `iae-sam-engineering-practices` PR #22
- [ ] Verify the real `submit-pr-review` description text matches slide 6
