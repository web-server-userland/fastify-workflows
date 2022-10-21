# @web-server-userland/fastify-workflows

This is the github workflows for the fastify plugin community.

Inspired by: [fastify/workflows](https://github.com/fastify/workflows)

## Usage

A reusable workflow is called by using the uses keyword in another workflow:

```yml
name: CI

on:
  push:
    paths-ignore:
      - 'docs/**'
      - '*.md'
  pull_request:
    paths-ignore:
      - 'docs/**'
      - '*.md'

jobs:
  npm:
    uses: web-server-userland/fastify-workflows/.github/workflows/plugin-ci-npm.yml@v2
    with:
      lint: true

  yarn:
    uses: web-server-userland/fastify-workflows/.github/workflows/plugin-ci-yarn.yml@v2

  pnpm:
    uses: web-server-userland/fastify-workflows/.github/workflows/plugin-ci-pnpm.yml@v2
```

### Inputs

#### npm

| Input Name          | Required | Type    | Default                        | Description                                                              |
| ------------------- | -------- | ------- | ------------------------------ | ------------------------------------------------------------------------ |
| `lint`              | false    | boolean | `false`                        | Set to `true` to run the `lint` script in a repository's `package.json`. |
| `lint-node-version` | false    | string  | `16`                           | Version of node to install for lint script.                              |
| `lint-script`       | false    | string  | `npm run lint`                 | npm run lint script.                                                     |
| `install-script`    | false    | string  | `npm install --ignore-scripts` | npm run install script.                                                  |
| `test-script`       | false    | string  | `npm run test:ci`              | npm run test script.                                                     |
| `coveralls`         | false    | boolean | `false`                        | enable coveralls.                                                        |

#### yarn

| Input Name          | Required | Type    | Default                                           | Description                                                              |
| ------------------- | -------- | ------- | ------------------------------------------------- | ------------------------------------------------------------------------ |
| `lint`              | false    | boolean | `false`                                           | Set to `true` to run the `lint` script in a repository's `package.json`. |
| `lint-node-version` | false    | string  | `16`                                              | Version of node to install for lint script.                              |
| `lint-script`       | false    | string  | `yarn run lint`                                   | Yarn run lint script.                                                    |
| `install-script`    | false    | string  | `yarn install --ignore-scripts --frozen-lockfile` | Yarn run install script.                                                 |
| `test-script`       | false    | string  | `yarn run test:ci`                                | Yarn run test script.                                                    |
| `coveralls`         | false    | boolean | `false`                                           | enable coveralls.                                                        |

#### pnpm

| Input Name          | Required | Type    | Default                         | Description                                                              |
| ------------------- | -------- | ------- | ------------------------------- | ------------------------------------------------------------------------ |
| `lint`              | false    | boolean | `false`                         | set to `true` to run the `lint` script in a repository's `package.json`. |
| `lint-node-version` | false    | string  | `16`                            | version of node to install for lint script.                              |
| `lint-script`       | false    | string  | `pnpm run lint`                 | pnpm run lint script.                                                    |
| `install-script`    | false    | string  | `pnpm install --ignore-scripts` | pnpm run install script.                                                 |
| `test-script`       | false    | string  | `pnpm run test:ci`              | pnpm run test script.                                                    |
| `coveralls`         | false    | string  | `false`                         | enable coveralls.                                                        |
| `pnpm-version`      | false    | boolean | `7.4.0`                         | install pnpm version.                                                    |
