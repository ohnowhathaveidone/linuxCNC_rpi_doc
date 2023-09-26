# setting up linuxCNC on a raspberry pi 4
this is work in progress. 

## specs
raspi: model 4, 8GB ram -> OS: arch linux  
host: 10 year old laptop -> OS: gentoo

## get base operating system (raspi)
this works very well and should set you up with a 64 bit operating system:  
https://archlinuxarm.org/platforms/armv8/broadcom/raspberry-pi-4 

## cross compile kernel
get crossdev on gentoo:  
https://wiki.gentoo.org/wiki/Embedded_Handbook/General/Creating_a_cross-compiler 
install arm64 toolcain:   
´´´crossdev --target aarch64´´´
this will provide you with ´´´aarch64-unknown-linux-gnu´´´ -> adjust the compiler name in the build script  

## load arch linux on raspi

## useful links
arch RT kernel: https://wiki.archlinux.org/title/Realtime_kernel_patchset   
comfile rt kernel compilation: http://comfilewiki.co.kr/en/doku.php?id=comfilepi:compile_a_real-time_kernel:index   
gentoo crossdev: https://wiki.gentoo.org/wiki/Embedded_Handbook/General/Creating_a_cross-compiler  
arch arm project setup raspi: https://archlinuxarm.org/platforms/armv8/broadcom/raspberry-pi-4   

