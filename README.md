# QUality EVEnt Engine (quevee) github action

This action accepts a set of input URLs pointing to release artifacts of various categories (like 'documentation' or 'testing'), and creates a toml file that contains project and release metadata as well as the artifact URLs. The goal is to document release artifacts that are relevant for assessment of project quality aspects, and present them for evaluation and archival in quality assessment processes.

## Inputs

### `release_url`

URL of the release this manifest refers to.

### `artifacts_documentation`

Comma-separated list of URLs of documentation artifacts.

### `artifacts_readme`

Comma-separated list of URLs of readme files.

### `artifacts_requirements`

Comma-separated list of URLs of requirement files.

### `artifacts_testing`

Comma-separated list of URLs of test results.

## Outputs

### `manifest_file`

Process artifacts manifest file name.

## Example usage

__Note__: github action variables contain URLs generated by previous steps like 'create release' or 'upload file to release'.

```yaml
- name: Collect quality artifacts
  uses: actions/quevee@v1
  id: quevee
  with:
    release_url: ${{ steps.create_release.outputs.url }}
    artifacts_readme: ${{ steps.upload_readme.outputs.browser_download_url }}
    artifacts_requirements: ${{ steps.upload_license.outputs.browser_download_url }},https://yet.another.org/example/artifact.bz2
```