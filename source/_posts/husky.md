---
title: vue3+vite 项目配置 husky
date: 2023-11-13 11:53:03
---

前言

在上面我们已经集成好了我们代码校验工具，但是需要每次手动的去执行命令才会格式化我们的代码。如果有人没有格式化就提交了远程仓库中，那这个规范就没什么用。所以我们需要强制让开发人员按照代码规范来提交。

要做到这件事情，就需要利用 husky 在代码提交之前触发 git hook(git 在客户端的钩子)，然后执行 pnpm run format 来自动的格式化我们的代码。

4.1 安装 husky

```text
pnpm install -D husky
```

执行

```text
npx husky-init
```

会在根目录下生成个一个.husky 目录，在这个目录下面会有一个 pre-commit 文件，这个文件里面的命令在我们执行 commit 的时候就会执行。

在.husky/pre-commit 文件添加如下命令：

```cmd
#!/usr/bin/env sh
."$(dirname -- "$0")/_/husky.sh"
pnpm run formar
```

当我们对代码进行 commit 操作的时候，就会执行命令，对代码进行格式化，然后再提交。
