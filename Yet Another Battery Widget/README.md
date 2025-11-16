<img width="527" height="378" alt="image" src="https://github.com/user-attachments/assets/bf1591b8-01b6-4f90-bf9e-6dcd0f1cffcf" />

A detailed, data-rich **KWGT battery statistics widget** powered by Tasker and Shizuku.  
This widget delivers accurate real-time metrics such as drain rate, mA consumption, cycles, temperature, and battery health — all presented in a clean digital dashboard layout.

---

## ⚡ Features

- LED-style **battery percentage**
    
- **Screen-On-Time (SOT)** indicator
    
- Time since unplugged & **drain mA**
    
- **24-hour battery graph** with smooth lines
    
- Battery **cycles**, **health %**, and **charge limit** status
    
- Temperature monitoring
    
- Minimal, dark-theme friendly design
    

---

## 🛠 Requirements

To get full functionality (especially mA, cycle count, health, SOT and advanced stats), you MUST have:

- **KWGT Pro**
    
- **Tasker**
    
- **Shizuku** (ADB or root mode)
    
- Shizuku permissions granted to Tasker
    
- Tasker project imported and configured
    

Without Tasker + Shizuku, the widget will only show basic battery information.

---

## ⚠️ Important Note (Not Noob-Friendly)

This setup requires some working knowledge of:

- Tasker (importing projects, granting permissions, background execution)
    
- KWGT (scaling, layers, globals)
    
- Shizuku setup (ADB wireless or USB)
    

Expect to tweak configurations based on your phone.  
**If you're new to KWGT or Tasker, this may not be beginner-friendly.**

---

## 🔧 Compatibility

### ✔ Confirmed Working

- **Google Pixel devices** (tested and stable)
    

### ⚠ May Not Work Well On

Chinese OEMs such as:

- Xiaomi / Redmi / POCO
    
- Vivo / iQOO
    
- Oppo / Realme
    
- Huawei
    

These brands aggressively limit background access, which may cause missing or delayed data updates.

---

## 📱 Scaling & Layout

Depending on screen resolution, DPI, and launcher grid:

- Go to **KWGT → Layer → Scale** and adjust
    
- Modify padding in launcher settings
    
Each device may require slight adjustments.

---

## 📁 File Locations (Single-Line Paths)

**KWGT Widget File**

`KWGT-Widgets/Yet Another Battery Widget/KWGT File/YABW_Nov_2025.kwgt`

**Tasker Project File**

`KWGT-Widgets/Yet Another Battery Widget/Tasker Project/Battery.prj.xml`

---

## 📝 Installation

### 1. Install required apps

- KWGT
    
- **KWGT Pro**
    
- Tasker
    
- Shizuku
    

### 2. Enable Shizuku

- Start via ADB Wireless or USB
    
- Ensure Tasker is granted Shizuku permission
    

### 3. Import Tasker Project

In Tasker:

`Profiles → Import → Battery.prj.xml`

Enable the profile and run an initial test.

### 4. Import KWGT Preset

Copy the `.kwgt` file to your KWGT Working Folder:

`Internal Storage/KWGT/widgets`

Add a KWGT widget → Tap to load → Select **YABW_Nov_2025.kwgt**.

---

## 🎨 Customization

Inside KWGT, you can edit:

- Colors and typography
    
- Graph style & thickness
    
- Data labels and placement
    
- Spacing, padding, and scale
    
- Update intervals (via Tasker)
    

Everything is modular and tweakable.

---

## 🤝 Contributing

Contributions are welcome! Feel free to:

- Improve Tasker logic
    
- Add new data sources
    
- Enhance appearance
    
- Provide compatibility profiles for more devices
    

Submit a pull request anytime.

---

## 📜 License

Released under the **MIT License** — free to use, modify, and redistribute with attribution.
