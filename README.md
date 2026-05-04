# VeloClimat_ESP32_Firmware

Build a Veloclimap from A to Z.

# Dependencies 

- ESP-IDF
<br></br>

# Step 1: Unbox the components

You should have four components:

- A SHT40 I2C sensor
- A ESP32 Board
- A SPST switch
- A 1800 mAh LiPo Battery 

The following hardware have been tested:

- ESP32-WROOM-32E
- ESP32-C3 (devkit-lipo)
- SHT40 (DFRobot module v1)

-> TODO add picture before welding

# Step 2: Weld the components

The components should be welded using the following pinout and diagram

## Pinout

ESP32 GPIO_NUM_8 -> SHT40 SDA  
ESP32 GPIO_NUM_9 -> SHT40 SCL  
ESP32 GND        -> SHT40 GND  
ESP32 3.3V       -> SHT40 VCC

ESP32 BAT-       -> Switch side 1  
Switch side 2    -> BAT-  
BAT+             -> ESP32 BAT+

## Diagram

```mermaid
flowchart LR
    subgraph ESP32 [ESP32 Board]
        P8(GPIO_NUM_8)
        P9(GPIO_NUM_9)
        GND(GND)
        V33(3.3V)
        EBAT_P(BAT+)
        EBAT_M(BAT-)
    end

    subgraph SHT40 [SHT40 DFRobot Module]
        SDA(SDA)
        SCL(SCL)
        SGND(GND)
        SVCC(VCC)
    end

    subgraph Power [1800mAh LiPo Battery]
        BP(BAT+)
        BM(BAT-)
    end

    subgraph Switch [SPST Switch]
        S1(Side 1)
        S2(Side 2)
    end

    %% I2C Connections
    P8 <-->|I2C Data| SDA
    P9 --->|I2C Clock| SCL
    GND --- SGND
    V33 ---> SVCC

    %% Power Connections
    BP ---> EBAT_P
    BM --- S2
    S1 --- EBAT_M
```
-> TODO add picture after welding


# Step 3: Install the app

Open a terminal

Clone the repository on your laptop
```bash
git clone https://github.com/franetibe/VeloClimat_ESP32_Firmware.git
```

Build the app on your laptop
```bash
get_idf # or make sure you have the idf environment loaded in your terminal
cd VeloClimat_ESP32_Firmware
idf.py build
```

-> Connect the ESP32 with the laptop ?

Flash the app on the ESP32
```bash
idf.py flash monitor
```

# Step 4: Test the communication between the app and the hardware

-> TODO Rewrite this part ?

- Set the target for your esp32 model (example `idf.py set_target esp32-c3`)
- Make sure you have the flash size of your particular esp32 set right (`idf.py menuconfig`)
- Make sure you have the I2C pins set right `GPIO_SDA_PIN` and  `GPIO_SCL_PIN` defines in the gatts_server.c
- You can choose the accuracy level you want by changing the line `uint8_t command[1] = {SHT40_MEDIUM_ACCURACY_MEASURMENT_COMMAND};` in `sht_get_data`

# Step 5: Mount the shield and place the hardware inside the shield

-> TODO Rewrite this part and add pictures ?

- You can soften the switch hole with a heat gun or a hot air station before inserting it
- The battery is taped to the back with a piece of nano tape
- The battery connector on the ESP32 can be desoldered to solder the wires through the vias
- The rest is soldered on headers and covered with heat shrink tube

# Additional information

- As it stands a 1800mAh battery should last about 26hrs  




