# Git Commit 规范

这里采用 `commitizen` 这个工具辅助

## github commit 应该包含四个信息

type（必需）、scope（可选）和subject（必需）、body (可选)

## 使用方式

`git cz`

### type

feat :新功能

fix :修复bug  

docs : 文档改变

style : 代码格式改变

refactor :某个已有功能重构

perf :性能优化

test :增加测试/测试用例

revert: 撤销上一次的 commit

chore: 改变构建流程、或者增加依赖库、工具等

Init：新建库

build :改变了build工具 如 grunt换成了 npm

### scope

scope用于说明 commit 影响的范围，比如数据层、控制层、视图层等等，视项目不同而不同

### subject

subject是 commit 目的的简短描述，不超过50个字符
以动词开头，使用第一人称现在时，比如change，而不是changed或changes
第一个字母小写
结尾不加句号（.）

### body

对本次 commit 的详细描述，可以分成多行