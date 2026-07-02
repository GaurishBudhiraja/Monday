# MONDAY AI Operating System (AIOS)

# Project Structure Specification

Version: 1.0

Status: Active

Owner: Core Architecture Team

---

# Purpose

This document defines the official repository structure of MONDAY AIOS.

The project structure is designed to maximize:

- Maintainability
- Scalability
- Modularity
- Testability
- Security
- Developer Experience
- Long-term evolution

The repository structure itself is considered part of the architecture and must remain consistent throughout the lifetime of the project.

---

# Design Philosophy

MONDAY is not organized around features.

MONDAY is organized around responsibilities.

Every directory represents a single responsibility within the architecture.

No directory should contain unrelated functionality.

The architecture follows the principle:

Single Responsibility at every level.

---

# High-Level Repository Layout

```
Monday/

├── backend/
├── frontend/
├── plugins/
├── docker/
├── scripts/
├── tests/
├── docs/
├── .github/

├── README.md
├── LICENSE
├── CHANGELOG.md
├── CONTRIBUTING.md
├── SECURITY.md

├── CLAUDE.md
├── GEMINI.md
```

---

# Backend Structure

The backend contains the complete AI Operating System.

```
backend/

src/

core/

agents/

memory/

providers/

plugins/

tools/

desktop/

browser/

voice/

vision/

api/

events/

scheduler/

config/

logging/

security/

database/

models/

services/

utils/

shared/

tests/
```

Every directory must remain independent whenever possible.

Circular dependencies are prohibited.

---

# Directory Responsibilities

## core/

Contains the operating system kernel.

Responsibilities

- Orchestrator
- Event Bus
- Dependency Injection
- Startup
- Shutdown
- Runtime
- Lifecycle
- Configuration Loader

Nothing outside core should control application lifecycle.

---

## agents/

Contains intelligent agents.

Examples

Planner Agent

Desktop Agent

Browser Agent

Research Agent

Memory Agent

Coding Agent

Voice Agent

Scheduling Agent

Coordinator Agent

Future agents

Agents never communicate directly.

All communication occurs through the Event Bus.

---

## memory/

Contains every memory implementation.

Includes

Working Memory

Semantic Memory

Episodic Memory

User Profile

Knowledge Store

Conversation History

Memory Indexing

Vector Retrieval

Memory Consolidation

Memory Synchronization

---

## providers/

Contains every AI provider.

Supported providers include

Claude

Gemini

OpenAI

Ollama

LM Studio

Future providers

Every provider must implement the same interface.

The rest of MONDAY must never know which provider is active.

---

## plugins/

Contains the Plugin SDK and built-in plugins.

Future third-party plugins are loaded here.

Plugins must never access the operating system directly.

Every request passes through the Security Broker.

---

## tools/

Contains executable tools.

Examples

Filesystem

Terminal

Browser

Clipboard

Calendar

Spotify

WhatsApp

Git

Docker

VS Code

Chrome

Firefox

Email

Weather

Maps

Translation

OCR

PDF

Image Processing

Document Processing

Tools expose capabilities.

Agents decide when to use them.

---

## desktop/

Contains desktop automation.

Responsibilities

Application management

Keyboard

Mouse

Windows

Processes

Clipboard

Notifications

Accessibility

Multi-monitor support

---

## browser/

Contains browser automation.

Responsibilities

Chrome

Edge

Firefox

Web scraping

Authentication

Downloads

Uploads

Tabs

Cookies

Session management

Automation pipelines

---

## voice/

Contains voice intelligence.

Responsibilities

Speech Recognition

Streaming

Text To Speech

Wake Word

Noise Reduction

Voice Profiles

Conversation Streaming

---

## vision/

Contains visual intelligence.

Responsibilities

OCR

Screen Understanding

Object Detection

Screenshot Analysis

UI Recognition

Image Processing

Future Computer Vision

---

## api/

Contains external interfaces.

Includes

REST API

WebSocket

IPC

Future gRPC

---

## events/

Contains event definitions.

Every subsystem communicates through events.

No subsystem directly invokes another subsystem.

Everything becomes an event.

---

## scheduler/

Responsible for

Background Jobs

Recurring Tasks

Cron Jobs

Mission Scheduling

Delayed Execution

Workflow Recovery

---

## config/

Contains

Environment

Runtime Configuration

Feature Flags

Provider Selection

Plugin Settings

Security Policies

---

## logging/

Contains

Audit Logs

Debug Logs

Performance Logs

Mission Logs

Plugin Logs

Execution Logs

---

## security/

Contains

Permission Broker

Policy Engine

Credential Vault

Encryption

Authentication

Authorization

Secrets

Sandbox

Approval Manager

Security Scanner

---

## database/

Contains database adapters.

Supported databases

SQLite

PostgreSQL

Vector Database

Future Cloud Databases

---

## models/

Contains shared domain models.

Examples

Mission

Task

Agent

Plugin

Memory

Conversation

Workflow

Provider

Tool

Event

Every module imports models from here.

---

## services/

Business services shared across modules.

Examples

Search

Embeddings

Ranking

Notifications

Downloads

Uploads

Caching

---

## shared/

Contains

Constants

Interfaces

Enums

Exceptions

Validators

Utilities

Reusable Components

---

## tests/

Backend tests only.

Includes

Unit Tests

Integration Tests

Performance Tests

Security Tests

Regression Tests

---

# Dependency Rules

Allowed

Agent → Event Bus

Agent → Memory

Agent → Provider

Agent → Tools

Tool → Security

Plugin → Event Bus

API → Core

Forbidden

Tool → Tool

Agent → Agent

Provider → Tool

UI → Database

Plugin → Database

Browser → Desktop

Everything must communicate through architecture, never shortcuts.

---

# Scalability Strategy

The project must support

Single User

Multiple Users

Remote Execution

Distributed Agents

Cloud Synchronization

Third-Party Plugins

Enterprise Deployments

Without redesigning the repository.

---

# Repository Rule

The repository structure is considered architecture.

Folders may evolve.

Responsibilities must never blur.

If a new capability does not clearly belong inside an existing directory, a new architectural proposal must be written before introducing a new top-level module.

The architecture must remain understandable even after years of continuous development.
