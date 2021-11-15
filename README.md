# vue3-info-project

基于 vue3 + webpack + antv + ts + lodash 从 0-1 实现一个信息管理系统

# 第一阶段

## 添加 commit 强校验

1. 使用 husky,它可以方便我们在项目中添加 git hooks,以下都是以 @7.0.4 版本为例
   安装

```
npm i -D husky
```

2. 执行 `npx husky install` 命令,该命令会创建 .husky/ 目录,并指定该目录为 git hooks 所在目录,即修改 git hooks 默认目录
3. 添加 git hooks,语法: husky add \<file\> \[cmd\] ，运行一下命令创建 git hooks `pre-commit`,git commit 之前会执行的 hook

```
npx husky add .husky/pre-commit "npm run test"
```

执行成功之后 .husky 目录下面会有一个名为 pre-commit de shell 脚本,在执行 commit 之前会执行该脚本.
脚本内容为

```
#!/bin/sh
. "$(dirname "$0")/_/husky.sh"

npm run test
```

将脚本内容更改为:

```
#!/bin/sh
. "$(dirname "$0")/_/husky.sh"

echo "========== 执行pre-commit 操作 =========="

git add ./
```

#! 是一个约定的标记，它告诉系统这个脚本需要什么解释器来执行，即使用哪一种 Shell。
echo 命令用于向窗口输出文本。

表示,执行 git add . 操作(具体操作可根据自己的项目调整)

4. 添加 commit-msg 校验
   安装 commit 规范校验 commitlint

```
npm install --save-dev @commitlint/config-conventional @commitlint/cli
```

根目录下,创建文件 commitlint.config.js,配置相关的 commit 规范定义
,文件内容参考根目录下 commitlint.config.js,具体配置可在官网查看

5.  绑定检验,执行命令
    `npx husky add .husky/commit-msg 'npx --no-install commitlint --edit "$1"'`
    来校验我们 commit 时添加的备注信息是否符合规范
    如果以上命令执行不成功的话,可以去掉 cmd 命令,先创建文件再,修改文件内容即可

        最后文件修改内容为

```
#!/bin/sh
. "$(dirname "$0")/_/husky.sh"

echo "========= 执行commit-msg校验 ======="
npx --no-install commitlint --edit $1

```

最后 .husk 目录的结构为

```
-- _
    -- .gitignore
    -- husky.sh
-- commit-msg
-- pre-commit
```

在之后的 git 代码提交中会对每次的 git commit 内容进行校验,关于 commit 规范,推荐参考 https://zhuanlan.zhihu.com/p/182553920

内容参考:

1. https://zhuanlan.zhihu.com/p/366786798
2. https://www.runoob.com/linux/linux-shell.html
