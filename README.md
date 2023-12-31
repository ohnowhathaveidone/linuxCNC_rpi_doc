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
`crossdev --target aarch64`
this will provide you with `aarch64-unknown-linux-gnu` -> adjust the compiler name in the build script  
at the time of writing this, the kernel version in comfile's build script is not the latest stable RT kernel. you may want to adjust the version.
the latest stable kernel ca be found at https://git.kernel.org/pub/scm/linux/kernel/git/rt/linux-stable-rt.git  

## load arch linux on raspi
follow comfile's instructions to load the newly compiled kernel on your raspi.  
it seems that upgrades via pacman will pull a new kernel, however this will not actually change anything to the kernel. uname still reports an RT kernel after the upgrade.  
this may cause issues. i'm keeping this for reference: https://www.digitalocean.com/community/tutorials/pacman-syu-kernel-update-solved-how-to-ignore-arch-kernel-upgrades  

## performance upgrades  
the default cpu governor behavior seems to be set to powersave or ondemand. to permanently change to performance, install cpupower, edit the defalt behavior `/etc/default/cpupower`to 'performance' and enable the service.  
comfile has another tweak that will allow you to keep one cpu core free for a task: http://comfilewiki.co.kr/en/doku.php?id=comfilepi:improving_real-time_performance:index  
i'm still looking into this. but from what i understand, linuxCNC uses only one core anyway. so this should work.  

## useful links (tl;dr)
arch arm project setup raspi: https://archlinuxarm.org/platforms/armv8/broadcom/raspberry-pi-4 - set up a base system on the raspi  
comfile rt kernel compilation: http://comfilewiki.co.kr/en/doku.php?id=comfilepi:compile_a_real-time_kernel:index - compile an rt kernel on your host machine  
comfile performance tweaks: http://comfilewiki.co.kr/en/doku.php?id=comfilepi:improving_real-time_performance:index - get cpupower running first
gentoo crossdev: https://wiki.gentoo.org/wiki/Embedded_Handbook/General/Creating_a_cross-compiler - get toolchain for cross compilation  
RT kernel repo: https://git.kernel.org/pub/scm/linux/kernel/git/rt/linux-stable-rt.git - get repo for latest RT kernel  
arch RT kernel docs: https://wiki.archlinux.org/title/Realtime_kernel_patchset - kernel testing  
