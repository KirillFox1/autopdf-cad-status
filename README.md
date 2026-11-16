# AutoPDF CAD status

Public read-only availability policies for AutoPDF CAD.

`main/status.txt` is retired and disabled for versions 0.7.2–0.8.1.
The current v0.8.2 policy is on branch `release-0.8.2`. Do not re-enable
`main` when enabling the current release. Version 0.7.1 uses a separate,
retired Sites service. Versions up to 0.7.0 have no remote check.

AutoPDF v0.8.1 reads the public Atom history of `main/status.txt`, validates
its repository and latest SHA, then reads the immutable `github.com` commit diff.
It reconstructs the complete three-line policy and checks its Git blob hash.
Both requests stay on `github.com`; Raw hosting is not required.
Older clients read the same file through their previous route.
The file contains only the product identifier, state and a positive revision.

Only the repository owner and explicitly authorized writers can change it.
To change current release access, edit its own branch's status file and
increment `revision`. Keep retired channels disabled unless the owner
explicitly requests restoring those versions.

No device identifiers, drawing data, credentials or administrative API are stored
here. Client network or policy errors deny access. The plugin requests a fresh
URL and caches successful checks for at most ten seconds; GitHub propagation
may add a delay. Existing AutoPDF v0.7.1 uses a separate legacy status service.
