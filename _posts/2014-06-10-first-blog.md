---

layout:	    post
title:     	开博第一篇
category: 	learning
tag:        guide

---



> no zuo no die why you try,  
> you try you die don't ask why.  
> just do it!



## 选择和决定

早些时候，我为了能在短时间内搭建一个私人博客，选择了WorldPress作为我的博客架构。因为只希望能让自己有个私人域名的博客用自己喜欢的方式写写随笔，所以预算并不多。

我当初考虑的域名商：

- [GoDaddy](http://www.godaddy.com/)
- [万网](http://www.net.cn/)

由于只是在中国使用，考虑到解析速度，我选择了万网，然后花了147元RMB买了3年的mingminy.com的英文域名。

当初考虑的空间商：

- [bluehost](http://cn.bluehost.com/)
- [阿里云](http://www.net.cn/hosting/?spm=0.0.0.0.CEhpIz)
- [openshift](https://www.openshift.com/)

最后我选择了免费又好用的openshift。

如上是我原先建博客时的选择，当我把[博客](https://blog-mmy.rhcloud.com/)搭建完后，首先发现打开的速度实在是太慢了；其次，wordpress虽然非常好用，但总感觉它太臃肿了，我只想用最原始的方式，用markdown写博客。

使用了一阵子后，我最后决定研究下jekyll来做一个纯静态的blog。
<input type='hidden'>


## jekyll建站搭建步骤

jekyll的文档官方相当详细，同时提供了中英文版：

- [英文版](http://jekyllrb.com/)
- [中文版](http://jekyllcn.com/)

我是果断选择了中文版，然后把整篇文章读了一遍。读完之后我想了想自己该怎么做呢？我开始思考：

- 我应该像WorldPress一样找个主题在上面改一改，不可能自己从头开始写，因为没这份精力。
- 文档上说jekyll有自带的测试服务器，我可以把博客的基本架构先在本地搭出来。
- 域名使用m.mingminy.com
- 空间的话一定是将免费进行到底，速度只要在可接受范围就行。

按照这个思路我首先开始找我喜欢的主题：

- [This site now runs on jekyllrb](http://blog.crash-override.net/blog/2013/03/28/this-site-now-runs-on-jekyllrb.html)
- [Rasmus Andersson](http://rsms.me/)
- [...](https://github.com/jekyll/jekyll/wiki/Sites)

在这茫茫站点中找寻自己喜欢的它是多么的不容易啊！这一点WorldPress比jekyll做的好多了。最后我终于找到了自己喜爱的主题——poole.lanyon，然后开始自我发挥啦！


### _config.yml

- 如何打开`Markdown Redcarpet`的`tables`语法扩展：

  ```
  redcarpet:
    extensions: [
    tables
    ]
  ```

  参考了[配置·Markdown选项](http://jekyllcn.com/docs/configuration/#markdown-)

- 解决左侧栏`Home`页不高亮：

  ```
  baseurl:
  ```  

- 配置文档摘要，并用特殊的分隔符不让它被Redcarpet转换后失效：

  ```
  excerpt_separator:  <input type='hidden'>
  ```
  - 参考了[配置·默认配置](http://jekyllcn.com/docs/configuration/#section-4)
  - 参考了[jekyll issue](https://github.com/jekyll/jekyll/issues/1839)

  如何找到解决方法的具体细节记不清了。


### _drafts

如何使用草稿，只需要在`_drafts`目录下创建一个Markdown文件就可以啦！终端命令：

```
mac$ jekyll serve --drafts
```


### _includes

`_includes`的详细用法参考[官方文档](http://jekyllcn.com/docs/structure/)。

我主要把所有的链接从绝对路径改为了相对路径，即在路径上加了`site.baseurl`参数。

关于侧边栏目前是动态载入的，但发现栏位的顺序会乱掉，估计以后还需要优化下。


### _layouts

我主要修改了`post.html`，具体修改如下：

- 添加评论[多说](http://mingminy.duoshuo.com/admin/)
- 添加分享[加网](http://www.jiathis.com/)
- 添加`<<返回`按钮

目前主流的社会化评论分享服务有：

- [友言](http://www.uyan.cc/)
- [评论啦](http://www.pinglun.la/)
- [畅言](http://changyan.sohu.com/)
- [Disqus](http://www.disqus.com/)
- [JiaThis](http://www.jiathis.com/)
- [addThis](http://www.addthis.com/)

这些信息的收集参考了这篇文章——[《第三方评论系统》](http://www.cnblogs.com/seanxyh/archive/2013/04/10/3012399.html)


### _posts

`_posts`存放着我们写的文章，所以新建一篇文章很简单，就在该目录下新建一个文件即可；若你喜欢markdown格式的话，只需要创建后缀名为md的文件。

新建的文章都需要添加一个yml文章头，最基本的头信息：

```
---

layout:     post
title:      开博第一篇·绝对干货
category:   learning
tag:        guide

---
```


### public

这个目录我主要设置下logo。


### index.html

在目前的框架下，index被集成到了default布局中；我对index页面做了如下修改：

- 把显示全文替换成显示摘要
- 添加`Read More>>`按钮

对于`显示摘要`我遇到了不少麻烦；页面中只需要添加`post.excerpt`变量，但在对分隔符的定义却比较讲究；这主要因我使用了`Markdown Redcarpet`语法。

解决方法就是找一个很特殊的不会被转换的分隔符；考虑到分隔符不能影响文章的显示，最后我决定用html标记`<input type='hidden'>`作为分隔符。


### 设计归档、分类、标签

我遇到的主要问题是：

- 显示的样式
- 如何使用`site.categories`和`site.tags`参数枚举

显示的样式我后来做了如下设计：

- archives用表格显示，一共2列，第1列是时间，第2列是文章
- categories用分类名当小标题，文档依次列举
- tags的设计跟categories一样

现在的问题是[官方文档](http://jekyllcn.com/docs/variables/#site)只对`site.categories.CATEGORY`和`site.tags.TAG`做了简要说明，怎么使用`site.categories`和`site.tags`成了难题。

我后来像无头苍蝇一样找了很多混乱的信息：

- http://vvv.tobiassjosten.net/jekyll/jekyll-tag-cloud/
- https://gist.github.com/yeban/2290195
- http://enrmarc.github.io/blog/Jekyll-tagcloud/

最后七拼八凑的把语法试出来了：

```
for category in site.categories
category | first
for post in category[1]
// 遍历
endfor
endfor
```

试出来后发现 so easy；其实很多东西都是看起来很高大上，其实尼玛的很easy。


### GitHub Pages

这个文档就这么多：

- http://jekyllcn.com/docs/github-pages/
- https://pages.github.com/

根据自己的需求创建相应的repository。


### 设置域名

最后来分享下如何给`GitHub Pages`设置一个属于自己的域名；说到这，大家一定很激动吧，行走`江湖`多年，终于能有个`名分`了。

不多说了，我直接上菜，例行公事，先贴[官方文档](https://help.github.com/articles/setting-up-a-custom-domain-with-github-pages#step-1-add-a-cname-file-to-your-repository)。

接下来，我来说明下设置步骤：

- 在根目录下创建`CNAME`文件，注意木有后缀名
  - 用文本编辑器打开，如果你很`Hacker`用vim打开也行，然后写上你的名分，比如`m.mingminy.com`
  - `然后git push`一下呗，耐心等待10分钟，你可以泡杯咖啡哈
- 到你的域名服务商里设置下域名解析

全部搞定，是不是很easy。


### 问题和解决方案

- Q: 谷歌`fonts.googleapis.com`被屏蔽，导致网站加载速度巨慢。
	- A: 把字体的载入方式换成本地载入的形式，具体步骤如下：
		1. 在`_include/head.html`中找到原始链接`http://fonts.googleapis.com/css?family=PT+Serif:400,400italic,700|PT+Sans:400">`
		2. 在浏览器中打开此链接，打不开的话多刷几次，实在不行的话只能翻墙了。
		3. 把全部内容粘贴，在`public/css`目录下新建一个名叫`fonts.googleapis.com.css`的文件，把内容全部粘贴进去
		4. 把head.html中的引用路径修改为`{{ site.baseurl}}/public/css/fonts.googleapis.css`

