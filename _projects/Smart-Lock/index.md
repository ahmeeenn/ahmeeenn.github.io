---
layout: post
title: Solar Smart Lock – IoT Access System (Full Stack)
description: Developed all software and system-level logic for a solar-powered smart lock, including backend, frontend, WPF GUI, database, and ESP32 integration.
skills: 
  - Flask & REST API development
  - SQLite database modeling
  - C# WPF (Windows GUI)
  - Web frontend (HTML/CSS/JS)
  - Serial & COM port communication
  - IoT system integration (ESP32 + backend)
  - Low-level firmware interfacing (COM setup, MAC binding)
  - Git-based collaboration
main-image: /Untitled-2.png
---

## Project: Solar Smart Lock

The **Solar Smart Lock** is a distributed, solar-powered access control system for cabinet or door security. My role focused on **all IoT-related software** – everything from backend to database, desktop app, web frontend, and ESP32 integration.

I worked in a team of four. While others handled hardware and CAD (SolidWorks), I built and integrated all code and logic from **ESP32 to server to UI**.

---

## My Responsibilities

- 📡 **Flask-based Backend API**
  - Designed all REST endpoints (`/register`, `/cards`, `/check_card`, `/request_unlock`, etc.)
  - Built unlock logic using MAC-address-based validation
  - Integrated SQLite with `ON DELETE CASCADE` and relational integrity

- 🗃️ **SQLite Database Modeling**
  - Users, cards, locks, and access rights
  - User-role system (admin, user)
  - Card-to-user and lock-to-user mapping via join tables

- 💻 **C# WPF Desktop Application**
  - RFID card scan via ESP32 reader (HTTP requests)
  - UID lookup and user auto-fill
  - Registration of new users + password input
  - Lock assignment + role selection
  - Flashing ESP32 firmware via PlatformIO CLI
  - Serial COM configuration of lock devices (Wi-Fi credentials + name)

- 🌐 **Web Interface**
  - Admin dashboard: manage users, assign locks, trigger remote unlocks
  - User dashboard: see own locks, unlock them remotely
  - JavaScript + REST API integration
  - Mobile-friendly layout (CSS grid + flex)

- 🔌 **Serial & COM Port Integration**
  - C# script to configure new ESP32 locks:
    - Sends Wi-Fi SSID, password, lock name
    - Registers MAC with backend
  - Triggers PlatformIO flashing process

---

## Architecture Diagram

{% include image-gallery.html images="/system_architecture.png" height="400" %}

---

## Screenshots

### Desktop App (WPF)
{% include image-gallery.html images="/c_app_mainpage.png, /c_app_user_table.png" height="400" %}

### Web Dashboard
{% include image-gallery.html images="/admin_dash_web.png, /user_dash_web.png" height="400" %}

---

## Sample Endpoints (Flask Backend)

```python
@app.route('/check_card')
def check_card():
    uid = request.args.get("uid")
    lock = request.args.get("lock")
    # Check if user has access
    ...

@app.route('/register', methods=["POST"])
def register():
    data = request.get_json()
    email = data["email"]
    password = hash_password(data["password"])
    ...
