# thin-rc.d
Simple FreeBSD rc script for thin

## Reason
Thin does not provide `--install` for the FreeBSD platform. 

* https://github.com/macournoyer/thin/
```ruby
File.directory?('/etc/rc.d') ? '/etc/rc.d/thin' : '/etc/init.d/thin'
```
The thin `rubygem-thin` does not provide a rc.d script either. 

* https://github.com/freebsd/freebsd-ports/tree/master/www/rubygem-thin

## Install

Download the rc.d script, make it executable, place it in the `/usr/local/etc/rc.d/`, profit $$.

```shell
mkdir -p /usr/local/etc/rc.d
cd /usr/local/etc/rc.d/
fetch https://raw.githubusercontent.com/packets-at-rest/thin-rc.d/master/rc.d/thin
chmod +x thin
echo 'thin_enable="YES"' >> /etc/rc.conf
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

## Example Configuration

```shell
thin_enable="YES"
thin_host="10.1.0.50"
thin_port="9001"
thin_appdir="/opt/packets-at-rest"
```

## Service

`/usr/local/etc/rc.d/thin start`

## Logs

You logs will be here by default

`/var/log/thin.80.log`
