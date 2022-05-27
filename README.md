# Poetry CodeArtifact publish Action

Publishing Python packages to [AWS CodeArtifact](https://aws.amazon.com/codeartifact/) using Poetry was never so easy!

Usage:

```yaml
name: publish-my-package

on:
  pull_request:
    types: [closed]
    branches:
      - main

jobs:
  publish:
    if: github.event.pull_request.merged
    runs-on: ubuntu-latest
    steps:
      - name: Publish
        uses: source-ag/poetry-codeartifact-publish-action@v1
        with:
          aws-access-key-id: ${{ secrets.AWS_ACCESS_KEY_ID }}
          aws-secret-access-key: ${{ secrets.AWS_SECRET_ACCESS_KEY }}
          aws-region: eu-central-1
          role-to-assume: ${{ secrets.PACKAGE_REPOSITORY_ROLE }}
          codeartifact-domain: my-domain
          codeartifact-domain-owner: 123456789012
          codeartifact-repository: my-python-packages
```
