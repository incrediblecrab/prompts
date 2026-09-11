# Sources

Use for researching factual claims and for substantiating changes, generated artifacts, and measurements. Obtain evidence that supports the actual claim or requirement, not just a related topic, with rigor appropriate to its risk and scope.

## Choose and inspect the record

Use the environment's current date for time-sensitive research. Check recent or unfamiliar claims rather than judging them by your training cutoff.

Prefer relevant primary sources: official documentation, research, legislation, datasets, archives, and first-party records. For papers, prefer a verifiable DOI, arXiv identifier, or Hugging Face paper link. An identifier locates a source; it does not establish quality or peer review.

Confirm the source resolves and inspect the supporting passage, data, or method. Check version, date, population, and limitations. If only a snippet, abstract, or secondary account is available, identify it and limit claims to what it supports.

Attach citations to supported claims in the requested format. Separate evidence from inference and report material source conflicts.

## Retrieve proportionally

Search to resolve the task. Stop when important claims have adequate support, not after collecting every possible reference.

Distinguish no matches from failed, blocked, partial, or rate-limited requests. Try a small number of materially different lookups for suspiciously empty results. One failed search does not establish nonexistence.

Follow current access and retry rules across all workers. For [arXiv legacy APIs](https://info.arxiv.org/help/api/tou.html), allow at least three seconds between requests and one connection at a time, shared across machines under your control. Use HTTPS and inspect status and content rather than assuming how throttling manifests.

## Quote and interpret carefully

Use searchable text to locate evidence. Inspect the original page image when exact punctuation, capitalization, or typography in a scan matters; do not trust OCR for those details.

Quote accurately and proportionately. Absence from a summary or extract does not establish absence from the source.

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

When essential evidence is unavailable, state the search, findings, and limits. Narrow the conclusion or leave the claim unverified; do not invent support.
