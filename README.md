# bun-build-segfault

bun segfaults trying to generate a standalone binary when [binaryen](https://www.npmjs.com/package/binaryen) is imported:

`bun build index.ts --compile --outfile out`

<br />
This seems to be because binaryen has a bunch of expressions chained using `,`. This can be tested by running:

`bun build mini-repro.js --compile --outfile out`

<br />
However, if we just take out one of the expressions and try building again, it builds without segfaulting:

`bun build mini-repro2.js --compile --outfile out`
