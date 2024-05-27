# Canvas


当涉及到 Unity 中的 UI 渲染时，Canvas 组件是一个非常重要的组件。它提供了一种容纳和渲染 UI 元素的方式。下面是一些常见的 Canvas 组件及其属性的介绍：

1. Render Mode（渲染模式）：
	* Render Mode 属性定义了 Canvas 如何渲染 UI 元素。
	* Screen Space - Overlay：Canvas 元素以屏幕为基准进行渲染，覆盖在其他元素之上。
	* Screen Space - Camera：Canvas 元素以摄像机为基准进行渲染。需要将渲染摄像机指定给 Canvas。
	* World Space：Canvas 元素在世界空间中进行渲染，可以与场景中的其他物体进行交互。
2. Sorting Layer（排序层）：
	* Sorting Layer 属性定义了 Canvas 的渲染层级。通过设置不同的 Sorting Layer，可以控制 UI 元素的显示顺序。
	* 你可以在 Inspector 视图中创建和管理 Sorting Layer。
3. Sorting Order（排序顺序）：
	* Sorting Order 属性定义了 Canvas 中每个元素的具体渲染顺序。
	* 较高的 Sorting Order 值会使元素显示在较低的值之上。
4. Pixel Perfect（像素完美）：
	* Pixel Perfect 属性允许 Canvas 在渲染时对齐到像素级别，以提供更清晰的图像效果。
5. UI Scale Mode（UI 缩放模式）：
	* UI Scale Mode 属性定义了 UI 元素如何随着屏幕尺寸的变化而缩放。
	* Constant Pixel Size：UI 元素的像素大小保持不变。
	* Scale With Screen Size：UI 元素根据屏幕的尺寸进行缩放。
	* Constant Physical Size：UI 元素的物理尺寸保持不变。
6. Reference Pixels Per Unit（参考像素单位）：
	* Reference Pixels Per Unit 属性定义了 Canvas 的参考像素单位。这对于在不同分辨率下保持一致的 UI 元素尺寸很有用。
7. 当你为对象添加了一个canvas组件的时候他的身上可以要在添加一个GraphicRaycaster [[GraphicRaycaster|GraphicRaycaster]]




在创建Canvas 时还提供了其他几个组件来实现Canvas的一些功能
1.  Canvas组件是在Web开发中常用的HTML5元素之一，它提供了一个可绘制图形的区域，可以通过JavaScript来控制和操作图形。Canvas允许开发者使用JavaScript绘制图形、动画、游戏等内容，使得在网页上创建丰富的可视化效果成为可能。

以下是Canvas组件的主要功能和用途：

1. 图形绘制：Canvas提供了一组API用于绘制2D图形，例如直线、矩形、圆形、多边形等。开发者可以使用这些API来绘制静态或动态的图形，实现自定义的可视化效果。
    
2. 动画效果：通过使用Canvas和JavaScript结合，可以创建各种动画效果，如平移、旋转、缩放、渐变等。开发者可以在Canvas上绘制图形，并使用动画循环不断更新图形的状态，从而实现流畅的动画效果。
    
3. 游戏开发：Canvas在游戏开发中得到广泛应用。开发者可以使用Canvas绘制游戏场景、角色、粒子效果等，并通过JavaScript控制游戏逻辑和交互。Canvas提供了与游戏相关的功能，如碰撞检测、事件处理等。
    
4. 数据可视化：Canvas可以用于创建各种数据可视化的图表和图形，如柱状图、折线图、饼图等。开发者可以根据数据动态绘制图形，并通过交互操作来实现数据的可视化展示和探索。
    
5. 图像处理：Canvas提供了图像处理的功能，可以加载、绘制和编辑图像。开发者可以使用Canvas对图像进行裁剪、缩放、滤镜、融合等操作，实现图像的处理和编辑功能。
    

需要注意的是，Canvas是基于像素的绘图技术，绘制的图形是通过绘制像素点来构成的。相比于矢量图形，Canvas在缩放或变换时可能会有一定的失真。如果需要更高的分辨率和可伸缩性，可以考虑使用SVG（Scalable Vector Graphics）等矢量图形技术。
2. Canvas Scaler（画布缩放器）是Unity游戏引擎中的一个组件，用于调整画布（Canvas）在不同屏幕分辨率下的缩放和适配。它提供了一些选项和方法，以确保UI元素在不同设备上的呈现效果一致。

Canvas Scaler的主要作用是解决不同屏幕分辨率下的UI适配问题。当游戏在不同的设备上运行时，屏幕的大小和分辨率可能会有所不同，而UI元素的大小和位置需要相应地进行调整，以适应不同的屏幕尺寸。

以下是Canvas Scaler的一些常见用途：

1. 屏幕适配：Canvas Scaler可以根据设备的屏幕分辨率和调整设置，自动缩放和调整UI元素的大小和位置，以适应不同的屏幕尺寸。这样可以确保UI在不同设备上的可见性和可操作性。
    
2. 分辨率独立性：Canvas Scaler可以使UI元素在不同的分辨率下保持相同的物理尺寸。例如，一个按钮在不同分辨率下显示的像素数量可能不同，但通过Canvas Scaler的设置，可以使按钮的物理尺寸保持一致，从而保持一致的用户体验。
    
3. 缩放模式：Canvas Scaler提供了不同的缩放模式选项，如Constant Pixel Size（固定像素大小）、Scale With Screen Size（随屏幕尺寸缩放）、Constant Physical Size（固定物理尺寸）等。这些选项允许开发者根据需求选择合适的缩放模式来适配UI元素。
    
4. 分辨率变化事件：Canvas Scaler还提供了分辨率变化的事件回调，开发者可以通过监听这些事件，在屏幕分辨率发生变化时进行相应的处理和调整，以实现更精确的适配效果。
    

通过Canvas Scaler的配置和调整，开发者可以更方便地实现UI在不同屏幕分辨率下的适配和呈现，提供更好的用户体验，并确保游戏在不同设备上的一致性。
3. 在Unity游戏引擎中，Event System（事件系统）是一种用于处理用户输入和交互的组件。它负责接收、分发和管理用户输入事件，以便将其传递给正确的游戏对象进行处理。Event System是构建交互式UI和用户输入响应的关键组件。

Event System的主要作用如下：

1. 输入事件管理：Event System负责管理用户输入事件，包括点击、触摸、鼠标移动、键盘按键等。它通过接收底层输入事件，并将其转化为更高级的Unity事件，然后将事件传递给正确的游戏对象进行处理。
    
2. 事件分发：Event System可以将接收到的输入事件分发到合适的游戏对象进行处理。它通过射线检测、碰撞体等方式来确定与输入事件相关的游戏对象，并将事件传递给它们的事件处理器进行响应。这样，开发者可以通过编写相应的事件处理代码来实现与用户交互相关的逻辑。
    
3. 交互式UI：Event System是Unity中用于处理UI交互的关键组件。它可以接收UI元素（如按钮、滑块、输入框等）的点击事件，并将这些事件传递给相应的UI组件进行响应。通过Event System，开发者可以实现按钮点击、滑动、拖拽等各种交互操作。
    
4. 事件监听：Event System提供事件监听的机制，开发者可以通过注册事件监听器来监听特定的事件，以便在事件发生时执行相应的代码。这样可以实现事件驱动的编程模式，使得开发者可以根据用户输入来触发特定的逻辑。
    

需要注意的是，为了正常使用Event System，通常需要配合其他组件一起使用，如Graphic Raycaster（图形射线投射器）用于射线检测，以及各种UI组件用于接收和处理事件。通过组合和配置这些组件，可以实现复杂的用户交互和UI功能。

总之，Event System是Unity中用于处理用户输入和交互的关键组件，它负责接收、分发和管理用户输入事件，并将其传递给适当的游戏对象进行处理。通过使用Event System，开发者可以构建丰富的交互式UI和实现与用户的有效互动。
4. StandaloneInputModule（独立输入模块）是Unity的Event System（事件系统）中的一种InputModule（输入模块），用于处理Unity应用程序在独立平台上的用户输入。它是针对非移动设备（如电脑、主机等）的输入处理提供的一种默认实现。

StandaloneInputModule提供了以下功能：

1. 鼠标输入处理：StandaloneInputModule可以处理鼠标的点击、滚动和移动等输入事件。它可以检测鼠标的位置、按钮状态和滚轮滑动，并将这些输入事件转化为Unity事件系统中的相应事件，以便在游戏中进行处理。
    
2. 键盘输入处理：StandaloneInputModule可以处理键盘的按键事件。它可以检测键盘上按下和释放的按键，并将它们转化为相应的Unity事件，用于响应和处理用户的键盘输入操作。
    
3. 输入事件分发：StandaloneInputModule负责将接收到的鼠标和键盘输入事件分发给UI组件进行处理。通过射线检测和事件目标的识别，它可以确定用户输入事件所针对的UI元素，并将事件传递给相应的UI组件进行处理。
    
4. 内置的触摸支持：除了鼠标和键盘输入，StandaloneInputModule还提供了基本的触摸输入支持。它可以处理触摸屏上的触摸手势，如点击、滑动和缩放等，以及转化为Unity事件进行处理。
    

StandaloneInputModule是Unity的默认输入模块，适用于独立平台上的用户输入处理。它可以与Event System和其他UI组件配合使用，实现用户与应用程序之间的交互操作。开发者也可以通过自定义输入模块来扩展或替代StandaloneInputModule，以满足特定的输入需求。
#让3D物体实现ui事件
PhysicsRaycaster是一个用于在Unity中处理UI事件的Raycaster组件之一，它主要用于检测3D物体上的UI事件.如果你需要让3D物体实现ui的操作的话,那么这个组件必不可少.