# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Purpose

Workspace for the **Sistema de Gestión de Órdenes de Restaurante (SGOR)** — a reactive Spring Boot microservice built with Hexagonal Architecture (Ports and Adapters) using the `springboot-hexagonal-builder` plugin.

SGOR centralizes order management for a restaurant chain: receives orders from physical tables (waitstaff) and digital channels (customers), communicates comandas in real time to a Kitchen Display System (KDS), tracks full order lifecycle, and closes the business cycle with payment and receipt generation.

## Domain Model

Core entities and their key states:

| Entity | Key States / Notes |
|--------|-------------------|
| `Orden` | PENDIENTE → EN_PREPARACION → LISTA → ENTREGADA → CERRADA \| CANCELADA |
| `ItemOrden` | Belongs to an Orden; has quantity and optional modifications |
| `ProductoMenu` | Catalog item with name, price, category, availability flag |
| `Mesa` | Physical table with identifier, capacity, and occupancy state (LIBRE / OCUPADA) |

Order channels: **mesa física** (waitstaff-operated terminal/tablet) and **canal digital** (customer self-service app/web).

## Project Documentation

- `docs/prd/PRD-sistema-gestion-ordenes-restaurante.md` — product vision, success criteria, scope, stakeholders
- `docs/srs/SRS-sistema-gestion-ordenes-restaurante.md` — functional/non-functional requirements, use cases, data model, traceability matrix

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

Generated microservices follow this layer structure:

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
