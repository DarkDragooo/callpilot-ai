# callpilot-ai
Autonomous voice logistics system that deploys parallel AI calling agents to book real-world appointments in minutes.

# CallPilot — Autonomous Voice Logistics for Appointment Booking

CallPilot turns the phone network into an executable API.

A user says: “Book a dentist tomorrow afternoon.”  
CallPilot validates the user’s calendar, previews real providers, then deploys a **parallel calling swarm** of voice agents to negotiate availability and secure the best slot.

## Demo (Golden Path)
1) User: “Book a dentist tomorrow afternoon.”  
2) Orchestrator: checks calendar → previews providers → asks to launch  
3) Swarm: calls multiple providers in parallel  
4) Result: best slot returned for confirmation

> **Hackathon note:** For demo safety, swarm calls can run against test numbers / simulated receptionists.

## Architecture
**Orchestrator (Manager)** — talks to the user and launches swarm  
**Provider Agent (Worker)** — talks to receptionists and negotiates slots  
**Swarm Engine** — runs parallel calls, aggregates results, ranks options  
**Tools** — calendar, provider lookup, distance, swarm launch


## Key Features
- **State-machine Orchestrator:** Collect → Validate → Preview → Execute
- **Calendar-safe booking:** avoids double booking before calling
- **Parallel outreach (“Swarm Mode”):** calls multiple providers simultaneously
- **Real provider preview:** Google Places / directory data before launch
- **Deterministic tool-driven execution:** no hallucinated availability

## Tools
- `check_user_calendar(start_datetime, end_datetime)`
- `preview_providers(service_keyword, location)`
- `launch_swarm(service_type, target_time_window, max_calls=5)`

## Repo Structure (planned)
- `backend/` FastAPI/Node swarm engine + tool endpoints
- `agents/` prompts + config for Orchestrator and Provider Agent
- `dashboard/` realtime swarm visualization (cards: Dialing → Negotiating → Slot Found)
- `docs/` architecture + demo script

## Setup (high level)
1) Configure ElevenLabs Agents:
   - Orchestrator (user-facing)
   - Provider Agent (receptionist-facing)
2) Run backend tool server (calendar/provider/swarm)
3) Run dashboard to visualize calls

## Team
Built for the ElevenLabs Agentic Voice Hackathon.
