我们在编写完.cs代码后,unity会转圈编译,这个时候就是在编译成中间语言IL并保存在dll文件中,在运行的时候会把dll文件变成机械码进行运行
- **启动应用程序**：
    
    - 当用户双击 `MyGame.exe` 文件时，操作系统启动该可执行文件。
    - `.exe` 文件作为应用程序的入口点，负责初始化和启动 Unity 引擎。
- **加载 DLL 文件**：
    
    - `MyGame.exe` 启动后，Unity 引擎会加载 `MyGame_Data/Managed` 文件夹中的 DLL 文件。
    - 这些 DLL 文件包含了编译后的中间语言（IL）代码，Unity 引擎使用 JIT 编译（Mono）或 AOT 编译（IL2CPP）将其转换为机器码并执行。