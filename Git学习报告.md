# Git学习报告

## 安装

终端输入sudo install git

如果提示要运行	 ```git config --global user.email "you@example.com"
  								  		 git config --global user.name "Your Name"```

就在终端输入指令，邮箱和名字改成自己的

## 创建版本库

1. 创建一个空目录：

```c
$ mkdir gitfile 
$ cd gitfile 
$ pwd
```

2. 把这个目录变成Git可以管理的仓库

```c
$ git init
```

## 添加文件到版本库

1. 编写文件

2. 把编写的文件放到gitfile（在主目录里找找）里去

3. 添加文件到仓库

   ```c
   $ git add filename
   ```

   成功后无提示

4. 提交文件，xxxx是这次提交文件的说明

   ```c
   $ git commit -m "xxxx"
   ```

   成功后提示 1 file changed, 2 insertions(+)

   可以一次add多个文件，然后一次性commit

## 版本管理

1. 修改文件后查看状态（有哪些文件被修改，是否已提交）：

   ```c
   $ git status
   ```

   查看文件的修改内容（不加filename也可以）

   ```c
   $ git diff filename 
   ```

   提交修改

   ```c
   $ git add filename 
   $ git commit -m "说明" 
   ```

   提交之后，再运行git status和git diff就和刚才不一样了

   ==每次commit就相当于保存一个快照，想回退时就是用每次commit的内容

2. 版本回退：

   查看每次修改概要（不加filename也可以）,显示每次commit的人和日期

   ```c
    $ git log filename
   ```

   查看版本号

   ```c
   $ git log --pretty=oneline
   ```

   回退版本（HEAD^回退一个版本，HEAD ^^两个版本，HEAD~100回退100个）

   ``` c
   $ git reset --hard HEAD^
   ```

   版本跳转（可以向已经回退过的版本跳转）

   ```c
   $ git reflog（得到历次命令的历史记录）
   ```

   ```c
   $ git reset --hard  xxxx(上面得到的commit id的前几位)
   ```

3. 其他

   删除文件

   ```c
   $ rm filename
   ```

   然后sit status 会提示文件被删除

   如果真删，用`` $ git rm filename``然后``$ git commit``

   如果撤回（相当于用版本库中的文件代替），用``$ git checkout -- filename``

 ## 使用github

### 建立远程仓库

1. 注册并登陆github
2. 右上角点击加号，再点New repository，输入Repository name，点击“Create repository”按钮，创建一个新仓库

3. 在本地终端运行``$ git remote add origin git@github.com:xxxx.git(自己的账户名、库名，网页标签上有)``

4. 配置SSH Key，按照<https://blog.csdn.net/u013778905/article/details/83501204>

5. 然后git push -u origin master推送master分支
6. 随后有任何更改使用命令``$ git push origin master``推送最新修改

### 在github上提交代码

点击Create new file并按提示操作

### 提交文件

点击Upload files并按提示操作