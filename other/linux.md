1.yum install 和 yum groupinstall
​	yum install 是安装单个软件,以及这个软件的依赖关系
​	yum groupinstall	安装一个软件包，该包包涵多个单个软件以及其依赖

2.各个目录的作用
	  /etc        存放了系统配置方面的文件 
	  /dev      存放与设备(包括外设)有关的文件(unix和linux系统均把设备当成文件) 
	 /home   存放个人数据
	/tmp       linux系统会定期自动对这个目录进行清理 
   /usr        /bin或/etc目录下的额外的工具 
   /opt

3.查看linux版本
 rpm -q centos-release 

4.配置环境变量
	vim /etc/profile
	末尾添加 export PATH=$PATH:/opt/Nginx/sbin/ 
注/etc/profile文件  只有Login shell 启动时才会运行 /etc/profile 这个脚本 修改完要切换用户或者重新连接或者运行 **source /etc/profile** 

5.关闭防火墙

6.查看端口
	 netstat -an | grep 端口 





php版本7.2
nginx版本1.6.1 /opt/nginx