##JDK1.8源码分析之idea搭建源码阅读环境

目前新开发的项目， 大多数都是基于JDK1.8开发，所以我选择该版本进行源码分析。

JDK1.8版本号：jdk1.8.0_151

###一. JDK1.8的src在哪里？

找到JDK安装包所在目录，会看到src.zip的压缩包，这里面就是JDK的源码，如下图。

![img](images/20201204001.png)

###二. idea搭建步骤

**01. 新建一个简单的Java工程** 打开idea，菜单栏File => Project，出现如下图

![img](images/20201204002.png)

在点Next， 选个初始化一个Hello word应用，出现如下图：

![img](images/20201204003.png)

再点Next, 输入项目名， 及保存路径：

![img](images/20201204004.png)

最后出现的界面如下：

![img](images/20201204005.png)

**02. 把源码src.zip解压到该工程下的src目录下**

![img](images/20201204006.png)

你以为这样就万事大吉了吗？NO, NO, NO

我导入后，运行Main.java文件里面，看能不能正常运行起来，结果在编译的时候，出现了各种ERROR, 找不到xxx类等问题。

![img](images/20201204007.png)

看着这么多错误，我有打算放弃的念头。但是，针对技术，我是一个很倔强的人。

索性思考了一番，这不就是我没遇到过的问题吗？如果解决了，那不是又增长了知识。

开始了我的疯狂自虐操作。

比如 找不到xxx类，可以去网上找相关的类，添加进去就好。只要不是与项目JDK有冲突问题，就都还好。

索性最后问题都被我逐一解决了，最终运行成功。

![img](images/20201204008.png)

###三. 搭建过程中问题总结

各种ERROR解决思路，为以后的朋友们铺平道路

我是一个修路工人。

#### 问题1：缺少com.sun.tools包

![img](images/20201204009.png)

**解决思路：**File => Project structure => Libraries 把jdk路径下的lib包添加到工程中，如下图： ![img](images/20201204010.png)

#### 问题2：缺少sun.awt.UNIXToolkit 和 sun.font.FontConfigManager这两个类

**解决思路：** 在src的目录下手动添加这两个类 ![img](images/20201204011.png)

#### 问题3：debug的时候，出现如下，调用的src.zip中的文件

![img](images/20201204012.png)

**解决思路：** 排除掉src.zip文件，按下图操作即可。 ![img](images/20201204013.png)

#### 问题4：debug的时候，误点Alternative source availble for the class xxxx 的disable

![img](images/20201204014.png)

**解决思路：** 打开setting => Debugger， 如下图 选中该选项。

![](images/20201204015.png)