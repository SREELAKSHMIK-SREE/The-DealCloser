# The DealCloser – Intelligent B2B Sales Prep Agent
Multi-agent Gemini-powered Sales Research &amp; Outreach Generator for B2B SDRs

A Gemini-powered multi-agent system that researches a target company, extracts likely business problems, and drafts a personalized cold email for a specific buyer role.

## 1. Problem

B2B SDRs spend significant time:
- Researching target accounts
- Guessing their current strategic priorities
- Manually writing “personalized” cold emails

This is repetitive, slow, and often produces generic outreach.

## 2. Solution

DealCloser is an intelligent B2B sales prep agent that:
1. Searches for the latest strategic business news about a target company.
2. Analyzes that news to extract a small set of key business problems.
3. Writes a concise, role-specific cold email that speaks directly to those problems.

## 3. Architecture

- **LLM**: Google Gemini (via `ChatGoogleGenerativeAI`).
- **Orchestration**: LangGraph `StateGraph` + `MemorySaver`.
- **Tools**: `DuckDuckGoSearchRun` for web search.
- **Agents**:
  - `researcher` – fetches recent news about the company.
  - `analyst` – summarizes the news into 2 key business problems.
  - `copywriter` – drafts a short cold email for a given role.

```mermaid
flowchart LR
    A[User Input\nCompany + Role] --> R[Research Agent\n(web search)]
    R --> S[Analysis Agent\n(business problems)]
    S --> C[Copywriter Agent\n(cold email)]
    C --> O[Final Email Draft]
