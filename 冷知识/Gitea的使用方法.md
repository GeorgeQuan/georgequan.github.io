使用SSH 时
1. 设置密钥
2. 设置自定义配置SSH \Gitea\custom\conf\app.ini  找到后在[server] 特性下面添加START_SSH_SERVER=true
	允许SSH 因为我们的系统默认没有SSH 所以需要我们手动添加
	在官网可以找到这个API[Config Cheat Sheet | Gitea Documentation](https://docs.gitea.com/next/administration/config-cheat-sheet)
	然后就可以正常使用了

关于访问
http://localhost:3000/
localhost 代表本机
3000 是端口号 在下载的时候会设置