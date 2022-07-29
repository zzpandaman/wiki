# ci-di

## 1 jenkins

使用docker部署jenkins

```
docker run ^
	--name jenkins ^
	-u root ^
	-d ^
	-p 8082:8080 ^
	-p 50000:50000 ^
	-v D:\dockervolumes\jenkins\jenkins-data:/var/jenkins_home ^
jenkinsci/blueocean
```

1 安装并配置jdk、maven、git 

2 安装插件 `Maven Integration` `Publish Over SSH`

3 生成ssh密钥对，将公钥推送给应用服务器

```
ssh-keygen -m PEM -t rsa -b 4096
scp ./id_rsa.pub x@192.168.1.112:C:/Users/X/.ssh/authorized_keys
```

4 发布任务配置:不同的构建模板都能达到一样的效果

<img src="../../_static/img/ci-di0.png" width="80%" height="80%">

- General

	<img src="../../_static/img/ci-di1.png" width="60%" height="60%">

	+ Discard old builds:设置构建历史留存规则：最大保存天数、最大保存条数
	
- 源码管理

	<img src="../../_static/img/ci-di2.png" width="60%" height="60%">

	+ Repository URL:代码仓库地址，与`git clone`时的一致
	+ Credentials:配置证书
	+ Branches to build:指定分支

- 构建触发器 & 构建环境
	
	<img src="../../_static/img/ci-di3.png" width="60%" height="60%">
	<img src="../../_static/img/ci-di4.png" width="60%" height="60%">

	- Build periodically:周期性构建-定时构建语法
	- Add timestamps to the Console Output：控制台添加时间戳

- Build
	
	<img src="../../_static/img/ci-di5.png" width="60%" height="60%">

	- Root POM:项目根pom
	- Goals and options:`mvn clean package`等命令及参数

- Post Steps

	<img src="../../_static/img/ci-di6.png" width="60%" height="60%">

	- 根据Build结果是否运行Post Steps
	- Send files or execute commands over SSH:需下载Publish Over SSH

		<img src="../../_static/img/ci-di7.png" width="60%" height="60%">

		- Name:需在系统配置中配置远程节点
			
			<img src="../../_static/img/ci-di8.png" width="60%" height="60%">

		- Transfer Set:一次文件传输、执行命令（最少有一项）;一次传输中文件传输结束才执行命令；多次传输则按顺序执行
			+ Source files：源文件--jenkins服务器；支持通配符、分隔符
			+ Remove prefix：文件路径过深时减少文件层次
			+ Remote directory：目标位置--应用服务器
			+ Exec command：命令;对于windows服务器格式`cmd /c "命令1 & 命令2 ..."`

<!-- 		<img src="../../_static/img/ci-di1.jpeg" width="80%" height="80%">
		<img src="../../_static/img/ci-di3.jpeg" width="80%" height="80%"> -->

- pipline
	+ 源码管理：checkout: Check out from version control
	+ General+构建触发器：properties: Set job properties
	+ 构建环境：wrap: General Build Wrapper