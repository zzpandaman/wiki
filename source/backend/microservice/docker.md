# docker

## 1 概述

## 2 安装

- Linux

- Windows

## 3 使用

- 镜像
	
	<center class="half">
	<img src="../../_static/img/docker_img.png" width="50%" height="60%"><img src="../../_static/img/docker_img1.png" width="50%" height="60%">
	</center>

	- 镜像结构
	- 自定义镜像 主要指令：`FROM` `ENV` `COPY` `RUN` `EXPOSE` `ENTRYPOINT`
	
		```
		# 指定基础镜像
		FROM ubuntu:16.0.4
		# 配置环境变量，JDK安装目录
		ENV JAVA_DIR=/usr/local
		# 拷贝JDK,项目JAR包到镜像内
		COPY ./jdk.jar.gz $JAVA_DIR
		# 安装JDK: 解压缩、重命名
		RUN cd $JAVA_DIR \
		    && tar -xf ./jdk.jar.gz \
		    && mv ./jdk1.8.0_144 ./java8
		# 配置环境变量
		ENV JAVA_HOME=$JAVA_DIR/java8
		ENV PATH=$PATH:$JAVA_HOME/bin
	
		## 由于是分层结构，可以直接从java镜像开始构建，效果是一样的
		#FROM java:8-alpine
	
		# 拷贝JDK,项目JAR包到镜像内
		COPY ./docker-demo.jar /tmp/app.jar
		# 暴露端口
		EXPOSE 8090
		# 入口，启动 JAVA项目
		ENTRYPOINT java -jar /tmp/app.jar
		```

	- 命令
	- DockerCompose
	- 镜像仓库搭建
	
- 容器
- 数据卷
- 集群部署

## 4 jenkins

```
docker run ^
  --name jenkins ^
  -u root ^
  --rm ^
  -d ^
  -p 8082:8080 ^
  -v D:\dockervolumes\jenkins\jenkins-data:/var/jenkins_home ^
  -v D:\dockervolumes\jenkins\docker.sock:/var/run/docker.sock ^
  jenkinsci/blueocean:1.25.5-bcc31d32159f
```

