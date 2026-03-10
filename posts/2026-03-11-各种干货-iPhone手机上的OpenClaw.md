---
title: 各种干货-iPhone 手机上的 OpenClaw
date: 2026-03-11
category: 技术
tags: [OpenClaw]
top: 18
---

# 各种干货-iPhone 手机上的 OpenClaw

> 来源：Telegraph
> 原文链接：https://telegra.ph/%E5%90%84%E7%A7%8D%E5%B9%B2%E8%B4%A7-iPhone%E6%89%8B%E6%9C%BA%E4%B8%8A%E7%9A%84OpenClaw-03-10

自从ChatGPT问世以来各种基于AI的服务如雨后春笋般生长出来。

OpenClaw现在很火，很多小伙伴们都想跃跃欲试，养一只属于自己的小龙虾。但是配置实在是太难太复杂，想体验完整的又得去买各家服务器厂商提供的服务，不仅麻烦还得花钱。

![Image 1](/zoooo0-blog/assets/2026-03-11-各种干货-iPhone手机上的OpenClaw/cover.png)

上面是OpenClaw的网页概览页面，别说没接触过的，我用过都不能完全的知道哪些是做什么用的，想要完全弄好符合自己需求的配置，需要更多的时间去研究测试，太难了。

那么问题来了，有没有体验的，操作不复杂并且手机上就能搞定的？有！只不过权限没那大，仅仅是在手机上操作。但是对于日常用户使用来说够了，因为小白用户只是想体验一下，并没有落地的业务需求，而且token那么贵，也不足以持续花钱搞这个。

这个App叫OpenMinis。下面是作者的GitHub，还没什么内容，但是看得出来，这个App里面内置了iSH（iSH是一个模拟器，用来在ARM架构的iOS设备上模拟x86架构，让iOS设备在本地运行Linux Shell环境）和web浏览器。也是这个app最大的优势，可以让ai去执行ssh命令和浏览器访问。

https://github.com/OpenMinis

![Image 2](/zoooo0-blog/assets/2026-03-11-各种干货-iPhone手机上的OpenClaw/image-02.png)

界面很简单，就是一个浏览器聊天的页面。配置好后你只需要跟它聊天即可。由于是在iPhone/iPad上运行的，可以执行系统级别的任务（只要苹果给了接口）。

系统原生能力主要通过一组 `apple-*` 命令行工具（调用 iOS 框架）实现，常见的有：

*   **apple-alarm**：闹钟/计时器

*   **apple-calendar**：日历事件

*   **apple-clipboard**：剪贴板读写

*   **apple-contacts**：联系人

*   **apple-healthkit**：健康数据（受权限限制）

*   **apple-location**：定位

*   **apple-maps**：地图搜索/路线/ETA

*   **apple-media**：媒体库

*   **apple-nlp**：文本分析

*   **apple-open**：打开 URL/文件

*   **apple-photos**：相册

*   **apple-player**：播放音视频

*   **apple-speak**：语音朗读

*   **apple-vision**：图像识别

*   **apple-weather**：天气

软件的配置选项虽然很简单，但是功能却不少。如下：

![Image 3](/zoooo0-blog/assets/2026-03-11-各种干货-iPhone手机上的OpenClaw/image-03.png)

我简单介绍一下。

第一项：Manage Providers，主要是用来配置token的。

第二项：Model Groups，主要是设置默认模型的。这块不设置也可以，到时候在聊天页面选择也是可以的。

第三项：Token Usage，用来显示你使用的token数量，用作统计使用。

第四项：Skill，这个玩过OpenClaw的应该很熟悉，就是教ai的一些技能。

第五项：Memory，这个是让ai记住你说的话存放地点。它可以自己编辑保存到这个位置。

后面的基本上配置就复杂了，使用默认即可。

首先，我们先进入Manage Providers进行ai的配置，点击右上角的+进入添加的页面。

![Image 4](/zoooo0-blog/assets/2026-03-11-各种干货-iPhone手机上的OpenClaw/image-04.png)

![Image 5](/zoooo0-blog/assets/2026-03-11-各种干货-iPhone手机上的OpenClaw/image-05.png)

它是支持API和OAuth登录的，简单理解就是，可以拿各家ai的key使用，也可以登录账号后使用。

拿OpenAI举例，你可以选择API Key。

![Image 6](/zoooo0-blog/assets/2026-03-11-各种干货-iPhone手机上的OpenClaw/image-06.png)

![Image 7](/zoooo0-blog/assets/2026-03-11-各种干货-iPhone手机上的OpenClaw/image-07.png)

API Key：就是你购买的服务商提供的，这个兼容OpenAI的都可以用。

Custom API Base：也是服务商提供的。

填完后下面会出现一堆Models，这个就是你用的时候需要使用的模型，如果没有可以点下面的Add Custom Model手动添加。

![Image 8](/zoooo0-blog/assets/2026-03-11-各种干货-iPhone手机上的OpenClaw/image-08.png)

另外一种是OAuth登录，最简单，但是需要特殊网络才能访问，点击Sign in with OpenAI即跳转到登录页面，登录成功即可拿到OAuth。

![Image 9](/zoooo0-blog/assets/2026-03-11-各种干货-iPhone手机上的OpenClaw/image-09.png)

以上就是配置API的简单介绍，这里配置好之后基本上就完事了，可以使用这个OpenMinis当私人管家了。

我举几个简单例子。

![Image 10](/zoooo0-blog/assets/2026-03-11-各种干货-iPhone手机上的OpenClaw/image-10.png)

上面我让它根据位置查询并且给我当前的天气情况。很快就给到结果了，并且有显示它在用什么工具在处理。

当然你会说，还用这么麻烦干啥，豆包，DeepSeek不都可以实现吗？确实，这些都行。只不过这个是通过自己的手机端和购买的token实现的。

下面我再举个例子，直接看图。

![Image 11](/zoooo0-blog/assets/2026-03-11-各种干货-iPhone手机上的OpenClaw/image-11.png)

![Image 12](/zoooo0-blog/assets/2026-03-11-各种干货-iPhone手机上的OpenClaw/image-12.png)

![Image 13](/zoooo0-blog/assets/2026-03-11-各种干货-iPhone手机上的OpenClaw/image-13.png)

![Image 14](/zoooo0-blog/assets/2026-03-11-各种干货-iPhone手机上的OpenClaw/image-14.png)

![Image 15](/zoooo0-blog/assets/2026-03-11-各种干货-iPhone手机上的OpenClaw/image-15.png)

从这上面的截图中看，经过几次提示，它便可以自己找到小红书登录页面，找到扫码登录的位置，让我登录，后面还有自动发布内容，我没有放出来，这已经是一个完整的操作过程了。并且我让它把这个流程记录下来，下次登录直接给我结果。

其实这就是简化版的豆包手机，它虽然控制不了手机中的app，但是它可以利用浏览器和ssh进行操作。

相对于OpenClaw，OpenMinis的好处是，在手机端，获取的网络和环境都是手机上的，不容易风控，我用OpenClaw登录都不能成功，服务器IP不行。

![Image 16](/zoooo0-blog/assets/2026-03-11-各种干货-iPhone手机上的OpenClaw/image-16.png)

OpenMinis的缺点就是不能随时在线，关了app就无法执行任务了，只能打开再次使用。但是提醒什么的都可以通过app执行，我也测试过定时和提醒app，都是能正常调用的。

OpenMinis还在内测阶段，后续会发展成什么样，我也不确定，但是对于手机上，尤其iPhone上进行自动化操作的用户来说，这真是一个好app。

上午在写这篇文章的时候和朋友聊天，他说，“前两天看到一个采访，一个人说，当你token足够多，才能突破一个ai能力的界限值，才能对ai的认识发生改变。”

我非常认同这句话，现在的局限就是token。

当我们token自由的时候，你能实现的界限，就是你的认知界限。

最后我想说，希望我们都能抓住这个时代的机遇，好好享受ai带给我们的便利。
