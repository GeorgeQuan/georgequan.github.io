# 如何用image来做小地图


首先创建 我们需要一个 camera 一个image 一个 great. Render...渲染贴图 一个材质球Material
1 把我们创建好的渲染贴图放到camera选项下的Target Texture 里面(相当于相机把他看到的渲染在了这个图片上)
![[./_resources/如何用image来做小地图.resources/unknown_filename.2.png|59x0]]
2 进行材质球设置把材质球的Shader选项 改成unlit ->Texture  然后把贴图拖进select的框里面
 ![[./_resources/如何用image来做小地图.resources/unknown_filename.3.png|98x0]]![[./_resources/如何用image来做小地图.resources/unknown_filename.1.png|66x0]]
3 把我们设置好的材质球放到渲染贴图的Material选项里

小地图摄像机跟随的小代码
![[./_resources/如何用image来做小地图.resources/unknown_filename.png|196x0]]

