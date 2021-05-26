## Git 提交规范

### 参考
[commitizen + husky 规范git提交信息](https://juejin.cn/post/6844904025868271629)
[GitGuide](https://zjdoc-gitguide.readthedocs.io/zh_CN/latest/)
[git为不同的项目设置不同的用户名](https://www.jianshu.com/p/d3f80a1246d6)
[关于 Git 提交这些规范，你都遵守了吗？](https://www.huaweicloud.com/articles/a6f73ba7bbde52c8d3bbda85f20164f7.html)
[优雅的提交你的 Git Commit Message](https://zhuanlan.zhihu.com/p/34223150)
### gitconfig

在项目中的`.git`目录中可以对 `config` 文件 进行配置

### 使用 .gitmessage 模板

`config`文件中 配置

```
[commit]
	template = .gitmessage
```

执行 `git commit` 后使用 vim 提交

### Conventional提交规范
[Conventional Commits 1.0.0](https://www.conventionalcommits.org/en/v1.0.0/#summary)

```
<类型>[可选的作用域]: <描述>

[可选的正文]

[可选的脚注]
```

```
1.Select the type of change that you're committing 选择改动类型 ()

2.What is the scope of this change (e.g. component or file name)? 填写改动范围 ()

3.Write a short, imperative tense description of the change: 写一个精简的描述 ()

4.Provide a longer description of the change: (press enter to skip) 对于改动写一段长描述 ()

5.Are there any breaking changes? (y/n) 是破坏性修改吗？默认n (
) 6.Does this change affect any openreve issues? (y/n) 改动修复了哪个问题？默认n (
)  
生成的commit message格式如下：

 
(): 



 
填写完毕后，husky会调用commitlint对message进行格式校验，默认规定type及subject为必填项。

 
任何git commit指令的option都能用在 git cz指令上, 例如git cz -a

 
Commit message规范在rrd-fe落地使用情况
 
针对团队目前使用的情况，我们讨论后拟定了commit message每一部分的填写规则。

 
1. type
 
type为必填项，用于指定commit的类型，约定了feat、fix两个主要type，以及docs、style、build、refactor、revert五个特殊type，其余type暂不使用。

 
# 主要type
feat: 增加新功能
fix: 修复bug

# 特殊type
docs: 只改动了文档相关的内容
style: 不影响代码含义的改动，例如去掉空格、改变缩进、增删分号
build: 构造工具的或者外部依赖的改动，例如webpack，npm
refactor: 代码重构时使用
revert:   执行git revert打印的message

# 暂不使用type
test: 添加测试或者修改现有测试
perf: 提高性能的改动
ci: 与CI（持续集成服务）有关的改动
chore: 不修改src或者test的其余修改，例如构建过程或辅助工具的变动
 
当一次改动包括主要type与特殊type时，统一采用主要type。

 
2. scope
 
scope也为必填项，用于描述改动的范围，格式为项目名/模块名，例如：node-pc/common rrd-h5/activity，而we-sdk不需指定模块名。如果一次commit修改多个模块，建议拆分成多次commit，以便更好追踪和维护。

 
3. body
 
body填写详细描述，主要描述改动之前的情况及修改动机，对于小的修改不作要求，但是重大需求、更新等必须添加body来作说明。

 
4. break changes
 
break changes指明是否产生了破坏性修改，涉及break changes的改动必须指明该项，类似版本升级、接口参数减少、接口删除、迁移等。

 
5. affect issues
 
affect issues指明是否影响了某个问题。例如我们使用jira时，我们在commit message中可以填写其影响的JIRA_ID，若要开启该功能需要先打通jira与gitlab。

 
参考文档：

 
 
 
docs.gitlab.com/ee/user/project/integrations/jira.html

 
 
 
填写方式例如：

 
re #JIRA_ID
fix #JIRA_ID
 
示例
 
完整的commit message示例
[](https://res-static.hc-cdn.cn/fms/img/c1bf9cd718863d24ead46e686c37eb1a1603772900693)
  
相应的git log

[](https://res-static.hc-cdn.cn/fms/img/132c7fa710751493dbb6ac53ee1dbc761603772900693)
 
扩展阅读
 
conventional commits 必读 介绍约定式提交标准。

conventionalcommits.org/zh/v1.0.0-beta.3/

Angular规范 必读 介绍Angular标准每个部分该写什么、该怎么写。
 
github.com/angular/angular/blob/22b96b9/CONTRIBUTING.md#-commit-message-guidelines
 
@commitlint/config-conventional 必读 介绍commitlint的校验规则config-conventional，以及一些常见passes/fails情况。

github.com/conventional-changelog/commitlint/tree/master/%40commitlint/config-conventional#type-enum

  
```
### commitizen

#### 项目级安装

```
npm install -D commitizen
```