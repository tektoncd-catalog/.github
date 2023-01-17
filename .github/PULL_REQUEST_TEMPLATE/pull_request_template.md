<!-- 🎉🎉🎉 Thank you for the PR!!! 🎉🎉🎉 -->

# Changes

<!-- Describe your changes here- ideally you can get that description straight from
your descriptive commit message(s)! -->

# Submitter Checklist

These are the criteria that every PR should meet, please check them off as you
review them:

- [ ] Follows the [authoring recommendations](../../recommendations.md)
- [ ] Includes [docs][docs] (if user facing)
- [ ] Includes [tests][tests] (for new tasks or changed functionality)
  - See the [automated testing documentation][e2e] for guidance and CI details.
- [ ] Meets the [Tekton contributor standards][contributor] (including functionality, content, code)
- [ ] Commit messages follow [commit message best practices][commit]
- [ ] Has a kind label. You can add one by adding a comment on this PR that
  contains `/kind <type>`. Valid types are bug, cleanup, design, documentation,
  feature, flake, misc, question, tep
- [ ] Complies with [Catalog Organization TEP][TEP], see [example]. **Note** [An issue has been filed to automate this validation][validation]
  - [ ] File path follows  `<kind>/<name>/name.yaml`
  - [ ] Has `README.md` at `<kind>/<name>/README.md`
  - [ ] Has mandatory `metadata.labels` - `app.kubernetes.io/version` the same as the `<version>` of the resource
    - The `<version>` should follow semantic versioning strategy (e.g. `<major>.<minor>.<patch>`)
  - [ ] Has mandatory `metadata.annotations` `tekton.dev/pipelines.minVersion`
  - [ ] mandatory `spec.description` follows the convention

          ```

          spec:
            description: >-
              one line summary of the resource

              Paragraph(s) to describe the resource.
          ```

_See [the contribution guide][catalog-contributor] for more details._

[TEP]: https://github.com/tektoncd/community/blob/master/teps/0003-tekton-catalog-organization.md
[example]: https://github.com/tektoncd-catalog/golang
[validation]: https://github.com/tektoncd/catalog/issues/413
[authoring]: https://github.com/tektoncd/catalog/blob/main/recommendations.md
[docs]: https://github.com/tektoncd/community/blob/master/standards.md#docs
[tests]: https://github.com/tektoncd/community/blob/master/standards.md#tests
[e2e]: ../../CONTRIBUTING.md#automated-testing
[contributor]: https://github.com/tektoncd/community/blob/main/standards.md
[commit]: https://github.com/tektoncd/community/blob/master/standards.md#commits
[catalog-contributor]: ../../CONTRIBUTING.md