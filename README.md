# docker-building-on-ci

Example project for the CircleCI blog tutorial [Using CircleCI workflows to replicate Docker Hub automated builds](https://circleci.com/blog/using-circleci-workflows-to-replicate-docker-hub-automated-builds/).

The workflow in [`.circleci/config.yml`](.circleci/config.yml):

- builds the image from the [`Dockerfile`](Dockerfile) on every branch push
- on `main`, pushes it to Docker Hub as `latest` and `0.0.<CIRCLE_BUILD_NUM>`
- on Git tags that start with `v` (for example `v1.2.3`), pushes it as `latest` and `1.2.3`

## Setup

Add two environment variables to the CircleCI project (**Project Settings** > **Environment Variables**):

| Name | Value |
| --- | --- |
| `DOCKERHUB_USERNAME` | Docker Hub username, or the organization name when using an organization access token |
| `DOCKERHUB_TOKEN` | Docker Hub personal access token with the **Repo Read & Write** permission |

Images are pushed to `$DOCKERHUB_USERNAME/building-on-ci`.
