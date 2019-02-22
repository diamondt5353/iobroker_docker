# iobroker_docker
本项目文件仅用于docker部署iobroker的初始化配置


docker部署iobroker方法



因为iobroker需要占用9000端口，所以安装的时候，就可能有的同学存在着端口冲突。


首先你需要确认主机的9000端口有没有被占用，自己也不确定的同学可以使用 netstat -tunlp 命令自行查询。



1、在任意位置新建一个名为iobroker的文件夹。
2、从本项目里面下载iobroker.json，objects.json，states.json这三个初始化配置文件，并放在iobroker文件夹下。
3、根据实际情况选择性运行如下命令。（切勿忘了把下面命令里面的路径替换成你自己的）

一、9000端口没被占用，部署iobroker命令

docker run --restart=always --name=iobroker -e TZ=Asia/Shanghai -v /&此处替换成你自己的实际路径&/iobroker:/opt/iobroker/iobroker-data --net=host buanet/iobroker 


二、9000端口已被占用，部署iobroker命令

docker run --restart=always --name=iobroker -e TZ=Asia/Shanghai -v /&此处替换成你自己的实际路径&/iobroker:/opt/iobroker/iobroker-data -p 8081:8081 -p 9099:9000 buanet/iobroker 


完成！



等待部署完成，在浏览器输入  http://"your_host_ip":8081 即可进入iobroker的web管理页面。
