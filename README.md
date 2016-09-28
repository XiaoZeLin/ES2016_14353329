# 嵌入式系统Lab2_ReadMe
标签（空格分隔）： github_for_ES_lab2

---

 1. Description:
    由于这次实验是配置DOL环境，需要在虚拟机Ubuntu中进行。在配置过程中遇到的问题和困难并不算多，只是在C++complier的时候提示失败。DOL的整体配置过程：install ant、jdk和unzip—>systemc-2.3.1.tgz和dol_ethz.zip这两个压缩包 —> 最后是编译systemc和dol。整个过程历经一晚，主要是因为下载的龟速。

 2. How to install
    一开始按照师兄给的配置指导PPT，安装ant，jdk和unzip。其中jdk的91.6KB下载了好久，可能是他一边下载一边解压所以特别慢。然后到了编译systemc的步骤，我在运行configure的时候遇到了错误，它提示我c compiler cannot create executables。后来，我上网百度运行命令行：sudo apt-get install build-essential就可以了。最后，按照PPT进行dol的编译，就大功告成了。


 3. Experimental experience
    这次实验配置再次用到虚拟机，拥有虚拟机的感觉好棒，不再是单调的win7系统！！！Ubuntu系统其实感觉还不错，就是界面切换和文件查找的时候比较麻烦了一点。。

