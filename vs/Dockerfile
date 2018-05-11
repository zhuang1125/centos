# It could have some security problem
#选择一个已有的os镜像作为基础  
FROM centos
   
# 镜像的作者  
MAINTAINER zhangzhuang 
   
# 安装openssh-server和sudo软件包，并且将sshd的UsePAM参数设置成no  
RUN yum install -y openssh-server sudo  wget && \
RUN mkdir  /opt/software/
RUN cd  /opt/software/   
RUN    wget /P /opt/software/ https://download.epicgames.com/Builds/UnrealEngineLauncher/Installers/EpicGamesLauncherInstaller-2.12.19-3269887.msi
#RUN    wget /P /opt/software/ http://mirrors.tuna.tsinghua.edu.cn/apache/hadoop/common/hadoop-2.8.1/hadoop-2.8.1.tar.gz 
#RUN     wget /P /opt/software/ http://mirrors.tuna.tsinghua.edu.cn/apache/hadoop/common/hadoop-2.7.4/hadoop-2.7.4.tar.gz  
#RUN     wget /P /opt/software/ https://d3kbcqa49mib13.cloudfront.net/spark-2.2.0-bin-hadoop2.7.tgz  
#RUN     wget /P /opt/software/ https://d3kbcqa49mib13.cloudfront.net/spark-2.1.0-bin-hadoop2.7.tgz 
#RUN     wget /P /opt/software/ https://d3kbcqa49mib13.cloudfront.net/spark-2.0.2-bin-hadoop2.7.tgz 
#RUN     wget /P /opt/software/ https://d3kbcqa49mib13.cloudfront.net/spark-2.0.1-bin-hadoop2.7.tgz  
#RUN     wget /P /opt/software/ https://d3kbcqa49mib13.cloudfront.net/spark-2.0.0-bin-hadoop2.7.tgz 
#RUN     wget /P /opt/software/ http://mirrors.hust.edu.cn/apache/hive/hive-2.3.0/apache-hive-2.3.0-bin.tar.gz 
#RUN     wget /P /opt/software/ http://mirrors.hust.edu.cn/apache/hive/hive-2.2.0/apache-hive-2.2.0-bin.tar.gz  
#RUN     wget /P /opt/software/ http://mirrors.hust.edu.cn/apache/hive/hive-2.1.1/apache-hive-2.1.1-bin.tar.gz  
#RUN     wget /P /opt/software/ http://mirrors.hust.edu.cn/apache/hive/hive-1.2.2/apache-hive-1.2.2-bin.tar.gz
    
# sed -i 's/UsePAM yes/UsePAM no/g' /etc/ssh/sshd_config   && \
#安装openssh-clients
 yum  install -y openssh-clients  && \
   
# 添加测试用户root，密码root，并且将此用户添加到sudoers里  
 echo "root:root" | chpasswd   && \ 
 echo "root   ALL=(ALL)       ALL" >> /etc/sudoers   && \
  
# 下面这两句比较特殊，在centos6上必须要有，否则创建出来的容器sshd不能登录  
 ssh-keygen -t dsa -f /etc/ssh/ssh_host_dsa_key    && \
 ssh-keygen -t rsa -f /etc/ssh/ssh_host_rsa_key    && \
   
# 启动sshd服务并且暴露22端口  
 mkdir /var/run/sshd   
EXPOSE 22  
CMD ["/usr/sbin/sshd", "-D"]
