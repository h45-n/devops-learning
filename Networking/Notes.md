# NetworkChuck New  
- Initially made on Remnote, but, later transferred to here.
- Extracurricular understanding  

# Networking — Subnet ep1  

- Ansar are like Hosts... In IP address, we have the last set (host) 192.168.1.0  
- IP Address is like street, Home is like Host.  
- When device wants to communicate outside street/ IP address (outside network), has to talk with Router/ Default Gateway  
- Network portion 192.168.1 (first 3 no's)—— constant does not change., like if you live at the same address, but different rooms in your house
- Host— last number, eg .0 — can change — Variable (like the rooms in your house)  
> I use the Same House, different Room analogy, makes more sense in a Local Area Network (where we live at the same location, but, different devices are different hosts.)  
> Eg. I live at this address (x street), in this room (7). Eg, laptop is 192.168.1.48, PS5, 192.168.1.60, phone 192.168.1.30  
> Can hand data packets at the same address/ network, different Room  
> BUT, if you have to discuss data packets across different parts of the world/ networks, gotta go through router.  

Initial understanding, subnet mask is locked with the first 3 numbers of IP address. — ie. Locked with subnet mask (255.255.255.0)  
- in IP Address, the last part of octet (.0) in, 192.168.1.0, can't touch/ configure a device to it — Network address/ Subnet ID  
- 192.168.1.255 — broadcast address — loudmouth  
- 192.168.1.1 — Default Gateway — Router  
- Last portion of IP address, host, can assign a number, 0-255 range. 0 can't, 1 can't, 256, can't. So 256-3=253 devices can have their own host.  

Subnet Mask tells us what our House Address is — IP address.  
> Number with IP Address is Locked, when there's a corresponding  255 in Subnet (eg, 1 and 255, 1.0.0.0; 255.0.0.0) — same octet/set in IP address,  They're locked basically — can't assign devices.  
> 3 255s = locking in first 3 (IP) numbers  
   
**> If a company has a IP address (combos big), eg. 4.0.0.0 and 255.0.0.0 — they can shorten it into 4.5.6.0; 255.255.255.0 — reducing their combos (from like millions to just 0–255, 256.) Turning a large network into smaller/ sub net-works. (Subnet= smaller pool of combos.)  
> If my IP is 10.0.0.0 and subnet is 255.255.0.0 then the first two sets, in the IP address, are locked (with those 255s in Subnet)  

We all have only 1 Public IP Address + we have the private IP address (eg. 192.168.1.0) at home, but, to access the internet, a NAT is used to translate that to a public IP address.  
- They (IANA) took a chunk/ range of Public IP Addresses and designated it as Private (eg. 192.168.0.0–192.168.255.255, subnet 255.255.255.0)  

- Our network leaves our bubble/ LAN, with one identity/ public ip  

Subnet Mask trick  
> At the end right, there's the host part, first part (on left) is network..to calc, how many hosts we can have, we do 2^(no.Zeroes)-2  
- how many zeroes there are, eg. In subnet mask, 255.255.255.0, there's 2⁸^(-2) = 254 (subnet ID, broadcasting address removed)  

*>>  If Subnet Mask= 255.255.254.0, we have 11111111.11111111.11111110.00000000 (9, zeroes, 2⁹(-2) =512-2 bits), which translates to 510 available hosts ↓↓  
- 510 devices can connect, 510 usable IP Addresses on network.  
- Subnet Mask tells us how *big* our network is.  
- Subnet Mask is Contiguous (row of ones, row of zeroes.)  


MaShaAllahu LaQuwataIlaBillah 