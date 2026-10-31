# WebSocket Protocol | FreeMoCap

Skip to main content

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

# WebSocket Protocol
 What is a WebSocket?

A WebSocket is a persistent, two-way connection between a client (like a web browser) and a server. Unlike regular HTTP requests (which are one-shot: you ask, you get a response, the connection closes), a WebSocket stays open so the server can push data to the client continuously — perfect for streaming live camera frames. SkellyCam uses WebSocket for real-time video streaming and also for sending log messages and status updates.

Learn more: WebSocket (Wikipedia)

The WebSocket endpoint at /skellycam/websocket/connect carries three types of traffic:

- Binary frame payloads (server -> client) — Multi-camera JPEG frames

- JSON messages (server -> client) — Log records, framerate updates, application state

- Text messages (client -> server) — Frame acknowledgments and ping/pong

## Connection Lifecycle​

- Client opens a WebSocket connection to /skellycam/websocket/connect.

- Server accepts the connection and starts four concurrent tasks: image relay, log relay, state sender, and client message handler.

- Client begins receiving messages immediately.

- When the client disconnects (or the server shuts down), all tasks are cancelled and the connection is closed.

## Binary Frame Payload Format​

When cameras are active, the server sends binary (bytes) messages containing JPEG-compressed frames from all cameras in the active group. Each binary message is a self-contained multi-frame payload with the following structure:

```

+--------------------------------------------+

|              Payload Header (24 bytes)      |

+--------------------------------------------+

|         Frame Header Camera 0 (56 bytes)   |

+--------------------------------------------+

|         JPEG Data Camera 0 (variable)      |

+--------------------------------------------+

|         Frame Header Camera 1 (56 bytes)   |

+--------------------------------------------+

|         JPEG Data Camera 1 (variable)      |

+--------------------------------------------+

|                    ...                      |

+--------------------------------------------+

|         Frame Header Camera N (56 bytes)   |

+--------------------------------------------+

|         JPEG Data Camera N (variable)      |

+--------------------------------------------+

|              Payload Footer (24 bytes)      |

+--------------------------------------------+

```

All multi-byte integers are little-endian. Structures use aligned layout (numpy align=True), which introduces padding bytes for natural alignment.

### Payload Header (24 bytes)​

OffsetSizeTypeFieldDescription

01uint8message_typeAlways 0 (PAYLOAD_HEADER)

1-77—(padding)Alignment padding for 8-byte frame_number

88int64frame_numberMonotonically increasing frame counter

164int32number_of_camerasNumber of camera frames in this payload

20-234—(padding)Struct alignment padding

### Frame Header (56 bytes, one per camera)​

OffsetSizeTypeFieldDescription

01uint8message_typeAlways 1 (FRAME_HEADER)

1-77—(padding)Alignment padding

88int64frame_numberSame frame number as the payload header

1616asciicamera_idNull-terminated ASCII string, zero-padded to 16 bytes

324int32camera_indexInteger index of the camera

364int32image_widthWidth of the JPEG image in pixels

404int32image_heightHeight of the JPEG image in pixels

444int32color_channelsNumber of color channels (typically 3)

484int32jpeg_string_lengthLength of the following JPEG data in bytes

52-554—(padding)Struct alignment padding

Immediately following each frame header is the raw JPEG data (jpeg_string_length bytes). There is no padding between the JPEG data and the next frame header.

### Payload Footer (24 bytes)​

OffsetSizeTypeFieldDescription

01uint8message_typeAlways 2 (PAYLOAD_FOOTER)

1-77—(padding)Alignment padding

88int64frame_numberMust match the payload header's frame number

164int32number_of_camerasMust match the payload header's camera count

20-234—(padding)Struct alignment padding

The footer serves as a consistency check — parsers can verify that frame_number and number_of_cameras match the header.

### Message Type Constants​

ValueNameDescription

0PAYLOAD_HEADERStart of a multi-frame payload

1FRAME_HEADERPer-camera frame metadata (followed by JPEG data)

2PAYLOAD_FOOTEREnd of a multi-frame payload

### Parsing a Payload​

To parse a binary payload:

- Read 24 bytes -> payload header. Verify message_type == 0. Extract frame_number and number_of_cameras.

- For each camera (number_of_cameras times):

- Read 56 bytes -> frame header. Verify message_type == 1. Extract jpeg_string_length.

- Read jpeg_string_length bytes -> raw JPEG image data.

- Read 24 bytes -> payload footer. Verify message_type == 2 and that frame_number / number_of_cameras match the header.

### Implementation References​

- Python (server): skellycam/core/types/frontend_payload_bytearray.py — create_frontend_payload() builds the binary payload using numpy structured arrays. skellycam/api/websocket/websocket_message_types.py — WebsocketMessageType enum defining all JSON message type strings.

- TypeScript (client): skellycam-ui/src/services/server/server-helpers/frame-processor/binary-protocol.ts — struct definitions and field offsets. binary-frame-parser.ts — parseMultiFramePayload() parses the binary data and creates ImageBitmap objects.

### Image Processing Notes​

The server resizes each camera frame before JPEG encoding. If the client has sent displayImageSizes in a frame acknowledgment, the server resizes to match the client's display dimensions. Otherwise, images are scaled to 50% of their native resolution. JPEG encoding uses quality level 80 by default.

## JSON Messages (Server -> Client)​

All JSON messages are encoded server-side using msgspec for fast serialization. The message_type field in each message corresponds to a value in the WebsocketMessageType enum (skellycam/api/websocket/websocket_message_types.py), which serves as the single source of truth for all message type strings. The wire format is standard JSON text — the encoding library is an internal optimization that does not affect the protocol.

### Log Records​

```

{

  "message_type": "log_record",

  "levelname": "INFO",

  "levelno": 20,

  "message": "Camera group started",

  "name": "skellycam.core.camera_group",

  "filename": "camera_group.py",

  "lineno": 42,

  "funcName": "start",

  "created": 1700000000.123,

  "formatted_message": "2024-01-01 12:00:00 [INFO] Camera group started",

  "delta_t": "0.123ms"

}

```

Log records at TRACE level (level 5) and above are forwarded to the WebSocket. The frontend displays these in the log terminal panel. Log records are produced by skellylogs.

### Framerate Updates​

```

{

  "message_type": "framerate_update",

  "camera_group_id": "group-0",

  "backend_framerate": {

    "mean_frame_duration_ms": 33.3,

    "mean_frames_per_second": 30.0,

    "frame_duration_max": 40.1,

    "frame_duration_min": 28.5,

    "frame_duration_mean": 33.3,

    "frame_duration_stddev": 2.1,

    "frame_duration_median": 33.2,

    "frame_duration_coefficient_of_variation": 0.063,

    "calculation_window_size": 100,

    "framerate_source": "Server"

  },

  "frontend_framerate": {

    "mean_frame_duration_ms": 34.1,

    "mean_frames_per_second": 29.3,

    "framerate_source": "Display"

  }

}

```

Sent approximately every 250ms when cameras are active. The backend_framerate represents the true camera capture rate (computed from frame numbers and capture timestamps, accurate even when the WebSocket skips frames due to backpressure). The frontend_framerate represents the WebSocket delivery rate (what the UI actually receives).

### Application State​

```

{

  "message_type": "app_state",

  "state": {

    "camera_groups": {

      "group-0": {

        "id": "group-0",

        "camera_ids": ["0", "1"],

        "is_recording": false,

        "is_paused": false

      }

    }

  }

}

```

Sent approximately every 1 second and whenever the application state changes (e.g., recording starts/stops).

## Client -> Server Messages​

### Frame Acknowledgment​

After processing a binary frame payload, the client sends an acknowledgment:

```

{

  "frameNumber": 42,

  "displayImageSizes": {

    "group-0": {

      "0": { "width": 640, "height": 480 },

      "1": { "width": 640, "height": 480 }

    }

  }

}

```

The frameNumber field tells the server which frame has been rendered. The server uses this for backpressure management — it will not send new frames until the previous frame is acknowledged. If the frontend falls behind, the server skips frames to prevent buffer bloat.

The displayImageSizes field (optional) tells the server the current display dimensions for each camera, allowing it to resize JPEG frames to match, reducing bandwidth.

### Ping/Pong​

Sending the text "ping" will receive "pong" in response. This can be used for connection health checks.

## Backpressure Management​

The server tracks the last sent frame number and the last acknowledged frame number. If the frontend has not acknowledged the most recent frame:

- The server skips sending new frames.

- After acknowledgment arrives, the server skips one additional frame to let the frontend catch up.

- If the gap exceeds 1000 frames, a trace-level warning is logged.

This ensures the WebSocket buffer does not grow unbounded even when the frontend rendering is slower than the camera capture rate.

- Connection Lifecycle

- Binary Frame Payload Format

- Payload Header (24 bytes)

- Frame Header (56 bytes, one per camera)

- Payload Footer (24 bytes)

- Message Type Constants

- Parsing a Payload

- Implementation References

- Image Processing Notes

- JSON Messages (Server -> Client)

- Log Records

- Framerate Updates

- Application State

- Client -> Server Messages

- Frame Acknowledgment

- Ping/Pong

- Backpressure Management
