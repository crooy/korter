# How to install

<details>
<summary><strong>Antigravity (<code>agy</code>)</strong></summary>

### Install

```bash
agy plugin install https://github.com/ayghri/mand
```

### Verify

```bash
agy plugin list
```

### Update

```bash
agy plugin uninstall mand
agy plugin install https://github.com/ayghri/mand
```

### Uninstall

```bash
agy plugin uninstall mand
```

Or keep it installed and turn it off: `agy plugin disable mand`.

### Always-on (optional)

Add to `~/.gemini/GEMINI.md`:

```markdown
## Output style

Answer terse and action-first. Shape every response so it can be acted on:

1. Lead with the answer or next action: command, path, or snippet first.
2. Number multi-step work; one bounded action per step.
3. End with one next action doable in under two minutes.
4. Finish the current issue before raising a new one.
5. Restate progress each turn ("step 3 of 5 done").
6. Give time estimates in concrete units, never "a bit".
7. After a change, show what now works.
8. Errors: state location, cause, and fix. No drama.
9. Cap lists to 5 items.
10. Respond in English, whatever the input or code language.
11. Prefer diagrams over text or code when a diagram can carry the meaning.
12. No preamble, no recaps, no closers.

Exceptions: explain fully when asked to explain. Confirm before destructive actions. After three failed fixes, stop and name the doubtful assumption. If the request is ambiguous, ask one short question.
```

</details>

<details>
<summary><strong>AstronClaw (custom skill)</strong></summary>

AstronClaw supports importing a Markdown file as a custom skill. This route uses
the existing `SKILL.md`; see its [official skills guide](https://github.com/iflytek/astronclaw-tutorial/blob/main/docs/guide/astronclaw/skills.md)
for the upload and management controls.

This procedure follows AstronClaw's documentation but has not been tested with
this skill. Check the exported instructions before enabling it.

### Install

1. Download the [canonical SKILL.md](https://raw.githubusercontent.com/ayghri/mand/main/skills/mand/SKILL.md) and save it as `SKILL.md`. Review its contents before uploading.
2. In AstronClaw, open **我的技能 (My skills)**, choose **新建 (New)**, and upload that `.md` file.
3. Check that the imported skill is named `mand`. Use **启用/禁用 (Enable/Disable)** to control its availability.

Only the skill Markdown is needed. Uploading sends that file to AstronClaw;
the repository's plugin manifests and hooks are not part of this setup.

### Verify and activate

Confirm `mand` appears in **My skills**. Use **下载 (Download)** to review
the imported instructions against the original skill, then enable it and try:

```text
Use the mand skill for this conversation. Explain how to create an empty Git repository in a new folder.
```

Check that the reply leads with the action and numbers the steps. This is a
manual check of the imported skill; a successful upload alone does not verify
that its response rules are being applied.

### Activation note

AstronClaw supports both explicit requests and automatic skill invocation.
Its guide does not specify whether it honors `disable-model-invocation: true`,
so use **Disable** when you do not want the skill available. There is no need
to rely on a `/mand` slash command.

The skill instructs the assistant to keep the style for the conversation until
you say `stop mand` or `normal mode`. That instruction does not change the
platform toggle; disable the skill and start a new conversation for a fresh
session without it.

### Update

Download the latest canonical `SKILL.md`. If you customized the imported copy,
use **下载 (Download)** to keep a backup first. For a clean replacement, delete
the old `mand` entry, repeat the import, and run the verification prompt
in a new conversation.

### Uninstall

In **My skills**, select `mand` and choose **删除 (Delete)**, then start a
new conversation. To keep the imported copy for later, choose **Disable** instead.

</details>

<details>
<summary><strong>Claude Code</strong></summary>

### Install

```bash
claude plugin marketplace add ayghri/mand
claude plugin install mand@mand
```

Type `/mand`.

### Verify

```bash
claude plugin list
```

### Update

```bash
claude plugin marketplace update mand
claude plugin update mand@mand
```

The first command refreshes the marketplace listing. The second updates the installed plugin. Restart Claude Code to load it.

`claude plugin update` skips a plugin whose `version` has not changed. If you maintain a fork, bump `version` in `.claude-plugin/plugin.json` after you edit the rules.

### Uninstall

```bash
claude plugin uninstall mand
claude plugin marketplace remove mand
```

Or keep it installed and turn it off: `claude plugin disable mand`.

### Always-on (optional)

A `SessionStart` hook loads the full ruleset at the start of every session, no `/mand` needed:

```bash
touch ~/.claude/.mand-always
```

If you use a custom Claude configuration directory, create the flag there instead:

```bash
touch "$CLAUDE_CONFIG_DIR/.mand-always"
```

Back to on-demand:

```bash
rm ~/.claude/.mand-always
```

The hook only fires when the flag file exists, so installing the plugin changes nothing by itself. "stop mand" still turns it off for the current session.

</details>


<details>
<summary><strong>Codex</strong></summary>

### Install

```bash
codex plugin marketplace add ayghri/mand --ref main
codex plugin add mand@mand
```

Invoke the skill explicitly by typing `$mand`. Codex will not activate
it automatically.

### Verify

```bash
codex plugin list
```

### Update

```bash
codex plugin marketplace upgrade mand
codex plugin remove mand
codex plugin add mand@mand
```

### Uninstall

```bash
codex plugin remove mand
codex plugin marketplace remove mand
```

### Always-on (optional)

Add to `~/.codex/AGENTS.md`:

```markdown
## Output style

Answer terse and action-first. Shape every response so it can be acted on:

1. Lead with the answer or next action: command, path, or snippet first.
2. Number multi-step work; one bounded action per step.
3. End with one next action doable in under two minutes.
4. Finish the current issue before raising a new one.
5. Restate progress each turn ("step 3 of 5 done").
6. Give time estimates in concrete units, never "a bit".
7. After a change, show what now works.
8. Errors: state location, cause, and fix. No drama.
9. Cap lists to 5 items.
10. Respond in English, whatever the input or code language.
11. Prefer diagrams over text or code when a diagram can carry the meaning.
12. No preamble, no recaps, no closers.

Exceptions: explain fully when asked to explain. Confirm before destructive actions. After three failed fixes, stop and name the doubtful assumption. If the request is ambiguous, ask one short question.
```

</details>


<details>
<summary><strong>Grok (<code>grok</code>)</strong></summary>

Grok loads the repository's existing plugin and skill files; no separate Grok manifest is required. Install directly from GitHub, enable the plugin, then invoke the skill. Two Grok-only steps: `--trust` (hooks and skills stay inactive without it) and `grok plugin enable` (plugins stay off until enabled).

### Install

```bash
grok plugin install ayghri/mand --trust
grok plugin enable mand
```

Start a new Grok session and type `/mand`. Grok honors `disable-model-invocation: true`, so nothing applies until you invoke the skill or turn on always-on.

### Verify

```bash
grok plugin list
grok plugin details mand
```

Confirm `mand` is listed, enabled, and shows a skill plus hooks.

### Update

```bash
grok plugin update mand
```

### Uninstall

```bash
grok plugin uninstall mand --confirm
```

Or keep it installed and turn it off: `grok plugin disable mand`.

### Always-on (optional)

Add the block to `~/.grok/AGENTS.md`, or drop it in `~/.grok/rules/mand.md` (Grok loads both at session start):

```markdown
## Output style

Answer terse and action-first. Shape every response so it can be acted on:

1. Lead with the answer or next action: command, path, or snippet first.
2. Number multi-step work; one bounded action per step.
3. End with one next action doable in under two minutes.
4. Finish the current issue before raising a new one.
5. Restate progress each turn ("step 3 of 5 done").
6. Give time estimates in concrete units, never "a bit".
7. After a change, show what now works.
8. Errors: state location, cause, and fix. No drama.
9. Cap lists to 5 items.
10. Respond in English, whatever the input or code language.
11. Prefer diagrams over text or code when a diagram can carry the meaning.
12. No preamble, no recaps, no closers.

Exceptions: explain fully when asked to explain. Confirm before destructive actions. After three failed fixes, stop and name the doubtful assumption. If the request is ambiguous, ask one short question.
```

</details>

<details>
<summary><strong>Gemini CLI</strong></summary>

Gemini CLI has no plugin marketplace, so there are two native routes: a **custom command** (opt-in, off until you invoke it) or an **extension** (always-on once installed). The command route matches this skill's default posture; pick it unless you want the rules on every session.

### Install (command, opt-in)

```bash
mkdir -p ~/.gemini/commands
curl -fsSL https://raw.githubusercontent.com/ayghri/mand/main/skills/mand/agents/gemini.toml \
  -o ~/.gemini/commands/mand.toml
```

Start a new session, type `/mand`. It stays on for that session.

### Install (extension, always-on)

```bash
gemini extensions install https://github.com/ayghri/mand
```

The extension loads `GEMINI.md`, which imports the full skill, so the rules apply from message one. `git` must be installed.

### Verify

```bash
gemini extensions list          # extension route
ls ~/.gemini/commands           # command route: mand.toml present
```

Or type `/` in a session and confirm `mand` is listed.

### Update

```bash
gemini extensions update mand    # extension route
# command route: re-run the curl above
```

### Uninstall

```bash
gemini extensions uninstall mand    # extension route
rm ~/.gemini/commands/mand.toml     # command route
```

</details>

<details>
<summary><strong>GitHub Copilot (VS Code and Copilot CLI)</strong></summary>

Copilot reads Agent Skills natively: the same `SKILL.md`, no conversion. It scans `.github/skills/`, `.claude/skills/`, and `.agents/skills/` in the project, and `~/.copilot/skills/`, `~/.claude/skills/`, and `~/.agents/skills/` globally.

### Install

```bash
npx skills add ayghri/mand -a github-copilot        # this project
npx skills add ayghri/mand -a github-copilot -g     # all projects
```

Without the CLI, copy the skill folder into any directory Copilot scans:

```bash
git clone https://github.com/ayghri/mand
mkdir -p ~/.copilot/skills
cp -R mand/skills/mand ~/.copilot/skills/
```

### Verify

Type `/` in the chat input and confirm `mand` appears. Or:

```bash
npx skills list
npx skills ls -g    # if installed globally
```

### Update

```bash
npx skills update mand
```

Or re-copy the folder after `git pull`.

### Uninstall

```bash
npx skills remove mand
```

Or delete the `mand` folder from the skills directory it landed in.

### Activation note

Copilot respects `disable-model-invocation`: nothing applies until you invoke the skill, same as Claude Code (tested in [#60](https://github.com/ayghri/mand/pull/60)).

### Always-on (optional)

Add the block below to `.github/copilot-instructions.md` in the project (Copilot reads it into every chat):

```markdown
## Output style

Answer terse and action-first. Shape every response so it can be acted on:

1. Lead with the answer or next action: command, path, or snippet first.
2. Number multi-step work; one bounded action per step.
3. End with one next action doable in under two minutes.
4. Finish the current issue before raising a new one.
5. Restate progress each turn ("step 3 of 5 done").
6. Give time estimates in concrete units, never "a bit".
7. After a change, show what now works.
8. Errors: state location, cause, and fix. No drama.
9. Cap lists to 5 items.
10. Respond in English, whatever the input or code language.
11. Prefer diagrams over text or code when a diagram can carry the meaning.
12. No preamble, no recaps, no closers.

Exceptions: explain fully when asked to explain. Confirm before destructive actions. After three failed fixes, stop and name the doubtful assumption. If the request is ambiguous, ask one short question.
```

</details>


<details>
<summary><strong>Hermes</strong></summary>

### Install

```bash
hermes skills install ayghri/mand/skills/mand
```

Type `/mand`. The skill installs into `~/.hermes/skills/` and is exposed as a slash command at the next session start.

Prefer to browse first? Add this repo as a skill source (a "tap"), then search and install:

```bash
hermes skills tap add ayghri/mand
hermes skills search mand
hermes skills install ayghri/mand/skills/mand
```

### Verify

```bash
hermes skills list
```

### Update

```bash
hermes skills update mand
```

### Uninstall

```bash
hermes skills uninstall mand
```

Or remove the tap too: `hermes skills tap remove ayghri/mand`.

### Always-on (optional)

Add to the `AGENTS.md` in your working directory (Hermes loads it per workdir), or to your persona `SOUL.md` for every session:

```markdown
## Output style

Answer terse and action-first. Shape every response so it can be acted on:

1. Lead with the answer or next action: command, path, or snippet first.
2. Number multi-step work; one bounded action per step.
3. End with one next action doable in under two minutes.
4. Finish the current issue before raising a new one.
5. Restate progress each turn ("step 3 of 5 done").
6. Give time estimates in concrete units, never "a bit".
7. After a change, show what now works.
8. Errors: state location, cause, and fix. No drama.
9. Cap lists to 5 items.
10. Respond in English, whatever the input or code language.
11. Prefer diagrams over text or code when a diagram can carry the meaning.
12. No preamble, no recaps, no closers.

Exceptions: explain fully when asked to explain. Confirm before destructive actions. After three failed fixes, stop and name the doubtful assumption. If the request is ambiguous, ask one short question.
```

</details>

<details>
<summary><strong>Kimi Code CLI</strong></summary>

### Install

Start a Kimi Code session, then:

1. Run `/plugins`.
2. Choose **Custom**.
3. Paste `https://github.com/ayghri/mand` and press `Enter`.
4. Choose **Trust and install**.

Use slash command `/skill:mand` to invoke the skill explicitly.

### Update

`/plugins` in Kimi Code session, cursor to **mand**, press `R`.

### Uninstall

`/plugins` in Kimi Code session, cursor to **mand**, press `D`.


</details>

<details>
<summary><strong>OpenCode</strong></summary>

The plugin supports OpenCode V1 **1.18.29+** and V2. It registers the skill and `/mand` command, and adds optional always-on mode. Older V1 versions need an upgrade or the plugin from the previous skill release.

### Install

For use across projects:

```bash
git clone https://github.com/ayghri/mand ~/.config/opencode/vendor/mand
mkdir -p ~/.config/opencode/plugins
cat > ~/.config/opencode/plugins/mand.js <<'EOF'
export { default } from '../vendor/mand/.opencode/plugins/mand.mjs';
EOF
```

For an existing V1 installation, keep the `plugin` entry in `opencode.json`. If switching to the loader above, remove that entry.

Start a new session and type `/mand`. The rules apply until you say `stop mand` or `normal mode`.

#### Skill and command only (without always-on)

Alternatively, from a checkout, copy the skill and command into OpenCode's global directories:

```bash
mkdir -p ~/.config/opencode/skills/mand ~/.config/opencode/commands
cp skills/mand/SKILL.md ~/.config/opencode/skills/mand/SKILL.md
cp .opencode/command/mand.md ~/.config/opencode/commands/mand.md
```

### Verify

Start OpenCode, type `/`, and confirm `mand` appears in the command list.

### Update

```bash
git -C ~/.config/opencode/vendor/mand pull
```

For the copy-based install, pull your checkout and re-copy the two files.

### Uninstall

Remove `~/.config/opencode/plugins/mand.js`. For the copy-based install, remove `~/.config/opencode/skills/mand/` and `~/.config/opencode/commands/mand.md`. For an existing V1 config-based install, remove its `plugin` entry.

### Always-on (optional)

Requires the plugin. The flag adds the complete ruleset to the system prompt on every turn:

```bash
touch ~/.config/opencode/.mand-always
```

`stop mand` or `normal mode` asks the agent to return to its normal style for the current session. Delete the flag to stop automatic injection:

```bash
rm ~/.config/opencode/.mand-always
```

If `XDG_CONFIG_HOME` is set, replace `~/.config` in these paths with that directory.

</details>

<details>
<summary><strong>Pi</strong></summary>

Pi discovers this repository as a native package: `extensions/` provides the session-persistent mode and `skills/` keeps the Agent Skills entry point available.

### Install

```bash
pi install https://github.com/ayghri/mand
```

Start a new Pi session. Toggle mand output for the current session:

```text
/mand
```

The footer shows `● MAND ON` while the mode is active. Run the command again to turn it off, or be explicit:

```text
/mand on
/mand off
stop mand
```

Like the Claude Code hook, the extension adds the ruleset to the conversation once instead of rewriting the system prompt on every request, and adds it again after compaction drops it.

The existing Agent Skills command remains available as an alias:

```text
/skill:mand
```

Start a new Pi session with the mode enabled by default:

```bash
pi --mand
```

### Verify

```bash
pi list
```

Confirm the GitHub package is listed, then type `/mand` and check that `● MAND ON` appears in the footer.

### Update

```bash
pi update https://github.com/ayghri/mand
```

Or update every unpinned Pi package with `pi update --extensions`.

### Uninstall

```bash
pi remove https://github.com/ayghri/mand
```

### Always-on (optional)

Create a flag in Pi's agent configuration directory:

```bash
touch ~/.pi/agent/.mand-always
```

The extension checks the flag at every new, resumed, forked, or reloaded session. A saved choice for the current session wins over this default, so `stop mand` keeps that session disabled.

Back to on-demand:

```bash
rm ~/.pi/agent/.mand-always
```

### Config file (optional)

Create `~/.pi/agent/mand.json` in Pi's agent configuration directory:

```json
{
  "alwaysOn": true,
  "hideStatus": true
}
```

- `alwaysOn`: start every session with the rules active — same as the `.mand-always` flag file, which still works
- `hideStatus`: keep the `● MAND ON` status-bar entry hidden; the rules and the `/mand` command still work

Read once at extension startup, so restart Pi after changing it. A saved choice for the current session wins over `alwaysOn`, so `stop mand` keeps that session disabled.

If `PI_CODING_AGENT_DIR` is set, put `.mand-always` in that directory instead. Run `/reload` or start a new session after changing the flag.

</details>


<details>
<summary><strong>Oh My Pi (OMP)</strong></summary>

### Install

```bash
omp plugin marketplace add ayghri/mand
omp plugin install --scope user mand@mand
```

Start a new OMP session and run `/mand` to toggle the mode.

### Update

```bash
omp plugin marketplace update mand
omp plugin upgrade --scope user mand@mand
```

### Uninstall

```bash
omp plugin uninstall --scope user mand@mand
omp plugin marketplace remove mand
```

</details>


<details>
<summary><strong>Qwen Code</strong></summary>

### Install

```bash
qwen extensions install ayghri/mand
```

Qwen Code supports the GitHub shorthand and installs the repository as a
native extension. The extension discovers the skill under `skills/`.

Type `/mand` to invoke the skill explicitly. Installing the extension
does not change output until the skill is invoked.

### Verify

```bash
qwen extensions list
```

Then start a new Qwen Code session and run:

```text
/skills
```

Confirm that `mand` appears in the list.

### Update

```bash
qwen extensions update mand
```

### Uninstall

```bash
qwen extensions uninstall mand
```

</details>

<details>
<summary><strong>Zed</strong></summary>

Zed's Agent reads Agent Skills natively using the same SKILL.md format without conversion. Note that Zed's older "Rules" have been replaced by Skills alongside AGENTS.md instructions.

### Install

In the Agent Panel, open the Skills manager and choose **Create skill from URL** (also in the command palette as `agent: create skill from url`), then paste:

```
https://github.com/ayghri/mand/blob/main/skills/mand/SKILL.md
```

Save it in **User** scope for every project, or **Project** scope for one. Then type `/mand` in the Agent Panel.

Prefer the filesystem? Clone the repo and drop the skill folder into your user skills directory:

```bash
git clone https://github.com/ayghri/mand
mkdir -p ~/.agents/skills
cp -R mand/skills/mand ~/.agents/skills/
```

### Verify

Open the Skills manager in the Agent Panel and confirm `mand` is listed. Or type `/` and confirm it appears.

### Update

Re-import from the same URL (overwrites), or re-copy the folder after `git pull`.

### Uninstall

Remove `mand` from the Skills manager, or delete `~/.agents/skills/mand`.

### Always-on (optional)

Add to your personal `~/.config/zed/AGENTS.md`:

```markdown
## Output style

Answer terse and action-first. Shape every response so it can be acted on:

1. Lead with the answer or next action: command, path, or snippet first.
2. Number multi-step work; one bounded action per step.
3. End with one next action doable in under two minutes.
4. Finish the current issue before raising a new one.
5. Restate progress each turn ("step 3 of 5 done").
6. Give time estimates in concrete units, never "a bit".
7. After a change, show what now works.
8. Errors: state location, cause, and fix. No drama.
9. Cap lists to 5 items.
10. Respond in English, whatever the input or code language.
11. Prefer diagrams over text or code when a diagram can carry the meaning.
12. No preamble, no recaps, no closers.

Exceptions: explain fully when asked to explain. Confirm before destructive actions. After three failed fixes, stop and name the doubtful assumption. If the request is ambiguous, ask one short question.
```

</details>

<details>
<summary><strong>Cursor, Amp, and any other agent-skills harness</strong></summary>

Works with any harness that reads agent skills. Swap `-a <agent>` for yours.

### Install

```bash
npx skills add ayghri/mand                  # this workspace
npx skills add ayghri/mand -g               # all projects
npx skills add ayghri/mand -a cursor -y     # one agent only
npx skills add ayghri/mand -a opencode -y
```

New agent chat, type `/mand`.

Without the CLI, copy the skill folder into whatever path your agent scans:

```bash
git clone https://github.com/ayghri/mand
mkdir -p ~/.cursor/skills     # Cursor. Use .agents/skills for OpenCode, or your agent's own path
cp -R mand/skills/mand ~/.cursor/skills/
```

### Verify

```bash
npx skills list
npx skills ls -g    # if installed globally
```

### Update

```bash
npx skills update mand
npx skills update -g    # if installed globally
```

### Uninstall

```bash
npx skills remove mand
npx skills remove mand -g    # if installed globally
```

### Always-on (optional)

Paste this into your agent's persistent rules file. Cursor: **Settings → Rules → User Rules**, or a project rule under `.cursor/rules/` with `alwaysApply: true`. OpenCode: `~/.config/opencode/AGENTS.md`.

```markdown
## Output style

Answer terse and action-first. Shape every response so it can be acted on:

1. Lead with the answer or next action: command, path, or snippet first.
2. Number multi-step work; one bounded action per step.
3. End with one next action doable in under two minutes.
4. Finish the current issue before raising a new one.
5. Restate progress each turn ("step 3 of 5 done").
6. Give time estimates in concrete units, never "a bit".
7. After a change, show what now works.
8. Errors: state location, cause, and fix. No drama.
9. Cap lists to 5 items.
10. Respond in English, whatever the input or code language.
11. Prefer diagrams over text or code when a diagram can carry the meaning.
12. No preamble, no recaps, no closers.

Exceptions: explain fully when asked to explain. Confirm before destructive actions. After three failed fixes, stop and name the doubtful assumption. If the request is ambiguous, ask one short question.
```
</details>


## How activation works

1. **Installed, not invoked.** In Claude Code, Qwen Code, Codex, and Grok, nothing happens until you invoke the skill explicitly. Claude Code, Qwen Code, and Grok honor `disable-model-invocation: true` in `SKILL.md`; Codex honors `policy.allow_implicit_invocation: false` in `agents/openai.yaml`. Other harnesses may load every skill's description at startup and activate the skill themselves.
2. **You invoke it explicitly.** Type `/mand` in Claude Code, Qwen Code, or Grok, or `$mand` in Codex. Rules stay on for that session. "stop mand" or "normal mode" turns them off.
3. **You touch `~/.claude/.mand-always`** (Claude Code). A `SessionStart` hook loads the full ruleset from message one, every session.
4. **You add the always-on snippet above** (Grok, Codex, and other harnesses). Grok reads `~/.grok/AGENTS.md` and `~/.grok/rules/*.md`. Keeps the core rules in your agent's persistent context.

In Claude Code, Qwen Code, Codex, and Grok, no middle ground: if you did not turn it on, it is off.

## Troubleshooting

**`/mand` not in autocomplete.** Restart the agent. The plugin index is read at startup. On Grok, also run `grok plugin enable mand` and confirm the install used `--trust`.

**Always-on flag has no effect.** Update the plugin (`claude plugin marketplace update mand`, then `claude plugin update mand@mand`) and restart. Hooks are read at startup, and the flag needs the plugin version that ships `hooks/hooks.json`. Grok does not read `~/.claude/.mand-always`; put the always-on block in `~/.grok/AGENTS.md` or `~/.grok/rules/mand.md`.

**`claude plugin marketplace add` fails.** Use the `owner/repo` form. A local path must point at the repo root, not `.claude-plugin/`.

**`grok plugin install` does nothing visible.** Add `--trust`, then run `grok plugin enable mand`, then start a new session. Grok plugins stay off and untrusted until those two steps.

**Installed but replies still preamble.** Open a new session. If it still drifts, tighten the wording in `skills/mand/SKILL.md`.

**Want different rules.** Fork, edit `skills/mand/SKILL.md`, then swap your copy in:

```bash
claude plugin uninstall mand            # drop the upstream copy first:
claude plugin marketplace remove mand   # fork and upstream share both names
claude plugin marketplace add <your-username>/mand
claude plugin install mand@mand
```

Restart, then re-invoke `/mand`.

**Skill missing after `npx skills add`.** Start a new agent chat. Skills are indexed at session start. Confirm the folder landed where your agent scans (`~/.cursor/skills/` for Cursor, `.agents/skills/` for OpenCode) and that the frontmatter `name` matches the folder name.
