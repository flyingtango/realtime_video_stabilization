## real-time video stabilisation
### 环境
运行系统：windows 10 
运行环境：vs2013、opencv
### 可执行程序运行
在exe文件夹中，有两个可执行程序stab360p和stab720p，两个均可在无opencv环境的电脑中运行。
#### 运行需知
*当屏幕中显示：please input the camera number 时，请输入您电脑摄像头的编号，自带的为0。笔记本的话只需要输入0即可。*
*程序会自动运行，并出现两个窗口，一个为处理前的原始画面，另一个为处理后的稳定画面。您可以晃动摄像头**（注意是摄像头，不是画面中的人，比如转头等）**，去查看处理前后的变化。*
*若需要退出，则按ESC键即可，随后窗口会显示处理的帧数。*
### 源码编译需知
**非常不建议自行编译运行，opencv的环境配置繁琐，随电脑的变化和VS版本的变化差异非常大。考虑到程序的可移植性，我配置了相对路径和自动编译，可是在测试时，试了3台电脑，每次都仍需重新配置项目属性，VC路径，十分不便，故不推荐**
虽然不推荐，以下仍给出配置方法。
#### 配置opencv和vs环境
参照：[http://blog.csdn.net/waterbinbin/article/details/52238519][1]，其中配置项目路径时，不需要新建一个空项目，直接打开vs2013\_project/stab/stab.sln项目，然后对该项目的属性进行配置。
#### 可能出现的问题
1.在使用比vs2013版本高的vs导入项目时，会出现无法加载平台中的解决方案，没有安装v120的工具集等问题，这时需要调整vs的平台工具集。第一种方法是找到导航栏中的生成—-\>重新生成解决方案；第二种方法是如图，
![]()([http://www.baidu.com/img/bdlogo.gif][3])
打开项目属性，调整工具集的版本，可高可低，选择自己vs已经安装的版本即可。

2.若出现找不到core/core.h等情况，请检查项目属性中的路径是否包含完整。
3.若需使用opencl或cuda加速程序，需用cmake编译opencv，程序默认使用cpu，要启用gpu可以在define.h文件中修改后编译运行。并且若您需要调教显示画面的大小，也可以通过define.h中的#define去选择。
4.项目的主要文件为videostab.cpp，所包含处理过程，如匹配等均为单独文件，并include在主函数文件中。

[1]:	http://blog.csdn.net/waterbinbin/article/details/52238519
[3]:	https://github.com/flyingtango/real-time-video-stabilization/blob/master/1.png