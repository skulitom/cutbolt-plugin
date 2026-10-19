# Cutbolt for Claude Code

Edit recorded footage with Claude: cut talking heads and interviews, add captions from a transcript, adjust loudness,
and export finished videos, as saved, reversible edits on your own machine. Cutbolt is a local video editing engine
for AI agents; this plugin gives Claude its MCP tools and six workflow skills (captions, talking-head recuts,
multi-camera interviews, screen tutorials, delivery and review, and the general `cutbolt` skill).

This repository holds the Claude Code plugin and its eval cases in `evals/`. Cutbolt itself, its source and its docs
are at [skulitom/Cutbolt](https://github.com/skulitom/Cutbolt).

## Install

1. Install the `cutbolt` engine and put it on your PATH. The skills follow Cutbolt's main branch, so the matching
   engine is `cargo install --git https://github.com/skulitom/Cutbolt --locked` (needs a Rust toolchain). A prebuilt
   archive from [Cutbolt's latest release](https://github.com/skulitom/Cutbolt/releases/latest) is quicker; check it
   against `SHA256SUMS`. It can be older than the skills.
2. Put FFmpeg and ffprobe on your PATH. Cutbolt bundles neither.
3. In a terminal:

   ```
   claude plugin install cutbolt --marketplace skulitom/cutbolt-plugin
   ```

   Or inside Claude Code: `/plugin marketplace add skulitom/cutbolt-plugin`, then `/plugin install cutbolt@cutbolt-local`.

4. Restart Claude Code in the folder that holds your footage. `cutbolt doctor` checks the setup.

If you already added the `cutbolt-local` marketplace from skulitom/Cutbolt, keep using it, or remove it first
(`claude plugin marketplace remove cutbolt-local`): both marketplaces have that name and hold the same plugin.

Then ask in your own words, for example: "Put captions on talks/demo.mp4 from talks/demo.transcript.json and save a
captioned MP4 next to the original."

## What it runs, writes and sends

- **What it runs:** the plugin starts `cutbolt --workspace <the folder you opened in Claude Code> mcp` from your PATH.
  Cutbolt runs FFmpeg and ffprobe for media work.
- **What it reads and writes:** files in that folder. It saves edits as revisions, writes outputs under new names and
  never overwrites your originals. Files outside the folder need an input root you choose.
- **What it sends:** the plugin sends nothing itself. Cutbolt runs on your machine and needs no account or hosted
  service.
- **What it may fetch:** the plugin downloads nothing. If `cutbolt` isn't installed, the skills tell Claude to offer,
  with your agreement, to install it as in step 1: build it with `cargo install --git
  https://github.com/skulitom/Cutbolt --locked`, or download the release archive from GitHub and check it against
  `SHA256SUMS`.
- **Eval cases:** `evals/` holds test cases with mocked replies for `claude plugin eval`. Claude Code never loads them
  when you use the plugin.

If no `cutbolt_*` tools appear, `cutbolt` isn't on your PATH. Install it as in step 1 and restart Claude Code.

## Licence

MIT. See [LICENSE](LICENSE). Report a security problem privately, as [SECURITY.md](SECURITY.md) says.
