[toc]

# CentOS安装

略

# Xshell和XFTP使用

略

# 问题：启动服务器时未加载网卡，导致IP地址初始化失败

1：查看Linux操作系统的IP地址：
ip addr

![img](/Users/yannlau/Documents/JavaSet/Java韩顺平/2.JavaWeb/assets/b8620a5ec5af4ba5b0e58b5a749fad99.png)

并没有获取到linux系统的IP地址。这是由于启动服务器时未加载网卡，导致IP地址初始化失败而造成的。

2：需要来修改网络初始化配置，设定网卡在系统启动时初始化。
1). 修改网卡的配置项

cd /				进入根目录
cd etc				进入etc目录
cd sysconfig		进入sysconfig目录
cd network-scripts	进入network-scripts
vi ifcfg-ens33		编辑ifcfg-ens33文件

进入文件后执行如下操作: 
①. 按 i 键 		 进入编辑状态
②. 按↑↓键来移动光标, 删除no,输入yes 
③. 按 ESC 键
④. 输入 :wq
⑤. 按 ENTER	保存退出
把这个文件的配置项ONBOOT的值有no改为yes即可

![img](/Users/yannlau/Documents/JavaSet/Java韩顺平/2.JavaWeb/assets/8b79462bf55d45a18fb11c49bf8f0c7b.png)

重启虚拟机即可。

# CentOS安装MySQL5

[10、MySQL的初始化配置_哔哩哔哩_bilibili](https://www.bilibili.com/video/BV13A41197fD?p=11&spm_id_from=pageDriver&vd_source=9bfe1ca76c0d7c42a70bafd019e62999)

下载mysql的tar包，解压得到许多rpm安装包。

取消一个依赖，避免兼容性问题。yum - mariadb --nodeps

安装其中的几个rpm，略。不是本文重点。

`set password for root@xxx=password("xxxx"); `修改用户密码

> 设置MySQL远程可以登录。
>
> use mysql;
> update user set host = '%' where user ='root';
> flush privileges;

# CentOS安装Tomcat

work目录 放置jsp、servlet编译后的class文件。

设置 CATALINA_HOME

将bin目录放入PATH。

# 放置工件

将war包放入webapps下qidongtomcat即可访问。

如果是单个的静态网页，只需要在webapps下创建一个文件夹，放入文件夹内，然后访问该静态资源即可。