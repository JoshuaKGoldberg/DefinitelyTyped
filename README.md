# Definitely Typed Performance Repro

Reproduction case for ESLint JSDoc performance.

## Setup

```shell
npm i
```

## Run

You can measure linting performance on a subset of DefinitelyTyped's files with globs:

```shell
hyperfine "npx eslint \"types/a*/**/index.d.ts\"\" --ignore-failure
```

The following measurements were taken on an M2 Macbook Air.

### Baseline

```plaintext
$ hyperfine "npx eslint \"types/a*/**/index.d.ts\"" --ignore-failure
Benchmark 1: npx eslint "types/a*/**/index.d.ts"
  Time (mean ± σ):     16.315 s ±  0.543 s    [User: 20.721 s, System: 1.039 s]
  Range (min … max):   14.904 s … 16.889 s    10 runs
```

### With Caching

Apply the proposed changes to the `search` function to see changed results.

```plaintext
$ hyperfine "npx eslint \"types/a*/**/index.d.ts\"" --ignore-failure
Benchmark 1: npx eslint "types/a*/**/index.d.ts"
  Time (mean ± σ):      7.291 s ±  0.191 s    [User: 10.928 s, System: 0.875 s]
  Range (min … max):    7.094 s …  7.684 s    10 runs
```
