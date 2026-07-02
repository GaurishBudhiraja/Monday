# MONDAY AI Operating System (AIOS)

# REST API Specification

Version: 1.0

Status: API Specification

Owner: Backend API Team

Priority: CRITICAL

---

# 1. Purpose

The REST API provides synchronous communication between clients and the MONDAY Backend.

It exposes secure, versioned, provider-independent endpoints that allow applications to interact with the Kernel without exposing internal implementation details.

The REST API is responsible only for communication.

Business logic belongs exclusively to the Kernel.

---

# 2. Design Principles

The REST API follows

RESTful Design

Versioned APIs

Stateless Requests

Secure by Default

Structured Responses

Provider Independence

Consistent Error Handling

Observable Requests

Idempotent Operations where applicable

---

# 3. API Versioning

Current Version

v1

Future versions

v2

v3

Versioning occurs through

/api/v1/

Breaking changes require a new API version.

---

# 4. Authentication

Supported authentication methods

JWT

OAuth2

API Keys

Enterprise SSO

Development Tokens

All authenticated requests include

Authorization: Bearer <token>

---

# 5. API Categories

Mission API

Conversation API

Memory API

Workflow API

Plugin API

Provider API

Tool API

System API

Configuration API

User API

Authentication API

Enterprise API

---

# 6. Standard Response Format

Every response follows

{
"success": true,
"timestamp": "...",
"requestId": "...",
"data": {},
"errors": [],
"metadata": {}
}

Every response includes a unique Request ID.

---

# 7. Error Format

Errors follow

{
"success": false,
"code": "...",
"message": "...",
"details": {},
"requestId": "..."
}

Errors remain machine-readable.

---

# 8. Mission Endpoints

POST

/api/v1/missions

Create Mission

GET

/api/v1/missions/{id}

Mission Status

GET

/api/v1/missions

Mission List

DELETE

/api/v1/missions/{id}

Cancel Mission

POST

/api/v1/missions/{id}/retry

Retry Mission

---

# 9. Conversation Endpoints

POST

/api/v1/chat

Create Conversation

GET

/api/v1/chat/history

Conversation History

POST

/api/v1/chat/message

Send Message

DELETE

/api/v1/chat/{id}

Delete Conversation

---

# 10. Memory Endpoints

GET

/api/v1/memory/search

POST

/api/v1/memory/store

PATCH

/api/v1/memory/update

DELETE

/api/v1/memory/delete

GET

/api/v1/memory/graph

GET

/api/v1/memory/preferences

---

# 11. Workflow Endpoints

POST

/api/v1/workflows

GET

/api/v1/workflows

GET

/api/v1/workflows/{id}

POST

/api/v1/workflows/{id}/resume

POST

/api/v1/workflows/{id}/pause

DELETE

/api/v1/workflows/{id}

---

# 12. Plugin Endpoints

GET

/api/v1/plugins

GET

/api/v1/plugins/{id}

POST

/api/v1/plugins/install

POST

/api/v1/plugins/update

DELETE

/api/v1/plugins/remove

POST

/api/v1/plugins/enable

POST

/api/v1/plugins/disable

---

# 13. Provider Endpoints

GET

/api/v1/providers

GET

/api/v1/providers/health

GET

/api/v1/providers/models

PATCH

/api/v1/providers/preferences

---

# 14. Tool Endpoints

GET

/api/v1/tools

GET

/api/v1/tools/{id}

POST

/api/v1/tools/test

GET

/api/v1/tools/health

---

# 15. Configuration Endpoints

GET

/api/v1/config

PATCH

/api/v1/config

POST

/api/v1/config/reload

GET

/api/v1/config/version

---

# 16. System Endpoints

GET

/api/v1/system/status

GET

/api/v1/system/health

GET

/api/v1/system/version

GET

/api/v1/system/metrics

GET

/api/v1/system/logs

---

# 17. Security

Every endpoint requires

Authentication

Permission Validation

Security Validation

Audit Logging

Rate Limiting

Sensitive endpoints require elevated permissions.

---

# 18. Rate Limiting

Supports

Per User

Per API Key

Per Organization

Per Endpoint

Burst Limits

Enterprise deployments may define custom policies.

---

# 19. Observability

Every request records

Request ID

User

Mission

Latency

Status Code

Endpoint

Response Time

Audit ID

---

# 20. Future Expansion

Future API versions may support

GraphQL

gRPC

Server Sent Events

AI Streaming APIs

Batch Requests

Enterprise Extensions

Without breaking existing contracts.

---

# 21. Design Rules

REST endpoints never contain business logic.

Kernel owns execution.

Responses remain structured.

Authentication is mandatory.

Versioning is explicit.

Errors are standardized.

Every request is observable.

The REST API provides a stable, secure, and extensible interface for interacting with the MONDAY AI Operating System.
