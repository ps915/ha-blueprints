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
| `heizrate_sensor` | Optional Statistics sensor providing the real-time heating rate (`Change second`, °C/s). The value is automatically converted to °C/h inside the blueprint | Optional; converted value must be 75–150% of Default Rate to be used |
| `aufheiz_timer` | Timer helper entity to track the calculated heat-up duration | Required |

---

## 🧠 How It Works

1. **Trigger 🌡️:** Automation starts whenever the whirlpool temperature sensor changes.  
2. **Heating Rate Check ⚡:**  
   - Uses optional heating rate sensor if enabled and value is valid.  
   - Otherwise, falls back to Default Heating Rate.  
3. **Unit Conversion 🔄:**  
   - The optional sensor delivers °C/second (`Change second`); the blueprint converts it to °C/hour (×3600) so it is comparable to the Default Rate.  
4. **Validation 🛡️:**  
   - Dynamic sensor value is only used if it is between 75%–150% of Default Rate.  
   - Invalid or missing values → Default Rate is used.  
5. **Time Calculation ⏳:**  
   - Calculates estimated remaining time based on current temp, target temp, and validated heating rate.  
6. **Start Timer 🚀:**  
   - The selected timer helper is set to the calculated duration and started. Countdown can be monitored in your dashboard.

---

## 📥 Import Blueprint

To import directly into your Home Assistant instance, click:

[![Open your Home Assistant instance and show the blueprint import dialog with a specific blueprint pre-filled.](https://community-assets.home-assistant.io/original/4X/d/7/6/d7625545838a4970873f3a996172212440b7e0ae.svg
)](https://my.home-assistant.io/redirect/blueprint_import/?blueprint_url=https%3A%2F%2Fraw.githubusercontent.com%2Fps915%2Fha-blueprints%2Frefs%2Fheads%2Fmain%2Fwhirlpool_heatup_timer%2Fwhirlpool_heatup_timer.yaml)

---

## 📜 Changelog

**Version 1.2**  
- Fixed unit mismatch: the dynamic heating rate sensor (`Change second`, °C/s) is now converted to °C/h (×3600) before validation. Previously the raw value (~0.0005) never passed the 75–150% check against the Default Rate (°C/h), so the dynamic rate was silently ignored and the Default Rate was always used.  
- Clarified the `heizrate_sensor` input description (raw value is °C/s and converted internally).  

**Version 1.1**  
- Added validation for optional heating rate (must be 75–150% of Default Rate).  
- Added `use_dynamic_rate` toggle for easy control of dynamic sensor usage.  
- More robust handling of invalid sensor values.  

**Version 1.0**  
- Initial release.


---

## 💬 Feedback & Support

For questions, feedback, or support, please visit the [Home Assistant Community Forum](https://community.home-assistant.io/t/whirlpool-heat-up-timer-automatically-calculates-heat-up-time/)
