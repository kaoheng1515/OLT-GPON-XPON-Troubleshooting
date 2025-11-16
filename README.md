![GitHub](https://img.shields.io/github/license/kaoheng1515/OLT-GPON-XPON-Troubleshooting?style=flat)
![GitHub last commit](https://img.shields.io/github/last-commit/kaoheng1515/OLT-GPON-XPON-Troubleshooting?style=flat)
![ViewCount](https://views.whatilearened.today/views/github/kaoheng1515/OLT-GPON-XPON-Troubleshooting.svg?cache=remove)
# Supported Vendors & Devices

| Vendor     | OLT Models Supported                                      | ONU/ONT Models Supported                              |
|------------|-----------------------------------------------------------|-------------------------------------------------------|
| **Huawei**    | MA5600T, MA5800, MA5680T, EA5800, EA5801, MA5800-X17/X15/X7 | HG8245H, HG8546M, EG8145V5, AN5506, HS8145V5, EG8141A5, etc. |

# GPON Troubleshooting Commands & Guides
## Quick Links
- Huawei OLT/ONU → [/huawei](https://github.com/kaoheng1515/Huawei-OLT-VSolution-Config)
## Most Used in Cambodia (2025)
| Task                      | Command (Huawei OLT)                        | Command (ZTE OLT)                          |
|---------------------------|---------------------------------------------|--------------------------------------------|
| Check ONU signal          | `display ont optical-info 0/3/0 all`        | `show gpon onu optics gpon-olt-1/1/1`      |
| Find offline ONUs         | `display ont info summary 0/3/0 | incl down`| `show pon offline-onu`                     |
| Reboot ONU                | `ont reset 0/3/0 15`                        | `onu reboot gpon-onu-1/1/1:15`             |
| Get PPPoE username        | `display ont wan-info 0/3/0 15 all`         | `show onu running config gpon-onu-1/1/1:15` |

### 1. Check OLT Board & Port Status
```bash
display board 0                     # All boards status
display board 0/0                   # Specific slot
display port state 0/0/0            # GPON port status (online/offline/LOS)
display port optical 0/0/0          # OLT-side optical module info
```

### 2. ONU Discovery & Registration Issues
```bash
display ont autofind all            # All discovered but not confirmed ONUs
display ont autofind 0/0/0          # Per specific port
display ont failed-register all     # ONUs that failed registration

# Clean pending autofind (optional)
delete ont autofind 0/0/0 time 2025-11-17
```

### 3. ONU Status & Basic Info
```bash
display ont info 0 0 0              # Summary (Run state, SN, Description)
display ont info 0/0/0 all          # All ONUs on one port
display ont version 0 0 0           # ONU firmware version
display ont capability 0 0 0        # Supported ports (ETH/POTS/WiFi/CATV)
```
### 4. Optical Power Problems (99% of Cambodia issues)
```bash
display ont optical-info 0 0 0      # Rx/Tx power, temp, voltage, bias
display ont optical-info 0/0/0 all

# Quick summary for whole PON port
display ont optical-info summary 0/0/0

# Acceptable values (Class C+)
# ONU Rx power: −28 dBm to −8 dBm
# ONU Tx power: +0.5 dBm to +5 dBm
```
### 5. ONU Keeps Going Offline (LOSi / LOFi / Dying Gasp)
```bash
display alarm active
display alarm history | include LOSi|LOFi|Dying
display ont dying-gasp 0/0/0 all
display ont alarm 0 0 0
```

### 6. Service / Internet Not Working (ONU Online but No Internet)
```bash
display service-port vlan 100
display service-port ont 0 0 0
display ont port vlan 0 0 0 eth 1   # Check native VLAN
ping ont 0 0 0 ip 192.168.1.100     # Ping customer device directly
display mac-address vlan 100
```

### 7. Bandwidth / Speed Issues
```bash
display dba-profile profile-id 10
display tcont 0 0 0
display ont statistics 0 0 0 eth 1  # Real-time traffic counters
```

### 8. Reboot / Reset ONU
```bash
ont reset 0 0 0                     # Soft reset
ont reboot 0 0 0                    # Hard reboot (power cycle)
```
### 9. Delete Problematic ONU (Start Fresh)
```bash
ont delete 0 0 0
delete ont autofind 0/0/0 all       # Clean pending first
```

### 10. Quick One-Liner Health Check (Copy-Paste in Field)
```bash
display board 0; display port state all; display ont info summary all; display ont optical-info summary all
```

### 11. Log & History Commands
```bash
display log all
display logbuffer
display alarm active
display alarm history
```

### 12. Export ONU List with Optical Power (For Reports)
```bash
display ont info summary all > flash:/onu_list.txt
display ont optical-info all > flash:/onu_optical.txt
```

## Contributing
Very welcome! Especially:
- Metfone / Viettel Cambodia profiles
- Cellcard Nokia profiles
- New 2025 firmware hidden passwords

## License
MIT © 2025 – Free for commercial & personal use

 Cambodian ISP Technicians Community