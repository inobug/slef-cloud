### Centos上安装Minikube

###### 在root环境下安装：

- 安装docker

  ```python
  1.使用 root 权限登录 Centos。确保 yum 包更新到最新。
  	sudo yum update
  2.安装需要的软件包， yum-util 提供yum-config-manager功能，另外两个是devicemapper驱动依赖的
  	sudo yum install -y yum-utils device-mapper-persistent-data lvm2
  3.设置yum源
  	sudo yum-config-manager --add-repo http://mirrors.aliyun.com/docker-ce/linux/centos/docker-ce.repo
  4.可以查看所有仓库中所有docker版本，并选择特定版本安装
  	yum list docker-ce --showduplicates | sort -r
  5.安装docker
  	sudo yum install docker-ce(需要安装的版本)
  6.启动并加入开机启动
  	sudo systemctl start docker
   	sudo systemctl enable docker
  7.验证是否安装成功
  	docker version
  
  ```

- 安装virtualbox 

  [官网地址](https://www.virtualbox.org/wiki/Downloads)

- 安装kubectl

  [下载kubectl安装包]('https://storage.googleapis.com/kubernetes-release/release/v1.7.1/bin/linux/amd64/kubectl')

  下载完成kubectl后,授权kubectl

  ```
  $ sudo chmod +x ./kubectl
  $ sudo mv ./kubectl /usr/local/bin/kubectl
  $ kubectl version # 验证kubectl安装是否成功
  ```

  

- 安装minikube

  [下载minikube国内软件包]('http://kubernetes.oss-cn-hangzhou.aliyuncs.com/minikube/releases/v1.2.0/minikube-linux-amd64')

  ```
  $ chmod +x minikube
  $ sudo install minikube /usr/local/bin
  ```

  

- 使用minikube

  不需要启动虚拟机的方式开启minikube

  ```
  minikube start --registry-mirror=https://registry.docker-cn.com --vm-driver=none
  ```
