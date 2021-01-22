# 写在前面
1.ndk-build 版本有要求 ，不能r21,r10e可以用

2.vim ~/.bashrc

# andorid ndk-build
# NDK_HOME必须和ndk的路径一致！
export NDK_HOME=/home/tianbo/下载/android-ndk-r21b
export PATH=$PATH:$NDK_HOME
# 友情链接
3.详细地址：https://www.lofter.com/lpost/1ede179c_1caed164d
		  https://developer.android.google.cn/ndk/downloads/
# 详细使用
The droid-VNC-server projects consists in three main modules parts: the daemon, wrapper libs and the GUI.

- Daemon -
Provides the vnc server functionality, injects input/touch events, clipboard management, etc
Available in jni/ folder

- Wrapper libs -
Compiled against the AOSP so everyone can build the daemon/GUI without having to fetch +2GB files.
Currently there are 2 wrappers, gralloc and flinger.

Available in nativeMethods/ folder, and precompiled libs in nativeMethods/lib/

- GUI - 
GUI handles user-friendly control.
Connects to the daemon using local IPC.

-------------- Compile C daemon ---------------------
On project folder:
  $ ndk-build
  $ ./updateExecsAndLibs.sh

-------------- Compile Wrapper libs -----------------
  $ cd <aosp_folder>
  $ . build/envsetup.sh
  $ lunch
  $ ln -s <droid-vnc-folder>/nativeMethods/ external/

To build:
  $ cd external/nativeMethods
  $ mm .
  $ cd <droid-vnc-folder>
  $ ./updateExecsAndLibs.sh

-------------- Compile GUI------- -------------------
Import using eclipse as a regular Android project
