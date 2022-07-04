# 实验四

## 实验环境

Ubuntu 20.04 Server 64bit

Vscode

**首先得配好vs环境**

[参考配置vs](https://www.pianshen.com/article/46881682669/)

![](img/vs.jpg)


## 实验任务

### 用bash编写一个图片批处理脚本，实现以下功能

 ☑支持命令行参数方式使用不同功能

 ☑支持对指定目录下所有支持格式的图片文件进行批处理指定目录进行批处理

 ☑支持以下常见图片批处理功能的单独使用或组合使用

 ☑支持对jpeg格式图片进行图片质量压缩

 ☑支持对jpeg/png/svg格式图片在保持原始宽高比的前提下压缩分辨率

 ☑支持对图片批量添加自定义文本水印

 ☑支持批量重命名（统一添加文件名前缀或后缀，不影响原始文件扩展名）

 ☑支持将png/svg图片统一转换为jpg格式

### 用bash编写一个文本批处理脚本， 对以下附件分别进行批量处理完成相应的数据统计任务

 ☑统计不同年龄区间范围（20岁以下、[20-30]、30岁以上）的球员数量、百分比

 ☑统计不同场上位置的球员数量、百分比

 ☑名字最长的球员是谁？名字最短的球员是谁？

 ☑年龄最大的球员是谁？年龄最小的球员是谁？

### 用bash编写一个文本批处理脚本，对以下附件分别进行批量处理完成相应的数据统计任务

 ☑统计访问来源主机TOP 100和分别对应出现的总次数

 ☑统计访问来源主机TOP 100 IP和分别对应出现的总次数

 ☑统计最频繁被访问的URL TOP 100

 ☑统计不同响应状态码的出现次数和对应百分比

 ☑分别统计不同4XX状态码对应的TOP 10 URL和对应出现的总次数

 ☑给定URL输出TOP 100访问来源主机


### 任务1


 **安装`imagemagick`和`shellcheck`**

    sudo apt-get update
    sudo apt-get install shellcheck
    sudo apt-get install imagemagick

**通过scp的方式把3张不同格式的图发送到虚拟机上**

    scp 1.jpg cuc@192.168.56.101:/home/cuc/4chap/
    scp 2.png cuc@192.168.56.101:/home/cuc/4chap/
    scp 3.svg cuc@192.168.56.101:/home/cuc/4chap/

![](img/scp-3.jpg)

**执行效果如下**

    bash task01.sh -h

 ![1h](img/-h.jpg)

    bash task01.sh -r 50

 ![1R](img/-r.jpg)

    bash task01.sh -a 50 zsq

 ![水印](img/50zsq.jpg)

    bash task01.sh -add_1 A

 ![前缀名](img/Aad.jpg)

    bash task01.sh -add_2 a

 ![后缀名](img/2Aad.jpg)

    bash task01.sh -c

 ![修改类型](img/-c.jpg)

### 任务2

 码2[task02.sh](code/task02.sh)

 查看[task02最终效果](task02_result.md)

### 任务3

 码3[task03.sh](code/task03.sh)

 查看[task03最终效果](task03_result.md)


### 参考链接

[参考配置vs](https://www.pianshen.com/article/46881682669/)


[韩涛同学的作业链接](https://github.com/CUCCS/2022-linux-public-HantaoGG/tree/task0x04)

[jpg格式图片进行图片质量压缩](https://blog.csdn.net/jiangxinyu/article/details/1698997)


[正则表达式在线匹配](https://c.runoob.com/front-end/854/)


