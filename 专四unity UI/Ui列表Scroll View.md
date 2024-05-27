# Ui列表Scroll View


Scroll View 是unity Ui中的列表在在创建它时有三个子对象 

1. Viewprot 是列表中的内容我们对内容的一些修改都在这里进行,content是他的子类我们一般会添加两个组件在它身上 他们分别是Grid Layout Group 网格布局 它的意思是列表中的内容会按照网格的形状平铺在列表上,并且可以添加间距使得更加美观. 还有一个组件是Content Size Fitter 他的意思是内容大小筛选器它的作用是列表会根据你图片的数量向下延申,从而达到一个展示完全的效果.
2. Scrollbar Horizontal 水平滚动条 可以对水平的滚动条进行一些调节
3. Scrollbar Vertical 垂直滚动条 同上

通常我们列表中的图片会作为子对象放在Viewprot 下面.
显示的图片我们用预制体来做这个是预制体是挂在的脚本
![[./_resources/Ui列表Scroll_View.resources/unknown_filename.png|461x0]]
这个是管理界面.
![[./_resources/Ui列表Scroll_View.resources/unknown_filename.1.png|401x0]]
ins 的两个数字重载第一个参数的对象第二个是挂载的父类

