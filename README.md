# VeloClimat_ESP32_Firmware

Get data from a sht40 I2C sensor and transmits it over BLE
<br></br>

# Dependencies 

- ESP-IDF
<br></br>

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
<br></br>

# Additional Infos

- Set the target for your esp32 model (example `idf.py set_target esp32-c3`)  
- Make sure you have the flash size of your particular esp32 set right (`idf.py menuconfig`)
- Make sure you have the I2C pins set right `GPIO_SDA_PIN` and  `GPIO_SCL_PIN` defines in the gatts_server.c  
- You can choose the accuracy level you want by changing the line `uint8_t command[1] = {SHT40_MEDIUM_ACCURACY_MEASURMENT_COMMAND};` in `sht_get_data`
- As it stands a 1800mAh battery should last about 26hrs  

<br></br>

# Tested hardware

- ESP32-WROOM-32E
- ESP32-C3 (devkit-lipo)
- SHT40 (DFRobot module v1)

<br></br>

# TODO

- Potential fan before measure
- Case