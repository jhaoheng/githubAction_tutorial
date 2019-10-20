# Badge set

- Format is : `[![Actions Status](https://github.com/{owner}/{repo}/workflows/{workflow_name}/badge.svg)](https://github.com/{owner}/{repo}/actions)`

## for example

> 根據 ./github/workflows/...yml

[![Actions Status](https://github.com/jhaoheng/githubAction_training/workflows/bash/badge.svg)](https://github.com/jhaoheng/githubAction_training/actions)

[![Actions Status](https://github.com/jhaoheng/githubAction_training/workflows/golang/badge.svg)](https://github.com/jhaoheng/githubAction_training/actions)

[![Actions Status](https://github.com/jhaoheng/githubAction_training/workflows/docker/badge.svg)](https://github.com/jhaoheng/githubAction_training/actions)

[![Actions Status](https://github.com/jhaoheng/githubAction_training/workflows/coverage/badge.svg)](https://github.com/jhaoheng/githubAction_training/actions)

# Workflow syntax for GitHub Actions
> https://help.github.com/en/articles/workflow-syntax-for-github-actions#jobsjob_idsteps

# Metadata syntax for GitHub Actions
> https://help.github.com/en/articles/metadata-syntax-for-github-actions

# 取得 repo source code

- 在 github action 的 virtual machine 中, 是空的 instance, 需要透過 git 下載 source code
- 可以使用已經建立好的 action 透過 checkout 來獲取 repo 的 source code
    - https://github.com/actions/checkout

```
- name: Check out code into the Go module directory
    uses: actions/checkout@v1
```

# 關於建立自己的 action 與 如何參考 action

## [about Action](https://help.github.com/en/articles/about-actions#types-of-actions)

## [Referencing actions in your workflow](https://help.github.com/en/articles/configuring-a-workflow#referencing-actions-in-your-workflow)

- 建議在 repo 的設計結構如下

```
|-- hello-world (repository)
|   |__ .github
|       └── workflows
|           └── my-first-workflow.yml
|       └── actions
|           |__ hello-world-action
|               └── action.yml
```

```
jobs:
  build:
    runs-on: ubuntu-latest
    steps:
      # This step checks out a copy of your repository.
      - uses: actions/checkout@v1
      # This step references the directory that contains the action.
      - uses: ./.github/actions/hello-world-action
```

## [Referencing a container on Docker Hub](https://help.github.com/en/articles/configuring-a-workflow#referencing-a-container-on-docker-hub)

> 關鍵字 : `docker://{image}:{tag}`

```
jobs:
  my_first_job:
    steps:
      - name: My first step
        uses: docker://alpine:3.8
```