## <center>Git关联Github远程库生成SSH密钥绑定</center>
参考原文链接：https://blog.csdn.net/weixin_30340775/article/details/96546458

问题描述：在用git从github远程库克隆的时候出现此问题。
```git：Please make sure you have the correct access rights and the repository exists```

意思是要进行密钥生成，和GitHub远程库绑定联接。

#### 解决办法：

1. 在shell中输入Git命令：
```
git config --global user.name "your name"  
git config --global user.email "your@email.com" 
ssh-keygen -t rsa -C "your@email.com" 
#均是输入自己的邮箱和用户名
```

操作完成之后会在对应的文件夹（用户文件）下产生id_rsa.pub和id_rsa两个文件。

2. 关联ssh密钥

打开GitHub账号，在[https://github.com/settings/keys ](https://github.com/settings/keys) 页面新建一个ssh key, 将id_rsa.pub里的内容复制过去即可。

4. 验证是否成功
```
ssh -T git@github.com
```
如果成功，会出现successfully authenticated部分，否则根据返回的结果进行处理。
完成之后，GitHub会给你的邮箱（git账号）发送一个邮件进行提示。
