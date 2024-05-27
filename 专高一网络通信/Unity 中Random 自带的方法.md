
1`Random.Range(min, max)`：生成一个指定范围内的随机整数或浮点数。`min` 参数是范围的最小值，`max` 参数是范围的最大值。生成的随机数可能包括 `min`，但不包括 `max`。
```csharp
int randomInt = Random.Range(1, 10);  // 生成 1 到 9 之间的随机整数
float randomFloat = Random.Range(0.0f, 1.0f);  // 生成 0.0 到 1.0 之间的随机浮点数
```
2 `Random.value`：生成一个 0.0 到 1.0 之间的随机浮点数。

```csharp
float randomValue = Random.value;  // 生成 0.0 到 1.0 之间的随机浮点数
```

3`Random.insideUnitCircle`：生成一个位于单位圆内的随机二维向量。向量的分量的取值范围是 -1 到 1 之间
```csharp
Vector2 randomPoint = Random.insideUnitCircle;  // 生成一个位于单位圆内的随机二维向量
```
4`Random.insideUnitSphere`：生成一个位于单位球内的随机三维向量。向量的分量的取值范围是 -1 到 1 之间。

```csharp
Vector3 randomPoint = Random.insideUnitSphere;  // 生成一个位于单位球内的随机三维向量
```
5`Random.onUnitSphere`：生成一个位于单位球表面的随机三维向量。向量的长度为 1。

```csharp
Vector3 randomPoint = Random.onUnitSphere;  // 生成一个位于单位球表面的随机三维向量
```
在3,4,5, 中我可以通过乘对应的数来改变实际得到的范围,比如3乘50.就代表随机一个50到-50 的二维向量