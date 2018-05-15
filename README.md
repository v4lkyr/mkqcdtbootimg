mkqcdtbootimg
=============

Copyright 2007, The Android Open Source Project  
Copyright (c) 2012, The Linux Foundation. All rights reserved.  
Copyright (c) 2013, Sony Mobile Communications AB  

mkqcdtbootimg is an extended version of the Android mkbootimg tool, found at [android.googlesource.com][]. It adds support for including one or more device tree blobs in a `QC table of device tree`, as specified in `dtbtool.txt`.

The added command line option is `--dt_dir` which takes a path that will be searched for dtb files.


Recommended usage is to add the following to your `BoardConfig.mk` and then build Android as normal
```
BOARD_CUSTOM_MKBOOTIMG := mkqcdtbootimg
BOARD_MKBOOTIMG_ARGS += --dt_dir device/x/y/dtbs
```

 [android.googlesource.com]: https://android.googlesource.com/platform/system/core/+/master/mkbootimg/

String for Xperia Z2:

./mkqcdtbootimg --kernel $(KERNEL_SRC_PATH)/arch/arm/boot/zImage --ramdisk ramdisk.cpio.gz --base 0x00000000 --ramdisk_offset 0x02000000 --tags_offset 0x01E00000 --pagesize 2048 --cmdline "androidboot.hardware=qcom user_debug=31 msm_rtb.filter=0x37 ehci-hcd.park=3 dwc3.maximum_speed=high dwc3_msm.prop_chg_detect=Y" --dt_dir $(KERNEL_SRC_PATH)/arch/arm/boot/ --dt_version 2 -o boot.img

RR

./mkqcdtbootimg --kernel $(KERNEL_SRC_PATH)/arch/arm/boot/zImage --ramdisk ramdisk.cpio.gz --base 0x00000000 --ramdisk_offset 0x02000000 --tags_offset 0x01E00000 --pagesize 2048 --cmdline "androidboot.hardware=qcom msm_rtb.filter=0x3b7 ehci-hcd.park=3 dwc3.maximum_speed=high dwc3_msm.prop_chg_detect=Y androidboot.selinux=permissive buildvariant=userdebug vmalloc=512M" --dt_dir $(KERNEL_SRC_PATH)/arch/arm/boot/ --dt_version 2 -o boot.img
