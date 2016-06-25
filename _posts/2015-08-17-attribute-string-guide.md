---


layout:     post
title:      Attributed String 编程指南
category:   ios
tag:        guide

---

在处理字体和段落中，iOS提供了[Attributed String Programming Guide](https://developer.apple.com/library/prerelease/ios/documentation/Cocoa/Conceptual/AttributedStrings/AttributedStrings.html#//apple_ref/doc/uid/10000036-BBCCGDBG)来帮助开发者编写各种形态的字体，接下来对Attributed String做详细的介绍。

### 创建Attributed Strings

`NSAttributedString`对象可以用好几种方式创建，你可以通过`initWithString:`，`initWithString:attributes:`或者`initWithAttributedString:`方法来创建新的`Attributed String`。下面是一个常规的创建例子：

~~~objectivec
UIFont *font = [UIFont fontWithName:@"Palatino-Roman" size:14.0];
NSDictionary *attrsDictionary = [NSDictionary dictionaryWithObject:font forKey:NSFontAttributeName];
NSAttributedString *attrString = [[NSAttributedString alloc] initWithString:@"strigil" attributes:attrsDictionary];
~~~

`NSAttributedString`是不可修改的，所以经常使用`NSMutableAttributedString`来对`Attributed String`做修改。

### 修改Attributed Strings

`NSMutableAttributedString`声明了很多方法去修改字符和属性，比如主要的方法`replaceCharactersInRange:withString:`和`setAttributes:range:`，或者更方便的方法`addAttribute:value:range:`等等。

下面的例子介绍了如何在一个`Attribued String`中把选中的区域指定为Url链接，添加下划线，并且字体设置成蓝色。例子中使用了`beginEditing`和`endEditing`为了修复不一致的问题。

~~~objectivec
NSMutableAttributedString *string; // assume string exists
NSRange selectedRange; // assume this is set

NSURL *linkURL = [NSURL URLWithString:@"http://www.apple.com/"];

[string beginEditing];
[string addAttribute:NSLinkAttributeName
               value:linkURL
               range:selectedRange];

[string addAttribute:NSForegroundColorAttributeName
               value:[UIColor blueColor]
               range:selectedRange];

[string addAttribute:NSUnderlineStyleAttributeName
               value:[NSNumber numberWithInteger:1]
               range:selectedRange];
[string endEditing];
~~~

### 计算Attributed Strings的文本区域

`NSAttributedString`提供了方法来帮助我们计算文本区域，以便动态的设置文本域的宽或高。

下面的例子介绍了如何在固定宽度的情况下，计算文本域的高度。

~~~objectivec
NSAttributedString *    attrStr;    // assume string exists
CGSize                  txtSize;    // assume txtSize width
txtSize = [attrStr boundingRectWithSize:CGSizeMake(txtSize.width, MAXFLOAT)
                                options:(NSStringDrawingUsesLineFragmentOrigin | NSStringDrawingUsesFontLeading)
                                context:nil].size;
~~~

### 常用的Attributes

~~~objectivec
NSDictionary *  attrDict;
// 设置字体大小
attrDict =
@{
    NSFontAttributeName: [UIFont systemFontOfSize:18]
};
// 设置字体颜色
attrDict =
@{
    NSForegroundColorAttributeName: [UIColor redColor]
};
// 设置斜体
attrDict =
@{
    NSObliquenessAttributeName: @(0.5)
};
// 设置删除线
attrDict =
@{
    NSStrikethroughStyleAttributeName: @(1),
    NSStrikethroughColorAttributeName: [UIColor redColor]
};
// 设置下划线
attrDict =
@{
    NSUnderlineStyleAttributeName: @(NSUnderlineStyleDouble),
    NSUnderlineColorAttributeName: [UIColor redColor]
};
// 设置行间距
NSMutableParagraphStyle * ps    = [[NSMutableParagraphStyle alloc] init];
ps.lineSpacing                  = 10;
attrDict =
@{
    NSParagraphStyleAttributeName: ps
};
// 设置字间距
attrDict = 
@{
    NSKernAttributeName: @(10)
};
~~~

