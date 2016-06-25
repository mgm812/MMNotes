---

layout: 	post
title:     	在Xcode中开发iOS遇到的常见问题
category: 	ios
tag: 		problem

---

> 这篇文章会收集开发iOS时经常碰到的问题（frequently asked questions）并提供解决方法。

### lipo合并.a出错，报`No architectures to compile for (ONLY_ACTIVE_ARCH=YES, active arch=i386, VALID_ARCHS=armv7 armv7s)`

原因是Xcode编译时做了**Valid Architectures**，去掉了不用的架构，导致合并时找不到某些架构导致报错。

解决方法是修改**Build Settings**的**Valid Architectures**为`armv6 $(ARCHS_STANDARD_32_BIT)`。

### 如何手动导出ipa？

用**xcodebuild**命令可以手动导出ipa；具体步骤为：

1. 用Xcode打一个archive包。
2. 执行**xcodebuild**命令，可以参考如下命令：

	~~~
	xcodebuild -exportArchive -exportFormat ipa -archivePath ./cmblife.xcarchive -exportPath ./cmblife.ipa -exportProvisioningProfile "NewHouseDistributeProfile"`
	~~~

### 编译bundle时多倍图被自动合并成了tiff，如何关闭自动合并？

在bundle的target中，选中**Build Settings**，在**User-Defined**中找到`COMBINE_HIDPI_IMAGES`设置为NO。

在**stackoverflow**中有人碰到了相同的问题，[点击查看](http://stackoverflow.com/questions/12244494/image-resources-for-ios)
