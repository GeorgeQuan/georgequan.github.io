# unity 小拓展


![[./_resources/unity_小拓展.resources/unknown_filename.png|463x0]]

轮子跟着小汽车旋转![[./_resources/unity_小拓展.resources/unknown_filename.1.png]]
摄像机平滑移动 
![[./_resources/unity_小拓展.resources/unknown_filename.5.png|454x0]]
在玩家附近召唤小兵
三角函数 
球一个顶点的坐标(x,y)
弧度=2\*派/小兵的数量;=2\*mathf.pi/number(这是一个数量) 2派就是360度
x=r\*mathf.cos(float 这是一个弧度);
y=r\*mathf.sin(float 一样是弧度);
r 是半径
![[./_resources/unity_小拓展.resources/unknown_filename.2.png]]
angle 求得是弧度num 是数量

unity 中自带的类似与字典的小东西(PlayerPrefs)他也是一个键值对组合 优点是就算程序结束一样可以保留之前输入的值  缺点是一样的建只能有一个数并且不能储存容器类型的东西
![[./_resources/unity_小拓展.resources/unknown_filename.3.png|70x0]]
如何用鼠标控制人物移动(摄像机射线)
# invokRepeating
InvokeRepeating (调用的方法,延迟多少秒开始调用,每隔几秒调用一次)
Invoke("函数",延迟执行时间)
这里需要注意Invoke 和 InvokeRepeating 调用的方法必须是void类型且必须无参。
如果想关闭延迟函数的话 CancelInvoke("Printtext");
Cancellnvoke  是Monobehaver 中的方法,用于关闭延迟函数,参数是方法名称
如果不写参数的话会关闭脚本中所有的延迟函数

unity中种子的设置方法
![[./_resources/unity_小拓展.resources/unknown_filename.4.png|224x0]]
失活所有子类小方法
![[./_resources/unity_小拓展.resources/unknown_filename.6.png|197x0]]
获取当前场景名字
![[./_resources/unity_小拓展.resources/unknown_filename.7.png|163x0]]
扇形子弹
![[./_resources/unity_小拓展.resources/unknown_filename.8.png|528x0]]

![[./_resources/unity_小拓展.resources/unknown_filename.9.png|563x0]]
如何让一个物体跟随鼠标进行移动呢![[./_resources/unity_小拓展.resources/unknown_filename.10.png|361x0]]

如果你想敌人随机移动时出现了移动方向的问题,一定要查看坐标系是否正确.

 如果导航报错说太近或太远 最好的解决方法是把预制体的坐标清零在执行,也可以使用Instantiate的重载 **在他被生成的时候就修改他的位置.因为预制体自带的坐标大于导航地点的位置**

**int 动画在连线的时候要考虑是否能在两个动画之间随机切换,如果他们两个之间没有连线的话就会出现切换不过去的情况导致一种在执行一个动画或抽搐**


