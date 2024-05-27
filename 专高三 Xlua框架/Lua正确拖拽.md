```lua
--[[界面拖拽方法,界面拖拽效果正确]]

local function DragInterface(self,obj)

    local DragPointer=obj:AddComponent(UIPointerDrag,"")

    DragPointer:SetOnBeginDrag(function (eventData)

         NowPosition=obj.rectTransform.anchoredPosition-eventData.position--获取鼠标到界面位置的插值

    end)

    DragPointer:SetOnDrag(function (eventData)

        obj.rectTransform.anchoredPosition=eventData.position+NowPosition--在移动时加上插值

    end)

end
```
