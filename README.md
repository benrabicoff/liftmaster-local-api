# LiftMaster Local API

The local API appears to be based off the Radio Thermostat Company of America Wi-Fi USNAP Module API. You can reference the API docs [here](RadioThermostat_CT50_Honeywell_Wifi_API_V1.3.pdf).

[#,#] next to the endpoint represents whether GET/POST are accepted.

## Local API Endpoints
`http://<ip-address>/sys` [1,1]

Fetches the basic state of the GDO.

```json
{
    "uuid": "XXXXXXXXXXXXXXXXXXXXXXXXXXX",
    "interface": "uap",
    "prov": {
        "types": []
    },
    "connection": {
        "station": {
            "mac_addr": "XX-XX-XX-XX-XX-XX",
            "configured": 1,
            "status": 2,
            "ssid": "WifiNetwork",
            "bssid": "XX:XX:XX:XX:XX:XX",
            "channel": 11,
            "security": 4,
            "rssi": -40,
            "ip": {
                "ipv4": {
                    "iptype": 1,
                    "ipaddr": "192.168.1.80",
                    "ipmask": "255.255.255.0",
                    "ipgw": "192.168.1.1",
                    "ipdns1": "1.1.1.1",
                    "ipdns2": "0.0.0.0"
                }
            }
        }
    }
}
```


<hr>

`http://<ip-address>/sys/services` [1,0]

Retrieves the list of services available on the GDO

```json
{
    "httpd_handlers": {
        "/sys/network": [
            1,
            1
        ],
        "/sys/time": [
            1,
            1
        ],
        "/sys/command": [
            0,
            1
        ],
        "/sys/connection": [
            1,
            0
        ],
        "/sys/services": [
            1,
            0
        ],
        "/sys/prov_status": [
            0,
            1
        ],
        "/sys/interface": [
            1,
            0
        ],
        "/sys": [
            1,
            1
        ],
        "/sys/mode": [
            1,
            1
        ]
    }
}
```

<hr>

`http://<ip-address>/sys/command` [0,1]

Currently only “reboot” command is supported.

```
curl -d '{"command": "reboot"}' http://<ip-address>/sys/command</code>
```

<hr>

`http://<ip-address>/sys/connection` [1,0]

Connection state of the GDO

```json
{
    "auth_failed": 0,
    "conn_failed": 0,
    "dhcp_failed": 0,
    "conn_success": 1
}
```

<hr>

`http://<ip-address>/sys/interface` [1,0]

Connection interface of the system

```
{
    "interface": "uap"
}
```

<hr>

`http://<ip-address>/sys/network` [1,1]

Network details of the GDO

```json
{
    "ssid": "WifiNetwork",
    "bssid": "XX:XX:XX:XX:XX:XX",
    "channel": 11,
    "security": 4,
    "rssi": -40,
    "ip": {
        "ipv4": {
            "iptype": 1,
            "ipaddr": "192.168.1.80",
            "ipmask": "255.255.255.0",
            "ipgw": "192.168.1.1",
            "ipdns1": "1.1.1.1",
            "ipdns2": "0.0.0.0"
        }
    }
}
```

<hr>

`http://<ip-address>/sys/mode` [1,1]

Indicates system operating mode.

```json
{
    "mode": 1
}
```

0 – provisioning, 1 – normal (Integer)

```
curl -d '{“mode”: 0}' http://<ip-address>/sys/mode
```

A POST with the value of mode as 0, resets the device back into provisioning mode.

<hr>

`http://<ip-address>/sys/prov_status` [0,1]

Finish MyQ setup?

```
curl -d '{"finish": 1}' http://<ip-address>/sys/prov_status
```

<hr>

`http://<ip-address>/sys/time` [1,1]

Unix time stamp

```json
{"epoch":1699536654}
```

```
curl -d '{"epoch": 1699485550}' http://<ip-address>/sys/time
```

## Webserver Files
### HTML
`http://<ipaddress>/index.html` (redirects to start.html)

`http://<ip-address>/start.html`

`http://<ip-address>/about`

`http://<ip-address>/about.html`

`http://<ip-address>/config.html`

`http://<ip-address>/config_gdo.html`

`http://<ip-address>/config_hub.html`

`http://<ip-address>/connect_gdo.html`

`http://<ip-address>/connect_hub.html`

`http://<ip-address>/game.html` (ref’d in about.html, but 404s)

###  JSON
`http://<ip-address>/jabout`

`http://<ip-address>/jconfig_save` (ref’d but 404s)

`http://<ip-address>/jscan_results` (ref’d but 404s)

`http://<ip-address>/jserial`

`http://<ip-address>/jserial_connect` (ref’d but 404s)

`http://<ip-address>/jstart`

### CSS
`http://<ip-address>/base.css`

`http://<ip-address>/brand.css`

`http://<ip-address>/style.css`

`http://<ip-address>/myq.css`

### Javascript
`http://<ip-address>/brand.js`

`http://<ip-address>/language.js`

`http://<ip-address>/myq.js`

### Images
`http://<ip-address>/adjustbutton.gif`

`http://<ip-address>/mainlogo.png`

`http://<ip-address>/myqlogo.png`

`http://<ip-address>/myfavicon.png`

`http://<ip-address>/grayspin.gif`

`http://<ip-address>/signal_excellent.png`

`http://<ip-address>/signal_good.png`

`http://<ip-address>/signal_fair.png`

`http://<ip-address>/signal_poor.png`

`http://<ip-address>/lock.gif`
