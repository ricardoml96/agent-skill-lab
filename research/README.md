# Research

Phase 0 exists to test the Agent Skill Lab product thesis before implementation.

## Current artifacts

- [Methodology](methodology.md) — how samples and tools will be compared safely.
- [Candidate corpus](corpus.yml) — 12 public skill packages selected for diversity.
- [Result schema](result-schema.md) — common structure for normalized observations.
- [Initial observations](findings-001.md) — evidence gathered before running scanners.
- [Fixture policy](fixtures/README.md) — rules for future controlled test fixtures.

## Current status

The corpus is **candidate-only**. Each entry has been confirmed to exist at the stated
path, but complete repository snapshots have not yet been pinned or downloaded.

No skill in the corpus has been executed by this project.

## Research questions

1. Which structural and packaging failures are missed by security-first scanners?
2. How often do scanners disagree, and do their reports include enough evidence to
   resolve the disagreement?
3. Can capabilities be normalized across platforms without implying enforcement?
4. Which compatibility claims can be checked deterministically and offline?
5. Which report fields are stable enough for CI and long-term comparison?
6. Do authors value conformance and portability checks enough to adopt them?

## Decision gate

Implementation begins only if research demonstrates:

- at least three repeatable compatibility or quality problems;
- at least two meaningful disagreements between existing tools, or equivalent gaps;
- at least one useful check that can run deterministically, locally, and without
  executing the inspected skill.

If these conditions are not met, the project scope must be changed before code is
written.

## Safety

Research follows the repository [Threat Model](../docs/threat-model.md).

- Static inspection comes before execution.
- Public URLs are references, not trust endorsements.
- No live malware is added to the repository.
- No third-party code is executed on a personal or credentialed host.
- Any future scanner execution must use pinned versions and a disposable environment.
