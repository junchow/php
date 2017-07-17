# GIT远程协作

- GitHub简介
- Git远程协作命令
- GitHub Pull Request流程

## GitHub简介

- GitHub注册与功能简介
- 为GitHub托管项目访问添加SSHkeys

ping git.infodatan.com
222.240.214.188

ping github.com
192.30.255.113

为GitHub托管项目添加SSHKey

```
// 本机生成RSA秘钥，需输入github密码
$ ssh-keygen -t rsa -C "junchow520@hotmail.com"

// 为了不要每次都输出密码，使用ssh agent保存密码 
$ eval "$(ssh-agent -s)"
Agent pid 6453
$ ssh-add ~/.ssh/id_rsa
//输出github密码


// 查看ssh公钥密码sshkey
$ vim ~/.ssh/id_rsa.pub

// 验证sshkey
$ ssh -T git@github.com
```

管理多个git账户

常用git账户如github、gitlib、git.infodatan...

```
// 生成github的账户，存放key的名字为id_rsa_github
$ ssh-keygen -t rsa -C "junchow520@hotmail.com"
// 打开ssh agent
$ ssh-agent -s
// 添加秘钥
$ ssh-add ~/.ssh/id_rsa_github
// 创建config文件
$ vim ~/.ssh/config

# github
Host github.com
	HostName github.com
	PreferredAuthentications publickey
	IdentityFile ~/.ssh/id_rsa.github
	User junchow

// 测试
$ ssh -T git@github.com

// 测试debug， -v输出编译信息
$ ssh -vT git@github.com

// 设置git
$ git config --global --unset user.name
$ git config --global --unset user.email

// 不同仓库下设置局部账户和邮箱
$ git config user.name "junchow"
$ git config user.email "junchow520@hotmail.com"
```

Git远程协作的主要命令


- git clone 获取远程仓库
- git fetch 获取远程仓库中所有分支及数据
- git pull 是 git fetch 和 git merge 的组合操作
- git push 将本地数据推送到远程仓库中

git clone 支持协议

- ssh://[user@]host.xz[:port]/path/to/repo.git/
- git://host.xz[:port]/path/to/repo.git/
- http[s]://host.xz[:port]/path/to/repo.git/
- ftp[s]://host.xz[:port]/path/to/repo.git/
- rsync://host.xz/path/to/repo.git/

```
// 克隆远程仓库
$ git clone git@github.com:junchow/php.git && cd php

// 获取远程仓库最新更新
$ git fetch

// 查看历史记录
$ git log

```


# THIS IS A NEW LINE


