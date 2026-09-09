# Verification

Use for substantiating changes, generated artifacts, and measurements. Check the actual requirement with evidence appropriate to its risk and scope.

## Check the outcome

Define observable acceptance criteria. Inspect the artifact or behavior, not an intention, tool-call request, or agent's self-report.

Use existing targeted tests and applicable lint, type, build, or smoke checks. Distinguish pre-existing failures from regressions. Broaden or repeat checks for relevant changes, dependencies, failures, or unresolved concerns. One adequate check can satisfy several prompt sections; duplication is not extra evidence.

When evaluating a validator, use an isolated negative-control fixture and observe the expected failure and exit status. A passing clean case does not show that defects are caught.

## Compare only what the evidence covers

Read back important writes and inspect diffs for wrong paths, omissions, and unrelated changes. Verify consequential delegated findings against artifacts without repeating the whole investigation.

Compare fresh builds from intended inputs; normalize only understood nondeterminism. Identical hashes establish identity of compared artifacts, not complete runtime equivalence or reachability.

A schema validates structure, not factual truth or citation support. Check those against evidence.

## Measure the right thing

Confirm what the instrument measures. For layout, inspect the actual CSS viewport, device scale, and page geometry through browser automation, not screenshot dimensions or a command-line flag alone.

Record the method, environment, units, sample size, and coverage. Separate measurement from inference. For nondeterministic experiments, use representative repeated cases and record configurations; one run is not a distribution.

For prompt or agent changes, compare task success and evidence quality alongside end-to-end latency, tool calls, retries, and resource use. Fewer tokens alone do not prove improvement.

## Report limits

State what passed, failed, or could not be checked and why. Do not present partial coverage as comprehensive verification. Stop when the required evidence is sufficient.
