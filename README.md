# Awesome NVIDIA TTS

[![Awesome](https://awesome.re/badge.svg)](https://awesome.re)
[![License: CC0-1.0](https://img.shields.io/badge/License-CC0_1.0-lightgrey.svg)](http://creativecommons.org/publicdomain/zero/1.0/)
[![PRs Welcome](https://img.shields.io/badge/PRs-welcome-brightgreen.svg)](./CONTRIBUTING.md)

A curated registry of tools, models, microservices, and integrations for **text-to-speech (TTS) with NVIDIA technology**. Covers cloud APIs, self-hosted NIMs, embedded Jetson deployments, voice cloning, and agent-facing MCP integrations.

---

## Contents

- [Core NVIDIA TTS Products](#core-nvidia-tts-products)
- [TTS NIM Microservice](#tts-nim-microservice)
- [NVIDIA Riva TTS](#nvidia-riva-tts)
- [Riva Studio / NeMo TTS](#riva-studio--nemo-tts)
- [Digital-Human Audio (ACE / Audio2Face)](#digital-human-audio-ace--audio2face)
- [Deployment Targets](#deployment-targets)
- [Voice Capabilities](#voice-capabilities)
- [SDKs, Clients & Integrations](#sdks-clients--integrations)
- [Community Tools & Examples](#community-tools--examples)
- [Learning Resources](#learning-resources)
- [Contributing](#contributing)
- [License](#license)

---

## Core NVIDIA TTS Products

| Product | Best For | Deployment |
|---|---|---|
| **NVIDIA TTS NIM** | Production self-hosted TTS microservice | Cloud / data center / workstation GPUs |
| **NVIDIA Riva TTS** | Full speech-AI stack (ASR + TTS + NMT) | Self-hosted Docker or Jetson |
| **Riva Studio / NeMo TTS** | Custom voice training and fine-tuning | Cloud training, on-prem GPUs |
| **NVIDIA ACE / Audio2Face** | Digital-human facial animation driven by TTS audio | RTX workstations, cloud |

---

## TTS NIM Microservice

The [NVIDIA TTS NIM](https://docs.nvidia.com/nim/speech/latest/tts/index.html) packages pre-trained NeMo models into an optimized, self-contained inference container.

### Available models

| Model | Languages | Modes | Key Capability |
|---|---|---|---|
| **Magpie TTS Multilingual** | English, Spanish, French, German, Mandarin, Vietnamese, Italian, Hindi, Japanese | Streaming + Offline | Multi-voice, multi-language synthesis |
| **Magpie TTS Zeroshot** | English | Streaming + Offline | Voice cloning from 3–10s reference audio |
| **Magpie TTS Flow** | English | Offline | Voice cloning with audio prompt + transcript |
| **Chatterbox TTS Multilingual** | 23 languages incl. Arabic, Korean, Portuguese, Russian | Streaming + Offline | Emotion exaggeration |

### Deployment

- **[TTS NIM Documentation](https://docs.nvidia.com/nim/speech/latest/tts/index.html)** `Official`
- **[TTS NIM Tutorial](https://docs.nvidia.com/nim/speech/latest/tts/tutorial.html)** `Official`
- **[NGC TTS NIM Container](https://catalog.ngc.nvidia.com/orgs/nim/teams/nvidia/collections/text_to_speech)** `Official`
- **Quick run** (requires NGC login / NVAIE entitlement):
  ```bash
  docker run --gpus all --runtime=nvidia -it \
    -e NVIDIA_API_KEY=$NVIDIA_API_KEY \
    -p 50051:50051 \
    nvcr.io/nim/nvidia/tts:latest
  ```

---

## NVIDIA Riva TTS

Riva is NVIDIA's speech-AI SDK. The TTS skill supports high-quality, low-latency synthesis with gRPC and Python clients.

- **[NVIDIA Riva](https://www.nvidia.com/en-us/ai/riva/)** `Official` — Speech AI SDK with ASR, TTS, and NMT.
- **[Riva TTS Quick Start](https://docs.nvidia.com/deeplearning/riva/user-guide/docs/quick-start-guide/tts.html)** `Official`
- **[Riva Skills on Embedded](https://docs.nvidia.com/deeplearning/riva/user-guide/docs/quick-start-guide.html)** `Official` — Jetson deployment guide.
- **[Riva Python Client](https://github.com/nvidia-riva/python-clients)** `Official`
- **List voices & synthesize**:
  ```bash
  python3 /opt/riva/examples/talk.py --list-voices
  python3 /opt/riva/examples/talk.py \
    --text "Hello from NVIDIA Riva" \
    --voice Magpie-Multilingual.EN-US.Mia \
    --language-code en-US \
    --output /opt/riva/wav/output.wav
  ```

---

## Riva Studio / NeMo TTS

For custom voices and fine-tuned models.

- **[NVIDIA Riva Studio](https://www.nvidia.com/en-us/gpu-cloud/riva-studio/)** `Official` — No-code voice customization, recording, training, and deployment.
- **[NVIDIA NeMo](https://github.com/NVIDIA/NeMo)** `Official` — End-to-end framework for building and customizing speech and language models.
- **[NeMo TTS Models](https://docs.nvidia.com/nemo-framework/user-guide/latest/nemotoolkit/tts/intro.html)** `Official` — Tacotron2, FastPitch, RadTTS, Mixer-TTS, and more.
- **[NeMo Curator](https://github.com/NVIDIA/NeMo-Curator)** `Official` — Data-curation tools for training custom TTS datasets.

---

## Digital-Human Audio (ACE / Audio2Face)

While not pure TTS, these products consume TTS output to animate digital humans.

- **[NVIDIA ACE](https://www.nvidia.com/en-us/ai/ace/)** `Official` — Avatar Cloud Engine combining Riva ASR/TTS, NeMo LLMs, and Audio2Face animation.
- **[NVIDIA Audio2Face](https://www.nvidia.com/en-us/omniverse/audio2face/)** `Official` — Generate real-time 3D facial animation from audio.
- **[Audio2Face NIM](https://build.nvidia.com/nvidia/audio2face-3d)** `Official` — Self-hosted microservice for facial animation on RTX.
- **[NVIDIA voice-agent-examples](https://github.com/NVIDIA/voice-agent-examples)** `Official` — Reference voice-agent pipelines using Riva/NeMo TTS, ASR, and LLMs.

---

## Deployment Targets

| Target | Product | Notes |
|---|---|---|
| **Cloud / data center** | TTS NIM, Riva Server | Requires NVAIE for production; Docker/Helm on Kubernetes |
| **Workstation / RTX PC** | TTS NIM, Riva, Audio2Face | Local inference for dev/test and digital humans |
| **Embedded / Jetson** | Riva TTS (arm64 quickstart) | Optimized models for Jetson Orin / Nano |
| **Hosted API** | build.nvidia.com NIM endpoints | Prototyping and low-volume inference; rate-limited |

---

## Voice Capabilities

- **Multilingual synthesis** — 23+ languages across Magpie and Chatterbox models.
- **Voice cloning / Zeroshot** — Clone a voice from a few seconds of reference audio.
- **Emotional styles** — Select emotions such as Happy, Calm, Excited via voice naming (e.g. `Magpie-Multilingual.EN-US.Aria.Happy`).
- **SSML support** — Control phoneme pronunciation and prosody.
- **Streaming & offline** — Low-latency streaming for agents; offline for batch content.
- **Custom pronunciation dictionaries** — IPA-based word-to-phoneme mappings.

---

## SDKs, Clients & Integrations

- **[Riva Python Client](https://github.com/nvidia-riva/python-clients)** `Official` — Official Python gRPC client for Riva TTS.
- **[Riva C++ / gRPC API](https://docs.nvidia.com/deeplearning/riva/user-guide/docs/protoc-docs/reference/protoc.html)** `Official` — Low-level gRPC definitions.
- **[LiveKit NVIDIA Riva TTS plugin](https://docs.livekit.io/agents/models/tts/nvidia/)** `Community` — Use Riva TTS in LiveKit voice agents.
  - Install: `uv add "livekit-agents[nvidia]~=1.5"`
- **[NVIDIA Pipecat voice-agent-examples](https://github.com/NVIDIA/voice-agent-examples)** `Official` — Voice-agent examples using Pipecat with NemotronASR / NemotronTTS services.
- **[OpenAI-compatible NIM endpoints](https://docs.nvidia.com/nim/speech/latest/tts/index.html)** `Official` — TTS NIM exposes standard HTTP/gRPC APIs.

---

## Community Tools & Examples

- **[LLMAvatarTalk-An-Interactive-AI-Assistant](https://github.com/wsxqaza12/LLMAvatarTalk-An-Interactive-AI-Assistant) `Community` — Tutorial project combining Riva ASR/TTS, NIM LLM, Audio2Face, and Unreal Engine MetaHuman.
- **[livekit-plugins-nvidia](https://github.com/livekit/agents)** `Community` — LiveKit plugin for NVIDIA Riva TTS.

---

## Learning Resources

- **[NVIDIA TTS NIM Docs](https://docs.nvidia.com/nim/speech/latest/tts/index.html)** `Official`
- **[Riva TTS Docs](https://docs.nvidia.com/deeplearning/riva/user-guide/docs/tts/index.html)** `Official`
- **[NeMo TTS Docs](https://docs.nvidia.com/nemo-framework/user-guide/latest/nemotoolkit/tts/intro.html)** `Official`
- **[NVIDIA ACE / Digital Humans](https://www.nvidia.com/en-us/ai/ace/)** `Official`
- **[NVIDIA Speech AI Forum](https://forums.developer.nvidia.com/c/gaming-and-visualization-technologies/audio-video-photo/122)** `Official`

---

## Contributing

Read [CONTRIBUTING.md](./CONTRIBUTING.md) for the quality bar, entry format, and PR process.

---

## License

This list is released into the public domain under [CC0-1.0](./LICENSE).

## Want us to build this for you?

Enterprise AI Atlas is maintained by [Vibe Coding Agency](https://vibecodingagency.com). We prototype and ship agentic systems, MCP servers, and enterprise AI integrations for teams that need working software fast — without hiring a full AI engineering team.
