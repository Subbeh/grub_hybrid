### Associate a loop device with the image file
```
loop_device=$(sudo losetup --partscan --show --find boot.img)
```

### Mount
```
sudo mkdir /mnt/{efi,data}
sudo mount -o rw,umask=0000 "$loop_device"p2 /mnt/efi
sudo mount "$loop_device"p3 /mnt/data
```

### Test
```
qemu-system-x86_64 -enable-kvm -m 1G boot.img
```
