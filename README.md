# grave-indexer-pub-rehearsal

NON-PRODUCTION rehearsal repository for the GraveYield/grave-indexer snapshot
publication pipeline (PR #5 remediation).

This repository exists ONLY to rehearse the real GitHub release operations of
`publish-console-snapshot.yml` in full isolation:

- the workflow `rehearsal-publication.yml` hard-guards on repository identity
  as its FIRST step (before checkout, before any write) and aborts anywhere
  else;
- it uses only the automatic `github.token` of its own run — the production
  release credential (`GY_RELEASE_PAT`) is never wired in;
- everything it creates here (versioned releases, the annotated tag object
  behind `refs/tags/console-snapshot-prod`, rollback drills) is rehearsal
  material and may be freely cleaned up after evidence has been recorded.

Scenarios (workflow_dispatch input `scenario`):
`happy` | `partial-upload` | `promotion-failure` | `incomplete-artifact` | `post-activation-failure`

See `docs/PUBLICATION_REHEARSAL.md` for the evidence-recording protocol.
