
## 嵌入式系统Lab2_ReadMe##

* * *

**Description:**


   分布式操作层（DOL）是一个框架，使（半）应用到多处理器架构平台自动绘制形状，基本上由三个部分：
   
1.    DOL应用程序编程接口：DOL定义了一组计算和通信的例程，使分布式的编程，对图形平台的并行应用程序。使用这些程序，应用程序程序员可以编写程序，而不必对底层的架构有详细的了解。事实上，在硬件相关的软件这些程序有待进一步细化（HDS）层。
2.    DOL的仿真功能：为程序员提供一个可能性来测试他们的应用程序，功能仿真框架已经形成。除了应用程序的功能验证，该框架是用来获得在应用程序级的性能参数。
3.    DOL的DOL映射优化：优化的目标是计算一组应用程序的最佳映射到图形架构平台。在第一步骤中，基于XML的规范格式已被定义，允许描述的应用程序和在一个抽象的水平的体系结构。然而，所有必要的信息，以获得准确的性能估计是包含。
   
==   由于这次实验是配置DOL环境，需要在虚拟机Ubuntu中进行。在配置过程中遇到的问题和困难并不算多，只是在C++complier的时候提示失败。DOL的整体配置过程：install ant、jdk和unzip—>systemc-2.3.1.tgz和dol_ethz.zip这两个压缩包 —> 最后是编译systemc和dol。整个过程历经一晚，主要是因为下载的龟速。==
   
**How to install：**


  一开始按照师兄给的配置指导PPT，安装ant，jdk和unzip。其中jdk的91.6KB下载了好久，可能是他一边下载一边解压所以特别慢。
```	
   $	sudo apt-get update
   $	sudo apt-get install ant
   $    sudo apt-get install openjdk-7-jdk
   $	sudo apt-get install unzip
```
   然后到了编译systemc的步骤:
```
   $	mkdir dol
   $	unzip dol_ethz.zip -d dol
   $	tar -zxvf systemc-2.3.1.tgz
   $	cd systemc-2.3.1
   $	mkdir objdir
   $	cd objdir
   $	../configure CXX=g++ --disable-async-updates
   $	sudo make install
   $	pwd
```
   
   我在运行configure的时候遇到了错误，它提示我c compiler cannot create executables。后来，我上网百度运行命令行：`sudo apt-get install build-essential`就可以了。编译configure成功的时候的截图如下：
   ![](https://github.com/XiaoZeLin/photo/blob/master/%E5%B5%8C%E5%85%A5%E5%BC%8Flab2_1.png)
   
   
   最重要的是在运行pwd的时候会打开当前文件路径，这需要记下来，因为待会编译dol的时候要用到。
   
   最后，按照PPT进行dol的编译：
   ```
   $	cd ../dol
```
   修改build_zip.xml文件找到下面这段话，就是说上面编译的systemc位置在哪里，将YYY改成刚才记下来的systemc的路径：    
   *property name="systemc.inc" value="YYY/include"/*
   *property name="systemc.lib" value="YYY/lib-linux/libsystemc.a"/*
   ```
   $	ant -f build_zip.xml all
   $	cd build/bin/main
   $	ant -f runexample.xml -Dnumber=1
```
  最后运行第一个例子，截图如下：
  
  ![](https://github.com/XiaoZeLin/photo/blob/master/%E5%B5%8C%E5%85%A5%E5%BC%8Flab2_3.png)
  
  
  到这里就大功告成！！！
   
**Experimental experience：**


   这次实验配置再次用到虚拟机，拥有虚拟机的感觉好棒，不再是单调的win7系统！！！Ubuntu系统其实感觉还不错，就是界面切换和文件查找的时候比较麻烦了一点。。


* * *


