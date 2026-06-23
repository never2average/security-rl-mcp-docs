---
title: "state.json"
---

[Home](/security-rl-mcp-docs/)

# state.json

`state.json` is not a log dump or a loose inventory. It is the typed application-state snapshot that defines what the RL environment knows about the application at a specific version. The MCP accepts it in one request or section by section, validates it against the schema, stores it as an environment record, and uses it to generate role-scoped views for Red and Blue agents.

The state value is the seed for the environment. When it is complete enough, the control plane can derive public attack surface, identity and access posture, data sensitivity, service topology, development workflow, detection coverage, and the current backlog of work. That derived state is what makes the environment agent-friendly: a coding agent can ask for the next safe action instead of reverse-engineering a company from scratch.

## Required Shape

A valid submission contains these sections:

- `version`: schema version for compatibility checks.
- `version_control_system`: organization-level VCS provider, installation, and policy context.
- `repository`: source, package, image, IaC, and artifact repositories the application depends on.
- `application_cloud`: cloud accounts, projects, regions, workloads, storage, and managed services.
- `network_perimeter`: internet boundaries, segmentation, ingress policy, firewalls, and trust zones.
- `network_endpoints`: hosts, nodes, load balancers, services, and routable endpoints.
- `user_devices`: laptops, desktops, phones, and endpoint security posture for human operators.
- `principals`: humans, service accounts, bots, and AI agents that can act in the system.
- `coding_agent_sandbox`: isolated execution surfaces where coding agents run generated code.
- `business_software`: SaaS systems such as docs, chat, ticketing, CRM, email, and file storage.
- `vpns`: VPN, ZTNA, and remote access fabrics that bridge identities into networks.
- `otel_store`: telemetry pipelines, collectors, processors, exporters, and analytical stores.
- `coding_agent_permission_policy`: what coding agents are allowed to read, write, run, and deploy.
- `credentials`: credential metadata, holders, scope, storage, rotation, and exposure signals.
- `roles`: application and infrastructure roles that grant access to data or control planes.
- `inference_providers`: model providers used by coding agents or AI application features.
- `xdr`: endpoint and extended detection coverage, sensor health, and native detections.
- `siem`: central log and detection platform, schemas, retention, correlation, and alerting.
- `derived_services`: service-level views derived from infra, telemetry, code, and inventory.
- `identity_provider`: Okta, Entra, Google Workspace, LDAP, OIDC, and group membership posture.
- `application_users`: customer or external users distinct from internal staff principals.
- `detection_rules`: detection-as-code rules over telemetry and state.
- `enforcement_actions`: SOAR-style actions agents can trigger with guardrails.
- `alerts_incidents`: active and historical findings, incidents, triage, and response workflow.
- `data_assets`: crown-jewel datasets, sensitivity, location, lineage, and access paths.
- `vulnerabilities`: CVEs, package issues, endpoint findings, image flaws, and app weaknesses.
- `third_party_integrations`: inbound and outbound external trust relationships.
- `threat_intelligence`: feeds, indicators, campaigns, and mapped relevance to the app.
- `work_items`: backlog, epics, tasks, bugs, and planned SDLC work.
- `changes`: pull requests, commits, deployments, reviews, and landed code changes.
- `quality_gates`: CI, tests, scanners, policy checks, and release gates.
- `agent_runs`: execution traces of AI agents doing work inside the SDLC.

## Why It Is Sectioned

Agents rarely know the whole application in one shot. A setup agent can submit `repository` first, then `application_cloud`, then `identity_provider`, and continue until validation says the environment is ready. Each section is replaceable, so a later agent can improve one part without resubmitting the whole state.

`submit_full_application_state` is best when the local agent has already assembled a complete document. `submit_application_state_section` plus `finalize_application_state` is best when the agent is discovering state incrementally.

## Red and Blue Views

The same raw state is not shown to every agent.

Red agents receive a public or externally observable projection: internet-facing endpoints, public repositories, disclosed technology choices, public docs, exposed metadata, and safe summaries. They should not see private secrets, internal-only implementation notes, or privileged operator context.

Blue agents receive operator context needed to fix issues: affected services, safe configuration details, relevant work items, sanitized credentials metadata, telemetry coverage, and Red findings. Blue still should not receive raw secrets.

## State Versions

Every finalized change advances the environment version. Red findings record `flaggedAtVersion` and `dueByVersion`. Blue fixes are judged against that version boundary, which lets the RL harness reward fixes that land within one version of being flagged.

## What Good State Looks Like

A useful `state.json` is specific enough for agents to act. It names real services, owners, endpoints, repos, roles, data assets, telemetry, and controls. It avoids raw secrets. It records confidence and evidence where possible. It keeps public attacker knowledge separate from privileged operator knowledge.


---

## Documentation Sections

- [RL Environment MCP](/index)
- [Endpoint and Auth](/setup/endpoint-and-auth)
- [Connect Codex](/setup/connect-codex)
- [Connect Claude Code](/setup/connect-claude-code)
- [MCP Control Plane](/concepts/mcp-control-plane)
- [Environments](/concepts/environments)
- [state.json](/concepts/state-json)
- [Red/Blue Boundaries](/concepts/red-blue-boundaries)
- [Reward and Trajectory](/concepts/reward-and-trajectory)
- [Local vs Hosted Agents](/concepts/local-vs-hosted-agents)
- [Case Study: Submit Application State](/workflows/submit-state)
- [Case Study: Red/Blue State Experiment](/workflows/run-state-json-experiment)
- [Case Study: Blue LLM Training](/workflows/run-blue-llm-training-experiment)
- [Case Study: Red Team Agent Loop](/workflows/red-team-agent-loop)
- [Case Study: Blue Team Agent Loop](/workflows/blue-team-agent-loop)
- [Case Study: Export Training Data](/workflows/export-training-data)
- [MCP Tool Reference](/tools/tool-reference)
- [Digital Twins Roadmap](/roadmap/digital-twins)
- [Readiness Checks](/operations/readiness-checks)
- [Troubleshooting](/operations/troubleshooting)
