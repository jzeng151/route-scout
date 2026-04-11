# Route Scout

## What This Is

A web app for planning trips with interesting stops. Users import saved places from Google Maps (saved lists and custom maps), set an origin and destination, and the app generates routes in three modes: shortest path, optimized multi-stop with constraints, and a discovery mode that surfaces attractions from TripAdvisor and Atlas Obscura. Turn-by-turn navigation happens in-app. Built with TypeScript, strict TDD, and comprehensive test coverage (unit, integration, E2E with edge case coverage).

## Core Value

Users can plan a route between two points that intelligently incorporates their saved places and discovers new attractions along the way — something no single tool does well today.

## Requirements

### Validated

(None yet — ship to validate)

### Active

- [ ] User can import saved places from Google Maps (saved lists and custom maps)
- [ ] User can set origin location (manual input or geolocation)
- [ ] User can set destination location (manual input or search)
- [ ] User can generate shortest path route between origin and destination
- [ ] User can select saved places and generate optimized multi-stop route (with pinning constraints — certain stops can be pinned to a specific order)
- [ ] User can generate discovery route with suggested attractions from TripAdvisor and Atlas Obscura along their path
- [ ] Discovery mode can build routes around user-picked attractions AND suggest stops along an existing route
- [ ] User can navigate routes with in-app turn-by-turn navigation
- [ ] All user inputs are validated and sanitized
- [ ] Code has concise comments for human and AI readability
- [ ] Comprehensive test coverage: unit, integration, and E2E tests covering all edge cases

### Out of Scope

- Import from Apple Maps — post-MVP (multi-platform imports)
- Import from TripAdvisor — post-MVP
- AI-powered smart curation of recommendations — post-MVP
- AI-powered natural language trip planning — post-MVP
- Mobile native app — web-first
- Social features (sharing routes, collaborating) — not planned
- Offline navigation — deferred

## Context

- Born from personal trip planning frustration — existing tools don't combine saved places, route optimization, and attraction discovery
- Target users: road trippers planning multi-stop journeys AND tourists/sightseers exploring new cities
- Post-MVP vision: expand imports to Apple Maps and TripAdvisor; add AI integration for smart curation (picking best stops based on preferences/route constraints) and natural language planning (describe trip in plain English, AI builds route)
- Semantic versioning: minor versions (v0.1 → v0.2) are shippable milestones, patches (v0.1.1 → v0.1.2) are incremental feature additions
- Built with TypeScript throughout
- Robust TDD — tests before implementation
- All test types: unit, integration, E2E with full edge case coverage

## Constraints

- **Tech Stack**: TypeScript — strict typing throughout, no plain JS
- **Testing**: TDD required — tests written before implementation, all types (unit, integration, E2E), edge case coverage mandatory
- **Code Quality**: Concise comments for human and AI readability; all user inputs validated and sanitized
- **Platform**: Web app (browser-based, responsive for mobile usage)

## Key Decisions

| Decision | Rationale | Outcome |
|----------|-----------|---------|
| Web app (not native) | Broader reach, simpler deployment, no app store overhead | — Pending |
| Google Maps import (both lists + custom maps) | Covers the most common saved places format; post-MVP expands to Apple Maps and TripAdvisor | — Pending |
| AI for both curation and natural language planning | Maximizes value — AI picks best stops AND lets users describe trips conversationally | — Pending (post-MVP) |
| Semantic versioning (minor = milestone, patch = feature) | Provides clear checkpoints and deployable increments | — Pending |

## Evolution

This document evolves at phase transitions and milestone boundaries.

**After each phase transition** (via `/gsd-transition`):
1. Requirements invalidated? → Move to Out of Scope with reason
2. Requirements validated? → Move to Validated with phase reference
3. New requirements emerged? → Add to Active
4. Decisions to log? → Add to Key Decisions
5. "What This Is" still accurate? → Update if drifted

**After each milestone** (via `/gsd-complete-milestone`):
1. Full review of all sections
2. Core Value check — still the right priority?
3. Audit Out of Scope — reasons still valid?
4. Update Context with current state

---
*Last updated: 2026-04-11 after initialization*
