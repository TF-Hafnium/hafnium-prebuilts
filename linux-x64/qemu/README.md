qemu-system-aarch64 7.1.0

``` shell
wget https://download.qemu.org/qemu-7.1.0.tar.xz
tar xf qemu-6.0.0.tar.xz
cd qemu-7.1.0
./configure --target-list=aarch64-softmmu --disable-gtk --disable-vnc --disable-sdl --disable-opengl --disable-vhost-net --disable-vhost-user --disable-vhost-crypto --disable-libusb --disable-tpm --disable-kvm --disable-qom-cast-debug --disable-guest-agent --disable-replication --disable-live-block-migration --disable-blobs --audio-drv-list= --disable-xkbcommon --static --disable-alsa --disable-bochs --disable-bpf --disable-brlapi --disable-bzip2 --disable-canokey --disable-cap-ng --disable-capstone --disable-cloop --disable-cocoa --disable-coreaudio --disable-crypto-afalg --disable-dsound --disable-guest-agent-msi --disable-jack --disable-l2tpv3 --disable-libdaxctl --disable-libiscsi --disable-libnfs --disable-libvduse --disable-linux-aio --disable-linux-io-uring --disable-lzfse --disable-lzo --disable-netmap --disable-nettle --disable-numa --disable-oss --disable-pa --disable-parallels --disable-png --disable-pvrdma --disable-qcow1 --disable-qed --disable-qga-vss --disable-rbd --disable-rdma --disable-seccomp --disable-selinux --disable-slirp-smbd --disable-smartcard --disable-snappy --disable-sparse --disable-spice --disable-spice-protocol --disable-sdl-image --disable-vte --disable-hax --disable-hvf --disable-whpx --disable-nvmm --disable-vhost-kernel --disable-vhost-user-blk-server --disable-vhost-vdpa --disable-virglrenderer --disable-u2f --disable-usb-redir --disable-vde --disable-vfio-user-server --disable-vduse-blk-export --disable-vnc-jpeg --disable-vnc-sasl --disable-zstd
make -j64
strip aarch64-softmmu/qemu-system-aarch64
cp aarch64-softmmu/qemu-system-aarch64 ../hafnium/prebuilts/linux-x64/qemu/qemu-system-aarch64
```
