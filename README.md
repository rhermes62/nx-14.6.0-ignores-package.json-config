# nx-14.6.0-ignores-package.json-config

A repo for simulating https://github.com/nrwl/nx/issues/12735

This contains 2 sub packages with `a` depending on `b` with an `nx` configuration that has the `test` script depend on

## Steps to Replicate The Issue

1. Run `npm ci && npm run test` as is and see that `Running target test for 2 project(s) and 2 task(s) they depend on` is printed along with the mock scripts for those tasks.
2. Run `npm install nx@14.6.0 && npm run test` and see `Running target test for 2 project(s)` is printed with no `build` scripts executed instead of `Running target test for 2 project(s) and 2 task(s) they depend on`.
