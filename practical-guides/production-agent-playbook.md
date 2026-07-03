# Production Agent Playbook

> Step-by-step guide for deploying reliable AI agents — based on 306 practitioners and 100+ papers

---

## Phase 1: Foundation (Week 1-2)

### 1.1 Define Success Criteria
```
□ What does "correct" mean for each task?
□ What's the acceptable error rate?
□ What's the fallback when the agent fails?
□ Who reviews agent outputs, and how often?
```

**From MAP study**: 74% of production agents rely on human evaluation. You need automated metrics too.

### 1.2 Choose Your Architecture
```
□ Start simple: ReAct loop or prompt chain
□ Add complexity only when proven necessary
□ Plan for human checkpoints every 5-10 steps
□ Design for append-only transcripts (audit trail)
```

**From MAP study**: 68% of agents run ≤10 steps. Don't over-engineer.

### 1.3 Set Up Evaluation
```
□ Create regression test suite (20-50 representative tasks)
□ Include adversarial inputs
□ Run on every model/prompt/tool change
□ Track: success rate, latency, token cost, error types
```

---

## Phase 2: Harness Engineering (Week 2-4)

### 2.1 Context Management
```
□ Append-only storage with compaction views
□ Structured summaries (not truncation)
□ Full audit trail for every agent action
```

### 2.2 Tool Integration
```
□ Type signatures for every tool
□ Compile-time validation before execution
□ Tool registry with versioning
□ Sandbox for untrusted tool execution
```

### 2.3 Memory System
```
□ Match memory type to task type:
  - Timeline → event-based tasks
  - Semantic graph → conversational tasks
  - State log → database/API tasks
□ Local maintenance (not global rebuilds)
□ Periodic memory recovery audits
```

### 2.4 Safety Guardrails
```
□ LLM-VA vector alignment (minutes, no training)
□ Type-checked agent actions
□ Human checkpoint every 5-10 steps
□ Prompt injection detection
```

---

## Phase 3: Optimization (Week 4+)

### 3.1 When to Fine-Tune
```
□ Start with prompt engineering (70% of production agents stop here)
□ If prompts aren't enough → SFT on curated trajectories
□ If SFT isn't enough → GRPO with verifiable rewards
□ Monitor for entropy collapse (use STARE if needed)
```

### 3.2 Inference Optimization
```
□ Try speculative decoding (DSpark: 60-85% speedup)
□ Try test-time compute scaling before model upgrades
□ Prune redundant reasoning tokens (DRP: -64% tokens)
□ Quantize models (HyperQuant: 3.9x compression)
```

### 3.3 Cost Control
```
□ Track cost per task, not just per token
□ Use orchestrator pattern (small model routes to large models)
□ Batch similar queries when possible
□ Cache frequent tool call results
```

---

## Phase 4: Production Readiness

### 4.1 Reliability Checklist
```
□ Circuit breakers for each sub-agent
□ Graceful degradation (not catastrophic failure)
□ Health checks and alerting
□ Rate limiting and concurrency control
□ Idempotency for all state-changing operations
```

### 4.2 Observability
```
□ OpenTelemetry tracing across all steps
□ Structured logs for every model call, tool call, state change
□ Drift detection on prompts, models, tools
□ Cost tracking per agent/task/user
```

### 4.3 Continuous Improvement
```
□ Monthly regression test runs
□ Track error patterns → update prompts/tools
□ Review memory recovery rate (MEMPROBE approach)
□ Update safety audits after model upgrades
```

---

## 🚨 Top 5 Production Failure Modes

1. **Context explosion**: Passive history accumulation → agent loses coherence after 10+ turns
2. **Tool call errors**: Malformed JSON, wrong parameter types, hallucinated tools
3. **Silent degradation**: Agent appears to work but accuracy slowly drops over time
4. **Prompt injection**: User input reaches tool calls or system prompts
5. **Cost runaway**: Unbounded retry loops or excessive tool calls

---

*Last updated: July 2026 · [Back to README](../README.md)*
