### Docker-从入门到实践
#### url:https://yeasy.gitbooks.io/docker_practice/content/basic_concept/
### Image镜像
镜像构建时，是一层层构建，前一层是后一层的基础，每一层构建完就不会再发生改变

拉取镜像
docker pull
运行docker容器
docker run -it --name [容器名称]　-p [本地端口]:[docker端口]　--rm [镜像名称]:[tag] bash
进入容器
docker exec -it [容器名称] bash
列出镜像
docker image ls
删除虚悬镜像
docker image prune
删除本地镜像
docker image rm [选项]　<镜像>
查看容器修改内容
docker diff [容器名称]
保存修改后的容器
docker commit --author "yangxiaoxiao@idriverplus.com" --message "hello-world" [容器名称] [<仓库名>[:<标签>]]
查看镜像内的历史记录
docker history [仓库名:标签]



### Container容器
容器的实质是进程
每一个容器运行时，是以镜像为基础层，在其上创建一个当前容器的存储层
所有的文件写入操作，都应该使用数据卷、或者绑定宿主目录
新建并启动容器
docker run [镜像:tag] -it /bin/bash
后台运行
-d
查看容器信息
docker container ls
docker container ls --all  # 显示所有的容器，包括已经结束的
查看容器内的输出结果
docker container logs [容器id]
终止运行中的容器
docker container stop
启动已终止容器
docker container start
删除容器
docker container rm [容器]
清除所有处于终止状态的容器
docker container prune
获取容器的输出信息
docker container logs


### Hub仓库
集中存储、分发镜像的服务
Docker Registry 仓库　标签
搜索仓库中的镜像
docker search
拉取镜像
docker pull


### Docker数据管理
在容器中管理数据主要有两种方式，数据卷和挂载主机目录
#### 数据卷
数据卷是一个可供一个或多个容器使用的特殊目录，可以在容器之间共享和重用，对数据卷的修改会立马生效，对数据卷的更新不会影响镜像
创建一个数据卷
docker volume create my-vol
查看制定数据卷的信息
docker volume inspect my-vol
查看所有数据卷
docker volume ls
启动容器时挂载一个数据卷
-v
创建一个名为xxx的容器，并加载一个数据卷到容器的/yyyy目录
docker run -d -P --name xxx --mount source=my-vol,target=/yyyy 
删除数据卷
docker volume rm my-vol
#### 挂载主机目录
指定挂载一个本地主机的目录到容器中
docker run -d -P --name xxx --mount type=bind,source=/src/app,target=/opt/app

### 使用网络
指定映射端口
-p
查看映射端口的配置
docker port <container_name> <port_number>




### 实践
#### 在深度学习服务器上搭建tensorflow & ROS的镜像


### Tips
容器存储层要保持无状态化，所有的文件写入操作，都应该使用数据卷、或者绑定宿主目录，在这些位置的读写会跳过容器存储层，直接对宿主发生读写，其性能和稳定性更高
导出本地某个容器 docker export [container id] > [file name].tar
