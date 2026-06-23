# AGENTS.md — Awesome NVIDIA TTS

## Purpose

This repository is a curated registry of NVIDIA text-to-speech resources. It is intended for both human developers and automated agents that need to discover, compare, and deploy TTS solutions.

## Scope

Cover the following topics when adding or editing content:

- NVIDIA TTS NIM microservice and available models (Magpie, Chatterbox).
- NVIDIA Riva TTS deployment, clients, and quick-start guides.
- Riva Studio / NeMo TTS for custom voice training.
- Digital-human audio pipelines (NVIDIA ACE, Audio2Face) when driven by TTS.
- SDKs and integrations (Python client, gRPC, LiveKit, Pipecat).
- Deployment targets (cloud, data center, workstation, Jetson).
- Voice capabilities (multilingual, voice cloning, SSML, emotional styles).

## Style

- Follow the same format as the other `awesome-*` repositories in this workspace.
- Label official NVIDIA resources as `Official` and third-party resources as `Community`.
- Prefer official documentation and GitHub repository links.

## Maintenance

- Run `./scripts/validate-links.sh` before finishing any edit.
- Keep model tables current as NVIDIA releases new TTS NIM models.

## Important reminders

- Do not provide legal advice.
- Verify that links point to current product names and documentation.
