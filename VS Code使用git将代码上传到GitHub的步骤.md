# VS Code使用git将代码上传到GitHub的步骤

## 1.初始化git并生成SSH密钥添加到指定的GitHub账户中

```
git config --global user.name "username"
//username为你的GitHub用户名
git config --global user.email "email@email.com"
ssh-keygen -t rsa -C "email@email.com"
//email@email.com为你的GitHub绑定邮箱
```

## 2.在VSCode中将代码上传到GitHub

### 1.首先在VSCode终端中初始化要上传的文件夹

```
git init
```

### 2.添加远程存储库

选择你要上传到哪个存储库，在VSCode中这是必须的

## 3.将要上传的文件先添加到暂存区并提交到本地仓库

```
git add .
//将文件添加到暂存区
git commit -m "0000"
//将文件提交到本地仓库，"0000"为提交信息可自定义
```

## 4.在GitHub的目标仓库中选择SSH，复制其中的"…or push an existing repository from the command line"命令行,大功告成啦!

```
git remote add origin git@github.com:username/name.git
//username为你的GitHub用户名，name为你的仓库名
git branch -M main
git push -u origin main
```

