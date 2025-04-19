# 🛡️ Home Network Security Hardening (2025)

> Hardened and optimized my home network after a forced ISP factory reset.  
> Focused on balancing **OPSEC**, **gaming performance**, **streaming stability**, and **long-term scalability** for future home lab expansions.

---

## 🔐 Configuration Overview

| Setting                     | Value / Status                          |
|-----------------------------|------------------------------------------|
| Gateway / Modem             | ARRIS (Liberty ISP)                     |
| DNS                         | Cloudflare (1.1.1.1 / 1.0.0.1)          |
| DHCP Range                  | 192.168.0.100 – 192.168.0.200           |
| Wi-Fi Encryption            | WPA2-PSK (AES) only (2.4GHz + 5GHz)     |
| IPv6                        | ❌ Disabled (WAN + LAN)                 |
| WPS                         | ❌ Disabled                             |
| UPnP                        | ✅ Enabled for Xbox only                |
| Remote Management           | ❌ Disabled (HTTP + HTTPS fully off)    |
| DDNS                        | ❌ Disabled                             |
| DMZ                         | ❌ Disabled                             |
| Admin Access                | LAN only (no WAN access)               |
| ProtonVPN                   | Used on public Wi-Fi only              |

---

## 🧱 Firewall & ALG Configuration

- ✅ **Firewall Enabled** with DoS protection and ICMP blocking  
- ✅ **Block Fragmented IP Packets**  
- ✅ **IPSec & L2TP Passthrough** ON (for VPN compatibility)  
- ✅ **ALG: Only SIP + IKE enabled** for FaceTime & VPN  
- ❌ **All other ALGs (FTP, TFTP, PPTP, IRC, etc.) disabled**  

---

## 📶 Wi-Fi Settings

### 2.4GHz
- SSID: `<Private_2.4GHz_SSID>`
- Security: WPA2-PSK (AES)
- Channel: Manual (1 / 6 / 11)
- Bandwidth: 20MHz
- TX Power: High

### 5GHz
- SSID: `<Private_5GHz_SSID>`
- Security: WPA2-PSK (AES)
- Channel: Manual (DFS-free range)
- Bandwidth: 40–80MHz
- TX Power: High

---

## 🧠 Security Notes

- Cleaned and re-secured repeater with WPA2-AES, static IP, and WPS off  
- Set static IPs for repeater and Xbox to maintain UPnP consistency  
- Admin credentials changed and stored offline  
- All changes exported as `.bin` config backup post-hardening  
- Verified stealth mode with ping blocks, no open ports, no remote access  

---

## 🔮 Future Additions & Home Lab Goals

- ✅ MAC address whitelisting  
- ✅ Guest Wi-Fi with isolation  
- ✅ Self-hosted VPN (OpenVPN / WireGuard)  
- ✅ Parental controls & URL filtering via DNS  
- ✅ Ethical Wi-Fi testing after earning networking certifications  
- ✅ VLAN segmentation for IoT + guest devices  
- ✅ Deploy IDS/IPS for live monitoring & packet inspection  
- ✅ Launch local NAS and/or Plex server  
- ✅ Backup config auto-versioned into GitHub (private repo)

---

📁 Full configuration log & recovery file:  
`Yeray_Router_Config_Apr19_2025.bin`

_Last updated: April 19, 2025_
