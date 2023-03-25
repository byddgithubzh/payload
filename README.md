# actions_android_bootimg_payload_dumper
利用Github Actions云端解包payload.bin并提取boot.img


## 简介 ##
这是一个利用github actions云端自动化提取刷机包payload.bin中的任意镜像的脚本。

# 快速编辑

一步打开[get_images.yml](https://github.com/byddgithubzh/payload/edit/main/.github/workflows/geeting.yml)


# 打开GitHub Action

快捷打开[Github Action](https://github.com/byddgithubzh/alto_payload/actions)
一些留存代码段放在了，[build.txt](https://github.com/byddgithubzh/alto_payload/blob/main/%E8%BD%AF%E4%BB%B6/build.txt)


# 使用

我测试的是Redmi K40的，其他相同情况的同理。

首先点击fork这个仓库到你自己的账号下。 
 
接着，编辑.github/workflows文件夹下的.yml文件，将ROM_URL改成你要提取的刷机包直链地址（最好是官方直链，如miui的官方下载地址），支持zip刷机包（zip里面是payload.bin）。

最后，仅仅需要按下Star小星星按钮，就可以提取刷机包payload.bin中的任意镜像文件

查看进度，在Actions菜单，get_bootimg_from_payload→make→Upload the bootimg to WeTransfer中找到Download link:xxx就是下载地址。

本项目依赖来自：https://github.com/ssut/payload-dumper-go 感谢。


# 一些可用快捷方便程序

经过测试可用affggh开发的[logo_dumper](https://github.com/affggh/logo_dumper)程序提取bmp位图，实际上也是用dd命令。

尤其的，需要使用一个其中一个30 Jul 2021 [commits](https://github.com/affggh/logo_dumper/tree/6760663fc56d8c694a0417f368e3c5eaed9c4e93)中的程序。
语法：打开CMD使用logo_dumper.bat，logo_dumper.bat logo.img extract/inject

联发科设备使用的，[LogoBuilde](https://sites.google.com/site/kadanutilities/home/logobuilder)

重点：快捷的dd命令

提取命令

dd if=logo.img skip=16384 count=6998454 of=1.bmp bs=1

填充命令

dd if=1.bmp of=logo.img seek=16384 count=6998454 bs=1
