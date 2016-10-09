# DOL框架描述
    DOL，即distributed operation layer，分布式操作层，是一种能够将应用程序全自动或半自动地映射到多处理器SHAPES架构平台的框架。
DOL基本上由三部分组成
## DOL应用程序编程接口
    DOL定义了一些可用于SHAPES平台的应用编程的计算与通信的例程，作为接口给编程人人员使用。
## DOL的仿真功能
    仿真功能为编程人员提供了一种方法来测试他们编写的应用程序。
## DOL映射优化
    DOL映射优化的目标就是计算一组从应用程序到SHAPES架构平台的最优映射。


# DOL的安装
建议在linux的环境下进行，可以使用VMWARE虚拟机并安装一个Ubuntu。下面为具体步骤：
## 安装一些必要的环境
    a.更新已安装的包。 （sudo apt-get update）
    b.安装Ant工具，Ant类似于C语言中的make脚本，而它用java的类来扩展，是一个流程脚本引擎，用于自动化调用程序完成项目的编译、打包和测试等。 （sudo apt-get install ant）
    c.安装java的开发环境，在大多数linux发行版本里，内置或者通过软件安装jdk的话，都是安装openjdk，openjdk是jdk的开放原始码版本。 
    （sudo apt-get install openjdk-7-jdk）
    d.解压。 （sudo apt-get install unzip）
## 下载需要的文件。 
    a.下载systemc的压缩包，systemc是一种软硬件协同设计语言，一种新的系统级建模语言。（sudo wget http://www.accellera.org/images/downloads/standards/systemc/systemc-2.3.1.tgz）
    b.下载我们所需要的dol的压缩包。（sudo wget http://www.tik.ee.ethz.ch/~shapes/downloads/dol_ethz.zip）
## 解压文件
    a.新建dol的文件夹。 （mkdir dol）
    b.将dolethz.zip解压到dol文件夹中。 （unzip dol_ethz.zip -d dol）
    c.解压systemc。 （tar -zxvf systemc-2.3.1.tgz）
## 编译systemc
    a.进入systemc的目录下。 （cd systemc-2.3.1）
    b.新建一个临时文件夹。 （mkdir objdir）
    c.进入新建的文件夹。 （cd objdir）
    d.运行configure。 （../configure CXX=g++ --disable-async-updates） configure之后结果如图。
    ![configure结果][1]
    e.编译。 （sudo make install）
    f.记录当前的工作路径。 （pwd）这里出现的路径最好记下来，后面会用到。
## 编译dol
    a.进入dol文件夹。 （cd../dol）
    b.打开build_zip.xml文件，找到下面这段话。
    <property name="systemc.inc" value="YYY/include"/>
    <property name="systemc.lib" value="YYY/lib-linux/libsystemc.a"/>
    将其中的YYY改成你所记录的pwd的结果。
    c.进行编译。 （ant -f build_zip.xml）这里如果编译成功会显示build successful。
    d.进入build/bin/main路径下。 （cd build/bin/main） 然后运行第一个例子。 （sudo ant -f runexample.xml -Dnumber=1） 运行成功结果如下图。
    ![运行成功结果][2]


# 实验心得
	dol编译完成后可能运行不成功，可能是因为安装了多个版本的java。解决方法是设置java的环境变量。这里我们要修改profile，先获得root权限，使用gedit编辑。（sudo gedit /etc/profile）  然后进入profile文件，在文件末尾添加三行，这里要根据自己具体的情况修改。
    export JAVA_HOME=（这里是你的jdk存放目录）
    export CLASSPATH=...
    export PATH=...

  [1]: ./images/configure.jpg "configure.jpg"
  [2]: ./images/run-example.jpg "run-example.jpg"