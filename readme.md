# Raspberry Pi Adventures
## Setup
Make sure to expand the space on your Raspberry so that you don't run into space issues when upgrading.

    $ sudo raspi-config


Update your Raspberry Pi by typing


    $ sudo apt-get update

Now you need to upgrade you Pi, type

    $ sudo apt-get upgrade

## Networking

    $ sudo nano /etc/network/interfaces


    # local host configuration
    auto lo
    iface lo inet loopback

    # ethernet configuration
    auto eth0
    allow-hotplug eth0
    iface eth0 inet static
    address 192.168.1.8
    netmask 255.255.255.0
    gateway 192.168.1.1
    
    # wireless configuration
    auto wlan0
    allow-hotplug wlan0
    iface wlan0 inet manual
    wpa-roam /etc/wpa_supplicant/wpa_supplicant.conf

    iface default inet dhcp


    sudo nano /etc/wpa_supplicant/wpa_supplicant.conf


    ctrl_interface=DIR=/var/run/wpa_supplicant GROUP=netdev
    update_config=1
    
    network={
        ssid="%actual ssid%"
        scan_ssid=1
        key_mgmt=WPA-PSK
        psk="%actual key%"
    }