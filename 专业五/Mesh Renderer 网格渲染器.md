# Mesh Renderer 网格渲染器


*  Materials(材质)

1. 颜色（Color）：材质的基本颜色，决定物体的外观。
2. 纹理（Texture）：用于将图像或纹理映射到物体表面，以增加细节和逼真度。纹理可以包括颜色纹理、法线贴图、高光贴图等。
3. 法线贴图（Normal Map）：通过修改法线向量，模拟物体表面的微小凹凸细节，以使表面看起来更加真实。
4. 光照模型（Lighting Model）：定义了物体如何对光源的照明做出反应，包括漫反射、镜面高光、环境光等。
5. 透明度（Transparency）：控制物体的透明度或半透明度，影响光线如何穿过物体。
6. 反射率（Reflectivity）：决定物体对光线的反射程度，影响物体的镜面反射效果。
7. 投射阴影（Shadow Casting）：指定物体是否投射阴影。   我们经常用Mesh 中的Materials.color来改变对象的颜色 
	

	Lighting 
	

1. CastShadows  [[MeshRenderer  Shadwo阴影模式|MeshRenderer  Shadwo阴影模式]]
	
2. Receive Shadows  它默认是关闭的状态 它的效果是是否接受其他物体的阴影照射   如果打开是它就会因为其他物体的阴影受到影响,而关闭后它就不会被其他物体的阴影照射到

