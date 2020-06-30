# 安装基础环境（Windows）

需要用到的软件和下载地址如下。

进入下载地址：

- GO：[https://golang.org/dl/](https://golang.org/dl/)
- NodeJS：[https://nodejs.org/en/download/](https://nodejs.org/en/download/)
- Git：[https://git-scm.com/](https://git-scm.com/)
- hugo：[https://github.com/gohugoio/hugo/releases](https://github.com/gohugoio/hugo/releases)

默认下载最新版。如果go官网上不去，自己搭梯子，或者使用中文网，或者谷歌中国下载。

go和nodejs在Windows下安装很简单，直接双击默认下一步就OK。

在终端下验证，如果没有路径自己手动添加路径。

hugo把zip安装下载到后解压，然后手动把文件夹添加到系统环境变量path中。

最后都在cmd里面验证一遍。

安装腾讯云云开发命令行工具（CLI）

```bash
npm i -g @cloudbase/cli
```

通过查看版本验证是否成功。

# 使用hugo创建站点

```bash
hugo new site blog
```

使用主题：

加载主题

```bash
git submodule add https://github.com/forecho/hugo-theme-echo.git themes/echo
```

修改配置文件（作者源文件）：

```bash
baseURL = "http://localhost:1313"
languageCode = "en-us"
title = "Forecho's Blog"
theme = "echo"
DefaultContentLanguage = "cn"
# 自动检测是否包含中文/日文/韩文，该参数会影响摘要和字数统计功能，建议设置为true
hasCJKLanguage = true
# 设置页面生成形式，将默认的网站路径/修改成.html
uglyURLs = true
googleAnalytics = ""      # UA-XXXXXXXX-X

## 评论系统
changyanAppid = "" # Changyan app id             # 畅言
changyanAppkey = "" # Changyan app key
disqusShortname = "forecho-blog" # disqus account name
livereUID = "" # LiveRe UID                  # 来必力

[markup.highlight]
codeFences = true # 高亮markdown的代码块
guessSyntax = true # 高亮markdown中没有标注语言的代码块
hl_Lines = ""
lineNoStart = 1
lineNos = true
lineNumbersInTable = true
noClasses = true
style = "manni"
tabWidth = 2

# https://gohugo.io/content-management/urls/#aliases
[permalinks]
posts = "/:filename"

[outputFormats.RSS]
mediatype = "application/rss"
baseName = "atom"

[services.rss]
limit = 20

[author]
name = "forecho"
avatar = "https://avatars0.githubusercontent.com/u/1725326?s=460&v=4"
bio = "7年开发经验，寻求技术 Leader 工作机会。Wechat: ipzone"
homepage = "https://forecho.io/"

[params]
favicon = "https://avatars0.githubusercontent.com/u/1725326?s=460&v=4"
keywords = "Hugo, theme, echo"
description = "Hugo theme echo example site."
toc = true
navItems = [
  ["HOME", "/"],
  ["ARCHIVE", "/posts.html"],
  ["ABOUT", "/about.html"],
  ["RSS", "/atom.xml"]
]
# rss 全文输出
rssFullContent = true
uglyURLs = true
busuanzi = true # 是否使用不蒜子统计站点访问量
staticCDNPrefix = "https://cdn.bootcss.com/font-awesome/5.11.2"
extraHead = '<script async src="https://www.googletagmanager.com/gtag/js?id=UA-xxx"></script>'
postAds = ""
profileAds = '<div class="bg-white shadow"><img class=" object-cover w-auto mx-auto mt-6" src="https://blog-1251237404.cos.ap-guangzhou.myqcloud.com/20190424153337.png" alt="微信打赏"></div>'
notFoundAds = ''

# 开启版权声明，协议名字和链接都可以换
[params.cc]
name = "署名-非商业性使用 4.0 国际 (CC BY-NC 4.0)"
link = "https://creativecommons.org/licenses/by-nc/4.0/deed.zh"

# 文章打赏
[params.reward]
enable = true
title = "打赏"
wechat = "https://blog-1251237404.cos.ap-guangzhou.myqcloud.com/20190424153510.png" # 微信二维码
alipay = "https://blog-1251237404.cos.ap-guangzhou.myqcloud.com/20190424153431.png" # 支付宝二维码

############## 评论系统  start ##############
[params.gitment] # Gitment is a comment system based on GitHub issues. see https://github.com/imsun/gitment
owner = "" # Your GitHub ID
repo = "" # The repo to store comments
clientId = "" # Your client ID
clientSecret = "" # Your client secret

[params.utterances] # https://utteranc.es/
owner = "" # Your GitHub ID
repo = "" # The repo to store comments

[params.gitalk] # Gitalk is a comment system based on GitHub issues. see https://github.com/gitalk/gitalk
owner = "" # Your GitHub ID
repo = "" # The repo to store comments
clientId = "" # Your client ID
clientSecret = "" # Your client secret

# Valine.
# You can get your appid and appkey from https://leancloud.cn
# more info please open https://valine.js.org
[params.valine]
enable = false
appId = '你的appId'
appKey = '你的appKey'
notify = false # mail notifier , https://github.com/xCss/Valine/wiki
verify = false # Verification code
avatar = 'mm'
placeholder = '说点什么吧...'
visitor = false

############ 评论系统  end ##############
## 社交链接
[social]
github = "forecho"
jsfiddle = "forecho"
codepen = "forecho"
dribbble = "forecho"
behance = "forecho"
flickr = "forecho"
instagram = "forecho"
youtube = "forecho"
vimeo = "forecho"
vine = "forecho"
medium = "forecho"
wordpress = "forecho"
tumblr = "forecho"
linkedin = "forecho"
slideshare = "forecho"
stackoverflow = "forecho"
reddit = "forecho"
pinterest = "forecho"
weibo = "forecho"
facebook = "forecho"
twitter = "caizhenghai"
douban = "ipzone"
rss = "/atom.xml"
```



启动预览：

```bash
hugo server
```

编译：



```bash
hugo -D
```



# 部署到云环境



我们进入腾讯云的云开发(cloudbase)控制台，选择开通一个云环境:

![img](https://mmbiz.qpic.cn/mmbiz_png/nkojgd9FeuZpZZMDaicc8ezbfl59zm2OgS4a5EWhIm2dIhm8PNsFZQPDkkMEMicRbqiaiba5neHPe7M5jcD6XSpnWQ/640?wx_fmt=png&tp=webp&wxfrom=5&wx_lazy=1&wx_co=1)

这里要注意选择是按量计费的模式(只有按量计费才能开通静态网站托管)。创建完成后，点击进入我们刚刚创建的云环境，进入云环境管理界面：

![img](https://mmbiz.qpic.cn/mmbiz_png/nkojgd9FeuZpZZMDaicc8ezbfl59zm2OgBchqSOevJeR5MIQZTDRJ5WTEU4UwPJCV8OHHqN9zZEA1fKV7sY3X3w/640?wx_fmt=png&tp=webp&wxfrom=5&wx_lazy=1&wx_co=1)

在云环境管理界面，在右侧的网站托管中，我们可以将刚刚项目中生成好的静态页面给上传上去。当然，手动上传显得不太友好，我们也可以借助 cloudbase cli 以命令行的方式执行上传。

首先，安装cloudbase cli:



```
npm install -g @cloudbase/cli
```



执行登录命令：

```
tcb login
```



![img](https://mmbiz.qpic.cn/mmbiz_png/nkojgd9FeuZpZZMDaicc8ezbfl59zm2OgiaAbeZdEicS5vKeLHwQyvEUnHL1Vo1icnFAYvkgXQLkY7uXchLObe0xVw/640?wx_fmt=png&tp=webp&wxfrom=5&wx_lazy=1&wx_co=1)

在弹出的页面确认授权:

![img](https://mmbiz.qpic.cn/mmbiz_png/nkojgd9FeuZpZZMDaicc8ezbfl59zm2OgzJodRLP4eMPiaRs1cFVPViaOMH9iaz4uo7S6icY6cpZZZz6UW4pa61iaKmg/640?wx_fmt=png&tp=webp&wxfrom=5&wx_lazy=1&wx_co=1)

接着，在hugo-site中将public目录中的文件给部署上去：



```
cloudbase hosting:deploy ./public  -e EndId
```



这里的 EnvID 替换为刚创建好的环境ID。



云环境开通静态网页托管功能，就可以通过域名访问了。