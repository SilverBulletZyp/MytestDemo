# 配置SVN用户权限

主要是修改/svn/mycode/conf目录下的三个文件

1.打开svnserve.conf，将下列配置项前面的#和空格都去掉

```
# anon-access = read
# auth-access = write  
  
# password-db = passwd  
# authz-db = authz  
```
anon-access = read代表匿名访问的时候是只读的，若改为anon-access = none代表禁止匿名访问，需要帐号密码才能访问

2.打开passwd，在[users]下面添加帐号和密码

```
// 账号 = 密码
[users]  
XX = XXX 
```
3.打开authz，配置用户组和权限

* 我们可以将在passwd里添加的用户分配到不同的用户组里，以后的话，就可以对不同用户组设置不同的权限，没有必要对每个用户进行单独设置权限。
在[groups]下面添加组名和用户名，多个用户之间用逗号(,)隔开

```
// 以下则说明两个用户都是这个组
[groups]  
topgroup=XX,XX 
```
权限配置,使用[/]代表svn服务器中的所有资源库

```
[/]  
@topgroup = rw  
// 或
[/]  
XX = rw  

```
上面的配置说明topgroup这个组中的所有用户对所有资源库都有读写(rw)权限，组名前面要用@
如果是用户名，不用加@，比如XX这个用户有读写权限

4.启动svn服务器

```
svnserve -d -r /Users/apple/svn
// 或
svnserve -d -r /Users/apple/svn/mycode
```
无提示则说明成功

5.关闭svn服务器

打开活动监视器，关闭svnserve

# 使用SVN客户端功能
1.从本地导入代码到服务器

```
svn import 本地目录地址 svn地址 --username=XX --password=XX -m "初始化导入"
```
2.clone svn仓库到本地

```
svn co svn地址
// 也可使用
svn checkout svn地址 --username=XX --password=XX 本地目录地址
```
3.cd到本地仓库

4.修改源码之后查看源码状态

```
svn st
```
5.提交更改过的代码到服务器

```
svn ci -m "注释"
```
6.更新服务器代码到客户端

```
svn update
```

7.svn帮助

```
svn help
```
# 其他教程
* [svn配置大全]<http://www.cnblogs.com/armyfai/p/3985660.html>
