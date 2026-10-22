Day 3: 10/13/26 Switch Setup, WireShark, & DORA.

  * Connected all the cables and turned on the switch, with all green lights turning on meant all cables were successfully crimped and working properly.
  * Created a DHCP reservation for the switch IP by logging into router configurations and setting the IP to static.
  * Logged into the switch, created an admin password, updated the firmware to the respective switch model. 
  * SSH'ed into the pi to confirm everything was running smoothly and that the pi was correctly setup, and it was.
  * Downloaded Wireshark and watched a tutorial on how to read and filter packets. 
  * My PC's ethernet port was disabled for some reason, turned it on using Device Manager.

  What I learned:
  * Filtering packets for DHCP and going into my pc's command prompt and using ipconfig /release and ipconfing /renew
  * Finally saw a real time DORA request and looked back into what DORA is to refresh memory. 
        * 1. Discover: “Is there a DHCP server out there?”
            * Your PC has no IP yet, so it sends from 0.0.0.0 to 255.255.255.255, the broadcast address. That means it shouts to every device on the local network.
        * 2. Offer: “Here’s an address you can use.”
            * The router replies with an offer: an IP address (like 192.168.1.159), plus the subnet mask, default gateway, DNS servers, and how long the lease lasts.
        * 3. Request: “I’ll take that one.”
            * Your PC formally asks for the offered address. It’s still a broadcast, because if multiple DHCP servers made offers, this tells all of them which one the PC accepted.
        * 4. Ack (acknowledge): “Confirmed, it’s yours.”
            * The router locks in the lease, and your PC configures itself with the IP, gateway, and DNS.
  
