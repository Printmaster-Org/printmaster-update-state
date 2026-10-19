# PrintMaster update publication records

This public repository keeps publisher recovery fingerprints independently of
the application Server and Backblaze B2. It is not an update-signature scheme:
TUF remains the publisher authorization boundary.

## Current status

**Unreleased and unprovisioned.** The explicit generation-zero `state.json`
contains no latest or pending publication. No production signing or delivery
credential is configured. Actions are disabled in this records-only repository.

`main` requires administrator-enforced protection, linear history, restricted
pushes, no force-push and no branch deletion. The owner is the only permitted
writer initially. Future automation requires a separately reviewed scoped
credential and single-writer orchestration; neither is activated here.

## Public content only

Store only public-metadata root/timestamp/sealed-record SHA256 fingerprints,
timestamp versions and publication transition state. Publication timing and
fingerprints are permanently public. Never commit signing keys, credentials,
internal paths, private release data or operational logs.

Do not manually clear pending state, reset generation or replace a missing
state file as a recovery shortcut. The application tooling reserves the exact
pending publication before B2 writes and completes it only after verified
delivery. Interrupted operations require explicit retries of the same sealed
publication, not new signatures. Missing, conflicting or pending authority must
fail closed for latest-publication selection.

Conditional state updates are not distributed locks on B2. All publishing and
recovery writers must still be externally serialized. GitHub administrators and
authorized writers remain trusted: this repository is independent of B2/Server,
not GitHub or a compromised GitHub-hosted signer. Preserve latest-safe root and
publication fingerprint records outside GitHub as well.

Canonical procedures:
- https://docs.printmaster.work/development/update-publication-custody/
- https://docs.printmaster.work/development/update-signing-operations/

Until the paired documentation/source commits are published, those pages may
not yet describe the local unreleased implementation. No Actions or Pages
deployment is required to retain these records.
