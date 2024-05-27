# c#中的自带委托


1. Action<T> 表示一个没有返回值的委托,接受一个泛型的参数;
2. Func<T,TResult> result(结果)  表示一个具有返回值为TResult(泛型)的委托,接受泛型为参数  在定义时尖括号内最后一个参数为返回值
3. Predicate<T> 表示一个具有bool类型返回值的委托,它接受一个泛型的参数
4. Comparison<T> 表示用于比较两个泛型参数的委托,返回一个int类型为结果   list.Sort()的底层就是这个委托

