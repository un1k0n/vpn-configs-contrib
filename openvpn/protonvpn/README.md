# Port Forwarding with ProtonVPN

Port forwarding for ProtonVPN has been implemented in this [update-port.sh](/openvpn/protonvpn/update-port.sh) script. The novel part of this script is based on the [port forwarding instructions from ProtonVPN](https://protonvpn.com/support/port-forwarding-manual-setup/#linux). 

## Requirements:
- an account with ProtonVPN
- a build of haugene/docker-transmission-openvpn that has natpmpc installed.
  - The dev branch of haugene/docker-transmission-docker has the natpmpc install. As of 2023-11-19, it is not yet in the master branch and/or the published image.
  - If your transmission container does not have natpmpc then transmission will still work - you just will not be using port-forwarding.
  - The brave may manually install natpmpc inside their transmission-openvpn container.
  - The less brave will need to wait until the published image of docker-transmission-openvpn has natpmpc.


## Notes:
This script has been manually tested to work with the following ProtonVPN configs that are included in this repo.:
- ch.protonvpn.net.udp
- es.protonvpn.net.tcp
- es.protonvpn.net.udp
- is.protonvpn.net.tcp
- is.protonvpn.net.udp
- ng.protonvpn.net.tcp
- ng.protonvpn.net.udp
- nl.protonvpn.net.tcp
- nl.protonvpn.net.udp
- ro.protonvpn.net.udp
- ro.protonvpn.net.tcp
- se.protonvpn.net.tcp
- se.protonvpn.net.udp
- uk.protonvpn.net.udp
- us.protonvpn.net.udp

## Environment Variables for transmission-openvpn
```
environment:
  - PUID=[PUID]
  - PGID=[PGID]
  - OPENVPN_CONFIG=us.protonvpn.net.udp
  - OPENVPN_PROVIDER=PROTONVPN
  - OPENVPN_USERNAME=[OpenVPN / IKEv2 username] # See here: https://account.protonvpn.com/account
  - OPENVPN_PASSWORD=[OpenVPN / IKEv2 password] # See here: https://account.protonvpn.com/account
  - LOCAL_NETWORK=[your local network]/24 
  - DISABLE_PORT_FORWARDER=false
  - OPENVPN_OPTS=--inactive 3600 --ping 10 --ping-exit 60
...   
```
