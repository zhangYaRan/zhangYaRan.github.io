# zhangYaRan blog

### 关于收到"Page Build Warning"的 email

由于 jekyll 升级到 3.0.x,对原来的 pygments 代码高亮不再支持，现只支持一种-rouge，所以你需要在 `_config.yml`文件中修改`highlighter: rouge`.另外还需要在`_config.yml`文件中加上`gems: [jekyll-paginate]`.

同时,你需要更新你的本地 jekyll 环境.

使用`npm run preview`的同学需要这样：

1. `gem update jekyll` # 更新 jekyll
2. `gem update github-pages` #更新依赖的包

使用`bundle exec jekyll server`的同学在更新 jekyll 后，需要输入`bundle update`来更新依赖的包.

参考文档：[using jekyll with pages](https://help.github.com/articles/using-jekyll-with-pages/) & [Upgrading from 2.x to 3.x](http://jekyllrb.com/docs/upgrading/2-to-3/)

#### Environment

如果你安装了 jekyll，那你只需要在命令行输入`jekyll serve`就能在本地浏览器预览主题。你还可以输入`jekyll serve --watch`，这样可以边修改边自动运行修改后的文件。

经 [@BrucZhaoR](https://github.com/BruceZhaoR)的测试，好像两个命令都是可以的自动运行修改后的文件的，刷新后可以实时预览。官方文件是建议安装 bundler，这样你在本地的效果就跟在 github 上面是一样的。详情请见这里：https://help.github.com/articles/using-jekyll-with-pages/#installing-jekyll

#### Get Started

你可以通用修改 `_config.yml`文件来轻松的开始搭建自己的博客:

```
# Site settings
title: zhangYaRan Blog             # 你的博客网站标题
SEOTitle: zhangYaRan Blog			# 在后面会详细谈到
description: "Cool Blog"    # 随便说点，描述一下

# SNS settings
github_username: zhangYaRan     # 你的github账号
weibo_username: zhangYaRan      # 你的微博账号，底部链接会自动更新的。

# Build settings
# paginate: 10              # 一页你准备放几篇文章
```

Jekyll 官方网站还有很多的参数可以调，比如设置文章的链接形式...网址在这里：[Jekyll - Official Site](http://jekyllrb.com/) 中文版的在这里：[Jekyll 中文](http://jekyllcn.com/).

#### write-posts

要发表的文章一般以 markdown 的格式放在这里`_posts/`，你只要看看这篇模板里的文章你就立刻明白该如何设置。

yaml 头文件长这样:

```
---
layout:     post
title:      "Hello 2015"
subtitle:   "Hello World, Hello Blog"
date:       2015-01-29 12:00:00
author:     "zhangYaRan"
header-img: "img/post-bg-2015.jpg"
tags:
    - Life
---

```

#### SideBar

设置是在 `_config.yml`文件里面的`Sidebar settings`那块。

```
# Sidebar settings
sidebar: true  #添加侧边栏
sidebar-about-description: "简单的描述一下你自己"
sidebar-avatar: /img/avatar-zyr.jpg     #你的大头贴，请使用绝对地址.
```

侧边栏是响应式布局的，当屏幕尺寸小于 992px 的时候，侧边栏就会移动到底部。具体请见 bootstrap 栅格系统 <http://v3.bootcss.com/css/>

#### Mini About Me

Mini-About-Me 这个模块将在你的头像下面，展示你所有的社交账号。这个也是响应式布局，当屏幕变小时候，会将其移动到页面底部，只不过会稍微有点小变化，具体请看代码。

#### Featured Tags

看到这个网站 [Medium](http://medium.com) 的推荐标签非常的炫酷，所以我将他加了进来。
这个模块现在是独立的，可以呈现在所有页面，包括主页和发表的每一篇文章标题的头上。

```
# Featured Tags
featured-tags: true
featured-condition-size: 1     # A tag will be featured if the size of it is more than this condition value
```

唯一需要注意的是`featured-condition-size`: 如果一个标签的 SIZE，也就是使用该标签的文章数大于上面设定的条件值，这个标签就会在首页上被推荐。

内部有一个条件模板 `{% if tag[1].size > {{site.featured-condition-size}} %}` 是用来做筛选过滤的.

#### Friends

好友链接部分。这会在全部页面显示。

设置是在 `_config.yml`文件里面的`Friends`那块，自己加吧。

```
# Friends
friends: [
    {
        title: "Foo Blog",
        href: "http://foo.github.io/"
    },
    {
        title: "Bar Blog",
        href: "http://bar.github.io"
    }
]
```

#### Keynote Layout

HTML5 幻灯片的排版：

![](http://huangxuan.me/img/blog-keynote.jpg)

这部分是用于占用 html 格式的幻灯片的，一般用到的是 Reveal.js, Impress.js, Slides, Prezi 等等.我认为一个现代化的博客怎么能少了放 html 幻灯的功能呢~

其主要原理是添加一个 `iframe`，在里面加入外部链接。你可以直接写到头文件里面去，详情请见下面的 yaml 头文件的写法。

```
---
layout:     keynote
iframe:     "http://huangxuan.me/js-module-7day/"
---
```

iframe 在不同的设备中，将会自动的调整大小。保留内边距是为了让手机用户可以向下滑动，以及添加更多的内容。

#### Comment

博客不仅支持多说[Duoshuo](http://duoshuo.com)评论系统，也支持[Disqus](http://disqus.com)评论系统。

`Disqus`优点是：国际比较流行，界面也很大气、简介，如果有人评论，还能实时通知，直接回复通知的邮件就行了；缺点是：评论必须要去注册一个 disqus 账号，分享一般只有 Facebook 和 Twitter，另外在墙内加载速度略慢了一点。想要知道长啥样，可以看以前的版本点[这里](http://brucezhaor.github.io/about.html) 最下面就可以看到。

`多说` 优点是：支持国内各主流社交软件(微博，微信，豆瓣，QQ 空间 ...)一键分享按钮功能，另外登陆比较方便，管理界面也是纯中文的，相对于 disqus 全英文的要容易操作一些；缺点是：就是界面丑了一点。
当然你是可以自定义界面的 css 的，详情请看多说开发者文档 http://dev.duoshuo.com/docs/5003ecd94cab3e7250000008 。

**首先**，你需要去注册一个账号，不管是 disqus 还是多说的。**不要直接使用我的啊！**

**其次**，你只需要在下面的 yaml 头文件中设置一下就可以了。

```
duoshuo_username: _你的用户名_
# 或者
disqus_username: _你的用户名_
```

**最后**多说是支持分享的，如果你不想分享，请这样设置：`duoshuo_share: false`。你可以同时使用两个评论系统，不过个人感觉怪怪的。

#### Analytics

网站分析，现在支持百度统计和 Google Analytics。需要去官方网站注册一下，然后将返回的 code 贴在下面：

```
# Baidu Analytics
ba_track_id: 4cc1f2d8f3067386cc5cdb626a202900

# Google Analytics
ga_track_id: 'UA-49627206-1'            # 你用Google账号去注册一个就会给你一个这样的id
ga_domain: huangxuan.me			# 默认的是 auto, 这里我是自定义了的域名，你如果没有自己的域名，需要改成auto。
```

#### Customization

如果你喜欢折腾，你可以去自定义我的这个模板的 code，[Grunt](gruntjs.com)已经为你准备好了。（感谢 Clean Blog）

JavaScript 的压缩混淆、Less 的编译、Apache 2.0 许可通告的添加与 watch 代码改动，这些任务都揽括其中。简单的在命令行中输入 `grunt` 就可以执行默认任务来帮你构建文件了。如果你想搞一搞 JavaScript 或 Less 的话，`grunt watch` 会帮助到你的。

**如果你可以理解 `_include/` 和 `_layouts/`文件夹下的代码（这里是整个界面布局的地方），你就可以使用 Jekyll 使用的模版引擎 [Liquid](https://github.com/Shopify/liquid/wiki)的语法直接修改/添加代码，来进行更有创意的自定义界面啦！**
