# WebRTC x WebSockets (JS ↔ Django) — Peer-to-Peer Video

## Goal
Build a **peer-to-peer WebRTC video connection** where a browser-based JavaScript client connects to another peer and uses a **Django backend (Django Channels/WebSockets)** as the signaling layer.  
The signaling server is only used to exchange SDP offers/answers and ICE candidates; media flows directly between peers.

## What’s Been Done So Far
This repository is currently a **research + learning workspace**, with structured notes and resources covering the building blocks needed for the final implementation:

- **WebRTC concepts**: peer-to-peer vs client-server, STUN/TURN/ICE, SDP, signaling flow, and limitations of P2P.
- **WebSockets & Socket.IO**: notes on real-time communication models and Socket.IO usage.
- **Django Channels**: setup steps, channel layers, Redis-backed groups, and consumer patterns.
- **Asyncio basics**: concurrency primitives and task orchestration notes.
- **HTTP protocol foundations**: background on HTTP versions and real-time protocol constraints.
- **Python WebRTC (aiortc)**: notes on aiortc events and usage patterns.
- Curated **resource links** for WebRTC, WebSockets, Socket.IO, and Django Channels.

> **Status:** No runnable end-to-end WebRTC + Django signaling implementation yet. The repo is a knowledge base preparing for that build.

## Intended Architecture (Target Design)
1. **Frontend (JavaScript)**  
   - Capture media with `getUserMedia()`.
   - Create `RTCPeerConnection`.
   - Send SDP offers/answers and ICE candidates through the signaling channel.

2. **Backend (Django + Channels)**  
   - WebSocket endpoint for signaling.
   - Relay SDP + ICE between peers.
   - Optional Redis-backed channel layers for scale.

3. **NAT Traversal**  
   - STUN for public IP discovery.  
   - TURN if direct peer connectivity fails.

## Repository Structure
- `WebRTC/`  
  - Concept notes on signaling, STUN/TURN/ICE, SDP, and WebRTC workflows.  
  - `Python_aiortc/` includes notes on using `aiortc` in Python.
- `WebSockets/`  
  - Placeholder for WebSocket notes (not yet populated with readable text).
- `Socket_IO(JS)/`  
  - Socket.IO resources and conceptual notes.
- `Django_Channels/`  
  - Channel setup notes, consumer patterns, and channel layer guidance.
  - `asyncio/` includes asyncio fundamentals.
- `HTTP(Versions)/`  
  - Notes on HTTP/1.x, HTTP/2, HTTP/3, and how they relate to real-time protocols.
- `Resources.md`  
  - Central resource list for WebRTC + WebSockets.

## How to Use This Repo Right Now
Open the `.ipynb` notebooks or the `Resources.md` files to review the research and references.
There is no runnable app yet.

## Planned Next Steps (Not Implemented Yet)
- Create a Django project with Channels + WebSocket routing.
- Build a minimal JS client that:
  - Captures local video
  - Connects to the signaling WebSocket
  - Establishes a peer-to-peer connection
- Add STUN/TURN configuration.
- Build a simple UI for peer pairing and video display.

---
If you want, I can now scaffold the Django project and implement the signaling flow + basic JS client.
