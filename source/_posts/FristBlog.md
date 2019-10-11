---
title: 如何用HEXO免费搭建个人博客
tags: 
date: 2019-10-10 20:54:00
cover: /2019/10/10/FristBlog/bg.jpg
---
----
# 前言
 本教程基于windows系统，用的是[Hexo](https://hexo.io/zh-cn/)的框架，服务器也是选的github免费的静态挂载page，所以windows系统方便我们平常的博客的更新。
#准备
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
{% asset_img gitp1.png %}
__这里第一个是只能在文件夹右键GitBash才能使用GitBash，第二个是允许在第三方软件使用Git Bash.我一般都用Webstrom敲前端代码所以我选的是第二个，这样就能在Webstrom的界面里面发布博客__  
继续next
* [ ] <font color='red'>!new</font>的字样 非必选项不用管直接下一步
安装完后可以鼠标右键
{% asset_img gitp2.png %}
安装成功!!!
[安装详情可以参考这篇文章](https://blog.csdn.net/huangqqdy/article/details/83032408)
****
-注册Github账号
 [Github官网](https://github.com/)  国内可能打开有点慢  
 注册完成后右上角个人信息展开有一个 _+_New repository 新建仓库  
  Repository name * 填写[你的Github用户名.github.io](),这里[.github.io]() 前面如果是你的用户名Github会自动识别生成一个静态页面也就是以后我们博客的页面，***但是你也可以选择你喜欢的名字填进去，之后在Settings里面手动创建Github Pages,点击Setting往下翻到GitHub Pages点击choose theme随便选个样式确定就行***
 -生成SSH
 {% asset_img gitp2.png %}
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
