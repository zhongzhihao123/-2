# Git

1 git是一个版本控制管理系统

## git的下载和安装

[git-scm.com](git)

一直点next



## git的命令

1.   git --version表示版本

## git的基本工作流程

1. git分为**工作目录**，**暂存区**，**git仓库**
2. 工作者先提交项目，再放到暂存区，最后放到git仓库

## git的基本使用

### 1.1git使用配置

1. 配置提交人姓名:`git config --global user.name 提交人姓名`
2. 配置提交人邮箱：`git config --global user.email 提交人邮箱`
3. 查看git配置信息：`git config --list`

注意：修改信息，重复以上配置就好

### 1.2git提交步骤

1. `git init `初始化git 仓库
2. `git status`查看文件状态
3. `git add 文件列表`追踪文件  添加到暂存区中
4. `git commit -m提交信息(提交说明)`向仓库提交代码,就是提交到git仓库中
5. `gitlog`查看提交记录 

### 1.2撤销

- 用暂存区中的文件覆盖工作目录中的文件：`git checkout 文件`
- 将文件从暂存区中删除：`git rm --cached 文件`
- 将git仓库中指定的更新记录恢复出来，并且覆盖暂存区和工作目录：`git rest --hard commitID`这个ID是在git log 里有个commit的ID，这个作用是让更早的。即放在git仓库中恢复过来

## git分支

### 2.1分支细分

1. 主分支(master)：第一次向git仓库中提交更新记录自动产生的一个分支
2. 开发分支(develop):作为开发的分支，基于master分支创建
3. 功能分支(feature):作为开发具有功能的分支，基于开发分支创建

### 2.2分支命令

- `git branch`查看分支
- `git branch 分支名称`创建分支
- `git checkout 分支名称` 切换分支
- `git merge 来源分支` 合并分支
- `git branch -d分支名称` 删除分支（分支被合并后才允许删除） （-D强制删除）要先切换到其他分支才可以删除

### 2.3暂时保存更改

- 存储临时改动：`git stash` 就是剪贴你的内容
- 恢复临时改动：`git stash pop` 恢复你剪贴的内容

# Github

## 出现的问题

​		问题1：Failed to connect to github.com port 443: Timed out

​		方法：`git config --global --unset http.proxy`

## 推送到远程仓库

`git push 地址 分支名称`

注意，如果不想一直弄地址可以用

`git remote add 名字 地址` 到时推送直接git push 名字 分支名称就好

## 克隆远程仓库

克隆远端数据仓库到本地：`git clone`仓库地址`

克隆远程仓库后，在本地仓库修改，而修改的内容不能直接推送到远程仓库中，需要跟原创者成为合作伙伴，即

原创者在github中的settings有个colloabors建立合作伙伴，然后克隆者接受

## 3.4.2 拉取远程仓库中最新的版本

拉取远程仓库中最新的版本：`git pull 远程仓库地址 分支名称`



## 3.5 解决冲突

在多人同时开发一个项目时，如果两个人修改了同一个文件的同一个地方，就会发生冲突。冲突需要人为解决

将冲突的内容拉取下来，再解决

## 3.6 跨团队协作

1. 程序员 C fork仓库  就是复制一份仓库到自己的仓库
2. 程序员 C 将仓库克隆在本地进行修改
3. 程序员 C 将仓库推送到远程
4. 程序员 C 发起pull reqest
5. 原仓库作者审核
6. 原仓库作者合并代码就是merge

# Gulp

## Gulp能做什么

- l项目上线，HTML、CSS、JS文件压缩合并
- l语法转换（es6、less ...）
- l公共文件抽离
- l修改文件浏览器自动刷新

## Gulp的使用

1. 使用npm install gulp下载gulp库文件
2. 在项目根目录下建立gulpfile.js文件
3. 重构项目的文件夹结构 src目录放置源代码文件 dist目录放置构建后文件
4. 在gulpfile.js文件中编写任务.
5. 在命令行工具中执行gulp任务   （先安装`npm install gulp-cli -g`)

##  **Gulp中提供的方法**

- lgulp.src()：获取任务要处理的文件
- lgulp.dest()：输出文件
- lgulp.task()：建立gulp任务
- lgulp.watch()：监控文件的变化

例子

```javascript
 const gulp = require('gulp');
  // 使用gulp.task()方法建立任务
 gulp.task('first', () => {
    // 获取要处理的文件
    gulp.src('./src/css/base.css') 
    // 将处理后的文件输出到dist目录
    .pipe(gulp.dest('./dist/css'));//pipe就是获取文件后要做的事情
 });

```

## Gulp插件

- gulp-htmlmin ：html文件压缩

- gulp-csso ：压缩css

- gulp-babel ：JavaScript语法转化

- gulp-less: less语法转化

- gulp-uglify ：压缩混淆JavaScript

- gulp-file-include 公共文件包含

- browsersync 浏览器实时同步

  **注意：插件的使用查文档，都需要安装然后调用**

