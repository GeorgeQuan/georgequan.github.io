在Unity中，垃圾回收（GC）过程中的标记阶段是通过遍历所有根对象来进行的。根对象包括全局变量、活动线程的栈和静态变量等。具体来说，垃圾回收器会从这些根对象开始，递归地遍历所有可达对象，并将其标记为“活动”状态。

具体步骤如下：

1. **初始化标记位**：首先，垃圾回收器会重置内存节点的标记位，以便区分已访问的对象和未访问的对象。
2. **遍历根对象**：从程序中的根对象开始，垃圾回收器会遍历这些根对象。这包括全局变量、活动线程的栈和静态变量等。
3. **递归遍历**：对于每一个被访问到的对象，垃圾回收器会继续遍历该对象所引用的其他对象，并将这些对象也标记为“活动”。
4. **构建引用图**：在这个过程中，垃圾回收器会构建一个引用图，将所有可达的对象连接起来。

通过这种方式，垃圾回收器能够确保所有被根对象引用的对象都被标记为活动，从而避免在后续的清除阶段错误地释放这些对象。
### 标记阶段

在标记阶段，垃圾收集器会遍历堆上的所有对象，并检查每个对象是否被应用程序的根集合引用。如果一个对象没有任何引用指向它，那么它就被认为是“不可达”的，即已经不再被使用。这个过程通常是从根集合开始，递归地向下查找所有可达的对象，最终标记出所有不可达的对象。

### 清除阶段

在清除阶段，垃圾收集器会删除所有被标记为不可达的对象，从而释放这些对象占用的内存空间。这一阶段的目的是将废弃的内存重新回收再次使用。

Unity中使用的BoehmGC是一个基于标记-清除算法的垃圾回收器，它是stop-the-world类型的垃圾收集器，这意味着在执行垃圾回收时，会暂停正在运行的程序，以确保垃圾回收操作能够正确完成。这种方式虽然可以保证垃圾回收的准确性，但也可能导致程序在执行垃圾回收时出现卡顿现象。

### **扩容机制**
Unity中的托管堆是由Mono或IL2CPP运行时系统自动管理的。这些系统负责分配和回收托管堆内的内存。在Unity程序初始化期间，Mono平台会向操作系统申请一段内存，用于生成堆内存空间（通常称为托管堆）。

当Unity发现托管堆的内存不足以分配新对象时，会首先进行垃圾回收（GC）。这种扩容是必要的，因为Unity的垃圾收集策略可能会导致内存碎片化，从而阻止大型堆的收缩。

扩容过程涉及申请更多的内存来增加堆的大小。这通常是通过向操作系统请求更多内存来实现的。
，Unity 在需要进行堆空间扩容时，通常会将堆空间扩大两倍，以优化内存使用和避免内存碎片化问题。这种策略反映了 Unity 对内存管理的深入理解和优化努力。


GC也会管理非托管资源,因为创建非托管资源时的非托管对象来是被托管管理的,我们在写非托管代码的时候必须要实现非托管资源的Dispose 方法用于清除非托管内存,并且在析构函数中调用Dispose方法,而析构函数是由GC 管理的. 当非托管对象不被引用的时候,就会把析构函数放到析构队列中并且在下一次垃圾回收的时候实现这些析构函数