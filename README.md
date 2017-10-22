# rpi_ap_mode
Files to make a Raspberry Pi act like an Access Point

Borrowed from [elinux.org](https://elinux.org/RPI-Wireless-Hotspot)

### TODO

* [Force interface names to be predicatable](https://raspberrypi.stackexchange.com/questions/43560/raspberry-pi-3-eth0-wrongfully-named-enx)

* Configure second WLAN adapeter to connect to nearby WLAN networks

* Enabled conditional IP forwarding from AP if second WLAN interface has a path to the internet

## Install packages

```
sudo apt-get install hostapd udhcpd
```

## Install udhcpd.conf

Copy `udhcpd.conf` to `/etc/udhcpd.conf`


## Edit /etc/default/udhcpd

Comment out `DHCPD_ENABLED="no"`

## Install interfaces file

Copy `interfaces` to `/etc/network/interfaces`

## Install hostapd.conf config

Copy `hostapd.conf` to `/etc/hostapd/hostapd.conf`

## Edit /etc/default/hostapd to point to config

```
DAEMON_CONF="/etc/hostapd/hostapd.conf"
```

## Enabled and start services

```
sudo systemctl restart networking
sudo systemctl enable hostapd udhcpd
sudo systemctl start hostapd udhcpd
```
