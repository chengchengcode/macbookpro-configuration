# macbookpro-configuration
macbookpro-configuration

# IDL 7.0 安装

## 这是以前为intel版本的macbook写的安装笔记：

安装XQuartz，安装IDL，打开IDL，报错

1，time machine之类的不支持

官网说要 . /Applications/exelis/idl82/bin/idl_setup.bash

也就是启动IDL前刷一下 idl_setup.bash，有时候不太灵，su登录到root后也许会好些

2，X11不对

这个报错源于很久前X11在/usr，而新的苹果系统把X11放到/opt，所以可以做一个从opt到/usr的软链接：sudo ln -s /opt/X11 /usr/X11

把

idl71/bin/bin.darwin.x86_64/libz.1.dylib 

换名字：

sudo mv libz.1.dylib libz.1.dylib.HIDE

3，X11还是不对

重装XQuartz为版本2.7.7

5，偶尔有不重要的报错

把

idl71/bin/bin.darwin.x86_64/gl_driver.so 

改为

idl71/bin/bin.darwin.x86_64/gl_driver.so.bak

6，从time mechine备份里还原系统后，X11找不到

/usr/local 里有个内容为空的、删不掉的X11的超链接，用 ls -al 可以找到这个文件的位置，再把/opt里的X11软链接到这里

## 这是在安装配备了M3的macbook的笔记：

在装IDL的时候，我按照IDL安装笔记建议，尽全力也只能做到终端输入idl后，输入su密码才能打开idl

运行的时候，idl认得出来的path是在idl里输入 !PATH，发现我的idl库都不在这些位置，只好把idl库文件全都放到!PATH显示的 idl lib位置

我用textmate写idl程序，需要安装idl的bundle，新系统能装textmate2，界面差不多，在这里：

https://github.com/mgalloy/idl.tmbundle

下载安装这个东西，只好可以把一些祖传的idl bundle文件放在这里

/Users/chengcheng/Library/Application Support/TextMate/Bundles/idl.tmbundle/Snippets

# 奔图打印机安装

在奔图打印机网站找到mac系统的驱动，安装驱动

在系统设置里找到添加打印机，选IP：输入打印机的IP在address；Protocol选LPD；Name里写个记得住的名字；Use里选Pantum P3000 Series

# 三指拖动

搜索添加三指拖动的方法

# Swarp安装

容易找到的github的swarp不好用，改成早期的版本：

https://web.archive.org/web/20170314015522/https://www.astromatic.net/download/swarp/swarp-2.38.0.tar.gz

# SExtractor安装

brew install 能装上

# Bagpipes报错 dlsym(RTLD_DEFAULT, run)

参考：https://github.com/ACCarnall/bagpipes/issues/83 改用nautilus

import bagpipes as pipes
galaxy = pipes.galaxy("17433", load_goodss, spectrum_exists=False, filt_list=goodss_filt_list)
fit = pipes.fit(galaxy, fit_instructions)
fit.fit(n_live=1000, verbose=True, use_MPI=False, sampler="nautilus", pool=12)

# ds9安装后容易报错甚至不能WCS对齐

找到ds9网站换个版本，认真看安装说明和报错
