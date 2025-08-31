# Raspberry Pi 3D Printer + NAS Setup

This repository contains configuration and scripts for managing a Raspberry Pi 4 (4GB RAM) running multiple services for 3D printing, camera streaming, and local NAS storage.

---

## 📁 Folder Structure

``` 
raspi-3d-nas/
├── crowsnest/ # Crowsnest camera configuration
│ └── crowsnest.conf
├── klipper/ # Klipper printer firmware configuration
│ └── printer.cfg
├── mainsail/ # Mainsail UI configuration (optional)
│ └── ui-settings.json
├── docker/ # Docker setup for Nextcloud + MariaDB
│ ├── docker-compose.yml # Docker compose file
│ ├── nextcloud/ # Nextcloud persistent folders (only configs)
│ │ ├── config/
│ │ └── data/ # Only config files, NOT actual data
├── scripts/ # Automation scripts
│ └── move_clips_to_nextcloud.sh
├── misc/ # Miscellaneous notes, diagrams, temp files
└── README.md # This file
```

---

## ⚙️ Components Overview

- **Klipper Screen UI**  
  - Runs on the Pi display for printer control.  
  - Handles printer firmware commands locally.  

- **Mainsail UI**  
  - Browser-based interface to monitor & control the printer.  
  - Communicates with Klipper via Moonraker API.  

- **Crowsnest**  
  - Standalone software managing Pi camera streaming/recording.  
  - Streams via HTTP/MJPEG (`http://<pi_ip>:8080`) and can record clips.  

- **Docker / Nextcloud**  
  - Central NAS for storing camera clips, phone backups, and other files.  
  - Uses Docker containers: Nextcloud + MariaDB.  
  - Current storage is Pi microSD; future RAID SSDs are recommended for redundancy.  

---

## 📌 Notes

- Only configuration files and scripts are stored here; **Nextcloud data and camera clips are not included**.  
- Camera clips can be saved into Nextcloud either via direct configuration in Crowsnest or using automation scripts.  
- `misc/` folder is for notes, diagrams, or temporary files related to the setup.  

---

## 🤖 AI-Friendly Explanation

This setup integrates multiple services on a single Raspberry Pi 4:

1. **3D Printing**
   - **Klipper firmware** runs locally on the Pi.
   - **Mainsail** provides a web UI for monitoring and controlling prints.
2. **Camera Management**
   - **Crowsnest** streams and optionally records the Pi camera.
   - Clips can be stored locally or pushed into Nextcloud for central storage.
3. **NAS / File Backup**
   - **Nextcloud** in Docker handles file storage for cameras and mobile devices.
   - Can later be expanded with RAID SSDs for redundancy.
4. **Automation**
   - Scripts can move camera clips to Nextcloud automatically.
   - Permissions and folder structure ensure Docker containers can read/write properly.

> With this structure and AI-friendly metadata, future AI agents can understand your setup without manual explanation. Each folder corresponds to a service and contains configuration or automation scripts.

---

## 🔧 Future Improvements

- Add RAID SSD setup for Nextcloud and camera storage.  
- Automate camera clip backup directly into Nextcloud.  
- Add scripts to monitor and rotate logs or clips to manage storage.  

