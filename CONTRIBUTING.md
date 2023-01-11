# Contributing to the tektoncd-catalog Github Organization

Thank you for your interest in contributing!

This doc is about how to contribute to the Tekton Verified Catalogs. For how to 
contribute to each of the Verified Catalog, please see the individual `CONTRIBUTING.md` files in the respective repository. 
Please also see [the Tekton Community README](https://github.com/tektoncd/community/blob/main/README.md) for guidelines to contribute to tektoncd projects in general.

**All contributors must comply with
[the code of conduct](./code-of-conduct.md).**

PRs are welcome, and will follow
[the tektoncd pull request process](https://github.com/tektoncd/community/blob/main/process.md#pull-request-process).

## How to Contribute a new Verified Catalog

The `tektoncd-catalog` org is intended to serve as a location to host the [`Tekton Verified Catalogs`](https://github.com/tektoncd/community/blob/main/teps/0115-tekton-catalog-git-based-versioning.md#tekton-catalog-github-organization), following the new [decentralized
catalog contract](https://github.com/tektoncd/community/blob/main/teps/0115-tekton-catalog-git-based-versioning.md#organization-contract) and the new [git-based versioning](https://github.com/tektoncd/community/blob/main/teps/0115-tekton-catalog-git-based-versioning.md#versioning-in-a-catalog). The `Verified Catalogs` hosted under this org are selected based on the usefulness of the resource and the bandwidth of tektoncd catalog maintainers. 

The addition of new catalogs in this org should be an exception, not the norm. Please see the `community catalog migration guide` doc (TODO) to create and publish your own catalog. However, if you see a strong reason to promote a catalog from the `community` to the `verified` support tier, please feel free to create an issue and the tektoncd catalog maintainers will start the investigation.

Please see more information in the [Ownership & Maintaienance](https://github.com/tektoncd/community/blob/main/teps/0079-tekton-catalog-support-tiers.md#ownership-and-maintenance-1) section of TEP-0079.

## How to Contribute an existing Verified Catalog

Pull requests to the `main` branch (the development branch) are welcomed to improve the existing Verified Catalogs. Please follow the below [guidelines](#guidelines) when proposing changes in the catalog. The version/release creation privilege is only granted to the tektoncd catalog maintainers. The maintainers will `sign` the resources and create new releases in separate branches when necessary. The changes will be included in the next release of the Verified Catalog after the pull request is merged.

The `Trusted Resource` feature is integrated to all the Verified Catalogs, please see integration details and release strategy in [Verified Remote Resources](https://github.com/tektoncd/community/blob/main/teps/0079-tekton-catalog-support-tiers.md#verified-remote-resources-1) section of TEP-0079.

### Guidelines

When reviewing PRs that add or update `Task`s or `Pipeline`s, maintainers will follow
the following guidelines:

* Submissions should be useful in real-world applications.
While this org is meant to be educational, its primary goal is to serve
as a place of useful and high-quality resources that are owned by tektoncd catalog maintainers.
This is **not** a samples repo to showcase Tekton features.
* Submissions should follow established [authoring recommendations](./recommendations.md)
* Submissions should be well-documented.
* Submissions should be testable, and come with the required tests.

If you have an idea for a new submission, feel free to open an issue to discuss
the idea with the catalog maintainers and community.
Once you are ready to write your submission, please open a PR with the code,
documentation and tests and a maintainer will review it.

### Technical requirements

* Must pass the Task validation (aka `kubectl create -f task.yaml`
  should succeed)
* Images should be published and maintained on an public image
  registry (gcr.io, docker.io, quay.io, …). A bonus if those images are
  auto-built.
* Images should not have any major security vulnerabilities
* Should follow Kubernetes best practices
* Provide as many default parameter values as possible
* Provide [Automated Testing](#automated-testing)
* Provide versions without `PipelineResource`

### Automated Testing

There are two types of automated tests set up in the Verified Catalog CI: build tests and integration(e2e) tests.

#### Build Test

The build tests check the syntax of the yaml files and the contract of the Catalog. The successful completion of the build test pass `pull-tekton-catalog-build-tests` GitHub check to unblock a PR merge.

The build tests leverage [Catlin](https://github.com/tektoncd/catlin) as the linting tool to validate Tekton Resources and Catalogs:
  - If the resource is on a valid path
  - If the resource is a valid Tekton Resource
  - If all mandatory fields are added to the resource file
  - If all images used in Task Spec are tagged
  - If platforms are specified in a correct format

Please see details in [Automated Testing and Dogfooding](https://github.com/tektoncd/community/blob/main/teps/0079-tekton-catalog-support-tiers.md#automated-testing-and-dogfooding-1) section of TEP-0079


#### Integration Test (E2E Test)

The integration tests SHOULD run the catalog resource from end to end. The successful completion of the integration test passes `pull-tekton-catalog-integration-tests` GitHub check to unblock a PR merge (TODO: update this section after https://github.com/tektoncd/community/pull/914 is merged).  

There are two types of e2e tests launched on CI.

The first one would just apply the yaml files making sure they don't have any
syntax issues. Pretty simple one, it just basically checks the syntax.

The second one would do some proper functional testing, making sure the task
actually **ran** properly.

A helper script called `run-test.sh` is provided in the `test` directory of each repo to help the developer run the test locally. Just specify the task name  i.e:

```yaml
./test/run-test.sh git-clone
```

and it will use your current Kubernetes context to run the test and show you the outputs similar to the CI.

Please see details in [Automated Testing and Dogfooding](https://github.com/tektoncd/community/blob/main/teps/0079-tekton-catalog-support-tiers.md#automated-testing-and-dogfooding-1) section of TEP-0079

*This org only contains testing infra needed for Verified Catalogs. Please check the [contributing](https://github.com/tektoncd/catalog/blob/main/CONTRIBUTING.md#end-to-end-testing) doc of the legacy [centralized catalog repo](https://github.com/tektoncd/catalog/) to find more test infra that we provided earlier*

### Owning and Maintaining a Verified Catalog

Please see details in [TEP-0079](https://github.com/tektoncd/community/blob/main/teps/0079-tekton-catalog-support-tiers.md#ownership-and-maintenance-1) for requirements and responsibilities of owning and maintaining a catalog.

## OWNERS

The top-level `OWNERS` file of each Verified Catalog repo lists the `Owners` and `Collaborators` of the catalog. The process to becoming an `Owner` or `Collaborator` is the same as other Tekton project [process](https://github.com/tektoncd/community/blob/main/process.md#owners).
