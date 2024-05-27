# 专业3 day2


![[./_resources/专业3_day2.resources/unknown_filename.png]]

go.SetActive(!go.activeSelf)
go是一个游戏对象 go.activeself 会返回当前游戏对象的激活状态true false  go.setactive 会根据括号内的布尔值对游戏对象的激活状态进行改变;

* go.SetActive(!go.activeSelf) 的意思就是:**如果该游戏对象当前是激活状态,就把它设置为非激活状态;如果是非激活状态,就把它设置为激活状态。**

deltaTime在Unity中表示一帧的时间间隔,以秒为单位。
每一帧的deltaTime可能都是不同的,这取决于游戏运行时的帧率。

Translate 的用法
![[./_resources/专业3_day2.resources/unknown_filename.1.png]]![[./_resources/专业3_day2.resources/unknown_filename.2.png]]
![[./_resources/专业3_day2.resources/unknown_filename.3.png]]
vector3 的小用法
![[./_resources/专业3_day2.resources/unknown_filename.4.png]]
RotateAround 公转的小方法
![[./_resources/专业3_day2.resources/unknown_filename.5.png]]
![[./_resources/专业3_day2.resources/unknown_filename.6.png]]
自转 公转 移动
![[./_resources/专业3_day2.resources/unknown_filename.7.png]]
space.self 表示按照自身坐标进行移动
space.World表示按照世界坐标进行移动
Translate 是unity内封装好的移动的方法
Rotate
![[./_resources/专业3_day2.resources/unknown_filename.8.png]]

