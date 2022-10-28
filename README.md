# nx-14.6.0-ignores-package.json-config

A repo for simulating https://github.com/nrwl/nx/issues/12735

This contains 2 sub packages with:

* Package `a` which depends on package `b` and has a `test` script which depends in its `build` script which depends on the `build` script of its dependencies.
* Package `b` which has a `test` script which depends on its `build` script.

As of nx `14.5.10`, running `npm run test` will execute all scripts.

Upgrading to nx `14.6.0` suddenly causes the `nx` configurations in the `package.json`'s to appear to be ignored given the `build` scripts are not executed anymore.

## Steps to Replicate The Issue

1. Run `npm ci && npm run test` as is and see that `Running target test for 2 project(s) and 2 task(s) they depend on` is printed along with the mock scripts for those tasks.
2. Run `npm install nx@14.6.0 && npm run test` and see `Running target test for 2 project(s)` is printed with no `build` scripts executed.
