## Basic knowledge in k8s

### k8s的部署架构

![Image](img/00/1.png)

k8s有两类资源，分别是master和node。
1. master: 负责管理整个集群，例如，对应用进行调度(扩缩)、维护应用期望的状态、对应用进行发布等。
2. node: 集群中的宿主机（可以是物理机也可以是虚拟机），每个node上都有一个agent，名为kubelet，用于跟master通信。同时一个node需要有管理容器的工具包，用于管理在node上运行的容器(docker或rkt)。一个k8s集群至少要有3个节点。kubelet通过master暴露的API与master通信，用户也可以直接调用master的API做集群的管理。

### k8s的对象

#### pod

1. k8s中的最小部署单元，不是一个程序/进程，而是一个环境(包括容器、存储、网络ip:port、容器配置)。其中可以运行1个或多个container（docker或其他容器），在一个pod内部的container共享所有资源，包括共享pod的ip:port和磁盘。
2. pod是临时性的，用完即丢弃的，当pod中的进程结束、node故障，或者资源短缺时，pod会被干掉。基于此，用户很少直接创建一个独立的pods，而会通过k8s中的controller来对pod进行管理。
controller通过pod templates来创建pod，pod template是一个静态模板，创建出来之后的pod就跟模板没有关系了，模板的修改也不会影响现有的pod。

