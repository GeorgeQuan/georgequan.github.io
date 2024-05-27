#Editor
在Unity等游戏引擎中，`Editor`文件夹是一个特殊的文件夹，主要用于存放编辑器脚本。这些脚本只能在编辑器中运行，而不会被打入最终的游戏构建中

以下是`Editor`文件夹的主要特点：

- **编辑器专用**：`Editor`文件夹中的脚本只能用于编辑器环境，不能在游戏运行时调用。这意味着，如果你的脚本需要在游戏运行时调用，那么你不应该把它放在`Editor`文件夹中[1](https://blog.csdn.net/u012424962/article/details/52497867)[3](https://docs.unity3d.com/cn/2020.3/Manual/SpecialFolders.html)[4](https://www.cnblogs.com/Damon-3707/p/11445321.html)。

- **不参与构建**：`Editor`文件夹中的脚本不会被打入最终的游戏构建中。这意味着，即使你的脚本在编辑器中运行良好，但如果它在`Editor`文件夹中，它也不会出现在游戏的最终版本中[1](https://blog.csdn.net/u012424962/article/details/52497867)[3](https://docs.unity3d.com/cn/2020.3/Manual/SpecialFolders.html)[4](https://www.cnblogs.com/Damon-3707/p/11445321.html)。

- **可以有多个`Editor`文件夹**：在Unity项目中，你可以创建多个`Editor`文件夹，并将相关的编辑器脚本放入其中。这有助于你更好地组织和分类你的编辑器脚本[1](https://blog.csdn.net/u012424962/article/details/52497867)[4](https://www.cnblogs.com/Damon-3707/p/11445321.html)。

- **EditorDefaultResources**：`Editor`文件夹还可以包含一个名为`Editor Default Resources`的子文件夹，用于存放编辑器使用的默认资源。这些资源可以通过`EditorGUIUtility.Load`函数在编辑器脚本中加载，但不会被打入最终的游戏构建中[3](https://docs.unity3d.com/cn/2020.3/Manual/SpecialFolders.html)。

总的来说，`Editor`文件夹是一个非常强大的功能，它可以帮助你编写只在编辑器环境中运行的脚本，从而提高你的工作效率。

#EditorWindow
`EditorWindow` 是Unity中的一个基类，专门用于在Unity编辑器中创建自定义的编辑器窗口。这些窗口的行为类似于Inspector、Scene视图或其他内置视图。`EditorWindow`提供了一个框架，允许开发者创建具有图形用户界面的窗口，这些窗口可以在编辑器中显示和交互。
`EditorWindow`类在Unity中用于创建和管理编辑器中的自定义窗口。以下是一些重要的`EditorWindow`类的函数和方法：

1. `OnGUI()`: 这是`EditorWindow`类的主要方法，用于在编辑器窗口中绘制GUI元素。每次编辑器窗口更新时，都会调用这个方法[1](https://blog.csdn.net/qq_36383623/article/details/100168395)。

2. `Show()`: 显示窗口。如果你想手动控制窗口何时出现，可以使用这个方法[1](https://blog.csdn.net/qq_36383623/article/details/100168395)。

3. `Close()`: 关闭窗口[1](https://blog.csdn.net/qq_36383623/article/details/100168395)。

4. `ShowPopup()`: 以弹出形式显示窗口[1](https://blog.csdn.net/qq_36383623/article/details/100168395)。

5. `ShowUtility()`: 显示为浮动工具窗口[1](https://blog.csdn.net/qq_36383623/article/details/100168395)。

6. `GetWindow()`: 获取一个已经存在的窗口实例[1](https://blog.csdn.net/qq_36383623/article/details/100168395)。

7. `GetWindowWithRect()`: 获取一个窗口实例，并且指定窗口的位置和大小[1](https://blog.csdn.net/qq_36383623/article/details/100168395)。

8. `Awake()` 和 `OnEnable()`: 在窗口初始化和启用时调用，可以用来设置窗口的状态和行为[1](https://blog.csdn.net/qq_36383623/article/details/100168395)。

9. `OnDestroy()`: 当窗口被销毁时调用，可以用来清理资源[1](https://blog.csdn.net/qq_36383623/article/details/100168395)。

10. `OnFocus()` 和 `OnLostFocus()`: 当窗口获得或失去焦点时调用，可以用来处理焦点变化时的行为[1](https://blog.csdn.net/qq_36383623/article/details/100168395)。

11. `Update()`: 每帧调用一次，可以用来处理窗口的动态行为[1](https://blog.csdn.net/qq_36383623/article/details/100168395)。

12. `GetInstanceID()`: 获取窗口的唯一标识符[1](https://blog.csdn.net/qq_36383623/article/details/100168395)。

13. `ToString()`: 返回窗口的名称[1](https://blog.csdn.net/qq_36383623/article/details/100168395)。

14. `Destroy()` 和 `DestroyImmediate()`: 销毁窗口或对象[1](https://blog.csdn.net/qq_36383623/article/details/100168395)。

15. `DontDestroyOnLoad()`: 在加载新场景时保留窗口[1](https://blog.csdn.net/qq_36383623/article/details/100168395)。

16. `FindObjectOfType()` 和 `FindObjectsOfType()`: 查找具有特定类型的已加载对象[1](https://blog.csdn.net/qq_36383623/article/details/100168395)。

17. `Instantiate()` 和 `CreateInstance()`: 克隆对象或创建脚本化对象的实例[1](https://blog.csdn.net/qq_36383623/article/details/100168395)。

以上就是`EditorWindow`类的一些重要函数和方法，它们可以帮助你在Unity编辑器中创建和管理自定义窗口。



**总结**
当你在Unity中创建一个脚本并使其继承自`EditorWindow`时，该脚本默认就会在编辑器中运行，而不是在游戏运行时运行。这是因为`EditorWindow`是专门为了在Unity编辑器中创建自定义窗口而设计的。无论你是否显式地在代码中使用了`EditorWindow`的功能，只要你的脚本继承了这个类，它就会被视为一个编辑器脚本，并在编辑器中执行[2](https://juejin.cn/s/unity%20%E7%BB%A7%E6%89%BFeditor)。

此外，如果你的脚本位于`Assets/Editor`文件夹中，那么无论其是否继承自`EditorWindow`，它都会被视为编辑器脚本，并在编辑器中执行。这是因为Unity会将`Editor`文件夹下的脚本作为编辑器脚本进行处理，它们不会被包含在游戏构建中，而是在编辑器中运行[1](https://www.cnblogs.com/suoluo/p/10769289.html)[3](https://juejin.cn/post/7231967430947733563)。

所以，如果你的脚本既继承自`EditorWindow`又位于`Assets/Editor`文件夹中，那么它不仅会在编辑器中运行，而且还具有创建自定义编辑器窗口的能力。


