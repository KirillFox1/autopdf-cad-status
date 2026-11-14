# AutoPDF CAD status

Public read-only availability policy for AutoPDF CAD v0.7.2 and later.

AutoPDF v0.8.1 reads the public Atom history of `main/status.txt`, validates
its repository and latest SHA, then reads the immutable `github.com` commit diff.
It reconstructs the complete three-line policy and checks its Git blob hash.
Both requests stay on `github.com`; Raw hosting is not required.
Older clients read the same file through their previous route.
The file contains only the product identifier, state and a positive revision.

Only the repository owner and explicitly authorized writers can change it.
To disable access, change `state=enabled` to `state=disabled` and increment
`revision`. To restore access, change it back and increment `revision` again.

No device identifiers, drawing data, credentials or administrative API are stored
here. Client network or policy errors deny access. The plugin requests a fresh
URL and caches successful checks for at most ten seconds; GitHub propagation
may add a delay. Existing AutoPDF v0.7.1 uses a separate legacy status service.
