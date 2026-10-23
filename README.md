# Legacy GitHub Pages redirects

This repository serves browser redirects from `greenoso.github.io` to the current
websites under `jiachengliu12345.github.io`.

## Published paths

| Legacy path | Destination |
| --- | --- |
| `/` | <https://jiachengliu12345.github.io/> |
| `/NextGen-CAPTCHAs_webpage/` | <https://jiachengliu12345.github.io/NextGen-CAPTCHAs_webpage/> |
| `/world-models-survey/` | <https://jiachengliu12345.github.io/world-models-survey/> |

The inline script replaces the current browser history entry and preserves query
parameters and fragment identifiers. A meta refresh and a visible link provide
fallback navigation. GitHub Pages serves these as static HTML pages; the initial
HTTP response is not a server-side 301 redirect.

## Hosting

The owner must be the `Greenoso` organization, and the repository name must be
`greenoso.github.io`. Enable GitHub Pages with branch `main` and source folder `/`.
The `.nojekyll` file keeps publication static.

Keep the research source repositories under their current owners. Hosting these
pages in the organization site avoids creating duplicate project repositories
under the old owner name, which could replace existing repository redirects.
