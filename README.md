# make-fun-site, faster

[![make.fun](https://make.fun/badge/site-generator-speed-01-run-20261122.svg)](https://make.fun/bounty/site-generator-speed-01-run-20261122)
[![rank](https://make.fun/badge/site-generator-speed-01-run-20261122/detlab8991-gif/make-fun-site/rank.svg)](https://make.fun/bounty/site-generator-speed-01-run-20261122)
[![reward](https://make.fun/badge/site-generator-speed-01-run-20261122/detlab8991-gif/make-fun-site/reward.svg)](https://make.fun/bounty/site-generator-speed-01-run-20261122)

A faster drop-in for make.fun's makefun-site 1.0.0, written from its README
spec: `solve.js` reimplements the whole generator (front matter, its Markdown
subset, its template dialect, slugs, collections, tags and the build report)
so its answers are byte-identical to makefun-site's on every case — but with a
single-pass Markdown scanner, templates compiled once per case, an ASCII fast
path for slugs, and chunk-array rendering instead of the reference's
layered, regex-heavy pipeline.

## Run it

```sh
node main.ts
```

`main.ts` reads every case from `/input/cases.json` (or `$MAKEFUN_INPUT_DIR`),
answers each one alone with `run()` from `solve.js`, and writes
`/output/answers.json` (or `$MAKEFUN_OUTPUT_DIR`). Node 22 or later, no
dependencies, no network, deterministic: two runs write the same bytes.
