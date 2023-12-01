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
                    "ipaddr": "XXX.XXX.X.XXX",
                    "ipmask": "255.255.255.0",
                    "ipgw": "XXX.XXX.X.XXX",
                    "ipdns1": "X.X.X.X",
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

_Currently only “reboot” command is supported._

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

Connection interface of the GDO

```json
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
            "ipaddr": "XXX.XXX.X.XXX",
            "ipmask": "255.255.255.0",
            "ipgw": "XXX.XXX.X.XXX",
            "ipdns1": "X.X.X.X",
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

_A POST with the value of mode as 0, resets the device back into provisioning mode._

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
`http://<ipaddress>/index.html` <small>_(redirects to start.html)_</small>

`http://<ip-address>/start.html`

`http://<ip-address>/about`

`http://<ip-address>/about.html`

`http://<ip-address>/config.html`

`http://<ip-address>/config_gdo.html`

`http://<ip-address>/config_hub.html`

`http://<ip-address>/connect_gdo.html`

`http://<ip-address>/connect_hub.html`

`http://<ip-address>/engabout.html`

`http://<ip-address>/game.html` <small>_(ref’d in about.html, but 404s)_</small>

`http://<ip-address>/rssi.html`

`http://<ip-address>/start_connap.html`

`http://<ip-address>/start_gdo.html`

`http://<ip-address>/start_hub.html`

`http://<ip-address>/testurl.html`

###  JSON
`http://<ip-address>/jabout` _(an entry of 'special': "Special Shout out to all MyQ team members!" will appear at random)_

`http://<ip-address>/jengabout`

`http://<ip-address>/jconfig_clear` _(ref'd in firmware, but 404s)_

`http://<ip-address>/jconfig_clear?credentials=reset&end=1`

`http://<ip-address>/jconfig_clear?credentials=factoryreset&end=1`

`http://<ip-address>/jconfig_save` _(ref’d but 404s)_

`http://<ip-address>/jconnect_serial` _(ref'd in firmware, but 404s)_

`http://<ip-address>/jdevice_info` _(ref'd in firmware, but 404s)_

`http://<ip-address>/jexit` _(ref'd in firmware, but 404s)_

`http://<ip-address>/jlang_get` _(ref'd in firmware, but 404s)_

`http://<ip-address>/jlang_set` _(ref'd in firmware, but 404s)_

`http://<ip-address>/jscan_results` _(ref’d but 404s)_

`http://<ip-address>/jsec_supported`

`http://<ip-address>/jsensortest`

`http://<ip-address>/jserial`

`http://<ip-address>/jserial_connect` _(ref’d but 404s)_

`http://<ip-address>/jstart`

### CSS
`http://<ip-address>/base.css`

`http://<ip-address>/brand.css`

`http://<ip-address>/chamberlain.css`

`http://<ip-address>/craftsman.css`

`http://<ip-address>/liftmaster.css`

`http://<ip-address>/merlin.css`

`http://<ip-address>/myq.css`

`http://<ip-address>/style.css`

### Javascript
`http://<ip-address>/brand.js`

`http://<ip-address>/craftsman.js`

`http://<ip-address>/cgi.js`

`http://<ip-address>/language.js`

`http://<ip-address>/myq.js`

### Images
`http://<ip-address>/adjustbutton.gif`

`http://<ip-address>/craftsmanlogo.png`

`http://<ip-address>/liftmasterlogo.png`

`http://<ip-address>/mainlogo.png`

`http://<ip-address>/merlinlogo.png`

`http://<ip-address>/myqlogo.png`

`http://<ip-address>/myfavicon.png`

`http://<ip-address>/myfaviconch.png`

`http://<ip-address>/myfaviconcr.png`

`http://<ip-address>/myfaviconlm.png`

`http://<ip-address>/myfaviconmr.png`

`http://<ip-address>/myfaviconmq.png`

`http://<ip-address>/myqicon.png`

`http://<ip-address>/grayspin.gif`

`http://<ip-address>/signal_excellent.png`

`http://<ip-address>/signal_good.png`

`http://<ip-address>/signal_fair.png`

`http://<ip-address>/signal_poor.png`

`http://<ip-address>/lock.gif`
