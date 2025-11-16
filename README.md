
# Supported Vendors & Devices

| Vendor     | OLT Models Supported                                      | ONU/ONT Models Supported                              |
|------------|-----------------------------------------------------------|-------------------------------------------------------|
| **Huawei**    | MA5600T, MA5800, MA5680T, EA5800, EA5801, MA5800-X17/X15/X7 | HG8245H, HG8546M, EG8145V5, AN5506, HS8145V5, EG8141A5, etc. |

# GPON Troubleshooting Commands & Guides

Practical, field-tested GPON/EPON troubleshooting commands, hidden menus, recovery methods, and scripts for ISP technicians in Cambodia and worldwide.

Supported country-specific ISPs: Viettel, Metfone, Smart, Cellcard, CooTel, Sinfa Net, Digi, etc. (Cambodia focus)

## Supported Vendors
See complete list → [/vendors/supported-vendors.md](/vendors/supported-vendors.md)

## Quick Links
- Huawei OLT/ONU → [/huawei](https://github.com/kaoheng1515/Huawei-OLT-VSolution-Config)

## Most Used in Cambodia (2025)
| Task                      | Command (Huawei OLT)                        | Command (ZTE OLT)                          |
|---------------------------|---------------------------------------------|--------------------------------------------|
| Check ONU signal          | `display ont optical-info 0/3/0 all`        | `show gpon onu optics gpon-olt-1/1/1`      |
| Find offline ONUs         | `display ont info summary 0/3/0 | incl down`| `show pon offline-onu`                     |
| Reboot ONU                | `ont reset 0/3/0 15`                        | `onu reboot gpon-onu-1/1/1:15`             |
| Get PPPoE username        | `display ont wan-info 0/3/0 15 all`         | `show onu running config gpon-onu-1/1/1:15` |

More commands inside each vendor folder.

## Contributing
Very welcome! Especially:
- Metfone / Viettel Cambodia profiles
- Cellcard Nokia profiles
- New 2025 firmware hidden passwords

## License
MIT © 2025 – Free for commercial & personal use

 Cambodian ISP Technicians Community

 # Huawei GPON Troubleshooting

## OLT Common Commands (MA56xx/MA58xx/EA58xx)
```bash
display ont info summary 0/3/0
display ont optical-info 0/3/0 all
display ont wan-info 0/3/0 15 all
ont confirm 0/3/0 15
ont reset 0/3/0 15