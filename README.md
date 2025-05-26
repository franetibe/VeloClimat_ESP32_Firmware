# VeloClimat_ESP32_Firmware

Get data from a sht40 I2C sensor and transmits it over BLE

# Dependencies 

- ESP-IDF

# Build

Clone the repository :  
```bash
git clone https://github.com/The-Last-Resort-FR/VeloClimat_ESP32_Firmware.git
```

Build the app
```bash
get_idf # or make sure you have the idf environement loaded in your terminal
cd VeloClimat_ESP32_Firmware
idf.py build
```

Flash the app on the ESP32
```bash
idf.py flash monitor
```

# Additional Infos

As it stands a 1800mAh battery should last about 26hrs

# TODO

- Sleep between measures
- Unique adv name for multiple sensors around
- Full Bluetooth SIG compliance ?
- Potential fan before measure
- Case