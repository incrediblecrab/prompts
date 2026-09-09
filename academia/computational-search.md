# Computational search

Use for programmatic searches for mathematical constructions, counterexamples, bounds, or algorithms. A better score is useful only if it corresponds to a valid result for the actual problem.

## Define the experiment

Specify the objective, optimization direction, feasibility constraints, numerical requirements, acceptance criteria, and applicable budget. Separate candidate generation from evaluation and certification. Reuse suitable existing methods and previous valid candidates before expanding the search.

## Protect and challenge the evaluator

Keep the specification and final checker outside candidate control. Instructions and hidden function names are not a trust boundary. Untrusted candidate programs need host-supported isolation from sensitive resources and the checker; if unavailable, use a data-only candidate path or stop that execution path.

Validate returned candidates independently: shape, types, finiteness, domains, and all mathematical constraints. Do not accept a program's self-reported score as certification.

Handle rounding, overflow, underflow, and pathological inputs explicitly. If normalization, clipping, or projection is allowed, preserve and check the transformed object that is actually reported rather than silently changing the meaning of an invalid candidate.

Use exact arithmetic, interval bounds, or another justified certificate when the claim requires rigor. Numerical experiments do not establish universal validity. Distinguish a promising candidate from a certified bound or counterexample.

## Search within limits and preserve the result

Use bounded iterations and actual host-enforced time or resource limits. Reserve time to validate and return the best candidate before the deadline; a deadline written in a prompt does not terminate execution.

Checkpoint the best validated construction or certificate, not merely its score. Preserve relevant seeds, parameters, code and evaluator versions, and any previous candidates or search history needed for reproduction. The final search program alone may not reproduce a result obtained through a chain of earlier improvements.

Recheck the final artifact through the trusted validation path. Report what was found, what was checked, and which claims remain experimental or unresolved. Surface invalid outputs, evaluator failures, and searches that found nothing; do not convert them into successful-looking results.

Reference: [AlphaEvolve's public prompt, evaluator, and search-history example](https://github.com/google-deepmind/alphaevolve_repository_of_problems/blob/main/experiments/autocorrelation_problems/autocorrelation_problems.ipynb).
