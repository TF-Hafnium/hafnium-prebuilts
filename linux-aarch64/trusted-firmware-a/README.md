# FF-A Secure Partition Manager (SPMD/BL31)

We also use trusted-firmware-a from [TrustedFirmware.org](https://git.trustedfirmware.org/TF-A/trusted-firmware-a.git/), because we depend on SPMD implementation to run Hafnium as SPMC.

trusted-firmware-a was built, to generate 'bl31_spmd.bin', with the following commands:

```
$ make CROSS_COMPILE=aarch64-none-elf- SPD=spmd CTX_INCLUDE_MTE_REGS=1 CTX_INCLUDE_EL2_REGS=1 ARM_ARCH_MINOR=5 BRANCH_PROTECTION=1 CTX_INCLUDE_PAUTH_REGS=1 PLAT=fvp SP_LAYOUT_FILE=dummy RESET_TO_BL31=1 ARM_LINUX_KERNEL_AS_BL33=1 PRELOADED_BL33_BASE=0x88000000 ARM_PRELOADED_DTB_BASE=0x82000000 -j8
$ cp build/fvp/release/bl31.bin ../hafnium/prebuilts/linux-aarch64/trusted-firmware-a/fvp/bl31_spmd.bin
```
