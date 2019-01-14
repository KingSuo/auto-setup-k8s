# auto-setup-k8s
[VirtualBox + Vagrant + Ansible快速搭建K8s(1.13.0)集群][u01]

## 步骤

### 开始前准备

1.	[下载项目到本地(宿主机)][u02]；
2.	安装[Virtual Box][u03]和[Vagrant][u04]；
3.	修改[Vagrantfile][u05]，主要针对`private_network`，自定义为宿主机同一网段下任意ip即可，其余配置自行决定；
4.	对应步骤`3`中自定义的IP，修改[hosts][u06]及[kubeadm-config.yaml][u07]对应参数；
5.	下载依赖资源到本地：
	*	[docker-ce-18.06.1.ce-3.el7.x86_64.rpm][u08]
	*	[k8s-repo-1.13.0][u09]  密码:aqq6
	*	[k8s-v1.13.0-rpms.tgz][u10]  密码:4x77
6.	修改[just-go.yml][u11]中对应参数(**path/to/your**修改为你下载资源所在的目录)

### 开始

1.	创建虚拟机
	*	进入项目目录，执行`vagrant up`创建虚拟机；
	*	自行配置宿主机SSH免密登陆虚拟机(ssh-keygen、ssh-copy-id)
2.	搭建K8s集群
	*	进入项目目录，执行`ansible-playbook -i hosts just-go.yml`


[u01]:	
[u02]:	https://github.com/KingSuo/auto-setup-k8s.git
[u03]:	https://www.virtualbox.org/wiki/Downloads
[u04]:	https://www.vagrantup.com/downloads.html
[u05]:	https://github.com/KingSuo/auto-setup-k8s/blob/master/Vagrantfile
[u06]:	https://github.com/KingSuo/auto-setup-k8s/blob/master/hosts
[u07]:	https://github.com/KingSuo/auto-setup-k8s/blob/master/kubeadm-config.yaml
[u08]:	https://mirrors.tuna.tsinghua.edu.cn/docker-ce/linux/centos/7/x86_64/stable/Packages/docker-ce-18.06.1.ce-3.el7.x86_64.rpm
[u09]:	https://pan.baidu.com/s/1V90inVwvdJM9LKDgOfNglA
[u10]:	https://pan.baidu.com/s/12dL5r_M33-VyBrVWXj9kdw
[u11]:	https://github.com/KingSuo/auto-setup-k8s/blob/master/just-go.yml