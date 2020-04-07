# FusionCompute 6.5.1 – VM Agent Installation in SLES 15

We've found vm-agent not running on newly installed SLES 15 (SUSE Linux Enterprise Server 15) - FusionCompute 6.5.1 after installed VM Tools.

Issue was, a conflict with Qemu-guest-agent which is came up with SLES 15 version.

So, we've found some workaround solution to fix this issue, the details are as follows.


1. **Uninstall qemu-guest-agent**

	
- [x] Open Yast --> Software manager 
- [x] Remove qemu-guest-agent


2. Install vm-tools for SLES 

Open terminal (Suppose /dev/sr0 as a mounted drive which is having vm-tools-* )
```
$ mkdir /root/xvdd
$ mount  /dev/sr0 /root/xvdd   
$ cd /root/xvdd
$ cp vmtools-for-suse11sp3-x86_64-2.5.0.142.tar.bz2 /root
$ cd /root
$ tar –xjvf vmtools-for-suse11sp3-x86_64-2.5.0.142.tar.bz2
$ cd vmtools
$ ./install
$ service vm-agent status
```


3. Check vm-agent started successfully by running 

`$ sudo service vm-agent status`


4. Install qemu-guest-agent 

- [x] Open Yast --> Software manager
- [x] Install qemu-guest-agent


5. Restart vm-agent 

`$ sudo vm-agent restart`

6. Check the service is up and running.


Author: [Manoj Mohanan](mail-to:manojmohanan.kollam@gmail.com) - [Devexpat](https://devexpat.com) - [Phpremedy](https://phpremedy.com)


*END*
