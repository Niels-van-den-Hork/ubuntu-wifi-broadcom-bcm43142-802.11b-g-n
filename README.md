# ubuntu-wifi-broadcom-bcm43142-802.11b-g-n
This fixes the 'no network adapter found' issues for my hp pavilion laptop on ubuntu.

Start the following from a clean install of ubuntu (in my case 18.04 and previously 16.04):

https://askubuntu.com/questions/55868/installing-broadcom-wireless-drivers
sudo apt install bcmwl-kernel-source

```
niels@niels-laptop:~$ sudo lshw -C network
  *-network UNCLAIMED       
       description: Network controller
       product: BCM43142 802.11b/g/n
       vendor: Broadcom Inc. and subsidiaries
       physical id: 0
       bus info: pci@0000:08:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress cap_list
       configuration: latency=0
       resources: memory:c6100000-c6107fff
  *-network
       description: Ethernet interface
       product: RTL810xE PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:09:00.0
       logical name: eno1
       version: 08
       serial: d0:bf:9c:93:f2:e8
       size: 100Mbit/s
       capacity: 100Mbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 duplex=full firmware=rtl8106e-2_0.0.1 04/23/13 ip=10.21.2.30 latency=0 link=yes multicast=yes port=MII speed=100Mbit/s
       resources: irq:19 ioport:4000(size=256) memory:c6004000-c6004fff memory:c6000000-c6003fff
```

```
niels@niels-laptop:~$ sudo lshw -C network
[sudo] password for niels: 
  *-network                 
       description: Wireless interface
       product: BCM43142 802.11b/g/n
       vendor: Broadcom Inc. and subsidiaries
       physical id: 0
       bus info: pci@0000:08:00.0
       logical name: wlo1
       version: 01
       serial: 74:29:af:e8:f7:19
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=wl0 driverversion=6.30.223.271 (r587334) ip=10.33.21.150 latency=0 multicast=yes wireless=IEEE 802.11
       resources: irq:18 memory:c6100000-c6107fff
  *-network
       description: Ethernet interface
       product: RTL810xE PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:09:00.0
       logical name: eno1
       version: 08
       serial: d0:bf:9c:93:f2:e8
       capacity: 100Mbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 firmware=rtl8106e-2_0.0.1 04/23/13 latency=0 link=no multicast=yes port=MII
       resources: irq:19 ioport:4000(size=256) memory:c6004000-c6004fff memory:c6000000-c6003fff
```
