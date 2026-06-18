# ♨️ Whirlpool Heat-up Timer ⏱️

**Version 1.2**

Never wait again! This Home Assistant blueprint automatically calculates your whirlpool's **heat-up time** and starts a **timer** that tells you exactly when your desired temperature is reached. Always ready for your relaxing bath! 🛀✨

<img width="690" height="115" alt="Bildschirmfoto 2025-10-03 um 18 20 13" src="https://github.com/user-attachments/assets/661b9770-0592-4ec1-a9be-edf586a03306" />


---

## 🔧 Inputs

| Input | Description | Default / Notes |
|-------|-------------|----------------|
| `temperatur_sensor` | The sensor that provides the current whirlpool temperature | Required |
| `zieltemperatur` | Target temperature (°C) | Default: 38 |
| `standard_heizrate` | Default heating rate in °C/hour | Default: 2 |
| `use_dynamic_rate` | Toggle to use optional heating rate sensor for dynamic calculation | Default: true |
| `heizrate_sensor` | Optional sensor providing real-time heating rate (°C/hour) | Optional; must be 75–150% of Default Rate to be used |
| `aufheiz_timer` | Timer helper entity to track the calculated heat-up duration | Required |

---

## 🧠 How It Works

1. **Trigger 🌡️:** Automation starts whenever the whirlpool temperature sensor changes.  
2. **Heating Rate Check ⚡:**  
   - Uses optional heating rate sensor if enabled and value is valid.  
   - Otherwise, falls back to Default Heating Rate.  
3. **Validation 🛡️:**  
   - Dynamic sensor value is only used if it is between 75%–150% of Default Rate.  
   - Invalid or missing values → Default Rate is used.  
4. **Time Calculation ⏳:**  
   - Calculates estimated remaining time based on current temp, target temp, and validated heating rate.  
5. **Start Timer 🚀:**  
   - The selected timer helper is set to the calculated duration and started. Countdown can be monitored in your dashboard.

---

## 📥 Import Blueprint

To import directly into your Home Assistant instance, click:

[![Open your Home Assistant instance and show the blueprint import dialog with a specific blueprint pre-filled.](https://community-assets.home-assistant.io/original/4X/d/7/6/d7625545838a4970873f3a996172212440b7e0ae.svg
)](https://my.home-assistant.io/redirect/blueprint_import/?blueprint_url=https%3A%2F%2Fraw.githubusercontent.com%2Fps915%2Fha-blueprints%2Frefs%2Fheads%2Fmain%2Fwhirlpool_heatup_timer%2Fwhirlpool_heatup_timer.yaml)

---

## 📜 Changelog



**Version 1.1**  
- Added validation for optional heating rate (must be 75–150% of Default Rate).  
- Added `use_dynamic_rate` toggle for easy control of dynamic sensor usage.  
- More robust handling of invalid sensor values.  

**Version 1.0**  
- Initial release.


---

## 💬 Feedback & Support

For questions, feedback, or support, please visit the [Home Assistant Community Forum](https://community.home-assistant.io/t/whirlpool-heat-up-timer-automatically-calculates-heat-up-time/)
