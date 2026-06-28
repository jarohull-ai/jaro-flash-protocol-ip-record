# JARO Flash Protocol (JFP) - Core Specification Definition

## 1. Philosophy
A prompt is not a protocol. AI can generate. JFP controls.
JFP replaces vague instruction with deterministic, auditable execution graphs.

## 2. JFP Document Structure (The .jfp format)
Every valid JFP document must strictly adhere to this machine-readable layout:

*   `JFP_DOCUMENT`: Root container.
*   `META`: Versioning, author, timestamp.
*   `BUILD_GRAPH`: Dependencies and execution steps.
*   `OUTPUT_MAP`: Expected outputs and file mappings.
*   `CONSTRAINTS`: Hard limits (memory, time, API calls).
*   `SIGNAL_ORANGE`: Risk flags and anomaly triggers.
*   `FACT_LAYER`: Validated, source-attributed facts only.
*   `DECISION_LAYER`: Arbitration logic and outcome mapping.
*   `CORRECTION_LAYER`: Self-healing and rollback instructions.
*   `END_JFP`: Termination block.

## 3. The 8 JFP Operating Rules
1. Define before you generate
2. Map before you create
3. Constrain before you execute
4. Validate before you trust
5. Dry-run before you change
6. Stop before you guess
7. Verify before you deliver
8. Report before you ask for trust

## 4. JFP Signal Matrix (Decision Outputs)
JFP systems do not output narrative text. They output structured signals:

*   `SIGNAL_UNKNOWN`: No verified data available (refuses to hallucinate).
*   `SIGNAL_DENY`: Action blocked (constitutional violation detected).
*   `DISPATCH_TACTICAL`: Forwarded to tactical/autonomous layer.
*   `DISPATCHED`: Action successfully dispatched.
*   `VOQL_AUTHORIZED`: Query authorized by VIKI Operational Query Language.
*   `SPEC_PARSED`: Syntax validation passed.

## 5. System Architecture (VIKI Integration)
JFP serves as the control plane for the VIKI ecosystem:

*   **Perception (VISION):** Uses probabilistic AI (e.g., Llama 4, Qwen2.5) to extract
    raw data into `FACT_LAYER`.
*   **Control (JFP / Hard-Software):** Deterministic layer validates facts against
    `CONSTRAINTS` and `DECISION_LAYER`. Executes in sub-microsecond bounds.
*   **Action (VIPER / OPSDESK):** Executes `DISPATCH_TACTICAL` or triggers
    `VIPER HEALER` for self-recovery.
*   **Audit (JFP-BC):** Every decision is written to an immutable blockchain audit trail.

## 6. Constitutional Invariants
The following rules are hardcoded and cannot be overridden by any prompt or model output:

*   No action may be taken on `SIGNAL_UNKNOWN` data.
*   `DEC_FAILSAFE` is the default state. `DEC_SAFE` must be mathematically proven.
*   All `DISPATCH_TACTICAL` events must be logged to `JFP-BC` before execution.
*   The `CORRECTION_LAYER` must be evaluated before any destructive operation.
