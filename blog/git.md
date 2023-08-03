## GIT

git 官网：
https://git-scm.com/book/zh/v2

<!-- 教程 -->
https://backlog.com/git-tutorial/cn/contents/

<!-- git-recipes -->
https://github.com/geeeeeeeeek/git-recipes

<!-- Git 的奇技淫巧 -->
https://github.com/521xueweihan/git-tips


<!-- git 提交规范 -->
https://github.com/commitizen/cz-cli

## Learn Git Branching 
(在线交互方式学习  git)

## 一、新建代码库

# 在当前目录新建一个Git代码库
$ git init

# 新建一个目录，将其初始化为Git代码库
$ git init [project-name]

# 下载一个项目和它的整个代码历史
$ git clone [url]


## 初始化配置

# 显示当前的Git配置
$ git config --list

# 编辑Git配置文件
$ git config -e [--global]

git config --global user.name [username]

git config --global user.email [email]

ssh-keygen -t rsa -C "2632734769@qq.com"

cat ~/.ssh/id_rsa.pub

cd ~/.ssh


## 三、增加/删除文件

# 添加指定文件到暂存区
$ git add [file1] [file2] ...

# 添加指定目录到暂存区，包括子目录
$ git add [dir]

# 添加当前目录的所有文件到暂存区
$ git add .

# 添加每个变化前，都会要求确认
# 对于同一个文件的多处变化，可以实现分次提交
$ git add -p


## 四、代码提交

# 删除工作区文件，并且将这次删除放入暂存区
$ git rm [file1] [file2] ...

# 停止追踪指定文件，但该文件会保留在工作区
$ git rm --cached [file]

# 改名文件，并且将这个改名放入暂存区
$ git mv [file-original] [file-renamed]

# 提交暂存区到仓库区
$ git commit -m [message]

# 提交暂存区的指定文件到仓库区
$ git commit [file1] [file2] ... -m [message]

# 提交工作区自上次commit之后的变化，直接到仓库区
$ git commit -a

# 提交时显示所有diff信息
$ git commit -v

# 使用一次新的commit，替代上一次提交
# 如果代码没有任何新变化，则用来改写上一次commit的提交信息
$ git commit --amend -m [message]

# 重做上一次commit，并包括指定文件的新变化
$ git commit --amend [file1] [file2] ...



## 五、分支

# 列出所有本地分支
$ git branch

# 列出所有远程分支
$ git branch -r

# 列出所有本地分支和远程分支
$ git branch -a

# 新建一个分支，但依然停留在当前分支
$ git branch [branch-name]

# 新建一个分支，并切换到该分支
$ git checkout -b [branch]

# 切换到指定分支，并更新工作区
$ git checkout [branch-name]

# 切换到上一个分支
$ git checkout -

# 建立追踪关系，在现有分支与指定的远程分支之间
$ git branch --set-upstream [branch] [remote-branch]

# 合并指定分支到当前分支
$ git merge [branch]
git merge --abort

# 选择一个commit，合并进当前分支
$ git cherry-pick [commit]

# 删除分支
$ git branch -d [branch-name]

# 删除远程分支
$ git push origin --delete [branch-name]
$ git branch -dr [remote/branch]


## 六、标签

# 列出所有tag
$ git tag

# 新建一个tag在当前commit
$ git tag [tag]

# 新建一个tag在指定commit
$ git tag [tag] [commit]

# 删除本地tag
$ git tag -d [tag]

# 删除远程tag
$ git push origin :refs/tags/[tagName]

# 查看tag信息
$ git show [tag]

# 提交指定tag
$ git push [remote] [tag]

# 提交所有tag
$ git push [remote] --tags

# 新建一个分支，指向某个tag
$ git checkout -b [branch] [tag]

命令git push origin <tagname>可以推送一个本地标签；

命令git push origin --tags可以推送全部未推送过的本地标签；

命令git tag -d <tagname>可以删除一个本地标签；

命令git push origin :refs/tags/<tagname>可以删除一个远程标签。


删除本地分支：git branch -d 分支名（remotes/origin/分支名）

强制删本地：git branch -D 分支名

删除远程分支：git push origin --delete 分支名（remotes/origin/分支名）
where node

git branch --set-upstream-to=origin/<branch>      master

关联分支：
$ git remote add origin git@github.com:michaelliao/learngit.git

## 七、查看信息

# 显示有变更的文件
$ git status

# 显示当前分支的版本历史
$ git log
git log --graph --pretty=oneline --abbrev-commit

# 显示commit历史，以及每次commit发生变更的文件
$ git log --stat

# 搜索提交历史，根据关键词
$ git log -S [keyword]

# 显示某个commit之后的所有变动，每个commit占据一行
$ git log [tag] HEAD --pretty=format:%s

# 显示某个commit之后的所有变动，其"提交说明"必须符合搜索条件
$ git log [tag] HEAD --grep feature

# 显示指定文件是什么人在什么时间修改过
$ git blame [file]

# 显示暂存区和工作区的差异
$ git diff

# 显示暂存区和上一个commit的差异
$ git diff --cached [file]

# 显示工作区与当前分支最新commit之间的差异
$ git diff HEAD

# 显示两次提交之间的差异
$ git diff [first-branch]...[second-branch]

# 显示今天你写了多少行代码
$ git diff --shortstat "@{0 day ago}"

# 显示某次提交时，某个文件的内容
$ git show [commit]:[filename]

# 显示当前分支的最近几次提交
$ git reflog


## 八、远程同步

# 下载远程仓库的所有变动
$ git fetch [remote]

# 显示所有远程仓库
$ git remote -v

# 显示某个远程仓库的信息
$ git remote show [remote]

# 取回远程仓库的变化，并与本地分支合并
$ git pull [remote] [branch]

# 上传本地指定分支到远程仓库
$ git push [remote] [branch]

# 强行推送当前分支到远程仓库，即使有冲突
$ git push [remote] --force

# 推送所有分支到远程仓库
$ git push [remote] --all

### .gitignore

如果文件已经提交了，再写忽略规则那么不会生效，必须提交之前写上


如果你确实想添加该文件，可以用-f强制添加到Git：

$ git add -f App.class
或者你发现，可能是.gitignore写得有问题，需要找出来到底哪个规则写错了，可以用git check-ignore命令检查：

$ git check-ignore -v App.class
.gitignore:3:*.class	App.class
Git会告诉我们，.gitignore的第3行规则忽略了该文件，于是我们就可以知道应该修订哪个规则。


### config

 cat .git/config



### git 撤销之前

1. 未添加到暂存区的撤销(没有git add)

```
git checkout -- filename来撤销修改
```

2. 下面是添加到暂存区的 git add (注意不是 --hard)

```
git reset HEAD
```

3. -soft 只是撤销commit，保留到暂存区

```
git reset –soft HEAD^ 重置HEAD到上一版本，即撤销commit操作，不影响index和workdir。
git reset –soft HEAD^1 ^后面的数字表示恢复到哪个父提交的版本，一个提交可能会对应多个父提交，用于指定回到哪个
git reset –soft commitid 后面添加comiit_id指明回退到哪个版本
```

4. 撤销commit和add 保留到本地文件

```
git reset –mixed HEAD^ 效果同git reset HEAD^
git reset –mixed HEAD^1 ^后面的数字表示恢复到哪个父提交的版本，一个提交可能会对应多个父提交，用于指定回到哪个
```

5. 撤销commit、add操作，并将本地版本也重置为上一版本， 直接将commit节点去掉

```
git reset –hard HEAD^ 重置head到上一版本，会覆盖index， –hard会使head、index、workdir都重置回之前的版本，远程服务器上不会变，如果希望远程服务器上也回到上一版本的话，就使用一下git push –force。
git reset –hard HEAD^1 ^后面的数字表示恢复到哪个父提交的版本，一个提交可能会对应多个父提交，用于指定回到哪个
git reset –hard commitid 用commit_id指定回到哪次 commit
```


6. 如果当commit提交后想撤销的话，这就需要revert命令。git revert 命令是撤销某次操作，而在此次操作之前和之后的提交记录都会保留。

```
git    revert 2842c8065322085c31fb7b8207b6296047c4ea3
```

7. git revert

```
git revert commitid 使用某一次提交覆盖当前，已达到恢复到某次的效果。revert之后执行一次git push同步到server。
```


[参考1](https://blog.csdn.net/qq_25730711/article/details/53581231)

　　(1)git reset命令
　　　　1.git reset –mixed + 版本号
　　　　　　暂存区(add/index区)和提交区(commit区)会回退到某个版本，但代码不改变。
　　　　2.git reset –soft + 版本号
　　　　　　提交区(commit区)会回退到某个版本，暂存区(add/index区)不会回退，代码不改变。
　　　　3.git reset –hard + 版本号
　　　　　　暂存区(add/index区)和提交区(commit区)会回退到某个版本，代码会改变。(推荐)

　　(2)git revert命令

　　　　git revert + 版本号
　　　　　　远程master和本地master都会回退到某个版本。暂存区(add/index区)和提交区(commit区)会回退到


## 注意事项

### 1. git pull 和 git fetch 的区别。

简单来说 git pull === git fetch + git merge

参考： https://blog.csdn.net/riddle1981/article/details/74938111

### 2. git rebase 和 git merge 的区别

简单来说

1. git rebase 不会多出一个commit , git merge 会出现一个commit
2. git rebase 最后呈现的是一条直线 相当于移交, git merge 最后保留的是一次性复制代码到merge的target分支并提交
3. git rebase 会查找每次的commit 并且解决冲突文件直到最后的文件冲突解决完，git merge 只需要解决最后的代码冲突即可

当需要保留详细的合并信息的时候建议使用git merge，特别是需要将分支合并进入master分支时；当发现自己修改某个功能时，频繁进行了git commit提交时，发现其实过多的提交信息没有必要时，可以尝试git rebase。

参考： https://juejin.im/post/5af26c4d5188256728605809

### 3. git 分支管理实践

参考：https://nvie.com/posts/a-successful-git-branching-model/

### 4. svn git 区别

参考：https://www.jianshu.com/p/bfec042349ca

### 5. 关于git stash

```
git stash
stash 命令就会将你此时工作区的代码存起来，待你想继续工作时，执行

git stash apply
```
参考： cnblogs.com/zndxall/archive/2018/09/04/9586088.html

TODO:
3. git 底层原理

## 如何解除关联

git remote rm 远程仓库名，这里是origin,

git remote rm origin

git remote -v

再查看是否有关联的远程仓库 git remote -v 发现没有了。

第一步：先把本地项目作为git仓库，git init。

第二步：把本地git仓库关联到远程仓库 git remote add origin <你的项目地址>。




# npm 及 node 命令

	https://www.npmjs.com.cn/                       官网网址

	使用淘宝命令：

	$ npm install --registry=https://registry.npm.taobao.org

	$ npm install -g cnpm --registry=https://registry.npm.taobao.org

	$ cnpm install [name]

---

	升级npm以及node.js

	npm install npm@latest -g   升级npm

	node.js                     直接下载覆盖原来路径即可

	where node                  查看node的安装路径

---

	更新全局包：
	npm update <name> -g

	更新生产环境依赖包：
	npm update <name> --save

	更新开发环境依赖包：
	npm update <name> --save-dev

---


npm uninstall -g @tarojs/cli
npm install -g @tarojs/cli@3.0.18
yarn global remove @tarojs/cli
yarn global add @tarojs/cli@3.0.18

npm list -g --depth 0

yarn global list


Bash

<!-- 教程参考 -->
https://wangdoc.com/bash/grammar.html


版本： bash --versioin

## echo


1. 默认情况下，echo输出的文本末尾会有一个回车符。-n参数可以取消末尾的回车符，使得下一个提示符紧跟在输出内容的后面。

```
$ echo a;echo b
a
b

$ echo -n a;echo b
ab
```

2. -e参数 转义字符

```
$ echo "Hello\nWorld"
Hello\nWorld

# 双引号的情况
$ echo -e "Hello\nWorld"
Hello
World

# 单引号的情况
$ echo -e 'Hello\nWorld'
Hello
World
```

3. bash 单个命令一般都是一行，用户按下回车键，就开始执行。有些命令比较长，写成多行会有利于阅读和编辑，这时可以在每一行的结尾加上反斜杠，Bash 就会将下一行跟当前行放在一起解释。

```
$ echo foo bar

# 等同于
$ echo foo \
bar
```

4. 分号

分号（;）是命令的结束符，使得一行可以放置多个命令，上一个命令执行结束后，再执行第二个命令。
注意，使用分号时，第二个命令总是接着第一个命令执行，不管第一个命令执行成功或失败。

```
$ clear; ls
```

5. 命令的组合符&&和||

除了分号，Bash 还提供两个命令组合符&&和||，允许更好地控制多个命令之间的继发关系。

```Command1 && Command2```
上面命令的意思是，如果Command1命令运行成功，则继续运行Command2命令。

```Command1 || Command2```
上面命令的意思是，如果Command1命令运行失败，则继续运行Command2命令。

```
Ctrl + L：清除屏幕并将当前行移到页面顶部。
Ctrl + C：中止当前正在执行的命令。
Shift + PageUp：向上滚动。
Shift + PageDown：向下滚动。
Ctrl + U：从光标位置删除到行首。
Ctrl + K：从光标位置删除到行尾。
Ctrl + D：关闭 Shell 会话。
↑，↓：浏览已执行命令的历史记录。
```


## 扩展

1. ? 字符扩展
?字符代表文件路径里面的任意单个字符，不包括空字符。比如，Data???匹配所有Data后面跟着三个字符的文件名。


如果匹配多个字符，就需要多个?连用。

- 存在文件 a.txt、b.txt 和 ab.txt

```
$ ls ??.txt
ab.txt
```

2. * 字符扩展

*字符代表文件路径里面的任意数量的任意字符，包括零个字符。

# 存在文件 a.txt、b.txt 和 ab.txt
$ ls *.txt
a.txt b.txt ab.txt
上面例子中，*.txt代表后缀名为.txt的所有文件。

如果想输出当前目录的所有文件，直接用*即可。

$ ls *
*可以匹配空字符，下面是一个例子。

# 存在文件 a.txt、b.txt 和 ab.txt
$ ls a*.txt
a.txt ab.txt

$ ls *b*
b.txt ab.txt
注意，*不会匹配隐藏文件（以.开头的文件），即ls *不会输出隐藏文件。

如果要匹配隐藏文件，需要写成.*。

# 显示所有隐藏文件
$ echo .*




- 方括号扩展

方括号扩展的形式是[...]，只有文件确实存在的前提下才会扩展。如果文件不存在，就会原样输出。括号之中的任意一个字符。比如，[aeiou]可以匹配五个元音字母中的任意一个。

# 存在文件 a.txt 和 b.txt
$ ls [ab].txt
a.txt b.txt

# 只存在文件 a.txt
$ ls [ab].txt
a.txt
上面例子中，[ab]可以匹配a或b，前提是确实存在相应的文件。


- [start-end] 扩展

方括号扩展有一个简写形式[start-end]，表示匹配一个连续的范围。比如，[a-c]等同于[abc]，[0-9]匹配[0123456789]。

# 存在文件 a.txt、b.txt 和 c.txt
```
$ ls [a-c].txt
a.txt
b.txt
c.txt
```

# 存在文件 report1.txt、report2.txt 和 report3.txt

```
$ ls report[0-9].txt
report1.txt
report2.txt
report3.txt
...
```

- 大括号扩展

大括号扩展{...}表示分别扩展成大括号里面的所有值，各个值之间使用逗号分隔。比如，{1,2,3}扩展成1 2 3。

```
$ echo {1,2,3}
1 2 3

$ echo d{a,e,i,u,o}g
dag deg dig dug dog

$ echo Front-{A,B,C}-Back
Front-A-Back Front-B-Back Front-C-Back
```

- {start..end} 扩展

大括号扩展有一个简写形式{start..end}，表示扩展成一个连续序列。比如，{a..z}可以扩展成26个小写英文字母。

$ echo {a..c}
a b c

$ echo d{a..d}g
dag dbg dcg ddg

$ echo {1..4}
1 2 3 4

$ echo Number_{1..5}
Number_1 Number_2 Number_3 Number_4 Number_5



一、打标签：

git tag -a v1.01 -m "Relase version 1.01"
注解：git tag 是打标签的命令，-a 是添加标签，其后要跟 新标签号，-m 及后面的字符串是对该标签的注释。


二、提交标签到远程仓库：

git push origin --tags
注解：就像git push origin master 把本地修改提交到远程仓库一样，--tags可以把本地的打的标签全部提交到远程仓库。


三、删除标签：
git tag -d v1.01
注解：-d 表示删除，后面跟要删除的tag名字；


四、删除远程标签
git push origin :refs/tags/v1.01
注解：就像git push origin :branch_1 可以删除远程仓库的分支branch_1一样， 冒号前为空表示删除远程仓库的tag。


五、查看标签

git tag
或者
git tag -l

---

git pull : 首先，基于本地的FETCH_HEAD记录，比对本地的FETCH_HEAD记录与远程仓库的版本号，然后git fetch 获得当前指向的远程分支的后续版本的数据，然后再利用git merge将其与本地的当前分支合并。所以可以认为git pull是git fetch和git merge两个步骤的结合。


git pull --rebase 和 git pull 区别

https://www.cnblogs.com/kevingrace/p/5896706.html


GIT:
https://backlog.com/git-tutorial/cn/intro/intro1_1.html
https://geeeeeeeeek.github.io/git-recipes/
