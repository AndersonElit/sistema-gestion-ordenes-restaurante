# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Purpose

Workspace for the **Sistema de Gestion de Ordenes** — a reactive Spring Boot microservice for a restaurant chain's order management, following **Hexagonal Architecture** (Ports and Adapters) using the `springboot-hexagonal-builder` plugin.

## Project Context

This system centralizes restaurant order management: receiving orders from physical tables (waiters) and digital channels (delivery platforms), dispatching kitchen tickets (comandas) in real-time, tracking order lifecycle (PENDIENTE -> EN_PREPARACION -> LISTA -> ENTREGADA -> CERRADA), and integrating with external billing systems. Multi-branch support is required from v1.0.

**Requirements documentation** (already generated):
- `docs/PRD-sistema-gestion-ordenes-restaurante.md` — Product Requirements Document with domain model, use cases, user stories, business rules, and MoSCoW prioritization
- `docs/srs/SRS-sistema-gestion-ordenes-restaurante.md` — Software Requirements Specification (IEEE 830) with 30 functional requirements across 7 modules, 17 non-functional requirements, data model, and traceability matrix

## Available Skills

Use the Skill tool to invoke these at any time:

| Skill | Purpose |
|---|---|
| `springboot-hexagonal-builder:hexagonal-architecture-builder` | Scaffold a new Spring Boot microservice |
| `springboot-hexagonal-builder:c4-architecture` | Generate C4 model diagrams (Mermaid) |
| `springboot-hexagonal-builder:nosql-schema-builder` | Design MongoDB/NoSQL collection schemas |
| `springboot-hexagonal-builder:relational-db-schema-builder` | Design relational DB schemas and ER diagrams |
| `springboot-hexagonal-builder:openapi-doc-builder` | Generate OpenAPI 3.x / Swagger specs |
| `springboot-hexagonal-builder:srs-document-builder` | Generate SRS/ERS requirements documents |
| `springboot-hexagonal-builder:java-development-best-practices` | Review/refactor Java code (SOLID, Clean Code, GoF) |

## Infrastructure

Two services are pre-configured via `.claude/settings.local.json` (gitignored):

- **MongoDB Atlas** — use MCP tools `mcp__plugin_springboot-hexagonal-builder_mongodb__*` to query/manage collections directly.
- **Supabase** — use MCP tools `mcp__plugin_springboot-hexagonal-builder_supabase__*` to run SQL migrations, deploy edge functions, manage projects.

## Hexagonal Architecture Pattern

Generated microservices are structured as:

- **Domain** — business logic only; entities, value objects, port interfaces. No framework dependencies.
- **Application** — use cases that orchestrate domain objects through port interfaces.
- **Infrastructure (adapters)** — port implementations: REST controllers (inbound), repository adapters (outbound), messaging, etc.

Stack: **Spring WebFlux + Project Reactor** (non-blocking/reactive throughout).

## Build Commands (inside a generated project)

```bash
./mvnw clean package -DskipTests              # build
./mvnw spring-boot:run                        # run
./mvnw test                                   # all tests
./mvnw test -Dtest=MyServiceTest              # single test class
./mvnw test -Dtest=MyServiceTest#myMethod     # single method
./mvnw checkstyle:check                       # lint
```
