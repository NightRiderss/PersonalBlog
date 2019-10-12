---
title: 如何用HEXO免费搭建个人博客
tags: 
date: 2019-10-10 20:54:00
cover: http://pz767zynd.bkt.clouddn.com/2019-10-10-1.jpg
---
----
# 前言
 本教程基于windows系统，用的是[Hexo](https://hexo.io/zh-cn/)的框架，服务器也是选的github免费的静态挂载page，所以windows系统方便我们平常的博客的更新。
# 准备
+ 安装nodejs
+ 安装Git
+ 注册GitHub账号
+ 注册域名
****
# 过程
- 安装nodejs  
进入[nodejs官网](https://nodejs.org/en/) 首页就是下载页面有两个<font color="green">绿色下载按钮</font>**下载**左边的稳定版一路Next安装  
::::如果对版本有需求可以查看导航栏的DOWNLOADS下载历史版本和MAC，Linux的版本  
[安装详情可以参考这篇文章](https://blog.csdn.net/muzidigbig/article/details/80493880)
****
- 安装Git
Windows系统：进入[Git下载页面](https://git-scm.com/download/win)  
浏览器应该会自动弹出下载框，如果没有弹出点击<font color='#0388A6'>click here to download manually</font>下载行了
下载完后一直NEXT
![](http://pz767zynd.bkt.clouddn.com/2019-10-10-2.png)
__第一个是只能在文件夹右键GitBash才能使用GitBash，  
第二个是允许在第三方软件使用Git Bash.  
我用Webstrom所以选第二个__  
继续next
* [ ] <font color='red'>!new</font>的字样 非必选项不用管直接下一步
安装完后可以鼠标右键
![](http://pz767zynd.bkt.clouddn.com/2019-10-10-3.png)
安装成功!!!
[安装详情可以参考这篇文章](https://blog.csdn.net/huangqqdy/article/details/83032408)
****
- 注册Github账号
 [Github官网](https://github.com/)  国内可能打开有点慢  
 注册完成后右上角个人信息展开有一个 _+_New repository 新建仓库  
  Repository name * 填写[你的Github用户名.github.io](),这里[.github.io]() 前面如果是你的用户名Github会自动识别生成一个静态页面也就是以后我们博客的页面，***但是你也可以选择你喜欢的名字填进去，之后在Settings里面手动创建Github Pages,点击Setting往下翻到GitHub Pages点击choose theme随便选个样式确定就行***
 - 生成SSH
![](http://pz767zynd.bkt.clouddn.com/2019-10-10-3.png)
 点击GitBash
 {% codeblock lang:git %}
git config --global user.name "yourname"
git config --global user.email "youremail"
 {% endcodeblock %}
 yourname:填个你喜欢的名字  
 
 youremail:填你自己的邮箱（可以和github的不一样）  
 
 {% codeblock lang:git %}
 git config -l
 {% endcodeblock %}
确认下信息是否正确
出现`END`按wq退出
{% codeblock lang:git %}
 ssh-keygen -t rsa -C "youremail"
 {% endcodeblock %}
  中间有设密码的环节不过密码可以为空，一直按回车就行  
    
    
 需要将自己电脑生成的SSH的公钥给GitHub
 所以找到.shh的文件夹（生成ssh后会自动生成这个文件夹）用记事本打开`id_rsa.pub`，复制。
 回到GitHub右上角个人信息点击Setting（与之前的GitHub pages的Setting不是同一个）,找到SSH Keys(SSH and GPG keys)点击New SSH key将`id_rsa.pub`内容复制到Key里面，点击Add SSH key
      
 输入
{% codeblock lang:git %}
     ssh -T git@github.com
{% endcodeblock %}
出现success说明成功

- 安装Hexo
{% codeblock lang:git %}
//安装Hexo
 npm install hexo -g
//推荐新手安装这个
 npm install hexo-cli -g
{% endcodeblock %}
 + 初始化Hexo
 {% codeblock lang:git %}
 //存放blog项目的文件夹(路径一定要存在，没有就自己建)
   CD d:/不是中文的名字
  //新建Hexo项目(myblog随便取名字)
   hexo init myblog
 {% endcodeblock %}
    本地搭建成功接下来看看效果怎么样
  + 预览
  {% codeblock lang:git %}
   // 进入文件夹
   cd myblog
   //生成静态文件
   hexo g
   //启动本地服务器
   hexo s
{% endcodeblock %}

# 部署Git
 现在本地已经可以看到自己的博客了，接下来部署到git上就可以然所有人都看见了
   
   打开文件夹 `d:/不是中文的名字/myblog` 找到`_config.yml`打开后翻到最下面
   {% codeblock lang:git %}
   deploy:
   type: git
   repo: https://github.com/YourgithubName/YourgithubName.github.io.git
   branch: master
   {% endcodeblock %}
  
  然后这时需要一份插件来部署到Github
  {% codeblock lang:git %}
  npm install hexo-deployer-git --save
  {% endcodeblock %}
  + OK 最后部署到GitHub上
  {% codeblock lang:git %}
    hexo clean
    hexo g
    hexo d
    {% endcodeblock %}
    `hexo clean`清理之前生成的东西合一不加
    `hexo g` 生成静态文章`hexo generate`缩写
    `hexo d` 部署上传`hexo deploy`缩写
    第一次部署可能要输入Github的账号和密码
    成功部署过一会就可以查看`http://yourname.github.io`
    
    # 域名绑定
    嫌弃`http://yourname.github.io`不好看？
    上[阿里云](https://wanwang.aliyun.com)购买个喜欢的域名，一般新域名都要花时间进行DNS解析，.com2小时以内，cn24小时以内，其他的域名48小时内
    看个人喜好每款价格都不一样。
       点击控制台→域名
       可以看见刚买的域名 点击*解析*
       解析设置 `添加记录`
>记录类型：CNAME  
>
>主机记录：@ 或者 www  
>
>解析路线：默认   
>
>记录值：yourname.github.io  
>
>TTL：1天
>
需要实名认证说是3-5个工作日其实半天可能就通过了

回到GitHub Settings `GitHub Pages` 
将`Custom domain`中填入你刚买的域名 然后`Save`

等待域名的DNS解析完毕
然后你就可以通过你设置的域名访问了
# 写博客

 {% codeblock lang:git%}
  hexo new post wodeboke
{% endcodeblock %}
 `post`属于布局方式除了`post`还有`draft`，`page`
 具体写法[可以参考这里](https://hexo.io/zh-cn/docs/writing)
 再就是用的是Markdown语言
可以使用[这个先写好在发布](https://www.mdeditor.com/)
    