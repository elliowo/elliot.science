+++
title = "Running Mullvad VPN on Gentoo with OpenRC with OpenDoas"
date = 2023-04-08
[extra]
math = false
[taxonomies]
categories = ["projects"]
tags = ["vpn", "gentoo", "shell"]
+++

### Preface

This is a post about my fork of [phvr's](https://github.com/phvr/mullvad-wg) Mullvad script for Gentoo and OpenRC, replacing sudo with 
OpenDoas, with some additional features. Also details how to use it.

I have been using exclusively Linux for a few years now and started using VPN's around a bit before 
using Linux. I have used a few VPN's and Mullvad was the most appealing provider to me but when I 
moved from Arch to Gentoo. I had issues using it due to it not being in the default Gentoo overlay and
it's lack of support for OpenRC. I looked around for some solutions and discovered [phvr's](https://github.com/phvr/mullvad-wg) Mullvad 
script for Gentoo.

I have used this for the past year and it is a great script, but I have found it is missing some features
that would be nice. This is why I have created a fork of it with some of the features I would like and
some broken bits due to Mullvad changing their naming system.

Requires less resources due to no UI and OpenVPN :)


#### Installation

To add the overlay that contains it for portage:

```
$ eselect repository add elliowo-overlay git https://github.com/elliowo/elliowo-overlay.git
$ emerge --sync
$ emerge mullvad-wg-doas
$ mullvad help
```

From source:
```
$ git clone https://github.com/elliowo/mullvad-wg-doas.git
$ cd mullvad-wg-doas
$ chmod +x mullvad
$ ./mullvad help
```

#### Usage

##### Configuring the servers
To initialise the script to pull in all available servers and their wireguard configs, this will prompt your account number.
```
mullvad update servers
```
To rename the files to work with the script consistently:
```
mullvad update rename
```
To set a default server, is not required. You can get servers with `mullvad list`
```
mullvad update default
```


##### Connecting to a server
To connect to a random server
```
mullvad random
```

To connect to a default server, or can specify it.
```
mullvad connect
```

Note that this needs to be set with `mullvad update default`, before using the above command.



##### Enabling/Disabling kill-switch
Enable a kill-switch
```
mullvad kill-switch on <server>
```

Disable a kill-switch
```
mullvad kill-switch off <server>
```

It is possible to choose multiple servers. To enable a kill-switch for all servers run
```
mullvad kill-switch <on|off> all
```

##### Status of current connection
To get more detailed information about your connection, run
```
mullvad status
```
or
```
mullvad verify
```
to verify using the am.i.mullvad.net API

##### Choosing start-up server
It is possible to choose a server that will auto connect on boot.
```
mullvad start-up <on|off> <server>
```
Show the currently selected startup server:
```
mullvad start-up show
```
For this to work you need the 'local' service enabled:
```
# rc-update add local default
```

##### More information
* [repository](https://github.com/elliowo/mullvad-wg-doas) - Repository on github
* [phvr script](https://github.com/phvr/mullvad-wg) - Script this is based on.
* [Running WireGuard with Mullvad on Linux](https://mullvad.net/en/guides/wireguard-and-mullvad-vpn/) - Mullvad's official guide.
* [WireGuard](https://www.wireguard.com/) - Official WireGuard website.
* [OpenDoas](https://github.com/Duncaen/OpenDoas) - OpenDoas GitHub.
