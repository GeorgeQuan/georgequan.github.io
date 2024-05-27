# Socket 网络通信类


socket 自带的方法 (套接字)

1. Connect：连接到远程主机。用于客户端，通过指定远程主机的IP地址和端口号来建立与服务器的连接。
2. Bind：将Socket绑定到指定的本地IP地址和端口号。用于服务器端，指定服务器要监听的本地地址和端口。
	
3. Listen：开始监听连接请求。用于服务器端，指定Socket开始接受连接请求，并设置最大连接请求队列的长度。
4. Accept：接受来自客户端的连接请求，并创建一个新的Socket实例用于与客户端通信。
5. Send：发送数据到已连接的Socket。用于发送字节流数据或字符数据。
6. Receive：从已连接的Socket接收数据。用于接收来自远程主机的字节流或字符数据。
7. Close：关闭Socket连接，并释放相关资源。
8. Shutdown：禁用Socket的发送或接收功能。可以选择禁用发送、接收或同时禁用两者。
9. GetHostEntry：根据主机名或IP地址获取主机的信息，包括IP地址、别名等。
10. GetHostName：获取本地计算机的主机名。
11. BeginConnect 和 EndConnect：异步地连接到远程主机，并在连接完成时使用回调函数进行处理。
12. BeginSend 和 EndSend：异步发送数据到已连接的Socket，并在发送完成时使用回调函数进行处理。
13. BeginReceive 和 EndReceive：异步从已连接的Socket接收数据，并在接收完成时使用回调函数进行处理。
```c# 
	//也是socket异步的使用 这里使用的是SendAsync 和Task await
	
      Socket socket = new Socket(default);
      byte[] data = Encoding.UTF8.GetBytes("QWQ");
      var sentCount = await socket.SendAsync(data, SocketFlags.None);

```

在socket 的构造函数里拥有三个枚举类型的参数(1 AddressFamily 用于添加套接字的地址,2 SocketType 用于选择套接字内的数据类型 3 套接字的协议)
[[AddressFamily(添加地址族) 套接字中的枚举地址类型|AddressFamily(添加地址族) 套接字中的枚举地址类型]]
[[定义套接字可以选择的数类型|定义套接字可以选择的数类型]]
[[定义套接字中包含的协议|定义套接字中包含的协议]]
套接字在网络通讯中起到了一个重要的作用, 我们把套接字比作一个插口用来实现客户端与服务器的连接.
![[./_resources/Socket_网络通信类.resources/unknown_filename.png|274x0]] 
在计算机编程中，"fd" 是文件描述符（File Descriptor）的缩写，它是用于标识打开的文件或者I/O设备的整数值。在Socket编程中，fd指的是用于标识网络套接字（Socket）的文件描述符。每个套接字在操作系统中都有一个唯一的标识符. 套接字描述符是一个整数值，用于在程序中标识和引用特定的套接字。它由操作系统分配并与每个套接字相关联。套接字描述符充当了程序和操作系统之间的接口，通过它，程序可以进行套接字的创建、读写操作、关闭等。

运行窗口输入Ipconfig 可以查看当前的网络地址

