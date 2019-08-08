# zookeeper
安装配置范例：https://blog.csdn.net/xiang2lin/article/details/80616453 

 

 

主要配置项及使用说明：

        tickTime=2000   # The number of milliseconds of each tick

        initLimit=10

        syncLimit=5     #syncLimit标识 Leader 与 Follower 之间发送消息，请求和应答时间长度，最长不能超过多少个 tickTime 的时间长度

        dataDir=/usr/local/zookeeper/data         #zookeeper保存数据的目录，也是配置文件所在目录

        ZOO_LOG_DIR=/usr/local/zookeeper/logs     #日志文件保存目录

        clientPort=2181                           #客户11端连接 Zookeeper 服务器的端口，Zookeeper 会监听这个端口，接受客户端的访问请求

        

        /*

          # zookeeper安装份单机模式、伪集群模式(同一集群中的服务器的都放在同一物理机上运行，通过配置不同IP端口实现)、集群模式。

          # 集群模式时，集群服务器配置格式为server.A=B：C：D。A为数字表示第几台服务器，B为IP，C为与集群Leader通信端口，

            D为Leader挂掉后重新推举Leader时的通信端口。当集群有多个服务器时就会有多个这样形式的配置。配置示例如下所示。

          # 集群中的同一成员服务器的C与D不能相同。伪集群模式时，因为IP已相同，故不同成员服务器的C、D应该互不相同。集群的编号A必须从0起算。

          # 组织集群时需要在dataDir配置的路径下增加一个名称为 myid 的文件，文件内容为该服务器的编号A

          # 特别注意：只有集群中超过半数服务器正常运行后，"bin/zkServer.sh  status"命令查询才不会报异常。

        */

        server.0=127.0.0.1:2880:3880

  

伪集群模式部署方法：

        一台机子上复制出多份zookeeper软件，各自配置好使用不同的dataDir路径，配置好集群服务设备的不同通信端口号（server.A=B：C：D）。
