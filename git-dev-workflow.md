# Git Dev Workflow
开发工作流

1. 团队成员克隆仓库到本地
  - `$ git clone ...`
2. 在本地切换到开发（dev）分支
  - `$ git checkout dev`
3. 以自己的名称（例：张三）建立属于自己的开发分支
  - `$ git checkout -b dev_zhangsan`
4. 编写代码，然后提交commit
  - `$ git add file`
  - `$ git commit --message "feat: 新增的功能"`
5. 推送到远程仓库之前，先在本地rebase远程dev分支的最新代码
  - `$ git pull --rebase origin dev`
6. 再将本地开发分支的代码，推送到远程开发分支上
  - `$ git push origin dev_zhangsan`
7. 在远程，向开发分支提交一个PR（Pull Request）
  - 申请远程`dev_zhangsan`分支合并到远程`dev`分支
8. 开发负责人对PR进行代码评审
9. 评审通过后，将`dev`分支代码构建成新的docker镜像，部署到测试环境服务器进行全面测试
10. 全面测试通过后，将docker镜像再部署到线上正式环境服务器
11. 结束