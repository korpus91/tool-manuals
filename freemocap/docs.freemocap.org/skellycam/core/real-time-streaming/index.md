# Real-Time Streaming | FreeMoCap

Skip to main content

# Real-Time Streaming
🤖AI-generated documentation✓ curatedAI Generated
This page was drafted by an AI assistant and may contain inaccuracies. This content has been reviewed by a human curator.About content generation types

🤖
AI Generated — Page drafted entirely by AI from codebase or prompt instructions.
(e.g., docs generated from codebase analysis)
← this page

✋→🤖
AI Transformatted — Human provided raw material; AI restructured it into a different format.
(e.g., livestream → blog post, meeting notes → docs)

✋
Human Generated — Page written entirely by a human author.
(e.g., hand-written tutorial)

More info about content generation types ↗

📡
A compact binary WebSocket protocol streams multi-camera frames to the React/Electron frontend with built-in backpressure management. The API treats a multi-camera group with the same expectations as a singular camera — a consistent frame rate delivering one image per camera per frame.

## Single-camera semantics for multi-camera systems​

A key design goal of SkellyCam's API is that a multi-camera group behaves like a single camera. Instead of managing N independent camera streams with independent frame rates and connection lifecycles, you connect to one WebSocket endpoint and receive a single stream of synchronized multi-frame payloads.

Each payload contains exactly one image per camera per frame event, captured at the same realworld timeslice, delivered at a consistent frame rate. Your application code doesn't need to correlate frames across cameras, handle drift, or manage per-camera connections. You just process each payload knowing it represents a single synchronized moment across all cameras.

## The WebSocket protocol​

SkellyCam uses a compact binary WebSocket protocol to stream frames:

- JPEG compression — Each camera's frame is JPEG-compressed (quality 80 by default) and optionally downscaled to match the client's display dimensions.

- Binary packing — All compressed frames for a single multi-frame event are packed into one binary WebSocket message, along with per-camera metadata (camera ID, resolution, timestamp).

- Backpressure management — If the client can't keep up, the server drops frames rather than buffering indefinitely. This prevents memory buildup and keeps the stream responsive.

The same WebSocket connection also carries JSON messages for logs, state updates, framerate statistics, and control commands.

For full protocol details, see the WebSocket Protocol reference. The server-side implementation lives in the websocket_server.py module.

## Frontend rendering​

The React/Electron frontend processes incoming frames through a pipeline optimized for performance (see the camera view components and server services in the UI source):

- Binary parse — The binary payload is parsed to extract per-camera JPEG blobs.

- ImageBitmap creation — Each JPEG blob is decoded into an ImageBitmap, which can be transferred to a worker thread without copying.

- OffscreenCanvas rendering — Each camera's feed is rendered on an OffscreenCanvas in a dedicated Web Worker, keeping the main thread free for UI interactions.

This architecture supports many simultaneous camera feeds without frame drops in the UI.

Work in progress

In practice, our frontend streaming still struggles to consistently hit the 30-60 FPS it SHOULD be capable of. This is an active area of improvement, and we could use help! See the Development section if you're interested in contributing to frontend performance.

## What's next​

The current implementation uses WebSocket over TCP, which works well for most use cases. Future plans include introducing additional streaming methods beyond WebSocket — including UDP and potentially memory-based approaches (such as shared memory or memory-mapped files) that could achieve higher frame rates by bypassing the network card entirely. These alternative transports would be especially useful for local, same-machine consumers that need maximum throughput. See the roadmap items above for planned transport and client improvements.

- Single-camera semantics for multi-camera systems

- The WebSocket protocol

- Frontend rendering

- What's next
