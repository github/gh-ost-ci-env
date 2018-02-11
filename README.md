# gh-ost-ci-env

CI environment for `gh-ost` testing.

This repository serves as a collateral repo to [gh-ost](https://github.com/github/gh-ost), GitHub's schema migration tool. It provides a multi-version testing environment that can be used by `gh-ost`'s CI, without polluting `gh-ost`'s repo.

Since `gh-ost` uses public [Travis CI](https://travis-ci.org/), we confine ourselves to a single docker image, created at each CI. To that effect we wish to be able to quickly bootstrap multiple MySQL master-replica environments.

We choose [dbdeployer](https://github.com/datacharmer/dbdeployer), a tool that deploys MySQL replication clusters in user space, created by @datacharmer.

This repository incorporates:

- `dbdeployer` binary
- Various MySQL minimal tarballs

### Usage

`gh-ost` CI will use this repo as follows:

- Clone it from within the Docker image
- Deploy and boostrap MySQL master-replica environments
- Run `gh-ost` integration tests on each master-replica environment
