# Trusted Firmware-A

TF-A is built with command line options to include the SPMD (FF-A Secure Partition Manager Dispatcher) into the BL31 image.
Additional options are provided to support Hafnium/SPMC running at S-EL2.
PIE and RESET_TO_BL31 options are used as test configurations don't assume BL1/BL2 bootloaders usage.

```
$ make CROSS_COMPILE=aarch64-none-elf- SPD=spmd CTX_INCLUDE_MTE_REGS=1 CTX_INCLUDE_EL2_REGS=1 ARM_ARCH_MINOR=5 BRANCH_PROTECTION=1 CTX_INCLUDE_PAUTH_REGS=1 PLAT=fvp SP_LAYOUT_FILE=dummy RESET_TO_BL31=1 ARM_LINUX_KERNEL_AS_BL33=1 PRELOADED_BL33_BASE=0x88000000 ARM_PRELOADED_DTB_BASE=0x82000000 GIC_EXT_INTID=1 PLAT_TEST_SPM=1 -j8
$ cp build/fvp/release/bl31.bin ../hafnium/prebuilts/linux-aarch64/trusted-firmware-a-spmd/fvp/bl31.bin
```
