# Juggler.ai

**Dynamic AI Scheduler**

Juggler.ai is an intelligent backend service that turns static to-do lists into dynamic, adaptable schedules. Built for high-performers, it uses Spring Boot 4 and Google Gemini AI to automatically reschedule your day based on real-time progress—so your plan stays realistic when tasks finish early or run late.

---

## Features

- **Adaptive rescheduling** — When a task is completed early or late, remaining tasks are automatically shifted so the rest of the day stays coherent.
- **Smart buffer logic** — Configurable intervals (default 30 min) that scale with task intensity (e.g., longer cooldowns after Deep Work).
- **Google ecosystem** — Native sync with Google Tasks and Google Calendar.
- **AI-driven optimization** — Gemini 2.5 Pro analyzes schedule context and applies time-management principles (e.g. “Eat the Frog”) to reduce burnout and improve ordering.
- **Modern stack** — Java 21, Spring Boot 4, virtual threads, and versioned APIs.

---

## Tech stack

| Layer        | Technology |
|-------------|------------|
| Backend     | Java 21, Spring Boot 4.0.2 (Spring Framework 7) |
| AI          | Spring AI 2.0.0-M2 (Google Gemini) |
| External    | Google Tasks API, Google Calendar API |
| Cloud       | AWS (Lambda / RDS), Docker |
| Build & tools | Maven, Lombok, JSpecify (null safety) |

---

## Prerequisites

- **Java 21**
- **Maven** (or use the included wrapper `./mvnw`)
- **Environment variables** for API keys and OAuth (see [Configuration](#configuration))

---

## Configuration

Create or edit `src/main/resources/application.yml` and wire in your credentials via environment variables. Do not commit real keys.

```yaml
spring:
  ai:
    google:
      genai:
        api-key: ${GEMINI_API_KEY}
  security:
    oauth2:
      client:
        registration:
          google:
            client-id: ${GOOGLE_CLIENT_ID}
            client-secret: ${GOOGLE_CLIENT_SECRET}

juggler:
  buffer:
    default-minutes: 30
    deep-work-cooldown: 45
    admin-transition: 15
```

Set `GEMINI_API_KEY`, `GOOGLE_CLIENT_ID`, and `GOOGLE_CLIENT_SECRET` in your environment or in a local config file that is not committed (e.g. `application-local.yml`).

---

## Getting started

**Clone and enter the repo:**

```bash
git clone https://github.com/yourusername/juggler-ai-backend.git
cd juggler-ai-backend
```

**Build:**

```bash
./mvnw clean install
```

**Run:**

```bash
./mvnw spring-boot:run
```

---

## API reference (v1)

| Method | Endpoint | Description |
|--------|----------|-------------|
| `POST` | `/api/v1/schedule/complete` | Signal task completion and trigger a full schedule juggle. |
| `GET`  | `/api/v1/schedule/current` | Return the current optimized timeline (from Google Tasks). |
| `PATCH`| `/api/v1/config/buffer`    | Update buffer settings at runtime. |

---

## Productivity principles

- **30-minute gap** — Every reschedule includes a mandatory mental reset window between blocks.
- **Contextual buffers** — The system treats “Deep Work” tasks (e.g. LeetCode, focused coding) as higher intensity and applies longer recovery periods automatically.

---

## Development

We use an agile workflow and GitHub for backlog, code, and collaboration. See [docs/AGILE.md](docs/AGILE.md) for workflow, branch naming, and how we use Issues and Pull Requests.
