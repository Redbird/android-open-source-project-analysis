# Android Open Source Project Analysis

<img src="https://github.com/guoxiaoxing/android-framework-source-code-analysis/raw/master/art/android_7_nougat.jpg" width="1000"/>

作者: 郭孝星  
邮箱: guoxiaoxingse@163.com  
博客: http://blog.csdn.net/allenwells   
简书: http://www.jianshu.com/users/66a47e04215b/latest_articles  

**关于作者**

>郭孝星，非著名程序员，代码洁癖患者，爱编程，好吉他，喜烹饪，爱一切有趣的事物和人。

**关于文章**

>作者的文章会同时发布在Github、CSDN与简书上, 文章顶部也会附上文章的Github链接。如果文章中有什么疑问也欢迎发邮件与我交流, 对于交流
的问题, 请描述清楚问题并附上代码与日志, 一般都会给予回复。如果文章中有什么错误, 也欢迎斧正。如果你觉得本文章对你有所帮助, 也欢迎去
star文章, 关注文章的最新的动态。另外建议大家去Github上浏览文章，一方面文章的写作都是在Github上进行的，所以Github上的更新是最及时
的，另一方面感觉Github对Markdown的支持更好，文章的渲染也更加美观。

文章目录：https://github.com/guoxiaoxing/android-open-source-project-analysis/blob/master/README.md

**写在前面**

>作者曾经看过很多关于Android源码分析的文章与书籍，这些前辈都写的很好，给Android技术的普及带来了很大的推动作用，随着Android技术的更
新，目前已经来到了Android 7.0 Nougat版本。所以笔者打算根据最新的源码从内核层到框架层再到应用层，从内核空间到用户空间，全面地去分析
Android系统内部的实现原理和设计思路，本系列的文章也会以一种独特的视角来做原理解析，来减轻大家在阅读源码时的枯燥感，好了，让我们开始吧。

**代码版本**

>[android-7.1.1_r1](https://source.android.com/source/build-numbers.html#source-code-tags-and-builds)

**分析思路**

>以某一个支线为起点，从上层往底层，不断地追溯，在各个模块、文件、方法之间来回跳转，反复地阅读，理清整个流程的逻辑。
同时带着思考去看源码，去揣测作者的用意，去理解代码的精妙之处，去思考代码可能存在的缺陷，去总结优秀的代码设计思想。

本系列文章由下至上，从内核层到框架层再到应用层，从内核空间到用户空间，全面的分析内部的实现原理和设计思路。在源码的分析过程中，还会穿插分析源码的
设计模式与编程思想（编程中的抽象、接口、六大原则以及23种设计模式），以下为后续文章的具体安排。

**Android系统架构图**

<img src="https://github.com/guoxiaoxing/android-framework-source-code-analysis/raw/master/art/android_system_structure.png" width="700"/>

文章更新中...

在正式开始分析源码之前，我们先做一些准备工作。

- [导读](https://github.com/guoxiaoxing/android-open-source-project-analysis/blob/master/doc/导读.md)

**Android系统应用框架篇**

- [1Android系统应用框架篇：Activity源码概览](https://github.com/guoxiaoxing/android-open-source-project-analysis/blob/master/doc/Android系统应用框架篇/1Android系统应用框架篇：Activity源码概览.md)
- [2Android系统应用框架篇：Activity生命周期](https://github.com/guoxiaoxing/android-open-source-project-analysis/blob/master/doc/Android系统应用框架篇/2Android系统应用框架篇：Activity生命周期.md)
- [2Android系统应用框架篇：Activity启动模式与标识位](https://github.com/guoxiaoxing/android-open-source-project-analysis/blob/master/doc/Android系统应用框架篇/2Android系统应用框架篇：Activity启动模式与标识位.md)
- [3Android系统应用框架篇：Activity启动流程](https://github.com/guoxiaoxing/android-open-source-project-analysis/blob/master/doc/Android系统应用框架篇/3Android系统应用框架篇：Activity启动流程.md)
- Android系统应用框架篇：Service源码概览
- Android系统应用框架篇：Service生命周期
- Android系统应用框架篇：Service启动流程与绑定流程
- Android系统应用框架篇：Broadcast Receiver源码概览
- Android系统应用框架篇：Broadcast Receiver广播的注册与发送
- Android系统应用框架篇：Content Provider源码概览
- Android系统应用框架篇：Content Provider启动流程
- Android系统应用框架篇：Android应用程序框架
- Android系统应用框架篇：Android UI框架
- Android系统应用框架篇：Android 应用资源管理框架
- Android系统应用框架篇：Android应用消息处理系统
- Android系统应用框架篇：Andriod进程与线程
- Android系统应用框架篇：Webkit
- Android系统应用框架篇：OpenGL|ES
- Android系统应用框架篇：Android 多媒体系统
- Android系统应用框架篇：Android 定位系统
- Android系统应用框架篇：Android 安全机制

**Android系统底层框架篇**

>本篇章从Android源码的下载与编译开始，讲述HAL、智能指针等底层原理。

- Android系统基础篇：硬件抽象层
- Android系统基础篇：智能指针
- Android系统基础篇：ART/Dalvik 虚拟机
- Android系统驱动篇：Binder进程通信系统
- Android系统驱动篇：Ashmem匿名共享内存系统

**Android系统编程思想篇**

- [1Android系统编程思想篇：单例模式](https://github.com/guoxiaoxing/android-open-source-project-analysis/blob/master/doc/Android系统编程思想篇/1Android系统编程思想篇：单例模式.md)
- [1Android系统编程思想篇：建造者模式](https://github.com/guoxiaoxing/android-open-source-project-analysis/blob/master/doc/Android系统编程思想篇/2Android系统编程思想篇：建造者模式.md)
- Android系统编程思想篇：原型模式
- Android系统编程思想篇：工厂模式
- Android系统编程思想篇：抽象工厂模式
- Android系统编程思想篇：策略模式
- Android系统编程思想篇：状态模式
- Android系统编程思想篇：责任链模式
- Android系统编程思想篇：解释器模式
- Android系统编程思想篇：命令模式
- Android系统编程思想篇：观察者模式
- Android系统编程思想篇：备忘录模式
- Android系统编程思想篇：迭代器模式
- Android系统编程思想篇：模板方法模式
- Android系统编程思想篇：访问者模式
- Android系统编程思想篇：中介者模式
- Android系统编程思想篇：代理模式
- Android系统编程思想篇：组合模式
- Android系统编程思想篇：适配器模式
- Android系统编程思想篇：装饰模式
- Android系统编程思想篇：享元模式
- Android系统编程思想篇：外观模式
- Android系统编程思想篇：桥接模式
- Android系统编程思想篇：软件设计原则
