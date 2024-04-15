# Github Actions Bundler Audit with Reviewdog 🐶

Implementation of [bundler-audit](https://github.com/rubysec/bundler-audit) with
[reviewdog](https://github.com/reviewdog/reviewdog) on pull requests to improve security review experience.

## ⚙️ <ins>Inputs</ins>

- `github_token`
    * Github Token.
    * Optional
    * Default value is `github.GITHUB_TOKEN`

- `level`
    * Report level for reviewdog, options are info, warning, error.
    * Optional
    * Default value is `error`

- `reporter`
    * Reporter of reviewdog command, options are `github-pr-check, github-check, github-pr-review, github-pr-annotations`
    * Optional
    * Default value is `github-pr-review`

- `filter_mode`
    * Filtering mode for the reviewdog command, options are `added, diff_context, file, nofilter`
    * Optional
    * Default value is `added`

- `fail_on_error`
    * Exit code for reviewdog when errors are found, options are `true, false`
    * Optional
    * Default value is `false`

## 👀 <ins>Example Usage</ins>
```yaml
name: "Ruby on Rails CI"
on: [ pull_request ]

jobs:
  lint:
    runs-on: ubuntu-latest
    steps:
      - name: Checkout code
        uses: actions/checkout@v3
      - name: Install Ruby and gems
        uses: ruby/setup-ruby@87ccb7599f56623090bd4a1c8ece2c4091856de3 # v1.92
      # Add or replace any other lints here
      - name: bundler_audit
        uses: buck-ai/github-actions-bundler-audit-with-reviewdog@v0.1.6
        with:
          reporter: github-pr-review
          github_token: ${{secrets.GITHUB_TOKEN}}
```
