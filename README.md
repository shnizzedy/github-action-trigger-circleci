# Trigger CircleCI Job

Fork of [zivkaziv/circleci-trigger-github-action](https://github.com/zivkaziv/circleci-trigger-github-action).

[GitHub Action](https://github.com/features/actions) for triggering CircleCI job

This can be useful when you want to migrate from CircleCI into Github actions and you want to do it step by step (e.g. run the first job in GitHub actions and then trigger the second job).

## Inputs

- `token`: is a [personal API token](https://circleci.com/docs/2.0/managing-api-tokens/#creating-a-personal-api-token)
- `org`: variable that refers to the name of your CircleCI organization (default: `Current repo organization`)
- `repo`: variable that refers to the name of your repository (default: `Current repo`)
- `branch`: variable that refers to the name of your branch (default: `Current Branch`)
- `job`: variable that refers to the name of the CircleCI job

## Usage Example

```yaml
name: Trigger CircleCi job

on:
  push:
      branches:
        - master

jobs:
  build:
    runs-on: ubuntu-latest

    steps:
      - uses: actions/checkout@master

      - name: Trigger exiting circleci job
        uses: simonhkswan/circleci-trigger-github-action
        with:
          token: ${{ secrets.CIRCLE_CI_TOKEN }}
          branch: master
          job: build-and-deploy
```

## License

Scripts and documentation in this project are released under the [MIT license](LICENSE).

