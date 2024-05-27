因为命名空间不同所以Proto中的集合不能像SystemList 一样sort排序
我的解决方案是先把Proto集合转换成System集合然后在转回来
``` csharp
List<RoomData> list = _allRoom.AllRoom_.ToList();
            list.Sort(OnSort);
            _allRoom.AllRoom_.Clear();
            _allRoom.AllRoom_.AddRange(list);
```
这里的_allRoom 是Proto类型的