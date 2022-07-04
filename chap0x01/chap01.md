# 作业1
##实验问题

1、调查并记录实验环境的如下信息：

- 当前 Linux 发行版基本信息
- 当前 Linux 内核版本信息

2、Virtualbox 安装完 Ubuntu 之后新添加的网卡如何实现系统开机自动启用和自动获取 IP？

3、如何使用 scp 在「虚拟机和宿主机之间」、「本机和远程 Linux 系统之间」传输文件？

4、如何配置 SSH 免密登录？

##实验过程

###打开虚拟机就遇到网络配置问题，参考畅课互动区同学的解决方案
![](img\error.jpg)

###解决网络问题后进入ub
![](img\begin.jpg)

## 一、调查并记录实验环境的如下信息：

### 1、当前Linux发行版基本信息（以下使用了三种不同的方法）



简易cat

    cat /etc/issue

![当前 Linux 发行版基本信息](img\1.1release1.jpg)

详细cat

    cat /etc/os-release
![当前 Linux 发行版基本信息](img\1.1release2.jpg)

less

    less /etc/os-release 


![当前 Linux 发行版基本信息](img\1.1release3.jpg)

*Q退出命令执行*

### 2、查看当前Linux内核版本信息

    cat /proc/version

或

    uname -r
![当前 Linux 内核版本信息](img\1.2core.jpg)

## 二、Virtualbox安装完Ubuntu之后新添加的网卡如何实现系统开机自动启用和自动获取IP？

### 查询所有网卡

    ip a

![查询网卡](img\2.1ip.jpg)
### vim
    cd /etc/netplan

![](img\2.2vim.jpg)
###yaml
![yaml](img\2.3yaml.jpg)

ub20会自动分配好

## 三、如何使用 scp 在「虚拟机和宿主机之间」、「本机和远程 Linux 系统之间」传输文件？


**在虚拟机里创建一个txt文本（后来发现此项操作是多余的）**

    cuc@cuc-lab :~s touch newtext.txt
    cuc@cuc-lab :~$ls
    neutext.txt
    cuc@cuc-lab :~spwd neutext.txt
    /home/cuc
 
**为Ubuntu安装ssh**

    sudo apt-get install openssh-server

![安装ssh](img\openssh.jpg)

**在虚拟机中创建一个文件夹my-dir,再`cd`到文件夹中。创建三个文件1,2,3,使用`pwd`命令查看他们的路径**

    cuc@cuc-lab:~$mkdir my-dir
   
    cuc@cuc-lab:~$ cd my-dir
    cuc@cuc-lab:~/my-dir$ touch 1
    cuc@cuc-lab:~/my-dir$ touch 2
    cuc@cuc-lab:~/my-dir$ touch 3
    cuc@cuc-lab:~/my-dir$ ls
    1 2 3
    cuc@cuc-lab:~/my-dir$ puw my-dir
    /home/cuc/ my-dir


![创建一个文件夹](img\touch.jpg)

**在本地git-bash中输入如下命令,就可以将虚拟机的文件传输到主机**

    scp -r cuc@192.168.56.101:/home/cuc my-dir

![](img\scp.jpg)

**将文件从本地传输到虚拟机**

    scp C:\Users\zhang\Desktop\text.txt cuc@192.168.56.101:/home/cuc/

![将文件从本地传输到虚拟机](img\scp2.jpg)


##四.如何配置SSH免密登录？
**在本地git-bash生成公私钥对**

    ssh-keygen -t rsa
**将主机的公钥传到虚拟机中**

    ssh-copy-id cuc@192.168.56.101

![](img\sshpass.jpg)


##问题与解决


- **刚开始就遇到完全进不去虚拟机的情况**。参考了*畅课讨论区武国雯同学的解答方法*（要是没有同学那个解决方案，我可能就是寸步难行。）她的解决方案非常详细！

- 在做到传输文件的实验室**本地的git bash一直都连接不上SSH**（这个地方花了我一晚上都没有解决，最后我也不知道是怎么解决的，*可能是我把防火墙给关了？*反正这个地方真的是让我觉得匪夷所思，因为前面我都是对的，我也是先安装了sSH服务才做的，但是不知道为什么就一直卡在那个地方，第2天起来做的时候他莫名就好了）

**以上2个问题都耗费了我大量的时间。让我怀疑人生，但最终是艰难地解决了**

##参考

[虚拟机安装ubuntu&文件传输&远程连接和控制](https://blog.csdn.net/weixin_34062469/article/details/88057755?ops_request_misc=%257B%2522request%255Fid%2522%253A%2522165676404116782389423436%2522%252C%2522scm%2522%253A%252220140713.130102334.pc%255Fall.%2522%257D&request_id=165676404116782389423436&biz_id=0&utm_medium=distribute.pc_search_result.none-task-blog-2~all~first_rank_ecpm_v1~pc_rank_34-2-88057755-null-null.142^v30^pc_rank_34,185^v2^control&utm_term=linux%E4%BD%BF%E7%94%A8scp%E5%86%8D%E8%99%9A%E6%8B%9F%E6%9C%BA%E5%92%8C%E5%AE%BF%E4%B8%BB%E4%B9%8B%E9%97%B4%E4%BC%A0%E8%BE%93%E6%96%87%E4%BB%B6&spm=1018.2226.3001.4187)

[ub配置网络](https://www.serverlab.ca/tutorials/linux/administration-linux/how-to-configure-networking-in-ubuntu-20-04-with-netplan/)


[武国雯同学的讨论区帖子](http://courses.cuc.edu.cn/course/82669/forum#/topics/197992?show_sidebar=false&scrollTo=topic-197992&pageIndex=1&pageCount=2&topicIds=318163,232642,231166,231100,229408,219979,218713,214099,200422,197992&predicate=lastUpdatedDate&reverse)