# report 
### student number：14353223
### name: 罗海福

* **Description**：
 The distributed operation layer (DOL) is a framework that enables the (semi-) automatic mapping of applications onto the multiprocessor SHAPES architecture platform.
	
	1. **DOL Application Programming Interface:** The DOL defines a set of computation and communication routines that enable the programming of distributed, parallel applications for the SHAPES platform. Using these routines, application programmers can write programs without having detailed knowledge about the underlying architecture. In fact, these routines are subject to further refinement in the hardware dependent software (HdS) layer.

	2. **DOL Functional Simulation:** To provide programmers a possibility to test their applications, a functional simulation framework has been developed. Besides functional verification of applications, this framework is used to obtain performance parameters at the application level.

	3. **DOL Mapping Optimization:** The goal of the DOL mapping optimization is to compute a set of optimal mappings of an application onto the SHAPES architecture platform. In a first step, XML based specification formats have been defined that allow to describe the application and the architecture at an abstract level. Still, all the information necessary to obtain accurate performance estimates is contained.

* **How to install**

	* 本次实验环境在Linux下进行，使用VMware安装Ubuntu。利用网上教程安装并打开Ubuntu 安装一些必要的环境
		
		
		` sudo apt-get update `
		` sudo apt-get install ant`
		` sudo apt-get install openjdk-7-jdk`
		`sudo apt-get install unzip`
	* 下载文件
		` sudo wget http://www.accellera.org/images/downloads/standards/systemc/systemc-2.3.1.tgz`

		` sudo wget http://www.tik.ee.ethz.ch/~shapes/downloads/dol_ethz.zip`

	* 解压文件

		新建dol的文件夹

		` mkdir dol`
	
		将dolethz.zip解压到dol文件夹中
	
		` unzip dol_ethz.zip -d dol`
	
		解压systemc
	
		` tar -zxvf systemc-2.3.1.tgz`
	
	* 编译systemc 
	
		解压后进入systemc-2.3.1的目录下
	
		` cd systemc-2.3.1`

		新建一个临时文件夹objdir

		` mkdir objdir`

		进入该文件夹

		` cd objdir`

		运行configure（能根据系统的环境设置一下参数用于编译）

		` ../configure CXX=g++ --disable-async-updates`

		 ![](http://p1.bqimg.com/4851/4caa368b04be9787.png)
		上图为运行configure之后的截图

		编译

		` sudo make install`
	
		编译完之后 `cd ..`，`ls `

		文件目录如下：
		![](http://p1.bqimg.com/4851/91a366a7ae2303dc.png)

		当前工作的路径为 `pwd`
		![](http://p1.bqimg.com/4851/1601dddd0d363a90.png)

	* 编译dol
	
		进入刚刚的dol文件
		
		` cd ../dol`

		修改build_zip.xml文件

		` sudo gedit build_zip.xml`

		更改编译的systemc的路径为我们刚刚的工作路径：
		![](http://p1.bpimg.com/4851/228b13cba06aa796.png)

		编译
	
		` ant -f build_zip.xml all`

		成功会显示build successful
		![](http://p1.bpimg.com/4851/d8d5fab50f26d716.png)

		接着试着运行第一个例子，进入build/bin/main路径下
	
		`cd build/bin/main`

		运行第一个例子

		`sudo ant -f runexample.xml -Dnumber=1`

		成功结果如图

		![](http://p1.bpimg.com/4851/eae0008bb2985b78.png)
		![](http://p1.bqimg.com/4851/2798c3753047bd7e.png)

* Experimental experience
	
	* 实验过程中的问题
		* 在编译systemc的时候 configure总是失败无法编译完，可能是因为没有装g++的缘故。运行`sudo apt-get install g++` 语句将g++装上即可编译成功，编译成功后要`sudo make install`然后查看文件目录是否齐全。
		 

		* 一定要记录当前的工作路径方便之后更改systemc的位置。切记不可有换行符以及路径名称不可输入错误，最好粘贴复制之前记录的工作路径。

		* 如果最后一步一直build failed 可能是因为runexample.xml中第211行到218行需要被注释掉的原因。
		![](http://p1.bqimg.com/4851/845dee1f34d43ea7.png)

	* 实验感想
	
		1. 本次实验主要是以配置环境为主，中间可能会出现各种各样的问题，在此我只将困扰我比较久的问题加以总结概括，进行阐述。本次实验需要我们重点了解dol的框架结构，以及利用Ubuntu命令行进行配置dol环境，按部就班将环境配置好，相对来说对于命令行的操作还是需要对命令行语句相当熟练才可以，看懂每一步在做些什么。
		2. 版本控制：了解为什么要做版本控制？如何做版本控制？本次课程选择使用Git进行版本控制，并将仓库托管在Github上，我们通过[Git教程-廖雪峰的官方网站](http://www.liaoxuefeng.com/wiki/0013739516305929606dd18361248578c67b8067c8c017b000)进行Github的配置安装，了解基本Git的操作方法，以及相应的语法。然后再提供Git仓库托管服务的Github网站上注册一个账号获得Git远程仓库。然后学习实现本地仓库和远程仓库的关联同步。可以把本地库的所有内容推送到远程库上，也可以从远程库克隆到本地库。
		
		
		


		  
		 