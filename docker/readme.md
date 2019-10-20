# workflow 執行條件

1. 只有當 `docker/*` 與 `myWorkflow_Docker.yml` 有變更，才會執行 workflow

```
on: 
  push:
    branches:
      - master
    paths:
      - 'docker/*'
      - '.github/workflows/myWorkflow_Docker.yml'
```

# jobs 流程

1. 設定 action.yml 腳本
2. 透過 `uses` tag 使用 action 腳本, 帶入環境參數 `who-to-greet` 給 container
    - https://help.github.com/en/articles/virtual-environments-for-github-actions#creating-and-using-secrets-encrypted-variables
    - Secrets variables 限制
        - 每個 workflow 有上限 100 個 secrets 的設定
        - 每個 secret name 在 repo 必須是唯一名稱
        - secret 的 size 限制在 64KB 以內
        - 超過 64kb 請參考相關做法 (you can store encrypted secrets in your repository and save the decryption passphrase as a secret on GitHub.)
3. 輸出 `action.yml->outputs`