# MeshRenderer Shadwo阴影模式


当我们想调整一个3D模型的阴影状态是我们可以用 Mesh Renderer (网格渲染器)中的Lighting 下的Cast Shadows方法 这个方法是一个枚举类型的组件![[./_resources/MeshRenderer_Shadwo阴影模式.resources/unknown_filename.png|242x0]]在这个枚举中有四种模式     
on 为默认打开阴影
off 为关闭阴影 能看见模型而看不见阴影
Twosided  使用这个模式时物体不会考虑背对着光的情况,一般情况下效果和on一致 但是要注意 启用 Twosided 模式可能会增加阴影的计算和渲染开销，因为需要为所有面计算阴影。在性能敏感的情况下，请谨慎使用该设置。
shadwos only 为只显示阴影 只能看见阴影而看不见物体

