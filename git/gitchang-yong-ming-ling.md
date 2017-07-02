config git

	git config --global user.name "\*\*\*"

	git config --global user.email "@\*\*\*gmail.com"

	git config --global color.ui true

	git config --global alias.st status \(change status to st/git st\)

	git config --global alisa.co checkout

	git config --global alias.ci commit

	git config --global alias.br branch

	git config --global alias.unstage 'reset HEAD'

	git config --global alias.last 'log -1'

	git config --global alias.lg "log --color --graph --

		pretty=format:'%Cred%h%Creset -%C\(yellow\)%d%Creset %s %Cgreen\(%cr\)

		%C\(bold blue\)&lt;%an&gt;%Creset' --abbrev-commit"

	

Create Repository

	git init path

	

add to 	stage

	git add readme.txt

	

commit to master 

	git commit readme.txt -m "message"

	git commit -m "message" \(commit all from stage\)

	

look current workspace status 

	git status

	

look difference

	git diff readme.txt

	

look history record

	git log readme.txt

	git log readme.txt --pretty=oneline

	git log --graph\(look branch merge\)  

	git log --abbrev-commit

	

look record command

	git reflog readme.txt

	

version roolback

	git reset --hard Head^ \(back to previous version\)

	git reset --hard commitId

	

back to the most recent git commit/git add

	git checkout -- readme.txt



cancel the change of stage

	git reset HEAD readme.txt

	

delete file

	ex:

		git add test.txt

		git commit test.txt -m "add test.txt"

		rm -rf test.txt

		git status

			git commit or git checkout -- test.txt

		

remote

	

create shh key \(make sure only you can change this repository\)

	ssh-keygen -t rsa -c \*\*\*\*@gamil.com

	login github 

	open Account settings 

	click sshkeys

	click ssh key

	

create a new repository on the command line

	git init

	git add README.md

	git commit -m "first commit"

	git remote add origin git@github.com:MorrisWare01/Test.git

	git push -u origin master

	

push an existing repository from the command line

	git remote add origin git@github.com:MorrisWare01/Test.git

	git push -u origin master

	

push master 

	git push -u origin master \(-u linked the remote master named origin\)

	git push origin master

	git push origin dev

	

clone master

	git clone git@github.com:MorrisWare01/Test.git

	git checkout -b dev origin/dev



create branch

	git branch \*\*\*



switch branch

	git checkout \*\*\*

	

create branch and switch the new branch	

	git checkout -b \*\*\*

	

look all branch

	git branch\(now have \*\)



merge \*\*\* to master

	git merge \*\*\* \(Fast-forward \*master-&gt;\*\*\*\)

	git merge --no-ff -m "message" \*\*\* \(don't use ff\)	

	

delete merge

	git branch -d \*\*\*

	git branch -D \*\*\* \(delete forcibly/enforce\)

		

save work directory

	git stash

	

look work directory

	git stash list

	

restore work directory

	git stash apply stash@{\*}



delete stash 

	git stash drop stash@{\*}

	

restore work directory and delete stash 

	git stash pop stash@{\*}

	

look remote message

	git remote

	git remote -v \(detail\) fetch/push if you have Permission

	

pull remote to master or dev

	git pull 

	git branch --set-upstream dev origin/dev 

	\(no tracking infomation\)指定本地dev分支和远程origin/dev分支的链接



create tags

	git tag \*\*\* \(present branch\)

	git tag \*\*\* commitId

	git tag -a v1.0 -m "version 1.0 release" commitId

	git tag -s v1.0 -m "version 1.0 release by s" commitId

	

look tags

	git tag

	git show tagname



delete tags

	git tag -d tagname

	git push origin :refs/tags/tagname

	

push tags to remote origin

	git push origin tagname

	git push origin --tags\(push all tags\)



	

config .gitnore	

	忽略文件的原则是：

		1. 忽略操作系统自动生成的文件，如缩略图等；

		2. 忽略编译生成的中间文件、可执行文件等，也就是如果一个文件是通过另一个文件自

		动生成的，那自动生成的文件就没必要放进版本库，比如Java编译产生的.class文

		件；

		3. 忽略你自己的带有敏感信息的配置文件，比如存放⼝令的配置文件。

		

