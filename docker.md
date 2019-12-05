`Docker` 的核心组件包括：

1. **Docker Client**
2. **Docker daemon**
3. **Docker Image**
4. **Docker Registry**
5. **Docker Container**

 `Docker Client` ，也称 `Docker` 客户端。它其实就是 `Docker` 提供命令行界面 `(CLI)` 工具 。

 `Docker daemon` 是服务器组件，以 `Linux` 后台服务的方式运行，是 `Docker` 最核心的后台进程，我们也把它称为守护进程 。 `Docker Daemon` 可以认为是通过 `Docker Server` 模块接受 `Docker Client` 的请求，并在 `Engine` 中处理请求，然后根据请求类型，创建出指定的 `Job` 并运行 



 `Docker` 镜像可以看作是一个特殊的文件系统，除了提供容器运行时所需的程序、库、资源、配置等文件外，还包含了一些为运行时准备的一些配置参数（如匿名卷、环境变量、用户等 )。 将镜像的内容和创建步骤描述在一个文本文件中，这个文件被称作 `Dockerfile` ，通过执行 `docker build ` 命令可以构建出 Docker 镜像 



docker工作流程

1. `Docker` 客户端执行 `docker run` 命令
2. `Docker daemon` 发现本地没有我们需要的镜像
3. `daemon` 从 `Docker Hub` 下载镜像
4. 下载完成后，镜像被保存到本地
5. `Docker daemon` 启动容器