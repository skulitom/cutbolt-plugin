# Privacy

This plugin and the Cutbolt engine it starts run on your computer. Neither has an account, telemetry or analytics,
and neither sends your footage, transcripts or edits to the developer or to any other service.

- **What it reads:** the media, transcript and project files you ask Claude to work with, inside the folder you opened
  in Claude Code. Footage and transcripts can contain personal data, such as the people seen or heard in them.
- **What it stores:** your edits, revisions, exports and its own state (the session store, job queue, cache and
  scratch files in a `.cutbolt/` folder), in that folder on your computer, until you delete them. Ducking, loudness
  measurement and transcription briefly copy audio from your footage into your system's temporary folder and delete
  it when the operation ends; a run that is killed part-way can leave such a file behind.
- **What it sends:** nothing. What Claude itself sends to Anthropic while it works is covered by Anthropic's own
  privacy policy, not this one.
- **Optional installs:** if the `cutbolt` engine is missing, the skills may offer, with your agreement, to download it
  from Cutbolt's GitHub release or build it from its GitHub source with `cargo install`, which also downloads its
  dependencies from crates.io.

Questions: open an issue on [skulitom/cutbolt-plugin](https://github.com/skulitom/cutbolt-plugin/issues), or report a
security problem privately as [SECURITY.md](SECURITY.md) says.
