ubnatu下运行QT遇到的问题

1、缺少头文件
error: GL/gl.h: No such file or directory
解决方式：sudo apt-get install mesa-common-dev

2、编译出现如下错误提示：
/usr/bin/ld: cannot find -lGL
解决方式：sudo apt-get install libgl1-mesa-dev libglu1-mesa-dev

3.切换到root用户 sudo su

4.

user@ubuntu:~$ apt-get install libgll-mesa-dev libglul-mesa-dev freeglut3-dev
E: Could not open lock file /var/lib/dpkg/lock - open (13: Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?
user@ubuntu:~$ sudo su
[sudo] password for user: 
root@ubuntu:/home/user# apt-get install libgll-mesa-dev libglul-mesa-dev freeglut3-dev
E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
root@ubuntu:/home/user# ps afx|grep apt
  4077 pts/0    S+     0:00          |                   \_ grep --color=auto apt
  1196 ?        Ss     0:00 /bin/sh /usr/lib/apt/apt.systemd.daily update
  1235 ?        S      0:00  \_ /bin/sh /usr/lib/apt/apt.systemd.daily lock_is_held update
  2765 ?        S      0:00          \_ /usr/lib/apt/methods/http
  2766 ?        S      0:01          \_ /usr/lib/apt/methods/http
root@ubuntu:/home/user# sudo kill -9 2765
root@ubuntu:/home/user# sudo kill -9 2766
root@ubuntu:/home/user# sudo kill -9 1235
