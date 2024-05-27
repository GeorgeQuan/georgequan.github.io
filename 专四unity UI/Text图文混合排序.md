# Text图文混合排序


首先用建造Texas(TMP)ui组件,![[./_resources/Text图文混合排序.resources/unknown_filename.1.png|216x0]]点击引入,引入后会多一个
![[./_resources/Text图文混合排序.resources/unknown_filename.2.png|138x0]]这样的文件夹![[./_resources/Text图文混合排序.resources/unknown_filename.png|67x0]]输入索引得到一个图片.
但是默认的文字是不允许输入中文的所以我们需要为它添加新的字体.
点击Window->TextMathPow->![[./_resources/Text图文混合排序.resources/unknown_filename.3.png]]  找到生成字体的面板.
一下是输入好的面板
首先你需要一个字体,经过文件夹拖到Source Font  File 里面
其次需要建立文本里面输入你想要的文字把它拖进Characer File 里面
其中Atlas Resolution 是调节字体的清晰度 切记不要太高不然会白底 也不能太低
CharacterSet 中我们设置成Characters from File 文字设置模式
之后点击Generate Font Atlas后就能创建出可用的文件了.
![[./_resources/Text图文混合排序.resources/unknown_filename.4.png|172x0]]

同样在项目中也能使用该ui 
但是需要引入using TMPro 
**TextMeshProUGUI 这个类型****![[./_resources/Text图文混合排序.resources/unknown_filename.6.png|187x0]]**
**![[./_resources/Text图文混合排序.resources/unknown_filename.5.png|221x0]]像这样就能使用了**
**Rerct Transform 是ui自带的一种组价它比transfrom更精准**
**![[./_resources/Text图文混合排序.resources/unknown_filename.7.png|500x0]]**
快速创建字体,拖入字体后右键找到Font Asset
