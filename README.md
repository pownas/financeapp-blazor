# FinanceApp Blazor – MVP (Proof of Concept)

Ett första MVP/PoC för en webbaserad ekonomiapp baserad på kravspecifikationen (2025-09-03).  
Fokus: Mobile First, enkel översikt, grund för vidareutveckling.

## Innehåll
- Blazor WebAssembly Hosted (Client, Server, Shared)
- Minimal APIs: Transaktioner, Kategorier, Summering, Auth-stub
- EF Core InMemory (lätt att byta till riktig databas)
- PWA: manifest + service worker (stub)
- Ljus/Mörk temabas (CSS design tokens)
- Grundsidor: Dashboard, Transaktioner, Kategorier, Inställningar
- Dokumentation: Arkitektur, Backlog, Design Tokens
- Förberett för: Riktig auth, bankintegration, export, AI-funktioner

## Funktioner (MVP)

| Funktion | Status | Kommentar |
|----------|--------|-----------|
| Transaktionslista | Klar | Enkel tabell + sortering via datum (server) |
| Skapa / Ta bort transaktion | Klar | POST/DELETE |
| Kategorier | Klar | CRUD |
| Summering per månad | Klar | Senaste 12 månader |
| Temaväxling (ljus/mörk) | Grund | Per session, ej persisterad |
| PWA manifest + SW | Stub | Ingen cachingstrategi ännu |
| Auth | Stub | “demo user” |
| Offline-läge | Ej | Kommer med cachingstrategi |
| Diagram | Ej | Planerat Iteration 2 |
| Export (CSV/PDF) | Ej | Planerat |
| Notifikationer | Ej | Planerat |
| Bankimport | Ej | Placeholder service |

## Kom igång

Förutsättningar:
- .NET 8 SDK

Kör:
```bash
dotnet restore
dotnet run --project src/Server/FinanceApp.Server.csproj
```
Öppna klienten (WASM hostad via server):  
http://localhost:5000 eller https://localhost:5001

## Projektstruktur
```
FinanceApp.sln
src/
  Client/
  Server/
  Shared/
docs/
  architecture.md
  backlog_mvp.md
  design_tokens.md
```

## Nästa rekommenderade steg
1. Riktig autentisering (ASP.NET Identity + JWT).
2. Databas: byt InMemory → SQLite / PostgreSQL.
3. Diagram (Chart.js interop eller MudBlazor).
4. Export (CSV först, sedan PDF via t.ex. QuestPDF).
5. Offline caching (Workbox + fallback).
6. Notifieringar (Email + Web Push).
7. Bankimport (CSV/ISO20022 + bakgrundsjobb).
8. Feature toggles (appsettings / LaunchDarkly / egna flags).

## Arkitektur (kort)
- Client: Blazor WASM (UI + API-anrop)
- Server: ASP.NET Core Minimal APIs + EF Core
- Shared: Modeller / DTO:er
- PWA: manifest + service worker (kräver vidare strategi)
- Teman: CSS Custom Properties (design tokens)

Mer detaljer: se docs/architecture.md

## Design & Tillgänglighet
- Mobile First (flex/grid)
- Grundläggande färgkontrast
- Kommande: WCAG 2.2 AA (fokus, aria-labels, skip links m.m.)

## Backlog & Roadmap
Se docs/backlog_mvp.md:
- MVP-status
- Nästa iteration
- Epics & User stories
- Tekniska stories

## Utveckling (tips)
- Lägg till testprojekt (xUnit) i /tests
- CI via GitHub Actions (build + test)
- Dockerfile för server (multi-stage)
- Branch-konvention: feature/*, fix/*, chore/*

## Miljövariabler (framtid)

| Variabel | Användning | Status |
|----------|------------|--------|
| CONNECTION_STRING | Databas | Ej än |
| JWT_ISSUER | Auth | Kommer |
| BANK_API_KEY | Bankintegration | Kommer |

## Licens
MIT – se LICENSE.

## Ansvarsfriskrivning
Detta är ett MVP/PoC. Ej produktionsredo (ingen riktig auth, ingen persisterad databas, ej härdad säkerhet).

## Kontakt / Vidare
Skapa gärna issues för:
- Förbättringar
- Buggar
- Nya förslag

---
© 2025 FinanceApp (arbetsnamn). MIT-licens.