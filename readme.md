# workflows badge

[![Actions Status](https://github.com/jhaoheng/githubAction_training/workflows/bash/badge.svg)](https://github.com/jhaoheng/githubAction_training/actions)

[![Actions Status](https://github.com/jhaoheng/githubAction_training/workflows/golang/badge.svg)](https://github.com/jhaoheng/githubAction_training/actions)

[![Actions Status](https://github.com/jhaoheng/githubAction_training/workflows/docker/badge.svg)](https://github.com/jhaoheng/githubAction_training/actions)

[![Actions Status](https://github.com/jhaoheng/githubAction_training/workflows/coverage/badge.svg)](https://github.com/jhaoheng/githubAction_training/actions)

# operation flow

event trigger -> virtual machine -> clone source code -> do something

## 取得 repo source code

- 在 github action 的 virtual machine 中, 是空的 instance, 需要透過 git 下載 source code
- 可以使用已經建立好的 action 透過 checkout 來獲取 repo 的 source code
    - https://github.com/actions/checkout

```
- name: Check out code into the Go module directory
    uses: actions/checkout@v1
```

# folder 結構

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


# Q
- [所有標籤使用方法](https://docs.github.com/en/actions/reference/workflow-syntax-for-github-actions)

- [如何使用別人的 action](https://docs.github.com/en/actions/configuring-and-managing-workflows/configuring-a-workflow#referencing-actions-in-your-workflow)

- [推送時, 如何忽略某過 file 的變更, 不執行 action](https://help.github.com/en/articles/workflow-syntax-for-github-actions#onpushpull_requestpaths)

- [推送時, 忽略 branch or tag (release) 的迭代, 不執行 action](https://help.github.com/en/articles/workflow-syntax-for-github-actions#example-ignoring-branches-and-tags)

- [如何使用 secret 參數? action 執行時, 隱藏敏感性資料](https://help.github.com/en/articles/virtual-environments-for-github-actions#creating-and-using-secrets-encrypted-variables)

- [如何建立自己的 actions](https://docs.github.com/en/actions/creating-actions)
  - [You can build Docker container and JavaScript actions](https://help.github.com/en/articles/about-actions#types-of-actions)
	- [action yaml 的 metadata](https://docs.github.com/en/actions/creating-actions/metadata-syntax-for-github-actions)

- [如何使用 slack action](https://github.com/marketplace/actions/action-slack)

- [如何建立 badge?](https://docs.github.com/en/actions/configuring-and-managing-workflows/configuring-a-workflow#adding-a-workflow-status-badge-to-your-repository)
	- format : `[![Actions Status](https://github.com/{owner}/{repo}/workflows/{workflow_name}/badge.svg)](https://github.com/{owner}/{repo}/actions)`

- [如何在 step 中使用 docker](https://docs.github.com/en/actions/configuring-and-managing-workflows/configuring-a-workflow#referencing-a-container-on-docker-hub)

