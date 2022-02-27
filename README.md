# single-gpu-passthrough
This is a tutorial for me to follow when I "forget" how to do Single GPU Passthrough using libvirt and qemu.

If anybody else stumbles upon this tutorial, make note: I have an **AMD RX560 GPU** and that's the only GPU I describe using this tutorial. Your mileage may vary.

### Kernel parameters
The following kernel parameters need to be enabled: `amd_iommu=on iommu=pt video=efifb:off`.

If using **systemd-boot**, as I did when writing this tutorial, just add this to `/boot/loader/entries/arch*.conf`:

`options root="LABEL=arch_os" rw amd_iommu=on iommu=pt video=efifb:off`

### TODO
Maybe create a script that does all the stuff mentioned above automatically. Include all necessary files in repositoy.

The script should:
- Configure GPU for single passhtrough
- Add a script to attach the given USB port to the virtual machine
- Automatically create a valid Windows 10 qemu configuration from a template file
- Download and place the **stable** virtio drivers: https://fedorapeople.org/groups/virt/virtio-win/direct-downloads/stable-virtio/virtio-win.iso
- etc.