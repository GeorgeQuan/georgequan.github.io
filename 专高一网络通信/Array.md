# Array


Array 是c# 中自带的一个类他用有很多封装好的方法用于对数组进行操作

* Length 属性：获取数组的长度（元素的总数）。
* Rank 属性：获取数组的维度数。
* GetLength(int dimension) 方法：获取指定维度的长度。
* GetValue(params int\[\] indices) 方法：根据索引获取数组中的值。
* SetValue(object value, params int\[\] indices) 方法：根据索引设置数组中的值。
* CopyTo(Array destination, int index) 方法：将数组的元素复制到另一个数组中。
* Sort() 方法：对数组进行排序。
* IndexOf(object value) 方法：在数组中查找指定值的第一个匹配项的索引。
* ForEach(Action<T> action) 方法：对数组中的每个元素执行指定的操作。
* Array.Reverse(copy); 是一个用于反转数组元素顺序的方法调用。

