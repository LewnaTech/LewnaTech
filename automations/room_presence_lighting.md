# 💡 Room Presence Lighting (Timer Delay)

Automatically turns a light on when room presence is detected, and off after X seconds of absence.  
Designed to work with Adaptive Lighting for a natural ambient feel.

---

## 🔧 Requirements

- Home Assistant set up and running ([Setup Guide](https://www.home-assistant.io/getting-started/))
- [Adaptive Lighting integration](https://github.com/basnijholt/adaptive-lighting) **(Optional)**
- Presence sensor (e.g. [Aqara FP2 – Amazon Affiliate](https://www.amazon.co.uk/s?k=Aqara+FP2&tag=YOUR_TAG))
- Light entity (e.g. smart downlights)
- [![Support LewnaTech](https://ko-fi.com/img/githubbutton_sm.svg)](https://ko-fi.com/lewnatech)

---

## 🧾 YAML Code

> ⚠️ **IMPORTANT**: Replace all placeholders (in CAPS) with your own Home Assistant entity IDs before saving.

```yaml
alias: Room Presence Lighting (Adaptive Lighting, 10s Off Delay)
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
   _↪️ Insert GIF here_

2. Click **Automations & Scenes** → **Automations**  
   _↪️ Insert GIF here_

3. Click **+ Create Automation**  
   _↪️ Insert GIF here_

4. Select **Start with an empty automation**  
   _↪️ Insert GIF here_

5. Click the **three-dot menu** (⋮) in the top-right corner and choose **Edit in YAML**  
   _↪️ Insert GIF here_

6. Paste the YAML code above into the editor  
   _↪️ Insert GIF here_

7. Replace all placeholders (in CAPS) with your own Home Assistant entity IDs before saving  
   _↪️ Insert GIF here_
 
9. Click **Save**, give your automation a name, and you’re done!  
   _↪️ Insert GIF here_

---

🆕 More automations added regularly — [Follow on GitHub](https://github.com/LewnaTech/LewnaTech) for updates!

[![Support LewnaTech](https://ko-fi.com/img/githubbutton_sm.svg)](https://ko-fi.com/lewnatech)
