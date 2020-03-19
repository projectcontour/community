# Contour Quality assessment

## Unit testing and Code Coverage

Unit testing is the primary mechanism for ensuring Contour code and product quality. Unit tests generally fall into two categories:
- Internal API package tests
- End-to-end feature tests.

Internal API package tests are typical unit tests that validate the API of internal code packages. End-to-end feature tests mock the complete internal workflow from receiving Kubernetes events to emitting Envoy configuration.

Total code coverage from the full test suite hovers around 78%, per [coverage metrics](https://codecov.io/gh/projectcontour/contour).

The internal API packages consist of around 75% of the codebase and have 86% code coverage. The area most lacking in unit test coverage (about 18%
coverage) is the command-line interfaces that are accessible from the `contour` CLI, which includes server setup and initialization, certificate generation and leader election. This area consists of approximately 10% of the codebase.

## Integration Testing

Integration testing ensures that Contour features work as expected in a real Kubernetes cluster, and program Envoy with working configurations.

As noted in the CI section, CI checks that Contour can be successfully installed into Kind clusters.

Contour has no automated integration tests. This is being worked on as a separate test harness. Additionally, when the Kubernetes SIG-NETWORK Ingress conformance tests are available, the Contour project will integrate them into the CI pipeline.

At release time, a collection of integration tests is performed manually as per [#2223](https://github.com/projectcontour/contour/issues/2223).

## Continuous Integration

The Contour project run checks on every PR to ensure that the master branch is always releasable.
[Travis](https://travis-ci.org/github/projectcontour/contour)
is the current CI host, but the project plans to migrate to a different provider in the near future as per [#2200](https://github.com/projectcontour/contour/issues/2200).

Contour runs 5 CI jobs:

1. Codegen. This job verifies that all generated files are up to date. Contour generates Go code for Kubernetes types, YAML for Kubernetes deployments, and documentation for metrics and Kubernetes APIs.

2. Unit Tests. The CI system runs all the unit tests as describes above, and posts the coverage data to [Codecov](https://codecov.io/gh/projectcontour/contour). The Codecov Github bot posts the coverage results of the code change to the PR so that contributers can see where to improve their tests.

3. Lint. This runs
[golangci-lint](https://github.com/golangci/golangci-lint) checks for Go coding style, YAML [lint](https://github.com/adrienverge/yamllint),
spell checking and custom checks for CLI argument help.

4. Site Proofing. This job runs
[htmlproofer](https://github.com/gjtorikian/html-proofer) to ensure HTML link consistency in the documentation and website.

5. Integration. This job could more accurately be called "install test". Builds Contour from the current PR branch, and installs it to a Kind cluster using the deployment YAML also taken from the current PR branch. This ensures that Contour is able to install, start and become healthy.

## Releasing

Contour aims to release point updates monthly. Now that the HTTPProxy API is marked "v1" and Contour's version is > 1.0, updates are not allowed to break compatibility with previous releases. You can learn more about the Contour release process [here](https://github.com/projectcontour/contour/blob/master/RELEASES.md).

The release process consists of a set of [documented](https://projectcontour.io/resources/release-process/) manual steps.

The main release artifact is a Docker image that is published to [DockerHub](https://hub.docker.com/r/projectcontour/contour).
Secondary release artifacts are
[versioned documentation](https://projectcontour.io/docs/v1.2.1/)
and unversioned example
[deployment YAML](https://projectcontour.io/quickstart/contour.yaml).

## Scale and Performance Testing

There are a number of scaling dimensions that are could be relevant to users of the Contour project. Operators need to care about both the control plane (Contour) and the data plane (Envoy).

The example deployment documented by the Contour project deploys Envoy as a daemonset. This may not be suitable to all operators or deployments.
In general, Envoy scaling and performance characteristics are not tested by the Contour project, which relies on the upstream Envoy community for this.

Scaling Contour itself can be measured in a number of dimensions:

    - number of configured ingresses
    - type of configured ingress (e.g. TLS, delegation)
    - number of relevant Kubernetes documents
    - rate of change (i.e. configuration throughput)
    - number of Envoy clients

Contour has been manually tested to handle low thousands of configured ingresses. Its primary scaling limit is the number of Kubernetes documents that it can retain in memory. In practice, this can a very high number.

The maximum rate of change is limited by Contour throttling the Envoy update rate to avoid driving Envoy out of memory with stale configurations.

To the best of my knowledge, Contour has not been tested by scaling the numbers of Envoy clients. Since Contour can be deployed in an active-active configuration, more Contour instances may be needed for large clusters that have a lot of Envoy processes.

You can find additional information on Envoy and Contour resource limits [here](https://projectcontour.io/guides/resource-limits/)

## Code size breakdown

The following table shows the breakdown of the code in the Contour repository, reported by [scc](https://github.com/boyter/scc).  This includes Contour itself, the documentation (multiple versioned copies), deployment YAML and tooling scripts.

```
───────────────────────────────────────────────────────────────────────────────
Language                 Files     Lines   Blanks  Comments     Code Complexity
───────────────────────────────────────────────────────────────────────────────
Markdown                   163     26297     5535         0    20762          0
Go (including tests)       136     50842     3325      3997    43520       1719
Go (excluding tests)        75     13324     1603      2523     9198       1398
Sass                       103      7927     1288      1080     5559         36
YAML                       100     16920      108       414    16398          0
HTML                        27      7276       31        24     7221          0
Shell                        8       385       89        57      239         17
SVG                          7       542        0         6      536          0
JavaScript                   3       496       83        93      320         67
Smarty Template              3       157       18         0      139         13
BASH                         2        41        9         4       28          2
Ruby                         2       155       27        16      112         10
Docker ignore                1         7        0         0        7          0
Dockerfile                   1        14        3         0       11          0
Gemfile                      1        15        1         0       14          0
Go Template                  1        15        3         0       12          0
JSON                         1        28        0         0       28          0
License                      1       201       32         0      169          0
Makefile                     1       258       44        15      199          9
TOML                         1        18        1         3       14          0
gitignore                    1        27        1         2       24          0
───────────────────────────────────────────────────────────────────────────────
Total                      563    111621    10598      5711    95312       1873
───────────────────────────────────────────────────────────────────────────────
```

