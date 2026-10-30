# AI Business Development Automation

> ⚠️ **This repository does not contain source code.**
> The code is the intellectual property of **Coworky** and is proprietary.
> This repo exists solely to document my internship contribution.

## Context

Built during my internship at **[Coworky](https://www.coworky.org/)** (Nabeul, Tunisia)
from **June 1 to July 31, 2025**, as part of my engineering degree.

This module was integrated into **Yes-Sir.io**, Coworky's flagship SaaS platform for
HR management and recruitment. I was the **sole developer** on this module, under the
supervision of **Wassim Houes** (Dev Lead).

---

## What is this project?

An end-to-end **automated B2B business development module** that replaces manual
commercial prospection with an AI-driven pipeline. The system automatically:

1. Profiles the company using AI (website scraping + guided conversation)
2. Detects relevant opportunities from job boards and directories
3. Discovers target prospects via web search and Google Maps
4. Scores opportunities and prospects using LLM agents
5. Generates personalized outreach email proposals
6. Tracks email replies and classifies them using AI
7. Manages validated leads through a CRM lifecycle

---

## Tech Stack

| Layer | Technology |
|---|---|
| Backend API | Node.js, Express, Socket.IO |
| AI / Scraper | Python, Flask, Celery |
| Databases | MySQL, MongoDB, Redis |
| Frontend | React, Vite, Tailwind CSS |
| AI Models | Groq (LLaMA 3.3 70B), OpenRouter |
| Infrastructure | Docker Compose, Traefik |
| External APIs | Tavily, SerpAPI (Google Maps), Hunter.io |


### AI Agents (15 total)

| Module | Agent | Role |
|---|---|---|
| companyProfiler | `discoveryAgent` | Scrapes and extracts company data |
| companyProfiler | `profilingAgent` | Builds structured company profile |
| companyProfiler | `conversationAgent` | Guides admin Q&A to complete profile |
| companyProfiler | `businessDeveloperGraph` | Orchestrates profiling workflow |
| opportunityHunter | `opportunitySearchAgent` | Searches opportunity sources |
| opportunityHunter | `leadScoringAgent` | Scores opportunities with LLM |
| opportunityHunter | `demandIntentAgent` | Detects buying intent signals |
| opportunityHunter | `listParserAgent` | Parses directory listings |
| opportunityHunter | `opportunityProposalAgent` | Generates opportunity proposals |
| opportunityHunter | `serviceDemandStrategyAgent` | Builds search strategy per service |
| prospectDiscovery | `prospectSearchAgent` | Searches prospects via Tavily + SerpAPI |
| prospectDiscovery | `prospectScoringAgent` | Scores prospects with LLM |
| prospectDiscovery | `prospectDemandStrategyAgent` | Builds prospect search strategy |
| prospectDiscovery | `proposalGeneratorAgent` | Generates personalized email proposals |
| emailOutreach | `replyClassifierAgent` | Classifies email replies (positive/negative/neutral) |

---

## Key Features

- **Automated daily search** — BullMQ workers trigger opportunity and prospect
  searches every 24h for all companies with a complete profile
- **Dual discovery pipeline** — opportunities from scraped sources + prospects
  from AI web search and Google Maps (SerpAPI)
- **LLM scoring with feedback loop** — admin decisions (approve/reject) influence
  future scoring through a feedback-aware prompt system
- **Personalized AI proposals** — each outreach email is generated based on
  the prospect's context, the company's services, and real research data
- **Real-time dashboard** — all pipeline events streamed live via Socket.IO
- **Lead CRM** — approved prospects become leads with full activity tracking

---



