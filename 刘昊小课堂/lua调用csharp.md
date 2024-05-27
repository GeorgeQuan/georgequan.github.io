在xlua 中想调用unity 中的代码你用cs.unity 中的代码
```lua
function LuaStart()

    print("lua侧的入口")

  

    gameObject = CS.UnityEngine.GameObject.Find("QWQ")
UnityEngine 是一个命名空间,我要找到场景中叫QWQ的游戏对象并返回
  
在lua 中创建对象的new可以省略

    gameObject.transform.position = CS.UnityEngine.Vector3(0, 0, 0)

    gameObject:GetComponent(typeof(CS.UnityEngine.Rigidbody))
	:相当于把自己当作第一个参数放到形参内了
	在unity 中start 不能直接访问类的实例他需要一个参数传进来一个类才能调用
    在非静态的方法中它其实也需要这么做但c#把他们隐藏了
    下面两个代码是一个意思 c#代码
public void TestMethod((这里省略了自己这个类型)string text)
    {
        Debug.Log(this.Value);
        Debug.Log(text);
    }

    public static void TestMethod2((需要添加自己这个类型)TestScript self, string text)
    {
        Debug.Log(self.Value);
        Debug.Log(text);

        int qwq = 12312;
        string awa = "WEFWJEOIFWEOIF";

        var gameObject = GameObject.Find("QWQ");
        gameObject.GetComponent((这里也省略了类的本身)typeof(Rigidbody));
    }
    这个方法是谁的就是省略了谁
end
```