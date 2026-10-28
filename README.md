# Active Directory Attack & Detection Lab

A virtualized Active Directory environment, built as a simulated company inside a home lab server, for practicing identity attacks and building detections in Splunk.

## Why I Built This

I worked with Active Directory during a past internship and wanted to expand that experience while getting more comfortable with core networking concepts. To do that, I'm building a small company from scratch inside a home lab server so I can set up, break, and defend a realistic environment.

## Status

- [x] Mini PC set up as a dedicated host, RAM upgraded to 24GB
- [x] Proxmox VE installed
- [x] Secure remote access via Tailscale
- [x] Internal-only lab network (`vmbr1`)
- [x] First VM: Windows Server 2025 (`DC01`) installed with VirtIO drivers and renamed
- [ ] Promote `DC01` to a domain controller
- [ ] Windows 11 client joined to the domain
- [ ] Proxmox hardening (2FA, non-root user)
- [ ] OPNsense firewall
- [ ] Logging (Sysmon + Splunk)
- [ ] Attack simulation & detections

## Hardware

| Component | Spec |
|---|---|
| Host | Lenovo ThinkCentre M710q (mini PC) |
| RAM | 24GB |
| Storage | 256GB |

## Tech Stack

- **Virtualization:** Proxmox VE
- **Remote access:** Tailscale
- **Server OS:** Windows Server 2025 (Desktop Experience)
- **Drivers:** VirtIO (storage, network, guest agent)

## Write-ups

1. Proxmox Setup *(`docs/proxmox-setup.md`)*
2. Windows Server / DC01 Setup *(`docs/windows-server-setup.md`)*
