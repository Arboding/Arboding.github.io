## Git 和 GitHub 的绑定

1. #### 获取SSH keys

  输入 cd ~/.ssh，返回"no such file or directory"表明电脑没有ssh key，需要创建ssh key。

![img](https://i-blog.csdnimg.cn/blog_migrate/c278adb498ea7f7763e7851b4132e8ff.png)

​        然后输入 ssh-keygen -t rsa -C “git账号”

![img](https://i-blog.csdnimg.cn/blog_migrate/954cf2276f4fc95b1d86627fd8db37c2.png)

​         输入之后一路（三次）Enter（确认）就可以了

​	以下截图就证明成功了，这个时候按照它给的打开以下地址：

![img](https://i-blog.csdnimg.cn/blog_migrate/0954f838b74f652f3e28d0fa05ccde55.png)

      按路径进入.ssh，里面存储的是两个ssh key的秘钥，id_rsa.pub文件里面存储的是公钥，id_rsa文件里存储的是私钥，不能告诉别人。打开id_rsa.pub文件，复制里面的内容。

![img](https://i-blog.csdnimg.cn/blog_migrate/b5e36a8ce85552624fafd8d0589c0be7.png)

####  2.绑定ssh密钥

1. ##### 接下来我们需要登录到我们的GitHub上边添加这个密匙

![img](https://i-blog.csdnimg.cn/blog_migrate/38a75dfd792d544bfaa6284fce52d646.png)

2. ##### 随便填写名字以及刚才复制的公钥（id_rsa.pub内容），添加后配置完成。

![img](https://i-blog.csdnimg.cn/blog_migrate/ba2a00b8a3e20d99ab6fef3068d7a4f1.png)

之后我们就添加成功啦！ 

![img](https://i-blog.csdnimg.cn/blog_migrate/ef0c8695931dbd171f91c94f6b2c5ef3.png)

##### 3.之后我们回到Git bash上边

​	输入：ssh -T git@github.com
​	来检查是否成功绑定。如果输入代码之后再选择yes出来是这样说明就成功啦！！！

![img](https://i-blog.csdnimg.cn/blog_migrate/09339edae9347cb993469e50caf82e43.png)

接下来还需要简单的设置一些东西。

name最好和GitHub上边的一样，email是一定要是注册GitHub的那个邮箱地址

这两个的顺序可以颠倒，没有固定的顺序。

~~~bash
git config --global user.name “gitname”
git config --global user.email “git邮箱”
~~~



 我们完成了本地 Git 与远程 GitHub 的绑定，这意味着我们已经可以通过 Git 向 GitHub 提交代码啦！

### 通过Git将代码提交到GitHub

我们需要先了解两个命令，也是我们在将来需要经常用到的两个命令，分别为push和pull。

~~~bash
push：该单词直译过来就是“推”的意思，如果我们本地的代码有了更新，为了保持本地与远程的代码同步，我们就需要把本地的代码推到远程的仓库，代码示例：

git push origin master

pull：该单词直译过来就是“拉”的意思，如果我们远程仓库的代码有了更新，同样为了保持本地与远程的代码同步，我们就需要把远程的代码拉到本地，代码示例：

git pull origin master
~~~



#### 1.克隆仓库 

下面就要将我们的库克隆下来到本地电脑中，方便以后进行上传代码。

![img](https://i-blog.csdnimg.cn/blog_migrate/33605e0c9dd5e55d7969ac6b4ec8d1b6.png)

点进仓库之后点击Code，点击ssh会看到一串网址（http也可以），这个地址就是代码地址，git clone 命令会用的到。

![img](https://i-blog.csdnimg.cn/blog_migrate/203e0089e4f082e5a60c2969d1f22cc4.png)

 接下来我们就开始选择文件存储地方了，在本地电脑中找到存储文件的地方，然后右键选择Git Bash Here：

![img](https://i-blog.csdnimg.cn/blog_migrate/7a5eebdd9ec93d112f1000d60b64d7fc.png)

然后输入 git clone 地址（这个地址就是刚刚库那个Code的上代码地址）

![img](https://i-blog.csdnimg.cn/blog_migrate/cd7e868c7e6ff095f2ac864486826002.png)

 过程有时候可能会输入账号密码啥的，记得不要输错啦！

 下图可以看到，指定目录已经存在了我们的库文件![img](https://i-blog.csdnimg.cn/blog_migrate/768e9abb6fcdaf0fdcb4c9d8d008731f.png)

 2.测试提交代码
1.打开这个文件夹，然后在其中创建一个任意格式，任意名称的文件（这里新建了一个测试文件）。

![img](https://i-blog.csdnimg.cn/blog_migrate/8ad292a64b4ff0e4a4017e65a01f9765.png)

####  2.然后同样在这个文件夹里面右键git bash进黑框框，git add我们新增的文件

#### ![img](https://i-blog.csdnimg.cn/blog_migrate/cc56b467fbdfd18d144bc8d1cc9cadbc.png)

####  3.之后输入然后git commit -m “测试是否成功” 引号内的内容可以随意改动，这个语句的意思是 给你刚刚上传的文件一个备注，方便查找记忆而已

![img](https://i-blog.csdnimg.cn/blog_migrate/1f25d81cb1a1014618922cd374092f9a.png)

####  4.接着输入push指令 git push origin main    下图就代表成功了

![img](https://i-blog.csdnimg.cn/blog_migrate/51296c5b1ceadbb2f99fc8fc889a4a6b.png)

 打开GitHub，看到刚刚上传的文件，显示成功。

![img](https://i-blog.csdnimg.cn/blog_migrate/a88a671baa90d12141d2d1099e5d5004.png)