# LiftMaster Local API

The local API appears to be based off the Radio Thermostat Company of America Wi-Fi USNAP Module API. You can reference the API docs here: .

## Local API Endpoints
/sys

GET: YES · POST: YES

Fetches the basic state of the system

/sys/services

GET: YES · POST: NO

Retrieves the list of services available on the device

`/sys/command`

GET: NO · POST: YES

Currently only “reboot” command is supported.

<code>curl -d '{"command": "reboot"}' http://[ip-address]/sys/command</code>

/sys/connection

GET: YES · POST: NO

Connection state of the system

/sys/interface

GET: YES · POST: NO

Connection interface of the system

/sys/network

GET: YES · POST: YES

Network details of the system

/sys/mode

GET: YES · POST: YES

Indicates system operating mode.

0 – provisioning, 1 – normal (Integer)

`curl -d '{“mode”: 0}' http://<ip-address>/sys/mode`

* A POST with the value of mode as 0, resets the device back into provisioning mode.

/sys/prov_status

GET: NO · POST: YES

Finish MyQ setup?

`curl -d '{"finish": 1}' http://<ip-address>/sys/prov_status`

/sys/time

GET: YES · POST: YES

Unix time stamp 

`curl -d '{"epoch": 1699485550}' http://<ip-address>/sys/time`

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
