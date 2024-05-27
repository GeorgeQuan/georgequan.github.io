使用:
创建.proto 的文件,用VSC打开
下面是proto 语法
```c#
syntax = "proto3";

// 定义一个包含不同基本数据类型的消息
message ExampleMessage {
  // uint32 类型
  uint32 id = 1;

  // sint32 类型
  sint32 score = 2;

  // fixed32 类型
  fixed32 timestamp = 3;

  // sfixed32 类型
  sfixed32 price = 4;

  // int32 类型
  int32 age = 5;

  // bool 类型
  bool isActive = 6;

  // float 类型
  float height = 7;

  // double 类型
  double weight = 8;

  // string 类型
  string name = 9;

  // bytes 类型
  bytes data = 10;

  // 枚举类型
  enum Color {
    RED = 0;
    GREEN = 1;
    BLUE = 2;
  }
  Color favorite_color = 11;

  // 列表
  repeated string tags = 12;
}

```
这里是cmd 中生成.cs的写法双引号中为地址,后面是文件名字
protoc --csharp_out="D:\\MyWorld\\MyProtoBuffer\\" Plane.proto 

使用protoBuffer 类型需要的Google 包
NuGet 是.NET 生态系统中的包管理器,这个网址是所有包的管理器,你可以在这里找到所有你想下载的包,找到![[Pasted image 20240521223119.png]]
点击箭头所指的方向下载包,大部分包都是有依赖的,如果你把下载好的包拖进去发现报错的话,就在找缺少的包下载就行了
![[Pasted image 20240521224253.png]]
这里可以查看当前unity 版本的兼容级别,加载最大级别内的包类型,就可以了.

 plane.ToByteArray();//转换成buye[]
 Plane plane = Plane.Parser.ParseFrom(data);//从byte[]转换回来