# rate
Based on vue elementUI-rate component

## gh-pages steps

 ``` bash

    git init // 初始化

    git checkout --orphan gh-pages // 创建gh-pages分支

    git add .  // 添加所有文件到暂存区         git add text #缓存(某个文件夹或具体文件名）

    git commit -m 'first pages commit'  // 添加信息

    git remote add origin https://github.com/fen666/vueCli_gh-pages.git  // 添加仓库

    git subtree push --prefix=gh-pages origin gh-pages  // 指定的gh-pages文件部署到gh-pages分支上

```
