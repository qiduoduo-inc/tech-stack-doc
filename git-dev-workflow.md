# Git Dev Workflow

企朵朵团队的 Git 开发工作流，进入项目开发前必读

1. 配置好自己的Git

- `$ git config --global user.name "你的名称"`
- `$ git config --global user.email "你的Github账号邮箱"`

2. 团队成员克隆仓库到本地

- `$ git clone git@github.com:qiduoduo-inc/xxx.git`

3. 进入项目，在本地切换到开发（dev）分支

- `$ cd xxx`
- `$ git checkout dev`

4. 以自己的名称（例：张三）建立属于自己的开发分支

- `$ git checkout -b dev_zhangsan`

5. 编写代码，然后提交 commit

- `$ git add file`
- `$ git commit --message "提交类型(模块): 标题"`
  - git commit message 里的提交类型有以下几种可选择
    - `feat` // 新增功能
    - `fix` // 修复 Bug
    - `perf` // 性能提升
    - `style` // 优化代码格式
    - `docs` // 编写文档
    - `test` // 编写测试
    - `refactor` // 代码重构
    - `build` // 编译打包
    - `ci` // 持续集成
    - `cd` // 持续部署
    - `chore` // 其他修改，比如构建流程
    - `revert` // 代码回滚
    - `workflow` // 工作流
    - `types` // 定义变量类型
    - `config` // 项目配置
    - `dependency` // 项目依赖

6. 推送到远程仓库之前，先在本地 rebase 远程公共开发分支 dev 的最新代码

- `$ git pull --rebase origin dev`

7. 再将本地开发分支的代码，推送到属于自己的远程开发分支上

- `$ git push origin dev_zhangsan`
  - 此处注意：所有开发同学只能向属于自己的开发分支推送 push 代码，不允许直接向公共分支`master`、`main`、`dev`和`test`等推送代码

8. 在远程，向公共开发分支`dev`提交一个 PR（Pull Request），申请合并代码

- 例：申请远程分支`dev_zhangsan`合并到远程公共分支`dev`

9. 开发负责人会对 PR 进行代码评审 CR（Code Review）
10. CR 评审通过后，项目负责人将`dev`分支代码合并到`test`分支，构建测试容器镜像，将镜像部署到测试环境服务器进行全面测试
11. 全面测试通过后，项目负责人会将`test`分支代码合并到`master`分支，构建正式容器镜像，再部署到线上正式环境服务器
12. 结束
