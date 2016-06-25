---

layout:     post
title:      Mac常用终端命令收录
category:   cmd
tag:        shell

---

### RVM 常用命令

[RVM](https://rvm.io/)的全称是`Ruby Version Manager`，是常用的命令行工具，允许你在多个Ruby环境下更简单的安装、管理和工作。

有时候，因系统升级等原因RVM无法正常使用。此时，首先要删除RVM：

~~~bash
rvm implode
gem uninstall rvm
rm -rf ~/.rvm .zshrc .zprofile
# 删除 ~/.bash ~/.bash_profile 文件中 activate RVM 指令
~~~

然后，重新安装RVM：

~~~bash
curl -L https://get.rvm.io | bash -s stable
source ~/.rvm/scripts/rvm
rvm requirements
~~~

若要多个ruby环境时，需要安装不同的ruby版本：

~~~bash
rvm install 1.9.3
rvm install 2.2.2
~~~

例如，查看当前安装了哪些ruby的版本，默认版本是什么，当前版本是什么：

~~~bash
rvm list
~~~

切换ruby版本：

~~~bash
rvm use 2.2.2
ruby -v
rvm use system # 切换到当前系统的ruby
~~~

设置当前选中ruby为默认ruby：

~~~bash
rvm default
ruby -v
~~~

### gem常用命令

[gem](https://rubygems.org/)的全称是`RubyGems`，是Ruby编程的包管理器，提供了一个标准的格式发布Ruby的程序和库，是一个非常容易管理已安装的`Gem packages`的工具，是一个发布gems的服务。

gem命令被用来编译，上传，下载和安装`Gem Packages`。

安装我的`Gem package`：

~~~
gem install mygem
~~~

通常安装的`Gem Packages`，例如：

~~~
gem install cocoapods
gem install jekyll
~~~

更新我的`Gem Package`：

~~~
gem update mygem
~~~

卸载我的`Gem package`：

~~~
gem uninstall mygem
~~~

列出已经安装的`Gem packages`：

~~~
gem list --local
~~~

因为GFW的原因，导致[rubygems.org](http://rubygems.org/)存放在`Amazon S3`上面的资源文件间歇性连接失败。于是淘宝搭建了一个[同步镜像](http://ruby.taobao.org/)，根据需要可以吧gem的source更换掉：

~~~
gem sources --remove https://rubygems.org/
gem sources -a https://ruby.taobao.org/
gem sources -l
~~~

gem命令经常被用来构建和维护`.gemspec`和`.gem`文件，构建`Gem Package`。
从一个`.gemspec`文件构建`.gem`：

~~~
gem build mygem.gemspec
~~~

更多的信息，参考[RubyGems手册](http://docs.rubygems.org/read/chapter/1)。
