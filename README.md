<p align="center">
  <img src="./logo.png" alt="korter" width="140" />
</p>
<p align="center">
  <strong align="center">Terse, action-first outputs. No diagnosis needed!</strong>
</p>
<p align="center">
  <a href="LICENSE"><img src="https://img.shields.io/github/license/crooy/korter?style=flat" alt="License"></a>
</p>



## Install

Copy/paste into your CLI prompt:

```text
Install the korter skill/plugin from https://github.com/crooy/korter, refer to the repo's AGENTS.md for instructions.
```

Or 🔗 [check the installation instructions](INSTALL.md).

## What it does

A skill for your coding assistant that stops it from burying the answer. Action first. Steps numbered. No "Hope this helps!"

[Kacper Rutkiewicz | AI Made Simple](https://youtu.be/NEl8kPWZP_Y) has made a good breakdown of an earlier version of the skill.
## What changes


<table>
<tr>
<td width="50%">

## Before

> Great question! Let me think about this. Your auth flow has a few moving pieces: the middleware, the token verification, and the cookie handling. Looking at `src/auth.ts`, the `verifyToken` function (around lines 42-58) seems to be using an older `jsonwebtoken` API. One approach would be to update the package and rewrite that function. After making the change, you'd want to run the auth tests to confirm nothing breaks. By the way, you might also want to look at your dependency versions overall. Hope this helps! Let me know if you want to dig deeper.

</td>

<td width="50%">

## After

> Edit `src/auth.ts:42` to update the token validation.
>
> 1. Open `src/auth.ts`
> 2. Replace `verifyToken` (lines 42–58) with the snippet below
> 3. Run `npm test -- auth.spec.ts`
>
> Next: paste the first failing line if any test fails.

</td>
</tr>
</table>


## The rules

13 rules. Full text in [SKILL.md](./skills/korter/SKILL.md).

1. Lead with the next action.
2. Number multi-step tasks.
3. End with one concrete next step.
4. Suppress tangents.
5. Restate state every turn.
6. Specific time estimates (minutes, not "a bit").
7. Make wins visible.
8. Matter-of-fact errors.
9. Cap lists to 5 items.
10. English always: user may write in any language or mix languages; response stays English.
11. Diagrams over text or code whenever a diagram fits.
12. No preamble. No recap. No closers.
13. Fewer words: no filler, no empty hedging, fragments fine.

## Tune it

Fork, edit `skills/korter/SKILL.md`, then swap your copy in:

```bash
claude plugin uninstall korter            # drop the upstream copy first:
claude plugin marketplace remove korter   # fork and upstream share both names
claude plugin marketplace add <your-username>/korter
claude plugin install korter@korter
```

Restart your coding assistant, then re-invoke `/korter`.

## Credits

Derived work. Two skills, merged and reshaped:

- **i-have-adhd** by **Ayoub Ghriss** ([@ayghri](https://github.com/ayghri)) — [github.com/ayghri/i-have-adhd](https://github.com/ayghri/i-have-adhd) (MIT). Source of the action-first response rules (1–9), the persistence model, and this fork's starting structure.
- **caveman** by **Julius Brussee** ([@JuliusBrussee](https://github.com/JuliusBrussee)) — [github.com/JuliusBrussee/caveman](https://github.com/JuliusBrussee/caveman) (Apache-2.0). Source of the compression mechanics behind rule 13: drop filler, fragments fine, never drop negations, numbers/units/code verbatim, and "compression never grows output".

korter's additions on top: rule 10 (English always for multilingual users), rule 11 (diagrams over words), rule 13's merge with action-first structure, and the "Why terse helps" framing.

Also based on ideas from J. Russell Ramsay and Anthony L. Rostain's work on practical, action-first working habits; adapted for how an LLM should respond, not how a human should organize their day.

## License

[MIT](LICENSE).

Star ⭐ if it saved you one scroll past one "Great question!"
