# 当触发器的isTrigger 被勾选的时候


当触发器的isTrigger 被勾选的时候 

1. 不会产生物理碰撞效果,可以实现物体穿透的效果。
2. 不会触发OnCollisionEnter等碰撞回调,取而代之触发OnTriggerEnter、OnTriggerStay、OnTriggerExit等回调。
3. 更轻量化,无需处理物理碰撞的计算。
4. 经常用于检测进入区域或实现交互的效果

