# mysql 安装和修改密码教程
  mysql的安装有解压版和安装版可以使用，安装版的就直接按照安装过称下一步就行了。现在先不讲安装版的安装过程，此文先讲解解压版的安装过称。
##### 1. 解压 & 增加系统环境变量
先将解压版的 `.zip` 等压缩文件利用压缩工具将其解压。将解压的sdk文件目录增加到当前服务器的环境变量中。(如何添加环境变量由于简单，不做过多的介绍)
##### 2. 修改配置文件
解压的文件夹下会有一个配置文件，名称可能是 `my.ini` 或者 `my-default.ini` 文件，用文本编辑器打开该文件，修改里面的 basedir(mysql的解压目录) 参数 和 datadir(数据库的data 文件夹的位置)。5.7.* 版本中的data文件夹如果自己创建，<font color="red">容易出错</font>，因此，我们可以通过 `mysqld --initialize` 命令，先进性初始化，自动生成 `data\` 文件夹
##### 3. 初始化mysql环境
执行命令 `mysqld --initialize` 初始化环境。此时，mysql的服务会在%JAVA_HOME%下的data文件夹里面生成数据，以便于能够登录使用。
##### 4. 注册mysql服务
打开命令行工具(cmd) 工具，输入命令`mysqld install MySQL --default-file="%JAVA_HOME%\my-default.ini"`，命令行显示注册服务成功即可。
##### 5. 修改密码
首次登录mysql会出现无法登录的情况，此时，我们需要在 `my-default.ini` 文件中加入 `skip-grant-tables` 参数。此时我们需要重启一下mysql 服务，可以通过命令重启mysql服务
```
net stop mysql // 关闭mysql服务
net start mysql // 开启mysql服务
```
此时，我们就可以免密码登录到mysql服务其中
登录输入`mysql -u root -p` 连续回车，不需要输入密码，直接回车就可以登录到mysql数据库服务器中。然后我们可以修改密码root密码。执行sql语句
```
use msyql; // 切换数据库
update user set authentication_string = password("new_password") where user = "root"; //修改root用户的密码 
```
#### 到此为止，安装过程完成，如果是安装版本的，可能就没有这么多的问题了。