# PointerEventData(指针事件数据)


PointerEventData 类是 Unity 引擎中用于存储和传递指针事件数据的类。它包含了与指针操作相关的各种信息，以便在事件处理过程中进行访问和使用。
以下是 PointerEventData 类中常见的属性和方法：

1. pointerId：指针的唯一标识符。用于区分不同的指针，如鼠标、触摸屏等。
2. position：指针点击的位置。通常是相对于屏幕或相对于某个 UI 元素的坐标。
3. delta：指针位置相对于上一帧的变化量。可以用于计算拖拽操作的移动距离。
4. clickCount：点击次数。记录指针点击的次数，可以用于判断单击、双击等操作。
5. button：点击的按钮。表示触发点击事件的鼠标按钮，如左键、右键等。
6. clickTime：点击的时间戳。记录指针点击事件的时间戳，可以用于计算点击操作的时间间隔。
7. pointerCurrentRaycast：当前的射线投射结果。包含有关指针点击位置的射线投射信息，如点击的对象、点击的位置等。
8. pointerDrag：拖拽的对象。如果发生了拖拽操作，该属性用于存储被拖拽的对象。
9. eligibleForClick：是否可以触发点击事件。用于判断当前指针操作是否满足触发点击事件的条件。

此外，PointerEventData 类还提供了一些辅助方法来处理指针事件，例如：

* GetPress()：检查指针按钮是否按下。
* IsPointerMoving()：检查指针是否在移动。
* IsPointerOverGameObject()：检查指针是否悬停在某个游戏对象上。

通过使用 PointerEventData 类提供的属性和方法，开发者可以获取和操作与指针事件相关的信息，以便在事件处理中进行逻辑判断和操作。
PointerEventData.pointerPressRaycast 指针按下时响应射线检测的ui,在一次点击事件中不会改变,**pointerCurrentRaycast这个会随着拖动等操作变化**

