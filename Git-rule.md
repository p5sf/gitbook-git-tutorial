# 提交规范

## 分支规范

为了保持提交的整洁，方便后续维护，需要规范分支名称

- master 分支：主分支受保护，常常用来部署线上的代码，它一般由 develop 以及hotfix 分支合并，任何时间都不能直接修改代码
- develop 分支：开发分支受保护，保持最新代码以及Bug 修改后的代码，合并feature 分支然后测试代码，如果通过测试则合并master 分支上
- releaser 分支：预上线分支，发布测试阶段，如果已经通过测试，可以创建版本号，从 develop分支派生，必须合并 develop分支 和 master 分支
- hotfix 分支：紧急Bug 分支，从master分支派生，必须合并回develop 分支和master分支
- feature 分支：功能分支，开发新功能，一般基于 develop 分支下创建

## commit 格式

```
<type>: <subject>
<BLANK LINE>
<body>
<BLANK LINE>
<footer>
```

- type: 本次 commit 的类型，诸如 bugfix docs style 等
- scope: 本次 commit 波及的范围
- subject: 简明扼要的阐述下本次 commit 的主旨，在原文中特意强调了几点 1. 使用祈使句，是不是很熟悉又陌生的一个词，来传送门在此 祈使句 2. 首字母不要大写 3. 结尾无需添加标点
- body: 同样使用祈使句，在主体内容中我们需要把本次 commit 详细的描述一下，比如此次变更的动机，如需换行，则使用 |
- footer: 描述下与之关联的 issue 或 break change，详见案例

Type 类型

- feat: 添加新特性
- fix: 修复bug
- docs: 仅仅修改了文档
- style: 仅仅修改了空格、格式缩进、都好等等，不改变代码逻辑
- refactor: 代码重构，没有加新功能或者修复bug
- perf: 增加代码进行性能测试
- test: 增加测试用例
- chore: 改变构建流程、或者增加依赖库、工具等

案例如下

```java
docs(guide/component):add missing :
chore: fix eslint error
chore(docs-app): enusre Toc links contain the path
fix(grunt-utils): correctly detect java 
```

