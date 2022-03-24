docker-compose 离线下载 使用putty上传到linux服务器的步骤：


1. 先下好docker-compose的文件

2. 在shell/bash 里执行命令。

	pscp 本地文件路径   服务器用户名@ip:文件服务器存放的路径 。

	如果是windows没有注册程序的全局路径，可以直接进入到程序所在的目录，使用上述命令。

3. 之后按照远程ssh登录的流程来就好

4. 在服务器的远程命令行里，先进入到之前上传的位置，执行以下命令
	
	 mv docker-compose-Linux-x86_64 /usr/local/bin/docker-compose

5. 授权 chmod +x /usr/local/bin/docker-compose

6. 查看版本信息 docker-compose -v