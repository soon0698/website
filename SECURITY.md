# Static site security

This repository publishes a static GitHub Pages site. It contains no PHP server,
login endpoint, application database, or JavaScript dependency runtime.

The page denies script execution, network API connections, embedded objects, base
URL changes, and form submissions through a meta Content Security Policy. Styles
are served from the local stylesheet. Google-hosted Lato fonts remain explicitly
allowed. Publication previews use CSS instead of inline scripts or event handlers.

The deployment workflow pins actions to commit IDs, disables persisted checkout
credentials, and uploads an explicit public file list. Do not put credentials or
private documents in `data/` or `material/`: those directories are public.

GitHub Pages serves HTTPS with HSTS. HTTP-response-only protections such as CSP
`frame-ancestors`, `X-Content-Type-Options`, and `Permissions-Policy` are not added
by this repository's HTML. An edge proxy or hosting configuration capable of
setting response headers is needed to implement those controls. A meta tag must
not be treated as a substitute for `frame-ancestors`.

No claim of complete immunity is made; account access and domain/DNS security
also need to be maintained by their owners.
