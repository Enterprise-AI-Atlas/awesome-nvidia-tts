# Contributing

Contributions are welcome. Please read this guide before opening a pull request.

## What belongs in this list

This registry is for resources that help developers, architects, and agents build text-to-speech applications with NVIDIA technology. Acceptable entries include:

- Official NVIDIA TTS products, models, and microservices (TTS NIM, Riva TTS, NeMo TTS, Riva Studio).
- Official and community SDKs, clients, and integrations for NVIDIA TTS.
- Reference implementations, tutorials, and voice-agent examples using NVIDIA TTS.
- Adjacent digital-human technologies (ACE, Audio2Face) when the entry explicitly relates to TTS-driven animation.

## What does **not** belong

- Generic TTS services with no NVIDIA-specific integration.
- Closed-source or paywalled-only tools with no public documentation.
- Duplicate entries.

## Quality bar

Every submission must be:

1. **Publicly accessible** — open source or publicly documented.
2. **Actively maintained** — last meaningful commit or release within the last 12 months (exceptions for official NVIDIA reference repos).
3. **Documented** — a real README with setup or install instructions.
4. **Correctly categorized** — placed under the TTS topic it primarily targets.
5. **Honestly labeled** — use the `Official` or `Community` badge.

## Entry format

Use this pattern:

```markdown
- **[Name](URL)** `Official` — One-sentence description.
  - Install: `command here`
```

If there is no install command, omit the install line.

## Sections

The README is organized by **TTS topic**, not by resource type. New sections are allowed only if they contain at least three entries.

## Pull request process

1. Fork the repository.
2. Add your entry in the correct topic section.
3. Run `./scripts/validate-links.sh` and fix any broken links or anchors.
4. Open a pull request with a clear description of the resource and why it fits.

One resource per pull request is preferred.
