# Git使用手册

## 配置个人信息
`git config --global user.name "ifui"`
`git config --global user.email ifui@foxmail.com`

## 查看配置信息
`git config --list`

## 初始化仓库
`git init`

## 添加新文件
`git add <filename>`

## 添加远程仓库
`git remote add origin https://github.com/ifui/IBOOK.git`
`git push -u origin master`

## 

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

- 差异： `git diff <source_branch> <target_branch>`

## 标签
`git tag 1.0.0 <id>`

可用 `git log` 获取ID

## 使用`github`

### 生成 `SSH KEY`
`ssh-keygen -t rsa -C "ifui@foxmail.com"`
### 将`id_rsa.pub`里的内容复制到`github`de `SSH KEY`里面去
`vim ~/.ssh/id_rsa.pub`