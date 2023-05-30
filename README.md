# Hexo Deploy Action


这 [GitHub action](https://github.com/features/actions) 将处理 hexo 项目的构建和部署过程。

## 入门示例



```yml
name: Build and Deploy
on:
  push:
    branches:
      - main
jobs:
  build-and-deploy:
    runs-on: ubuntu-latest
    steps:
    - name: Checkout
      uses: actions/checkout@master

    - name: Build and Deploy
      uses: cyolc932/hexo-deploy-action@master
      env:
        PERSONAL_TOKEN: ${{ secrets.CI_TOKEN }}
        PUBLISH_REPOSITORY: 用户名/用户名.github.io # 目标存储库 
        BRANCH: gh-pages  # 目标仓库的分支 
        PUBLISH_DIR: ./public # 应该部署的文件夹中 
```


## 配置

工作流程的 `env` 部分**必须**在操作生效之前进行配置。  您可以将这些添加到上面示例中的“env”部分。  必须使用括号语法引用任何“秘密”，并将其存储在 GitHub 存储库的“设置/秘密”菜单中。  您可以了解有关使用 GitHub 操作设置环境变量的[更多信息](https://help.github.com/en/articles/workflow-syntax-for-github-actions#jobsjob_idstepsenv).

B下面是对每个选项的描述。

| Key  | Value Information | Type | Required |
| ------------- | ------------- | ------------- | ------------- |
| `PERSONAL_TOKEN`  | 根据存储库权限，您可能需要为该操作提供GitHub个人访问令牌才能进行部署。 [在这里了解更多关于如何生成的信息](https://help.github.com/en/articles/creating-a-personal-access-token-for-the-command-line). **这应该作为秘密存储**. | `secrets` | **Yes** |
| `PUBLISH_REPOSITORY`  | 操作应该部署到的存储库。例如 `用户名/用户名.github.io` | `env` | **Yes** |
| `BRANCH`  | 操作应该部署到的分支。例如 `master` | `env` | **Yes** |
| `PUBLISH_DIR`  | 操作应该部署的文件夹y. 例如 `./public`| `env` | **Yes** |

