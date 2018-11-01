git 踩坑

在windows 10下使用git客户端对github上的仓库进行操作的过程中发现：每次打开git的shell之，进行clone、push等操作会出现permission denied错误；
但是新开一个git shell仍旧会出现该问题，需要手动运行：
	eval `ssh-agent -s`
	ssh-add ~/.ssh/KEY
执行完之后在就可以连通了 测试ssh -T git@github.com

但是每次打开git bash都要配置显然不是一个IT男该干的事，所以必须找一个一劳永逸的办法
那就是 放到git的bashrc中：打开git的安装目录，进入到etc/中，使用文本编辑软件（比如Editplus）编辑 bash.bashrc 文件，在末尾添加两行：
	eval `ssh-agent -s`
	ssh-add ~/.ssh/KEY
这样，在每次新打开git的shell之后，会自动执行这两句话，并在shell中回显。
OK 问题解决。

