## RASA internal temperature / humidity daemon

Part of the observatory software for the Warwick La Palma telescopes.

`sht35d` wraps a SHT35 temperature/humidity sensor and makes the latest measurement available for other services via Pyro.

`sht35` is a commandline utility that reports the latest measurement from the RASA sht35 sensor.

See [Software Infrastructure](https://github.com/warwick-one-metre/docs/wiki/Software-Infrastructure) for an overview of the W1m software architecture and instructions for developing and deploying the code.

### Software Setup

* Run `sudo raspi-config`, select `Interface Options` and enable the I2C interface
* `sudo apt install git python3-pip python3-smbus` to install dependencies
* `sudo pip3 install Pyro4` to install dependencies
* Clone the [warwick-observatory-common](https://github.com/warwick-one-metre/warwick-observatory-common/) repository and `sudo python3 setup.py install`
* Clone the [sht35d](https://github.com/warwick-one-metre/sht35d/) repository
* `sudo cp sht35 sht35d /usr/local/bin/` to install the daemon and client
* `sudo cp sht35.service /etc/systemd/system/` to install the systemd service
* `sudo systemctl enable sht35` to enable the system service
* `sudo systemctl start sht35` or reboot to start the system service
