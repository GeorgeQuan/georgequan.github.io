# All DoTween 用法


在DoTween  中的方法一般都会返回一个Tweener 的动画对象 我们可以用这个动画对象进行对动画的一系列操作

1 在 DOTween 中，Tweener 是一个代表动画的对象。它用于控制和管理动画的各个方面，如播放、暂停、重启、停止、设置延迟、循环、回调等。
Tweener 是 Tween 类的子类，而 Tween 是 DOTween 中所有动画类型的基类。Tweener 是 Tween 的一种特殊类型，用于处理属性动画，例如颜色、位置、旋转等属性的渐变。
在 DOTween 中，当你调用类似于 DOFade、DOMove、DORotate 等方法时，它们会返回一个 Tweener 对象，表示生成的动画。你可以使用该 Tweener 对象来控制动画的执行和参数设置。
下面是一些常用的 Tweener 方法和属性：

* Play()：播放动画。
* Pause()：暂停动画。
* Rewind()：将动画重置为其初始状态。
* Restart()：重新播放动画。
* Complete()：立即完成动画。
* SetDelay(float delay)：设置动画的延迟时间。
* SetLoops(int loops, LoopType loopType)：设置动画的循环次数和循环类型。
* OnComplete(Action callback)：在动画完成时执行回调函数。
* OnUpdate(Action<float> callback)：在动画更新时执行回调函数，传递动画的进度作为参数。

通过这些方法和属性，你可以控制动画的播放、暂停、重启，设置延迟和循环，以及在特定事件发生时执行回调函数。
 下面让我们来仔细介绍一下ToTween中封装好的一些动画效果

1.  DOFade   这个方法用作控制目标对象的不透明度渐变动画, 它接收两个参数第一个是目标透明度 从0到1  零是完全透明 而一是完全不透明 第二个是动画的持续时间 例如，image.DOFade(0f, 1f) 将使 image 图片的不透明度从当前值渐变为完全透明，持续时间为1秒 注意该方法不会自动设置图片的透明度,要在图片上自己设置初始透明度
	
2. DoMove  用做控制目标对象的位置移动动画.该方法接收两个参数 第一个是目标位置 接收一个v3类型的变量作为目标点,而第二个参数是动画持续时间。它通常用在三维物体上 用transfrom.DOmove。但它也可以用在二维物体上 但是还是接收一个三维向量我们需要把三维向量的Z轴设置为当前对象本身的Z轴这样才能够正确的显示.myObject.DOMove(new Vector3(2f, 0f, myObject.position.z), 1f); 像这样
	
3. DoRotate 用做控制目标对象的旋转动画 它同样接收两个参数 第一个是目标旋转值 接收一个三维向量,第二个同样是动画的持续时间      transform.DORotate(new Vector3(0f, 90f, 0f), 1f) 将使目标对象在Y轴上平滑旋转90度，持续时间为1秒。同样DORotate 也可以作用在二维游戏对象上 ![[./_resources/All_DoTween_用法.resources/unknown_filename.png|207x0]]
	
4. DOScale 用做控制目标对象的缩放动画 transform.DOScale(new Vector3(2f, 2f, 2f), 1f); // 将目标对象的缩放从当前值平滑地变为 (2, 2, 2)，持续时间为1秒![[./_resources/All_DoTween_用法.resources/unknown_filename.1.png|261x0]]
	
5. DOColor：用于控制目标对象的颜色渐变动画。![[./_resources/All_DoTween_用法.resources/unknown_filename.2.png|307x0]]
	
6. DOJump：用于控制目标对象的跳跃动画，模拟物体跳跃的效果。![[./_resources/All_DoTween_用法.resources/unknown_filename.3.png|354x0]]
	
7. DOPath：用于控制目标对象沿指定路径移动的动画。 dopath 的用法比较复杂 首先它接受的第一个参数是一个v3类型的数组里面包含了目标对象移动的所有点位对象会按照数组内的坐标顺序来依次进行移动,第二个参数是动画持续的时间,第三个动画移动的类型(pathtype)(1)Linear：线性路径，物体沿着路径的点依次移动。(2)CatmullRom：Catmull-Rom 样条路径，物体将在路径点之间进行平滑插值。他还拥有第四个参数的重载(Pathmode) 用于指定路径的模式常见的模式包括(1)Full3D：在三维空间中完整移动物体，包括位置和旋转。(2)TopDown2D：在二维平面上移动物体，只改变位置，不改变旋转。
	
8. DoLocalMove   它的用法和DoMove 的用法基本一样但还是有一些区别,因为DolocalMove 是基于自身坐标系进行的移动所以它会受到父对象的影响![[./_resources/All_DoTween_用法.resources/unknown_filename.4.png|310x0]]
	
9. DOShakePosition 是 DOTween 库中的一个方法，用于在指定的持续时间内使物体以震动的方式在位置上产生动画效果。它可以用于在游戏开发中模拟震动、颤动或抖动的效果。![[./_resources/All_DoTween_用法.resources/unknown_filename.5.png|188x0]]他还拥有一种重载![[./_resources/All_DoTween_用法.resources/unknown_filename.6.png|160x0]]
	
10. 在DOTween库中，To 方法用于在指定的时间内对一个属性或字段进行动画化的渐变操作。它允许你从一个初始值过渡到一个目标值，并且可以在指定的时间段内平滑地插值过渡。![[./_resources/All_DoTween_用法.resources/unknown_filename.7.png]]setter设置器 我们可以理解dotween 在一直调用它他会从前到后获取起点到目标点的位置赋值给对象从而达到一个平滑的效果

