# Roadmap

This roadmap is outcome-based. Dates will be added only after the discovery phase
produces credible estimates.

## Phase 0 — Foundation

**Status:** in progress

- define the product thesis and non-goals;
- document the competitive landscape;
- establish the initial threat model;
- define the compatibility model;
- gather representative public skill fixtures;
- interview or collect feedback from skill authors and users;
- decide the implementation language after prototyping parsers and report formats.

**Exit criteria**

- the project has at least five documented user problems;
- at least three existing tools have been tested against the same fixtures;
- the first compatibility profiles have primary-source references;
- the MVP scope can be implemented without executing untrusted code.

## Phase 1 — Deterministic inspector

- discover and load one local skill directory;
- reject unsafe paths, links, archives, and oversized inputs;
- parse `SKILL.md` metadata and directory contents;
- validate the core Agent Skills structure;
- inventory scripts, references, assets, and declared requirements;
- infer a limited set of capabilities with evidence;
- export stable terminal, Markdown, and JSON reports;
- provide a versioned report schema;
- add unit tests and a corpus of safe and malformed fixtures.

**Exit criteria**

- no network or LLM is needed for baseline inspection;
- inspected files are never executed;
- report results are deterministic;
- each finding includes a source location and rule identifier.

## Phase 2 — Compatibility profiles

- implement versioned profiles for the open Agent Skills format;
- add OpenClaw / ClawHub, Hermes Agent, NanoClaw, Codex, and Claude Code profiles;
- distinguish syntax support from runtime capability support;
- produce a compatibility matrix and remediation suggestions;
- add profile conformance fixtures supplied or reviewed by platform users.

## Phase 3 — Developer workflow

- publish a standalone CLI package;
- add pre-commit and GitHub Actions integrations;
- compare reports between skill versions;
- support machine-readable policy thresholds;
- integrate established third-party security scanners as optional engines;
- preserve each engine's name, version, raw result, and limitations.

## Phase 4 — Behavioral lab

- design isolated runners with no ambient credentials;
- use deny-by-default filesystem and network policies;
- define reproducible task scenarios and expected outcomes;
- record tool calls, file access, network attempts, and process execution;
- compare declared intent with observed behavior;
- add explicit approval gates before any untrusted execution.

Behavioral execution will not be released until the sandbox threat model has received
independent review.

## Phase 5 — Accessible interface

- provide a local visual interface for non-specialists;
- explain findings without removing technical evidence;
- add guided remediation for authors;
- support signed and reproducible report bundles;
- evaluate an optional hosted collaboration service without weakening local-first use.

## Ideas deliberately deferred

- a public skill registry;
- universal safety certification;
- automated installation of untrusted skills;
- autonomous remediation without review;
- proprietary rules required for baseline operation.
