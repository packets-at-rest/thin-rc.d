# thin-rc.d
Simple FreeBSD rc script for thin

## Reason
Thin does not provide --install for FreeBSD.

## Install
```shell
mkdir -p /usr/local/etc/rc.d
cd /usr/local/etc/rc.d/
fetch https://raw.githubusercontent.com/packets-at-rest/thin-rc.d/master/rc.d/thin
chmod +x thin
echo "thin_enable="\YES\"" >> /etc/rc.conf
```

Provide the additional configurations for your /etc/rc.conf
``` shell
# Add the following lines to /etc/rc.conf to enable thin:
# thin_enable (bool):      Set to YES to enable
#                 Default: NO
# thin_host (str):   Logging Directory
#               Default: "0.0.0.0"
# thin_port (str):   Logging Format
#               Default: "80"
# thin_appdir (str):  Network interface to sniff
#               Default: "/usr/local/www/app"
# thin_adapter (str):    Extra flags passed 
#               Default: "autodetect"
# thin_log (str):    Extra flags passed 
#               Default: "/var/log/thin.log"
# thin_env (str):    Extra flags passed 
#               Default: "development"
# thin_servers (str):    Extra flags passed 
#               Default: ""
```

## Service

`/usr/local/etc/rc.d/thin start`
