# action-site-install
github action to install drupal site in CI to validate config

# implementation

```name: Test Install Drupal Site

permissions:
  id-token: write
  contents: read

on:
  pull_request:
    branches:
      - main
    types:
      - opened
      - synchronize
  workflow_dispatch: {}

jobs:
  install:
    runs-on: ubuntu-latest

    steps:
      - name: Install Drupal Site
        uses: discoverygarden/action-site-install@v1
        with:
          aws-role: ${{ vars.ECR_PUSH_ROLE }}
          aws-region: ${{ vars.ECR_AWS_REGION }}
          ssh-key: ${{ secrets.COMPOSER_SSH_KEY }}
          composer-auth: ${{ secrets.COMPOSER_AUTH }}
```
