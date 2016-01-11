# Git常用代码

* 下载最新版本的git
	* http://git-scm.com/downloads

1.查看版本号

```
git --version 
```
2.设置用户名

```
git config --global user.name 你的名字
```
3.设置邮箱

```
git config --global user.email 你的Email
```
4.Clone项目

```
git clone http://git.oschina.net/xxxxxx/xxxxxx.git
```
5.创建特性分支

```
git checkout -b $feature_name
```
6.写代码，提交变更

```
git commit -am "My feature is ready"
```
7.Linux系统中设置git颜色

```
git config --global color.ui true
```
8.git配置清单

```
git config --list
```
9.查看git所有配置

```
git config
```

# 关于SSH Keys
SSH key可以让电脑与服务器建立安全的加密连接

1.生成SSH key

```
ssh-keygen -t rsa -C "xxxxx@xxxxx.com"# Creates a new ssh key using the provided email
// 返回
Generating public/private rsa key pair...
```

2.查看public key（并添加至服务器）

```
cat ~/.ssh/id_rsa.pub
// 返回
ssh-rsa AAAAB3NzaC1yc2EAAAADAQABAAABAQC6eNtGpNGwstc....
```

3.以Git@OSC为例，添加后输入

```
ssh -T git@git.oschina.net
// 若返回以下消息则成功
Welcome to Git@OSC, yourname! 
```

# 在Git@OSC上导入外部git仓库
1.clone Github上原始地址

```
git clone --bare  https://github.com/bartaz/impress.js.git
```
2.Git@OSC上创建项目

3.以镜像的方式把clone的项目push到Git@OSC上，若提示输入git用户密码，则去http://git.oschina.net/keys 添加 SSH Key

```
cd impress.js.git
git push --mirror git@git.oschina.net:username/impress-js.git
```
* 关于如何导入外部仓库到Git@OSC的其他办法
	* http://www.oschina.net/question/82993_133520 

#Git版本控制入门
* Git官网 <http://git-scm.com>
* Git@OSC客户端 <http://git.oschina.net/appclient>
* Git手册 <http://git-scm.com/docs>
* Git详细教程 <http://git-scm.com/book/zh/v2>
* [Git@OSC教程] (http://git.oschina.net/oschina/git-osc/wikis/%E5%B8%AE%E5%8A%A9#继续阅读)
* [Git入门教程] (http://www.liaoxuefeng.com/wiki/0013739516305929606dd18361248578c67b8067c8c017b000/001373962845513aefd77a99f4145f0a2c7a7ca057e7570000)
* Git快速入门（gif动画）<http://git.oschina.net/wzw/git-quick-start>

