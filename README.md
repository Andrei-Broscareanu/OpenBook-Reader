# 📖 eBook Reader Portabil – ESP32-C6 Edition

Un eBook Reader cu consum redus, afișaj E-Ink și conectivitate modernă (Wi-Fi 6 & Bluetooth 5), construit în jurul microcontrollerului **ESP32-C6-WROOM-1-N8**.

---

## 🔧 Arhitectură Hardware

### 🧠 Microcontroller
- **ESP32-C6-WROOM-1-N8**
  - RISC-V core
  - Wi-Fi 6 și Bluetooth 5
  - Criptografie hardware integrată
  - Interfețe: SPI, I2C, GPIO

### 💾 Memorie
- **64MB NOR Flash** – W25Q512JVEIQ, conectată prin SPI
- **Slot microSD** – pentru stocare eBooks, conectat pe SPI separat

### 🔋 Alimentare
- **USB-C (PMF0501)** – intrare standard 5V
- **Protecție ESD (USBLC6-2SC6Y)** – pentru liniile USB
- **Încărcător Li-Po (MCP73831)** – pentru o celulă 3.7V, max 500mA
- **Baterie Li-Po 3.7V** – autonomie extinsă
- **Regulator LDO (MCP1700-3302E)** – convertește 5V la 3.3V

---

## 🖼️ Afișaj E-Ink

- Conector pentru ecrane de **1.54" E-Paper (200x200px)**
- Interfață: **SPI + GPIO**
- Circuit de alimentare:
  - Transistor Q3
  - Inductor L1
  - Diodă D2
- **Selector SJ1** – pentru tipul de display

---

## 📦 Periferice & Senzori

| Componentă        | Funcție                                | Interfață | Pini ESP32-C6         |
|-------------------|-----------------------------------------|-----------|------------------------|
| **BME688**        | Temperatură, umiditate, presiune, VOCs | I2C       | GPIO1 (SDA), GPIO2 (SCL) |
| **DS3231SN**      | RTC – ceas timp real                   | I2C       | GPIO1 (SDA), GPIO2 (SCL) |
| **MAX17048G-T10** | Fuel gauge baterie                     | I2C       | GPIO1 (SDA), GPIO2 (SCL) |
| **Buton Reset**   | Sistem reset                           | GPIO      | GPIO0                  |
| **Buton Boot**    | Bootloader                             | GPIO      | GPIO3                  |
| **Qwiic/Stemma QT**| Extensii rapide I2C                   | I2C       | GPIO1 (SDA), GPIO2 (SCL) |

---

## 🔌 Pini utilizați pe ESP32-C6

| Componentă       | Interfață     | Pini ESP32-C6             | Observații                |
|------------------|---------------|---------------------------|---------------------------|
| SD Card          | SPI           | GPIO10, GPIO11, GPIO12, GPIO13 | Bus SPI dedicat         |
| NOR Flash        | SPI           | GPIO6, GPIO7, GPIO8, GPIO9      | Bus SPI separat         |
| E-Ink Display    | SPI + GPIO    | GPIO18, GPIO19, GPIO20, GPIO21 | Control ecran           |
| Senzori + RTC    | I2C           | GPIO1 (SDA), GPIO2 (SCL)        | Comun I2C               |
| Butoane sistem   | GPIO          | GPIO0 (RST), GPIO3 (BOOT)       | Control utilizator      |
| Test Pads        | GPIO/UART     | GPIO17, GPIO22                   | Debug/UART              |

---

## ⚡ Estimare consum de energie

| Modul                    | Consum aproximativ         |
|--------------------------|----------------------------|
| ESP32-C6 activ           | ~80-100 mA                 |
| ESP32-C6 deep sleep      | ~10 µA                     |
| E-Ink refresh            | ~25 mA (temporar)          |
| SD Card idle / acces     | ~2 mA / ~50 mA             |
| RTC + BME688 standby     | ~3-5 µA                    |
| MAX17048                 | ~3 µA                      |

**Autonomie estimată cu baterie Li-Po 500mAh:**
- Utilizare normală: **15-20 ore**
- Standby (deep sleep): **până la câteva săptămâni**

---

## 🧩 Design PCB și carcasă

- Blocuri separate: alimentare, MCU, afișaj, senzori
- Plan de masă comun și trasee optimizate
- Conectori accesibili extern (USB, afisaj, butoane)
- Carcasă 3D ergonomică și compactă
- Randări 3D disponibile

---

## ✅ Status proiect

- [x] Hardware complet funcțional
- [x] PCB finalizat și validat
- [x] Carcasă 3D completă
- [x] Optimizare consum energetic
- [x] Conectivitate Wi-Fi 6 și Bluetooth 5

---
