# rpi_ap_mode
Files to make a Raspberry Pi act like an Access Point

Borrowed from [elinux.org](https://elinux.org/RPI-Wireless-Hotspot)

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
