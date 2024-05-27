# 强行刷新ui布局


`LayoutRebuilder.ForceRebuildLayoutImmediate(Parent)` 是 Unity 引擎中用于立即强制重建布局的方法。
LayoutRebuilder 是 Unity 提供的一个用于重新计算和重建 UI 布局的工具类。在 UI 元素的位置、尺寸或布局发生变化时，可以使用 LayoutRebuilder 来触发布局的重新计算和重建。
ForceRebuildLayoutImmediate(Parent) 方法用于立即强制重建指定父级对象（Parent）的布局。这意味着在调用该方法后，Unity 引擎会立即重新计算指定父级对象及其下属的所有子对象的布局，并应用新的位置和尺寸。
这个方法适用于需要立即更新 UI 布局的情况，例如在动态修改 UI 元素的属性后需要立即更新它们的位置和尺寸。但需要注意的是，由于该方法会引起布局的重新计算，频繁地调用它可能会对性能产生影响，因此应该谨慎使用
他常用在实例化第一个ui没有改变布局从而显示不好的情况

