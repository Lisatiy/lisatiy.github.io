---
layout:     post
title:      Pic+jsDeliver+Github  我的最佳图床选择
subtitle:   再也不为图床选择费心了，搭建免费可靠的图床！
date:       2020-04-05
author:     Shufei
header-img: img/post-bg-picbed.jpg
catalog: true
tags:
    - 图床
    - PicGo
    - GitHub
    - jsDeliver
    - PicBed
    - Riot
---

为了搭建自己的博客，对于图床的选择可真是难题。在2020年4月，经过深入调查，免费的图床基本上不再提供优质的服务。七牛云目前提供的测试账号1个月会收回，添加自己搭建的域名需要ICP备案，这对于个人博客来说是费钱非精力的；网易云目前关闭了个人认证；一直广受好评的新浪微博图床加入了防盗链接；腾讯、百度、阿里都会收费。鉴于小众化图床提供的服务可能缺乏稳定性和持续性，只好自己**使用PicGo+jsDeliver+GitHub搭建图床**。

## 创建自己的GitHub图床

#### 1. 注册/登录GitHub账号

注册GitHub账号的教程比较多，这部分就不再详细演示。

#### 2. 创建作为图床的Repository

顺序执行 **1->2->3->4->5->6->7** 步骤

![](https://cdn.jsdelivr.net/gh/lisatiy/picbed-lisatiy@master/img/2020/20200405100901.jpg)

> 第5步为该repository初始化一个Readme.md文件和第6步选择license非必选。

#### 3.生成一个Token用于操作GitHub repository

回到主页，点击 **setting** 按钮，进入页面后，点击 **Developer settings** 按钮。

![](https://cdn.jsdelivr.net/gh/lisatiy/picbed-lisatiy@master/img/2020/20200405101058.jpg)

点击左上方的 **Personal access tokens** 按钮，填写相关的**信息(Note)**并勾选 **相应的权限** ，最后点击 **Generate token** 按钮。

![](https://cdn.jsdelivr.net/gh/lisatiy/picbed-lisatiy@master/img/2020/20200405101334.jpg)

> 创建成功后，会生成一串token，这串token之后不会再显示，所以第一次看到的时候记得保存下来，忘记了只能重新生成，每次都不一样的。

## 配置PicGo和jsDeliver

#### 1. 下载运行PicGo

点击此处下载 [应用](https://github.com/Molunerfinn/PicGo/releases)

windows用户下载最新的exe文件，Linux用户下载AppImage文件，macOS用户下载最新版本的dmg文件。

> 只在window上面做过测试，其他平台或许有更好的选择

#### 2. 配置图床

按照这个格式配置就好.

![](https://cdn.jsdelivr.net/gh/lisatiy/picbed-lisatiy@master/img/2020/20200405101610.jpg)

- 仓库名 "账户名/仓库名"
- 分支名 默认是"master"
- Token就是刚刚复制的那一串字符
- 存储路径按照我这样填，会在该repository下创建一个"xxx/xxx/"文件夹，注意可以自己定义你的文件夹名字
- 自定义域名的格式为: cdn.jsdelivr.net/gh/用户名/仓库名@分支名，**分支名后面不要再加路径/xxx/xxx** 。自定义域名作用是在上传图片成功后，PicGo会将"自定义域名+上传的图像名"生成访问链接，放到剪切板上，生成的链接格式为:  https://cdn.jsdelivr.net/gh/用户名/仓库名@分支名/xxx/xxx/xxxxxx.png

> 1. cdn.jsdelivr.net/gh/用户名/仓库名@分支名 提供了一个加速图片的方法: CDN加速，具体原理谷歌。这种方式是引用仓库中某个分支的资源，其他引用资源的方法 [戳这里](https://zhuanlan.zhihu.com/p/76951130)。
> 2. 我这里在图床的repository下创建了img/xxx文件夹。为了索引和整理方便，我会每年新建一个文件夹，以年份数字为名称。

#### 3. 快捷键配置

支持快捷键control+shift+p（windows\linux）或者command+shift+p（macOS）用以支持快捷上传剪贴板里的图片，具体配置比较简单，不再详述。

#### 4. 图片压缩处理工具

推荐使用Riot，小巧强悍，具体请 [戳这里](https://zhuanlan.zhihu.com/p/32186907) 。

截图工具推荐使用Snipaste，同样小巧强悍，链接就先不放了。

#### 5. 图片上传注意事项

- 从剪切板中通过control+shift+p上传的文件会以"$yyyyMMddHHmmss$.png"时间格式命名；若从本地图库中拖拽上传，建议修改名称。
- **上传的图片能压缩到200KB最好**，这样会提高速度
- 碰到无法上传的问题时，可以在GitHub的图床repo中提交commit试试

## 总结

将上面步骤设置好后，就可以开心的写Markdown文档了哈哈。

### 感谢

感谢 [洪卫的博客](https://sunhwee.com/posts/1788dd4a.html) 、[虾丸派](https://www.playpi.org/2019042701.ht ml) 和 [TRHX](https://zhuanlan.zhihu.com/p/76951130) 提供了思路，此篇是对他们的总结和拓展。