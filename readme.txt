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
	
	-
	
	