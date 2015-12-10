# xilium.cefglue

#Intruduction

CefGlue是建立在Cef项目之上的，
Cef项目是C/C++的项目；
CefGlue只不过是通过PInvoke来访问Cef项目生成的一些dll
下面我们来看看Cef项目生成的一些dll和资源都是做什么用的
打开这个目录\cef_binary_3.1453.1236_windows_xilium\Release
libcef.dll-------------------------->Cef的核心类库
icudt.dll-------------------------->支持unicode的类库
ffmpegsumo.dll------------------>支持音频和视频的类库
d3dcompiler_43.dll--------------->WinXP下支持3D的类库
d3dcompiler_46.dll--------------->Win7和之后的Win支持3D的类库
libEGL.dll------------------------->用于支持3D
libGLESv2.dll--------------------->用于支持3D

打开目录：\cef_binary_3.1453.1236_windows_xilium\Resources
locales--------------------------->此文件夹存放了各种国家的语言资源
cef.pak-------------------------->为WebKit相关的资源（谷歌浏览器的核心是webkit）
devtools_resources.pak--------->调试器的相关资源（我们做的项目是可以使用谷歌浏览器的调试器的）

##
在程序集中创建一个文件夹取名dll
在程序集的属性里设置此程序集的预先生成事件的命令

```xcopy $(ProjectDir)dll $(TargetDir) /e /i /y```

这个命令的目的是：每次编译的时候把dll文件夹中的文件拷贝的输出目录中

把\cef_binary_3.1453.1236_windows_xilium\Release此目录下的所有文件都拷贝到CefDemo的dll目录中去
把\cef_binary_3.1453.1236_windows_xilium\Resources此目录下的所有文件和文件夹拷贝到dll目录中去
注意：locales子目录下的文件大部分都没有用，你可以把所有的文件都删掉，只留下zh-CN.pak文件。
打开Xilium.CefGlue工程，release编译CefGlue程序集，把生成的Xilium.CefGlue.dll也拷贝到CefDemo的dll目录中去
在CefDemo项目中添加Xilium.CefGlue.dll的引用
