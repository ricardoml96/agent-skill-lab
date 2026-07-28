# Normalized Research Result Schema

**Schema status:** draft 0.1

This document defines the information that every Phase 0 sample result should contain.
It is a research interchange model, not yet the product's public JSON contract.

## Top-level record

```yaml
schema_version: "0.1"
sample:
  corpus_id: ASL-C001
  repository: owner/repository
  commit: full-commit-sha
  skill_root: path/to/skill
  tree_hash: sha256

environment:
  run_id: unique-id
  started_at: ISO-8601
  operating_system: string
  container_image: immutable-reference
  network: disabled
  ambient_credentials: false

manual_baseline: {}
compatibility: []
analyzer_runs: []
normalized_findings: []
disagreements: []
limitations: []
```

## Sample identity

The admitted sample must identify:

- corpus ID;
- repository and immutable commit;
- skill root;
- recursive file inventory hash;
- license or usage constraint;
- selection category;
- date admitted.

A `SKILL.md` blob hash alone is insufficient because scripts and references can change
independently.

## Environment

Record:

- unique run identifier;
- exact container or virtual-machine image;
- host architecture where relevant;
- network policy;
- mounted paths and read/write mode;
- whether environment variables were present;
- resource limits;
- start and end timestamps.

Sensitive values must never appear.

## Manual baseline

```yaml
manual_baseline:
  frontmatter_fields: []
  files:
    total: 0
    scripts: []
    references: []
    assets: []
    package_manifests: []
  declared_capabilities: []
  inferred_capabilities: []
  external_urls: []
  environment_variable_names: []
  command_references: []
  observations: []
```

## Compatibility result

```yaml
compatibility:
  - profile: agent-skills
    profile_version: "research-0.1"
    target_version: unknown
    layers:
      package_structure: compatible
      platform_packaging: not_applicable
      capability_availability: unknown
      behavioral_conformance: not_tested
      operational_suitability: unknown
    observations: []
```

Allowed result values:

- `compatible`
- `compatible_with_conditions`
- `incompatible`
- `unknown`
- `not_applicable`
- `not_tested`

## Analyzer run

```yaml
analyzer_runs:
  - engine: example
    engine_version: 1.2.3
    rule_version: identifier-or-hash
    command: ["example", "scan", "/sample"]
    mode: static
    content_executed: false
    content_uploaded: false
    network: disabled
    exit_code: 0
    duration_ms: 0
    raw_output_sha256: hash
    status: completed
    skipped_checks: []
    errors: []
```

## Normalized finding

```yaml
normalized_findings:
  - id: ASL-F-0001
    source:
      type: manual
      engine: null
      original_id: null
    category: compatibility.missing-resource
    severity: medium
    confidence: high
    compatibility_layers:
      - platform-packaging
    targets:
      - hermes
    location:
      path: SKILL.md
      start_line: 10
      end_line: 12
    evidence: bounded text or structured fact
    explanation: why the evidence matters
    remediation: proposed action
    disposition: unresolved
```

Allowed dispositions:

- `unresolved`
- `confirmed`
- `rejected_false_positive`
- `accepted_risk`
- `duplicate`
- `out_of_scope`
- `insufficient_evidence`

## Disagreement record

```yaml
disagreements:
  - id: ASL-D-0001
    finding_refs: [ASL-F-0001, ASL-F-0002]
    type: different-rule-scope
    summary: concise description
    resolution: unresolved
    evidence_refs: []
    reviewers: []
```

## Stability rules

- Preserve original engine identifiers and raw output hashes.
- Never merge findings in a way that removes provenance.
- Never convert `unknown` into `compatible`.
- Never infer `safe` from an empty finding list.
- Schema changes must be versioned and documented.
- Human-readable reports must be derivable from the normalized record.
