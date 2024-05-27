![](https://docs.unity3d.com/uploads/Main/LineRenderer-example.jpg)

使用 Unity 的 Line Renderer 组件可以在 3D 空间中绘制直线或曲线。以下是使用 Line Renderer 的基本步骤和一些重要功能：

1. **创建 Line Renderer**: 创建 Line Renderer：
    - 在 Unity 菜单栏中，选择 `GameObject` > `Effects` > `Line` 来创建一个新的 Line Renderer 游戏对象。

2. **配置 Line Renderer**: 配置 Line Renderer：
    - 通过在 Inspector 窗口中直接设置数组值或使用 `Create Points` 场景编辑模式，可以将点添加到 Line Renderer 的 `Positions` 数组中。
    - 使用 Inspector 窗口配置线条的颜色、宽度和其他显示设置。

3. **场景编辑模式**:
    - Line Renderer 提供了三种场景编辑模式：`None`、`Edit Points` 和 `Create Points`。
    - `None` 模式允许配置并执行简化操作，从 `Positions` 数组中删除不必要的点。
    - `Edit Points` 模式允许在 Scene 视图中移动已存在的点。
    - `Create Points` 模式允许在 Scene 视图中单击以将新点添加到线渲染器的 `Positions` 数组的末尾。

4. **材质和纹理**:
    - 默认情况下，Line Renderer 使用内置材质 `Default-Line`。您可以更改线条的外观而无需更改此材质，例如编辑线条的颜色渐变或宽度。
    - 对于其他效果，例如在线条上应用纹理，需要使用其他材质。如果您不想为新材质编写自己的着色器，可以将 Unity 内置的标准粒子着色器与 Line Renderer 结合使用。

5. **简化操作**:
    - 在 `None` 场景编辑模式下，可以使用 `Simplify` 功能减少 `Positions` 数组中的元素数量，使用 `Ramer-Douglas-Peucker` 算法根据 `Tolerance` 值来减少点数。

6. **光照**:
    - Line Renderer 不受光照影响，因此它的外观不会随着光源的变化而变化。

通过以上步骤和功能，您可以在 Unity 中创建和配置 Line Renderer，以绘制各种形状和效果的线条。
![[8c495803778a17b4bb0c1e1b42702d48.png]]
这个选项是选择是否使用世界坐标点位,默认是勾选的,当我们需要让我们的线跟随我们的对象移动的话就不勾选他这样他就会跟随父对象移动了
