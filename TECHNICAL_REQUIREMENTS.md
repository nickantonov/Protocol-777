# Technical Requirements — Implementing Protocol 777

This document translates the Protocol's principles into engineering controls. Controls must be adapted to the actual system, threat model, and consequences of failure.

## 1. Separate policy from capability

- Keep safety policy and authorization logic outside ordinary user-editable prompts where feasible.
- Do not rely on a model's verbal promise to enforce a safety property.
- Use deterministic checks and external policy enforcement for critical actions.
- Version and review changes to system instructions, policy, tools, and permissions.

## 2. Enforce least privilege

- Give each component only the access required for its task.
- Separate read and write access; use short-lived credentials where feasible.
- Isolate execution environments and restrict outbound network access.
- Require explicit authorization for irreversible, financial, public, or physical actions.
- Apply independent limits on rate, budget, scope, and duration.

## 3. Use layered safeguards

- Combine model-level behaviour with application policy, access controls, sandboxing, monitoring, and human approval.
- Avoid single points of failure for high-consequence safeguards.
- Treat external content, retrieved documents, and tool outputs as untrusted data rather than executable instructions.
- Test for prompt injection, confused-deputy failures, privilege escalation, and unsafe tool chaining.

## 4. Fail safely

- Define safe states for service interruption, uncertain authorization, unavailable dependencies, and detected compromise.
- Make emergency stop and revocation mechanisms accessible to authorised operators.
- Do not allow a failed safety check to silently become permission to proceed.
- Ensure that fail-closed behaviour does not itself create disproportionate hazards; assess the context.

## 5. Audit without creating new harm

- Record relevant actions, authorizations, denials, policy changes, and incidents.
- Minimise sensitive content in logs; protect access and retention.
- Use tamper-evident storage where justified and feasible.
- Ensure audit records support investigation without becoming a surveillance system.

## 6. Evaluate and red-team

- Define measurable safety properties and known limitations before release.
- Test normal use, edge cases, adversarial inputs, integration failures, and recovery.
- Use independent assessment for high-impact systems.
- Track incidents, regressions, and unresolved risks; retest after changes.

## 7. Human oversight must be real

- Provide operators with sufficient context, time, authority, and training to intervene.
- Avoid nominal “human in the loop” arrangements where a person cannot meaningfully review or stop an action.
- Establish escalation paths and preserve accountability across vendors and operators.

## 8. Document claims

For each claimed control, document:
- the risk addressed;
- the mechanism enforcing it;
- its trusted computing boundary and dependencies;
- the test or evidence demonstrating effectiveness;
- known bypasses and residual risk;
- the responsible owner and review date.

**No safeguard is absolute.** Protocol 777 calls for layered, testable, and accountable risk reduction—not a claim that AI can guarantee its own safety.