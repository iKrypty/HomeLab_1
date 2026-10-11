# HomeLab_1
My first ever home lab as an amateur. Figuring my way out in the networking world. For this lab, my main mission is to hide my day to day internet traffic from my ISP.

My Goals:
* Segment my network with VLANs and firewall rules
* Turn traffic coming in and out of my ISP incognito
* Monitor and analyze traffic (Wireshark, Zeek, Suricata)
* Run self-hosted services (DNS, VPN, monitoring)
* Practice troubleshooting and document everything I learn

Devices
- Raspberry Pi 4 (4GB)
  Linux server, future network sensor. Raspberry Pi OS Lite (64-bit), headless, managed over SSH
- TP-Link TL-SG108PE
  Managed switch, 8 gigabit ports, 4 PoE, 802.1Q VLANs, port mirroring
- Cat6 pure copper cable
  Patch cables. Hand-terminated T568B, every cable tested
- ZOERAX network tool kit
  Pass-through crimper, cable tester, punch-down tool

Running Cost: 
 - Raspberry Pi 4:            $170.59
 - TP Link Switch:             $66.40
 - ZOERAX Tool kit:            $47.75
 - Cat6 Cable, boots, plugs:   $54.00
 - Total -------------------- $338.74



Day 1: 10/10/26
Raspberry Pi Setup:
* Flashed microSD with Pi OS Lite, and setup installation. Had to do it twice due to disk format error.
* Setup headless access through SSH
* Created a DHCP reservation through router to convert raspberry IP from dynamic to static.
* The Pi wouldn't accept SSH connections at first. Here's how I narrowed it down:
  > Layer 1 (Physical)
      ip addr on the Pi -eth0 showed NO-CARRIER / DOWN, so the cable was loose. Reseated it.
  > Layer 2 (Data Link)
      arp -a on my PC - Matched the Pi's MAC address to its IP
  > Layer 3 (Network)
      ping, Replies with TTL=64, which is typical of a Linux host
  > Layer 4 / Application
      ssh - "Connection refused" meant nothing was listening on port 22. Reflashing the SD card fixed it.
Total time spent ~ 2:30hr
What I learned: 
* Work from the bottom of the OSI model up instead of guessing
* "Connection refused" (host reachable, port closed) is different from a timeout (host unreachable)
* Windows asks to format a Pi SD card because it can't read the Linux partition. Never click Format.
* DHCP reservations keep a server's IP stable without hardcoding it on the device










    
