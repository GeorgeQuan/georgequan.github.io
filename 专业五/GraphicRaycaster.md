# GraphicRaycaster


GraphicRaycaster 组件是用于处理鼠标和触摸事件的组件，它允许 Canvas 上的 UI 元素能够与用户进行交互。当你添加 GraphicRaycaster 组件到 Canvas 上时，它会将用户的输入事件（如点击）转发给位于 Canvas 下方的 UI 元素。
Canvas 默认情况下包含 GraphicRaycaster 组件，这是因为 Unity 提供了灵活的设计选择。有时候，你可能希望 Canvas 上的 UI 元素不接收用户的输入事件，而是仅作为显示元素。这种情况下，你可以选择不添加 GraphicRaycaster 组件。
但是，当你需要处理用户的输入事件时，你需要手动添加 GraphicRaycaster 组件到 Canvas 上。你可以在 Unity 编辑器中的 Inspector 视图中找到 Canvas 组件，并在组件的属性面板中点击 "Add Component" 按钮，然后选择 "UI"，再选择 "Graphic Raycaster"。
总结起来，添加 Canvas 对象时需要再加上 GraphicRaycaster 组件是因为 GraphicRaycaster 组件是用于处理用户输入事件的组件，它使得 Canvas 上的 UI 元素能够接收用户的点击、拖拽等交互操作。

