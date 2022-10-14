# 1.相关概念
## 1.1镜像
1. 一个root文件系统，不包含动态数据
2. 分层存储：每层构建完就不会发生改变，对于删除前一层的操作，只是在当前层标记删除
## 1.2容器
1. 镜像运行的实体
2. 容器存储层
   * 以镜像为基础层，创建一个当前容器的存储层
   * 生命周期和容器一样，为容器运行是读写准备的存储层
   * 容器不应该向容器存储层写入数据
3. 数据卷
   * 跳过容器存储层，直接对宿主进行读写
   * 独立于容器，容器消亡，数据卷不会消亡
   * 数据不会丢失
## 1.3仓库
* 管理镜像
# 2.镜像的使用
1. 下载镜像：docker pull 镜像地址
2. 运行镜像：docker run  -it 镜像 bash
3. 查看镜像列表：docker image ls
    * 查看虚悬镜像：docker image ls -f dangling=true
    * 按给定格式查看镜像列表：docker image ls --format "{{.ID}}:{{.Repository}}"
4. 磁盘占用情况：docker system df
5. 删除镜像：docker image rm 镜像
## 2.1.DockerFile
* 每一条指令都会建立一层镜像
  * 可以把多条命令用&&连成一条，避免层数过多
  * 可以添加清理工作的命令，避免镜像臃肿
 ### 2.1.1指令
1. 指定基础镜像：FROM 镜像名称
2. 执行命令行命令：RUN 命令行命令
3. 构建镜像
   * 在DockerFile文件所在目录执行：docker build -t 镜像名称 上下文路径
      * git仓库、压缩包、文本文件都可以进行镜像构建
4. 复制文件：COPY ./package.json /app/  这里.表示上下文路径
   * 可以自动解压缩的复制文件：ADD 源路径 目标路径
5. 容器启动：CMD 默认容器启动时所需要运行的程序和参数
   * docker run 镜像名称后边的command会替换CMD命令
   * 主进程退出，容器退出：执行的程序，如nginx，需要以前台运行
6.  容器启动：ENTRYPOINT 默认容器启动时所需要运行的程序和参数
    * ENTRYPOINT "CMD"：CMD命令作为参数，给ENTRYPOINT
 7. 设置环境变量：ENV VERSION=1.0 
 8. 设置环境变量，容器运行后不存在：ARG
 9. 定义匿名卷：VOLUME
 10. 生命运行时容器提供服务端口：EXPOSE
 11. 指定工作目录：WORKDIR
 12. 指定当前用户：USER
 13. 检查容器健康状态：HEALTHCHECK
 14. 以当前镜像为基础镜像时才执行：ONBUILD
 15. 添加元数据：LABEL
 16. SHELL指令：SHELL
## 2.2 
# 参考资料:
* 《Docker——从入门到实践》
