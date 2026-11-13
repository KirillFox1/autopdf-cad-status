# AutoPDF CAD status

Public read-only availability policy for AutoPDF CAD v0.7.2 and later.

`status.txt` is fetched over HTTPS by the plugin. It contains only the product
identifier, enabled/disabled state and a positive integer revision.

Only the repository owner and explicitly authorized writers can change it.
To disable access, change `state=enabled` to `state=disabled` and increment
`revision`. To restore access, change it back and increment `revision` again.

No device identifiers, drawing data, credentials or administrative API are stored
here. Client network or policy errors deny access. The plugin requests a fresh
URL and caches successful checks for at most ten seconds; GitHub propagation
may add a delay. Existing AutoPDF v0.7.1 uses a separate legacy status service.
