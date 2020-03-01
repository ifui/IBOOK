# Git使用手册

## 配置个人信息
`git config --global user.name "ifui"`
`git config --global user.email ifui@foxmail.com`

## 初始化仓库
`git init`

## 添加新文件
`git add <filename>`

## 提交版本
`git commit -m "<string>"`

-a：将所有被修改或者已删除的且已经被git管理的文档提交到仓库中

## 下载到本地
`git clone ssh://example.com/project.git`

## 推送到服务器
`git push ssh://example.com/project.git`

## 取回更新,并合并
`git pull`

## 删除
`git rm <filename>`

## 分支

- 创建：`git branch test`

- 更改： `git checkout test`

- 合并： `git merge test`

- 删除： `git branch -d test`


