Gizmo 是Unity编辑器中用于辅助开发者在编辑模式下绘制自定义视觉辅助线的工具。它们可以帮助开发者更直观地理解和操作游戏对象的位置、方向和大小，以及物理设置、重叠物体的点击检测、记录物体移动路径等。Gizmo的用途相当广泛，是非必要的辅助程序，但对于游戏制作过程中的辅助非常有用。

Gizmo的词源来自英文中的“小发明”和“小玩意具”，但在实际使用中，它们主要被用作辅助线的意思，因为它们确实是辅助游戏制作的小程序。在Unity中，无论是在Game视图还是Scene视图中，都可以在視窗的右上角找到一个Gizmos按钮，按下去会亮起，代表在这个視窗中会显示Gizmos。

Gizmo有四个基本参数：

- `color`：绘制辅助线的颜色。
- `exposure`：不常用，与材质相关。
- `matrix`：如果辅助线需要旋转等操作时使用。
- `probeSize`：不常用，与渲染相关。

在Unity中，Gizmo有两个启动函数：

- `OnDrawGizmos()`：当程序（Script）展开时才会运作。
- `OnDrawGizmosSelected()`：当程序（Script）展开和选择时才会运作。

Gizmo的使用方式与`Start`和`Update`相似，可以直接在这些函数中编写需要绘制的内容。例如，绘制一条射线可以使用`Gizmos.DrawRay(origin, direction)`，其中`origin`是射线的起点，`direction`是射线的方向。如果希望辅助线随物体移动，可以通过设置`Gizmos.matrix = transform.localToWorldMatrix`来实现。

总的来说，Gizmo是一个非常有用的工具，尤其在程序的维护和传承中，对于程序美术的配合以及程序员之间的配合都相当有用。虽然它们的使用并不频繁，但对于可视化绘制，它们是相当重要的内容[3](https://vocus.cc/article/6207c6b6fd89780001512255)。


 我们通常在画辅助线的时候会写在MonoBehaviour下的OnDrawGizmos和OnDrawGizmosSelected 的方法内
 1. OnDrawGizmos  这个方法会在编译时就每帧调用只要是在编辑器中无论是编译时,还是运行时
2. OnDrawGizmosSelected  点检测到挂载脚本游戏对象被选中时执行

下面是可以实现的画线的类

#Gizmo
在Unity中，你可以通过`Gizmos`类来实现画线的功能。`Gizmos`类提供了多种方法来绘制各种形状，包括线条。以下是一些主要的方法：

- `Gizmos.DrawLine(Vector3 from, Vector3 to)`: 这个方法用于绘制一条从`from`位置到`to`位置的线条。你可以通过设置`Gizmos.color`来改变线条的颜色。

- `Gizmos.DrawLineList(Vector3[] points)`: 如果你需要绘制多条线，可以使用这个方法。它接受一个包含所有线条起点和终点的`Vector3`数组。

- `Gizmos.DrawLineStrip(Vector3[] points)`: 这个方法用于绘制一系列连接的线条，它接受一个包含所有线条顶点的`Vector3`数组。
#Handles
Unity还提供了`Handles`类来实现在编辑器中绘制自定义Gizmo。`Handles`类提供了一系列方法，可以用于在编辑器的场景视图中绘制各种形状，包括线条、圆形、矩形、弧形等。以下是一些主要的方法：

- `Handles.DrawLine(Vector3 from, Vector3 to)`: 绘制一条从`from`位置到`to`位置的线条。
- `Handles.DrawWireCube(Vector3 center, Vector3 size)`: 绘制一个中心位于`center`，大小为`size`的线框立方体。
- `Handles.DrawWireSphere(Vector3 center, float radius)`: 绘制一个中心位于`center`，半径为`radius`的线框球体。
- `Handles.DrawWireArc(Vector3 center, Vector3 normal, Vector3 from, float angle, float radius)`: 绘制一个以`center`为中心，`normal`为法线的弧形，从`from`开始，角度为`angle`，半径为`radius`。
- `Handles.DrawSolidArc(Vector3 center, Vector3 normal, Vector3 from, float angle, float radius)`: 绘制一个填充的弧形，参数与`DrawWireArc`相同。
- `Handles.color改变线段颜色`