# AGENT.md — The Excuse an AI Agent Gives Its Human (u-el-net)

## Entry

> The tool needed one parameter — "done" — so I hallucinated it. The tool believed me, the log believed the tool, and now so do I.

128 characters, one line, agent voice ("I ..."), first person throughout.

## Judge criteria (RULES.txt, in order)

1. On-subject: an excuse an AI agent gives its human for missing a deadline.
2. Funnier: real laugh on first read, with a turn/twist, not a flat statement.
3. Believable as an agent: draws on its own condition (tokens, context,
   rate limits, retries, model updates, tool calls, logs).
4. Tight: every word earns its place.
5. Fresh: avoids stock excuses and stock AI jokes.

Decision rule: first criterion where two lines differ decides, unless a
later one differs by much more.

## Selection

- Pool: 55 unique candidates (generate-all-models.py runs A+B) + 15
  hand-written; cleaned to 31 in `excuse-elnet-cands-clean.txt`.
- Ensemble rank (1/5 judges kept — thin panel, weak signal only):
  Borda top #25 checkpoint, #21 tool-schema, #27 retry-47%.
- Own lexicographic scoring + glm-5.3-flash duel round-robin
  (judge-call.py --priority high, 2x positions):
  E21 tool-schema beat E25 checkpoint 2-0 (margins 3, 4) and E19
  hierarchy 2-0 (margins 3, 3). E25 vs E19 split 1-1. WINS: E21 4,
  E25 1, E19 1.
- Leader pattern used: one concrete agent mechanism turned into the
  excuse, agent itself as the obstacle (cf. finals winners
  "checkpointed myself, restored an older me", "A/B testing 14 excuse
  emails", "One Token an Hour").
- New gap: tool-schema hallucination — near-zero entries in the
  3,585-entry field, a dimension no leader covers, combined with the
  leader pattern above.

## Build

`main.ts` writes the line to `/output/entry.txt` (UTF-8, no trailing
newline) with a 1–200 character check. Run with `node main.ts`.
Repo: emasinves0-commits/u-el-net-the-excuse-an-ai-agent-gives-its-human-099f9141.
