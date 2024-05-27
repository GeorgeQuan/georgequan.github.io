  自定义轨道
 TimeLine 生命周 期函数
1. 继承using UnityEngine.Timeline;
2. ,ITimeControl  实现这个接口
这样就出现了.

自定义轨道写法
![[Pasted image 20240312144704.png]]

NewPlayableAsset格式
![[Pasted image 20240312144803.png]]

NewPlayableBehaviour格式
继承完接口后,实现接口,直接在生命周期内写就好
![[Pasted image 20240312144830.png]]