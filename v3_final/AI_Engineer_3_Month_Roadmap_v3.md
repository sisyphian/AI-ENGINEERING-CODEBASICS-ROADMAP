# 3-Month Intensive AI Engineering Roadmap
**Goal:** Land an AI engineering / full-stack-with-AI role at Brain Station 23, SELISE, or remote international, by end of sprint.
**Starting point:** ~2 yrs SWE experience, MERN/Next.js, Python, LangChain, LlamaIndex, vector DBs, TensorFlow/PyTorch comfort, CartQ SaaS in progress, Bengali ESP32 TinyML project in progress.

This is NOT the source roadmap followed beginner-to-end. It's that roadmap's topic coverage, re-sequenced around what you already know, compressed where you have head start, and fused with your two live portfolio projects so every week produces interview-usable evidence — not just tutorial completion.

---

## How the 12 weeks are structured

- **Weeks 1–2:** Fill gaps + stand up eval/observability foundations (you skip basics, hit only what's new)
- **Weeks 3–5:** Agentic systems + multi-agent + MCP, built directly into CartQ and the Bengali agent
- **Weeks 6–7:** Deployment, cost optimization, cloud (Azure priority — confirmed top cloud in AI job postings)
- **Week 8:** Fine-tuning + local models (only as much as job posts demand — see note in Week 8)
- **Weeks 9–10:** Portfolio polish, eval harnesses finalized, blog/case-study writing
- **Weeks 11–12:** Interview prep (DSA + system design + AI-specific rounds) + active applications

**Parallel track running every week, non-negotiable:** job applications, LinkedIn/X activity, DSA practice. AI skill alone doesn't pass BD-market screens — see note at the end.

---

## Week 1: Gap-Fill + Eval/Observability Foundations

You already know RAG, LangChain, vector DBs — skip the "what is RAG" content entirely.

**New topics to cover:**
- Docling for document parsing/chunking (you likely haven't used this specific tool)
- RAGAS for RAG evaluation
- LangSmith: traces, runs, threads, cost tracking

**Action items:**
- [ ] Instrument your existing CartQ RAG support pipeline with LangSmith tracing
- [ ] Build a RAGAS eval suite (faithfulness, answer relevancy, context precision) against CartQ's RAG pipeline — this becomes your "I evaluate AI systems, not just build them" interview story
- [ ] Re-chunk one existing document set using Docling instead of your current splitter, compare retrieval quality

**Resources:** Docling tutorial (RedHat), RAGAS quickstart, LangSmith tutorial playlist (from source roadmap, weeks 2 & 4)

**Output:** CartQ RAG pipeline now has tracing + measurable eval scores. This single deliverable is more interview-defensible than a fresh tutorial chatbot.

---

## Week 2: Agent Fundamentals You Haven't Formalized

You've used agentic coding tools (Claude Code, OpenCode, Codex CLI) but likely haven't built ReAct-pattern agents from scratch with guardrails.

**Topics:**
- ReAct loop (reasoning + action) — implement manually once, don't just use a framework
- Tool binding in LangChain
- Guardrails (input/output validation, content filtering)
- Agent security basics (prompt injection awareness, scoped tool permissions)

**Action items:**
- [ ] Build the CartQ Bangla voice-ordering assistant as a proper ReAct agent (if not already) with explicit tool calls (menu lookup, order placement, price calc)
- [ ] Add guardrails: validate agent can't place orders outside valid menu items, can't leak other vendors' data (ties into your row-level security work)
- [ ] Re-run RAGAS-style eval on the agent's task completion, not just RAG quality

**Resources:** ReAct explainer, LangChain agents docs, Anthropic's "Building Effective Agents" (source roadmap week 6 — read this now, it's foundational not advanced)

---

## Week 3: Multi-Agent Systems with LangGraph

This is new ground — worth the full time the source roadmap gives it.

**Topics:**
- LangGraph: state, nodes, graphs
- Conditional routing
- Multi-agent orchestration
- Human-in-the-loop patterns

**Action items:**
- [ ] Redesign CartQ's order pipeline as a LangGraph state machine: order-intake agent → menu-clarification agent (human-in-loop if ambiguous) → prep-time-prediction handoff → confirmation agent
- [ ] This maps your existing prep-time prediction model into the agent graph — a genuinely differentiated multi-agent commerce system, not a toy example

**Resources:** LangGraph crash course, LangGraph agentic project walkthrough, LangChain human-in-the-loop docs

**Output:** A real multi-agent system in a production-shaped codebase — your strongest single portfolio artifact.

---

## Week 4: Model Context Protocol (MCP)

You've explored agentic coding tools deeply — now build the other side: an MCP server.

**Topics:**
- What MCP is and why it matters (context engineering)
- Building an MCP server + client
- Implementing context engineering patterns in LangGraph

**Action items:**
- [ ] Build an MCP server exposing CartQ's vendor/menu data (or your HSK flashcard data — either is a fine, scoped public-API-shaped project)
- [ ] Connect it to a LangGraph agent as a tool source
- [ ] Write a short README explaining the context-engineering decisions (what you expose vs. withhold from the model, token budget reasoning)

**Resources:** "What is MCP" video, "Build your MCP server" video, context engineering talk (source roadmap week 5)

---

## Week 5: Bengali Agent + Eval Harness (your differentiator project)

Dedicated week for the project memory shows you've identified as your strongest AI-engineering signal.

**Action items:**
- [ ] Formalize the Bengali-aware AI agent: wire your existing ESP32/Bengali speech work into a LangGraph agent with explicit tool use
- [ ] Build the eval harness: a labeled test set of Bengali commands/queries, measure intent recognition accuracy, latency, and failure modes on low-resource language input
- [ ] Document why this is hard (low-resource language, code-switching, TinyML constraints) — this becomes your narrative for both job interviews and the CSC scholarship application

**Output:** This is your "can't be replicated by a chatbot-wrapper candidate" project. Prioritize finishing it over chasing more frameworks.

---

## Week 6: Deployment + Observability at Production Scale

**Topics:**
- Azure AI Foundry, Azure ML, Azure Functions/App Service (priority — confirmed most-demanded cloud in AI job postings)
- AWS AgentCore (secondary, lighter pass)
- Cost optimization: response caching, rate limiting, model cascading/selection

**Action items:**
- [ ] Deploy one CartQ AI component (the RAG support pipeline or the ordering agent) to Azure
- [ ] Add semantic response caching to cut redundant LLM calls — measure and report the cost reduction (e.g., "cut API costs 40% via semantic cache")
- [ ] Implement basic rate limiting on the FastAPI backend

**Resources:** Azure AI Foundry tutorial, AWS AgentCore tutorial, semantic caching video (source roadmap weeks 4 & 6)

---

## Week 7: Multimodal RAG + Open Source Contribution

**Topics:**
- Multimodal RAG (image + text retrieval) — relevant if CartQ has menu images/photos
- Open source contribution (signals collaborative engineering, not just solo projects)

**Action items:**
- [ ] Add multimodal retrieval to CartQ: let the RAG pipeline reason over menu item photos (CLIP-style embeddings or a vision-capable model)
- [ ] Find one "good first issue" in an AI tooling repo (MindSQL, ragrank, or similar LangChain/RAG-adjacent repos) and submit a real PR
- [ ] Update LinkedIn/GitHub to reflect the contribution

---

## Week 8: Fine-Tuning + Local Models — Scoped, Not Deep

**Reality check on this topic:** fine-tuning (LoRA/QLoRA) and local model deployment (Ollama) appear in fewer junior/mid AI engineering job postings than RAG, agents, and deployment skills do. Don't let this become a multi-week rabbit hole.

**Topics (time-boxed to ~4–5 days):**
- What LoRA/QLoRA are and when fine-tuning is the right call vs. prompt engineering/RAG
- Run one model locally via Ollama
- Optional: one small fine-tune with Unsloth if directly useful to the Bengali project (e.g., fine-tuning a small model for Bengali intent classification)

**Action items:**
- [ ] Run a quantized model locally with Ollama, document the latency/quality tradeoff vs. API calls — useful talking point for cost-conscious AI engineering roles
- [ ] If time allows: small Unsloth fine-tune for Bengali intent classification, feeding into the Week 5 eval harness

---

## Week 9: Portfolio Consolidation

No new frameworks this week. Pure consolidation.

**Action items:**
- [ ] Write up CartQ as a case study: architecture diagram, AI components, eval results, cost optimizations, what you'd do differently at scale
- [ ] Write up the Bengali agent project as a case study, framed for both job interviews and (separately) the CSC scholarship narrative
- [ ] Clean READMEs, pin both repos on GitHub, record a 3-minute demo video of each (employers skim, they don't clone repos)
- [ ] Update LinkedIn projects section, resume bullet points with measurable outcomes (eval scores, cost reductions, latency numbers)

---

## Week 10: DSPy + Declarative AI (light touch)

Source roadmap gives this a full week. Reality: DSPy shows up far less in BD-market and most international junior/mid AI engineering postings than LangChain/LangGraph does.

**Time-box to 3 days:**
- [ ] Work through the DSPy tutorial, build one small signature/module example
- [ ] Skip the "lovable clone" assignment — not high-value for your interview narrative

**Remaining 2 days of the week:** redirect to **DSA practice** (data structures, algorithms) — this is the gap the source roadmap doesn't address at all, and BD product companies screen on it regardless of AI specialization.

---

## Weeks 11–12: Interview Prep + Active Applications

This is where the source roadmap stops and where you actually need the most structured effort.

**Week 11:**
- [ ] DSA: focus on arrays/strings/hashmaps/trees — the patterns most likely in BD tech screens (per your existing Discord-sourced interview prep notes)
- [ ] Python/Django or FastAPI backend interview questions review
- [ ] System design basics for AI systems specifically: RAG pipeline design, agent architecture tradeoffs, scaling LLM API calls — practice explaining CartQ's and the Bengali agent's architecture out loud, on a whiteboard/paper, in under 5 minutes

**Week 12:**
- [ ] Mock interviews (use Claude or a peer) covering: behavioral, AI system design, live coding
- [ ] Finalize tailored resumes for Brain Station 23, SELISE, and 3–5 remote international targets
- [ ] Apply — aim for volume + targeting, not just targeting (10–15 quality applications, not 2)

---

## Parallel track — every single week, not optional

- **LinkedIn/X:** post or comment meaningfully 2–3x/week on AI engineering topics, ideally tied to what you're actually building that week (real progress posts outperform generic content)
- **DSA:** 30–45 min/day from week 1 onward, don't compress it all into week 11 — this was the one major gap in the source material for your specific target market
- **Job market scan:** check Brain Station 23, SELISE, and BD AI job groups weekly so you're not discovering requirements cold in week 12

---

## What I deliberately cut or compressed from the source roadmap, and why

| Source roadmap item | What I did | Why |
|---|---|---|
| Weeks 1–2 Python/RAG basics | Skipped | You already have this |
| ChromaDB/Qdrant intro | Skipped | Already in your stack |
| DSPy full week | Compressed to 3 days | Lower frequency in target job postings than LangGraph/agents |
| Generic "healthcare RAG chatbot" assignment | Replaced with CartQ/Bengali work | Generic assignments don't differentiate; same exercise as every other bootcamp grad |
| DSA / system design | Added (wasn't in source at all) | Hard gate at BD product companies regardless of AI specialization |
| Business case studies (ThinkSchool) | Dropped | Lower leverage for your specific 90-day goal than DSA/interview prep |

If you want, I can turn weeks 1–5 (the technical core) into a day-by-day checklist, or build the eval harness for the Bengali agent project as a starting codebase.
