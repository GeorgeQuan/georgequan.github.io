一、NavMeshSurface组件
该组件主要用于烘焙特定的导航网格代理类型的寻路区域
在旧版中，我们使用Navigaiton的Bake选项卡来烘焙网格，所有烘焙的网格数据都是根据Bake中参数的设置来烘焙的，所以烘焙的路径只能适用一种代理类型（如果你觉得有点抽象请往下看，下面会举例子）
![[Pasted image 20240408225843.png]]


1.Agent Type | 根据Agent来烘焙特定网格数据
上面我们已经说过了，旧版烘焙的网格数据只能适用于一种代理类型，而新版则可以适用多种类型的代理，这个适用的方法就是多烘焙几个网格数据不就行了hhh

这里我们可以举一个恰当的例子，比如我要做RTS游戏，当我选中不同的兵种并指定目的地时，这些兵种就会开始寻找并前往指定点，如果游戏地图很复杂，各种山川河流，各种残垣断壁。我们可以通过设置不同区域的代价来促使AI做出合理的选择，但是我们无法让不同兵种做出不一样的选择，因为所有的兵种挂载的都是相同的代理。

现在呢，我们通过NavMeshSurface组件可以给每一种代理都烘焙一个网格数据，这样就可以让不同兵种做出不同的选择，比如高个子无法穿越桥洞，只能绕道，而矮个子可以，比如坦克无法行驶在小道上，而摩托车可以。

如果我们想要做到上述几点，那么我们需要这样做
1.通过Navigation的Agents来设置不同的代理类型

这里我设置了两种类型，摩托和坦克，摩托半径0.3，坦克半径1.5，其他数据随意
![[Pasted image 20240408225916.png]]

2.我们创建好测试场景，蓝色是摩托、红色是坦克
![[Pasted image 20240408225928.png]]


3.给每个测试方块设置代理组件，并修改它们的Agent Type类型，并且添加逻辑脚本指定目标
![[Pasted image 20240408225939.png]]


4.创建一个空物体，添加NavMeshSurface组件，要添加两个，一个用于烘焙摩托寻路网格、一个烘焙坦克寻路网格，如果有更多兵种，则需要为每一种网格代理类型烘焙不同的网格
![[Pasted image 20240408230236.png]]


5.大功告成，运行查看效果
![[Pasted image 20240408230248.png]]


2.Collect Objects & Include Layers
上面我们创建空物体并添加了NavMeshSurface组件，这时如果我们烘焙，则场景中所有物体都会受到该组件的影响，因为该组件默认选择全部烘焙
![[Pasted image 20240408230413.png]]


All Game Objects 就是烘焙所有的对象,可以选择下面的层级选择层级烘焙,
Volume 就是下面图的效果
Current Object Hierarchy 当前对象层级关系的对象进行烘焙
NavMeshModifier Component Only 挂载了NavMeshModifier 的组件进行烘焙
![[Pasted image 20240408230629.png]]


至于Include Layers参数则是通过层来确定烘焙，很简单，就不做解释了。

3.Use Geometry
![[Pasted image 20240408230716.png]]

Render Meshes(渲染网格) | Physics Colliders(物理碰撞体)
与使用渲染网格体选项相比，物理碰撞体可使AI更接近环境的物理边界（摘自官方文档，暂无其他解释，以后看懂了回来补上）

4.高级设置
![[Pasted image 20240408230835.png]]

参数	作用
Default Area	设置默认区域
Override Voxel Size	控制Unity处理NavMesh烘焙的准确度，不勾选则会自动计算，Unity会在烘焙速度与准确性之间做一个均衡，若你想要控制更偏向烘焙速度或准确性，则可以勾选此项，并手动计算出合适的值，但可能会导致烘焙不准确，代理无法通行，请自行判断。（例图1）
Override Tile Size	控制烘焙Tile的大小，默认256体素，Tile越小，导航网格体被分割的碎片就越多，这有时会导致非最佳路径，但这样可能保持较低内存使用量（例图2）
Minimum Region Area	允许剔除与较大导航网格体断开连接的小区域，烘焙时不会保留曲面尺寸小于该指定值的网格区域（例图3）
例图

例图1
![[Pasted image 20240408230900.png]]

例图2
![[Pasted image 20240408230911.png]]

例图3
![[Pasted image 20240408230922.png]]

5.注意点
1.当使用NavMeshSurface组件烘焙好对应代理的网格数据后，无需使用原本的Navigation的Bake进行烘焙

2.使用NavMeshSurface组件烘焙时，物体无需设置Navigation Static，旧版是必须的

3.需要注意当你使用一种新的Agent类型时，必须有对应的烘焙数据，否则会报错，旧版则是默认使用同一种Agent类型

二、NavMeshLink组件
该组件主要来链接不同导航网格的表面，默认情况下，AI会从入口边缘的最近位置穿越链接。对于旧版系统，则可以使用Off Mesh Link组件来生成外链接，或者通过Navigation的Object，勾选Generate OffMeshLinks来根据设置自动生成。
![[Pasted image 20240408230944.png]]


参数
参数	作用
Agent Type	可以使用链接的代理类型
Start Point	链接起点
End Point	链接终点
Swap	将起点和终点的位置互换
Align Transform	如果点击此按钮，则轴朝向始终同终点对齐
Width*	该链接的显示宽度
Cost Modifier	当该值非负时，使用该链接的成本等价于该值乘以NavMeshLink端点之间的欧式距离（Euclidean Distance）
Auto Update Position*	如果启用此属性，当端点动态移动时（运行时移动端点位置），链接将重新连接到导航网格。如果禁用，即使移动了端点，链接也将保持在其起始位置。
Bidirectional	如果启用此属性，则可以双向遍历，否则，只能按照从Start到End的方向遍历链接
Area Type	该链接的区域类型（会影响AI使用该链接的成本判断）
欧式距离 Euclidean Distance
上表中，当Cost Modifier值是非负数时，成本计算需要两端点之间的欧式距离乘以这个值才能得出实际成本。下面是欧式距离的相关介绍。（实际使用大可不必认真计算，有个大概值即可）
欧氏距离定义：欧氏距离是一个通常采用的距离定义，它是在n维空间中两个点之间的真实距离。
在二维和三维空间中的欧式距离的就是两点之间的距离。

公式：
![[Pasted image 20240408231031.png]]

演示
AI之所以会选择边缘处，是因为我设置了Cost Modifier是一个个递增的，AI选择了成本最低的路径
![[Pasted image 20240408231112.png]]



原文链接：https://blog.csdn.net/weixin_43147385/article/details/127936636