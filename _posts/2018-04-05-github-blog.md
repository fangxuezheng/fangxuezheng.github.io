---
layout: post
title: github blog 搭建流程 
category: github
tag: [github, blog]
---
**相关步骤：**

1、安装Node.js和配置好Node.js环境，打开cmd命令行，成功界面如下

![](https://images2017.cnblogs.com/blog/1108615/201710/1108615-20171021222335756-1508643846.png)

&nbsp;

&nbsp;2、安装Git和配置好Git环境，安装成功的象征就是在电脑上任何位置**鼠标右键**能够出现如下两个选择

&nbsp;![](https://images2017.cnblogs.com/blog/1108615/201710/1108615-20171021222542474-1351750125.png)

注意：一般出于安全考虑，只有在Git Bash Here中才能进行Git的相关操作。如果需要在cmd命令行里调用Git，那么就要配置电脑的环境变量Path，或者在安装的时候选择use Git from the Windows Command Prompt。这个可有可无，影响不大，成功配置的界面如图

![](https://images2017.cnblogs.com/blog/1108615/201710/1108615-20171021223101193-1524328031.png)

&nbsp;

&nbsp;3、Github账户注册和新建项目，项目必须要遵守格式：账户名.github.io，不然接下来会有很多麻烦。并且需要勾选Initialize this repository with a README

![](https://images2017.cnblogs.com/blog/1108615/201710/1108615-20171021223639881-1998790649.png)

&nbsp;

在建好的项目右侧有个settings按钮，点击它，向下拉到GitHub Pages，你会看到那边有个网址，访问它，你将会惊奇的发现该项目已经被部署到网络上，能够通过外网来访问它。&nbsp;

![](https://images2017.cnblogs.com/blog/1108615/201710/1108615-20171021223928802-1978574025.png)

&nbsp;

&nbsp;4、安装Hexo，在自己认为合适的地方创个文件夹，我是在D盘建了一个blog文件夹。然后通过命令行进入到该文件夹里面

![](https://images2017.cnblogs.com/blog/1108615/201710/1108615-20171021224442443-1196707159.png)

&nbsp;

输入npm install hexo -g，开始安装Hexo

![](https://images2017.cnblogs.com/blog/1108615/201710/1108615-20171021224910568-2096615217.png)

&nbsp;

输入hexo -v，检查hexo是否安装成功

![](https://images2017.cnblogs.com/blog/1108615/201710/1108615-20171021225015224-1426206003.png)

&nbsp;

输入hexo init，初始化该文件夹（有点漫长的等待。。。）

![](https://images2017.cnblogs.com/blog/1108615/201710/1108615-20171021230203912-509196411.png)

![](https://images2017.cnblogs.com/blog/1108615/201710/1108615-20171021230241646-1660449756.png)

看到后面的“Start blogging with Hexo！”，激动有木有！！！！！

&nbsp;

输入npm install，安装所需要的组件

![](https://images2017.cnblogs.com/blog/1108615/201710/1108615-20171021231521646-1099473727.png)

&nbsp;

输入hexo g，首次体验Hexo

![](https://images2017.cnblogs.com/blog/1108615/201710/1108615-20171021231705474-1404994153.png)

&nbsp;

&nbsp;输入hexo s，开启服务器，访问该网址，正式体验Hexo

![](https://images2017.cnblogs.com/blog/1108615/201710/1108615-20171021231833912-663774637.png)

问题：假如页面一直无法跳转，那么可能端口被占用了。此时我们ctrl+c停止服务器，接着输入“hexo server -p 端口号”来改变端口号

![](https://images2017.cnblogs.com/blog/1108615/201710/1108615-20171021232311912-1198771378.png)

那么出现如下图就成功了

![](https://images2017.cnblogs.com/blog/1108615/201710/1108615-20171021232413224-1288183746.png)

&nbsp;

&nbsp;

&nbsp;5、将Hexo与Github page联系起来，设置Git的user name和email（如果是第一次的话）

&nbsp;![](https://images2017.cnblogs.com/blog/1108615/201710/1108615-20171021233157224-1386748377.png)

上图是在其文件夹里面鼠标右键，点击Git Base Here。这里“feng”可以替换成自己的用户名，邮箱可以替换成自己的邮箱

&nbsp;

输入cd ~/.ssh，检查是否由.ssh的文件夹

![](https://images2017.cnblogs.com/blog/1108615/201710/1108615-20171021233543052-76995831.png)

&nbsp;

输入ls，列出该文件下的内容。下图说明存在

![](https://images2017.cnblogs.com/blog/1108615/201710/1108615-20171021233630568-279882178.png)

&nbsp;

&nbsp;输入ssh-keygen -t rsa -C “929762930@qq.com”，连续三个回车，生成密钥，最后得到了两个文件：id_rsa和id_rsa.pub（默认存储路径是：C:<span class="hljs-command">\Users<span class="hljs-command">\Administrator<span class="hljs-command">\.ssh）</span></span></span>。

&nbsp;![](https://images2017.cnblogs.com/blog/1108615/201710/1108615-20171021234107209-1205335399.png)

&nbsp;

&nbsp;输入eval "$(ssh-agent -s)"，添加密钥到ssh-agent

![](https://images2017.cnblogs.com/blog/1108615/201710/1108615-20171021234314146-695835137.png)

&nbsp;

&nbsp;再输入ssh-add ~/.ssh/id_rsa，添加生成的SSH key到ssh-agent

![](https://images2017.cnblogs.com/blog/1108615/201710/1108615-20171021234528552-610835964.png)

&nbsp;

&nbsp;登录Github，点击头像下的settings，添加ssh

&nbsp;![](https://images2017.cnblogs.com/blog/1108615/201710/1108615-20171021234636834-426105098.png)

&nbsp;

新建一个new ssh key，将id_rsa.pub文件里的内容复制上去

![](https://images2017.cnblogs.com/blog/1108615/201710/1108615-20171021234906724-1938556332.png)

&nbsp;

输入ssh -T git@github.com，测试添加ssh是否成功。如果看到Hi后面是你的用户名，就说明成功了

![](https://images2017.cnblogs.com/blog/1108615/201710/1108615-20171021235116271-1521882533.png)

<span style="color: #993300">**问题：**</span>假如ssh-key配置失败，那么只要以下步骤就能完全解决

<div>
<div>

首先，清除所有的key-pair
ssh-add -D
rm -r ~/.ssh
删除你在github中的public-key

重新生成ssh密钥对
ssh-keygen -t rsa -C "xxx@xxx.com"

接下来正常操作
在github上添加公钥public-key:
1、首先在你的终端运行 xclip -sel c ~/.ssh/id_rsa.pub将公钥内容复制到剪切板
2、在github上添加公钥时，直接复制即可
3、保存

测试：
在终端 ssh -T git@github.com</div>

</div>

&nbsp;

6、配置Deployment，在其文件夹中，找到_config.yml文件，修改repo值（在末尾）

&nbsp;![](https://images2017.cnblogs.com/blog/1108615/201710/1108615-20171021235812974-84318377.png)

&nbsp;

repo值是你在github项目里的ssh（右下角）

![](https://images2017.cnblogs.com/blog/1108615/201710/1108615-20171021235722365-818312042.png)

&nbsp;

7、新建一篇博客，在cmd执行命令：hexo new post “博客名”

![](https://images2017.cnblogs.com/blog/1108615/201710/1108615-20171022000227834-1991784353.png)

&nbsp;

&nbsp;这时候在文件夹_posts目录下将会看到已经创建的文件

![](https://images2017.cnblogs.com/blog/1108615/201710/1108615-20171022000508865-46787156.png)

&nbsp;

在生成以及部署文章之前，需要安装一个扩展：npm install hexo<span class="hljs-attribute">-deployer<span class="hljs-attribute">-git <span class="hljs-subst">--save</span></span></span>

![](https://images2017.cnblogs.com/blog/1108615/201710/1108615-20171022001237943-657272339.png)

&nbsp;

使用编辑器编好文章，那么就可以使用命令：hexo d -g，生成以及部署了

&nbsp;![](https://images2017.cnblogs.com/blog/1108615/201710/1108615-20171022001410662-1611125904.png)

&nbsp;

部署成功后访问你的地址：http://用户名.github.io。那么将看到生成的文章

![](https://images2017.cnblogs.com/blog/1108615/201710/1108615-20171022001738037-1195721153.png)

&nbsp;

&nbsp;好了，到此为止，最基本的也是最全面的hexo+github搭建博客完结。接下来是进阶的操作

&nbsp;
 

###参考资料

1. Pro Git 简体中文版
2. Git权威指南
3. 命令行man手册
