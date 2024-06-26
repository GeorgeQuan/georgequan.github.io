# OSI七层模型 OSI(国际标准化组织)


首先让我们来介绍七层模型都有哪七层 并且简单介绍一下他们的功能
1 应用层     网络服务与最终用户的一个接口（可理解为人机交互界面）
2 表示层     数据的表示,安全,压缩
3 会话层     建立,管理,终止对话
4 传输层     定义传输数据的协议端口号,以及流控和差错校验
5 网络层     进行逻辑地址寻址,实现不同网络之间的路径选择
6 数据链条层     建立逻辑连接,进行硬件地址寻址,差错校验等功能
7 物理层    建立,维护,断开物理连接

接下来让我们举个例子
小A通过计算机的电脑端的微信给小B发消息
应用层
最直观的理解就是人机交互界面,或者说是系统程序窗口,把消息输入进电脑微信软件
表示层

计算机如何处理消息,答案就是翻译,计算机是理解不了人类的语言的,所以计算机会把你发送的消息转换成二进制自己能读懂的语言.当然表示层还有其他的功能,例如安全加密和压缩等.(表示层数据处理)
会话层
计算机知道你要发送的东西之后,就要准备发送了,那么,第一步就是要找到小B,并且和对方建立会话关系,直接理解:会话层属于软件层面,允许不同机器上的用户之间建立会话关系.
传输层
传输层可以理解为同一个软件中的两个端口进行数据传输,我用微信发消息,你也需要用微信来接收,那么就是电脑端微信用户之间的传输.
网络层
传输层已经准备好了之后,可是我们知道微信的用户成千上万,我们要怎么实现小A就能发送到小B的微信上面呢,这就需要网络层的IP地址了.只要我们知道了小B的ip地址,就可以选择最佳路线进行准确的数据传输了.
数据链条层
网路层接受到数据后需要继续往下传输,需要使用工具,就是数据链条层的网卡,继续进行传输
物理层
数据达到物理层后,变成信号传输.
数据到达目标主机后,开始进行一个逆向的过程.
654321这样反过来在显示到小B的电脑上

![[./_resources/OSI七层模型_OSI(国际标准化组织).resources/unknown_filename.png]]
![[./_resources/OSI七层模型_OSI(国际标准化组织).resources/unknown_filename.1.png]]
![[./_resources/OSI七层模型_OSI(国际标准化组织).resources/unknown_filename.2.png]]
第一层：物理层。
是参考模型的最低层。该层是网络通信的数据传输介质，由连接不同结点的电缆与设备共同构成。主要跟功能是：利用传输介质为数据链路层提供物理连接，负责处理数据传输并监控数据出错率，以便数据流的透明传输。传输数据的单位是比特（Bits）

机械性能：接口的形状，尺寸的大小，引脚的数目和排列方式等；

电气性能：接口规定信号的电压、电流、阻抗、波形、速率好平衡特性等；

工程规范：接口引脚的意义、特性、标准。

工作方式：确定数据位流的传输方式，如：半双工、全双工等。

物理层协议：美国电子工业协会（EIA）的RS232/RS422/RS423等；

国际电报电话咨询委员会（CCITT）的X.25/X.21等；

物理层的数据单位是位（BIT），典型设备时集线器HUB。

这主要是和硬件有关，与软件关系不大。

第二层：数据链路层。
是参考模型的第二层。主要功能是：在物理层提供的服务基础上，在通信的实体间建立数据链路连接，传输的数据单位是“帧”，并采用差错控制与流量控制方法，使有差错的物理线路变成无差错的数据链路。

链路层屏蔽传输介质的物理特征，使数据可靠传送。

内容包括介质访问控制、连接控制、顺序控制、流量控制、差错控制和仲裁协议等。

链路层协议有：协议有面向字符的通讯协议（PPP）和面向位的通讯协议（HDLC）。

仲裁协议：CSMA/CD(Carrier Sense Multiple Access with Collision Detection)、Token Bus、Token Ring

链路层数据单位是帧，实现对MAC地址的访问，典型设备是交换机SWITCH。

第三层：网络层。
是参考模型的第三层。主要功能是：为数据在节点之间传输创建逻辑链路，通过路由选择算法为分组通过通信子网选择最适当的路径，以及实现拥塞控制、网络互连等功能。

网络层管理连接方式和路由选择。

连接方式：虚电路和数据报服务。

虚电路是面向连接的，数据通讯一次路由，通过会话建立的一条通路。数据报是非连接的，每个数据报都有路由能力。网络层的数据单位是包，使用的是IP地址，典型设备时路由器Router。

这一层可以进行流量控制，但流量控制更多的是使用第二层或第四层。

第四层：传输层。
是参考模型的第四层。主要功能是：向用户提供可靠地端到端服务，处理数据包错误、数据包次序，以及其他一些关键传输问题。传输层向高层屏蔽了下层数据通信的细节。因此，它是计算机通信体系结构中关键的一层。

提供端到端的服务，可以实现流量控制、负载均衡。

传输层信息包括端口、控制字和校验和。

传输层协议主要是TCP和UDP。

传输层位于OSI的第四层，这层使用的设备时主机本身。

第五层：会话层。
是参考模型的第五层。主要功能是：负责维扩两个结点之间的传输连接，以便确保点到点传输不中断，以及管理数据交换等功能。

会话层主要内容时通过 绘画进行身份验证、绘画管理和确定通讯方式。一旦建立连接，会话层的任务就是管理会话。

第六层：表示层。
是参考模型的第六层。主要功能是：用于处理在两个通信系统中交换信息的表示方法，主要包括数据格式变换、数据加密与解密、数据压缩与恢复等功能。

表示层主要是解释通讯数据的意义，如代码转换、格式变换等，使不同的终端可以表示。

还包括加密与解密、压缩与解压等。

第七层：应用层。
是参考模型的最高层。主要功能是：为应用软件提供了很多服务，比如文件服务器、数据库服务、电子邮件与其他网络软件服务。

应用层应该是直接面向用户的程序或服务，包括系统程序和用户程序，比如www、FTP、DNS、POP3和SMTP等都是应用层服务。

数据再发送时是数据从应用层至物理层的一个大包的过程，接收时是数据从物理层至应用层的一个解包过程。

从功能角度可以分为三组：1/2层解决网络通信问题，3/4层解决传输问题，5/6/7层处理对应用进程的访问。

从控制角度可分为二组：1/2/3层是通信子网，4/5/6/7是主机控制层。
原文链接：<https://blog.csdn.net/CN_TangZheng/article/details/102476750>

