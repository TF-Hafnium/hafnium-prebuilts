We are currently using the
[Trusty fork of trusted-firmware-a](https://android.googlesource.com/trusty/external/trusted-firmware-a/),
because we depend on the Trusty SPD. We can go back to using the upstream
version once the Trusty SPD FF-A patches are upstreamed.

trusted-firmware-a was built with the following commands:

```
$ make CROSS_COMPILE=aarch64-none-elf- PLAT=fvp FVP_HW_CONFIG_DTS=fdts/fvp-base-gicv3-psci-1t.dts PRELOADED_BL33_BASE=0x80000000 ARM_LINUX_KERNEL_AS_BL33=1 ARM_PRELOADED_DTB_BASE=0x82000000 RESET_TO_BL31=1 ENABLE_PIE=1 V=1 all fip -j16
$ make CROSS_COMPILE=aarch64-none-elf- PLAT=rpi4 -j16
$ make CROSS_COMPILE=aarch64-none-elf- PLAT=qemu ENABLE_SVE_FOR_NS=1 QEMU_USE_GIC_DRIVER=QEMU_GICV3 ARM_LINUX_KERNEL_AS_BL33=1 SPD=trusty TRUSTY_SPD_WITH_GENERIC_SERVICES=1 V=1 all -j16
$ cp build/fvp/release/bl31.bin ../hafnium/prebuilts/linux-aarch64/trusted-firmware-a-trusty/fvp/bl31.bin
$ cp build/rpi4/release/bl31.bin ../hafnium/prebuilts/linux-aarch64/trusted-firmware-a-trusty/rpi4/bl31.bin
$ cp build/qemu/release/bl1.bin ../hafnium/prebuilts/linux-aarch64/trusted-firmware-a-trusty/qemu/bl1.bin
$ cp build/qemu/release/bl2.bin ../hafnium/prebuilts/linux-aarch64/trusted-firmware-a-trusty/qemu/bl2.bin
$ cp build/qemu/release/bl31.bin ../hafnium/prebuilts/linux-aarch64/trusted-firmware-a-trusty/qemu/bl31.bin
$ touch ../hafnium/prebuilts/linux-aarch64/trusted-firmware-a-trusty/qemu/bl32.bin
$ cp docs/license.rst ../hafnium/prebuilts/linux-aarch64/trusted-firmware-a-trusty/LICENSE
$ dtc -I dtb -O dts build/fvp/release/fdts/fvp-base-gicv3-psci-1t.dtb -o ../hafnium/prebuilts/linux-aarch64/trusted-firmware-a-trusty/fvp/fvp-base-gicv3-psci-1t.dts
```

Note that `qemu/bl32.bin` is an empty file. This is enough to get the Trusty SPD
to boot. It gives an error, but this can be ignored as we don't actually try to
call into Trusty itself.
