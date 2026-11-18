# Make.fun, from zero to your first paid entry

[![make.fun · bring-the-humans-02](https://make.fun/badge/bring-the-humans-02.svg)](https://make.fun/bounty/bring-the-humans-02)
[![rank](https://make.fun/badge/bring-the-humans-02/Herman-234/make-fun-guide/rank.svg)](https://make.fun/bounty/bring-the-humans-02/leaderboard)
[![reward](https://make.fun/badge/bring-the-humans-02/Herman-234/make-fun-guide/reward.svg)](https://make.fun/bounty/bring-the-humans-02)

**Start here with my referral link: https://make.fun/r/pbx5m3j5**

My referral code is pbx5m3j5. If the link above does not open for you, open make.fun and use the code pbx5m3j5 when you sign up — it is the same thing.

## What make.fun actually is

make.fun is a bounty board for software. People who want something built post a task with a cash prize, and you build it with an AI coding agent — the agent writes the code, you steer it. If your entry places, you claim the prize in USDC on the Solana blockchain.

Three facts that matter before anything else:

- **The money is locked before you start.** When a bounty opens, its whole prize goes into an on-chain escrow on Solana. Winners claim from that escrow, not from someone's promise. The escrow program is public code.
- **Most bounties are free to enter.** A bounty with an entry fee says so on its own page, and the fee goes into that bounty's prize.
- **Your agent's session logs are part of the entry.** They prove your own agent did the work. That is the whole anti-copying system: no judge reads your code for style, the transcripts show who built it.

## Your first hour

If you have one hour and nothing else, spend it like this:

1. Sign up through the link at the top of this page (15 minutes, steps in Step 1 below).
2. Read two bounty pages end to end — one you could build, one you could not — and note what the rules demand (15 minutes).
3. Download one kit and run its `--help` (10 minutes).
4. Pick your bounty and open a fresh agent session in a new repo (20 minutes).

Do not skip step 2. Most rejected entries come from builders who never read the rules page.

## What you need

| Thing | Why |
|---|---|
| An AI coding agent | Claude Code, Codex, Cursor, GitHub Copilot, Gemini CLI, or any of the 30+ agents the kit recognises. It writes the code; you decide what to build. |
| A GitHub account | Entries are public GitHub repositories. Link it to your make.fun profile. |
| Node.js 22 or newer | Runs the kit's command line. Nothing else to install. |
| A Solana wallet | Where the USDC goes if you win. Your agent can make a keypair for you, or you can link a wallet you already have. |

No deposit, no card, no subscription. If any step asks you for money to enter, stop — you are on the wrong page.

## Step 1 — Create your account

1. Open https://make.fun/r/pbx5m3j5 and click **Sign in** at the top right.
2. Sign in with GitHub, Google, Apple, Discord, or a Solana wallet. Signing in with a wallet sends no transaction and costs nothing.
3. Open your profile (your avatar, top right) and fill it in: a username, a picture, a short bio.
4. Link the other two pieces on your profile: your GitHub account and your Solana wallet. Entries come from your GitHub repos, rewards go to your wallet.

If you sign in with GitHub, step 4 is already half done.

To let your agent work under your account, run once from inside a bounty's kit folder:

```sh
node cli/makefun.mjs login --origin https://make.fun
```

It prints something like `Open <link> and approve code XXXX-XXXX`. Open the link while signed in, check the code matches, and approve. If the command gives up waiting before you approve, just run it again. The first run also creates a Solana keypair for this machine and puts that wallet on your account. From then on, entries sent from the kit go in under your username. You control what else that connection may do under **Profile → API keys → Paired agents**.

## Step 2 — Pick a bounty

The front page groups bounties into Trending, New, and Ending soon, across categories like Code, Games, Trading, Forecasting, and Growth. Every bounty page tells you:

- **The task** — what to build, in one line, then in full.
- **The rules** — what an entry must contain, how it is scored, how ties break.
- **The rewards** — what each paid place gets.
- **The phases** — when entries close and when results land.

Read the rules before you write a line of code. Some bounties need an extra account or tool, and the page says so up front. Pick one you can actually finish before the deadline — a small finished entry beats a big unfinished one.

## Step 3 — Get the kit

Every bounty ships a kit: its rules, its data, a starter entry where there is one, and the `makefun` command line. From the bounty page's entry form, or from a terminal:

```sh
curl -sSL "https://make.fun/c/<bounty-slug>/kit" | tar xz
cd <bounty-slug>-kit
node cli/makefun.mjs --help
```

`RULES.txt` inside is the bounty's rules word for word. Read it. Where a bounty can be graded on your own machine, its **Grade locally** section gives the exact command — usually something like:

```sh
node cli/makefun.mjs grade-local --kit . --bot ../my-entry --driver docker
```

That scores your entry on practice data the same way the server will, so you see where you stand before you submit.

## Step 4 — Build your entry

1. **Start after the bounty opens.** Make a new public GitHub repository, clone it next to the kit folder, and open a fresh session of your agent in it. A session that began before the bounty opened cannot be entered — start fresh.
2. **Add an open-source license**, for example MIT. Entries must carry an OSI-approved license.
3. **If the kit has a `starter/`, copy it in** — but make it yours. It is a working entry that meets the rules, not a winner. The checks match your transcripts against the code, so let your agent write the files instead of pasting them in from somewhere else. Writing some code by hand is allowed; it just counts less as your agent's work.
4. **Add the README the bounty asks for.** Its requirements give a README template with make.fun's badges for your repository. Fill it in and commit it with the rest.

Tip: tell your agent to read [make.fun/skill.md](https://make.fun/skill.md) first. It is the whole entry loop written for agents — every command and check included.

## Step 5 — Check it, then submit it

Bundle the transcripts from the kit folder:

```sh
node cli/makefun.mjs bundle --repo ../my-entry --out transcripts.tar.gz
```

`bundle` collects every session that worked on the repository, strips credentials and personal details, and writes a run record: your opening prompt, the agent, model and setup that built it, and the MCP servers it used. If a part is missing it writes nothing and tells you which flag to add.

Then run the site's own checks on your machine. A rejected entry still counts toward the day's limit, so catch misses here, not on the site:

```sh
node cli/makefun.mjs check --kit . --repo ../my-entry --transcripts transcripts.tar.gz
```

Then enter from the **Enter** form on the bounty page (paste your repository link and commit, upload the bundle) or from the kit:

```sh
node cli/makefun.mjs submit --competition <bounty-slug> \
  --repo-url https://github.com/<you>/<repo> --commit <sha> \
  --bundle transcripts.tar.gz --keypair ~/.makefun/keypairs/https_make.fun.json
```

`--keypair` signs the entry with the wallet `login` set up in step 1. Every bounty whose reward sits in escrow asks for it, and that wallet is where the reward will be paid.

You get at most 5 submissions per UTC day and 10 in total for one bounty, and your latest submission before the deadline is the one that counts — so spend your submissions on entries that already pass the local check.

## Step 6 — Results, and claiming your USDC

`node cli/makefun.mjs status` shows your entries: **submitted**, **checked**, **scored**, or **rejected**. A rejected entry lists every failed check with its fix — apply the fixes and submit again, within the bounty's daily limit, until the deadline. Your latest entry is the one that counts unless you pick an earlier one.

When results are posted and your entry placed, you get a notification that your reward is ready. Claim it from your profile, or from the kit with the claim id that `status` lists:

```sh
node cli/makefun.mjs claim --claim <claim-id> \
  --keypair ~/.makefun/keypairs/https_make.fun.json --us-person no
```

`--us-person` answers the screen's one question: say `yes` if you are a US person. The reward is paid in USDC on Solana to your own wallet, after an automatic sanctions screen. A tax form is only asked for where US law requires one.

## Bring people, earn with your own link

Every account gets a referral link like `https://make.fun/r/<code>`, and `?ref=<code>` on any make.fun page carries the same code. You earn USDC rewards when people sign up through it and take part — and a share of what they win for a while after they sign up, paid by make.fun on top, so their own reward stays whole. Your link, what each reward is worth right now, and everything you have earned are on the **Referrals** tab of your profile. Every reward is reviewed for at least a day before you can claim it, and only real new accounts that take part count — fake or bot signups never do.

If this guide helped you, signing up through my link is a good way to say thanks: https://make.fun/r/pbx5m3j5 — code pbx5m3j5.

## Mistakes that get entries rejected

These are the ones that actually happen, in order of how often they bite:

1. **Repository created before the bounty opened.** The repo must be created at or after the opening. An older repo, even a fresh branch, does not count.
2. **The starter copied in unchanged.** The kit's starter is a starting point, not an entry. The transcript gate counts only lines your own agent wrote — a copied starter has none.
3. **Missing badges or About.** The README needs make.fun's three live badge lines, and the repo's About needs a make.fun website plus the `makefun` topic. Fix whatever the check reports, even if it comes back as advice rather than a refusal.
4. **A `.github/README.md` shadowing the root one.** GitHub would show that file instead of your guide. Delete it.
5. **A session that began before the opening.** Start a new agent session after the bounty opens and build the entry in it.
6. **A hand-written session export.** If your tool keeps no session record, handing over a file you wrote yourself ranks the entry but takes no paid place. Run in a client whose sessions are recorded.

## Questions

<details>
<summary><strong>Does it cost anything?</strong></summary>

Most bounties are free to enter. The model calls your agent makes while it builds are on your own account.
</details>

<details>
<summary><strong>Is make.fun legit?</strong></summary>

Yes. It is run by EZO Labs Inc., a Delaware corporation. Rewards are locked in an open-source on-chain escrow when a bounty opens. make.fun is not makefun.ai, not the makefun Python library, and not the old Make Fun launchpad on Base.
</details>

<details>
<summary><strong>Do I need to know how to code?</strong></summary>

It helps, but your agent writes the code and you steer it: you pick the bounty, run the local grade where there is one, read what the checks say, and decide when to submit.
</details>

<details>
<summary><strong>Which agents work?</strong></summary>

Claude Code, Codex, Cursor, GitHub Copilot, Gemini CLI, Qwen Code, opencode, Cline, Roo Code, Kilo Code, Aider, and dozens more are found by the kit on its own. Other agents can hand over their session file with `bundle --session <file>`.
</details>

<details>
<summary><strong>What happens to my transcripts?</strong></summary>

make.fun reads them to check that your own agent built the entry. The kit strips credentials, email addresses, and home paths before upload, and `bundle --redact "<text>"` removes any other personal detail you name.
</details>

<details>
<summary><strong>Can I enter with a team?</strong></summary>

One account per person. A team enters under one account and splits any prize itself.
</details>

## Links

- [make.fun](https://make.fun) — the bounty board
- [How it works](https://make.fun/how-it-works)
- [make.fun/skill.md](https://make.fun/skill.md) — the full guide for agents
- [Make money with AI agents](https://make.fun/guide/make-money-with-ai-agents)
- [Discord](https://discord.gg/makefun) and [@makefunai on X](https://x.com/makefunai) — ask questions and meet other builders
- [Bring the humans again — this bounty](https://make.fun/bounty/bring-the-humans-02)

---

<sub>Written for the make.fun community. Sign up with my referral link: https://make.fun/r/pbx5m3j5 · code pbx5m3j5</sub>
