# BlueDucky

![duckmenu](https://github.com/krazystar55/BlueDucky/assets/130956429/2f3dcc25-6cff-493e-a402-d6140e80e893)

# BlueDucky Ver 2.1 (Android) 🦆

Thanks to all the people for joining US!

![BlueDucky](https://github.com/krazystar55/BlueDucky/assets/130956429/11647367-488d-47a2-8761-e785657349ca)


🚨 CVE-2023-45866 - BlueDucky Implementation (Using DuckyScript)

🔓 Unauthenticated Peering Leading to Code Execution (Using HID Keyboard)

[This is an implementation of the CVE discovered by marcnewlin](https://github.com/marcnewlin/hi_my_name_is_keyboard)

<p align="center">
  <img src="./images/BlueDucky.gif">
</p>

## Introduction 📢
BlueDucky is a powerful tool for exploiting a vulnerability in Bluetooth devices. By running this script, you can:

1. 📡 Load saved Bluetooth devices that are no longer visible but have Bluetooth still enabled.
2. 📂 Automatically save any devices you scan.
3. 💌 Send messages via ducky script format to interact with devices.

I've successfully run this on a Raspberry Pi 4 using the default Bluetooth module. It works against various phones, with an interesting exception for a New Zealand brand, Vodafone.

## Installation and Usage 🛠️

### Setup Instructions

```bash
# update apt
sudo apt-get update
sudo apt-get -y upgrade

# install dependencies from apt
sudo apt install -y bluez-tools bluez-hcidump libbluetooth-dev \
                    git gcc python3-pip python3-setuptools \
                    python3-pydbus

# install pybluez from source
git clone https://github.com/pybluez/pybluez.git
cd pybluez
sudo python3 setup.py install

# build bdaddr from the bluez source
cd ~/
git clone --depth=1 https://github.com/bluez/bluez.git
gcc -o bdaddr ~/bluez/tools/bdaddr.c ~/bluez/src/oui.c -I ~/bluez -lbluetooth
sudo cp bdaddr /usr/local/bin/
```

## Running BlueDucky
```bash
git clone https://github.com/pentestfunctions/BlueDucky.git
cd BlueDucky
sudo hciconfig hci0 up
python3 BlueDucky.py
```

## Operational Steps 🕹️
1. On running, it prompts for the target MAC address.
2. Pressing nothing triggers an automatic scan for devices.
3. Devices previously found are stored in known_devices.txt.
4. If known_devices.txt exists, it checks this file before scanning.
5. Executes using payload.txt file.
6. Successful execution will result in automatic connection and script running.

## Duckyscript 💻
🚧 Work in Progress:
- Suggest me ideas

## Version 2.1 🐛
- Updated UI
- Improved User Experience
- Bluetooth Debugger; Checks your bluetooth adapters, and installed dependancies before allowing access to the application, this is to prevent devices that are not supported.
- Please Note: Numerous Changes have been made,please reference the commit history for specific changes.
  
## Enjoy experimenting with BlueDucky! 🌟







