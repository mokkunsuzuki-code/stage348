# REMEDA Stage348

## Quantum-Safe Evidence Binding Schema Layer

Stage348 extends Stage347 by binding PQC/QKD evidence metadata to a shared schema, SHA256 hashes, Git commit metadata, and signature presence checks.

Stage347 introduced quantum-safe behavior templates.

Stage348 strengthens that layer by reducing:

- self-reported JSON trust
- schema drift
- unbound evidence
- unknown behavior passing as valid

---

## Purpose

Stage347:

```text
PQC/QKD Behavior Templates
↓
pass / fail / unknown

Stage348:

PQC/QKD Evidence JSON
↓
JSON Schema Validation
↓
SHA256 Binding
↓
Git Commit Binding
↓
Signature / Sigstore Presence Check
↓
pass / fail

Stage348 is fail-closed.

If the evidence is invalid, unknown, unsigned, schema-incompatible, or unsafe, the binding decision fails.

What Stage348 Adds
quantum_safe_evidence.schema.json
quantum_execution_evidence.json
quantum_schema_validation_result.json
quantum_evidence_binding_result.json
schema versioning
evidence SHA256 binding
schema SHA256 binding
source Git commit binding
producer ID
signature presence check
Sigstore bundle presence check
fail-closed decision behavior
Public Artifacts
docs/schema/quantum_safe_evidence.schema.json
docs/quantum/quantum_execution_evidence.json
docs/quantum/quantum_schema_validation_result.json
docs/quantum/quantum_evidence_binding_result.json
Safety Boundary

Stage348 publishes safe metadata only.

It does not publish:

private keys
raw QKD key material
cryptographic secrets
exploit code
attack procedures
production cryptographic backend code
Decision Meaning
pass: schema is valid, evidence is hash-bound, commit-bound, and signature indicators are present
fail: schema invalid, unsafe metadata detected, signature indicators missing, or unknown state detected
Position

Stage347:

Quantum-Safe Behavior Template Layer

↓

Stage348:

Quantum-Safe Evidence Binding Schema Layer

Stage348 moves the system from self-reported PQC/QKD JSON toward schema-validated and hash-bound evidence metadata.

License

MIT License

Copyright (c) 2026 Motohiro Suzuki
