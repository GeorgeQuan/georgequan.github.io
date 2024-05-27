```
	git clone 后面是库的地址,这句是克隆的意思,当我们需要从远程服务器复制库的时候会用到它
	
	git add .  跟踪当前目录
	
	git status 查看当前目录下哪些是已经修改没有暂存  status颜色 也可以用来查看冲突
	1. 绿色：表示该文件已被修改并已添加到暂存区（Staging Area）。这些文件将在下一次提交         （`git commit`）时包含在版本控制中
	2. 红色：表示该文件已被修改，但尚未添加到暂存区。这些文件的修改尚未被记录或保存到版本控制中
	3. 白色：表示该文件未被修改，也未被添加到暂存区。这些文件在当前状态下与最新的提交版本一致。
	.vs 可能会导致git没有权限访问文件,解决方法:在库中创建.gitignore 文件,(忽略工程项目中的文件的版本控制),每一行写一个名字(要忽略的文件名字),可以用git status 来确认是否忽略成功
	github 有自己的过滤脚本  
	
	git commit -m '本次提交的内容'  //每次提交之前都需要先 git add 你想要修改的文件名字,如果都要修改就git add .    
	可以简写为git commit -am 'feature1'
	
	
	git reset head~ --soft  用于重置最近的一次提交并保留更改,但是不能应用与只有一次提交的情况
	git reset head~ --hard 用于重置最近的一次提交并不保留,但是不能应用与只有一次提交的情况
	一般head 代表的是最近的一次提交而加上~就是最近一次提交的上一次提交
	
	git diff 是一个 Git 命令，用于显示当前工作目录与暂存区（或最新提交）之间的差异。
	
	git log 是一个 Git 命令，用于查看当前分支的提交历史。
	我们可以自定义log 打印的格式 比如说git log --pretty=oneline 把一次提交显示在一行
	git log --graph 图形化显示,多分支的时候看着清晰
	git log --all 查看所有分支的提交
	git log --all --graph 查看并显示分支
	
	git remote add orgin https://github.com/GeorgeQuan/PlaneServer.git
	这个命令用于将远程仓库添加到你的本地 Git 仓库中，并将其命名为 "origin"
	可以通过 git remote 来查看
	如果你想修改仓库的名字的话git remote rename origin orgin (先写原仓库名字,后写新仓库名字)
	git remote -v 查看当前的仓库
	git remote remove backup 移除远程仓库 后面是仓库名字
	
	git branch feature1  创建分支,后面是分支名字,
	git branch --list 查看所有的分支
	git checkout feature1   切换分支 后面的是分支名字
	如果你想创建分支并切换过去git checkout -b feature2
	
	git merge feature1 合并分支把目标分支合并到当前分支上
	
	
 	

	
	
	
	
	
```
### 哪些文件不需要进行版本控制
[gitignore/Unity.gitignore 位于 main · github/gitignore --- gitignore/Unity.gitignore at main · github/gitignore](https://github.com/github/gitignore/blob/main/Unity.gitignore)
上面是github 官方写的gitignore ,个人项目直接复制就行了
在 Unity 项目中，通常建议对以下文件夹进行版本控制：

1. Assets 文件夹：这是存放项目资源的主要文件夹，包括场景、脚本、材质、纹理、模型等。这些文件是项目的核心部分，需要进行版本控制以确保团队成员之间的协作和版本管理。
    
2. ProjectSettings 文件夹：此文件夹包含了 Unity 项目的设置文件，如输入设置、渲染设置、平台设置等。这些设置对于项目的一致性和协作非常重要，因此应进行版本控制。
    
3. Packages 文件夹：如果你的项目使用 Unity Package Manager 管理第三方依赖或插件，Packages 文件夹包含了这些依赖的信息。为了确保项目的一致性和可重现性，应该对 Packages 文件夹进行版本控制。
    
4. ProjectName.sln 和 ProjectName.csproj（或其他相关项目文件）：如果你的 Unity 项目与 Visual Studio 或其他外部 IDE 集成，这些生成的解决方案和项目文件应该进行版本控制。这样可以确保团队成员在不同环境中能够正确地打开和编辑项目。
    

需要注意的是，对于一些自动生成的文件或临时文件，通常应该将其添加到 `.gitignore` 文件中进行忽略，以避免将这些不必要的文件添加到版本控制中。一些常见的应该忽略的文件或文件夹包括：

- Library 文件夹：Unity 自动生成的库文件和缓存文件。
- Temp 文件夹：Unity 自动生成的临时文件。
- obj 文件夹：编译过程中生成的目标文件。
- Builds 文件夹：构建输出的文件夹。
- .vscode 文件夹：Visual Studio Code 相关的设置文件夹（如果你使用 Visual Studio Code）。

通过 `.gitignore` 文件可以指定要忽略的文件和文件夹，确保不会将不必要的文件添加到版本控制中。
