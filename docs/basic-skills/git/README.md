# <center>  Git / Git-Nutzung 

## 01、认识Git

​		本地仓库与远程仓库的对接。根据现象我理解Git为前面的意思，Git在本地主机上创建一个本地仓库然后与远程仓库进行关联。完成一次开源尝试。步骤是 init --> add --> commit --> push/pull，每一个过程既是开始也是结束，周而复始的操作本地与远程的同步。声明本文章依据网上的教程加上自己的实践，文章内的图片是根据作者与网上作者公开的过程相似度无差异，索性就用他们的图片。本身这个文章是简单的实操，不存在让读者成为Git专家的可能。

​		Git是当前最先进、最主流的**分布式**版本控制系统，免费、开源！核心能力就是版本控制。再具体一点，就是面向代码文件的版本控制，代码的任何修改历史都会被记录管理起来，意味着可以恢复到到以前的任意时刻状态。支持跨区域多人协作编辑，是团队项目开发的必备基础，所以Git也就成了程序员的必备技能。  



**🟢主要特点**：

- 开源自由，使用广泛。
- 强大的文档（代码）的历史版本管理，直接记录完整快照（完整内容，而非差异），支持回滚、对比。
- 分布式多人协作的的代码协同开发，几乎所有操作都是本地执行的，支持代码合并、代码同步。
- 简单易用的分支管理，支持高效的创建分支、合并分支。

<img src="https://gitee.com/PussIn/my-images/raw/master/Gitee/%E5%9B%BE%E7%89%87/1.gif" alt="1731980489488" style="zoom: 50%;" />

# Windows环境安装及配置git并连接gitee远程仓库

### 1.下载git安装包

<img src="https://git-scm.com/images/logo@2x.png" alt="Git" style="zoom:25%;" /> [地址](https://git-scm.com/)

<img src="https://gitee.com/PussIn/my-images/raw/master/Gitee/%E5%9B%BE%E7%89%87/001.jpg" alt="1731980489488" style="zoom: 100%;" />

------



### 2.安装git



1、安装时需要联网，双击安装包并点击next

2、根据自身情况选择安装文件夹

<img src="https://gitee.com/PussIn/my-images/raw/master/Gitee/%E5%9B%BE%E7%89%87/001.jpg" alt="1731980489488" style="zoom:100%;" />



3、创建桌面图标并点击next，然后一直按照默认选项点击next即可(最后一个选项配置cmd终端)，直到出现安装按钮

<img src="https://gitee.com/PussIn/my-images/raw/master/Gitee/%E5%9B%BE%E7%89%87/002.jpg" alt="1731980489488" style="zoom:100%;" />



4、点击安装，等待安装结束

<img src="https://gitee.com/PussIn/my-images/raw/master/Gitee/%E5%9B%BE%E7%89%87/003.jpg" alt="1731980489488" style="zoom:100%;" />



5、取消勾选，点击完成。

<img src="https://gitee.com/PussIn/my-images/raw/master/Gitee/%E5%9B%BE%E7%89%87/004.jpg" alt="1731980489488" style="zoom:100%;" />



6、我们可以通过鼠标右键或者桌面图标进入git命令行，或者使用cmd打开

<img src="https://gitee.com/PussIn/my-images/raw/master/Gitee/%E5%9B%BE%E7%89%87/005.jpg" alt="1731980489488" style="zoom:100%;" />



### 3.配置用户名及邮箱

1、依次输入下面的命令来配置并查看

```
git config --global user.name "username"
git config --global user.email "email"
git config --list --global
```

2、这里的用户名和邮箱都可以随便设置，但是建议邮箱使用真实邮箱。

<img src="https://gitee.com/PussIn/my-images/raw/master/Gitee/%E5%9B%BE%E7%89%87/006.jpg" alt="1731980489488" style="zoom:100%;" />



### 4.配置gitee

1、首先登陆自己的gitee账号，点击加号新建仓库



<img src="https://gitee.com/PussIn/my-images/raw/master/Gitee/%E5%9B%BE%E7%89%87/007.jpg" alt="1731980489488" style="zoom:100%;" />



2、输入仓库名称，根据需要配置仓库的其他属性，点击创建即可

<img src="https://gitee.com/PussIn/my-images/raw/master/Gitee/%E5%9B%BE%E7%89%87/008.jpg" alt="1731980489488" style="zoom:100%;" />

3、**创建SSH公钥**

```
$ ssh-keygen -t rsa -C "自己的邮箱"

Generating public/private rsa key pair.
...
The key's randomart image is:
+---[RSA 3072]----+

+----[SHA256]-----+
```

4、继续输入以下命令，可以看到下图所示 ssh-rsa 开头的一串代码，说明生成 SSH 公钥成功**

```
cat ~/.ssh/id_rsa.pub
```

<img src="https://gitee.com/PussIn/my-images/raw/master/Gitee/%E5%9B%BE%E7%89%87/009.jpg" alt="1731980489488" style="zoom:100%;" />



**5、通过点击 Gitee 主页右上角头像 「设置」->「安全设置」->「SSH公钥」进行公钥添加 ，复制(全部选中后，鼠标右键 copy），将复制的 ssh-rsa 开头的内容添加到下图公钥框中。并点击确认按钮**

<img src="https://gitee.com/PussIn/my-images/raw/master/Gitee/%E5%9B%BE%E7%89%87/010.jpg" alt="1731980489488" style="zoom:100%;" />



**6、测试SSH连接**

```
ssh -T git@gitee.com

按照提示输入yes，回车，提示successfully之类的就说明SSH连接正常。

首次使用需要确认并添加主机到本机SSH可信列表。

```

<img src="https://gitee.com/PussIn/my-images/raw/master/Gitee/%E5%9B%BE%E7%89%87/011.jpg" alt="1731980489488" style="zoom:100%;" />



7、现在就可以在本地和gitee仓库之间进行连接了。

<img src="https://gitee.com/PussIn/my-images/raw/master/Gitee/%E5%9B%BE%E7%89%87/012.jpg" alt="1731980489488" style="zoom:100%;" />

```
$ ssh -T git@gitee.com
The authenticity of host 'gitee.com (180.76.198.225)' can't be established.
ED25519 key fingerprint is SHA256:xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx
This key is not known by any other names.
Are you sure you want to continue connecting (yes/no/[fingerprint])? yes
Warning: Permanently added 'gitee.com' (ED25519) to the list of known hosts.
Hi xxxx(@xxxx)! You've successfully authenticated, but GITEE.COM does not provide shell access.
```



### 5.建立本地仓库并提交代码

1、打开git客户端，通过cd命令进入需要上传的项目的所在文件夹，初始化本地仓库

```
git init
```

```
$ git init
Initialized empty Git repository in E:/桌面/Gitee/.git/
```



2、**初始化本地仓库并克隆远程 `x你的仓库x` 仓库，命令如下所示：**

```
git init                                #初始化仓库
git remote add origin 粘贴复制的SSH地址  #建立远程连接/关联
git clone 粘贴复制的SSH地址              #克隆远程仓库
```

```
git remote add origin 粘贴复制的SSH地址
```



3、提交

```
cd 你的文件夹              #定位到 你的文件名 文件夹
touch 测试.txt               #新建一个测试.txt文件
git add 测试.txt             #新增“测试.txt”至暂存区
git commit -m "新纪录"       #确认新增“测试.txt”至数据目录
git push -u origin master   #推送新增文件到远程仓库
```

工作原理示意图：

<img src="https://gitee.com/PussIn/my-images/raw/master/Gitee/%E5%9B%BE%E7%89%87/013.jpg" alt="1731980489488" style="zoom:100%;" />

4、**确认远程仓库中是否新增了“测试.txt”的内容**

`无图`



###  6.**删除远程仓库中的指定文件**

1、如果仓库中有多余文件想要删除，如何远程删除呢？ Git 提供了非常简单的操作指令 `git rm + 文件名`。

2、我们创建的 hello-gitee 仓库中有一个 README.en.md的文档，我们就以它为例，看看如何来删除吧！

#### 3、**删除仓库指定文件操作步骤**

1. 确保本地仓库与远程仓库内容一致
2. 在本地用命令删除想要删除的文件 “README.en.md”并确认本次删除操作
3. 推送到远程仓库，完成指定文件删除

4、具体操作可按下方代码操作：

```
git pull                    #同步远程仓库到本地
rm README.en.md             #删除本地文件
git commit -m "delete"      #确认删除并备注“delete”
git push                    #删除操作同步到远程仓库
```

```
$ git pull origin master
From gitee.com:exkk/Git-Nutzung
 * branch            master     -> FETCH_HEAD
 
$ ls
README.en.md  README.md

$ git rm README.en.md
rm 'README.en.md'

$ git commit -m "delete"
[master 203f675] delete
 1 file changed, 36 deletions(-)
 delete mode 100644 README.en.md
 
 $ git push -u origin master
Enumerating objects: 3, done.
Counting objects: 100% (3/3), done.
Delta compression using up to 16 threads
Compressing objects: 100% (1/1), done.
Writing objects: 100% (2/2), 227 bytes | 227.00 KiB/s, done.
Total 2 (delta 0), reused 0 (delta 0), pack-reused 0 (from 0)
remote: Powered by GITEE.COM [1.1.5]
remote: Set trace flag xxxxxxxxxxxx
xxxxxxxxxxxxxxx  master -> master
branch 'master' set up to track 'origin/master'.
```



5、使用clone命令，地址直接在仓库“克隆/下载”选项复制

```
git clone 地址
```

<img src="https://gitee.com/PussIn/my-images/raw/master/Gitee/%E5%9B%BE%E7%89%87/014.jpg" alt="1731980489488" style="zoom:100%;" />



## 后续

在创建远程的后的时候尽量修改默认分支的名称，以免本地当前分支对远程仓库发送时候造成后果是上传到其他的非主分支，避免操作过于同义反复。也许你的习惯不在主分支上测试和展示效果。在对各个分支合并操作的时候尽量对命令的熟悉。Git 客户端本地分支默认的`master`分支，Github建立仓库的默认是`main`，之前是`master`后来就是`main`，其原因社会的进步和反种族主义的活动，一些人认为使用master分支可能存在种族主义的隐喻。为了避免任何可能的歧义，GitHub决定将默认分支名称从master改为main。

**解决方法**

如果还是习惯于使用 `master` 分支，那么大可不用更改继续使用下去。

若想要支持相关的行动，则可以跟随以下的操作将`master`分支无损迁移到`main`分支。

### 本地修改分支

1. 首先将`master`分支移到`main`分支下

```
git branch -m master main
```

2. 随后将新命名的分支`main`推送到远程库中

```
git push -u origin main
```

3. 再将HEAD指向`main`分支

```
git symbolic-ref refs/remotes/origin/HEAD refs/remotes/origin/main
```

4. 最后删除远程库中旧的`master`分支即可

```
git push origin --delete master
```

同理

### 在 GitHub 上修改默认分支

用户、组织和企业可以在以下地址修改默认分支名。

首先，你需要将远程仓库的默认分支从 `main` 更改为其他分支`master`分支

1. **登录 GitHub**，进入你的仓库页面。
2. 点击页面上方的 **Settings**（设置）标签。
3. 在左侧菜单中选择 **Branches**（分支）。
4. 在 **Default branch** 部分，点击 **Change default branch**（更改默认分支）。
5. 在下拉菜单中选择你希望作为新默认分支的分支（例如 `master`），然后点击 **Update**。

#### **删除远程的 `main` 分支**

```
git push origin --delete main
```

#### **删除本地的 `main` 分支**

```
git branch -d main
```





开源

## 参考资料

- [博客园 | 深入浅出Git教程](https://www.cnblogs.com/syp172654682/p/7689328.html)

- [猴子都能懂的GIT入门](https://backlog.com/git-tutorial/cn/)

- [廖雪峰的GIT教程](https://www.liaoxuefeng.com/wiki/896043488029600)

- 电子书《[ProGit-Git教程](https://www.yuque.com/kanding/ktech/ng8w19)》

- Gitee码云的 [Git 大全](https://gitee.com/all-about-git)，真的挺全

- [敏捷过程实践-git代码分支管理规范](https://www.processon.com/view/59ec836de4b0c86d400e99f1)

- [易百教程-Git教程](https://www.yiibai.com/git)？

- [在线Git学习+练习](https://learngitbranching.js.org/)

- [GUI Clients](https://git-scm.com/downloads/guis) Git网站上的GUI工具列表

- [Git常用指令集合🔥🔥](https://www.yuque.com/kanding/ktech/ai3d3ky8f0dgixto)

- [Git入门图文教程(1.5W字40图)🔥🔥--深入浅出、图文并茂 ](https://www.cnblogs.com/anding/p/16987769.html)

- [Windows环境安装及配置git并连接gitee远程仓库 ](https://developer.aliyun.com/article/1361286)

- ## [Gitee操作极速上手指南](https://gitee.com/mvphp/gitee_yes)

