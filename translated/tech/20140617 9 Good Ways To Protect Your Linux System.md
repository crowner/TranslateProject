保护你的Linux系统的9种好方法
================================================================================
在现在这个世道中，保障基于Linux的系统的安全是十分重要的。但是，你得知道怎么干。一个简单反恶意程序软件这是远远不够的，你需要采取其它措施来协同工作。那么试试下面这些手段吧。

![](http://www.efytimes.com/admin/useradmin/photo/2Rak10143PM6172014.jpeg)

### 1. 使用SELinux ###

[SELinux][1]是用来对Linux进行安全加固的，有了它，用户和管理们就可以对访问控制进行更多控制。SELinux为访问控制添加了更细的颗粒度控制。与仅可以指定谁可以读、写或执行一个文件的权限不同的是，SELinux可以让你指定谁可以解链接，仅追加，移动一个文件之类。

### 2. 订阅漏洞警报服务 ###

你的操作系统可能不一定受伤害的那一台。事实上，漏洞多见于安装的应用程序之中。为了避免这个问题的发生，你必须保持你的应用程序更新到最新版本。此外，订阅漏洞警报服务，如[SecurityFocus][2]。

### 3. 禁用不用的服务和应用 ###

通常来讲，用户大多数时候都用不到他们系统上的服务和应用的一半。然而，这些服务和应用还是会运行，这会招来攻击者。因而，最好是把这些不用的服务停掉。

### 4. 检查系统日志 ###

你的系统日志告诉你在系统上发生了什么活动，包括攻击者是否成功进入或试着访问系统。时刻保持警惕，是你第一条防线，而经常性地监控系统日志就是为了守好这道防线。

### 5. 考虑使用端口敲门 ###

设置端口敲门是建立服务器安全连接的好方法。而基本上会发生的问题是，别有用心的人会发送一个特别的包给服务器，这个包会开启来自服务器的回应/连接。端口敲门对于那些有开放端口的系统上是一个很好的防护措施。

### 6. 使用Iptables ###

Iptables是什么？这是一个应用程序框架，它允许用户自己为系统写一个强大的防火墙。因此，要做得好，就要学习怎样一个好的防火墙以及怎样使用Iptables框架。

### 7. 默认拒绝所有 ###

防火墙允许两个宗旨：一个是允许每一点通信，另一个是拒绝所有访问，提示你是否许可。第二个选项是两者中更好的一个。你应该只允许那些重要的通信进入。

### 8. 使用入侵检测系统 ###

入侵检测系统，或者叫IDS，允许你更好地管理系统上的通信和受到的攻击。[Snort][3]

加密的数据更难窃取，有时候根本不可能被窃取，这就是你应该对整个驱动器加密的原因。采用这种方式后，如果有某个人进入到你的系统，那么他看到这些加密的数据后，就有得头痛了。根据一些报告，大多数数据丢失源于机器被盗。

--------------------------------------------------------------------------------

via: http://www.efytimes.com/e1/fullnews.asp?edid=141368

译者：[GOLinux](https://github.com/GOLinux) 校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创翻译，[Linux中国](http://linux.cn/) 荣誉推出

[1]:http://selinuxproject.org/page/Main_Page
[2]:http://www.securityfocus.com/rss/vulnerabilities.xml
[3]:http://www.snort.org/