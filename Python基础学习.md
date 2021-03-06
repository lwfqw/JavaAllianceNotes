#   Python基础学习

##  前言

Python就为我们提供了非常完善的基础代码库，覆盖了网络、文件、GUI、数据库、文本等大量内容，被形象地称作“内置电池（batteries included）”。用Python开发，许多功能不必从零编写，直接使用现成的即可。

那Python适合开发哪些类型的应用呢？

首选是网络应用，包括网站、后台服务等等；

其次是许多日常需要的小工具，包括系统管理员需要的脚本任务等等；

另外就是把其他语言开发的程序再包装起来，方便使用。



## 一、安装Python

因为Python是跨平台的，它可以运行在Windows、Mac和各种Linux/Unix系统上。在Windows上写Python程序，放到Linux上也是能够运行的。

要开始学习Python编程，首先就得把Python安装到你的电脑里。安装后，你会得到Python解释器（就是负责运行Python程序的），一个命令行交互环境，还有一个简单的集成开发环境。

### 安装Python 3.7

目前，Python有两个版本，一个是2.x版，一个是3.x版，这两个版本是不兼容的。由于3.x版越来越普及，我们的教程将以最新的Python 3.7版本为基础。请确保你的电脑上安装的Python版本是最新的3.7.x，这样，你才能无痛学习这个教程。

#### 在Mac上安装Python

如果你正在使用Mac，系统是OS X>=10.9，那么系统自带的Python版本是2.7。要安装最新的Python 3.7，有两个方法：

方法一：从Python官网下载Python 3.7的[安装程序](https://www.python.org/ftp/python/3.7.0/python-3.7.0-macosx10.9.pkg)（网速慢的同学请移步[国内镜像](https://pan.baidu.com/s/1kU5OCOB#list/path=%2Fpub%2Fpython)），双击运行并安装；

方法二：如果安装了[Homebrew](https://brew.sh/)，直接通过命令`brew install python3`安装即可。

#### 在Linux上安装Python

如果你正在使用Linux，那我可以假定你有Linux系统管理经验，自行安装Python 3应该没有问题，否则，请换回Windows系统。

对于大量的目前仍在使用Windows的同学，如果短期内没有打算换Mac，就可以继续阅读以下内容。

#### 在Windows上安装Python

首先，根据你的Windows版本（64位还是32位）从Python的官方网站下载Python 3.7对应的[64位安装程序](https://www.python.org/ftp/python/3.7.0/python-3.7.0-amd64.exe)或[32位安装程序](https://www.python.org/ftp/python/3.7.0/python-3.7.0.exe)（网速慢的同学请移步[国内镜像](https://pan.baidu.com/s/1kU5OCOB#list/path=%2Fpub%2Fpython)），然后，运行下载的EXE安装包：

<img src="https://javaalliance.oss-cn-shenzhen.aliyuncs.com/img/20190603152727.png"/>

特别要注意勾上`Add Python 3.7 to PATH`，然后点“Install Now”即可完成安装。

### 运行Python

安装成功后，打开命令提示符窗口，敲入python后，会出现两种情况：

情况一：

<img src="https://javaalliance.oss-cn-shenzhen.aliyuncs.com/img/20190603153424.png"/>

看到上面的画面，就说明Python安装成功！

你看到提示符`>>>`就表示我们已经在Python交互式环境中了，可以输入任何Python代码，回车后会立刻得到执行结果。现在，输入`exit()`并回车，就可以退出Python交互式环境（直接关掉命令行窗口也可以）。



情况二：得到一个错误：

<img src="https://javaalliance.oss-cn-shenzhen.aliyuncs.com/img/20190603153613.png"/>

这是因为Windows会根据一个`Path`的环境变量设定的路径去查找`python.exe`，如果没找到，就会报错。如果在安装时漏掉了勾选`Add Python 3.7 to PATH`，那就要手动把`python.exe`所在的路径添加到Path中。

如果你不知道怎么修改环境变量，建议把Python安装程序重新运行一遍，务必记得勾上`Add Python 3.7 to PATH`。

##  二、Python解释器

------

当我们编写Python代码时，我们得到的是一个包含Python代码的以`.py`为扩展名的文本文件。要运行代码，就需要Python解释器去执行`.py`文件。

由于整个Python语言从规范到解释器都是开源的，所以理论上，只要水平够高，任何人都可以编写Python解释器来执行Python代码（当然难度很大）。事实上，确实存在多种Python解释器。

### CPython

当我们从[Python官方网站](https://www.python.org/)下载并安装好Python 3.x后，我们就直接获得了一个官方版本的解释器：CPython。这个解释器是用C语言开发的，所以叫CPython。在命令行下运行`python`就是启动CPython解释器。

CPython是使用最广的Python解释器。教程的所有代码也都在CPython下执行。

### IPython

IPython是基于CPython之上的一个交互式解释器，也就是说，IPython只是在交互方式上有所增强，但是执行Python代码的功能和CPython是完全一样的。好比很多国产浏览器虽然外观不同，但内核其实都是调用了IE。

CPython用`>>>`作为提示符，而IPython用`In [序号]:`作为提示符。

### PyPy

PyPy是另一个Python解释器，它的目标是执行速度。PyPy采用[JIT技术](http://en.wikipedia.org/wiki/Just-in-time_compilation)，对Python代码进行动态编译（注意不是解释），所以可以显著提高Python代码的执行速度。

绝大部分Python代码都可以在PyPy下运行，但是PyPy和CPython有一些是不同的，这就导致相同的Python代码在两种解释器下执行可能会有不同的结果。如果你的代码要放到PyPy下执行，就需要了解[PyPy和CPython的不同点](http://pypy.readthedocs.org/en/latest/cpython_differences.html)。

### Jython

Jython是运行在Java平台上的Python解释器，可以直接把Python代码编译成Java字节码执行。

### IronPython

IronPython和Jython类似，只不过IronPython是运行在微软.Net平台上的Python解释器，可以直接把Python代码编译成.Net的字节码。

### 小结

Python的解释器很多，但使用最广泛的还是CPython。如果要和Java或.Net平台交互，最好的办法不是用Jython或IronPython，而是通过网络调用来交互，确保各程序之间的独立性。

本教程的所有代码只确保在CPython 3.x版本下运行。请务必在本地安装CPython（也就是从Python官方网站下载的安装程序）