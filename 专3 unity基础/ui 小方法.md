# ui 小方法


我们在创建ui对象的时候 会出现两个绑定在此ui一起的游戏对象不要删除. 我们的ui的对象都创建在Apple里面. 
panel 也是ui中很关键的一个对象 他的意思是面板 我们的ui对象写在panel 就会呈现以下效果
 ![[./_resources/ui_小方法.resources/unknown_filename.2.png]]
下面是老师上课讲过的一些ui 的基本用法和兰姆达表达式
兰姆达表达式就是没有函数明的函数 格式如下
( 这里放参数 直接写名字 表达式会根据需要的参数来变成相应的类型)=>{}
Unity 中的兰姆达表达式(Lambda Expression)是一种匿名方法的便捷表示法,可以用更简洁的语法表示一个方法。
![[./_resources/ui_小方法.resources/unknown_filename.png]]
![[./_resources/ui_小方法.resources/unknown_filename.1.png]]关于血条的ui 小方法
通常我们把image 用来当作玩家或敌人的血条 下图中是image 的一些基础设置 Soure image 填充图片 当我们选择图片后才会出现imageType 图像类型选项  作为血条我们选择Filled(填充类型)  fillMEthod 填充模式我们选择Horizontal(水平模式) FillAMount 是血量显示的可以理解为减血条 掉血就是以这个做修改
通常为了更直观的看到掉血我们会再设置一个image 用来当作血量的背景来使用方便我在掉血时观看血量的情况 
通常血量作为背景的子对象,这样只要把背景跟随玩家就可以实现了
hp.transform.position = Camera.main.WorldToScreenPoint(transform.position)+Vector3.up\*30;//把玩家的世界坐标转换成image要用到的屏幕坐标 这里的30是像素
![[./_resources/ui_小方法.resources/unknown_filename.3.png|170x0]]
![[./_resources/ui_小方法.resources/联想截图_20230903194201.png]]

