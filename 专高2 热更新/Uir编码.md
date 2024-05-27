URI：**uniform resource identifier** 统一资源标识符，是一个用于标识某一互联网资源名称的字符串。 URL：uniform resource locator 统一资源定位符，在www上每一个信息资源都有统一的且在网上唯一的地址，该地址就叫URL。 URN：uniform resource name 统一资源名。
在c# 中有能转换成URI编码的API
```c#
string originalString = "Hello World!";
string encodedString = System.Net.WebUtility.UrlEncode(originalString);
Console.WriteLine(encodedString);
```
