English · [Русский](README.md)

# You have seen the list of biases — it never tells you which one is at work in the decision in front of you

You describe the situation in plain words, the scan runs it through twenty-five marker questions,
keeps the two or three biases with the strongest markers, and hands you a procedure for each one:
who does what, and when.

```
claude plugin marketplace add https://github.com/beCyborg/jadlis-start.git
claude plugin install cognitive-biases@jadlis
```

There are no keys here and no third-party subscriptions: the only setting is the `MEMORY_DIR`
folder where the advisor keeps its profile, and even that is optional — leave it out and the
advisor says so and goes on without memory.

![The situation passes through marker questions and the biases sort into active, possible and not active](docs/img/hero-jadlis-cognitive-biases.webp)

In words: on the left, the decision described in plain language; on the right, three buckets —
active, possible, not active — and out of the top bucket come two or three biases, each with its
own procedure.

This is my workbench published as it is, not a product: whatever I stopped using, I removed.

## Before → after

| By hand | With an AI chat | With this plugin |
|---|---|---|
| **How a bias gets picked.** The whole list is open in front of you, and nearly all of it feels like it fits. | It names what gets mentioned most often: sunk cost, Dunning-Kruger, losses hurting twice as much as gains. | Twenty-five marker questions walk through your situation, and every bias comes back tagged: active, possible, not active. |
| **How solid the finding is.** A poster with a hundred biases puts all of them on the same footing. | The famous one sounds exactly as confident as the repeatedly replicated one. | Every bias sits on one of five tiers — by effect size and by whether the data replicate — and the tier is named alongside the finding. |
| **What to do once it is named.** The bias has a name, and the rest is "be more careful". | Advice of the general kind: keep it in mind while deciding. | Each priority bias comes with a procedure: the mechanism, the steps, the adjustment for your domain and stakes, and, on its own line, what the procedure will not fix. |
| **The famous explanations.** Losses, Dunning-Kruger and choice overload you have heard about and taken as law. | They come back in the original, loudest formulation. | Six of them get a file of their own: what the original claimed, what re-examination showed, and what to use instead. |
| **How many findings you walk away with.** You tick off half the list and cannot tell where to start. | The answer grows with the question. | The scan is capped at two or three biases: if everything comes back active, that counts as a failed triage, not a rich catch. |

## How it works

![The situation, twenty-five marker questions, the map of active biases, a procedure for each priority one](docs/img/how-jadlis-cognitive-biases.webp)

Going in — your situation: the domain, the stakes, whether the decision is reversible, whether
you decide alone or in a group.
Inside — twenty-five marker questions sort the biases into active, possible and not active, and
two or three with the biggest effect on this choice get priority.
Coming out — the scan map and a debiasing procedure for every priority bias.

In words: situation → twenty-five marker questions → an active / possible / not active map →
two or three priority biases → a procedure for each.

The advisor lays the material out across seven references: two for the first tier (estimation and
planning; authority and the group), two for the second (the frame of the choice; memory and
after-the-fact evaluation), and one for the third — domain-specific, covering finance, hiring,
group dynamics and problem-solving. A separate file holds the examined myths, and one more holds
ten debiasing techniques: reference-class forecasting, the pre-mortem, consider-the-opposite,
devil's advocate, the steelman, independent evaluation, prospective hindsight, anonymization,
implementation intentions, the outside evaluator. Each technique records which biases it works
against, the steps, and what it does not deliver.

Session context goes into `{MEMORY_DIR}/Профили/adv-CognitiveBiases.md`: the domain, the stakes,
the biases found and their status, the techniques applied. On the next run that file is read first
and you confirm the context still holds. Nothing is ever written outside the memory folder.

## Installing and the first run

**a) Text to paste to an agent.** Copy the whole thing into a Claude Code chat:

```
You are the installer. Install the plugin cognitive-biases from the jadlis marketplace
on this Mac. Run exactly these commands, verbatim, shortening nothing:
1. claude plugin marketplace add https://github.com/beCyborg/jadlis-start.git
2. claude plugin install cognitive-biases@jadlis
3. claude plugin list — show me the line about cognitive-biases and its version.
This plugin needs no keys, no third-party subscriptions and no external CLIs — do not go
looking for them and do not ask. The only setting is the memory folder MEMORY_DIR: ask me
for the path and use what I give you, never invent one; if I decline, install without it.
Before each command show it to me in full and wait for "yes". If I say "no", do not run it,
tell me what you skipped, and move on.
If a command returns an error, stop, show me the output, and do not move to the next one.
```

**b) Commands by hand.**

```
claude plugin marketplace add https://github.com/beCyborg/jadlis-start.git
claude plugin install cognitive-biases@jadlis
claude plugin list
```

The first command installs nothing — it adds the marketplace. Only the second one installs, and
one line removes it: `claude plugin uninstall cognitive-biases@jadlis --keep-data`.

The memory folder can be set straight in the install — `claude plugin install
cognitive-biases@jadlis --config MEMORY_DIR=~/advisors-memory` — or later through `/plugin` →
cognitive-biases → settings. Every Jadlis advisor can point at the same folder: the skeleton
unpacks idempotently and existing files are left alone. The folder is private — keep it out of
public repositories.

**c) The short command.** Open Claude Code in the folder you work in and type:

```
/cognitive-biases <the decision or situation>
```

If it is not found, check the name with `claude plugin list`. Start it without describing the
situation and there is nothing to triage against, so the answer comes out generic: give the
domain, the stakes, the reversibility, and whether you decide alone or in a group.

## Limits, cost, updating

**What it does not do.** It does not convene a council and does not merge the verdicts of several
lenses — that is `/advisor-decision`. That council does carry a lens with a similar name, but that
lens is built from five books and is different content, not this reference set. It does not go to
the web and does not check whether a fresh re-examination has come out: the numbers and citations
are baked into the reference files and age along with them. It does not cross-verify claims. It
does not write a verdict file into a council folder — only the session profile is saved. It does
not diagnose and does not replace a professional: the boundaries are spelled out in
`NOTICE.md`. And it does not decide for you — the scan says where to look for the bias,
the choice stays yours.

**What you need.** No keys. The plugin brings up no MCP servers, requires no external CLIs or
binaries, and depends on no other plugin. The only setting is the optional `MEMORY_DIR` folder on
your own disk; the default is `~/advisors-memory`.

**How tokens get spent.** A run is light: one skill inside your session, no subagents and no
parallel lenses — the heavy fan-outs live in the councils, not here. Reading the references costs
more than the rest, which is why the skill picks not all seven but the ones the navigation route
points to for your situation.

[уточнить] — the repository holds no ranked list of all 111 biases: the references cover
forty-eight named ones, and the rest exist only as a number in the plugin description.

**Verified where I work:** my Mac, my Claude Code subscription. Where else this works — [уточнить].

**Terms of use.** There is no license: all rights reserved by the author. You may read it and use it
personally. Commercial use, republishing and bundling it into your own products — by arrangement
with me.

**Updating.** With a third-party marketplace, auto-update is off on your side: until you run the
first command you keep the version you installed.

```
claude plugin marketplace update jadlis
claude plugin update cognitive-biases@jadlis
claude plugin list
```

Reinstall, if something ended up crooked:

```
claude plugin uninstall cognitive-biases@jadlis --keep-data && claude plugin install cognitive-biases@jadlis
```

This repository is generated from a private source, and a direct edit here fails the content-hash
check — if you find a problem, open an issue: the fix lands in the source and ships with the next
release.
