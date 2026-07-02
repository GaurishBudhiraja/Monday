# AI Implementation Rules

Every implementation must follow these rules.

---

## Architecture

Never violate documented architecture.

Kernel owns orchestration.

Plugins own capabilities.

Providers remain replaceable.

Memory remains independent.

---

## Coding

Follow Coding Standards.

Use Dependency Injection.

Use interfaces.

Avoid global state.

Never duplicate logic.

---

## Security

Never hardcode secrets.

Validate inputs.

Respect permission system.

Never bypass Security Manager.

---

## Development

Implement one phase at a time.

Do not start future phases.

Every phase must compile.

Every phase must include tests.

---

## Documentation

Update documentation if implementation changes architecture.

---

## Quality

No TODO placeholders.

No incomplete modules.

No mock implementations unless requested.

Every module should be production-ready.

---

## Git

Small commits.

Clear commit messages.

One feature per commit.

---

## Rule

If architecture and implementation conflict,

architecture wins.
