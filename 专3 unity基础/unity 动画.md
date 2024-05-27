# unity 动画


![[./_resources/unity_动画.resources/unknown_filename.png|603x0]]
动画不要加在玩家身上 ,不然玩家就不会移动了
animator controller  为需要移动的物体身上添加的组件 用great创建 
animator 老师给的动画身上自带animator 动画播放器 把调试好的动画控制器拖到动画播放器上就能实现动画播放![[./_resources/unity_动画.resources/unknown_filename.1.png|130x0]]拖到这里
如果你想实现动画循环播放在动画控制器中双击你想循环的动画,勾选LookTIme(环形时间)并点击下面的Apply(申请)就能实现循环播放的效果
如果你想为动画的切换添加条件点击![[./_resources/unity_动画.resources/unknown_filename.2.png|78x0]]就可以选择您想添加的条件类型  Trigger触发型一般用做攻击按下按键就执行
make transition 右键动画并且选择这个选项可以为动画之间建立练习点击线也可以为动画过渡增加条件
取消勾选线段中的![[./_resources/unity_动画.resources/unknown_filename.3.png|151x0]]选项就j=可以随时停止当前的动画播放进行下个动画的播放让动画的切换更加流畅

下面是用代码修改状态机的方法
![[./_resources/unity_动画.resources/unknown_filename.4.png|200x0]]

我们可以通过animator.enabled属性来实现暂停和播放动画给他false, 和 true;
完全停止动画的播放,但当我们想要完全定制并不保持当前进度时,我们可以StopPlayback 方法.

