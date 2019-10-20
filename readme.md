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