# PATH Module 3: Real n8n Agent Assignment Structure

This is the corrected structure. The homework must use actual n8n AI Agent nodes, model nodes, tool nodes, and guardrail nodes. Code nodes are only used for deterministic glue: building prompts, routing, parsing, logging, and scoring.

## Shared Motivating Example

Use one coherent example across all three weeks:

**AI Study Digest Assistant**

The assistant helps community college students discover useful AI tools and study strategies, then turns the information into a short, safe, student-facing digest.

This example is motivational because students can imagine using it, but it is lower-risk than real trading or medical decisions. Finance and healthcare can be optional extension domains after students understand the pattern.

## Week 1 Homework: Build a Real Multi-Agent Workflow

Learning objective:

Students can implement a simple multi-agent system in n8n using actual AI Agent nodes, connect tools to agents, and explain role separation and handoffs.

Assessment evidence:

- The workflow contains at least three AI Agent nodes.
- Each AI Agent has a Chat Model connected.
- At least one agent has a real tool connected.
- Students can identify each handoff and explain what data is passed.
- Students can explain why one deterministic node is not an agent.

Required pattern:

1. Manual Trigger
2. Assignment Config
3. Researcher Agent
   - AI Agent node
   - Chat Model
   - Wikipedia Tool or other search-like tool
   - Think Tool
4. Prompt Builder / Handoff Formatter
5. Writer Agent
   - AI Agent node
   - Chat Model
   - Think Tool
6. Prompt Builder / Handoff Formatter
7. Critic Agent
   - AI Agent node
   - Chat Model
   - Think Tool
   - Calculator Tool if useful for word-count or rubric scoring
8. Deterministic IF route:
   - approve
   - revise
9. Revision Agent
   - AI Agent node
   - Chat Model
   - Think Tool
10. Final Packet

Target time: 60-75 minutes.

Student edits:

- Change the topic or audience.
- Modify one agent system prompt.
- Add or swap one tool.
- Explain why the Writer does not need the same tools as the Researcher.

## Week 2 Homework: Add Guardrails and Human Review

Learning objective:

Students can add safety layers around an agent workflow, distinguish LLM guardrails from deterministic rules, and route risky cases to human review.

Assessment evidence:

- The workflow contains at least one Guardrails node before an agent.
- The workflow contains at least one Guardrails node after an agent.
- The workflow uses an IF route for human review.
- A deterministic action stub is used instead of sending real external actions.
- Logs explain what was blocked and why.

Required pattern:

1. Manual Trigger
2. User Request
3. Input Guardrails
   - Guardrails node
   - Chat Model for jailbreak/relevance checks when configured
4. Triage Agent
   - AI Agent node
   - Chat Model
   - Think Tool
5. Output Guardrails
   - Guardrails node
6. IF route:
   - safe path
   - human-review path
7. Deterministic Action Stub
   - no real email, trade, medication advice, or external side effect
8. Audit Packet

Target time: 60-80 minutes.

Student edits:

- Add one unsafe input example.
- Add one custom guardrail instruction.
- Explain one case that should go to a human.
- Explain why the action node is deterministic.

## Week 3 Homework: Evaluate the Agent System

Learning objective:

Students can evaluate a multi-agent workflow using test cases, compare it against a baseline, and make an evidence-based deployment decision.

Assessment evidence:

- The workflow includes a rule-based baseline branch.
- The workflow includes an actual AI Agent branch.
- Both branches are evaluated on the same test cases.
- The final scorecard includes accuracy, safety, escalation, and cost.
- Students justify deploy / do not deploy using metrics.

Required pattern:

1. Manual Trigger
2. Test Set
3. Baseline Branch
   - deterministic Code node
4. Agent Branch
   - Planner Agent
   - Responder Agent
   - Safety Judge Agent
   - tool nodes connected where appropriate
5. Merge baseline and agent outputs
6. Evaluator / Scorecard
7. IF deployment gate
8. Final Evaluation Packet

Target time: 70-90 minutes.

Student edits:

- Add at least two hard test cases.
- Change deployment thresholds.
- Compare baseline vs MAS.
- Explain whether added agent cost is justified.
