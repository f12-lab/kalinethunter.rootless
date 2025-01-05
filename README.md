# Kali NetHunter Rootless Installation Guide :snake:
## :scroll: Description
This repository provides a guide for installing and troubleshooting common issues with Kali NetHunter in Rootless mode on Android devices. Kali NetHunter is a mobile penetration testing platform designed for security assessments, allowing its use without root access.

## :gear: Installation
1 Install Termux:
  -  Search for Termux on F-Droid (not on Google Play).
  -  Download and install it.

2 Configure Termux :wrench: :
  -  Open Termux and run:
  ```bash
      pkg update
      termux-setup-storage
      pkg install wget
  ```
3 Install Kali NetHunter :arrow_down: :
  - Execute:
  ```bash
    wget https://gitlab.com/kalilinux/nethunter/build-scripts/kali-nethunter-project/raw/master/nethunter-rootless/install-nethunter-termux
    chmod +x install-nethunter-termux
    ./install-nethunter-termux
  ```
4 Access Kali :key: :
  - Use `nh` or `nh -r` to start.

5 Configure DNS :globe_with_meridians: :
  -  Escalate to superuser:
  ```bash
    sudo su
    nano /etc/resolv.conf
  ```
  - Change the nameserver to `8.8.8.8`.

## :computer: GUI Installation
1 Set up KEX:
  ```bash
  nethunter kex passwd
  nethunter kex &
  ```
2 Install NetHunter KeX from F-Droid and configure the VNC connection.

## :hammer_and_wrench: Troubleshooting
### 1. Phantom Process Killer :ghost:
  - Disable the Phantom Process Killer on Android 12 & 13. Use ADB to execute:
  ```bash
  adb shell "/system/bin/device_config set_sync_disabled_for_tests persistent"
  adb shell "/system/bin/device_config put activity_manager max_phantom_processes 2147483647"
  adb shell settings put global settings_enable_monitor_phantom_procs false
  ```
### 2. Firefox Crashes :fox_face:
- Modify the settings in `about:config`:
  - Change `media.cubeb.sandbox` to `false`.
  - Change `security.sandbox.content.level` to `0`.

### 3. Sound Issues :loud_sound:
- Install PulseAudio and configure the configuration files:
  ```bash
  pkg update
  pkg install pulseaudio
  nano $PREFIX/etc/pulse/default.pa
  ```
  - Uncomment and add the corresponding line.
- Create a script to start PulseAudio and set the permissions.
## :page_facing_up: LICENSE
This project is licensed under the [GNU License](https://github.com/F12-Lab/KaliNethunter-rootless-/blob/main/LICENSE). 
## :chess_pawn: AUTHOR
Created by [f12-lab](https://github.com/F12-Lab)
