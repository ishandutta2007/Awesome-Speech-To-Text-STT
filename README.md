# Awesome-Speech-To-Text-STT

# Top Speech-to-Text (STT) Tools Ecosystem

**Curated List of SaaS Products & Open-Source GitHub Projects**  
*Focused on Streaming Transcription, Speaker Diarization & Word-Level Timestamps*  
**Last updated: March 2026**

This repository tracks notable **SaaS platforms** and **open-source projects** for **Speech-to-Text (STT)**. These tools convert spoken audio into written text — powering meeting transcription, voice interfaces, subtitle generation, call analytics, and accessibility features — with options ranging from managed APIs with sub-second streaming latency to local models that run entirely offline.

**Examples** include Rev AI, Google Cloud STT, Deepgram, Whisper, Speechmatics, AssemblyAI, Otter.ai, Verbit, Sonix, and Trint (the category leaders).

**Open-source emphasis**: This section is heavily expanded with every major active project for self-hosting, local inference, and transparent model weights — ideal for teams prioritizing data sovereignty, developers building offline voice features, and organizations avoiding per-minute transcription costs.

Contributions welcome! Open a PR to add/update entries. Keep descriptions factual and link to official sites.

## Table of Contents
- [SaaS/Hosted Platforms](#saas-hosted-platforms)
- [Open-Source GitHub Projects](#open-source-github-projects)
- [How to Contribute](#how-to-contribute)
- [Disclaimer](#disclaimer)

## SaaS/Hosted Platforms

- **[Deepgram](https://deepgram.com/)**  
  **Enterprise-grade STT API with the fastest streaming latency and highest accuracy in independent benchmarks.** A 2026 feature comparison found Deepgram delivered **the best combination of speed and accuracy** on real-world business audio, with the strongest entity detection and streaming response times. **Nova-3** targets noisy environments. Pricing is usage-based per minute with volume discounts. **Best for real-time voice agents and call analytics** where latency matters.

- **[AssemblyAI](https://www.assemblyai.com/)**  
  **Developer-first STT API with strong accuracy and a free tier.** Handles **speaker diarization, sentiment analysis, topic detection, and PII redaction** in a single API call. **Universal-2** model focuses on accuracy across accents and noisy conditions. Free tier includes limited monthly transcription; paid plans scale per hour. **Best for developers wanting rich audio intelligence features alongside transcription.**

- **[Rev AI](https://www.rev.com/)**  
  **High-accuracy STT API with human transcription options for the same account.** Rev AI claims **industry-leading accuracy** with the ability to escalate to human transcription when the model isn't confident enough. Supports **custom vocabulary, sentiment analysis, and topic extraction**. Usage-based pricing with volume discounts. **Best for teams needing a human-in-the-loop fallback for critical content.**

- **[Google Cloud Speech-to-Text](https://cloud.google.com/speech-to-text)**  
  **Mature, globally distributed STT service with 125+ languages.** Supports **streaming, batch, and real-time transcription** with automatic punctuation, speaker diarization, and **model adaptation** for domain-specific vocabulary. Deep integration with Google Cloud ecosystem. **Best for teams already invested in Google Cloud.**

- **[Speechmatics](https://www.speechmatics.com/)**  
  **Enterprise STT with strong accuracy across accents and dialects.** Features **real-time and batch transcription**, speaker diarization, and **custom dictionary** support. UK-based with GDPR-focused deployment options. **Best for European enterprises with data residency requirements.**

- **[Otter.ai](https://otter.ai/)**  
  **Meeting transcription and note-taking platform** rather than a raw API. Joins Zoom, Google Meet, and Teams calls automatically, produces summaries and action items, and maintains a searchable meeting archive. Free tier with limited minutes; paid plans per user. **Best for knowledge workers wanting meeting notes without API integration.**

- **[Verbit](https://verbit.ai/)**  
  **Transcription and captioning platform for legal, education, and media industries** with hybrid AI + human workflows.

- **[Sonix](https://sonix.ai/)**  
  **Automated transcription with multi-language support and editing tools.** Pay-as-you-go pricing with a free trial. **Best for podcasters and journalists** wanting transcription without a subscription.

- **[Trint](https://trint.com/)**  
  **Transcription platform designed for journalists and media organizations** with collaborative editing and story verification features.

## Open-Source GitHub Projects

- **[Whisper](https://github.com/openai/whisper)**  
  **The foundational open-source speech recognition model** — MIT licensed, 88,000+ GitHub stars. Trained on **680,000 hours of multilingual and multitask supervised data** collected from the web, approaching human-level robustness on English speech recognition. Supports **99 languages** with automatic language detection, **word-level timestamps**, and translation to English. **Approach**: large-scale weak supervision eliminates the need for significant fine-tuning for domain adaptation. **Limitations**: `openai-whisper` runs **17x slower than real-time on CPU** and doesn't handle streaming natively. **Best as the reference model** — most production open-source STT stacks build on Whisper weights via faster inference engines.

- **[faster-whisper](https://github.com/SYSTRAN/faster-whisper)**  
  **The production inference engine for Whisper** — **up to 4x faster than openai/whisper with the same accuracy** and **less memory usage** using CTranslate2. MIT licensed. Supports **CPU and GPU** with 8-bit and 16-bit quantization. **`large-v3` model reaches ~2.2x real-time on GPU** and runs on CPU with int8 quantization. **The default choice for self-hosted Whisper inference** — used by WhisperX, WhisperLiveKit, and most production deployments. Install via `pip install faster-whisper`.

- **[WhisperX](https://github.com/m-bain/whisperX)**  
  **Word-level timestamps and speaker diarization for Whisper** — BSD-2-Clause licensed, 16,000+ GitHub stars. Adds **forced alignment** for accurate word-level timestamps (essential for subtitle sync) and **speaker diarization** via pyannote-audio. Claims **70x real-time transcription on GPU**. **The standard choice for subtitle generation and meeting transcription** where "who said what when" matters. Requires Hugging Face token for diarization models.

- **[WhisperLiveKit](https://github.com/QuentinFuxa/WhisperLiveKit)**  
  **Real-time speech-to-text server with speaker diarization and turn detection** — 2,000+ GitHub stars. **Streaming with configurable latency** from 200ms (low-latency realtime) to 2000ms (high-precision batch). **simulstreaming** for fast models plus **WhisperStreaming** for higher accuracy. **Built-in speaker diarization** with Sortformer and Diarizen. **VAD-based turn detection** for knowing when someone is speaking. **WebSocket API and web interface** included. **Best for building real-time transcription servers** with speaker attribution.

- **[whisper.cpp](https://github.com/ggerganov/whisper.cpp)**  
  **High-performance C/C++ implementation of Whisper** — MIT licensed, 40,000+ GitHub stars. **Runs on CPU, Apple Silicon (Metal), CUDA, and Vulkan** with no Python or PyTorch dependency. **Quantized GGUF models** enable running Whisper on Raspberry Pi and mobile devices. **`whisper-server`** provides OpenAI-compatible API. **The foundation for on-device and embedded transcription** — used by many mobile apps and edge deployments.

- **[WhisperLive](https://github.com/collabora/WhisperLive)**  
  **Practical real-time implementation of OpenAI Whisper** from Collabora — 5,000+ GitHub stars. **WebSocket-based** with client libraries for Python and JavaScript. Supports **faster-whisper backend** and **multiple concurrent clients**. **The battle-tested choice for browser-to-server streaming transcription** — integrated into meeting tools and voice assistants.

- **[NVIDIA NeMo](https://github.com/NVIDIA/NeMo)**  
  **NVIDIA's toolkit for conversational AI including state-of-the-art STT models** — Apache 2.0 licensed. **Parakeet** and **Canary** models rank at the top of the Hugging Face Open ASR Leaderboard for accuracy and speed. **Optimized for NVIDIA GPUs** with TensorRT integration. **Best for GPU-accelerated transcription at scale** where maximum throughput matters.

- **[SpeechBrain](https://github.com/speechbrain/speechbrain)**  
  **Open-source conversational AI toolkit with speech recognition, speaker diarization, and enhancement** — Apache 2.0 licensed, 9,000+ GitHub stars. **Used in academic research and production** — integrated by the University of Groningen's CogniGron and other research institutions. **Best for researchers** wanting a unified framework for multiple speech tasks.

- **[Kaldi](https://github.com/kaldi-asr/kaldi)**  
  **The classic open-source speech recognition toolkit** — the foundation for many older systems. **Steep learning curve** but still used in research and legacy deployments. **Best for researchers** studying traditional ASR architectures.

- **[Vosk](https://github.com/alphacep/vosk-api)**  
  **Offline speech recognition toolkit with 20+ language models** — Apache 2.0 licensed. **Lightweight models** (50MB) run on Raspberry Pi, Android, and iOS without internet. **`vosk-server`** provides WebSocket API. **Best for offline, low-resource devices** where cloud connectivity isn't available.

- **[Whisper-Streaming](https://github.com/ufal/whisper_streaming)**  
  **Real-time streaming implementation of Whisper** from Charles University — Apache 2.0 licensed. **Uses LocalAgreement policy** to emit confirmed text with low latency. **Best for research on streaming Whisper architectures**.

### Additional Strong Open-Source Options

- **WhisperX Large-v3** — Combined with faster-whisper backend for highest accuracy with word-level timestamps.
- **Silero VAD** — Voice activity detection model for segmenting audio before transcription. Essential for efficient long-form processing.
- **pyannote-audio** — Speaker diarization library used by WhisperX and WhisperLiveKit.
- **wav2vec 2.0 / HuBERT / WavLM** — Self-supervised speech representation models from Meta and Microsoft. Foundation for many fine-tuned ASR systems.
- **Speech Recognition Toolkit (Sphinx)** — CMU's classic speech recognition system.

**Frameworks for building custom systems**: Combine **faster-whisper** for production inference at 4x speed with same accuracy, **WhisperX** for word-level timestamps and speaker diarization, **WhisperLiveKit** or **WhisperLive** for real-time streaming with VAD turn detection, **NVIDIA NeMo** for GPU-optimized batch transcription at scale, and **Vosk** for fully offline edge deployment — to build a complete self-hosted STT stack from real-time voice agents to offline subtitle generation.

## How to Contribute

1. Fork the repo.
2. Add/edit entries in `README.md` (follow existing format).
3. Include: name, link, 1–2 sentence description, and whether it's SaaS or open-source.
4. Submit PR with a short explanation.

Star the repo if you find it useful!

## Disclaimer

- This is a **community-curated** list — not exhaustive and not an endorsement.
- Speech-to-text tools differ significantly in latency, accuracy, language support, and deployment model. **OpenAI's `openai-whisper` runs 17x slower than real-time on CPU** — use faster-whisper or whisper.cpp for production . **faster-whisper delivers 4x speedup with the same accuracy** via CTranslate2 . **WhisperX adds word-level timestamps and diarization** essential for subtitle sync and meeting attribution . **Deepgram leads on streaming latency and accuracy** in independent business-audio comparisons, but hosted APIs require sending audio to third parties. **Speaker diarization quality varies significantly** — pyannote models require Hugging Face tokens and add processing overhead. **Word-level timestamps from forced alignment can be wrong** on overlapping speech or heavy accents .
- Self-hosted open-source solutions require proper GPU infrastructure for real-time performance, VAD configuration for long-form audio, and model selection tradeoffs between accuracy and speed.

---

**Made for developers, researchers, meeting transcription builders, and anyone building speech-to-text applications.**  
Let's make speech-to-text more open, accurate, and locally runnable.
