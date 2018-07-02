# Brad's Homelab

This page describes my home server & networking setup.

# Goals

The primary goals of this project are...

* to have a highly-available home Internet setup, with no SPOF (Single Point of Failure)

* to learn and have fun.

# In summary

I have 3 physical machines plugged into 3 switches, with all switches
connected to each other. I don't have a physical
router/gateway. Instead, a Linux virtual machine handles the IPv4 NAT,
IPv6 announcements, DHCP, DNS, etc, and that Linux VM floats between
the 3 VMs as needed, including live migration during maintenance.

My 4 Wifi APs are PoE-powered from the two switches. I have two ISPs.

I have two UPSes and two PDUs powering separate halves of the gear,
and separate ISPs, giving me about 35-45 minutes of runtime (and thus
Internt) during a power outage. The whole house might be dark, but the
battery-powered wifi will work.

# Gear

## Servers

* 3 x [Supermicro SYS-5018D-FN8T](https://www.supermicro.com/products/system/1u/5018/SYS-5018D-FN8T.cfm)
  * 64 GB RAM (2 x 32GB DDR4 PC4-19200 2400MHz 288p RDIMM), leaving room to double RAM later
  * boot/OS disk: 64 GB SATA DOM ([SSD-DM064-SMCMVN1](https://www.supermicro.com/products/nfo/SATADOM.cfm))
  * SSD 1: Samsung SSD 850 EVO 500GB
  * SSD 2: Samsung SSD 860 EVO 1TB
  * HDD, external: 8000 GB [HGST HUH728080ALE600](https://www.amazon.com/gp/product/B00NP6AOCK)

## Switches

* 2 x [UniFi Switch 24 PoE-250W](https://www.ubnt.com/unifi-switching/unifi-switch-poe/): 24x Power-over-Ethernet 1Gbps ports
* 1 x [UniFi Switch 16 XG](https://www.ubnt.com/unifi-switching/unifi-switch-16-xg/): 10Gbps Aggregation Switch

## Wi-Fi APs

* 2 x [UniFi AP-AC-Pro](https://www.ubnt.com/unifi/unifi-ap-ac-pro/)
* 2 x [UniFi AP-AC-In Wall](https://inwall.ubnt.com/)

## Power

The whole setup including all APs and switches draws about 220 watts idle.

* 2 x [APC Back-UPS Pro 1000 BR1000G](https://www.amazon.com/APC-Back-UPS-Battery-Protector-BR1000G/dp/B0038ZTZ3W)
* 2 x [APC AP7801 Rack PDU](https://www.amazon.com/gp/product/B004Y39T7Y/)

## ISPs

* CenturyLink Fiber (gigabit), primary ISP.
* [Atlas Networks](http://www.gigabitseattle.com/), my backup ISP: a ~100Mbps radio link, using a [Unifi NanoBeam AC](https://www.ubnt.com/airmax/nanobeam-ac-gen2/).

# Software

* [Proxmox VE](https://www.proxmox.com/en/) for VMs (previously tried VMware for about a year, both are [annoying in different ways](https://twitter.com/bradfitz/status/1000087524876800000).
* [Ceph](https://ceph.com/) for storage. I love Ceph so much and discovering it makes this whole adventure worth it. Still much to learn, though.


