关于win10系统双JDK使用切换的解决方案
---
2018-04-30，星期一

#### ① 问题背景
> 因为毕业设计采用的是64位的JDK及开发工具，版本为jdk8，公司的项目使用的是32位的JDK及开发工具，版本为jdk7。在切换两个不同的开发环境时遇到了一些问题，遂做以下相关问题的解决方案。

#### ② 准备JDK
+ 下载JDK
    > 在Oracle官网挑选jdk版本和位数,一般来说，32位系统只能安装32位的jdk，64位系统安装64位jdk完美发挥性能。对于开发工具，一般来说要和jdk位数对应。
+ 安装JDK
    > 两个版本的jdk和jre都安装到你指定的位置，在`控制面板 → 程序`中可以看到`Java`程序配置选项。

#### ③ 配置环境变量
+ 配置JAVA_HOME
    > 因为是两个版本，避免重复修改路径，新建两个键值，分别对应两个路径，即`JAVA7_HOME`、`JAVA8_HOME`,需要使用哪个版本，就去掉对应的版本数字
+ 配置Path
    > 在Path配置`%JAVA_HOME%\bin;%JAVA_HOME%\jre\bin;`，一般来说该配置，需要放在`Oracle\Java\javapath`的配置前面。
+ 配置CLASSPATH
    > 添加`CALSSPATH`，设置参数为`.;%JAVA_HOME%\lib;%JAVA_HOME%\lib\tools.jar`,至此环境变量配置结束。

#### ④ 配置Java程序参数
+ 删除干扰程序
    > 在`Windows → System32`中选中`java.exe、javaw.exe、javaws.exe`然后删掉，此举在于避免此处优先级高于环境变量配置，导致切换失败。
+ 配置参数
    > 在`控制面板 → 程序`中可以看到`Java`程序配置选项，打开Java程序，选中Java菜单然后查看，此时已经读取到两个版本的jdk信息，选择使用的jdk版本点击启用即可。

#### ⑤ 测试方案
+ 选中JDK
    > 在环境变量和Java参数设置里选用统一使用的jdk版本
+ 测试jdk版本
    > 在命令提示符键入`java -version`即可查询到当前使用的jdk版本信息

#### ⑥ 写在后面
> 只是针对已经使用jdk对切换jdk有需求的使用者，记录了自己解决相关问题的方案，至于遗漏和其他问题不做详解，再有增修，会做批注。
