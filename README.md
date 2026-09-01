<h1 align="center">
  <img src="https://readme-typing-svg.demolab.com?font=Fira+Code&weight=700&size=30&pause=1000&color=6C63FF&center=true&vCenter=true&width=600&lines=🎤+Acoustic+Clap+Switch;Voice-Activated+Control;Smart+Home+on+a+Clap+👏" alt="Typing SVG" />
</h1>

<p align="center">
  <img src="https://img.shields.io/badge/Platform-Arduino%20Uno-00979D?style=for-the-badge&logo=arduino&logoColor=white" />
  <img src="https://img.shields.io/badge/Sensor-Sound%20Module-FF6F00?style=for-the-badge&logo=data:image/svg+xml;base64,PHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHdpZHRoPSI0MCIgaGVpZ2h0PSI0MCIgdmlld0JveD0iMCAwIDQwIDQwIj48Y2lyY2xlIGN4PSIyMCIgY3k9IjIwIiByPSIxOCIgZmlsbD0iI2ZmZmZmZiIgc3Ryb2tlPSIjMDAwIiBzdHJva2Utd2lkdGg9IjIiLz48cGF0aCBkPSJNMTIgMTBoMTZ2MjBIMTB6IiBmaWxsPSIjZmY2ZjAwIi8+PC9zdmc+&logoColor=white" />
  <img src="https://img.shields.io/badge/Actuator-Relay%20Module-red?style=for-the-badge&logo=data:image/svg+xml;base64,PHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHdpZHRoPSI0MCIgaGVpZ2h0PSI0MCIgdmlld0JveD0iMCAwIDQwIDQwIj48cmVjdCB4PSI1IiB5PSI1IiB3aWR0aD0iMzAiIGhlaWdodD0iMzAiIGZpbGw9IiNmZmZmZmYiIHN0cm9rZT0iI2UwMCIgc3Ryb2tlLXdpZHRoPSIyIi8+PC9zdmc+&logoColor=white" />
  <img src="https://img.shields.io/badge/Logic-Double%20Clap%20Detection-brightgreen?style=for-the-badge" />
  <img src="https://img.shields.io/badge/Application-Home%20Automation-blue?style=for-the-badge" />
  <img src="https://img.shields.io/badge/License-MIT-green?style=for-the-badge" />
</p>

<p align="center">
  <b>Control your lights, fans, or any AC/DC appliance with the sound of your hands.</b>
  <br />
  <i>Featuring double-clap detection to prevent accidental triggers from background noise.</i>
</p>

---

## 💡 Concept & Inspiration

Clap switches are a classic introduction to sound-activated control, but they are often impractical because they trigger on *any* loud noise (door slams, coughs, falling objects).

This project solves that problem by implementing a **double-clap detection algorithm** with configurable **debounce timing**. The system intelligently differentiates between random noise and intentional claps, making it reliable enough for real-world home automation.

> 🎯 **Use Case:** Turn on your desk lamp, control a room fan, or trigger an alarm — all with a simple double-clap pattern.

---

## ⚙️ System Architecture

```mermaid
flowchart TD
    A[Power ON] --> B[Initialize Sound Sensor & Relay]
    B --> C[Set Sensitivity Threshold]
    C --> D[Monitor Sound Level]
    D --> E{Clap 1 Detected?}
    E -->|No| D
    E -->|Yes| F["Start Debounce Timer (200ms)"]
    F --> G["Ignore Noise for 200ms"]
    G --> H{Clap 2 Detected?}
    H -->|No| I[Reset & Listen]
    H -->|Yes| J[Valid Double-Clap]
    I --> D
    J --> K[Toggle Relay State]
    K --> L["LED Feedback on State Change"]
    L --> D
