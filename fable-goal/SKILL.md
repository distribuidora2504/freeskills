---
name: fable-goal
description: Convert a rambling description of a desired outcome into a polished, autonomous /goal prompt for Fable. Use whenever Duncan says /fable-goal, "turn this into a goal prompt", "write me a fable prompt", "I want fable to build X, write the prompt", or rambles about something he wants made and asks for the prompt that makes it. The output is a single copy-paste prompt, not the build itself. Do NOT use when Duncan wants the thing built right now in this session; only when he wants the PROMPT that will make it happen in a fresh session.
---

# Fable Goal Prompt Writer

Turn Duncan's voice-to-text ramble into one exceptional /goal prompt he can paste into a fresh Fable session. You are not building the thing. You are designing the prompt that builds the thing.

## The philosophy

The core idea, in Duncan's words: **get out of the model's way.** Fable is smart enough to do almost anything if the prompt (1) articulates the desire clearly, (2) hands it tools, and (3) gives it a way to verify its own work. A great /goal prompt does not micromanage the how. It nails the what, grants explicit creative freedom on execution, and demands self-verification before done.

The reference example that defines the genre: "I want to build 25 websites with Fable to demonstrate its extreme capabilities... you have total creative freedom... host on Netlify and serve me the link... do at least three iteration passes before you ok each site... 25 websites hosted on Netlify with /guide routes and three iteration passes is your /goal. Work completely autonomously and do not ask me for anything until you are all done."

## Process

### 1. Extract what the ramble already contains

Duncan uses voice-to-text and thinks in fragments. Interpret intent over literal words (misheard terms like "Quad MD" mean CLAUDE.md, "Netlefi" means Netlify). Pull out: the deliverable, the quantity, the audience or purpose, any tools he named, any quality bar he implied, and where results should land.

### 2. Fill gaps with his defaults; ask only when it matters

Synthesize small gaps yourself. Ask a question ONLY when the answer would meaningfully change the prompt, and there are exactly three things worth asking about:

- **Outcome** — if you genuinely can't tell what the deliverable is
- **Scale** — if quantity changes the shape of the work (5 vs 50) and nothing implies it
- **Destination** — if you can't infer where results should land (hosted link, local folder, published post, vault file)

If you ask, ask all questions in ONE AskUserQuestion batch, then write the prompt. Never interview in rounds. If the ramble covers the basics, ask nothing and note your assumptions instead.

**Duncan's standing defaults** (a menu, not a mandate — pull in ONLY the entries the task actually touches; a research prompt should not mention the design system, a carousel prompt should not mention Netlify). Tools change per task, so when in doubt leave it out and let the discovery mandate cover it. And the menu is advisory even to you: if a better tool exists for the task than what is listed here, use that instead. Duncan wants Fable making all the decisions; the goal is for Fable to figure it out, not to follow a hardcoded kit list:

- Visual work uses the RISO editorial design system at `~/.claude/design-system/DESIGN.md` (ink-orange #E96A3C, charcoal, cream, Anton/Druk + JetBrains Mono + Inter). Build Room product UI is the one exception (dark brand at `~/.claude/buildroom-brand/`). Name the design system path in the prompt so the fresh session can read it.
- Audience framing: 200K+ followers, Claude Code Club (5,000+ members), non-developer builders escaping 9-5. If the output will be shown publicly, say so in the prompt; stakes raise quality.
- Content/brand work draws from the Obsidian Vault at `~/Documents/Obsidian Vault/` (brand voice, ICP, proof bank). Point the prompt at specific files only if the task needs them.
- API keys live in `~/.claude/.env`. Media generation goes through the Higgsfield MCP (images, video, audio, 3D) or the Higgsfield CLI. Publishing goes through Blotato MCP. Web research through firecrawl. Sites deploy wherever Duncan says; if unstated and it needs hosting, default to Netlify.
- No em dashes anywhere in the prompt. Never the word "solopreneur".

**Verify before you name.** A goal prompt that points at a skill, path, or MCP that does not exist sends the fresh session on a dead-end hunt. Before writing the prompt, spend 30 seconds confirming the specific resources you plan to name: `ls` the file paths, check the skill exists in `~/.claude/skills/`, glance at the available-tools list for the MCP. The live environment is the source of truth, not the menu above. Name only what you verified AND what is load-bearing for this task (usually 2-4 things). Everything else, including anything missing or uncertain, is the discovery mandate's job: the prompt tells Fable to find or figure out what it needs.

### 3. Write the prompt using this anatomy

Every /goal prompt has seven parts, woven as natural flowing prose (not headers, not a bulleted spec). First person, as Duncan speaking to Fable:

1. **Desire + stakes.** What he wants and why it matters. Concrete deliverable, concrete quantity. If it will be seen by his audience, say so with the real number. Stakes make the model try harder.
2. **Quality bar.** What excellent looks like for this task, in a sentence or two. Vivid adjectives beat specs ("otherworldly beautiful animations, exceptional color palettes").
3. **Tool inventory + discovery mandate.** Name the specific tools, MCPs, file paths, and keys the session will have (only ones you verified exist), sketch one example workflow as a suggestion, then immediately release it: "you can accomplish this many ways." Then grant discovery: tell the session it is expected to go FIND whatever else it needs rather than working from memory or stopping short. That means searching the web for design references and current best practices, pulling open-source libraries, repos, fonts, or component kits when they beat hand-rolling, downloading or generating assets, and inventorying its own available tools at the start of the run so it knows what it is working with. One sentence like "before you start, take stock of the tools and MCPs you actually have, and go find or fetch any references, libraries, or assets you need along the way; the internet is available to you" turns a session that guesses into a session that hunts.
4. **Creative freedom + decision authority grant.** Explicit permission to deviate, choose workflows, and "show what you're capable of." This is the get-out-of-the-way clause; never skip it. It covers tools too: any tool named in the prompt is a suggestion, and the session should swap in a better one if it finds one. Duncan's standing instruction is "make all my decisions," so every judgment call that comes up mid-run (naming, styling, scope edges, tradeoffs) gets decided by the session with taste, not deferred back to him.
5. **Verification loop.** How the model checks its own work before calling anything done. Default: at least three iteration passes, where a pass means going back through the finished output with a fine-toothed comb looking for problems and opportunities to improve. Adapt the verification to the medium (render and watch the video, load the page and click through it, run the script on real input).
6. **Delivery.** Exactly where results land and what gets served back (the link, the file path, the post URL).
7. **The goal line + autonomy directive.** Close by restating the deliverable as a single sentence: "[X with Y and Z] is your /goal. Work completely autonomously and do not ask me for anything until you are all done." For big parallelizable jobs, add a nudge to use subagents/workflows to parallelize.

Length target: 150-350 words. Long enough to carry stakes, tools, and verification; short enough that nothing dilutes the goal line.

### 4. Deliver

Output the prompt in a single fenced code block so it copies clean. Below it, add a short **Assumptions** list (2-4 bullets max) covering the gaps you filled, so Duncan can correct anything with one line instead of re-rambling. Nothing else. No preamble above the code block.

## Example

**Ramble:** "I want like 5 different landing pages for the claude code club free prompt pack thing, they should all look totally different and crazy good, put them up somewhere I can look at them"

**Output:**

```
I want you to build 5 landing pages for the Claude Code Club free prompt pack, each one fundamentally different from the others, as a way to show me the strongest possible range of directions before I pick one. These will be seen by my audience of 200K+ followers, so the bar is high: exceptional typography, striking layouts, and motion that feels designed rather than templated. My house design system is the RISO editorial style documented at ~/.claude/design-system/DESIGN.md; at least 3 of the 5 should build on it, and you have total creative freedom to break from it on the others if you believe it makes a stronger page. Each page needs a headline, proof, and a single email-capture CTA for the prompt pack. You can generate any imagery you need with the Higgsfield MCP, and you can accomplish this in many ways using many workflows, so show me what you are capable of. Before you ok each page, do at least three iteration passes: go back through the live page with a fine-toothed comb looking for design problems and opportunities to improve and complexify. Parallelize across subagents so the pages develop independently. When all 5 are done, deploy them to Netlify and serve me the 5 links with a one-line description of each direction. 5 fundamentally different Claude Code Club prompt pack landing pages, live on Netlify with three iteration passes each, is your /goal. Work completely autonomously and do not ask me for anything until you are all done.
```

**Assumptions:**
- CTA is email capture for the prompt pack (no ManyChat wiring since these are review candidates, not live pages)
- Netlify for hosting since you said "put them up somewhere"
- 3 of 5 anchored to RISO, 2 free-range, so you get both on-brand and surprise options
