# Creating my first virtual machine: Windows server

**Initial Prep**

- Created the internal lab network w/ a Linux bridge; vmbr1
- Installed Windows Server 2025 Standard Evaluation ISO to local storage in Proxmox
- Created VM w/ installed server ISO

**VirtIO Setup**

- Emulating devices takes more time and processing power since the VM must pause completely to use the mini pc's hardware. Using VirtIO allows the VM and the mini pc to "share" the hardware resources, making performance faster and less CPU-intensive (especially when running multiple VMs)
- However, Windows does not include VirtIO drivers by default, so I installed them manually before setting up the Windows Server:
  1. Uploaded VirtIO drivers ISO to local storage in Proxmox (virtio-win-0.1.271.iso)
  2. Set disk controller to VirtIO SCSI single and network card to VirtIO
  3. During Windows install, loaded vioscsi storage driver from the VirtIO ISO
  4. Ran virtio-win-gt-x64: remaining drivers
  5. Ran virtio-win-guest-tools: QEMU guest agent, which allows Proxmox to view the VM server's IP and shut it down

**VM settings**

| Tab | Setting |
|---|---|
| **General** | Name: `DC01` |
| **OS** | Windows Server 2025 Standard Evaluation (Desktop Experience) |
| | Add additional drive for VirtIO drivers |
| **System** | Machine: `q35` |
| | BIOS: `OVMF (UEFI)` |
| | Add EFI Disk |
| | Add TPM |
| | SCSI Controller: `VirtIO SCSI single` |
| | QEMU Agent |
| **Disks** | Bus: `SCSI`, Size: `60 GB` |
| | Discard |
| | IO thread |
| **CPU** | `2` cores, type `x86-64-v3` |
| **Memory** | `4096 MB` |
| **Network** | Bridge: `vmbr1`, Model: `VirtIO` |
