# 💡 Room Presence Lighting (Timer Delay)

Automatically turns a light on when room presence is detected, and off after X seconds of absence.  
Designed to work with Adaptive Lighting for a natural ambient feel.

---

## 🎥 Sample
<p align="left">
      <img src="https://i.imgur.com/1bdGfEe.gif" width="300" height="300">
      </p>

## 🔧 Requirements

- Home Assistant set up and running ([Setup Guide](https://www.home-assistant.io/getting-started/))
- [Adaptive Lighting integration](https://github.com/basnijholt/adaptive-lighting) **(Optional)**
- Presence sensor (e.g. [Aqara FP2 – Amazon Affiliate](https://amzn.to/45pg5qV))
- Light entity (e.g. smart downlights)
- [![Support LewnaTech](https://ko-fi.com/img/githubbutton_sm.svg)](https://ko-fi.com/lewnatech)

---

## 🧾 YAML Code

> ⚠️ **IMPORTANT**: Replace all placeholders (in CAPS) with your own Home Assistant entity IDs before saving.

```yaml
alias: Room Presence Lighting (Adaptive Lighting, Timer Off Delay)
trigger:
  - platform: state
    entity_id: BINARY_SENSOR.ROOM_OCCUPANCY
    to: "on"
  - platform: state
    entity_id: BINARY_SENSOR.ROOM_OCCUPANCY
    to: "off"
action:
  - choose:
      - conditions:
          - condition: state
            entity_id: BINARY_SENSOR.ROOM_OCCUPANCY
            state: "on"
        sequence:
          - service: light.turn_on
            target:
              entity_id: LIGHT.ROOM_LIGHT
            data: {}
      - conditions:
          - condition: state
            entity_id: BINARY_SENSOR.ROOM_OCCUPANCY
            state: "off"
        sequence:
          - wait_for_trigger:
              - platform: state
                entity_id: BINARY_SENSOR.ROOM_OCCUPANCY
                to: "on"
            timeout: "00:00:10" # adjust timeout if needed
            continue_on_timeout: true
          - condition: state
            entity_id: BINARY_SENSOR.ROOM_OCCUPANCY
            state: "off"
          - service: light.turn_off
            target:
              entity_id: LIGHT.ROOM_LIGHT
            data: {}
mode: restart
```

---

## 🛠️ Step-by-Step Installation

1. Click **Settings** in Home Assistant
- <details>
      <summary>Show GIF demo</summary>
      <p align="left">
      <img src="https://i.imgur.com/bq2St4B.gif" width="300" height="300">
      </p>
      </details>

3. Click **Automations & Scenes** → **Automations**  
- <details>
      <summary>Show GIF demo</summary>
      <p align="left">
      <img src="https://i.imgur.com/40ijoX0.gif" width="300" height="300">
      </p>
      </details>

5. Click **+ Create Automation**  
- <details>
      <summary>Show GIF demo</summary>
      <p align="left">
      <img src="https://i.imgur.com/RQsahkN.gif" width="300" height="300">
      </p>
      </details>

6. Select **Start with an empty automation**  
- <details>
      <summary>Show GIF demo</summary>
      <p align="left">
      <img src="https://i.imgur.com/86i35Gs.gif" width="300" height="300">
      </p>
      </details>

7. Click the **three-dot menu** (⋮) in the top-right corner and choose **Edit in YAML**  
- <details>
      <summary>Show GIF demo</summary>
      <p align="left">
      <img src="https://i.imgur.com/AmrddUY.gif" width="300" height="300">
      </p>
      </details>

8. Paste the YAML code above into the editor **(Remove sample code)** 
- <details>
      <summary>Show GIF demo</summary>
      <p align="left">
      <img src="https://i.imgur.com/GyaA2AT.gif" width="300" height="300">
      </p>
      </details>

9. Replace **ALL** placeholders (in CAPS) with your own Home Assistant entity IDs before saving  
- <details>
      <summary>Show GIF demo</summary>
      <p align="left">
      <img src="https://i.imgur.com/KhMXyIP.gif" width="300" height="300">
      </p>
      </details>
 
10. Click **Save**, give your automation a name, and you’re done! 
- <details>
      <summary>Show GIF demo</summary>
      <p align="left">
      <img src="https://i.imgur.com/vgJctMW.gif" width="300" height="300">
      </p>
      </details>
      
---

🆕 More automations added regularly — [Follow on GitHub](https://github.com/LewnaTech/LewnaTech) for updates!

[![Support LewnaTech](https://ko-fi.com/img/githubbutton_sm.svg)](https://ko-fi.com/lewnatech)
