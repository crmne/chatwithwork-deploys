# Chat with Work deploy approvals

Every production deploy of [Chat with Work](https://chatwithwork.com) waits here for Carmine's approval. The deploy dispatches [`approve.yml`](.github/workflows/approve.yml) with the exact commit and container image digest about to go live; the job waits in the `production` environment until Carmine, its only required reviewer, approves it (GitHub's app notifies his phone); then it signs that request with a key only that environment holds, and the deploy checks the signature before it goes ahead.

The repository is public because GitHub offers required reviewers on environments to public repositories on its free plan. Nothing in it is secret: the signing key is an encrypted environment secret that a job reaches only after the approval, and the requests name a commit and an image digest, nothing else.

How it works and what it protects against: `docs/security/deploy-approval.md` in Chat with Work's repository.
