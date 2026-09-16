# AGENTS.md — voice-providers/

Developer guide and architectural rules for AI agents implementing third-party voice and telephony providers in Cloudflare Workers.

## Architecture Overview

Voice capabilities in the Cloudflare Agents SDK combine low-latency WebSocket / WebRTC audio streaming with stateful Durable Objects.

```
┌─────────────────┐       Audio (PCM / µ-law)       ┌────────────────────────┐
│  Client / Phone ├────────────────────────────────►│   Cloudflare Agent     │
│ (Browser/SIP)   │◄────────────────────────────────┤   (Durable Object)     │
└─────────────────┘       Synthesized Speech        └───────────┬────────────┘
                                                                │ Full-Duplex
                                                                │ Stream
                                                                ▼
                                                    ┌────────────────────────┐
                                                    │ Voice / Telephony API  │
                                                    │(Deepgram/Eleven/Twilio)│
                                                    └────────────────────────┘
```

## Supported Provider Categories

### 1. Speech-to-Text (STT) & Realtime Voice AI
- **Deepgram**: Ultra-low-latency transcription (Nova-2 / Nova-3) over WebSockets.
- **AssemblyAI**: Real-time streaming transcription with turn detection and audio formatting.
- **ElevenLabs**: Conversational AI agent platform, natural text-to-speech, and voice cloning.

### 2. Telephony & SIP Trunks
- **Twilio**: Bidirectional Media Streams for live phone calls connected to conversational agents.
- **Telnyx**: TeXML and Media Streaming for inbound/outbound automated phone calls.
- **Plivo**: XML-based call flow handling and WebSocket audio streams.

## Technical Rules for Agents

1. **Audio Format Negotiation**: Ensure proper sample rate and encoding negotiation (e.g. 8kHz 8-bit mulaw for PSTN telephony vs. 16kHz/24kHz linear PCM or Opus for web browsers).
2. **Buffer Management**: Do not buffer large audio payloads in worker memory; forward audio frames in chunks via streaming WebSockets.
3. **Keep-Alive & Alarms**: Use Cloudflare Durable Object alarms or periodic heartbeat frames to prevent WebSocket timeouts during silent conversation pauses.
