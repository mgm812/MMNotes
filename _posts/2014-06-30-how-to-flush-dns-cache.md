---

layout:	post
title:     	如何清除DNS缓存
category: 	work
tag: 		dns

---

有时候需要刷新下DNS缓存，我不知道Mac系统用什么命令清理，然后在网上搜索了下找到一篇总结比较好的[文章](http://codelife.me/blog/2012/11/20/how-to-flush-your-dns-cache/)；为了加深印象顺便做个备份，我又把各个平台命令全部记了一遍。



## Mac OS X

- Mac OS X 10.7 10.8 10.9

  ```
$ sudo killall -HUP mDNSResponder
  ```

- Mac OS X 10.5 10.6

  ```
$ dscacheutil -flushcache
  ```

- Mac OS X 10.4

  ```
$ lookupd -flushcache
  ```

<input type='hidden'>

## Windows

- Vista/Win7 以上系统
  - 查看DNS缓存

    ```
    > ipconfig /displaydns
    ```

  - 清除DNS缓存

    ```
    > ipconfig /flushdns
    ```

- Winxp和之前的老系统

  ```
  > net stop dnscache
  > net start dnscache
  ```

## Linux

```
$ sudo /etc/init.d/nscd restart
```


