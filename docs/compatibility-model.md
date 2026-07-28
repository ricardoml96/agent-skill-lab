# Compatibility Model

## Goal

Describe compatibility as evidence across layers, not as a single yes/no label.

## Compatibility layers

### Layer 1 — Package structure

Can the skill be discovered and parsed as a folder-based Agent Skill?

Examples:

- required `SKILL.md`;
- valid frontmatter;
- valid name and description;
- resolvable bundled resources.

### Layer 2 — Platform packaging

Does the target platform recognize the skill's location, metadata, naming, and install
method?

Examples:

- OpenClaw-specific metadata;
- Hermes skill directories and discovery;
- NanoClaw build-time customization conventions;
- Codex or Claude Code skill discovery paths.

### Layer 3 — Capability availability

Does the target runtime provide the tools or environment that the skill assumes?

Examples:

- shell execution;
- browser control;
- MCP servers;
- required binaries;
- environment variables;
- filesystem mounts.

### Layer 4 — Behavioral conformance

Does the skill complete defined scenarios with expected outcomes on the target runtime?

This layer requires approved execution and is deferred beyond the static MVP.

### Layer 5 — Operational suitability

Is the skill appropriate under the user's policy, privacy, and deployment constraints?

This cannot be reduced to technical compatibility alone.

## Result vocabulary

- **Compatible:** all checks in the evaluated layers passed.
- **Compatible with conditions:** required configuration or capabilities are explicit.
- **Incompatible:** a known requirement cannot be satisfied.
- **Unknown:** the relevant layer was not tested or cannot be determined.
- **Not applicable:** the check does not apply to the target.

Every result must identify which layers were evaluated.

## Initial profiles

| Profile | Planned static scope | Primary references |
|---|---|---|
| Agent Skills | Core folder and metadata conformance | <https://agentskills.io/home> |
| OpenClaw / ClawHub | Publishing metadata and runtime requirements | <https://github.com/openclaw/clawhub/blob/main/docs/skill-format.md> |
| Hermes Agent | Standard compatibility and discovery conventions | <https://hermes-agent.nousresearch.com/docs/user-guide/features/skills> |
| NanoClaw | Skill-based installation and customization assumptions | <https://github.com/nanocoai/nanoclaw> |
| Codex | Skill package conventions supported by Codex | Official Codex documentation and fixtures, to be pinned during research |
| Claude Code | Custom skill discovery and packaging | Official Claude Agent Skills documentation and fixtures |

No profile is implemented yet.

## Versioning

Profiles will be versioned independently from the CLI because platforms can change
without a core release.

A report should record:

- Agent Skill Lab version;
- report schema version;
- profile name and version;
- target platform version or range, when known;
- rule identifiers and versions;
- configuration and skipped checks.

## Portability principle

Platform-specific metadata is allowed, but the report should separate:

- portable core information;
- namespaced platform extensions;
- requirements that cannot be represented elsewhere;
- transformations that would lose behavior or meaning.

Automatic conversion must never silently discard unsupported information.
