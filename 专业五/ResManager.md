# ResManager


1 object 和Object 的区别  
在Unity中，"object"和"Object"是两个不同的概念。

1. "object"（小写）：它是C#编程语言中的关键字，表示所有其他类型的基类。在Unity中，"object"是所有对象的基类，包括游戏对象、脚本组件等。您可以使用"object"作为通用类型来引用任何对象。
2. "Object"（大写）：它是Unity引擎中的一个类，属于UnityEngine命名空间。这个类是所有Unity对象的基类，包括游戏对象、资源、材质等。"Object"类提供了一些通用的方法和属性，如销毁对象、获取对象实例ID等。

需要注意的是，"object"和"Object"之间的区别在于大小写和所属的上下文。"object"是C#语言的关键字，表示通用的基类类型，而"Object"是Unity引擎的类，表示Unity中的对象基类.

```
Resources.UnloadAsset(); 和
Resources.UnloadUnusedAssets();的区别
Resources.UnloadAsset()和Resources.UnloadUnusedAssets()是Unity游戏引擎中用于卸载资源的两个函数。它们的主要区别如下：
1. Resources.UnloadAsset()函数用于卸载单个资源对象。当你加载一个资源（例如纹理、音频剪辑或预制体）时，它会被加载到内存中并占用一定的资源。使用Resources.UnloadAsset()函数可以手动卸载特定的资源对象，从而释放其占用的内存。这个函数需要传入要卸载的资源对象作为参数。
2. Resources.UnloadUnusedAssets()函数用于卸载未使用的资源。当你加载多个资源时，有些资源可能会在游戏运行过程中变得不再使用，但仍然占用着内存。使用Resources.UnloadUnusedAssets()函数可以自动卸载未使用的资源，从而释放它们占用的内存。这个函数会检查当前场景中未使用的资源，并将其卸载。
总结一下，Resources.UnloadAsset()用于手动卸载指定的资源对象，而Resources.UnloadUnusedAssets()用于自动卸载未使用的资源。如果你知道哪些资源不再需要，可以使用Resources.UnloadAsset()手动卸载它们；如果你想自动卸载未使用的资源以释放内存，可以使用Resources.UnloadUnusedAssets()函数。

System.GC.Collect()
在Unity中，System.GC.Collect()是一个用于垃圾回收的方法。GC代表"Garbage Collector"（垃圾回收器），是一个负责自动管理和释放不再使用的内存资源的系统。
当你在Unity中创建、加载和销毁对象时，内存会被分配和释放。然而，有时候在释放对象后，内存并不会立即被回收，而是等待垃圾回收器执行清理操作。垃圾回收器会周期性地扫描内存，查找那些没有被引用的对象，并将其标记为可回收的垃圾。
System.GC.Collect()方法是一种手动触发垃圾回收的方式。当你调用这个方法时，它会立即执行一次垃圾回收操作，尽可能地释放被标记为垃圾的内存。请注意，这个方法的调用通常是在特殊情况下使用的，因为垃圾回收器会根据需要自动执行回收操作，以避免频繁的手动调用。
需要注意的是，在大多数情况下，你不需要手动调用System.GC.Collect()来管理内存，因为Unity的垃圾回收机制通常能够很好地处理内存管理。只有在特殊情况下，例如在加载大量资源后立即释放内存，或者在性能测试和优化方面，才需要考虑手动触发垃圾回收。
```

