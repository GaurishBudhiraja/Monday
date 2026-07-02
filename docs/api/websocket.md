# MONDAY AI Operating System (AIOS)

# WebSocket API Specification

Version: 1.0

Status: API Specification

Owner: Backend API Team

Priority: CRITICAL

---

# 1. Purpose

The WebSocket API provides persistent, bidirectional, low-latency communication between the MONDAY frontend and backend.

Unlike the REST API, which is request-response based, the WebSocket API continuously streams mission progress, workflow execution, AI responses, provider updates, plugin events, telemetry, and system notifications.

The WebSocket connection enables the frontend to remain synchronized with the backend in real time.

---

# 2. Design Philosophy

Persistent Connection

Low Latency

Bidirectional Communication

Streaming First

Event Driven

Fault Tolerant

Observable

Reconnectable

Provider Independent

---

# 3. Connection Lifecycle

Client Connect

↓

Authentication

↓

Session Creation

↓

Subscription Registration

↓

Heartbeat

↓

Streaming Events

↓

Graceful Disconnect

↓

Session Cleanup

---

# 4. Connection Endpoint

/ws/v1

Every client maintains a persistent authenticated connection.

---

# 5. Authentication

Authentication occurs immediately after connection.

Supported methods

JWT

OAuth

Enterprise Token

Development Token

Unauthenticated clients are disconnected.

---

# 6. Event Categories

Mission Events

Workflow Events

Conversation Events

Memory Events

Provider Events

Plugin Events

Tool Events

Security Events

Learning Events

Reflection Events

Telemetry Events

Notification Events

System Events

---

# 7. Client → Server Messages

Examples include

Send User Message

Pause Mission

Resume Mission

Cancel Mission

Subscribe

Unsubscribe

Heartbeat

Ping

Update Preferences

Developer Commands

---

# 8. Server → Client Messages

Examples include

Mission Created

Mission Updated

Mission Completed

Mission Failed

Workflow Progress

Streaming Tokens

Provider Changed

Plugin Loaded

Plugin Failed

Memory Updated

Security Alert

Reflection Generated

Learning Completed

System Notification

---

# 9. Streaming Responses

Streaming supports

AI Tokens

Markdown

Code

Images

Structured JSON

Tool Results

Mission Timeline

Partial Results

Streaming is incremental.

---

# 10. Mission Streaming

Mission

↓

Planning

↓

Memory Retrieval

↓

Provider Selection

↓

Plugin Execution

↓

Tool Execution

↓

Reflection

↓

Learning

↓

Mission Completed

Each stage produces live events.

---

# 11. Subscription Model

Clients subscribe to

Mission Updates

Workflow Updates

Memory Updates

Provider Status

Plugin Status

Security Alerts

Notifications

Telemetry

Subscriptions may be modified during runtime.

---

# 12. Heartbeat

Heartbeat maintains connection health.

Client

↓

Ping

↓

Server

↓

Pong

Missed heartbeats trigger reconnection procedures.

---

# 13. Error Handling

Errors include

Authentication Failure

Permission Denied

Invalid Message

Mission Not Found

Provider Failure

Plugin Failure

Internal Error

Every error includes

Code

Message

Correlation ID

Recovery Recommendation

---

# 14. Reconnection

Reconnection supports

Automatic Retry

Session Recovery

Mission Recovery

Subscription Recovery

Streaming Recovery

Checkpoint Recovery

Users should not lose active Missions.

---

# 15. Performance

Targets

Low Latency

Minimal Overhead

Incremental Updates

Efficient Serialization

Connection Pooling

Scalable Event Distribution

---

# 16. Security

WebSocket security includes

Authentication

Authorization

TLS

Rate Limiting

Message Validation

Session Protection

Audit Logging

Every message is validated.

---

# 17. Observability

Every connection records

Connection ID

Session

Latency

Bandwidth

Dropped Messages

Reconnect Count

Subscription Count

Health Status

---

# 18. Future Expansion

Future versions may support

Binary Protocols

Collaborative Sessions

Shared Workspaces

Remote Agents

Distributed Streaming

Enterprise Event Routing

Without breaking the protocol.

---

# 19. Design Rules

Connections remain persistent.

Streaming is incremental.

Events are immutable.

Messages are authenticated.

Sessions are recoverable.

Subscriptions are dynamic.

Every event is observable.

The WebSocket API provides real-time communication between the frontend and the MONDAY backend, enabling live mission execution, streaming AI responses, continuous telemetry, and synchronized system state.
