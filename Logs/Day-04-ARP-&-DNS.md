Day 3: 10/22/26 Understanding ARP & DNS through WireShark:

* Started a Wireshark capture on Ethernet with the filter arp, cleared my PC's ARP cache (admin PowerShell) so it had to ask again.
* Changed the Wireshark filter to dns, cleared the DNS cache (needed an admin PowerShell window)
* Connected my second PC to the switch using another custom length cable.
* ARP has no authentication. Any device can reply "that IP is me," which is how ARP spoofing and man-in-the-middle attacks work.

What I learned: 
 * ARP connects Layer 3 to Layer 2. Requests are broadcast, replies are unicast.
 * "Dynamic" in arp -a describes how the mapping was learned, not how the device got its IP.
 * DNS uses A records for IPv4 and AAAA for IPv6, over UDP port 53.
 * Windows may try DNS suffixes before the actual name, which explains "No such name" results I didn't expect.
 * Plain DNS is visible to anyone on the path, which is why encrypted DNS matters.
 * Some commands (ipconfig /flushdns, arp -d *) require an administrator shell.

Queries went from my PC to my router (192.168.1.1) on UDP port 53. Each query and its response share a Transaction ID, the same idea as in DHCP. The answer includes a TTL, which is how long my PC can cache the result.

Time Spent: 1.5 hours












