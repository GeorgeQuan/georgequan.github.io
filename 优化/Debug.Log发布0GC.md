每执行移除Debug.Log 都会造成大约1.4kb 的垃圾,那么如何避免在程序发布的时候执行Debug.Log呢.
```c#
public static class MyLogger
{
    [Conditional("ENABLE_DEBUG_LOG")]
    public static void Log(string content)
    {
        Debug.Log(content) ;
    }
}

```
Conditionial(有条件的) 
下图是设置条件的位置
![[Pasted image 20240505201039.png]]
设置条件的作用是,如果条件不满足的话,那么在编译成中间语言IL时不会包含条件不满足的代码.
另一种写法
```c#
#define ENABLE_DEBUG_LOG  //定义条件

using System.Diagnostics;

public class DebugLogger
{
    [Conditional("ENABLE_DEBUG_LOG")]
    public static void Log(string message)
    {
        Console.WriteLine(message);
    }
}

public class Program
{
    public static void Main()
    {
        DebugLogger.Log("Debug message 1"); // 会被编译器包含

        #undef ENABLE_DEBUG_LOG  //卸载条件

        DebugLogger.Log("Debug message 2"); // 不会被编译器包含
    }
}
```