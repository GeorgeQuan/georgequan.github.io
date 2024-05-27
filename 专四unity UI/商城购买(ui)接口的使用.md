# 商城购买(ui)接口的使用


要实现商城点击购买首先要实现接口,在ui上挂载的脚本是添加引用 ![[./_resources/商城购买(ui)接口的使用.resources/unknown_filename.png]]
添加引用后
![[./_resources/商城购买(ui)接口的使用.resources/unknown_filename.1.png]]
右键实现接口
![[./_resources/商城购买(ui)接口的使用.resources/unknown_filename.2.png|475x0]]
在这个函数中实现点击后触发的事件

当 MonoBehavior 希望接收到某些事件时, 需要实现 UnityEngine.EventSystems 下的接口
例如, 当一个 MonoBehavior 实现 IPointerDownHandler 的接口时, 它就可以处理指针按下的事件, 其他接口诸如 IPointerUpHandler, IPointerOverHandler 也是如此

|     |     |     |
| --- | --- | --- |
| 接口名称 | 翻译  | 描述  |
| IPointerDownHandler | 指针按下 | 鼠标按下或者移动端屏幕触摸时引发 |
| IPointerUpHandler | 指针抬起 | 鼠标抬起火移动端屏幕抬起时引发 |
| IPointerClickHandler | 指针单击 | 鼠标按下并抬起或者移动端触摸并抬起时引发 |

文档: \[\]

