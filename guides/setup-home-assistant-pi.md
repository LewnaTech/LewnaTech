# 🏠 Install Home Assistant on a Raspberry Pi (Beginner Guide)

Welcome to the **Ultimate Beginner Guide** to installing **Home Assistant** on a **Raspberry Pi** — perfect for first-timers looking to build their smart home from the ground up.

---

## ✅ What You’ll Need

| Item | Purpose | Link |
|------|---------|------|
| **Raspberry Pi 4 (4GB or 8GB)** | The brains of the system | [Buy on Amazon](#your-affiliate-link) |
| **32GB+ MicroSD Card (Class 10)** | For the Home Assistant OS | [Buy on Amazon](#your-affiliate-link) |
| **MicroSD Card Reader** | For flashing the image on your PC/Mac | [Buy on Amazon](#your-affiliate-link) |
| **USB-C Power Supply (5V/3A min)** | Official or reliable 3rd party | [Buy on Amazon](#your-affiliate-link) |
| **PC or Mac** | To prepare the microSD card |
| **Wi-Fi or Ethernet Connection** | See Wi‑Fi setup below |
| (Optional) **Raspberry Pi Case + Heatsink/Fan** | For cooling and protection | [Buy on Amazon](#your-affiliate-link) |

---

## 📥 Step 1: Download & Flash Home Assistant OS

1. Go to the official Home Assistant site:  
   🔗 [https://www.home-assistant.io/installation/raspberrypi](https://www.home-assistant.io/installation/raspberrypi)

2. Download the `.img.xz` for **Raspberry Pi 4** (32-bit is fine for most users).

3. Install **Balena Etcher** on your PC/Mac:  
   🔗 [https://www.balena.io/etcher/](https://www.balena.io/etcher/)

4. Insert your **microSD card** using a card reader.

5. In Etcher:
   - Select the Home Assistant image
   - Choose your SD card
   - Click **Flash**

⏱ This may take a few minutes. Once complete, safely eject the card.

---

## 📶 Step 2: Set Up Wi‑Fi (Skip this step if using Ethernet)

> 🟡 **Skip this step if you're using a wired Ethernet connection.**

1. After flashing, **reinsert** the microSD card into your computer.
2. Open the **“boot”** partition of the card.
3. Create a new folder named:
   ```
   CONFIG
   ```
4. Inside `CONFIG`, create another folder named:
   ```
   network
   ```
5. Inside the `network` folder, create a file:
   ```
   my-network
   ```
   *(No file extension — not `.txt`!)*

6. Paste the following into `my-network`, replacing `YOUR_SSID` and `YOUR_PASSWORD`:

   ```ini
   [connection]
   id=my-network
   uuid=$(uuidgen)
   type=wifi

   [wifi]
   mode=infrastructure
   ssid=YOUR_SSID

   [wifi-security]
   auth-alg=open
   key-mgmt=wpa-psk
   psk=YOUR_PASSWORD

   [ipv4]
   method=auto

   [ipv6]
   method=auto
   ```

7. Save and eject the SD card safely.

---

## 🔌 Step 3: Boot Your Raspberry Pi

1. Insert the microSD card into your Pi.
2. Connect the **power supply**.
3. If using Ethernet, plug it in now.
4. Wait 5–10 minutes for the OS to finish setup.

Once ready, open a browser and go to:

```
http://homeassistant.local:8123
```

> If that doesn't work, find your Pi’s IP address from your router and go to:
```
http://<YOUR_PI_IP>:8123
```

---

## 🧭 Step 4: Complete the Home Assistant Setup

1. Create your admin account.
2. Set location, timezone, unit preferences.
3. Add integrations (e.g. Philips Hue, Spotify, Tesla, etc.)
4. Begin building your smart home automations!

---

## 🧰 Optional Accessories

| Item | Use | Link |
|------|-----|------|
| **USB SSD** | More reliable than microSD | [Buy on Amazon](#your-affiliate-link) |
| **Zigbee USB Stick (Sonoff/Zooz)** | Control Zigbee devices directly | [Buy on Amazon](#your-affiliate-link) |
| **Z-Wave USB Stick** | For Z-Wave smart gear | [Buy on Amazon](#your-affiliate-link) |
| **GPIO sensor modules** | For custom automations | [Buy on Amazon](#your-affiliate-link) |

---

## 💡 What To Do Next

- Explore integrations: [home-assistant.io/integrations](https://www.home-assistant.io/integrations/)
- Set up dashboards
- Create automations and scenes (e.g. motion lights, bedtime routine)
- Add the **Home Assistant mobile app** for presence detection and notifications

---

## ☕ Support  
If you find this useful, consider buying me a coffee:

[![Support LewnaTech](https://ko-fi.com/img/githubbutton_sm.svg)](https://ko-fi.com/lewnatech)
