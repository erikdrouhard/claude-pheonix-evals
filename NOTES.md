# Claude Code and Pheonix Arize evals!
- Hamel and Mikyo King 
- Mikyo opensource work at arise, was before at apple in ML

Open source: https://github.com/Arize-ai/phoenix

## Pheonix 
- Very agent friendly!
- a lot that was manuel before can be automated with pheonix


- This is still evolving and cutting edge so might be a bit rough around the edges.

- Skills will be used!
- Will have to evolve the skills over time.
- Always make sure the skills you use are safe to use and secure!


---


## Building agents with Claude code and Arize Pheonix

- Decemeber with Opus was a big turning point 
- Intelligence of these agents is a bit ahead of the infra.

---

## Evolution of software eng.
Who consumes the telemetry data?

### Phase 1
- App
- Observability platform
- Human Dev - (writes code)
- IDE


## Phase 2 (we are currently in phase 2)
- App
- Observability platform
- Human dev (prompts agent)
- Agentic IDE
  - Coding agent

## Phase 3 (speculative future)
- Application
- Observability platform
- Coding agent
- (notifies humnan who only monitors agent)


Obserability platform must evolve from human dashboards to programmatic interfaces an agent can consume
---

## Why traces ARE the source of truth
Code you can read vs Agents you can't!

### Traditional softeare
- you can read the logic
- (show DAG graph with if then statements and functions).
- Every path is visible and determinitic. You see it all before it runs
_source of truth_: The code itself


### AI Agent
- You cant read the logic
- (Shows dag that shows what the agent is doing. E.g. searching calling up another subagent etc, but you can't peer into why it decided those things at a fundamental level)
- You can't see ANY of this code that determines the output. You can only see it AFTER in the traces.
_the source of truth_: The traces

---

## Anatomy of a coding agent

### Coding agent (in random order) (The harness consists of:)
- Skills
- MCP
- Browser
- Tools
- Editor
- Prompts
- Memory
- Code execution

You need to tune the harness for your particular use case. And you do that mostly with SKILLS!
---

## Give a coding agent the obserability stack

1. Agentic app
2. Arize Phoenix
  - Traces
  - Evaluations
  - Feedback
3. Pheonix CLI
4. Coding agent (Implement change(PR) and restart app)
5. Codebase (re-run workload, test user journey back to step 4)

---

## The AI Engineer loop!
- Arize Pheonix is in the middle it powers the loop

_Agent does all these steps_:
- Observation (Look at the data) 
- Annotate data and build evals 
- Hypothesize why output is bad
- Design and run experiments
- Measure outcomes/ analyze errors
- If good, apply; else iterate

---

## DEMO

He has claude code connected to a custom Agent CLI which is connected to the Pheonex CLI.

Can ask claude what was the last trace in pheonix so it can trace what you were talking about with the Agent CLI we are testing that is connected to Pheonix


- Pulls the pheonix eval skill to do some axial coding with the agent!
  - Pulls down the data
  - Goes through the files
  - Does the open code step


- Do you think it's a good idea to have an agent do your open coding/axial coding for you?
  - YOU STILL NEED TO LOOK AT THE DATA!

- Agents allow you to get a second opinion on things. It might think of something you didn't.

- Agent can come up with a different coding strategy than I do.

- Will the agent have taste? Some agent harnesses do but you can build it into SKILLS


- You can prompt it to come up with a hypothesis.

- Voice to text

- Are you doing the analysis in pheonix?
- He's doing it with its own memory system directly in the agent right now.

- UX that forced you do to the open coding then you can have an agent also do open coding to compare the delta.


- Don't forget he has SKILLS that are set up with his own taste to use Pheonix

- After the hypothesis step, you can have the agent design an experiment to test the hypothesis. You can have it run the experiment and then analyze the results.

- Prove me right or prove me wrong through evals.

- Experiment is similar to scientific method. 
  - Control variables
  - System prompt of agent
  - Can you change it to give it better grounding?


- Use ASCII in terminal instead of MD. you can have a skill format that.

- Experiment is when you already have an eval its basically one one of a test.
- When you run it again you change 1 metric and then you can compare the results to see if it improved or not.

- **Separate to the evals themselves**: the question they are trying to answer in this mini class is "Will agents be able to write evals?"



---









