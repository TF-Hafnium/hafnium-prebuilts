# Trusted Firmware-A

TF-A is built with command line options to include the SPMD (FF-A Secure Partition Manager
Dispatcher) into the BL31 image.
Additional options are provided to support SPMC running at EL3.
PIE and RESET_TO_BL31 options are used as test configurations don't assume BL1/BL2 bootloaders
usage.

Pick patches [1] and [2]

[1] https://review.trustedfirmware.org/c/TF-A/trusted-firmware-a/+/19740
[2] https://review.trustedfirmware.org/c/TF-A/trusted-firmware-a/+/20259/1

```
$ make CROSS_COMPILE=aarch64-none-elf- PLAT=fvp SPD=spmd		\
  ARM_SPMC_MANIFEST_DTS=plat/arm/board/fvp/fdts/fvp_tsp_sp_manifest.dts	\
  SPMC_AT_EL3=1 SPMD_SPM_AT_SEL2=0  PRELOADED_BL33_BASE=0x80000000	\
  ARM_LINUX_KERNEL_AS_BL33=1 ARM_PRELOADED_DTB_BASE=0x82000000		\
  FVP_HW_CONFIG_DTS=fdts/fvp-base-gicv3-psci-1t.dts RESET_TO_BL31=1	\
  BRANCH_PROTECTION=1  CTX_INCLUDE_PAUTH_REGS=1 ARM_ARCH_MINOR=5	\
  ENABLE_PIE=1 V=1 DEBUG=1 all fip -j8

$ cp build/fvp/debug/bl31.bin ../hafnium/prebuilts/linux-aarch64/trusted-firmware-a-el3-spmc/bl31.bin
$ cp build/fvp/debug/bl32.bin ../hafnium/prebuilts/linux-aarch64/trusted-firmware-a-el3-spmc/bl32.bin
$ cp build/fvp/debug/fdts/fvp_tsp_sp_manifest.dtb \
  ../hafnium/prebuilts/linux-aarch64/trusted-firmware-a-el3-spmc/fdts/fvp_tsp_sp_manifest.dtb
```
