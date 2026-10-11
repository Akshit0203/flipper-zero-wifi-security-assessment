# References

> Standards, tools, and further reading referenced throughout this project.

[← Back to README](../README.md)

---

## Standards & Protocols

- **IEEE 802.11i** — Robust Security Network (RSN) / WPA2 specification.
- **IEEE 802.11w** — Protected Management Frames (PMF).
- **WPA3 / SAE** — Wi-Fi Alliance WPA3 specification (Simultaneous Authentication of Equals).
- **RFC 2898 / PBKDF2** — Password-Based Key Derivation Function used to derive the PMK.
- **EAPOL** — Extensible Authentication Protocol over LAN (IEEE 802.1X).

## Firmware

- [Momentum Firmware](https://momentum-fw.dev/) — custom Flipper Zero firmware.
- [ESP32 Marauder — justcallmekoko](https://github.com/justcallmekoko/ESP32Marauder) — 802.11 recon & attack firmware for the ESP32.

## Flashing Tools

- [FZEE Flasher](https://flipper.ee/flash) — browser-based (WebSerial) ESP32 flasher.
- ESP Flasher — on-device Flipper Zero flashing application.
- [Silicon Labs CP210x VCP Drivers](https://www.silabs.com/developer-tools/usb-to-uart-bridge-vcp-drivers) — USB-to-UART bridge drivers.

## Capture Analysis & Cracking

- [hashcat](https://hashcat.net/hashcat/) — advanced password recovery.
- [hashcat — Cracking WPA/WPA2 (mode 22000)](https://hashcat.net/wiki/doku.php?id=cracking_wpawpa2) — official guidance.
- [hcxtools — ZerBea](https://github.com/ZerBea/hcxtools) — `hcxpcapngtool` and related capture utilities.
- [cap2hashcat](https://hashcat.net/cap2hashcat/) — online `.pcap`/`.cap` → `.22000` converter.
- [REDD's PCAP OHC Uploader — InfoSecREDD](https://github.com/InfoSecREDD) — OnlineHashCrack submission helper.
- [OnlineHashCrack](https://www.onlinehashcrack.com/) — online hash-cracking service.

## Analysis Tooling

- [Wireshark](https://www.wireshark.org/) — packet capture inspection and verification.

## Further Reading

- hashcat mode **22000** (WPA-PBKDF2-PMKID+EAPOL) format notes.
- PMKID clientless attack — original research by *atom* (hashcat), 2018.
- Wi-Fi Alliance — WPA3 security considerations and transition-mode guidance.

---

> ⚠️ All tools above are dual-use. Use them only against networks you own or are explicitly authorized to test. See [`DISCLAIMER.md`](../DISCLAIMER.md).
