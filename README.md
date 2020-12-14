# micropython-play
Playing around with Micropython on ESP-8266 and ESP-32

## Installation

To begin playing with Micropython, we initially need two tools, `esptool` and `rshell`.  They can be installed using the following `pip` command

```
pip install esptool rshell
```

### Download firmware
```
wget https://micropython.org/resources/firmware/esp32-idf3-20200902-v1.13.bin  # For ESP32
wget https://micropython.org/resources/firmware/esp8266-20200911-v1.13.bin     # For ESP8266
```


To write the firmware to the device, we first need to add the user to the dialout group and change the tty permissions
```
sudo usermod -a -G dialout $USER
sudo chmod a+rw /dev/ttyUSB0
```

```
esptool.py --chip esp32 --port /dev/ttyUSB0 --baud 115200 erase_flash
```
