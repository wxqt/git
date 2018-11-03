/* Git 操作流程 */

	- 把当前目录变成Git可以管理的仓库
		git init

	- 把文件添加到仓库
		git add readme.txt
		git add file1.txt
		git add file2.txt file3.txt
		
	- 把文件提交到仓库 并加上说明【-m 后面为说明】
		git commit -m "the first add"
		
	- 修改后的文件用git status查看状态 如果有修改 用git diff查看改动 然后再执行上两步提交
		git status
		git dif readme.txt
		git add readme.txt
		git commit -m "Second add"
		
		git status 【最后查看有没有要提交的文件】
		
	- 用git log 查看提交记录 --pretty=oneline可以单行显示
		git log

	- 回退记录 git reset --hard "id" 将HEAD指针指向commit id就可以了
	- 也可以git reset --hard HEAD^回退上一个
	- 也可以git reset --hard HEAD^^回退上两个 或 HEAD^^^^^^^^n个
		git reset --hard HEAD^
		
	- 回退记录后git log找不到最近的记录了 用git reflog 查看以往的命令记录 找到commit id 再执行git reset
		$ git reflog
		a079f31 (HEAD -> master) HEAD@{0}: reset: moving to HEAD^
		c27af6e HEAD@{1}: commit: asdfadf
		a079f31 (HEAD -> master) HEAD@{2}: commit: add log
		def03e0 HEAD@{3}: commit: third add
		c42c414 HEAD@{4}: commit: second modfiy
		c4f4057 HEAD@{5}: commit (initial): the first add
		
	- 撤销修改 在git add后并没有commit 文件只是在暂存区 这时用git checkout -- readme.txt 就可以回退到上一个提交 把工作区的改动回退到以前
	- 用git reset HEAD readme.txt 把暂存区的文件重新放回工作区 工作区的改动不变
	
	- 删除文件 先手动删队文件 再git rm file 再git commit -m "del file" 
	- 不想删了 git checkout -- file 从版本库中恢复到工作区
	- 已经删除的文件只能从版本库中恢复到最新的版本
	
	- 添加远程库
		* 首先查看本机Git主目录 cd ~ 下有没有.ssh文件夹 如果有 看里面有没有id_rsa和id_rsa.pub这两个文件
		* 如果没有 在主目录下
			ssh-keygen -t rsa -C “youremail@example.com"
		* 生成后id_rsa.pub文件中的内容添加到github上
		* 在github上新建库 把本地库添加到远程库
			git remote add origin git@github.com:wxqt/git.git  //连接远程库
			git push -u origin master			//推送本地库  -u 第一次使用后就把两端自动连接 以后就不用再加了
			
	- 从远程库克隆
		* 先从行程建库 然后克隆到本地
			$ git clone git@github.com:wxqt/gitclone.git
	
	
	- 创建分支
		git branch dev
	- 切换到分支
		git checkout dev
	- 也可以用	-b  创建加切换
		git checkout -b dev
	- 查看分支
		git branch		//带*号的为当前分支
	- 合并分支 切换到主分支中 将dev合并到masterdx                                                                                     
		git merge dev
	- 删除分支
		git branch -d dev
		

	- 解决冲突
		当Git无法自动合并分支时，就必须首先解决冲突。解决冲突后，再提交，合并完成。
		解决冲突就是把Git合并失败的文件手动编辑为我们希望的内容，再提交。
		用git log --graph命令可以看到分支合并图。
		

	- 分支管理策略
		合并分支时，加上--no-ff参数就可以用普通模式合并，合并后的历史有分支，能看出来曾经做过合并
		git merge --no-ff -m "add no-ff" dev
		
		查看分支历史
		git log --graph --pretty=oneline --abbrev-commit
		
<<<<<<< HEAD
		def03e0
		
		dlkflkdsf
=======
>>>>>>> dev
