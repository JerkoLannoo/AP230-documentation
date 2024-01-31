# AP230 documentation for MAC-based-auth
Adding MAC-based authentication to AP230 via the CLI. You could use this for a NAC, like e.g. PacketFence.
## Reset to factory defaults
 ```
reset config bootstrap
reset config
```
The default username is `admin` and the default password is `aerohive`.
## Set admin password
~~~
admin root-admin admin password [password]
~~~
## Disable controller connection
To disable controller based access to the AP, use this following command:
~~~
no capwap client enable
~~~
## Add user profile
~~~
user-profile [profile-name] vlan-id [vlan-id] attribute [attribute-id]
~~~
You can set the `vlan-id` to one.
## Add security-object
~~~
security-object [name]
~~~
## Adding primary security protocol (for open Wi-Fi)
To set the Wi-Fi protocol to `open`, use this command:
~~~
security-object [object name] security protocol-suite open
~~~
## Adding secondory security protocol (MAC-based-auth)
To use MAC-based-auth, use this command:
~~~
security-object [object name] security additional-auth-method mac-based-auth
~~~
## Adding RADIUS authentication server
~~~
aaa radius-server primary [ip] shared-secret [key]
~~~
## Adding RADIUS accounting server
To add a RADIUS accounting server, use this command:
~~~
aaa radius-server accounting [ip] shared-secret [key]
~~~
To enable interim updates, you can use this command:
~~~
aaa radius-server account-interim-interval [time in seconds]
~~~
## Enable Wi-Fi radio
There are two interfaces:
- `wifi0`, which is 2.4GHz
- `wifi1`, which is 5GHz
To enable the Wi-Fi radio, in this case Wi-Fi 5 (5GHz), use this command:
~~~
interface wifi1 radio profile radio_ac1 #WIFI 5
~~~
## Assign SSID to interface
~~~
interface wifi1 ssid "[security-object name]"
~~~
## Save config
To save the current configuration to ROM, use this command:
~~~
save config
~~~
