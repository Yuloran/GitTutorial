# GitTutorial

> [Download：Git for windows](https://github.com/git-for-windows/git/releases/tag/v2.14.1.windows.1)

## 前言

Android 开发中常用的版本控制工具就是 `Git`。商业项目大多使用 [`Git(自己搭建服务器)`](https://www.liaoxuefeng.com/wiki/0013739516305929606dd18361248578c67b8067c8c017b000/00137583770360579bc4b458f044ce7afed3df579123eca000) + `Gerrit` + `Jenkins` 搭建代码审核及持续集成系统。个人开源项目大多托管在 `Github`，这样就不必搭建 `Git` 服务器。本文以 `Github` 为例，简述 `Git` 账户配置及 `Git Bash` 命令别名配置。

## 一、远程登录授权

Git使用SSH协议验证和登录远程服务器，所以首先需要生成SSH Key，并把Public Key添加到Github账户。

## 二、检查SSH Key

检查本地是否已存在SSH Key：`ls -al ~/.ssh`

## 三、生成新的SSH Key

1. `ssh-keygen -t rsa -b 4096 -C "your_email@example.com"`
2. `eval $(ssh-agent -s)`
3. `ssh-add ~/.ssh/id_rsa`

## 四、添加SSH Key到Github账户

- `clip < ~/.ssh/id_rsa.pub`

- ![粘贴公钥，点击 "Add SSH Key"](pictures/add-ssh-public-key.png)


## 五、测试连接

- `ssh -T git@github.com`

## 六、配置用户名和邮箱

- `git config --global user.name "your_name"`
- `git config --global user.email your_email@example.com`
- `git config --list`

## 七、配置命令别名

- git bash 清屏：编辑‪`D:\Program Files\Git\etc\profile.d\aliases.sh`，添加`alias cls='clear'`

- git 常用命令别名配置：

```
git config --global alias.st status
git config --global alias.co checkout
git config --global alias.ci commit
git config --global alias.br branch
git config --global alias.last 'log -1'
git config --global alias.lg "log --color --graph --pretty=format:'%Cred%h%Creset -%C(yellow)%d%Creset %s %Cgreen(%cr) %C(bold blue)<%an>%Creset' --abbrev-commit"
```

## 八、Git 使用教程

参考 [廖雪峰的Git教程](https://www.liaoxuefeng.com/wiki/0013739516305929606dd18361248578c67b8067c8c017b000)