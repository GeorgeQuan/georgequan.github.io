在Unity中，乒乓函数（PingPong）是一种常用的数学函数，用于在指定的时间范围内循环地从一个值到另一个值，然后再返回。向乒乓球一样来回运动
他给我们提供了两个参数1(t)我们叫他时间值2(length)我们叫他周期长度

```c#
float pingPongValue = Mathf.PingPong(Time.time * speed, 10f);
我们喜欢把t的位置放进时间通过乘以一个速度来增加乒乓增加和减少的速度
这里我们设置Length为10 这意味着这个乒乓函数会返回给我一个0-10之间的数字
注意乒乓函数无法指定初始数字都是从0开始的
当t小于10时乒乓函数会返回给你t的值1-10
当t大于最大数的时候乒乓函数就会开始逐渐变小10-1 这样一直循环达到一个一直往复的效果
```
现在我需要让一个物体往返运动我可以写
```c#
cube.position=new Vector3(Mathf.PingPong(Time.time*speed,10),0,0);
这样这个物体就会在x轴0-10 之间进行往返运动
```
这种方法也使用在缩放
乒乓函数可以在很多场景中使用，以下是一些常见的应用场景：

1. 游戏动画：乒乓函数可以用于控制游戏中的动画效果。例如，可以使用乒乓函数来实现角色的来回移动、物体的振动效果、水波的波动等。
    
2. 路径动画：乒乓函数可以用于创建物体沿着指定路径往返移动的动画效果。通过在路径上使用乒乓函数，可以使物体以平滑的方式在路径的两个端点之间来回移动。
    
3. 粒子系统：乒乓函数可以用于控制粒子系统中粒子的运动轨迹。通过将乒乓函数的返回值应用于粒子的位置、速度或加速度等属性，可以实现粒子在指定范围内的来回运动。
    
4. UI动画：乒乓函数可以用于创建UI元素的动画效果。例如，可以使用乒乓函数来实现按钮的闪烁效果、文本的渐隐渐现效果等。
    
5. 物体交互：乒乓函数可以用于处理物体之间的交互效果。例如，在游戏中的碰撞检测中，可以利用乒乓函数来控制物体的反弹运动，使其在碰撞时以乒乓球的方式反弹。
    
6. 游戏设计中的循环效果：乒乓函数可以用于创建循环的游戏效果。例如，可以使用乒乓函数来实现循环背景音乐的渐变、循环关卡的设计等。