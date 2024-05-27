```c#
using System.Collections;
using System.Collections.Generic;
using UnityEngine;
//IEnumerable 可迭代类型
//IEnumerator 枚举器(枚举器就是迭代器)
//一个类型只要实现了IEnumerable 接口就可以对他进行遍历
//yield关键字就是实现了IEnumerator枚举器

public class DieDaiQi : IEnumerable
{
    /// <summary>
    ///  IEnumerable 接口可迭代类型包括迭代器接口的实现
    /// </summary>
    /// <returns></returns>
    public IEnumerator GetEnumerator()
    {

        yield return "王喆笑嘻嘻1";
        yield return "王喆笑嘻嘻2";
        yield return "王喆笑嘻嘻3";
        //上下效果相同
        //string[] student = { "王喆笑嘻嘻1", "王喆笑嘻嘻2", "王喆笑嘻嘻3" };
        //return new StudentEnumerator(student);

    }


}

internal class StudentEnumerator : IEnumerator
{
    private string[] student;
    int _index = -1;
    public StudentEnumerator(string[] student)
    {
        this.student = student;
    }
    public object Current
    {
        get
        {
            if (_index == -1)
            {
                throw new System.Exception();
            }
            if (_index >= student.Length)
            {
                throw new System.Exception();
            }
            return student[_index];
        }

    }

    public bool MoveNext()
    {
        if (_index < student.Length - 1)
        {
            _index++;
            return true;
        }
        else
        {
            return false;
        }

    }

    public void Reset()
    {
        _index = -1;
    }
}
```
上面只是迭代器的第一次底层,在往下挖的化还有状态机


