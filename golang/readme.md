# workflow 執行條件

1. 只有當 `golang/*` 與 `myWorkflow_golang.yml` 有變更，才會執行 workflow

```
on: 
  push:
    branches:
      - master
    paths:
      - 'golang/*'
      - '.github/workflows/myWorkflow_golang.yml'
```

# jobs 流程

1. 設定 golang 版本
2. git fetch source code