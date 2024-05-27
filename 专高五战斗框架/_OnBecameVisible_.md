

## 描述

_OnBecameVisible_ 在对象变为对任意摄像机可见时调用。

该消息将发送到附加到渲染器的所有脚本。 _OnBecameVisible_ 和 _OnBecameInvisible_ 有助于避免仅在对象可见时才需要进行的计算。

using UnityEngine;  
  
public class Example : [MonoBehaviour](https://docs.unity.cn/cn/2019.4/ScriptReference/MonoBehaviour.html)
{
    // Disable the behaviour when it becomes invisible...
    void OnBecameInvisible()
    {
        enabled = false;
    }  
  
    // ...and enable it again when it becomes visible.
    void OnBecameVisible()
    {
        enabled = true;
    }
}

注意，当需要在场景中渲染某个对象时，则认为该对象可见。例如， 有的对象实际上可能不会被任何摄像机看到， 但由于阴影原因仍需要渲染。此外，在 Editor 中运行时，Scene 视图摄像机也会导致 调用该函数。