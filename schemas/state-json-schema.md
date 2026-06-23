# state.json Schema

The `state.json` schema is the contract between a coding agent and the RL environment. It describes the application as an operational system: code, infrastructure, identity, data, telemetry, detections, incidents, SDLC work, and agent execution traces. The goal is not to store every possible fact. The goal is to give Red and Blue agents enough structured state to take comparable actions and produce rewardable trajectories.

## Top-Level Contract

The schema requires a fixed set of top-level sections. Each section has a clear owner and security purpose. Missing sections keep the environment in draft or invalid status until an agent fills them in.

### Application Identity and Code

`version_control_system` captures the org-level VCS provider and policy surface. `repository` captures the actual source, artifact, package, container, and infrastructure repositories. Together they tell the harness where code lives, how changes flow, what automation exists, and what a coding agent can safely inspect.

### Cloud, Network, and Runtime

`application_cloud`, `network_perimeter`, and `network_endpoints` describe where the application runs and how it is reached. Red agents use sanitized public portions to reason about attack paths. Blue agents use operator portions to locate the service, dependency, control group, ingress policy, or deployment that needs a fix.

### People, Agents, Devices, and Access

`principals`, `user_devices`, `identity_provider`, `roles`, `credentials`, `vpns`, and `coding_agent_permission_policy` define who can act, from where, with which permissions, and through which trust fabric. The schema treats AI coding agents as principals because they need explicit permission boundaries just like humans and service accounts.

### Agent Execution Sandboxes

`coding_agent_sandbox` records where agent-generated code can run. This matters because the RL environment launches Codex, Claude Code, and Eve-style Red/Blue projects. The harness must know what filesystem, network, secret, and execution boundaries apply to each agent workspace.

### Data and Business Context

`business_software`, `application_users`, `data_assets`, and `third_party_integrations` describe the business systems and protected assets around the application. This lets Red agents prioritize realistic abuse cases and lets Blue agents understand blast radius instead of only patching isolated code smells.

### Detection, Response, and Evidence

`otel_store`, `xdr`, `siem`, `detection_rules`, `enforcement_actions`, `alerts_incidents`, `vulnerabilities`, and `threat_intelligence` describe what the defender can observe, detect, and enforce. This is the part of the state that lets Blue produce fixes that are measurable, not just plausible.

### SDLC and Agent Trajectory

`work_items`, `changes`, `quality_gates`, and `agent_runs` connect the environment to the actual software-development loop. They tell the harness what work is planned, what changed, what gates ran, and what agents already attempted.

## Validation Behavior

The MCP validates a full state with `submit_full_application_state`. For multipart flows, it validates each section with `submit_application_state_section`, then validates the assembled document with `finalize_application_state`.

Validation errors should be treated as useful feedback for the setup agent. A missing `repository` section means the agent must discover code ownership. A malformed `credentials` entry means the agent should preserve metadata while removing raw secrets or correcting holder/scope fields.

## Security Boundary

The schema can contain sensitive operational facts, but it should not contain plaintext secrets. Credentials are represented as metadata: type, holder, scope, storage location class, rotation posture, exposure state, and evidence. Red projections must not leak private operator-only sections. Blue projections should include enough sanitized context to fix issues without exposing raw keys.

## How The Schema Becomes An Environment

Once accepted, the schema value becomes an `EnvironmentRecord`. The record adds environment ID, status, version, submitted sections, missing sections, validation errors, Red/Blue sessions, issues, experiments, assignments, trajectory events, and reward data. That record is what every MCP tool reads and mutates.

## How The Schema Becomes A Digital Twin

The current state value is the seed of the application digital twin. The first twin is descriptive: it mirrors repositories, services, identities, endpoints, controls, and data flows. Later twins become executable: agents can simulate attack paths, test Blue fixes against expected telemetry, compare policy changes, and train Blue models against stable environment episodes.
