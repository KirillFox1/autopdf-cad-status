# AutoPDF CAD status

Public read-only availability policy for AutoPDF CAD v0.8.2.

This release uses its own `release-0.8.2` branch. Retired versions 0.7.2–0.8.1
use `main`, which must stay disabled when the current release is enabled.
Version 0.7.1 uses a separate retired Sites service. Versions up to 0.7.0
have no remote check and cannot be revoked through these policies.

AutoPDF v0.8.2 reads the public Atom history of `release-0.8.2/status.txt`, validates
its repository and latest SHA, then reads the immutable `github.com` commit diff.
It reconstructs the complete three-line policy and checks its Git blob hash.
Both requests stay on `github.com`; Raw hosting is not required.
Older clients remain bound to their retired channels; there is no fallback.
The file contains only the product identifier, state and a positive revision.

Only the repository owner and explicitly authorized writers can change it.
To disable access, change `state=enabled` to `state=disabled` and increment
`revision` on this release branch. To restore this release, change it back
and increment `revision` again. Do not re-enable the retired channels.

No device identifiers, drawing data, credentials or administrative API are stored
here. Client network or policy errors deny access. The plugin requests a fresh
URL and caches successful checks for at most ten seconds; GitHub propagation
may add a delay. Existing AutoPDF v0.7.1 uses a separate legacy status service.
