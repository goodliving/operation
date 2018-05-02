### 概述

这是关于软件项目的开发、测试、上线的流程描述，以及基础设施的组成。

### 技术栈

* kubernetes
* coredns
* flannel
* traefic
* drone
* harbor
* robotframework
* ceph
* ldap
* rocket.chat
* FLK
* mocha
* locust
* avajs

### 业务场景

项目的基础设施采用目前主流的`kubernetes`，设置不同的命名空间来区分开发、测试、运维的资源，首先开发完成业务功能的编写，提交代码，通过`drone`来构建，完成单元测试，等待通过之后，将业务镜像推送到`harbor`中，然后通过插件在`kubernets`中构建整个业务环境，最后运行冒烟测试，通过后，将信息通知给测试。

测试接收到该信号，在集群的测试环境中根据提供的升级文档完成环境的安装，之后开始业务的测试以及一系列回归测试。在通过业务测试以及环境安装，之后将该升级方案提交给运维。

运维接收到升级方案后，进行线上环境的升级，待升级后，验证监控指标和业务功能，这样就完成整个版本的迭代。

### 具体功能

kubernets是整个系统的基础架构，`coredns`提供域名服务，`flannel`提供路由规则，`traefic`提供负载均衡和外部服务，`drone`提供持续集成能力，`harbor`提供镜像仓库以及镜像安全扫描，`ceph`提供外部存储，`ldap`提供权限认证，`robotframework`编写接口自动化用例，`mocha`编写web段自动化用例，`rocket.chat`提供团队交流功能，`FLK`提供线上业务运维、`locust`压力负载测试工具，`avajs`自动化测试工具。