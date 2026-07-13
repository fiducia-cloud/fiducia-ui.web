# workflows

GitHub Actions CI definitions for the fiducia-ui site.

- `ci.yml` — runs on pushes to `main`, PRs, and manual dispatch. Checks out this
  repo alongside its sibling `file:../` dependencies (`fiducia-interfaces`,
  `fiducia-test-config`) at explicit full commit SHAs so `npm ci` resolves a
  repeatable dependency graph, then runs the Node contract tests and the Astro
  production build as required gates. A bounded `browser-e2e` job runs the
  Playwright/Puppeteer suite with a real Chrome and uses the same immutable
  sibling pins; browser regressions fail CI.
