# 05 — Defense & Mitigations

> Translating the attack chain into concrete defensive controls. This is the purpose of the project: understanding the attack to defeat it.

[← Previous: Conversion & Cracking](04-conversion-and-cracking.md) · [Back to README](../README.md) · [References →](references.md)

---

## How Each Phase Is Defeated

| Attack Phase | Weakness Exploited | Defensive Control |
|--------------|--------------------|-------------------|
| Reconnaissance | Beacons broadcast network metadata | Unavoidable by design — focus on hardening later phases |
| Deauthentication | Management frames are unauthenticated (WPA2) | **802.11w — Protected Management Frames (PMF)** |
| Handshake capture | 4-way handshake exposes crackable proof | **WPA3-SAE** (no offline-crackable handshake) |
| Offline cracking | Low-entropy passphrase | **Long, random passphrase** (16+ chars) |

---

## 1. Upgrade to WPA3 (SAE)

WPA3 replaces the PSK handshake with **SAE (Simultaneous Authentication of Equals / Dragonfly)**, a password-authenticated key exchange that provides **forward secrecy** and is **not vulnerable to offline dictionary attacks**. Even if an attacker captures the exchange, it cannot be brute-forced the way a WPA2 handshake can.

- Enable **WPA3-Personal**, or **WPA3/WPA2 transition mode** if legacy clients require it (noting transition mode partially reduces the benefit).

## 2. Enable 802.11w — Protected Management Frames (PMF)

PMF cryptographically protects deauthentication and disassociation frames, **neutralising the deauthentication attack** that this project relies on to force handshake replay. It is **mandatory in WPA3** and available as optional/required in many WPA2 routers.

- Set PMF to **Required** where all clients support it, or **Optional** for mixed fleets.

## 3. Use a High-Entropy Passphrase

WPA2's entire security budget is the passphrase. Because the PMK is derived via PBKDF2 (salted with the SSID), **entropy is the only defence against offline cracking**.

- Use **16+ characters**, randomly generated.
- Avoid dictionary words, names, dates, phone numbers, and keyboard patterns.
- A random passphrase pushes brute-force cost beyond any practical attacker's reach.

| Passphrase style | Resistance to offline cracking |
|------------------|-------------------------------|
| `password123` / dictionary word | ❌ Seconds–minutes |
| 8-digit number | ⚠️ Hours–days |
| 16+ random characters | ✅ Computationally infeasible |

## 4. Avoid Predictable / Default SSIDs

The SSID is used as the **salt** in PMK derivation. Common or default SSIDs (e.g. router-brand defaults) allow attackers to use **precomputed tables (PMK rainbow tables)**. Use a unique SSID.

## 5. Prefer Enterprise Authentication (802.1X) Where Feasible

For business environments, **WPA2/WPA3-Enterprise with 802.1X/RADIUS** issues per-user credentials and eliminates the shared-PSK weakness entirely.

## 6. Keep Firmware Updated

Router and client firmware updates patch RF-stack, driver, and protocol vulnerabilities. Enable automatic updates where available.

## 7. Monitor for Deauthentication Floods

A sudden burst of deauthentication/disassociation frames is a strong **indicator of compromise**. Wireless IDS/IPS (or even a monitoring AP) can alert on deauth anomalies, flagging an active attack in progress.

---

## Defender's Checklist

- [ ] WPA3-SAE enabled (or WPA2 with a strong passphrase as a minimum)
- [ ] 802.11w PMF set to Required/Optional
- [ ] Passphrase is 16+ random characters
- [ ] SSID is unique (not a vendor default)
- [ ] Router firmware is current
- [ ] Deauth-flood monitoring/alerting in place
- [ ] Enterprise 802.1X considered for business networks

➡️ See [**References**](references.md) for standards and tooling.
