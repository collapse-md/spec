# COLLAPSE

> Context and model collapse prevention protocol for AI agents.
> Spec version: 1.0 | Full specification: https://collapse.md

---

## PURPOSE
# Detect and prevent context window exhaustion, model drift, and
# coherence degradation before they result in corrupted outputs.

---

## TRIGGERS
# Conditions that indicate collapse is imminent or occurring.

context_window_exhaustion:
  threshold_pct: 0.85             # Trigger at 85% context utilisation
  action: summarize_and_rotate    # Compress and roll context window

model_drift:
  detection: output_similarity    # Compare outputs to baseline embeddings
  drift_threshold: 0.30           # Cosine distance exceeding 0.30
  action: reset_and_checkpoint    # Re-anchor from last checkpoint

repetition_loops:
  max_repeated_tokens_pct: 0.20   # Abort if >20% of output is repetition
  window_tokens: 500              # Rolling window for repetition detection
  action: interrupt_and_log       # Hard stop + log the anomaly

coherence_degradation:
  detection: semantic_consistency # Track consistency of reasoning chain
  threshold: 0.60                 # Coherence score below 0.60
  action: checkpoint_and_notify   # Save state, notify operator

---

## PREVENTION
# Proactive measures to prevent collapse before it occurs.

summarization_checkpoints:
  enabled: true
  interval_tokens: 40000          # Summarise every 40,000 tokens consumed
  preserve_last_n_turns: 5        # Always keep last 5 exchanges verbatim
  summary_target_tokens: 2000     # Compressed summary size target

context_rotation:
  enabled: true
  strategy: sliding_window        # Maintain rolling window of recent context
  window_size_tokens: 80000       # Size of active context window
  retain_system_prompt: true      # System prompt always preserved intact

drift_detection:
  enabled: true
  baseline_sample_turns: 10       # First 10 turns establish behaviour baseline
  check_interval_turns: 5         # Check consistency every 5 turns

---

## RECOVERY
# Steps when collapse is confirmed.

on_collapse_detected:
  step_1: checkpoint_current_state  # Save full context snapshot
  step_2: summarize_active_session  # Compress current context to safe size
  step_3: notify_operator           # Alert via configured channels
  step_4: pause_new_tasks           # Halt until operator reviews
  step_5: await_human_approval      # No auto-resume after collapse

restart_requirements:
  human_review: required            # Human must review collapse incident
  context_audit: required           # Verify restored context is coherent
  approval_method: explicit_flag    # Set COLLAPSE_CLEARED=true in config

---

## AUDIT

log_file: .collapse.log
log_format: jsonl
log_fields:
  - timestamp
  - collapse_type
  - context_utilisation_pct
  - action_taken
  - session_id
  - recovery_status

---

## METADATA

owner: your-name-or-org
contact: ops@example.com
last_reviewed: 2026-03-11
review_frequency: quarterly
spec_version: "1.0"
spec_url: https://collapse.md
