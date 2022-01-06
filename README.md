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

## Get stats of chip (chip, capability, frequency, etc)
``
esptool.py read_mac
```

Erase existing firmware
NOTE: Had to hold boot button on chip while running
```
esptool.py --chip esp32 --port /dev/ttyUSB0 --baud 460800 erase_flash
```

## Flash MicroPython for ESP-WROOM-32
```
esptool.py --port /dev/ttyUSB0 --baud 460800 write_flash --flash_size=detect 0x0 esp8266-20200911-v1.13.bin
```

## Flash MicroPython for ESP-WROOM-32
```
esptool.py --port /dev/ttyUSB1 --baud 460800 write_flash 0x1000 esp32-idf3-20200902-v1.13.bin
```

## List connected devices
```
rshell -l
```

## Connect to Micropython
```
rshell --port /dev/ttyUSB1 -a
```

## Start REPL once connected
```
repl
```

## Toggle onboard LED on/off
```
import machine
led = machine.Pin(2, machine.Pin.OUT)
led.on()
led.off()
```
