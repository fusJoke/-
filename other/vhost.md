场景：

​	win10下的phpstudy：php7+nginx+tp5配置虚拟主机

​	虚拟域名：www.tptest.com;

​	phpstudy安装位置：D:\study

步骤：

​	①C:\Windows\System32\drivers\etc\hosts 新增一行

​		127.0.0.1	   www.tptest.com

​		作用：修改dns映射；是www.tptest.com默认访问127.0.0.1

​	![1552380126548](C:\Users\aumak\AppData\Roaming\Typora\typora-user-images\1552380126548.png)

​	②配置虚拟主机

​		1.修改nginx.conf文件(D:\phpstudy\PHPTutorial\nginx\conf\nginx.conf)

​			新增代码如下

![1552380556082](C:\Users\aumak\AppData\Roaming\Typora\typora-user-images\1552380556082.png)

​			晒出坑：

![1552380694895](C:\Users\aumak\AppData\Roaming\Typora\typora-user-images\1552380694895.png)

总结：遇到nginx配置的相关问题先看error.log报错日志，而不是百度。不思考的结果是更低效，花更多时间。