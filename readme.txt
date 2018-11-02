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