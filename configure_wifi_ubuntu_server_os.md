# Configure Wifi in Ubuntu Server OS

First start wlan0

    ifconfig wlan0 up

create a file named **wpa_supplicant.conf**

    sudo nano /etc/wpa_supplicant/wpa_supplicant.conf

Add below lines in the file

    network={
    	    ssid="wifi_Name"
    	    psk="wifi_Password"
    }

Create another file named **rc.local** (if not exists, most probably it does not exists)

    sudo nano /etc/rc.local

Add below lines in the file

    #!/bin/bash
    sudo wpa_supplicant -B -iwlan0 -c/etc/wpa_supplicant/wpa_supplicant.conf
    sleep 5
    sudo dhclient wlan0

Change file permission

    sudo chmod +x /etc/rc.local

**Reboot**