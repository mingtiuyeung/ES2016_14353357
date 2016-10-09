# DOL框架描述(Description)
 The distributed operation layer (DOL) is a software development framework to program parallel applications. The DOL allows to specify applications based on the Kahn process network model of computation and features a simulation engine based on SystemC. Moreover, the DOL provides an XML-based specification format to describe the implementation of a parallel application on a multi-processor systems, including binding and mapping.
 The DOL consists of basically three parts:
*DOL Application Programming Interface: The DOL defines a set of computation and communication routines that enable the programming of distributed, parallel applications for the SHAPES platform. Using these routines, application programmers can write programs without having detailed knowledge about the underlying architecture. In fact, these routines are subject to further refinement in the hardware dependent software (HdS) layer.
*DOL Functional Simulation: To provide programmers a possibility to test their applications, a functional simulation framework has been developed. Besides functional verification of applications, this framework is used to obtain performance parameters at the application level.
*DOL Mapping Optimization: The goal of the DOL mapping optimization is to compute a set of optimal mappings of an application onto the SHAPES architecture platform. In a first step, XML based specification formats have been defined that allow to describe the application and the architecture at an abstract level. Still, all the information necessary to obtain accurate performance estimates is contained.
![frame](http://p1.bpimg.com/4851/2816b7851abd9647.png)
#How to install
1. 以ubunto为例，先是安装一些必要的环境：
* $	sudo apt-get update
* $	sudo apt-get install ant
* $ 	sudo apt-get install openjdk-7-jdk
* $	sudo apt-get install unzip
2. 然后是下载文件，使用Vmware虚拟机。
sudo wget http://www.accellera.org/images/downloads/standards/systemc/systemc-2.3.1.tgz
sudo wget http://www.tik.ee.ethz.ch/~shapes/downloads/dol_ethz.zip
3. 解压文件
$	mkdir dol
将dolethz.zip解压到 dol文件夹中
$	unzip dol_ethz.zip -d dol
解压systemc
$	tar -zxvf systemc-2.3.1.tgz
4. 编译systemc
解压后进入systemc-2.3.1的目录下
$	cd systemc-2.3.1
新建一个临时文件夹objdir
$	mkdir objdir
进入该文件夹objdir
$	cd objdir
运行configure
$	../configure CXX=g++ --disable-async-updates
![config](http://i1.piimg.com/4851/28262e0db67de54a.jpg)
编译
$	sudo make install
编译完后文件目录如下($ cd ..        $ ls
![config2](http://i1.piimg.com/4851/6e7c75af10274f50.jpg)
记录当前的工作路径(可知路径为/root/systemc-2.3.1)
$	pwd
![config3](http://i1.piimg.com/4851/953cb81b9f26422b.jpg)
5. 编译dol
进入刚刚dol的文件夹
$	cd ../dol
修改build_zip.xml文件
找到下面这段话，表明上面编译的systemc位置在哪里，
<property name="systemc.inc" value="YYY/include"/>
<property name="systemc.lib" value="YYY/lib-linux/libsystemc.a"/>
把YYY改成上页pwd的结果.
然后是编译
$	ant -f build_zip.xml all
若成功会显示build successful

接着可以试试运行第一个例子
进入build/bin/mian路径下
$	cd build/bin/main
然后运行第一个例子
$	ant -f runexample.xml -Dnumber=1
成功结果如图
![suc](http://i1.piimg.com/4851/953cb81b9f26422b.jpg)
#Experimental experience
本次实验主要是了解DOL框架原理，同时配置环境安装DOL。实验文档中有详细具体的安装步骤，因此在安装过程中没有出现太多意外，最终也成功安装好DOL。此外，由于我基础较为不好，在本次实验过程时，对于很多安装语句和过程仍需要更多的了解与熟悉。
