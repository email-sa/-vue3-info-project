# vue3-info-project
基于vue3 + webpack + antv + ts + lodash 从0-1实现一个信息管理系统


# 第一阶段

基于命令搭建一个基础的vue3项目基建,具体安装详情可以 参考官网
https://cli.vuejs.org/zh/guide/installation.html
安装的参数选择,选择自定义安装,scss预处理器,ts,jest单元测试和eslint+pretter,不勾选vuex其他的参数都可以默认

如果之前有安装vue2的的话,避免安装和更新出现问题,建议先卸载之后再安装.

卸载
```
npm uninstall -g @vue/cli
```
安装
```
npm install -g @vue/cli
# OR
yarn global add @vue/cli
```

安装后的项目结构为
```
-node_modules
-public
-src
-tests
-.browserslistrc
-.eslintrc.js
-.gitignore
-babel.config.js
-jest.config.js
-package.json
-package-lock.json
-README.md
-tsconfig.json

```

整理项目内容,删除不需要的文件

# 第二阶段
完善项目的配置，添加git提交校验，webpack打包配置等等
## 给项目添加git commit代码提交描述强校验
可在对应分支 feater/commit-verify 查看README.md详细内容
## 给项目引入webpack，并正对不同环境添加不同配置打包
