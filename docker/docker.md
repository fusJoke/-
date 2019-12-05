1. 容器

2. 镜像
   查看所有的镜像

3. dockerfile

4. docker-compose
   docker-compose up -d 创建并启动容器，-d 表示以守护进程模式运行
    compose命令都需要到docker-compose.yml文件所在的目录下才能执行 

5. 查看各容器的dockerIP地址
   docker inspect -f '{{.Name}} - {{range .NetworkSettings.Networks}}{{.IPAddress}}{{end}}' $(docker ps -aq)

6. docker run 参数

   --rm  可以在容器启动时设置--rm选项，这样在容器退出时就能够自动清理容器内部的文件系统 

   -it   **-i:** 以交互模式运行容器，通常与 -t 同时使用；

   ​       **-t:** 为容器重新分配一个伪输入终端，通常与 -i 同时使用； 

   -w  指定容器的工作区域

   -v  将宿主机的工作环境挂载(映射)容器的目录里面，

   docker run -it --rm -v $PWD:/tmp -w /tmp php:7.1-fpm php Server.php
   																					镜像        

参考文章: https://segmentfault.com/a/1190000018643542?utm_source=tag-newest 





