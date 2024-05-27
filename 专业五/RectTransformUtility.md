# RectTransformUtility


RectTransformUtility 是 Unity 提供的一个实用工具类，用于处理 RectTransform 相关的操作和计算。它包含了一些静态方法，用于执行常见的 RectTransform 转换和计算操作。
RectTransformUtility 提供的一些常用方法包括：

1. RectTransformUtility.ScreenPointToLocalPointInRectangle()：将屏幕坐标点转换为指定 RectTransform 的本地坐标点。可以使用这个方法将鼠标或触摸事件的屏幕坐标转换为 UI 元素内的本地坐标。
2. RectTransformUtility.WorldToScreenPoint()：将世界坐标点转换为屏幕坐标点。可以使用这个方法将 3D 场景中的世界坐标点转换为 UI 元素所在的屏幕坐标。
3. RectTransformUtility.PixelAdjustPoint()：根据 RectTransform 的像素对齐设置，调整指定点的坐标。可以使用这个方法将坐标点根据 UI 元素的像素对齐设置进行调整，以确保 UI 元素的像素对齐正确。
4. RectTransformUtility.FlipLayoutOnAxis()：根据指定的轴翻转 RectTransform 的布局。可以使用这个方法在水平或垂直方向上翻转 UI 元素的布局。

这些方法可以帮助你在处理 UI 元素时执行一些常见的转换和计算操作。例如，你可以使用 RectTransformUtility.ScreenPointToLocalPointInRectangle() 将屏幕坐标点转换为 UI 元素内的本地坐标，以便进行与 UI 元素交互相关的操作。
使用 RectTransformUtility 方法时，你需要提供相应的参数，如 RectTransform 对象、坐标点等，以确保方法能够正确执行所需的转换和计算。
这些方法提供了一些便捷的功能，帮助简化 RectTransform 的操作和计算。了解这些方法可以帮助你更好地处理 UI 元素的定位、转换和交互。
**5** RectTransformUtility.RectangleContainsScreenPoint() 是 RectTransformUtility 类中的一个静态方法，用于检查一个屏幕坐标点是否位于指定 RctTransform 的矩形区域内。![[./_resources/RectTransformUtility.resources/unknown_filename.png|309x0]]

