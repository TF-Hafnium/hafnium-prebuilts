qemu-system-aarch64 6.0.0

``` shell
wget https://download.qemu.org/qemu-6.0.0.tar.xz
tar xf qemu-6.0.0.tar.xz
cd qemu-6.0.0
./configure --target-list=aarch64-softmmu --disable-gtk --disable-vnc --disable-sdl --disable-opengl --disable-vhost-net --disable-vhost-vsock --disable-vhost-user --disable-vhost-scsi --disable-vhost-crypto --disable-libxml2 --disable-libusb --disable-tpm --disable-kvm --disable-qom-cast-debug --disable-guest-agent --disable-replication --disable-live-block-migration --disable-blobs --audio-drv-list= --disable-xkbcommon --static
make -j64
strip aarch64-softmmu/qemu-system-aarch64
cp aarch64-softmmu/qemu-system-aarch64 ../hafnium/prebuilts/linux-x64/qemu/qemu-system-aarch64
```
