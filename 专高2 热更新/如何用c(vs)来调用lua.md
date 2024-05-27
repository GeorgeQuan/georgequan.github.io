首先我们展示XluaManager
```c#
public class XLuaManager : MonoBehaviour
{
    // Start is called before the first frame update
    private LuaEnv luaEnv;//lua 的虚拟机
    private Action LuaStart;//c#调用Lua
    private Action LuaUpdate;
   
    private void Awake()
    {
        luaEnv = new LuaEnv();//实例化虚拟机
        luaEnv.AddLoader(CustomerLoader);//添加一个自定义加载器
        luaEnv.DoString("require 'Main'");//引入Main文件
        LuaStart = luaEnv.Global.Get<Action>("LuaStart");
        LuaUpdate = luaEnv.Global.Get<Action>("LuaUpdate");
    }
    /// <summary>
    /// 自定义加载器
    /// </summary>
    /// <param name="filepath"></param>
    /// <returns></returns>
    private byte[] CustomerLoader(ref string filepath)
    {
        return File.ReadAllBytes(Application.dataPath + "/Lua/" + filepath + ".lua");
    }

    void Start()
    {
        LuaStart?.Invoke();//尝试调用lua中名为LuaStart的函数  invoke 是执行    ?就算lua中没有这个函数也不会报错 检查空
    }

    // Update is called once per frame
    void Update()
    {
        LuaUpdate?.Invoke();
    }
    private void OnDestroy()//程序关闭的时候
    {
        if (luaEnv != null)//判断虚拟机是否为空
        {
            luaEnv.Dispose();//销毁虚拟机
        }
    }
    /// <summary>
    /// 获取虚拟机
    /// </summary>
    public LuaEnv GetLua
    {
        get
        {
            return luaEnv;
        }
    }

}
```
在最后我们可以看到有一个获取虚拟机是的,当你需要调用Lua时首先要获取虚拟机来和Lua进行通讯.
当我们已经成功获取到虚拟机后就可以开始调用lua 中的方法了
LuaEnv.Global.Get<T>("T");
1. `LuaEnv` 是 Lua 虚拟机的一个实例，用于执行 Lua 脚本和与 C# 进行交互。
    
2. `Global` 是 `LuaEnv` 实例的一个属性，用于获取全局环境。
    
3. `Get<T>("T")` 是 `Global` 对象的一个方法，用于获取名为 "T" 的全局变量，并将其转换为类型 `T`。尖括号内的是泛型