# Homebrew 

官网： https://brew.sh/index_zh-cn

## 安装
`/usr/bin/ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install)"`

## 查看brew的帮助
`brew –help`

## 安装软件
`brew install git`

## 卸载软件
`brew uninstall git`

## 搜索软件
`brew search git`

## 显示已经安装软件列表
`brew list`

## 更新软件，把所有的Formula目录更新，并且会对本机已经安装并有更新的软件用*标明。
`brew update`

## 更新某具体软件
`brew upgrade git`

## 查看软件信息
`brew [info | home] [FORMULA...]`

## 删除程序，和upgrade一样，单个软件删除和所有程序老版删除。
`brew cleanup git`

`brew cleanup`

## 查看那些已安装的程序需要更新
`brew outdated`

## 列出已安装的软件
`brew list`

## 更新Homebrew
`brew update`

## 用浏览器打开
`brew home *`

## 显示软件内容信息
`brew info *`

## 显示包依赖
`brew deps *`

## 启动web服务器，可以通过浏览器访问http://localhost:4567/ 来同网页来管理包
`brew server *`

## 帮助
`brew -h brew`

## 显示已安装的包
`brew list`

## 相关服务命令

### 查看使用brew安装的服务列表
`brew services list`

### 启动服务（仅启动不注册）
`brew services run formula|--all`

### 启动服务，并注册
`brew services start formula|--all`

### 停止服务，并取消注册
`brew services stop formula|--all`

### 重启服务，并注册
`brew services restart formula|--all`

### 清除已卸载应用的无用的配置
`brew services cleanup`